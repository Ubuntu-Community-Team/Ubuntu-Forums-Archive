---
title: "New 2.6.24 -20 Kernel, Better luck Guys!"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-28
Hey Guys,
i'm currently downloading another 2.6.24-20 Kernel Update as well as some other stuff. To all the guys who had booting problems last time around, hope you have better luck this time!

Good luck.

---

### Post by cdtech on 2008-07-28
I just upgraded to the -21 myself....

---

### Post by BGFG on 2008-07-28
Wow, I only have the 'proposed' enabled, can't afford to break my one machine. come across any bugs yet ?



Excuse me while i restart... :)

---

### Post by cdtech on 2008-07-28
Only one so far. lol

My "iwconfig wlan0" command show's nothing, although I can connect via wireless.
```

wlan0     IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:217  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

---

### Post by BGFG on 2008-07-29
So i restarted, and then some.... Still stable though. I think it's just me, but everytime i do a kernel update i tell my self that the system responds faster and my screen is brighter...How sad, i know..

So now i'm getting Alpha3 for Intrepid Ibex from Softpedia, they have direct download and a torrent file.. (using the torrent)
I'll try it in VirtualBox tomorrow.

Yourself ?

---

### Post by PmDematagoda on 2008-07-29
> **BGFG said:**
> So i restarted, and then some.... Still stable though. I think it's just me, but everytime i do a kernel update i tell my self that the system responds faster and my screen is brighter...How sad, i know..

Perhaps it's because you don't use an Nvidia or ATi card on that PC?

---

### Post by nycste on 2008-07-29
i upgraded by mistake to 2.6.24-20

i had to reconfig vmware, and reinstall nvidia with envyng... once that was done i notice no difference and no issues

my modem died lol but i dont think its cuz of the kernal, modem is replaced fyi :)

im always dying to be bleeding edge and have all the updates, but im quickly learning in ubuntu linux thats not always a good thing unless your pretty good with linux/ubuntu and settings etc

just wanted to share my experience

---

### Post by PmDematagoda on 2008-07-29
> **nycste said:**
> im always dying to be bleeding edge and have all the updates, but im quickly learning in ubuntu linux thats not always a good thing unless your pretty good with linux/ubuntu and settings etc

just wanted to share my experience

That usually depends on your hardware, the nvidia-glx packages probably weren't uploaded for -20 yet(and perhaps even fglrx along with some other packages) which caused the problem for so many people on Nvidia and ATi VGA cards. If someone using an Intel VGA card had updated to -20 then the issues he faces would be much less compared to the others.

---

### Post by nycste on 2008-07-29
> **PmDematagoda said:**
> That usually depends on your hardware, the nvidia-glx packages probably weren't uploaded for -20 yet(and perhaps even fglrx along with some other packages) which caused the problem for so many people on Nvidia and ATi VGA cards. If someone using an Intel VGA card had updated to -20 then the issues he faces would be much less compared to the others.

you might be 100percent correct, i have no clue lol...

but like i said to upgrade a kernal, and only have to reconfigure vmware and just hit enter 200times and then reinstall nvidia drivers using envyng was a pretty simple task once i learned how

im tempted to learn how to do system backup, save it.. then install or have to compile latest kernal and throw that on, then upgrade nautlis too :) but there are bugs with that im reading, not necesially with the latest kernal which is 2.6.26 something right

---

### Post by waspbr on 2008-07-29
awesome!awesome!awesome!awesome!

have I mentioned this is awesome? 

I just updated my desktop and I can finally boot in the new kernel, bah-bye kernel -19.

sorry but I get really giddy when there's a kernel update, I always expect that the update is going to bring more features and make the ride even smoothier... but yeah I am a techie... and damn proud of it.:D

---

### Post by wariskampar on 2008-07-29
How come I don't get update notification for this new kernel. I'm still using 19

---

### Post by PmDematagoda on 2008-07-29
> **wariskampar said:**
> How come I don't get update notification for this new kernel. I'm still using 19

That might be because you don't have the proposed updates repository enabled.

---

### Post by wariskampar on 2008-07-29
All this while, i'll get notification on new kernel released. Btw, how to enable 'propose update' feature.

---

### Post by philinux on 2008-07-29
Because the OP is using bleeding edge, read buggy, proposed repo.

[https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security](https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security)

> Proposed is the testing area for -updates. A number of people must give positive feedback on these packages before they are allowed into -updates. This repository is recommend to ONLY interested in helping to test updates and provide feedback. Since they are in effect testing updates, there is a higher chance of defective updates in this repository.

Not recommended for your main machine.

---

### Post by wariskampar on 2008-07-29
ok! Thanks philinux. So far 19 is good for me

---

### Post by NilsE on 2008-07-29
> **BGFG said:**
> I think it's just me, but everytime i do a kernel update i tell my self that the system responds faster and my screen is brighter...How sad, i know..

Yourself ?
Hey, I am with you on this one.  It is just like when you wash your car it seems to run so much better.:lolflag:

Oh yeah, update worked fine for me but I don't have any of the problem hardware (see below)

---

### Post by BGFG on 2008-07-29
> **PmDematagoda said:**
> Perhaps it's because you don't use an Nvidia or ATi card on that PC?

You Hit the nail on the head :) My Nvidia is onboard..
HA HA!! and as i post to you guys i see new updates!! 
:( It's just firefox... Oh yaay.

Only thing i had to do this morning is reload my VB kernel thingy. That's kind of obvious : new kernel, reload kernel thingy :)
I still can't install intrepid in VB though. Tells me it's only seeing an i586 architecture. i downloaded the amd64 iso. Might start a new thread for this if i can't suss it.

Though since VB 1.6.2 64 bit support is enabled, or supposed to be. 
You think aptitude update ?

I'm off to wash my firefox NilsE....

---

### Post by chewit on 2008-07-29
Using -20 now, all seems to be running fine :D

Specs are below and I'm using WiFi which works fine!

---

### Post by BGFG on 2008-07-29
Nice to see someone with no wifi problems...

The firefox update was for 3.0 my current was 3.0.1 After the update, I still ran it cause the tray had the lil red arrow with the exclamation mark in it, It's as though he admonishes you until you update :), My version still says 3.0.1 so whatever.

Maybe update manager just dosn't go into all that detail.

---

### Post by philinux on 2008-07-29
> **BGFG said:**
> Though since VB 1.6.2 64 bit support is enabled, or supposed to be. 
....


[http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

---

### Post by ibuclaw on 2008-07-29
Why all the fuss about 2.6.24?

I'm on a vanilla 2.6.26 kernel straight from the kernel.org git repository, er, last sync'd about 4 hours ago... :D

---

### Post by BGFG on 2008-07-29
> **philinux said:**
> [http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

Oh Crap. :(

Thanks Philinux....

---

### Post by BGFG on 2008-07-29
> **tinivole said:**
> Why all the fuss about 2.6.24?

I'm on a vanilla 2.6.26 kernel straight from the kernel.org git repository, er, last sync'd about 4 hours ago... :D

So in which Kernel is Ext4 going to be ?

---

### Post by ibuclaw on 2008-07-29
> **BGFG said:**
> So in which Kernel is Ext4 going to be ?

Ext4 Supported \o/
but you are adviced not to use it as your / root filesystem yet for stability reasons... :(

And I believe that Ext4 modules are left out currently in the Intrepid Alpha release... although, I haven't tried alpha 2/3 yet...

---

### Post by philinux on 2008-07-29
Ext4 Discussed here.

[http://ubuntuforums.org/showthread.php?t=837589](http://ubuntuforums.org/showthread.php?t=837589)

---

### Post by BGFG on 2008-07-29
> **philinux said:**
> Ext4 Discussed here.

[http://ubuntuforums.org/showthread.php?t=837589](http://ubuntuforums.org/showthread.php?t=837589)

I had read that ext4 was to be included in the -25 kernel so when tinivole said -26. i wasn't even aware the kernel had gotten that far. Now you guys have me excited about btrfs. Thanks for the reading material.

---

### Post by gjoellee on 2008-07-29
the last update seams to work totally fine for me! kernel 2.6.26-20.38

---

### Post by articpenguin on 2008-07-30
> **BGFG said:**
> So in which Kernel is Ext4 going to be ?


I do not think ext4 is going to be in hardy maybe intrepid?

---

### Post by cdtech on 2008-07-30
> **tinivole said:**
> Why all the fuss about 2.6.24?

I'm on a vanilla 2.6.26 kernel straight from the kernel.org git repository, er, last sync'd about 4 hours ago... :D

Seems if I go above the 24 I have serious issues....

---

### Post by PmDematagoda on 2008-07-30
> **articpenguin said:**
> I do not think ext4 is going to be in hardy maybe intrepid?

Ext4 may(it is very unlikely) never be on Hardy unless you compile a kernel including the modules on your own and install the ext4 utilities. On Intrepid, there was no blueprint for the inclusion of ext4 into Intrepid, so ext4 may not reach Intrepid either.

---

### Post by PmDematagoda on 2008-07-30
> **cdtech said:**
> Seems if I go above the 24 I have serious issues....

Perhaps you compiled it wrong?

---

### Post by BGFG on 2008-07-31
> **PmDematagoda said:**
> Ext4 may(it is very unlikely) never be on Hardy unless you compile a kernel including the modules on your own and install the ext4 utilities. On Intrepid, there was no blueprint for the inclusion of ext4 into Intrepid, so ext4 may not reach Intrepid either.

So next year then ? I think so. The ext4 engineers seem to be really pushing.
But what fs do you use ? and why ?
I plan to replace my vista install with Debian. Doing some research and trying to get some feedback on the various filesystems.

---

### Post by PmDematagoda on 2008-07-31
> **BGFG said:**
> So next year then ? I think so. The ext4 engineers seem to be really pushing.
But what fs do you use ? and why ?
I plan to replace my vista install with Debian. Doing some research and trying to get some feedback on the various filesystems.

I currently use ext3, I use it because it is known to be reliable and also because it has the necessary utilities which can be useful when the filesystem breaks down in some way, as I understand it the ext4 utilities are not completed yet.

---

### Post by chewit on 2008-07-31
Maybe a stupid question. But when ext4 reaches Ubuntu, will the file system change to ext4 from 3 during the distro update?

---

### Post by PmDematagoda on 2008-07-31
> **chewit said:**
> Maybe a stupid question. But when ext4 reaches Ubuntu, will the file system change to ext4 from 3 during the distro update?

I don't think so, doing an upgrade is only upgrading the packages and no more. But it's not like ext3 support will be dropped by Ubuntu instantaneously, look at ext2.

---

### Post by BGFG on 2008-07-31
I don't think that was a stupid question either. Filesystems are how the data is physically stored on the disk. So if you were to change a fs i don't see how it could be converted to a new physical format and still maintain data integrity. But that would be cool to see though. 
Whenever ext4 gets here, Fresh install for me.

---

