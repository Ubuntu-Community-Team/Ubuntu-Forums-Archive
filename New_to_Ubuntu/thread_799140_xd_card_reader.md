---
title: "xd card reader"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-05-18
I just picked up a xd Card reader from radio shack.  I plugged it in to the USB port and I thought it may just show up.  Wrong.  I probably need to mount it, right?  How do I do that?  The card reader says it is Mac and PC compatible.  Of course only specifying mac and Windows.  Any ideas?

---

### Post by rustutzman on 2008-05-18
Did you put media in it? It won't show up unless you have a card in it.

Russ

---

### Post by drrwhistle3 on 2008-05-18
Yes, I put the card in and I does have media on it.  but, nothing happens.

---

### Post by HotShotDJ on 2008-05-18
Is this the one you got?  I found one post in a review of it that says that it works under Ubuntu.  Obviously, that is not the case with you.  Honestly, I've had no luck getting my built-in card reader to detect xD cards, although it works swimmingly with other types of media.  In the end, I just plug my camera into the USB port to download the photos.  I can only suggest that you do some Googling around and see what you can find.

---

### Post by drrwhistle3 on 2008-05-18
Yep that's it!  I tried to plug it in several times and even tried to change the USB drive but no luck.  Any other ideas or a way to find it and manually mount it?

---

### Post by spiderbatdad on 2008-05-18
sometimes hot-plugging is enhanced with the option pci=routeirq look through ```
dmesg
```or boot one time with pci=routeirq by pressing 'e' at the grub menu, then arrow key to the line beginning with the word 'kernel,' press 'e' again. Go to the end of the kernel line...delete --quiet splash...add pci=routeirq
Hit enter, then 'b' to boot. This will not change the file /boot/grub/menu.lst. Edit that file to make the change permanent.

---

### Post by drrwhistle3 on 2008-05-18
This is what the dmesg said:



Does this mean anything to anyone?

---

### Post by spiderbatdad on 2008-05-18
lol. Please edit your post with code tags around that output, or delete and upload the thing as an archive by saving it to a text file and right click on the file...select archive. Then use the manage attachment tool below the reply window to upload the archive.

---

### Post by spiderbatdad on 2008-05-18
The file is not complete. Missing some possibly important info at the head. open terminal and select Edit>>current profile. Go to 'Scrolling' and increase the scrollback/kilobyte values.

---

### Post by HotShotDJ on 2008-05-18
> **spiderbatdad said:**
> The file is not complete. Missing some possibly important info at the head. open terminal and select Edit>>current profile. Go to 'Scrolling' and increase the scrollback/kilobyte values.Or, it might be easier for you both if you do this:```
dmesg > dmesg.txt
```and then simply attached dmesg.txt to your next post. :) (I'm interested in seeing if this thing works in Ubuntu as well... if so, I'm running out to Radio Shack tommorow!)

---

### Post by drrwhistle3 on 2008-05-18
I can't get the dmesg to attach. the files are too big.  Tried .txt, .odt, .doc.  All are over the limit.

---

### Post by spiderbatdad on 2008-05-18
> **drrwhistle3 said:**
> I can't get the dmesg to attach. the files are too big.  Tried .txt, .odt, .doc.  All are over the limit.

Try right clicking on the file and selecting 'Archive' then upload the archive. There is a 99kb max I believe.

---

### Post by HotShotDJ on 2008-05-18
> **drrwhistle3 said:**
> I can't get the dmesg to attach. the files are too big.  Tried .txt, .odt, .doc.  All are over the limit.
:shock:

Ok.  Open up Places --> Home Folder. Right click on the dmesg file file you created and choose Create Archive from the pop up menu.  Accept the defaults (.tar.bz2) and click create.  That should make it small enough.

---

### Post by drrwhistle3 on 2008-05-18
Ok I think this is it.

---

### Post by spiderbatdad on 2008-05-18
This is what I was referring to:>  PCI: Using ACPI for IRQ routing
[   24.475940] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
Also there is a note about booting: > Booting paravirtualized kernel on bare hardware 

The first instance can be attempted as outlined earlier, or by editing /boot/grub/menu.lst with the command ```
gksu gedit /boot/grub/menu.lst
```Scroll down to the section that begins:
####END DEFAULT OPTIONS###
Edit the end of the line that begins with the word 'kernel' to make it look like this:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro **pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
``` See where pci=routeirq is highlighted, above.

Save the file. Next. to fix the other issue:
```
sudo update-initramfs -k `uname -r` -c
```

Reboot.

---

### Post by drrwhistle3 on 2008-05-19
Before I do this I just want to verify;

I am supposed to edit the kernel line to match? 

Am I supposed to do it exact (UUID+604f.....)?

This is what mine says:

```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d8e22160-ee51-43aa-bbf5-24cc2bf7368e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d8e22160-ee51-43aa-bbf5-24cc2bf7368e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

```

I am just supposed to edit the first?

Just don't want to mess up.
Thanks

---

### Post by spiderbatdad on 2008-05-19
just the end of the line, as i have highlighted in bold, above.

---

### Post by drrwhistle3 on 2008-05-19
Ok, thought it would work but, not yet.  When I first rebooted it had a curser flashing on the screen and wouldn't do anything else, however the light on the card reader was on.  So I waited and waited but nothing.  I powered the computer down pulled the card reader and restarted.  This time it started.  A little weird, though.  The typical Ubuntu bar that advances wasn't there but I watch all he procedures(?) as it was starting.  Then entered user and password and started up.  Plugged card reader in and light flashed and that is it.  Tried a couple more times but nothing. Any other ideas?

---

### Post by spiderbatdad on 2008-05-19
with the card reader in, what output from ```
lsusb
```

---

### Post by drrwhistle3 on 2008-05-19
```
Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 043d:0065 Lexmark International, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:2105 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

---

### Post by spiderbatdad on 2008-05-19
hmmm. maybe detected as a disk?```
sudo fdisk -l
```searching bug reports...

---

### Post by spiderbatdad on 2008-05-19
have you seen this thread? 
[http://ubuntuforums.org/showthread.php?t=420721](http://ubuntuforums.org/showthread.php?t=420721)

And from this bug report:xD cards are still unreadable on Gutsy kernel 2.6.22-14-generic with all updates installed as of 10/15
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88992](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88992)
xd card do not appear to be readable...

---

### Post by drrwhistle3 on 2008-05-19
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10543    84638452+   7  HPFS/NTFS
/dev/sda3           10544       19083    68597550   83  Linux
/dev/sda4           19084       19452     2963992+   5  Extended
/dev/sda5           19084       19452     2963961   82  Linux swap / Solaris

```

---

### Post by drrwhistle3 on 2008-05-19
I just read your previous post.  Looks like I'm out of luck, huh.  I do appreciate your help and your time.  Sorry it didn't work out better.  Unfortunately, my wife has found another reason, beside her greeting card maker, not to get rid of M$ windows.  CRAP!

---

### Post by HotShotDJ on 2008-05-19
> **drrwhistle3 said:**
> Unfortunately, my wife has found another reason, beside her greeting card maker, not to get rid of M$ windows.Well, I can't help with the xD reader, but there IS a solution for the greeting card maker... Scribus (it's in the repositories)  You can grab the Greeting Card Template and Instructions here: [http://www.scotsworld.net/Downloads.html](http://www.scotsworld.net/Downloads.html).  It looks pretty simple to me.

---

