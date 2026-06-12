---
title: "HOWTO: running Ubuntu on HP nx7400 laptops"
date: 2007-02-14
forum: Outdated Tutorials &amp; Tips
---

### Post by john_brown_jr on 2007-02-14
**Introduction**
This is an attempt to describe steps required to unlock full functionality of Ubuntu on HP nx7400 laptops. Please note that nx7400 come in wide array of configurations (there are differences in processor types and wireless cards). HP nx7400 is Linux-friendly laptop, and (almost) everything works out-of-the-box in Ubuntu 6.10 (**Edgy**). Notable exception is ACPI support, which requires a little tweaking.

**Problems**
HP nx7400 laptops, as many other recent HP laptops, sufer from "bad state" problem. Laptop enters bad state whenever it is shut down or rebooted. This affects the latest official Ubuntu (6.10), the latest SUSE (10.2), and perhaps quite a few other distributions. Possible indicators of this problem are: CPU frequency scaling (speedstepping) does not work, support for some of the ACPI events (such as power source change from AC to battery) is broken, battery state is not updated when running under battery power.  A quick workarround is to remove all power sources (both battery and AC) and wait for up to 20 seconds. To fix it permanently, it is necessarry to unload "psmouse" before laptop is shut down or rebooted. Furthermore, suspend2ram requires module "i8042" to be removed before suspend. (SUSE team has done a great job in fixing these problems in their kernel. Compiled kernel which fixes these probems is already available from their FTP servers, and patches should make into the next official kernel update. I wonder if Ubuntu folks could do a similar thing.)

The laptop also fails to resume from suspend2ram. While kernels < 2.6.19 had broken SATA support and could not wake up at all, the latest kernels seem to have a problem with "i8042" (keyboard) module.

Another problem is wireless support. If you are unlucky to have Broadcom wireless card, you will have to use ndiswrapper to enable it.

**Solution**
Ubuntu kernels include psmouse compiled as module by default, however, "i8042" is compiled into kernel, so you will need to recompile the kernel and enable it as module. To compile a new kernel, you may use this tutorial: [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158). I used 2.6.20 kernel, but you might want to experiment with earlier (more stable) versions. In the kernel configuration step you will need to set up i8042 as module. During configuration phase you must also enable SATA support, or the new kernel won't boot.

It's time to modify /etc/init.d/halt.local and /etc/init.d/reboot.local scripts to remove psmouse before reboot. For example scripts, see this ([http://emisca.altervista.org/nx7400](http://emisca.altervista.org/nx7400)) page. To enable suspend2ram, it's necessary to edit /etc/default/acpi-support file to unload "psmouse" and "i8042" before suspend. For example acpi-support script, see this ([http://www.ubuntuforums.org/showthread.php?t=357769&highlight=nx7400](http://www.ubuntuforums.org/showthread.php?t=357769&highlight=nx7400)) page. It is very important to unload these modules, otherwise all the work with compiling a custom kernel is useless.

That's it - you laptop should now read the correct battery charge, and should be able to suspend and wake up. 

Wireless support requires LATEST version of ndiswrapper - older versions, like the one currently is installed by Automatix, may not work. Windows drivers can be downloaded from HP site (search for "support", then for "nx7400"). Follow the guide from [5] when installing ndiswrapper.

**Kernel configuration (SATA compiled in, psmouse and i8042 as module)**
The following is a copy from [http://www.ubuntuforums.org/showpost.php?p=2080485&postcount=95](http://www.ubuntuforums.org/showpost.php?p=2080485&postcount=95)

For SATA:
> 
Now what to enable in the make xconfig:
Device Drivers:
|---ATA/ATAPI/MFM/RLL support
|------ATA/ATAPI/MFM/RLL support
|----------Enhanced IDE/MFM/RLL disk/cdrom/tape/floppy support
|--------------support for SATA(deprecated;conflicts with libata SATA driver)
---------------#enable above choice, make sure it's a Y, not M(module)
|---SCSI device support
|-------SCSI device support
--------#enable above choice, make sure it's a Y, not M(module)
|-------SCSI disk support
--------#enable above choice, make sure it's a Y, not M(module)
|---Serial ATA(prod) and Parallel ATA(experimental) drivers
|-------ATA device support
--------#enable above choice, make sure it's a Y, not M(module)
|-----------Intel PIIX/ICH SATA support
------------#there are many kinds of support here, for me I chose this, to understand what you should choose, see below.

How to decide which ATA device support driver you should choose:
I used lspci |grep IDE and it gives:
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
And after looking through all the device supported with keyword "intel" in xconfig, I found 3, only 1 for mine, the other 2 were for PATA, so I hope yours isn't too complicated either.


For i8042:
> 
In xconfig

1) go to General Setup -> configure standard kernel features, enable it (Y)
2) go to Device Drivers -> Input Device Support -> Keyboards, change AT Keyboard to M (module)
3) Device Drivers -> Input Device Support -> Hardware IO ports -> you should now be able to set i8042 as module


For psmouse:
No need to change anything if you are using default Ubuntu configuration. If you are compiling a new kernel, make sure it is a module (M) instead of compiled in (Y).

**"E820-reserverd" errors when booting kernels >= 2.6.20**
If you get this when booting kernel:
> 
PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserverd
PCI: Not using MMCONFIG


As far as I know, this error is not dangerous, but in case it is annoying, it's very easy to get rid of it. You can simply add kernel parameter "pci=nommconf" in your /boot/grub/menu.conf. Read more about that here: [http://www.ubuntuforums.org/showthread.php?t=368663&highlight=nx7400](http://www.ubuntuforums.org/showthread.php?t=368663&highlight=nx7400)

**Troubleshooting**
In case the speedstepping is still not working, you might be required to update your BIOS version.

**References**
[1] [http://emisca.altervista.org/nx7400/](http://emisca.altervista.org/nx7400/) - Information about Debian/Ubuntu
[2] [http://en.opensuse.org/HCL/Laptops/HP](http://en.opensuse.org/HCL/Laptops/HP) Some info on SUSE kernels
[3] [https://bugzilla.novell.com/show_bug.cgi?id=179702](https://bugzilla.novell.com/show_bug.cgi?id=179702) More about the bad state problem
[4] [http://www.ubuntuforums.org/showthread.php?t=357769&highlight=nx7400](http://www.ubuntuforums.org/showthread.php?t=357769&highlight=nx7400) How to get rid of i8042 kernel module
[5] [http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3) Howto compile the latest ndiswrapper
[6] [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx7400) - Some general tips / workarrounds
[7] [http://www.ubuntuforums.org/showpost.php?p=2080485&postcount=95](http://www.ubuntuforums.org/showpost.php?p=2080485&postcount=95) - Howto enable SATA support when compiling kernel

**Todo**
Perhaps I should add links to Ubuntu Lauchpad bugs related to HP laptops. Currently, the only problem remaining is screen back light. When display goes into sleep mode, the back light sometimes stays on, and sometimes switches on later. I am certain that I will find a solution for this, but I don't have time for that right now.

---

### Post by beercz on 2007-03-12
Thanks for this.  I have an HP nx7400 laptop and have decided to recompile my 2.6.20-9 kernel with i8042 as a module.

I followed the instructions found [here]("http://www.ubuntuforums.org/showthread.php?t=311158") but am an unable to change the i8042 option to a module in qconf - it is included by default.

Any ideas how to enable this option in qconf?

Thanks in advance

---

### Post by john_brown_jr on 2007-03-12
Hi,

In xconfig

1) go to General Setup -> configure standard kernel features, enable it (Y)
2) go to Device Drivers -> Input Device Support -> Keyboards, change AT Keyboard to M (module)
3)  Device Drivers -> Input Device Support -> Hardware IO ports -> you should now be able to set i8042 as module

Let me know how it goes.

Best wishes,
John

---

### Post by adrianj on 2007-03-12
I run FF Herd 5 on a nx9420 and have the keyboard issue when suspending to ram, ie module i8042 problem. When resuming I get the password control on the screen but cannot type in anything. I am not very keen on compiling an own kernel and was wondering if this issue will be solved in future versions? 

Thanks,
Adrian

---

### Post by beercz on 2007-03-12
Thanks for replying so quickly john_brown_jr.

I have now managed to compile my kernel as per your instructions.

However, when I boot I get this message several times:

> [  xxx.yyyyyy] device-mapper: ioctl: error adding target to table
[  xxx.yyyyyy] device-mapper: table: 254:0: linear: dm-linear: Device lookup failed
(note the values for xxx.yyyyyy varies but the message is always the same)

I can successfully boot, but I still cannot hibernate.  When I try, I see the same messages as above, and then my machine goes into the lock screen (i.e. screensaver) mode.  When I unlock, I get the message (in a speech bubble near the clock): 

> HAL failed to hibernate.  Check the help file for common problems.

Can anyone enlighten me further?

Thanks again.

---

### Post by john_brown_jr on 2007-03-13
beercz, are you using Feisty? I had all sorts of weird issues with Feisty on my desktop (in fact, it locks every 2-3 minutes), so I haven't tried Feisty on my nx7400 yet,.

---

### Post by beercz on 2007-03-13
Yep - using feisty

Hmmm!! That could be a problem by the sound of it!

I am using kernel 2.6.20.10-generic at the moment (not my compiled one).

I read somewhere ([here]("http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1026460&admit=-682735245+1173783330621+28353475") - message dated 7th March by Emilio Scalise) that patches for psmouse to correct the bad state problem are included in vanilla kernel 2.6.21-rc2.

I might have another go later or wait a while for an updated kernel.

---

### Post by beercz on 2007-03-14
> **john_brown_jr said:**
> ..... During configuration phase you must also enable SATA support, or the new kernel won't boot.

john_brown_jr I am tempted to have another go at compiling a new kernel (in feisty) to see if I can get the bad state problem resolved. I've got everything backed up and a live CD handy, so if I break my ubuntu I can recover.

Where in qconf does one exactly enable SATA support?

Thanks in advance.

Wish me luck!!

---

### Post by john_brown_jr on 2007-03-14
I have updated nx7400 tutorial and included information about enabling SATA (see a couple of posts above).

As for the bad state problem - I think we should actually create a bug report in Launchpad. This bug is nasty enough, and affects quite a few HP laptops, so I believe that we can get Ubuntu kernel developers to fix it once and for all.

---

### Post by beercz on 2007-03-14
Thanks john_brown_jr - I will have a go at compiling later.

There is already a reported bug:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/81767](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/81767)

---

### Post by beercz on 2007-03-14
Right, I have made a bit of progress here.

I have sucessfully managed to compile a new kernel following john_brown_jr's instructions, and have booted from it.

Suspend seems to work OK, but my nx7400 laptop will not hibernate.

Also, about every 2 seconds there is an attempt to read my empty DVD drive for some reason.

I have temporarily reverted back to my previous kernel (2.6.20-10-generic).

Any ideas anyone?

Thanks in advance and thanks again john_brown_jr.

btw has anyone actually got suspend/hibernate working properly on the nx7400?  In feisty?

---

### Post by spikyjt on 2007-04-10
Bug #23497 shows the status of the suspend/resume problem. Sadly it seems it will not be fixed officially in Feisty final. There is a patch supplied on that bug page, but it has a bug itself and is for an older version of acpi-support than the current Feisty version.
Anyway here's what I did:

    sudo nano /etc/acpi/suspend.d/20-i8042-input.sh

    #!/bin/sh
    # Unbind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
    fi

(save ctrl-x)

    sudo nano /etc/acpi/resume.d/39-i8042-input.sh

    #!/bin/sh
    # Rebind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
    fi

(save ctrl-x)

    sudo chmod +x /etc/acpi/suspend.d/20-i8042-input.sh
    sudo chmod +x /etc/acpi/resume.d/39-i8042-input.sh

That's it! Bargain - it works a treat. Hope this works for everyone else. Thanks to Scott Robinson for the patch.

---

### Post by beercz on 2007-04-10
> **spikyjt said:**
> Bug #23497 shows the status of the suspend/resume problem. Sadly it seems it will not be fixed officially in Feisty final. There is a patch supplied on that bug page, but it has a bug itself and is for an older version of acpi-support than the current Feisty version.
Anyway here's what I did:

    sudo nano /etc/acpi/suspend.d/20-i8042-input.sh

    #!/bin/sh
    # Unbind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
    fi

(save ctrl-x)

    sudo nano /etc/acpi/resume.d/39-i8042-input.sh

    #!/bin/sh
    # Rebind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
    fi

(save ctrl-x)

    sudo chmod +x /etc/acpi/suspend.d/20-i8042-input.sh
    sudo chmod +x /etc/acpi/resume.d/39-i8042-input.sh

That's it! Bargain - it works a treat. Hope this works for everyone else. Thanks to Scott Robinson for the patch.

Thanks for this spikyjt.

The suspend option seems to work.

Can the same principle be applied to hibernate as well, if so how?

Thanks again.

---

### Post by FrancoNero on 2007-04-19
any chance all those problems be fixed ina  regularly shipped feisty update anytime soon? this problem is a major annoyance.... everybody talking about 3d effects and whatnot, and in the meantime the most basic stuff seems to not work

---

### Post by unikuser on 2007-05-08
> **spikyjt said:**
> Bug #23497 shows the status of the suspend/resume problem. Sadly it seems it will not be fixed officially in Feisty final. There is a patch supplied on that bug page, but it has a bug itself and is for an older version of acpi-support than the current Feisty version.
Anyway here's what I did:

    sudo nano /etc/acpi/suspend.d/20-i8042-input.sh

    #!/bin/sh
    # Unbind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
    fi

(save ctrl-x)

    sudo nano /etc/acpi/resume.d/39-i8042-input.sh

    #!/bin/sh
    # Rebind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
    fi

(save ctrl-x)

    sudo chmod +x /etc/acpi/suspend.d/20-i8042-input.sh
    sudo chmod +x /etc/acpi/resume.d/39-i8042-input.sh

That's it! Bargain - it works a treat. Hope this works for everyone else. Thanks to Scott Robinson for the patch.

I tried the steps mentioned and resume/suspend works perfectly well! I use nc8430 laptop. I already have the suspend.d file though.

---

### Post by FrancoNero on 2007-05-08
test 1: suspend seems to work

i could return from suspend and use mouse and keyboard, so i could log back in. still gave me some ugly graphics stuff, and once,(test 2)  i got a "failed to suspend" error. but basically it kinda worked.

test 3: hibernate still doesn't really work. when i go to hibernate, it gives me a black screen with lines and lines of usb, acpi and whatever errors and at some point the laptop switches off. when i return, it looks like it hibernated, but i suspect it didnt really....

---

### Post by sweRascal on 2007-05-23
Seems to work fine for my HP nc6400 as well...

---

### Post by aasche on 2007-06-10
If suspend doesn't work, check the post #34 from Johan Brannlund on 2007-06-08 at:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/23497")

Works on nx7400 RH401ET#ABD :)

---

### Post by vinodis on 2007-08-30
Suspend To Memory on Feisty with Compaq nx6320 works well after including the script mentioned by Spikyjt. Thank you!

---

### Post by FrancoNero on 2007-08-30
for me it works now, with the latest gutsy updates.
hibernate still doesn't

---

### Post by eurgain on 2007-09-25
> **spikyjt said:**
> Bug #23497 shows the status of the suspend/resume problem. Sadly it seems it will not be fixed officially in Feisty final. There is a patch supplied on that bug page, but it has a bug itself and is for an older version of acpi-support than the current Feisty version.
Anyway here's what I did:

    sudo nano /etc/acpi/suspend.d/20-i8042-input.sh

    #!/bin/sh
    # Unbind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/unbind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
    fi

(save ctrl-x)

    sudo nano /etc/acpi/resume.d/39-i8042-input.sh

    #!/bin/sh
    # Rebind the AT keyboard interface.
    if [ -f /sys/bus/platform/drivers/i8042/bind ]; then
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
    fi

(save ctrl-x)

    sudo chmod +x /etc/acpi/suspend.d/20-i8042-input.sh
    sudo chmod +x /etc/acpi/resume.d/39-i8042-input.sh

That's it! Bargain - it works a treat. Hope this works for everyone else. Thanks to Scott Robinson for the patch.

This is not yet in Gutsy Flight 5, in which suspend is still broken in the default install.

However, I can confirm that the above fix-up has sorted my nx7400 with Intel video and ipw3945, although there is a little warning message bubble on resume that tells me, incrrectly, that suspend failed (but this can be suppressed).  No kernel re-compilation was required.

To prove it, I am sending this after three successive suspend/resume cycles, with no user intervention to get anything working.  I have a super machine with a great OS, so I am very pleased!

A

PS.  The machine came pre-loaded with Vista.  I had no option - it was some sort of very cheap old-new-stock deal.  I played with it for a couple of days, and thought about setting up a dual boot system.  However, Vista was just *so* slow.  I thought I had bought a lemon!  Thankfully, all that is behind me now.

---

### Post by beercz on 2007-09-26
> **eurgain said:**
> This is not yet in Gutsy Flight 5, in which suspend is still broken in the default install.

However, I can confirm that the above fix-up has sorted my nx7400 with Intel video and ipw3945, although there is a little warning message bubble on resume that tells me, incrrectly, that suspend failed (but this can be suppressed).  No kernel re-compilation was required.

To prove it, I am sending this after three successive suspend/resume cycles, with no user intervention to get anything working.  I have a super machine with a great OS, so I am very pleased!

A

PS.  The machine came pre-loaded with Vista.  I had no option - it was some sort of very cheap old-new-stock deal.  I played with it for a couple of days, and thought about setting up a dual boot system.  However, Vista was just *so* slow.  I thought I had bought a lemon!  Thankfully, all that is behind me now.
Hmm!

Although this worked in feisty, I can't get it to work in gutsy :-(

When I find the time I will look into this.

In the meantime, anyone else got any ideas?

---

### Post by FrancoNero on 2007-09-26
suspend works fine now (gutsy, latest updates), as stated earlier. hibernate still no go on the nx7400. just does not work.

---

### Post by beercz on 2007-10-30
> **FrancoNero said:**
> suspend works fine now (gutsy, latest updates), as stated earlier. hibernate still no go on the nx7400. just does not work.
At the moment I have exactly the reverse situation working on my nx7400 laptop running gutsy.

I got hibernate working by following the instructions given on [this page]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/").

Working on suspend at the moment - although this is less of an issue for me.

---

### Post by FrancoNero on 2007-10-30
well gutsy is dead for me for now, i'll wait a couple weeks and run updates and see if there's any improvement. gutsy final is beta software in my eyes

---

### Post by john_brown_jr on 2007-11-14
I can report limited success with suspend to RAM in Gutsy. It's kind of strange - it does not wake on it's own, but does so only when some keyboard keys are pressed. So, it wakes up, for example, if I'm holding down 'left' key on the keyboard after resume from suspend. Can anyone else confirm this?

P.S.
When my nx7400 has returned from suspend, shutdown/suspend does not work correctly. Again, holding down some keys on the keyboard helps it to shutdown/suspend correctly.

In Gutsy (unlike Feisty) I had no success with custom-compiled kernels (manually unloading i8042 before suspend et al.)

---

### Post by john_brown_jr on 2007-11-16
Created a bug report for Gutsy suspend problem:
[https://bugs.launchpad.net/ubuntu/+bug/163115](https://bugs.launchpad.net/ubuntu/+bug/163115)

---

### Post by Delkster on 2007-12-10
> **john_brown_jr said:**
> I can report limited success with suspend to RAM in Gutsy. It's kind of strange - it does not wake on it's own, but does so only when some keyboard keys are pressed.
I've seen this also. I'm running Gutsy upgraded from Feisty. To me this seems to be a regression from Feisty as suspend and resume worked fine in the previous release (after changing the resume.sh script to bring back the keyboard).

> So, it wakes up, for example, if I'm holding down 'left' key on the keyboard after resume from suspend. Can anyone else confirm this?
I had never found out about the key pressing trick, but I'll try that when the problem occurs again, even if it seems that it doesn't directly provide a real solution.

---

### Post by FrancoNero on 2008-02-24
still no success hibernate on hardy..... I would assume canonical has the financial resources to at least test some of the most prominent hardware for its operating system? i'm having a hard time to believe that an HP laptop wouldn't fall into that category

---

### Post by beercz on 2008-03-11
I have just reinstalled Gutsy (after trying Hardy for a while).  Still not got suspend/hibernate working.  Everything else works "perfectly peachy" as my son would say :-)
 
Anyone have any success with the hibernate/suspend issue on a nx7400?  I don't want to trawl the forums/google again to try to get it working unless I have to.
 
If not, and I manage to get it working, I will post back here as to how I did it.
 
Thanks in advance.

---

