---
title: "Hardware Enablement Stack update crashed computer"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by dipper2 on 2014-07-17
Hi everybody. I'm new here and new to Ubuntu so please assume I know almost nothing.

I'm running Ubuntu 12.04.4 LTS (GNU/Linux 3.13.0-32-generic x86_64). I installed a few upgrades this morning then saw the HWE upgrade which I installed. At the end I got a message to say that my BOOT sector was nearly full. I was going to restart the computer and then try to sort that out. Mrs Dipper still had programs running so I logged into her account, closed the programs and logged off. Rather than return to my account I got a black screen with a flashing cursor.

After waiting for a while I turned the computer off with the power button and restarted it. The Ubuntu screen came up with a message saying *'The system is running in low-graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.*'

I then get an option screen for 1: run in low graphics mode 2: reconfigure graphics 3: troubleshoot error or 4: exit to console login.

Option 1 gave a message to stand by for one minute whilst the display restarts but nothing happened. When I pressed return I was taken to the Terminal screen (I think).
Option 2 asked me how I would like to reconfigure the display (default or backed-up) but selecting either just returned me to the same message.
Option 3 gave me 4 choices but any of those would be beyond my limited skills
Option 4 I didn't understand!

I can log in from the screen that comes up in option 1 and I get *'Welcome to Ubuntu etc' *and *'Your Hardware Enablement Stack (HME) is supported until April 2007'*.

Any help for this complete novice will be greatly appreciated before Mrs Dipper kills me for losing her photos. :(

Many thanks in advance.

---

### Post by grahammechanical on 2014-07-17
My experience regarding low graphics mode or failsafeX mode is that it is broken. It does not do anything on my system. What can you do in this situation?

1) at the Grub menu select Advanced Options for Ubuntu or Recovery Mode, whichever appears in your Grub boot menu. Recovery mode will give these options

1) resume ====== resume normal boot. It boots without using a proprietary video driver.
2) clean ======== try to make free space. That may sort out the problem with the boot sector being nearly full.
3) dpkg ========= repair broken packages. That speaks for itself.
4) failsafeX ====== run in failsafe graphic mode. Broken if you ask me.
5) fsck ========= check all file systems. Again, it speaks for itself.
6) grub ========= update grub boot loader. It runs the update-grub script
7) network ======= enable networking. Makes a connection to the router and hence to the internet. This is necessary if we are going to use recovery mode to update the system or install applications.
8) root ========== drop to a root shell prompt. Lets us run the usual terminal commands. To return to the recovery menu type exit. Some of those actions also put the file system in read/write mode which is needed if we are going to use Root to make changes to the file system.

My suggestion is: a) run clean; b) run network; c) run root and run these commands

```
apt-get update
apt-get upgrade
exit
```

d) run resume. If that gets you to a desktop try changing video drivers using Additional Drivers. You will be in a fall back video mode so it will need a reboot to get a user experience that you are familiar with.

Keep in mind also that the Grub menu gives us access to previous Linux kernels. Sometimes running one of them gets us to a desktop.

If any of this works, make a note of it and then you can give advice to others. And it seems that there will be others getting that upgrade message and hitting this problem.

Regards.

---

### Post by dipper2 on 2014-07-17
Thanks Graham. Trying that now.

---

### Post by dipper2 on 2014-07-17
OK. Ran clean and accepted the recommended items to remove. A few error messages seemed to scroll across the screen but too fast to see what they were. Anyway, it reached the end and I returned to the menu.

Ran network and it loaded all sorts of plugins. The last process was 16423 followed by 7 plugins. Now there is a flashing cursor at the bottom and no instructions to press enter to return to the menu.

---

### Post by plucky on 2014-07-17
What is your video card?

I have a old Nvidia card on my test system and I found the HWE would not allow the Nvidia-173 driver to install.

I had to get it to load the Nouveau driver. 

To remove Nvidia driver I used ```
sudo apt-get remove nvidia*
``` and then rebooted.
I also had to select 2D mode at the login screen.

On my main system I will wait until the 14.04.1 upgrade is offered.

Good Luck

---

### Post by dipper2 on 2014-07-17
Thanks for the input Plucky. I don't know what my card is. It's a new HP computer preloaded with Ubuntu so I didn't have to do anything myself - that seemed the safest option considering my computer skills.

I'm still stuck on the network screen with the flashing cursor. Return and exit don't do anything. Should I just switch off at the power switch and start it up again?

---

### Post by grahammechanical on 2014-07-17
@dipper2

I am having the same problem with Recovery>Network and I should not be getting it. I am using a fully functional Utopic Unicorn updated this morning with the newest kernel. And when I try Recovery>Network the script does not complete. The message is

> could not find support for '/sys/device/pci ... blah, blah ... not supported by any plugin

I do not approve of bad mouthing developers but they sure messed up this time.

To get out of that broken Network action we do a hard power off. It is the only way that I could find. Now we need the file system in read/write mode and a simple way to do it and we need a network connection because I am hoping that an update/upgrade might bring in some fix. So,

at the recovery menu run 

1) dpkg. That will put the file system into read/write mode
2) root. That will give us a root prompt. Now we can run

```
ifup -a
apt-get update
apt-get upgrade
exit
```

That should let us update/upgrade the system which might fix things. Before Exiting root we could also try dpkg again. Just for luck.
```
 /lib/recovery-mode/options/dpkg
```

and you might try the suggested

```
apt-get remove nvidia*
```

provided that you have an Nvidia card. sudo is not needed at the root prompt. I do not know what the command is for AMD/Ati cards. All this can be done from recovery root but we do need a network connection to update.

Resume may get us to a desktop.

Edit: to find out what video card you have run

```
ubuntu-drivers devices
```

Regards.

---

### Post by dipper2 on 2014-07-17
No change I'm afraid Graham. I got lots of error messages scrolling past. It also wouldn't accept the sudo-apt remove NVidia* command. Still giving the low graphics warning.

There is a factory reset option. Is that worth doing or will I lose all my data?

---

### Post by dipper2 on 2014-07-17
@grahammechanic I don't know whether it is significant, but my computer never managed to install linux-image-3.5.0-49-generic and linux-image-3.5.0-51-generic.

---

### Post by kansasnoob on 2014-07-17
Can you possibly boot an older kernel if you choose advanced options from the grub menu?

---

### Post by dipper2 on 2014-07-17
> **kansasnoob said:**
> Can you possibly boot an older kernel if you choose advanced options from the grub menu?

@kansasnoob Thanks for that suggestion. I seem to have Linux 3.5.0-49-generic and 51 and 52. Do you think any of those would work OK? Could I get back to the current version if it didn't?

---

### Post by dipper2 on 2014-07-17
Tried earlier versions. Just ended up with a black screen with a static cursor top left each time.

---

### Post by kansasnoob on 2014-07-17
Do you have a live DVD or live USB that you can use for troubleshooting?

---

### Post by dipper2 on 2014-07-18
> **kansasnoob said:**
> Do you have a live DVD or live USB that you can use for troubleshooting?

No. The computer came pre-loaded but didn't have a DVD or USB with it.

---

### Post by kansasnoob on 2014-07-18
> **dipper2 said:**
> No. The computer came pre-loaded but didn't have a DVD or USB with it.

I thought that may be the case, do you have access to another computer so you can create a live DVD or live USB?

---

### Post by dipper2 on 2014-07-18
Thanks for the prompt response.

I have a Windows laptop. I'll need instructions though. Will using a live DVD delete all my photos and emails?

My computer does have the option to restore to factory state. Will that delete everything as well?

---

### Post by kansasnoob on 2014-07-18
> My computer does have the option to restore to factory state. Will that delete everything as well? 

No idea, is that a pure Ubuntu puter or a dual boot with Windows? Regardless you'd have to ask the manufacturer about that.

Just running a live DVD or live USB from the live desktop will not delete anything, but reinstalling certainly would.

But I found a link where they describe how to clean /boot and free up some space:

[http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition](http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition)

Look at the command line option in the first answer.

What you'd have to do is boot into recovery mode, select enable networking, then select root shell, and remove the oldest kernel. Then since the new kernel did not fully install try:

```
apt-get update
```

```
apt-get dist-upgrade
```

This command may provide some info:

```
apt-get -f install
```

It may tell you something I can't really anticipate.

But a live DVD or live USB can be very useful for performing many tasks, including backing up data off a crashed install.

I was actually thinking of using it with a chroot:

[http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html](http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html)

But we'd begin by just collecting info like figuring out the partition layout, what graphics chip you have, etc.

There are simple instructions about downloading, verifying the download, and creating live media here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Just scroll down to the "Easy ways to switch to Ubuntu 14.04 LTS" and "From Windows". But don't try reinstalling or anything that radical until we've tried everything else.

---

### Post by dipper2 on 2014-07-18
Thanks for taking the time with that comprehensive reply. I'll give that a go.

---

### Post by kansasnoob on 2014-07-18
> **dipper2 said:**
> Thanks for taking the time with that comprehensive reply. I'll give that a go.

It's all good clean fun for us :lolflag:

Just take things one step at a time, be cautious, if you're confused just stop and ask more questions, and please be a little patient. I'm guessing you have a newer PC with Secure Boot and/or UEFI BIOS which I think requires a separate /boot partition and I'm guessing that the manufacturer provided much too small of a /boot. So we'll want to find out some stuff to not only fix the current problem but also to lessen the chance of future problems.

If you are creating a live DVD/USB once you've done so please take time to boot it, display the advanced boot options, and select Check disc for defects before using it for anything:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

That way you'll know you're working with good media ;)

---

### Post by dipper2 on 2014-07-18
Thanks Kansasnoob. I'm burning a live DVD of 14.04 LTS now.

I tried deleting an old kernel but it wouldn't do it. My neighbour is a software engineer and he's coming round later to help. I'll show him your instructions and he may be able to troubleshoot where I'm going wrong. If we are successful, I'll post back here in case it is helpful for others.

The computer is only a couple of months old so there is not a lot of new stuff on it to lose. Interestingly, HP seem to have discontinued it now which is a shame.

---

### Post by kansasnoob on 2014-07-18
The newest hardware I have is about 3 years old so I'm still a dummy when it comes to UEFI and Secure Boot, but I'd love to know more about that specific computer.

---

### Post by dipper2 on 2014-07-18
Unfortunately, none of those commands worked. My neighbour has managed to delete the oldest kernel and freed up some space in root but now we've run out of time. He has also found all our photos and documents but not yet worked out how to copy them to an external drive. Emails may be more of a problem.

> **kansasnoob said:**
> The newest hardware I have is about 3 years old so I'm still a dummy when it comes to UEFI and Secure Boot, but I'd love to know more about that specific computer.

I'll try and find details of the computer and post them here. I can't do any more until Sunday at the earliest but I think we might be getting somewhere. Thanks again.

---

### Post by kansasnoob on 2014-07-18
> **dipper2 said:**
> Unfortunately, none of those commands worked. My neighbour has managed to delete the oldest kernel and freed up some space in root but now we've run out of time. He has also found all our photos and documents but not yet worked out how to copy them to an external drive. Emails may be more of a problem.



I'll try and find details of the computer and post them here. I can't do any more until Sunday at the earliest but I think we might be getting somewhere. Thanks again.

Let us know what email app you use and we should be able to tell you where to find the existing profile.

---

### Post by dipper2 on 2014-07-19
I'm not doing very well. :(

I've copied the Ubuntu 14.04 disc image file but I can't extract the files. My Windows 7 laptop doesn't give me any option other than copying the file again. There isn't the 'Write to disc' option shown in your link.

I'm using Thunderbird for emails.
[B][I]
Edit: I've found instructions for Windows. I now have files and folders for 14.04.[/I][/B]

---

### Post by kansasnoob on 2014-07-19
> **dipper2 said:**
> I'm not doing very well. :(

I've copied the Ubuntu 14.04 disc image file but I can't extract the files. My Windows 7 laptop doesn't give me any option other than copying the file again. There isn't the 'Write to disc' option shown in your link.

I'm using Thunderbird for emails.
[B][I]
Edit: I've found instructions for Windows. I now have files and folders for 14.04.[/I][/B]

Just copying the Ubuntu iso files and folders won't create a bootable live DVD. If your Win 7 doesn't offer “Burn disc image” you may need to use Infra Recorder, just scroll down here to where it says ***2000/ XP / Vista / 7: Infra Recorder***:

[https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows](https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Windows)

But you should check the md5sum first:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

And remember to access the advanced boot options and run Check disc for defects:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Since you'll likely be accessing those files/folders with the 14.04 live DVD it'll look something like this; Locate and open the Home folder then you'll see folders for each user. You'll need to backup the files and folders for each user individually so click on a user, then when that window opens click on the ^:

[ATTACH=CONFIG]254841[/ATTACH]

That will let you click on Show Hidden Files:

[ATTACH=CONFIG]254842[/ATTACH]

Then you'll see what I call "hidden dots":

[ATTACH=CONFIG]254843[/ATTACH]

.thunderbird is Thunderbird and .mozilla is Firefox

If that's even remotely unclear ask for clarification.

I do still hold out some hope that we can still save that install though if you're game :)

---

### Post by dipper2 on 2014-07-19
I'm away tonight so can't check the computer.

I'm pretty confident I have created the live DVD properly using the 'burn disc image' command. The DVD even started trying to load Ubuntu on the laptop. I verified it at the same time as I burnt it.

I don't understand the md5sum business.

I'll check the disc for errors when I get home.

How do I start to access the files/folders using the live DVD? Do I just insert the DVD into the drive?

I'm happy to keep trying. I treat it as a challenge. :)

---

### Post by kansasnoob on 2014-07-19
> **dipper2 said:**
> I'm away tonight so can't check the computer.

I'm pretty confident I have created the live DVD properly using the 'burn disc image' command. The DVD even started trying to load Ubuntu on the laptop. I verified it at the same time as I burnt it.

I don't understand the md5sum business.

I'll check the disc for errors when I get home.

How do I start to access the files/folders using the live DVD? Do I just insert the DVD into the drive?

I'm happy to keep trying. I treat it as a challenge. :)

If running Check disc for defects passes there is no need to worry about the md5sum. When you see [this screen]("http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png?cache=") you have a whopping 3 seconds to press a key to display the boot options. I always just press Enter. Then select your desired language. It takes several minutes for that test to complete but I can't think of many things more irritating than wasting time trying to use a faulty live disc.

If you boot the live DVD and choose to Try Ubuntu without installing you should be able to access your files from the live session. I never did ask what desktop environment you're running, is it Unity? You can browse through this tour:

[http://www.ubuntu.com/desktop/take-the-tour](http://www.ubuntu.com/desktop/take-the-tour)

Is that fairly familiar?

No doubt 14.04 is a little different than 12.04 but the same principles apply. I personally use either Ubuntu GNOME or Ubuntu with the [flashback session]("http://ubuntuforums.org/showthread.php?t=2220264"), mostly because Unity is just too resource hungry for my oldish weak hardware.

I'll try to type up some stuff so we can try to rescue that before we throw in the towel ................ but it may be about 12 hours.

---

### Post by dipper2 on 2014-07-20
The desktop is Unity.

Does it matter that I will be using a 14.04 live disc with 12.04?

One thing that may be significant is that the 'Network enabling' doesn't seem to run its course and hangs after loading quite a few items. I have to power off and on again to get back in.

Then when I try update it can't find the urls, presumably because it can't connect to the internet.

---

### Post by kansasnoob on 2014-07-20
So the network issues are (were) with 12.04? I assume so since you mention updating.

If you were having trouble with networking on 12.04 it might well be worth just biting the bullet and giving 14.04 a go.

There is also the fact that 12.04 is supported until April 2017 whereas 14.04 is supported until April 2019.

There are some changes to Unity that I've seen some users praise while others have cursed the changes, I can't personally comment since I don't use Unity.

If that new DVD works OK I'd like you to post the full output of two commands:

```
sudo parted -l
```

```
sudo blkid
```

That may give me enough info to know how HP laid out the partitions on that PC.

---

### Post by kansasnoob on 2014-07-20
Forgot to answer this:

> Does it matter that I will be using a 14.04 live disc with 12.04?

No, but I've made the assumption that the OS is 64bit. If you were to boot into recovery mode again, enable networking, then in root shell run:

```
uname -m
```

That would tell us if the OS is 32 bit or 64 bit. (64 bit users would see x86_64, 32 bit users would see i686)

---

### Post by dipper2 on 2014-07-20
OK. Making progress.

Using the laptop to check the disc - pressing enter at the right time didn't work. I put the disc into the Ubuntu computer and although I didn't get that screen, another list of options including check disc came up and the disc checked OK.

I have managed to copy my files and Mrs Dipper's files to an external hard drive but not Firefox settings or emails and addresses in Thunderbird as I don't have 'permission'.

> Sudo parted -1

Model ATA WDC WD10EZEX-60Z (scsi)
Disk /dev/sda: 1000GB
Sector size logical/physical): 512B/4096B
Partition table: msdos

Number Start        End          Size       Type        File System      Flags
1           1049kB    211MB     210MB    primary   fat32
2           211MB     4505MB   4294MB  primary    ntfs                  boot
3           4506MB998GB     994GB    extended                         lba
5            4507MB   953GB     949GB    logical      ext4
6           953GB      994GB     41.0GB   logical      ext4
7           994GB      998GB     4095MB  logical      Linux-swap(v1)
4           998GB      1000GB   1999MB  primary    fat32                lba


Warning: Unable topen /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read only.
Error: Can't have a partition outside the disk!

I had to type this out manually so there may be errors. Answer to your next request follows. (Sorry - I tried to line up the columns but it hasn't shown up here)

---

### Post by dipper2 on 2014-07-20
> sudo blkid

/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="BOOT" UUID="E4AF-209C" TYPE="vfat"
/dev/sda2: LABEL="HP_RECOVERY" UUID="FC4EB0344EAFE61C" TYPE="ntfs"
/dev/sda4: LABEL="HP_TOOLS" UUID="7F3C-E055" TYPE="vfat"
/dev/sda5: LABEL="HOME" UUID="92f12a54-8291-48cf-a7e3-d9bd155ffa94" TYPE="ext4"
/dev/sda6: LABEL="ROOT" UUID="6c594ed4-072c-473b-88d1-e6de2128fd5d" TYPE="ext4"
/dev/sda7: LABEL="SWAP" UUID="003431f9-acea-4a95-baee-ba0721b5f9d6" TYPE="swap"
/dev/sr0: LABEL="Ubuntu14.04 LTS amd64" TYPE="9660"

> uname -m
x86_64

Again, typed out manually so there may be errors. The demo 14.04 disc is running.

---

### Post by kansasnoob on 2014-07-20
Why can't you just copy-n-paste the text?

I mean it doesn't really matter to me but that's a lot of work for you ;)

---

### Post by dipper2 on 2014-07-20
The text is on the Ubuntu computer and I am writing this on my Windows 7 laptop.

---

### Post by kansasnoob on 2014-07-20
> **dipper2 said:**
> The text is on the Ubuntu computer and I am writing this on my Windows 7 laptop.

Wouldn't it be easier to just open Firefox in the live session, login here at the forums, and reply directly from the broken PC using the live session? Or is it not connecting to the internet?

Anyway I can see that does have a separate /boot, which is /dev/sda1. If you open Gparted in the live session the graphic should show how much free space is available.

I performed a test installation of Ubuntu 12.04.2 which should coincide with your currently broken OS but I need time to check something. It could take me several hours to get back to you because I'll be away from the desk for a while.

It seems odd that you can't just copy the .thunderbird and .mozilla profiles ................ that will require some thought and experimentation on my end.

Oh, before we even think about reinstalling, I must ask - is that still under warranty? If so I don't think we should install 14.04.

I still hold out hope that we can fix it without too much trouble, it's always harder to explain what to do than it is to just do it :)

I almost wonder if it would be safe to just resize your partitions using Gparted???? I don't know though so don't try it until we do know! They did make an awfully small /boot partition - only 210MB - which is maybe large enough for 3 or 4 kernel updates before things go kablooey - like they just did!

---

### Post by dipper2 on 2014-07-20
> **kansasnoob said:**
> Wouldn't it be easier to just open Firefox in the live session, login here at the forums, and reply directly from the broken PC using the live session? Or is it not connecting to the internet?

I didn't think of that. This is the absolute beginners forum after all and I wouldn't want to disappoint. :)

Here we go again from the broken computer:

sudo parted -l

Model: ATA WDC WD10EZEX-60Z (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  211MB   210MB   primary   fat32
 2      211MB   4505MB  4294MB  primary   ntfs            boot
 3      4506MB  998GB   994GB   extended                  lba
 5      4507MB  953GB   949GB   logical   ext4
 6      953GB   994GB   41.0GB  logical   ext4
 7      994GB   998GB   4095MB  logical   linux-swap(v1)
 4      998GB   1000GB  1999MB  primary   fat32           lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

sudo blkid

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="BOOT" UUID="E4AF-209C" TYPE="vfat" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="FC4EB0344EAFE61C" TYPE="ntfs" 
/dev/sda4: LABEL="HP_TOOLS" UUID="7F3C-E055" TYPE="vfat" 
/dev/sda5: LABEL="HOME" UUID="92f12a54-8291-48cf-a7e3-d9bd155ffa94" TYPE="ext4" 
/dev/sda6: LABEL="ROOT" UUID="6c594ed4-072c-473b-88d1-e6de2128fd5d" TYPE="ext4" 
/dev/sda7: LABEL="SWAP" UUID="003431f9-acea-4a95-baee-ba0721b5f9d6" TYPE="swap" 
/dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660" 

My neighbour removed the oldest kernel and got the BOOT down to 136MB if I remember correctly. There are still some other kernels that could be removed to make even more space. Even I recognised that just over 200MB seemed rather mean.

The computer is still under warranty (I think) but I would have upgraded to 14.04 in early August anyway. HP have discontinued it now so I'm quite happy to experiment and I am learning all the time which is fun in itself. I don't think any of the hardware is malfunctioning.

---

### Post by kansasnoob on 2014-07-21
That's a lot easier than all that typing, eh?

One more hint, no need to redo any of those postings, but it may come in handy in the future - if you click on the **#** icon at the top of these forum reply boxes it will display code tags with a blinking cursor in between, so if you copy some text from a terminal output - then click on the # icon - then position the mouse pointer over the blinking cursor and select paste it would post like this ***example***:

```
lance@lance-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  105GB  105GB   primary   ext4            boot
 2      105GB   210GB  105GB   primary   ext4
 3      210GB   232GB  21.8GB  primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   374GB  20.0GB  logical   ext4
13      374GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.1GB  logical   ext4
15      415GB   435GB  20.1GB  logical   ext4
16      435GB   455GB  20.4GB  logical   ext4
17      455GB   476GB  20.4GB  logical   ext4
18      476GB   498GB  21.9GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


lance@lance-desktop:~$ sudo blkid
/dev/sda1: LABEL="Trusty sda1" UUID="3b8734f7-6f22-4f5f-a7ce-7cdb714c7404" TYPE="ext4" 
/dev/sda2: LABEL="Precise sda2" UUID="c1dc4187-4170-406f-8b8e-c1a3904e1315" TYPE="ext4" 
/dev/sda5: UUID="80627269-1ccd-4774-b4ea-a5ef8824ffaa" TYPE="swap" 
/dev/sda6: LABEL="Edubuntu SS i386" UUID="0997e4c2-c015-4da1-96d7-ce933d07f3be" TYPE="ext4" 
/dev/sda14: LABEL="12.04.2 amd64" UUID="19498718-187c-4434-8014-d970771be3c4" TYPE="ext4" 
/dev/sda15: UUID="4ff15f30-a834-4706-a865-a863dbf4f3f1" TYPE="ext4" 
/dev/sda16: UUID="35cae7e4-93b7-451c-bbb2-da100bf6800d" TYPE="ext4" 
/dev/sda17: LABEL="sda17" UUID="e32a70b1-c79e-4cf3-ae2c-33c0d111b4d9" TYPE="ext4" 
/dev/sda18: LABEL="sda18" UUID="943fc60c-4910-4151-8ccc-b77f41bd16f8" TYPE="ext4" 
/dev/sda3: LABEL="Lubuntu SS ->" UUID="cecea214-9cb0-4940-97ca-54361f8e293f" TYPE="ext4" 
/dev/sda7: LABEL="Edubuntu PP ->" UUID="87f3829e-47d0-4b76-ad45-a2a7d9f275a9" TYPE="ext4" 
/dev/sda8: LABEL="12.04.2 ->" UUID="c9eca1e8-74f1-4bc0-b885-722cf2945c40" TYPE="ext4" 
/dev/sda9: LABEL="12.04.3 ->" UUID="4819e518-0cf2-4414-9537-8a073a1ec562" TYPE="ext4" 
/dev/sda10: LABEL="12.04.4 ->" UUID="8313d9dd-21b5-43e1-a036-a3d4c554af98" TYPE="ext4" 
/dev/sda11: LABEL="UGR SS i386 ->" UUID="4ae12232-62de-4ff0-8858-d99b96ece85c" TYPE="ext4" 
/dev/sda12: LABEL="UGR SS amd64 ->" UUID="227a7a6f-b98c-405d-b0e9-d65e885ce891" TYPE="ext4" 
/dev/sda13: LABEL="12.04.5 ->" UUID="a1549d21-88ff-4a9e-8f1b-490648b0abb9" TYPE="ext4" 

```

Now I'll try to pull some notes together and post what I think may work.

---

### Post by kansasnoob on 2014-07-21
Just FYI the reason things are taking so long is due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264)

Canonical really dropped the ball on this play :mad:

The only way I can make a recommendation is by trying things myself, so that means blowing things up and starting over a few times.

---

### Post by kansasnoob on 2014-07-21
Oh, did you happen to look in the Gparted graphic using the live session to see how much free space you have in that small /boot partition?

---

### Post by kansasnoob on 2014-07-21
OK, where I'm at right now;

I can verify that the amd64 command shown here works for 64 bit (which is what you have):

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264/comments/3](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264/comments/3)

Of course that would be a lot of typing and must be 100% correct to work, but if you wanted to you could boot into recovery mode again, enable networking, then open root shell. Then I think the following command will display the free space in /boot since it's a separate partition:

```
df -H
```

Or maybe you already checked the free space using Gparted?

But if you have enough free space in /boot that command may get you working if you're willing to do that much typing :redface:

I'm scratching my head a bit about using a chroot with a separate /home. That's kind of stupid on my part but I stopped using a separate /home clear back in about 2010 and I don't like to post inaccurate info - so I need to play a bit.

I'll be playing anyway because 14.04.1 iso testing begins later today so I'll try a test build with separate /boot, /root/, and /home partitions just to see if my chroot scripting works or not.

Sorry this is taking so long .................... oh - one thing I haven't bothered with yet;

We should know what graphics chip you're using (just in case) so if you would please boot to a live session agin using the 14.04 DVD and post the output of:

```
lspci | grep VGA
```

---

### Post by dipper2 on 2014-07-21
Thanks for the hint about posting code and the link to the bug.

> **kansasnoob said:**
> Oh, did you happen to look in the Gparted graphic using the live session to see how much free space you have in that small /boot partition?

sda1 is Size 200.00Mib, Used 140.06 MiB and Unused 59.94 MiB.

> **kansasnoob said:**
> I can verify that the amd64 command shown here works for 64 bit (which is what you have):

I tried the amd64 command (without the live disc in the drive) and got:

```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened
```

Again I don't think enable networking worked properly. After running that I have to power off and on again to get back in.

---

### Post by dipper2 on 2014-07-21
> **kansasnoob said:**
> Sorry this is taking so long .................... oh - one thing I haven't bothered with yet;

We should know what graphics chip you're using (just in case) so if you would please boot to a live session agin using the 14.04 DVD and post the output of:

```
lspci | grep VGA
```

I got this:

```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8240]

```

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> Thanks for the hint about posting code and the link to the bug.



sda1 is Size 200.00Mib, Used 140.06 MiB and Unused 59.94 MiB.



I tried the amd64 command (without the live disc in the drive) and got:

```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened
```

Again I don't think enable networking worked properly. After running that I have to power off and on again to get back in.

I think that will be sufficient space. It looks like the devs intentionally disabled read/write in recovery for a reason:

[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/575469](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/575469)

How far do you get in the boot process if you just let that borked OS boot normally? By normally I mean without selecting recovery or an older kernel.

I ask because you might be able to enter a TTY (terminal) once you reach a frozen state by pressing Ctrl +  Alt + F1. Then you could type that command. Using a TTY can seem tricky - you'll be asked to login using the root users name and password.

BTW when done using a TTY or terminal in recovery mode, rather than doing a hard reset type reboot (or sudo reboot) to restart, or sudo halt -p to shutdown. That's much easier on hardware than a hard reboot or power-off - more here:

[http://askubuntu.com/questions/192527/problem-with-sudo-halt-command](http://askubuntu.com/questions/192527/problem-with-sudo-halt-command)

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> I got this:

```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8240]

```

I'd guess we'll have to do some work getting the third party graphics drivers installed/working after we get that far.

---

### Post by dipper2 on 2014-07-21
> **kansasnoob said:**
> I ask because you might be able to enter a TTY (terminal) once you reach a frozen state by pressing Ctrl +  Alt + F1. Then you could type that command. Using a TTY can seem tricky - you'll be asked to login using the root users name and password.

Trying that now.

---

### Post by dipper2 on 2014-07-21
If I run through the low graphic error screens I end up with a terminal with tty1 at the end of the first line.

I have realised that I was typing an l instead of a 1 in libgl1 but even with the correct entry I now get a message:

> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied}
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I'll try Ctrl +  Alt + F1 and see if that makes a difference although I remember trying to log in as root before and it wouldn't accept my username/password.

***Edit: Ctrl +  Alt + F1 gives me the same tty1 screen asking me to log in with my user name and password***.

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> If I run through the low graphic error screens I end up with a terminal with tty1 at the end of the first line.

I have realised that I was typing an l instead of a 1 in libgl1 but even with the correct entry I now get a message:



I'll try Ctrl +  Alt + F1 and see if that makes a difference although I remember trying to log in as root before and it wouldn't accept my username/password.

***Edit: Ctrl +  Alt + F1 gives me the same tty1 screen asking me to log in with my user name and password***.

Remember to use sudo. I think they left sudo off of that command at Launchpad, people there seldom give consideration to us noobs - note that my forum moniker *kansasnoob* was totally appropriate when I began - oh the mistakes I made (and still make) #-o

---

### Post by kansasnoob on 2014-07-21
When you're in a root shell in recovery mode you're root so no sudo is needed, the same is true in a chroot.

The terminal prompt looks different when you're root:

```
lance@lance-desktop:~$ sudo -i
[sudo] password for lance: 
**root@lance-desktop:~#** exit
logout
**lance@lance-desktop:~$ **

```

You can tell by the # or $ symbols. When you see # you're already root so no sudo is needed, when you see $ you're not root and need to use sudo. Sorry I didn't think to mention that earlier.

---

### Post by dipper2 on 2014-07-21
Progress!!

Typing sudo worked. 34 to newly install, 3 not to upgrade, 1 not fully installed or removed. Need to get 21.4MB of archives.

Now the snag. After this operation 80.6 MB of additional disk space will be used.

Is that in the 200 MB of ROOT? Have I enough space?

Continue [Y/n]?

---

### Post by kansasnoob on 2014-07-21
> If I run through the low graphic error screens

OK, once we get that command to run properly and know that all of the packaging issues are resolved we need to investigate the graphics ordeal - if it still exists, which wouldn't surprise me :(

This page shows how to temporarily edit the grub boot parameter to hopefully get to a working GUI., albeit temporarily:

[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Jump to where it says Temporarily Add a Kernel Boot Parameter for Testing. The second screenshot there shows a line that begins with linux and ends with quiet splash.

You'll want to use the arrow keys to navigate to the end of that line, then backspace to remove quiet splash and replace it with nomodeset - That is lower case NOMODESET - then press Ctrl+X to boot the system using the nomodeset parameter.

With any luck that will get you to a working GUI - though it may be quite ugly - then we need to figure out how to install/enable the proper graphics drivers. I'll have to study that myself as I'm not sure where it's located in Precise Unity with the Trusty HWE :-k

---

### Post by dipper2 on 2014-07-21
Do I select Y or n to continue - see above?

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> Progress!!

Typing sudo worked. 34 to newly install, 3 not to upgrade, 1 not fully installed or removed. Need to get 21.4MB of archives.

Now the snag. After this operation 80.6 MB of additional disk space will be used.

Is that in the 200 MB of ROOT? Have I enough space?

Continue [Y/n]?

Type Y - we'll have to see ;)

When that completes run:

```
sudo apt-get -f install
```

That may provide some essential info.

I'm a bit worried about that "1 not fully installed or removed" but we can only see what happens, hopefully it will resolve itself.

---

### Post by dipper2 on 2014-07-21
Pages of text getting and unwrapping packages then at the end this:

> ln: failed to get hard link `/boot/initrd.img=3.13.0-32-generic.dpkg-bak' => `/boot/initrd.img-3.13.0-32-generic': Operation not permitted
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generica
W: Possible missing firmware /lib/firmware/rtl_nic/rt18168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rt18168g-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rt18106e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rt18168g-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rt18411-2.fw for module r8169
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by dipper2 on 2014-07-21
> **kansasnoob said:**
> When that completes run:

```
sudo apt-get -f install
```

That may provide some essential info.

reading packaging lists and dependency tree done then:


> 0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade 

**Edit - also reading state information done.**

---

### Post by kansasnoob on 2014-07-21
Go ahead and run:

```
sudo apt-get dist-upgrade
```

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> Pages of text getting and unwrapping packages then at the end this:

That's worrisome - I suspect it's due to that failed kernel installation due to /boot being too full.

I'll have to put my thinking cap on.

---

### Post by dipper2 on 2014-07-21
I have always had problems with automatic updates for linux-image=3.5.0-49-generic, ....51 generic and ....52 generic which never installed and this is what the command seems to be trying to install. Similar error messages for 51 and 52 but 49 seems OK.

> dpkg: error processing /var/cache/apt/archives/Linux-image-3.5.0-51-generic_3.5.9=51.77~precise_amd54.deb (=unpack):[
unable to make backup link of `./boot/abi-3.5.0-51-generic' before installing new version: Operation not permitted

and

> dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

and

> E: Sub=process /usr/bin/dpkg returned an error code (1)

Interesting that 49 was replaced successfully but not 51 and 52.

---

### Post by dipper2 on 2014-07-21
I ran Gparted again

/dev/sda1 now 148.66MiB used and 51.34Mib Unused if that's any help.

I also ran:

```
sudo apt-get -f install
```

and it only tried to install 51 and 52 so presumably 49 is OK now?

---

### Post by dipper2 on 2014-07-21
Please also see my two posts above.

I rebooted the computer and ran

```
sudo apt-get -f install
```

and it 'found' things!

Rebooted again and repeated the command and all it came up with was 0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

It's still giving the low-graphics warning though. :(

---

### Post by kansasnoob on 2014-07-21
> It's still giving the low-graphics warning though

Do you get to a usable desktop?

If so open the dashboard - type drivers - click on Additional Drivers and let it search.

If you're not getting to a usable desktop at all try the nomodeset option as I described here:

[http://ubuntuforums.org/showthread.php?t=2234830&page=5&p=13079147#post13079147](http://ubuntuforums.org/showthread.php?t=2234830&page=5&p=13079147#post13079147)

All of the Xorg files and folders moved in the Trusty HWE stack so we need to let the proper graphics drivers install in the proper place - I hope.

BTW we're going to want to remove all of those old Quantal series kernels but lets go one step at a time.

---

### Post by kansasnoob on 2014-07-21
I still wonder what the 2 not to upgrade is all about?????

---

### Post by dipper2 on 2014-07-21
I'm not getting a usable desktop. No change from before.

I can't get a Grub screen. Pressing and holding shift - it just loads up as before to the low graphics warning
Pressing and holding escape (which is given as the alternative) takes me to a menu that I think is HP's. Again, no Grub screen.

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> I'm not getting a usable desktop. No change from before.

I can't get a Grub screen. Pressing and holding shift - it just loads up as before to the low graphics warning
Pressing and holding escape (which is given as the alternative) takes me to a menu that I think is HP's. Again, no Grub screen.

Hmmmm, you were obviously getting the grub menu before, eh? Had to be to select recovery mode.

I don't know why you'd no longer be able to access the grub menu.

---

### Post by dipper2 on 2014-07-21
I can't recall ever getting the GNU Grub screen as in your link [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters").

---

### Post by dipper2 on 2014-07-21
Recovery mode comes up with an option

> grub Update grub boot loader

but I can't edit it and it doesn't look like the screenshot.

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> Recovery mode comes up with an option



but I can't edit it and it doesn't look like the screenshot.

Should look more like these:

[http://www.ubuntuvibes.com/2012/09/ubuntu-1210-simplifies-grub-boot-menu.html](http://www.ubuntuvibes.com/2012/09/ubuntu-1210-simplifies-grub-boot-menu.html)

Probably more like the third one.

---

### Post by dipper2 on 2014-07-21
Yes. It's the last one but what do I do with it?

Edit: found the e key!

---

### Post by dipper2 on 2014-07-21
There is some text after quiet splash

```
quiet splash $vt_handoff_
```

Do I remove all of this before typing nomodeset?

---

### Post by dipper2 on 2014-07-21
There's also a triple space between ro and quiet. Does that matter?

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> There is some text after quiet splash

```
quiet splash $vt_handoff_
```

Do I remove all of this before typing nomodeset?

Just to make the boot process prettier:

[http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg](http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg)

Yes you can remove it too - remember these changes are only for one boot - totally temporary to see if we can access the desktop in a way to allow us to open the dash and search for Additional Drivers.

---

### Post by kansasnoob on 2014-07-21
> **dipper2 said:**
> There's also a triple space between ro and quiet. Does that matter?

I'd never seen that but just make a single space between ro and nomodeset.

---

### Post by kansasnoob on 2014-07-21
BTW if you do get a graphic desktop the resolution will probably be incredibly wrong. That's expected. We need the proper graphics drivers to install - I hope.

---

### Post by dipper2 on 2014-07-21
No change I'm afraid. I'm still getting the low graphic warning.

Got to go now but back tomorrow. Thank you so much for all your hard work.

---

### Post by kansasnoob on 2014-07-21
I'm about ready for a snooze, so if anyone else jumps in they should see this:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264/comments/11](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264/comments/11)

Forget the part about bug #10, he meant comment #10, but we've already passed that point.

But the Trusty X-stack completely moved the location of all the X files and folders, so I suspect that most (or all) users of nVidia and Radeon graphics chips will encounter problems with the Trusty X-stack in Precise.

The problems with using a symlink are - well - it's sloppy and may or may not work.

---

### Post by kansasnoob on 2014-07-21
I think you should concentrate on finding out how to copy those .mozilla and .thunderbird profiles because things are looking more and more like you may have to pull the trigger on that HP Recovery and see what happens, but I fear it'll wipe all your personal files.

---

### Post by dipper2 on 2014-07-22
Just ran dpkg and got:

> No candidate ver: firstboot-video2
No candidate ver: locale-support-plugin
No candidate ver: oobe-dim-disable
No candidate ver: Ubuntu-recovery-bootloader

2 packages are going to be upgraded


Entered d for details and got:

> Upgrade: Linux-image-3.5.0-51-generic Linux-image-3.5.0-52-generic

These are the two upgrades (along with 49) that wouldn't install when the computer was running. They need 81.5 MB.

Clicking y to continue gives me 'Failed to fetch http:/' and 'Could not resolve'  messages

---

### Post by dipper2 on 2014-07-22
Tried selecting y again and got:

> E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by kansasnoob on 2014-07-23
Were you able to successfully backup the .mozilla and .thunderbird profiles?

I really think that's what you need to focus on now, and then try the HP recovery.

---

### Post by dipper2 on 2014-07-23
> **kansasnoob said:**
> Were you able to successfully backup the .mozilla and .thunderbird profiles?

I really think that's what you need to focus on now, and then try the HP recovery.

No. I don't have permissions and if I try to change permissions it says that I am not the owner of the program and can't change them.

Please would you run through backup from the live DVD in case I am doing it wrong. I'm not worried about Firefox, just Thunderbird. I have already copied pictures and documents to an external hard drive.

---

### Post by dipper2 on 2014-07-23
Sorry. I didn't explain properly.

When I copied my files, only the pictures and documents were copied. Thunderbird needed permissions.

When I tried backup using the live DVD, all I think it did was to backup from the live DVD but there is nothing in there. It didn't find the old files and nothing appeared on my external hard drive.

---

### Post by kansasnoob on 2014-07-23
Please open a new thread requesting help backing up your files using the live DVD.

I'm performing 14.04.1 iso/upgrade testing right now so will be busy until Friday.

---

### Post by dipper2 on 2014-07-25
Final update. See my post #57.

Following the removal of all files in ROOT relating to linux-image-3.5.0-49-generic (searched and listed those ending in -49-generic) they were reinstalled and did not needing updating.

We decided to remove all the series with 51 and 52 in them and again ran:

```
sudo apt-get dist-upgrade
```

and

```
sudo apt-get -f install
```

These were reinstalled and we got the message:

```
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade
```

I hoped that this was going to solve the problem but unfortunately I still got the low graphics warning. With no other ideas to pursue, we saved my files and loaded Ubuntu 14.04 from the live disc. There's no low graphics warning now!

Thanks to everyone for their help especially kansasnoob. Much appreciated. I see why this is called a community.

---

### Post by kansasnoob on 2014-07-25
Very glad you got things sorted out :D

---

