---
title: "[SOLVED] Help on formatting WinXP disk with grub inside"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by belier on 2008-10-20
Hi.

After installing kubuntu this weekend I've decided to make a new install of formatting the hard disk. The problem resides in the fact that the disk I want to format is the boot disk. If I format it using the full format option, will I list the GRUB?
If the answer is yes, what do I must do to recover it?

Thanks in advance.

(Yes, I know, WinXP is for sissies, but also for Bioschock, HL2, COD4, etc... :lolflag:)

---

### Post by billgoldberg on 2008-10-20
> **belier said:**
> Hi.

After installing kubuntu this weekend I've decided to make a new install of formatting the hard disk. The problem resides in the fact that the disk I want to format is the boot disk. If I format it using the full format option, will I list the GRUB?
If the answer is yes, what do I must do to recover it?

Thanks in advance.

(Yes, I know, WinXP is for sissies, but also for Bioschock, HL2, COD4, etc... :lolflag:)

Sorry man, but I don't understand what you are trying to say.

---

### Post by belier on 2008-10-20
Easy.
I have two disks. One with WinXP on it, that is the boot disk, and the other with ubuntu installed.
I'm going to format WinXP dosk in order to reinstall it. So I asume that I'm going to lost GRUB and I'll not be able to boot the ubuntu disk.
I've been reading about booting from LiveCD and reinstalling GRUB on the MBR. Is LiveCD the CD that I used to install ubuntu for first time? Does it let's mee boot from ubuntu disk?

---

### Post by Archmage on 2008-10-20
There are two (or better three) different install-discs. One of them can boot into a live system this is the Live-CD. The other ones are alternate-CD (and server-CD).

From the Live-CD it is possible to restore GRUB. There are also other ways.

I wonder when Microsoft Windows will bringt out a system that will respekt the boot loader and don't erase it.

---

### Post by belier on 2008-10-20
The question is: Once the WinXP disk formatted, is there any way to recover GRUB? From the bootable CD I used to install, it's possible to start ubuntu on hard disk and then recover GRUB?

---

### Post by ajgreeny on 2008-10-20
I assume you have a Ubuntu Live CD, which is the easiest way to do this.  If I'm right simply:-

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

Good luck with this.  I can see no reason why it shouldn't work.  It has for me a few times, and for many other users as well.

---

### Post by belier on 2008-10-20
Thx to all. I'll try to do it.:)
First of all, just to see if it's LiveCD what I have.

---

### Post by belier on 2008-10-21
What I've done and hasn't worked:

I've booted from kubuntu CD. From the options I've chosen the one of testing kubuntu without installing.
And then I followed your tutorial.
Still booting from windows.
The answer from "find /boot/grub/stage1" was "(hd0,0)". So I did "root (hd0,0)"
The messages I got from "setup (hd0)" seemed to indicated that everything went OK.

Any suggestion?

---

### Post by ajgreeny on 2008-10-21
OK, from the live CD let's see the output of sudo fdisk -l to try to find out if your windows hard disk is set as the first disk in the system.  I am a bit baffled at the moment, but if grub was put on to the first booting disk it should show grub on startup, unless, of course, you set windows to be the default option in your grub menu.lst file, and you either hid the grub menu or set a very short default time for the menu to show.

---

### Post by belier on 2008-10-21
Thanks for answering. Now I'm at work. 
And yes, I had WinXP as default SO on menu.lst file with 10 seconds of timeout (default timeout).

When at home I'll make a the fdisk and see what it says.

---

### Post by ajgreeny on 2008-10-21
OK, so if windows was the default OS to boot from grub, it will still be the first to boot, though you should see the menu, unless that was hidden, when a quick press of Esc will bring it up.

---

### Post by belier on 2008-10-21
I was seeing the menu before installing winxp. However, menu.lst file must be intact.
The delay between last action of POST (Checking NVRAM) and windows load screen is 0.
In three hours I'll be at home to continue testing things. First of all fdisk.
Fortunately, installation is recent and I don't have added  too much stuff...

---

### Post by belier on 2008-10-21
Well. I did what you told me. With fdisk -l i get the list of devices. I see that kubuntu disk is sda1. I remember that it was sde1 on first install.
I've reinstalled kubuntu and I still have no boot menu...

---

### Post by ajgreeny on 2008-10-21
Sorry, but I am now out of my depth here and will have to leave it to other people to try and help you.  Good luck; I'm sure it must be a simple thing that just has not occurred to me, and someone else will get the problem sorted.

---

### Post by caljohnsmith on 2008-10-21
To begin with, how about posting the full output of:
```
sudo fdisk -lu
```
So we can get a better picture of your setup.

---

### Post by belier on 2008-10-22
Well. 
First of all let me introduce you my disks. I have 5 disks: 3 SATA of 200GB each one, and 2 IDE of 85GB and 120GB.
I have installed ubuntu on the 85GB as it was originally to give him a go. Now I have the 120 one formatted with ext3 for having more additional space.
My boot disk on bios was one of the 200GB.

What I've discovered:
After my first kubuntu installation, I had the next disk map:

/sda1 -> 200GB with XP
/sdb1 -> 200GB NTFS
/sdc1 -> 200GB NTFS
/sd31 -> 85GB kubuntu
/sdd1 -> 120GB ext3

After formatting the 200GB with XP and installing on it WinXP again I couldn't boot.
Then I used the tuto above to install grub again.
When typing "find /boot/grub/stage1" I got always (hd0,0), so I used this with root and setup commands.

Yesterday I decided to reformat kubuntu disk, because I had nothing to lose.

Still not booting from WinXP disk.
Then I went to bios and changed boot disk to the 85GB one.
There was the grub...
After starting and updating kubuntu a new surprise: The name of the devices had changed to:

/sda1 -> 85GB kubuntu
/sdb1 -> 120GB ext3
/sdc1 -> WinXP
/sdd1 -> 200GB NTFS
/sde1 -> 200GB NTFS

The problem now is that from the grub menu I can't launch WinXP. I get an error about NTLDR not found.
The fdisk output is:

```
Disc /dev/sda: 81.9 GB, 81964302336 octets
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x32043204

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *          63   153468944    76734441   83  Linux
/dev/sda2       153468945   160071659     3301357+   5  Estesa
/dev/sda5       153469008   160071659     3301326   82  Intercanvi Linux / Solar
is

Disc /dev/sdb: 122.9 GB, 122942324736 octets
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7155ded4

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *          63   240107489   120053713+   7  HPFS/NTFS

Disc /dev/sdc: 203.9 GB, 203928109056 octets
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81386421

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdc1   *          63   398283479   199141708+   7  HPFS/NTFS

Disc /dev/sdd: 203.9 GB, 203928109056 octets
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf491d1c3

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdd1              63   398283479   199141708+   7  HPFS/NTFS

Disc /dev/sde: 203.9 GB, 203928109056 octets
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf491d1c4

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sde1   *          63   398283479   199141708+   7  HPFS/NTFS
```

And the menu.lst file is:

```
title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-21-generic
root=UUID=1a0be74f-e7d5-433d-85aa-3c863078a73a ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-21-generic
root=UUID=1a0be74f-e7d5-433d-85aa-3c863078a73a ro single
initrd          /boot/initrd.img-2.6.24-21-generic

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic
root=UUID=1a0be74f-e7d5-433d-85aa-3c863078a73a ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic
root=UUID=1a0be74f-e7d5-433d-85aa-3c863078a73a ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

Can you give some clues about what has happened? I'll appreciate it in case I need to reformat or reinstall something.

Thanks in advance.

---

### Post by Yoke &amp; Chung on 2008-10-22
I had similar problems as you in installing different OS to different hard disks, here is a my crude solution:

1. Unplug all the hard disk cables except the one that you want to install the OS, then load the OS as per normal. 

2. Then swtich to another hard disk, unplug the other cabales and plug only the hard disk you want to install the OS to. Install OS as per normal.

3. Repeat until all OSes are done. 

4. In the BIOs setting, select which hard disk you want to boot from as default.

Now you can boot WinXP as the default and if you want Ubuntu, just hit "ESC" or other key during boot up which will bring up a small menu to select hard disk. 

Very crude I know, but works fine for me so far. In my case it is between Mythbuntu, LinuxMint, and PCLinuxOS. For some strange reasons, I couldn't get tripple/double boot to work when I install the OSes on different hard disks.

---

### Post by caljohnsmith on 2008-10-22
OK, I think I see the problem; there is ambiguity which HDD the Windows XP drive is on start up, because on start up Grub sees the order of drives as the same as the BIOS boot order. That means the drive you set to boot off of will always be (hd0), regardless of what the device.map file says, and then the next drive in the boot order will be (hd1), and so on. When you are running Grub commands in Ubuntu though, that's when (hd0) is sda, (hd1) is sdb, (hd2) is sdc, and so on. 

So bottom line, since we don't know for sure where the XP drive is in the boot order, the easiest way to find out is to simply add all possible combos for booting Win XP in your menu.lst, and then try them on start up. So if you first pull up your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Then at the bottom replace your Windows entries with the following:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title	   Windows XP (hd4)
root       (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
Note that we can omit the (hd2) entry since you all ready tried that. Save the above changes, reboot, and one of those entries should work to boot Windows assuming you don't have any Windows problems. If none of them work, the please let me know exactly what happens on start up when you choose each one. Let me know how it goes. :)

---

### Post by belier on 2008-10-22
Thanks a lot for the answer. I hate having to change boot device via boot menu. I'll try that when I reach home. Say... 3 hours.

---

### Post by caljohnsmith on 2008-10-22
> **belier said:**
> Thanks a lot for the answer. I hate having to change boot device via boot menu. I'll try that when I reach home. Say... 3 hours.
I think you may have misunderstood me; please don't change your BIOS boot order, because if you can boot into Ubuntu OK now, that means you are booting your Ubuntu drive on start up since your Ubuntu entries use (hd0); and that's the most ideal. All you need to do is boot into Ubuntu and add those Windows entries to your menu.lst, reboot, and see which one (hopefully) works. Once you figure out which one works, you can delete the other Windows entries from your menu.lst. :)

---

### Post by belier on 2008-10-22
I think it's you who has misunderstood me... :lolflag:
What I say is that I hate using bios to select boot device, so I'll do everything to have grub working for kubuntu and windows. And for device order I know that I must keep booting from kubuntu drive for not losing the maps on /etc/fstab.

---

### Post by belier on 2008-10-22
Done. It was hd3.
What started like a test has become a definitive installment. It's a great SO. Needs a bit of tweaking but doesn't mind.

Thx a lot to all the posters here.:guitar:

---

