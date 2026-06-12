---
title: "Ubuntu &amp; WinXp DualBoot Graphical HowTo"
date: 2006-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by h.mehdi on 2006-02-10
Hi Friends,

I've prepared a graphical "Breezy & WinXp DualBoot Installation HowTo" at : 
[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

Your comments and ideas will make the guide more complete and userfriendly...:) 

Hope it's usefull for newbies

****
PS: This Guide has these chapters now:

Installing Ubuntu 5.10 & MS Windows Xp On HDD

    * Installation on a new or completely formatted HDD

         1. Installing MS Windows Xp on a new HDD
         2. Creating new partitions using GParted
         3. Installing Ubuntu 5.10 on this HDD

    * Installation On HDD with already installed and Working MS Windows Xp

         1. Editing and creating partitions using GParted
         2. Installing Ubuntu 5.10 on this HDD

Graphical Boot Management using GAG

   1. Downloading GAG
   2. Coping and preparing GAG on a floppy in MS DOS
   3. Coping and preparing GAG on a floppy in MS Windows
   4. Coping and preparing GAG on a floppy in MS Windows Xp
   5. Coping and preparing GAG on a floppy in Linux
   6. Configuring & installing GAG on HDD
   7. Uninstalling GAG from HDD

MS Windows Xp & Ubuntu 5.10 reinstallation on same HDD

   1. MS Windows Xp reinstallation
   2. Ubuntu 5.10 reinstallation

---

### Post by Nu-Buntu on 2006-02-10
H. Mehdi,

You did a terrific job on this. I am sure it will help many.

I do have a question though . . .

Why use GAG instead of Ubuntu's installation of Grub? I have set up several dual boot machines and find Grub has worked fine. I know Leo Laporte has mentioned GAG as a favorite on "Call For Help" ([www.callforhelptv.com](www.callforhelptv.com)), but I don't know much else about it.

Thanks!

BTW, I like your signature poem.

---

### Post by Robor on 2006-02-10
Very nice HowTo!  :D

I have to ask the same question as Nu-Buntu though.  I'm a Linux (Ubuntu) noob and (using some online references/how-to's) even I managed to get my WinXP Pro and Ubuntu dual boot system going on the first try using the standard Grub tool.

---

### Post by h.mehdi on 2006-02-11
Dear Nu-Buntu & Robor,

Thanks, Hope it can help newbies at least!

GAG is the best Graphical Boot Manager I know, it has many good features you may read more about GAG features here : [http://gag.sourceforge.net/](http://gag.sourceforge.net/)
And this guide can be used as a GAG HowTo also, for people interested in installing and using GAG...;) 

Please note that GAG is not something instead of GRUB or LILO, GAG is not a BootLoader... This means that you need GRUB or LILO beside GAG
BUT if you want to use GAG you should not install GRUB on your HDD's MBR as I've mentioned in this HowTo....

GAG is very usefull when we need to reinstall windows on a dualboot HDD, we don't need to recover GRUB after reinstalling windows (there is a section for reinstalling windows or Ubuntu in this HowTo)...

---

