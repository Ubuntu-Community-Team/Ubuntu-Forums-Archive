---
title: "HOWTO: Get Ubuntu 10.04 working properly on the Toshiba A505 laptop"
date: 2010-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by purelinuxuser on 2010-06-06
[SIZE=4]**HOWTO: Get Ubuntu 10.04 working properly on the Toshiba A505 laptop**[/SIZE]

For those of you who are struggling getting Ubuntu working with the Toshiba A505 laptop (myself included), I've decided to write a step-by-step guide in the Tutorials & Tips section.  The problems with this laptop and the various obscure fixes are described in this thread: [http://ubuntuforums.org/showthread.php?t=1470732](http://ubuntuforums.org/showthread.php?t=1470732).

[SIZE=3]**Table of Contents**[/SIZE]

[LIST=1]
[*]Background Information
[*]Step 1: Actually getting Ubuntu installed!
[*]The Easy Way: Installing kernel 2.6.35-rc1
[*]The Hard Way: Recompiling the stock kernel with the copy_dsdt patch
[/LIST]
[SIZE=3][B]1.0 - Background Information
[/B][SIZE=1]
Basically, the crummy BIOS built into the A505's motherboard messes up the DSDT frames and causes Linux (but apparently not Windows 7 :-s) to go crazy.  Various things are broken including graphics, USB (**!**) support, internal webcam, and ACPI (**!**) support (aka no power management).

To get around this, a kernel patch was created that forces the kernel to reproduce each DSDT frame to avoid errors.  Unfortunately, this patch did not make it into the stock Lucid kernel, so those affected are left with two options: install a newer kernel or recompile the old one with the patch included.

[/SIZE][/SIZE][SIZE=3]**2.0 - Step 1: Actually getting Ubuntu installed!**[/SIZE]
[SIZE=3][SIZE=1]
Okay, the first thing you'll see when you boot the Ubuntu live CD is a BSOD (black screen of death).  Lovely, isn't it? ;)
[/SIZE][/SIZE]
[LIST=1]
[*]As the live cd boots, there should be a (rather low-resolution) boot screen with a keyboard and an accessibility icon on it.
[IMG]http://humphreybc.files.wordpress.com/2010/03/livecd14.png[/IMG]
[*]Press any key and you should be taken to a main menu, just like earlier releases of Ubuntu. :D
[*]Press F6 (Other Options) and be sure "Safe Graphics Mode" is **checked**.  Then hit 'Try Ubuntu without installing" or "Install Ubuntu" depending on your preference.
[*]Ubuntu and/or the installer should fire up with graphics working- albeit in low-res mode. :(
[*]Install Ubuntu normally, then proceed to one of the following two sections.
[/LIST]
[SIZE=3]**3.0 - The Easy Way - Installing kernel 2.6.35-rc1**[/SIZE]

[LIST=1]
[*]First things first, we'll have to get around the BSOD (black screen of death) that you see booting your "brand new OS!"  Unlike the live CD, the installed version of Ubuntu 10.04 has no "safe graphics mode."  Instead,
[*]Hold SHIFT as you start your computer.  After a few seconds, you should see a menu asking you which operating system to boot.  Just go to the top option and press "E."
[*]Use the arrow keys to move the cursor to the end, and then type a space and "nomodeset."
[*]Press ENTER to boot, and Ubuntu should boot normally (again, in low-resolution mode).
[*]If you can, plug your laptop into Ethernet to get an Internet connection.  Otherwise, download the following packages on another computer and transfer them using a flash drive.
[*]Download the 2.6.35 version of the Linux kernel at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc1-lucid/"):
[LIST]
[*]Download the package "linux-headers-2.6.35-020635rc1-generic_2.6.35-020635rc1_**[ARCH]**.deb," where **[ARCH]** is i386 (32-bit) or amd64 (64-bit).
[*]Download the package "linux-headers-2.6.35-020635rc1_2.6.35-020635rc1_all.deb."
[*]Download the package "linux-image-2.6.35-020635rc1-generic_2.6.35-020635rc1_**[ARCH]**.deb," where **[ARCH]** is i386 (32-bit) or amd64 (64-bit).
[/LIST]
 
[*]Place all three packages under your Downloads folder.
[*]Open a Terminal (Applications > Accessories > Terminal) and type the following commands:
```
cd ~/Downloads
sudo dpkg -i *.deb
```**IMPORTANT: When you type the second command, you will be asked for your "sudo" password.  Just type your normal login password, however you will NOT be able to see any characters (including *s).**
[*]Close the terminal, and press Alt+F2.
[*]Type
```
gksudo gedit /etc/default/grub
```and click "Run."
[*]Browse for the line that says "GRUB_CMDLINE_LINUX=."  In the quotes, add "acpi=copy_dsdt" (without the quotes).
[*]Open another terminal and type
```
sudo update-grub
```
[*]Reboot, and hopefullly everything will work properly! :D
[/LIST]
After the new kernel is installed, you may find that wireless does not work.  In that case you will have to download and install the drivers from realtek.  Please do this on your own, I don't have time to write a  new tutorial.
:lolflag:
[SIZE=3][B]3.0 - The Hard Way: Recompiling the stock kernel with the copy_dsdt patch
[/B][SIZE=1]
This method [/SIZE][/SIZE]involves recompiling your kernel with the copy_dsdt patch applied manually.  It involves a fair amount of work in the command line, so be prepared for *a lot* of typing.

[LIST=1]
[*]Perform steps 1 - 4 in the section above to get Ubuntu booted up.
[*]Plug your laptop into Ethernet to get an Internet connection.
[*]Open a Terminal (Applications > Accessories > Terminal).
[*]Follow the steps at [http://ubuntuforums.org/showpost.php?p=9317100&postcount=11](http://ubuntuforums.org/showpost.php?p=9317100&postcount=11) to recompile your kernel.
[/LIST]
____________________

Well, that's pretty much it!  Post back with any problems/suggestions/comments you guys might have. ;)

---

### Post by markos7007 on 2010-06-08
So far so good thanx. havent gotten the wireless connection yet but im workin on it. but after loading the new kernal it seems my screen is like flashing well its like acting weird i dont know how to explain it.  Its not like that tho when i load up the other non modified kernal or windows 7, any ideas

---

### Post by zeus77 on 2010-06-11
Wow, thanks a lot.

Just one question -- when reinstalling a new kernel (i.e. the easy option), do you think it is sufficient to install one of the v2.6.33 kernels instead of the newer v2.6.35?  For example, the ones available here --
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/)

Maybe I'm wrong, but part of me wonders if the 2.6.33 kernel has received more testing, and may be less prone to breakage... plus, it's less of a jump from the stock 2.6.32 lucid kernel.  Anyway, bottom line: anyone know if the 2.6.33 kernel will work?

Many thanks!
zeus77

---

### Post by kenaih on 2010-06-11
> **zeus77 said:**
> Wow, thanks a lot.

Just one question -- when reinstalling a new kernel (i.e. the easy option), do you think it is sufficient to install one of the v2.6.33 kernels instead of the newer v2.6.35?  For example, the ones available here --
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/)

Maybe I'm wrong, but part of me wonders if the 2.6.33 kernel has received more testing, and may be less prone to breakage... plus, it's less of a jump from the stock 2.6.32 lucid kernel.  Anyway, bottom line: anyone know if the 2.6.33 kernel will work?

Many thanks!
zeus77

Hi zeuz77,

I don't think so.

The CHANGE file doesn't show anything about the DSDT copy patch. 
But it will probably be added in future *.33 versions

So, the way you check out for yourself whether a specific kernel version will have the needed patch or not is simply looking for ACPICA changes regarding the DSDT tables at that file.

i.e in the 2.6.35 CHANGE file you get this:
      ACPICA: Update DSDT copy/detection.

---

### Post by gloria0227 on 2010-06-26
> **markos7007 said:**
> So far so good thanx. havent gotten the wireless connection yet but im workin on it. but after loading the new kernal it seems my screen is like flashing well its like acting weird i dont know how to explain it.  Its not like that tho when i load up the other non modified kernal or windows 7, any ideas


I am also having the same flickering type thing with my display.  Any ideas?

---

### Post by theviking10 on 2010-06-28
Hullo! After installing the basic system I am unable to find a login menu - I get the default background and control of the mouse - nothing else. Is this a typical problem for laptops of this type? I am using a Toshiba A505 S6005.

---

### Post by gloria0227 on 2010-06-28
> **theviking10 said:**
> Hullo! After installing the basic system I am unable to find a login menu - I get the default background and control of the mouse - nothing else. Is this a typical problem for laptops of this type? I am using a Toshiba A505 S6005.

Are you using 9.10 as your profile says or are you using 10.04... with 10.04 on the S6005 you should not have this problem... I dont.

---

### Post by theviking10 on 2010-06-28
> **gloria0227 said:**
> Are you using 9.10 as your profile says or are you using 10.04... with 10.04 on the S6005 you should not have this problem... I dont.

I used 9.10 until I got my new laptop this april (the toshiba). I have been attempting to install 10.04 since.

However, yes - after installing the base system there is no login menu upon reboot. (however, there are the characteristic three drumbeats)

I have been logging in with ctrl+alt+F2. I am attempting your fix this Wednesday. (I have business on my windows machine to complete before then) Hopefully the new kernel will not have this issue.


An additional question: I have had much more success with Linux Mint on this machine. Do the kernel ppa archives for lucid support the new Mint as well?

---

### Post by theviking10 on 2010-06-30
> **theviking10 said:**
> I used 9.10 until I got my new laptop this april (the toshiba). I have been attempting to install 10.04 since.

However, yes - after installing the base system there is no login menu upon reboot. (however, there are the characteristic three drumbeats)

I have been logging in with ctrl+alt+F2. I am attempting your fix this Wednesday. (I have business on my windows machine to complete before then) Hopefully the new kernel will not have this issue.


An additional question: I have had much more success with Linux Mint on this machine. Do the kernel ppa archives for lucid support the new Mint as well?




HUZZAH! It works! Thank you! Now to deal with the flickering and wireless . . .

---

### Post by Threat Blvd on 2010-06-30
> **gloria0227 said:**
> I am also having the same flickering type thing with my display.  Any ideas?

I too am having the weird flickery screen after following this HOWTO. It's so bad it gives me a headache. Can the OP acknowledge this issue and let us know if there's a way to fix it? My Toshiba (Satellite A505-S6005) has the Intel graphics chipset, do others have a different one?

---

### Post by theviking10 on 2010-06-30
Do we need to install certain packages to install the wireless driver?

---

### Post by Threat Blvd on 2010-06-30
> **theviking10 said:**
> Do we need to install certain packages to install the wireless driver?

See this post: [http://ubuntuforums.org/showpost.php?p=9446203&postcount=35]("http://ubuntuforums.org/showpost.php?p=9446203&postcount=35")

---

### Post by gloria0227 on 2010-07-17
> **Threat Blvd said:**
> I too am having the weird flickery screen after following this HOWTO.


Has anyone been able to figure out how to get rid of the flickering yet?

---

### Post by JayminP on 2010-07-28
hey guys about the flickering...
i did try to install ubuntu on Toshiba a505 but didn't do this tut...

..if flickering only occurs during full screen video playback...(only on flash?)...

to solve the problem go to youtube..and pick a vid...right click and go to setting...then uncheck hardware acceleration...possibly restart pc if needed... 

let me know whats the result...again i could be wrong :( but it fix my problem

---

### Post by JayminP on 2010-07-28
Hi Guys there is no more need for getting around there is easy way....

i downloaded new ubuntu 10.10 alpha (maverick) its easy...just put on flash drive....boot it...pick first option..(for testing)....& wireless works perfectly with no need for driver...battery works perfect too.. :)

i have core i7 so it detects all 8 cores(4 real, 4 virtual)....everything is COOL now & perfect...

tx to new kernel 2.6.35 & ubuntu....

i will make new post so everyone knows that has Toshiba because it was real pain...

:popcorn::popcorn::popcorn:

---

### Post by Bildo Baggins on 2010-07-31
Sup fellas. Got the Linux bug again and it looks like things have progressed a bit since my last load. I have a Toshiba A505-6986 and was wondering what the latest was on the wireless et al issues. Is 10.10 the ticket?

---

### Post by JaSoN369 on 2010-07-31
hello all my first post here. I followed the easy kernel install to the "T" and get these messages on boot up.
4.899860] corrupted low memory at ffff880000006118 (6118 phys) = 040000
4.899906] corrupted low memory at ffff880000006198 (6198 phys) = 040000
4.899979] memory corruption detected in low memory

there is also another message that pops up but its go's away to fast for me to read.

i also did a memory test from the live cd it went 2 passes with 0 errors.

everything seems to work fine but that message concern me ( i did not get this message on 2.6.32)

toshiba a505 s6960
4 gig ram
120 ocz agilty ssd
2.10 intel core2duo
                                                                thanks, Jason

---

### Post by JayminP on 2010-07-31
10.10 is the perfect ticket...works eveything even the touchpad turn of btn & webcam...even with alpha im surprised...no extra install needed for ANY driver....

im still gone wait for 10.10 tho...

:KS Ubuntu 10.10 :KS

---

### Post by gloria0227 on 2010-08-04
Up until today 2.6.32-24-generic fixed all of the problems.  Has anyone else had any success with 2.6.32-24-generic?

---

### Post by zloy_smiertniy on 2010-08-06
Hell-o!! thanks for this post it was absolutely helpful, I was just wondering you figured out this on your own? it is great!! it worked just great. thanks

---

### Post by GeneBrotherton on 2010-08-20
Purelinux, do you think will this method work for the A505 6025 model?

---

### Post by JaSoN369 on 2010-08-23
i resolved my issue on post #17 with a bios update . Afterwards i received a update stating "pci 0000:04:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref] " this error can be fixed if lan is connected or disable lan in bios.

---

### Post by JayminP on 2010-08-24
Wonder if its possible to download & install really easy way from package manager...search for linux-image-x.x.x-generic....& uninstall old once after restart & that would update grub by it self too...

???

---

### Post by coreyh on 2010-08-25
@purelinuxuser:

your instructions worked perfectly for my Satellite C650.  Thanks.

---

### Post by andydch on 2010-09-23
i get this error

```
drivers/acpi/acpica/tbxface.c:58: error: conflicting types for ‘acpi_tb_copy_dsdt’
drivers/acpi/acpica/actables.h:112: note: previous declaration of ‘acpi_tb_copy_dsdt’ was here
drivers/acpi/acpica/tbxface.c: In function ‘acpi_tb_load_namespace’:
drivers/acpi/acpica/tbxface.c:593: error: void value not ignored as it ought to be
make[4]: *** [drivers/acpi/acpica/tbxface.o] Error 1
make[3]: *** [drivers/acpi/acpica] Error 2
make[2]: *** [drivers/acpi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.35.2'
make: *** [debian/stamp/build/kernel] Error 2

```

how to solve this?

Thanks

---

### Post by soad6 on 2010-09-23
or you could just install the 10.10 beta and quit trying to deal with all the problems. 10.10 fixes all the acpi issues and the issues with the graphics card. Im running it right now, with only one minor issue, with the kernel that when i plug in a wifi usb card i cant use it for aireplay-ng cuz it sets it to channel -1 but i think i may have found a patch for that.

---

### Post by andydch on 2010-09-24
> **soad6 said:**
> or you could just install the 10.10 beta and quit trying to deal with all the problems. 10.10 fixes all the acpi issues and the issues with the graphics card. Im running it right now, with only one minor issue, with the kernel that when i plug in a wifi usb card i cant use it for aireplay-ng cuz it sets it to channel -1 but i think i may have found a patch for that.

ok Soad6, i will try ubuntu 10.10

thanks

---

### Post by andydch on 2010-09-30
> **soad6 said:**
> or you could just install the 10.10 beta and quit trying to deal with all the problems. 10.10 fixes all the acpi issues and the issues with the graphics card. Im running it right now, with only one minor issue, with the kernel that when i plug in a wifi usb card i cant use it for aireplay-ng cuz it sets it to channel -1 but i think i may have found a patch for that.

Hi Soad6, I still have to set acpi=off when boot with 10.10 beta so only 1 core processor run but wifi & bluetooth work properly :)

My laptop is Toshiba L510 with intel core i3
Do u have any suggestion for me?

Thanks

---

### Post by Bucky Ball on 2010-11-04
andydch, use this instead if still having problems. You will get a few things back probably:

```
 acpi=copy_dsdt
```I have 10.10 running beautifully on brand new Satellite Pro L510 with this command in /etc/default/grub. Only problem now is wireless slipping from 100% perfect to 50% randomly. Fan started behaving immediately and the volume dial on the front started working and showing on the desktop when I moved it. 

I am in Australia and have this model: PSLGXA-002002.

---

### Post by andydch on 2010-11-04
> **Bucky Ball said:**
> andydch, use this instead if still having problems. You will get a few things back probably:

```
 acpi=copy_dsdt
```I have 10.10 running beautifully on brand new Satellite Pro L510 with this command in /etc/default/grub. Only problem now is wireless slipping from 100% perfect to 50% randomly. Fan started behaving immediately and the volume dial on the front started working and showing on the desktop when I moved it. 

I am in Australia and have this model: PSLGXA-002002.

thanks Bucky, it works and everything running well. :guitar:

---

