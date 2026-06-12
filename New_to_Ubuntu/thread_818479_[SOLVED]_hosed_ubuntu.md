---
title: "[SOLVED] hosed ubuntu"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-04
this would be a user error.

down to the nuts and bolts.  I boot w/o a disc in and GRUB goes on to say "Error 5" and won't let me pick any install.

I was going to overwrite my ubuntu partition for PCfluxboxOS because I had just had way too many apps on ubuntu.  (I had installed KDE, XCFE, Ubuntu Studio and so had tons of apps I was never going to use and didn't feel like going thru them and manually deleting them) and so went to synaptic and searched "KDE" and deleted all things there.  did that with the others too.  long story short I now get that error.  

Sooo.  here's what I want to do.

Install PCFluxboxOS (or Fluxbuntu but I know where the PCFluxboxOS CD is.  can't find fluxbuntu) ..  or **anything** lightweight..  and install it where the ubuntu partition was (I formatted it to try and make room for PCFluxboxOS following the draklive installer guide and it told me to reboot and click "use configured partitons" or something to that effect meaning choose what I've already got going:

"please select the type of HD install you will be doing" - I click normal HD.

"choose the sizes "root"/"swap".  I moved root all the way up and swap to 200.  size in MB.  

Here's my issue.  before I did this it had a nice screen to show my partitions.  I formatted the ubuntu partition and resized it to 80 gigs and figured I'd just reboot and click the 80 gig partition, then install and boom I'm good to go.

and now I'm screwed.

If this seems like I'm in panic mode..  it's because I am.

I need help to install *something*.  The only other computer I have access to has windows ME on it.  I hope to high heaven that I don't have to go out there and try and burn a linux distro on that but if I have to I will.

Thanks 1000 times over.

ps.

you can see my computer specs below.  this computer is only two years old so everything is working OK I just want to maximize the space I can use on it instead of having my OS taking up a lot of space.  what lightweight distros would you recommend?  I'm willing to try almost anything; but I would like my windows XP on here, too.  I'd like it to be about half and half.

Thanks again.

---

### Post by bobnutfield on 2008-06-04
Hello,

It looks like your partition table is messed up.  Try running PCLinuxOS as a live CD, open a terminal and type:

> fdisk -l

Post the results back so we can see where you have everything installed.

Bob

---

### Post by AnLGP on 2008-06-04
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         573       19183   149492857+   7  HPFS/NTFS
/dev/sda2               1         572     4594558+   b  W95 FAT32
/dev/sda4           19184       30401    90108585    5  Extended

Partition table entries are not in disk order

---

### Post by bobnutfield on 2008-06-04
I am not an expert at repairing your partition table, but I know it can be down with fdisk.  DO NOT TRY THAT UNLESS YOU HAVE STEP BY STEP INTRUCTIONS!  I am assuming you were trying to install on sda4.  You might try to install PCLinuxOS from the live CD and it should repair your partition table during the process.  Just be CAREFUL NOT TO INSTALL ON /dev/sda1 where your Windows partition is.  If that does not work, you can start a new thread HOW TO REPAIR PARTITION TABLE and one of the experts here will help (I have seen this before.)

Bob

---

### Post by AnLGP on 2008-06-04
I don't know where I was trying to install it via that table but I know I had allocated 80 gigs for it.

I won't mess with anything until I have step-by-step instructions.  Thanks!

---

### Post by Inxsible on 2008-06-04
Your best bet would be to do this:

Put in a ubuntu/kubuntu/xubuntu live CD in there and use the partion editor to first partition the drive. Make enough space for Linux and then install either PCFluxboxOS or Fluxbuntu in that partition. AFAIK, Fluxbuntu live CD does not work and so you will have to partition it in the command line which I don't think would be very intuitive.

As for lightweight distros there are a LOT of options :
Ubuntu minimal with any of the following WMs(Window Manager)
1)IceWM
2)Fluxbox or Fluxbuntu itself
3)Openbox
4)Blackbox
5)JWM
6)Enlightenment 17 - its in alpha release yet so you might have problems or OzOs 
7)PekWM

All those mentioned above are just WMs and not DE (Desktop Environment), so you will not get all the functionality of Gnome KDE or Xfce. You will have to install all the apps yourself. But they give you the flexibility to choose your own apps.

If that does not sound like your cup of tea, you should go with a standard DE - the lightest of which is Xfce.

---

### Post by AnLGP on 2008-06-04
Thanks.  That would explain why I can't install it.  I'll get ubuntu and strip it down to minimal over the weekend.

---

### Post by ubernuber on 2008-06-05
+1 to what inxibel said...

I started with xubuntu as well and I have already created a dual boot with a minimal install and I am relatively new to Linux :)

I feel proud :D

I still have the complete xubuntu install - just in case I screw up somewhere- at least I will still be able to go in one OS.

---

### Post by AnLGP on 2008-06-05
I'm trying to build debian from the ground up as we speak.  It's not working well :lolflag:

---

### Post by Inxsible on 2008-06-05
What are the problems that you are facing?

I would suggest that you first make a list of all the apps that you need and want on the install. For eg..something to this effect...

1) Xorg - obviously
2) File Manager -  PCManFM, emelFM2, clex(CLI based)
3) Window Manager - you have probably chosen one already
4) Editor -- I would suggest leafpad here..it does not have too many dependencies. Very lightweight
5) to get desktop icons - iDesk
6) to get panels - fbpanel is lightweight, but you can get xfce4-panel if you like too
7) A package manager - most ppl go with Synaptic here but there are others
8 )Browser - Kazehakase is lightweight but no plugins - firefox is the only choice which has all plugins opera to an extent.
9) Terminal - lots of choices - aterm, eterm, xterm, rxvt,mrxvt, urxvt, Sakura, tilda, xfce4-terminal...the list goes on
10)Image viewer - Mirage is lightweight
11) CD/DVD burner - Recorder - but you will have to compile this from source since I am not aware of any available deb packages. There might be some out there
12)you may need to install alsa-utils and alsa-conf and or alsa-oss for sound
13)your graphics card drivers
14)gFTP - for ftp
15)SSH - openssh-server
16)display manager - GDM, KDM, WDM, XDM - I am a minimalist and I dont install DMs at all. simply login at CLI and have a login script take you directly to your desktop. DMs are a waste of space after you login anyway :)
17) Time and Date management - orage
18 )

...If I rbr anything else.. I will add to that list. Now all you have to do is```
sudo apt-get install *package-name1 package-name2 ......*
```

---

### Post by AnLGP on 2008-06-05
I've been having a bit of behind the scenes help and have gotten off to a decent start.

I've got fluxbox as I'm trying to ditch DEs and go with a more trim system.

I'd like to learn clex but for the moment I'm sticking with thunar.

I've got cmus for my sound playing stuff and epiphany for the web browser.

i've heard osmo is good?

---

### Post by Inxsible on 2008-06-05
I dont use clex full time either... i do like to see icons in my file manager. I use PCManFM. Its great. Thunar is good too - the only problem is that it depends on a few xfce libs which I can do without..

When I go minimalistic... I guess I overdo it ;)

Oh and I have no clue about osmo

---

### Post by Predatorian on 2008-07-01
hello, im not sure if i can post here, but i have a question about fluxbuntu and sound. i downloaded all the updates when i got network connectivity, but when i try to download the alsa packages, it says it was included with the update, but the fluxbox menu that says alsa.conf, when i run it it says it doesnt exist. i went searching for it, and i cant find any scripts to help me  configure alsa so i can get sound out of my laptop. i found something called asoundconf, and it said to run $asoundconf list, and it listed two sound cards, IPX and Modem. im not sure where all to go from there.

my stats of this laptop that i am aware of are:
Compaq Presario V2000
Altec Lansing Speakers
1gb ram
80gb hdd
AMD Turion 64 
ATI Radeon Xpress 200m


any help is greatly appreciated. thanks guys.

---

### Post by Inxsible on 2008-07-01
> **Predatorian said:**
> hello, im not sure if i can post here, but i have a question about fluxbuntu and sound. i downloaded all the updates when i got network connectivity, but when i try to download the alsa packages, it says it was included with the update, but the fluxbox menu that says alsa.conf, when i run it it says it doesnt exist. i went searching for it, and i cant find any scripts to help me  configure alsa so i can get sound out of my laptop. i found something called asoundconf, and it said to run $asoundconf list, and it listed two sound cards, IPX and Modem. im not sure where all to go from there.

my stats of this laptop that i am aware of are:
Compaq Presario V2000
Altec Lansing Speakers
1gb ram
80gb hdd
AMD Turion 64 
ATI Radeon Xpress 200m


any help is greatly appreciated. thanks guys.The command is ```
alsaconf
``` without the dot in between. Try running that in a terminal. Let us know what you get.

---

### Post by Predatorian on 2008-07-03
i am unable to find that file, and when i do a search for it, i only find alsa in my /usr/share folder, then i have alsa and alsa-base. the contents of those are: 

# this is my /usr/share/alsa folder
alsa.conf
cards
pcm
smixer.conf
sndo-mixer.alisp
speaker-test
user-must-execute-asoundconf-set-default-card.update-notifier


# this is my /usr/share/alsa-base folder
alsa.default

is there a package im missing?

---

