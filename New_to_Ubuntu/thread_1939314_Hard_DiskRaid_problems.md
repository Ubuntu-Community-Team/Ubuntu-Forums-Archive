---
title: "Hard Disk/Raid problems"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by orthogonal on 2012-03-11
Also posted here:  [http://askubuntu.com/questions/112085/wubi-hard-disk-not-cooperating-error-code-13-raid-problems](http://askubuntu.com/questions/112085/wubi-hard-disk-not-cooperating-error-code-13-raid-problems)

Earlier I was trying to dual-boot from a Live CD, and I had [this]("http://askubuntu.com/questions/111926/installation-stuck-on-installation-type-screen") problem.

As part of that, I opened the Terminal and typed sudo apt-get remove dmraid and then y.

Eventually, I got irritated and decided to try Wubi instead. My goal is to be able to boot into Ubuntu most of the time, but still have Windows 7 available.

Wubi did everything fine in the Windows environment, but when I restarted computer, I got the following error on startup:

NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware.

It then suggested that, in the former case, I run chdsk /f in Windows and then restarted to Windows twice. I did this, and there didn't seem to be any errors, but when I tried to reboot to Ubuntu, it gave me the same error.

For the latter case, it said If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory. I didn't know how to do this.

After the errors described above, it then said mounting /dev/disk/by-uuid/(letters and numbers) on /root failed: No such device The instructions it gave here were to run chkdsk /r and Reboot into Windows twice.

Finally, it said filesystem = ntfs, error code = 13

I'm new to Ubuntu and just trying to be a normal new user who wants to switch to it, while still holding onto Windows.  If I wasn't so dedicated on making the switch, I would have given up a long time ago - the irritation and risk of accidentally deleting all my Windows stuff isn't worth it.  What can I do and what does all this mean? I've spent the last hour on Google and all the forum posts are about people who can't boot into Windows anymore, which is really unnerving.

---

### Post by oldfred on 2012-03-12
Welcome to the forums.

Were drives ever in a RAID set or have you ever set RAID in BIOS?

How many partitions have you already used? MBR only allows 4 primary partitions, but one primary can be an extended which can hold many logical partitions. Windows has to boot from a primary, but data & Linux can boot from logical partitions.

Post this from a liveCD:
```

sudo fdisk -lu
```

Backup is always important best to have good backups and a Windows repairCD/USB.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

