---
title: "Drag &amp; Drop Sudo"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by gavv on 2012-08-08
Hi everyone, I'm an absolute beginner with Ubuntu and Linux in general. I'm having trouble with a simple command that can be found in [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

I'm attempting to execute, 
```
gksudo "gnome-open %u"
```but I can't seem to get it to work.

I found out that 'gnome-open' was not installed, so I simply installed libgnome2-0, but after having it installed and running the command again, I'm still not seeing this launcher which lets files be opened as Root with its own associated application.

---

### Post by deadflowr on 2012-08-08
Open up a terminal and run: 
```
man gnome-open
```
It'll give you a rundown of how to get it to work. q to quit.
But basically when running, as an example, if I wanted to ,let's say, look and edit at my samba smb.conf file I'd run

```
gksudo gnome-open /etc/samba/smb.conf
```

Of course, I prefer editing my files with nano, but that's just me.

---

### Post by JKyleOKC on 2012-08-09
> **gavv said:**
> I'm attempting to execute, 
```
gksudo "gnome-open %u"
```but I can't seem to get it to work.Try this very small change and let us know what happens:```
gksudo gnome-open "%u"
```

Your original version is telling gksudo to launch a program with the explicit name "gnome-open %u" (or, possibly, with the %u expanded to the name of the file you dropped on it, but still everything within the quote marks is taken as the name of the program to launch).

My modification changes things to tell gksudo to launch "gnome-open" and pass the string that you dropped on it to gnome-open as its parameters.

That ought to make all the difference in the world...

---

### Post by mc4man on 2012-08-09
> **gavv said:**
> Hi everyone, I'm an absolute beginner with Ubuntu and Linux in general. I'm having trouble with a simple command that can be found in [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

I'm attempting to execute, 
```
gksudo "gnome-open %u"
```but I can't seem to get it to work.

I found out that 'gnome-open' was not installed, so I simply installed libgnome2-0, but after having it installed and running the command again, I'm still not seeing this launcher which lets files be opened as Root with its own associated application.

Simply running a command isn't going to create a 'launcher', drag & drop or otherwise.

For The Desktop DnD launcher that you appear to want you could look here in an older tutorial that I updated the command (xdg-open) & method to create the launcher on the Desktop
[http://ubuntuforums.org/showpost.php?p=11657989&postcount=86](http://ubuntuforums.org/showpost.php?p=11657989&postcount=86)

---

### Post by gavv on 2012-08-09
> **deadflowr said:**
> 
```
man gnome-open
```It'll give you a rundown of how to get it to work. q to quit.
But basically when running, as an example, if I wanted to ,let's say, look and edit at my samba smb.conf file I'd run

```
gksudo gnome-open /etc/samba/smb.conf
```Thank you!
---

> **JKyleOKC said:**
> Try this very small change and let us know what  happens:```
gksudo gnome-open "%u"
```Your original version is  telling gksudo to launch a program with the explicit name "gnome-open  %u" (or, possibly, with the %u expanded to the name of the file you  dropped on it, but still everything within the quote marks is taken as  the name of the program to launch).

My modification changes things to tell gksudo to launch "gnome-open" and  pass the string that you dropped on it to gnome-open as its parameters.

That ought to make all the difference in the world...

Well, I gave 
```
gksudo gnome-open "%u" 
```a shot but no dice. I didn't notice any change after I ran the command, twice. What's interesting is that on [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo), the quotes are like the original version. Perhaps this command worked in a previous version of Ubuntu; I'm currently on 12.04.
---

> **mc4man said:**
> Simply running a command isn't going to create a 'launcher', drag & drop or otherwise.

For The Desktop DnD launcher that you appear to want you could look here  in an older tutorial that I updated the command (xdg-open) & method  to create the launcher on the Desktop
[http://ubuntuforums.org/showpost.php?p=11657989&postcount=86](http://ubuntuforums.org/showpost.php?p=11657989&postcount=86)

I went through the tutorial, but I'm coming up short. I have the  launcher on the Desktop, but I can't get the DnD to work. When I drag a  file onto the launcher, the file is placed on or under the launcher  instead.

For the MimeType, I put MimeType= ~/Desktop/openit.desktop

---

### Post by NikTh on 2012-08-09
> **gavv said:**
>  Perhaps this command worked in a previous version of Ubuntu; I'm currently on 12.04.

Hi , 
I agree with above you said. The thread that mentioned in this How To [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) is from 2005 !!! 
[http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008)

If you want to do something specific , just tell us . 
Thanks

---

### Post by gavv on 2012-08-09
> **NikTh said:**
> Hi , 
I agree with above you said. The thread that mentioned in this How To [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) is from 2005 !!! 
[http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008)

If you want to do something specific , just tell us . 
Thanks

I'm trying to create a launcher such that when a file is dragged and dropped onto it, it will be opened as Root with its own associated application.

---

### Post by NikTh on 2012-08-09
> **gavv said:**
> I'm trying to create a launcher such that when a file is dragged and dropped onto it, it will be opened as Root with its own associated application.

Hi, 
to open a file with preferred application , I know that is ```
xdg-open
``` command. 
eg ```
xdg-open <file>
```To create a launcher in 12.04 is not to difficult. Install a package first
```
 sudo apt-get install --no-install-recommends gnome-panel
```and then run in terminal ```
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```Try to experiment with above. Maybe you will figure out something and solve your problem. 
Although I smell a script here and I cannot help you further. Be patient for someone more experienced.
My little experience "said" that , when root privileges entangled , things are more difficult. 
Thanks

---

### Post by gavv on 2012-08-09
> **NikTh said:**
> Hi, 
to open a file with preferred application , I know that is ```
xdg-open
``` command. 
eg ```
xdg-open <file>
```To create a launcher in 12.04 is not to difficult. Install a package first
```
 sudo apt-get install --no-install-recommends gnome-panel
```and then run in terminal ```
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```Try to experiment with above. Maybe you will figure out something and solve your problem. 
Thanks

I got it to work with gnome-panel.
```
gnome-desktop-item-edit ~/Desktop --create-new
```Name: Open as root
Command: gksudo "xdg-open %u"

As explained in [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo), I can now edit config files owned by Root by simply dragging and dropping files onto the launcher.

Thanks everyone for the support.

---

