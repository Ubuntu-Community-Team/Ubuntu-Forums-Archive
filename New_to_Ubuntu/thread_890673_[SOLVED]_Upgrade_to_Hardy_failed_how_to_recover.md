---
title: "[SOLVED] Upgrade to Hardy failed: how to recover?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-08-15
Hi guys!

I have been dual-booting XP/Ubuntu since Edgy.
I upgraded to Fiesty then Gutsy OK.
I just tried to upgrade to Hardy, but the installation hung (over an hour) with "8 minutes left..." necessitating a manual power-down.

Ubuntu now runs, but with lots of problems.

I guess this is the time for a clean install.
Can somebody please suggest the best (safest) way to do this?
I assume I should wipe out (reformat?) the old Ubuntu partitions, then boot to the 8.04 iso CD & install from there?
Or is there an easier way?

Presumably once I wipe out the partitions (except XP!) then I will no longer be able to boot to XP until I successfully install Hardy?
Maybe via the old GAG 4.7 boot disk??
I would like to be clear on this before starting!

I also think this is probably a good time to add a /home partition which I did not have previously.
Am I right in thinking I can use GParted to convert my old primary "shared" partition into an extended partition, then fill that with a new logical shared partition plus a new logical home partition?

Other hints & tips also gratefully received!  :)

---

### Post by iaculallad on 2008-08-15
Boot Ubuntu using Recovery mode:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
startx
```

---

### Post by 2CV67 on 2008-08-15
Thanks.

I have been through recovery mode & tried "repair broken packages" but even that sticks at the same place as the original installation (Generating locales en_AU.UTF-8...) needing REISUB to escape.

Basically I can boot Ubuntu at the moment, but I don't think I can repair it, so want advice on replacing (rather than upgrading or doing a fresh install).

Thanks again.

---

### Post by OldGrey on 2008-08-15
The quickest way is download an ISO of Hardy; burn it onto a CD; boot from the CD; select install; follow the instructions and install it over your current Ubuntu installation.

Sorry noticed you do not want to fresh install, but would like to replace. Not sure what the difference is, so can you epand a little on that?

---

### Post by 2CV67 on 2008-08-15
Sorry I was not clear enough!

I found plenty of instructions for upgrading from one level of Ubuntu (working OK) to the next level.
I found plenty of instructions for making a fresh installation of Ubuntu where there was nothing before.
What I want to do is make a good clean installation of Ubuntu where there is currently a corrupted version.
Without carrying over any of the corruption!
I don't think that is covered by either of the above.

Are you saying I can just install from the iso CD & that will overwrite perfectly any old Ubuntu underneath?
That would be simpler if it is sure to work.

Thanks a lot!

---

### Post by Stunt Double on 2008-08-15
That is interesting 2CV67 because on one of my Ubuntu computers I can't go beyond 7.10. With both an upgrade and a clean install, the computer hangs at exactly the same place.
  The computer is a IBM NetVista all-in-one with a 730 Mhz Celeron processor and 512MB of PC 133 memory.
Does anyone know if it is a known problem?

---

### Post by kansasnoob on 2008-08-15
> **2CV67 said:**
> Sorry I was not clear enough!

I found plenty of instructions for upgrading from one level of Ubuntu (working OK) to the next level.
I found plenty of instructions for making a fresh installation of Ubuntu where there was nothing before.
What I want to do is make a good clean installation of Ubuntu where there is currently a corrupted version.
Without carrying over any of the corruption!
I don't think that is covered by either of the above.

Are you saying I can just install from the iso CD & that will overwrite perfectly any old Ubuntu underneath?
That would be simpler if it is sure to work.

Thanks a lot!

After backing up anything I don't want to lose, I'd boot the new Hardy Live CD and then navigate to System > Administration > Partition Editor (aka, Gparted). Then I would manually delete the old Ubuntu partitions, including SWAP. Then you'll just end up with one unformatted space and when you double click the "install" icon on the desktop, after answering a few basic questions you'll come to a screen like this:

[ATTACH]81652[/ATTACH]

(Of course your partitions will look different! You should have one blank gray area where Ubuntu will install.)
Then just choose "Guided - use the largest continuous free space" and the installer will create the Ubuntu partition and a new swap partition.

Now, that's what I'd do, BUT I store all of my data on removable media and/or external drives so I don't worry about creating a separate home partition and such. If you want to create a separate home partition before reinstalling it's possible. 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then you'd want to use the "manual partitioning" option and create your own specific partitions. Something like this:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

---

### Post by kansasnoob on 2008-08-15
> **Stunt Double said:**
> That is interesting 2CV67 because on one of my Ubuntu computers I can't go beyond 7.10. With both an upgrade and a clean install, the computer hangs at exactly the same place.
  The computer is a IBM NetVista all-in-one with a 730 Mhz Celeron processor and 512MB of PC 133 memory.
Does anyone know if it is a known problem?

Are you sure you're not pinched for disc space?

At any rate my luck with upgrades has been about 50/50. Half the time it all works out fine and the other half I end up doing a clean install after trying.

---

### Post by OldGrey on 2008-08-15
To answer your question - yes. You can reformat the linux partitition as part of the installation and install a new clean version.

---

### Post by 2CV67 on 2008-08-15
Stunt Double:
That's bad news!

Kansasnoob:
Thanks for an excellent link.
I still want to have a separate /home though.

I don't think I am pinched for disc space.
My new partitions are:
XP 80Go
Ubuntu 10Go
Home 10Go
Share 10Go
Swap 1Go

Thanks OldGrey.

My PC is a desktop Acer T120-3000 with AMD XP 3000+ at 2.16GHz.
RAM upgraded from 216 to 512Mo.

I have now done my partition fiddling, without erasing anything, and downloaded 8.04.1, checked md5 & tried the CD & run the CD error check.

So I am now ready to either wipe the old Gutsy & install Hardy or simply install Hardy over the top.
Since I have created a new partition for /home, I am inclined to wipe out the old first.
Comments?

Is this all a waste of time if it is going to hang on clean install anyway???

---

### Post by redester on 2008-08-15
[CENTER][SIZE="4"][/SIZE][/CENTER]

I have done my ubuntu 7.0 system in by a wrong CHMOD command at ROOT!:(

I have the live 8.04 DVD in hand and am wondering if there is a way I can save my existing system with only an UPGRADE?

Oh yes!  I cannot access the modem either.... So, of course, no email is available for chit-chat with more knowledgeable folks in the Linux community.

Any help will be appreciated,

Ray   :confused:

---

### Post by kansasnoob on 2008-08-15
> Is this all a waste of time if it is going to hang on clean install anyway???

Well, definitely try running the Live CD first and check it for errors!

But your failures so far have been upgrading via internet, eh? If so that's no indication that installing from either a Live CD or an Alternate CD would fail.

BTW, where all you'd be replacing is the OS you'll definitely want to use manual partitioning.

---

### Post by 2CV67 on 2008-08-15
Thanks.

Yes I ran the live CD OK & checked it for errors OK.

I was just commenting on Stunt Double's problem where the installation hung both on update (exactly like mine) and then also on clean install - where I am going next!

---

### Post by kansasnoob on 2008-08-15
Oh, one additional thing. If you should choose not to create a new SWAP partition you'll end up in UUID hell! I only recently learned this:

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

The fix is easy but I thought I should mention it.

---

### Post by 2CV67 on 2008-08-15
Well...

I wiped out Gutsy (formatted old partition in GParted) and installed Hardy from the CD with no apparent problems! :):)

Also got fully updated via Synapt.

That was using ethernet.

All that remains is to get the rest up & running:
Wi-fi
Printer
Scanner
Networking with XP & Vista
Boot order
and a few others!

Took me months the first time round, but this time....

Thanks for all your help!

---

