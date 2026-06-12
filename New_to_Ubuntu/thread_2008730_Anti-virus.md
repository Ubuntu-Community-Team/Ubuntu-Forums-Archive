---
title: "Anti-virus?"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by Neferti on 2012-06-23
Hey, 

I run win7 parallel with ubuntu, and recently i got a virus on the win7 OS. The computer is completely unusable with win7, as soon as I log in a message from a fake police appears and I can do nothing more. 

So I figured I could do a virus scan from the ubuntu OS since it's still usable. The only problem is that I don't think i have an anti-virus for the ubuntu os. Or is there originally an anti-virus on the OS? 

Anyway, what program should I use to scan the disk with ubuntu? I tried AVG which I use on win7, but I can't seem to make it work.. 

Thanks,

---

### Post by HiImTye on 2012-06-23
just answered this in general help
[http://ubuntuforums.org/showpost.php?p=12047941&postcount=7](http://ubuntuforums.org/showpost.php?p=12047941&postcount=7)

---

### Post by Neferti on 2012-06-23
ah, thanks! 

How would I know what package to use? RPM, DEB or TAR GZ?

---

### Post by dave2001 on 2012-06-23
Hi Neferti, sorry to hear your windows install is infested.

I can offer a little bit of advice, but as I've never had your specific problem, I've not tried any of this firsthand.

Ubuntu (or any other flavor of Linux) doesn't really get viruses, so there isn't much in the way of anti-virus software. There is one anti-virus program, called ClamAV, which many people use to scan files they plan on using in windows. This might be useful in your case as well. It's in the repositories, so you should be able to find it in Software Center.

I'm not sure how well this program will work at scanning another entire operating system (which I'm guessing you have on another partition of the same drive?).

I'm also a Windows user, and my suggestion for anyone who's machine has been infected to the extent yours has, is to do a complete reinstall of windows. That way you don't have to worry whether or not you found all the viruses, keyloggers, rootkits, etc.

---

### Post by Paqman on 2012-06-23
Probably the easiest thing to do is use a bootable antivirus suite (something like BitDefender Rescue CD). Just burn it to a disk, boot up from it and see if you can get your Windows side sorted.

If the damage is too extensive it might just be easier to nuke Windows and reinstall it. If you do that you'll need to [reinstall Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") so you can dual-boot.

---

### Post by Neferti on 2012-06-24
I downloaded ClamAV, and it works quite good. However, if I choose to scan the whole disc which is mainly used by windows, the scan is very brief and the program reports that only 8 files have been scanned, even though the files that are to be scanned is like 120 gb.. Does somebody know what could be done?

---

### Post by OrangeCrate on 2012-06-24
> **Paqman said:**
> Probably the easiest thing to do is use a bootable antivirus suite (something like BitDefender Rescue CD). Just burn it to a disk, boot up from it and see if you can get your Windows side sorted.

If the damage is too extensive it might just be easier to **nuke Windows and reinstall it**. If you do that you'll need to [reinstall Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") so you can dual-boot.

This.

Personally, I would never trust a Windows install that has been compromised.

---

### Post by gakon77 on 2012-06-24
> **Neferti said:**
> I downloaded ClamAV, and it works quite good. However, if I choose to scan the whole disc which is mainly used by windows, the scan is very brief and the program reports that only 8 files have been scanned, even though the files that are to be scanned is like 120 gb.. Does somebody know what could be done?

That looks like a problem with permissions. Your windows partition can only be accessed by root, therefore if you run any application as a normal user those files only accessible by root will be left out.

Never had the same problem as you, but I would recommend to run ClamAV from the terminal as root
```
sudo clamav
```
This should make ClamAV work as usual but with root privileges (I've never had to do such thing before, so not sure if it'll do...)

Good luck.

---

### Post by Paqman on 2012-06-24
If you're going to use ClamAV, be prepared for a large number of false positives. Unless you know your way around the innards of Windows very well I'd be very wary of just killing any files it flags as malware.

---

### Post by Gone fishing on 2012-06-24
Antivir [http://www.avira.com/en/download/product/avira-free-antivirus](http://www.avira.com/en/download/product/avira-free-antivirus) and AVG [http://free.avg.com/gb-en/download](http://free.avg.com/gb-en/download) have Linux versions. I remember the Antivir being quite good when I used it to scan Windows shares.

However, if your Windows has been infected do yourself a favour use Linux to copy all your personal files somewhere safe and then clean them with Clamav or one of the above. Then delete the Windows partition and reinstall Windows. The virus will have corrupted the Windows registry etc and it will still be a problem even when cleaned of viruses.

I note that Parted Magic live cd now comes with clamav and gui [http://partedmagic.com/doku.php?id=programs](http://partedmagic.com/doku.php?id=programs)

---

### Post by Neferti on 2012-06-24
Thanks! 

Do you think it is possible to boot from a win7 CD, erase the win7 currently installed and install a new one, while the ubuntu OS is still intact?

---

### Post by Paqman on 2012-06-24
Yes, as long as you tell it to use the existing NTFS partition. You will have to reinstall Ubuntu's Grub bootloader afterwards:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Gone fishing on 2012-06-24
Yes - should be possible.

When you install Windows it will ask you where to install chose the Windows partition and tell it to format. Note however, Windows will overwrite Grub and you will need to fix Grub after your Windows installation.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Neferti on 2012-06-24
Okay.. Well, I haven't really used ubuntu that much, so there isn't really any problem for me to reinstall it since I don't have any significant files on this OS. Do you think it would be easier to just erase every OS (I think i currently have 1 virus infected win7 and 2 kinds of ubuntu), then install win7 and afterwards install ubuntu, all new? I'd move all the files of any importance to my external hard drive. Or is there a better way?

---

### Post by Gone fishing on 2012-06-24
Either way installing Ubuntu is quick and easy - there is no need to remove Ubuntu but if your Ubuntu has not been used much why not.

---

### Post by westie457 on 2012-06-24
Probably the best thing to do without reinstalling Windows (updates and reboots for 2 days) is install and run [Superantispyware]("http://www.superantispyware.com/").


Power up your system and repeatedly tap the F8 key after the POST Screen and before you get the Loading Windows screen
Boot Windows into 'Safe Mode with Networking'
Go to the site in the above link and follow the instructions to download and install and use it.

This program is the only one I know of that will install to Windows in 'Safe Mode'.

---

### Post by dave2001 on 2012-06-24
> **Neferti said:**
> Thanks! 

Do you think it is possible to boot from a win7 CD, erase the win7 currently installed and install a new one, while the ubuntu OS is still intact?

Yes it is. As others have mentioned, If your using grub, it will need to be reinstalled (which is fairly easy without having to reinstall all of Ubuntu). 

OR you could simply configure the windows loader to find Ubuntu. That's my preferred method on a dual-boot machine. If you want an easy, graphical way to do this, use _EasyBCD_.
[http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html](http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html)

---

### Post by Gone fishing on 2012-06-26
Mmm not used EASYBCD allways liked GAG myself [http://gag.sourceforge.net/](http://gag.sourceforge.net/) if you use GAG grub2 will need to be on the root partition.

---

### Post by Lyfang on 2012-06-28
WARNING! Caution, don't try on production machines without fear of dealing with problems.

Presenting a different way, install GRUB from a Linux Live USB flash drive.

Launch the Linux Live USB flash drive (created with e.g. UNetbootin) & open the Terminal:

```
sudo fdisk -l
sudo mount /dev/sdaX /mnt
```
(e.g. sudo mount /dev/sda1 /mnt)
```
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
sudo update-grub
sudo reboot
```

---

