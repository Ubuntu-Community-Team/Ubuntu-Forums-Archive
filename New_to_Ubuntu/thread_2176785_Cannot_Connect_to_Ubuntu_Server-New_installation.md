---
title: "Cannot Connect to Ubuntu Server-New installation"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by Harry_Gohil on 2013-09-26
Hi guys, I have a VMware and I am running  a Ubuntu server on it. I've been trying to connect to it for more than a week now without really getting anywhere(Was able to see certificate error once or twice maybe). I've tried doing a lot of things.. Installed Windows7 after removing windows8(I Thought it was OS problem), then searched the forums and tried setting a static ip(I have no idea if I was successful doing it as I could not connect to the server.), copy pasted a lot of commands etc. So basically I wanted to know where exactly am I going wrong as this is a bit frustrating now.

I have installed the server as I mentioned before on a VMware and I am currently playing the file with VMware to run the server. I usually connect to the server by connecting to the eth0 inet address . I don't know if this helps but I am using a laptop connected to a wireless modem. 

Thanks:)

---

### Post by 7182818 on 2013-09-26
Can you use a program like PuTTY to SSH to it?  If you have problems with that, the issue might be that the VMWare network interface card is set to the wrong type (Make sure it's Bridged instead of NAT) or the network settings aren't configured properly in the VM.  If you can SSH to it and you are having problems connecting to a webserver, for example, make sure it is running (For example, for apache, 'httpd -k start')

---

### Post by Harry_Gohil on 2013-09-26
Wowowow, No idea how but I removed the image from the VMware that I had and installed it again.. Tried to connect to the ip after ifconfig and it shows the "It works" page. Thanks a lot for the help..
Now I was wondering how I can access the index.html file (or any other files that I might wanna upload.)

---

