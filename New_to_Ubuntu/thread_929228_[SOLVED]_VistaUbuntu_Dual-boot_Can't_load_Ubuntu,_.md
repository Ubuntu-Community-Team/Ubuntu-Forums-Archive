---
title: "[SOLVED] Vista/Ubuntu Dual-boot: Can't load Ubuntu, goes  to &amp;quot;grub&amp;quot;"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Nerdriot on 2008-09-24
Well, I have a pretty bad problem. The machine I'm using here dual-boots Vista and Ubuntu Hardy. Vista was installed first, and I installed Ubuntu via Wubi (thought I'd give it a shot). Well, about an hour ago, the electricity in the house went out for about a minute, and when I booted the machine back up, and selected "Ubuntu" from the list, it brought me to a command line with "Grub >". I have no idea what to do. I can't do ANYTHING with it.

I booted up a ubuntu live cd, and searched for the Ubuntu partition, but I simply can't find it. I have no idea where Wubi installed Ubuntu. There's only one HD, but I still can't find the partition. I even loaded Gparted to see if it would show it. Blah.

Also, I checked c:\ubuntu aanfound a "menu.lst", and it appears to be the list I get when  I try to boot into Ubuntu.

I'm seriously lost here. ANY help would be greatly appreciated.

---

### Post by Crafty Kisses on 2008-09-24
Is this an actual dual boot, or are you going through Wubi?

---

### Post by eternalnewbee on 2008-09-24
You could reinstall ubuntu. That should work.
But you might want to wait for reactions from more experienced users. Good luck

---

### Post by Nerdriot on 2008-09-24
It's a dual-boot, I just "installed" Ubuntu through Wubi in Vista. I remember Wubi creating a partition for Ubuntu, and the swap, etc., but I just can't find it. I should have just installed Ubuntu "the old fashioned way", but I was feeling lazy... :(

---

### Post by Nerdriot on 2008-09-24
> **eternalnewbee said:**
> You could reinstall ubuntu. That should work.
But you might want to wait for reactions from more experienced users. Good luck

Thank you for the well-wishing... :) I have already accumulated quite a lot of stuff on that partition, so I don't want to lose it unless I HAVE to, hehe... :)

---

### Post by Crafty Kisses on 2008-09-24
Try booting back into Vista and shutting down properly, then boot back into Ubuntu see if that solves the issue.

---

### Post by Nerdriot on 2008-09-24
> **Codename said:**
> Try booting back into Vista and shutting down properly, then boot back into Ubuntu see if that solves the issue.

Tried it :( I was hoping a cold boot would bring it back to life, but it seems like it's borked.

The menu.lst is in c:\ubuntu\winboot, so I'm doubting that it's the menu.lst that's loaded when the computer's booted up...

I'm so lost.

---

### Post by Crafty Kisses on 2008-09-24
I'm not sure you can do this since you're using Wubi, but there is something called "Super Grub Disk" it recovers your GRUB boot loader, you might want to check it out, here is the link:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Nerdriot on 2008-09-24
> **Codename said:**
> I'm not sure you can do this since you're using Wubi, but there is something called "Super Grub Disk" it recovers your GRUB boot loader, here is the link, you might want to check it out > [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Thank you! I'll give it a shot and see if that works out. :) I hope so, because I'm COMPLETELY at a loss here. It's almost as if /boot/grub/menu.lst doesn't even exist, or it just won't load. I'm wondering if the partition might be damaged now or something...

---

### Post by Crafty Kisses on 2008-09-24
The thing is I don't think Wubi really partitions, you can easily remove Ubuntu from Windows and try reinstalling it like that, but try my method, see if that springs Ubuntu back to life.

---

### Post by Nerdriot on 2008-09-24
> **Codename said:**
> The thing is I don't think Wubi really partitions, you can easily remove Ubuntu from Windows and try reinstalling it like that, but try my method, see if that springs Ubuntu back to life.

I'm thinking you're right. When I booted up a livecd of Ubuntu, the ONLY thing I could find resembling a Ubuntu "install", was in Vista, under the "ubuntu" folder. There was another folder named "disks", which had question marks under the permissions, owner, etc. when I checked it with ls -la.

I should just install Ubuntu the way I know how, lol. Wubi might be really neat for people who need it, but I prefer the other way. At least then, I can find my ext3 partitions.

Tanks again for your help! I'm going to boot that livecd up again and check if maybe Ubuntu shows up in in another dir, and if not, I'm just going to delete it and start over.

---

### Post by akiratheoni on 2008-09-24
I'm not too familiar with Wubi but the reason why you can't find a partition and you can only find an ubuntu folder in the Vista partition is because Wubi doesn't create any partitions when you install Ubuntu through it. Just so you know why you couldn't find any partitions when you booted the Live CD.

---

### Post by Crafty Kisses on 2008-09-24
The real way to see if you have a Linux partition is boot Ubuntu from the LiveCD and run the following command:
```
sudo fdisk -l
```
Post back the results here.

---

### Post by caljohnsmith on 2008-09-24
Nerdriot, a standard Wubi install just installs your Ubuntu into Windows in the C:\ubuntu directory; in other words, the main Wubi Ubuntu install is a huge gigabyte file in Windows, however big you allocated for Ubuntu. To delete/uninstall it, you have to go to "Add/Remove Programs" (or whatever it is in Vista, I'm used to XP), and there you can uninstall Ubuntu.

---

### Post by Nerdriot on 2008-09-24
Gah! That explains it. There is no partition for Ubuntu... God, I'm slow... I should have paid more attention..

So now my only question is, I downloaded things in Ubuntu, and I have no idea where they are now, since I can't get into Ubuntu anymore... If you install with Wubi, and you use Ubuntu installed that way, where are all your files saved to? I can't find an answer for that anywhere (curse you, Google...)

Anyone know?

Thanks for all the help, btw!

---

### Post by caljohnsmith on 2008-09-24
> **Nerdriot said:**
> Gah! That explains it. There is no partition for Ubuntu... God, I'm slow... I should have paid more attention..

So now my only question is, I downloaded things in Ubuntu, and I have no idea where they are now, since I can't get into Ubuntu anymore... If you install with Wubi, and you use Ubuntu installed that way, where are all your files saved to? I can't find an answer for that anywhere (curse you, Google...)

Anyone know?

Thanks for all the help, btw!
OK, try this: boot your Ubuntu Live CD, open a terminal (applications > accessories > terminal), and then:
```
sudo fdisk -l

```
Find your Vista partition as /dev/sdX, for instance sda1, and then use that as follows:
```
sudo mount /dev/sdX /mnt
cd /mnt/ubuntu/disks
```
And then use "ls -l" and "cd" to look for your main Ubuntu partition in that folder and the folders below it; you'll know it by its huge gigabyte size. It's been too long since I used Wubi, so sorry I don't remember exactly where it is in those folders. Once you find it, run an fsck on it:
```
sudo fsck -y <Ubuntu partition>
```
Also, post the output of all the above commands.

EDIT: if I remember correctly, the Ubuntu partition (file) is called "root.disk", but I could be wrong.

---

### Post by Nerdriot on 2008-09-24
Oh boy, this doesn't look good...

So, here's the output for fdisk -l:

```
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40415   305537368+   7  HPFS/NTFS
/dev/sda2           40416       41345     7030800    7  HPFS/NTFS

```

So, I mounted sda1 to mnt, then tried to cd to /mnt/ubuntu/disks, and it doesn't exist anymore. I know it DID exist, when this whole mess started, but now it's gone. I remember when I checked it with ls -la, it had question marks in the "permissions" and "owner" sections. Confused me...

I guess this means that I've lost all the files then, huh? That sucks... :(

---

### Post by Nerdriot on 2008-09-24
Also worth noting, regarding "disks"; when I tried to ls or cd to disks, when it DID exist, it gave me a nice input/output error message. I wish I would have saved it, but it seemed nasty.

I guess it's all gone now. Sadface...

---

### Post by caljohnsmith on 2008-09-24
If you:
```
cd /mnt
ls -l
```
Does it show your "ubuntu" directory at all? And if it does, then:
```
cd ubuntu
ls -l
```
And repeat that into whatever other directories exist there, and tell us what is left in your ubuntu directory tree, if anything. Also, can you "cd" into Vista's other directories without getting an "input/output error"?

---

### Post by Nerdriot on 2008-09-24
> **caljohnsmith said:**
> If you:
```
cd /mnt
ls -l
```
Does it show your "ubuntu" directory at all? And if it does, then:
```
cd ubuntu
ls -l
```
And repeat that into whatever other directories exist there, and tell us what is left in your ubuntu directory tree, if anything. Also, can you "cd" into Vista's other directories without getting an "input/output error"?

This is all I have in the ubuntu dir:

```
ubuntu@ubuntu:/mnt/ubuntu$ ls -l
total 152
-rwxrwxrwx 1 root root   1795 2008-09-23 14:56 curl_log.txt
drwxrwxrwx 1 root root      0 2008-09-23 14:55 docs
drwxrwxrwx 1 root root   4096 2008-09-23 19:05 install
-rwxrwxrwx 2 root root   2682 2008-09-23 14:56 metadl_log.txt
-rwxrwxrwx 1 root root  25214 2008-06-30 15:30 Ubuntu.ico
-rwxrwxrwx 2 root root 113921 2008-09-23 14:55 Uninstall-Ubuntu.exe
drwxrwxrwx 1 root root      0 2008-09-23 14:55 winboot


```

Last time I checked it with the livecd, it did have a "disks" folder, but that's gone now. I was only getting the input/output error on that folder. Once I booted back into Vista, and then rebooted using the livecd, the "disks" dir is gone. :(

---

### Post by Nerdriot on 2008-09-24
Also, here's ls -l for the other dirs:

```
ubuntu@ubuntu:/mnt/ubuntu$ ls -l docs
total 0
ubuntu@ubuntu:/mnt/ubuntu$ ls -l install
total 0
ubuntu@ubuntu:/mnt/ubuntu$ ls -l winboot
total 404
-rwxrwxrwx 1 root root    806 2008-06-30 15:30 menu.lst
-rwxrwxrwx 1 root root 188547 2008-06-30 15:30 wubildr
-rwxrwxrwx 1 root root 204963 2008-06-30 15:30 wubildr.exe
-rwxrwxrwx 1 root root   8192 2008-06-30 15:30 wubildr.mbr

```

---

### Post by Nerdriot on 2008-09-25
Well, here's an interesting find...

While searching today for root.disk (thought I'd give it one last shot before trashing it), I ran across a directory named "found.000", and when I  checked it, inside was this...

```
ubuntu@ubuntu:/mnt$ ls -l found.000
total 4
drwxrwxrwx 1 root root 4096 2008-09-25 00:05 dir0000.chk

```

When I checked in "dir0000.chk", it had root.disk, as well as other necessary files for loading Ubuntu. For instance...

```
ubuntu@ubuntu:/mnt$ ls -l found.000/dir0000.chk/
total 14648444
drwxrwxrwx 1 root root        4096 2008-09-23 14:51 boot
-rwxrwxrwx 2 root root 14000000000 2008-09-24 22:54 root.disk
drwxrwxrwx 1 root root           0 2008-09-23 14:55 shared
-rwxrwxrwx 2 root root  1000000000 2008-09-23 16:59 swap.disk

```

And...

```
ubuntu@ubuntu:/mnt$ ls -l found.000/dir0000.chk/boot/
total 19612
-rwxrwxrwx 1 root root  420224 2008-08-20 22:15 abi-2.6.24-19-generic
-rwxrwxrwx 1 root root   74164 2008-08-20 22:15 config-2.6.24-19-generic
drwxrwxrwx 1 root root       0 2008-09-23 14:49 grub
-rwxrwxrwx 1 root root 7997398 2008-09-23 14:51 initrd.img-2.6.24-19-generic
-rwxrwxrwx 1 root root 8413698 2008-09-23 19:04 initrd.img-2.6.24-19-generic.bak
-rwxrwxrwx 1 root root  103204 2007-09-28 11:03 memtest86+.bin
-rwxrwxrwx 1 root root 1152364 2008-08-20 22:15 System.map-2.6.24-19-generic
-rwxrwxrwx 1 root root 1903096 2008-08-20 22:15 vmlinuz-2.6.24-19-generic

```

So this is nice, I'm thinking. Now all I need to know is the directory structure of Wubi's ubuntu install, so I can place these files back where they belong, recover my "lost" data, and then uninstall it, and then finally install Ubuntu the real way. Woo!

I'll search around for the directory structure, unless one of you guys already know it, in which case, thanks a ton!

And thanks for all your help, guys!

---

### Post by Paqman on 2008-09-25
> **Nerdriot said:**
>  Well, about an hour ago, the electricity in the house went out for about a minute

Wubi REALLY doesn't like power cuts. From the Wubi site:
> 
Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


If the filesystem is too broken, you'll have to reinstall. You can use the Ubuntu LiveCD to boot up into a live session and make a backup of your /home folder and any data you want to recover. Then boot into Windows, uninstall Ubuntu and reinstall.

If power cuts are going to continue to be a threat, i'd advise installing Ubuntu onto it's own partition.

---

### Post by Nerdriot on 2008-09-25
> **Paqman said:**
> Wubi REALLY doesn't like power cuts. From the Wubi site:


If the filesystem is too broken, you'll have to reinstall. You can use the Ubuntu LiveCD to boot up into a live session and make a backup of your /home folder and any data you want to recover. Then boot into Windows, uninstall Ubuntu and reinstall.

If power cuts are going to continue to be a threat, i'd advise installing Ubuntu onto it's own partition.

Thank you, and you're right; I think it's best to set up Ubuntu the real way.

On a good note, I did manage to get it working again. I created a folder in "c:\ubuntu" named "disks", and placed all of the .disk files there, as well as the grub directories and so on. It booted up normally. Now, I'm moving everything over to Vista, and then I'm going to install Ubuntu on a separate partition.

Thanks a lot, guys! I'm marking the thread "solved". :)

---

### Post by kansasnoob on 2008-09-25
When you're ready to do an actual dual boot this guide is simple and straight forward:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Of course start by cleaning up and defragging Vista, and backup your info just in case!

---

### Post by rscheideman on 2008-09-25
Wubi is not yet supported by ubuntu. I would dual boot the old school way.

---

### Post by JacquiOh on 2008-09-25
If you're using Vista and Ubuntu as I am, you might want to turn off the automatic updates on Windows. I had to reinstall Ubuntu after Vista wrote over my Ubuntu partitions following a Windows "Security Update". I tried all the GRUB disks and recovery stuff and nothing would get it back for me. All was lost.

That was a month ago and I'm still so SO SO annoyed (I rarely use Windows, so all my stuff was in Ubuntu). If I could get my mobile phone working with Ubuntu I'd be rid of Windows forever. :mad:

---

### Post by Nerdriot on 2008-09-25
> **JacquiOh said:**
> If you're using Vista and Ubuntu as I am, you might want to turn off the automatic updates on Windows. I had to reinstall Ubuntu after Vista wrote over my Ubuntu partitions following a Windows "Security Update". I tried all the GRUB disks and recovery stuff and nothing would get it back for me. All was lost.

That was a month ago and I'm still so SO SO annoyed (I rarely use Windows, so all my stuff was in Ubuntu). If I could get my mobile phone working with Ubuntu I'd be rid of Windows forever. :mad:

Oh my God, thanks for the heads up. This is my girlfriend's computer, and I would be severely upset if the installation got borked because of Microsoft garbage. (Also, because I'd have to fix it... :P)

Myself at home, I have a dual boot with XP, but only so I can play certain games (Guild Wars, mainly). I use Ubuntu for everything else. I actually think she'll be able to run Guild Wars and other Windows games through Wine, since she has a much better machine than I do, so I may convince her to let me completely remove Vista from here... ;)

---

### Post by Paqman on 2008-09-25
> **rscheideman said:**
> Wubi is not yet supported by ubuntu. I would dual boot the old school way.

Actually, as of Hardy, it is. It's even included on the LiveCD.

---

