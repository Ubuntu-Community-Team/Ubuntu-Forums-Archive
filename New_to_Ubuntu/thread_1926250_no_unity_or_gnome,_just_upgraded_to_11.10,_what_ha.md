---
title: "no unity or gnome, just upgraded to 11.10, what happened???"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by shemdroid on 2012-02-15
ok i just upgraded to 11.10, i have done nothing but reboot. 
 the login screen is correct, and i log right on however, when the desktop loads all i have is the three icons that have been on my desktop (just a couple .deb packages and a the android sdk launcher), and at the top of the screen where it would say activities, places, system in gnome 2 (i realize that this is not what would be there in 11.10 to begin with but just for the sake of giving a good depiction) it says file, edit, view etc. just like as if it was an application open. 
 i dont get it at all, i dont have access to anything except the files in the filesystem. i dont know how to access the terminal or any other apps cept the android-sdk. HELP lol

---

### Post by wildmanne39 on 2012-02-16
Hi, move your mouse all the way to the left of the screen and the launcher pops out, that has applications and the terminal and many more icons on it.
Thanks

---

### Post by shemdroid on 2012-02-16
yea I am afraid the solution is apparently not quit so easy.   I wish!   
I'm looking at it now. there is file, edit, view, go, bookmarks, help.  there are no other menus, options, icons, or otherwise. period!  like I said, I don't get it.

save for the three icons I had previously mentioned.

---

### Post by wildmanne39 on 2012-02-16
Hi, if you hit the windows key does the launcher on the left of the screen come out?
thanks

---

### Post by jasonrisenburg on 2012-02-16
yes the super user key does do winders but there is 4 tabs at the bottom to. or install the classic menu ppa, and it will make it fel more like old gnome for you. Its what I use.
[http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray](http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray)

---

### Post by shemdroid on 2012-02-16
no the windows key doesn't do anything.  
>  yes the super user key does do winders but there is 4 tabs at the bottom to. or
install the classic menu ppa, and it will make it feel more like old gnome for you.
Its what I use. 

I don't think I'm explaining this right.......   unity is not there. neither is gnome 2 or 3, nor xfce, nor lxde, nor open box!  I have no desktop environment. its as if my Linux opened up as (in the form of) an application rather than an desktop environment where I am able to browse apps and just do the normal stuff you do on the computer. 
all I am able to access is the file system, as in I am able to browse the folders and files.  its really weird!!!

---

### Post by shemdroid on 2012-02-16
I'm actually rather fond of unity, I like that j can just type the first letter of an app and POW, there is every app that starts with the letter "f" f.e.

---

### Post by linux6994 on 2012-02-16
I would suggest trying the Alt-F2 and getting to a command prompt then ensuring  that all of the packages are there.

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install gnome-desktop

then do a ctrl backspace to logout and see if it will give you a session?

---

### Post by shemdroid on 2012-02-16
> **linux6994 said:**
> I would suggest trying the Alt-F2 and getting to a command prompt then ensuring  that all of the packages are there.

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install gnome-desktop

then do a ctrl backspace to logout and see if it will give you a session?

k than I'll try that after work and let you know what happens ;)

---

### Post by forrestcupp on 2012-02-16
Also, maybe your computer won't support Unity and you may need to try Unity2D. Since your login screen works, try clicking on the gear icon by your user name, and choose Unity2D. Then try logging on and see what happens.

---

### Post by shemdroid on 2012-02-16
yea I've tried 2d in both the newer kernel and the previous

---

### Post by shemdroid on 2012-02-16
> **linux6994 said:**
> I would suggest trying the Alt-F2 and getting to a command prompt then ensuring  that all of the packages are there.

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install gnome-desktop

then do a ctrl backspace to logout and see if it will give you a session?

OK so I did that and I now have gnome but its kinda weird.  
first it only has activities and places on the task bar and the system options are integrated into that. but what's really weird is that grub has a graphical thing. a planet and it says " debian, the universal operating system.  I realize that Ubuntu is a derivative of debian but I'm pretty sure that shouldn't be my grub. 
any who, more importantly, how do I get unity back or at least gnome3

---

### Post by Scott Baker on 2012-02-16
A couple of thoughts here. First, were you doing your upgrade through a wired or wireless connection? I've watched some people frag their upgrade by trying to do it wirelessly. It sounds as if you'd do better if you started fresh. You probably don't want to spend a lot of time messing with trying to repair this issue. If you can, get a fresh copy of the distro of choice (some swear by the 10.04 LTS, others, it doesn't seem to matter a whole lot). Use that copy to boot your system (thumb/flash drives seem to be faster, but CD/DVD also will work). Once booted up, back up whatever you need from the original installation. Once done, reboot your machine, and when you get to the choice screen ( try or install ) hit install instead of try (it seems to install faster this way) then sit back, enjoy a cold brew or a hot cider, and let the install work its magic. And don't forget, if possible, stay with wired connections when doing upgrades. Good luck, and keep us up to date please.  [-o<

---

### Post by shemdroid on 2012-02-16
> **Scott Baker said:**
> A couple of thoughts here. First, were you doing your upgrade through a wired or wireless connection? I've watched some people frag their upgrade by trying to do it wirelessly. It sounds as if you'd do better if you started fresh. You probably don't want to spend a lot of time messing with trying to repair this issue. If you can, get a fresh copy of the distro of choice (some swear by the 10.04 LTS, others, it doesn't seem to matter a whole lot). Use that copy to boot your system (thumb/flash drives seem to be faster, but CD/DVD also will work). Once booted up, back up whatever you need from the original installation. Once done, reboot your machine, and when you get to the choice screen ( try or install ) hit install instead of try (it seems to install faster this way) then sit back, enjoy a cold brew or a hot cider, and let the install work its magic. And don't forget, if possible, stay with wired connections when doing upgrades. Good luck, and keep us up to date please.  [-o<

well the fix was to login to the guest account,  logout and log back into my account and all was well,  I have unity.  
when I do have to reinstall I also use 10.04.3 lts, its actually the only version that will install properly on my machine.  I have a fairly new Toshiba satellite laptop and getting everything working on it is a nightmare. so I'm just gonna hope all is well and not worry about grub for now as it does appear to be functioning properly. lol.  anyway than for your help :)     oh and yeabi think i was using wireless

---

### Post by jasonrisenburg on 2012-02-23
> **shemdroid said:**
> no the windows key doesn't do anything.  


I don't think I'm explaining this right.......   unity is not there. neither is gnome 2 or 3, nor xfce, nor lxde, nor open box!  I have no desktop environment. its as if my Linux opened up as (in the form of) an application rather than an desktop environment where I am able to browse apps and just do the normal stuff you do on the computer. 
all I am able to access is the file system, as in I am able to browse the folders and files.  its really weird!!!

Here is a link to 31 uses of the super user + (whatever key you press)

[http://www.techdrivein.com/2011/04/31-useful-ubuntu-1104-unity.html](http://www.techdrivein.com/2011/04/31-useful-ubuntu-1104-unity.html)

---

