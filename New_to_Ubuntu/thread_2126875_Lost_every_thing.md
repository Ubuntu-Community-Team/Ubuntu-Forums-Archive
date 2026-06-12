---
title: "Lost every thing"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by crazysawsaw on 2013-03-18
i just installed ubuntu on my pc and i had VISTA so i choosed to put ubuntu instead of vista and after install i can'd find any thing in my hard drive 
is there any way to get it back?????:(

---

### Post by Cheesemill on 2013-03-18
Can you post the output of...
```
sudo fdisk -l
```

This will let us know haw everything is arranged on your hard drive.

---

### Post by tgalati4 on 2013-03-18
If you partitioned and installed Ubuntu correctly, then in Nautilus (file manager) you should see a Windows Vista drive in the "Places" column on the left side.  If you installed Ubuntu over your Vista installation, then it's quite possible that your files got overwritten.  Let's hope that your installation went OK.

---

### Post by crazysawsaw on 2013-03-18
it dosent work 
HELP, PLEASE

---

### Post by crazysawsaw on 2013-03-18
i think it got overwritten 
that's mean it's gone forever ever never ever RIGHT 
](*,)

---

### Post by Cheesemill on 2013-03-18
First post the output of the command I asked for earlier...
```
sudo fdisk -l
```
(that's a lower case L, not a one).

---

### Post by fantab on 2013-03-18
What 'option' did you use during install? Did you choose to "replace Windows" or "alongside Windows"? If you opted for the former then Ubuntu has wiped out your HDD and installed itself. If you opted for the later option then your Windows should be alright. 

Can you boot Ubuntu? Does it show the option to boot Windows? 

If you can boot into Ubuntu then open "TERMINAL" and type:

```
$ sudo fdisk -l
```

Post the output here.

You will be prompted to type your password, go ahead and type it, though you won't be able to see it in the Terminal.

---

### Post by crazysawsaw on 2013-03-18
[IMG]http://i48.tinypic.com/swy9g0.png[/IMG]

---

### Post by fantab on 2013-03-18
Relax. Even if you have lost your Data there are tools to recover it.

In the search box type Terminal and post the output of the command we gave you in earlier post.

---

### Post by crazysawsaw on 2013-03-18
i choosed (replace Windows) 
i thoght it's like windows > put it self on c drive > but i was wrong 
thanx guys any way :D

---

### Post by fantab on 2013-03-18
You can try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover your DATA. Read carefully all that is there to read on that page the given link represents.

Also search this forum for threads dealing with recovering lost data and partitons. If you have any doubts then get back here...

Good Luck

---

### Post by crazysawsaw on 2013-03-18
_**I FOUND IT **_
[IMG]http://i46.tinypic.com/xvd6q.png[/IMG]

---

### Post by fantab on 2013-03-18
NO it is "

```
$ sudo fdisk -l 
```

and not "sudo fdisk - l" no space between - and l

---

### Post by crazysawsaw on 2013-03-18
**HOW ABOUT NOW **



[IMG]http://i47.tinypic.com/wk35au.png[/IMG]

---

### Post by fantab on 2013-03-18
Yep, it wiped it all.

If you have lost any important DATA and want to recover it than I suggest you read the link I gave you in my earlier post about TestDisk...

[more info]("https://help.ubuntu.com/community/DataRecovery")...

---

### Post by crazysawsaw on 2013-03-18
many thanx my friend :D

---

### Post by Mark Phelps on 2013-03-18
> **crazysawsaw said:**
> i just installed ubuntu on my pc and i had VISTA so i choosed to put ubuntu instead of vista and after install i can'd find any thing in my hard drive 
is there any way to get it back?????:(

If you really need to get some Windows files back, and are prepared to spend some money to do that, and have access to a Windows PC, to which you can connect your current drive and install an app ...  then, read on:

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by tgalati4 on 2013-03-18
With a 500GB drive and a typical Linux installation using 5GB and a 2GB swap file that is in use (because you booted into Linux), so 7GB are gone, leaving 493GB of potential files to recover.  Since a typical Vista installation is ~15GB, that leaves 98% personal data recovery rate (485GB/493GB).  How much space was used in Vista before you installed Ubuntu?

Read and become an expert on data recovery before attempting this recovery.  You don't want to make the same mistake twice.

---

