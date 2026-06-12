---
title: "Instalation problem"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Jalim on 2008-06-08
Well finally I decided to leave Windows. After some reading and tries I think Ubuntu is more suitable for me.

But...

I had 2 hard disks, one small, quite old 60 Gb that is used for general storage and a bigger HD (160 Gb) partitioned in 2, a primary partition were i used to have the WIN XP pro system files and a logical partition for general use.

Using a liveCD I installed the Ubuntu 8.04. The guided installation just give me the option to install ubuntu in the logical partition. As I want to keep the logical partition as it is what I did is reduce the windows partition and use the installer option to use the new free space.

Installation goes fine but at restart no signal of ubuntu. I was expecting a menu to give me chance to choose XP or ubuntu but the machine goes directly to XP as usual.

As I want to remove windows from this computer, using the Gparted (included in the liveCD) I deleted the windows partition and the ubuntu partition that was in there. Then in the new free space I manually make a new primary partition with ext3 format to install Ubuntu and also make the Swap space. After that I install the Ubuntu there using the manual option. Installation went OK.
At restart I get the message "No Operative System Found". But Using the Live CD I can go to the Ubuntu installed in the hard disk.
What I could do to boot directly from the HD?

Thanks

---

### Post by Happy_Man on 2008-06-08
Hm, it would seem that your Ubuntu drive is not being picked up as the master by your BIOS. Go into your BIOS settings and change that, and then it should work fine.

---

### Post by Jalim on 2008-06-08
Well, it seems a strange problem to me too. I forgot to mention that, but I already did that, the BIOS is set to boot from that HD. 

Cheking the partitions with the Gparted i noticed that none of the partitions have any flags. I flagged the Ubuntu pratition as Boot (There is another optios but I do not know what they mean), but that did not work either.

How do you set the Master Boot Partition?

---

### Post by RequinB4 on 2008-06-08
Probably GRUB didn't get install correctly (it's the bootloader that changes the mbr to say which PARTITION of the drive to boot from) when you installed.

Go on the livecd

```

sudo grub
find /boot/grub/stage1

```

assuming the output of the last command is hd(0,2) or w/e (use whatever you get as output)

```

root (hd0,2)            # Comma, not period
setup (hd0)

```

Reference: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by Jalim on 2008-06-08
Many Thank for your answers...

RequinB4 suggestion Done... 

______________________________________________________________________
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.
________________________________________________________

Result:  No luck...

I get  "Missing Oparetive System" ...  I'm still on the CDLive  

Should I try the solution that is in your reference (RequinB4)?

---

### Post by RequinB4 on 2008-06-08
since you got (hd1,0) you need to use hd1 instead of hd0 on the last step :)

SIDE NOTE:  The only important part of my reference is using the following if you want to install grub on your linux partition and NOT your MBR (Which, to the best of my understanding, is not what you want to do, since your BIOS can't specify which parition to boot to):
> 
Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.


---

### Post by Jalim on 2008-06-08
Ok, some progress...

grub started but the only thing i get is "Error 17: Cannot mount selected partition" pressing any key goes to a menu with three Ubuntu vertions (normal, recovery mode and other) but choosing any get back to the error 17 and get cycled there...

(I can get into the Ubuntu installed in the HD through the Live CD option "boot from primary HD")
What's missing?

---

### Post by RequinB4 on 2008-06-08
In your /boot/grub/menu.lst :

Where it says the root for linux, change it to root (hd1,0).

So it should say something like :
> 
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=SEQUENCEOFLETTERSANDNUMBERS BOOTOPTION1 BOOTOPTION2
initrd		/boot/initrd.img-2.6.24-18-generic
quiet


Change the second line to "root		(hd1,0)"

You'll have to do this for any other kernels you have stored

---

### Post by Jalim on 2008-06-08
The menu.lst file seems ok

look:
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9dc139af-fd45-4dbd-8367-9f4852af1096 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9dc139af-fd45-4dbd-8367-9f4852af1096 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

Another option? 

by the way you say:

> **RequinB4 said:**
> 

You'll have to do this for any other kernels you have stored

kernel? what do you mean (is it similar to users?) (Sorry, I'm newbie and I'm not used to the terms)

---

### Post by Happy_Man on 2008-06-08
The menu options, eg the stuff that looks like ```
Ubuntu Hardy 8.04 2.6.24-16 generic
```. 

A kernel is basically the core of any OS. It is what everything else is based upon and relies on. Very very important stuff.

---

