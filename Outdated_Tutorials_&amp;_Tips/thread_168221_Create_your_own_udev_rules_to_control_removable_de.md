---
title: "Create your own udev rules to control removable devices"
date: 2006-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Sutekh on 2006-04-30
I'm sure many people who use removable devices have noticed that sometimes they don't appear where they were before.  

You plug your USB drive in, and use fdisk to find the device node and then mount it.  Sometimes the USB appears as /dev/sda1, sometimes /dev/sdb1.  It can depend on what order you plug in your USB devices, and where you plug them in.  This is a real pain if you mount devices manually or if you are trying to customise your /etc/fstab.

[udev]("http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html") allows the assignment of a persistant device node, /dev/..., based on a rule match defined by your specific hardware.  In other words, if a device is attached that matches certain criteria it is given it's own device node, rather than being assigned a dynamic one.

It's actually really easy to setup.

______

To start with you need to know the dynamic device node that is given to a device when attached for the first time.  The way that I would do this is to use the **tail** command
```
tail -f /var/log/messages
``` When a device is plugged in, the screen will update with the newest messages, usually imparting some knowledge on the location of the new device.  My USB flash disc for example, produced this output when plugged in.
> Apr 30 16:37:01 localhost kernel: [4294885.683000] usb 1-3: new full speed USB device using ohci_hcd and address 6
Apr 30 16:37:01 localhost kernel: [4294885.853000] scsi5 : SCSI emulation for USB Mass Storage devices
Apr 30 16:37:02 localhost usb.agent[10421]:      usb-storage: already loaded
Apr 30 16:37:06 localhost kernel: [4294890.859000]   Vendor:           Model: TS128MJFLASHA     Rev: 1.00
Apr 30 16:37:06 localhost kernel: [4294890.859000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Apr 30 16:37:06 localhost kernel: [4294890.883000] SCSI device **sdd**: 253400 512-byte hdwr sectors (130 MB)
Apr 30 16:37:06 localhost kernel: [4294890.896000] **sdd**: Write Protect is off
Apr 30 16:37:06 localhost kernel: [4294890.924000] SCSI device **sdd**: 253400 512-byte hdwr sectors (130 MB)
Apr 30 16:37:06 localhost kernel: [4294890.937000] **sdd**: Write Protect is off
Apr 30 16:37:07 localhost kernel: [4294890.937000]  /dev/scsi/host5/bus0/target0/lun0: p1
Apr 30 16:37:07 localhost kernel: [4294891.046000] Attached scsi removable disk **sdd** at scsi5, channel 0, id 0, lun 0
Apr 30 16:37:07 localhost scsi.agent[10469]:      sd_mod: loaded sucessfully (for disk) The output shows that the USB device attached is assigned the device node **/dev/sdd**.  You may also want to determine the partition number using 
```
sudo fdisk -l
``` For my USB flash disc, the partition is **/dev/sdd1**.  

So next thing is to find out some unique information from the device, information that will be used in defining the udev rule, remembering a match is required to assign the persistant node. The next command I have used is from the [Writing udev rules]("http://reactivated.net/writing_udev_rules.html") link at the bottom of this HOWTO
```
udevinfo -a -p $(udevinfo -q path -n **/dev/sdd**)
``` This command outputs a lot information about the hardware associated with **/dev/sdd**.  I've left out *a lot* of the information, leaving only the section I think is most relevant.  This section contains the more specific information about my USB flash disc.  

Note the bolded text in the output.  It is important that information used in a udev rule is contained in the one section.
```

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
[B]Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.[/B]
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:02.0/usb1/1-3':
    [COLOR=red]BUS=="usb"[/COLOR]
    ID=="1-3"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0100"
    SYSFS{bmAttributes}=="80"
    SYSFS{configuration}==""
    SYSFS{devnum}=="6"
    SYSFS{idProduct}=="0005"
    SYSFS{idVendor}=="0c76"
    SYSFS{maxchild}=="0"
    [COLOR=red]SYSFS{product}=="TS128MJFLASHA"[/COLOR]
    SYSFS{speed}=="12"
    SYSFS{version}==" 1.10"

``` The items that contain specific information regarding my USB disc have been coloured red.  These are the two items of interest to me, the device is connected to the [COLOR=red]USB[/COLOR] bus, and the product is identified by [COLOR=red]TS128MJFLASHA[/COLOR]

______

The next step is to create the udev rule concerning this device. I'll start by creating my own .rules file
```
sudo nano /etc/udev/rules.d/10-local.rules
``` By naming my set of rules **10-local.rules** they should be looked at before the other rules set in this folder.

The rule I will use for the flash disc looks like this.
> [COLOR=red]BUS=="usb"[/COLOR], [COLOR=red]SYSFS{product}=="TS128MJFLASHA"[/COLOR], [COLOR=green]KERNEL=="sd?1"[/COLOR], [COLOR=Blue]NAME="transcend128mb"[/COLOR], [COLOR=Magenta]SYMLINK="usbdevices/transcend128mb"[/COLOR] A quick explanation.

 - The [COLOR=red]BUS==&#8221;usb&#8221;[/COLOR] and [COLOR=red]SYSFS{product}==&#8221;TS128MJFLASHA&#8221;[/COLOR] options are the same as those I picked out from the **udevinfo** output.

 - The option [COLOR=green]KERNEL="sd?1"[/COLOR] will only match locations like /dev/sda1, /dev/sdb1 and more importantly, it won't match nodes like /dev/sda, /dev/sdb, which can be fdisk'ed.  The 'Writing udev rules' guide also mentions this.

 - The options [COLOR=Blue]NAME="128FLASH"[/COLOR] and [COLOR=Magenta]SYMLINK="usbdisc/128FLASH"[/COLOR] will create the persistant node at /dev/transcend128mb and a symlink /dev/usbdisc/transcend128mb that points to the persistant node /dev/transcend128mb.  The SYMLINK option is not required.  The reason I have included it is so that all my USB devices will have a symlink starting with /dev/usbdevices/...
I just think its neater.

There are other options that could be used to create udev rules, such as GROUP=&#8221;some_group&#8221;, if you want to assigned the group ownership of the device node to a specific group, and MODE=&#8221;0660&#8221;, which would give the owner/group read and write permissions, like **chmod**.

The [Writing udev rules]("http://reactivated.net/writing_udev_rules.html") guide contains some more detailed information on these other options.

______

To start using these new rules, you need to run the command udevstart 
```
sudo udevstart
```
You can also restart udev using 
```
sudo /etc/init.d/udev restart
```
This should work for later versions of udev, that don't appear to use the udevstart command

- thanks to **ash211** for pointing this out

Now to quickly check that the new node for my example has been created.
```
user@ubuntu:~$ ls -l /dev/trans*
brw-r-----  1 root plugdev 8, 49 2006-04-30 16:37 /dev/transcend128mb
user@ubuntu:~$ ls -l /dev/usbdevices/
lrwxrwxrwx  1 root root 17 2006-04-30 16:37 transcend128mb -> ../transcend128mb
``` 
______

Finally the fstab can be edited to include the new persistant device node, but first we'll back it up
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Then we can add an entry for the example USB device using either the device node **or** the symlink (if used), so in my example I could either use the new device node
```
/dev/transcend128mb  /media/usb128mb  vfat  iocharset=utf8,umask=000   0   0
``` **or** the symlink to the node, which I prefer as all my USB devices have symlinks in /dev/usbdevices.  I think makes the fstab look neater.
```
/dev/usbdevices/transcend128mb  /media/usb128mb vfat iocharset=utf8,umask=000  0  0
``` When the entry has been correctly entered, you can save the file (Ctrl+O) and exit (Ctrl+X), and then mount the device, in this example my USB disc using
```
sudo mount /media/usb128mb
``` or
```
sudo mount -a
``` Once this is all completed, the example USB drive will always appear at /dev/transcend128mb so the entry in the fstab can remain unchanged and will always find the device.


And you're all done!


Hope that helps some people, like it did me.  

Please let me know if this works for you, and of course if there are any typos, errors or things that need clarifying.



The useful links I needed to get this working
[Kernel.org - udev]("http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html")

[Writing udev rules]("http://reactivated.net/writing_udev_rules.html")

---

### Post by Sutekh on 2006-05-05
I feel so cheap for doing this, but that was a lot of work.   I would love to know if anyone has tried this, and how it went.

---

### Post by DrBair on 2006-05-14
I just used the guide to set up a custom node/mount point for my flash card reader.  Its been a long time since I've played with udev and I needed the help. Thanks!

I think theres just not a lot of people out there that need this or are willing to dabble with config files.  But I'm sure plenty of people (like me) will get good use out of this guide.

---

### Post by Sutekh on 2006-05-15
Thanks for the feedback.  

I actually wrote this after a thread where several people were encountering the same issue with USB devices.   It does look like hard work, but it's mostly documenting the output from commands.  There's only really a handful of commands that you have to do.

Glad it helped you out.

---

### Post by woot on 2006-05-22
*edit* rebooting helped solving my problem

---

### Post by Ocxic on 2006-05-22
this is a great guide my usb audio keeps getting shuffled this should help me get it under control, thanks.

---

### Post by DROP on 2006-05-22
I am going to try this when I get home. It looks very useful.

---

### Post by DROP on 2006-05-23
Thanks - this is pretty cool.

---

### Post by EReckase on 2006-05-23
I have a 512 MB Intelligent Stick USB drive that I want to use for my GnuPG keys.  I want the USB drive to automatically be mounted at a known location every time it's plugged in, so that the GnuPG paths can stay fixed regardless of whether or not I plug in another device.  This HOWTO worked great, except for one little detail...how can I make the USB drive automount now that I've set up a mount point for it?  When I remove the drive, re-inserting it does not automount it like it did before I made the changes above.  I'll happily install autofs if need be, but I could use some pointers (/me is a n00b).

The one difference I had from your tutorial is that my external drive is formatted ext3 rather than vfat, so my mount line in fstab is
```
/dev/usbdevices/usb_gnupg  /media/usb_gnupg ext3 defaults,errors=remount-ro  0  0
```

Regards, and thanks for the tutorial.
Is that correct?

---

### Post by Sutekh on 2006-05-24
[quote=woot]*edit* rebooting helped solving my problem[/quote] 
The version of udev in Dapper doesn't seem to have or use *udevstart*.  I ended up re-booting to affect the changes when I tried this in Dapper.  

I'm sure there must be another way though. 

[quote=Ocxic]this is a great guide my usb audio keeps getting shuffled this should help me get it under control, thanks.[/quote] Well make sure you let me know if this works for your audio devices, and if you wouldn't mind post your rules here too.   


I think udev rules might also be useful for people with multiple network cards (such as me!) and who find that they get swapped after updates (:().  This is something I wan't to give a try soon.

[quote=DROP]Thanks - this is pretty cool.[/quote] 
I'm glad it helped you out. Feel free to post your udev rules if you think they had something extra to them. The ones I used here were pretty plain.

---

### Post by Sutekh on 2006-05-24
> **EReckase]I have a 512 MB Intelligent Stick USB drive that I want to use for my GnuPG keys. I want the USB drive to automatically be mounted at a known location every time it's plugged in, so that the GnuPG paths can stay fixed regardless of whether or not I plug in another device. This HOWTO worked great, except for one little detail...how can I make the USB drive automount now that I've set up a mount point for it? When I remove the drive, re-inserting it does not automount it like it did before I made the changes above. I'll happily install autofs if need be, but I could use some pointers (/me is a n00b).

The one difference I had from your tutorial is that my external drive is formatted ext3 rather than vfat, so my mount line in fstab is
```
/dev/usbdevices/usb_gnupg  /media/usb_gnupg ext3 defaults,errors=remount-ro  0  0
``` 
Regards, and thanks for the tutorial.
Is that correct?[/quote] You don't need autofs.  If you are using the **gnome-volume-manager** (default Ubuntu/GNOME installation = yes), it should handle the automounting.  

All udev does is set the device node for the attached device, which you have done correctly if you can mount the USB via the new device node.

Getting it to automount should really only be an issue with the /etc/fstab.  The fact that it is ext3, should make this easier too.  I always had major issues trying to automount FAT16 partitions in Breezy.

________________

When the gnome-volume-manager finds a new device (courtesy of hotplug, hal and udev) it will mount it using its own method. What's special about the gnome-volume-manager is that it can mount a device without needing root privileges. Meaning it doesn't require *sudo*.

If a line in the /etc/fstab has been specified, then that line takes precedence over the gnome-volume-manager's method. If this is the case, the line must allow for an ordinary user to mount the USB disc, or the gnome-volume-manager can't mount it automatically.

That's the theory though  said:**
> 
/dev/usbdevices/usb_gnupg  /media/usb_gnupg ext3 **user**,[COLOR=Red]suid,dev,exec,auto, async[/COLOR],errors=remount-ro  0  0 Then try un-plugging/plugging in the USB.

  - I replaced the **defaults** option with [COLOR=Red]suid,dev,exec,auto, async [/COLOR]because the **user** option over-rides the defaults (the options in red).  You can read more about these options, by using
 ```
man mount
```  or going here

[Mount Man Page]("http://www.die.net/doc/linux/man/man8/mount.8.html")
[COLOR=Red]

[/COLOR]Fingers crossed.

---

### Post by ash211 on 2006-05-24
[QUOTE=Sutekh]The version of udev in Dapper doesn't seem to have or use *udevstart*.  I ended up re-booting to affect the changes when I tried this in Dapper.  

I'm sure there must be another way though. [/QUOTE]

I searched around and found out that ```
sudo /etc/init.d/udev restart
``` will do the same thing.


By the way, thanks for writing this up Sutekh, it's always nice to learn something!

---

### Post by Sutekh on 2006-05-26
[quote=ash211]I searched around and found out that ```
sudo /etc/init.d/udev restart
``` will do the same thing.


By the way, thanks for writing this up Sutekh, it's always nice to learn something![/quote]
Ok that's great.  Makes sense to have it there, along with countless others (gdm, powernowd, firestarter, etc)

Thanks for pointing that out!  I shall edit the original post and include that if I port this HOWTO for Dapper.

I'm glad you found it useful!

---

### Post by woot on 2006-06-01
i rechecked this thread for the automount thingy which has been discussed here :)

about the udev start i already knew, my problem, for which i had to reboot, was that udevinfo -p - blabla etc :) didnt work correctly, no matter what i tried and as i was sure i had it done before i just started after a clean startup :)

---

### Post by grsing on 2006-06-03
Thanks!  Fixed both that problem, and, with the MODE part in the rules, my problem with permissions on my flash drive.  Only question is, is there a way to make the drive still automount with this, rather than having to do it manually?  If not, it's only a minor annoyance, but that'd be awesome if there was.  Thanks again.

Nevermind, I just read the rest of the thread.  Great stuff.

---

### Post by Stormbringer on 2006-06-08
Sutekh, you were so kind to point my attention to this HOWTO in the reply to the question I posted over in the "Video and Sound" forum.

In the meantime I did a little research on the matter of "How do I swap the sound device?" ... seems as this isn't going to be as easy to solve as writing up a rule for automounts. Nailing the sound devices to a specific /dev/dsp|audio|mixer seems a lot more troublesome.

I dug my way through the boot-process of Dapper to see where and why the sound devices get "mixed up" (Remember? Breezy, using hotplug for the job, initialized them the other, correct, way around) --- and after seven (7) hours I still have no clue why the usb headset gets initialized before the onboard ac97 codec.

Maybe you, or anyone else, will happen to have an idea that'll lead the way to crack it down ...

By looking at /var/log/udev (the log that gets written by udevmonitor) I clearly see that the usb-audio device gets initialized first (/dev/dsp|audo|mixer) - followed by the onboard audio (/dev/dsp1|audio1|mixer1).

What I'm unable to grasp is -> where does the assignment of the device-nodes actually happen?

The rules in /etc/udev/rules.d all look very nice - but which one of them does the job? 

20-names.rules seems to be the closest one, but by looking at the content the audio devices are listed in top of usb; so the onboard audio should be the first on the line (unless I'm terribly mistaken).

So, the question is ...

Does anyone know which udev rule is in charge of assigning the device-nodes (/dev/dsp, /dev/audio and /dev/mixer) to the hardware/driver?

Having a starting point would surely help to dig further into it to get the problem solved.

Thanks for any valueable ideas,
Storm.

---

### Post by snaga on 2006-06-27
This has been a very useful how-to, thanks.

I am having a bit of difficulty with something I'm trying to do, so I'm hoping to get a little more help.

I used this how-to to get a Sandisk 1GB Cruzer mounting properly. Here's what I would like to do:

I need to make sure that the Cruzer gets backed up to my HD each time it is unmounted. I am already backing it up when it mounts, using the RUN command and an ACTION of "add". I am trying to run a script when the ACTION is "remove", but that doesn't seem to happen. Here is my rules line for this:

```

BUS=="usb", SYSFS{product}=="Cruzer Mini", KERNEL=="sd?1",ACTION=="remove", RUN+="/usr/local/scripts/test.sh"

```

The script referenced in this line is just to tell me if it is working. It isn't. The scripts exists there and runs ok on its own, but doesn't run on an umount of the Cruzer.

Any thoughts? Thanks.

---

### Post by djaya2 on 2006-07-12
Hey - This was super helpful!  Now my comp recognizes my flash drive the same way every time.  One question, though, how do I make it work for two drives?  Whenever I try to add an iPod too, the system doesn't recognize either drive properly any more.  I tried two ways---adding another line for the iPod to the .rules file, and when that didn't work, adding a semicolon at the end of the line.  No luck with that either.  Thanks, though, this guide is just what I wanted.

---

### Post by domino on 2006-07-15
Hi and thank you for this tut. I wonder if this will fix my USB issues.

I have a USB wlan stick and an ext USB drive. Every time i mount/dismount the ext drive, I loose the USB wlan device. Do you think this will help me from having to unplug and connect the USB wlan every time I mount/dismount the ext drive?

---

### Post by TiredBird on 2006-08-09
Unfortunately I read this HOWTO after I had solved my problem by another means. Now however, I'm wondering if the method I used is okay or if I just got lucky.

I am using both an external USB hard-drive (160GB) and a USB thumb-drive (1GB). The contents of the hard-drive (I call it 'WD-160') are shared on my network via Samba whereas the contents of the thumb-drive (I call that 'WWMEM1G') are part of an encrypted file system. Thus it is important, regardless of the order in which they are inserted, that they always end up mounted at the same place, (and I wanted them each in their own root level folders, not in '/media').

Both are formatted FAT32 and since I have used them both on a WIN XP system, I was able to label the drives as 'WD-160' and 'WWMEM1G'. I noticed that when mounted in '/media', folders were created with those names. 

In '/dev/disk/by-label' I found symbolic links having the same names and pointing to either '/dev/sda1' or '/dev/sdb1' depending on which order I had inserted them. 

In '/etc/fstab' I added mount directives for the devices '/dev/dis/by-label/WD-160' and '/dev/disk/by-label/WWMEM1G' specifying the desired mount points for each as well as the other usual parameters for FAT32 filesystems.

Both filesystems now mount in the correct spot automatically. When they are inserted, (boot time or later), or the order of insertion does not seem to matter.

In order for them to mount automatically, I had to set the 'Removable Drives and Media Preferences', (System > Preferences > Removable Drives and Media), with a check-mark in each of the first two boxes on the 'Storage' tab.

It works fine but with all of my screwing around to get it to work I have ended up with duplicate icons on the desktop, (two for each of my devices when mounted). Any suggestions for how to get rid of the extras.

(Please forgive my ignorance about all of this, I'm a Ubuntu/Linux newbie and until I read this howto I had never even heard of 'udev'.)

---

### Post by hanzomon4 on 2006-09-06
Nevermind fix with a reboot and fsck

---

### Post by rshel on 2006-10-20
I haven't tried this yet, but I'm curious to know if it will work with more than one usb drive.  I have four (yes 4, i'm ashamed to say) Cruzer Minis from SanDisk that I use for various things.  Following the guide, each needs something unique to identify it so it can be mounted at the same place.  But all have Product Name "cruzer mini" and the same product id, etc. so what would I do in this case?  Thanks in advance and apologies if this is a dumb question.

---

### Post by koshari on 2006-10-29
i dont know about a product ID but i used a model string and mine worked fine on dapper, maybe you could mask the sd?1 part to reflect the various sticks?

heres my ```
10-local.rules
``` file

```
BUS=="usb", SYSFS{Model}=="MTM809A2-103  00  Rev: 1.01", KERNEL=="sd?1", NAME="mysonSD", SYMLINK="usbdevices/mysonSD"
```

and after a quick
```

sudo /etc/init.d/udev restart
```

i was in buisness.

---

### Post by dugan on 2006-10-29
This is odd. When I used update-manager to upgrade to Edgy, update-manager removed udev. No problem; I reinstalled it. But now none of my udev rules work anymore.

The permissions and ownership appear to be set correctly:

```

**>ls -l /etc/udev/rules.d/10-local-rules**
-rw-r--r-- 1 root root 202 2006-10-29 16:55 /etc/udev/rules.d/10-local-rules

```

And the rules file itself is unchanged from when it *did* work.

```

**>cat /etc/udev/rules.d/10-local-rules**
BUS="scsi", SYSFS{model}="YP-U1", KERNEL="sd?1", NAME="ipod"
BUS="scsi", SYSFS{vendor}="Motorola", KERNEL="sd?1", NAME="phone"
BUS="scsi", SYSFS{model}="PSP", KERNEL="sd?1", NAME="psp"

```

Nevertheless, when I plug in my "ipod" (a Samsung knockoff), the device node still gets created at /dev/sda1 and not at /dev/ipod like it's supposed to.

And yes, I've tried running "/etc/init.d/udev restart". Over and over, in fact.

Any ideas?

---

### Post by berserker on 2006-10-29
> **dugan said:**
> Nevertheless, when I plug in my "ipod" (a Samsung knockoff), the device node still gets created at /dev/sda1 and not at /dev/ipod like it's supposed to.

I'm experiencing the exact same situation.  This is the one upgrade issue I haven't figured out.

---

### Post by kabo on 2006-11-01
> **berserker said:**
> I'm experiencing the exact same situation.  This is the one upgrade issue I haven't figured out.

I'm also experiencing this.
Would be nice of somebody had a fix for this...
I have a LaCie-disk (was /dev/LaCie now is /dev/sda3) that I want mounted at /media/LaCie. But when I double-click it to mount it I get a message saying the mount point could not be established.
But when I manually create the directory /media/LaCie the disk mounts no problemo... at /media/LaCie-1
My fix is to make a link from /media/LaCie to /media/LaCie-1

Now when I restart and double-click on the disk it mounts at /media/LaCie-2. So I remove /media/LaCie and /media/LaCie-1. Won't mount.
I then do
```
>sudo ln -s /media/LaCie-1 /media/Lacie
```
Still won't mount. So I remove the link and create the directory /media/LaCie and the disk mounts at /media/LaCie-1 again.
I can then remove /media/LaCie and make the link again.
```
>sudo ln -s /media/LaCie-1 /media/Lacie
```

Now everything works, but it's still annoying.
Permanent fix would be nice... :)

---

### Post by kabo on 2006-11-10
Yeay, I've fixed it! :)
In the first post it said:
> - The option KERNEL="sd?1" will only match locations like /dev/sda1, /dev/sdb1 and more importantly, it won't match nodes like /dev/sda, /dev/sdb, which can be fdisk'ed. The 'Writing udev rules' guide also mentions this.

But it should be KERNEL=="sd?1". (it does say so on the line above it)
Now it works again! :)

---

### Post by dugan on 2006-11-10
Okay I did it.

1. renamed my 10-local-rules file to 10-local.rules

2. smacked self upside the head

3. Changed the contents of 10-local**.**rules to:
```

BUS=="scsi", SYSFS{model}=="YP-U1", KERNEL=="sd?1", NAME="ipod"
BUS=="scsi", SYSFS{vendor}=="Motorola", KERNEL=="sd?1", NAME="phone"
BUS=="scsi", SYSFS{model}=="PSP", KERNEL=="sd?1", NAME="psp"

```

---

### Post by boncey on 2006-11-12
Hi, just a quick thanks for this guide.

I have 4 seperate USB devices that I regularly swap in and out and it's been driving me mad that they always appear on the wrong mount point.
I'd heard udev could be the answer and tonight I decided to look into it.

It took me around 20 minutes from reading your guide to having it all working perfectly.

Thanks a lot.

---

### Post by wgaprotest on 2006-11-25
ok, this is a very good howto, and I was struggling like crazy with the same base document you used. No one seemed to know how to do this, and and a howto I was following didn't mention udev rules at all. 

Question: your base document and your howto both talk about devices, but how about lirc? It's not a block device, but a class in the sys tree, so I'm doing my best here, but I'm not at all sure I'm doing it right. At the latest edit, my 10-local.rules file looks like this:

    BUS=="ide", KERNEL=="hdc", MODE="0666", SYMLINK+="cdrom", GROUP="cdrom"
BUS=="ide", KERNEL=="hdc", MODE="0777", SYMLINK+="cdrw", GROUP="cdrom"
BUS=="ide", KERNEL=="hdc", MODE="0666", SYMLINK+="dvd", GROUP="cdrom"
BUS=="ide", KERNEL=="hdc", MODE="0777", SYMLINK+="dvdrw", GROUP="cdrom"
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="_end"
    [INDENT]# For brother
    SYSFS{idVendor}=="04f9", MODE="666", GROUP="scanner"
    LABEL="_end"[/INDENT]
BUS=="usb", KERNEL=="lirc0", SUBSYSTEM=="lirc", SYSFS{dev}=="61:0",        [INDENT]GROUP=”daemon”, MODE="0777", SYMLINK="usbdevices/remote",  RUN+="/usr/local/bin/change-channel-lirc.pl"[/INDENT]

Obviously I want certain devices writable and executable by all users, as lirc needs to be. And I didn't give it a name because I don't need it to be in a persistant place.

Thank you; I hope it will work better than the last attempt :), and we'll see it if works just as well with Edgy. A lot of people are having real trouble with lirc, so perhaps this late reply will bubble it up.

---

### Post by zoobave on 2007-06-19
is there any way to run a script in "/usr/local/zoobave" whenever a USB is plugged?

---

### Post by Carlos Santiago on 2007-07-17
Yes there is! Just had RUN+="/usr/local/zoobave"

---

### Post by ridgeland on 2007-08-02
Thanks Sutekh,
I had this problem:
Home LAN - wife's laptop and my desktop.
NFS file sharing
New camera via USB, old camera's Compact Flash via a card reader USB.
With Ubuntu 7.04 when I copied the files from the USB device the files were mode 711.  When my wife connected to them she couldn't do anything with them.
Now the two mount with names and mode 777.  Thank again.
I did have a couple of challenges following the steps though.
Your: SYSFS{product}=="TS128MJFLASHA"
for me was: ATTRS{product}=="NIKON DSC COOLPIX S4"
also for BUS I needed SUBSYSTEMS
```
SUBSYSTEMS=="usb", ATTRS{product}=="NIKON DSC COOLPIX S4", KERNEL=="sd?1", NAME="Coolpix_S4", SYMLINK="usbdevices/Coolpix_S4"
```
I also had the problem of not being allowed to mount the USB device after booting.  So I adjusted /etc/fstab to add users like a previous post explained:
```
/dev/Coolpix_S4  /media/Coolpix_S4  vfat  iocharset=utf8,users,umask=000   0   0
```
I also made the directories in /media
$ sudo mkdir /media/Coolpix_S4
Now I have mode 777 which I was seeking and the bonus of better names than disk and disk-1. 
I have not found what the last part of 10-local.rules does ... the SYMLINK=

---

### Post by Sir_Yaro on 2007-11-10
this how-to works fine on gusty

---

### Post by cmccartin on 2007-12-20
I have a Sierra Wireless AC595U EVDO usb modem that I'm trying to write a rule for. When the device is connected, it creates 3 ttyUSB ports. i.e. ttyUSB0, ttyUSB1, ttyUSB2

The actual "modem" port is always the first of the 3 to be created. What I would like to do is have a symlink to the first created ttyUSB port of this device, called "/dev/modem".

To add additional complexity, I have other devices that are also recognized as ttyUSB devices, so I can't just create a symlink directly to /dev/ttyUSB0 and always have it work, since the 3-port USB modem may not have been inserted first.

The basic rule I've been using is:
KERNEL=="ttyUSB*", SYSFS{idVendor}=="1199", SYSFS{idProduct}=="0120", ACTION=="add", SYMLINK+="modem"

The symlink *IS* created, but it is created for the last of the 3 ports, which is not useful.

Using major/minor numbers of the device faces the same issue, so no luck there. Major number is always 188, but minor number depends on order of insertion of ttyUSB devices. (i.e. can't always depend on 188:0)

udevinfo on each of the ports shows the same exact information as far as the physical device attributes are concerned. The only differences are the ttyUSB number, and the minor number of the device.

Any ideas or suggestions on this?

---

### Post by cmccartin on 2008-01-03
Here's the solution that I came up with for my own problem. When the AC595U USB modem is inserted, the SYSFS properties for vendor and product are checked, the new device is called ac595u0,1,2 (or whatever numbers are assigned). The modem.agent script runs with "add" as the argument, and a symlink is created from /dev/modem to whatever the first ac595u device is (ac595u0 if there are no other ttyUSB devices, but this will change if there *are* other ttyUSB devices).

Upon removal (of any ttyUSB device), the modem.agent is executed with "del" as the argument and if no ac595u devices exist, the /dev/modem symlink is removed.


my new udev rules:
```

KERNEL=="ttyUSB*", ACTION=="add", SYSFS{idVendor}=="1199", SYSFS{idProduct}=="0120", NAME="ac595u%n", RUN+="modem.agent add"

KERNEL=="ttyUSB*", ACTION=="remove", RUN+="modem.agent del"

```


The modem.agent script (lives in /lib/udev and must be executable):
** Note: to test this on the command line, change "print $10" to "print $9". For whatever reason, when using awk in a script called from udev, the argument list is increased by 1 **
```

#!/bin/bash

if [ $# -gt 0 ]; then
        MODEM=`ls -l /dev/ac595u* | head -1 | awk '{ print $10 }'`

        if [ "$1" = "add" ]; then
                if [ -n "$MODEM" ]; then
                        ln -sf $MODEM /dev/modem
                fi
        elif [ "$1" = "del" ]; then
                # ac595u device found?
                if [ ! -n "$MODEM" ]; then
                        # device not found - check for modem symlink
                        if [ -L /dev/modem ]; then
                                # remove link to modem
                                rm /dev/modem
                        fi
                fi
        fi
fi
```

---

### Post by ashikahamed on 2008-02-07
When I use udev rules to execute a bash script it is executed more than once (7 times).Is there a way to stop it after the first time?

---

### Post by demarshall on 2008-03-09
I just got an AFT-ZPO, a 6 in 1 Portable Flash Card Reader, and am trying to get it mounted to read flash cards for me. I tried following the tutorial but got lost part way through. Is it difficult to get a device like this mounted so that I can read flash cards?

I'm running Gutsy.

Thanks

---

### Post by demarshall on 2008-03-10
More information on the device - it's from Atech Flash Technology Inc.

Also, it appears attached to one of my USB 2 ports. I don't know how to access it though. That information came from the Device Manager.

---

### Post by ridgeland on 2008-03-11
Hi demarshall,

Sounds like you're just trying to plug and play.  You should not need to edit udev rules for that.  Did simple tests work?
Can you insert a card in the reader then plug the reader in and it auto mount itself?
I always like to assume its a simple issue until I learn more.  If you just plug it in (with a card in it) there should be a new icon on the desktop that you can just double-click and nautilus opens it to show you the contents.  Does that work?

---

### Post by demarshall on 2008-03-13
It's working now. The only thing that I've done is that I've rebooted the computer a few times.

---

### Post by locoocol on 2008-03-19
Hi, first I will confess that i am a linux noob

Im having troubles with my EEEPC mod (Internal usb hub + 4gb datatraveler to act as a HD + bluetooth). 

On boot everything works like a charm, the usb mounts as /home as I've configured during the instalation. But when I return from a Suspend, the drive seems to return as a read-only device. I cannot write o create folders on my user Home folder. Please help me figuring out this, 

These are my Fstab, Mtab and the 01-ina.rule created to always mount the pendrive in the same position.

My FSTAB

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc124318-7b33-47e1-ab82-68c8cc6f982a /               ext3    noatime,defaults,errors=remount-ro 0       0
# /dev/sdc1
# UUID=5a32cf9c-a43c-4ef8-9c8d-08d866d15024 /home           ext3  noatime,defaults,errors=remount-ro        0       0
/dev/usf	/home           ext3    rw,users,auto,noatime        0       0

tmpfs     /var/log       tmpfs     defaults,noatime        0 0
tmpfs     /tmp              tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp       tmpfs     defaults,noatime        0 0
```
THE RULE (/etc/udev/rules.d/01-ina.rules):
```
# Rules to ensure USB storage devices have persistent names and are mounted
# at boot.

# USB FIXED
BUS=="usb", KERNEL=="sd*", SYSFS{serial}=="89900000000000000000007C", NAME="usf", OPTIONS+="last_rule", RUN+="/bin/mount /dev/usf"
```
THE MTAB:
```
/dev/sda1 / ext3 rw,noatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-12-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/usf /home ext3 rw,noatime 0 0
```

---

### Post by chosi on 2008-03-27
Hey, I was going to set up my usb stick like given in the tutorial but I seem to fail at one of the very first steps :/
I know where my USB stick is (/dev/sdc1) but udevinfo does NOT give me the needed information - I think.
Do I need it all in SYSFS{}-tags? 'Cause I'm not getting these.
Here's what udevinfo-output looks like:
[http://nopaste.biz/38639](http://nopaste.biz/38639)

EDIT:
This works:
```
ATTRS{model}=="Flexi-Drive EC2",ATTRS{vendor}=="Sharkoon",KERNEL=="sd?1",NAME="usbstick1"
```
When I add RUN+="/usr/local/bin/usbstick1.sh" it won't run the specified shellscript (it is executable, has a "shebang" and is supposed to copy a file from /home/chosenone to /media/usbstick1)

---

### Post by ludovicc on 2008-04-27
Hello,

I tried on Hardy the udev rules way of giving names to removable devices, but no matter what i tried it doesn't work.

However, simply labeling your drives (follow the excellent tutorial at [http://www.debuntu.org/device-partition-labeling]("http://www.debuntu.org/device-partition-labeling")) works.

A new drive with a label appears as /media/<drive label> when you mount it.

Then you can follow the method proposed by Tirebird in [post #20]("http://ph.ubuntuforums.com/showpost.php?p=1360006&postcount=20") of this thread if you need more control on the directory where the drive is mounted.

Hope this helps,
Ludovic

---

### Post by keithacole on 2008-05-06
i am trying to sync my Archos605 when i plug it in. here is the udev that i have created but still cannot seem to get working

Ubuntu 8.04, kernel 2.6.24-16-rt

here is my lsusb
```
lashmoove@UbuntuStudio:~$ lsusb
Bus 004 Device 008: ID 0e79:1312 Archos, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c513 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
```



here is my  /etc/udev/rules.d/85-my_rule.rules
```
ATTRS{idVendor}=="0e79", ATTRS{idProduct}=="1312", RUN+="/home/lashmoove/sync_archos"

```

and here is my sync_archos
```
#!/bin/bash
grsync -e Email
grsync -e Miro
grsync -e Pictures

```

better stuff here
```
 looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb4/4-5':
    KERNELS=="4-5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:412"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="493"
    ATTRS{idVendor}=="0e79"
    ATTRS{idProduct}=="1312"
    ATTRS{bcdDevice}=="0316"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="29"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="ARCHOS"
    ATTRS{product}=="a605"
    ATTRS{serial}=="NMP3BALPAS85"
```

according to this. my rule is running fine.
```
lashmoove@UbuntuStudio:~$ udevtest /devices/pci0000:00/0000:00:1d.7/usb4/4-5
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/025_logitechmouse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-udev-early.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-basic-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-kvm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libmtp7.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-libpisock9.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-virtualbox-ose.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-dmsetup.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-my_rule.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/etc/udev/rules.d/kino.rules' as rules file
import_uevent_var: import into environment: 'MAJOR=189'
import_uevent_var: import into environment: 'MINOR=390'
import_uevent_var: import into environment: 'DEVTYPE=usb_device'
import_uevent_var: import into environment: 'DRIVER=usb'
import_uevent_var: import into environment: 'DEVICE=/proc/bus/usb/004/007'
import_uevent_var: import into environment: 'PRODUCT=e79/1312/316'
import_uevent_var: import into environment: 'TYPE=0/0/0'
import_uevent_var: import into environment: 'BUSNUM=004'
import_uevent_var: import into environment: 'DEVNUM=007'
udevtest: looking at device '/devices/pci0000:00/0000:00:1d.7/usb4/4-5' from subsystem 'usb'
udev_rules_get_name: rule applied, '4-5' becomes 'bus/usb/004/007'
udev_db_get_device: found a symlink as db file
udev_device_event: device '/devices/pci0000:00/0000:00:1d.7/usb4/4-5' already in database, cleanup
udev_node_add: creating device node '/dev/bus/usb/004/007', major=189, minor=390, mode=0664, uid=0, gid=0
udevtest: run: 'bash /home/lashmoove/sync_archos'
udevtest: run: 'socket:/org/freedesktop/hal/udev_event'
udevtest: run: 'socket:/org/kernel/udev/monitor'

```

---

### Post by Manslen on 2008-06-14
Same trouble here, running Hardy as well and trying to sync my A604 and disk-on-key devices. udevtest expects nothing by greatness, but udev itself leaves me empty handed.

I also tried using Upstart, but it seems upstart won't generate an event for a new usb device - you'd have to emit an event using udev. :(

---

### Post by RockyRoads on 2008-06-16
This is just a quick post to say Thank You for this excellent guide!

I have a laptop and move around a lot and use various different USB harddrives, thanks to this guide my I'm no longer pulling my hair out and going mad tyring to sync or in some cases just easily access the drives.


Thanks a lot!!

---

### Post by Manslen on 2008-06-17
> **Manslen said:**
> Same trouble here, running Hardy as well and trying to sync my A604 and disk-on-key devices. udevtest expects nothing by greatness, but udev itself leaves me empty handed.

I also tried using Upstart, but it seems upstart won't generate an event for a new usb device - you'd have to emit an event using udev. :(

I made a newbie's mistake, and tried running my command without a full path qualifier. changing it to /bin/myscript solved the problem.

---

### Post by Manslen on 2008-06-22
For what it's worth, here is how I got my USB device to automatically be synchronized once I plug it in.

I am synchronizing my podcast library, located at /home/michael/POD.
First, I created a mount point:
```
sudo mkdir /media/A604
```

Next, I wrote a small script that attempts to mount the USB device and then run rsync to perform the synchronization.
```
sudo nano /usr/local/bin/sync-pmp
```

The content:
```

#!/bin/bash
/bin/mount -t auto /dev/$1 /media/A604
if [ $? == 0 ]
then
        rsync -rtuv home/michael/POD --delete /media/A604&
fi

```

don't forget to give it execute permissions.
```
chmod a+x /usr/local/bin/sync-archos
```

What the script does, is attempts to mount the USB device and if it succeeds it runs rsync. The mounting is done on an unknown device name ($1) since I cannot rely on a constant device name (I have several USB devices periodically connected).

For the udev rule, I followed the first post on this thread to get the device info. I was interested in the node in which the value of KERNEL was sdb (this is the parameter I want to pass over to my script).
```

  looking at device '/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{dev}=="8:16"
    ATTR{range}=="16"
    ATTR{removable}=="1"
    ATTR{size}=="58396275"
    ATTR{stat}=="      62      675     1019      304        0        0        0        0        0      188      304"
    ATTR{capability}=="13"

```

I was also interested in a parameter that would uniquely identify my Archos player. udev rules allow you to pick attributes from one parent of the node you are interested in, and I found one.
```

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-1':
    KERNELS=="2-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:131"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="453"
    ATTRS{idVendor}=="0e79"
    ATTRS{idProduct}=="130a"
    ATTRS{bcdDevice}=="0316"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="ARCHOS"
    ATTRS{product}=="a604wifi"
    ATTRS{serial}=="DFN59TCU1RNE"

```
The last two attributes are exactly what I need.

I then wrote the udev rule.
```

sudo nano /etc/udev/01-synchronize-pmp.rules

```

And the content:
```

SUBSYSTEM=="block", ACTION=="add", ATTRS{product}=="a604wifi", ATTRS{serial}=="DFN59TCU1RNE", ATTRS{removable}=="1", RUN+="/usr/local/bin/sync-archos %k1"

```

Test your settings by plugging in your USB device and then restarting udev.
```
sudo /etc/init.d/udev restart
```

This is my first linux hack/howto, so feel free to point out what I got wrong. :-)

---

### Post by Graham Stark on 2008-07-23
Just to say a big 'thank you' for this: that was very useful indeed.

Graham

---

### Post by Kevin F on 2008-08-30
I am attempting to use this guide to create a rule for a symbol barcode scanner. The scanner works perfectly in Linux, becoming a keyboard when it is plugged in... except that is not what I want. I would like the output to go to a file, or a serial port style device.
I have written a rule in a file named 09-symbol.rules:
```
ATTRS{idVendor}=="05e0", OPTIONS+="ignore_device"
```
I also tried
```
SYSFS{idVendor}=="05e0", OPTIONS+="ignore_device"
```
I then
```
sudo /etc/init.d/udev restart
```
I then disconnect and re-connect the device, which causes this output in /var/messages
```
Aug 30 02:39:36 inky kernel: [53458.705373] usb 4-1: new full speed USB device using uhci_hcd and address 8
Aug 30 02:39:37 inky kernel: [53458.911375] usb 4-1: configuration #1 chosen from 1 choice
Aug 30 02:39:37 inky kernel: [53458.922426] input: ?Symbol Technologies, Inc, 2002 Symbol Bar Code Scanner as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input20
Aug 30 02:39:37 inky kernel: [53458.949614] input,hidraw0: USB HID v1.10 Keyboard [?Symbol Technologies, Inc, 2002 Symbol Bar Code Scanner] on usb-0000:00:1d.3-1
```

I intentionally used the "ignore_device" rule, so I would know when I have the rule recognized, and then could work on what I want the rule to do, but as you can see, it is still set-up as an HID keyboard.

Thanks for your help !

---

### Post by areskz on 2008-10-30
Thank you for this guide.
I'm almost in business, I almost got to the point I'm heading to =) The only problem is when the KDE (I use Kubuntu 8.04) tries to mount new media (I am dealing with a 60 gb external drive), it fails because of lack or permissions.

Seems like current user have no permissions to mount this media via "**KDE Daemon**" (a popup thingy that you see when a new media was connected). Dolphin tells me: "**Permissions denied**".

[IMG]http://img146.imageshack.us/img146/7271/permissionsdenieddolphivs9.png[/IMG]

I've tried to set uid,gid,umask options in fstab, but, as I've read above, the environment's default volume manager overrides that options, and uses it's own way.
```
## external media
/dev/usbdevices/60gbext /media/60gbext  ntfs-3g locale=ru_RU.UTF-8,umask=000,uid=1000,gid=1000  0       0

```
Also tried to set write/read permissions in **10-local.rules**:
```
SUBSYSTEMS=="usb", ATTRS{product}=="USB 2.0  IDE DEVICE    ", KERNEL=="sd?1", NAME="60gbext", SYMLINK="usbdevices/60gbext", MODE="0666", GROUP="areskz"

```
Nothing helped =(

But everything works with```
sudo mount -a
```But I don't want to use sudo every time I need to mount a media.

Any thoughts?

---

### Post by ridgeland on 2008-10-30
Hi areskz,
I have camera card readers mounting fine.  I posted #33 back up a ways.
My first thought is simplify some more for the test.  Comment out the fstab line and the udev line and boot again.  What happens when you plug in the external drive then?  Does it mount and put an icon on the desktop?  Auto-mount OK? Then try with just the fstab line (no udev rule) and booting again.  

I use gnome not KDE.  Gnome normally just puts the new device on the desktop.

---

### Post by areskz on 2008-10-31
Hi ridgeland.
Thank you for your help.
Without a udev rule, or without a fstab line, or without them both everything is okay &#8212; device connects successfully and an icon appears on a desktop. But the trouble is that I **need** to set **locale=ru_RU.UTF-8** to be able to read russian filenames on that drive. Otherwise, if I won't set this option, I will be able to see only english filenames.

Only a *fstab line* doesn't make the sense just because the drive has different names every time it is connected.

Only a *udev line* is not a choice because I need to set the locale option, as I've said before.

Just now tried out playing with symlink chmod, but it didn't help.

---

### Post by ridgeland on 2008-10-31
I think the problem is fstab.  Forget udev until fstab works the way you want it.
I would test options other than:
locale=ru_RU.UTF-8,umask=000,uid=1000,gid=1000

My approach is always "baby steps"
try just
locale=ru_RU.UTF-8
and see if that gets the Russian file names even if it is read-only.

I think the "permission denied" is due to:
umask=000,uid=1000,gid=1000

---

### Post by DavidInNH on 2009-03-25
Hi all:

I have been trying to get a rule to work for an hidraw device but have been unable to do so. The rule is 

ATTRS{idVendor}=="xxxx", ATTRS{idProduct}="yyyy", MODE="0666"

(where of course XXXX and YYYY are real VID and PID of the device.)

When I plug the device into the USB port, two new entries appear in /dev:  /dev/hiddev2 and /dev/hidraw3 (the standard HID and raw HID interfaces). The standard HID's file (/dev/hiddev2) gets the 666 permissions (and when I had the group and user name to run under specified, got those as well) but the raw interface (/dev/hidraw3) does not get changed.

I've tried everything I could think of but can't get this to work. It is the hidraw interface that I need to let the user have access to and hence need the permissions set.

Any help would be appreciated.

Thanks, Dave

---

### Post by mbrush on 2009-09-14
Just following along with Ubuntu 9.04 when I noticed udevinfo was missing, or rather, renamed.  I didn't check all the other posts to see if there was a solution, but this worked for me (as root):

```

ln -s /sbin/udevadm /usr/bin/udevinfo

```

To make a link from the new/renamed program to where it used to be, or just call the new program/version directly:

```

udevadm info -a -p $(udevadm info -q path -n /dev/XXX)

```

I also had to do this, instead of 'udevstart', as mentioned in the guide:

```

sudo /etc/init.d/udev restart

```

I hope that saves someone some googling :)

EDIT:
Just finished the rest of the guide, works like a charm!  I now have my USB->Serial GPS receiver being attached to /dev/gps.  Thanks!

---

### Post by mattydee on 2009-09-27
Thank YOU very much! This was extremely helpful!

By the way, when I added a second entry to 10-local.rules, I didn't even have to restart udev. Just unplugged and replugged the device.

---

### Post by aggman on 2009-10-21
[SIZE=2]Reply for thread:
[http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673)

I was getting same errors with my [/SIZE]**[SIZE=2]ST3300601XSRK [/SIZE]**[SIZE=2]seagate [/SIZE][SIZE=2]esata external HDD, on [/SIZE][SIZE=2]gentoo [/SIZE][SIZE=2]linux with [/SIZE]kernel 2.6.28 and 2.6.30
I just added in /etc/conf.d/local.start

echo 1024 > /sys/block/sdb/queue/max_sectors_kb
echo 1 > /sys/class/scsi_disk/2:0:0:0/allow_restart
and now everything is back in order. !!!:guitar:[SIZE=2]
Thanks a lot !!!:)[/SIZE]:popcorn:
[SIZE=2]
[/SIZE]

---

### Post by kc8hr on 2009-12-26
Excellent job, Sutekh. I have been beating my head against the wall for a long time trying to figure out a solution to this problem. I have several USB devices that are recognized as drives, and trying to figure out which is mounted where is very annoying when a new mount point is written every time you insert the device.

You might remind everyone that a new udev rule file is required for each device.

Thanks!
Tim:guitar:

---

### Post by zaurus on 2010-03-03
Very useful guide, but unforunatly for me it covers mainly storage devices and yet USB attached. I have trouble with my DVB-cards both PCI and USB which change device number with every boot. How can i use this guide in this situation?
Would be also great to update the guide for current Ubuntu release, means new commands and make it more device generic.

KR

---

### Post by idman on 2010-06-03
> **zaurus said:**
> Very useful guide, but unforunatly for me it covers mainly storage devices and yet USB attached. I have trouble with my DVB-cards both PCI and USB which change device number with every boot. How can i use this guide in this situation?
Would be also great to update the guide for current Ubuntu release, means new commands and make it more device generic.

KR

You can use other match string, eg.:

```

root@server:~# cat /etc/udev/rules.d/10-local.rules
# Mount hdd backup as /dev/sda
SUBSYSTEMS=="usb",ATTRS{manufacturer}=="Western Digital ",**ATTRS{serial}=="574341553434313231343834"**,KERNEL=="sda",SYMLINK+="sda%n"
root@server:~#

```Serial is unique.

---

### Post by hun.gergov on 2010-07-05
Hi!

I've been using something similar on my old 7.04 installation to name fixed SATA hard disks.
Today I finally decided to upgrade my system to lucid, but my udev rule file does not work anymore. The partitions on the disks get mounted "randomly" to one of the mount points described in fstab.

I think the problem is that mountall and udev runs concurrently. (mountall runs in daemon mode, so udev starts before mountall is actually done with all of its work) While mountall is still mounting the file systems from the fstab files, udev renames the device nodes and everything gets messed up.

I use a file in /etc/udev/rules.d named 10-local.rules with the following content:

SUBSYSTEM=="block", SUBSYSTEMS=="scsi", ATTRS{model}=="SAMSUNG SP2514N ", NAME="sda%n"
SUBSYSTEM=="block", SUBSYSTEMS=="scsi", ATTRS{model}=="SAMSUNG HD103UJ ", NAME="sdb%n"
SUBSYSTEM=="block", SUBSYSTEMS=="scsi", ATTRS{model}=="Hitachi HDS72202", NAME="sdc%n"

I've already tried to modify some .conf files in /etc/init, tried to mount /proc and run udev before mountall starts, run mountall normally instead of daemon mode but nothing helped.

I hope somebody can help me. Thanks!

---

### Post by ridgeland on 2010-07-05
Just a quick comment, see this:
[https://bugs.launchpad.net/ubuntu/+bug/569645](https://bugs.launchpad.net/ubuntu/+bug/569645)
It shows my work-arounds.

---

### Post by ridgeland on 2010-07-31
More upgrade papercuts.
udev rules worked fine for me with Ubuntu 9.04.  I had an entry in /etc/fstab for the devices I mount on the usb.  I had rules.d with simple one liners to mount the USB device to it's own directory with mode=777 so it was shared as soon as I copied it across.
Ubuntu 10.04 ended that.
Now if I put the mount point in /etc/fstab and boot without having the camera card connected I get a stop and wait message that the card was not found, hit a key to continue the boot.  When I connect it later it has mode=644, others cannot edit the photos.
The rules.d rules from before don't work at all, they are ignored.
So here is the work around I have now.
I used "Mount under /media; use partition label if present"
from:
[Udev ArchWiki]("http://wiki.archlinux.org/index.php/Udev")
Changing umask to 000, this mounts the device with mode=777 so when I copy it to /Data/Images/somewhere others on the NFS can edit the photos (my spouse :) )  Problem is only root can unmount it!  ArchWiki's pmount did not work for me.
So to unmount it I added an application launcher to my panel that is just "sudo umount /dev/sdc1".  I'm only using one USB card reader at a time so it always gets sdc1 here.
From a user (me) point of view the only difference is that now to unmount I click on the panel and enter my sudo password rather than the old way of right-click and unmount.
It works but...
Anyone got a better solution?

---

### Post by extraordinary_boy08 on 2011-01-12
[http://ubuntuforums.org/showthread.php?t=1665278](http://ubuntuforums.org/showthread.php?t=1665278)

Please do help me with this problem. Thank you very much.

---

### Post by repsol05 on 2011-05-11
Hey I have been having problems for a year with /dev/sdb vs /dev/sdc on reboots. I have filled my disk because my mounted drive had the wrong name. I created different fstabs and created a script that looked for what sd? it mounted as then would overwrite the fstab. It was a stupid solution and worked about half the time. I ran across your tut and it worked. The cool thing is I am on a CENTOS box and your tut worked perfectly except the restarting udev. I googled how to restart it on contos and it worked perfectly. 

I wish I would have found this a year ago. You solved my issue completely so,


THANK YOU!!!!!

---

### Post by donniezazen on 2011-06-22
> udevadm info -a -p $(udevadm info -q path -n /dev/sdb1)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb1':
    KERNEL=="sdb1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{partition}=="1"
    ATTR{start}=="63"
    ATTR{size}=="2930277104"
    ATTR{ro}=="0"
    ATTR{alignment_offset}=="0"
    ATTR{discard_alignment}=="4294935040"
    ATTR{stat}=="      47        4      408      516        0        0        0        0        0      516      516"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host2/target2:0:0/2:0:0:0/block/sdb':
    KERNELS=="sdb"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{range}=="16"
    ATTRS{ext_range}=="256"
    ATTRS{removable}=="0"
    ATTRS{ro}=="0"
    ATTRS{size}=="2930277168"
    ATTRS{alignment_offset}=="0"
    ATTRS{discard_alignment}=="0"
    ATTRS{capability}=="50"
    ATTRS{stat}=="      62       30      736     7512        0        0        0        0        0     7512     7512"
    ATTRS{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host2/target2:0:0/2:0:0:0':
    KERNELS=="2:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="WD      "
    ATTRS{model}=="15EADS External "
    ATTRS{rev}=="1.75"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x6a"
    ATTRS{iodone_cnt}=="0x6a"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host2/target2:0:0':
    KERNELS=="target2:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/host2':
    KERNELS=="host2"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0':
    KERNELS=="1-5:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-5':
    KERNELS=="1-5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{urbnum}=="326"
    ATTRS{idVendor}=="1058"
    ATTRS{idProduct}=="1003"
    ATTRS{bcdDevice}=="0175"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="5"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Western Digital "
    ATTRS{product}=="External HDD    "
    ATTRS{serial}=="57442D574341565530323937323835"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="36"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.38-8-generic-pae ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x27cc"
    ATTRS{subsystem_vendor}=="0x1028"
    ATTRS{subsystem_device}=="0x01bd"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


How do i use this information?

---

### Post by donniezazen on 2011-07-10
I was able to get this working but then it started unmounting itself and would not mount by sudo mount -a. Any help?

---

### Post by wesblake on 2011-08-24
Im having similar issues to these later posts. It would seem, Natty (11.04) or does not even listen to rules?
My rule file is 9-probox.rules (VirtualBox already has a 10- rules file in there)
Here's the content, should work, no?
SUBSYSTEM=="block", SUBSYSTEMS=="scsi", ATTRS{model}=="HD204UI", MODE="0755"
But my drives (there are 2 matching this rule, external usb hard drives) still mount as 700 permissions!
Anyone know why? I'm trying to add media from them to Plex Media Server, and it can not see inside them I'm assuming due to the permissions they mount with.
Thanks!

---

### Post by bloco on 2011-12-03
How about a rules for ignoring a device, I came up with

ATTRS{model}=="TOSHIBA 674338", OPTIONS="ignore_device"

but this didn't work.

Any ideas how to prevent disk of the format /dev/sda from being detected,
i.e. to not create /dev/sda /dev/sdaX and all the symlinks in /dev/disk?

Using ubuntu 11.04

---

### Post by shreepads on 2012-09-06
At least for USB drives can't this be done easier by using UUIDs?

I'll try and post results...

---

### Post by shreepads on 2012-09-06
> **shreepads said:**
> At least for USB drives can't this be done easier by using UUIDs?

I'll try and post results...

Yup, works fine...

1. Run in the terminal
```
sudo blkid
```

2. Connect the USB drive and let it automount.

3. Run in the terminal
```
sudo blkid
```

4. Note the UUID(s) of the new partition(s) listed, which would be the one(s) on the USB drive.

5. Create a suitable mount point(s)
```
cd /media
sudo mkdir SS4GB1
sudo chgrp plugdev SS4GB1
```

6. Edit fstab and add an entry like so (tweak any settings you like)
```
UUID=<insert UUID from above without quotes>                                 /media/SS4GB1    vfat   auto,noexec,rw,users,nodev,nosuid,noatime,flush     0        2

```

Now you can leave it plugged in at boot, 'Remove Safely', plug it back in while running, remove as another user etc etc and it is always on /media/SS4GB1 (err.. except when it is ejected of course! :lolflag:)

---

### Post by mattydee on 2012-09-09
Yep, UUIDs would be much cleaner I think.

---

### Post by shreepads on 2012-09-10
> **mattydee said:**
> Yep, UUIDs would be much cleaner I think.

Only one problem, it holds up the boot sequence if the USB stick isn't plugged in and you need to hit 'S' to skip trying to mount it.

I guess that can be fixed by adding "nofail" to the fstab mount options...

---

### Post by mattydee on 2012-09-12
> **shreepads said:**
> Only one problem, it holds up the boot sequence if the USB stick isn't plugged in and you need to hit 'S' to skip trying to mount it.

I guess that can be fixed by adding "nofail" to the fstab mount options...

Good point. Wouldn't you have the same problem using udev rules anyway? The system would try to mount the same (disconnected) USB device at boot from the udev created device node (EDIT: except in this case it wouldn't be created so the system would try to mount from a device node that doesn't exist), so you'd still need the nofail option. Unless I'm missing something.

---

### Post by shreepads on 2012-09-12
> **mattydee said:**
> Good point. Wouldn't you have the same problem using udev rules anyway? The system would try to mount the same (disconnected) USB device at boot from the udev created device node (EDIT: except in this case it wouldn't be created so the system would try to mount from a device node that doesn't exist), so you'd still need the nofail option. Unless I'm missing something.

Yup, makes sense... But I won't be trying it out using udev, far too complicated!

---

### Post by Nattereri on 2012-09-20
[SIZE=3][FONT=Calibri]After many hours of reading and experimenting I have come to an acceptable solution for mounting my external USB hard drive. I am posting it here in the hopes it will help others.[/FONT][/SIZE][FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Some background: I am running Ubuntu 10.04.4 Server and therefore have no GUI installed nor do I want one. This is the reasoning behind getting UDEV to work for me. I have an external USB hard drive in an enclosure that is going to store cloned images of the workstations in my network. I wanted to produce a UDEV rule that would at least mount the USB drive for me as I am a former Windows user and tend to be lazy.[/FONT][/SIZE][FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]My solution had to overcome some difficulties. First I could not run the mount command from within the UDEV rule so I had to use a script. Second the script has to be run with root privileges.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT][SIZE=3][FONT=Calibri]I created a UDEV rule as follows[/FONT][/SIZE]
```
 
 SUBSYSTEM=="usb", ATTR{serial}=="###########", ACTION=="add", WAIT_FOR="/dev/sdx1", RUN+="/usr/bin/sudo /home/user/udev_mount_MyDrive.sh"

```
[SIZE=3][FONT=Calibri]The WAIT_FOR  key was needed because the mount script would simple silently fail. I believe this is related to something I read about UDEV terminating processes.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]The script file is a simple mount command such as:[/FONT][/SIZE]
```
 
mount /dev/sdx1 /my/mount/dir

```
[SIZE=3][FONT=Calibri]To execute the script without entering a password I added the user to the sudoers file for this mount script. I changed the permission on the mount script so root has rwx and others have no permissions. This has worked for me but I do have a concern. From what I've been able to decipher from the Ubuntu teams scripts they use the serial id to create the drive letter and thus this should keep working correctly. I could be wrong on that as I have only had time to examine a few UDEV rules.[/FONT][/SIZE]

---

### Post by mattydee on 2012-09-23
Nattereri:

You shouldn't be writing a script to mount that drive. You can use udev rules if you want, but as shreepads and I discussed, using UUIDs is probably a cleaner option. 

If you use UUID, the only thing you have to modify is /etc/fstab. For example, you would add the entry: 
```

UUID=DE8A05A28A057873    /home-files     ntfs-3g nofail,uid=1000,gid=1001,fmask=113,dmask=002   0       0
```

replacing the UUID with the one from your drive of course. To find out the UUID of your drive, use the command blkid. In this example, I set the permissions using the uid,gid, fmask and dmask options because it's an NTFS drive, but your situation my differ. The important option here is the nofail one, as discussed above. Refer to man fstab for more info. 

Not sure if I'm missing something, but again: you really shouldn't be writing scripts and adding users to sudo to mount drives when you can use /etc/fstab.

EDIT: I guess what I missed was the fact that you want the drive to mount automagically after plugging it in, correct?

---

### Post by Nattereri on 2012-09-24
mattydee:
Yes I want it to automagically mount after pluggin it in. I did not read about fstab and maybe I should investigate it. I knew about the drives failing on boot and that is why I went with the udev route. But maybe I could use a combination of the two to eliminate the root mounting problem and just execute mount -a. A more elegant solution and less files laying around to secure.

---

### Post by mattydee on 2012-09-30
> **Nattereri said:**
> mattydee:
Yes I want it to automagically mount after pluggin it in. I did not read about fstab and maybe I should investigate it. I knew about the drives failing on boot and that is why I went with the udev route. But maybe I could use a combination of the two to eliminate the root mounting problem and just execute mount -a. A more elegant solution and less files laying around to secure.

You could probably use a combination of the udev rules that detect and then execute the mount command, based on the UUID. Then in your fstab, you would have the proper entry for that device with an option like "user" which allows users to mount that particular device. I would stay away from a mount -a (mount all)command, since that could very well lead to unforeseen problems!!!

EDIT: 
So an overview
1. your fstab would have an entry of the form 
```
UUID=1234  /folder/mydevice  ntfs-3g  nofail,user,{other options} 0  0
```
2. You would have udev rules that detects a device that has UUID 1234 being plugged in to execute "mount /folder/mydevice"

EDIT2: 
You might not even have to use the UUID in your udev rule. Only in the fstab

---

### Post by goodvibes on 2013-01-11
Hi Shreepads,
 
In Ubuntu 12.04.01 LTS you can use the nobootwait (instead of nofail) option in /etc/fstab to stop the 'S to skip' message when the USB drive is not connected while booting.

---

### Post by malc659 on 2013-06-11
Your post is good and top of my Google "ubuntu udev rules" search, but I think that:

**BUS** is now deprecated, we're supposed to use "**SUBSYSTEM**" instead.
**SYSFS** is deprecated, we're supposed to use "**ATTR**" now (probably means "attribute").

See: [https://bugs.launchpad.net/ubuntu/+source/gpsd/+bug/512464](https://bugs.launchpad.net/ubuntu/+source/gpsd/+bug/512464)

Maybe someone else can be bothered to post exactly when (version) the old keywords won't work.

---

### Post by coffeecat on 2013-06-12
Indeed. This tutorial has long been obsolete.

*Moved to **Outdated Tutorials & Tips***

---

