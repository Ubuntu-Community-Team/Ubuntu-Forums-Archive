---
title: "plymouth logo resolution"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-05-14
okay, i really don't like the plymouth logo turning fat and ugly while starting up and shutting down my ubuntu 10.04 system. it was not so previously. i remember pressing F2 as the display message while booting the system on my laptop asks for to enter into BIOS setup. it did not entered into BIOS setup instead kept booting normally. so i tried hitting DEL+F2 as this might help in most cases i had known. so since then the plymouth resolution is turned to this ugly fat type. it's not a big deal as i have my system running normally but you see i just hate that ugly green logo. it sucks! please help.

---

### Post by jtarin on 2012-05-14
[This is what you need..]("http://ubuntuguide.net/plymouth-manager-gui-tool-to-change-initial-splash-screen-themes-in-ubuntu")

---

### Post by Face-Ache on 2012-05-14
Does that Plymouth Manager mess with the Grub at all?

I was trying to change my Plymouth screen using Super Boot Manager's Plymouth function, couldn't get it to work, obviously played with something i shouldn't have, and ended up booting to a black screen  :(

As a novice Ubuntu user, i had to do a full HDD format and reinstall to get it sorted out.

So i'm reluctant to muck around with Grub stuff anymore - i can get over an ugly boot screen as long as my system works (The "If it ain't broke, don't fix it" way  :) )

---

### Post by tojonukokhadush on 2012-05-14
thankyou all for your suggestions.
i guess i ll go with Face-Ache's suggestion as i am not into these internal system stuffs!

---

### Post by jtarin on 2012-05-14
> **Face-Ache said:**
> Does that Plymouth Manager mess with the Grub at all?

I was trying to change my Plymouth screen using Super Boot Manager's Plymouth function, couldn't get it to work, obviously played with something i shouldn't have, and ended up booting to a black screen  :(

As a novice Ubuntu user, i had to do a full HDD format and reinstall to get it sorted out.

So i'm reluctant to muck around with Grub stuff anymore - i can get over an ugly boot screen as long as my system works (The "If it ain't broke, don't fix it" way  :) )
No....but make backups when your not sure of anything.

---

### Post by Face-Ache on 2012-05-14
So backup the Grub to a USB drive? How would you actually go about doing that please?

---

### Post by jtarin on 2012-05-15
> **Face-Ache said:**
> So backup the Grub to a USB drive? How would you actually go about doing that please?No I meant backup your files in case you can't boot for some reason. This is what seems to concern you the most. Reinstalling Grub is simple.

---

### Post by tojonukokhadush on 2012-05-18
i guess this site is going to be useful to me and others regarding this problem.


[http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu](http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu)

---

### Post by jtarin on 2012-05-18
> **tojonukokhadush said:**
> i guess this site is going to be useful to me and others regarding this problem.


[http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu](http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu)
It would seem so. Seek and you will find.;)

---

### Post by Face-Ache on 2012-05-18
The link that tojo posted above doesn't work for me, as i don't have any '10_linux' file in that directory (I'm running Ubuntu 11.10), when they ask you to enter; 
```
gksu gedit /etc/grub.d/10_linux
```

I do have a '10_linux_proxy' file, but it doesn't have anything like GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7" listed.

jtarin, i'm not worried about backing up files on this PC; i've learnt from experience that Linux is quite unforgiving - change one parameter incorrectly, and boom, you suddenly can't boot - so i don't keep anything important on this hard-drive, it's all on an external.

Don't get me wrong, i'm not ragging on Linux, just saying that as an Operating System, it assumes you know what you're doing. Probably why it puts a lot of novice users off.

---

### Post by jtarin on 2012-05-18
> **Face-Ache said:**
> The link that tojo posted above doesn't work for me, as i don't have any '10_linux' file in that directory (I'm running Ubuntu 11.10), when they ask you to enter; 
```
gksu gedit /etc/grub.d/10_linux
```

I do have a '10_linux_proxy' file, but it doesn't have anything like GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7" listed.

jtarin, i'm not worried about backing up files on this PC; i've learnt from experience that Linux is quite unforgiving - change one parameter incorrectly, and boom, you suddenly can't boot - so i don't keep anything important on this hard-drive, it's all on an external.

Don't get me wrong, i'm not ragging on Linux, just saying that as an Operating System, it assumes you know what you're doing. Probably why it puts a lot of novice users off.
I look for that "/etc/grub.d/10_linux" when I get home later...not on my Ubuntu machine at present.You could go to that directory using Nautilus and see if there is something comparable to that file. Maybe just a number change.At one time I think it was Debian_5 or something as such.....it seems to be a moving target according to the developers.
As to backing up.....it's good sense no matter what OS you use. Everyone does a backup differently. You can back up your "Home" directory or place it on a separate partition, that way it isn't overwritten next install. Some make a partition for /etc,/boot,/var......get the point? It's up to you what you want to keep. Me? I just make an image of my partition weekly and back up from that if needed.

---

### Post by tojonukokhadush on 2012-05-18
okay, i posted the link just hoping it might help someone; but i was still reluctant to use it in mine coz i completely agree with faceache! i can't just figure out when ubuntu cease to work!! missed one step and it's goin' to cost you your OS. else ubuntu is still the best.

---

### Post by Face-Ache on 2012-05-18
I believe the file jtarin is talking about is called 05_Debian_Theme, but there's no GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7" listed in it.

I went through every file in that grub.d directory, and i can't see any one of them containing GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT vt.handoff=7" - looked through them, but also searched for any instances of vt.handoff=7.

So yeah, i'm still at a bit of a loss, and without any kind of definitive solution to the Plymouth screen, i think Grub is a thing best left alone!!  :)

It might not look very pretty, but if it ain't broke, don't try and fix it! I can live with a few ugly lines of code at boot/shutdown when my desktop looks so blingin'  :D

---

### Post by tojonukokhadush on 2012-05-18
hey guys do not misinterpret my excitement for ubuntu but i found this that might be helpful ;-) but its for 10.10 and do forgive me; m still not goin' to try the one on my own :-D


[http://www.n00bsonubuntu.net/content/install-ubuntu-10-10-plymouth-theme-on-ubuntu-10-10-maverick-meerkat/](http://www.n00bsonubuntu.net/content/install-ubuntu-10-10-plymouth-theme-on-ubuntu-10-10-maverick-meerkat/)

---

### Post by jtarin on 2012-05-18
I'll be home in a few hours.....hold on till then. There is a solution I made it work for mine.

---

### Post by jtarin on 2012-05-19
[Plymouth Manager- A nice tool to change plymouth resolution and boot theme in Ubuntu]("http://sourceforge.net/projects/plymouthmanager/")

---

### Post by Face-Ache on 2012-05-19
Awesome, cheers - will that be okay for 11.10?

---

### Post by jtarin on 2012-05-19
> **Face-Ache said:**
> Awesome, cheers - will that be okay for 11.10?
No problem!:p

---

