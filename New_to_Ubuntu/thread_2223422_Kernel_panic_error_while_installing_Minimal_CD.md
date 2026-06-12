---
title: "Kernel panic error while installing Minimal CD"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by jacoby2 on 2014-05-11
I recently created a bootable USB of [Ubuntu 14.04 Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso/") using the disk destroyer. When I boot, I have the options - Install, Advanced Install, Command Line Install & Help. Clicking on any of the install options shows this error:

kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,2)

Note-

[LIST=1]
[*]The md5check was correct.
[*]The USB was full formatted to FAT32 prior to the installation via dd.
[*]I'm currently using [Porteus 3.0]("http://porteus.org/") as my OS.
[*]I tried installing using UNetbootin, but it didn't work.
[/LIST]

I have checked other forums, and the solutions said something about Grub or updating the kernel. Since I'm new to Linux, I'm not familiar with any of those terms. So a detailed answer would really be helpful. Thanks!

---

### Post by sudodus on 2014-05-11
Welcome to the Ubuntu Forums :-)

Can you describe exactly the command you used with dd?

I know that it works to make a USB boot drive with dd, but I don't do it directly, because of the risk (you know the nick-name already). Instead I made a shell-script, mkusb, to make cloning or flashing with dd safe. See this link
[URL="http://ubuntuforums.org/showthread.php?t=1958073"]
Howto make USB boot drives[/URL]

It seems from the link, that you have the 32-bit version of the mini.iso. It should work with most computers, but not with UEFI and not with powerpc.

---

### Post by jacoby2 on 2014-05-11
[COLOR=#000000][FONT=monospace]I used this command: 

sudo dd if=[/FONT][/COLOR]/mnt/sda1/mini[COLOR=#000000][FONT=monospace].iso of=/dev/sdb

I'll check your link once I get home. Thanks![/FONT][/COLOR]

---

### Post by sudodus on 2014-05-11
Input file = the iso file
Output file = a block device

It looks OK. But obviously something does not work.

- Can you try if the USB drive works in another computer? (You can stop before it starts writing to disk)
- Or can you try some other Ubuntu flavour, for example a desktop iso file, or an older version of mini.iso?

Edit: The 12.04 LTS works only from CD/DVD, not from USB. The 13.10 and 14.04 LTS mini.iso work from USB.

---

### Post by jacoby2 on 2014-05-11
My other laptop went berserk a few days ago, so I'm stuck with this Porteus device for now. 

I previously downloaded the desktop iso of Ubuntu 14.04 on the same USB stick (using UNetbootin, but it's not working now for some reason) and it installed and ran fine. I could not do the full install but ran the Live version instead since it's just a 4 GB drive. So I planned to install the barebones to cut down space and also because the Live version takes a lot of time to boot and is not always stable (even with persistence).

So this morning I formatted the USB drive to FAT32 (and thus deleting the Ubuntu 14.04 live version, bad decision) hoping to install the minimal CD and start from scratch, and now here I am. Mine's a netbook, so burning the iso into a CD is not an option. Does it have anything to do with the grub thing as other forums say?

I'll check if the older versions work, but I was really hoping the latest version did. Anyways, I'll keep you updated!

Thanks!

---

### Post by sudodus on 2014-05-11
If you can run Ubuntu 14.04 live off the pendrive, you should be able to install Lubuntu, Lubuntu Core or a mini system and run that too. Did you download and test Ubuntu 14.04 32-bit or 64-bit? Is there Windows in the netbook? In that case what version of Windows?

I suggest that you try a few alternatives for example a text based system made from the mini.iso, that can be installed with 9w according to these links (posts #88, #89 and #147)

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)
[http://ubuntuforums.org/showthread.php?t=2209683&page=8&p=13003225#post13003225](http://ubuntuforums.org/showthread.php?t=2209683&page=8&p=13003225#post13003225)

You can also look at these links (posts #40: 9w, and #64: the One Button Installer) 

[http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216](http://ubuntuforums.org/showthread.php?t=2216356&page=2&p=13003216#post13003216)
[http://ubuntuforums.org/showthread.php?t=2216356&page=4&p=13016786#post13016786](http://ubuntuforums.org/showthread.php?t=2216356&page=4&p=13016786#post13016786)

or use some of the other tarballs of the One Button Installer

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

-o-

And last but not least: What did you intend to do, and what were you actually doing?

Let us assume that the pendrive flashed with mini.iso is good. You booted. What was the target drive? Did you intend to install from the mini.iso to the internal drive, to another USB drive or to the same USB drive? It does not work to install to the same drive as you install from, at least not if it is made from an Ubuntu iso file. Maybe this was what you did because the drives were mixed up. And maybe the file system on the pendrive was damaged in that process, so that you should flash it again (with dd or mkusb).

---

