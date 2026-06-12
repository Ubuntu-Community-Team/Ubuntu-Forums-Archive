---
title: "Ubuntu 12 64-bit CD image download"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by Xinghao_Chen on 2013-10-01
Sorry to trouble you all. Just need to know where to go to download a CD disk image for Ubuntu 12 64-bit. I started with a 32-bit Ubuntu 11.10 sometime ago and updated to 12. I got a ThinkPad X200 laptop which is a 64-bit capable and I want to try it out with 64-bit Ubuntu 12.

---

### Post by hansdown on 2013-10-01
Welcome to the forum, Xinghao_Chen.

This should help.

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

---

### Post by DuckHook on 2013-10-01
*hansdown* has pointed you to a useful site if you want really specific versions and kernels, but [this]("http://www.ubuntu.com/download/alternative-downloads") is a simpler site. I would recommend the torrent download not only because it is generally faster and less taxing on the Ubuntu servers, but also because it is more robust due to dynamic error-correction.

---

### Post by Xinghao_Chen on 2013-10-01
Thank you for the pointer. But I don't find a 64-bit laptop entry for Intel processors.

---

### Post by deadflowr on 2013-10-01
AMD64 is for both AMD and intel.
It's a legacy naming convention.
Has nothing to do with being only for AMD processors.

Like how 32-bit is listed as i386, where as most people running 32-bit probably have i686 or similar.
In fact the newer kernels don't even support 386 processors anymore.

---

### Post by papibe on 2013-10-01
+1 to what deadflowr said

Use either: **ubuntu-12.04.3-desktop-amd64.iso**  or **ubuntu-12.04.3-desktop-amd64.iso.torrent**

Regards.

---

### Post by Xinghao_Chen on 2013-10-02
Got it. Thank you all.

---

### Post by Xinghao_Chen on 2013-10-02
Just ran into a problem: the ISO file is too large to be put on a 700MB CD disk. My laptop says the ISO image is a 708MB file.

---

### Post by DuckHook on 2013-10-02
> **Xinghao_Chen said:**
> ...the ISO file is too large to be put on a 700MB CDAll new versions now require DVD, If you don't have a DVD installed, you will need to use USB.

---

### Post by Xinghao_Chen on 2013-10-02
Got it. Thank you.

---

### Post by Xinghao_Chen on 2013-11-10
Well, I tried a couple of times but still could not get a 64-bit version installed on my ThiinkPad T400.

As devised, I downloaded the ubuntu-12.04.3-desktop-amd64.iso (724,992 KB of size) and made a DVD disk copy of it. Then I booted the T400 with the DVD disk: the screen showed a few text lines (too fast for me to read anything from it) and then stuck on a screen with the keyboard cursor blinking and showing nothing else (I left it on for about 10 minutes, hoping to see some activities); the DVD drive is not turning (after the initial spining at boot); the purple Ubuntu screen never came up.

I used the same setup with my old 32-bit Ubuntu 11.10 CD disk and this one runs just fine.

Any advice?

---

### Post by deadflowr on 2013-11-10
I don't which option you might need to set, but when you start the livecd, you should get a screen with options to either install or try.
On that screen, you should see option at the bottom, one of those options is F6, press that and and drop down of items is listed.
Among those items is nomodeset. This option is a normal option for people to set when things aren't booting properly.
Simply mark the option and then press escape, then select try or install and hit enter.

---

### Post by Xinghao_Chen on 2013-11-10
My screen doesn't have anything but the keyboard cursor, with the background being lit just a little, nothing else. None of the Ubuntu setup screens came up. I installed Ubuntu 11.10 with a CD disk before. If the process is the same, I was expecting a purple screen with the sign of Ubuntu and then setup screens. With this 64-bit DVD disk, the install went dead before any Ubuntu screen comes up, which is why I am puzzled by it.

---

### Post by deadflowr on 2013-11-10
> **Xinghao_Chen said:**
> My screen doesn't have anything but the keyboard cursor, with the background being lit just a little, nothing else. None of the Ubuntu setup screens came up. I installed Ubuntu 11.10 with a CD disk before. If the process is the same, I was expecting a purple screen with the sign of Ubuntu and then setup screens. With this 64-bit DVD disk, the install went dead before any Ubuntu screen comes up, which is why I am puzzled by it.

Do you mean a keyboard icon at the bottom of the screen?

---

### Post by Xinghao_Chen on 2013-11-10
No. It is the little flashing - sign (similar to the DOS mode key/keyboard cursor and the Ubuntu/Linux command line cursor) at the top-left on the screen.

---

### Post by Xinghao_Chen on 2013-11-11
Someone, please help. I have not been able to install the ubuntu-12.04.3-desktop-amd64.iso (724,992 KB of size) on my ThinkPad T400. A 32-bit Ubuntu 11.10 version is working. I really need a 64-bit version to work.

---

### Post by deadflowr on 2013-11-12
Can you run any version of 64-bit?

Though I would rather not go this route, but you could try downloading [11.10 dead release version 64-bit]("http://old-releases.ubuntu.com/releases/oneiric/") and see if that loads.
My thinking is that, since you know that it works with 32-bit, it might work with 64-bit.
If it does , then try and see if you can then do a system upgrade to 12.04.
And if you can, then see if any problems arise.
This is only an option, and I stress, it is not one I normally endorse. I'm simply spitballing an idea.
But since it would be only to a)see if the system can run a 64-bit Ubuntu, and b) it'll be upgraded to a supported version ASAP, it should ok.

Of course, you can also go in the opposite direction, one I WOULD recommend, of trying to install a newer still supported release, such as 13.10.

Then again, it could always be a simple bad burn on the 12.04 disk. (That happens, burners can go down in quality)
You could try a new disk, burn another. And see.

---

### Post by monkeybrain20122 on 2013-11-12
The live DVD doesn't boot basically. Have you tried a 12.04 32 bit? Maybe your machine just can't run 64 bit. You can also try 12.04.1 or 12.0.4.2

---

### Post by Xinghao_Chen on 2013-11-12
The ThinkPad T400 came with a 64-bit Windows Vista Business Edition installment.

The tried 64-bit version is for AMD processors. My T400 has an Intel Core 2 processor - I was advised that the 64-bit 12.04 Ubuntu for AMD works also for Intel CPUs. Maybe it doesn't? Then there is not 64-bit listed explicitly for Intel CPUs at the download site.  

Since my 32-bit 11.10 worked on this T400, I am thinking about trying out a 64-bit 11.10 version of Ubuntu.

---

### Post by deadflowr on 2013-11-12
> **Xinghao_Chen said:**
> The ThinkPad T400 came with a 64-bit Windows Vista Business Edition installment.

The tried 64-bit version is for AMD processors. My T400 has an Intel Core 2 processor - I was advised that the 64-bit 12.04 Ubuntu for AMD works also for Intel CPUs. Maybe it doesn't? Then there is not 64-bit listed explicitly for Intel CPUs at the download site.  


As stated before, that is wrong.
The 64-bit works for both intel and AMD.

I know, I am running an intel chip as of now and it is 64-bit.
The iso was the amd64 version.

Stop thinking that it is only for amd chips.

There could be any number of reasons for why the disk isn't loading.
Quite possibly a bad disk burn.

Edit and added: It could also be that the machine isn't reading the disk or the setting to read the disk aren't right.

---

### Post by Xinghao_Chen on 2013-11-12
Thank you for the confirmation that the 64-bit ISO is for all CPUs.

My T400 setup runs the 11.10 32-bit CD disk just fine. So, the T400 setup is not the cause.

The only possibility left is that the 64-bit ISO got a bad DVD disk burn, which I can wipe it clean and re-burn the ISO on it. 

I compared my 32-bit 11.10 CD disk and the 64-bit 12.04 DVD disk: on the 32-bit CD disk there are directories and files (such as .disk and boot directories and autorun and wubi files, etc.; on the 64-bit DVD disk, there is only one large ISO file. 

After I downloaded the 64-bit 11.10, the file structure is the same as the 32-bit: directories and files. 

However, the 64-bit 12.04 I downloaded is of a single large ISO file. So, I am wondering that I might not have burn the DVD disk with a proper file structure. If a single ISO file on the 64-bit 12.04 install DVD disk is not a correct one to start, how do I go about making the DVD install disk with this ISO file?

---

### Post by Xinghao_Chen on 2013-11-13
Well, I finally found out that I did not burn the DVD disk correctly - for some reason on my T400 Windows Vista Business Edition I need to manual extract the ISO file to the HDD and then burn the individual files and directories to a DVD disk - extracting the ISO file directly to a DVD disk doesn't complete properly.


Now I have a working 64-bit 12.04 to work with. Thank you all for helping me sorting out the problem.

---

### Post by deadflowr on 2013-11-13
> [COLOR=#000000]Now I have a working 65-bit 12.04 to work with. Thank you all for helping me sorting out the problem.[/COLOR]

Cranking it up to 11?
Is 65-bit any better than 64-bit?;)

Joke aside, good luck with it.
Enjoy!

---

### Post by Xinghao_Chen on 2013-11-14
Thank you for the cheerful comment on a typo. But the unintended extra bit did lead to a different path.

First, I installed the 64-bit 12.04 on a low-profile USB 32GB stick memory (Sandisk Cruzer Fit) without the HDD inserted. It went well until the later system updates somehow made the speakers "not speaking" (even though all the control panels and buttons indicate the speakers are set properly). 

Next, I inserted the original Windows Vista HDD into the T400 case and turn on the power without the Ubuntu 12.04 USB memory and the T400 would not boot: the message is saying something like "device not found" and "grub rescue"  - I don't know what these messages mean. Now, with both the Vista HDD and the USB flash memory of Ubuntu 12.04 64-bit inserted in their places, I can boot the T400 in the purple-color dual-boot menu with the 64-bit Ubuntu 12.04 install but not the Vista - it would say "device not found" and "grub rescue" etc. For some reason the Vista is no longer working on this T400. 

This is all the extra bit brought to me - joke or not. 

I have several ThinkPad models. with Win7, Vista and the old XP Pro. I have two 32-bit Ubuntu 11.10 installs on two USB sticks. When I need to use Ubuntu I can boot the PCs with the 32-bit Ubuntu by selecting (F12) the boot device to start with the USB flash memory. When I use Windows I can boot the PCs without the Ubuntu USB flash memory or select the HDD to boot.

I wonder if the 64-bit 12.04 install made any changes to the T400 BIOS that it doesn't boot with the original Vista HDD, along or with the Ubuntu-installed USB memory inserted.

---

### Post by deadflowr on 2013-11-14
Try plugging both the ubuntu device and the vista device, then try booting into ubuntu.
If successful, open up a terminal and run
```
sudo update-grub
```
Then look over the output, and see if an entry for vista, or windows shows up.
Then close the terminal and try rebooting and see if vista loads.

---

### Post by Xinghao_Chen on 2013-11-15
Thank you for the reply. 

Before readin your latest reply, I did rebuit the 64-bit 12.04 on the same USB stck memory for a different reason - the system updates after the initial DVD disk install somehow made the speakers not "speaking" anymore. This rebuild on the USB memory has only what from the DVD disk initial install and everything in Ubuntu seems to work fine.

This rebuild was made while the Vista HDD was in the T400.

I then rebuild the Vista on the same HDD as it was not working in any boot method (before reading your latest reply). As the T400's BIOS is set with the boot order of HDD and then USB, booting to Vista is not a problem. Now, if I hit F12 and get to the boot device selection screen, I can select Ubuntu to boot and it then brings me to the Ubuntu purple-color dual-boot selection screen and I can select Ubuntu to boot without any problem; but if I select Vista in this purple-coler dual-boot screen to boot, the screen would stay in the purple-color background with 2 lines saying the same thing "device not found" (without "grub rescue" ) and I hit the return key and it would go back to the purple-color dual-boot screen again. This is fine with me, as I can access Vista and Ubuntu just fine - just don't understand why the dual-boot screen doesn't work for Vista on the same HDD.

I have halted Ubuntu 12.04 64-bit system updates for now, because the trouble with needing Adobe Flash Player and no-sound speakers. The thread is

[http://ubuntuforums.org/showthread.php?t=2187784](http://ubuntuforums.org/showthread.php?t=2187784)

and so far I there has been no advice there. Of the 148 system updates I don't know which ones caused the two problem. 

Thank you.

---

