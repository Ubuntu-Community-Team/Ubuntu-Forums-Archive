---
title: "Installation on UEFI Windows 8 Sony Vaio."
date: 2013-10-29
forum: New to Ubuntu
---

### Post by kayve on 2013-10-29
The tech help doesn't work.  I have not been able to set up my 13.04 on dual boot with UEFI Windows 8 Sony Vaio.  I have to run from CD   Here is a pastebin [http://paste.ubuntu.com/6284562/](http://paste.ubuntu.com/6284562/)   Also I asked questions:  [http://askubuntu.com/questions/363355/failing-to-install-ubuntu-13-04](http://askubuntu.com/questions/363355/failing-to-install-ubuntu-13-04)   When I reboot with no CD I get "VAIO" for a second, F2 RARELY gets me to UEFI/BIOS, and I quickly get a red box that says "Operating System Not Valid"  and a pile of smoking metal that I can hard reboot or press the button does get me back to my CD OS.. The boot-repair CD will not boot, another suggested CD does not boot.  Only my Ubuntu 13.04 live CD OS gets me to the window "install ubuntu"  "try ubuntu" "OEM.." etc.   then I "try ubuntu" and get a CD OS that has to churn and churn and I can't save any settings I have to reinstall my WiFi and supply a 16 character password by hand every time.  The firmware password of my Comcast WiFi.

---

### Post by papibe on 2013-10-29
Move to its own thread.

---

### Post by kayve on 2013-10-30
I have already created "its own thread," it was created before this one by a couple days with little response.  I hope you are posting over there as I hoped.

---

### Post by oldfred on 2013-10-30
Post a link to the entire boot info report so we can see if it outputs some of your UEFI data.

Some other threads with Sony.
 Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
 Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570](http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

---

### Post by QIII on 2013-10-30
> **kayve said:**
> I have already created "its own thread," it was created before this one by a couple days with little response.  I hope you are posting over there as I hoped.

If you are referring to your post on askubuntu, then that has nothing to do with your thread on Ubuntu Forums having been moved.

---

### Post by kayve on 2013-10-31
Forgive me, but I detect no "help" only sniping.  I followed the directions created paste bins and it is dead silence.  I have done boot-repair repeatedly.  I fixed my "operating system not found" error to be replaced with "operating system invalid"

Here are two pastebins I provided in the other link.  I am supposed to make a new "thread" with this?

[http://paste.ubuntu.com/6284562/](http://paste.ubuntu.com/6284562/)

[http://paste.ubuntu.com/6298621/](http://paste.ubuntu.com/6298621/)

I just rebooted and resupplied my 16 character firmware wifi password.  l guess that link helped me get into UEFI/BIOS, and Secure Boot is disabled boot mode is UEFI and I still get the red box invalid OS.  I don't have a USB device I dedicate for booting, I have never done that, I am booting from CD.

---

### Post by oldfred on 2013-10-31
Installs do work a lot better with a wired Ethernet connection. Not all wireless drivers are installed and as you have found when booting a live version you have to redo everything you change or add each time.

Are pastebins now current or have you reinstalled or rerun Boot-Repair.
Last pastebin did show signed kernel that should work with secure boot. 
Do you have an ubuntu entry in your UEFI menu, with secure boot on or with it off?
Only secure boot systems will show if secure boot is on.

---

### Post by kayve on 2013-10-31
I am getting heart palpitations ppl are always messing with my head because I'm a paranoid schizophrenic

Where is the UEFI menu?  I cannot run Windows 8.. It is hard to get to  the start up UEFI/BIOS but I am getting better at it.  I guess I have to  send myself another email with these scores of browser tabs so I can  reboot.  Here is some stuff I did before I realized someone was talking  to me:

OK Gparted seems to have magically appeared in my Ubuntu.  Here is a   screenshot of that    [http://monkeyview.net/id/965/fsck/vaio2013/GParted.vhtml](http://monkeyview.net/id/965/fsck/vaio2013/GParted.vhtml)   I am working   on burning a CD while running from CD.  I think I blew away my Firefox   menus in the process.

---

### Post by oldfred on 2013-11-01
Partitions look normal on left version. Live installer mounts swap automatically (little check mark shows mounted). And the Microsoft reserved is just unformatted space for Windows so gparted will show the red icon as it cannot tell format. 
But second screen has just about every partition with red icons. If that is newer than left one you may have major issues or something did not mount correctly. Click on icon for more info on what issue is.

Several users posted these as UEFI screens.

---

### Post by kayve on 2013-11-02
OK.. I see I have some work to do to answer all your questions.  One thing I wanted to quick paste: 

[http://monkeyview.net/id/965/fsck/vaio2013/index.vhtml](http://monkeyview.net/id/965/fsck/vaio2013/index.vhtml)

that is a bunch of screenshots of stuff I have done.  I did go back into boot-repair and change some things.  Right now, I indeed I have two GParted windows open as
seen in this screenshot:

[http://monkeyview.net/id/965/fsck/vaio2013/GParted.vhtml](http://monkeyview.net/id/965/fsck/vaio2013/GParted.vhtml)

I don't know if that helps anything.  I think I am going to go to Home Depot for something right now and then ruminate on your very much appreciated requests when I get back.  I thought I could maybe burn a CD while running from CD with Brasero, but that is not looking good.  I am guessing the best thing to do will be to follow your directions as quickly as possible instead of going down a red herring road burning a 13.10 disk.

I have yet to see something as sweet looking as this:

[http://ubuntuforums.org/attachment.php?attachmentid=247466&d=1383334392](http://ubuntuforums.org/attachment.php?attachmentid=247466&d=1383334392)

this looks like BIOS

[http://ubuntuforums.org/attachment.php?attachmentid=247464&d=1383334261](http://ubuntuforums.org/attachment.php?attachmentid=247464&d=1383334261)

..but not mine.  Did you get to that from UEFI?  I am better at getting to that now.  When I reboot I go gonzo on 1) the [Fn] key that is located amidst 3 other partner-requiring keys on my keyboard's lower left corner, bracketed by Ctrl and Alt and sitting to the left of the Uncle Bill key; 2) the F2 key; and 3) the ASSIST key, which is smiliar-ish to the power key, separated from the standard-ish keyboard, very near the screen at the top left.  

After booting into UEFI.. well.. I really feel like getting my camera from my friend's house to answer that.

My BIOS doesn't look exactly like this:

[http://ubuntuforums.org/attachment.php?attachmentid=247465&d=1383334272](http://ubuntuforums.org/attachment.php?attachmentid=247465&d=1383334272)

..but I am familiar with that Boot Mode toggle depicted.  I have set it to Legacy and back to UEFI again.  I forget the progression of that, but I think it is currently set to UEFI.  Hmm.. should I toggle that back to Legacy and see what happens when I boot?  My recollection now is that  because I have already toggled the BIOS boot device precedence so that CD/DVD is highest priority, this Boot Mode doesn't change my machine's behavior when I boot with a CD/DVD in the drive.  Therefore, I feel confident about toggling with this Boot Mode will not cause a magic smoke deficient hunk of metal with a red box "Operating System not Valid" as long as I have these CD/DVDs.  It seems I am failing to burn with Brasero running on CD OS.  I could go with a command line solution.  I should probably try that, but more motivated about getting my camera.  I have to ride public transit 30 miles to east Oakland and meet a friend who is busy all day to get that camera.  Won't happen until tonight [PST].

Fun definition of a term used in the above composition:

[http://www.catb.org/~esr/jargon/html/M/magic-smoke.html](http://www.catb.org/~esr/jargon/html/M/magic-smoke.html)

---

### Post by oldfred on 2013-11-03
If you run the "buggy" fix in Boot-Repair you may not be able to directly boot Windows for UEFI menu. 
Some UEFI/BIOS have been modified (not per UEFI standard) to only boot the Windows efi file with the Microsoft signing key.
The fix is to rename Windows to a backup and rename grub2's shim to have the Windows name. Shim also has Microsoft signing key for secure boot. Then from grub menu you can boot the Windows backedup named file to boot Windows.

If you need to Boot Windows directly from UEFI menu, you then have to restore the original names.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

It looks like you also ticked the secure boot option. Some UEFI only boot with secure boot, but with many systems, you actually should be able to boot both Ubuntu & Windows with secure boot off. If you have signed grub shim & kernels then you should be able to boot Ubuntu with secure boot on.

---

### Post by kayve on 2013-11-04
OK.  I don't know what happened to some posts I thought I made.  Somebody showed me some BIOS, and I talked about it.  I am uploading pictures of my BIOS and UEFI

I have provided this link before, but I have just greatly added to the images:

[http://monkeyview.net/id/965/fsck/vaio2013/index.vhtml](http://monkeyview.net/id/965/fsck/vaio2013/index.vhtml)

Here is one interesting one:  

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04005701.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04005701.vhtml)

Diagnostic history.  Not sure what the codes mean.   The pictures are in order, for example, when I attempted to go into rescue mode

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006001.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006001.vhtml)

The next thing that happened was the red box invalid OS

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006201.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006201.vhtml)

These past images, I gather are the "UEFI" system that I can get to by frantically pressing three keys 1) [Fn], 2) F2, and 3) Assist, found apart from the keyboard somewhat resembling a power key.  From the following link:

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006601.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006601.vhtml)

.. I get to "Legacy BIOS.."  something I am more familiar with.  

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006701.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006701.vhtml)

I am wondering about this Advanced tab

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007401.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007401.vhtml)

.. I guess I am not worried about virtualization

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007501.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007501.vhtml)

I guess my problem can't be related to xHCI USB support

[http://en.wikipedia.org/wiki/Extensible_Host_Controller_Interface](http://en.wikipedia.org/wiki/Extensible_Host_Controller_Interface)

onto the Security tab

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007802.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007802.vhtml)

Secure Boot [Disabled]  Secure Boot Mode [Standard]

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007902.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04007902.vhtml)

finally.. the Boot tab

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04008202.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04008202.vhtml)

Boot Mode [UEFI]  External Device Boot [Enabled]  Network Boot [Disabled]

Boot Priority:
   [External Device]
   [Internal Optical Disc Drive]
   [Internal Hard Disk Drive]
   [Network]

[http://www.monkeyview.net/id/965/fsck/vaio2013/PB04008401.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04008401.vhtml)

Is the only thing you need the "bootinfoscript?"

Here is a pastebin of a rerun of that with the date command used, did it a few minutes ago 

[http://paste.ubuntu.com/6361375/](http://paste.ubuntu.com/6361375/)

---

### Post by oldfred on 2013-11-04
I do not understand how you could get a secure boot error if you have secure boot turned off?

Your efi partition now does not show any Windows boot files. Did you delete them? If you tried to install 11.04 it had a bug that deleted the efi partition and then recreated it with Ubuntu only. But that was fixed in all new versions.

This from report says you ran the file rename.
 chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi

But that file is not now in the efi partition.

Did you look at the other threads with Sony. From post #4?

I also do not understand how your boot menu does not show anything from efi partition like UEFI is supposed to.

---

### Post by kayve on 2013-11-04
> **oldfred said:**
> 
The fix is to rename Windows to a backup and rename grub2's shim to have the Windows name. Shim also has Microsoft signing key for secure boot. Then from grub menu you can boot the Windows backedup named file to boot Windows.

.

I'm not understanding how to do this

reiteration of what I did:

1) tried to click the install Ubunu 13.04 from the Live CD and I wanted to use I forget ~200GB of my 750GB internal storage hard disk 
2) that broke Windows 8 so I ended up going into UEFI and doing repair Windows 8.  
3) got Windows 8 back.  Used Windows 8 partitioning to create partitions I wanted to use for Ubuntu
4) did a custom creation of partitions by using Live CD and install 13.04 icon same as before, but now I had a partition created by windows.  Broke that partition into
    desired partitions and kept some disk free for possible future different distros
 5) now with no live CD boot up looks like this: 

     [http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006201.vhtml](http://www.monkeyview.net/id/965/fsck/vaio2013/PB04006201.vhtml)

6) burned boot-repair CD and it would not boot
7) burned

There is no boot menu.  This is boot menu:

[http://monkeyview.net/id/965/fsck/vaio2013/PB04006201.vhtml](http://monkeyview.net/id/965/fsck/vaio2013/PB04006201.vhtml)

Okay I just followed this 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

and got the interesting result  

ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
EFI boot on HDD
ubuntu@ubuntu:~$ 

that doesn't seem to make sense.  My "boot menu" only comes like this 

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]


OK.. I guess that site explains that.  I have no idea to get here though

[http://pix.toile-libre.org/upload/original/1347270285.jpg](http://pix.toile-libre.org/upload/original/1347270285.jpg)
[http://monkeyview.net/id/965/fsck/vaio2013/EFI_bootHDD.vhtml](http://monkeyview.net/id/965/fsck/vaio2013/EFI_bootHDD.vhtml)

I saw the word "Insyde" somewhere

[http://monkeyview.net/id/965/fsck/vaio2013/index.vhtml?load=PB04000101](http://monkeyview.net/id/965/fsck/vaio2013/index.vhtml?load=PB04000101)

so I guess this must be relevant

[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)

[http://monkeyview.net/id/965/fsck/vaio2013/parted_print.vhtml](http://monkeyview.net/id/965/fsck/vaio2013/parted_print.vhtml)

I don't know how you think those link outs are supposed to be that helpful when few of the paste bins work any more!

[http://paste.ubuntu.com/1440212/](http://paste.ubuntu.com/1440212/)

[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)

This is clearly a conspiracy of loathesome perportions

I hate the world I want to die.

---

### Post by oldfred on 2013-11-04
It is more what other users post.

And it seems like you have a UEFI that only boots Windows and does not even give any choice.
Boot-Repair does the work around of renaming shim that is in the askubuntu link you just posted above that explains how to change it manually. Or you can possibly use rEFInd.

Yours seems to be like this, but I thought vendors were fixing it.
 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by rubensaurus on 2013-11-05
If I remember, on my laptop I made sure fast boot was disabled so you could boot from a live usb, make sure secure boot is disabled, if you're starting from scratch make sure your hd is mapped as Gpt. I believe installing windows first was easier. After installing windows you can then open the disk manager and shrink the volume so you can create a partition for Linux. After doing this, reboot  into a live usb and install Linux to the partition you created. You might have to use gpart to create a Linux swap and format the rest to ext4. After doing this you probably won't get to choose what you boot into. You'll have to run boot repair. I ended up removing windows 8 and keeping Ubuntu

---

### Post by kayve on 2013-11-25
I have been booting from CD, although I did create the USB thing and my whole booting this has been getting very confusing, which is typical for me.  I have mounted about a half dozen disks that all have linux boots on them of various distros.  Sometimes I am not sure what is booting.  

 
Does anyone have a nutshell opinion  on what you get if you pay the $49 for RHEL Desktop versus $100+ for  Workstation?   If I get Desktop do I still have root powers?  What do I get for Workstation?   I know I need to suffer through some endless googling, that is what I am supposed to do.  Maybe I will do that when I am notk too dirt poor to afford EITHER Workstation or Desktop.

---

### Post by baabsaget on 2013-11-25
you're going to want to use rEFInd...

Download - [http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
Installation - [http://www.rodsbooks.com/refind/installing.html#linux](http://www.rodsbooks.com/refind/installing.html#linux)
Go to the install link and follow the instructions
See the warning marked "Weird", I believe that is what is causing you trouble

---

### Post by kayve on 2013-11-26
I have already burned a rEFInd disk and it failed to boot.

um.. OK... taking a second look.. I realized I HAVE successfully booted  Fedora on my UEFI firmware, but was frustrated by an inability to  install my WiFi driver and get a persistant connection via ethernet to  my Comcast cable modem.  I have begun following the instructions on the  installation page as you requested, but this seems troubling:

ubuntu@ubuntu:/mnt$ df /boot/efi
df: ‘/boot/efi’: No such file or directory
ubuntu@ubuntu:/mnt$ sudo df /boot/efi
df: ‘/boot/efi’: No such file or directory
ubuntu@ubuntu:/mnt$

OK.. continuing to follow instructions.. redirected browser to this page:

[http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html)

::sigh:: OK.. btw I guess /dev/sda must be the new hard drive Sony gave me (well.. I am supposed to fix this mess and send the other one back).. I have been afraid to mess with it thus far.. right now I have a bunch of disks hooked up to my CD booted computer.. I guess the first step will be to reinstall Microsoft Windows using the Vaio Recovery Media Kit they also gave me.  

Here is a pastebin of all the HW I am currently messing with 

[http://paste.ubuntu.com/6491093/](http://paste.ubuntu.com/6491093/)

---

