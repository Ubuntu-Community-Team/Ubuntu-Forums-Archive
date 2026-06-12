---
title: "[Howto] Live Webcam for video chat and other things...."
date: 2006-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by encompass on 2006-07-17
**[CENTER]Live Webcam Feed[/CENTER]**
This Howto has totally changed to make things A LOT easier.  After a year of working with this thing I have got it down pretty good.
I have a few things before it is totally done...
I need to not have camserv start at startup and I am working on a frontend called CamServFront that will start and stop the webcam whenever you like...
Sadly, I have many other projects I am also working on so it will have to wait until demand provides. In other words, if you want to pay be a small amount it would be worth it. :D
1: INSTALL
```
sudo apt-get install webfs camserv
```
```
mkdir ~/.CamServFront
[CODE]mkdir /home/skunkyjay/.CamServFront/Server
```
Then download the attached file called...WebcamSetup....
2: SETUP
Extract the file and put it in .CamServFront/Server
Setup Camser by editing the file for camserv
```
sudo gedit /etc/camserv/camserv.cfg
```
Make sure you have set everything up for your webcam.  If you are worried.  Ask me and I will help you.  Until I understand how detailed I need to be there I won't right anything.
I jsut recommend not changing the port as everything else in my instructs depend on that.
From here it is rather easy...
Run this command...
```
webfsd -p 1026 -b U:P -F -r ~/.CamServFront/Server/
```
Where the U and the P are your username and password.  Look at man webfsd for details.
Go here and record your IP address.... [www.whatismyip.com](www.whatismyip.com)
Go to your webbrowser and type your IP addy in with the port :1026 like this.... 85.111.119.250:1026
For the user and pass DON'T USE ANYTHING that you use now... these are saved as plain text and anyone can read then on your computer.
Did you see anything?  You won't or should see your cam yet... but you will see a java applet and a simple webpage.  If so your running your webserver properly.
Then we change ip information found here...
```
gedit ~/.CamServFront/Server/index.html
```
Find the line "param name="url" value="http://84.250.111.119:9192""change the ip address to your IP address.  Be sure to leave the port there... that is the number after ":"
From there... you can test the cam....
Start a Terminal and run this... leaving it open...
```
webfsd -p 1026 -b U:P -F -r ~/.CamServFront/Server/
```
There you should be able to type your username and password in and it should show your directory with index.html click it and hopfully it work.
When your done I recommand killing running command with cntrl-c and unpluging your cam, until I get this camserv thing stopped you have to do it manually and that is a pain.  to stop the cam manully type...
```
sudo /etc/init.d/camserv stop
``` (and start to run it again)
Tell me what I can improve and I will make things better from there...

---

### Post by wakady on 2007-07-06
good work 
will try it later
thx

---

### Post by mmoalem on 2007-09-01
hi there and thanks for the effort - however i did try to follow on your instructions but its kind of a mess like the line
gedit ~/.CamServFront/Server
server is a directory and not a file
also you write:
run this comand...
and you dont write what command...
any chance you could clear this up a bit
cheers
michel

---

### Post by encompass on 2007-09-02
I will fix it when I can.  Very busy right at the moment on this...
[http://launchpad.net/memaker](http://launchpad.net/memaker)
And I am very sorry for the mess.  It was a quick copy paste.

---

### Post by newpants2003 on 2007-09-10
> **encompass said:**
> I will fix it when I can.  Very busy right at the moment on this...
[http://launchpad.net/memaker](http://launchpad.net/memaker)
And I am very sorry for the mess.  It was a quick copy paste.

still waiting...........

---

### Post by newpants2003 on 2007-09-11
> **encompass said:**
> I will fix it when I can.  Very busy right at the moment on this...
[http://launchpad.net/memaker](http://launchpad.net/memaker)
And I am very sorry for the mess.  It was a quick copy paste.

what is the username and password?

---

### Post by encompass on 2007-09-11
> **newpants2003 said:**
> what is the username and password?

When your start your webserver called webfsd you ser it with the -b option so if you want jason and the pasword brower you add the -b jason:brower.
Remember that this password should not be something that you normally use.  As it is seen in the console.

---

### Post by newpants2003 on 2007-09-27
could i just pick frame by using the software you wrote?

and could it be compiled for arm9 ?

---

### Post by encompass on 2007-09-28
In theory you can use any HTML browser to grab the frame port something... you can set that with camserv.cfg.
Sadlly, many browswer freek out when they see it.  Except for good old netscape and mozzilla.  That is why I stream it over the camboloza server.
You could simply try downloading and running the cambaloza java program to your phone(I am presuming) and run it from there.  You may have to tweak it a bit... but it should work.
Good luck with the idea and don't be afraid to ask anything else.

Actually, the port is 9192 by default.  So with a browser you could type.... ip.of.com:9192 and see if it works.  Report back if you have any good news. :D

---

### Post by encompass on 2007-09-28
I have updated the page... and added a screenshot of the cam in action.  I hope you can get it running.  It was nice to take the time to get this page working again.

---

### Post by shezars on 2011-01-19
First thanks for nice post, but why in second command, like:
#webfsd -p 1026 -b shezars:123456 -F -r ~/.CamServFront/Server/
bind: Address already in use

and if i access on the web, still "Please Hold, with the default picture" ...
any suggestion ?
:popcorn: :popcorn:

---

### Post by shezars on 2011-01-19
First thanks for nice post, but why in second command, like:
#webfsd -p 1026 -b shezars:123456 -F -r ~/.CamServFront/Server/
bind: Address already in use

and if i access on the web, still "Please Hold, with the default picture" ...
any suggestion ?
:popcorn: :popcorn:

---

