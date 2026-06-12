---
title: "Grub Loading Stage 1.5"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by juzar on 2008-06-30
Hi I just installed Ubuntu 6.06 via the live CD but on rebooting it simply shows a message "GRUB LOADING STAGE 1.5" and gets stuck...Please tell me how do I fix this problem I'm new to UBUNTU and aint very sure of how to work it out..please help...

---

### Post by unutbu on 2008-06-30
Hi juzar, we need a bit more information.
Please boot from the LiveCD, open a terminal, and post the output of 
```

sudo fdisk -l
```

---

### Post by juzar on 2008-06-30
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2329    18707661   83  Linux
/dev/hda2            2330        2432      827347+   5  Extended
/dev/hda5            2330        2432      827316   82  Linux swap / Solaris

here is the output...

---

### Post by unutbu on 2008-06-30
Please post the output of
```
sudo mkdir /Ubuntu
sudo mount /dev/hda1 /Ubuntu
cat /Ubuntu/boot/grub/menu.lst
```

---

### Post by juzar on 2008-06-30
when i give it the command  sudo mount /dev/hda1/Ubuntu it gives the output as mount: can't find /dev/hda1/Ubuntu in /etc/fstab or /etc/mtab

---

### Post by unutbu on 2008-06-30
> **juzar said:**
> when i give it the command  sudo mount /dev/hda1/Ubuntu it gives the output as mount: can't find /dev/hda1/Ubuntu in /etc/fstab or /etc/mtab

Put a space between /dev/hda1 and /Ubuntu.
(We are mounting the /dev/hda1 partition at a mount point called /Ubuntu.)

---

### Post by ChameleonDave on 2008-06-30
> **juzar said:**
> Hi, I just installed UBUNTU 6.06 via a live CD on my GATEWAY laptop and when I reboot it shows a message "GRUB LOADING STAGE 1.5" and gets stuck...please guide me through this problem...

HEY!!

DO NOT CROSS POST!

You have posted this in both *Installation & Upgrades* and *Absolute Beginners Talk*.

You are wasting people's time by getting two separate lots of people independently giving you the same advice.  Have some respect for others, please.

---

### Post by juzar on 2008-06-30
really sorry for the cross post will delete the other one immediately there was some problem with the internet connection at that time..sorry

---

### Post by juzar on 2008-06-30
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
 here is the menu.lst file

---

### Post by ChameleonDave on 2008-06-30
> **unutbu said:**
> Put a space between /dev/hda1 and /Ubuntu.
(We are mounting the /dev/hda1 partition at a mount point called /Ubuntu.)

Sometimes it can be helpful with newbies to put a double or triple space between strings of text, in order to make it clear that they are separated.  The command line treats any number of spaces as the same thing.

---

### Post by ChameleonDave on 2008-06-30
> **juzar said:**
> Hi I just installed Ubuntu 6.06 via the live CD but on rebooting it simply shows a message "GRUB LOADING STAGE 1.5" and gets stuck...Please tell me how do I fix this problem I'm new to UBUNTU and aint very sure of how to work it out..please help...
(I just gave this exact same advice to someone else but they didn't need it.  I hope you find it useful!)

In certain situations, GRUB can be left trying to load its files from the wrong location.  This is because GRUB goes by rules like "load files from the fifth partition of what the BIOS tells me is the second drive attached to the machine".

You can get info about all the drives by running the "fdisk -l" command as root (normally by putting "sudo" in front of it).

You will no doubt have to reinstall GRUB, which is easy.  Just boot from a Linux live CD, go to a command-line terminal and run "grub" as root.  Grub will then take over the terminal and allow you to type in the following:

```
grub> find /boot/grub/stage1
 (hd1,6)

grub> root (hd1,6)

grub> setup (hd1)

grub> quit
```

The above is an example showing how it would work on my computer.  As you can see, the first command comes back with the information that the files GRUB needs are on hard drive 1, partition 6.  I then used that info to set the root partition as being hd1,6, and then told it to install itself to the master boot record of hard drive 1.  Then I quit.

You'll find that if you press Tab while typing "root (hd", GRUB will helpfully do some autocompletion for you, suggesting possible drives and suchlike.  In fact, the info it gives you as you do this can actually dispense with the need to use "find" or "fdisk".

---

### Post by kansasnoob on 2008-06-30
This older how-to might be helpful:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Also the "Quick Start" section of this tutorial may be helpful:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

NOTE: I fully realize that you didn't mess up GRUB installing windows which is why I say to look only at the "Quick Start" section of that second guide. I've just found it useful as a nOOb.

---

### Post by juzar on 2008-06-30
Hi Im sorry but the idea of reinstalling grub did not work out for me I tried exactly as u had posted and rebooted but it still got stuck at the same place showing "GRUB LOADING STAGE 1.5"

---

### Post by juzar on 2008-06-30
Hey is anyone there guys plz help...

---

### Post by ChameleonDave on 2008-06-30
> **juzar said:**
> Hey is anyone there guys plz help...
When you typed "*find /boot/grub/stage1*" what was the output?

---

### Post by juzar on 2008-06-30
(hd0,0) this was the o/p

---

### Post by ChameleonDave on 2008-06-30
> **juzar said:**
> (hd0,0) this was the o/p
That looks fine.

But the contents of your menu.lst that you posted before looked incomplete to me.  Edit that file, and add these lines to the top:

```

default         0                            
timeout         10                                           
color cyan/blue white/blue 

```

This will ensure that a menu comes up with a choice of options.

Does it still fail at the same point?

---

### Post by juzar on 2008-06-30
hello anyone there, guys please help out...

---

### Post by juzar on 2008-06-30
YES it still keeps failing at the same point...guys please help...

---

### Post by ChameleonDave on 2008-06-30
> **juzar said:**
> YES it still keeps failing at the same point...guys please help...

Stop all this "please help please help please help please help" stuff.  I'm checking this thread regularly.  All you have to do is answer the last question that you are asked.  It's like you're implying we're not already helping you.


I don't understand why GRUB is unable to work.  This is not even an Ubuntu or Linux problem.  GRUB should definitely get to the OS choices list after all we have done.

All I can imagine is that some abnormality in the BIOS of the motherboard or in the physical configuration of the hard drive is causing an error.  Go into your BIOS configuration when you power up the machine.  Look through all the options and see if something can be changed to affect the booting process.

Has this machine previously had an operating system working on it correctly?  Do you have an installation CD for another operating system available for testing?

The only other suggestion I can think of is to install LILO instead of GRUB.

---

### Post by juzar on 2008-06-30
Hey did all that u said n yes it had an windows working fine on it previously... also let me know how do i install lilo instead of grub.

---

### Post by unutbu on 2008-06-30
Boot from LiveCD.
Open a terminal.
Type

```
sudo grub
```

At the grub> prompt type
```

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```
Reboot.

---

### Post by kansasnoob on 2008-06-30
I'm admittedly lost, but:

Install Lilo from a Linux LiveCD

[http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD](http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD)

Is there any way you could get your hands on (or burn) a Super Grub Disk?

---

### Post by kansasnoob on 2008-06-30
Oops, forgot a link:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

But, follow what Unutbu is saying first!!!!!!!

As I said I'm lost:confused:

---

### Post by juzar on 2008-06-30
While installing from the live CD it gives no option between grub and lillo. Am I missing something during installation...how do I install lilo from the live CD?

---

### Post by stchman on 2008-06-30
> **juzar said:**
> Hi I just installed Ubuntu 6.06 via the live CD but on rebooting it simply shows a message "GRUB LOADING STAGE 1.5" and gets stuck...Please tell me how do I fix this problem I'm new to UBUNTU and aint very sure of how to work it out..please help...

Granted 6.06 is LTS, but if you are going to install Ubuntu new then go for 8.04.  It has a lot more features and is more usable.

---

### Post by ChameleonDave on 2008-06-30
> **kansasnoob said:**
> 

But, follow what Unutbu is saying first!!!!!!!


For chrissake... am I wasting my time here?  I explained to the guy how to install GRUB, he replies that it still fails, Unutbu comes along and tells the guy to install GRUB (as though I hadn't already gone through that!), and then you tell the guy to "follow what Unutbu is saying"!

> **stchman said:**
> Granted 6.06 is LTS, but if you are going to install Ubuntu new then go for 8.04.  It has a lot more features and is more usable.

Damn, I missed that bit.  Yes, he should be using Hardy Heron.  I can't give him tech support unless he's using recent software.

> **juzar said:**
> 
[QUOTE=kansasnoob;5292196]
Install Lilo from a Linux LiveCD

[http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD](http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD)


While installing from the live CD it gives no option between grub and lillo. Am I missing something during installation...how do I install lilo from the live CD?[/QUOTE]
Kansasnoob provides you with a link to a guide to installing LILO, and you respond with a request for a guide to installing LILO?

I just give up.

---

### Post by unutbu on 2008-06-30
> **ChameleonDave said:**
> Grub will then take over the terminal and allow you to type in the following:

```
grub> find /boot/grub/stage1
 (hd1,6)

grub> root (hd1,6)

grub> setup (hd1)

grub> quit
```


> **juzar said:**
> Hi Im sorry but the idea of reinstalling grub did not work out for me I tried **exactly as u had posted** and rebooted but it still got stuck at the same place showing "GRUB LOADING STAGE 1.5"

It sounds to me that juzar typed exactly what you posted ChameleonDave. I know you know how to modify them appropriately, ChameleonDave. But I'm not sure that juzar realized that these were not exactly the right commands for him. That is why I posted the exact commands he needs to use for his setup, and told him to try GRUB again.

---

### Post by kansasnoob on 2008-06-30
> **ChameleonDave said:**
> For chrissake... am I wasting my time here?  I explained to the guy how to install GRUB, he replies that it still fails, Unutbu comes along and tells the guy to install GRUB (as though I hadn't already gone through that!), and then you tell the guy to "follow what Unutbu is saying"!



Damn, I missed that bit.  Yes, he should be using Hardy Heron.  I can't give him tech support unless he's using recent software.


Kansasnoob provides you with a link to a guide to installing LILO, and you respond with a request for a guide to installing LILO?

I just give up.


Calm down man! Only 5 months ago I started out with gOS and Freespire (well I had tried Lindows 5 or 6 years ago when it first came out) and I quite often had to ask folks to repeat things ad nauseum. I still do more things wrong than I do right.

One of the reasons I landed on Ubuntu was the helpfulness and patience I encountered here at the forums. I think you probably even helped me in the past. We nOObs need all the help we can get!

Patience, my friend, patience:)

Though I do think that either 8.04 or a Super GRUB Disk would be the best way forward now in this case, but maybe that's not an option available to them:confused:

---

### Post by juzar on 2008-07-01
hi, I tried installing lilo via the Synaptic package manager and this is the output I got when I ran the command "liloconfig"

ubuntu@ubuntu:/usr/sbin$ liloconfig
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.

    WARNING!
        Your /etc/fstab configuration file gives device unionfs as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle.

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.

Any ideas of what i can do to resolve this problem...

---

### Post by juzar on 2008-07-01
hi, I tried installing lilo via the Synaptic package manager and this is the output I got when I ran the command "liloconfig"

ubuntu@ubuntu:/usr/sbin$ liloconfig
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.

    WARNING!
        Your /etc/fstab configuration file gives device unionfs as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle.

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.

Any ideas of what i can do to resolve this problem...

---

### Post by ChameleonDave on 2008-07-01
> **juzar said:**
> 
"Documentation for LILO can be found in /usr/share/doc/lilo/."

Any ideas of what i can do to resolve this problem...
Well, you could try reading the documentation found in /usr/share/doc/lilo/.

---

### Post by juzar on 2008-07-03
Tried reading the documentation but could't find any solution...Is there anyway I can download lilo from the internet and install it...please keep in mind that I have no OS installed on the system and will be downloading via the internet connection from the live CD.

---

