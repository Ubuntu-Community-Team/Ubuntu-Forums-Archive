---
title: "How to Boot LiveCD with Windows Bootloader"
date: 2009-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by TJCIB on 2009-01-31
What we will do:
Give the option of booting to an Ubuntu 8.10 LiveUSB or booting Windows XP from the hard drive WITHOUT the use of a boot CD OR writing GRUB to the Master Boot Record (yay).  

Why I did this:
My BIOS did not support booting from USB.
Although it was intended because booting from USB wasn’t possible, it works and is my preferred method on my systems that CAN boot from USB, it is simply another option rather than BIOS.  Especially those times I rebooted and either forgot to plug in the USB soon enough, or forgot to take it out.  As mentioned before, it also keeps away from the MBR.

This will require a little work in both Ubuntu LiveCD and Windows.

What you need:
•	A LiveCD for Ubuntu 8.10
•	Windows already installed on hard drive (tested on XP Pro)
o	This how-to assumes XP is installed on the first partition of the first HD

go here, [http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/]("http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/"), if you need help making your LiveUSB for this to work with.

Boot into the Ubuntu LiveCD.  We will first collect all the files we need from there.

```
sudo mkdir /media/disk
```
```
sudo mount /dev/sda1 /media/disk
```
```
sudo mkdir /media/disk/boot
```

```
sudo cp /cdrom/casper/initrd.gz /media/disk/boot
```

```
sudo cp /cdrom/casper/vmlinuz /media/disk/boot
```

```
sudo nano /media/disk/menu.lst
```

paste this into the file.  Close (crtl+x) and confirm save (y)
```
######################################################
color black/cyan yellow/cyan
timeout=2
default=1
hiddenmenu

title Windows XP
	rootnoverify (hd0,0)
	chainloader +1
	boot

title Run Ubuntu 8.10 from USB DISK
root (hd0,0)
kernel /boot/vmlinuz file=/boot/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /boot/initrd.gz
boot 
######################################################
```

```
sudo cp -R /cdrom/preseed /media/disk/boot
```


Now save this how-to and boot into Windows...see you in a few minutes...

Now You’re In Windows.
Right Click link below and 'Save Target As' to download the file: grldr (191 KB)
VERY IMPORTANT: Make sure the filename is enclosed in " " marks
i.e. Put "grldr" INCLUDING the " " in the Save Target As dialog box

The file should be saved into the top level (not inside any folders) of c:\
[http://www.icpug.org.uk/national/programs/grldr]("http://www.icpug.org.uk/national/programs/grldr")

(I got this file from the Win'N'Lin NewB Project, here is the link FYI [http://www.icpug.org.uk/national/linnwin/step1-xp.htm]("http://www.icpug.org.uk/national/linnwin/step1-xp.htm"))
The rest of this is basically from that same website, but I will put it here for simplicity and make a few changes per this situation.  I want to thank these guys for all their information!

1.	From the Start Menu select Control Panel

2.	Open System

3.	Select the Advanced tab
You will see three buttons all labeled Settings.

4.	Click the Settings button for Startup and Recovery

5.	Ensure the option Time to display list of operating systems is ticked and select a delay time.

This delay defines how long, in seconds, the list of operating systems is shown before the default automatically starts. The value chosen is a matter of personal choice. The smaller the value, the quicker the default, usually Windows, will boot. The larger the value, the longer you have to select Linux. I suggest newbies start with a value of 10 to give plenty of time to make a selection. As you gain experience you may find this too slow when booting the default system. For this reason, I use a value of 2 and when I want to choose Linux I get ready with my finger on the keyboard! You can always change the value later if you don't get it right first time.

6.	click the Edit button

7.	Add the following line to the list in the [operating systems] section. This line is usually the last line in the file. Copy the line EXACTLY, including quotes, and press Enter at the end.

```
c:\grldr="Start Linux"
```


File should look something like this (note the line starting with “multi(0)” should be one line, even though it may show up on two lines of the screen.  You can maximize notepad to check this:

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
c:\grldr="Start Linux"
```

8.	Close the Notepad window and click the Yes button when asked 'Do you want to save the changes?'
9.	Click the OK button on the Startup and Recovery window.
10.	Click the OK button on the System Properties window.
11.	Close the Control Panel window.


What you should end with is two new files on your c:\ drive in Windows XP.
1.	grldr
2.	menu.lst

You should also have a folder named “boot” in the c:\ drive [c:\boot\] with the following
1.	initrd.gz
2.	vmlinuz
3.	preseed (folder)
a.	in this you should have three (3) *.seed files
b.	the most important is ubuntu.seed, but I put the other ones there cause…I did.

You should be able to plug your LiveUSB in and reboot.  You should have a menu giving you the option to choose either XP or Ubuntu 8.10.

I hope this works for you.  Let me know if it doesn’t.
I used the above link as a source as well as [www.pendrivelinux.com](www.pendrivelinux.com)
To undo what you did, you can basically delete everything you put in the c:\ drive and take out the edited changes in the Control Panel>>System section

---

### Post by Jose Catre-Vandis on 2009-02-01
Nice work :)

---

### Post by TJCIB on 2009-02-02
mis-titled....arg

---

### Post by godspiral on 2009-11-02
looks easy, and thank you, but:

* this assumes/requires a live-usb setup for the usb, with it formatted as fat32?
  * will this still work if you have ext3/swap partitions setup on usb?

* the first "sudo mkdir /media/disk" is made on what device? (linux newb question... I understand that rest of commands are copying files to the windows HD)
  *nothing magical about that first mkdir command... all of the copying can just as easily be done in windows?

---

