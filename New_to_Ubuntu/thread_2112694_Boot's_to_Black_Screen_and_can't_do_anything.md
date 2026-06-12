---
title: "Boot's to Black Screen and can't do anything"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by BPDice on 2013-02-05
Sorry if this has already been answered, but I've looked everywhere and can't seem to fix it.
When I boot my laptop up (LG LS50A see below for specs) on my Xubuntu 12.04 OS all I get is a black screen with a white underscore flashing, I cannot go into text mode (by pressing Crtl-Alt-F1) or do anything and need to shutdown and restart.
However if I put in the USB with the ISO on it, it starts no problem.
I have tried changing the GRUB and adding console=tty1 in the Grub CMDLine but still didn't help.
Thanks and if I forgot anything let me know.


[LIST]
[*] Processor Intel Pentium M 725 / 1.6 GHz
[*] Memory 512.0 MB / 2.0 GB (max)
[*] Hard Drive 60.0 GB
[*] Operating System Microsoft Windows XP Professional
[*] Display Type 15.0 in TFT active matrix
[*] Max Resolution 1024 x 768 ( XGA )
[*] Graphics Processor Intel Extreme Graphics 2 Dynamic Video Memory Technology 2.0
[*] Optical Drive DVD±RW / DVD-RAM
[/LIST]

---

### Post by |{urse on 2013-02-05
I know this may sound silly but unplug all usb devices (especially external storage like flash drives) and see if it boots correctly after that.

---

### Post by |{urse on 2013-02-05
"However if I put in the USB with the ISO on it, it starts no problem."

Maybe you installed grub to usb accidentally?

---

### Post by BPDice on 2013-02-05
Thanks I've tried that and still no dice :( and it would appear that the grub is install on the physical drive and I can take it out and still run the OS and the file system is on my HD, is there a way I can double check?
Thanks for your help BTW

---

### Post by bogan on 2013-02-05
Hi!, **BpDice**,

Is Xubuntu a direct install to HDD or SSD?,  dual with Windows or any other OS, or a Wubi program in Windows??

You Posted:> However if I put in the USB with the ISO on it, it starts no problem. Does it then boot directly to the LiveCD, and offer to Try or Install, or to a Grub Menu from which you can choose? or directly to Xubuntu??

Also:> When I boot my laptop up ..... on my Xubuntu  12.04 OS all I get is a black screen with a white underscore flashing,That is without the USB. Right?
Do you then get a Grub menu? [press 'Shift' if necessary]

At which point in the boot sequence does it hang on the flashing cursor?
& do you get to log-in??

And:> I have tried changing the GRUB and adding console=tty1 in the Grub CMDLine Is that in the Grub menu, using 'e', or in /etc/default/grub?

If you can get a Terminal or TTY [when booted to Xubuntu] please Post:```
lspci -nnk | grep -iA3 vga
```Chao!, **bogan**.

---

### Post by BPDice on 2013-02-05
Thanks for your help

Is Xubuntu a direct install to HDD or SSD?,  dual with Windows or any other OS, or a Wubi program in Windows??
**It's a direct install to the HDD**

You Posted: Does it then boot directly to the LiveCD, and offer to Try or Install, or to a Grub Menu from which you can choose? or directly to Xubuntu??
**It boots directly to Xubuntu**

Also:That is without the USB. Right?
Do you then get a Grub menu? [press 'Shift' if necessary]
**No, even with the shift**

At which point in the boot sequence does it hang on the flashing cursor?
& do you get to log-in??
**Right after the BIOS screen**

And:Is that in the Grub menu, using 'e', or in /etc/default/grub?
**in the /etc/default/grub**

If you can get a Terminal or TTY [when booted to Xubuntu] please Post:lspci -nnk | grep -iA3 vga
Here is what i get;
[B]00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
    Subsystem: LG Electronics, Inc. Device [1854:000a]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915[/B]

Thank you everyone you've all been awesome!

---

### Post by bogan on 2013-02-05
Hi!, **BoDice**,

As you can boot into Xubuntu, [with the UsbLive plugged in] the obvious thing to try, would be to remove the Usb [COLOR=Red]after booting is complete[/COLOR] and logged in, and you have installed the correct drivers for Video and WiFi, to ensure everything still works OK.

I have had a system like that, and when I pulled the Usb out, everything crashed, though I have no idea why; other systems have not.

If it survives, then install grub-pc to the HDD with the Usb removed, and restart . Of course you need a working Internet connection to do that. [ Ask if you need detailed instructions.]

However, if everything boots and runs OK with the Usb plugged in, why not leave well alone and use it like that??

Is it that it is a Laptop and the usb is too large? you can get very small ones these days, I have an 8Gb that protrudes less than 15mm.

Chao!, **bogan**.

---

### Post by BPDice on 2013-02-05
Thanks for the quick reply.
Once the OS is booted I can remove the usb key and everything works (& my plan B is to just leave it in).
If you could let me know what I need to do to install grub-pc to hdd, that would be awesome.
Thanks

---

### Post by bogan on 2013-02-06
Hi!,**BpDice,**
 
What is the Bios boot default priority set to?  
And will it boot  correctly to the LiveUsb? if you use the Bios boot menu to select it.?

To get Grub to run from the booted OS :.>>

Check in which drive & partition the OS you want is installed.
'gparted' will open & show the active drive with '/' and a key symbol, against the root partition, note which it is. In your case, probably sda1.

Or you can use```
 sudo  fdisk -lu
```Then:```
sudo -i # To get to Root, enter 'exit' to revert.
apt-get update
apt-get upgrade
apt-get grub-install /dev/sda # change 'sda' if needed, but do not add the partition number.
apt-get grub-install --recheck /dev/sda # to confirm
update-grub # be sure LiveUsb is not in, or it will be listed in the Grub menu.
exit
# then restart
```That should fix it, if your installation is normal. [ but I have some doubts ] and give a Grub Menu, if you have more than one OS installed, or after pressing 'Shift' repeatedly, following the Bios splash screen.

if it does not, there are a couple of other ways to try, such as a complete grub purge and reinstall, or boot from the USB and mount the HDD from there.

Post how it goes, & list any Error messages in full.

Cha!, **bogan**.

---

### Post by BPDice on 2013-02-06
Thanks **Bogan** again for all your help, I get halfway through what I should do and then I get this;
E: Invalid operation grub
I then did
apt-get install grub
That worked & then I got this;
Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-3.2.0-37-generic
Found kernel: /boot/vmlinuz-3.2.0-29-generic
Found kernel: /boot/memtest86+.bin
Restarting now, wish me luck!
Thanks,
BP

---

### Post by BPDice on 2013-02-06
Thank you **Bogan!**
It boots now without any issues.
BP

---

### Post by evertonmint on 2013-02-06
I'm having a similar problem, I put the CD in and pressed 'TRY'  after a while I decided to install 12.04 LTS  from the menu on the left. After (taking disk out) rebooting, I arrived at a black screen just after the bios screen (where windows welcome used to come in).
I don't use a 'monitor' I use my TV set to PC INPUT. When the black screen appears I get an 'information' box 'OUT OF RANGE'!

Any Idea's? All that is in the PC is the usb locater for my wireless mouse.
I had previously formated the drive so no O/S installed.

Regards

Evertonmint.
PS i am now back on the CD trial version.

---

### Post by bogan on 2013-02-06
> **BPDice said:**
> Thank you **Bogan!**
It boots now without any issues.
BPWell, I am glad it is working! But!

You may perhaps recall that I posted: > If it survives, then install [COLOR=Red]grub-pc[/COLOR] to the HDD Grub-pc is the current version 2.00 of grub.

What you installed: "grub", is the legacy version v1.9 dated back to pre 10.04, and that uses the /boot/grub/menu.lst file it looked for, but which grub v2 does not want.

To switch to the current version is a bit complex, & and I would need to look it up. With the luck you asked for it should be OK until there is an update to the kernal or to grub-pc, which could give you problems.

Still, on the old Ford principle of: "If it aint broke, don't fix it", here's hoping.

Chao!, [B]bogan.
[/B]

---

### Post by bogan on 2013-02-06
@**evertonmint**: Your post is a duplicate!!  I just wasted 15 minutes writing a response, only to find you have already Posted an exact duplicate elseware, to which you already have replies. I suggest you**[COLOR=Red] delete the Post in this thread[/COLOR]**.

ANNOYED, bogan.

> **evertonmint said:**
> I'm having a similar problem, I put the CD in and pressed 'TRY'  after a while I decided to install 12.04 LTS  from the menu on the left. After (taking disk out) rebooting, I arrived at a black screen just after the bios screen (where windows welcome used to come in).
I don't use a 'monitor' I use my TV set to PC INPUT. When the black screen appears I get an 'information' box 'OUT OF RANGE'!Immediately after the Bios splash screen, press 'Shift' repeatedly. You should get a Grub Menu with entries for the normal boot to the OS you installed and for 'Recovery' mode.

If so, left click on the first entry to highlight it, and press 'e' to go into edit mode.
Scroll down to the line that starts: 'Linux /boot' and across to ' ro quiet splash '.

Add ' nomodeset ' [ no quotes] and press 'Ctrl+x' to continue booting. If that does not work try with the second grub menu entry: 'Recovery', and 'Resume Booting' in the Recovery menu.

Post how it goes and give details of your set up including CPU & video card details if you know them, If not Post:```
lspci -nnk | grep -i A3 VGA # and its output.
``` Edit: Include whether you did so from the LivCD or from the HDD.

Chao!,** bogan**.

---

### Post by grablist on 2013-02-13
Same problem, in my case following a system update, but I haven't been able to find a solution.

System was working normally. I did a routine weekly update, which included among other things "grub-pc 1.99-21ubuntu3.7 1.99-21ubuntu3.9" and kernel version 3.2.0-37. When I rebooted to complete the update, I got the BIOS and then a black screen with a flashing cursor in the upper left corner which persists indefinitely (>60 sec). I tried rebooting multiple times and pressing various keys (space, esc, random letters), but I cannot access grub or boot the system.

I have tried the steps suggested above, but they did not fix the problem for me. (N.B. I was doing it using a live CD, not a live USB.) I have also tried purging and reinstalling grub completely, using the chroot procedure detailed [here]("http://ubuntuforums.org/showthread.php?t=1581099"), but also no luck. Both procedures appeared to complete without error.

Any suggestions?

My installation is on a Lenovo X201 3249-CTO, with the following partitions:
/dev/sda1 => /boot
/dev/sda2 => swap (dmcrypt/LUKS encrypted with random key
/dev/sda3 => /mapper/sda3_crypt => / (dmcrypt/LUKS encrypted with passphrase)

Many thanks,
grablist

---

### Post by bogan on 2013-02-14
Hi!, **grablist,**

What does Synaptic & 'apt-cache policy grub-pc' show as currently installed ?

My 12.04, 3.2.0-37-generic-pae shows " GRUB=PC 1.99-21-ubuntu3.9... version 2 (PC/BIOS...)"  both as installed and as 'candidate'.

If yours still shows '1.99-21-3.7' and:```
sudo apt-get update 
sudo apt-get upgrade
```does not update it to -3.9, I suggest you remove --purge it using the 'chroot' method of your link and re-install it.

Chao!,** bogan.**

---

### Post by grablist on 2013-02-14
Bogan,

Many thanks. Glad you are still following this thread!

After booting from the live CD and opening a terminal, running "sudo apt-cache policy grub-pc" returns:

```
grub-pc:
  Installed: 1.99-21ubuntu3.1
  Candidate: 1.99-21ubuntu3.9
```

Running Synaptic from the Unity bar shows the same information. I assume that this is because both apt-cache and Synaptic are reporting the grub version installed on the live CD rather than on the hard drive. Chrooting and running apt-cache as follows:

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp/boot
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda3 sda3_crypt
Enter passphrase for /dev/sda3: 
ubuntu@ubuntu:~$ sudo mount /dev/mapper/sda3_crypt /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp/boot
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
cp: not writing through dangling symlink `/mnt/temp/etc/resolv.conf'
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# sudo apt-cache policy grub-pc
sudo: unable to resolve host ubuntu
grub-pc:
  Installed: 1.99-21ubuntu3.9
  Candidate: 1.99-21ubuntu3.9
```

appears to show that 1.99-21-3.9 is installed on the hard drive. I haven't been able to confirm with Synaptic, as trying to run Synaptic from the chroot command line produces the following error:

```
root@ubuntu:/# gksudo synaptic
No protocol specified
No protocol specified

(gksudo:5058): Gtk-WARNING **: cannot open display: :0
```

Any suggestions on where to go from here? Purge and reinstall again and see what happens??

grablist

---

### Post by grablist on 2013-02-14
Working again. My bad. My very, very bad. Lesson: Do not leave a blank SD card in your computer's handy-dandy built-in SD card reader and then expect it to boot normally when you have USB devices set to boot priority 1. Apologies for the waste of time. --grablist

---

### Post by bogan on 2013-02-14
> **grablist said:**
> Working again. My bad. My very, very bad. Lesson: Do not leave a blank SD card in your computer's handy-dandy built-in SD card reader and then expect it to boot normally when you have USB devices set to boot priority 1. Apologies for the waste of time. --grablistWell, as they say in Spanish: "Menos Mal!", or:'It could be a lot worse!'.

Chao!,** bogan.**

---

