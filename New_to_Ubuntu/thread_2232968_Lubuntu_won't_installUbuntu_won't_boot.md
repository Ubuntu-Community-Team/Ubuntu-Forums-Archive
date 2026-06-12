---
title: "Lubuntu won't install/Ubuntu won't boot"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by Nimono on 2014-07-05
I have a desktop with a currently-broken windows 7 install on it, and I'd like to install ubuntu to check on my files and see about fixing it. I've tried to run both Lubuntu from USB, and Ubuntu from USB and disc, but neither method works. Lubuntu USB gets to the screen asking if i want to try or install, but both options give me a perpetual black screen with a blinking _ cursor, and my USB drive's light turns off at this point. Ubuntu USB gives me the opening purple screen, but afterwards goes to tye black screen, then to windows boot options after a few seconds. CD Ubuntu doesn't even show the purple screen, going straight to the issue the USB version has.

I have 3gb ram, an eMachines motherboard, an Intel processor I forgot the specs of, and an Nvidia GeForce graphics card. My USB drive is 2gb (effective 1.86) and the CD is a DVD+R. The last Ubuntu install I tried was on the disc, and it was 64-bit; I had the Universal USB Installer get me the USB .isos automatically, so I have no clue what type they are. I've tried disconnecting the graphics card, but it did not help, nor did the boot option in lubuntu these forums said might fix the issue. I'm really confused about why this is happening. I've asked my friends for help, but they're just as confused, so I turn to all of you for help.

---

### Post by jp734 on 2014-07-05
It might just be how the OS is copied to your USB flash drive. I would download the ISO instead of letting the program doing it for you, then check the md5sum and use unetbootin to install it on your flash drive. I've never had any problem with unetbootin and lubuntu

---

### Post by JeQhdMD on 2014-07-05
I recently installed Linux on a friends old HPtx100us laptop.  It has similar specs to what you're describing (except it only as 2 gigs of RAM).   Anyway, I didn't have much luck with the official "Ubuntu" Unity install media.   Finally, I looked for a version of Linux more expressly designed for older systems.  I downloaded "Linux Lite 2.0" from the distrowatch.com website, created a Live DVD, and used that to install on the HP laptop.  The install went super-smooth.  No video issues as it by default used the nouveau graphics driver.  In this situation, Linux was/is the ONLY operating system on the PC (making the install brain-dead super easy).   BTW - Linux Lite IS based on Ubuntu 14.04 and uses the same repos, and has the same support cycle.  ;)

Now, it seems, in your case, you need or want a dual-boot install.  That is a bit more involved, especially depending on whether the machine has traditional bios or the new (last 3 - 4 years) UEFI/GPT bios.   If the PC uses UEFI . . . you have some reading/homework to do.   If you use a traditional bios, the process I described above will work depending on if you:

>   cleaned up Win7 fragmentation (e.g., defragged hdd once or better, twice)
>   used the Win7 tools to "shrink" the Win7 partition to about 50% of it's size (then booted back to windows twice so windows will run filecheck and then reboot normally)
>   This will create an "unallocated" space of about 50% on the hdd (I prefer to format it now using a Live Linux CD to a recognized Linux file system such as ext4 (this makes it easier to "see" when the installer wants you to choose where to install  - I usually also create a small "swap" partition so I don't have to do it later - - anywhere from 2 to 4 GB will usually do)
>   Use the Live (in this case Linux Lite CD) to step through the install (be careful not to choose "install alongside"  - - instead, choose the last option "something else") which is a custom install allowing you to put Linux exactly at sda "x" where x is the parttion id such as sda5
>   When you get to the partitions screen on the official install DVD - be sure to "edit" the linux partition as the installer insists on you "re-creating" the ext4 partition again, - - then where it asks where to mount, choose "/" (root)
>   After the step above, the rest of the install is usually super easy - just follow the prompts.

Lastly, I've always found it VERY useful to have a FAST live CD for previewing and setting up partitions ahead of the install.   My personal favorite is "Parted Magic" as it runs super fast (from RAM) and has just the right tools for you to do what's needed.  Plus it's a good rescue tool for broken OS's (WIndows or Linux).   The only caveat re using Parted Magic, is the creator of that distro has now gone to a "pay" model to obtain the iso (it's minimal, like $5 or so), and well worth it IMHO (by the way, I'm not connected in any way to that distro or the developer).

Well, good luck, . . . . i hope this helps and doesn't confuse things . . . but I wish I had access to this basic info a couple time when I was learning how to install Linux back around 2003/2004.

---

### Post by Nimono on 2014-07-05
> **jp734 said:**
> It might just be how the OS is copied to your USB flash drive. I would download the ISO instead of letting the program doing it for you, then check the md5sum and use unetbootin to install it on your flash drive. I've never had any problem with unetbootin and lubuntu
I used the unetbootin with ubuntu, but it's still doing the same thing. It's frozen SOMEWHERE, I guess... I just selected 'help', and it stops after displaying the following:

```
[    3.572026] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
```
what does this mean?

EDIT: also, to the above poster: i never changed the size of the windows partition because i never needed to before, and now i can't get in.

---

### Post by Bashing-om on 2014-07-05
Nimonol Hi ! My welcome to the Forum.

As you are certain that the liveUSB is viable, next in my opinion is a graphics driver issue.
Try this:
Boot the liveUSB, as soon as the bios screen clears depress and hold the right -shift- key -> language screen; escape key to accept the default -> boot options screen -> F6 key for the preset options.
Arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time. Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
If you are able now to boot to the desktop, we can direct on installing the required graphics driver with the "Additional Drivers" utility.

One thing at a time, process of isolation
[INDENT][INDENT]gets you up and running ubuntu
[/INDENT][/INDENT]

---

### Post by Nimono on 2014-07-05
> **Bashing-om said:**
> Nimonol Hi ! My welcome to the Forum.

As you are certain that the liveUSB is viable, next in my opinion is a graphics driver issue.
Try this:
Boot the liveUSB, as soon as the bios screen clears depress and hold the right -shift- key -> language screen; escape key to accept the default -> boot options screen -> F6 key for the preset options.
Arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time. Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
If you are able now to boot to the desktop, we can direct on installing the required graphics driver with the "Additional Drivers" utility.

One thing at a time, process of isolation[INDENT][INDENT]gets you up and running ubuntu
[/INDENT]
[/INDENT]

This is that 'option' I mentioned earlier that I tried, but forgot the name of. nomodeset did not fix the issue, it won't boot, :(

Furthermore, I have more information. The machine my motherboard and processor came from is an eMachines EL1582G-52w. Does this have anything to do with my issues? Also, money is currently very tight so I can't afford any replacement parts at all...

---

### Post by Bashing-om on 2014-07-05
Nimono; Hummm ...

Pretty decent little box you have there, according to the specs.
OK, We have a booting issue, what version of Windows came pre-installed on it ? Maybe we are having to cope with UEFI and secure boot on the later releases of Windows ??

Don't know yet
[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by Nimono on 2014-07-05
> **Bashing-om said:**
> Nimono; Hummm ...

Pretty decent little box you have there, according to the specs.
OK, We have a booting issue, what version of Windows came pre-installed on it ? Maybe we are having to cope with UEFI and secure boot on the later releases of Windows ??

Don't know yet[INDENT][INDENT]just a thought
[/INDENT]
[/INDENT]

Windows 7 Home Premium, 64-bit. That partition currently will not boot, which is why I wanted to use Ubuntu. Oh, by the way, how do i change the boot option when I've used unetbootin? That's the one thing I can get to the boot options screen on without knowing how to enable nomodeset; it doesn't launch the standard ubuntu startup. (Should I try another USB burner?)

---

### Post by Bashing-om on 2014-07-05
Nimono; Welp,

Re-ordering the boot priority differs with each manufacturer ( and version). I have no idea what that particular procedure would be in the eMachines EL1582G-52w . 

Later Windows 7 also had UEFI for booting vice the legacy MBR method. And the method to set up what boots where is totally different;
In your setup routines, do you see any references to such things as UEFI, EFI, secure boot, rapid boot ?
IF NO, we are looking at the legacy booting, such that some key on the keyboard gives access to the bios set up utility to change the boot priority.

So our first step is to determine the method that you are booting. Then I have never used unetbootin, so can not advise.

Presently you are not able to boot anything on that box ? How are you now communicating with the forum ? ( what means are at our disposal to make up a new install medium) 

[INDENT][INDENT]look'n for a way
[INDENT][INDENT][INDENT]to make it happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Nimono on 2014-07-05
> **Bashing-om said:**
> Nimono; Welp,

Re-ordering the boot priority differs with each manufacturer ( and version). I have no idea what that particular procedure would be in the eMachines EL1582G-52w . 

Later Windows 7 also had UEFI for booting vice the legacy MBR method. And the method to set up what boots where is totally different;
In your setup routines, do you see any references to such things as UEFI, EFI, secure boot, rapid boot ?
IF NO, we are looking at the legacy booting, such that some key on the keyboard gives access to the bios set up utility to change the boot priority.

So our first step is to determine the method that you are booting. Then I have never used unetbootin, so can not advise.

Presently you are not able to boot anything on that box ? How are you now communicating with the forum ? ( what means are at our disposal to make up a new install medium) 
[INDENT][INDENT]look'n for a way[INDENT][INDENT][INDENT]to make it happen
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

I know there's a Quick Boot option, and another boot option below it i forgot the name of, both are enabled by default, and i have USB and CD set to boot before the hard drive. As for communication, I'm using my Wii U's internet browser, but did all my downloading on my parents' laptop. I have nothing else on my computer to boot into; windows 7 is all that's on it, no discs for anything else but the windows 7 repair disc, which freezes just like windows 7 itself; it may be loading the corrupted file stopping me from loading windows, aswRvrt.sys.

---

### Post by Bashing-om on 2014-07-05
Nimono; OK ;

Let's consider this:
Disable "quick boot" as that relates to hibernation ( a Windows thing) and the hard drive booting, as we do want to boot from another means.
Then see if you can boot from the USB.

> 
but did all my downloading on my parents' laptop.

Again is the 'work' box of a Window's nature ? - IF we go the rout of downloading and burning a DVD - so we can provide the instructions appropriate to the environment .

Once we get ubuntu booting, maybe that will also fix Windows booting ( as we get boot code installed, and ubuntu can pick up Windows and Chainload Windows to ubuntu's boot menu).

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Nimono on 2014-07-05
> **Bashing-om said:**
> Nimono; OK ;

Let's consider this:
Disable "quick boot" as that relates to hibernation ( a Windows thing) and the hard drive booting, as we do want to boot from another means.
Then see if you can boot from the USB.


Again is the 'work' box of a Window's nature ? - IF we go the rout of downloading and burning a DVD - so we can provide the instructions appropriate to the environment .

Once we get ubuntu booting, maybe that will also fix Windows booting ( as we get boot code installed, and ubuntu can pick up Windows and Chainload Windows to ubuntu's boot menu).[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]

I couldn't find an option to outright disable hard drive booting, and the laptop is Windows 7 home premium, but is 32-bit. EDIT: the boot option under Quick Boot is Quiet Boot; i turned that off, too, will retry the install now.

Okay, turning them off did nothing... I tried installing lubuntu earlier with my hard drive unplugged, but it still wouldn't work. The USB normally glows when it's running, blinking when working, but selecting one of the options makes it stop glowing.

---

### Post by Bashing-om on 2014-07-05
Nimono; Yuk.

Appears you are in this boat also:

> 
I don't know if there is any software with a default windows install to do the job. You download a program called Imgburn, once that is downloaded you can open it and check the options on the tabs in its window and find an option to "burn as image". That is what you need to do. If you can't get any software to "burn the iso as an image", it won't boot.

You need to use something like unetbootin or pendrivelinus to put the iso of Ubuntu on the flash drive or it will not be bootable also. You need to have the flash in the port when you boot the computer. You need to change the boot priority in the BIOS to set the flash drive to boot first. The methods for doing this vary with computer manufacturers. If it fails in one usb port try another. I have an Acer notebook which will boot a flash drive but only the first port so you need to check that if it fails.
(gratis: yancek)


So, how bout we try from your parent's Windows 7 box to "burn" as an image the liveDVD of ubuntu:
Download a fresh .iso;
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Verify the .iso image from within windows:
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
Burn the .iso file as an image in Windows:
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
Verify the DVD:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)


Now all that (re-)done, you have a good verified means to install ubuntu ! With that foundation we can proceed.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Nimono on 2014-07-05
> **Bashing-om said:**
> Nimono; Yuk.

Appears you are in this boat also:



So, how bout we try from your parent's Windows 7 box to "burn" as an image the liveDVD of ubuntu:
Download a fresh .iso;
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Verify the .iso image from within windows:
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
Burn the .iso file as an image in Windows:
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
Verify the DVD:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)


Now all that (re-)done, you have a good verified means to install ubuntu ! With that foundation we can proceed.
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]

I did that once before with a DVD+R, but it never shows the boot options screen, just the black screen with blinking cursor. It's the same .iso I burned to USB earlier, the one we've been working with, and I know it's good, I verified it.

---

### Post by Bashing-om on 2014-07-05
Nimono; OK ..

Graphics driver issue ?

What results:
Boot the liveDVD, as soon as the bios screen clears, depress and hold the right -shift- key. -> language screen, escape key to accept the default -> Do you get the ubuntu boot options screen ?
F6 key for preset options, for ATI and Nvidia graphics the "nomodeset" option often results in the ability to boot to the GUI ( degraded graphics is ok at this point). arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Enter key to continue the boot process to the GUI desk top.

If you can get this far

[INDENT][INDENT]installing ubuntu is most a done deal.
[/INDENT][/INDENT]

---

### Post by Nimono on 2014-07-05
Welp, I don't have a free DVD+R disc, and I can't get any DVD-RWs right now...


I tried a USB boot again, and I actually got to the boot options screen for Ubuntu...but nomodeset still doesn't do anything, it still gets stuck on a black screen when trying to load anything but memtest. Should I try a 32-bit .iso? Could that work despite my computer being 64-bit?

---

### Post by Bashing-om on 2014-07-05
Nimono; sheessh ;

No on trying 32 bit, will make no difference.

OK, what results from the boot options menu when you choose "check disk for defects" ? I expect at that point in the system, that the fall back grub driver is in use, If the check does not run, problems elsewhere than graphics.

Might try other preset boot options, like "noapic" and see what results .

[INDENT]still look'n for the cause
[/INDENT]

---

### Post by Nimono on 2014-07-05
> **Bashing-om said:**
> Nimono; sheessh ;

No on trying 32 bit, will make no difference.

OK, what results from the boot options menu when you choose "check disk for defects" ? I expect at that point in the system, that the fall back grub driver is in use, If the check does not run, problems elsewhere than graphics.

Might try other preset boot options, like "noapic" and see what results .
[INDENT]still look'n for the cause
[/INDENT]

OH THANK YOU! I turned on nomodeset, noapic, and nolapic, and the Try option worked! I am currently looking at Ubuntu on my desktop, and now I need to figure out how to check on the files in my windows partition so I can check my options for salvaging what's there, and possibly fix windows without a reinstall. THANK YOU SO MUCH!!

---

### Post by Bashing-om on 2014-07-05
Nimono; Hey,


Good deal !
Just try'n to help - process of elimination..

OK, from here what is your main end goal here ? Is it your intent to install and use ubuntu ? OR see about fixing the Windows booting ... Or both ?

Presently to access Windows; at the ubuntu desktop, left side of screen is the 'launcher' next to top icon that looks like a folder is ubuntu's file manager - nautilis -. Open nautilus and in the left pane are all the file systems that ubuntu is aware of. Your Windows' partitions should be listed; click to open.

A bit more direction to enable us to give instruction.

[INDENT][INDENT]better questions get better responses
[/INDENT][/INDENT]

---

### Post by Nimono on 2014-07-05
> **Bashing-om said:**
> Nimono; Hey,


Good deal !
Just try'n to help - process of elimination..

OK, from here what is your main end goal here ? Is it your intent to install and use ubuntu ? OR see about fixing the Windows booting ... Or both ?

Presently to access Windows; at the ubuntu desktop, left side of screen is the 'launcher' next to top icon that looks like a folder is ubuntu's file manager - nautilis -. Open nautilus and in the left pane are all the file systems that ubuntu is aware of. Your Windows' partitions should be listed; click to open.

A bit more direction to enable us to give instruction.
[INDENT][INDENT]better questions get better responses
[/INDENT]
[/INDENT]

Well, I was honestly considering installing it permanently and not using windows again, but i'd also like to back up my data and try to fix windows, just in case i want to keep using that. Right now, primary concern is moving as many of my files as possible to my free USB drives, so I can keep them safe. Again, thank you SO MUCH for all your help!!

---

### Post by Bashing-om on 2014-07-05
Nimono; Weellll, like this.

We are here to help. Best advise, not a good idea to up and desert Windows and try and go cold turkey. Linux is not windows and a different attitude toward the operating system is required than that of Windows. There is a rather steep learning curve once you progress beyond the point and click stage.

For now to save your data, plug in a usb thumb drive - open the file manager to your Windows files, and in the file manager open an additional window, and open it on the usb drive: drag and drop between the two windows.

If you decide to install ubuntu, we can continue to instruct to get that job done.

Else; if this matter is satisfactorily concluded:
Please mark this thread solved; aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.

Bear in mind we do look forward to a continued association.

[INDENT][INDENT][INDENT]it's ubuntu, all things are possible
[/INDENT][/INDENT][/INDENT]

---

