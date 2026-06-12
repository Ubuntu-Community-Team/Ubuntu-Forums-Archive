---
title: "Xming + putty = cannot open display: :0"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by bjnr on 2008-08-06
Hi guys!

I installed Xming on my Windows PC. 
Xming.exe :0 -clipboard -multiwindow

Putty
Enable X11 forwarding - checked
X display location - localhost:0

Connect to Ubuntu via putty - 
root@Ubuntu-804-hardy-LTS-32-minimal:~# export DISPLAY=:0
root@Ubuntu-804-hardy-LTS-32-minimal:~# firefox
Error: cannot open display: :0

What am I doing wrong?

Thank you for answers!!!

---

### Post by maybeway36 on 2008-08-06
Don't run DISPLAY=:0 first. It should work without that.

---

### Post by bjnr on 2008-08-06
I get the following then -
root@Ubuntu-804-hardy-LTS-32-minimal:~# firefox
Error: no display specified

---

### Post by bjnr on 2008-08-06
sudo apt-get install xauth 
helped me.

The connection is sooo slow thou...
Do you know how to compress it or make it faster?
The Ubuntu server is in another country.

---

### Post by bodhi.zazen on 2008-08-06
1. Forward applications and not an entire desktop

ssh -X -c blowfish user@server

see man ssh.

2. Learn the command line :twisted:

The majority of server management is editing text files which does not require X.

3. Use a web tool / web interface, ie webmin (or similar).

---

### Post by bjnr on 2008-08-06
Hm..
My goal is to run VMware Workstation on it. I do not need webmin or anything, I only need VMware WS.
I do forward firefox only I think, not the entire desktop as I do not have any desktop on my Ubuntu server - it's empty. Firefox only at the moment.

And I am kinda familiar with command line. Played around with Solaris for a while.

So the question is - how to make remote X11 application thing faster. The network consumption is huge and the application(firefox) is veeeery slow. I think it is trying to send me 24 bmp files per second or something like this..

Thanks for anwers.

---

### Post by bodhi.zazen on 2008-08-06
VMWare Server 2.0 has a web interface , do not know if that is an option.

Server 1.0.6 has the "Management interface"

> The VMware Server Web-based management interface. Install on your VMware Server system to enable control from a Web browser. Includes downloadable VMware Server Console installation files.

Why do you need to forward firefox ? Can you use a lighter browser ?

ssh -CX user@server

---

### Post by bjnr on 2008-08-06
firefox was for testing only.
Vmware is my goal!
Thanks for the tip reg Server option.

---

