---
title: "Ubuntu/Windows 8 Dual Boot (GPT Table issue) (Asus 1015)"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by james.gravley on 2014-09-18
I will try to keep the length of this post down, but it does require a bit of back story.

BACKGROUND: Bought the Asus 1015 ([HERE]("https://www.google.hn/url?sa=t&rct=j&q=&esrc=s&source=web&cd=10&ved=0CFIQFjAJ&url=http%3A%2F%2Fwww.amazon.com%2F1015E-DS03-10-1-Inch-Laptop-Ubuntu-VERSION%2Fdp%2FB00COQK8QY&ei=su0aVKyLN5eXgwTts4G4CA&v6u=https%3A%2F%2Fs-v6exp1-v4.metric.gstatic.com%2Fgen_204%3Fip%3D190.109.212.98%26ts%3D1411050931351375%26auth%3D4iyavp7766j34slfqngmfhbwytulsu5a%26rndm%3D0.33672521566040814&v6s=2&v6t=3293&usg=AFQjCNHMtMns04v3xsHtdn4m_2UEzxWyUQ&sig2=DjY5u8t9OZEu-xQ-6AtpWA") for specs) for cheap with Ubuntu 12.04 LTS native. Worked awesome all summer, returned to my job at an International School. Had the tech guys install Windows 8 - problems with dual install - wiped native Ubuntu - installed Windows 8. Windows 8 worked great, but I would like to dual boot. I prefer Ubuntu 14.04 but need Windows 8 for school (footnotes in OpenOffice are not compatible). Go to install Unbuntu 14.04, thinking it will be easy as pie like normal - discover the UEFI issue for Windows 8 - open a can of worms...

PROBLEM: Run Ubuntu USB install - ready to setup partition - does not see partition. (see "does not see partition" attached). However, Windows partition editor sees partition fine. There should be two partitions, one unallocated and one with Windows 8 (tech guy setups). Think to myself "this is curious" - go to Live version - run GParted - get GTP Error (see other picture) - begin searching here for solution - find [THIS]("http://ubuntuforums.org/showthread.php?t=1510017") post - followed suggestions by srs9654 - think I can fix, but really I just messed something up...

HELP: Now, when I try to boot normal it just sits on a black screen with a little white blinking cursor. I would prefer to preserve the Windows 8 install, is this possible after having deleted the GTP stuff (per the directions from srs9654)? It is issues like this that remind me that I am still a Linux noob. 

Any links, help, whatever that can be offered would be more than appreciated!

---

### Post by Gordonbp531 on 2014-09-18
I reported this bug of not seeing the Windows 8 install last year. [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564)
It's still not been sorted in 14.04! 
Your best option is to restore the Windows 8 install as it was before the attempt to install Ubuntu.
Then:



a) Do not remove anything to do with GPT or Intel fast boot, or UEFI.
b) Use 14.04 instead of 12.04
c) Create the free space within Windows - do NOT use GParted for this as it can affect the Windows install.
d) Run the Live CD/USB with Ubuntu on it.
e) Click install, and when it gets to the "Install on the disk" option, click on Other.
f) Then set up your Ubuntu partitions in the free space, setting the partition for Grub as the EFI partition.

Done!
Hope that helps!

---

### Post by oldfred on 2014-09-18
Did you install Windows in UEFI mode or gpt mode.
The error seems like you had gpt partitioning with Ubuntu which could have been either BIOS or UEFI.
But many manual installs of Windows are in BIOS mode not UEFI. And then if drive was gpt Windows auto converts to MBR(msdos) but does it incorrectly. It leaves the backup gpt partition table.

Then you need to use fixparts to remove backup gpt partition table. Do not run any conversion from gpt to MBR if you installed Windows in UEFI mode as that only then boots from gpt partitioned drives.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Best to post this first:
sudo fdisk -lu
sudo parted -l

If gpt  partitioned then fdisk will just report drive is gpt and that is correct as fdisk does not work with gpt partitioned drives. parted & gdisk (also on rodsbook site) work with gpt partitioned drives.

---

### Post by Gordonbp531 on 2014-09-18
I didn't think Windows 8 will install in anything other than UEFI mode...

---

### Post by oldfred on 2014-09-18
You can install Windows 8 in either BIOS mode or UEFI. It also installs to older Windows 7 era systems that are BIOS only.
How you boot install media is how it installs. That is the same for Ubuntu and even Windows 7.

It is mainly that UEFI and BIOS are not compatible and once started booting in one mode you cannot switch to the other mode. How UEFI or BIOS system loads data for operating system to use is so different, you cannot switch modes.

Windows only boots from gpt partitioned drives with UEFI. Or UEFI must have gpt.
Windows only boots from MBR(msdos) partitioned drives with BIOS. Or BIOS must be MBR.

Ubuntu will boot from gpt partitioned drive with either UEFI or BIOS if you have correct supporting partitions.
All UEFI installs need an efi partition for boot files. 
With BIOS Ubuntu needs an extra bios_grub partition to correctly install to gpt's protective MBR as the space after the MBR where core.img (part of grub) is normally installed does not exist with gpt.

---

### Post by Michael_McKenney on 2014-09-18
Windows 8 security could be the issue.  I am staying with Windows 7 x64 till Microsoft fixes everything in Windows 10.  Try disabling UAC in Windows 8.   You will not be able to upgrade from the Windows store with it off.

---

### Post by Gordonbp531 on 2014-09-18
Eh? Nothing at all to do with "Windows 8 security"....or UAC or anything like that.

---

### Post by james.gravley on 2014-09-18
Thank you for the help, and I have now found tons of documentation about the specific issue. 

However, what I am trying to fix is my using the "zap" command on System Rescue to fix the GTP issue. I used that command and now Windows 8 will not boot. It sits on the black screen with blinking cursor. This does not conincide with all of the documentation I have read. 

Any suggestions for getting Windows 8 to boot?

---

### Post by oldfred on 2014-09-18
See this thread, same issue?
[http://ubuntuforums.org/showthread.php?t=2244669](http://ubuntuforums.org/showthread.php?t=2244669)

Did you use testdisk to restore partitions?
Do you have a Windows repairCD or flash drive, or even better did you make a full backup of Windows?

---

### Post by james.gravley on 2014-09-19
thanks again for all the help! i decided the best idea is to reinstall windows 8 and fix the junk the tech guys did not do right. From there i can dual boot    thx

---

