---
title: "Hardy suddenly slow down on HP DV2000!!!"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by sarc on 2008-09-30
I have Hardy on an HP DV2000 and it ran very well until one day after update (included Firefox 3) one of my user accounts (in Chinese language option with screen effects) would log on OK but then Gnome would freeze, moving the mouse is very jerky and it takes minutes to get a response on a mouse click.  The hard disk spins constantly, looks like it's trying to page everything to disk, and the CPU load is 70-80%.  Now another user account in English language and no screen effects is getting slow.  I tried system monitor utilities and did not show any undue processes running.  What's going on?  I'd really rather not reinstall.  And my Grub screen does not show an option to boot from previous (stable) versions like it did with Feisty.  THANKS!

---

### Post by gnrathon on 2008-09-30
sounds like your swap partition might be corrupted
the same thing happened to me and i saw that my swap wasn't working right

to fix it i just reinstalled

also try undusting your somputer

---

### Post by MrFSL on 2008-09-30
> **gnrathon said:**
> sounds like your swap partition might be corrupted
the same thing happened to me and i saw that my swap wasn't working right

to fix it i just reinstalled

also try undusting your somputer

Please ... you don't have to reinstall to fix a swap partition.

From the command line at boot up or at any other time you can choose to install a previous kernel version to get the "option to boot from previous" that you saw in feisty.

I would check you logs for errors. And perhaps create a new user and see if the problem happens in this new account. If it doesn't then it might be configuration issue with your accounts or software you have run on your accounts. You can back up your data and re-create your account if this fixes your issue.

---

### Post by gnrathon on 2008-09-30
gees...
no need to be condicending

---

### Post by MrFSL on 2008-09-30
> **gnrathon said:**
> gees...
no need to be condicending

My apologies. I simply did not want this person (or future persons) to think they had to reinstall. 

The "Please" in my previous post was meant to be "pleading" in nature - not leveled at you with sarcasm. 

My apologies if I offended.

---

### Post by sarc on 2008-09-30
Cheers guys I'll try to run gparted and reformat the swap partition as soon as I get home (I'm sure I could find out how to do it from CLI but I'm time challenged!)  Will let you know how it goes.

---

### Post by sarc on 2008-09-30
Nope, reformatting SWAP didnt help.  Back to square 1.

---

### Post by sarc on 2008-09-30
Improvements!
I booted on safe mode, ran all the safety tests (X server and all other stuff on screen).  I ran apt-get thingy (forgot...) to clean out some garbage.  Ten cleaned the notebook and pressed hard the RAM in its socket.

Not the computer boots OK - one last weird thing!  If I click on the "Logoff" red button, gnome crashes, all toolbars disappear!  I have to hit ctrl-alt-backspace to reboot.  Happens every time.  any ideas???  Thanks!

---

### Post by sarc on 2008-09-30
Same thing.  The moment I click the red logout button I loose all toolbars (desktop stays unchanged and mouse works).  I have to ctrl-alt-backspace to logout.  User switching works.   h  e  l  p  !  !

---

### Post by sarc on 2008-10-01
Thanks to all the advice, it helped and when I rebooted a few times the drives got scanned (it may have had some errors?), then suddenly the Gnome crash problems stopped.  WHEW!  All good now.

---

