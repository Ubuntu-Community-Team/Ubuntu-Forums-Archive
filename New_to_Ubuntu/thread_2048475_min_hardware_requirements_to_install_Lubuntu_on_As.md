---
title: "min hardware requirements to install Lubuntu on Asus eeePC 900A netbook 4gb sshd"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by Sudan on 2012-08-26
Hi, newbie here.

I have a 3.5 year old Asus eee PC 900a netbook, 4gb sshd, 1gb ram.

I downloaded Lubuntu file "lubuntu-12.04-desktop-i386.iso". Then used "unetbootin-windows-578.exe" to make the bootable USB stick.

I have successfully booted used Lubuntu 12.04 from a USB stick.  And even finally mananged to install skype.  

When I try to install Lubuntu a dialog box says I need a minimum 4.4gb drive space available.

Why?  In the reading about Lubuntu I read it said it was a very small os that should run on old netbooks.

If it can't be installed on my netbook can anyone recommend a different os to install.  I only want to use the netbook for skype, gtalk, gmail, browser, etc.

On the other hand, do I just need a different method to install Lubuntu 12.04?  Remember I'm a newbie :(

P.S. I chose Lubuntu over Xubuntu and Ubuntu, because I believe Lubuntu is smaller.  But if my problem is just from the installation method I'm using, then I would prefer to use Ubuntu or Xubuntu.  If they are supposed to able to run on my hardware.

---

### Post by newb85 on 2012-08-26
You should try PeppermintOS.  [http://peppermintos.com/](http://peppermintos.com/)

It's a fork of Lubuntu.  It isn't officially supported by Ubuntu or Canonical, but you'll find it's similar enough that the info on the Ubuntu forums will still apply in most cases.

According to their website, the absolute minimum is 2GB HD space, with 4GB recommended, which sounds much better suited for your system specs than Lubuntu's 4.4GB absolute minimum.

Disclaimer:  I have never installed Peppermint.  I have however, run it from a Live CD, and was very impressed with the experience.

You could download (from [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)) and create an alternative install disc for Lubuntu, and then do a custom install to require less HD space, but that will probably be a lot more involved, and you will have to leave some things uninstalled.

I recommend you not bother with Ubuntu or Xubuntu on this machine.  Even if you pare them down far enough to fit on your 4GB HD, your performance will suffer at 1GB RAM (which would be shared with your graphics card), and I think it will be a generally unsatisfying experience.

---

### Post by Sudan on 2012-08-26
> **newb85 said:**
> You should try PeppermintOS.  [http://peppermintos.com/](http://peppermintos.com/)

Thanks, I'm in the process of downloading it.  What about the os called " Ubuntu Netbook Remix" should I try it?

---

### Post by Naimar on 2012-08-26
peppermint will work just fine, tested it on several older systems.

---

### Post by Sudan on 2012-08-26
> **newb85 said:**
> You should try PeppermintOS.  [http://peppermintos.com/](http://peppermintos.com/)

I created an install USB mem stick.  I have the same problem.  The installer says a min free hd space of 4.4gb is needed.  My sshd is 4gb, with 135mb free.

After reading all about peppermint and how small it is.  I'm amazed the installer requires more space than the low end hardware requirements.

I'm baffaled.  Maybe it is just my installer that is bad.

---

### Post by Miljet on 2012-08-26
You might have a look at Puppy Linux. It is designed to be run from a Live CD (or USB pen drive.) It only requires enough drive space for a small file to track installed components. 

Otherwise, you can install Lubuntu onto a pen drive instead of your hard drive.

---

### Post by mastablasta on 2012-08-27
you can use mini.iso to install basic system and then add what you want/need.
 
for example you can then add only lxde (the DE Lubuntu uses) or the whole lubuntu desktop:
 
[https://help.ubuntu.com/community/Installation/MinimalCD/](https://help.ubuntu.com/community/Installation/MinimalCD/)
 
here is a how to for instalation: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
ice wm is also an option if you don't mind to look a bit dated :-)
 
otherwise JoliOS (but i am not sure if you need to pay for it or not-it seems you need to register though) was designed with these small netbooks in mind. [http://www.jolicloud.com/jolios](http://www.jolicloud.com/jolios)
 
another good option is Bodhi linux (Ubuntu based and uses e17 desktop). it is also very small and light. [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

