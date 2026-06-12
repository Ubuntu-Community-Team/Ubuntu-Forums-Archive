---
title: "Desktop options"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by Liliths slave on 2012-03-10
I've just installed Ubuntu 11.10 and I don't much like the big clumsy buttons on the left.  I'm sure I've seen older versions without them - just two thin taskbars with "Applications" and Places" at the top.  is there any way of getting a desktop like this?

---

### Post by disabled20191128 on 2012-03-10
at the login screen go down and select classic gnome desktop instead of unity desktop

---

### Post by raja.genupula on 2012-03-10
yeah but for that you have to install gnome3 .after installing that you can choose Gnome classic from login screen .

I have got a useful link for you
[http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/](http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/)

---

### Post by winh8r on 2012-03-10
have a look here :

[http://ubuntuforums.org/showthread.php?t=1859960]("http://ubuntuforums.org/showthread.php?t=1859960")


or look at 


[http://mate-desktop.org/]("http://mate-desktop.org/")


for a more functional classic feel

hope this helps

---

### Post by Liliths slave on 2012-03-10
Mate looks too much like Windows - thanks anyway.  I'll install Gnome 3 and try it out.  Thanks to all.

---

### Post by raja.genupula on 2012-03-10
after installing that if you got anything please let us know else please mark the thread as solved from thread tools. 

Thank you .

---

### Post by Liliths slave on 2012-03-10
I'm having trouble getting gnome.  When I try it shows an installation screen, but it can't install it as I'm using Windows on the net because Ubuntu doesn't recognise my dongle.  I'll have to download the ISO whenever I can get on my mate's computer.  (my PAYG dongle is too expensive to wait for long downloads.)

---

### Post by raja.genupula on 2012-03-10
what internet modem it was ?

---

### Post by Liliths slave on 2012-03-10
Its a Vodafone dongle.  I don't know any technical details.  If there's anything specific you need to know, let me know how to find it.

---

### Post by JOHNNYG713 on 2012-03-10
I would not recommend mate as it takes over the system, install gnome fallback session, in synaptic, its not the same as gnome 2 but it is as close as your going to get without installing Lucid lts ! [http://ultimateedition.info/ultimate-edition/ultimate-edition-2-6/](http://ultimateedition.info/ultimate-edition/ultimate-edition-2-6/)< I highly recommend for those who dislike the unity DE ! they (Canonical) have extended the support period, I think they know how bugie Precise is and is going to be !!! Also TheeMahn, The developer of Ultimate Edition is about to unleash a new version (3.2) of Ultimate Edition that has fallback as default, and has added many improvements, and bug squashes!!  good luck to you !

---

### Post by Liliths slave on 2012-03-10
Ultimate Edition looks cool.  I'm on my mate's computer Monday, so I'll download it then and try it.  I'll let you know how I get on.  Thanks a lot.

---

### Post by raja.genupula on 2012-03-10
> **Liliths slave said:**
> Its a Vodafone dongle.  I don't know any technical details.  If there's anything specific you need to know, let me know how to find it.

do you know whats your APN ? 
whats the model of Modem ? 
post the output of **lsusb**

---

### Post by Liliths slave on 2012-03-10
The model is K3770.  Its made by Huawei.  This is all in tiny writing so I'm not sure if I'm reporting it right.  The rest is too technical for me.

---

### Post by raja.genupula on 2012-03-10
I have got a link for you with lot of working methods 
[http://ubuntuforums.org/showthread.php?t=1790375](http://ubuntuforums.org/showthread.php?t=1790375)

try that once .all the best .

---

### Post by Liliths slave on 2012-03-10
Thanks for the link.  I'm trying Sakis3G which is a script.  Do I have to copy this into a terminal or is there an easier way?

---

### Post by Liliths slave on 2012-03-10
Never mind.  I'm fed up of looking for simple to install software packages and finding lists of code that I don't know what to do with.  If I find a deb package and try to install it I find there are lib dependencies and it's all too much hassle!  All the Open Source software I want is available for windows anyway.  Linux is designed for intellectuals.  For the average user who just wants to install software and use it. linux is completely pointless!!!  Somebody else will have to mark this thread as solved because I don't know how to - this site is almost as user-unfriendly as Ubuntu!

---

### Post by raja.genupula on 2012-03-10
```
wget "http://www.sakis3g.org/versions/latest/i386/sakis3g.gz"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive
```

copy that in terminal .

---

### Post by raja.genupula on 2012-03-10
> **Liliths slave said:**
> Never mind.  I'm fed up of looking for simple to install software packages and finding lists of code that I don't know what to do with.  If I find a deb package and try to install it I find there are lib dependencies and it's all too much hassle!  All the Open Source software I want is available for windows anyway.  Linux is designed for intellectuals.  For the average user who just wants to install software and use it. linux is completely pointless!!!  Somebody else will have to mark this thread as solved because I don't know how to - this site is almost as user-unfriendly as Ubuntu!

Hi My dear friend , what makes you think like that . we are trying to give our best to you . 

if you look at the web page of that particular software i have given to you , after download there is instructions option as well . they have designed that thing by keeping basic users. may be you miss it my friend . i am saying again ...we will give you our best . 

come on friend . I am sure that gonna help you . 
If not then report us what you got .

All the best .

---

### Post by Liliths slave on 2012-03-12
I looked at the code you posted.  The problem is, the whole reason I need Sakis3D is because I can't get on the net, so what is the point of the wget command?  My point about Linux is not just about this, but about the whole system.  Why do I have to learn a new language to install software and what are these dependencies about?  If I install Gimp in Windows, GTK is included.  If I install Blender or Inkscape in Windows, everything is included.  I don't need a degree in coding, I just double-click the EXE file and it installs.  Linux developers seem to be very cynical about simple folk like myself!  I would love to love Linux because I hate Microsoft but I'm sorry, it's just too much hassle.  Thanks for trying anyway.

---

### Post by Liliths slave on 2012-03-12
Thanks.

---

### Post by 3rdalbum on 2012-03-12
> **Liliths slave said:**
>  Why do I have to learn a new language to install software and what are these dependencies about?

You don't. Just use Ubuntu Software Center.

Dependencies are handled automatically. It makes programs smaller to download and smaller on disk.

---

### Post by Liliths slave on 2012-03-12
Please please please read the thread - I CAN'T GET ON THE NET!

---

### Post by Liliths slave on 2012-03-12
Besides which, I doubt that USC covers all linux software.  For example, can you get Gnofract through USC?  How can it be smaller on disc if you have to install the dependencies anyway?  Gimp for windows doesn't take long to download, nor does Blender or Inkscape.

---

