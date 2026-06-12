---
title: "New dual core processor not showing up"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by forrestcupp on 2008-05-20
Hello friends.

I just took my hard drive with a Hardy install out of my old computer and put it into a new computer with an Athlon 64 X2 processor.  My old computer was single core.  So when I booted to Ubuntu in the new computer, everything worked out of the box, except the dual core.  My System Monitor is only showing one core, and I can't find any evidence anywhere else that I have 2 cores working.  I'm using the Generic kernel, so it should be supported.

Anyone have any ideas?

---

### Post by Inxsible on 2008-05-20
Since your old computer was a 32 bit computer, the Hardy install on it was a 32 bit one. I don't think it will recognize both cores unless you install a 64 bit OS.

Please correct me if I am wrong guys !

---

### Post by forrestcupp on 2008-05-20
From everything I've read, dual core should work in 32-bit *and* 64 bit

---

### Post by philinux on 2008-05-20
> **Inxsible said:**
> Since your old computer was a 32 bit computer, the Hardy install on it was a 32 bit one. I don't think it will recognize both cores unless you install a 64 bit OS.

Please correct me if I am wrong guys !

Many people with 64bit pc's are running the 32 os.

---

### Post by Inxsible on 2008-05-20
> **forrestcupp said:**
> From everything I've read, dual core should work in 32-bit *and* 64 bitand it is !!

you said your system works without a hitch right? But I don't think it will see both cores.

---

### Post by philinux on 2008-05-20
> **forrestcupp said:**
> Hello friends.

I just took my hard drive with a Hardy install out of my old computer and put it into a new computer with an Athlon 64 X2 processor.  My old computer was single core.  So when I booted to Ubuntu in the new computer, everything worked out of the box, except the dual core.  My System Monitor is only showing one core, and I can't find any evidence anywhere else that I have 2 cores working.  I'm using the Generic kernel, so it should be supported.

Anyone have any ideas?

Have you tried to update the system?

---

### Post by hellomoto on 2008-05-20
hmmm. My dual processor shows up on 32bit. I would try a fresh install with your HD installed in the new PC, this may resolve. If it doesn't I would then try a fresh 64 bit install from your new PC.

---

### Post by Inxsible on 2008-05-20
> **philinux said:**
> Many people with 64bit pc's are running the 32 os.I know. but it doesn't make use of both cores in parallel

---

### Post by philinux on 2008-05-20
Forest,

You need to run

sudo apt-get update && sudo apt-get upgrade

---

### Post by forrestcupp on 2008-05-20
> **Inxsible said:**
> I know. but it doesn't make use of both cores in parallel32 bit does recognize dual cores in parallel.  That's what I meant earlier.  Below is a testimony in this thread that someone has it working.

> **hellomoto said:**
> hmmm. My dual processor shows up on 32bit. I would try a fresh install with your HD installed in the new PC, this may resolve. If it doesn't I would then try a fresh 64 bit install from your new PC.

> **philinux said:**
> Have you tried to update the system?Yes.  I just updated, and it didn't change my status.

I know I may need to try reinstalling, but I'd rather not if there's a way.  I have a lot of things installed and set up that I'd rather not have to worry about.

---

### Post by HotShotDJ on 2008-05-20
> **Inxsible said:**
> I know. but it doesn't make use of both cores in parallelYes, Inxsible, it does (or is supposed to, anyway).  If one runs 32 bit Ubuntu on a Dual-Core system, it SHOULD make use of both processors.

Forrestcup:  Please check to see what kernel you have running... in a terminal, run: ```
uname -a
``` and post the results.

---

### Post by hellomoto on 2008-05-20
When the OS loads doesn't it check certain hardware specifications from when it was installed against what is actually installed to date?

What I mean is I know back when I used windows I changed a mobo and because the hardware wasn't the same it wouldn't load. I know that this is also due to licensing issues with windows but I wonder if this maybe a reason for your CPU not showing properly.

I am just going alot of assumptions here, just a trail of thought ain the hope of helping.

---

### Post by forrestcupp on 2008-05-20
Here are the results of uname -a
```
Linux Deep-Thought 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

```

It's generic, which should support it.  And does the 'SMP' tell anything?

---

### Post by forrestcupp on 2008-05-20
> **hellomoto said:**
> When the OS loads doesn't it check certain hardware specifications from when it was installed against what is actually installed to date?

What I mean is I know back when I used windows I changed a mobo and because the hardware wasn't the same it wouldn't load. I know that this is also due to licensing issues with windows but I wonder if this maybe a reason for your CPU not showing properly.

I am just going alot of assumptions here, just a trail of thought ain the hope of helping.

That's a good thought, but my new computer is using a different sound card, and it showed up and worked without problem.  So that leads me to believe that it can adapt.  They programmed Windows that way intentionally so that people wouldn't put the same copy on multiple computers.

---

### Post by HotShotDJ on 2008-05-20
> **forrestcupp said:**
> It's generic, which should support it.  And does the 'SMP' tell anything?Yes.. that stands for Symmetrical Multi-Processor (which is exactly what you want).  Stand by for a moment... don't touch that dial.. I'm doing a little research for you before I make a suggestion.

---

### Post by hellomoto on 2008-05-20
hmmm, yeh i thought MS probably would. I wasn't sure though as your CPU is such a key component.

But I hope you get it sorted out, sorry I can't be more help.

also Bump! ;)

---

### Post by bumanie on 2008-05-20
Post the output of > sudo cat /proc/cpuinfo That should say what ubuntu is seeing your processor as.

---

### Post by philinux on 2008-05-20
Forest,

Since you've done the update I'd reboot.

Also look in dmesg.

---

### Post by hellomoto on 2008-05-20
whoooooop! 

100 hundred posts here!

1
0
0


stay tuned... 1000 coming shortly!

also Bump ;)

---

### Post by H.Callahan on 2008-05-20
I am interested in the answer here, too.  I have a quad core in my (near) future, and want to know if Ubuntu supports it.  (I'd hate to go back to Windows on a technicality!)

---

### Post by stchman on 2008-05-20
> **forrestcupp said:**
> Hello friends.

I just took my hard drive with a Hardy install out of my old computer and put it into a new computer with an Athlon 64 X2 processor.  My old computer was single core.  So when I booted to Ubuntu in the new computer, everything worked out of the box, except the dual core.  My System Monitor is only showing one core, and I can't find any evidence anywhere else that I have 2 cores working.  I'm using the Generic kernel, so it should be supported.

Anyone have any ideas?

Yes, the -generic kernel (both i386 and amd64) support dual and quad cores.

I run a quad core Core 2 Quad on i386 and all cores are supported.

The -386 kernel do not support multi cores at all.

---

### Post by littletinman on 2008-05-20
Thats an awesome question H.Callahan, i wondered the same thing. I'm thinking about building a computer with a quadcore but i'm a hardcore Ubuntu man. I need to know if it will run correctly. I have both 32 and 64 bit ubuntu running on this laptop on seperate partitions. I recommend that you install 64 bit on another partition and give that a shot.


 Little Man

---

### Post by philinux on 2008-05-20
Forest,

[http://ubuntuforums.org/showthread.php?t=75827](http://ubuntuforums.org/showthread.php?t=75827)

---

### Post by HotShotDJ on 2008-05-20
Ok... I was just making sure that generic was the correct kernel -- there used to be a k7 kernel.  But you ARE running a kernel that is appropriate to your system.

I, too, would like to see the output of sudo cat /proc/cpuinfo as suggested by bumanie

Also, I'm wondering (and here, I'm speculating) if there might be a setting in the BIOS that needs setting for use with a 32 bit OS.  I can't image why such a setting would be there, but its worth checking before doing anything radical, like a reinstall.

---

### Post by forrestcupp on 2008-05-20
> **bumanie said:**
> Post the output of  That should say what ubuntu is seeing your processor as.

Here's my output:
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips	: 2057.49
clflush size	: 64

```
So it recognizes the processor correctly, but only shows 1 core.  Also, it says 1000 MHz, when it should be around 2.3 GHz per core.

And I have rebooted multiple times.

Thanks for the response, guys.

---

### Post by forrestcupp on 2008-05-20
> **philinux said:**
> Forest,

[http://ubuntuforums.org/showthread.php?t=75827](http://ubuntuforums.org/showthread.php?t=75827)

Good snooping, but that's a very old thread.  SMP should be supported in the Generic kernel.

---

### Post by bumanie on 2008-05-20
You should try the smp as suggested in the thread posted by philinux. I can vouch that an amd64 should show both cores on a 32-bit system as I run an amd 64 4800+ on 32bit ubuntu. Even conky shows up both cores.I can't check my /proc/cpuinfo as a comparison, as I am at work on a windoze machine, but I think it should show the 2.3ghz as you say.

PS: Disregard the smp thing then. Come to think of it, I didn't have to do anything like that to get my amd recognised correctly.

---

### Post by HotShotDJ on 2008-05-20
> **forrestcupp said:**
> So it recognizes the processor correctly, but only shows 1 core.  Also, it says 1000 MHz, when it should be around 2.3 GHz per core.The 1000 MHz thing is fine.  That is about the CPU stepping.  When needed, it will "step up" to the higher speeds.  Other than my suggestion about checking the system BIOS for some clues, I'm not sure what else to look at.  You MIGHT want to throw in an Ubuntu Installation CD and boot it up and see if the CPU gets detected properly there.  If so, it might take a reinstall to complete your migration to the new motherboard.

---

### Post by forrestcupp on 2008-05-20
> **HotShotDJ said:**
> The 1000 MHz thing is fine.  That is about the CPU stepping.  When needed, it will "step up" to the higher speeds.  Other than my suggestion about checking the system BIOS for some clues, I'm not sure what else to look at.  You MIGHT want to throw in an Ubuntu Installation CD and boot it up and see if the CPU gets detected properly there.  If so, it might take a reinstall to complete your migration to the new motherboard.
Thanks for the suggestions.  Both cores work in Vista, so I know it's not a BIOS setting.

I guess I'll probably just have to break down and reinstall.

If someone knows a solution to this, go ahead and post it for future reference.

Thanks everyone.

---

### Post by bumanie on 2008-05-20
> The 1000 MHz thing is fine. That is about the CPU stepping. When needed, it will "step up" to the higher speeds. You could be right. I can't remember what my /proc/cpuinfo says (as said, at work at present), but I do remember conky shows the cores running at 1GHz most of the time.

---

### Post by niteshifter on 2008-05-20
Hi,

@ forestcupp

Could you post /boot/grub/menu.lst here please? I'd like to have a look, I may have a solution.

---

### Post by philinux on 2008-05-20
You never said if rebooting did anything?

---

### Post by forrestcupp on 2008-05-20
> **niteshifter said:**
> Hi,

@ forestcupp

Could you post /boot/grub/menu.lst here please? I'd like to have a look, I may have a solution.
menu.lst```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f323177c-d65d-4f41-abd3-1a3636fb0353 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f323177c-d65d-4f41-abd3-1a3636fb0353 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f323177c-d65d-4f41-abd3-1a3636fb0353 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f323177c-d65d-4f41-abd3-1a3636fb0353 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f323177c-d65d-4f41-abd3-1a3636fb0353 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Factory System Restore
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

> **philinux said:**
> You never said if rebooting did anything?
Actually, I said I've rebooted several times, and I'm still obviously having the same trouble.  Thanks, though.

---

### Post by niteshifter on 2008-05-20
Hi,

Ah, sorry. My fix does not apply. I've seen this happen with nolapic specified on the boot line in menu.lst - but you're not using that option. I wanted to look because that option can be confused with noapic. The fix is to remove the nolapic option and reboot

---

### Post by forrestcupp on 2008-05-20
> **niteshifter said:**
> Hi,

Ah, sorry. My fix does not apply. I've seen this happen with nolapic specified on the boot line in menu.lst - but you're not using that option. I wanted to look because that option can be confused with noapic. The fix is to remove the nolapic option and reboot
It's good you went ahead and posted this.  Maybe this will come in handy for someone in the future.

---

### Post by forrestcupp on 2008-05-20
Ubuntu has no love for me.  I reinstalled it, and it still does not recognize my 2nd core.  I booted Vista (32-bit) to double check, and it *is* using both cores, so I know they work.

I don't know what to do.

---

### Post by hellomoto on 2008-05-20
this is interesting now!

Im very surprised that it didn't recognize your second processor on a reinstall.

I have no idea what could be the problem either.

did u install 64 or 32 bit?

---

### Post by forrestcupp on 2008-05-20
Well, in my case, I guess I'll have to eat my words.  I just found [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213011) that talks about the exact problem I'm having.  Come to find out, a lot of the people there have the same Acer Aspire computer that I have with an AMD chipset.  They all say that 32-bit only recognizes 1 core, but 64-bit works with both cores.

So I may have to try 64-bit.  I know it's a pain getting Java working, and I've heard bad reports about Atheros wireless in 64-bit, but I may have to try it anyway.

---

### Post by anxfisa on 2008-05-20
Thank you so much for listing this. I also use an Acer Aspire, it's AMD turion 64x2. I had to double check but it seems i installed the correct one by accident, LOL! I marked the 64 bit just because it said AMD and being totally new to Linux had no idea. 

Thank you for pointing out other issues as well. I am going through and double checking everything now.

---

### Post by forrestcupp on 2008-05-20
> **forrestcupp said:**
> 
So I may have to try 64-bit.  I know it's a pain getting Java working, and I've heard bad reports about Atheros wireless in 64-bit, but I may have to try it anyway.

Well, I installed 64-bit and it *does* recognize both cores.  So, sorry to Inxsible because in my case, you were right.

Also, I'm pretty stoked because the report I heard on Atheros is wrong.  My Atheros wireless worked OOTB with 64-bit.  No hassles other than entering my WEP code.  Now to tackle the normal 64-bit hardships, like Flash and Java.

---

### Post by markbuntu on 2008-05-20
FLash is no problem, just get the latest flashplugin-nonfree and update your pulseaudio and the get the nspluginwrapper. Is was all I had to do, no tweaking or screwing around in terminal... good luck.

---

### Post by forrestcupp on 2008-05-20
> **markbuntu said:**
> FLash is no problem, just get the latest flashplugin-nonfree and update your pulseaudio and the get the nspluginwrapper. Is was all I had to do, no tweaking or screwing around in terminal... good luck.

Thanks.  Flash was easy.  I just installed flashplugin-nonfree and it automatically downloaded all necessary dependencies and set it up for me.  It was pretty much as easy as 32-bit.

As for Java, I installed the FF plugin with OpenJDK and it is working for me well enough so far.  So that was painless too.

All in all, I'm glad I was forced into 64-bit.  It's a lot less painful than it was last time I tried.  It seems to run much smoother, too.  But that could just be that I have both processor cores working now.

---

### Post by philinux on 2008-05-20
> **forrestcupp said:**
> Thanks.  Flash was easy.  I just installed flashplugin-nonfree and it automatically downloaded all necessary dependencies and set it up for me.  It was pretty much as easy as 32-bit.

As for Java, I installed the FF plugin with OpenJDK and it is working for me well enough so far.  So that was painless too.

All in all, I'm glad I was forced into 64-bit.  It's a lot less painful than it was last time I tried.  It seems to run much smoother, too.  But that could just be that I have both processor cores working now.


Glad your on the way with 64 bit. It's the future really.
With my new pc i went straight for the 64 bit os. Have you got compiz running wow it's so neat.

---

### Post by Inxsible on 2008-05-21
64 bit OS is no longer a problem that it used to be. Flash and Java have become easier and so have most of other apps. There are a few apps that still don't have a 64 bit alternative, although you can install the 32 bit versions by installing the 32 bit libraries for them. Skype is one such software (unless they came out with a 64 bit one recently) and I think Opera was too until recently.

---

