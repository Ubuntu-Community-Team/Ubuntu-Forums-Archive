---
title: "HOWTO: Install Parallels on Ubuntu"
date: 2007-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Frak on 2007-07-31
[CENTER][SIZE="5"]Parallels Workstation is a program capable of completely emulating hardware to run other OS's.[/SIZE]

Until now, Parallels has had problems compiling the the newest kernel (2.6.21.5 or something like that), but Parallels has come out with a fixed file for correcting the mistake.
I have created this thread to help those who have valid licenses and want to use Parallels.


[SIZE="3"][COLOR="Red"]STEP 1[/COLOR][/SIZE]
Install Necessary Packages 
```
sudo aptitude install libqt3-mt-dev build-essential libstdc++5
```


[SIZE="3"][COLOR="Red"]STEP 2[/COLOR][/SIZE]
Install Parallels
[>>Download Here<<]("http://download.parallels.com/stuff/ubuntu_special/Parallels-2.2.2164-lin-en.deb")
Then, either automatically install it, or save it to desktop and double click it and install it. Your choice.


[CENTER][SIZE="3"][COLOR="Red"]STEP 3[/COLOR][/SIZE]
Configure Parallels
In the Terminal
```
sudo parallels-config
```
And agree to the license agreements.[/CENTER]
[COLOR="Red"]
[SIZE="4"]
FINISHED[/SIZE][/COLOR]
Now all to do is enter your license code, and your ready to Virtualize.[/CENTER]

---

### Post by El Gabito on 2007-08-17
The last command has changed and is now

```
sudo parallels-config
```

instead of "configure"

---

### Post by Frak on 2007-08-17
Thanks, I'll change that.

---

### Post by rpb on 2007-09-13
I am on feisty and had a few more problems. I did not have the linux-headers for my kernel installed which would not let me compile the parallels drivers. Once I had those, I also needed libstdc++5 to not get the prl_dhcpd error.

---

### Post by Frak on 2007-09-13
Thanks for the info.

I'll add that to the post.

---

### Post by LuisC-SM on 2007-09-16
Hi.

I have 2 weird issues.

I installed parallels just the way mentioned above with no compiling single issue. I'm running compiz-fussion on fesity.

The first issue is: on a fresh boot, when I try to run parallels it gives me the next popup window:

"Module **vm-mai**n is not found. **Parallels Wrokstation 2.2** is installed, but it has not been configured for your running kernel. To configure it please login as root and run **parallels-config**"

So I run AGAIN parallels-config (as root) and everything is ok, BUT ... my parallels window is so translucent that I can hardly read. So what I do is just to restart metacity and works fine. If i restart commpiz-fusion it seems not to work. But at this point I don't really care if I use emerald or metacity, I just want to not to run parallels-config everytime I boot.

Just FYI I have a VALID serial.

Thanks in advance for the help you can give me.

Luis

EDIT: I must add 2 more things.
1. The license agreement was never showed, however before the license agreement I inserted my serial number in this format XXXX-XXXX-XXXX-XXXX (with separators)
2. Running from a terminal I get the next error:> Now you can run Parallels Workstation 2.2
    Issue parallels command.

cacho@Toshiba-Laptop:~$ parallels
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
But parallels works just fine so...........????

---

### Post by Frak on 2007-09-16
For one, Parallels uses QT, which some apps written in QT have problems existing with Compiz-Fusion.

And for the X Error, don't worry about it. You get that error because you're not using a Wacom Tablet. It happens every time you use a Graphical app from the terminal.

---

### Post by LuisC-SM on 2007-09-16
Thanks a lot for your prompt response :)
> **Frak said:**
> For one, Parallels uses QT, which some apps written in QT have problems existing with Compiz-Fusion. Yes! and also I read this:
[http://forum.parallels.com/showthread.php?t=14149&highlight=compiz](http://forum.parallels.com/showthread.php?t=14149&highlight=compiz)
So it seems that this will be an issue using compiz-fusion
> 
And for the X Error, don't worry about it. You get that error because you're not using a Wacom Tablet. It happens every time you use a Graphical app from the terminal.
Again, thanks a lot I was thinking this had to be with the license agreement. :/
Luis

EDIT/UPDATE: the fix for the transparent window is explained in the next link and works just perfect:
[http://forum.parallels.com/thread940.html](http://forum.parallels.com/thread940.html)

So now the next is to figure how to avoid running **parallels-config** again and again

---

### Post by LuisC-SM on 2007-09-17
SOLVED  :guitar:

This is the workaround found here: (By: martin_42)
[http://forum.parallels.com/showthread.php?t=12420&highlight=run+parallels-config](http://forum.parallels.com/showthread.php?t=12420&highlight=run+parallels-config)

> The installer doesn't set up the /etc/init.d stuff, so the drivers don't get loaded. Running the parallels-config script doesn't fix that, but it has the side-effect of loading the drivers right at the end!

A workaround is to edit the launch command script /usr/bin/parallels so that the second line reads:

/usr/lib/parallels/autostart/drivers_start

While you're there, you may as well add an extra line at the bottom:

/usr/lib/parallels/autostart/drivers_stop

If I recall correctly, those 2 scripts use illegal syntax for /bin/sh. So to get them to actually work, you need to edit drivers_start and drivers_stop, and change line 1 in each case from #!/bin/sh to #!/bin/bash (and install bash on your box if it ain't there already).

I think I had to change the parallels-config script to use /bin/bash before that would run without errors.

All things considered, it's amazing that such a highly technical product works so well once it's up and running, but has silly little errors in some trivial scripts! I can only speculate that the parallels guys tested on a Linux distro that has subtly different behaviour from Ubuntu, so presumably the installation and start-up scripts worked with no problems, whereas they run into little snags on ubuntu/kubuntu edgy and feisty.

Did you get the sound working in Feisty BTW?

Cheers
I hope this helps newcommers

Cheeers

Luis

EDIT/UPDATE: Sorry to post bad news, but I was so happy when I thought this had already worked whe I logged out my session and logged back in ... but now that I have restarted :( same thing is happening... The "**[COLOR="Red"]good[/COLOR]**" news is that with that workaround but without adding the second command (/usr/lib/parallels/autostart/drivers_stop) and running as root, it just WORKS... even if I restarted it.... so I must just find a way to change the group (chown) to "/usr/lib/parallels/autostart/drivers_start", although I really don't know if this will help any.
If someone asks why to "chown" /usr/lib/parallels/autostart/drivers_start? ... just 'cause it is asking me for the root password and keeps on telling me the passwd I issued it's just wrong... :(((

**[COLOR="Red"]2nd EDIT/UDATE: S O L V E D !!!![/COLOR]**

Ok. I'll tell you what I did.

> cd /usr/lib/qt3/plugins/inputmethods/
sudo chmod 755 *
sudo parallels-config

Rebooted and now is working just fine :D

By the way, the solution I found it here:
[http://forum.parallels.com/showthread.php?t=4495](http://forum.parallels.com/showthread.php?t=4495)
The last post is the one I followed.

So, I believe the best to do to the original thread is to update it for the newcommers (just IMHO)

Cheers Luis

---

### Post by BDNiner on 2007-09-17
I hope that I can get this running. I have compiz fusion installed about parallels installs and runs no problem. I need to get my license when i return home from work, that way i can see if windows XP can run inside ubuntu. If it can that will be great. Means i can install VZAccess and use my blackberry for internet, hopefully. I still need to get my blackberry to be recognized though.

I still can't get parallels to run after rebooting after following these steps. I am still required to run parallels-config to get up and running. Has anyone successfully installed XP? I get about half way through the installation and it hangs  when windows is installing new devices.

---

### Post by kd7swh on 2008-01-09
> **BDNiner said:**
> I hope that I can get this running. I have compiz fusion installed about parallels installs and runs no problem. I need to get my license when i return home from work, that way i can see if windows XP can run inside ubuntu. If it can that will be great. Means i can install VZAccess and use my blackberry for internet, hopefully. I still need to get my blackberry to be recognized though.

I still can't get parallels to run after rebooting after following these steps. I am still required to run parallels-config to get up and running. Has anyone successfully installed XP? I get about half way through the installation and it hangs  when windows is installing new devices.

you can tether your blackberry in linux with xmblackberry and a modem script.

[http://xmblackberry.sourceforge.net/](http://xmblackberry.sourceforge.net/)

you don't need VZAccess. 

FYI: VZW has a new data plan too. Not all reps. were told about it. $30\mo unlimited data (no BES support though) promo code: 76138
enjoy

---

