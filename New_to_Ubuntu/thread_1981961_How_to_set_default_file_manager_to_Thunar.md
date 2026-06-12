---
title: "How to set default file manager to Thunar?"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-17
Hi,

I have created a LIVE-CD of latest Lubuntu 12.04, but its a bit slow on my old laptop.  I can see that the PcManFM comes by default, which looks great, but its too slow for my old laptop.

How can I replace it with Thunar?

thanks

---

### Post by kc1di on 2012-05-17
> **Houmie said:**
> Hi,

I have created a LIVE-CD of latest Lubuntu 12.04, but its a bit slow on my old laptop.  I can see that the PcManFM comes by default, which looks great, but its too slow for my old laptop.

How can I replace it with Thunar?

thanks
what version did you download?  LXDE?

PcManFm is acutully lighter than Thunar. and should actually be faster than it. 

There is no easy way to disengage PcManFm from lxde. but you can install Thunar if you wish. 

however if you still want to try here are a couple pages that will be of help. 

[http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how]("http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how")

[http://forums.debian.net/viewtopic.php?f=30&t=48235]("http://forums.debian.net/viewtopic.php?f=30&t=48235")

---

### Post by Houmie on 2012-05-17
> **kc1di said:**
> what version did you download?  LXDE?

PcManFm is acutully lighter than Thunar. and should actually be faster than it. 

There is no easy way to disengage PcManFm from lxde. but you can install Thunar if you wish. 

however if you still want to try here are a couple pages that will be of help. 

[[URL="http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how"]http://forums.debian.net/viewtopic.php?f=30&t=48235]("http://forums.debian.net/viewtopic.php?f=30&t=48235")[/URL]

Thanks for your help.

I have downloaded this version:

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso)

Is there also a pure laptop version? Its written Desktop, but not sure if there is also a netbook/laptop version.


Thanks,

---

### Post by kc1di on 2012-05-17
there is no longer a netbook /laptop version everything that was in them in the past is now in the desktop version. 

Lubuntu is about the lightest spin of ubuntu there is.

---

### Post by kc1di on 2012-05-17
> **Houmie said:**
> Hi,

I have created a LIVE-CD of latest Lubuntu 12.04, but its a bit slow on my old laptop.  I can see that the PcManFM comes by default, which looks great, but its too slow for my old laptop.

How can I replace it with Thunar?

thanks

could you give us some detail about your laptop. how old how much ram processor etc. that may help us give you better information on other possibilities.

---

### Post by Houmie on 2012-05-18
> **kc1di said:**
> could you give us some detail about your laptop. how old how much ram processor etc. that may help us give you better information on other possibilities.

Thanks, I have figured out what the problem is. It wasn't the performance as such. It is a lagging bug in AbiWord, confirmed here:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/988485](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/988485)

I have now installed LibreOffice and it flies.  I am so surprised they have classified this bug only as Medium.  It should be a blocker, who would use AbiWord in this state?


Laptop is from 2004, Dell inspirion 8600, 4GB RAM. :)

---

### Post by kc1di on 2012-05-18
> **Houmie said:**
> Thanks, I have figured out what the problem is. It wasn't the performance as such. It is a lagging bug in AbiWord, confirmed here:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/988485](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/988485)

I have now installed LibreOffice and it flies.  I am so surprised they have classified this bug only as Medium.  It should be a blocker, who would use AbiWord in this state?


Laptop is from 2004, Dell inspirion 8600, 4GB RAM. :)
Glad you got it going Lubuntu should work well on that hardware :) 
enjoy!

---

