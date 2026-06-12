---
title: "HowTo: Revert from grub2 to Legacy Grub."
date: 2009-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by kansasnoob on 2009-10-23
Edit thread closed.

Information available at [https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)


Someone will undoubtedly ask, "why would I want to revert to legacy grub"? My answer is, "I hope you don't". Grub 2 is the way of the future and I'd bet that a year from now nearly everyone will think of legacy grub as downright prehistoric! If you're new to Ubuntu I believe you'll find Grub 2 to be no more complicated than legacy grub, and the documentation continues to improve. I know 20 months ago legacy-grub was confusing to me.

That said I originally undertook this just as a matter of curiosity, I multi-boot and I'm a control freak! I knew that installing via the Alternate CD allowed installing with no boot-loader at all (or Lilo) and I've since learned that you can do somewhat likewise using the Live CD. Also legacy grub is quite familiar to me and the real beauty of Ubuntu, or Linux in general, is the ability to customize it to your hearts content (yeah, and even break it)! I should note here that I've only been able to test this on i386 since I have no 64 bit machines!

[COLOR="Red"]*************[/COLOR]

**[COLOR="Red"]Caution: check software sources before proceeding![/COLOR]** As of 01/09/2010 I've encountered several problems with the packages "grub" and "grub-common" (or even "grub-pc") not being available for installation during this procedure (particularly with the Australian server).

So before proceeding go to Synaptic Package Manager and click on Reload. When it's done click on Search and type grub, make sure that the packages grub, grub-pc, and grub-common are all available there.

If they're not we need to straighten out the software sources. Since we're in Synaptic I'd begin by just clicking on Settings > Repositories and change to the Main Server. Also be certain that all four of the Ubuntu repos are checked, but that the CD-ROM box is NOT checked.

Then click on reload again, and Search, type grub and check again to see that grub, grub-pc, and grub-common are all three there! If not DO NOT proceed, I'll need to see the output of:

```
cat /etc/apt/sources.list
```

Feel free to send me a brief PM pointing me to your specific thread here on the forums if need be.

[COLOR="Red"]*************[/COLOR]

So, on with business, [COLOR="Red"]please read this in it's entirety before beginning[/COLOR]. If you have any doubts ask questions here on the forums before beginning and make sure you have everything you need! You don't want to get part way through this and find you're unable to complete it! Since we're working on the boot-loader [COLOR="Red"]I recommend at the very least having an Ubuntu Live CD on hand (9.04 or prior)[/COLOR] that you know works so we can work from it if need be. [COLOR="Red"]If any of these steps fail to complete successfully you will most likely be unable to boot your system![/COLOR] Not to worry though if you have a Live CD, that's briefly explained in Appendix #1, and Appendix #2 describes very briefly how to reverse the steps outlined here.

Some prior knowledge regarding Legacy Grub is helpful and you must know how your system is partitioned, how many drives you have, etc. so I recommend figuring that out before you even begin! The following link is a great resource or, if in doubt, ask questions here at the forums.

[http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD](http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD)

I will not go into detail about editing the menu.lst here other than providing an example of my own boot entries. *(See Appendix #3)* Again this is a great resource:

[http://members.iinet.net.au/~herman546/p15.html#menu.lst](http://members.iinet.net.au/~herman546/p15.html#menu.lst)

I highly recommend using copy-n-paste to run these commands. *[COLOR="SeaGreen"]It can also be quite useful to keep a record of what happens in the terminal by simply keeping Abiword or Open Office Word open and "copy-n-pasting" the results of various steps into a document, then saving that document when done. That way if something goes haywire we can use that to troubleshoot what went wrong. I always put a copy in my Yahoo mailbox so I can access it easily from any computer or even the Live CD.[/COLOR]*

So, when you're ready, let's begin:

**Step #1: Rename the existing grub directory and create a new one.**

We want to rename the existing /boot/grub directory for use as a backup so go to the Terminal and run the command:

```
sudo mv /boot/grub /boot/grub_backup
```

Now we'll create a new grub directory:

```
sudo mkdir /boot/grub
```

To be certain those two commands were effective you can run the command:

```
ls /boot
```

[I]Note: that's a lower case L.
[/I]
You can see highlighted in the sample output below that we now have both grub and grub_backup in the boot directory:

> lance@lance-desktop:~$ ls /boot
/boot:
abi-2.6.31-11-generic         memtest86+.bin
config-2.6.31-11-generic      System.map-2.6.31-11-generic
**grub**                          vmcoreinfo-2.6.31-11-generic
**grub_backup**                  vmlinuz-2.6.31-11-generic
initrd.img-2.6.31-11-generic


Likewise if you run:

```
ls /boot/grub
```

You should see that the grub directory is currently empty because we haven't reinstalled grub yet.

Alternatively you can go to  Places > Computer > Filesystem > Boot, you should see the folders named "grub" and "grub_backup".

**Step #2: Remove Grub 2 packages, purge configuration files, and install legacy Grub packages.**

It is a good idea to purge any old Startup Manager configuration files so:

```
sudo apt-get --purge remove startupmanager
```

If it says "not installed so not removed" that's OK, we just wanted to be sure no old configuration files messed with us later on.

[I]Just FYI 'grub-pc' is grub2 and 'grub' is legacy grub.
[/I]
First remove grub2:

```
sudo apt-get --purge remove grub-pc grub-common
```


You'll be confronted with this text:

> Do you want to have all GRUB 2 files removed from /boot/grub? 
Your system would be then unbootable if you don't install another bootloader.                                                  Remove GRUB 2 from /boot/grub? 
   
**Yes**, you do! We've created a backup anyway.     
                  
Now install legacy grub:

```
sudo apt-get install grub
```

You'll notice that installing grub also reinstalls grub-common, that's normal behavior, we just wanted to "purge" the configuration files.

Now:

```
sudo update-grub
```

You'll be asked if you want to create a /boot/grub/menu.lst - **yes, you do**, so type y and enter!

**Step #3: Physically install and setup Legacy Grub.**

Now you must actually "install" legacy grub if you're going to use your new legacy grub to boot with and you must know where. In my case I have only one hard drive and I can see how it's recognized by Ubuntu by running the command:

```
sudo fdisk -l
```

(BTW that's a lower case L.) The pertinent part is in bold in this example:

> lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk **/dev/sda**: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63056305

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2104    16900348+   7  HPFS/NTFS
/dev/sda2            2883        9729    54998527+   5  Extended
/dev/sda3            2105        2882     6249285   83  Linux
/dev/sda5            4214        5012     6417967+  83  Linux
/dev/sda6            5013        7434    19454683+  83  Linux
/dev/sda7            7435        8199     6144831   83  Linux
/dev/sda8            8200        9576    11060721   83  Linux
/dev/sda9            9577        9729     1228941   82  Linux swap / Solaris
/dev/sda10           2883        4213    10691194+  83  Linux

Partition table entries are not in disk order

Since /dev/sda is where I'd want grub to be installed, I'd run this command:

&#65279;```
sudo grub-install /dev/sda
```

*Note: If you're at all unsure about where to install grub then ask for help here on the forums! Better to be sure of what you're doing than to play the trial and error game!*

*[COLOR="SeaGreen"]This would be a good time to create a word document of Terminal progress as recommended above if needed for troubleshooting purposes.[/COLOR]*

Now we need to open a Grub shell as root so run the command:

```
sudo grub
```

[I]Note: I've noticed while working in a grub shell that the enter key in the numerical block of the keyboard doesn't always work properly, so use the enter key just above the right shift key!
[/I]
Then:

&#65279;```
find /boot/grub/stage1
```

That will provide an output like (hd0,2) which you'll need to use in the next step:

&#65279;```
root (hd0,2)
```

You see I've used (hd0,2) from the "find" command, of course you'll use whatever the output was in your specific case. Then:

```
setup (hd0)
```

There I've used the hd0 (that is a zero) from the (**hd0**,2) output from the "find" command.

If correct you should see an output like:

&#65279;> Checking if "/boot/grub/stage1" exists... **yes**
 Checking if "/boot/grub/stage2" exists... **yes**
 Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
 **succeeded**
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
 2 /boot/grub/menu.lst"... **succeeded**
 Done.

*[COLOR="SeaGreen"]Again, this would be a good time to create a word document of Terminal progress as recommended above just for future troubleshooting purposes because:[/COLOR]*

[COLOR="Red"]If that failed you will likely not be able to boot your machine until we get it straightened out![/COLOR]

Next just type:

```
quit
```

To exit the Grub shell.

**If successful you're done! Time to reboot and see what happens. I hope you read this all first and kept a text record of the terminal just in case something went haywire.**

**Step #4: Install Startup Manager and lock package versions if desired.**

Of course if you want to use startupmanager install it:

```
sudo apt-get install startupmanager
```

*But I should say that I've had ongoing problems keeping startupmanager working in Karmic. It's working right now after following the above steps so [COLOR="Red"]I rather think it might be wise to go to Synaptic and choose to "lock version" both "grub" and "grub-common"[/COLOR], but I've chosen not to so I can monitor for changes (ie: breakage) and I'll report such here if and when that happens. *

**[COLOR="Red"]**************************************************[/COLOR]**

**Appendix #1:**

I'd mentioned above being able to "fix" things using a Live CD. I posted briefly about that here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Of course you'll need to know what partition to mount, what commands to run, etc. And, as mentioned above, this is where a printed record of terminal progress comes in handy! Literally every step necessary to repair or install and setup either legacy grub or grub2 can be completed using a Live CD if you know what to do! Of course if you haphazardly mount the wrong partition you can also destroy things and lose data really fast.

**[COLOR="Red"]**************************************************[/COLOR]**

**Appendix #2:**

OK, so imagine you've changed to legacy grub and now you want to switch back to grub2 (should be self explanatory, same logic applies):

sudo mv /boot/grub /boot/grub_legacy (we already used the name: grub_backup)
sudo mv /boot/grub_backup boot/grub (or sudo mkdir /boot/grub if you want to start fresh)
sudo apt-get --purge remove grub grub-common
sudo apt-get install grub-pc
sudo update-grub
sudo grub-install /dev/sda (replace /dev/sda with your proper destination)

Seems simple without my rambling verbosity, eh? I can now "flip" from one to the other in about 15 minutes - but not blindfolded.

**[COLOR="Red"]**************************************************[/COLOR]**

**Appendix #3**:

This is what my Karmic /boot/grub/menu.lst boot entries look like (of course I had to manually add the lines to boot Win XP, Jaunty, and Mint Gloria):

## ## End Default Options ##

title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic
uuid		d3d589c9-29e6-463e-9c99-806ec3646dea
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd		/boot/initrd.img-2.6.31-11-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
uuid		d3d589c9-29e6-463e-9c99-806ec3646dea
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro  single
initrd		/boot/initrd.img-2.6.31-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title         Linux Mint 7 Gloria, kernel 2.6.28-15-generic
root          (hd0,6)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title         Linux Mint 7 Gloria, kernel 2.6.28-15-generic (recovery mode)
root          (hd0,6)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro single
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot

**[COLOR="Red"]**************************************************[/COLOR]**

I've found this syntax to work better for adding Karmic to another existing grub menu.lst:

&#65279;title Ubuntu 9.10, kernel 2.6.31-11-generic (on /dev/sda3)
 root (hd0,2)
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd /boot/initrd.img-2.6.31-11-generic
 savedefault
 boot
 
title Ubuntu 9.10, kernel 2.6.31-11-generic (recovery mode) (on /dev/sda3)
 root (hd0,2)
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro single 
initrd /boot/initrd.img-2.6.31-11-generic
 savedefault
 boot 

Rather than this:

&#65279;title Ubuntu karmic (development branch), kernel 2.6.31-11-generic
 uuid d3d589c9-29e6-463e-9c99-806ec3646dea
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro quiet splash 
initrd /boot/initrd.img-2.6.31-11-generic
 
title Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
 uuid d3d589c9-29e6-463e-9c99-806ec3646dea
 kernel /boot/vmlinuz-2.6.31-11-generic root=UUID=d3d589c9-29e6-463e-9c99-806ec3646dea ro single
 initrd /boot/initrd.img-2.6.31-11-generic 

No idea why!

**[COLOR="Red"]***********************************************[/COLOR]**

**[COLOR="Red"]Just NOTES[/COLOR]**

**My "failsafe" method for installing or reinstalling grub2 to a drives mbr if other methods have failed:**

```
sudo mount /dev/sdXY /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
lsb_release -a
``` (Just to be sure you're in the right place)

```
grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**
```

```
grub-install --recheck /dev/sd**[COLOR="Red"]X[/COLOR]**
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

**To restore a Windows MBR with nothing but an Ubuntu Live CD:**

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sd**[COLOR="Red"]X[/COLOR]** mbr
```

**If simply running "update-grub" fails to find other OS's in grub2 try:**

```
sudo apt-get install --reinstall libdebian-installer4
```

```
sudo os-prober
```

```
sudo update-grub
```

---

### Post by bapoumba on 2009-11-05
Sorry it took so long for the tutorial to be approved. Thanks for you patience :)

As kansasnoob stated, please stick with grub2 ;)

---

### Post by julianb on 2009-11-07
Another source of info:
[Revert to Grub 1 -- community documentation]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

If you uninstalled grub2 and now grub doesn't work, here's a detailed explanation of [installing grub from an ordinary Ubuntu CD]("http://ubuntuforums.org/showthread.php?t=224351&highlight=livecd+grub")

---

### Post by kansasnoob on 2009-11-07
> **julianb said:**
> Another source of info:
[Revert to Grub 1 -- community documentation]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

If you uninstalled grub2 and now grub doesn't work, here's a detailed explanation of [installing grub from an ordinary Ubuntu CD]("http://ubuntuforums.org/showthread.php?t=224351&highlight=livecd+grub")

Unfortunately the official documentation falls short.

It does not create a new /boot/grub directory so you end up with mixed legacy grub and grub2 files which effects the operation of startupmanager and can also have adverse effects on boot times.

And I believe I went above and beyond trying to explain what each step of the procedure does.

BTW I intentionally used the _ (underscore) to rename/move the grub directory because no one else does that.

That way if someone does have trouble following my instructions I should easily be able to see what they did right or wrong.

The official documentation also falls short in the "legacy grub" setup area. They simply say: 

> #

With grub installed, the user must still create the menu.lst and stage1/stage2 files by running the following two commands.

   1.

      sudo update-grub
          *

            Generates menu.lst
                o Tab to "Yes" when prompted. 
   2.

      sudo grub-install /dev/sdX
          * Choose the correct device (sda, sdb, etc), normally the one on which Ubuntu is installed.
          *

            Creates the stage1 & stage2 files in /boot/grub and writes to the MBR. 

# Reboot 

With no mention of the typical:

> sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

Which is essential!

Quite simply, mine is better. (No humble pie here).

And with 294 views of this HowTo with no complaints, and 3,252 views of the original:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

I'd think I'd be hearing a lot of complaints and I'm not.

I do wish we could get someone like meierfra or caljohnsmith to help tackle some of the multi-boot/multi-drive problems with both grubs!

I've been getting in over my head there but no one else kicks in!

Maybe next spring I'll have enough money to build a spare multi-drive test system so I can test more scenarios.

---

### Post by old_salt on 2009-11-13
> **kansasnoob said:**
> Someone will undoubtedly ask, "why would I want to revert to legacy grub"? 

Because a lot of us are now experiencing Boot times of over a minute to a minute and a half (Mine over 70 Seconds) to get to the login screen when it used to take 23 or so seconds?

A LOT of users could care less about a Grub Bootsplash capability, fancy text or even colors. We only care about getting our systems booted up as fast as possible. Why care what the screen looks like if after a couple of seconds your looking at the system boot screen?

I can provide a picture of my boot process when I return home if you want it.

---

### Post by kansasnoob on 2009-11-13
> **old_salt said:**
> Because a lot of us are now experiencing Boot times of over a minute to a minute and a half (Mine over 70 Seconds) to get to the login screen when it used to take 23 or so seconds?

A LOT of users could care less about a Grub Bootsplash capability, fancy text or even colors. We only care about getting our systems booted up as fast as possible. Why care what the screen looks like if after a couple of seconds your looking at the system boot screen?


I can provide a picture of my boot process when I return home if you want it.

So, did my method of reverting work for you?

---

### Post by SeraphProfeta on 2009-11-14
Hi! I decided to revert to legacy grub to try to fix a problem I've never had with bootloaders until the new GRUB 2 with the latest Ubuntu 9.10 release.

Basically, after one or two reboots, in either OS (I'm dual booting Ubuntu and Windows 7 and have been since the Beta of W7), suddenly grub stops working. It'll say "Grub is loading..." or whatever then restart, not even let me choose an OS, essentially locking me out of my system. I'm about to can Ubuntu for now altogether, because I need my Windows stuff for work, but I certainly don't want to do this, so someone reccomended this tutorial to me, and I've gotten pretty far. I've installed the old grub, and am at the point where I am "in" it in the terminal, and I get  the part where you have to type:

"setup (hd0)"

now here is where I start to get errors, mostly

"Error 12: Invalid device requested."

When I do the find /boot/grub/stage one, it returns "(hd0,6)"

Am I doing something wrong? Is there a different way to fix my bootloader problem?

---

### Post by kansasnoob on 2009-11-15
> **SeraphProfeta said:**
> Hi! I decided to revert to legacy grub to try to fix a problem I've never had with bootloaders until the new GRUB 2 with the latest Ubuntu 9.10 release.

Basically, after one or two reboots, in either OS (I'm dual booting Ubuntu and Windows 7 and have been since the Beta of W7), suddenly grub stops working. It'll say "Grub is loading..." or whatever then restart, not even let me choose an OS, essentially locking me out of my system. I'm about to can Ubuntu for now altogether, because I need my Windows stuff for work, but I certainly don't want to do this, so someone reccomended this tutorial to me, and I've gotten pretty far. I've installed the old grub, and am at the point where I am "in" it in the terminal, and I get  the part where you have to type:

"setup (hd0)"

now here is where I start to get errors, mostly

"Error 12: Invalid device requested."

When I do the find /boot/grub/stage one, it returns "(hd0,6)"

Am I doing something wrong? Is there a different way to fix my bootloader problem?

The most helpful thing I could see to troubleshoot this is the results of the Boot Info script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by vexorian on 2009-11-16
Heya thanks for howto.

Now my Acer Aspire One boots 100% of the time. And if there is a system lock up / I run out of battery, grub1 does not get disconfigured and it will still boot! . Seriously, is there really a good reason to use grub2 besides liking all sorts of random headaches?

---

### Post by e_torano on 2009-11-28
May I start by saying thanks for this ;D However, you missed out one essential part- you didn't install grub anywhere and hence when you reach the part that saying 

sudo update-grub

nothing happens. You must first

sudo apt-get install grub

;D I didn't realise you'd missed this till I thought about it lol

---

### Post by vexorian on 2009-11-28
> **e_torano said:**
> May I start by saying thanks for this ;D However, you missed out one essential part- you didn't install grub anywhere and hence when you reach the part that saying 

sudo update-grub

nothing happens. You must first

sudo apt-get install grub

;D I didn't realise you'd missed this till I thought about it lol

.
[quote=OP]Yes, you do! We've created a backup anyway.

Now install legacy grub:

Code:

```
sudo apt-get install grub
```
[/quote]

---

### Post by kansasnoob on 2009-11-29
> **e_torano said:**
> May I start by saying thanks for this ;D However, you missed out one essential part- you didn't install grub anywhere and hence when you reach the part that saying 

sudo update-grub

nothing happens. You must first

sudo apt-get install grub

;D I didn't realise you'd missed this till I thought about it lol

Not quite sure who you're directing that to.

I go into almost painful detail, it's there!

Both installing the package and installing grub to the mbr.

---

### Post by e_torano on 2009-11-30
Wooops, my bad lmao I'm very sorry. I looked through twice and completely missed it both times >.> Need to stop skim-reading stuff and read properly.

---

### Post by kansasnoob on 2009-11-30
> **e_torano said:**
> Wooops, my bad lmao I'm very sorry. I looked through twice and completely missed it both times >.> Need to stop skim-reading stuff and read properly.

No problem. I actually did put a lot of thought into that regarding how much should be explained.

Certainly the added "explanations" detract from the needed commands, but I felt that I arrived at a reasonable "balance".

---

### Post by tipiglen on 2009-11-30
Thanks for the tutorial/howto.  I've done it all, and rebooted, but I don't get the option screen from which to choose which os.

The machine simply goes straight into karmic, which is OK, 'cause that's what I use anyway, but where is the choice?   I went through the effort to get a menu.lst, and I've got one, but it doesn't seem to be working....

I added a win xp line (just copied from yours, but it seemed right), and I have several kernel options (due to updates, etc), but I'm not offered a choice.

Any ideas?

At least it ain't broke, and I ain't missing xp, but would like the opportunity....

<a href="http://home2.btconnect.com/tipiglen/loveandpeace3.gif"><b>
Salaam/Shalom/Shanthi/Peace</b></a>
   Namaste -ed

---

### Post by tipiglen on 2009-12-01
Fixed it!  I edited (commented out) the "hidden" option in the top part of the new menu.lst 

Now working fine.  Thanks again.  Now to go and read up on grub2....
just in case I decide I like it better
;-)

---

### Post by e_torano on 2009-12-02
> **kansasnoob said:**
> No problem. I actually did put a lot of thought into that regarding how much should be explained.

Certainly the added "explanations" detract from the needed commands, but I felt that I arrived at a reasonable "balance".

Yeah, you did ;D I liked the fact you explained it all ^^ Just confused myself as usual.

---

### Post by dwasifar on 2009-12-02
Thanks for the tutorial.  I have actually installed grub before, but it was nice to have all the steps outlined in one place.

I've found grub2 to be unstable and unpredictable.  I have here two desktop machines running Karmic.  On one machine, the option to not show a kernel menu on boot is ignored every time I get a grub update from update-manager, the result of the os-prober failing to properly handle an unused Jaunty kernel on /dev/sdc.  So every time I get an update I have to physically disconnect /dev/sdc, run update-grub, then reconnect the drive.  On the other machine, suddenly yesterday it wouldn't boot until I edited the boot parms to point at /dev/sda instead of the drive's UUID.  I had to run update-grub to fix that, too.

Maybe grub2 will be ready for prime time when Lucid rolls around, but right now it doesn't look like an improvement.

---

### Post by pieguy on 2009-12-06
Thanks so much for this tut, I just successfully reverted.  Maybe when grub2 is mature and there are actually tools for it like there are for grub, then I'll consider using it, till then its asinine to drop people into and say, oh this is the future, and well, people hated grub when it came out.  Thats real fraking helpful, that in a years time there may be the tools available for grub2 that are as user friendly as there are for grub now.  But WTF! do we do til then.  Well, continue using grub :D

---

### Post by kansasnoob on 2009-12-06
> **pieguy said:**
> Thanks so much for this tut, I just successfully reverted.  Maybe when grub2 is mature and there are actually tools for it like there are for grub, then I'll consider using it, till then its asinine to drop people into and say, oh this is the future, and well, people hated grub when it came out.  Thats real fraking helpful, that in a years time there may be the tools available for grub2 that are as user friendly as there are for grub now.  But WTF! do we do til then.  Well, continue using grub :D

I understand your frustration. Maybe I should change the intro to my HowTo a bit.

I just didn't want to try and convince someone to revert or vice versa. I'll give it some thought.

For that matter I still rather like lilo for thumb drives - call me retro ;)

---

### Post by dwasifar on 2009-12-07
> **kansasnoob said:**
> For that matter I still rather like lilo for thumb drives - call me retro ;)

Yeah, that's a stitch.  :)

I upgraded two machines in place yesterday - one normal Ubuntu installation and one Ubuntu server.  Interestingly, on those machines, grub2 was not installed.  Grub is still in use on them.  I was clued in because one kept prompting me what to do with menu.lst and asking me if I wanted to install the package maintainer's version, and I was thinking, why would it be installing that?

Does anyone know if upgrades were setting up grub2 when Karmic first came out in October?

---

### Post by kansasnoob on 2009-12-08
> **dwasifar said:**
> Yeah, that's a stitch.  :)

I upgraded two machines in place yesterday - one normal Ubuntu installation and one Ubuntu server.  Interestingly, on those machines, grub2 was not installed.  Grub is still in use on them.  I was clued in because one kept prompting me what to do with menu.lst and asking me if I wanted to install the package maintainer's version, and I was thinking, why would it be installing that?

Does anyone know if upgrades were setting up grub2 when Karmic first came out in October?

Upgrades from Jaunty w/legacy grub stay on legacy grub. Only fresh installs get grub2, but you can change to grub2 if you wish.

---

### Post by mikemikemike on 2009-12-09
Thank you sooo much for this post. My stupid Grub2 was getting stuck at the Grub menu not counting down and no auto selecting. And I had to hit enter everytime. (Yes, I am that lazy, or maybe I just like things to work the way they were designed to.)

But anyway thank you so much.

---

### Post by funkwurm on 2009-12-14
Thanks for this tutorial, I too run into Grub 2 trouble after updating my Ubuntu (even when I deselect the new kernel, which seemed to cause the problem at first).

I need a little help figuring out which harddrive to install grub to, because I have an unusual configuration.

I use Wubi to install Ubuntu, and I can't switch to a physical partition just like that because I'm using a MacBook Pro.

Before Grub2, Wubi was the ideal solution to have a triple-boot system (Mac OS, Win XP, Ubuntu) without having to replace Apple firmware with rEFIt and manually creating partitions in the terminal and what not.

So what I know is that on this Mac, sda1 is where EFI resides, sda2 is where Mac OS X is installed and sda3 is the Windows partition. So I think I don't wanna install grub to sda or sda0, because that'll screw Apple's EFI and partition-table etc.

So can I just do this?
```
sudo grub-install /dev/sda3
```

If not, how would I go about figuring out where Wubi installed Grub 2? Is it in a config-file? Is it in the load-letter?

Thanks so much for the help in advance.

---

### Post by kansasnoob on 2009-12-14
> **funkwurm said:**
> Thanks for this tutorial, I too run into Grub 2 trouble after updating my Ubuntu (even when I deselect the new kernel, which seemed to cause the problem at first).

I need a little help figuring out which harddrive to install grub to, because I have an unusual configuration.

I use Wubi to install Ubuntu, and I can't switch to a physical partition just like that because I'm using a MacBook Pro.

Before Grub2, Wubi was the ideal solution to have a triple-boot system (Mac OS, Win XP, Ubuntu) without having to replace Apple firmware with rEFIt and manually creating partitions in the terminal and what not.

So what I know is that on this Mac, sda1 is where EFI resides, sda2 is where Mac OS X is installed and sda3 is the Windows partition. So I think I don't wanna install grub to sda or sda0, because that'll screw Apple's EFI and partition-table etc.

So can I just do this?
```
sudo grub-install /dev/sda3
```

If not, how would I go about figuring out where Wubi installed Grub 2? Is it in a config-file? Is it in the load-letter?

Thanks so much for the help in advance.

You might find some helpful info in the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Unfortunately I know very little about Wubi and even less about Mac.

---

### Post by Gannin on 2010-04-26
This reminds me of the old article on how to install the nVidia drivers from the nVidia site.  There were 50 steps too many and it had you do a bunch of stuff you didn't need to do.

I don't like Grub 2 because it's buggy on my system and doesn't work properly.  But Grub 1 works just fine.

To revert back to Grub 1, all you have to do is go to System > Administration > Synaptic, do a search for Grub, and click to install it.  That'll automatically remove Grub 2.  Then on the command line, issue the command "sudo update-grub", say yes to create menu.lst, then "sudo grub-install hd0" and you're done.  That even leaves you with the option of chainloading into the leftover Grub 2 files from the Grub boot menu.

---

### Post by kansasnoob on 2010-04-28
> **Gannin said:**
> This reminds me of the old article on how to install the nVidia drivers from the nVidia site.  There were 50 steps too many and it had you do a bunch of stuff you didn't need to do.

I don't like Grub 2 because it's buggy on my system and doesn't work properly.  But Grub 1 works just fine.

To revert back to Grub 1, all you have to do is go to System > Administration > Synaptic, do a search for Grub, and click to install it.  That'll automatically remove Grub 2.  Then on the command line, issue the command "sudo update-grub", say yes to create menu.lst, then "sudo grub-install hd0" and you're done.  That even leaves you with the option of chainloading into the leftover Grub 2 files from the Grub boot menu.

But having "mixed" grub2 and legacy grub files in /boot/grub interferes with a few things. You'll see when kernels don't update properly, or you can't get all functions of Startup Manager to work properly, etc :)

OTOH you could write your own how-to.

---

### Post by Gannin on 2010-04-28
> **kansasnoob said:**
> But having "mixed" grub2 and legacy grub files in /boot/grub interferes with a few things. You'll see when kernels don't update properly, or you can't get all functions of Startup Manager to work properly, etc :)

OTOH you could write your own how-to.

Actually, everything works just fine for me.  And, as I mentioned before, because the old Grub 2 files are still there, you automatically get a new entry in the Grub boot menu titled "Chainload into Grub 2" that lets you boot into your Grub 2 configuration if you really want to.  It's automatically setup to work this way.

---

### Post by kansasnoob on 2010-04-30
> **Gannin said:**
> Actually, everything works just fine for me.  And, as I mentioned before, because the old Grub 2 files are still there, you automatically get a new entry in the Grub boot menu titled "Chainload into Grub 2" that lets you boot into your Grub 2 configuration if you really want to.  It's automatically setup to work this way.

Well, don't be surprised if "update-grub" fails to pick up a kernel update :)

---

### Post by Gannin on 2010-04-30
> **kansasnoob said:**
> Well, don't be surprised if "update-grub" fails to pick up a kernel update :)

Actually, I've been using Grub 1 using the method I outlined above ever since 9.10 came out, and it automatically picks up every kernel update and adds it to the Grub boot menu.  Similarly, if I remove an old kernel, it'll automatically remove that kernel's entries from the Grub menu too :).  So as I said, it works fine.  It automatically gives you the option of chainloading into your old Grub 2 files, and it automatically updates the Grub boot menu with the addition and removal of kernels.

---

### Post by kansasnoob on 2010-04-30
> **Gannin said:**
> Actually, I've been using Grub 1 using the method I outlined above ever since 9.10 came out, and it automatically picks up every kernel update and adds it to the Grub boot menu.  Similarly, if I remove an old kernel, it'll automatically remove that kernel's entries from the Grub menu too :).  So as I said, it works fine.  It automatically gives you the option of chainloading into your old Grub 2 files, and it automatically updates the Grub boot menu with the addition and removal of kernels.

Fine, you don't like my HowTo. I'll lose no sleep :)

---

### Post by Gannin on 2010-04-30
> **kansasnoob said:**
> Fine, you don't like my HowTo. I'll lose no sleep :)

It's not that I don't like it, I appreciate the effort.  It's just that there are way more steps than there needs to be.

---

### Post by kansasnoob on 2010-04-30
You also obviously like to have the last word. I wrote this with the intention of helping people. If you find that it's somehow detrimental then report it to the mods.

You're wasting my time and making me angry ](*,)

---

### Post by Gannin on 2010-04-30
> **kansasnoob said:**
> You also obviously like to have the last word. I wrote this with the intention of helping people. If you find that it's somehow detrimental then report it to the mods.

You're wasting my time and making me angry ](*,)

Did I ever say it was detrimental?  No, just that it's more steps than are needed.  Whether you get angry or not is up to you :).  As for wasting your time, no one is making you come here and reply to my posts.  You're choosing to do that all on your own.

---

### Post by perspectoff on 2010-05-07
To each his own. Literally.

I use the time honored solution of having a small /boot partition (100 Mb) which has Grub Legacy in it.

The MBR (Master Boot Record) always loads that, and its only function is to chainload whichever bootloader belongs to the operating system of the partition being loaded.

That way I never have to think about which bootloader is screwing with which (which is the problem with Grub2, Windows Bootloader, Wubi, etc).

Each OS gets to keep its own bootloader quarantined within its own partition. end of story. Upgrades, updates, etc. only affect that OS, not the whole bloody hard drive.

How long extra does it take for the initial Grub Legacy (whose only job is to chainload)? Well, I set it to a timeout of one second, so it takes one second longer.

Guess what? It works with UUID-specified devices, too. I can chainload all kinds of stuff. Try doing that with Grub2!

Yeah, it took me about 15 minutes extra to set it up (a few years ago), but I have never had to fiddle with it despite 3 Ubuntu/Kubuntu upgrades, 7 partitions, and every imaginable OS. 

My walkthrough is at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation) (Ubuntuguide)

and

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation) (Kubuntuguide)

Becasue I did it a while ago, I didn't install Grub Legacy (as a previous post pointed out), so that my instructions don't include the

 sudo apt-get install grub

step to install Grub Legacy. Then again, I am not really replacing Grub2 with Grub Legacy on any operating system -- I'm merely installing it in its own small partition. So, I suppose if you install it you would have an extra step of re-installing Grub2 or something. Oy vay, what a headache! It is never a good idea to mix and match operating system components! To each its own!

---

### Post by kansasnoob on 2010-05-07
> To each his own. Literally.

That is exactly right. I personally like Meierfra's way of creating a custom grub2 menu:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

That's the beauty of Linux, tweak it to your own liking ;)

If there were one universal windows-ish way of doing things I'd get very very ill.

---

### Post by johnny678 on 2010-05-11
Thanks for your hard work!!!! Excellent guide. 

**grub2 is a disaster** as far as i can see!!!

[COLOR=Red]Installing grub2 [COLOR=Black]on the[/COLOR] root partition[/COLOR] as opposed to the[COLOR=Red] MBR [/COLOR]or [COLOR=Red]boot partition[/COLOR] failed miserably after two  restarts.

I [COLOR=Red]prefer grub [/COLOR]to be installed on the[COLOR=Red] root partition[/COLOR] so i can[COLOR=Red] boot all of my operating system[/COLOR]s with [COLOR=Red]gag  boot loader.[/COLOR]

This is what happened:

1. I installed ubuntu 10.03
2. Reboot .> Black screen
3. Inserted ubuntu 10.03 Live CD to run in gnome desktop.
4  Opened a terminal:

```
sudo fdisk -l
```ubuntu is located on /dev/sda8

Next:

```
sudo mount /dev/sda8 /mnt
```To completely reinstall grub2:

```
sudo grub-install  --force --root-directory=/mnt/ /dev/sda8 
```I then rebooted and was able to log into Ubuntu. 

5. Restarted again and was welcomed by a black screen.

6. Went through the whole process again. 

7. Logged into Ubuntu and updated. 

8. Rebooted into a black screen. Lucky me.

9. Went through the whole process again.

10. [COLOR=Red]Found your guide and grub2 is now nuked.[/COLOR]

Thanks again. Cheers

By the way Ubuntu stuffed grub on my fedora partition as well. Ubuntu can be a headache at times.

---

### Post by kansasnoob on 2010-05-11
> **johnny678 said:**
> Thanks for your hard work!!!! Excellent guide. 

**grub2 is a disaster** as far as i can see!!!

[COLOR=Red]Installing grub2 [COLOR=Black]on the[/COLOR] root partition[/COLOR] as opposed to the[COLOR=Red] MBR [/COLOR]or [COLOR=Red]boot partition[/COLOR] failed miserably after two  restarts.

I [COLOR=Red]prefer grub [/COLOR]to be installed on the[COLOR=Red] root partition[/COLOR] so i can[COLOR=Red] boot my all operating system[/COLOR]s with [COLOR=Red]gag  boot loader.[/COLOR]

This is what happened:

1. I installed ubuntu 10.03
2. Reboot .> Black screen
3. Inserted ubuntu 10.03 Live CD to run in gnome desktop.
4  Opened a terminal:

```
sudo fdisk -l
```ubuntu is located on /dev/sda8

Next:

```
sudo mount /dev/sda8 /mnt
```To completely reinstall grub2:

```
sudo grub-install  --force --root-directory=/mnt/ /dev/sda8 
```I then rebooted and was able to log into Ubuntu. 

5. Restarted again and was welcomed by a black screen.

6. Went through the whole process again. 

7. Logged into Ubuntu and updated. 

8. Rebooted into a black screen. Lucky me.

9. Went through the whole process again.

10. [COLOR=Red]Found your guide and grub2 is now nuked.[/COLOR]

Thanks again. Cheers

By the way Ubuntu stuffed grub on my fedora partition as well. Ubuntu can be a headache at times.

Indeed GAG is a sweet graphic boot manager but it does have limitations. While it's not yet ready for the masses there's something new coming for grub2:

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

It is still quite buggy though so only play with it if you can afford the breakage :)

---

### Post by kansasnoob on 2010-05-11
> **future987 said:**
> A lot of people, myself included, are having difficulty in understanding the 'logic' of grub2, personally I think that for the present grub legacy is a better bet. I am sure that will eventually change but it hasn't yet. The way I have been dealing with the situation is simply to install a distro that still uses grub legacy (Debian Stable in my case) to control the boot process (ie it is installed on the disk mbr) and to use that to chainload to all the newer grub2 distros (installed onto the partition boot record not the disk mbr). The grub2 distros can make as much of a mess as they like of my newer distro boot menus (and believe me they do!) because I don't have to read them, I have already chosen what I want to boot into from the comparatively sane and superior debian boot menu. That works for me, but I have always wanted to know how easy it is to get rid of grub2 from a distro that already has it and that is what I tried out today. Luckily the answer is that it is very easy. Most of the procedure is taken from the Ubuntu community Docs ([https://help.ubuntu.com/community/Grub2 ... B%20Legacy]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy")) although they gloss over one very important step at the end which basically means that you cant boot. That is why I am repeating the tutorial here.

      [BD](http://www.2funbd.com)       [BD   Forum](http://www.2funbd.com/forum)       [url=http://www.2funbd.com/Blog]BD   Blog[/url

I actually like grub2 a lot. I multi-boot a lot and I like the automagic feature of grub2 being able to find and update entries for additional operating systems, but it's certainly not flawless yet.

My HowTo differs from the official documentation in that it totally wipes grub2 from the OS involved. If followed properly it still works with both Lucid and Karmic, it's too soon to know about Maverick.

---

### Post by johnny678 on 2010-05-12
> **kansasnoob said:**
> Indeed GAG is a sweet graphic boot manager but it does have limitations. While it's not yet ready for the masses there's something new coming for grub2:

[http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html)

It is still quite buggy though so only play with it if you can afford the breakage :)

Hi there. I was able to boot fedora with [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/), however gag would no longer work. I've been using gag for a long time now and never had this problem. 

Anyway I could have reinstalled gag and looked into it deeper however i decided to try BootIt&#8482; Next Generation since i'll already use their imaging software.

BootIt is a bit on the expensive side but i thought i will give it a go. If it's not a buggy application i will be happy. So far so good.

I don't mind buying software if it is stable.

---

### Post by kansasnoob on 2010-05-21
**[COLOR="Red"]This post is a work in progress and you should only try this if you're adventurous![/COLOR]** **My goal is to enable anyone to restore any Linux or Windows MBR with any Ubuntu Live CD.**

Although it's been around for a while now Grub 2 introduced the problem of users not being sure what version of grub they have installed and therefore just exactly how to restore Grub after the installation of Windows, or some other event, wipes out Grub. IMHO the best solution is to mount and chroot the Ubuntu (or Mint/other derivative) to first determine what version of Grub is installed and then to "recover" Grub while in the chroot so you're dealing with the grub packages installed in that OS. This eliminates the need of using a specific version of Ubuntu/Mint/derivative Live CD.

Of course the first thing to do is learn what partition Ubuntu is installed on, and also whether or not you have a separate "/boot" partition. This would also be an excellent time to describe drive and partition designations in Ubuntu:

Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

In many cases you may be able to determine the Ubuntu partition simply by running "sudo fdisk -l" (BTW that's a lower case L), but if the partitioning scheme is at all complicated, or if you simply have any doubts, I recommend running the Boot Info Script. 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The first two sections of the RESULTS.txt show what OS's bootloader is installed to the mbr of which drive and a list of all partitions including what OS is installed to what partition.

I should also add some general info about my "mount and chroot" procedure. It's not a true script but rather just a series of commands connected by "space&&space", so if one part of it fails the rest will fail! I strongly recommend that you copy-n-paste all commands. This is also intended only for determining the version of and restoring grub. For installing/removing packages, etc. more commands are needed!

This procedure is actually well explained here:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

**[COLOR="Red"]Particularly pay attention to what's said there about mounting and unmounting a separate "/boot" partition if used![/COLOR]** My "script" does NOT include the commands for mounting and unmounting "/boot"!

So once you've determined what partition to mount simply boot any Ubuntu Live CD and, in Terminal, run:

```
sudo mount /dev/sdXY /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

Of course the X and Y need to be replaced by your proper drive and partition designations (the easiest way to do so is to "copy-n-paste" the command and then use the left and right arrow keys to edit).

To be certain you've mounted the proper partition/OS run:

```
lsb_release -a
```

If that appears to be right then check the installed version of Grub:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

Example:

> grub-install (GNU GRUB 1.98-1ubuntu6)
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed


You can see there that the grub version is "1.98-1ubuntu6" which is grub 2, basically "0.9*" = legacy grub, and "1.9*" = grub 2. As far as packages are concerned: 

grub = legacy grub
grub-pc = grub 2
grub-common is shared by both legacy grub and grub 2
os-prober is particularly necessary for the proper function of grub 2

So, **[COLOR="Red"]if that shows you have Grub 2[/COLOR]**, as in the example, installing it to the MBR of the proper drive is as simple as:

```
grub-install /dev/sdX
```

Should that produce any errors then:

```
grub-install --recheck /dev/sdX
```

Of course in both of those examples the X must be replaced with the proper DRIVE designation! I can't stress strongly enough that **[COLOR="Red"]it's very seldom wise to install grub (particularly Grub 2) to a partition rather than the MBR of a drive![/COLOR]**

I've also found that if any partitioning changes resulted in the loss of grub 2 boot it's a good idea to run:

```
update-grub
```

**[COLOR="Red"]Had that shown you had legacy grub[/COLOR]** you'd need to open a Grub shell so run the command::

```
grub
```

Note: I've noticed while working in a grub shell that the enter key in the numerical block of the keyboard doesn't always work properly, so use the enter key just above the right shift key!

Then:

```
find /boot/grub/stage1
```

That will provide an output like (hdX,Y) which you'll need to use in the next step:

```
root (hdX,Y)
```

You see I've used (hdX,Y) from the "find" command, of course you'll use the proper drive/partition designations as indicated by that command. Then:

```
setup (hdX)
```

There I've used only the proper drive designation indicated by the "find" command.

If correct you should see an output like:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done.

Hopefully you see three "yes" and two "succeeded" responses. If not something is wrong.

When done we need to exit the grub shell so be sure to run:

```
quit
```

Now, whether you recovered legacy grub or Grub 2, you must exit the chroot and umount when done:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Now, **[COLOR="Red"]how to recover a Windows MBR with only an Ubuntu Live CD[/COLOR]**:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sdX mbr
```

There again, the X must be replaced with the proper drive desigantion!

Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

---

### Post by Corn Flake on 2010-05-29
I would like to add my two cents.  I used your instructions, but having a separate /boot partition, I had to make some tweaks.

```
sudo grub-install [COLOR="Red"]--root-directory=/boot[/COLOR] /dev/sda

```

Even after that, I was greeted with a GRUB console upon boot.  Turns out that it was looking for /boot/grub/menu.lst in the /boot partition, instead of just grub/menu.lst.  So I fixed it with

```
cd /boot
sudo ln -s . boot

```

Now, I'm back to good 'ole Grub1. :)  Thanks for your instructions!!!

---

### Post by kansasnoob on 2010-05-29
> **Corn Flake said:**
> I would like to add my two cents.  I used your instructions, but having a separate /boot partition, I had to make some tweaks.

```
sudo grub-install [COLOR="Red"]--root-directory=/boot[/COLOR] /dev/sda

```

Even after that, I was greeted with a GRUB console upon boot.  Turns out that it was looking for /boot/grub/menu.lst in the /boot partition, instead of just grub/menu.lst.  So I fixed it with

```
cd /boot
sudo ln -s . boot

```

Now, I'm back to good 'ole Grub1. :)  Thanks for your instructions!!!

Aaaaaaaaaaaah, you're very right! I personally detest the use of a separate /boot partition unless absolutely necessary but I really should add a bit about that.

Thank you :)

---

### Post by kansasnoob on 2010-05-31
Just needed a place to throw a screenshot:

[ATTACH]158946[/ATTACH]

---

### Post by kansasnoob on 2010-06-08
> **Corn Flake said:**
> I would like to add my two cents.  I used your instructions, but having a separate /boot partition, I had to make some tweaks.

```
sudo grub-install [COLOR="Red"]--root-directory=/boot[/COLOR] /dev/sda

```

Even after that, I was greeted with a GRUB console upon boot.  Turns out that it was looking for /boot/grub/menu.lst in the /boot partition, instead of just grub/menu.lst.  So I fixed it with

```
cd /boot
sudo ln -s . boot

```

Now, I'm back to good 'ole Grub1. :)  Thanks for your instructions!!!

Thinking about this a bit more I need to try something, but I believe if I drop the "sudo grub-install /dev/sda" entirely and rely only on installing grub to the mbr using a grub shell this situation should be avoided.

In the next day or two I'll do a couple of tests, actually performing a test install with a separate /boot to find out ;)

Thanks for making me aware of this.

---

### Post by kansasnoob on 2010-06-12
> **kansasnoob said:**
> Thinking about this a bit more I need to try something, but I believe if I drop the "sudo grub-install /dev/sda" entirely and rely only on installing grub to the mbr using a grub shell this situation should be avoided.

In the next day or two I'll do a couple of tests, actually performing a test install with a separate /boot to find out ;)

Thanks for making me aware of this.

Nope! Tried that and I'm wrong so I must do an install with a /boot to do more testing :mad:

I still maintain that using a separate /boot is often a problem in itself!

---

### Post by kansasnoob on 2010-06-13
> **kansasnoob said:**
> Nope! Tried that and I'm wrong so I must do an install with a /boot to do more testing :mad:

I still maintain that using a separate /boot is often a problem in itself!

OK I think I'm gaining. It appears instead of running "find /boot/grub/stage1" if a separate /boot partition is used then the command should be:

```
find /grub/stage1
```

Then the output of the terminal after running "setup" is slightly different:

> grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.


But I still need to do a bit more retesting to be certain.

---

### Post by darkbler on 2010-08-18
Nice HowTo,
I'm trying to install grub2 to dual boot ubuntu 10.04 64-bit and windows 7, in Alienware M17x laptop. I did the revert process down to legacy but I could not get the windows partition to load in grub. Then I went back to grub-pc but then I completely lost the ability to load windows even with a SGD (which worked at the beginning to load either OS). Any hints and help will be greatly appreciated.

---

### Post by joachimbelmont on 2010-08-18
hey i know this is totally different to this but can anyone tell me how to create a thread:????? im lost with this and i have may question to do about ubuntu

---

### Post by kansasnoob on 2010-08-20
> **darkbler said:**
> Nice HowTo,
I'm trying to install grub2 to dual boot ubuntu 10.04 64-bit and windows 7, in Alienware M17x laptop. I did the revert process down to legacy but I could not get the windows partition to load in grub. Then I went back to grub-pc but then I completely lost the ability to load windows even with a SGD (which worked at the beginning to load either OS). Any hints and help will be greatly appreciated.

I would need to see the output of the Boot Info Script before proceeding:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'm curious why you needed to revert to begin with, what problems did you encounter with grub2?

It would actually be best to start a new thread here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

You'll get more traffic there ;)

---

### Post by kansasnoob on 2010-08-20
> **joachimbelmont said:**
> hey i know this is totally different to this but can anyone tell me how to create a thread:????? im lost with this and i have may question to do about ubuntu

Just click on the "New Thread" button here for Installations and Upgrades:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

or here for Absolute Beginners:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by kwill on 2010-09-08
Very useful, thanks, it's saved me time looking things up.

I have just installed Lucid and have to revert because as far as I can see there is now no way to pass kernel params via grub.  Easy as with Grub Legacy. Just add in menu.lst

Now if the effort had been put into some better error handling. What does error 15 mean, or error 13.

---

### Post by Corn Flake on 2010-09-09
Grub2 is more complicated that what it should be.  Whereas in Grub1 all you had to do is edit menu.lst and all the options were there, in one spot, in Grub2 you have a multitude of scripts, with the options buried deep in them.  All I wanted to do is require a password for booting into Windows, and a different password for editing boot parameters or booting into single user mode.

In Grub1, all I had to do was insert a couple of password lines in menu.lst and, presto!! I got it.  I tried to do the same in Grub2, but gave up ([http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)).  Too much hassle.

---

### Post by kansasnoob on 2010-09-13
@ kwill & Corn Flake,

I'm sorry it took me so long to respond. I'd been subscribed to this thread for a long time so replies would show up in my in-box but somehow that got goofed up.

Honestly grub2 should be much better in all but a very few corner situations. I obviously need to rewrite some of this and include recommendations to remedy some grub2 errors.

Should you decide to give grub2 another try it's quite simple, just look at Appendix #2 in the original post.

---

### Post by kansasnoob on 2011-05-06
I've been noticing a few too many reports of trouble booting with Natty's grub2 so I'm just posting this to eliminate the need for typing a new post each time. The reports I've been seeing indicate they've already tried recovering grub2 the normal way and also purging and reinstalling grub2 via this guide:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I've not been able to reproduce this on my own hardware so I've not yet figured out exactly what's wrong :(

**Step #1**:

The first thing to do is make sure that Ubuntu will boot so I recommend this disc:

[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

The download link is at the bottom of the page. As it says there, "Super GRUB2 Disk can only be used to boot a broken system, it cannot fix it directly." But I prefer we use only Ubuntu tools and packages to fix Ubuntu's grub2 anyway!

I've found the "Detect any OS" option to work very reliably. Expect it to be slow, like maybe even a couple of minutes slow booting. Chances are that if that disc won't boot your Ubuntu you have other underlying problems so the rest of this guide is likely worthless to you!

So, only if the Super GRUB2 Disk gets you booted into Natty proceed with step #2:

**Step #2**:

Please copy-n-paste all commands.

```
sudo mv /boot/grub /boot/grub_OLD
```

```
sudo mkdir /boot/grub
```

```
sudo mv /etc/default/grub /etc/default/grub_OLD
```

```
sudo rm -R /etc/grub.d
```

Some of the following commands will return a message like "not installed, so not removed" or "E: Unable to locate package", that's OK. You'll need to confirm removal of most packages by typing "y". (NOTE: It's also safe to reinstall 'grub-customizer', 'startupmanager', and 'ubuntu-tweak' after you know that grub 2 is restored and booting properly. But it is NOT safe to install the package 'grub'!) **When you "purge grub-pc" you'll be asked if you're sure you want to remove all grub files so you'll have to confirm that by using the Tab key to select Yes.**

```
sudo apt-get remove startupmanager
```

```
sudo apt-get remove grub-customizer
```

```
sudo apt-get remove ubuntu-tweak
```

```
sudo apt-get purge grub
```

```
sudo apt-get purge grub-pc
```

```
sudo apt-get purge grub-common
```

Reinstalling grub 2 would hopefully require only one command:

```
sudo apt-get install grub-pc
```

That will likely trigger a process that presents a few debconf windows similar to this:

[ATTACH]191329[/ATTACH]

Those windows are generally manipulated with the use of the Tab key, arrow keys, and to select/de-select "grub-install" devices you use the spacebar. **You must know where you want to install grub!**

If we're lucky that will boot now, if not move on to step #3 after the requisite amount of cursing and once again using the SGD2 disc.

**Step #3**: If you're here step #2 failed so we're going to try downgrading to Maverick grub packages, but grub packages are architecture dependent so **[COLOR="Red"]we must know whether this is a 32bit or 64bit OS![/COLOR]** To determine that run the command:

```
uname -m
```

The output **i686** = 32bit so if you have a 32bit OS go to step #4!

The output **x86_64** = 64bit so if you have a 64bit OS go to step #5!

**Step #4**, **[COLOR="Red"]for 32bit OS's only[/COLOR]:**

```
sudo rm -R /boot/grub
``` 

```
sudo mkdir /boot/grub
```

```
sudo rm -R /etc/default/grub
```

```
sudo rm -R /etc/grub.d
```

```
sudo apt-get purge grub-pc
```

```
sudo apt-get purge grub-common
```

```
wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/grub2/grub-common_1.98+20100804-5ubuntu3_i386.deb

```
```
wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/grub2/grub-pc_1.98+20100804-5ubuntu3_i386.deb
```

```
sudo dpkg -i grub-common_1.98+20100804-5ubuntu3_i386.deb
```

```
sudo dpkg -i grub-pc_1.98+20100804-5ubuntu3_i386.deb
```

Again more debconf windows. When complete reboot. If that works then you'll want to keep those packages from upgrading:

```
echo grub-common hold | sudo dpkg --set-selections
```

```
echo grub-pc hold | sudo dpkg --set-selections
```

**Step #5**, **[COLOR="Red"]For 64bit OS's only[/COLOR]:**

```
sudo rm -R /boot/grub
``` 

```
sudo mkdir /boot/grub
```

```
sudo rm -R /etc/default/grub
```

```
sudo rm -R /etc/grub.d
```

```
sudo apt-get purge grub-pc
```

```
sudo apt-get purge grub-common
```

```
wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/grub2/grub-common_1.98+20100804-5ubuntu3_amd64.deb
```

```
wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/grub2/grub-pc_1.98+20100804-5ubuntu3_amd64.deb
```

```
sudo dpkg -i grub-common_1.98+20100804-5ubuntu3_amd64.deb
```

```
sudo dpkg -i grub-pc_1.98+20100804-5ubuntu3_amd64.deb
```

Again more debconf windows. When complete reboot. If that works then you'll want to keep those packages from upgrading:

```
echo grub-common hold | sudo dpkg --set-selections
```

```
echo grub-pc hold | sudo dpkg --set-selections
```

**Step #6**:

This is totally optional but I'd personally appreciate it if you'd participate in getting this bug fixed by reporting here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/778059](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/778059)

I'm wondering if it's hardware related so I think it would be very helpful to collect a hardware profile by running:

```
sudo lshw > hardwareprofile.txt
```

You'll then find a file in your home folder titled "hardwareprofile.txt", so if you'll go to that bug report, make a brief comment, and click on "Add attachment or patch" a new window will open and clicking on "Browse" will allow you to locate that file :)

**General notes:**

If you want or need to release the "hold" on those grub packages just run:

```
echo grub-common install | sudo dpkg --set-selections
```

```
echo grub-pc install | sudo dpkg --set-selections
```

Then of course run:

```
sudo apt-get update
```

---

### Post by kansasnoob on 2011-05-08
[ATTACH]191549[/ATTACH]

This is just a test :)

---

### Post by wal3 on 2011-05-26
thanks kansasnoob

---

### Post by ProNux on 2011-09-30
Here is my scenario.  I install Windows x64 in BIOS/MBR mode.  I ran Live Natty to install Natty, but for some reasons, I cannot make it run in BIOS/MBR mode, so my Live USB boots in UEFI/GPT mode.  Absolutely no BIOS setting to change from UEFI/BIOS mode, poor BIOS.

I can install Natty without a problem, but once I reboot, no grub showup and instead boot Windows directly.

One suggestion was to remove GRUB2 and replace with GRUB1, so I followed this procedure.

Already finished Natty install and still has not reboot yet.  I don't want to reboot since grub does not show up and will just boot Windows instead.
Normally, if I follow the procedure, the /boot/grub directory points to the Live USB, not the actual Linux partition that I just installed.  I tried to change the address of the /boot/grub to something like /media/449b8b9e-027d-4272-9382-dc04fb43661/boot/grub to point to my Linux partition but I got errors.

QUESTION:
Is it possible to revert Grub2 to Grub1 while I am at Live USB?

---

### Post by kansasnoob on 2011-09-30
> **ProNux said:**
> Here is my scenario.  I install Windows x64 in BIOS/MBR mode.  I ran Live Natty to install Natty, but for some reasons, I cannot make it run in BIOS/MBR mode, so my Live USB boots in UEFI/GPT mode.  Absolutely no BIOS setting to change from UEFI/BIOS mode, poor BIOS.

I can install Natty without a problem, but once I reboot, no grub showup and instead boot Windows directly.

One suggestion was to remove GRUB2 and replace with GRUB1, so I followed this procedure.

Already finished Natty install and still has not reboot yet.  I don't want to reboot since grub does not show up and will just boot Windows instead.
Normally, if I follow the procedure, the /boot/grub directory points to the Live USB, not the actual Linux partition that I just installed.  I tried to change the address of the /boot/grub to something like /media/449b8b9e-027d-4272-9382-dc04fb43661/boot/grub to point to my Linux partition but I got errors.

QUESTION:
Is it possible to revert Grub2 to Grub1 while I am at Live USB?

While running the Live USB can you run the Boot Info Script and post the results as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'm also curious if your box has a CD/DVD drive. If so the Super GRUB2 Disk is a great tool to have on hand:

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

Note: the download link is at the very bottom of the page. It's not designed to "fix" anything but I've found that it can boot almost anything so it's a nice thing to have while working out boot problems :)

Creating a Super GRUB2 bootable USB drive currently requires the use of dd which can be quite complex and risky so I don't recommend that.

Regardless, the short answer to your question is yes. You can use a chroot from the Live USB to reconfigure grub, including changing from grub 2 to legacy grub. I mentioned it briefly here in post #1, Appendix #1, and included this link:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

**[COLOR="Red"]But you must be certain to mount the proper partition, etc!!!!!!!!!!!!![/COLOR]**

Finally, I may be unavailable for several hours, possibly 12 to 14 hours, so please be patient ;)

If you can boot into Windows right now, doing so will cause no harm. In fact my greatest concern is proceeding in a manner that we know will not harm your existing Windows installation.

I'm also curious, but certainly unsure, if a better way of dealing with this might be to use EasyBCD since Windows boots OK?

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

Should you decide to go that way we'd use a shorter version of a chroot to install Ubuntu's grub to it's own root partition and then let EasyBCD handle the boot process :)

It's really not incredibly complicated, only confusing when you haven't done it before.

---

### Post by ProNux on 2011-09-30
hi kansasnoob.

Actually I've done SO MANY things for the past 2 weeks just making my dual boot work.  The whole description is in the link below. 
*[http://ubuntuforums.org/showthread.php?t=1753717]("http://ubuntuforums.org/showthread.php?t=1753717")  *

Starting from post #5, it's all regarding my notebook up to page 6.  I think some of your future requests (if ever) are detailed in there already because I've done many experiments.
Please try to visit that link.

I've dedicated one hard disk for this, so any request from you I am willing to do, especially if it's a new experiment.  I've spent restless nights, nevertheless, I'm still willing to solve the problem.  I can reformat the Windows partition anytime, I have a handful of resources - bootable USB sticks, various Linux ISOs, working Dual-boot desktop, external DVD, etc... so don't hesitate if we really need to try an experiment.  I just want Dual-boot to work in my notebook.

I also have tried super grub2, BUT IT DOES NOT BOOT, instead, infinite loop after POST.  It is also described in the link above.

For your request, I will post here again my boot info script result (which is also posted in that thread).

Current State:
1. Installed Windows 7 HP x64; confirmed working
2. Ran Natty Live USB
3. Installed Natty alongside Windows 7
4. Reboot. NO GRUB Menu. Proceeds to boot Windows like there is no other OS installed.
4. Boot at "LUCID LYNX" Live USB (Due to Natty boot script bug)
5. Result below.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7390096 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   125,829,119   125,622,272   7 NTFS / exFAT / HPFS
/dev/sda3         125,831,166   625,141,759   499,310,594   5 Extended
/dev/sda5         125,831,168   609,200,127   483,368,960  83 Linux
/dev/sda6         609,202,176   625,141,759    15,939,584  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CEBAD848BAD82F29                       ntfs       System Reserved
/dev/sda2        041A4F051A4EF2EA                       ntfs       
/dev/sda5        283dec49-7d7e-4e40-8109-76e093551ed2   ext4       
/dev/sda6        7d751e0b-ef91-4360-8ed3-204895ba2136   swap       
/dev/sdb1        D87B-2965                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=283dec49-7d7e-4e40-8109-76e093551ed2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=283dec49-7d7e-4e40-8109-76e093551ed2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 283dec49-7d7e-4e40-8109-76e093551ed2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root CEBAD848BAD82F29
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=283dec49-7d7e-4e40-8109-76e093551ed2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7d751e0b-ef91-4360-8ed3-204895ba2136 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.126224518 = 111.804682240  boot/grub/grub.cfg                             1
  60.155155182 = 64.591106048   boot/initrd.img-2.6.38-8-generic               2
 202.131351471 = 217.036886016  boot/vmlinuz-2.6.38-8-generic                  1
  60.155155182 = 64.591106048   initrd.img                                     2
 202.131351471 = 217.036886016  vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32

prompt 0

menu title UNetbootin

timeout 100



label unetbootindefault

menu label Default

kernel /ubnkern

append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --



label ubnentry0

menu label ^Help

kernel /ubnkern

append initrd=/ubninit 



label ubnentry1

menu label ^Try Ubuntu without installing

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --



label ubnentry2

menu label ^Install Ubuntu

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --



label ubnentry3

menu label ^Check disc for defects

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --



label ubnentry4

menu label Test ^memory

kernel /install/mt86plus

append initrd=/ubninit 



label ubnentry5

menu label ^Boot from first hard disk

kernel /ubnkern

append initrd=/ubninit 



--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc
```
To give you a quick overview, hence:
1. Notebook is Fujitsu PH521 AMD E-350, 8GB RAM
2. BIOS: SecureCore Tiano, latest version (1.16)
3. Absolutely NO menu at BIOS to select UEFI or BIOS boot
4. OEM installed Win 7 HP x64 in BIOS/MBR mode (already set aside this hard disk)
5. Fresh Windows installation defaults to BIOS/MBR mode
6. Natty Live boots in UEFI/GPT mode
7. Installing Natty alongside Windows went fine.  First reboot after install: No GRUB menu, just boots Windows directly.
8. Installing Natty "alone" is working, BUT no GRUB after post; just boots directly to Ubuntu.

As for the detailed actions/tests I have done, "please" refer to that thread, my apology.  I think it would be easier if we continue on that thread, so this thread is only dedicated to GRUB2 to GRUB1 reversion, just a suggestion.

At this point, I'll depend on you which one is to try first then this and that.  I'm not a Linux expert but I think can follow instructions well, and I've installed dual boot PCs /NBs many times since Hardy.

If we go the Easy BCD way, so be it.  It's almost 2 AM, hopefully we can continue tomorrow.  Thanks.

---

### Post by ProNux on 2011-09-30
At this point, I removed Windows.I manually created an MBR partition on the hard disk by physically connecting it to my desktop PC and put bak the hard disk on my notebook and installed Natty alone, no Windows.

After first reboot, I ended up infinite loop at POST, NO GRUB menu.

Booted on Natty Live USB.

I've mounted the linux partition and used "chroot"

I got an error, see the last line.
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ clear
















ubuntu@ubuntu:~$ ls /boot
abi-2.6.38-8-generic     memtest86+_multiboot.bin
config-2.6.38-8-generic  System.map-2.6.38-8-generic
grub                     vmcoreinfo-2.6.38-8-generic
memtest86+.bin
ubuntu@ubuntu:~$ ls /boot/grub
gfxblacklist.txt  grubenv
ubuntu@ubuntu:~$ sudo mv /boot/grub /boot/grub_backup
ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ ls /boot
abi-2.6.38-8-generic     grub_backup               System.map-2.6.38-8-generic
config-2.6.38-8-generic  memtest86+.bin            vmcoreinfo-2.6.38-8-generic
grub                     memtest86+_multiboot.bin
ubuntu@ubuntu:~$ ls /boot/grub
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package startupmanager
ubuntu@ubuntu:~$ sudo apt-get --purge remove grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 3 to remove and 256 not upgraded.
After this operation, 7,803 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134325 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso
The following NEW packages will be installed:
  grub grub-common
0 upgraded, 2 newly installed, 0 to remove and 256 not upgraded.
Need to get 2,850 kB of archives.
After this operation, 6,947 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main grub-common amd64 1.99~rc1-13ubuntu3 [2,043 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty/main grub amd64 0.97-29ubuntu61 [807 kB]
Fetched 2,850 kB in 21s (134 kB/s)                                             
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 134009 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.99~rc1-13ubuntu3_amd64.deb) ...
Selecting previously deselected package grub.
Unpacking grub (from .../grub_0.97-29ubuntu61_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up grub-common (1.99~rc1-13ubuntu3) ...
Setting up grub (0.97-29ubuntu61) ...
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee367556

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31457280   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093ad3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    b  W95 FAT32
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


```


Issuing the command, as below, showed that Live USB booted in UEFI mode.```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] EFI v2.00 by Phoenix Technologies Ltd.
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x0000000000054000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x0000000000054000-0x0000000000055000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000055000-0x000000000008f000) (0MB)
[    0.000000] EFI: mem04: type=10, attr=0xf, range=[0x000000000008f000-0x0000000000090000) (0MB)
[    0.000000] EFI: mem05: type=3, attr=0xf, range=[0x0000000000090000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x000000000054d000) (4MB)
[    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x000000000054d000-0x0000000036570000) (864MB)
[    0.000000] EFI: mem08: type=2, attr=0xf, range=[0x0000000036570000-0x00000000372b0000) (13MB)
[    0.000000] EFI: mem09: type=7, attr=0xf, range=[0x00000000372b0000-0x000000007affa000) (1085MB)
[    0.000000] EFI: mem10: type=2, attr=0xf, range=[0x000000007affa000-0x00000000a4081000) (656MB)
[    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x00000000a4081000-0x00000000a40a1000) (0MB)
[    0.000000] EFI: mem12: type=7, attr=0xf, range=[0x00000000a40a1000-0x00000000a40bd000) (0MB)
[    0.000000] EFI: mem13: type=1, attr=0xf, range=[0x00000000a40bd000-0x00000000a411d000) (0MB)
[    0.000000] EFI: mem14: type=7, attr=0xf, range=[0x00000000a411d000-0x00000000a417d000) (0MB)
[    0.000000] EFI: mem15: type=4, attr=0xf, range=[0x00000000a417d000-0x00000000a5848000) (22MB)
[    0.000000] EFI: mem16: type=7, attr=0xf, range=[0x00000000a5848000-0x00000000a587e000) (0MB)
[    0.000000] EFI: mem17: type=4, attr=0xf, range=[0x00000000a587e000-0x00000000a66d6000) (14MB)
[    0.000000] EFI: mem18: type=7, attr=0xf, range=[0x00000000a66d6000-0x00000000a68bf000) (1MB)
[    0.000000] EFI: mem19: type=2, attr=0xf, range=[0x00000000a68bf000-0x00000000a68c5000) (0MB)
[    0.000000] EFI: mem20: type=3, attr=0xf, range=[0x00000000a68c5000-0x00000000a6f0b000) (6MB)
[    0.000000] EFI: mem21: type=5, attr=0x800000000000000f, range=[0x00000000a6f0b000-0x00000000a6f90000) (0MB)
[    0.000000] EFI: mem22: type=5, attr=0x800000000000000f, range=[0x00000000a6f90000-0x00000000a700b000) (0MB)
[    0.000000] EFI: mem23: type=6, attr=0x800000000000000f, range=[0x00000000a700b000-0x00000000a704b000) (0MB)
[    0.000000] EFI: mem24: type=6, attr=0x800000000000000f, range=[0x00000000a704b000-0x00000000a704f000) (0MB)
[    0.000000] EFI: mem25: type=0, attr=0xf, range=[0x00000000a704f000-0x00000000a70ba000) (0MB)
[    0.000000] EFI: mem26: type=6, attr=0x800000000000000f, range=[0x00000000a70ba000-0x00000000a71c2000) (1MB)
[    0.000000] EFI: mem27: type=0, attr=0xf, range=[0x00000000a71c2000-0x00000000a71c6000) (0MB)
[    0.000000] EFI: mem28: type=6, attr=0x800000000000000f, range=[0x00000000a71c6000-0x00000000a71c8000) (0MB)
[    0.000000] EFI: mem29: type=0, attr=0xf, range=[0x00000000a71c8000-0x00000000a72c9000) (1MB)
[    0.000000] EFI: mem30: type=6, attr=0x800000000000000f, range=[0x00000000a72c9000-0x00000000a730b000) (0MB)
[    0.000000] EFI: mem31: type=0, attr=0xf, range=[0x00000000a730b000-0x00000000a731b000) (0MB)
[    0.000000] EFI: mem32: type=10, attr=0xf, range=[0x00000000a731b000-0x00000000a7354000) (0MB)
[    0.000000] EFI: mem33: type=10, attr=0xf, range=[0x00000000a7354000-0x00000000a739b000) (0MB)
[    0.000000] EFI: mem34: type=9, attr=0xf, range=[0x00000000a739b000-0x00000000a73e1000) (0MB)
[    0.000000] EFI: mem35: type=9, attr=0xf, range=[0x00000000a73e1000-0x00000000a73fb000) (0MB)
[    0.000000] EFI: mem36: type=4, attr=0xf, range=[0x00000000a73fb000-0x00000000a7e00000) (10MB)
[    0.000000] EFI: mem37: type=7, attr=0xf, range=[0x0000000100000000-0x000000023f000000) (5104MB)
[    0.000000] EFI: mem38: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed81000) (0MB)
[    0.000000] ACPI: UEFI 00000000a73e7000 0003E (v01 FUJ    PC       00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e1000 0012A (v01 FUJ    PC       00000001 PTL  00000001)
[    5.633936] fb0: EFI VGA frame buffer device
[    6.382641] EFI Variables Facility v0.08 2004-May-17
[    7.739505] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
ubuntu@ubuntu:~$ 

```
As indicated on the previous post, my notebook is open for any test / configuration.  My ultimate target is to enable Dual boot.

---

### Post by kansasnoob on 2011-09-30
Lots to study here and I'm just headed out the door. If I haven't gotten back to this within 24 hours give me a reminder shout ;)

---

### Post by ProNux on 2011-10-01
I tried to "force" Live USB to boot in BIOS/MBR mode by deleting the "efi" folder in the Live USB.

Booted in Live USB, issuing the command, hence:
```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] ACPI: UEFI 00000000a73e7000 0003E (v01 FUJ    PC       00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e1000 0012A (v01 FUJ    PC       00000001 PTL  00000001)
ubuntu@ubuntu:~$ ^C

```

I still get the same ERROR on the last command as my previous post.
```
ubuntu@ubuntu:~$ sudo mv /boot/grub /boot/grub_backup
ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ ls /boot
abi-2.6.38-8-generic     grub_backup               System.map-2.6.38-8-generic
config-2.6.38-8-generic  memtest86+.bin            vmcoreinfo-2.6.38-8-generic
grub                     memtest86+_multiboot.bin
ubuntu@ubuntu:~$ ls /boot/grub
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package startupmanager
ubuntu@ubuntu:~$ sudo apt-get --purge remove grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 3 to remove and 256 not upgraded.
After this operation, 7,803 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134325 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso
The following NEW packages will be installed:
  grub grub-common
0 upgraded, 2 newly installed, 0 to remove and 256 not upgraded.
Need to get 2,850 kB of archives.
After this operation, 6,947 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main grub-common amd64 1.99~rc1-13ubuntu3 [2,043 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty/main grub amd64 0.97-29ubuntu61 [807 kB]
Fetched 2,850 kB in 24s (118 kB/s)                                             
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 134009 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.99~rc1-13ubuntu3_amd64.deb) ...
Selecting previously deselected package grub.
Unpacking grub (from .../grub_0.97-29ubuntu61_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up grub-common (1.99~rc1-13ubuntu3) ...
Setting up grub (0.97-29ubuntu61) ...
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee367556

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31457280   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093ad3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    b  W95 FAT32
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ 

```
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ 

```

---

### Post by kansasnoob on 2011-10-01
> **ProNux said:**
> I tried to "force" Live USB to boot in BIOS/MBR mode by deleting the "efi" folder in the Live USB.

Booted in Live USB, issuing the command, hence:
```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] ACPI: UEFI 00000000a73e7000 0003E (v01 FUJ    PC       00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000a73e1000 0012A (v01 FUJ    PC       00000001 PTL  00000001)
ubuntu@ubuntu:~$ ^C

```

I still get the same ERROR on the last command as my previous post.
```
ubuntu@ubuntu:~$ sudo mv /boot/grub /boot/grub_backup
ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ ls /boot
abi-2.6.38-8-generic     grub_backup               System.map-2.6.38-8-generic
config-2.6.38-8-generic  memtest86+.bin            vmcoreinfo-2.6.38-8-generic
grub                     memtest86+_multiboot.bin
ubuntu@ubuntu:~$ ls /boot/grub
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package startupmanager
ubuntu@ubuntu:~$ sudo apt-get --purge remove grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 3 to remove and 256 not upgraded.
After this operation, 7,803 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134325 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso
The following NEW packages will be installed:
  grub grub-common
0 upgraded, 2 newly installed, 0 to remove and 256 not upgraded.
Need to get 2,850 kB of archives.
After this operation, 6,947 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main grub-common amd64 1.99~rc1-13ubuntu3 [2,043 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty/main grub amd64 0.97-29ubuntu61 [807 kB]
Fetched 2,850 kB in 24s (118 kB/s)                                             
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 134009 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.99~rc1-13ubuntu3_amd64.deb) ...
Selecting previously deselected package grub.
Unpacking grub (from .../grub_0.97-29ubuntu61_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up grub-common (1.99~rc1-13ubuntu3) ...
Setting up grub (0.97-29ubuntu61) ...
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee367556

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31457280   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093ad3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    b  W95 FAT32
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ 

```
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ 

```

**[COLOR="Red"]Please read this all before beginning.[/COLOR]**

So, as indicated by "ubuntu@ubuntu", all that accomplished was removing grub 2 from the live USB. I don't know what effect that may have had on the live USB itself, so step #1 at this point is to assure that the live USB is correct.

I would personally just wipe the usb stick and create a new live USB, then when you boot the live USB press any key when the purple screen with two small icons at the bottom appears.

You have only about 3 seconds to display the language selector followed by the live boot menu. From there select "Check disc for defects". It takes several minutes to complete.

It must show no errors found before proceeding any further!!!!!!!!

This is very important because if the live media is lacking the proper grub packages and/or file structure it can not properly install grub!

Since you ultimately want a dual boot with Windows 7 I would next wipe the drive and reinstall Windows. Make sure it boots properly and then use Windows own partitioning tool to resize the Windows partition, creating the desired amount of free space for Ubuntu.

Once again be sure that Windows still boots properly after the resizing process is done. Next we're going to use the **known good** Live USB to create the partitions for Ubuntu as described here:

[http://members.iinet.net.au/%7Eherman546/p22.html](http://members.iinet.net.au/%7Eherman546/p22.html)

Note: That tutorial shows resizing the Windows partition with Gparted but I prefer using Windows own tools, so skip that part :)

First of all know in advance how large of a SWAP partition you want. Do you know how much RAM you have? You can see in Ubuntu by running:

```
free -m
```

If you truly have 8GB of RAM you'll probably want an 8GB SWAP to insure proper hibernation or suspend abilities.

Anyway review the section about creating partitions there and ask any questions you have before beginning. The reason we're doing this is so you can use the manual installation option (now literally called "Something else" as shown below):

[ATTACH]203318[/ATTACH]

You will have to manually select which partitions are used for what, and you'll then be able to select installing grub to the root "/" partition during installation as shown here:

[http://members.iinet.net.au/%7Eherman546/p22/035.png](http://members.iinet.net.au/%7Eherman546/p22/035.png)

Then you can hopefully boot using EasyBCD in Windows. But I'm kind of getting ahead of myself.

Review that link about creating partitions and installing Ubuntu manually. If you find any of it confusing ask questions before beginning.

You must understand and pay attention to device designations. In the example in that how-to the root "/" partition is /dev/sda5. That is where you'll want to install grub!

Then when the installation is complete and you reboot you'll boot directly into Windows again, only now you'll go to the link below and download and install EasyBCD 2.1:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Note: the free download link is at the bottom of the page.

Then follow the instructions here to setup EasyBCD:

[http://neosmart.net/wiki/display/EBCD/Windows+7](http://neosmart.net/wiki/display/EBCD/Windows+7)

Clear as mud?

A quick recap (since I've had a gazillion interruptions):

Step #1: Create new Live USB and check it for errors.

Step #2: Wipe the drive and reinstall Win 7.

Step #3: Resize Windows using it's own tools.

Step #4: Create the partitions for Ubuntu using Gparted from the Live USB. Be sure to pay attention to partition designations!

Step #5: Install Ubuntu using the "Something else" option so you can select where to install grub, **it must be installed to the root (aka: /) partition!**

Step #6: When the installation is complete you'll boot directly into Windows, so install EasyBCD.

Step #7: Run EasyBCD and follow the "Vista before Linux" steps here:

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

I believe that should work. If not I'll need to see a new results text from the Boot Info Script.

Good luck, if any of this is confusing please ask questions before beginning.

---

### Post by ProNux on 2011-10-01
@kansasnoob,
Thanks for the detailed procedure.  I will follow carefully as I can.  Will post the results once available.  It's 1:00AM in here, so I will try tomorrow.

Actually I've done various tests today, and I got the feeling the BIOS is the problem.  I have limited options to change, NO selection of UEFI/BIOS modes.  I actually had an old Karmic CD, booted Live and installed.  Just installed normally, no errors, no dual boot.  Infinite loop at POST.  Even the Super Grub2 disk won't boot.

---

### Post by kansasnoob on 2011-10-01
> **ProNux said:**
> @kansasnoob,
Thanks for the detailed procedure.  I will follow carefully as I can.  Will post the results once available.  It's 1:00AM in here, so I will try tomorrow.

In deed, rest :)

Just be sure to do one thing at a time, and if you find any of the instructions confusing ask for help and be a bit patient as I'm quite busy ATM.

Normally I don't recommend EasyBCD, but recently I've found hardware situations where it's the only sane option.

---

### Post by ProNux on 2011-10-02
@kansasnoob
It did not work.  When I select "Neosmart Linux" at startup, it only opens a grub shell.

I was thinking on the first place that Even an Ubuntu ONLY (no Dual Boot) does not boot in BIOS/MBR mode, so this EasyBCD may be futile. I can always run Ubuntu in Live USB, may it be UEFI (default) or by forced BIOS/MBR mode (by removing the "efi" folder in the Live USB).  So I'm thinking that my BIOS is the problem and I starting to think that DUAL BOOT is IMPOSSIBLE with my notebook.  I'm not sure if other bootloaders supporting UEFI should work.

Running Boot Info Script, results below.  By the way, the /dev/sda3 is intentionally unformatted.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........;.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7380432 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   167,979,007   167,772,160   7 NTFS / exFAT / HPFS
/dev/sda3         167,979,008   545,425,407   377,446,400   6 FAT16
/dev/sda4         545,427,454   625,141,759    79,714,306   5 Extended
/dev/sda5         545,427,456   608,342,015    62,914,560  83 Linux
/dev/sda6         608,344,064   625,141,759    16,797,696  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     7,826,383     7,826,322   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0CB8D5B2B8D59A92                       ntfs       System Reserved
/dev/sda2        1C7ED95E7ED9316E                       ntfs       
/dev/sda5        8c101f34-679e-404f-85f9-4b0510fbc23c   ext4       
/dev/sda6        992c7bee-ec80-411d-8a74-aa39899719ba   swap       
/dev/sdc1        08EC-09F3                              vfat       KYT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 8c101f34-679e-404f-85f9-4b0510fbc23c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 8c101f34-679e-404f-85f9-4b0510fbc23c
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 8c101f34-679e-404f-85f9-4b0510fbc23c
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=8c101f34-679e-404f-85f9-4b0510fbc23c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 8c101f34-679e-404f-85f9-4b0510fbc23c
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=8c101f34-679e-404f-85f9-4b0510fbc23c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 8c101f34-679e-404f-85f9-4b0510fbc23c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 8c101f34-679e-404f-85f9-4b0510fbc23c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0CB8D5B2B8D59A92
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=8c101f34-679e-404f-85f9-4b0510fbc23c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=992c7bee-ec80-411d-8a74-aa39899719ba none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 276.219089508 = 296.587988992  boot/grub/grub.cfg                             1
 261.256381989 = 280.521904128  boot/initrd.img-2.6.38-8-generic               2
 284.212894440 = 305.171271680  boot/vmlinuz-2.6.38-8-generic                  1
 261.256381989 = 280.521904128  initrd.img                                     2
 284.212894440 = 305.171271680  vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32

prompt 0

menu title UNetbootin

timeout 100



label unetbootindefault

menu label Default

kernel /ubnkern

append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --



label ubnentry0

menu label ^Help

kernel /ubnkern

append initrd=/ubninit 



label ubnentry1

menu label ^Try Ubuntu without installing

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --



label ubnentry2

menu label ^Install Ubuntu

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --



label ubnentry3

menu label ^Check disc for defects

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --



label ubnentry4

menu label Test ^memory

kernel /install/mt86plus

append initrd=/ubninit 



label ubnentry5

menu label ^Boot from first hard disk

kernel /ubnkern

append initrd=/ubninit 



label ubnentry6

menu label Try Ubuntu without installing

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --



label ubnentry7

menu label Install Ubuntu

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --



label ubnentry8

menu label Check disc for defects

kernel /casper/vmlinuz

append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --



--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

``` 

The history of my tests are found here. If you have not yet read, PLEASE do.
 [http://ubuntuforums.org/showthread.php?t=1753717&page=2]("http://ubuntuforums.org/showthread.php?t=1753717&page=2").  

Some key points:
1. My BIOS has no explicit selection to boot in UEFI/BIOS mode

2. If I install Ubuntu Natty x64 (no dual boot), it defaults to UEFI.  After reboot, the grub won't show up but boots directly.  If I force install to MBR (by manually creating/specifying MBR partition by connecting th hard disk to my dekstop), it results to infinite loop at POST.  If I install Ubuntu after installing Windows in MBR mode, it just boots directly Windows, no GRUB menu, as if no other OSes were installed except Windows.

3. If I attempt to install Windows 7 x64, it defaults to MBR.  If I force install Windows in UEFI (by manually creating UEFI/GPT), it won't continue.  It says Windows cannot be installed in a GPT disk.  Same error when I install Windows after Ubuntu install (dual boot) in UEFI/GPT.

4.  My BIOS seems to reject GRUB1.  It can accept GRUB2 but no GRUB menu after 1st reboot after Ubuntu install (no dual boot).  Even Super Grub2 WON'T boot!

5.  I'm thinking of using ELILO or Syslinux or any other boot loaders.  I think this is my direction right now.  What do you think?  But I don't know yet how.

Please read the history of my tests done on my notebook as I posted above. I've spent much effort on my dual boot to work.

I'm thinking this may be a new problem for Dual boot that needs to be addressed for a troublesome BIOS like mine.

---

### Post by ProNux on 2011-10-02
@kansasnoob
[COLOR="Red"][SIZE="3"]UPDATE:[/SIZE][/COLOR]
Out of curiosity, I followed your procedure again and installed Natty [COLOR="Red"][SIZE="3"]x86[/SIZE][/COLOR] (I have always used x64 in my previous tests) and the Easy BCD worked!  The Grub menu appeared after selecting the NeoSmart Linux (I did not rename the default name) at boot time.  What seems to be the rootcause?  Is it the GRUB2 for x-64?  If so, how to install GRUB from x86 to run Ubuntu x64?

I want to take full advantage of x64 because my CPU supports it and I have plenty of RAM.

---

### Post by kansasnoob on 2011-10-02
> **ProNux said:**
> @kansasnoob
[COLOR="Red"][SIZE="3"]UPDATE:[/SIZE][/COLOR]
Out of curiosity, I followed your procedure again and installed Natty [COLOR="Red"][SIZE="3"]x86[/SIZE][/COLOR] (I have always used x64 in my previous tests) and the Easy BCD worked!  The Grub menu appeared after selecting the NeoSmart Linux (I did not rename the default name) at boot time.  What seems to be the rootcause?  Is it the GRUB2 for x-64?  If so, how to install GRUB from x86 to run Ubuntu x64?

I want to take full advantage of x64 because my CPU supports it and I have plenty of RAM.

Great, that's helpful. Now be a bit patient so we can figure this out and get you set up properly :)

Somehow the 64 bit version failed to install grub to the partition boot sector. Look here:

> sda5: __________________________________________________________________________

    File system:       ext4
    [B][COLOR="Red"]Boot sector type:  -
    Boot sector info:  [/COLOR][/B]
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

Here's an example of what the root partitions output should look like if grub is installed to the boot sector:

> sda9: __________________________________________________________________________

    File system:       ext4
    [B][COLOR="Red"]Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda9 
                       and looks at sector 70638776 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.[/COLOR][/B]
    Operating System:  Ubuntu oneiric (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

You can also see it was missing **[COLOR="Red"]/boot/grub/core.img [/COLOR]**. It may be difficult and somewhat time consuming to figure this out so please be patient and we'll whack away at this one step at a time.

In the process we'll both likely learn a few things and even have a little fun ;)

The first place I want to start is double checking your current partitioning setup. I noticed you created a fairly large FAT16 partition:

> sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    **[COLOR="Red"]Mounting failed:   mount: unknown filesystem type ''[/COLOR]**

Is that for data? I think FAT16 is a poor choice but I'd like to know what you have in mind there.

Also I really stink at math, I always have, so I'd really appreciate either a screenshot of Gparted or the output of:

```
sudo parted -l
```

What I'm thinking is that you might really benefit from a multi-boot with Windows, Ubuntu 32 bit and Ubuntu 64 bit. That way if you're having troubles with something in 64 bit you can see if the behavior is the same in 32 bit, etc.

I do a lot of development iso-testing so I run multi-boots a lot. Here's a shot of a fairly recent testing build:

[ATTACH]203392[/ATTACH]

I don't recommend the same setup for you but it's just an example. I find it's always cool to have one well working stable distro while I'm testing a new one.

That way when the new one frustrates me to the point I'm about to pull all of my hair out I can just boot into the stable OS and enjoy.

I may be quite busy, and therefore have limited time to reply, for the next couple of weeks due to Oneiric final bug fixing and iso-testing, and I'm also trying to finish up remodeling my kitchen, so please be patient :D

---

### Post by kansasnoob on 2011-10-02
I just had a silly thought. Were both the 64 bit and 32 bit installation media produced with Unetbootin? 

I don't currently have 64 bit hardware to test on, but I will have in a few weeks. In fact I have a new mobo and CPU coming next week, but I have Oneiric testing to complete in the meanwhile (eleven days left to go) and I need to decide what case and other peripherals to use once I get it :)

But I very strongly suspect a problem with the installation media, no idea if it's an Ubuntu bug or something to do with Unetbootin.

Once we get a solid partitioning plan in place I think it would be wise to create a new 64 bit Live USB using your newly installed 32 bit with Ubuntu's own "Startup Disk Creator" just to be sure it's not a problem with how Unetbootin is handling the creation.

And always check the disk/USB integrity as previously explained :D

BTW, oldfred is very darn good at partitioning layouts ;)

---

### Post by ProNux on 2011-10-02
> **kansasnoob said:**
> I just had a silly thought. Were both the 64 bit and 32 bit installation media produced with Unetbootin? 

I don't currently have 64 bit hardware to test on, but I will have in a few weeks. In fact I have a new mobo and CPU coming next week, but I have Oneiric testing to complete in the meanwhile (eleven days left to go) and I need to decide what case and other peripherals to use once I get it :)

But I very strongly suspect a problem with the installation media, no idea if it's an Ubuntu bug or something to do with Unetbootin.

Once we get a solid partitioning plan in place I think it would be wise to create a new 64 bit Live USB using your newly installed 32 bit with Ubuntu's own "Startup Disk Creator" just to be sure it's not a problem with how Unetbootin is handling the creation.

And always check the disk/USB integrity as previously explained :D

BTW, oldfred is very darn good at partitioning layouts ;)

My long reply is still being composed, so to answer you now, YES, I used Unetbootin.  I also tried the Ubuntu Startup Disk creator before - same results.  Infinite loop at POST.  So using Unetbootin & the Ubuntu startup disk creator in my Dual Boot PC (Maverick x64 / Windows 7 x64)  yielded similar results, at least on my hardware.  I hope you can get your 64-bit HW soon, so you can confirm also.  My notebook is using AMD E-350 APU, I'm not sure if there may be differences.

I had checked the Live USB data integrity first before install.  I'm inclined this is a bug (I might be wrong though).  If so, at least it might be fixed before Oneiric.

---

### Post by ProNux on 2011-10-02
> **kansasnoob said:**
> 

The first place I want to start is double checking your current partitioning setup. I noticed you created a fairly large FAT16 partition:

Is that for data? I think FAT16 is a poor choice but I'd like to know what you have in mind there.

You are right; that empty partition is for Data.  I wonder where did you get the FAT16 when I haven't formatted it yet.

Actually, since I have plenty of time this morning, I tried at least three tests.
One instance, when my dual boot (Natty x86 & Win7 x64) was already working, I installed Natty x64 on another partition and somewhat "fooled" the installation process where to install GRUB of x64 (since I don't want to use the x64 GRUB) - I inserted another USB stick and installed the x64 GRUB there, and later remove! :idea: :D

When I finally finished (hence, triple boot now), as expected I cannot boot Natty x64 because I already removed the USB stick where the x64 GRUB was installed.  I just booted to Natty x86 and ran
```
sudo update-grub
``` so it can add entries to the x86 GRUB menu list.  Easy BCD was still used.

I rebooted, and finally had a successful triple boot (never thought I would end up in a triple-boot when I had spent weeks just to enable dual boot :o . Actually I can already live with this, but in essence, I still have not yet understood the whole scenario, and if there is really a bug.

I reformatted/wiped the disk (again) just for the sake of experiments.  This time I wanted to use the x86 GRUB with Natty x64. I ended up creating a dedicated GRUB partition (1st partition, 10MB, ext2 format), reinstalling Windows, and then Natty x86.  Dual boot is working through EasyBCD (without EasyBCD, I could not Dual boot).

Now since I just wanted the Natty x64 & GRUB x86, I installed Natty x64 on the partition of Natty x86, overwriting. Again, I directed x64 GRUB to the USB stick.  Installation done.
Reboot, and now I cannot boot Natty x64.  I tried to boot x64 live USB to do chroot and install grub manually but I get the same errors like in my post 63, as below.
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda

Probing devices to guess BIOS drives. This may take a long time.

Could not find device for /boot: Not found or not a block device.

ubuntu@ubuntu:~$
```
Last experiment, since I have another Linux iso, this time, it's Mint Katya x86, I tried to Dual-boot it with Windows x64, overwriting the GRUB partition with the GRUB in Mint's Live USB.

Result:  Working fine, still with EasyBCD.

So I confirmed, at least two x86 distros (albeit Mint Katya is based in Ubuntu) are working with their default x86 GRUBs.

Based on your snapshot, you did not allocate a separate GRUB partition.  Any disadvantages?

So my snapshot is below.  Can we start experimenting on my current setup?  Sorry if I destroyed the first setup.  If you suggest to reinstall and remove the GRUB partition, that would be okay.  The last partition is unformatted yet and is intended for data.

By the way, tomorrow is Monday, and my time to experiment is only when I got home at night.

---

### Post by kansasnoob on 2011-10-02
> **ProNux said:**
> My long reply is still being composed, so to answer you now, YES, I used Unetbootin.  I also tried the Ubuntu Startup Disk creator before - same results.  Infinite loop at POST.  So using Unetbootin & the Ubuntu startup disk creator in my Dual Boot PC (Maverick x64 / Windows 7 x64)  yielded similar results, at least on my hardware.  I hope you can get your 64-bit HW soon, so you can confirm also.  My notebook is using AMD E-350 APU, I'm not sure if there may be differences.

I had checked the Live USB data integrity first before install.  I'm inclined this is a bug (I might be wrong though).  If so, at least it might be fixed before Oneiric.

I think you're right about this being a bug with the 64 bit "installer". The live installer is "ubiquity".

The best way I can think of to troubleshoot this is to decide on a sane partitioning layout for you. No need to reinstall Windows again :)

Then set up a multi-boot with your existing 32 bit and a new 64 bit install - even if it fails as usual - and file a bug against ubiquity which will, if we do it right, collect some bug info to begin the debugging effort.

But let's go one step at a time because filing a bug against an unbootable OS requires a specific procedure :)

Very basically, you'd install but rather than rebooting to see if it boots you'd choose to "continue testing" and run the BIS. Then look at the results and see if grub installed where you told it to.

Then, if it once again did not install, you'd file a bug using the terminal by running:

```
ubuntu-bug ubiquity
```

Then give it a title like, Natty amd64 ubiquity fails to install grub. That may need modified but it's best to keep titles fairly basic.

That would collect some info from the installation process, but you should then leave that installation installed for quite a while if possible.

I do know how to properly install grub (either version) using a chroot, but it's not super duper simple. Well, it is to me, but there are a number of things to take into consideration :)

So lets figure out a truly appropriate partitioning scheme and then work from there. After wasting a week or so I hope you'll be patient now that we're beginning to narrow this down.

I very much appreciate your dedication to getting this figured out. Ubuntu needs more dedicated users such as yourself :D

---

### Post by kansasnoob on 2011-10-02
I have personally never used a separate grub partition and I'll certainly waste no more time helping you because you fail to follow my detailed instructions time after time!

That's it! I'm done! Find someone else to help you!

If you wish you can report me to the forum mods, but I have other things to do and I will not waste my time on someone that's impatient and refuses to follow instructions!

---

### Post by ProNux on 2011-10-02
> **kansasnoob said:**
> I have personally never used a separate grub partition and I'll certainly waste no more time helping you because you fail to follow my detailed instructions time after time!

That's it! I'm done! Find someone else to help you!

If you wish you can report me to the forum mods, but I have other things to do and I will not waste my time on someone that's impatient and refuses to follow instructions!

I have followed you since the previous pages, and what I did above are "extras" since I have enough time yesterday, so while waiting for you until midnight (local time), at least I can do more tests and give results.  You might misunderstood me. I gave you the data you need, and I can continue or start over again as to what setup you want in my own expense of time.

If you think I have not followed you, think again.  But anyway, thanks for your effort.

---

### Post by Elfy on 2012-06-30
Closed - information available at [https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)

---

