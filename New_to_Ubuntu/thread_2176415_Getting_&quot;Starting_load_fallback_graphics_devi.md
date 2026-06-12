---
title: "Getting &quot;Starting load fallback graphics devices [fail]&quot; - after Nvidia module update"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by curt2 on 2013-09-24
I am having an issue getting "Starting load fallback graphics devices [fail]".
I suspect that it is due to a 3rd party (Nvidia) driver for my  VGA  card. 
I put Ubuntu 12.04 LTS Desktop (downloaded 22 Sept 2013) on my old PC:  Asus P5W DH, Some intel dual core proc, ~4GB RAM, and an Nvidia GTS450 - all several years old.
It all installed easily & ran great at first! :-D  (This is my first Linux venture.  Total noob.)

* THEN *I got the bright idea of installing the 'latest' graphics card driver,  er, module, which I downloaded from NVidia for Linux.
While I could get it downloaded, I couldn't' get it to install.  Kept getting a root error.
So,  after hunting round in system preferences (or the like) I found a  cute  little icon of a PCI board that did it all for me.  I forget the  name  (and currently can't reboot into Ubuntu) but it was something like   "Install 3rd Party Drivers".
It worked a treat.  Downloaded and installed something from Nvidia and looked successful.  So, I went to bed.

Next day - **No boot.**  I just get a screen full of Starting this that & other, including "Starting load fallback graphics devices [fail]".   ](*,)](*,)
(Trying to load a pic here)
[IMG]file:///C:/CurtsUbuntuErr1.jpg[/IMG]

[COLOR=#0000ff]I  suspect I need to uninstall the Nvidia module  and reinstall the Nouveau  modules.  [/COLOR](I'd prefer to do this than to  reinstall the whole Ubuntu OS again  as I already installed and set up my ROR  environment.)[COLOR=#0000ff]
Can anyone direct me to a set of instructions on how to do this??[/COLOR]
I can get to Grub, but that's about it.

Thanks for any help!

---

### Post by Jonathan Precise on 2013-09-24
Press Ctrl. Alt. F1. Enter your username and password. (In the password, not even asterisks show up. This is normal.)

user@computer:~$ [flashing-cursor]

Try:
```
sudo apt-get purge nvidia-current
```

Then:

```
sudo apt-get install noveau-firmware xserver-xorg-video-nouveau xsever-xorg-video-nouveau-dbg
```

Post any errors with [noparse]```
Code/Error
```[/noparse] tags, to make it end up like:

```
Code/Error
```

---

### Post by curt2 on 2013-09-29
Thanks Jonathan, but I couldn't find any point at which I could get Alt-Ctrl-F1 to work.  I ended up re-installing the OS.  I think it was quicker.

---

### Post by Eskender on 2013-10-24
Hi,

I ran into a same problem the other day and the Internet can't seem to fetch the installation you recommended there (sudo apt-get install noveau-firmware xserver-xorg-video-nouveau xsever-xorg-video-nouveau-dbg) even though the NW cable is blinking and all. What other choice do I have, besides re-installing, to get my system up-and-running again. 

Thanks.

---

### Post by innocent-devil85 on 2013-11-19
I assume when you so alt, you are referring to the "option" button on a macbook?

---

### Post by chitrasen on 2014-02-02
I had same problem. This solved it.
[http://news.softpedia.com/news/How-to-Install-The-Latest-Nvidia-Driver-on-Ubuntu-12-04-295542.shtml](http://news.softpedia.com/news/How-to-Install-The-Latest-Nvidia-Driver-on-Ubuntu-12-04-295542.shtml)

---

### Post by olexandr2 on 2014-02-08
Hi! I have a similar problem.
In the device driver, I took the wrong version of the driver NVIDIA.

[LIST=1]
[*]Reboot computer and hold the Left Shift Key down.
[*]Select boot into recovery mode.
[IMG]http://i.stack.imgur.com/g8uDd.png[/IMG]
[*]After a few seconds you should get the "Recovery Mode Options" screen.
[IMG]http://s018.radikal.ru/i527/1209/d0/5702fb58c308t.jpg[/IMG]
[*]Select "clean         [FONT=Ubuntu Mono]Tryto make free space"[/FONT].
[*]Then I chose to remove the driver package Nvidia. Be careful, you may be a few other packages to remove. Prior to confirming please read what packages will be deleted! Sorry for my English.
[/LIST]

---

### Post by ss1133xx on 2014-03-03
[COLOR=#000000]Regarding:

I recommend a full ubuntu installation rather than a wubi install[/COLOR]:-s[COLOR=#000000]. Ask me why.

I am having the same issue.  Why do you "[/COLOR][COLOR=#000000]recommend a full ubuntu installation"?  I'm trying to decide whether to start all over again.  Do you know of a step-by-step reinstall guide?  (PC was working fine until an update.)


[/COLOR]

---

### Post by ss1133xx on 2014-03-03
Hi.  My facts are similar to the ones you described.  I have been trying to repair, but its not working.  Do you recall the steps you used to re-install 12.04?  I'm thinking that might be faster than a repair.

---

