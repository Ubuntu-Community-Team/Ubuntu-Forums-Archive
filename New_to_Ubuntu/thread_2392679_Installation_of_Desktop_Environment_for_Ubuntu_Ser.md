---
title: "Installation of Desktop Environment for Ubuntu Server Taking over 12 hours"
date: 2018-05-23
forum: New to Ubuntu
---

### Post by davekng0001 on 2018-05-23
Hello All!

I just received my first Linux Server internship gig, and Ive run into my first issue. The previous server administrator for this machine installed Ubuntu Server 16.04.3 LTS with no desktop environment (no gui) he also downloaded and installed about 40GB of software necessary for the server's function. 

When I received the machine first thing I wanted to do was install a desktop environment using the following

[HTML]
sudo apt-get update
sudo apt-get install ubuntu-desktop
[/HTML]
 
I first tested the procedures on my virtual machine that is running the same operating system, and it worked successfully taking only 15-30 minutes. I then went through with doing it on the physical server. 

At first it was going fast but after the first part of the installation ended and it asked me some [y/n] question it began going very slowly. over 12 hours has passed and it is still installing just as slowly.

An image of the output is seen below.

[ATTACH=CONFIG]279815[/ATTACH]


Any advice on why this is, would be very appreciated!

Thank you

---

### Post by QIII on 2018-05-23
Hello!

For some reason, which we cannot diagnose without further information, your machine is not connecting to the web or the server hosting the repo. That could be for any number of reasons, both internal and external.

What happens, for instance, if you attempt to ping the router or 8.8.8.8?  That will give us a starting point.

The previous admin didn't install Ubuntu Server without a desktop.  He or she installed Ubuntu Server, which does not have a GUI.  As you are an intern, my advice would be to use the server as intended and learn things right from the start.  A desktop adds a load of unnecessary services.  Servers, especially web servers, should be installed with the barest number of services needed to perform their intended purpose.  In the real world, it is exceedingly rare to find a server sporting a desktop.  Do that out here and folks might look at you sideways and ask themselves if you know what you are doing.

---

### Post by davekng0001 on 2018-05-23
Thanks for your response @Qlll! How should I safely stop the installation process, Im worried about just turning it off and then turning it on. 

Also Im curious why it is best for servers to be as bare as possible.

---

