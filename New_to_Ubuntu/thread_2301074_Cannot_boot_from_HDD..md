---
title: "Cannot boot from HDD."
date: 2015-10-30
forum: New to Ubuntu
---

### Post by elijah.d on 2015-10-30
I am attempting to install Ubuntu 14.04.3 on an Acer Aspire ES1-111-M-P2YU. The pre-packaged Windows installation was removed by the manufacturer; there are no other OSs on the computer. The computer can run Ubuntu from the USB itself, as I have used this function to try to troubleshoot it.

I am using a 64 bit installation (desktop variant downloaded via torrent) via a USB stick, which I have written using Win32DiskImager. (I have also attempted it with Unetbootin and LiLi USB Creator, to similar results.) My BIOS is set to have UEFI with secure boot disabled (this apparently being recommended when encountering problems with booting; it does much the same with secure boot enabled); using Legacy causes the USB drive to fail to read altogether.

After installing Ubuntu (which I have done like, six times now), the installer will ask me to restart, I will, I remove the USB stick when prompted, and restart. Once the computer is restarted, however, it just says "No Bootable Device" and fails to load. Most recently (and frustratingly), I used Boot-Repair to try to fix the problem. I used the recommended settings, it went through and did all its stuff, made a paste, and then told me to restart. The same issue occurs (secure boot enabled or disabled) at this point; it simply does not boot. This is the URL it gave me to share:

[http://paste.ubuntu.com/13009509/](http://paste.ubuntu.com/13009509/)

There are no files on my drive, as it is a new computer with a never-used OS, so it is okay if I have to reinstall, format, etc.

Thank you for any assistance.

---

### Post by yancek on 2015-10-30
> The pre-packaged Windows installation was removed by the manufacturer

They didn't do a very good job of it as they left the windows EFI files on that partition which you can see in the boot repair output.  Not sure if this is all/part of the problem so you might wait for someone else to post.  Your Ubuntu partition doesn't show all the files expected either.  Did you do an md5 checksum on the Ubuntu iso before you put it on the flash drive to verify the download?

---

### Post by Rammeloschie on 2015-10-30
I have nearly same computer and problem! posted 20mins ago xD 
Only difference is that I hadnt win installed.
When did u unplugg the stick?

---

### Post by elijah.d on 2015-10-30
> **yancek said:**
> They didn't do a very good job of it as they left the windows EFI files on that partition which you can see in the boot repair output.  Not sure if this is all/part of the problem so you might wait for someone else to post.  Your Ubuntu partition doesn't show all the files expected either.  Did you do an md5 checksum on the Ubuntu iso before you put it on the flash drive to verify the download?
I did not originally, but having just checked the iso, it seems to have the correct MD5 checksum value ([COLOR=#000000]cab6dd5ee6d649ed1b24e807c877c0ae)[/COLOR].

> **Rammeloschie said:**
> I have nearly same computer and problem! posted 20mins ago xD 
Only difference is that I hadnt win installed.
When did u unplugg the stick?
For the most recent installation, I'm pretty sure I unplugged it when prompted and before restarting the computer. (i.e. hit power button, prompt to sleep/shut down/restart, restart, wait, says to remove device and restart, remove device, hit power button)

---

### Post by Rammeloschie on 2015-10-30
i solved it! 
follow the steps in the link.

[http://itsfoss.com/no-bootable-device-found-ubuntu/](http://itsfoss.com/no-bootable-device-found-ubuntu/)


if u add the file to the thrusted ones it works fine. (at least for me xD)

good luck

---

### Post by elijah.d on 2015-10-30
> **Rammeloschie said:**
> i solved it! 
follow the steps in the link.

[http://itsfoss.com/no-bootable-device-found-ubuntu/](http://itsfoss.com/no-bootable-device-found-ubuntu/)


if u add the file to the thrusted ones it works fine. (at least for me xD)

good luck
Sadly did not work for me, as when I attempt Step 4 (selecting a UEFI file as trusted for executing), my hard disk does not appear as an option (indeed, there are no options at all).

---

### Post by oldfred on 2015-10-30
Did you set the supervisory password first?

       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757

[/URL]
 Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by elijah.d on 2015-10-30
Okay, problem solved, though I'm not quite sure how. I set a supervisor password and reinstalled Ubuntu, this time not using any of the "extra" options (internet updates, mp3 codec thing, etc). These are the only things that I changed: I did not modify any settings in the BIOS (I had set a supervisor password at some point in the past, though I'm not sure if that was before or after installing Ubuntu the previous time), and I used the exact same USB stick.

---

