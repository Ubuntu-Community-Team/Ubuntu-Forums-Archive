---
title: "HOWTO: Suspend2 in Breezy"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Griffin3 on 2005-10-13
Suspend2 brings to the Linux world the ability to suspend the current working state of the computer to hard disk, and power off the machine, then restart it to the exact same state where you left off. This is similar to the ability of Windows machines to hibernate, and is invaluable to laptop users; when your battery is about to run out, you can save your work in progress. After a while, I have found it helps my productivity enormously, because I can save my "mental state" in the layout of windows and browser tabs I have open, and restore a better summary of what I was working on at the time I had to leave the computer, without taking notes and bookmarking all the bits that I was in the process of researching.

Suspend2 differs from the suspend functionality built into the kernel in that it supports up to 4 GB of memory, compresses the save image while writing to the disk, and supports suspend to file and splashscreen integration (but this tutorial does not cover these last two.)  It also is rumored to support SMP, but we have not yet gotten that functionality working.  In addition, it just flat **works** on a whole bunch of machines and configurations that seem to cause the original suspend to fail.

This patch as modified might not function on clustered computers, but you could argue that it doesn't make much sense there. Also, there was a bit about Toshiba laptops I just had to guess at. I don't have either of these systems to test it on, so feel free to give feedback.

Problems with the modified patch should be directed to me, and not Nigel at suspend2.com. He knows I have been hacking on his patches, but I'm still responsible for any mess I've made of his code.

HOW TO:[LIST=1]
[*]Get the networking working properly, so that you can perform apt-get update.
[*]Start a terminal window from the menu, Applications->Accessories->Terminal
[*]Login as root
```
sudo -s
# enter password
```
[*]Install the kernel source and the tools to build it
```
apt-get -y install build-essential bin86 libncurses-dev alien
apt-get -y install linux-tree-2.6.12
cd /usr/src
```
[*]Download patched Suspend2
```
wget http://ubuntu.griffin3.com/software-suspend-2.1.9.9-for-2.6.12-ubuntu5.10.tar.bz2
wget http://www.suspend2.net/downloads/all/hibernate-1.12-1.i386.rpm
wget http://www.suspend2.net/downloads/all/suspend2-userui-0.5.1.tar.gz
```
[*]Unpack the lot
```
tar -xjf software-suspend-2.1.9.9-for-2.6.12-ubuntu5.10.tar.bz2
tar -zxf suspend2-userui-0.5.1.tar.gz
tar -xjf linux-source-2.6.12.tar.bz2
ln -s linux-source-2.6.12 linux
cd /usr/src/linux
```
[*]Install gcc-3.4 required by kernel
```
apt-get -y install gcc-3.4.5
CC=gcc-3.4
export CC
```
[*]Patch the kernel
```
cp /boot/config-2.6.12-9-386 .config
make oldconfig
../software-suspend-2.1.9.9-for-2.6.12-ubuntu5.10/apply
```
[*]Find your IDE chipset and swap partition--remember these
```
lspci | grep 'IDE'
fdisk -l | grep 'swap'
```
[*]Configure the kernel
```
make menuconfig
#    General setup --->
#        (-hibernate) Local version - append to kernel release
#    Power management options (ACPI, APM) --->
#        [ ]   Software Suspend (EXPERIMENTAL)
#        <*> Software Suspend 2 --->
#            <*> Swap Writer
#            (swap:/dev/hda3) Default resume device name
#    Device Drivers --->
#        ATA/ATAPI/MFM/RLL support --->
#            <*> ATA/ATAPI/MFM/RLL support
#            <*> Enhanced IDE/MFM/RLL disk/cdrom/tape/floppy support
#            <*> Include IDE/ATA-2 DISK support
#            <*> generic/default IDE chipset support
#===This will work, but speed is 5-7x faster with specific chipset support
#            <*> ALI M15x3 chipset support #===your IDE chipset
#    File systems --->
#        <*> Ext3 journalling file system support
#    Cryptographic options  --->
#        <*>   LZF compression algorithm
#===This is a good time to set the processor type, if desired [optional]
#    Processor type and features  --->
#        Processor family (Athlon/Duron/K7) #===your processor
```
[*]Install text-mode userui
```
cd /usr/src/suspend2-userui-0.5.1
make suspend2ui_text
cp -p suspend2ui_text /usr/local/sbin
```
[*]Install hibernate script and configure
```
cd /usr/src
alien -i hibernate-1.12-1.i386.rpm 
gedit /etc/hibernate/hibernate.conf
#    -> ImageSizeLimit nocache
#    -> ProcSetting expected_compression 50
# add-> ProcSetting userui_program /usr/local/sbin/suspend2ui_text
#    -> SwitchToTextMode no
```
[*]Set power button to hibernate
```
gedit /etc/acpi/events/powerbtn
#    -> action=/usr/sbin/hibernate
#    -> #action=/etc/acpi/powerbtn.sh
/etc/init.d/acpid restart
```
[*]Compile the kernel (get lunch now, takes about an hour on my AMD1700)
```
cd /usr/src/linux
make bzImage install modules modules_install
#cd /boot
#rm config vmlinuz System.map #optional: remove extra links, less clutter for grub
update-grub
```
[*]Read note below about restricted kernel modules, if you are using them: these include madwifi for wireless cards, fglrx for ATI video, and nVidia video cards
[*]Reboot to load the new kernel[/LIST]Pressing the power button should now cause hibernation! If the power button does not work on your laptop, in a terminal type:
```
sudo hibernate
``` 
After hibernating successfully, you can see some statistics by typing
```
sudo cat /proc/software_suspend/debug_info |grep 'compression\|speed'
``` In particular, if the disk read/write speed is about 5 MB/s or less, you probably do not have the correct IDE chipset driver installed, and are using the generic drivers. My speeds on this elderly eMachines laptop are ~35MB/s write, ~45MB/s read with the ALi drivers compiled into the kernel.

Most common failing is not getting all of the IDE drivers (and ext3 filesystem) compiled into the kernel during **make menuconfig**. If these are left out, the system will give a "Big Fat Error" on boot, or a "Kernel Panic". If you have to adjust any of these, the re-compile goes much faster, because it only has to compile the changes (step 14).

Any errors in the "patching the kernel" (step 8) are mine, and Nigel won't want to hear about them. I've tested this on the base Ubuntu kernel, without much added into it, and with the 386 and k7 switches applied. Errors on boot might be the result of missed steps (say, putting swap=/dev/hda3 instead of swap:/dev/hda3 in the Default resume device name, my personal nemesis). Looking through the mailing lists on suspend2 might be able to help, but we should be able to troubleshoot the Most Frequent Misteaks in this thread, check there first.

Finally, you might be tempted to install the fbsplash userui for suspend2. You are completely on your own there. It has been reported to completely gum up suspend-to-ram, and slow down the hibernation process greatly. The textmode is more trustworthy, and this eMachines 5309 with 512MB RAM hibernates in 6 seconds, and wakes in 8. It's not worth the instability for something that will just flash on the screen for 2/3 of that time; and anyway, that's why you prefer Ubuntu to Windows anyway, it doesn't hide the delicate inner workings of the system from you. Right? Right?

** NOTE re:** linux restricted modules
When you recompile the kernel, you can no longer use any of the Ubuntu linux-restricted-modules packages, so you will have to compile these on your own. These are best done before you reboot the computer, or something will be missing when it comes back up again. And if you do it this way, the modules will have the same internal version (-hibernate) as the kernel. I should be posting a HOWTO: for the madwifi here soon, because I had to do it myself.

---

### Post by naked on 2005-10-13
What benefit does this provide out of curiosity?

L

---

### Post by Griffin3 on 2005-10-14
Mostly benefit to laptop users, can suspend-to-disk when you turn off your laptop, and resume right where you left off (as opposed to desktop users who can simply leave their computer on.) I was addicted to this ability under Windows, one can save a snapshot of one's mental state to resume later, without having to think "where was I in what projects?" and "what web pages was I currently reading through?"

The built-in kernel suspend capability is not usable by as many machines, and is generally less configurable, as it expects hardware support for suspending computer state.

---

### Post by crobe on 2005-10-14
I am thinking of trying this later since hibernate mode is not functioning on my laptop.  I do have suspend to RAM (sleep mode) working, will doing this affect that?  Any drawbacks to not doing via hardware?  Either way it looks to be a well written guide and it'll fix my biggest problem with ubuntu on my laptop, so thanks ahead of time.

---

### Post by ajhobbs on 2005-10-14
Generally better to NOT set or enable a password for root.  Insteady you can use

```
sudo -s
```

Which gives you a root shell via sudo without a need of enabling root.

---

### Post by Griffin3 on 2005-10-14
crobe: one of the instructions in the HOWTO: specifically turns off the existing support for suspend-to-ram, that is:
```
make menuconfig
#        [ ]   Software Suspend (EXPERIMENTAL)
``` If you did not do this, the suspend-to-RAM should still be functional. I have never tested it that way; I just thought it would be better to not have any possible interference.

Let us know how it turns out.

---

### Post by chanders on 2005-10-18
If I am correct, doesn't Breezy now use gcc 4.0.1 or greater as the default compiler? Would setting CC to an earlier version of gcc cause any problems? Secondly, would this work if my filesystem is reiser?

I'll definitely want to give it a go!

Thanks

---

### Post by Griffin3 on 2005-10-18
Ubuntu does indeed use gcc4.0.2, but the kernel requires gcc 3.4 in order to compile. I believe that the 2.6.12 kernels were sort of a transition, they are possible to compile with gcc4 if you tweak them, but the standard way to do it is with gcc3.4. I think the 2.6.13 kernel comes ready to compile with gcc4. [http://ubuntuforums.org/showthread.php?t=75651]("http://ubuntuforums.org/showthread.php?t=75651") has some more information (but nothing very useful).

No problem if your filesystem is ReiserFS, except in the **make menuconfig** (step 10) make sure you mark ReiserFS as compiled into the kernel (instead of ext3). Since the suspend2 starts to restore the image right after the kernel loads, but before any modules or drivers, the filesystem support must be compiled into the kernel. If not, you get a "BIG FAT ERROR" on boot; I don't know if this is Nigel's humor, or someone on the kernel team ...

---

### Post by chanders on 2005-10-19
Great news, good news, not-so-good news....

Great news....
Firstly everything worked perfectly.... I absolutely love how fast this method works.... Clean and nice.....

Good news....
This was with the bundled nv driver which comes with Ubuntu. I would advise everyone with a laptop to install this.....

Not-so-good news....
I need to get hardware acceleration working. I recompiled the NVidia driver 7676 driver to work with the -hibernate driver. The driver works perfectly, except that suspend2 stops working.

I monitored what happens when the power button is pressed and I think when it comes to unloading the nvidia module it stops. Just for the heck of it I tried unloading the nvidia module from console 1 and I get 

            FATAL: Module nvidia is in use.

I did read on the suspend2.net wiki site that some people got it to work. it required them to do one aditional patch to the nv.c file...

            "Version 1.0.7676 needs this patch at line 3667"

however I cant find the nv.c file! Maybe you can give me some insight on this?  

In the mean time however the only way I can get it to work is by logging out of X, killing GDM and unloading module nvidia. Then I can hibernate....

I am sure there are hundreds of us who gave up on getting hibernate to work with the Nvidia driver on our laptops. I feel like we are so close, any input from anyone would be appreciated.....

---

### Post by hedge on 2005-10-19
Suspend2 has been a desire of mine since I found it at Suspend2.net. I'm currently running the 2.6.12-9-686-smp kernel. Your software-suspend-2.1.9.9-for-2.6.12-ubuntu5.10.tar.bz2 unfortunately is not for the kernel that I'm using. Do you have any suggestions for getting Suspend2 to work with the 2.6.12-9686-smp kernel? Maybe a list of the tweaks you made to the Suspend2 package?

TIA

hedge

---

### Post by chanders on 2005-10-19
Ok I got hibernate to work with the proprietory Nvidia driver..... This however does not allow you to press ctrl+alt+F1 to get to the console.

When you press ctrl+alt+F1 you get a garbled screen, but ctrl+alt+F7 works perfectly, so if you _only use X_ then I have found the solution for you...

Anyone interested please pm me....

---

### Post by Griffin3 on 2005-10-20
chanders: I hope I am not stating the obvious, but have you tried listing (and uncommenting) the nvidia modules in the /etc/hibernate/hibernate.conf file, where it says:
```
### modules
# UnloadModules snd_via82cxxx usb-ohci
...
LoadModules auto
```

I don't know if the nvidia module is one you can just unload like this, but maybe by putting it explicitly in this file (all these drivers are unloaded while still in X, before ss2 actually begins)

---

### Post by chanders on 2005-10-21
Thanks Griffin... I tried that before you even made the suggestion ;) Apparently the module cannot be unloaded while you have an X session running.

By commenting the module, the suspend process just bundles up everything without removing the module, and then shuts down the machine.

When it reboots however, all of my virtual consoles on F1 and F2 have a garbled screen, presumably because that text mode was not reinitialised on resume. The graphical mode (X) on F7 however works perfectly. I tried using vbetools to reinitialise the text mode on resume but that causes LCD burn...

It is a trade off between using the virtual consoles and having a working suspend to disk... 

Thanks again for your patch....

---

### Post by hedge on 2005-10-21
Hey Griffen3- I just got Suspend2 patched into a new 2.6.12-9-686-smp kernel using the swap writer yet I have a problem (lol, go figure!) When hibernating Suspend2 copies about 75% of the image then hangs.

Did you ever experience this? If so what was your tact to resolve this issue?

tia

hedge

---

### Post by blakken on 2005-10-22
I did exactly what you said point to point as I pasted the  commands and here is what I got :
 CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
kernel/built-in.o: In function `s2_compress_write_init':
compression.c:text+0x189cc: undefined reference to `get_next_filter'
compression.c:text+0x18a09: undefined reference to `bytes_out'
compression.c:text+0x18a13: undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_compress_write':
compression.c:text+0x18a3b: undefined reference to `bytes_out'
kernel/built-in.o: In function `s2_compress_write_chunk':
compression.c:text+0x18afa: undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_compress_read_init':
compression.c:text+0x18c3d: undefined reference to `get_next_filter'
kernel/built-in.o: In function `s2_compress_print_debug_stats':
compression.c:text+0x18ea5: undefined reference to `bytes_out'
compression.c:text+0x18eb5: undefined reference to `bytes_in'
compression.c:text+0x18ee6: undefined reference to `bytes_out'
compression.c:text+0x18eec: undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_compress_save_config_info':
compression.c:text+0x18f33: undefined reference to `bytes_in'
compression.c:text+0x18f43: undefined reference to `bytes_out'
kernel/built-in.o: In function `s2_compress_load_config_info':
compression.c:text+0x18f84: undefined reference to `bytes_in'
compression.ctext+0x18f8c: undefined reference to `bytes_out'
kernel/built-in.o: In function `s2_encrypt_write_init':
encryption.c:text+0x19195 undefined reference to `get_next_filter'
encryption.c:text+0x191e8 undefined reference to `bytes_out'
encryption.c:text+0x191f2: undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_encrypt_write_chunk':
encryption.c:text+0x19237: undefined reference to `bytes_in'
kernel/built-in.o: In function `s2_encrypt_read_init':
encryption.c:text+0x192cf): undefined reference to `get_next_filter'
kernel/built-in.o: In function `s2_compress_load':
compression.c.init.text+0xc8d): undefined reference to `suspend_register_plugin'
compression.c.init.text+0xca3): undefined reference to `suspend_register_procfile'
kernel/built-in.o: In function `s2_encrypt_load':
encryption.c.init.text+0xcd4 undefined reference to `suspend_register_plugin'
encryption.c.init.text+0xcea: undefined reference to `suspend_register_procfile'
make: *** [.tmp_vmlinux1] Error 1

What's the matter? :(

---

### Post by Mizzou_Engineer on 2005-10-22
This certainly does work. However, you must be sure to get *exactly* the right address for the swap device in the DEFAULT_RESUME_DEVICE field or you'll get a "BIG FAT ERROR" and have to continue booting the kernel all over.

You also must be sure to get your / filesystem type compiled into the kernel and not just a module. If you run Reiser you must compile Reiser in there, and it was not mentioned in there. Also, be sure to NOT use the nvidia or ATI drivers as these gum up suspend.

This is pretty dang fast- it goes down in about six seconds and comes up in about four. It also must not hurt that my IDE chipset was well-supported and I can write data at ~60MB/sec. Well done!

---

### Post by Mizzou_Engineer on 2005-10-22
Yeah, I *do* have one issue. When my display turns off via the power-management settings, I cannot "wake" it back up. This is running the custom -hibernate kernel after I have hibernated and resumed. 

Is there a work-around such as changing a line of the APCI or X config? Or should I just not have my laptop screen ever turn off (it's nice to have, but not nearly as important as the ability to suspend.)

---

### Post by munkymonkjr on 2005-10-23
griffin3, you're my hero :D 

for all those considering doing this how-to:
my advice : DO IT! so worth it. couple this with a usplash in custom kernel so you're not at a loss with eye candy, and you're in business

difficulty: medium
time: ~1h (took about 40 min or so on my AMD64 3200+)

griffin, although the instructions overall were understandable, there are some bits and pieces that took me a while to realize. lol, maybe its just me.

---

### Post by art on 2005-10-23
Well, I think I can say the suspend just doesn't work on Toshiba Satellite A65. I have tried a lot before , now I tried with griffin's suggestions, still no go, although I think I got a little further. Maybe someone can help me out here, which will make me a really happy person. The text after I type hibernate shows it saves all the needed info, then it sais Powering Down, and that's it... It stays there forever. If I press the power button, and boot back, I get a nonresposive gnome:( I tried with minimalistic environment as well, without any modules loaded, still hangs... Please, any suggestions... This is almost the last thing I don't have working on Ubuntu.
Thanks a lot

---

### Post by gillion on 2005-10-23
What advantage does Suspend2 on breezy provide over the default suspend to disk/hibernate function ?

---

### Post by art on 2005-10-24
Well in my case the default doesn't work, so this is I guess is the only hope, but if the default works, then I don't think you would want suspen2...

---

### Post by Griffin3 on 2005-10-24
Hello!  Had a long weekend that was very much like a vacation.  Maybe because I was away from the computer the whole time :cool:

art: The suspend2 has some toshiba-specific code in it that I could not make heads nor tails of when I was hacking the patch to fit the ubuntu files. But looking through the suspend2 mailing lists, it does not look like they have very good support for the toshibas yet. A lot of the name-brand laptops have started writing windows-specific BIOS routines for their power-management functions, and I think Toshiba is one of the worst at compliance with the standards that make linux programming easy. You might have better luck with the 2.2 suspend patch and a newest (2.6.14?) kernel, but then you lose all of the Ubuntu custom patches.

gillion: The built-in kernel suspend functions are still using the old, original codebase, and a lot of machines are not supported by this. A lot of standard, generic computers work fine, but the laptops which are least likely to use standardardized parts and BIOS are the ones that tend not to work with the built-in suspend. In addition, the suspend2 code works somewhat faster, has more feature, and compresses the image it writes to the disk (but I would not upgrade for these reasons, unless you really needed a particular feature.)

hedge: If the suspend is running about 75% and then failing, it sounds like it is writing all the caches and user-space code to the disk, and then failing on the atomic write of the kernel image. This likely has more to do with the parts of the patch I edited to work with the ubuntu, rather than the suspend2 code itself. Let me take a look at this, and see if I might find any obvious bonehead mistakes.

[Just in case anyone was wondering, most of the patches to the patches that I made were because of duplication, not me re-writing code. For instance, the patch to the Bernard-44 subsytem would not apply, because the Ubuntu people had already applied this patch, so I just removed the duplicate. On the smp and toshiba laptop stuff, I take full responsibility for the bugs.]

---

### Post by Griffin3 on 2005-10-24
Mizzou Engineer: I imagine when you turn off the old "Software Suspend" in the **make menuconfig** step it removes the hook for the wake-up call.  You *might* want to try re-compiling the kernel with this truned back on, and just be wary of conflicts between the two suspend methods.  If it was my machine, I would just disable the screen shutdown, or pick a black screen-saver (though, IIRC, black pixels consume the most power by a small fraction)

---

### Post by Griffin3 on 2005-10-24
I misplaced who was having the difficulty with running Suspend2 on LVM, due to overagressive deleting of messages :oops:; but there is a great how-to on Nigel's site at [http://www.suspend2.net/HOWTO-7.html#ss7.3](http://www.suspend2.net/HOWTO-7.html#ss7.3) -- apparently you need to use an initrd to run Suspend2 with LVM.

---

### Post by art on 2005-10-24
Yeah, I am afraid at this point I should juts give up on the hope of getting this to work... Thanks a lot though!

---

### Post by Abnaxos on 2005-10-24
[QUOTE=Griffin3]hedge: If the suspend is running about 75% and then failing, it sounds like it is writing all the caches and user-space code to the disk, and then failing on the atomic write of the kernel image. This likely has more to do with the parts of the patch I edited to work with the ubuntu, rather than the suspend2 code itself. Let me take a look at this, and see if I might find any obvious bonehead mistakes.[/QUOTE]

I had the same effect on a Dell Inspiron 5160 (SMP/Hyperthreading), that's when I first gave up. Now, I just tried it with a vanilla 2.6.13 kernel and the latest stable Suspend2. It still happened and with the current Version, you can also see the message saying that it's doing the atomic write. Actually, this only happens about 90% of the times, if it *does* get to the shutdown, it'll hang loading the kernel image, however.

Anyway, it doesn't seem to be a problem with your tweaks.

---

### Post by Griffin3 on 2005-10-24
[quote=Abnaxos]I had the same effect on a Dell Inspiron 5160 (SMP/Hyperthreading), that's when I first gave up. Now, I just tried it with a vanilla 2.6.13 kernel and the latest stable Suspend2. It still happened and with the current Version, you can also see the message saying that it's doing the atomic write. Actually, this only happens about 90% of the times, if it *does* get to the shutdown, it'll hang loading the kernel image, however.

Anyway, it doesn't seem to be a problem with your tweaks.[/quote]

Thanks for the info (validation).  I also suspect the code in there for clustered computers; if they are having trouble getting SMP machines to work, then I can't imagine they have a handle on a cluster yet.

---

### Post by hedge on 2005-10-24
[quote=Griffin3]Thanks for the info (validation). I also suspect the code in there for clustered computers; if they are having trouble getting SMP machines to work, then I can't imagine they have a handle on a cluster yet.[/quote]

When I was trying to get Suspend2 to work in Fedora this site has precompiled kernels that did support smp with Suspend2 from what I recall.. > [http://mhensler.de/swsusp/](http://mhensler.de/swsusp/) 

hedge

---

### Post by gmc on 2005-10-25
[QUOTE=Griffin3]art: The suspend2 has some toshiba-specific code in it that I could not make heads nor tails of when I was hacking the patch to fit the ubuntu files. But looking through the suspend2 mailing lists, it does not look like they have very good support for the toshibas yet. A lot of the name-brand laptops have started writing windows-specific BIOS routines for their power-management functions, and I think Toshiba is one of the worst at compliance with the standards that make linux programming easy. You might have better luck with the 2.2 suspend patch and a newest (2.6.14?) kernel, but then you lose all of the Ubuntu custom patches.
[/QUOTE]

Your HOWTO works perfectly with a Toshiba Satellite Pro 4600. It's an older Toshiba laptop (P3/750), circa 2001. I do have one question though? Is there a step missing for applying Ubuntu's kernel patches or are they already included in the 2.6.12 kernel source that (we) apt-get installed.

G.

---

### Post by Griffin3 on 2005-10-25
The Ubuntu patches are already applied in the linux-tree kernel source that you apt-get.  What is not already in there is the restricted modules, that are available in binary-only form, like the nvidia and madwifi drivers.

---

### Post by gmc on 2005-10-25
[QUOTE=Griffin3]The Ubuntu patches are already applied in the linux-tree kernel source that you apt-get.  What is not already in there is the restricted modules, that are available in binary-only form, like the nvidia and madwifi drivers.[/QUOTE]

Whoa, that was quick. Thanks Griffin3.

G.

---

### Post by prof.morbius on 2005-10-25
OK, I jumped to Ubuntu from Gentoo because I was tired of having to recompile my kernel when I discovered that I'd forgotten something, only to discover that the new options broke something that had been working.

So, my question is this: is there an unstable precompiled kernel I can use with my Dell Latitude D800, or would it work to activate the binary-only nVidia drivers instead of agpart (loading now) with the current suspend version?

Apropos the second part of that question, I was going to try this, but I can't find where agpart is being loaded.  It doesn't seem to be in /etc/X11/xorg.conf, nor is it in /etc/modules.  Would this change work, and if so, how is agpart being loaded (so I can replace it with nvidia-agp and nvidia)?

Thanks in advance,
Kevin

---

### Post by hedge on 2005-10-25
your looking for this lil process to get the nvidia drivers to work correctly with Suspend2: [http://ubuntuforums.org/showthread.php?t=79295](http://ubuntuforums.org/showthread.php?t=79295)

---

### Post by Abnaxos on 2005-10-26
[QUOTE=hedge]When I was trying to get Suspend2 to work in Fedora this site has precompiled kernels that did support smp with Suspend2 from what I recall.. > [http://mhensler.de/swsusp/](http://mhensler.de/swsusp/)[/QUOTE]

I myself had it working, too, about half a year ago on Debian. I've just tried a non-SMP kernel, just to see what happens. Without SMP, it worked like a charm (I suspended/resumed 3 times). It really looks like the SMP code is broken again.

---

### Post by benguin on 2005-10-29
Hi there,
First a big thanks to Griffin3 for the howto. I'm posting this to report my experience with swsups2 on a HP Pavilion ZX5000 Laptop. I did not buy this machine (got to use it from work); it has a pentium 4 3.2 GHz CPU which is not a mobile processor. The thing gets pretty darn hot too, and uses Broadcom wireless chipsets. In short, not very linux friendly. 

I wanted to try swsup2 since the default hibernate or suspend methods did not work for me. Now that said, Griffin3's howto on suspend2 almost worked, except I was having trouble making the thing hibernate. At around 80%, it would freeze at 'Doing atomic copy' and that would be it. After some googling around and some forum searching, I decided to append the '**noapic**' option to the kernel command line (/boot/grub/menu.lst). Voila! That made hibernation a reality. I was pretty happy with it, but then my sound went to hell (ATI IXP chipset). Scratching my head, I decided to try '**irqpoll**' in addition to 'noapic' kernel option. Double voila!! that fixed the sound. I was in power saving heaven-- running p4_clockmod to scale my cpu frequency, software suspend to never shut down my machine-- it was awesome. Then I hit another rock-- DVD burning stopped working. I tried nautilus-cd-burner, gnomebaker, graveman-- nothing would work. The failure? Nautilus would say, 'cannot write DVD, an unhandled error has occurred!' The other software gave something like that as well, nothing specific at all. To test if it was my kernel (and options I'm passing) I tried burning a DVD booting from the default breezy i686 kernel, and gnomebaker worked. 

So what am I looking for? Is there any kernel option that'll help me retain suspend2 capability, without screwing up DVD burning and audio? Or is it something I have to build into the kernel itself?

I really enjoy the swsups2 feature. Helps me keep working on stuff for a longer time without interruption. I do not have a second computer now: this laptop is my work/home/media-center machine.

Oh yeah, and it's got windows too, which I run once every... umm.. year?

Thanks again!

-J-

---

### Post by Nigel_C on 2005-10-29
Hi all.

I'm the developer of the Suspend2 patches.

Suspend2 does work with SMP and has done since the start of last year. Freezes part way through reading or writing the image are almost always due to driver issues, including things like APIC controllers. They're often specific to particular chipsets and/or configurations, so very hard for me to reproduce and debug. The best thing you can do is try to compile as minimal a kernel as possible, unload all modules (or as many as possible) and see if that works. Then add bits back until something can be identified as breaking things.

Regarding the in kernel implementation vs suspend2, if one works on a system, the other should. There are a huge number of differences, but the basic operation is exactly the same. If swsusp (the in-vanilla version) works and Suspend2 doesn't (same config otherwise), it's a bug I need to address. If Suspend2 works, swsusp should too.

Hope this helps,

Nigel

---

### Post by hedge on 2005-10-29
Benguin,

Have a few questions regarding your HP's configuration. does #dmesg (from a terminal) reflect that you have both Cpu0 and Cpu1?

And secondly, if you run # lspci | grep 'IDE' (from a terminal also) what chipset does it identify?

thx

hedge

---

### Post by benguin on 2005-10-29
Hi Hedge,
I am not running an SMP kernel, inspite of the CPU being HT. I tried the default breezy SMP kernel and performance was poor (slow). The IDE chipset is ATI IXP. This is the lspci output:

0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349

Cheers,
-J-

---

### Post by monotux on 2005-10-29
Is there any way to make gnome use suspend2 instead of whatever it uses now (when I select "Hibernate this computer" in the logout menu)?
That would be really, really great!

---

### Post by Abnaxos on 2005-10-30
[QUOTE=Nigel_C]Suspend2 does work with SMP and has done since the start of last year. Freezes part way through reading or writing the image are almost always due to driver issues, including things like APIC controllers.[/quote] Well, you're most probably right. It's still a pity. What happened? About half a year ago, with Debian Sarge, I had it. It worked perfectly. With SMP, nVidia and everything. Then I switched to Ubuntu. The patch didn't apply, so gave up. Then I found this thread, applied the patch and tried. I did many experiments including using vanilla kernels and several combinations of how to compile the kernel and booting them with many combinations of many arguments. No way, it would freeze during the atomic write. What happened? I mean, it's still the same machine? Suspend2 *used* to work *perfectly* on the *same* machine, and that's not such a long time ago. And the experiments I had to do back then were about the nVidia driver, now it'll even hang in single user mode with "exit 0" inserted as the first line of /etc/init.d/hotplug. (Not to mention: if I disable SMP, it'll work, back to X, using the nVidia driver and intel_agp, fully booted machine as installed by default by the Ubuntu installer, not even switching the nVidia driver to it's own AGP implementation, as suggested in another HOWTO).

So, for *my* machine, something very profound must have changed since then, and it must have something to do with SMP ... ;)

---

### Post by lerrup on 2005-10-31
Will this patch work on a 686 optimised kernel; and if it does is there anything special I need to do?

Also, should I reverse the changes I have made already following the HoaryPM wiki site and the nvidia suspend site?

Thanks.

---

### Post by Griffin3 on 2005-10-31
If you follow the steps in the how-to, when you are in the **make menuconfig** step (10) you can go up to Processor Type and select the optimization there.  I used k7 optimization, but did not include that in a "general" tutorial; should work fine.  

If you have previously made changes to the kernel, the patch may not apply.  I've only tested it with the linux-tree-2.6.12.  It might apply to a kernel prepatched with other minor changes, but as soon as one of those changes conflicts with a suspend2 patch, the suspend2 patch will fail to apply (and have to be hand-patched).

Following these instructions will break Ubuntu's nvidia video driver support, but one of the posts details the workaround for this.  I'm thankful someone else posted it, because I only have so much hardware here, and am fresh out of nvidia machines.

---

### Post by lerrup on 2005-11-02
I'm getting the following error "Big Fat Warning failed to translate device name into device id"

I've looked at the suspend2 FAQ and it comes down either to my mistake in compiling the kernel with the device name (very likely) or modules.

Can you confirm that the format you gave for the name is correct (I guess it is) and also how I delete the old Kernel to start again?

I had another go and got the same problem - aaarrrgggghhhh.  For some reason it doesn't want to remember this.  The kernel works apart from this and gives me a workable system

I also now have 2 kernels that I need to manually delete somehow.  How do I do this; I can't find anything about this as no one on the www seems to be worry about this as an issue.

Cheers!

---

### Post by Griffin3 on 2005-11-02
Device name for the swap drive should be likeswap:/dev/hda3--although, the swap device is not likely to be the sameplace on your machine. To see where your swap partition is, type in aroot terminal:
```
cat /proc/swaps
```
 
Also, make sure that the low-level IDE drivers, everything in the **make menuconfig**step is marked as (*) for compiled into the kernel, not (M) for buildasmodules. In addition, if you are not using the ext3 filesystem thatUbuntu defaults to, you need the driver for your filesystem alsocompiled into the kernel. If you are using ext3 filesystem, the ext2that it depends on must also be compiled in (although I do not know ifit is possible to disable this.)
 
 
Finally, in order to delete old, nasty, unused kernels:
```
sudo -s
cd /boot
ls
rm [all the unused kernels, the configs that match, and the system.maps]
update-grub
```
 
**WARNING: **do not delete all the kernels except for the oneyouare testing: make sure you keep at least one untouched, virginal,sure-to-be-working kernel, like the original -386 kernel that Ubuntuinstalled. Deleting this file will cause the spirits of malevolentbugness to infest your remaining experimental kernel, and cause it tocrash, even if it has performed flawlessly for thousands of previousboots. I found this out the hard way; it has something to do with theescaped chicken spirits.

---

### Post by lerrup on 2005-11-02
thanks, I'll watch out for the chicken spirits.

---

### Post by hastour on 2005-11-06
Hi,
I've got this suspend thing working, but it stopped after a few days, without any apparent reason.

I typed sudo hibernate and it said something about being unable to unload modules from a black list. Then, without really knowing what I was doing, I commented out "UnloadBlacklistedModules yes" from the config and it helped somehow, sudo hibernate works again. But it no longer works with a power button, only from console, which is an annoying step backwards. Any idea how to get the button working again? 

Oh, and besides, I'm a new guy to ubuntu and this forum, so hello everyone, and, just in case, sorry for my english.

---

### Post by russelld on 2005-11-06
suspend2 is not restoring the keyboard in this Acer 3002WLC!
So it's stuck with a mouse-touchpad only. 
This is similar to the frozen keyboard/mouse I got with regular ubuntu suspend.
[http://www.ubuntuforums.org/showthread.php?t=86491]("http://www.ubuntuforums.org/showthread.php?t=86491")
 
Also when a sleep (suspend to ram) is done, the restore brings up the login properly, but then proceeds to do a suspend2 to disk.  blimey.....:confused:

---

### Post by jrbeaton on 2005-11-06
I'm running 5.10 on an HP ZD7000.  I was able to get Suspend2 working (thanks!), but...

When I return from suspend, my Synaptics touchpad no longer scrolls or does tap-n-drag.  Also, the scroll wheel on my Logitech USB Optical Mouse stops working.

Before the first suspend, both the touchpad and the mouse work great.  After resuming, not so much...

Any ideas?


Thanks,
JRB

---

### Post by russelld on 2005-11-07
[QUOTE=russelld]suspend2 is not restoring the keyboard in this Acer 3002WLC..........snip..................................
Also when a sleep (suspend to ram) is done, the restore brings up the login properly, but then proceeds to do a suspend2 to disk.[/QUOTE]

This is still happening even after compiling mouse/touchpad and keyboard into kernel.  Except even stranger.  

Hibernate from prompt will send laptop into hibernation ~10secs.  When its restarted the gui reappears in ~1 min, with a frozen keyboard.  From here it can be supended into ram frome gnome log-in applet.

Then it gets interesting.  Using the touchpad the laptop can be made to sleep, via the gnome log-out applet. 

When suspend from gnome log-out applet is actioned, the laptop goes down into sleep.  When its woken with a keypress, it then wakes up and goes into hibernate via suspend2.  Bit only for about 5 seconds, it then reboots and restores the gui and has the prompt with keyboard and touchpad working.  Which is what is wanted, though a little long winded.  This also happens after a clean reboot.

Chicken spirits?   sounds like just a bunch of naughty script spirits!  ;)

---

### Post by hastour on 2005-11-07
I've got the same issue - it hibernates right after waking up from suspend to ram...

---

### Post by russelld on 2005-11-08
Overnight things have got better!

I disconnected the laptop over night from the mains power, then suspend2 works like its supposed to.  Totally caught me by surprise!  :p :p 

Did it again this morning, and pulled the power cable out from the laptop for 30 mins.  Again the same result.  If I did a restore too soon or still had the power connected, the keyboard froze.  Then the only way out was to suspend to ram and restore to get keyboard working.  Though this is not 100% reliable and occasionally have to hard reboot.

This hasn't been tested with battery as it really gets to run on mains power.

However, the recompiling both the keyboard and touchpad into the kernell has stuffed the sound, so I'm going back to the original suspend2 compile and will know tomorrow.

results:
# cat /proc/software_suspend/debug_info |grep 'compression\|speed'
- Overall expected compression percentage: 50.
Compressed 674312192 bytes into 302692897 (55 percent compression).
- I/O speed: Write 61 MB/s, Read 59 MB/s.
 
It took around 12s to suspend and around 45s to restore.  
 
Leaving me a very happy chappy :D

---

### Post by rabeldable on 2005-11-08
I have the hinernate problem and the following describes my situation:

I just (last night) installed 5.10 on a Toshiba M65-S9065.  First let me commend the ubuntu community.  This OS is a real nice piece of work and is very feature full.  I had a problem with my X display but I got through it.  My hibernate problem happens when I try to wake up the system.  The system boots back up and reads the saved file from disk.  It actually uncompresses and the OS tries to come online, however, X fails.  What I suspect is my gdm driver is reloaded and the 915resolution display attributes that I need to specify at boot are not saved with the rest of the OS.  It appears that some modules are loaded and some of them are saved as loaded.  I wonder if there is a special start script directory or config file that I could use to re-load my 915resolution values prior to gdm loading.

Thanks, 
David

---

### Post by russelld on 2005-11-08
[QUOTE=russelld]However, the recompiling both the keyboard and touchpad into the kernell has stuffed the sound, so I'm going back to the original suspend2 compile and will know tomorrow.
[/QUOTE]

Sound worked after killing shuting down some roge processes.
So it was due to too many processes graping at the sound and nothing to do with the kernel compile.

And suspend2 worked again this morning after been disconnected from mains power overnight.  

So this is good! reliable suspend!  Thanks Griffin3!  :cool:

---

### Post by El Cris on 2005-11-08
My computer hibernates succesfully but doesn't resume. It's just booting up normally. Any suggestions?
As I don't know what logs to post or what informations could be useful I only quote my hibernation.log. If you need some other logs, just ask for it.
In the log there are some entries about suspend being aborted. This happens regurlarly. When I reboot after that, it's then suspending as expected.
> ...
Starting suspend at Wed Nov 9 01:06:44 CET 2005
hibernate: [01] Executing CheckLastResume ...
hibernate: [01] Executing LockFileGet ...
hibernate: [01] Executing NewKernelFileCheck ...
hibernate: [10] Executing EnsureSwsusp2Capable ...
hibernate: [89] Executing SaveKernelModprobe ...
hibernate: [91] Executing ModulesUnloadBlacklist ...
hibernate: [97] Executing ChangeToSwsuspVT ...
hibernate: [98] Executing Swsusp2ConfigSet ...
hibernate: [99] Executing DoSwsusp2 ...
hibernate: Activating suspend ...
hibernate: [97] Executing ChangeFromSwsuspVT ...
hibernate: Suspend reported the following errors:
 - Suspend was aborted by user (see dmesg if unexpected).
hibernate: [90] Executing ModulesLoad ...
hibernate: [89] Executing RestoreKernelModprobe ...
hibernate: [70] Executing ClockRestore ...
hibernate: [01] Executing NoteLastResume ...
hibernate: [01] Executing LockFilePut ...
hibernate: [00] Executing RemoveSwsuspProcCruft ...
Resumed at Wed Nov 9 01:06:47 CET 2005
Starting suspend at Mi Nov 9 01:06:53 CET 2005
hibernate: [01] Executing CheckLastResume ...
hibernate: [01] Executing LockFileGet ...
hibernate: [01] Executing NewKernelFileCheck ...
hibernate: [10] Executing EnsureSwsusp2Capable ...
hibernate: [89] Executing SaveKernelModprobe ...
hibernate: [91] Executing ModulesUnloadBlacklist ...
hibernate: [97] Executing ChangeToSwsuspVT ...
hibernate: [98] Executing Swsusp2ConfigSet ...
hibernate: [99] Executing DoSwsusp2 ...
hibernate: Activating suspend ...
hibernate: [97] Executing ChangeFromSwsuspVT ...
hibernate: Suspend reported the following errors:
 - Suspend was aborted by user (see dmesg if unexpected).
hibernate: [90] Executing ModulesLoad ...
hibernate: [89] Executing RestoreKernelModprobe ...
hibernate: [70] Executing ClockRestore ...
hibernate: [01] Executing NoteLastResume ...
hibernate: [01] Executing LockFilePut ...
hibernate: [00] Executing RemoveSwsuspProcCruft ...
Resumed at Mi Nov 9 01:06:56 CET 2005
Starting suspend at Wed Nov 9 01:25:37 CET 2005
hibernate: [01] Executing CheckLastResume ...
hibernate: [01] Executing LockFileGet ...
hibernate: [01] Executing NewKernelFileCheck ...
hibernate: [10] Executing EnsureSwsusp2Capable ...
hibernate: [89] Executing SaveKernelModprobe ...
hibernate: [91] Executing ModulesUnloadBlacklist ...
hibernate: [97] Executing ChangeToSwsuspVT ...
hibernate: [98] Executing Swsusp2ConfigSet ...
hibernate: [99] Executing DoSwsusp2 ...
hibernate: Activating suspend ...
chris@blackjack:~$                              

---

### Post by russelld on 2005-11-08
Have you checked that the kernel can see where the swap file is?

I had to edit the kernel options in  /boot/grub/menu.lst to point the kernel to where the suspend2 file was.  The kernel had the swap file option for suspend2 compiled in, and it needed the extra kernel option at bootup to make it work. (?)
The kernel option is documented here at the suspend2 home page [http://www.suspend2.net/HOWTO-4.html]("http://www.suspend2.net/HOWTO-4.html")

To do this: 
log into a console as root.
edit /boot/grub/menu.lst
go to line 62 where the kernel options are and add
resume2=/dev/"location of your swap partition"
 
eg my swap partition is in /dev/hda5

```

# kopt=root=/dev/hda2 resume2=/dev/hda5 ro

```

then run (as root) update-grub

reboot and test the new setup.

---

### Post by kaamos on 2005-11-08
Thanks for the howto!

Works (almost) great. Sometimes when the state is resumed the mouse isn't responding at all. Is there a way to prevent this or a way to fix it when it occurs?

Also the write speed is low.. The ide shows:
```
0000:00:07.1 IDE interface: Intel Corp. 82440MX EIDE Controller

``` Does anyone know what would be the best option for this in config?

This has again brought the linux-laptop-experience to a new level. :)

---

### Post by jrbeaton on 2005-11-09
To answer my own question...

Thanks to help from **hedge**, I was able to get this working by adding a few lines to my hibernate.conf:

```

UnloadModules psmouse

StopServices bluez-utils pcmcia
StartServices bluez-utils pcmcia

```


[QUOTE=jrbeaton]I'm running 5.10 on an HP ZD7000.  I was able to get Suspend2 working (thanks!), but...

When I return from suspend, my Synaptics touchpad no longer scrolls or does tap-n-drag.  Also, the scroll wheel on my Logitech USB Optical Mouse stops working.

Before the first suspend, both the touchpad and the mouse work great.  After resuming, not so much...

Any ideas?


Thanks,
JRB[/QUOTE]

---

### Post by El Cris on 2005-11-10
Even with resume2=/dev/hda5 (which is my swap-partition) my PC doesn't resume after suspend. This is really strange, because it's suspending with no error. At least in the suspend2ui_text-program it reaches 100% and then it's powering down.

---

### Post by hedge on 2005-11-10
[quote=El Cris]Even with resume2=/dev/hda5 (which is my swap-partition) my PC doesn't resume after suspend. This is really strange, because it's suspending with no error. At least in the suspend2ui_text-program it reaches 100% and then it's powering down.[/quote]

Set verbrosity 1 in your hibernate.conf and then run a bug report. As root hibernate --bug-report > file1.txt
And email me a copy of it and your hibernate.conf

hedge

---

### Post by El Cris on 2005-11-10
[QUOTE=hedge]Set verbrosity 1 in your hibernate.conf and then run a bug report. As root hibernate --bug-report > file1.txt
And email me a copy of it and your hibernate.conf

hedge[/QUOTE]

Email sent. For all others being interested in my "hibernate --bug-report" and hibernate.conf, there it is:
[http://bhm.kicks-ass.net/files/hibernate_bug-report.tgz](http://bhm.kicks-ass.net/files/hibernate_bug-report.tgz)

---

### Post by El Cris on 2005-11-10
Ok, so far i noticed that my swap-partition seems to be broken after every failed resume (remember: suspending seems to work fine, only resume fails completely). Why I think that it's broken? Well, trying to swapon my /dev/hda5 gives me an error. When I do mkswap /dev/hda5 I'm able to swapon that partition with no error again.

[UPDATE]:
Ooooh boy, now its working so far for me. I noticed that I hadn't created an initrd but an initramfs. I just succeeded resuming from suspend.
It threw me a BIG FAT ERROR saying that my initrd is misconfigured or something else but thats probably just a script in /etc/mkinitrd/scripts/ I've put there before creating it. That was a tip somewhere I've read. I'll create a new initrd and try resuming than.

[UPDATE2]:
strange:
> Nov 10 23:42:11 localhost kernel: [4294674.870000] === Software Suspend ===
Nov 10 23:42:11 localhost kernel: [4294674.870000]
Nov 10 23:42:11 localhost kernel: [4294674.870000] BIG FAT WARNING!! Initrd not properly configured for resuming.
Nov 10 23:42:11 localhost kernel: [4294674.870000]
Nov 10 23:42:11 localhost kernel: [4294674.870000] If you want to use the current suspend image, reboot and try
Nov 10 23:42:11 localhost kernel: [4294674.870000] again with the same kernel that you suspended from. If you want
Nov 10 23:42:11 localhost kernel: [4294674.870000] to forget that image, continue and the image will be erased.
Nov 10 23:42:11 localhost kernel: [4294674.870000] Press SPACE to reboot or C to continue booting with this kernel
Nov 10 23:42:11 localhost kernel: [4294674.870000]
Nov 10 23:42:11 localhost kernel: [4294674.870000] Default action if you don't select one in 25 seconds is: continue booting.
Nov 10 23:42:11 localhost kernel: [4294675.050000] input: AT Translated Set 2 keyboard on isa0060/serio0
Nov 10 23:42:11 localhost kernel: [4294682.292000] Freeing unused kernel memory: 144k freed
Nov 10 23:42:11 localhost kernel: [4294682.305000] ACPI: Fan [FAN] (on)
Nov 10 23:42:11 localhost kernel: [4294682.310000] ACPI: CPU0 (power states: C1[C1])
Nov 10 23:42:11 localhost kernel: [4294682.311000] ACPI: Thermal Zone [THRM] (68 C)
Nov 10 23:42:11 localhost kernel: [4294682.321000] NET: Registered protocol family 1
Nov 10 23:42:11 localhost kernel: [4294682.321000] Resume block device is dffe0040.
Nov 10 23:42:11 localhost kernel: [4294682.329000] Software Suspend 2.1.9.9: Swapwriter: Signature found.
Nov 10 23:42:11 localhost kernel: [4294682.329000] Software Suspend 2.1.9.9: Suspending enabled.

Suspend succeeded here, but it's always showing the above BIG FAT WARNING. Funnily it says to hit C to "forget that image, continue and the image will be erased". But just after hitting C it's resuming. Well, no problem for me, but how can I get rid of that BIG FAT WARNING cause I don't want to hit C always or wait the 25seconds.

---

### Post by mariner09 on 2005-11-11
Griffin3,

Thanks for the pointers...

I did get suspend2 installed and working with a vanilla 2.6.14.1 kernel.

The 2.6.12 kernel compilation following your tips worked once and never again as I forgot to edit the Makefile for my extraversion on the 1st run.  Segfaults at random points.  The vanilla kernel had no issues.

I also have the new madwifi-ng code compiled in as well.

Now, I've used suspend2 on a few distros, most notably, RHEL and FC.  It's usually very fast.

This is not.  About 2+ minutes to suspend and 3-4 minutes to resume.

Can you explain why you recommended the modifications to hibernate.conf that you listed in your 1st post?

Any thoughts on how one might speed things up?

Here's my hibernate.conf:

# Example hibernate.conf file. Adapt to your own tastes.
# Options are not case sensitive.
# 
# Run "hibernate -h" for help on the configuration items.

##############################################################################
### Choose your Suspend method. You currently have 3 choices:
###
###    suspend2            Software Suspend 2 (requires kernel patches from
###                        [http://www.suspend2.net/](http://www.suspend2.net/))
###
###    sysfs_power_state   Uses /sys/power/state to suspend (activates pmdisk
###                        on kernels < 2.6.8, or vanilla swsusp otherwise).
###
###    acpi_sleep          Uses /proc/acpi/sleep to activate swsusp, or other
###                        ACPI sleep state supported by your machine.
###
##############################################################################

### suspend2 (for Software Suspend 2)
UseSuspend2 yes
Reboot no
EnableEscape yes
DefaultConsoleLevel 1
Compressor lzf
Encryptor none
ImageSizeLimit nocache
## useful for initrd usage:
SuspendDevice swap:/dev/hda3
## Powerdown method - 3 for suspend-to-RAM, 4 for ACPI S4 sleep, 5 for poweroff
# PowerdownMethod 5
## Any other /proc/software_suspend setting can be set like so:
ProcSetting expected_compression 50
## Or traditionally like this:
# Suspend2AllSettings 0 0 2056 65535 5
## Or even from the results of hibernate --save-settings with this:
# Suspend2AllSettingsFile /etc/hibernate/suspend-settings.conf
## For filewriter:
# FilewriterLocation /suspend_file 1000
# VerifyFilewriterResume2 yes
ProcSetting userui_program /usr/local/sbin/suspend2ui_text

### sysfs_power_state
## To use /sys/power/state to suspend your machine (which may offer
## suspend-to-RAM, suspend-to-disk, standby, etc) comment out all the options
## above for Software Suspend 2, below for acpi_sleep, and uncomment this line.
## You may replace mem with any one of the states from "cat /sys/power/state"
# UseSysfsPowerState mem
# PowerdownMethod shutdown

### acpi_sleep
## To use ACPI to suspend your machine (via /proc/acpi/sleep), comment out
## all the options above for Software Suspend 2 and sysfs, and uncomment this
## line. The number refers to the ACPI sleep state - 3 is suspend-to-RAM and
## 4 is suspend-to-disk.
# UseACPISleep 4

##############################################################################
### Some global settings
##############################################################################

Verbosity 0
LogFile /var/log/hibernate.log
LogVerbosity 1
# AlwaysForce yes
# AlwaysKill yes
# HibernateVT 15
# Distribution debian (or fedora/gentoo/mandrake/redhat/slackware/suse)
# XDisplay :0

##############################################################################
### Scriptlets
###   Scriptlets provide support for doing all sorts of things before and after
###   suspending. The defaults settings here should work for most people, but
###   you may wish to edit these to taste. Consult "hibernate -h" for help on
###   the configuration settings.
##############################################################################

### bootsplash
## If you use bootsplash, also enabling SwitchToTextMode is recommended if
## you use X, otherwise you may end up with a garbled X display.
# Bootsplash on
# BootsplashConfig /etc/bootsplash/default/config/bootsplash-1024x768.cfg

### clock
SaveClock restore-only

### devices
# IncompatibleDevices /dev/dsp /dev/video*

### diskcache
# DisableWriteCacheOn /dev/hda

### fbsplash (enable SwitchToTextMode if you use this)
# FBSplash on
# FBSplashTheme suspend2

### filesystems
# Unmount /nfsshare /windows /mnt/sambaserver
# UnmountFSTypes smbfs nfs
# UnmountGraceTime 1
# Mount /windows

### grub
# ChangeGrubMenu yes
# GrubMenuFile /boot/grub/menu.lst
# AlternateGrubMenuFile /boot/grub/menu-suspended.lst
# BackupGrubMenuFile /boot/grub/menu.lst.hibernate.bak

### hardware_tweaks
# IbmAcpi yes
# RadeonTool yes

### lilo
# EnsureLILOResumes yes

### lock (generally you only want one of the following options)
# LockConsoleAs root
# LockXScreenSaver yes
# LockKDE yes
# LockXLock yes
# LockXAutoLock yes

### misclaunch
# OnSuspend 20 echo "Good night!"
# OnResume 20 echo "Good morning!"

### modules
# UnloadModules snd_via82cxxx usb-ohci
# UnloadAllModules yes
UnloadBlacklistedModules yes
LoadModules auto
# LoadModulesFromFile /etc/modules

### modules-gentoo
# GentooModulesAutoload yes

### network
DownInterfaces eth0 ath0
# UpInterfaces auto

### pcmcia
# EjectCards yes

### programs
# IncompatiblePrograms xmms

### services
RestartServices ibm-wclient NetworkManager NetworkManagerDispatcher
# StopServices alsasound
# StartServices aumix

### vbetool
# EnableVbetool yes
# RestoreVbeStateFrom /var/lib/vbetool/vbestate
# VbetoolPost yes
# RestoreVCSAData yes

### xhacks
SwitchToTextMode no
# UseDummyXServer yes

### xstatus
## This can be set to gnome, kde or x:
XStatus gnome
# XSuspendText Preparing to suspend...
# XResumeText Resuming from suspend...
## When using XStatus x, and you have xosd installed:
# XosdSettings --font -misc-fixed-medium-r-semicondensed--*-120-*-*-c-*-*-* --colour=Green --shadow 1 --pos bottom --align center --offset 50

---

### Post by hedge on 2005-11-11
The most probable reason for a very slow suspend in the HD drivers you have complied into the kernel. Find the driver via lspci | grep 'ide'[FONT=monospace].
Otherwise set the verbosity to 1 in the hibernate.conf > [/FONT]Verbosity 1. Then to trouble shoot further run a bug report # hibernate --bug-report > filename.txt. this will give you an idea what is loaded when suspending and you may want to unload first. Do this by uncommenting and adding modules to UnloadModules psmouse etc...

Hope that helps,

hedge

pm or email me from this forum if ya need a hand...

---

### Post by RyanGT on 2005-11-11
I would really like to make hibernate work on my Compaq Presario laptop, and I am excited about this howto.  But I have two concerns:

1.  I tried something similar on Fedora Core 3 and it made my system unbootable.  I don't know if this was a hard ware specific thing - other people followed the same howto and had great results.  Is there anyone who has successfully used this procedure on a Compaq Presario 2500?  Are there any reports of serious problems after following this procedure - if I can't reboot into a hibernated session that is a problem but not an unrecoverable one - the problem I had before was that I couldn't even restart the computer into a fresh session.

2.  I run Ubuntu from an external USB harddrive.  To do this, I have to add some extra modules to the modules list for mkintiramfs for USB support.  Any idea whether this procedure will work for booting from the USB harddrive (my swap partition is also on the USB hard drive)?  Has anyone tried it?

Thanks,

Ryan

---

### Post by mariner09 on 2005-11-11
Here's my IDE chipset:

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 01)

I didn't see a very good choice in the ATA drivers section of the kernel compile, in fact, only 1 Intel chipset was listed.

If anyone can tell me there's a best choice that they're aware of, that would be great.

Shannon

---

### Post by RyanGT on 2005-11-11
Additionally, I am working through the howto and in the kernel configuration I don't have a perfect IDE chipset match.  I have:
root@ubuntu:/usr/src/linux# lspci | grep 'IDE'
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)

The closest is the ALi M15x3.  Will this work? Should I leave it as generic?

Ryan

---

### Post by RyanGT on 2005-11-11
is there a howto for combining this with madwifi?

Ryan

---

### Post by mariner09 on 2005-11-11
RyanGT,

Go to the madwifi wiki and get the latest source code using subversion.  Compile that against your custom kernel.

Shannon

---

### Post by RyanGT on 2005-11-11
Thanks for the quick reply.  I have not done this before.  I got the source from SVN using:
svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi-ng

What do you mean by compiling it against my new kernel?

Thanks,

Ryan

---

### Post by mariner09 on 2005-11-11
Once you compile your kernel with suspend2 support, you'll need to compile the madwifi-ng source against that kernel so you get the ath_pci driver you need.

Once you get the madwifi source down, cd ../madwifi-ng, make, sudo make install, modprobe ath_pci

Shannon

---

### Post by gaboo on 2005-11-11
Thank you !
Your HOWTO is perfect, easy and incredibly useful !
You changed my world !

For info, It works really well on my Dell Inspiron 8600.

```
- Overall expected compression percentage: 50.
  Compressed 342065152 bytes into 152248860 (55 percent compression).
- I/O speed: Write 56 MB/s, Read 39 MB/s.

```

---

### Post by mariner09 on 2005-11-11
My final success story came with a Vanilla kernel and specifying an IDE driver.

I have 2.6.14.1 running Suspend2 on Ubuntu Breezy.

24sec to suspend...

49sec to resume...

Thanks for getting me started

Shannon

---

### Post by El Cris on 2005-11-11
erm, mine says:
> chris@blackjack:~$ sudo cat /proc/software_suspend/debug_info
Please include the following information in bug reports:
- SUSPEND core   : 2.1.9.9
- Kernel Version : 2.6.12-hibernate
- Compiler vers. : 3.4
- Attempt number : 6
- Pageset sizes  : 9762 (9762 low) and 61225 (61225 low).
- Parameters     : 128 32 0 1 139 5
- Calculations   : Image size: 105. Ram to suspend: 2272.
- Limits         : 131056 pages RAM. Initial boot: 126624.
- Overall expected compression percentage: 50.
- Compressor lzf enabled.
  Compressed 290762752 bytes into 132260942 (54 percent compression).
- Swapwriter active.
  Swap available for image: 293164 pages.
- Highmem Support.
- Max extents used: 6
- I/O speed: Write 104 MB/s, Read 107 MB/s.

How can this enormous I/O speed be? I don't have a RAID here, it's only 1 HD that usually reads with ~54MB/sec (only tested using hdparm -t /dev/hdX).

---

### Post by Griffin3 on 2005-11-11
The speed it gives is before compression.  Or after compression, whichever way you want to look at it. So the write went from memory at 104MB/s, compressed 54%, and anctually wrote to the disk at 47MB/s

---

### Post by Griffin3 on 2005-11-11
RyanGT:

Yes, try the ALi driver, compiled into the kernel.  That is actually the same one I am using with my laptop, although the chipset doesn't seem to match perfectly.  I get the impression that these drivers are originally written for a specific chipset, and then are patched for all sorts of new chipsets as the parameters are discovered.

Also, for the madwifi, check out [http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451) -- I had to do this after I installed suspend2, so actually broke the one tutorial into two parts.

---

### Post by hedge on 2005-11-12
[quote=mariner09]Here's my IDE chipset:

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 01)

I didn't see a very good choice in the ATA drivers section of the kernel compile, in fact, only 1 Intel chipset was listed.

If anyone can tell me there's a best choice that they're aware of, that would be great.

Shannon[/quote]
Shannon your looking for the <*>  Intel PIIXn chipsets support . Along with the others listed in Griffin3's howto...

hedge

---

### Post by RyanGT on 2005-11-12
My new custom kernel is not bootable.  I mentioned earlier that I am booting from a USB harddrive.  My existing kernel has no problem with that.  The custom kernel with suspend2 support starts to boot and then complains that it cannot find my USB harddrive (at about the stage in the boot process where it would load the modules - as soon as the Ubuntu splash pops up).  In order to make the USB boot work, I have to add the following modules to /etc/mkinitramfs/modues:
ehci-hcd
usb-storage
scsi_mod
sd_mod

Do I need to do anything special in my kernel config to make sure these modules are still available?  

Thanks,

Ryan

---

### Post by RyanGT on 2005-11-12
There is actually a *.ko file somewhere in /lib/modules/2.6.12-hibernate for each module I listed in my previous post.  And the boot actually gets through the loading modules stage and hangs on mounting the root file system saying that /dev/sda8 does not exist (this is the root partition on the usb hard drive).

Any ideas?

Ryan

---

### Post by Nigel_C on 2005-11-20
Sorry for the slow reply.

[QUOTE=Abnaxos]Suspend2 *used* to work *perfectly* on the *same* machine, and that's not such a long time ago.[/QUOTE]

There's one thing that I forgot to mention in my original post - I recently (2.6.13 iirc) changed Suspend2 to rely on hotplug cpu for its SMP support. If you enable the CPU_HOTPLUG option, it should be fine. In 2.2-rc11, I made this dependency explicit in the Kconfig file.

Humble apologies.

Nigel

---

### Post by Nigel_C on 2005-11-20
[QUOTE=El Cris][UPDATE2]:
strange:

Suspend succeeded here, but it's always showing the above BIG FAT WARNING. Funnily it says to hit C to "forget that image, continue and the image will be erased". But just after hitting C it's resuming. Well, no problem for me, but how can I get rid of that BIG FAT WARNING cause I don't want to hit C always or wait the 25seconds.[/QUOTE]

Yeah. I believe I fixed that a while ago (2.1.9.9 is a few months old now). The "echo > /proc/software_suspend/do_resume" needs to be in your initrd, prior to mounting your root filesystem etc. If you don't do the echo during the initrd, you'll get this message. If you do an echo afterwards, especially if you've mounted filesystems in the meantime, you're in danger of corrupting your data on disk. This is because the image that is saved includes things like superblocks. If you mount the filesystems, journals will be replayed and the data on disk won't match the contents of the image anymore. This inconsistency can result in serious damage. This is why the warning exists. New versions of Suspend2 have modified things a little - 2.2-rc11 and later remount filesystems read only while suspending, and I've also added code that refuses to resume if the same root filesystem used in the image is mounted when you try to resume. These should provide more protection.

Regards,

Nigel

---

### Post by Maverick911 on 2005-11-20
Hi, I'm having a little problem with GCC and was hoping someone could point me in the right direction. When I run the command:
```
apt-get -y install gcc-3.4.5
```
I get this message:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4.5
```
Where can I find this package? Thanks in advance for any help

---

### Post by RyanGT on 2005-11-20
I don't think 3.4.5 is in the stable release section.  Use 3.4.4.  You can search in the Synaptics package manager for gcc-3.4 and see what your options are.

---

### Post by nevelis on 2005-11-20
Heya,

Have you tried:

```
apt-get install hibernate
```

Worked for me - Ubuntu Breezy on 2.6.12-9-k7

Cheers,
Aaron

---

### Post by benguin on 2005-11-21
EDIT: Mixed results (suspend success, but device failure) with 2.6.14. Read on.

I downloaded Nigel's latest suspend2 (2.2-rc12), downloaded kernel 2.6.14. Patched it. No problems there. Configured manually, not by copying the old config. Yes it is tidious but I know the hardware pretty well. At least I thought I did. Compiled in support for ext3, atiixp ide controller (kept no generic controllers in the kernel or as modules) and lzf compression built in as well.

Made a deb package using make-kpkg. Installed it. Fine and dandy. Wrote the scripts for initramfs; I followed this link in the suspend2 wiki. 
[http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger?highlight=(ubuntu)]("http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger?highlight=(ubuntu)")
Real good stuff there.

Booted into the new kernel. Popped up a few apps (nautilus, shell, firefox), did a suspend using sudo hibernate from a terminal. Crossed my fingers. and.. no! locked up at the point where suspend2 does the atomic copy. sleep failure.

Went back to kernel recompilation. Turned off local APIC support in uniprocessors. Did the whole compile-install bit again. This time, it slept like a charm!

Tried waking up. Usplash comes up.. and  then suspend2 started restoring! yaay! restore it did indeed. So i had a working hibernate-resume system, finally.  But.. 

yeah there is a but. My usb mouse stopped working. it's an optical mouse, and after resuming, the light just goes off! I tried unplugging and plugging in, several times on different USB ports, with no luck. Top of that, my sound is totally borked. it just plays a fraction of the sound iin a loop forever. like a broken record. If i move the mouse, sound works fine. So, to listen to an MP3 or even get the system past the startup sound, i have to keep my mouse moving! And, it has to be external mouse, not the touchpad. Moving the touchpad has no effect.

I looked into dmesg, it has a lot of ATI IXP IRQ messages. I'm writing from a different kernel now, I will post those. After resuming, when I re-plug the mouse back in, I see messages like this in the system log:

```

Nov 24 15:15:09 localhost kernel: [   35.205248] ohci_hcd 0000:02:07.1: OHCI Host Controller
Nov 24 15:15:15 localhost kernel: [   40.739609] ACPI: PCI interrupt for device
0000:02:07.1 disabled
Nov 24 15:15:15 localhost kernel: [   40.739616] ohci_hcd: probe of 0000:02:07.1 failed with error -16

```
The log also has these messages for the sound card:
```
Nov 24 16:00:02 localhost kernel: ] atiixp: codec read timeout (reg 1c)
Nov 24 16:00:02 localhost kernel: [   42.810293] atiixp: codec read timeout (reg 0)
```

Also interesting, at the very start of the system bootup cycle, this is printed to the log:
```
Nov 24 16:00:02 localhost kernel: Symbols match kernel version 2.6.14.
Nov 24 16:00:02 localhost kernel: No module symbols loaded - kernel modules not enabled.
```

I am most definitely using modules. And successfully too.

So, the hypothesis is: I can suspend2/resume2 if I do not use local IOAPIC support in the kernel. That trashes my sound and USB devices (maybe, mouse for sure). If I do compile in IOAPIC support, that fixes sound and USB, but I cannot suspend anymore, ( I get stuck at the "Doing Atomic Copy" point).

Any ideas to get me out of this nice area between a rock and a hard place?

_J_

OLD POST:

has anyone tried software suspend2 on a 2.6.14.x series kernel?

Before I go on, here are the specs for my laptop:

HP Pavilion ZX5000, P4 3.2 HT processor, 1 gig RAM, 80 GB harddrive, 15.4" (I think) widescreen, Broadcom BCM4306 54g wireless, Realtek RTL-8139 LAN, ATI IXP sound and modem (ALSA shows two devices), ATI Radeon M10 mobility 9600 graphics (64MB (possibly) dedicated VideoRAM), TI 1394 (4-pin) port, 3 USB ports (2 USB2.0, 1 USB1.1).

I have followed the tutorial for the breezy (2.6.12-9) kernel. It did not work for me as-is, I had to pass noapic and then irqpoll option to the kernel. Otherwise, without noapic, the suspend process would stop while doing the atomic copy operation. Without irqpoll and with noapic, my sound was totally screwed. So that was the fix. But I wanted to upgrade to the latest stable kernel, build it so that it's optimized for my laptop (and there are 5 more in the lab I work, same model) and make a redistributable package out of it. That is the motivation.

Unfortunately, building a vanilla (patched with SS2) kernel seemed to work great at the beginning, suspend process worked without any fancy kernerl parameters. All of my laptop devices worked as well, no problems with sound either. Only glitch, was the ndiswrapper-source module failed to build, but that is not a major concern at this time for me. One thing to note is that I used gcc-4 to build the kernel, not 3.4. 

Now comes the bad news. The resume process did not work. When i powered the machine back on after hibernation, the suspend image was not even detected! Yes, the default resume device is my swap partition, and properly written into the kernel (swap:/dev/hda4 to be exact). 

I was wondering if anyone here has had any luck with the vanilla 2.6.14 kernel and the latest SS2. 

Also, is there any way I can apply the Ubuntu patches to a vanilla kernel myself? I mean, are the patches by themselves available? Sorry, another question.. do we know what kernel Dapper will come with? :-)

Sorry for the (annoyingly) long post. Thanks in advance!

_J_

---

### Post by blackpaw on 2005-11-23
Hello there :)

I managed to get swsusp2 running by getting hibernate package from synapic.
Problem is: After Resume the system is unresponsive, it is as if I am running 100MhZ only and the wireless card is not working anymore, even after cardctrl eject and insert it won't work anymore...

any idea what is going wrong and how I can find out about it?

thanks,


andreas

---

### Post by hedge on 2005-11-23
Blackpaw,

The hibernate.conf can unload modules that may cause problems. Uncomment UnloadModules, and add the modules to unload prior to suspend. For example:    UnloadModules ieee1394 button uhci_hcd ehci_hcd ndiswrapper, etc...

Also a bug report can help to see what is happening and which modules you may want to unload.
hibernate --bug-report > (file name).txt

hope this helps

hedge

---

### Post by kwaanens on 2005-11-23
Will suspend2 work with 3d-accellerated ati-cards? Mine is x300, or whatever it's called. The default hibernate/suspend functions does not work after 3d-accelleration.

- Ketil

---

### Post by coaxx on 2005-11-24
[QUOTE=nevelis]Heya,

Have you tried:

```
apt-get install hibernate
```

Worked for me - Ubuntu Breezy on 2.6.12-9-k7

Cheers,
Aaron[/QUOTE]

After doing ```
apt-get install hibernate
``` I get this message when trying to hibernate via "hibernate" command:

```
Your kernel does not have any recent Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://softwaresuspend.berlios.de/ for
instructions on how to compile Software Suspend into your kernel.
hibernate: Aborting.

```

So the kernel patch is riquired additionally?

---

### Post by CHUCKYCHUCK on 2005-11-24
Hi ! the kernel built-in hibernate function doesn't work with my laptop, so i plan to use this how-to
but i have some questions :
_ i have an hyper-threading pentium 4, ( so i use the -686-smp kernel ), i'd like to know what commands do i have to change to keep the functionalities of my smp kernel ?? or maybe i have to change nothing .. 
( i'am afraid this how-to will downgrade my smp to a standard kernel, as i did'nt really understand if it is a patch or a totally new kernel installation ( as we have to download sources .. ))

thanks !
bye

---

### Post by hedge on 2005-11-24
Chuckychuck,

You very well may not be able to get suspend to work with the SMP kernel. You'd be better served with a vanallia kernel 2.6.14 and selecting your cpu and smp or importing the .config of the smp kernel as described in the HowTo. In addition to enabling -> Bus options (PCI, PCMCIA, EISA, MCA, ISA) --> 
[*] Support for hot-pluggable CPUs (EXPERIMENTAL) according to Nigel_C the developer of Suspend2. You will also need to get the Suspend2 patch, Hibernate sctipt and Userspace UI from the suspend2 site.

[http://suspend2.net/downloads/](http://suspend2.net/downloads/)

Otherwise, the process is still as the Howto outlines it.

good luck

hedge

---

### Post by grizzly on 2005-11-24
```
apt-get -y install linux-tree-2.6.12
```

This requires 44MB to be downloaded :cry:
That would take abt 3-4 hours on my computer. Any other way to get windows like hibernation. This is one of the best features of windows (for me), and is sorely missed.

---

### Post by CHUCKYCHUCK on 2005-11-25
[QUOTE=hedge]Chuckychuck,

You very well may not be able to get suspend to work with the SMP kernel. You'd be better served with a vanallia kernel 2.6.14 and selecting your cpu and smp or importing the .config of the smp kernel as described in the HowTo. In addition to enabling -> Bus options (PCI, PCMCIA, EISA, MCA, ISA) --> 
[*] Support for hot-pluggable CPUs (EXPERIMENTAL) according to Nigel_C the developer of Suspend2. You will also need to get the Suspend2 patch, Hibernate sctipt and Userspace UI from the suspend2 site.

[http://suspend2.net/downloads/](http://suspend2.net/downloads/)

Otherwise, the process is still as the Howto outlines it.

good luck

hedge[/QUOTE]

thanks for your help, but i've never compiled a kernel .. when do i have to import my old config file ? ( what commands ? )
and then when i have the vanilla kernel installed, i have to follow exactly
the suspend2 how-to ?

bye

---

### Post by hedge on 2005-11-25
ChuckyChuck,
Eyeball griffns HowTo he has it step by step for ya. You'll just be using  a different kernel, hibernate script and Userspace UI than griffin used. Other than that you'll need gcc-3.4 and all the rest of the HowTo just as it is written. Here is Griffins howTo [http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443)

good luck

hedge

---

### Post by hedge on 2005-11-27
ChuckyChuck,
Just a lil update regarding smp and HT. I finally got suspend2 to work with the 2.6.12 smp kernel. I was trying to use the 2.6.14 vanilla kernel at the urging of Nigel_c (developer of Suspend2) and was frustrated out of my mind and went back to 2.6.12 smp (installing from Synaptic), then importing the .config (config-2.6.12-9-686-smp) and compiling a new kernel leaving the default cpu (X) Pentium-Pro. I have yet to see any performance decline as a matter of fact is actually seems to run a lil better (probably because it suspends now, and I'm not totally peeved over not suspending.) I'm not totally pleased yet, not until I can actually use the correct cpu selection in the kernel and suspend. But for now, it is certainly prefered to suspend than to fret over smp and ht. In addition, you may find that your not really running smp or ht by typing 'sudo cat /proc/cpuinfo'. Because, the cpu has to be set in the kernel and compiled.

hope that helps

hedge

---

### Post by CHUCKYCHUCK on 2005-11-28
so you followed the suspend2 howto, using a 2.16.12 smp kernel ? or a "normal" kernel importing your old config file ? ( my english isn't perfect, didn't fully understand what u said )
( could you detail exactly what you've done plz )

thanks
bye

---

### Post by Rob2687 on 2005-11-29
It keeps telling me this:

hibernate: Suspend reported the following errors:
 - Suspend was aborted (see dmesg).
 - No swapspace was available. Try swapon?

The dmesg seems to indicate that I don't have enough space but I have 900mb free and this laptop has 640mb ram

Here's the dmesg
```

[4295185.072000] Suspend2 2.2-rc9: Initiating a software suspend cycle.
[4295187.073000] userspace ui: Failed to contact userspace process.
[4295187.092000] Suspend2 2.2-rc9: Swapwriter: Signature found.
[4295187.092000] Suspend2 2.2-rc9: Suspending enabled.
[4295187.092000] Freezing processes
[4295188.826000] You need some storage available to be able to suspend.
[4295188.832000] Suspend2 debugging info:
[4295188.832000] - SUSPEND core   : 2.2-rc9
[4295188.832000] - Kernel Version : 2.6.14-nitro2-suspend2
[4295188.832000] - Compiler vers. : 4.0
[4295188.832000] - Attempt number : 5
[4295188.832000] - Parameters     : 5 32 0 1 50 5
[4295188.832000] - Overall expected compression percentage: 50.
[4295188.832000] - Compressor lzf enabled.
[4295188.832000] - Swapwriter active.
[4295188.832000]   Swap available for image: 0 pages.
[4295188.832000] - No I/O speed stats available.

```

---

### Post by hedge on 2005-11-30
[quote=Rob2687]It keeps telling me this:

hibernate: Suspend reported the following errors:
 - Suspend was aborted (see dmesg).
 - No swapspace was available. Try swapon?

The dmesg seems to indicate that I don't have enough space but I have 900mb free and this laptop has 640mb ram
[/code][/quote]

 Rob2678,

Try running a --bug-report with the hibernate command like this hibernate --bug-report > filename.txt. This can give you some insite on what is actually causing the abort if it isn't actually a lack of swap space to write to.
Let us know what you get from the bug report.

L8r
hedge

---

### Post by Rob2687 on 2005-11-30
Actually, I just got it working an hour ago. 
I had to add swsups2 script to my initrd and reconfigure it.
See this page: [http://wiki.suspend2.net/DistroAndHardwareSetup/DebianInitrd](http://wiki.suspend2.net/DistroAndHardwareSetup/DebianInitrd)
Plus I left the nocache option commented out. Otherwise it will give me that swap error for some reason.

Part of the problem was probably because I tried to follow this guide but use the Suspend2 patch that was already included in the nitro2 kernel patch. :P I think they used a different version of Suspend2.

---

### Post by hedge on 2005-11-30
[quote=Rob2687]Part of the problem was probably because I tried to follow this guide but use the Suspend2 patch that was already included in the nitro2 kernel patch. :P I think they used a different version of Suspend2.[/quote]

Rob2687,

Where did ya get the nitro kernel from would like to have a look t it?

hedge

---

### Post by Rob2687 on 2005-11-30
[QUOTE=hedge]Rob2687,

Where did ya get the nitro kernel from would like to have a look t it?

hedge[/QUOTE]
[http://gentoo-wiki.com/HOWTO_nitro-sources](http://gentoo-wiki.com/HOWTO_nitro-sources)

---

### Post by hedge on 2005-12-01
[quote=CHUCKYCHUCK]so you followed the suspend2 howto, using a 2.16.12 smp kernel ? or a "normal" kernel importing your old config file ? ( my english isn't perfect, didn't fully understand what u said )
( could you detail exactly what you've done plz )

thanks
bye[/quote] 
Yup I used the ubunto 2.6.12 SMP kernel image and imported it'd config file frm /boot/config-2.6.12-9-686-smp. And following the HowTo did cp -p /boot/config-2.6.12-9-686-smp .config.

When in menuconfig the defalt cpu selection was Pentium Pro, so I just left it as I found it instead of selecting the P4 and SMP/HT. Other than that all the rest was simply as the howto outlines. I did do some kernel hacking cause the kernel has including the kitchen sink selected as a module. I also added support for the lid close event to hibernate the laptop. So that is about it...:)

L8r

hedge

---

### Post by qaqa on 2005-12-05
I've successfully installed swsusp2 on breezy (presario 17xl579 laptop)
It suspends to disk and resumes just fine..I just have one tiny problem:

When I run the hibernate script,the display switches off immediately and I get no messages about the progress of the hibernation. Since my laptop's ACPI is blacklisted, I need to turn it off manually. With hibernate giving me no messages, I have no idea when to turn it off! I wait for around 15 secs just to be safe before turning it off..Is there any way to rectify this situation? (I'm running hibernate.sh with the --verbosity=3 switch)

Hibernate is integrated into the gnome shutdown splashscreen. Is there any way to integrate it into the KDE shutdown splash screen?

I use suspend to disk for the primary reason that hibernate/resume is MUCH faster than shutting down and booting. It generally resumes in < 10 secs! (with a full KDE environment!)

---

### Post by hedge on 2005-12-05
[quote=qaqa]
When I run the hibernate script,the display switches off immediately and I get no messages about the progress of the hibernation. Since my laptop's ACPI is blacklisted, I need to turn it off manually. With hibernate giving me no messages, I have no idea when to turn it off! I wait for around 15 secs just to be safe before turning it off..Is there any way to rectify this situation? (I'm running hibernate.sh with the --verbosity=3 switch)[/quote]

Since your noy having the suspend cycle turn off the system, it appears that watching the HD light is your clue to when suspend is done. The light should indicate some activity with numerous bursts at first, then a long burst followed by a pause then one last burst as it does atomic copy. As soon as that last burst is done the poweroff sig is sent. On this 3 gig intel it happens in about 1/2 sec after the HD is completed the atomic copy.

[quote=qaqa] Hibernate is integrated into the gnome shutdown splashscreen. Is there any way to integrate it into the KDE shutdown splash screen?[/quote]

In KDE there is a Klaptop power management is the systray. After installing suspend2 there should be a selection next to hibernation in the prefrences that says to use suspend2 when hibernating. Once hibernation is enabled in Klaptop you can just rt clk Klaptop from the systray and choose hibernate. Or as Griffin3's howto showed, you can have it run when you hit the power buttin. I prefer to have it run when I close the lid so I had the lid event run hibernation.

hope that helps

hedge

---

### Post by bgalan on 2005-12-05
greetings,

i tried the how-to with my hp pavilion ze4145 but it didn't work :(  
it could be that i did something wrong, but i think i followed the instructions quite closely. the kernel does not boot; after starting the screen turns black and, although the hd is working (the light blinks), the screen remains black and the keyboard does not work. i tried adding the "noapic" option but nothing happened. I chose the athlon option in the kernel configuration. the original kernel works fine, but no hibernation. could someone, please, help me?  i love ubuntu and i'm learning many things, but i'm still quite new with linux. still, i almost never use windows anymore.  it'd be great to be able to hibernate the computer. thanks in advance for you help.

benjamin

---

### Post by Griffin3 on 2005-12-06
bgalan:

I would suggest first to try to compile and run the kernel with thesuspend2 built in, but without selecting the Athlon processor. Also, make sure you copy the existing config file before you **make oldconfig**,it may be that the HP Pavilion needs some strange settings that arediscovered in the Ubuntu install.  This would be a way to"recover" those settings.

---

### Post by strips on 2005-12-06
There is a deb file of the hibernate script:
[http://cp.yi.org/apt/hibernate/hibernate_1.12-1_all.deb](http://cp.yi.org/apt/hibernate/hibernate_1.12-1_all.deb) ([http://www.suspend2.net/](http://www.suspend2.net/))

---

### Post by bgalan on 2005-12-06
Thanks Griffin3, i'll try what you suggest. however, before i mess anything up, can i erase the custom kernel that i configured with suspend2 and start over?  and, if i download the deb file that strips suggests (thanks!), do i need to erase anything that i already have? sorry if the questions are much too simple, but i am very greatful for your help.

benjamin

---

### Post by Griffin3 on 2005-12-06
yes.  in /boot/ directory, delete the custom kernel and the System.map and .config file with the same extension.  Then run **update-grub** to rebuild the grub startup screen.  It is probably best to delete the entire linux tree directory with **rm -r /usr/src/linux-source-2.6.12** and then restart from the step where you unpack the linux-source-2.6.12.tar.bz2 file.  It will take about 20 minutes more, but you will be assured of starting from a fresh linux tree.

If you use the .deb that strips suggest, you can skip the steps where you download and unpack the hibernate script in the how-to.  Tell us how this works for you, since we haven't tested it yet.

---

### Post by bgalan on 2005-12-06
Griffin3

thanks again. i already deleted the files from the /boot directory and the linux kernel tree. i'll give it a try with the deb file once i get home tonight. once more question, though, you mentioned about copying the original config file before doing the make oldconfig, however, and it is a rookie mistake, i didn't. is it too late? can i still recover it? or is it going to be new once i reboot the computer? or, perhaps, if you know, where can i read more about it?  thanks again for your help. i think i might be getting closer to having hibernation working!

benjamin

---

### Post by Griffin3 on 2005-12-06
The original config shoulld still be there, try **cp /boot/config-2.6.12-9-386 /usr/src/linux/.config** -- but the source might be config-2.6.12-10-386 if you installed Ubuntu in the past, uh, 3-4 weeks or so, since they upgraded.

---

### Post by cow_racer on 2005-12-07
Anything like sleep?

---

### Post by ming0 on 2005-12-10
I've tried this howto twice, and I've gotten the same error both times. At reboot, I get:```
Kernel Panic-not syncing:VFS unable to mount root FS on unknown-block(0,0)
```The only step that doesn't work for me is:```
root@dim:/home/dean# apt-get -y install gcc-3.4.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4.5

```That is the only error thrown, but I don't think it is the problem?

Does anyone have any ideas?:confused:

---

### Post by alonso on 2005-12-10
I was able to install fglrx 8.19.10 and 8.20.8 to the ubuntu breezy 2.6.12-10 kernel, using the instructions in
[http://www.ubuntuforums.org/showthre...ighlight=fglrx](http://www.ubuntuforums.org/showthre...ighlight=fglrx)

but I'm having problems installing them to 2.6.12-9 with the swsusp2 patch from:
[http://www.ubuntuforums.org/showthre...hlight=swsusp2](http://www.ubuntuforums.org/showthre...hlight=swsusp2)

Any ideas?

This is the error i'm getting when I'm doing module-assistant a-i fglrx:

```
dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
fi
if [ -f postinst ]; then \
mv postinst fglrx-kernel-2.6.12.postinst; \
fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12-swsusp2'
CC [M] /usr/src/modules/fglrx/agp3.o
CC [M] /usr/src/modules/fglrx/nvidia-agp.o
CC [M] /usr/src/modules/fglrx/agpgart_be.o
/usr/src/modules/fglrx/agpgart_be.c: In function `__fgl_agp_init':
/usr/src/modules/fglrx/agpgart_be.c:8173: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/usr/src/modules/fglrx/agpgart_be.c: In function `__fgl_agp_cleanup':
/usr/src/modules/fglrx/agpgart_be.c:8183: warning: `pm_unregister_all' is deprecated (declared at include/linux/pm.h:116)
/usr/src/modules/fglrx/agpgart_be.c: At top level:
/usr/src/modules/fglrx/agpgart_be.c:6077: warning: 'ati_gart_base' defined but not used
CC [M] /usr/src/modules/fglrx/i7505-agp.o
CC [M] /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c: In function `firegl_stub_putminor':
/usr/src/modules/fglrx/firegl_public.c:543: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:56
/usr/src/modules/fglrx/firegl_public.c:545: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
/usr/src/modules/fglrx/firegl_public.c: In function `firegl_stub_register':
/usr/src/modules/fglrx/firegl_public.c:565: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
/usr/src/modules/fglrx/firegl_public.c:596: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:56
/usr/src/modules/fglrx/firegl_public.c: In function `fglrx_pci_suspend':
/usr/src/modules/fglrx/firegl_public.c:660: error: invalid operands to binary ==
/usr/src/modules/fglrx/firegl_public.c:678: error: incompatible types in assignment
/usr/src/modules/fglrx/firegl_public.c: In function `fglrx_pci_resume':
/usr/src/modules/fglrx/firegl_public.c:692: error: invalid operands to binary ==
/usr/src/modules/fglrx/firegl_public.c:703: error: invalid operands to binary ==
/usr/src/modules/fglrx/firegl_public.c:706: error: incompatible types in assignment
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:717: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function `do_vm_kmap_nopage':
/usr/src/modules/fglrx/firegl_public.c:2610: warning: assignment makes pointer from integer without a cast
make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[1]: *** [_module_/usr/src/modules/fglrx] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12-swsusp2'
make: *** [build] Error 2
```

---

### Post by ming0 on 2005-12-10
I figured out part of my problem, but a new one cropped up :(

I had to make an initrd with the following commands: ```
apt-get install module-init-tools initrd-tools procps
cd /boot/
mkinitrd -o /boot/initrd.img-2.6.8.1 2.6.8.1

```Now add that line in /boot/grub/menu.lst (just look at the other images for an example)

Once I did that and rebooted, I got the following error repeated a few times and then a kernel panic! ```
modprobe : FATAL : could not load /lib/modules/2.6.12/modules.dep : No such file or directory
``` Any more suggestions are appreciated.

---

### Post by nelposto on 2005-12-11
[QUOTE=ming0]I figured out part of my problem, but a new one cropped up :(

I had to make an initrd with the following commands: ```
apt-get install module-init-tools initrd-tools procps
cd /boot/
mkinitrd -o /boot/initrd.img-2.6.8.1 2.6.8.1

```Now add that line in /boot/grub/menu.lst (just look at the other images for an example)

Once I did that and rebooted, I got the following error repeated a few times and then a kernel panic! ```
modprobe : FATAL : could not load /lib/modules/2.6.12/modules.dep : No such file or directory
``` Any more suggestions are appreciated.[/QUOTE]

I had the same first problem as you, so I copied what you did and it let me boot into Ubuntu but gave me a Big fat warning (initrd not configured for suspend) which I ignored. Then it hibernated successfully but wouldn't resume due to the error above.

After some hunting I did this [http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger?highlight=(ubuntu](http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger?highlight=(ubuntu)) and now i have the same errors as you "modules.dep : No such file or directory"

---

### Post by ming0 on 2005-12-11
Thanks for that link--I'll give that a try when I've got a bit of time :)

---

### Post by nelposto on 2005-12-11
[QUOTE=ming0]Thanks for that link--I'll give that a try when I've got a bit of time :)[/QUOTE]

But I don't know if it's good... like I said, it only gave me a different problem. But I'm pretty new to this, so maybe you can get it right!

---

### Post by Griffin3 on 2005-12-12
ming0: re the gcc-3.4.5, the package info has changed. Now, you should use ```
apt-get -y install gcc-3.4
```which pulls the latest version. I'll be changing the how-to immediately.

The how-to as written does not work with an initrd; if you guys find out how to make it work with one, I'll cheerfully add it to the insturctions.

---

### Post by nelposto on 2005-12-13
[QUOTE=ming0]I've tried this howto twice, and I've gotten the same error both times. At reboot, I get:```
Kernel Panic-not syncing:VFS unable to mount root FS on unknown-block(0,0)
```The only step that doesn't work for me is:```
root@dim:/home/dean# apt-get -y install gcc-3.4.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4.5

```That is the only error thrown, but I don't think it is the problem?

Does anyone have any ideas?:confused:[/QUOTE]

So remember I had the same problem as you. I've since managed to get hibernation working!

What I did is compile first a clean version of the 2.6.14 kernel. Just clean, without any customisation from my default 2.6.12-10-386 kernel that boots nicely (set up by ubuntu). It booted, I was happy.

Then I applied the suspend2 patch for the 2.6.14 kernel ([www.suspend2.net)](www.suspend2.net)), and through make menuconfig changed ONLY power management - use suspend2, and specified my swap for the swap writer. (IE. I didn't enable any more filesystems, or compression, or set my processor type or IDE chipset type).

This kernel booted! and successfully hibernated / resumed! Unfortunately, so far it doesn't have the nice looking suspend progress bar that I saw while following this guide (unsuccessfully) .. but I'll see if I can get that working soon.

Just now I finished compiling a kernel that includes lzf compression. Fingers crossed that it works. If that works, then the problem may lie in enabling  
Ext3 journalling file system support?? 
Or otherwise perhaps customising my processor type to Pentium M?
... or probably to do with the IDE settings

I will try these and see.. but now to test lzf compression..

Edit:added website for 2.6.14 suspend2 patch

Edit again: lzf compression gets a green light! almost doubled my I/O speeds.

---

### Post by foxiness on 2005-12-13
first thank you for this How-to ,

1- after i do this on first time i do one with out bult-in support of my IDE than i do that [not done]
2- after i create kernel with IDE support it do suspend and resume [Done]
3- because i have on Grub menu to kernel with hibernate support (ubnutnu kernel x.x.x hibernate) (ubuntu kernel x.x.x hibernate.old) 
4- after i do hibernate [done] i select another kernel (ubuntu kernel x.x.x hibernate.old) 

out put"
: p1 p2 p3 < p5 >
[4294673.548000] EISA: Probing bus 0 at eisa.0
[4294673.548000] Cannot allocate resource for EISA slot 1
[4294673.548000] EISA: Detected 0 cards.
[4294673.548000] NET: Registered protocol family 2
[4294673.557000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294673.557000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294673.557000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294673.557000] TCP: Hash tables configured (established 32768 bind 32768)
[4294673.557000] NET: Registered protocol family 8
[4294673.557000] NET: Registered protocol family 20
[4294673.557000] Software Suspend Core.
[4294673.557000] Software Suspend Compression Driver loading.
[4294673.557000] Software Suspend Encryption Driver loading.
[4294673.557000] Software Suspend Swap Writer loading.
[4294673.557000] ACPI wakeup devices:
[4294673.557000] ELAN MIN1 USB1 USB2 USB3 EUSB MODM
[4294673.557000] ACPI: (supports S0 S3 S4 S4bios S5)
[4294673.558000] Resume block device is dffe0ac0.
[4294673.564000] Software Suspend 2.1.9.9: Swapwriter: Signature found.
[4294673.564000] Software Suspend 2.1.9.9: Suspending enabled.
[4294673.585000] === Software Suspend ===
[4294673.585000]
[4294673.585000] BIG FAT WARNING!! Incorrect kernel version
[4294673.585000]
[4294673.585000] If you want to use the current suspend image, reboot and try
[4294673.585000] again with the same kernel that you suspended from. If you want[4294673.585000] to forget that image, continue and the image will be erased.
[4294673.585000] Press SPACE to reboot or C to continue booting with this kernel[4294673.585000]
[4294673.585000] Default action if you don't select one in 25 seconds is: continue booting.
[4294674.153000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294682.506000] Software Suspend 2.1.9.9: Image invalidated.
[4294682.592000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294682.592000] EXT3-fs: write access will be enabled during recovery.
[4294683.110000] kjournald starting.  Commit interval 5 seconds
[4294683.110000] EXT3-fs: recovery complete.
[4294683.111000] EXT3-fs: mounted filesystem with ordered data mode.
[4294683.111000] VFS: Mounted root (ext3 filesystem) readonly.
[4294683.111000] Freeing unused kernel memory: 228k freed
[4294685.047000] NET: Registered protocol family 1
[4294685.976000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294689.026000] Adding 706820k swap on /dev/hda5.  Priority:-1 extents:1
[4294689.237000] EXT3 FS on hda2, internal journal
[4294692.569000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294692.569000] Uniform CD-ROM driver Revision: 3.20

"


5- becasue the system continue auto it erased the last one than i do another one from this oldone after that the same message appear every time
6- now i do this again will not resume and give me the last message above every time


i put this on google and i read FAQ and HOW-TO but i can not find something like my problem ,what shulde i do now ?

---

### Post by nelposto on 2005-12-13
[QUOTE=foxiness]4- after i do hibernate [done] i select another kernel (ubuntu kernel x.x.x hibernate.old) 
[/QUOTE]

You shouldn't load another kernel version than the one you suspended with.

Hibernate.old is the kernel you compiled without specific IDE support, you should make sure that the new one works, then delete this one.

---

### Post by foxiness on 2005-12-14
yes i do this one , and i dont have the old one anymore [read the note] 

2- after i create kernel with IDE support it do suspend and resume [Done]
[this step notwork anymore after i do step 3,4,5 once] and if i do now just step 2 [not done,and give the BIG FAT WARNING!! Incorrect kernel version]

but by mistake [because the (ubuntu kernel x.x.x hibernate.old) is the defaulte] one the sys boot with this.

is there away around this to get it back work again ? with my new kernel (hibernate)

note: i delete the old one complete from /boot [vim...hibernate.old config..hibernate.old ] and form menu.lst

---

### Post by nelposto on 2005-12-14
hm.. can you post here your menu.lst and "ls /boot" ?

---

### Post by foxiness on 2005-12-14
```

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
#splashimage=(hd0,1)/grub/splashimages/quitar.xpm.gz

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-hibernate
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-hibernate root=/dev/hda2 ro quiet splash
savedefault
boot



title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot



title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot



title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root





# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1



```

```
abi-2.6.12-9-386     config-2.6.12-hibernate  initrd.img-2.6.12-9-386  System.map-2.6.12-9-386      vmlinuz-2.6.12-9-386
config-2.6.10-5-386  grub                     memtest86+.bin           System.map-2.6.12-hibernate  vmlinuz-2.6.12-hibernate
config-2.6.12-9-386  initrd.img-2.6.10-5-386  System.map-2.6.10-5-386  vmlinuz-2.6.10-5-386

```

---

### Post by nelposto on 2005-12-14
Well I don't completely understand your problem...

Are you able to boot with that kernel at all? If not, try adding "noresume2" to the bootline... so

> 
kernel /boot/vmlinuz-2.6.12-hibernate root=/dev/hda2 ro quiet splash noresume2


... unless this is not your problem.

---

### Post by foxiness on 2005-12-14
yes i can boot to it ,but can not resume the image ... it erased and continue with normal boot like before

```

[4294673.585000] If you want to use the current suspend image, reboot and try
[4294673.585000] again with the same kernel that you suspended from. If you want[4294673.585000] to forget that image, continue and the image will be erased.
[4294673.585000] Press SPACE to reboot or C to continue booting with this kernel[4294673.585000]
[4294673.585000] Default action if you don't select one in 25 seconds is: continue booting.

```

---

### Post by nelposto on 2005-12-14
[QUOTE=foxiness]yes i can boot to it ,but can not resume the image ... it erased and continue with normal boot like before[/QUOTE]

Hmmm.. I don't know..
Maybe try specifing your resume partition at boot time:

> kernel /boot/vmlinuz-2.6.12-hibernate root=/dev/hda2 ro quiet splash **resume2=swap:(your swap partition here)**

---

### Post by foxiness on 2005-12-15
this not work too and i see new BIG FAT about this resum2=swap ...

but now it work after i do it again ,thank you nelposto for help me...

now i have new quistion about my sl-modem-demon it not work after i get to suspend ,how can i get sl-modem work?

note: if i press hibernate system>logout>hiberante "oldone" it return me after some sec and my modem work too ,it look like it run sl-modem-demon.
but i do not know how?!

---

### Post by Griffin3 on 2005-12-15
foxiness: sorry, I posted a reply before I saw you'd already found a solution.  But I can't delete it now.  So this space is intentionally left blank.

about your sl-modem: have you looked for anything like sl-modemd in /etc/init.d?  If so, try ```
/etc/init.d/sl-modemd stop
/etc/init.d/sl-modemd start
``` after you return from hibernation.  IF this works, you probably need to set the sl-modem driver to stop and start in the /etc/hibernate/hibernate.conf.

---

### Post by foxiness on 2005-12-16
bottom of service on file above i have this 

```

/etc/init.d/sl-modemd-daemon stop
/etc/init.d/sl-modemd-daemon start

```

but why you remove the solution i want to know how or maybe other will have this problem like me and he will find the answer.

thank you griffin3

---

### Post by hedge on 2005-12-16
[quote=foxiness]bottom of service on file above i have this 

```

/etc/init.d/sl-modemd-daemon stop
/etc/init.d/sl-modemd-daemon start

``` 
but why you remove the solution i want to know how or maybe other will have this problem like me and he will find the answer.

thank you griffin3[/quote] 
Foxiness,

If there is any driver or service that has trouble during the suspend/resume cycles, it is prefered to have it unload prior to suspending. In your case you would try the following.

1.  /etc/init.d/sl-modemd-daemon stop
2. hibernate

If it resumes and the modem then works, then adding it to the hibernate.conf by uncommenting the line #UnloadModules to look like this:

UnloadModules sl-modemd-daemon 

or use OnSuspend/OnResume like this:

OnSuspend 30 /etc/init.d/sl-modemd-daemon stop
OnResume 30 /etc/init.d/sl-modemd-daemon start

Then to test you should use:

hibernate --bug-report > file1.txt (this will create a file called file1.txt in the directory where you run the command from)

The bug report should show where the breakage is or if one of the 2 examples above works.

hope this helps

hedge

---

### Post by ashrack on 2005-12-26
It doesn't work 4 me. It goes into hibernation fine. But when I turn the computer on, I get a black screen when it should start GDM. And also CTRL+ALT+F1 don't work and gives black screen.

If am using the VESA driver all works great. I can use the original SUSPEND&HIBERNATION aswell as SUSPEND2 without any problems.

ps. I installed NVIDIA drivers using this faq:
[http://www.ubuntuforums.org/showthread.php?t=79295](http://www.ubuntuforums.org/showthread.php?t=79295)

---

### Post by gmatht on 2006-01-01
I followed the instructions above. I set the processor type to P4, and included both ext3 and reiserfs to be safe.

Now networking no longer works. It knows that eth0 and eth2 exists, but eth0 cannot connect to the DHCP server. When I set up the IP address (192.168.1.6) manually I can ping myself (192.168.1.6), but cannot ping any other machines on the network. Also, other machines cannot ping me.

Hibernate works fine, however resume doesn't. It doesn't give a "Big Fat Kernel: Incorrect Version Error" as it did when I had suspend and suspend2 compiled into the kernel at the same time (which also trashed networking). It just competely ingnores the fact that it should try to resume. Then when I try to hibernate again, I get:

Segmentation fault
hibernate: Suspend reported the following errors:
- No status was returned. Might be a buggy or incompatible kernel.

I don't notice anything odd in dmesg  (not that I'd really know). In debug_info, I notice that it claims that 
" - Swapwriter active
    Swap availiable for image: 0 pages."
This is obviously undesirable, however if this were the case, surely it wouldn't have let me hibernate?

---

### Post by gmatht on 2006-01-01
Ok, I've recompiled my Kernel from scratch.

I noticed two things. First where you say to copy ...2.6.12-8-386  to .config, you mean for us to replace 2.6.12-8-386 with the currently running kernel (2.6.12-10-686 in my case)? Also, I could not find the exact Intel chipset on the menu so I picked Intel PIIX.

This time I did not set processor, but instead left it as the default (PPro). After recompiling the kernel and rebooting. After the first time I attempted to hibernate/resume, networking started working again, but continual attempts to hibernate/resume seemed to break it. 

Also, this time I am getting BFW's about my kernel version being different, even though I am booting with the same kernel all the time. but unlike the previous poster with this problem,  adding a resume2=swap:/dev/hda4 to the options in menu.lst did not fix the problem.

---

### Post by gmatht on 2006-01-03
OK, I turned off LZF compression  and now swsusp2 rock solid. (Before I discovered this, I managed to trash my root partition. Oh well.)  However, when I build the kernel with swsusp2 networking still cuts out after ~15 seconds. Interestingly, if I hibernate, then the networking starts working after the resume ( for ~15 seconds ).

---

### Post by blackpaw on 2006-01-03
Hi there! 

I did as instructed (great guide, by the way) and everything is fine, even my wireless connection can immediately be reconnected. :)
I am running Breezy on a VAIO N505SN with a PII mobile, 400Mhz, Intel pIIx4 chipset.

Only thing I dislike is: the speed of the display (e.g. browsing, looking at pictures) is much slower after resume from hibernation and with the new kernel the system seems to take much longer to start up. I checked with hdparm, everything is ok there.. :confused: 
Anyone have hints for me?

Processor is a Pentium 2 mobile, so I compiled with "support for Intel Pentium II (pre-coppermine) processors". Can it be that Pentium II != Mobile Pentium II ?
I will try to compile it again and leave everything on PentiumPro (686) this time.


andreas

---

### Post by ashrack on 2006-01-04
how do I remove the kernel since
dpkg -r config-2.6.12-hibernate
says that it isn't installed. Alhough it's there in /boot

---

### Post by kevin79 on 2006-01-08
Thanks for the tutorial. I plan on trying it today. I do have a quick question though. Is there a way to change the "Hibernate the Computer" option in the Log Out screen so that it will instead do the Suspend2 option?

---

### Post by kevin79 on 2006-01-08
Ok, I'm going through the HowTo and I have a couple problems. First off, when going through step 10, is everything else supposed to be unchecked or are those the options that we need to make sure are checked? In step 12 and 13, do we just need to change the lines so that they look like this? Do we delete everything else in the file? Are those lines supposed to be commeted out?

In step 11, there isn't a file called suspend2ui_text in /usr/src/suspend2-userui-0.5.1. What do I do to get it?

Thanks.

---

### Post by ashrack on 2006-01-08
[QUOTE=kevin79]Ok, I'm going through the HowTo and I have a couple problems. First off, when going through step 10, is everything else supposed to be unchecked or are those the options that we need to make sure are checked? In step 12 and 13, do we just need to change the lines so that they look like this? Do we delete everything else in the file? Are those lines supposed to be commeted out?

In step 11, there isn't a file called suspend2ui_text in /usr/src/suspend2-userui-0.5.1. What do I do to get it?

Thanks.[/QUOTE]
In step 10 U should only change the settings that are listed. Leave the rest alone, if U don't know what your doing.


IN step 11, U should have SUSPEND2*, else U didn't follow the guide in detaill check steps 5 and 6

In steps 12,13 just change the values and add the ones that are missing. Leave the rest alone.The only line that is commented is ```
#    -> #action=/etc/acpi/powerbtn.sh
``` the rest are not.

hope that helps

---

### Post by kevin79 on 2006-01-08
[QUOTE=ashrack]


IN step 11, U should have SUSPEND2*, else U didn't follow the guide in detaill check steps 5 and 6

[/QUOTE]

I don't have that in the directory and I followed the steps exactly as they are.

Here are the contents:
/usr/src/suspend2-userui-0.5.1# ls
AUTHORS    fbsplash    README            USERUI_API     userui_skeleton.c
ChangeLog  KERNEL_API  suspend_userui.h  userui_core.c  userui_text.c
COPYING    Makefile    TODO              userui.h

What do I run make on?

---

### Post by ashrack on 2006-01-09
U only have the SUPEND2-user-ui. For the suspend2 to this(copy pasted from steps 5,6):
```

cd /usr/src
wget http://ubuntu.griffin3.com/software-suspend-2.1.9.9-for-2.6.12-ubuntu5.10.tar.bz2
tar -xjf software-suspend-2.1.9.9-for-2.6.12-ubuntu5.10.tar.bz2

```

> What do I run make on?
What do U mean by that?

---

### Post by kimera on 2006-01-09
Hi guys,

I have a question, someone know where is the exact line to put in the "echo > /proc/software_suspend/do_resume" ??? 

I am using Breezy over a Acer Aspire 1604 LC , P4 2.8, Ati Mobility 64MB etc etc, this how to is great but it wasn't work on my notebook until i decided to remove radeon module from kernel end using vesafb! Since that it is working fine!

But at every resume the kernel prompt me the BIG FAT WARNING initrd is not configured!

I tried everything mkinitrd, mkinitramfs, every script I found, but nothing to do!!
The only way to make it function (with BIG FAT WARNING)is to put the "echo > /proc/software_suspend/do_resume" at the end of linuxrc file inside the initrd!


Someone know the right way to do this!

P.S. sorry for my poor english!

---

### Post by kevin79 on 2006-01-09
I finally got this working. Great tutorial.  I do however have a problem. Will this cause my wifi card to stop working? I'm using the ipw2200 drivers along with wpa_supplicant.

---

### Post by mgchan on 2006-01-09
[QUOTE=art]Well, I think I can say the suspend just doesn't work on Toshiba Satellite A65. I have tried a lot before , now I tried with griffin's suggestions, still no go, although I think I got a little further. Maybe someone can help me out here, which will make me a really happy person. The text after I type hibernate shows it saves all the needed info, then it sais Powering Down, and that's it... It stays there forever. If I press the power button, and boot back, I get a nonresposive gnome:( I tried with minimalistic environment as well, without any modules loaded, still hangs... Please, any suggestions... This is almost the last thing I don't have working on Ubuntu.
Thanks a lot[/QUOTE]

I am having this same problem on my Thinkpad X40, except that I am able to resume.  Once it gets stuck at "Powering Down" I can forcefully shut down the computer and it will work upon reboot, picking up where I left off.  Any way to troubleshoot this?

---

### Post by dotdot on 2006-01-10
i'm working through the howto - and have come up against one small problem.

..ala

# apt-get -y install gcc-3.4.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4.5


- everything else up until went well - can anyone help ?

(I'm not going to proceed in case - it gets messy without gcc-3.4.5).

..

---

### Post by ashrack on 2006-01-11
[QUOTE=dotdot]i'm working through the howto - and have come up against one small problem.

..ala

# apt-get -y install gcc-3.4.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4.5


- everything else up until went well - can anyone help ?

(I'm not going to proceed in case - it gets messy without gcc-3.4.5).

..[/QUOTE]
This really  should be updated in the guide. 
U just get:
```
apt-get install gcc-3.4
```
And all should work well

---

### Post by nelposto on 2006-01-12
Hi,

back again ripping my hair out to get this to work.

I can't understand what I'm doing wrong, but for some reason, under /proc/ there is nothing about suspend2.

> 1      1671  5     7098  7496  7825  7900  7944  7990  8013  8043    buddyinfo  dma          interrupts  loadavg  net         sys
104    2     5707  7100  7501  7829  7901  7956  7992  8015  9017    bus        driver       iomem       locks    partitions  sysrq-trigger
11336  2896  5763  7113  7558  7830  7903  7980  7994  8017  948     cmdline    execdomains  ioports     meminfo  scsi        sysvipc
132    2948  5846  7126  7581  7831  7933  7982  7996  8035  953     cpuinfo    fb           irq         misc     self        tty
133    3     7     7131  7664  7832  7935  7984  7999  8037  957     crypto     filesystems  kallsyms    modules  slabinfo    uptime
134    4     7066  7152  7771  7855  7939  7986  8006  8039  acpi    devices    fs           kcore       mounts   stat        version
135    4206  7081  722   7784  7897  7941  7988  8009  8041  asound  diskstats  ide          kmsg        mtrr     swaps       vmstat


I think this is the reason my my machine will seem to hibernate, but then just boot normally afterwards.

How do I get the right files into /proc?

Thanks

---

### Post by bgalan on 2006-01-13
greetings!

hibernation is working! :razz:  i'm happy with it. i just followed the how-to and after a good while, my pavilion ze4145, athlon-1800, dual boot with windows, is working just fine... i do have a problem. it seems that my ati drive is in conflict with suspend2 (is that right?). now when i boot up into ubuntu i cannot see anything that is happening (blank screen) but the computer is working; after a while (not too long, really) i'm in the login screen, gdm. once i'm in gnome, if i press alt+f1, or f2, etc., into a console, i cannot see anything (just mixed colors, but no console). it really is not a big deal (i think the 3d feature of my ati card is disabled as well, but i don't care... i don't have time for games nor big graphic software). i can live with it as it is; but if it can be fixed, all the better! :cool: 
thanks a lot for your work and help

benjamin

---

### Post by phidippus on 2006-01-14
I worked through the instruction and get the karnel panic.


Software Suspend 2.1.9.9: Missing or invalid storage location (resume2= parameter). Please Correct and rerun lilo (or equivalent) before suspending.

Karnel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)

I checked the step 10, but I don't think I am missing anything. Although I was not usre what exactly to pick for "Intel Corp 82801 (ICH6M) SATA controller

I also get 

BIG FAT warning!! Failed to translate "/dev/sda5" into a device id.

---

### Post by ashrack on 2006-01-15
[QUOTE=phidippus]I worked through the instruction and get the karnel panic.


Software Suspend 2.1.9.9: Missing or invalid storage location (resume2= parameter). Please Correct and rerun lilo (or equivalent) before suspending.

Karnel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)

I checked the step 10, but I don't think I am missing anything. Although I was not usre what exactly to pick for "Intel Corp 82801 (ICH6M) SATA controller

I also get 

BIG FAT warning!! Failed to translate "/dev/sda5" into a device id.[/QUOTE]
Have U compiled your FS into the kernel? And also did U properly specify the swap partition?

---

### Post by Pausanias on 2006-01-15
To the poster above who asked about gcc-3.4.5, just install gcc-3.4 instead.

Now, for my question. Not that I expect answer, given how old the thread is. But here it is anyway.

How do I get this to work with SATA? All my drives come up as SATA, not IDE, so they are /dev/sd? instead of /dev/hd?. I compiled the kernel with my SATA driver. When it boots up, I get a big fat warning saying that it can't find my swap partition (/dev/sda5).

Argh, I knew this wouldn't be easy...

---

### Post by nelposto on 2006-01-15
[QUOTE=bgalan]greetings!

hibernation is working! :razz:  i'm happy with it. i just followed the how-to and after a good while, my pavilion ze4145, athlon-1800, dual boot with windows, is working just fine... i do have a problem. it seems that my ati drive is in conflict with suspend2 (is that right?). now when i boot up into ubuntu i cannot see anything that is happening (blank screen) but the computer is working; after a while (not too long, really) i'm in the login screen, gdm. once i'm in gnome, if i press alt+f1, or f2, etc., into a console, i cannot see anything (just mixed colors, but no console). it really is not a big deal (i think the 3d feature of my ati card is disabled as well, but i don't care... i don't have time for games nor big graphic software). i can live with it as it is; but if it can be fixed, all the better! :cool: 
thanks a lot for your work and help

benjamin[/QUOTE]

Try removing any vga=xxx line from your boot line .. if you screen then gives you problems, replace it with vga=normal.

If I'm correct [http://www.ubuntuforums.org/showpost.php?p=471544&postcount=69](http://www.ubuntuforums.org/showpost.php?p=471544&postcount=69) is the problem you are dealing with. If you want to keep a higher res console .. recompile with the option quoted in that post..

also ATI 3d support is definitely gone .. you should compile the driver against your kernel to have it work

---

### Post by phidippus on 2006-01-15
[QUOTE=ashrack]Have U compiled your FS into the kernel? And also did U properly specify the swap partition?[/QUOTE]

I checked

Ext3 journalling file system support

(this is what you are talking about right?) And I get 

fdisk -l | grep 'swap'
/dev/sda5            6674        6861     1510078+  82  Linux swap / Solaris

lspci | grep 'IDE'
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)

Am I doing this wrong?

---

### Post by Pausanias on 2006-01-15
the fact that your disk is called /dev/sda5 means that it's the SCSI Serial ATA, not IDE, interface that is controlling your drives. I have a similar problem.

Clearly, there is some issue that isn't being discussed here with regards to suspend2 and SATA. Anybody got suspend2 working with SATA?

It seems that SCSI SATA is not very well supported:

[http://lists.suspend2.net/lurker/message/20050411.221616.af0ec629.en.html#suspend2-users](http://lists.suspend2.net/lurker/message/20050411.221616.af0ec629.en.html#suspend2-users)

---

### Post by qaqa on 2006-01-17
It appears that swsusp2 is extremely popular! :KS 
Can someone make ubuntu packages of the patched kernel? It will be really useful for everyone and much less hassle-free. Are there any major problems involved in this?
Similar packages have been made for FedoraCore3...

Thanks in advance
Qaqa

---

### Post by nelposto on 2006-01-17
[QUOTE=Pausanias]the fact that your disk is called /dev/sda5 means that it's the SCSI Serial ATA, not IDE, interface that is controlling your drives. I have a similar problem.

Clearly, there is some issue that isn't being discussed here with regards to suspend2 and SATA. Anybody got suspend2 working with SATA?

It seems that SCSI SATA is not very well supported:

[http://lists.suspend2.net/lurker/message/20050411.221616.af0ec629.en.html#suspend2-users](http://lists.suspend2.net/lurker/message/20050411.221616.af0ec629.en.html#suspend2-users)[/QUOTE]

YO 

myself just today got it happening .. with SATA Had a long time working it out .. but here's the explanation to the best of my knowledge.

Default config of your kernel when you install Ubuntu has SATA / SCSI stuff modular. This works fine because Ubuntu also boots with an initrd.img which loads the modules for SATA support and allows you to boot.

The method outlined here does not include making an initrd.img .. mainly (i spose) because by default an initrd.img will load modules that pass the point where resuming is possible. This is the problem I had, after not being able to boot a kernel using the command the OP gave (make bzImage (etc)), I found another method of kernel compilation that produced an initrd.img (make-kpkg --initrd (etc.)). This would boot fine, because the SATA modules would be loaded. But after a seemingly successful hibernate, the kernel would always boot as normal. I finally worked out this was because suspend2 was being more or less 'skipped' by the initrd. It is possible to make changes to your initrd (linuxrc ..) to allow use of an initrd and suspend2 (also gives you the normal ubuntu splashscreen I think) ... there is information out there somewhere .. however easier is to simply compile into the kernel SATA support.

It's under device drivers -- SCSI support (or such) .. make sure the relevant sounding ones have (*) and not (M). Then you can compile using the method outlined here (make bzImage install modules modules_install), update grub, and have a kernel that boots from your SATA and (with any luck) suspends/resumes ... coooool.


eeeeeeeedit: phidippus, since you have the same model as me, make sure under SCSI low level drivers you have enabled **Intel PIIX/ICH SATA support**

---

### Post by bgalan on 2006-01-17
[QUOTE=nelposto]Try removing any vga=xxx line from your boot line .. if you screen then gives you problems, replace it with vga=normal.

If I'm correct [http://www.ubuntuforums.org/showpost.php?p=471544&postcount=69](http://www.ubuntuforums.org/showpost.php?p=471544&postcount=69) is the problem you are dealing with. If you want to keep a higher res console .. recompile with the option quoted in that post..

also ATI 3d support is definitely gone .. you should compile the driver against your kernel to have it work[/QUOTE]

hey nelposto,
that worked like a charm! \\:D/   thanks!
benjamin

---

### Post by RickKnight on 2006-01-17
Excellent howto. I've been looking for this and somehow just kept over looking it. 

Any,
I do have one problem. Suspend2 to swap works fine and starting back up works great too. But when I do suspend, the power doesn't actually turn off. I does save 100% of the image but I then have to hold the power button down for 5 seconds. Any idea what's causing this?

Thanks again,
Rick Knight

---

### Post by ashrack on 2006-01-19
Since I don't have a swap partition, am trying to hibernate of SWAPFILE.
I compiled in the kernel support for FILEWRITER
and did:
```
# dd if=/dev/zero of=/swapfile bs=1M count=512
mkswap /swapfile
swapon /swapfile

```
and then did:
```
cat /proc/software_suspend/headerlocations
```
and then added to menu.lst what I got from the upper code
```
resume2=swap:/dev/hda5:0x26f35@4096
```
and to hibernate.conf
```
SuspendDevice swap:/dev/hda5:0x26f35@4096
```

But it still won't hibernate. It goes into process of doing the hibernation but after 2sec am right back at the desktop.
Please check the attached file for the error description.

---

### Post by bgalan on 2006-01-19
hello everyone,
here i'm again with more rookie questions... my system just updated the kernel to the 2.6.10 kernel, so now it also appears in my grub options... my question is, do i need to go through the whole process of installing and recompiling this kernel also for suspend2 to work with it? everything is working fine, but if i understand correctly, it is always a good idea to update the kernel... i hope my question makes sense; and yes, thanks a lot for your help... one of the reasons i love linux, and ubuntu in particular, is the willingness that people have to help others. so, thanks to all... i hope one day i can know enough to help others as well...
benjamin

---

### Post by Skye on 2006-01-20
bgalan: Suspend2 will only work with kernels you've compiled yourself using the guide here Your previous (custom compiled) kernel should still be availible in the GRUB boot menu, just use that instead of selecting the new kernel on boot.  You don't have to upgrade to the newer kernel version- it's really just a personal choice.

I have a question as well.  Has anyone tried to compile using the current set of instructions/patches and the new 2.6.12 source that just came out through synaptic on Tuesday or Wensday?  I tried, and got the following error:

```
root@Cerberus:/usr/src/linux# ../software-suspend-2.1.9.9-for-2.6.12-ubuntu5.10/apply
Applying 160-wide-vt-fix-separate-submit.patch ...
160-wide-vt-fix-separate-submit.patch will not apply cleanly. Reverse applied patches [Yn]? n
root@Cerberus:/usr/src/linux#
```


Anyone have any ideas?

---

### Post by ashrack on 2006-01-24
SKYE
I have and it works splended.

---

### Post by ashrack on 2006-01-24
SKYE
I have and it works splended.

---

### Post by ashrack on 2006-01-26
GOt hibernation with SWSUP2 working flawlesly on my desktop(see specs in the sig under DESKTOP).
Since am using a SND-CS46XX for alsa which doesn't properly support suspending, I had set the hibernate.conf to reload alsa when restoring from hibernation 
```
/etc/init.d/alsa force-reload
``` which is kinda messy:rolleyes: 
Now onto my questions:
when I do modprobe -r snd-cs46xx I always get the following error:
```
FATAL: Module snd_cs46xx is in use.
```
Is there a way to force the module to unload?


ps. I also tried ```
rmmod -f snd-cs46xx
``` but then the terminal just hangs.

---

### Post by ashrack on 2006-01-28
> Ok I got hibernate to work with the proprietory Nvidia driver..... This however does not allow you to press ctrl+alt+F1 to get to the console.

When you press ctrl+alt+F1 you get a garbled screen, but ctrl+alt+F7 works perfectly, so if you only use X then I have found the solution for you...
Has anyone found a workaround 4 this?

ps. I temporary fix:
I blindly type

```
vbetool vbemode set 3
```

in the terminal in question and it restores it. But it is again garbled when I switch back to X and then back to the terminal.
Is there a way that the upper temporary fix could be set to be done automaticly whilst resume

---

### Post by Griffin3 on 2006-01-28
Hello, skye: I have not tried the patch set against the newest ubuntu 2.6.12.  If it's giving errors, I need to hand-tweak the patchset a bit: I will try to jump on this in the upcoming week.  I have to get a program ready for my consultees, come Monday, so ... after that, hopefully.

Hello, bgalen: I am still using an older kernel, myself.  The way I understand it, most of the little incremental new kernels are the ubuntu people patching around bugs they find, but more than likely if you don't have a problem with the kernel you are using, you aren't even touching the part of the code that has been patched.  Does that make sense?  For instance, one ubuntu patch that I was always working around when I first did this was for a bernoulli drive, which I'm pretty sure 99% of the users here have never heard of.  So, if your current kernel isn't acting goofy, then I wouldn't spend  the hours re-compiling.

---

### Post by Griffin3 on 2006-01-28
ash'rack: People are reading this, but most of us just don't have the nVidia drivers to worry about.  My new laptop (coming in today, yea!) is another ATI, so I still can't even really properly load the nvidia patch, here. :-(

---

### Post by Skye on 2006-01-28
Well, I think my error was a false alarm.  I forgot to thoroughly clean out my /usr/src directory before I attempted a recompile-  I tried it again last night after completely removing everything involved and starting from scratch, and all went fine.  Sorry about that, I should have tested it a bit more before crying error.

Again, thanks to Griffin3 for putting this guide together!

---

### Post by ninocass on 2006-02-03
hi
i had no swap file set up so i followed the guide here:

[http://ubuntuforums.org/showthread.php?t=89782&highlight=swap+space](http://ubuntuforums.org/showthread.php?t=89782&highlight=swap+space)

to add the swap file, which seems to be working, when i type "top" theres stuff going on.

in the menuconfig part i just put /swap_file and when i boot it sayd that /swap file cant be translated to a device, do i need to mount the swap_file?

thanks

nino

---

### Post by RyanGT on 2006-02-03
Don't delete the kernel until you are sure you aren't booting into it.  You need to look at the file /etc/grub/menu.lst.  Toward the end of that file are the menu options you see in grub at boot up.  They should look like this:

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.12-10-686
savedefault
boot

If you were careful to give your new kernel a seperate name, you sould be able to find that kernel name and comment out that entire section.  Once you are sure you are not booting into that kernel and it is removed from the menu.lst, then go ahead and delete it.

As far as that goes, you can leave the kernel and leave it in menu.lst if you are using another kernel and it won't hurt anything - it is just taking up space in your /boot partition which you may or may not care about.  I have several old kernels in there that I never boot into but just haven't deleted yet.

Ryan

---

### Post by jclw on 2006-02-06
[QUOTE=kevin79]I finally got this working. Great tutorial.  I do however have a problem. Will this cause my wifi card to stop working? I'm using the ipw2200 drivers along with wpa_supplicant.[/QUOTE]
no, but you will need to install the firmware into /lib/hotplug/firmware (assuming you have copied the ubuntu .config to your kernel)

---

### Post by Griffin3 on 2006-02-06
re: ipw2200 drivers; I just reinstalled my Ubuntu on a Sony Vaio, with the Intel wireless. Since I installed it from the CD (with the 2.6.12-9-386 kernel) and then updated it automagically through synaptic (with the 2.6.12-10-386 kernel) , I had two copies of the firmware in the /lib/hotplug/firmware directory. Since I did not need the -9-386 stuff any more, I just renamed them to match the new kernel using:
```
cd /lib/hotplug/firmware
rename 's/-9-386/-hibernate/' ipw-2.3*
``` Which completely fixed the wireless drivers, without any other adjustment. Now, if you still needed to have a functioning -9-386 kernel with wireless, you would have to make copies instead of simply renaming them.

I am finding that this ipw2200 card gets smashingly better signal reception than the old D-Link, but I imagine that is more likely because of the built-in laptop antenna. I was also very impressed that the Ubuntu LiveCD did a **flawless** job of recognizing all the hardware on this laptop, including the ridiculous 1920x1200 LCD display. The only bits it had difficulty with are the ALPS glidepoint touchpad (which [http://ubuntuforums.org/showthread.php?t=78904]("http://ubuntuforums.org/showthread.php?t=78904") fixed), and a failure to shut down completely without holding the power button down four seconds (although "reboot=h" in the kernel command line (in grub) fixed this for restarting). Way to go, Ubuntu team!

---

### Post by ninocass on 2006-02-16
is there any loss of usability through doing this ie, synaptic not working etc?

will i need to re apply any themes + settings

Thanks

---

### Post by hil on 2006-02-18
I re-compiled the kernel with the file writer in software suspend enabled. It works fine with me now. The kernel dump and stack trace disappeared. I am using suspend2 1.1.9.9 with ubuntu 5.12 linux kernel 2.6.12. I am satisfied with the results. However, my wireless devices fail to connect after resume. I think suspend2 unload the corresponding device driver modules in the suspend process and load the modules in the resume process. Besides that, sometimes my USB and IBM thinkpad T30 touch pad mouse scroll fail to function after resume. Doing a ```
 $ sudo hibernate -n 
``` could solve the mouse scroll problem. I suggest putting the wireless device reset after resume in the FQA at [http://www.suspend2.net/FAQ]("http://www.suspend2.net/FAQ")

I also noticed that if an application is locking a device file, the suspend fails but still remains in the /var/run/*.pid. I was testing it using Logitech quickcam with xawtv running. If I don't use xawtv, then hibernate works.

---

### Post by ashrack on 2006-02-18
Try using FORCE option in HIBERNATE.CONF that should force all the locked devices to get unlocked.
4 M this works

---

### Post by palomar on 2006-02-19
After hibernating my soundcard (SB Live) doesn't work anymore. How can I enable it?

I've read something about the command "/etc/init.d/alsa force-reload". When I execute it in console, it gets successfully reset, but the sound still doesn't work.

---

### Post by nelposto on 2006-02-24
Hi all,

Since been frustrated and plagued with problems in hibernating with the 2.6.12 kernel, I took a dive into Dapper Flight 4 and had a go at compiling suspend2 (the released version) into a 2.6.15.1 kernel ... which suspended and resumed famously. I then got my wireless working using a method similar to that which griffin describes above (It seems to work slightly differently in dapper, or maybe I just imagine it).

Successfully installed ati fglrx driver 8.22.05 .. and got 3D all good ... but this also breaks hibernation. It appears to be working fine, until 'making atomic copy' or however it's written. It sits at this for a few seconds, and then the progress indicator  disappears and the computer hangs. 

Is there some way I can *disable* fglrx for suspend and resume it after? I tried modprobe -r ing agppart but it's already in use :(

Any help would be uber appreciated

---

### Post by Whoopie on 2006-02-24
Hi,

do you use the hibernate script? If yes, put the following line into your hibernate.conf:

ProcSetting extra_pages_allowance 0

With this setting, I got hibernation with fglrx working.

Best regards,
Whoopie

---

### Post by nelposto on 2006-02-24
[QUOTE=Whoopie]Hi,

do you use the hibernate script? If yes, put the following line into your hibernate.conf:

ProcSetting extra_pages_allowance 0

With this setting, I got hibernation with fglrx working.

Best regards,
Whoopie[/QUOTE]

YES!

It worked!!!

Finally I can't beleive it! .. wireless, fgrlx and hibernate all living in perfect harmony!!

Thanks to Griff for the guide, Whoopie for the final clincher and anyone else whose advice I used!! \\:D/ \\:D/

* Edit: BTW .. I did as suggested in this guide and mapped the powerbutton on my laptop to hibernate - but unfortunately in Dapper this is also somehow mapped to showing a special Log out and other options screen. Probably should ask in the Dapper forum, but in case anyone here knows .. ? *

---

### Post by Whoopie on 2006-02-26
For everone, who likes to get a ubuntu-like suspend2 UI, here a small howto:

1. Install needed packages
```
sudo apt-get install subversion libpng12-dev libmng-dev
```

2. Grab current SVN form suspend2-userui
```
cd /usr/src
sudo svn checkout http://svn.suspend2.net/suspend2-userui/trunk suspend2-userui
```

3. Compile and install it
```
cd suspend2-userui/
sudo make install
```

4. Change your hibernate.conf

You need to adjust the following line in your hibernate.conf.

```
ProcSetting userui_program /usr/local/sbin/suspend2ui_text
```
to
```
ProcSetting userui_program /usr/local/sbin/suspend2ui_usplash
```

5. Create two mkinitramfs scripts (from [http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger](http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger))

/etc/mkinitramfs/hooks/suspend2 with the contents:
```

#!/bin/sh
PREREQ=""

prereqs()
{
      echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
      prereqs
      exit 0
      ;;
esac

. /usr/share/initramfs-tools/hook-functions

if [ -x /usr/local/sbin/suspend2ui_text ]; then
      mkdir --parents ${DESTDIR}/usr/local/sbin 2>/dev/null || true
      copy_exec /usr/local/sbin/suspend2ui_text usr/local/sbin

elif [ -x /usr/local/sbin/suspend2ui_usplash ]; then
      mkdir --parents ${DESTDIR}/usr/local/sbin 2>/dev/null || true
      copy_exec /usr/local/sbin/suspend2ui_usplash usr/local/sbin
fi

```


/etc/mkinitramfs/scripts/local-premount/suspend2 with the contents:
```

#!/bin/sh

PREREQ=""

prereqs()
{
      echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
      prereqs
      exit 0
      ;;
esac

if [ -d /proc/suspend2 ]; then
      echo > /proc/suspend2/do_resume
elif [ -d /proc/software_suspend ]; then
      echo > /proc/software_suspend/do_resume
fi

```

6. Make sure these files have execute permissions or it will not work:
```

sudo chmod +x /etc/mkinitramfs/hooks/suspend2
sudo chmod +x /etc/mkinitramfs/scripts/local-premount/suspend2

```

7. Regenerate the /boot/initrd.img-`uname -r`

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r`
```

8. Suspend and watch your new suspend2 UI.

That's it.

Best regards,
Whoopie

---

### Post by rahmza on 2006-02-26
Hey, I saw earlier in this thread someone had a problem with hibernating with ipw2200 driver. Specifically, the laptop would stop at the shut down stage unless the button is pressed. Maybe this was answered, (and a very quick look tells me no), but in /etc/hibernate/blacklisted-modules file, it needs to be altered to include the ipw2200 driver. The default checks the module version, so if you do this, it always unloads the module and fixed the problem for me.

```
#@ipw2200             0.0        0.20
ipw2200              2.60      2.6.99
```

---

### Post by marcog on 2006-02-28
I get the following error while compiling the kernal (step 14):

[FONT="Courier New"]fs/inode.c:1093: error: static declaration of ‘generic_drop_inode’ follows non-static declaration
include/linux/fs.h:1422: error: previous declaration of ‘generic_drop_inode’ was here
make[1]: *** [fs/inode.o] Error 1
make: *** [fs] Error 2[/FONT]

Any idea what I can do to get it to work? Tried searchin in this thread and on google for the error, but nothing came up. Hope I'm not alone with this one as it has boggled me! :-k

---

### Post by konradsa on 2006-03-01
[QUOTE=rahmza]Hey, I saw earlier in this thread someone had a problem with hibernating with ipw2200 driver. Specifically, the laptop would stop at the shut down stage unless the button is pressed. Maybe this was answered, (and a very quick look tells me no), but in /etc/hibernate/blacklisted-modules file, it needs to be altered to include the ipw2200 driver. The default checks the module version, so if you do this, it always unloads the module and fixed the problem for me.

```
#@ipw2200             0.0        0.20
ipw2200              2.60      2.6.99
```[/QUOTE]

Dude, you are a genius. I had this problem on my laptop, and your tip worked. Please add this tip and the tip that suggests to rename the ipw2200 drivers to the tutorial on page 1. By the way, there is a typo, 2.60 should be 2.6.0!

---

### Post by TheEclypse on 2006-03-25
I have followed the HOWTO and managed to get suspend2 compiled, but when I try to suspend, it stops at the point saying "Writing kernel & process data", and the progress bar content disappears.

Does anybody know what could be going wrong ?

Thanks.

---

### Post by nelposto on 2006-04-02
[QUOTE=TheEclypse]I have followed the HOWTO and managed to get suspend2 compiled, but when I try to suspend, it stops at the point saying "Writing kernel & process data", and the progress bar content disappears.

Does anybody know what could be going wrong ?

Thanks.[/QUOTE]

More info about your setup?

---

### Post by TheEclypse on 2006-04-04
[QUOTE=nelposto]More info about your setup?[/QUOTE]
Forgot to say I think ive solved it.  When I read hibernate.log I found entries saying "argh, out of blocks" or something to that effect, which I took to mean my swap (250mb) was too small to save the images sometimes - so ive reformated with 575mb swap, and its not failed yet...


However, I am having trouble getting ndiswrapper to compile, details of the error are here: [http://ubuntuforums.org/showpost.php?p=889846&postcount=24]("http://ubuntuforums.org/showpost.php?p=889846&postcount=24")

---

### Post by inf0c0m on 2006-04-04
so i did everything as told (least i thought i did), but it does not resume after suspending. it suspends instantly, but does not resume (just does a normal reboot). heres some info:

fs type: reiserFS
dell inspiron 5100 (so it uses hdc as the default instead of hda)

results from the sudo cat /proc/software_suspend/debug_info |grep 'compression\|speed': 
root@devlaptop:/usr/src/linux# cat /proc/software_suspend/debug_info |grep 'compression\|speed'
- Overall expected compression percentage: 0.
- No I/O speed stats available.

results from :lspci | grep 'IDE'
fdisk -l | grep 'swap'

root@devlaptop:/usr/src/linux# lspci | grep 'IDE'
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 02)
root@devlaptop:/usr/src/linux# fdisk -l | grep 'swap'
/dev/hdc3           12042       12161      963900   82  Linux swap / Solaris

so im not entirely sure which kernel option to choose.

any other info needed? Thanks,
Eric

---

### Post by GarethMB on 2006-04-07
Hi i'm a laptop user and i'm considering trying this. But first i have a few questions.

What seems to be the success rate of suspend2?
How complicated/risky is compiling a new kernal (i don't understand any programming languauges)?
Is this issue with hibernation going to be solved in any future releases, specifically Dapper or Dapper+1? I had a poke around on the wiki but didn't find anything that seemed conclusive.

Thanks

Gareth.

---

### Post by Griffin3 on 2006-04-08
Success rate on Suspend2 seems to be fairly good, especially now that all these folks have added bits about how to deal with the proprietary video drivers. It seems to work at least as well as the kernel suspend in nearly all cases, often much faster, and usually doesn't break anything badly (meaning that, if it doesn't work for you, you can just boot back into your original kernel and be exactly as you used to be.) I'm showing 1529 distinct downloads of the Ubuntu patch, compared to the several dozen problem reports here. I AM trying to find enough time to streamline it for Dapper Drake, roll in all the how-tos and hints&tips that people have added on here, and pointers to the other howtos, maybe see if I can't roll up the more common kernels as .deb packages. No promises.

The instructions are step-by-step, but if it doesn't work for you, you do need to be fairly computer literate in order to troubleshoot what is wrong. Nothing like real programming, as much as just digging into the internals of the .log files and figuring out where linux puts everything. And why. And randomly adjusting settings to see if they fix the problem.

Finally, I recall a discussion on one of the news groups a LONG time ago about the crack-smokingness of the suspend2 programming team; but since then apparently they've agreed to the reasoning of the linux team somewhat, have separated some the suspend2 innards out into user space and fixed up the code where it is not spiderwebbing all over the kernel so aggressively [my untrained analysis]. As it is, more and more of the suspend2 package seems to be already rolled into the kernel (or the debian version, anyway), which is nice because it makes the ubuntu patchset smaller. Eventually, it will be merged into the linux core, I imagine ... or the linux suspend will incorporate much of the features of Suspend2. But in a cursory search, I cannot find any recent news on how this merge is coming along. [I imagine sending a bit of the ol' monetary contributions to Nigel wouldn't hurt, seeing how he's gathered quite a sharp team to work on this over at suspend2.net, and you know how programmers need fuel.]

---

### Post by beanlover on 2006-04-25
Just want to report I have suspend2 working as outlined in this thread...thank you very much to all!

I have an HP ze4610us laptop and I didn't need to do anything out of the ordinary.  I did have a couple of dry-runs with my compile process because I didn't know the difference between <M> and <*> in the menuconfig.  Once I got that all sorted out I cleaned up my grub menu and was good to go.

Thanks again!

I even checked to see if my Synaptics touchpad would have the issues with the touch-scroll and the tap-and-drag as reported in this thread.  No issues there after unsuspending.  I did actually have that issue with Windows XP (the original OS installed on this laptop) so it's good to see that is NOT happening here.

Been using Ubuntu for about a month and a half now...if I can help it I'll never go back!  With all the hard working folks associated with Ubuntu I don't think that will happen.

B

EDIT: Well..ran into a MAJOR snafu.  Not sure if it's related to suspend2 or not but that was the last change I had made prior to my issues.  Here are the sequence of events:

1)Suspend to swap (as usual)
2)Boot to my previous kernel I was using prior to compiling in suspend2
3)Repeat step 2 a few times under normal use circumstances
4)Boot using suspend2 kernel

At this point I got something about missing magic number and that my root system needed to be fsck-ed (I'm thinking it already was ;) ).

So I did that...no joy.  Reboot...Grub error 17.  
Followed some basic instructions on these message boards to fix that...ended up with an error 15 after that.

So I reinstalled.  Not sure if it had anything to do with suspend2 or not but, just in case, don't try what I tried unless you want to try to reproduce this error.  I ended up having to reinstall. :(

---

### Post by geek.de.nz on 2006-04-30
Hi, this is great, the only feature I was missing in Linux is now (as usual) better and quicker than in windoze. Thank you guys for this.

However, my USB external hard-drive unmounts every time, I suspend2 disk, which makes it a bit tedious to remount it every time (sudo mount -a). Also, I get error messages every time I reload the computer about /dev/sda trying to automatically load in konqueror. If someone could at least tell me how to get rid of the error messages, I would be even more happy than now :-).


Also, when I (normal) boot the hibernation kernel image, I always have to press <control+D> to skip the error message that a partition wants to be checked (fsck.ext3; also on the external USB HD). This is not the case when I boot the out-of-the-box kernel of my kubuntu installation. Any ideas?

Disabled some of the unnecessary modules etc from the kernel as well and compiled in my VIA... IDE controller (not as module) and everything runs so much faster (hdparm -d1 ... etc.) :cool: .

---

### Post by ashrack on 2006-04-30
[QUOTE=geek.de.nz]However, my USB external hard-drive unmounts every time, I suspend2 disk, which makes it a bit tedious to remount it every time (sudo mount -a).Then why dont U put in 
[/QUOTE]
```
"/etc/hibernate/hiber.conf"
```
the following line(ATM am in Win2k so I have to do this by mind)But it should look similar:
```
On resume 20 mount -a
```

---

### Post by geek.de.nz on 2006-04-30
OK, thanks very much. Didn't know where to look at first.

But you probably mean OnResume in /etc/hibernate/hibernate.conf.

What I found on 'man hibernate.conf':

```

       OnResume NN <program to execute> [parameters for program]
                 Executes  a given program after resuming. NN is a number between 00 and 99, inclusive - a higher number means the program will be exe&#8208;
                 cuted earlier in the resume process. See the ORDERING section in the SCRIPTLET-API for details.

```


Thanks again for the quick reply. :-)

---

### Post by geek.de.nz on 2006-05-01
This doesn't seem to work. My partitions are not mounted. I even tried:
```
OnResume 99 mount -a
```
but did not help. Any ideas?

---

### Post by shof2k on 2006-05-04
Great guide! 
I got hibernate working with the noapic boot option. Unfortunately this knackers my sound, but I think that's an IRQ sharing problem.  Will try and use irqtune to balance this (Is there an easy way to manually assign IRQs?).  Also hibernate time is ~1min because the IDE chipset isn't available to the kernel :(

It'd be great if this made it into the kernel tree.

H/ware: 
I-friend nc202i4 laptop
PIV 2.0Ghz, 512MB ram, 80GB HD

---

### Post by grizzly on 2006-07-19
Hey odes this guide stilll hold for dapper?

---

### Post by Griffin3 on 2006-07-19
No, sorry, this patch definitely does NOT work for Dapper.  And in my limited experimentation, I was not able to hack the suspend2 patch to work with Ubuntu/Dapper; though you can still patch a raw kernel and get it to work that way.  Right now, real life is running me over, but if I get some free time coming up, I will try to revisit this project.

---

### Post by anasofiapaixao on 2006-07-19
Not sure if anyone has found this yet, but in case you can't get back from suspension/blank screen on a Toshiba laptop, I find that adjusting screen brightness works like a charm (Fn+F5 or F6 or whatever). Off topic but important to say ;)

---

### Post by kev23777 on 2007-10-28
I must be doing something wrong....

kevin@kevin-laptop:~$ sudo apt-get -y install linux-tree-2.6.12
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-tree-2.6.12

---

### Post by dninja on 2007-10-29
> **kev23777 said:**
> I must be doing something wrong....

kevin@kevin-laptop:~$ sudo apt-get -y install linux-tree-2.6.12
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-tree-2.6.12


Are you sure you don't want this:
kernel-tree-2.4.27 - Linux kernel source tree for building Debian kernel images

it is the only thing in the repo whose name seems to come close to what you are looking for but it is a 2.4 kernel not a 2.6 one.

---

### Post by Griffin3 on 2007-10-29
Hello, Kevin.   I'm afraid this HOW-TO applies to Breezy, and is several versions out-of-date.  But, there's good news:

Starting from fiesty, you can install Suspend2 by adding a line to your repositories, then just install the suspend2 package.  This almost replaces my entire how-to on the subject; you still have to make a change to the kernel bootup line in grub, on some machines, but for the most part, it's an automated install.  

I'll try to write up a how-to for gutsy if I get some free time today (if no-one has beat me to it.)

---

### Post by nprobably on 2008-04-19
> **Griffin3 said:**
> Hello, Kevin.   I'm afraid this HOW-TO applies to Breezy, and is several versions out-of-date.  But, there's good news:

Starting from fiesty, you can install Suspend2 by adding a line to your repositories, then just install the suspend2 package.  This almost replaces my entire how-to on the subject; you still have to make a change to the kernel bootup line in grub, on some machines, but for the most part, it's an automated install.  

I'll try to write up a how-to for gutsy if I get some free time today (if no-one has beat me to it.)


Hey!  I'm actually trying to install tuxonice on Hardy. I've been trying to build a custom kernel, no luck.....  I spent 30+ hours on this thing already..   : (

(my machine doesn't power down..)

could you tell me how to config the repositories to get the automated package??

---

### Post by freonchill on 2010-07-25
2 different variation of questions that ask somewhat the same thing

1. has anyone ever actually been able to resume from either suspend or hibernate using older nvidia drivers (96.xx) in ubuntu (been trying since 7.xx, still doesnt seem to work (out of the box), now on 10.04)?

2. does this work - would really like to get nvidia proprietary driver working (so my gui looks decent, flash videos play without flashing, etc) and have the ability to suspend / hibernate...

thanks (sorry for resurrecting this 2 year old thread, but it seems that it **could** work...

---

### Post by Griffin3 on 2010-07-25
Wow.  Did I write this?  It seems like another lifetime.  Oh, yeah, I had a couple kids in the meanwhile ... 

As I understood it, the 96.xx series of nvidia drivers just didn't have the proper suspend/revive hooks, and no amount of kernel adjustment would make it work.  The newer nvidia drivers put in the appropriate library functions, or debugged them, or whatever ... so upgrading your nvidia driver would really be the way to go.

If you have old hardware and can't upgrade your driver, I understand this is of absolutely no help to you.  But that is the solution.  And the diaper fumes have pretty much erased my understanding of the kernel suspend interface ...

---

### Post by freonchill on 2010-07-25
Griffin3

thanks for getting back to me
i have an older geforce 4 4200 mobile card (best driver i can get is the 96.xx)

its a laptop so its somewhat hard to "upgrade"

the question is - i have a very similar laptop, which has a geforce 5 5200/5600 mobile (nv31 / nv34)

which based on nvidia's website - 173.14
do you know (or can point me in the direction) of whether this newer card / driver has support before moving hardware around to test the theory?

thanks,

---

