---
title: "[SOLVED] Install help.  Won't go past login screen."
date: 2008-07-27
forum: New to Ubuntu
---

### Post by crjackson on 2008-07-27
I decided to do an install of 8.04.01 over a working 7.10 install on the kids system.

The install was uneventful and seemed to go as normal.  Then I removed the install disk, rebooted and was greeted with the login screen.

I proceeded to login, got the desktop music, the spinning loading wheel, then the screen when black and dumped me back to the login screen and the little drum sounded again.

I've powered off and rebooted several times and get the same thing.  The only think I did notice was during the preboot screen, I see a brief error about a timer to the apic.  So I hit the escape button during gurb screen, and added noapic to the kernel line.  It made no difference.  I still keep getting dumped back to the login screen over and over again.

Suggestions Please...

SYSTEM:
AMD 64 3200+
ATI intergrated graphics (ATI 200 Xpress I think, not sure)
1GB memory
100GB ATA HD
Linksys wrt54g wireless
MIS Motherboard (eMachines) - Worked fine with Gutsy

---

### Post by Locutus_of_Borg on 2008-07-27
can you login with any other username?

i had a similar problem once, and turned out to be i messed something up with the home directory of that user

if it is the only user of the machine, theres an offchance that the user has lost permissions to its home directory, boot into single user mode
(append the word "single" to the end of the kernel line) and try to ```
chown -R YOUR_USER_NAME: /home
```

otherwise i dont know...

---

### Post by crjackson on 2008-07-27
It's a fresh install.  It won't login to the install users name.  It does accept the login information but then dumps me back to the login screen before hitting the desktop.

---

### Post by crjackson on 2008-07-27
I just tried to boot the LiveCD and it won't login either.  It's an endless loop of trying to auto-login and dumping to the login screen.  There shouldn't even be a login screen on the LiveCD.  What's up with that?

---

### Post by crjackson on 2008-07-27
Recovery mode does the same thing too....

---

### Post by crjackson on 2008-07-27
I may have to go back to 7.10 or xp on this system it seems.  I don't think Ubuntu 8.04 is going to work out.  Damn!  The install of 7.10 had some issues with the package manager (couldn't get security updates) so I decided to just move up to 8.04.1.  I guess I should have just left it as is...  Damn It!!

---

### Post by Locutus_of_Borg on 2008-07-27
thats strange...bad disk?

seems unlikely though if it completed the installation...

can you login without the X window system?

as in, when at the login screen, hold ctrl and alt and press F1 and log in through that screen...

---

### Post by crjackson on 2008-07-27
> **Locutus_of_Borg said:**
> thats strange...bad disk?

seems unlikely though if it completed the installation...

can you login without the X window system?

as in, when at the login screen, hold ctrl and alt and press F1 and log in through that screen...

Not a bad disk.  Used it for 3 installs on other systems today.  In fact, used it to install AFTER this one.

---

### Post by crjackson on 2008-07-27
> **Locutus_of_Borg said:**
> can you login with any other username?

i had a similar problem once, and turned out to be i messed something up with the home directory of that user

if it is the only user of the machine, theres an offchance that the user has lost permissions to its home directory, boot into single user mode
(append the word "single" to the end of the kernel line) and try to ```
chown -R YOUR_USER_NAME: /home
```

otherwise i dont know...

If it allows me to login in this way, can I enable ALL software sources and install updates?  Perhaps this will fix the problem?

---

### Post by Locutus_of_Borg on 2008-07-27
yes

```
nano /etc/apt/sources.lst
```
remove the # from all the lines you want available to you
```
apt-get update
apt-get upgrade
```

---

### Post by crjackson on 2008-07-27
> **Locutus_of_Borg said:**
> yes

```
nano /etc/apt/sources.lst
```
remove the # from all the lines you want available to you
```
apt-get update
apt-get upgrade
```

going to give it a try now.

---

### Post by Locutus_of_Borg on 2008-07-27
if you have never used nano, to save, hold ctrl and press X, then press Y, then press enter

---

### Post by crjackson on 2008-07-28
> **Locutus_of_Borg said:**
> yes

```
nano /etc/apt/sources.lst
```
remove the # from all the lines you want available to you
```
apt-get update
apt-get upgrade
```

Well it turns out it should be /etc/apt/sources.list on Hardy.

However apt-get update & apt-get upgrade won't work because it's not working with the wireless at this point.

Also I've tried noapic noacpi nolapic and I still get the same results.

---

### Post by crjackson on 2008-07-28
> **Locutus_of_Borg said:**
> if you have never used nano, to save, hold ctrl and press X, then press Y, then press enter

Yeah, I've used it before.  I need this damned thing to boot to X.

---

### Post by crjackson on 2008-07-28
Obviously I was able to login using CLI so it must be an X thing.  Probably something to do with the freaking video card or something.

---

### Post by crjackson on 2008-07-28
Okay, moved the tower to a location where I can plug in a cable.  Download updates now.

If this doesn't work, does anyone have any other suggestions?

---

### Post by crjackson on 2008-07-28
How can I install the ATI proprietary driver from CLI?  I don't know what the package name is.  Perhaps this would help.

---

### Post by crjackson on 2008-07-28
Okay, I installed the ATI drive by CLI and that changed nothing.  Can't someone help here?  I know there must be a simple solution.  It comes so close to booting but just keeps dumping me to the login screen.

---

### Post by crjackson on 2008-07-28
Come on... Can on one help with this?

---

### Post by crjackson on 2008-07-28
I need some help here please.

---

### Post by run1206 on 2008-07-28
the only thing i can think of is if you can get the internet connection to work while in terminal, install bootchart...
```
sudo apt-get bootchart
```

it's an application that runs while the boot process is running and outputs a picture log file in /var/log/bootchart to view.

the thing is i'm trying to find the patch for it to run during the GNOME startup (afer login). that way you could check to see what's going on after your login.  

here's the sites i'm looking at, maybe you might be able to find something there...

[http://ubuntuforums.org/showthread.php?t=691110&highlight=access+login+service+terminal](http://ubuntuforums.org/showthread.php?t=691110&highlight=access+login+service+terminal)  (thread #7)

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/128803)
(towards the bottom they talk about the patch)

[http://www.gnome.org/~lcolitti/gnome-startup/analysis/](http://www.gnome.org/~lcolitti/gnome-startup/analysis/)
(i'm currently reading this to see how to implement the patch to view post login processes)  

don't know if it'll help but worth a shot...
good luck

---

### Post by dew5 on 2008-07-28
hey mate.

If you can go

system>administration>hardware drivers
ATI should be selected. 
hope this helps

dew

---

### Post by crjackson on 2008-07-28
> **dew5 said:**
> hey mate.

If you can go

system>administration>hardware drivers
ATI should be selected. 
hope this helps

dew

I can't get to the desktop.  If I could get to that point it would be great.

---

### Post by crjackson on 2008-07-28
I hate to say it but it looks like this machine is going back to windows.

---

### Post by run1206 on 2008-07-28
hopefully nothing is saved on that partition; see if you could delete Ubuntu and install it again

i had to do that for gutsy...worked the second time.

---

### Post by Troll_the_Great on 2008-07-28
Have you tried entering your user name and password several times?I had a similar problem after a kernel update.I would reach the login screen, enter my user name and password and after a few seconds I was back to the login screen.Then I would repeat the process and the second time it would work.

---

### Post by crjackson on 2008-07-28
> **Troll_the_Great said:**
> Have you tried entering your user name and password several times?I had a similar problem after a kernel update.I would reach the login screen, enter my user name and password and after a few seconds I was back to the login screen.Then I would repeat the process and the second time it would work.

Yes I've tired that.  I've found (by using google) many posts where people can't log in and have the exact same problem.  None of them seemed to have solve the problem though.

---

### Post by crjackson on 2008-07-28
Come on guys, can no one help me, or is it just too much trouble?  

I don't want to downgrade and I don't want to install windows but I have to make this a working system soon.  Please help.

Surely someone can walk me through making this work...

---

### Post by crjackson on 2008-07-29
So that's it then.  You guys are going to throw me to the dogs and not help anymore?  I know that someone on this forum knows about this problem and can help.  Won't you please help me?

---

### Post by Locutus_of_Borg on 2008-07-29
im surprised nobody said this:

```
nano /etc/X11/xorg.conf
```
change display driver to Vesa
save
startx


hope you havent gone to windows yet...

---

### Post by crjackson on 2008-07-29
> **Locutus_of_Borg said:**
> im surprised nobody said this:

```
nano /etc/X11/xorg.conf
```
change display driver to Vesa
save
startx

hope you havent gone to windows yet...

Thanks for your help and everyone else who tried, this didn't work either.  I'll marked the thread as solved now.

I fixed the problem by installing WinXP.  Thank you PmDematagoda for helping me decided what I must do.

It seems that because compiz is enabled by default, and the needed drivers for compiz aren't, then this is the problem.  I filed a bugreport and found a few that seem to be related.

None the less, this machine is doomed to WinXP.  Thanks again for your help.

---

### Post by naturalfreak on 2008-08-14
I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

---

### Post by crjackson on 2008-08-14
> **naturalfreak said:**
> I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

The system wouldn't boot by any means that allowed one to navigate to System > Administration > Hardware Drivers

If I could have gotten that far I would have been jumping for joy.

---

### Post by thumper13 on 2008-08-17
> **naturalfreak said:**
> I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

I think what this user meant to say was to change the session to Failsafe mode at the login screen... as in click on options, select session, and choose the Failsafe option...

Then proceed to enter user/pass..

You SHOULD then be able to access the desktop.

I have ATI x200s in my machines, and since I've installed this version, I've had to do that on my computers. If you activate the driver and let it patch accordingly, your next login should be smooth sailing.

EDIT: I Also believe this is relevant to the x200 (Possibly just onboard video) specifically, as I installed the same disc on a friends machine when he had the Radeon 9800, and then after he upgraded to the x800, and no problems were encountered.

---

### Post by crjackson on 2008-08-18
> **thumper13 said:**
> I think what this user meant to say was to change the session to Failsafe mode at the login screen... as in click on options, select session, and choose the Failsafe option...

Then proceed to enter user/pass..

You SHOULD then be able to access the desktop.

I have ATI x200s in my machines, and since I've installed this version, I've had to do that on my computers. If you activate the driver and let it patch accordingly, your next login should be smooth sailing.

EDIT: I Also believe this is relevant to the x200 (Possibly just onboard video) specifically, as I installed the same disc on a friends machine when he had the Radeon 9800, and then after he upgraded to the x800, and no problems were encountered.

I'll try that the next time I attempt to install Ubuntu Hardy on the machine.  I'm not going to change it in the near future though.  I do have another machine with an x200 in it. It's just setting in the corner so I might try it down the road.

---

### Post by abeautifulbeat on 2008-09-24
:) Thank you natural freak!  I had this exact same problem, ati 200 card and everything, and what you said worked! Thanks again!!!

---

### Post by bvadorno on 2010-11-08
After struggling a few hours trying to login in kde and always coming again to the login screen, I deleted the following folders:

 ~/.kde 
/var/tmp/kdecache-my_user_name
/tmp/ksocket-my_user_name
/tmp/kde-my_user_name

Finally, I could log in. Of course, I lost all my kde preferences, but it was better than simply reinstalling the system.

Cheers,
Bruno

---

