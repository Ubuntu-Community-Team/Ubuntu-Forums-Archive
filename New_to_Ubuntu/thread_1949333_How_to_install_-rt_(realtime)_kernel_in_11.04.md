---
title: "How to install -rt (realtime) kernel in 11.04?"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by sal89 on 2012-03-30
Hi all -

I'm a relative newcomer to Ubuntu.  I run PureData and work as an sound artist.

I'd like to install the linux-rt realtime kernel to improve my audio latency, but am completely stumped.

I run Ubuntu 11.04, **installed using wubi** (under Windows 7).

I did some research and tried adding these two repositories:
**sudo add-apt-repository ppa:ubuntustudio-dev/ppa**
and[B]
sudo add-apt-repository ppa:kernel-ppa/ppa[/B]

Then i tried typing:
**sudo apt-get install linux-rt**

But then all I get is this error:
[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-rt
sal@ubuntu:~$[/B]

???
Eeek! Can anyone help me?
I don't understand how repositories work, nor do I have any experience installing software on Ubuntu other than selecting stuff from a list in the Software Center.  In short, I have no idea what I'm doing :S

Cheers,
Sal

-----
Toshiba Satellite L750 laptop
Ubuntu 11.04 Natty - WUBI install, under Win7

---

### Post by Cheesemill on 2012-03-30
Did you do:
```
sudo apt-get update
```
after adding the repositories?

---

### Post by Jake5 on 2012-03-30
The -rt package sounds like its a little advanced for your needs, this is used for executing commands and sending them to automated machinery systems. It sounds like what you need is a better sound card, as the -rt package is hardware dependent, you may get a little better performance, but I doubt you will notice a difference. I hope it works out if you try it though.

---

### Post by Cheesemill on 2012-03-30
Apparently the -rt kernel is no longer being developed:
[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

See here for more options:
[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

---

### Post by Eiji Takanaka on 2012-03-30
I'm also into my sound recording dude.

Last i checked the latest stable r-t kernel was either 10.04 or 9.10. And it is a useful thing to have near zero latency in a sound recording situation, obviously. Was the reason i installed ubuntu studio a while back. 

After installing you gotta do a couple of things to tweak it, setting the rtprio and nice, allocating memory that sorta thing.

There are walkthroughs out there in the seven seas man, i think i wrote one a while ago, its not that majorly hard, just takes a wee bit of tatting is all.

Should be a couple guides on these forums somewhere if my memory serves...

I'll try and locate them for ya.........

---

### Post by Eiji Takanaka on 2012-03-30
This thread might be a start dude/ette...

[http://ubuntuforums.org/showthread.php?t=1055573&highlight=rt-kernel](http://ubuntuforums.org/showthread.php?t=1055573&highlight=rt-kernel)

---

