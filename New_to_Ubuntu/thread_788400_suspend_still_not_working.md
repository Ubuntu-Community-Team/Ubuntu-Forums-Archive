---
title: "suspend still not working"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Adahn on 2008-05-09
Using Hardy with current kernel, x.17
I've tried the canned ATI drivers and proprietary via Envy as well as tweaks here:
[http://www.lunders-and.no/wp/?p=99](http://www.lunders-and.no/wp/?p=99)

When trying to suspend, screen goes dark (but not off) with a blinking cursor in the upper left corner.  PC fans continue to run.  Only a hard reset restarts the PC.  S3 is on in bios.


suspend log below:

tony@tony-desktop:~$ cat /var/log/pm-suspend.log
Fri May  9 08:41:31 EDT 2008: running suspend hooks.
===== Fri May  9 08:41:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Fri May  9 08:41:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Fri May  9 08:41:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Fri May  9 08:41:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Fri May  9 08:41:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Fri May  9 08:41:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Fri May  9 08:41:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Fri May  9 08:41:33 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Fri May  9 08:41:33 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Fri May  9 08:41:33 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Fri May  9 08:41:33 EDT 2008: done running suspend hooks.
tony@tony-desktop:~$

---

### Post by betterthanjordan79 on 2008-05-09
exact same thing happens to me and also in hibernate!!!

---

### Post by dublued on 2008-05-09
did you create a swap partition when you first installed ubuntu?

i had similar poblems due to no swap

---

### Post by Adahn on 2008-05-09
> **dublued said:**
> did you create a swap partition when you first installed ubuntu?

i had similar poblems due to no swap

Yes, as far as I know, but I plan to confirm by booting into the live cd.
Any way to check while running?

---

### Post by kamitsukai on 2008-05-09
i have this problem as well :( although its no big suprise as i have never managed to get either suspend or hibernate to work on ubuntu...

---

### Post by dublued on 2008-05-09
yea you can check it without rebooting.

just install gparted

go into terminal and type the following

```
sudo apt-get install gparted
```
to run it... go into terminal and type...

```
gksudo gparted
```

you will be able to see all of your hard drives and their partitions.

---

### Post by Adahn on 2008-05-10
current swap is 1.29GB.
I have 2GB of system ram.  Should I resize?

---

### Post by dublued on 2008-05-10
i've heard two things from reading on here.

1)  Swap should always be double your ram.

2)  Swap should always be double your ram if you have less than 1 gig of ram... otherwise, swap should be the same as your ram.

did you size the swap partition yourself or did you let ubuntu installation take care of it?  i let ubuntu take care of the all the partitions and it gave me a swap partition of 2.8 GB ( i have 1 gig ram)

so try doubling your swap partition if you have the space... atleast get it to be the same as your ram.

goodluck

---

### Post by glennric on 2008-05-10
Your swap partition size won't matter if you are using S3 suspend.  Swap is only needed for hibernation.  

A quick and easy way to check your swap size and see if it is even being used is to type "free" in a terminal.  Type "sudo fisk -l" or use gparted to see if you have a swap partition.  In some cases you have a swap partition, but it is not being used.  This is usually due to your fstab not pointing to the correct place.

Have you also checked your bios for other ACPI options.  For instance what method do you have set for your monitor to be turned off?  Is it DMPS Off or some other method?

---

### Post by Adahn on 2008-05-14
swap file isn't even being used.

all the bios options are as they should be.   suspend/hibernate work fine on the winxp install on the same drive.

---

### Post by Adahn on 2008-06-08
picking up an old thread of mine:

Even though I wasn't even though I wasn't tapping into my swap file (and it has been active) I increased its size with gparted.

suspend/hibernate haven't been affected.

Neither have worked since Edgy IIRC, and that was when I had an Nvidia card (ATI now).  I recall that one updgrade broke suspend even for the nvidia card.

---

### Post by drs305 on 2008-06-08
> **Adahn said:**
> swap file isn't even being used.

all the bios options are as they should be.   suspend/hibernate work fine on the winxp install on the same drive.

If you see 0 in the swap usage after running **free** please check this - it may be the reason suspend isn't working:

Run the following commands:
```
sudo blkid
cat /etc/fstab | grep swap
```

See if the uuid's are the same. If they are not, change the fstab swap entry to match the **blkid** swap uuid. 

Sometimes uuid's get changed. If the swap uuid was changed, you might never notice that you don't actually have a usable swap partition (except for suspend issues, etc ;-) ). 

After making the changes, reboot and you will probably see numbers in the swap portion after running the **free** command again.

If you find that this had happened to you, please post back and I'll make a thread about it.

---

### Post by Adahn on 2008-06-08
/dev/sda1: TYPE="ntfs" UUID="BC24242F2423EB5A" 
/dev/sda3: UUID="245b4d9f-28d4-4391-a599-eff3147a6579" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="e970da9a-2d40-4bf1-83e1-3c0b69d35196" 
tony@tony-desktop:~$ cat /etc/fstab | grep swap
UUID=b0ea824a-0382-417b-97ea-cf86f2663537 none swap sw 0 0


yes the UIDs are different.

---

### Post by drs305 on 2008-06-08
> **Adahn said:**
> /dev/sda1: TYPE="ntfs" UUID="BC24242F2423EB5A" 
/dev/sda3: UUID="245b4d9f-28d4-4391-a599-eff3147a6579" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="e970da9a-2d40-4bf1-83e1-3c0b69d35196" 
tony@tony-desktop:~$ cat /etc/fstab | grep swap
UUID=b0ea824a-0382-417b-97ea-cf86f2663537 none swap sw 0 0

Your swap partition is not correctly identified in fstab. You need to change the following fstab entry from the one in normal type to the one in bold. This assumes the first line of the post was the result of the blkid command.

```

/dev/sda5: TYPE="swap" UUID="b0ea824a-0382-417b-97ea-cf86f2663537  none swap sw 0 0" 
**/dev/sda5: TYPE="swap" UUID="e970da9a-2d40-4bf1-83e1-3c0b69d35196  none swap sw 0 0" **

```

Do you know how to make the changes? If not I will tell you.
After the changes are made, please reboot, then try suspend, and let us know if it now works for you.

---

### Post by Adahn on 2008-06-08
> **drs305 said:**
> 

Do you know how to make the changes? If not I will tell you.


No.  Please, thank you!

---

### Post by drs305 on 2008-06-08
> **Adahn said:**
> No.  Please, thank you!

Okay, first, we will make a backup and then edit fstab:
```

sudo cp /etc/fstab /etc/fstab.bak1
gksudo gedit /etc/fstab

```

Find the line (the line above it will look something like "# Entry for /dev/sda5":
```
UUID=b0ea824a-0382-417b-97ea-cf86f2663537 none swap sw 0 0
```
and replace it with:
```

/dev/sda5: TYPE="swap" UUID="e970da9a-2d40-4bf1-83e1-3c0b69d35196  none swap sw 0 0" 
```

Save the file. Reboot to enable the swap file/partition. Then try suspend and see if it now works. Let us know.  Even if suspend still doesn't work, at least you now have a usable swap partition. ;-)

---

### Post by cprofitt on 2008-06-08
There is a 'big' in the -17 and -18 kernels.

[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/226279)

not sure if you want to wait for the fix in -19 or continue to troubleshoot.

---

### Post by Adahn on 2008-06-08
> **PrivateVoid said:**
> /url]

not sure if you want to wait for the fix in -19 or continue to troubleshoot.

I'm already using -19. I've had this issue for much longer than -17



I made those fstab changes.
'free' lists swap as 0 0 0

edit: turned swapon in gparted.
now:

             total       used       free     shared    buffers     cached
Mem:       2063268     992492    1070776          0      18164     508592
-/+ buffers/cache:     465736    1597532
Swap:      3686876          0    3686876


time to test suspend.

---

### Post by Adahn on 2008-06-08
Nope.   Suspend and hibernate both result in same black screen with blinking cursor (top left).
Perhaps I should try the open source ATI drivers again.  They didn't work before the swapfile fix.

Thanks for helping me fix the swap file anyway.

---

### Post by cprofitt on 2008-06-08
> **Adahn said:**
> I'm already using -19. I've had this issue for much longer than -17

Cool. I had not seen it released yet so made an assumption you were not using it.

---

### Post by markbuntu on 2008-06-08
This is a known problem with the ATI driver. the misrecognition of swap has been fixed but there is another problem with atieventsd. It has been fixed for kbuntu in the -19 kernel release and a general fix is expected soon so please be patient.

---

### Post by Adahn on 2008-06-12
> **markbuntu said:**
> It has been fixed for kbuntu in the -19 kernel release and a general fix is expected soon so please be patient.

Great news.  Will the fix be in the next kernel or in the driver?

---

