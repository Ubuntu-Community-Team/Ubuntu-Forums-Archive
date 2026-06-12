---
title: "Getting Frustraded!"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by londonlad on 2008-06-21
hi all,

i have an ADVENT 5301 laptop & i **cannot** get Ubuntu to install! :(

there must be an Ubuntu geek out there who can help me?

---

### Post by the_doc on 2008-06-21
Can you provide a few specifics as to your problem?

---

### Post by hyper_ch on 2008-06-21
(1) it is adivced to use a descriptive thread title that reflects the content of the post/inquiry/problem and not a generic one like "noob here" or "help needed"

(2) you just say you cannot install ubuntu.... however you don't give any information. It's like I'd say "I cannot watch tv"....

---

### Post by drs305 on 2008-06-21
You will have to be more specific about the type of problems you are having.

Here is a great site for helping you get started - from planning partitions, burning the ISO to post-install advice:
[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")

---

### Post by londonlad on 2008-06-21
ok guys,

i reboot my lappy with an original 8.04 cd, i get to the menu where you can choose to run ubuntu from the cd or install it etc etc. i choose to run it from the cd.........i get to the ubuntu loading screen then it simply freezes up on me!:(

i **did** manage to get the 6.06 live cd up n running, i needed to change the VGA settings though!

---

### Post by hyper_ch on 2008-06-21
did you make a cd check for defects?

---

### Post by londonlad on 2008-06-21
> **hyper_ch said:**
> did you make a cd check for defects?

yes i did, that freezes up too! :(

---

### Post by hyper_ch on 2008-06-21
then I think there's a problem with that cd...

---

### Post by nvteighen on 2008-06-21
Have you burned the disc yourself or was it shipped to you?

If you burned it, have you performed a checksum to the .iso file before burning it (see [https://help.ubuntu.com/community/HowToMD5SUM)?](https://help.ubuntu.com/community/HowToMD5SUM)?) And burned at the lowest speed?

Those steps will catch most CD defects... Of course, avoid to accidentally move the desk where the burner is working (a common cause for CD corruption which is often forgotten).

---

### Post by londonlad on 2008-06-21
the 8.04 cd was shipped to me, ive even burnt the 8.04 .iso file to cd & tried........same thing! :(

if i try to check the cd for defects or run ubuntu from the cd, this is what happens & everything just freezes:

[IMG]http://i164.photobucket.com/albums/u11/simonrogers_video/IMG_0003-1.jpg[/IMG]

i cant see there being anything wrong with the 8.04 cd coz i installed 8.04 alongside xp on my desktop & that installed fine!

---

### Post by WitchCraft on 2008-06-21
If you had to reconfigure your VGA settings then there might just be a problem with your graphics card driver.

You can use the alternate install cd, where you can install in text mode, which will allow you to resolve your driver settings problems. 

```

sudo dkpg-reconfigure xserver-xorg

```

But you need to know the settings of your graphics/video card.

In old Linux with xfree86 you could use SuperProbe, but since linux changed to xorg, SuperProbe is not available anymore.

You can try to install FreeBSD first, i think they still have SuperProbe.


Else, you can use the a little bit more complex way, with lspci:

lspci | grep "VGA compatible controller"
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

Then use the number obtained, in this example 00:02.0 with
lspci -vvv -s <number obtained>
```

root@all:~# lspci -vvv -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01c9
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at eff8 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

root@all:~# 

```

Which shows you how amongst other thins:
Graphics Card Manufacturer: Intel Corporation 
Model: Mobile 915GM/GMS/910GML Express Graphics Controller
Interrupt: IRQ 16
Frequency: 66 MHz
Video memory size: 256 MB ([size=256M])

---

### Post by londonlad on 2008-06-21
thats far too complicated for me.....im gonna try & install XP.....less hassle!

---

### Post by fatality_uk on 2008-06-21
> **londonlad said:**
> thats far too complicated for me.....im gonna try & install XP.....less hassle!

:lol:

Why bother...

---

### Post by londonlad on 2008-06-21
because xp is better than vista & ubuntu is being a real git to install! :(

---

### Post by cozmicharlie on 2008-06-21
Hate to see you give up, maybe another flavor of Linux will work better for you.  A couple come to mind, PCLinux ([http://www.pclinuxos.com/](http://www.pclinuxos.com/)) - this is very popular and many think much easier than Ubuntu.  Linux Mint ([http://linuxmint.com/](http://linuxmint.com/)) is also another good one to try.  If i had to choose one I would go with PCLinux.

---

### Post by WitchCraft on 2008-06-21
> **londonlad said:**
> because xp is better than vista & ubuntu is being a real git to install! :(

you just need to disable the UAC and the security settings in Vista, then it works fine.

additionally, the admin account has changed. If you're a normal admin now, you're just in the admin group, not the 'Administrator' user. 

So Vista has adopted the Linux root account and called it 'Administrator'.
If you are a normal admin user, you're just in the 'root' user group, so you have extended privileges, but you aren't allowed to change files owned by 'Administrator' without explicit permit (=infinite amount of affirmation mouseclicks...)

So all you need to do to get Vista to work just as XP is to login as 'Administrator', that is to say, 'root'.

Then it works just as fine as XP. Just that the (so called) 'security' is now 'offline'.
But: who cares, it's Windows, it's insecure anyway...

---

### Post by Dbugger on 2008-06-21
Since you are going to install a microsoft OS, why dont you try using Wubi, and install it from Windows, instead of using the live CD boot?

---

### Post by londonlad on 2008-06-22
> **WitchCraft said:**
> you just need to disable the UAC and the security settings in Vista, then it works fine.

additionally, the admin account has changed. If you're a normal admin now, you're just in the admin group, not the 'Administrator' user. 

So Vista has adopted the Linux root account and called it 'Administrator'.
If you are a normal user, you're just in the 'root' user group, so you have extended privileges, but you aren't allowed to change files owned by 'Administrator' without explicit permit (=infinite amount of affirmation mouseclicks...)

So all you need to do to get Vista to work just as XP is to login as 'Administrator', that is to say, 'root'.t

Then it works just as fine as XP. Just that the (so called) 'security' is now 'offline'.
But: who cares, it's Windows, it's insecure anyway...



how do i do the above? someone suggested PCLINUXOS to me.....that freezes up too......just about given up with linux now! :(

---

### Post by k3lt01 on 2008-06-22
What's your specs, things like RAM, HDD size, graphics etc? in other words the things that make your computer work. I know that if you don't have enough RAM you will have difficulty installing it just like Vista will not even attempt to install on a machine with less than the recommended amount or RAM. If that is the case use the alternate install CD as it doesn't need as much RAM apparently to install.

Just one last thing, if you are so willing to give up on Ubuntu after this then I hope XP doesn't start giving you grief cause you'll end up giving up with PCs with the grief it can give you.

---

### Post by WitchCraft on 2008-06-22
> **londonlad said:**
> how do i do the above? someone suggested PCLINUXOS to me.....that freezes up too......just about given up with linux now! :(

To disable Vista UAC:
[http://www.petri.co.il/disable_uac_in_windows_vista.htm](http://www.petri.co.il/disable_uac_in_windows_vista.htm)

To enable the 'Administrator' account:
[http://answers.yahoo.com/question/index?qid=20070327015326AAT27hL](http://answers.yahoo.com/question/index?qid=20070327015326AAT27hL)

I think alternatively you can press CTRL-ALT-DEL twice on the login screen, then appears a box with username and password.

Then you write in username: Administrator
and click ok, without password. Then you should be logged in as Administrator.


And I think you can also disable the annoying 'This is an exectable file format potentially containing a virus - please click yes if you really want to execute it' - warning by adding .exe and .com files to trusted filetypes.

---

### Post by Joeb454 on 2008-06-22
Did you try booting the Ubuntu CD in safe graphics mode?

---

### Post by Paqman on 2008-06-22
> **WitchCraft said:**
> you just need to disable the UAC and the security settings in Vista, then it works fine.


That's a really bad idea. UAC is a move towards a more *nix-like security model. The minor nag-factor is well worth it for the improvements in security.

---

### Post by WitchCraft on 2008-06-22
> **londonlad said:**
> how do i do the above? someone suggested PCLINUXOS to me.....that freezes up too......just about given up with linux now! :(

You have a problem with the Debian graphics card driver configuration program.
That won't go away if you take another Debian based Linux...

You could try Gentoo, or maybe Linux Mandrake. 
Mandrake sometimes works when all other Linux's fail.
Then you copy the configuration file from Mandrake and install the Linux you want ;-) I did so when I had to configure the graphics card for OpenBSD... IT WORKED !

---

### Post by WitchCraft on 2008-06-22
> **Paqman said:**
> That's a really bad idea. UAC is a move towards a more *nix-like security model. The minor nag-factor is well worth it for the improvements in security.

I've never considered an infinite amount of annoying pop-ups, that you start not even reading anymore to be adding anything to security...

The problem is when you run windows installers from a normal vista admin account as administrator (sudo) then it's a .exe file calling a .msi file. Then the .exe runs as administrator and the .msi as normal user. Consequently, installation fails, even if you ran it with the windows version of sudo...

And changing the startup menu by hand gives you an almost infinite amount of 'do you want to elevate your privileges' pop-ups...

Besides, you cannot add dll's to the system32 directory, and you cannot overwrite files there, if you're not administrator...

And the UAC is a worthless piece of crap.

---

### Post by WitchCraft on 2008-06-28
Bump :lolflag:

---

