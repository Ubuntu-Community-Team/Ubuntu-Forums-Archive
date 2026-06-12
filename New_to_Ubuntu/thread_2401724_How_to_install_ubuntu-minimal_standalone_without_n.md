---
title: "How to install ubuntu-minimal standalone without network"
date: 2018-09-21
forum: New to Ubuntu
---

### Post by santerikannisto on 2018-09-21
I have downloaded mini.iso and it requires network to download packages. I also found instructions (outdated?) to download server iso use it for minimal, but the server required as well network connection. Is there anywhere a clean iso image with ubuntu-minimal containing only core packages? I am asking this to find a good starting point for having an unbloated starting point for making a distro.

Thanks for reading this and for your help.

Cheers,

Santeri

---

### Post by zhanglini on 2018-09-21
I did my mini install five months ago, all you need to do is downloading the regular image, and when you install, there is a place to select "minimal install" something.  It has been a while....

---

### Post by tea for one on 2018-09-22
> **santerikannisto said:**
> I have downloaded mini.iso and it requires network to download packages. I also found instructions (outdated?) to download server iso use it for minimal, but the server required as well network connection. Is there anywhere a clean iso image with ubuntu-minimal containing only core packages? I am asking this to find a good starting point for having an unbloated starting point for making a distro.

Thanks for reading this and for your help.

Cheers,

Santeri

Would this link be any help in your quest (although it is Xubuntu rather than Ubuntu)?

[https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

---

### Post by deadflowr on 2018-09-22
If building a custom distro it's easier to just download a normal (desktop) image of Ubuntu and 
1)break it apart
2) make the changes you want to make
3)rebuild it

This is what most do.

If you're going to modify it for public distribution then you must also remove any and all Ubuntu branding
[https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy]("https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy")

---

### Post by santerikannisto on 2018-09-24
> **zhanglini said:**
> I did my mini install five months ago, all you need to do is downloading the regular image, and when you install, there is a place to select "minimal install" something. It has been a while....

Thanks for the tip. I tried it earlier with no luck.

> **tea for one said:**
> Would this link be any help in your quest (although it is Xubuntu rather than Ubuntu)?

[https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

Excellent! Exactly what I was looking for. I am downloading the ISO now.

> **deadflowr said:**
> If building a custom distro it's easier to just download a normal (desktop) image of Ubuntu and 
1) break it apart
2) make the changes you want to make
3) rebuild it

This is what most do.

If you're going to modify it for public distribution then you must also remove any and all Ubuntu branding
[https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy](https://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy)

I was considering that but then I discovered that GNU/Linux distributions for desktop are stil suffering from the same they did 15 years ago: full of overlapping and partly crappy software. Trying to provide everything for everyone simply does not work. 

Removing all ubuntu branding can be quite painfull as there are plenty of ubuntu words for example in the installer which all the ubuntu forks I tested have failed to replace. And even the ubuntu derivates tell in grub they are all ubuntu which is kind of confusing. After installing 5 different variants it was very hard to figure which Grub "ubuntu" was which.

---

### Post by santerikannisto on 2018-09-24
> **tea for one said:**
> [https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)

I tested the xubuntu core and here are the results.

Installation test: xubuntu-18.04-core-amd64.iso on 21.11.2018

Overall, this is an excellent starting point for making a custom xubuntu without the usual bloatware. Good job!

Here are a few bugs/features/observations:

[LIST]
[*]When installing the iso if the last partition is logical and it is resized to fit the install, the installation crashes: ubi-partman exit code 10.
[*]Selecting web browser from menu opens dialog offering Debian Sensible browser, which does not exist in the system.
[*]Changing settings in settings/workspaces has no effect to the default GUI.
[*]Settings/Keyboard has many Application shortcuts to applications that has not been installed (eg. Libre Office).
[/LIST]
Stripping out plymouth and replacing it with a blank screen during the boot would make the core even smaller. Who needs animations when they slow down and bloat the system :P Also, a recompiled kernel without debug data should save disk space as well as speed up the system. I was hoping to pass on this for the developers but unfortunately they shared only their IRC contact info at their website (I used IRC last time in 1992 and that was enough for me).

---

