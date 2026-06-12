---
title: "Not enough space for root partition"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by Niflheimr on 2014-04-14
Hi everyone, I started yesterday my second adventure with Linux (previously I only had created a live USB to recover some
files from an "orphan" HDD) and tried to install Lubuntu on a (quite) old computer. The notebook on which I installed Lubuntu
is a Toshiba S1410-604 and, having only 256 MB of RAM, I used the alternate image for low-RAM computers. Everything went
fine, I logged the first time in my password-protected account and everything worked, then I rebooted to switch to Windows
XP to get a couple of files. When I switched back to Lubuntu and logged in my password-protected account, nothing loaded
anymore, right click didn't work and there was just the background. I tried to wait but nothing happened, and the CPU and RAM
weren't doing anything (the laptop is old, so it's easy to tell if they are idle or if nothing appears on the screen but it's loading
by the noise). Now, **in synthesis**:

- Lubuntu doesn't load the GUI (only background is loaded) for my main (password-protected) account
- Lubuntu *does* load the GUI for the guest account
- Openbox and console (Ctrl+Alt+F1) work for all accounts
- I tried some solutions found around the Internet, without any luck:
[LIST]
[*][Clearing cache]("http://ubuntuforums.org/showthread.php?t=2187748") (but it was a Xubuntu fix) with cd .cache; rm -rf sessions 
[*][Running updates]("https://answers.launchpad.net/ubuntu/+question/240604") with sudo apt-get update; [...] upgrade; [...] dist-upgrade 
[/LIST]
[INDENT][but this brought up another problem because the console replied with "You don't have enough free space in
var/cache/apt/archives", even though I have (apart from the XP partition) 3 partitions, of which 2 (2.22GB and 280MB, full)
are logical and 1 (5.28GB, with 5.25GB unused) is primary. The clean and autoclean commands didn't do anything (althought
I think they were executed succesfully, because some text showed up when I ran autoclean in the console). I can make more 
room by resizing the partitions if needed.]
[/INDENT]

[LIST]
[*]Some other solutions that didn't work 
[/LIST]

Anyone know how to help me?

---

### Post by bapoumba on 2014-04-19
> You don't have enough free space in var/cache/apt/archives

From a virtual terminal, please run:
```
sudo apt-get autoclean
```
If it does not clear up enough room, please try:
```
sudo apt-get clean
```

You can see how your different partitions are filling up by running:
```
df -h
```

---

### Post by Niflheimr on 2014-05-11
Hi, thank you for your reply and sorry for the late response. I ran **df -h** and it reported me that sda5 (Windows is sda1) is full at
2.1GB/2.2GB, although there's nothing but Lubuntu installed. Running from the console** sudo apt-get autoclean** brings up a quick
check of the packages but nothing really changes, and **sudo apt-get clean** does *nothing at all*, I just get another line open for inputs.

edit: the "main" primary partition (J:) of Lubuntu is 5.28GB, of which only 40MB are used and the rest is free, the "Other" logical partition 
(under J:) is the 2.22GB full one. I don't know how to tell Lubuntu to use those free 5.28GB.

---

### Post by bapoumba on 2014-05-11
So please post the complete output to **df -h** here, thanks.

---

### Post by Niflheimr on 2014-05-11
> **bapoumba said:**
> So please post the complete output to **df -h** here, thanks.

Filesystem_______Size_____Used____Avail___Use%____Mounted on
/dev/sda5_______2.2G_____2.1G____0______100%____ /
none___________4.0K______0______4.0K____0%______ /sys/fs/cgroup
udev___________113M_____4.0K____113M___1%______ /dev
tmpfs___________25M_____964K____24M_____4%_____ /run
none___________5.0M______0______5.0M____0%______ /run/lock
none___________112M______0______112M____0%_____ /run/shm
none___________100M_____4.0K____100M____0%______ /run/user
overflow________1.0M_____4.0K____1020K____1%______ /tmp

---

### Post by bapoumba on 2014-05-11
Your root (/) partition is only 2.2 GB and is full. Unless you can remove some installed packages, I think it really is not enough. Do you have anything in your /home that you could remove ? Even 5GB is not very much..

What does sudo fdisk -l returns ?

You could resize the partitions with a live CD or usb. Prior to doing that, please backup anything you could not afford to loose and defrag windows a couple times.

If you agree to resizing the partitions (shrink the Windows one and extend the Linux one), I'll let others guide you as I have no experience in dealing with Windows :)

---

### Post by Niflheimr on 2014-05-11
> **bapoumba said:**
> Your root (/) partition is only 2.2 GB and is full. Unless you can remove some installed packages, I think it really is not enough. Do you have anything in your /home that you could remove ? Even 5GB is not very much..

What does sudo fdisk -l returns ?

You could resize the partitions with a live CD or usb. Prior to doing that, please backup anything you could not afford to loose and defrag windows a couple times.

If you agree to resizing the partitions (shrink the Windows one and extend the Linux one), I'll let others guide you as I have no experience in dealing with Windows :)
Yes, I could shrink the Windows partition to gain another 10GB (even more, if I decide to remove it altogether) free, but the 
problem is that neither GParted nor EaseUS Partition Manager allow me to resize that logical partition and it's not clear at all
to me how that works (even if I have unallocated space, the maximum size of that partition is still the same and I can't
assign more space to it). There are no installed packages because I just installed the OS with the alternate .iso (which 
shouldn't have much stuff, or less anyway, to begin with) and nothing else. I don't honestly understand why I allocated 5GB
but only 2.2 are available, I think I'm missing something. Anyway, **sudo fdisk -l** gives this:

Disk /dev/sda: 30.0GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27e90be5

Device_______Boot___________Start_____End______Blocks____Id___System
/dev/sda/1_____*______________63____41817194__20908566__b___W95 FAT32
/dev/sda/2______________42283080____53366335__5541628___7___HPFS/NTFS/exFAT
/dev/sda/3______________53366782____58603519__2618369___5___Extended
/dev/sda/5______________53366784____58021887__2327552__83___Linux
/dev/sda/6______________58023936____58603519___289792__82___Linux swap / Solaris

(dev/sda/4 is missing here, it's not a copy error)

---

### Post by bapoumba on 2014-05-11
OK thanks. If you do not mind, I will edit your thread title to attract expert eyes :)

---

### Post by Niflheimr on 2014-05-11
Sure, go ahead! Even if I'm not sure that, after fixing this space problem, the other missing GUI problem will be
fixed too... but, well, I guess I'll just rename it again or open another thread in case. Feel free to edit the title

edit: oh, and thanks again for your help! :)

---

### Post by coffeecat on 2014-05-11
> **Niflheimr said:**
> (dev/sda/4 is missing here, it's not a copy error)

It's the way mbr partition tables work. You are allowed up to four primary partitions, which are always numbered 1 to 4. An extended partition, which is a special type of primary, acts only as a container for logical partitions and you may have only one extended. Logical partitions are always numbered 5 and upwards. Your extended partition is sda3. You have used only 3 of your allowed primary/extended partitions. Hence the "missing" sda4.

I might be able to help you with resizing your sda5, but please do something first. In your attempt to get the formatting of your fdisk output right, you have made it hard to read. There's an easier way - the use of BBCode code tags. This is what you do:

[noparse]```
your terminal output
```[/noparse]

Appears as:

```
your terminal output
```

And it preserves formatting. It's best to use the advanced editor when using BBCode and if necessary click on the icon that looks like A/A to switch editor to source mode. If you use WYSIWYG editor with BBCode you can get in a muddle because WYSIWYG obscure the code tags. 

So - please post the output of "sudo fdisk -l" again but this time inside code tags. Also, the output of this as well:

```
sudo parted -l
```

Again between code tags please.

---

### Post by bapoumba on 2014-05-11
Thanks coffeecat :)
Thread title edited.

---

### Post by Niflheimr on 2014-05-12
> **coffeecat said:**
> I might be able to help you with resizing your sda5, but please do something first. In your attempt to get the formatting of your fdisk output right, you have made it hard to read. 

So - please post the output of "sudo fdisk -l" again but this time inside code tags. Also, the output of this as well:

```
sudo parted -l
```

Again between code tags please.
Well ok, it almost sounds like a trial to get access to temple but here it is: :)

**sudo fdisk -l**
```
Disk /dev/sda: 30.0GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27e90be5

Device        Boot          Start          End       Blocks    Id     System
/dev/sda/1     *               63     41817194     20908566     b     W95 FAT32
/dev/sda/2               42283080     53366335      5541628     7     HPFS/NTFS/exFAT
/dev/sda/3               53366782     58603519      2618369     5     Extended
/dev/sda/5               53366784     58021887      2327552    83     Linux
/dev/sda/6               58023936     58603519       289792    82     Linux swap / Solaris
```

**sudo parted -l**
```
Model: ATA TOSHIBA MK3018GA (scsi)
Disk dev/dsa 30.0GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number   Start     End      Size     Type      File system      Flags
1        32.2kB    21.4GB   21.4GB   primary   fat32            boot
2        21.6GB    27.3GB   5675MB   primary   ntfs
3        27.3GB    30.0GB   2681MB   extended
5        27.3GB    29.7GB   2383MB   logical   ext4
6        29.7GB    30.0GB   297MB    logical   linux-swap(v1)

Error: /dev/zram0: unrecognised disk label
```

Thanks for the explanation and the info :) Actually, is there a way to select and copy lines from the terminal?
I've been rewriting them until now, but there probably is a more efficient method.

---

### Post by coffeecat on 2014-05-12
> **Niflheimr said:**
> Actually, is there a way to select and copy lines from the terminal?

Highlight what you want to copy with the mouse, right-click -> copy.

By the way, it's /dev/sda1, not /dev/sda/1. (Ditto the rest of the partitions).

I was going to give you detailed instructions on how to enlarge your sda5 Lubuntu root partition, but now I see the details of your two Windows partitions, I'll just give you the basics. I really doubt whether it is feasible to gain an extra 10GB by shrinking one of the Windows partitions. I can't remember how much space XP needs but you must be near the minimum already. Also, your fat32 sda1 is 21 GB and the ntfs sda2 only 5.5GB. I'll have to take a guess at sda1 being your XP C: partition (it's unusual to run XP on fat32 but possible) and sda2 being a data partition. If you are intending to shrink the sda1 partition, you can do so with Gparted, but then you would have to move the sda2 partition to the left. Moving the partition could take a long time - perhaps an hour or more.

Also - a cautionary note. In order to resize the sda5 Lubuntu root partition, you will have to disable swap (see below). This will mean that the system will have to rely on your meagre 256 RAM with no swap capability. This is potentially hazardous. If the system runs out of memory during a partition resize, it will crash or freeze with resultant filesystem damage - probably irretrievable. Any partition work includes the possibility of this happening anyway, so I always suggest backing up everything of importance and being aware of this potential. In your situation it is much more likely. In the circumstances, I suggest you have a think about your best course of action. Since XP is no longer supported, one option would be to back up any important data, and simply re-install Lubuntu so that it replaces everything, using the whole hard drive.

But if you do want to attempt to resize sda5, this is what you do. Assuming you have created some unallocated space to the left (that is before) your sda3 extended partition, you have to do this from a live CD or USB of Lubuntu. You cannot do this from within your installed Lubuntu.

[list=1][*]Open Gparted from the live session.
[*]Highlight the sda6 swap partition, right-click and choose "swapoff". You cannot resize sda3 and sda5 until you do this.
[*]Resize/enlarge sda3 to the left, to include whatever unallocated space you have created by shrinking the Windows partition(s). You cannot resize sda5 until you have done this.
[*]Resize sda5 to the left, to include the unallocated space that is now within sda3. This will take a long time. This is the operation that is most likely to fail.[/list]

I haven't given you all the details of which menu to use in Gparted for which operation, because Gparted is fairly straightforward anyway, and I wanted to give you the basics since you would be advised to think about what I have said above before you decide whether or not to proceed.

---

### Post by Niflheimr on 2014-05-12
> **coffeecat said:**
> Highlight what you want to copy with the mouse, right-click -> copy.
The terminal is not graphical, I use Ctrl+Alt+F1 and only have the command-line interface, mouse doesn't even work there IIRC.

> **coffeecat said:**
> By the way, it's /dev/sda1, not /dev/sda/1. (Ditto the rest of the partitions).
Oh yeah, sorry about that. Thanks.

> **coffeecat said:**
> I was going to give you [...]
Well, Windows still has around 7GB free and I'm sure I could delete some stuff too to gain another 3GB. But yeah, it surely
wouldn't work properly after that with little space left (I wouldn't expect it to do, it was just to leave the files there). To 
delete the whole Windows partition I'll have to ask the owner, but I mainly didn't want to do it because I haven't really 
properly tried Lubuntu and wanted to know if it suited me before formatting. I guess it'll be a leap of faith :) Trying to 
keep the Windows partition seems to be too much hassle for too low gain. The trick would be to set the swap partition
to swapoff then, at least now I know it, thanks :) I'll see if I can delete Windows and post here again if I still have problems.

Thanks for your time :wink:

---

### Post by sudodus on 2014-05-12
If you run the command

```
( sudo parted -l )> output.txt
```

the output will be in the file **output.txt** and it can be copied to a computer with a graphical interface, which should be easier than to type everything manually.

---

### Post by coffeecat on 2014-05-12
> **Niflheimr said:**
> The terminal is not graphical, I use Ctrl+Alt+F1 and only have the command-line interface, mouse doesn't even work there IIRC.

I see. Sorry about that. Anyway, sudodus has given you a way of saving terminal output to a file if you ever need to do it again.

> **Niflheimr said:**
> I'll see if I can delete Windows and post here again if I still have problems.

If you do decide to overwrite everything with a new Lubuntu installation, there's a simpler and quicker way. In the Lubuntu installer, there's a choice "use whole hard drive" or words to that effect. If you choose that, it simply removes all the pre-existing partitions and sets you up with a 2 partition layout for Lubuntu using the whole hard drive.

Good luck!

---

