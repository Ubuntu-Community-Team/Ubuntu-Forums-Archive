---
title: "size of my compiled binary much larger than packaged binary"
date: 2010-10-01
forum: Packaging and Compiling Programs
---

### Post by captainnick on 2010-10-01
Hi,

When I build nginx from source, my executable ends up being 7x larger than the packaged pre-built binary:

my version: nginx 4832415
packaged:   nginx   657800

That said the version I've compiled appears to work perfectly well, but I'm worried that such a large discrepancy in size indicates perhaps I've built a debug-symbol bloated version. I'd like understand why there's such a large difference.
This is the first package I've attempted to build from source so I've probably made a misstep in the process, rather than it being something specific to nginx

I'm compiling on Ubuntu server 10.04 64bit intel. Starting with a clean Ubuntu image I compiled the source using the following steps:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nginx
sudo apt-get install build-essential
apt-get source nginx
sudo apt-get install libssl-dev libpcre3-dev zlib1g-dev
cd nginx-0.7.65

# nginx can be configured with many modules I copied the configuration I found in nginx-0.7.65/debian/rules:
./configure --conf-path=/etc/nginx/nginx.conf \
--with-cpu-opt=amd64 \
--error-log-path=/var/log/nginx/error.log \
--pid-path=/var/run/nginx.pid \
--lock-path=/var/lock/nginx.lock \
--http-log-path=/var/log/nginx/access.log \
--http-client-body-temp-path=/var/lib/nginx/body \
--http-proxy-temp-path=/var/lib/nginx/proxy \
--http-fastcgi-temp-path=/var/lib/nginx/fastcgi \
--with-debug \
--with-http_stub_status_module \
--with-http_flv_module \
--with-http_ssl_module \
--with-http_dav_module \
--with-http_gzip_static_module \
--with-http_realip_module \
--with-mail \
--with-mail_ssl_module \
--with-ipv6 \
--add-module=./modules/nginx-upstream-fair

make
ls -l objs/nginx
# result: 4832415 objs/nginx

# compare with:
ls -l /usr/sbin/nginx
# result: 657800 /usr/sbin/nginx

Thanks

Nick

---

### Post by SevenMachines on 2010-10-01
debuild also sets up the gcc build environment. when using configure/make you'll see that -O is passed to gcc whereas debuild passes -O2, so more optimisation, resulting in the large size difference. for example..

> $  ./configure --conf-path=/etc/nginx/nginx.conf  --with-cpu-opt=amd64 --error-log-path=/var/log/nginx/error.log  --pid-path=/var/run/nginx.pid --lock-path=/var/lock/nginx.lock  --http-log-path=/var/log/nginx/access.log  --http-client-body-temp-path=/var/lib/nginx/body  --http-proxy-temp-path=/var/lib/nginx/proxy  --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --with-debug  --with-http_stub_status_module --with-http_flv_module  --with-http_ssl_module --with-http_dav_module  --with-http_gzip_static_module --with-http_realip_module --with-mail  --with-mail_ssl_module --with-ipv6  --add-module=./modules/nginx-upstream-fair

$ make

$ ls -s objs/nginx 
4412 objs/nginx


$ CFLAGS+=-O2 ./configure --conf-path=/etc/nginx/nginx.conf --with-cpu-opt=amd64 --error-log-path=/var/log/nginx/error.log --pid-path=/var/run/nginx.pid --lock-path=/var/lock/nginx.lock --http-log-path=/var/log/nginx/access.log --http-client-body-temp-path=/var/lib/nginx/body --http-proxy-temp-path=/var/lib/nginx/proxy --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --with-debug --with-http_stub_status_module --with-http_flv_module --with-http_ssl_module --with-http_dav_module --with-http_gzip_static_module --with-http_realip_module --with-mail --with-mail_ssl_module --with-ipv6 --add-module=./modules/nginx-upstream-fair

$ make

$ ls -s objs/nginx 
656 objs/nginx



---

### Post by captainnick on 2010-10-01
> **SevenMachines said:**
> debuild also sets up the gcc build environment. when using configure/make you'll see that -O is passed to gcc whereas debuild passes -O2, so more optimisation, resulting in the large size difference. for example..

Thanks that help a lot. I guess time to familiarise myself with debuild and [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

