---
title: "Recovering hard drive with testdisk"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by ChakLong on 2013-02-19
Hi, when I was installing Ubuntu I somehow managed to screw up the installation and the installer decided to completely wipe an almost full 2TB HDD (E: Drive). Not only did my hard drive get wiped, but the installation seems extremely buggy, for example Ubuntu crashes whenever I move a window and there are strange unexplained errors popping up randomly, and when the boot menu comes up asking for what OS to run, I can't run Windows 7 from that menu and I have to change my boot order in my BIOS to boot to Windows.

Looking at some install guides, there seems to be a step where you can create a partition for Ubuntu when installing alongside Windows 7, but I never had that choice, as the installer just randomly decided to wipe my hard drive, and now it can't be accessed by anything, and I have no idea where Ubuntu is installed either.

I don't even seem to be able to access the hard drive properly in Ubuntu either for some strange reason, and the only drives I can see is my 256GB SSD (C: Drive) and 4TB HDD (G: Drive) which weren't affected.

If I try to open the affected 2TB HDD in Windows, it tells me that "You need to format the disk in drive E: before you can use it. Do you want to format it?"

Now I'm trying to recover my hard drive's original data with testdisk, but when I analyze it and select the option to show "List Files" when it comes up with a single partition, it tells me "Can't open filesystem. Filesystem seems damaged."

I am currently using Photorec on Windows 7 to recover my files and the files all seem to be present. How do I get Testdisk to recover my hard drive properly? Is there some other way to recover my data along with the original file directories and so on?

I'm just confused because Ubuntu just randomly wiped my HDD and the system doesn't even seem to have installed properly. The files are still there, so how do I restore the HDD?

---

### Post by Mark Phelps on 2013-02-19
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by arnav803 on 2013-02-19
if your filesystem is damaged ithink you should try fsck command or boot into rescue mode and then try fsck command it will repair your filesystem.

---

### Post by oldfred on 2013-02-19
Since you have multiple drives and multiple installs it may be best to see details.

But if you have actually installed Ubuntu over your data, you have to stop using it as every use is overwriting more data. Use liveCD/DVD/Flash drive you used to install.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

