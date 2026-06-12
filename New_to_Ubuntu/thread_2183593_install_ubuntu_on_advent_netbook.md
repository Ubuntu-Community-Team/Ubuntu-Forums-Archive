---
title: "install ubuntu on advent netbook"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by ukdave2 on 2013-10-25
Hi new to linux os i have installed ubuntu on a desktop pc for the wife no problems with running  so far but did not have much to do other than install as everything seems to work straight off i have an advent 4211 netbook not in use anymore so am wanting to install some form of ubuntu with educational software the netbook will then be given to our 6yrs old grandson have tried to install many times the install allways locks up at the same point it allows me to set language/time zone then locks up at the bootom of the install screen where the progress bar is it just says step 3 of 7 never gets any further this netbook is a rebadged version of the msi wind u100
netbook specs as below
advent 4211
intel atom n270 cpu
2gb ram ddr2
80gb hdd
there is a sticker on the back - msi model ms-6837d n1996
have tried several usb sticks for install none work i know the sticks are ok and have even loaded ubuntu onto desktop pc using same sticks have searched online found loads of solutions none seem to work i can run any os on the netbook as a live session from the usb no problems only get problems when trying to install to hdd this is my first post on here so i hope i have put my question over properly please help 
thanks in advance
David

---

### Post by ajgreeny on 2013-10-25
Are you doing this from the live desktop or are you installing from the first menu you see?

If you are trying to install from that menu, not from the live desktop, it may simply be that you need to boot the live system using a boot option such as nomodeset (there are several available options you can try) which you can see from pressing the F6 key when you boot the USB live system.

---

### Post by ukdave2 on 2013-10-25
Thanks for taking the time to reply i have tried to install from live desktop does not work when you say from the first menu i see i take it you mean the boot options on a black screen that appear before the desktop loads i have tried that as well but still no go i can get any distro to work on the netbook as live session everything works fine  just cannot install the os to the hard drive and i forgot to mention xp is running on netbook at the moment i have formated the drive and installed xp no problem i am thinking this could be a case of crappy advent drivers as i know someone with linux on an msi wind i am tempted to download the msi bios then try an install but shall leave that option till last.

---

### Post by The Cog on 2013-10-26
I have one of those Advent 4211 netbooks, same model. It currently runs Xubuntu 13.04 because I haven't got round to putting 13.10 on it yet. Mine also has 2G ram - I upgraded it from 1G after the warranty expired. 
So there is no fundamental reason why Ubuntu should not work, although I gather that Ubuntu is quite demanding these days, and it may be worth trying Xubuntu or Lubuntu instead as these don't need such a beefy machine. 

I have never needed any special steps to get the install to work, although I always do a custom partition because I keep 3 partitions - two of 15G as the root of two different 'buntu versions, and a large partition as /home for whichever root version I'm currently using. This allows me to test each new release without losing the last working one. I can't imagine that the way I partition has much to do with the problem though. I wonder if you have a problem with the disk drive hardware that mucks up the installation.

---

### Post by ukdave2 on 2013-10-26
This has me stuffed never had a problem installing an os on anything before but cannot install any linux os at all on this netbook i have deleted xp formated drive then reinstalled xp + drivers no problem i can run any linux os as a live session everything works as should but no go with the install just as i said in my first post the install starts ok but then hangs the computer when it says step 3 of 7 that is as far as it goes i have searched all over the net seems it is a common problem none of solutions i have found do any good reckon i will just dban the drive and try from there what do you think and thanks for the reply

---

### Post by The Cog on 2013-10-26
You really ought to look at getting your full stop key fixed.

I don't want to rub your nose in it, but I just installed Xubuntu 13.10 onto my Advent and am posting from it now.
I wonder if your Advent has a hardware problem - disk or memory perhaps. I think the live CD has a memory test option, and I know that you can install gnome-disk-utility while running from a live CD, which can then look at the disk SMART data and show if it is giving errors.

Finally, try intalling Xubuntu rather than Ubuntu. I can vouch for Xubuntu on the Advent, but have not tried Ubuntu.

---

### Post by v1k1ng1001 on 2013-10-26
I would second trying to install something lighter like lubuntu.  After, you can install any desktop experience you want.

My atom n270 is running 12.04 with unity 2d like a charm but I haven't upgraded it.

---

