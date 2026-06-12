---
title: "Trying to install Ubuntu"
date: 2023-07-07
forum: New to Ubuntu
---

### Post by andib2 on 2023-07-07
Apologies, i'm a totally new to Linux at this level and trying to install it to have a play and learn Docker, although i cant get past this basic install.
I have a Lenovo M73 Tiny PC that i am using for experimentation. 

I have been trying for a week to get Ubuntu to actually boot up once installed. Ubuntu version used is 22.04 LTS installed from a USB stick created with Rufus on a Windows PC as GPT and UEFI
BIOS is on the latest version. Secure Boot is enabled in my BIOS. UEFI only mode it selected.
Install is a minimal version, but with updates downloaded during the install process.

Once the install is completed and i reboot (waiting for the command to remove the media and then hit Enter), it keeps getting to a page saying

/dev/sda2: recovering journal
/dev/sda2: clean, xxx/yyy files, aaa/bbb blocks

or just 
/dev/sda2: clean, xxx/yyy files, aaa/bbb blocks (the x, y, a and b values changes if i use a different hard drive)

Once at this point, it never moves. Left it for over 5 hours.

If i try to boot into Recovery Mode, it gets so far though the processes and just stops.
If i try to boot from the USB drive again and select 'Try or Install Ubuntu' i get the three spinning dots for about 5 seconds, then it just freezes

I have tried two SSD drives as the main drive, both do the same thing.
Both have deleted all partitions. Install is set to auto create the partitions. I can install Windows to both drives without any issues on the same PC.

I think it may be a UEFI issue, but not 100% sure.
I have tried to read through this Thread ([https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)), but ill be honest, i'm lost with what the commands mean, plus i cant get to a command prompt as it wont boot from the hard drive or USB stick.

---

### Post by oldfred on 2023-07-07
Looks like that system has 4GB of RAM. That used to work just fine, but Ubuntu has grown and works better with more RAM.
I might try Kubuntu or one of the lightweight flavors. Kubuntu is what I use and is more a mid-weight flavor and had it work on an older system with 1.5GB of RAM where Ubuntu would not install at all.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I might try with UEFI Secure boot off also.

Flash drive still should boot from UEFI Boot menu.
Often first thing to try after install, and confirmation of UEFI settings, and boot issues is Boot-Repair.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2023-07-07
> **oldfred said:**
> I might try with UEFI Secure boot off also
Yes, agreed, disable Secure Boot
Also, disable other Lenovo security options in the UEFI settings i.e.
Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Legacy mode
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

---

### Post by Impavidus on 2023-07-07
The line```
/dev/sda2: recovering journal
```indicates that it detected that the system wasn't properly shut down last time and the OS checks up the filesystem.

The line```
/dev/sda2: clean, xxx/yyy files, aaa/bbb blocks
```indicates that the filesystem is clean.

It appears that the OS fails to start the GUI, specifically, the graphical login screen. Command line login may still be possible (try ctrl+alt+one of the Fx-keys).

---

### Post by guiverc on 2023-07-07
I'll add this, but you've already received numerous valid responses, thus it'll likely be limited extra detail.

The original post didn't mention what Ubuntu 22.04 LTS product attempted to be installed, ie. Desktop or Server?   Given the mention of docker I'd assume Server; but it's best if details are specific so we can accurately answer.

The Ubuntu 22.04 LTS Desktop system used the `ubiquity` installer (unlike Server) which in my experience is pretty good, but how the ISO is written really matters, as you can write it using some tools (inc. rufus) so it won't boot except on specific modes, so take note of the Rufus documentation and personally I'd stick to a **clone** form of write of ISO as other options cause the ISO to be reformatted on media (*which can impact your install causing it to fail*).

If your issue is graphics related, I'll suggest trying Xubuntu.

I QA-test the *lighter* flavors of Ubuntu, and on some graphic cards I tend to notice issues first on GNOME or KDE Plasma... then they impact MATE/Budgie & other GTK type desktops.. and almost always last will be Lubuntu & Xubuntu.  Both early 22.04 media for Lubuntu & Xubuntu (22.04 & 22.04.1) use the GA kernel stack for early installs, on older hardware this would be my choice, and I've found of late (23.04) Xubuntu is impacted later than Lubuntu with graphical issues too... thus Xubuntu maybe worth a go.

(Why I had Xubuntu still okay on 23.04 when I saw some issues with Lubuntu surprised me (*in two boxes & not just a single box*), usually Lubuntu is last to experience issues, alas I don't know - either way  those two *flavors* are always last in my experience.  If using Qt5 apps, Lubuntu is *lighter* and will perform best, but Xubuntu is *lightest* if using GTK3 apps & seems to just work so easily. Xubuntu uses the same `ubiquity` installer as Ubuntu 22.04 LTS Desktop though there are differences in what is included on the ISO inc. kernel stack, additional graphics stacks etc with less available with Xubuntu which maybe helps it to 'just work')

---

### Post by andib2 on 2023-07-10
Thanks all
I have been away all weekend, but hopefully with have time to play again tomorrow and report back.

To answer some questions
@guiverc its the Desktop version i am trying to install. I have managed to install it before and play with Docker on another machine (tried to use with Home Assistant), so was hoping it would be OK
@oldfred the PC will be getting an update to 16Gb RAM once i can get it installed, as with Docker there will be a higher load. Havent ordered the RAM yet until i could get past the simple bits 
@tead of one ill go through these settings first and see what it does. Thanks

---

### Post by aljames2 on 2023-07-10
> **andib2 said:**
> @oldfred the PC will be getting an update to 16Gb RAM once i can get it installed, as with Docker there will be a higher load. Havent ordered the RAM yet until i could get past the simple bits 

Might I suggest doing it the other way around.  I like to do fresh installs on the hardware I intend to use.  Sometimes adding new ram sticks after an install is not problematic, but it could be.  Plus, the install process may go more smootly if you just start with the ram upgrade.

+1 on the lighter flavours, especially if sticking with the 4gb ram.

---

### Post by ian-weisser on 2023-07-10
Put your install USB stick back in. Boot from it.

Enter the "Try Ubuntu" environment. It's a stock Ubuntu Desktop environment. It's a bit slower (USB vs HDD/SSD), but that's not important.

Test all your hardware in that environment. Stream a movie. Make a video call. Print something.

See what works and what doesn't.

---

### Post by andib2 on 2023-07-11
> **tea for one said:**
> Yes, agreed, disable Secure Boot
Also, disable other Lenovo security options in the UEFI settings i.e.
Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Legacy mode
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)


Thanks to you and OldFred
Its booting now. I played with the some of the above options (that i had) and it worked. Not sure which combo finally fixed it, but Secure Boot was involved.

Most grateful

---

### Post by TheFu on 2023-07-11
When a thread is "SOLVED", please help the community to not waste time by using the "Thread Tools" button and marking the thread as "SOLVED".  This helps both people looking for answers and people wanting to be helpful.  Only the person who creates a new thread can do this.

---

