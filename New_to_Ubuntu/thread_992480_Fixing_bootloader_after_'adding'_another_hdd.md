---
title: "Fixing bootloader after 'adding' another hdd"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by ash_nug on 2008-11-24
Hi i just installed ubuntu 8.10.
Out of fear of erasing the wrong HDD, I unplugged the "ide channel 3 master" (sata xp drive) as well as the "ide channel 1 slave" (ide data drive) and installed onto the "ide channel 4 master" (sata ubunto drive). After I finished the install, Ubuntu booted fine, so i plugged in the other two drives again (xp drive and data drive).
However, now whenever I start the computer up with all three drives enabled, ubuntu doesnt make it into the GUI and gives me a command line containing this error message:

ALERT! /dev/disk/by-uuid/ <bunch of numbers.....> does not exist. Dropping to a shell!

How do I point the bootloader in the right direction of the ubuntu partition?

Clearly im trying to create a dual boot computer with XP on one HDD and Ubuntu on the other, so it would be nice if I could configure the option of booting into windows from Ubuntu's bootloader as well (at the moment I have to change the hdd boot order in the bios in order to select which operating system/hdd to boot from).

Sorry for being such a nube :P

Ash.

---

### Post by ndefontenay on 2008-11-24
Hi.

I was doing that before and the only way I found was to have both plugged when installing.

At installation just have to make sure which one is the right hard disk but they have different sizes anyway...

I know it's not what you would like to hear x)

It's likely too that since your windows HDD wasn't plugged, the boot loader didn't recognize your windows OS and didn't incude the required lines.

I've completely removed windows recently and was trying to find out how to get rid of the windows line at all from grub.

Somebody gave me this:

[http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

Your answer might be in there.

Good luck

Nico

---

### Post by ash_nug on 2008-11-24
Actually once before i installed ubuntu on this 'second' hdd with the windows one still plugged in. grub installed itself onto BOTH hdd and i had to reinstall the bootloader on the windows drive... wasnt very fun at all.
Niether operating system booted when i did this. It seems ubuntu just likes being on the first hdd for some reason.
Im going to try to keep getting it working my way, but thanks for your reply :)

---

### Post by caljohnsmith on 2008-11-24
Did you change any of your BIOS settings related to your Ubuntu SATA drive when you connected your other drives? How about rebooting, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and then add "rootdelay=130" at the end similar to:
```
kernel	/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Red"]rootdelay=130[/COLOR]
```
After adding the rootdelay to the kernel line, press return to save the change, and finally "b" to boot. Let me know if that gets you any further, or if you get the same error. :)

---

### Post by Olivier2371 on 2008-11-24
1rst make sure both hdd are in.
2nd  make that the windows drive is in first, then put the second hdd.
3rd when you are installing unbuntu you should have the choice between SDA or SDB(sda should be windows and sdb should be ubuntu)
4th put the boot loader on sda (grub). It will detect windows and add it to grub.

---

### Post by egalvan on 2008-11-24
> **ash_nug said:**
>  It seems ubuntu just likes being on the first hdd for some reason.
**Im going to try to keep getting it working my way**, but thanks for your reply :)

No, Ubuntu does not care what drive it is on.

I have had it installed on the first, second and third physical drives. It works.

GRUB defaults to installing its first stage on the boot drive, and its second stage goes on the Linux partition.

But you can also intall GRUB into its own dedicated partition. 

See Hermans web site for more info.


And I agree, keep at it until it does what YOU want, not what the machine wants!

ErnestG

---

### Post by ash_nug on 2008-11-24
> **caljohnsmith said:**
> Did you change any of your BIOS settings related to your Ubuntu SATA drive when you connected your other drives? How about rebooting, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the "kernel" line, press "e" to edit it, and then add "rootdelay=130" at the end similar to:
```
kernel	/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Red"]rootdelay=130[/COLOR]
```
After adding the rootdelay to the kernel line, press return to save the change, and finally "b" to boot. Let me know if that gets you any further, or if you get the same error. :)

In order to get either windows or ubunto to boot, i set which drive i want in the bios. For example, atm i have the ubunto drive set to boot from first.

Oh wow it worked, i added that line and away she goes. 

However when i restart the computer the line i added seems to dissapear and the problem returns.
Now i just need to make this line permanent and also add another line so i have the option of booting into windows without having to alter the bios settings.

Thanks for your reply btw :)

---

### Post by caljohnsmith on 2008-11-24
That's great news it worked; I forgot to mention that editing your Grub menu entries on start up is only temporary, so to make the change permanent, open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then you can add the "rootdelay=130" to all the Ubuntu kernel lines in the menu.lst. Also, to boot Windows, add the following entries to the end of the menu.lst:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
One of those entries should work to boot Windows, but if not, then please post the output of:
```
sudo fdisk -lu
```
And we can work from there. :)

---

### Post by ash_nug on 2008-11-24
> **caljohnsmith said:**
> That's great news it worked; I forgot to mention that editing your Grub menu entries on start up is only temporary, s....
And we can work from there. :)

Oh wow, Ubuntu boots perfectly and so does windows. Your suggestion was spot on and now my computer is doing exactly what i want it to do.

Thankyou so much for your help caljohnsmith!

---

### Post by caljohnsmith on 2008-11-25
You're certainly welcome, and I'm glad both Windows and Ubuntu boot OK now. Cheers and have fun with your OSes. :)

---

### Post by theozzlives on 2008-11-25
I don't understand how you booted Ubuntu in the first place if sda was unplugged during install???

---

### Post by ash_nug on 2008-11-25
> **theozzlives said:**
> I don't understand how you booted Ubuntu in the first place if sda was unplugged during install???

Sorry im not up to date on linux speak and im not sure what SDA means. But basically i have XP installed on one hard drive, and Ubuntu installed on another.

If i want to boot ubuntu, i would select this hdd as boot priority in bios. Vice versa with XP. Both drives would be plugged in at this point. I simply installed Ubuntu initially with only one HDD plugged in.

Of course now i can dual boot so i dont need to go into the bios anymore....

---

### Post by Olivier2371 on 2008-11-25
That's a mistake. Never unplugged your HDD when you install a second OS for dual boot. If originally you had windows xp on the first drive(sda), and wanted to install ubuntu on the second drive all you had to do is during the installation choose the option to install Ubuntu on the second HDD(sdb),
and have grub installed on the first drive(sda).

---

### Post by ash_nug on 2009-01-03
I know. This has caused problems for me in the past. If grub installs itself on my windows partition the system becomes unbootable without manually editing grub, and to do that id have to get some kind forum member to basically do it for me, as im a total nube.
The easier solution was to simply unplug the windows drive, to make sure that ubuntu didnt do anything to **** it up whilst installing on another drive. This seems to have worked for me, and with the addition of the "root delay" thingy, now they both boot up fine.
What i cant figure out is why this works lol!

---

### Post by ash_nug on 2009-01-03
That said, the problem with the "rootdelay=130" thingy is that ubuntu takes FOREVER to boot up. I might start looking for another solution as its getting a little annoying to be honest. I think ill need to understand exactly how this works first though :S

---

### Post by ash_nug on 2009-01-04
After doing a little reading i see that the most likly reason the rootdelay option works is because my hard drives dont MOUNT in time. Other users seem have have a delay of just 10 for a USB drive, where i have a full 130 for an internal. I might try adjusting the numbers till i get a sufficiently fast bootup time with reliable results.

---

### Post by Medraq on 2009-01-04
Thanks for that info CalJohnSmith  :)

I just installed Ibex Server on a system with 2 SCSI HDD's and received the same error as Ash_nug.  Adding "rootdelay=130" to the 'kernel' lines in  /boot/grub/menu.lst  solved the problem    :)

Now on to why my second NIC wasn't found .... :confused:

---

### Post by ash_nug on 2009-01-04
> **Medraq said:**
> Thanks for that info CalJohnSmith  :)

I just installed Ibex Server on a system with 2 SCSI HDD's and received the same error as Ash_nug.  Adding "rootdelay=130" to the 'kernel' lines in  /boot/grub/menu.lst  solved the problem    :)

Now on to why my second NIC wasn't found .... :confused:

Has anyone had the chance to play around with the time on this?

130 seems like a long wait when booting up.

---

### Post by tad1073 on 2009-01-04
> **theozzlives said:**
> I don't understand how you booted Ubuntu in the first place if sda was unplugged during install???

grub will put itself on any available drive, example:

```

sdb=media
sdc=root

```

grub will put itself on sdb (unless you specify otherwise) because in reality sdb is hd0.

I could be wrong though.

---

### Post by Medraq on 2009-01-09
> **ash_nug said:**
> Has anyone had the chance to play around with the time on this?

130 seems like a long wait when booting up.
I reduced the 130 to 40, but I still had to wait about 45-50 seconds at the screen "Loading, please wait ...."

When I reduced the rootdelay to 30 I got the first error again.

I resolved both the rootdelay issue and my NIC issue by reformatting and installing Hardy instead of Intrepid, fwiw ...

---

