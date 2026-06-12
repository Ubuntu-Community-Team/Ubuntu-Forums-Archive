---
title: "exit x?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by fawzley on 2008-08-19
I am attempting to install drivers for my nvidia graphics card and I need to exit my x server.  What is an x server and how do I exit the beast?

Newbie using Ubuntu 8.04. Are there any comprehensive instructions for installing nvidia drivers for Ubuntu?  Nvidia has nothing and it has taken me over two weeks to get this far with the install. Every time I try to install per documentation something undocumented goes wrong and stalls me until I figure out the next weirdness.

HELP....

---

### Post by doas777 on 2008-08-19
> **fawzley said:**
> I am attempting to install drivers for my nvidia graphics card and I need to exit my x server.  What is an x server and how do I exit the beast?

Newbie using Ubuntu 8.04. Are there any comprehensive instructions for installing nvidia drivers for Ubuntu?  Nvidia has nothing and it has taken me over two weeks to get this far with the install. Every time I try to install per documentation something undocumented goes wrong and stalls me until I figure out the next weirdness.

HELP....

ok, think of x as the part of your system that sits below gnome and gives you a gui session. to restart x, there are a few things you can do. 
you can reboot, or you can logout, and while on the login screen, press cntrl + alt + backspace . your login manager will disappear and then reappear.
log in and you should be able to proceed with your install.

good luck,
Franklin

---

### Post by Separ on 2008-08-19
X is the graphical server that shows your user interface. To completely stop it for installing a graphics binary driver you will need to go to tty1 by pressing ctrl+alt+f1 and type
```
sudo /etc/init.d/gdm stop
``` then install the driver and type ```
sudo /etc/init.d/gdm start
``` to start the GUI up again.

---

### Post by doas777 on 2008-08-19
Separ is right, just hit Cntrl + Alt + F1 to bring up a terminal, login,  and use the commands he gave.

sorry i misread your post and though you we;re asking about restarting x. my bad.

---

### Post by Perfect Storm on 2008-08-19
Why not using the driver in the repo - It's much easier if you are a newbie.

Other than that if you want to install the driver from nvidia site:

Example the driver is downloaded to your Desktop;
Note by doing this you can loose wireless and everytime there is a kernel upgrade you need to do it again.
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential xserver-xorg-dev
sudo apt-get remove nvidia-glx-new nvidia-kernel-common

```

<alt>+ctrl>+<F1>

```
sudo /etc/init.d/gdm stop
cd ~/Desktop
sudo sh <name of the driver>
sudo nano /etc/X11/xorg.conf
```

Check if the driver is changed from "nv" to "nvidia"

save <ctrl>+<o> and exit <ctrl>+<x>

```
sudo /etc/init.d/gdm start
```

---

### Post by scorp123 on 2008-08-19
> **fawzley said:**
>  What is an x server  Wikipedia ftw ;)
[http://en.wikipedia.org/wiki/X11](http://en.wikipedia.org/wiki/X11)

---

### Post by fawzley on 2008-08-21
> **Separ said:**
> X is the graphical server that shows your user interface. To completely stop it for installing a graphics binary driver you will need to go to tty1 by pressing ctrl+alt+f1 and type
```
sudo /etc/init.d/gdm stop
``` then install the driver and type ```
sudo /etc/init.d/gdm start
``` to start the GUI up again.

Thx but still have a problem...  ctrl+alt+f1 worked, attempted install and I had to be root so I did sudo -i. As install was in process got 'no precompiled kernel interface' install y/n.   
 
Then got 'no precompiled kernel interface found'.

Software attempted to compile got & 'no libc header' and I need to install my distrobution libc development package. ??

Can you help?

Thx

---

### Post by fawzley on 2008-08-21
> **doas777 said:**
> Separ is right, just hit Cntrl + Alt + F1 to bring up a terminal, login,  and use the commands he gave.

sorry i misread your post and though you we;re asking about restarting x. my bad.


Sorry I am virgin newbie and don't know if I am asking the right questions or not..  thx...

---

### Post by Perfect Storm on 2008-08-22
> **fawzley said:**
> Thx but still have a problem...  ctrl+alt+f1 worked, attempted install and I had to be root so I did sudo -i. As install was in process got 'no precompiled kernel interface' install y/n.   
 
Then got 'no precompiled kernel interface found'.

Software attempted to compile got & 'no libc header' and I need to install my distrobution libc development package. ??

Can you help?

Thx


read my post again.
Besides---I'll ask again why not install the driver from the repo? ENVY is there if you want the latest nvidia driver.

---

### Post by fawzley on 2008-08-25
[read my post again.
Besides---I'll ask again why not install the driver from the repo? ENVY is there if you want the latest nvidia driver. ]

I am not sure what 'repo driver' or ENVY are; a local religion maybe?
And I am looking to get a better grip (read working knowledge) of Linux.

I need to set the display rotated 90 degrees and 1200x1920. 
The default Linux driver offers no rotation option and a maximum resolution 1280x800.
Hardware will handle the combination as it works under XP and Vista, my goal is to move some of my users away from an MS environment.

Can you help?

Thx  F.

---

### Post by jerome1232 on 2008-08-25
You probably don't have the build-essential package which is required to build that driver, trust us though this way sucks, you have to redo it everytime there's a kernel update = annoying

```
sudo apt-get install build-essential
```
Oh and btw that is how you install something from the repos.

But seriously do you want to rebuild your driver everytime there's a kernel upgrade or xorg update, I know I don't.

To install from the repos... RECOMMENDED 

```
sudo apt-get install nvidia-glx-new nvidia-settings
```
To adjust nvidia settings using their utility
```
gksudo nvidia-settings
```

Or if you want the most up-to-date drivers use envy as suggested
```
sudo apt-get install envyng-gtk
gksudo envyng -g
```

---

### Post by fawzley on 2008-08-26
jerome1232,


Ran commands and had problems,  I have included log of interactions. What did I do wrong. 

**-begin log -----------------**
user@snidley:~$ sudo apt-get install envyng-gtk
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  envyng-core
The following NEW packages will be installed:
  envyng-core envyng-gtk
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 232kB of archives.
After this operation, 1303kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe envyng-core 1.1.1ubuntu17 [136kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe envyng-gtk 1.1.1ubuntu1 [95.9kB]
Fetched 232kB in 2s (96.2kB/s)     
Selecting previously deselected package envyng-core.
(Reading database ... 105303 files and directories currently installed.)
Unpacking envyng-core (from .../envyng-core_1.1.1ubuntu17_all.deb) ...
Selecting previously deselected package envyng-gtk.
Unpacking envyng-gtk (from .../envyng-gtk_1.1.1ubuntu1_all.deb) ...
Setting up envyng-core (1.1.1ubuntu17) ...

Setting up envyng-gtk (1.1.1ubuntu1) ...

user@snidley:~$ gksudo envyng -g
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend
   "-k" for the QT4 frontend
   "--uninstall-all" to completely remove what EnvyNG has done
user@snidley:~$ gksudo envyng 
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend
   "-k" for the QT4 frontend
   "--uninstall-all" to completely remove what EnvyNG has done
user@snidley:~$ gksudo envyng-g
user@snidley:~$ gksudo envyng -g
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend
   "-k" for the QT4 frontend
   "--uninstall-all" to completely remove what EnvyNG has done
user@snidley:~$ gksudo envyng "-g"
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend
   "-k" for the QT4 frontend
   "--uninstall-all" to completely remove what EnvyNG has done
user@snidley:~$ sudo apt-get install nvidia-glx-new nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-new-kernel-source
The following NEW packages will be installed:
  nvidia-glx-new nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 679kB/5928kB of archives.
After this operation, 17.1MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe nvidia-settings 1.0+20080304-0ubuntu1.1 [679kB]
Fetched 679kB in 2s (248kB/s)           
Selecting previously deselected package nvidia-glx-new.
(Reading database ... 105411 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_1.0+20080304-0ubuntu1.1_i386.deb) ...
Setting up nvidia-glx-new (169.12+2.6.24.13-19.45) ...

Setting up nvidia-settings (1.0+20080304-0ubuntu1.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
user@snidley:~$ gksudo nvidia-settings
user@snidley:~$ sudo -i
root@snidley:~# nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


gksudo nvidia-settings
**-end log -----------------**

---

### Post by jerome1232 on 2008-08-26
huh odd, try it as just sudo envyng -g

---

### Post by fawzley on 2008-08-27
All seemed to go well, even  installed my exact driver  driver (GeForce 8600 GT) but now all the only choices I have for screen resolution is 640x480 or 320x240. The screen resolution is so low the x server display configuration is off the screen & I can not get to the lower right hand corner to reduce the size of the window. 
Any ideas?

---

### Post by DemonBob on 2008-08-27
Open terminal. 

envyng -t

Select remove nvidia when done reboot. 

Open terminal 

envyng -t

Reinstall. restart. 


And to the person that said use the repos, some times it's not the best option. For instance, i've had nothing but problems setting up tv-out with the driver in the repo's. Since then i've always used envy to install the drivers and never have had a problem.

---

### Post by shane19174 on 2008-08-27
I can also sympathize with wanting to use a non-repo nvidia driver, even as a newbie. I also have a GeForce 8600 GT, and it just didn't work with the repo driver. For some reason Envy didn't even work for me. That is, it worked, but it had lots of problems, so I was FORCED to download the driver from nvidia and use it (now using the latest beta). Yeah, it's kind of a pain to reinstall with every kernel change, but I've pretty much gotten used to it. And it's even more of a pain to have applications lock up, to not be able to run graphics-intensive programs at an acceptable speed, etc. It's not just overclockers and gamers who might be interested in a non-repo driver; sometimes it's just a matter of getting things to work.

PS: If using either Envy or a driver from the nvidia site, make sure to completely uninstall the other one first! Otherwise you get conflicts.

---

### Post by fawzley on 2008-08-27
DemonBob,

Nothing  succeeds like success the envyng delete and reinstall ---- worked...... Got scads of resolutions from 320x240 to 1600x1200.  What is envyng, who/what is responsible for the software, is documentation available?  Don't know jack and got a million questions...
You appear to know what you are doing here thank you.  
Now I need to figure how to rotate the display 90 degrees. the System/preferences/screen resolution Rotation button has no choice other than normal. Any Ideas?  
One side-effect of the envyng  driver change is the login screen is so large I am unable to see the login  prompt.
 Not a big problem but if you have any thoughts.. would be appreciated.  I have looked at System/administration / Login window but see no way to change the size there..

Thanks again, Fawzley

---

### Post by shane19174 on 2008-08-27
See here for more background on EnvyNG and its maker: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by fawzley on 2008-08-27
> **shane19174 said:**
> 

PS: If using either Envy or a driver from the nvidia site, make sure to completely uninstall the other one first! Otherwise you get conflicts.

Got 173.14.12 installed (I think) - Thanks

---

### Post by jerome1232 on 2008-08-27
@Demonbob, is there a big difference between envyng gtk based installer and the text based installer? Should I be recomending the text based (less problems etc...) I don't use envy so I would like to know why gtk based failed to seemingly edit xorg.conf while the text based one did just fine.

The reason I emphasize the repo drivers and envy is most new users think the only option is to download the driver off of nvidia's site when that should be the last thing to try when all else failed.

Glad ya got it working :)

---

