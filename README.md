### 欢迎加入直播源等影视资源分享交流群:https://t.me/tvzby

#
## Nginx反代教程
1.以Debian/Ubuntu系统举例，安装nginx:
```
sudo apt update
sudo apt install nginx
```
2.替换/etc/nginx/nginx.conf:
```
curl -fsSL https://raw.githubusercontent.com/rad168/mytv/refs/heads/main/nginx/nginx.conf -o /etc/nginx/nginx.conf
```
如需自定义token，请把nginx.conf第69行的"mytv123"修改为你自己的token。
3.重启Nginx:
```
sudo systemctl restart nginx
```
4.订阅链接(mytv.m3u)：
```
http://服务器ip:30000/mytv.m3u?token=mytv123
```
5.stream-link订阅链接:
```
http://服务器ip:30001/playlist.m3u?token=你的token
```

## Alpine系统Nginx反代教程
1.安装Nginx:
```
apk update
apk add nginx
service nginx start
rc-update add nginx boot
```
2.替换/etc/nginx/nginx.conf:
```
curl -fsSL https://raw.githubusercontent.com/rad168/mytv/refs/heads/main/nginx/alpine/nginx.conf -o /etc/nginx/nginx.conf
```
3.重启Nginx:
```
service nginx restart
```
4.订阅链接(mytv.m3u)：
```
http://服务器ip:30000/mytv.m3u?token=mytv123
```
5.stream-link订阅链接:
```
http://服务器ip:30001/playlist.m3u?token=你的token
```

## 无token版nginx.conf
除非你有特殊需求，否则不推荐使用,支持Ubuntu/Debian系统:
https://raw.githubusercontent.com/rad168/mytv/refs/heads/main/nginx/notoken/nginx.conf

## docker部署教程
1.下载alpine系统版的nginx.conf到指定目录(默认为/root/mytv):
```
mkdir -p /root/mytv && \
curl -fsSL https://raw.githubusercontent.com/rad168/mytv/refs/heads/main/nginx/alpine/nginx.conf -o /root/mytv/nginx.conf
```
2.一键部署命令：
```
docker run --name="mytv" --restart=always --net=host -d --mount type=bind,source=/root/mytv/nginx.conf,target=/etc/nginx/nginx.conf --log-opt max-size=10m --log-opt max-file=3 nginx:alpine3.22-slim
```
3.后续如果需要更新，可使用一键更新命令：
```
curl -fsSL https://raw.githubusercontent.com/rad168/mytv/refs/heads/main/nginx/alpine/nginx.conf -o /root/mytv/nginx.conf && docker restart mytv
```
4.订阅链接(mytv.m3u)：
```
http://服务器ip:30000/mytv.m3u?token=mytv123
```
5.stream-link订阅链接:
```
http://服务器ip:30001/playlist.m3u?token=你的token
```

## PHP部署方案：
1. 将 mytv.php 上传到网站目录  
   PHP文件链接：https://raw.githubusercontent.com/rad168/mytv/refs/heads/main/php/mytv.php  

2. 已支持获取订阅功能，访问：  
   `mytv.php?p=m3u`  

3. 也可代理任何其他 hls/m3u8 直播源：  
   `mytv.php?url=http://xxxx.com/hls/xxx.m3u8`


### 更多直播源分享，欢迎加入直播源等影视资源分享交流群:https://t.me/tvzby





