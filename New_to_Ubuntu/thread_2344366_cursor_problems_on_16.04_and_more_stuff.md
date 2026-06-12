---
title: "cursor problems on 16.04 and more stuff"
date: 2016-11-24
forum: New to Ubuntu
---

### Post by lemurpster on 2016-11-24
Hi everybody,
I'm a noob at ubuntu but I have been using it for a while now, maybe 6 months now. I haven't had any major problems until today, when my mouse cursor stopped working. It would sometimes disappear form the screen and sometimes freeze up, but regardless, it was unresponsive when i tried to use the touchpad. 

I saw a suggestion to install gdm and i rebooted with gdm, but my computer didn't even start up with gdm...So now I'm posting this from my Windows part of my dual install, and thank god I have touchscreen on my laptop lol. It really sucks though since I had all of my projects and such on Ubuntu.

Here's the thing though, my cursor doesn't even work on Windows now either, but I'm not sure if it's ubuntu that caused this problem or if my computer just went haywire.

I have an asus zenbook flip ux360ca.

**Update:** My cursor seems to work with my mouse. However, I am unable to boot up ubuntu now because of problems with gdm. See below for more info

**Update 2:** The issue with gdm is fixed now.

---

### Post by Autodave on 2016-11-24
That sounds more like a hardware problem.  One thing you can try: and this is good for any laptop with any problem:

Turn it off, remove the battery, go get a cup of coffee and enjoy  drinking it, put battery back in, power on computer and see if problem  is gone.

---

### Post by mc4man on 2016-11-24
May have the new deal of  using a built-in battery..

---

### Post by lemurpster on 2016-11-24
Haha yeah, the built-in battery is probably the most annoying part.

I realized that it was a hardware issue because the cursor started working when I plugged in my mouse on windows.

However, I still can't seem to get ubuntu started...After I took a suggestion on another thread of switching to gdm from lightdm prior to posting this, Ubuntu doesn't seem to boot up anymore...Like it's stuck on the bootup screen and sometimes I would get a frozen purple/black screen or just stuck on the logo.

---

### Post by lemurpster on 2016-11-24
Earlier I changed from lightdm to gdm because it was a suggested fix for another problem that I had. However, I can't seem to boot up ubuntu after this happened and am stuck on the purple/black screen.

Help would be appreciated!

---

### Post by tea for one on 2016-11-25
> **lemurpster said:**
> stuck on the purple/black screen.

I'm not quite sure where you are with a purple/black screen but nevertheless............

When you start your PC, does grub load OK?

If so, I think that you should try to get to recovery mode:-

Advanced options for Ubuntu
Ubuntu (recovery mode)
Drop to root shell prompt
Press enter for maintenance

```
sudo dpkg-reconfigure lightdm
```

Select lightdm

```
sudo reboot
```

---

### Post by DuckHook on 2016-11-25
Duplicate threads merged.

@lemurpster

You have been advised twice now to stop posting duplicate threads on the same subject because it confuses those trying to help and dilutes community effort. This is the third time and my reply constitutes a formal warning. Further duplicates will not be closed but jailed from public view. Please observe forum etiquette when posting.

---

### Post by lemurpster on 2016-11-25
@DuckHook

Hi, sorry; the first two times were accidents because my browser was being weird :/. I started a new thread because I thought since the topic kind of changed from my cursor problems to something else. Sorry about that!

---

### Post by lemurpster on 2016-11-25
@tea for one

I tried it but i got something along the lines of this: cannot move 'etc/X11 default-display manager' to '/etc/X11 default-display manager.dpkg-temp': read only file system.

On a separate note though...My mouse is moving again on windows YAYY no idea how tho lol

EDIT: nvm it's gone again

---

### Post by tea for one on 2016-11-27
> **lemurpster said:**
> @tea for one

I tried it but i got something along the lines of this: cannot move 'etc/X11 default-display manager' to '/etc/X11 default-display manager.dpkg-temp': read only file system.

On a separate note though...My mouse is moving again on windows YAYY no idea how tho lol

EDIT: nvm it's gone again

You can change the greeter from gdm3 to lightdm with a live cd/usb but your non-functioning cursor would probably prevent you from entering the commands accurately.

First of all, have you backed up your data? - This is vital.

The operating system can be restored but your data can be lost..........

Secondly, in essence, you would need to use chroot from a live cd/usb to access your Ubuntu partition.

Here is some information and points 1 - 7 of Update Failure would be helpful. 

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

You have to know where your Ubuntu is situated (it may **not** be sda1)

Anyway, please report back when your cursor is working and we can take the next step.

---

### Post by lemurpster on 2016-11-27
@tea for one
So I got my cursor to work with my mouse. Unfortunately, not all of my data was backed up...

---

### Post by Geoffrey_Arndt on 2016-11-28
Re the mouse . . . . just get a new one.   (without built in battery - - two double AA's will last for at least a year).    If using the a laptop/notebook, the Logitech m325 works great on all linux distros.

---

### Post by lemurpster on 2016-11-28
@Geoffrey_Arndt

Sorry, probably should've clarified: the cursor works with my mouse but not with the touchpad.

---

### Post by tea for one on 2016-11-28
If your mouse now works, I suggest you back up **all** your data using a live USB/DVD and then we'll try and fix the dilemma of gdm3 and lightdm.

I assume that you still cannot log in to Ubuntu?

---

### Post by lemurpster on 2016-11-28
Unfortunately not. Is there a tutorial somewhere that would help me back up my ubuntu data from my windows partition? Thanks.

---

### Post by tea for one on 2016-11-29
> **lemurpster said:**
> Unfortunately not. Is there a tutorial somewhere that would help me back up my ubuntu data from my windows partition? Thanks.

I do not know if you can back up Ubuntu data from Windows, perhaps you can ask in the Windows forum?

[https://ubuntuforums.org/forumdisplay.php?f=170](https://ubuntuforums.org/forumdisplay.php?f=170)

Is there a reason why you cannot use a live Ubuntu USB/DVD to back up your Ubuntu data?

---

### Post by lemurpster on 2016-11-29
Sorry, that is kind of what I meant, just worded it badly. I had no idea you could access the data from a live cd. Ok, I will do this, thanks

---

### Post by tea for one on 2016-11-30
> **lemurpster said:**
> Sorry, that is kind of what I meant, just worded it badly. I had no idea you could access the data from a live cd. Ok, I will do this, thanks

Splendid - After you have fully backed up your Ubuntu data, we will need to identify where your Ubuntu partition is situated on your PC to fix the lightdm greeter.

Using the live media, open a terminal and enter

```
sudo fdisk -l
```

Please post the results here.

---

### Post by lemurpster on 2016-12-01
Ok, I got it to work and was able to back up my data using a bootable usb. Also another strange thing to note is that my touchpad works on the bootable usb. Maybe I should file a bug report or something about it, since it only froze up in ubuntu when I was using it?

Here is the fdisk stuff:

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1459982336 bytes, 2851528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0AD423AC-02C6-4405-ACC9-444BA6A22D62

Device         Start        End   Sectors   Size Type
/dev/sda1       2048     534527    532480   260M EFI System
/dev/sda2     534528     567295     32768    16M Microsoft reserved
/dev/sda3     567296  217706484 217139189 103.6G Microsoft basic data
/dev/sda4  999192576 1000214527   1021952   499M Windows recovery environment
/dev/sda5  217706496  982626303 764919808 364.8G Linux filesystem
/dev/sda6  982626304  999192575  16566272   7.9G Linux swap

Partition table entries are not in disk order.


Disk /dev/sdb: 3.7 GiB, 3930062848 bytes, 7675904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1e16501d

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 7675903 7673856  3.7G  c W95 FAT32 (LBA)


Disk /dev/sdc: 14.6 GiB, 15664676864 bytes, 30595072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1          32 30595071 30595040 14.6G  c W95 FAT32 (LBA)


```

EDIT: could I just reinstall ubuntu? because that would fix the touchpad problem as well i would imagine.
EDIT2: never mind, I'm fairly sure this is a hardware problem now. The touchpad just stopped working after I turned my laptop upside down...

---

### Post by tea for one on 2016-12-02
> **lemurpster said:**
> Ok, I got it to work and was able to back up my data using a bootable usb. Also another strange thing to note is that my touchpad works on the bootable usb. Maybe I should file a bug report or something about it, since it only froze up in ubuntu when I was using it?

EDIT: could I just reinstall ubuntu? because that would fix the touchpad problem as well i would imagine.
EDIT2: never mind, I'm fairly sure this is a hardware problem now. The touchpad just stopped working after I turned my laptop upside down...

Yes, of course you can reinstall. Reinstallation is a good way to become confident with Ubuntu because you always have a last resort when things go pear-shaped (especially now that you have backed up your personal data)

Anyway, in order to fix the greeter, the fdisk output shows that Ubuntu is on sda5.

However, before you start this process, have you made your **recovery Windows USB** device?

Boot your PC using the live Ubuntu USB/DVD
Open a terminal and copy/paste these commands one at a time and press enter after each line.

```
sudo mount /dev/sda5 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo mount --bind /sys /mnt/sys

```
```
sudo chroot /mnt
```

```
sudo dpkg-reconfigure lightdm
```

Select lightdm

Close the window

Exit from the terminal.

Close the live USB/DVD.

Remove the USB/DVD device

Reboot your PC.

Hopefully the lightdm greeter will appear after the grub screen.

---

### Post by lemurpster on 2016-12-03
Thanks, it started to work again!

Now about the touchpad issue, I'm convinced that it's a software issue now because I got it to work a couple of times on Windows, but overall it doesn't work on either OS. Would you happen to know a good place where I could ask for help about this? Thanks!

---

### Post by tea for one on 2016-12-03
I'm pleased to read that the login greeter is now working as expected. 

If your touchpad misbehaves in both Windows and Ubuntu, I would double check the the instruction manual of your laptop.

You could also contact Asus support or even try to find an Asus forum where there may be suitable information.

Try this "asus touchpad fails after flip" in a search engine.

If you could change the thread title to something like "gdm3/lightdm difficulty" and then mark the thread as solved, that would be useful to other users.

I hope that you can solve your trackpad issue soon (perhaps start a new thread in the Hardware section)


Kind regards

---

### Post by lemurpster on 2016-12-03
Alright, will do, thanks!

---

