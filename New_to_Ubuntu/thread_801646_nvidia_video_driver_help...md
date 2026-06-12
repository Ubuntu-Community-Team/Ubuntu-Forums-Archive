---
title: "nvidia video driver help.."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Deckoh on 2008-05-20
big time noob here :confused:

if i run the compiz-check program i get this. 

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
 Driver in use:         Unknown
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on Compiz' whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not known to work with Compiz and thus may be blacklisted on
 certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n


when i go into system/admin/screens and graphics. it shows the nv driver is in use. the reason i am asking is i have some problems with video streaming and weird flashes when booting up and shutting down. any help is appreciated.

---

### Post by Xiong Chiamiov on 2008-05-21
Did you install the driver manually, or through the repos?  Have you tried using Envy? (it's in the repos)

---

### Post by randallecook on 2008-05-21
On my system I could only get the compiz effects after installing the "restricted" (i.e. closed-source) nVidia driver. If you can stomach the ethical implications of closed-source code on your system, I found the nVidia driver that the restricted/hardware drivers configuration panel found worked great. I now have a very gooey GUI. Tasty.

---

### Post by Xiong Chiamiov on 2008-05-21
Oh, if you get the works-until-I-reboot problem after installing the NVIDIA drivers, try [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

---

### Post by Deckoh on 2008-05-21
i used envy to install. under restricted drivers it is enabled. dont get me wrong here, it does work.. just bothers me on the weird flashs and video steaming (even downloaded) pauses.

edit: i havent tried what you have linked to "Xiong Chiamiov"... i will this afternoon and post reply. thanks in advanced to all that have helped so far.

---

### Post by thevikingking on 2008-05-21
i have a problem with my nvidia restricted drivers... anytime i activate them the computer is fine till reboot, then i see colored lines on my screen and that is all that comes up... 

what do i do about this? i am a noob and am a code idiot...

---

### Post by Deckoh on 2008-05-21
@ thevikingking, "Xiong Chiamiov" said to use this.. not positive, but i belive this is the fix..

try [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").[/QUOTE]

---

