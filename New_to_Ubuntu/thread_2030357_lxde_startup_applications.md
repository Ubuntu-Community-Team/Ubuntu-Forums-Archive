---
title: "lxde startup applications"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by degarb on 2012-07-20
I am trying out lxde to see if I can make it useful.  Everything seems snappier than with gnome classic no effects.   Forget about default ubuntu, which I don't think will run at all.

I got webilder (a must have application and a deal breaker for me) to work. 

Now, I cannot figure out how to add a startup application to lxde.   

So far, I got lxdesession-edit to run, but none of the junk I wish to add to startup is there.   Then there is a garbled bit of text over on wiki, [http://wiki.lxde.org/en/LXSession#Automatically_start_some_applications_on_login](http://wiki.lxde.org/en/LXSession#Automatically_start_some_applications_on_login)

I do not understand those instructions.  First off what is ~/directory?  And how would this relate to gnome v. lxde?  

Need help.

---

### Post by degarb on 2012-07-20
I have also played with home/autostart adding lines of gedit and copying shortcuts to it. Setting permissions.  No luck.
  
Another hour wasted.

---

### Post by sersang on 2012-07-20
~/ means your home directory. So you should create an empty file in your /home/.config/ and name it autostart.

~/.config/autostart means /home/.config/autostart :)

---

### Post by NikTh on 2012-07-20
Hi ,
check this out : [**[COLOR=Navy]Lubuntu[/COLOR]**-One Stop Thread](http://ubuntuforums.org/showthread.php?t=1844755) , start reading and you will learn much about . 
Thanks

---

### Post by degarb on 2012-07-20
> **sersang said:**
> ~/ means your home directory. So you should create an empty file in your /home/.config/ and name it autostart.

~/.config/autostart means /home/.config/autostart :)

I think you mean a folder, not a file called autostart.

Got one.  Nothing I add there will launch anything in lxde.   Stumped still and [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755) is just hours of reading with no applicable info.

I have tried making executable three line files to launch wbar, single line scripts, shortcuts, even copying the exe from usr/bin to that folder.  Nothing.

I need lxterminal, wbar, and webilder to run at start.   Mainly lxterminal since it refuses to launch as a shortcut in the taskbar.  Future needs require I master this before proceeding with lxde.

LXDE is using 200 k less ram than Unity classic , no effects.   Mainly peppier. LXDE needs a little polish --webilder, vertical shortcut list on taskbar, a startup list gui.  But it is close to ideal, just short; yet painfully, possibly unusable if the aforementioned things aren't figured out.

---

### Post by NikTh on 2012-07-21
> **degarb said:**
> 
Got one. Nothing I add there will launch anything in lxde. Stumped still and [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755) is just hours of reading with no applicable info.
Hi,
Reading this excelent Thread or this Wiki --> [https://wiki.ubuntu.com/Lubuntu/](https://wiki.ubuntu.com/Lubuntu/) (i think its the same , but wiki its easiest to read) you will learn many things about your Desktop Environment.



> **degarb said:**
> I need lxterminal, wbar, and webilder to run at start..
For lxterminal:
Open lxterminal and copy-paste this command
```
echo '@lxterminal' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart
```Logout and login to see lxterminal starts immediately, when login in.
Thanks

---

### Post by degarb on 2012-07-21
> **NikTh said:**
> 

For lxterminal:
Open lxterminal and copy-paste this command
```
echo '@lxterminal' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart
```Logout and login to see lxterminal starts immediately, when login in.
Thanks


Thanks. The info I needed. 

But..I am trying to make a desktop script that allows me to text add--filling the void of something we can weekly manage with ease, where the gui of lxde has fallen down. 

No luck there. I can open root nautilus and edit. But a pita. So, making an executable file with your command (or with gedit instead of tee), is not working.   Also no luck with simply, sudo gedit /etc/xdg/lxsession/lxde/autostart  doesn't work (I am lxde on top of ubuntu).

---

