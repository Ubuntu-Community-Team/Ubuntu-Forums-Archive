---
title: "Ubuntu 16 doesn't boot graphically and startx doesn't work"
date: 2016-05-28
forum: New to Ubuntu
---

### Post by manuel41 on 2016-05-28
Ubuntu used to work almost fine for the last two weeks, I restarted it to play a game under windows, I  restarted it again to boot Ubuntu again and now if I boot normally, it gets stuck in the boot screen. The dots under ubuntu won&#8217;t move. 

[LIST]
[*]   if I press ALT+F2 it says 
[/LIST]
[INDENT]```
A start job is running for Hold until boot process finishes up (xxmin xxs / no limit)
```
[/INDENT]
   
[LIST]
[*]if I try to reinstall Ubuntu with a thumbdrive the only option is to erase everything, I wanted to try to salvage the installation I&#8217;ve been using so far. 
[/LIST]
 
Through recovery mode:    

[LIST]
[*]  network says 
[/LIST]
[INDENT]```
Trying to start NetworkManager...           
unknow username &#8220;geoclue&#8221; in message bus configuration file
grep: /etc/resolv.conf: No Such file or directory    

```
[/INDENT]
[INDENT]and then repeats that last line 16 times 
[/INDENT]
 
 
[LIST]
[*]   if I hit resume, the screen blinks and keypresses are not always detected but I can login through the command line 
[*]  startx returns [this confusing screen]("http://i.imgur.com/j9lJlI3.jpg") 
[*]  I&#8217;ve tried messing a bit with the drivers (I have an hd6850): 
[/LIST]
[INDENT]```
sudo apt-get purge "fglrx.*"
sudo rm /etc/X11/xorg.conf             
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64             
sudo dpkg-reconfigure xserver-xorg             
sudo reboot  
```
[/INDENT]
[INDENT]and now I cannot even see ubuntu and the dots (but everything else is unchanged)  
[/INDENT]
[INDENT]
[/INDENT]
 How could I resolve this quite big issue?

---

### Post by ajgreeny on 2016-05-28
startx will not work in 16.04 which uses systemd, not upstart, but you may get somewhere by using command ```
sudo service lightdm start
```
However, that does not really help us to figure out what has happened and why you no longer boot to a desktop.

Should there be a user called **geoclue**; is that you? Or is that error a red herring; I am not sure but merely thinking as I type.  Certainly it is true that fglrx will not work with 16.04 so you were correct to remove that and use the open source driver, either radeon or amdgpu.

Let's see if you can get to a desktop first and then work from there.

---

### Post by UltimateCat on 2016-05-28
I learned this from a man in Debian Testing and it may help-;)

  	 	 	 	   If a system won't boot to desktop it has to be xorg, the kernel or maybe a proprietary video driver most likely.
It could also be something in the init system (sysvinit, startup and systemd) but in testing it's xorg related.
Run a update, if that doesn't work try Recovery Mode and direct it to boot when it get's around to asking what you want.
Recovery Mode runs a few more corrective tools and may fix it on it's own.
If you can run the DE as root the problems is with your user not the system at large.

---

### Post by manuel41 on 2016-05-28
> **ajgreeny said:**
> startx will not work in 16.04 which uses systemd, not upstart, but you may get somewhere by using command ```
sudo service lightdm start
``` However, that does not really help us to figure out what has happened and why you no longer boot to a desktop.  Should there be a user called **geoclue**; is that you? Or is that error a red herring; I am not sure but merely thinking as I type.  Certainly it is true that fglrx will not work with 16.04 so you were correct to remove that and use the open source driver, either radeon or amdgpu.  Let's see if you can get to a desktop first and then work from there.  thanks, finally something changed!      doing so results in  ```
Job for lightdm.service failed because the control process exited with error code. See "systemctl status lightdm.service" and "journalctl -xe" for details.
```   > **UltimateCat said:**
> I learned this from a man in Debian Testing and it may help-;)    	 	 	 	   If a system won't boot to desktop it has to be xorg, the kernel or maybe a proprietary video driver most likely. It could also be something in the init system (sysvinit, startup and systemd) but in testing it's xorg related. Run a update, if that doesn't work try Recovery Mode and direct it to boot when it get's around to asking what you want. Recovery Mode runs a few more corrective tools and may fix it on it's own. If you can run the DE as root the problems is with your user not the system at large.  I've been using linux for less than one month, I have no idea what the things you just wrote meant!     if running an update is sudo apt-get upgrade, then I have already done it from the recovery, from there I also tried to repair broken packages, but that didn't fix it either

---

### Post by ajgreeny on 2016-05-28
Run those two command shown in a terminal and see what output you get.
```
systemctl status lightdm.service
journalctl -xe
```
I have no idea if they must be run as root but if they do it will probably either tell you or show no output so try with **sudo** prefix if necessary.

I use 16.04 only in a VBox installation so can not really help with more info on 16.04 yet.

---

### Post by manuel41 on 2016-05-29
> **ajgreeny said:**
> Run those two command shown in a terminal and see what output you get. ```
systemctl status lightdm.service 
journalctl -xe
``` I have no idea if they must be run as root but if they do it will probably either tell you or show no output so try with **sudo** prefix if necessary.  I use 16.04 only in a VBox installation so can not really help with more info on 16.04 yet.  

the first one returns    
```
lightdm.service - Light Display Manager    Loaded: loaded (/lib/systemd/system/lightdm.service; static; vendor preset: enabled       
Active: inactive (dead)         
Docs: man:lightdm(1) 
``` 

 the second one returns 3707 lines, is there something in particular I should write down?    
the ones with colord-sane are red and return the same error, example:
 ```
colord-sane[12163]: io/hpmud/pp.c 627: unable to read device-id ret=-1
``` 

and where else could I post this issue?

---

### Post by ajgreeny on 2016-05-29
Sorry; not sure I can help you more with this.  As I say, I am not really using 16.04 yet and certainly do not understand systemd and all its implications, which is where the **journalctl -xe** is involved.

Wait to see if any more help comes along from those who are using and 16.04 better than I do.

---

### Post by pissedoffdude on 2016-05-30
Hi,

It might've been the case you had the proprietary drivers installed, ran some udpates that includes a new kernel update, and the module wasn't recompiled for that new kernel.

Can you let us know if running the below does it (it's okay if the cp and rm commands fail): 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get purge "fglrx.*"
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old1
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot
 
```

EDIT: I see you've tried this already, but can you give it another go, this time by ensuring you have the latest updates installed (added to the command list).

If it doesn't go, do you know if you installed updates or maybe used the 'drivers' UI and selected another video driver before you last rebooted?  If you ran anything in the terminal, you can use the 'history' command to see if you previously ran that might've caused this

---

### Post by manuel41 on 2016-05-30
> **pissedoffdude said:**
> Hi,

It might've been the case you had the proprietary drivers installed, ran some udpates that includes a new kernel update, and the module wasn't recompiled for that new kernel.

Can you let us know if running the below does it (it's okay if the cp and rm commands fail): 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get purge "fglrx.*"
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old1
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot
 
```

EDIT: I see you've tried this already, but can you give it another go, this time by ensuring you have the latest updates installed (added to the command list).

If it doesn't go, do you know if you installed updates or maybe used the 'drivers' UI and selected another video driver before you last rebooted?  If you ran anything in the terminal, you can use the 'history' command to see if you previously ran that might've caused this

done that, but it did not fix the issue :(
history command works (logs 600-ish lines), but I tried history > history_for_print.txt and  when I rebooted to windows, the file was empy. :)    
Actually the day before I installed some updates from the ubuntu software center thing, thought it was safe. Turns out I was wrong.

I think I'm done here, I really need a working machine and I have already lost three days. I'm recovering some files from windows and wiping out everything fresh.     
But it's really a bad feeling knowing you can screw everything by sneezing too loud near the computer.   
Good thing I did not thrust linux and saved everything in other hdds (btw, thanks ubuntu to make changing default folders so tricky).
I also hoped to learn something, but the only lesson learned was "thrust linux even less than before".

But thanks for the support and all the fish, I appreciate the effort, guys

---

