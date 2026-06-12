---
title: "Why can't I execute my command?"
date: 2019-10-16
forum: New to Ubuntu
---

### Post by qianqian2019 on 2019-10-16
[COLOR=#000000]I intend to run a docker container with command:
[/COLOR]```
docker run \
-it \
--env="DISPLAY=$DISPLAY" \
--volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
--volume="/home:/home \
ubuntu:16.04

```
[COLOR=#000000]I COPY the command ,PASTE into the terminal,press ENTER ,then I got
[/COLOR]```
lxq@ubuntu:~$ docker run \
> -it \
> --env="DISPLAY=$DISPLAY" \
> --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
> --volume="/home:/home \
> ubuntu:16.04
> 
> 
> 

```

[COLOR=#000000]everytime I press ENTER,a `>`shows up.[/COLOR]
[COLOR=#000000]I've tried `ctrl+c`,`ctrl+d`&#65292;but didn't work.[/COLOR]

[COLOR=#000000]If I input the command manually,the command works fine.[/COLOR]

[COLOR=#000000]My question is :[/COLOR]
[COLOR=#000000]Why does it happen?[/COLOR]
[COLOR=#000000]How can I fix it?(i.e. run the command using COPY and PASTE&#65289;[/COLOR]

[COLOR=#000000]Thanks&#65281;[/COLOR]

---

### Post by qianqian2019 on 2019-10-16
my bad ,I missed a double quotation mark after &#8216;home&#8217;

---

### Post by Claus7 on 2019-10-16
Hello,

I think that you should enclose the code using sideways double chevrons like:
docker  run \ << EOF
> -it \
> --env="DISPLAY=$DISPLAY" \
> --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
> --volume="/home:/home \
> ubuntu:16.04
EOF

Is it working that way? By pressing enter and seeing that more > are added it means that it cannot understand that the group of commands has ended, that's why by triggering EOF (End-Of-File) it does that exactly.

edit: good that you found solution, EOF is handy in many cases as well.

Regards!

---

