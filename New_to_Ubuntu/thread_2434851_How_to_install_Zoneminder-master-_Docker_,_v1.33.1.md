---
title: "How to install Zoneminder-master- Docker , v1.33.16 with MSMTP on Ubuntu 19.10 (Eoan"
date: 2020-01-12
forum: New to Ubuntu
---

### Post by bkjaya1952 on 2020-01-12
In this tutorial ,we are going to use [“Docker: Enterprise Container Platform”]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwjRx93Lsc7fAhXILY8KHar-AAcQFjAAegQIAhAB&url=https%3A%2F%2Fwww.docker.io%2F&usg=AOvVaw0Vr113vt10kRWhG_4dy1nX")  ([docker.io]("https://launchpad.net/ubuntu/+source/docker.io")) on Ubuntu 19.10.
 As , still there is on official  zoneminder issued for  Ubuntu 19.10  due dependency issues, the best option is to use docker Zoneminder  to  overcome dependency problems and to avoid conflicts with the default  setup of  Ubuntu 19.10
 First
 **Installation of Docker on Ubuntu 19.10**
 
On the Ubuntu terminal

 
sudo apt install docker.io

 
Then use , [bkjaya1952/docker-zoneminder-master  Docker Repository]("https://hub.docker.com/r/bkjaya1952/docker-zoneminder-master") to make a container . ( This image has been created on Ubuntu 19.04 disco )


sudo docker create -t -p 8085:80 --shm-size=4096m -e TZ=Asia/Colombo  --name myzm --privileged=true  bkjaya1952/docker-zoneminder-master:v1.33.16.

 
Note :- use your timezone instead of "TZ=Asia/Colombo"


For configuring MSMTP for emailing zoneminder motion detection events, please refer the following link.
 [URL="https://hub.docker.com/r/bkjaya1952/docker-zoneminder-master"]
https://hub.docker.com/r/bkjaya1952/docker-zoneminder-master[/URL]

 Open [http://localhost:8085/zm/](http://localhost:8085/zm/) and add the camera monitors
 
And fill up email details under the Optons/email of the ZM-Panel

 
Create appropriate zm-filter to send email alerts of motion detection events


 
sudo docker start myzm

[IMG]https://bkjaya.files.wordpress.com/2020/01/screenshot-from-2020-01-12-11-20-09.png?w=700[/IMG]


[CENTER]Figure:- 1 After adding Camera monitors to ZM

[/CENTER] [HR][/HR]  
 The scripts of the Dockerfile are as shown in the following figure



[IMG]https://bkjaya.files.wordpress.com/2020/01/screenshot-from-2020-01-12-11-07-16.png?w=700[/IMG]


[CENTER]Figure:-2 The scripts of the Dockerfile[/CENTER] 
To download the Dockerfile  [https://www.dropbox.com/s/737qnv3144b52bi/Dockerfile?dl=0](https://www.dropbox.com/s/737qnv3144b52bi/Dockerfile?dl=0)

 
To download the entrypoint.sh [https://www.dropbox.com/s/m5lgf2d196a4f5s/entrypoint.sh?dl=0](https://www.dropbox.com/s/m5lgf2d196a4f5s/entrypoint.sh?dl=0)

 
Please refer my following blog to know about the building an image and pushing to the Docker Hub

 [URL="https://bkjaya.wordpress.com/2019/12/20/how-to-build-a-zoneminder-docker-image-with-msmtp-using-a-dockerfile-push-to-docker-hub-ubuntu-19-10/"]
https://bkjaya.wordpress.com/2019/12/20/how-to-build-a-zoneminder-docker-image-with-msmtp-using-a-dockerfile-push-to-docker-hub-ubuntu-19-10/[/URL]

 
Acknowledgements : Based on Zoneminder and Andrew Bauer’s [EMAIL="zonexpertconsulting@outlook.com"]zonexpertconsulting@outlook.com[/EMAIL] entrypoint script

---

