---
title: "Another &quot;old PC&quot; thread, but this one is for a 4 year old!"
date: 2008-07-29
forum: Other OS Talk
---

### Post by timzak on 2008-07-29
I have an old PC that I set up for my 4 year old for basic email to and from family, Tux Paint, and a couple of other children's games (Gcompris and Childsplay suites).  It currently have Xubuntu 7.04, which uses 64MB of ram.  However, security updates will be ending soon for 7.04 and I'd like to get a more up-to-date OS on here.  The specs are:
Celeron 466 Mhz
256 MB ram
Intel i810 video
15 GB hard drive
Sound Blaster Live!

I tried Xubuntu 8.04 recently on another system and could not get memory usage below 100 MB, so I think it may be too heavy for this system.

The way I have the system set up now is a basic panel at the bottom with a really big launcher icons.  He's too young to navigate menus, so the apps need to be "shortcut-able" as desktop icons or panel launchers.  Keep this in mind when making recommendations.

I'd prefer an Ubuntu derivative or as Ubuntu-like as possible so that it will be easy for me to set up.  IceBuntu comes to mind, but I don't know if it can be set up with launcher icons or how easy it would be to do.

One other thing, it needs to be easy to shutdown.  I.e, shutdown icon that actually turns the computer off--not logs out and expects further actions from the logout window.  

I think a Debian base install with xfce might work great, but I'm not sure what all I need to install to get the system set up the way I propose above.  I don't want to be fiddling with this for days or weeks before he can use it again.

Seems a children's distro is in order, eh?

---

### Post by pkl266 on 2008-07-29
Have you tried or looked into edubuntu? [http://www.edubuntu.org/](http://www.edubuntu.org/)

As for upgrading, IMHO if it's not broken don't fix it. If 7.04 is working out just fine, I don't think there is too much of a reason to upgrade.

---

### Post by LaRoza on 2008-07-29
Any distro will work it seems. The only thing is you need to set it up.

You can drag and drop any icon onto the desktop or panel (or dock, if you have one).

For a light OS, you can try debian, but you'll have to set it up of course. It works like Ubuntu, but is much lighter.

---

### Post by timzak on 2008-07-29
> **pkl266 said:**
> Have you tried or looked into edubuntu? [http://www.edubuntu.org/](http://www.edubuntu.org/)

As for upgrading, IMHO if it's not broken don't fix it. If 7.04 is working out just fine, I don't think there is too much of a reason to upgrade.

It appears to have high system requirements and the interface is not modified at all for little ones with developing hand-eye coordination.  But I do like many of the applications that it installs.  Thank you for the link.

My concern with the current set up is that security updates will be ending soon, and packages are a little out-of-date as it stands.  I'd like access to newer package versions and security updates for the next year or so.  

Does anyone know if IceWM can be made with large icons or launchers that are easy for a 4-year-old to click?

---

### Post by timzak on 2008-07-29
> **LaRoza said:**
> Any distro will work it seems. The only thing is you need to set it up.

You can drag and drop any icon onto the desktop or panel (or dock, if you have one).

Which DE are you referring to?  I didn't think most lightweight WMs/DEs allowed this.

> For a light OS, you can try debian, but you'll have to set it up of course. It works like Ubuntu, but is much lighter.

I've done this before, but I'm never sure what underlying packages need to be installed for things like security, sound, printing, etc.  In Ubuntu it's easy to disable services and auto-started apps, but I've never figured out how to do this in Debian.  Can you (or anyone reading) give any pointers, or provide links that might help?

---

### Post by cardinals_fan on 2008-07-29
Arch + Xfce?

---

### Post by K.Mandla on 2008-07-30
I was going to say, if you try a minimal Ubuntu system and add XFCE to it, it will be pretty close to the Xubuntu layout you're used to. Add Synaptic and you're basically running the same environment as Xubuntu, without all the bloat they added. It's incredibly lighter and faster.

---

### Post by LaRoza on 2008-07-30
> **timzak said:**
> Which DE are you referring to?  I didn't think most lightweight WMs/DEs allowed this.
GNOME and KDE in this case. Debian with GNOME or KDE is much faster and lighter than Ubuntu with either.

> 
I've done this before, but I'm never sure what underlying packages need to be installed for things like security, sound, printing, etc.  In Ubuntu it's easy to disable services and auto-started apps, but I've never figured out how to do this in Debian.  Can you (or anyone reading) give any pointers, or provide links that might help?

Debian will allow you to configure that. Debian has less services to disable, and at the lightest, is just a base system so you can install packages individually.

---

### Post by kagashe on 2008-07-30
> **timzak said:**
> I've done this before, but I'm never sure what underlying packages need to be installed for things like security, sound, printing, etc.  In Ubuntu it's easy to disable services and auto-started apps, but I've never figured out how to do this in Debian.  Can you (or anyone reading) give any pointers, or provide links that might help?
I just had a look at cd images available for Debian Lenny on [this page]("http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/"). There is [XFCE cd image]("http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-xfce-CD-1.iso") which should install XFCE desktop.

kagashe

---

### Post by timzak on 2008-07-30
> **K.Mandla said:**
> I was going to say, if you try a minimal Ubuntu system and add XFCE to it, it will be pretty close to the Xubuntu layout you're used to. Add Synaptic and you're basically running the same environment as Xubuntu, without all the bloat they added. It's incredibly lighter and faster.

Thanks.  I read recently on here that building up from a Debian base is actually easier than an Ubuntu base because Debian updates the menu as you install apps, but Ubuntu doesn't?  That doesn't sound right, and I can't find the post right now that I read that from.  I think the poster was talking about Ubuntu base + XFCE will not auto-update the menu entries, whereas Ubuntu base + Xubuntu meta package will.

---

### Post by timzak on 2008-07-30
Thanks everyone.  I have a tentative plan.  I found a spare 20GB hard drive, so what I will do is leave the hard drive currently in the system alone, thus preserving the current 7.04 install.  Then as I have time, I'll swap drives out and start building a Debian base + XFCE install on the new drive.  When I'm done for the night, swap the drives back and the system is usable again with the original OS.  This will let me take my time setting Debian up right, and keep the original config for my son to play with in the meantime.

I'll come back with Debian questions as they come up.

Thanks again.

---

### Post by kagashe on 2008-07-31
> **timzak said:**
> Thanks everyone.  I have a tentative plan.  I found a spare 20GB hard drive, so what I will do is leave the hard drive currently in the system alone, thus preserving the current 7.04 install.  Then as I have time, I'll swap drives out and start building a Debian base + XFCE install on the new drive.  When I'm done for the night, swap the drives back and the system is usable again with the original OS.  This will let me take my time setting Debian up right, and keep the original config for my son to play with in the meantime.

I'll come back with Debian questions as they come up.

Thanks again.[This thread]("http://forums.debian.net/viewtopic.php?t=26566") on Debian Forum may help.

kagashe

---

### Post by K.Mandla on 2008-07-31
> **timzak said:**
> Thanks.  I read recently on here that building up from a Debian base is actually easier than an Ubuntu base because Debian updates the menu as you install apps, but Ubuntu doesn't?  That doesn't sound right, and I can't find the post right now that I read that from.  I think the poster was talking about Ubuntu base + XFCE will not auto-update the menu entries, whereas Ubuntu base + Xubuntu meta package will.
That strikes me as odd too. I think pure XFCE should automatically update its menus, since I believe it uses the same application information folder/system as Gnome, and the Ubuntu packages should dump entries for applications there, so long as the source program includes it (and maybe if it doesn't too).

That being said I know that there are some programs that don't add themselves to that system, and so are probably left out. Perhaps that's what they were talking about.

---

### Post by VitaLiNux on 2008-08-01
> **timzak said:**
> I have an old PC that I set up for my 4 year old for basic email to and from family, Tux Paint, and a couple of other children's games (Gcompris and Childsplay suites).  It currently have Xubuntu 7.04, which uses 64MB of ram.  However, security updates will be ending soon for 7.04 and I'd like to get a more up-to-date OS on here.  The specs are:
Celeron 466 Mhz
256 MB ram
Intel i810 video
15 GB hard drive
Sound Blaster Live!

I tried Xubuntu 8.04 recently on another system and could not get memory usage below 100 MB, so I think it may be too heavy for this system.

The way I have the system set up now is a basic panel at the bottom with a really big launcher icons.  He's too young to navigate menus, so the apps need to be "shortcut-able" as desktop icons or panel launchers.  Keep this in mind when making recommendations.

I'd prefer an Ubuntu derivative or as Ubuntu-like as possible so that it will be easy for me to set up.  IceBuntu comes to mind, but I don't know if it can be set up with launcher icons or how easy it would be to do.

One other thing, it needs to be easy to shutdown.  I.e, shutdown icon that actually turns the computer off--not logs out and expects further actions from the logout window.  

I think a Debian base install with xfce might work great, but I'm not sure what all I need to install to get the system set up the way I propose above.  I don't want to be fiddling with this for days or weeks before he can use it again.

Seems a children's distro is in order, eh?
Have you tried PCLinuxOS TinyMe? Just one word to describe it: AMAZING! It runs even on 64 mb with all the out-of-the-box eyecandy (I was using it through a virtual machine to which I put 64mb of ram after I read your first post to see its performance. I opened the Opera browser and posted this answer with it and everything was good!!!) You can install programs using synaptic. I have to tell you, this is one of the easiest Linux distro I have ever seen! You can make almost every configuration through GUI or editing config files as well. Give it a try and you will not regret it! Edit: This is very, very, very easy, so try it out. Even a person who has never used a pc should do ok with PCLinuxOS TinyMe:guitar:

---

### Post by VitaLiNux on 2008-08-01
timzak, if you need further help, do not hesitate to PM me or through this thread :)

---

### Post by Hallvor on 2008-08-02
> **VitaLiNux said:**
> Have you tried PCLinuxOS TinyMe? Just one word to describe it: AMAZING! It runs even on 64 mb with all the out-of-the-box eyecandy (I was using it through a virtual machine to which I put 64mb of ram after I read your first post to see its performance. I opened the Opera browser and posted this answer with it and everything was good!!!) You can install programs using synaptic. I have to tell you, this is one of the easiest Linux distro I have ever seen! You can make almost every configuration through GUI or editing config files as well. Give it a try and you will not regret it! Edit: This is very, very, very easy, so try it out. Even a person who has never used a pc should do ok with PCLinuxOS TinyMe:guitar:

+1. TinyMe is great. It has a PCLinuxOS base with Openbox on top, so it is also a rolling release. Install what you want, and the system can get upgrades and run for years. Don`t let Openbox scare you, since the version  in TinyMe has a GUI for (almost) everything.

[http://tinyme.mypclinuxos.com/wiki/doku.php?id=screenshots:2008.0:home](http://tinyme.mypclinuxos.com/wiki/doku.php?id=screenshots:2008.0:home)

---

### Post by timzak on 2008-08-02
Thanks to everyone for their help and tips.  I've got Debian Etch installed via netinstall, with XFCE and the handful of apps I need.  So far, so good.  It's still slow (it's the Intel 810 video, which is notoriously slow), but it fits the bill.  It uses about 54 MB of ram at startup, compared to 64 MB for Xubuntu 7.04.

I wish I tried TinyMe before I did this install, but I've already invested a lot of time in this install and it's working, so I'm going to leave it for now.

Thanks again.

---

### Post by kagashe on 2008-08-02
> **timzak said:**
> It's still slow (it's the Intel 810 video, which is notoriously slow), but it fits the bill. 
The old driver for your card was i810 and the new driver is intel. I think both are available in Debian Etch. You can edit /etc/xorg.conf and if the driver under device section is "i810" replace it by "intel".

This is assuming you have installed the latest version of Debian etch. 

kagashe

---

### Post by timzak on 2008-08-03
> **kagashe said:**
> The old driver for your card was i810 and the new driver is intel. I think both are available in Debian Etch. You can edit /etc/xorg.conf and if the driver under device section is "i810" replace it by "intel".

This is assuming you have installed the latest version of Debian etch. 

kagashe

How do I know I have the "intel" driver as an option?  I know if it's not there, I will need to restore a backup of xorg.conf from the command line.  I can do it, but it's uncomfortable territory for me.

I installed Etch from a brand new download of the .iso a couple of days ago.  Not etchnhalf, just etch.  Synaptic has not told me there are any available upgrades, so I must have downloaded the latest version.  

Thanks.

---

### Post by timzak on 2008-08-03
Another question on this same install:  When I hit the Quit button to shut down the system, Shutdown and Restart are greyed out--my only option is to log out.  I must then shutdown from within gdm.

I know Xubuntu allows a full shutdown from the desktop, so how can I accomplish this?

Thank you.

---

### Post by kagashe on 2008-08-03
> **timzak said:**
> How do I know I have the "intel" driver as an option?  I know if it's not there, I will need to restore a backup of xorg.conf from the command line.  I can do it, but it's uncomfortable territory for me.

I installed Etch from a brand new download of the .iso a couple of days ago.  Not etchnhalf, just etch.  Synaptic has not told me there are any available upgrades, so I must have downloaded the latest version.  

Thanks.It is good that you have installed Synaptic. Let us find out whether you have intel driver using it. Start Synaptic and click on Search button and enter the following in the box:
> xserver-xorg-video-intel
Select and install the driver if not already installed. Now you should be more comfortable backing up the xorg.conf file changing the driver from "i810" to "intel".

If you don't find the driver try apt-get update and apt-get upgrade and see whether the file "xserver-xorg-video-intel" is shown anywhere.

kagashe

---

### Post by kagashe on 2008-08-03
> **timzak said:**
> Another question on this same install:  When I hit the Quit button to shut down the system, Shutdown and Restart are greyed out--my only option is to log out.  I must then shutdown from within gdm.

I know Xubuntu allows a full shutdown from the desktop, so how can I accomplish this?

Thank you.I am sorry I don't use xfce on Debian. You can try searching [Debian Forum]("http://forums.debian.net/") or asking there. You may also ask on Debian folder in Other OS Talk on this forum.

kagashe

---

### Post by timzak on 2008-08-03
> **kagashe said:**
> It is good that you have installed Synaptic. Let us find out whether you have intel driver using it. Start Synaptic and click on Search button and enter the following in the box:
Select and install the driver if not already installed. Now you should be more comfortable backing up the xorg.conf file changing the driver from "i810" to "intel".

If you don't find the driver try apt-get update and apt-get upgrade and see whether the file "xserver-xorg-video-intel" is shown anywhere.

kagashe

Thanks, all worked as you explained.  I appreciate your help. :)

---

### Post by timzak on 2008-08-04
In case anyone else needs this, I've found a solution to allowing restarts and shutdowns from the desktop.

Edit the following file as root (I'm using mousepad, you use your favorite):

```
mousepad /etc/sudoers
```

And insert the following lines:

```
Defaults	!lecture,tty_tickets,!fqdn
``` (comment out any other Defaults line)

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

and 
```
YOUR_USER_NAME ALL= NOPASSWD:/usr/sbin/xfsm-shutdown-helper
``` (replace YOUR_USER_NAME with your actual username)

That fixed it for me.

---

