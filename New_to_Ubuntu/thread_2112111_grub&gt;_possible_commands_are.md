---
title: "grub&gt; possible commands are:"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by Jclot on 2013-02-03
Green user on a dell Dimension 3100 running Windows XP.
  Installed 12.10 using Wubi
  After install, I select “reboot now”
  Booted into Ubuntu.
  The PC processed and left me at a screen reading:
   
  “Grub>
  Possible commands are:”
   
  There is a list of possible commands to use. I don’t know which one to select.
  Any advice would be appreciated.
  Please understand that I’m at the bottom of the Ubutu learning curve. 

I'm unable to provide a screenshot.

---

### Post by bcbc on 2013-02-04
Did this happen the second time you booted Ubuntu? Or the first?

Did you have any issues on Ubuntu before it happened?

You can enter the following commands at the grub prompt:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
```

See what that says. Then enter "reboot" to restart the computer or Ctrl+Alt+Del

---

### Post by Jclot on 2013-02-04
Thank you for responding!
  This occurred on the second time booting into ubuntu.
  The first time there was an issue, but I didn&#8217;t document it. Assumed it was a bad install and reinstalled.
  I entered the code suggested and ended with the following:
   
    [FONT=&quot]grub> search -s -f -n /ubuntu/disks/root.disk[/FONT]
  [FONT=&quot]grub> echo $root[/FONT]
  [FONT=&quot]hd0,msdos1[/FONT]
  [FONT=&quot]grub> loopback loop0 /ubuntu/disks/root.disk[/FONT]
  [FONT=&quot]grub> set root=(loop0)[/FONT]
  [FONT=&quot]grub> reboot[/FONT]
  [FONT=&quot]error: can&#8217;t find command &#8216;reboot&#8217;[/FONT]
  [FONT=&quot]grub>[/FONT]
  
   
  Ctrl+Alt+Del reboots and brings me to the OS selection screen.
  Selecting ubuntu brings me back to grub.
  I&#8217;m unable to copy paste. Entered the code as you see.

---

### Post by bcbc on 2013-02-04
Okay - so it's finding the root.disk okay.

What if you try to load the grub menu. This time do:

```
search -s -f -n /ubuntu/disks/root.disk
echo $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
configfile /boot/grub/grub.cfg
```

---

### Post by Jclot on 2013-02-04
Brings me to a slightly different grub screen.
 grub> is in the top left corner of an otherwise empty screen.

---

### Post by bcbc on 2013-02-04
Hmm. You could try to boot it manually... but it seems like there's something else wrong... I'd guess some corruption to either the root.disk or NTFS. Since corruption of the grub.cfg seems less probable.

So you could either run "chkdsk /f" from Windows (go to Computer, right click on the C: drive and then select Properties, Tools, Error checking... Check now. Then "fix automatically'. You'll have to reboot to let it complete. (I'm assuming it's your C: drive that you installed on).

Or you could just try to boot the root.disk. This is how (generic instructions for any Wubi install):
```
search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

Since yours is on /dev/sda1 it might be easier for you to type in:
```
search -s -f -n /ubuntu/disks/root.disk
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

---

### Post by Jclot on 2013-02-04
I did this first &#8220;(go to Computer, right click on the C: drive and then select Properties, Tools, Error checking... Check now. Then "fix automatically'. You'll have to reboot to let it complete. (I'm assuming it's your C: drive that you installed on).&#8221;
  Entered the second group of code next. The result was similar to the third option.
  The result for the third option was the following:
  search -s -f -n /ubuntu/disks/root.diskloopback loop0 /ubuntu/disks/root.diskset root=(loop0)linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splasherror: invalid extent.initrd /initrd.imgerror: you need to load the kernel first.booterror: you need to load the kernel first.

---

### Post by bcbc on 2013-02-05
So there's something diagnostic-y to look at.
> error: invalid extent

How big is your hard drive? e.g. see this thread [http://ubuntuforums.org/showthread.php?t=1997316](http://ubuntuforums.org/showthread.php?t=1997316) (does that look like a promising avenue?)

---

### Post by Jclot on 2013-02-05
bcbc,
Windows disk management indicates I have only C drive partition and it's 149gb with 103gb free.
Could this be an issue?

---

### Post by bcbc on 2013-02-05
That doesn't seem likely.

Do you have a bootable Ubuntu USB or a DVD you can boot from to a Live desktop (select "Try Ubuntu") and then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?

---

### Post by Jclot on 2013-02-05
As my PC isn't recognizing my CD/DVD player, I think my next step is going to be creating a bootable usb flashdrive.
I suspect my hard drive is completely corrupt and I plan on removing Windows.
Would it be a bad idea to erase my hard drive prior to booting ubuntu from a bootable flash?
Less garbage to work through?
I sincerely appreciate your help!

---

### Post by bcbc on 2013-02-05
I would never recommend erasing your hard drive. That's a decision that only you can make. 

But something I find personally is that when I'm in problem solving mode, sometimes I'm more likely to do drastic, irreversible things, and then later go - oh crap. Because it's easier to jump to conclusions when you can't get something to work (e.g. assuming the reason Ubuntu doesn't work is because of a corrupt drive - which may not in fact be the case).

There's no benefit to be gained by trashing Windows prior to running the bootinfoscript, so my advice is to be patient - at least your computer works for now.

---

### Post by Jclot on 2013-02-06
I agree! The only reason I'd consider it is a secondary 11 year old machine that is too slow to use effectively. I recognize that some of it's slowness comes from the perspective of my having used  a better laptop, but a great deal is the fact that it's old. And sad. I hope to give it a second life with a new, clean OS.
  
I created a bootable flash and loaded Ubuntu from the flash drive.
The end result was an unresponsive black screen
No cursor, and no response to F, ctrl,alt,del commands.

I'm new and unsure of the etiquette...should I post this as anew thread?

Again, Thanks!

---

### Post by bcbc on 2013-02-06
The benefit of a new thread is your thread title will attract different people to help who may have more knowledge in that new area. There's nothing wrong with creating a new thread for a completely new subject.

However, booting to a black screen is fairly common - you can review this popular askubuntu thread for more info: [http://askubuntu.com/q/162075/14916](http://askubuntu.com/q/162075/14916)

---

### Post by Jclot on 2013-02-06
Holy Frijoles! It worked!
[http://askubuntu.com/q/162075/14916](http://askubuntu.com/q/162075/14916)
1000 thanks!

---

