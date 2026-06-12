---
title: "Ubuntu 11.10 desktop don't starts"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by Miguel2A on 2012-04-06
[FONT=Arial]Hi all people
I'm taking my first steps in this distribution Ubuntu and I downloaded Ubuntu 11.10
Everything worked fine until by mistake instead of install a program I uninstalled another named: udisks.

Now, when I start the PC shows a graph screen where asked to "enter  password" (before didn’t do that). However, despite entering the correct  password, the system seems to enter to desktop showing a black screen  but after a few seconds it back to starting point, ie "enter password"
I can enter to the console with:[/FONT]

[FONT=Courier New][SIZE=2]Ctrl+Alt+F1[/SIZE][/FONT]

[FONT=Arial]Over there I can login with my username and password,  even as "root". From there I tried to reinstall the program that I was  uninstalled with:[/FONT]

[FONT=Courier New]apt-get install udisks[/FONT]

[FONT=Arial]and apparently installed it. I rebooted but the problem remains the same.
Also execute the following commands because I thought the problem came from the graphic driver as it is not display the desktop.
[/FONT]
[FONT=Courier New]dpkg -configure -a
apt-get update
apt-get dist-upgrade
dpkg-reconfigure -phigh xserver-xorg
reboot
[/FONT]
[FONT=Arial]And there are no changes!
Anyone have any idea how to fix it without having to reinstall everything like Bill Gate’s operating system.
Thanks in advance[/FONT]

---

### Post by UnknownFearNG on 2012-04-06
Try typing

```
startx
```

What happens?

---

### Post by 2F4U on 2012-04-06
Unfortunately, udisks has quite some dependencies, so it is probably not sufficient to just reinstall udisks. You can look into /var/log/apt/history.log to find out what else got removed.

---

### Post by Miguel2A on 2012-04-06
Thanks for your answer UnknownFearNG.

> **UnknownFearNG said:**
> Try typing

```
startx
```What happens?


I tried this command. This is the result.

[FONT=Courier New]Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

Please consult the The X.Org Foundation support
     at [http://wiki.x.org](http://wiki.x.org) 
for help

  ddxSigGiveUp: Closing log
Invalid MIT-MAGIT-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Conection refused
xinit: server error[/FONT]

Do You know what  meaning these??

---

### Post by Dreamer Fithp Apprentice on 2012-04-06
> **2F4U said:**
> Unfortunately, udisks has quite some dependencies, so it is probably not sufficient to just reinstall udisks. You can look into /var/log/apt/history.log to find out what else got removed.
Doesn't apt-get check for dependencies?

---

### Post by Dreamer Fithp Apprentice on 2012-04-06
> **Miguel2A said:**
> 
[FONT=Arial]Over there I can login with my username and password,  even as "root".[/FONT][FONT=Arial]
Interesting. Does that mean you had previously enabled the root account? Don't go into how. That's a taboo subject here. But I'm curious to know if I understood you correctly.
[/FONT]> **Miguel2A said:**
> [FONT=Arial] From there I tried to reinstall the program that I was  uninstalled with:[/FONT]

[FONT=Courier New]apt-get install udisks[/FONT]

[FONT=Arial]and apparently installed it.[/FONT]
So were you su when you did this? Or did you sudo?

---

### Post by Miguel2A on 2012-04-07
Hi Dreamer

> So were you su when you did this? Or did you sudo? 

I did this as root.

I added user root and password when the system works fine.
So I can login as root. My command line is:

[FONT=Courier New][SIZE=2]root@matrix:~#_[/SIZE][/FONT][SIZE=3]
[/SIZE]
   Also I entered the following command:

apt-cache depends udisks

and gave me:

[FONT=Courier New]Depends of: libatasmart4
[/FONT][FONT=Courier New]Depends of: libc6
Depends of: libdbus-1-3
Depends of: libdbus-glid-1-2
Depends of: libdevmapper1.02.1
Depends of: libglib2.0-0
Depends of: libgudev-1.0-0
Depends of: liblvm2app2.2
Depends of: libparted0debian1
Depends of: libpolkit-gobject-1-0
Depends of: libsgutils2-2
Depends of: libudev0
Depends of: udev
Depends of: dbus
Suggested: xfsprogs
Suggested: reiserfsprogs
Suggested: mdadm
Suggested: cryptsetup
Recommended: policykit-1
Recommended: hdparm
Recommended: dosfstools
Recommended: mtools
Recommended: ntfs-3g
Recommended: ntfsprogs
Recommended: eject[/FONT]
[FONT=Courier New]Conflict with: <devicekit-disks>
Breacks: libgdu-gtk0
Breacks: libgdu0
Replaces: <devicekit-disks>[/FONT]



So I checked and all programs are installed except those marked with:"Suggested" and "Conflic with".
It is necessary that all of them are installed?

---

### Post by Dreamer Fithp Apprentice on 2012-04-09
I don't think so. I'm not an expert but I'm pretty sure the intent is that if you have all of the depends installed (you said you do if I understand correctly) and none of the conflicts installed (you didn't mention, but probably true) it should work. While waiting for someone who knows more than I to suggest something I can think of 3 things you might want to try:

1. Try doing what the error message suggested, to whit: "[FONT=Courier New]remove /tmp/.X0-lock" meaning navigate to /tmp/ with Nautilus as root and rename .X0-lock (I believe that is a zero in the name, not an O, but you want to be sure) something else, perhaps "0_Delete_me_later_if_this_works[.X0-lock]" and then maybe reboot.

[/FONT]
2. you might want to try installing some of the "suggested". It might be that one of them really should be marked depends.

3. Try the other suggestion in the error message, to whit: "[FONT=Courier New]Please consult the The X.Org Foundation support at [http://wiki.x.org]("http://wiki.x.org/") for help".

I hope you solve it, but for the future, I have a suggestion that might make it less trouble for you to reinstall the whole system when you run into something like this: Keep your data on a separate partition and back up the system installation partition or partitions regularly. I believe you can do this  when booted from the installation you are backing up with FSarchiver although I haven't tried that or Remastersys if the installation isn't too big for Remastesys. If you can boot from another partition, there are several tools you can use including, FSarchiver, DD, or Partimage. This has the advantage that you can continue to use your computer for other things while you are backing up that installation. Alternately you can boot from a Clonezilla CD and back up your installation that way. Probably you could do the same with a regular Ubuntu CD if you install one of the backup tools after you boot from it but I haven't tried that.
[/FONT]

---

### Post by bluswall on 2012-04-11
Hi
 I'm new to this forum and this seem like the best match to my problem.
   My system consist of an AMD A6-3650 2.6 ghz APU with ATI HD6530D graphics, 4GB ddr3. I am dual booting Windows XP, ubuntu 10.04 (working fine) and am trying to upgrade from 10.10 (seperate partition) to 11.10 I get a purple screen with the stick-man (sub-menu with onscreen keyboard etc ), the speaker icon, the digital clock and the exit icon . Nothing else seem to work. 
     Does anyone have a similar problem or have an idea of what is going on?

---

### Post by Dreamer Fithp Apprentice on 2012-04-18
> **bluswall said:**
> Hi
 I'm new to this forum and this seem like the best match to my problem.
   My system consist of an AMD A6-3650 2.6 ghz APU with ATI HD6530D graphics, 4GB ddr3. I am dual booting Windows XP, ubuntu 10.04 (working fine) and am trying to upgrade from 10.10 (seperate partition) to 11.10 I get a purple screen with the stick-man (sub-menu with onscreen keyboard etc ), the speaker icon, the digital clock and the exit icon . Nothing else seem to work. 
     Does anyone have a similar problem or have an idea of what is going on?

If I understand you correctly, you have 2 bootable OSs that are ok, and a third that was 10.10 that turned into something that doesn't work when you tried to update it to 11.10, right? If so, and you want to put 11.10 on that partition, why not just start over and install it again? If you have no login doodad with your user name showing it is obviously not right and the effort of tracking down and fixing whatever went wrong in installation or upgrade is almost sure to be far greater than just starting over  by downloading an iso and burning a CD for 11.10 (if you haven't already) and installing de novo to that partition. If you waited this long, I think you would do well to just stick with your 10.04 for now and wait for 12.04 which will be another LTS, due out any day now. And if you poke about the forum and google ubuntu on the internet you'll see that although it is contentious, 11.10 has been a huge disappointment to many of us. So why borrow trouble when in just a few days, they might just put out something better? I'd hang on to your working 10.04 for a while though. You may not like the new UI and if so you'll want to have a bootable OS that is usable while you either tinker with the new one long enough to see if you like it or try something else altogether.  Personally, I regret the absurd amount of time I've put into trying to make Oneiric fairly usable in the fashion I prefer to use it. I've been tinkering with it since it came out and I STILL haven't got it right. If I had it to do over I would abandon Ubuntu after Maverick. As it is, since 12.04 is almost ready I'm going to give it one more try but with an eye toward cutting my losses rather than get sucked in to the horrible time sink of trying to fix things that don't "just work" the way I want them to. I say that, not to discourage you from trying 12.04, I intend to myself and it may be fine, but just to caution  you from deleting the 10.04 too casually, until you KNOW you have something you like better. I always have at least two OSs bootable, at least one that is dependable and one to experiment with, and more than 2 when I have the drive space.

---

### Post by mgrameshbabu on 2012-04-19
> **Miguel2A said:**
> [FONT=Arial]Hi all people
I'm taking my first steps in this distribution Ubuntu and I downloaded Ubuntu 11.10
Everything worked fine until by mistake instead of install a program I uninstalled another named: udisks.

Now, when I start the PC shows a graph screen where asked to "enter  password" (before didn’t do that). However, despite entering the correct  password, the system seems to enter to desktop showing a black screen  but after a few seconds it back to starting point, ie "enter password"
I can enter to the console with:[/FONT]

[FONT=Courier New][SIZE=2]Ctrl+Alt+F1[/SIZE][/FONT]

[FONT=Arial]Over there I can login with my username and password,  even as "root". From there I tried to reinstall the program that I was  uninstalled with:[/FONT]

[FONT=Courier New]apt-get install udisks[/FONT]

[FONT=Arial]and apparently installed it. I rebooted but the problem remains the same.
Also execute the following commands because I thought the problem came from the graphic driver as it is not display the desktop.
[/FONT]
[FONT=Courier New]dpkg -configure -a
apt-get update
apt-get dist-upgrade
dpkg-reconfigure -phigh xserver-xorg
reboot
[/FONT]
[FONT=Arial]And there are no changes!
Anyone have any idea how to fix it without having to reinstall everything like Bill Gate’s operating system.
Thanks in advance[/FONT]
Hi Miguel2A,
I mam also facing the same problem. Did you get any solution of your problem? I am also new to Ubuntu. I got struck-up with this problem. If know the solution please inform me,

---

