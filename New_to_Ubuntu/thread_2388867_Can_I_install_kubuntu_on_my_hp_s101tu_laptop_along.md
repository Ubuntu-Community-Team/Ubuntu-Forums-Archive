---
title: "Can I install kubuntu on my hp s101tu laptop alongside Win 10 64 bit?"
date: 2018-04-08
forum: New to Ubuntu
---

### Post by jack117 on 2018-04-08
Hi,

My laptop came with Win 10 64 bit OS can I install ubuntu/kubuntu along with my Win 10 OS dual OS on the same laptop? 

And which one should I choose ubuntu or kubuntu and version 12? cuz it has long term support? I want to get acquainted with linux no specific purpose for using linux.

---

### Post by SeijiSensei on 2018-04-08
Install a copy of VirtualBox for Windows from here: [http://www.virtualbox.org/](http://www.virtualbox.org/).

Then download the Kubuntu disc image from here: [http://cdimage.ubuntu.com/kubuntu/xenial/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/xenial/daily-live/current/)

Now create a new virtual machine in VB and install Kubuntu into that.  (You won't need to burn a DVD either; you can just point to the ISO image on your hard drive when creating the virtual machine.) Much easier than dual booting, especially if you're just taking a test drive.

Ubuntu releases with long-term support happen in April of even-numbered years.  The 18.04 release should appear in the next few weeks.  I'm running the beta on a number of machines with no problems.  Just starting out, though, I'd stick with 16.04 for time being, or wait until 18.04 appears.  The nice thing about virtual machines is that you can have a number of them, so you could create a 16.04 VM and an 18.04 beta for testing.

Give the virtual machine 1-2 GB of memory depending on how much RAM you have.  I find Kubuntu runs fine in a 1.5 GB VM.

---

### Post by jack117 on 2018-04-08
But does virtual box gives the same feel as the installed OS any limitations or drawbacks using virtual box? eg. as you said RAM I have 4 GB RAM and i5 6th generation. Will allotting 2GB to ubuntu make my Windows slow? or the RAM will only be utilized If I run virtual box. If I want can I remove or uninstall ubuntu thru virtual box with out issues?

---

### Post by SeijiSensei on 2018-04-08
With four GB I recommend allocating 1.5 G to Linux and leaving the rest for Windows.

For pretty much any task you're likely to use Ubuntu for, you'll see little difference between installing in a VM and installing onto the hardware.  It would matter if you play games, but you wouldn't want to use Linux for that anyway.  

VB can run the virtual machine in a window, or full-screen, or (my favorite) in "seamless" mode where the two operating systems share the display.  Since I run Windows in a VM on a Linux host, I moved the Windows panel to the top of the screen and left the Kubuntu panel at the bottom.  In this mode every app in the VM runs in separate window on the shared screen.  I rarely use Windows except for some select programs like Microsoft Access for which this arrangement works well. You can aso copy and paste between the windows if you install the "extension pack" for VirtualBox which I strongly recommend.

If you don't like Linux you can delete the virtual machine with the VB manager, then remove VirtualBox from your Windows system entirely.

The great benefit of this approach is that you don't have to commit to repartitioning the hard drive and the like.  In my experience HP makes installing Linux in a dual-boot arrangement extremely difficult because they create four primary partitions on the hard drive to hold the various repair tools and such.  This makes it impossible to install Linux without some serious work.  That may not be a problem on modern HP machines with UEFI which aren't limited to four primary partitions, but knowing HP, they probably still assume that no one would want anything but Windows and partition the drives accordingly.  I described the arduous process of doing this some years back in this post: [https://ubuntuforums.org/showthread.php?t=1852213&p=11299287&viewfull=1#post11299287](https://ubuntuforums.org/showthread.php?t=1852213&p=11299287&viewfull=1#post11299287)

Also, see [https://ubuntuforums.org/showthread.php?t=2312918](https://ubuntuforums.org/showthread.php?t=2312918)

Compared to all that hassle, using VirtualBox is a breeze.

---

### Post by jack117 on 2018-04-08
Great! I will give it a try.

---

### Post by bsodx on 2018-04-17
Can help you with dualbooting since I did one recently.
This one is a overview of the things you need to do. If you choose to do so, tell me so I can expand this and add pictures.

First of all, if you are only going to test stick with Wubi or a VM. Dualbooting takes time and courage.
Second, BACKUP EVERYTHING. Seriously, use a software like Macrium Reflect and take a full image of your system. Playing with partitions is dangerous and if you screw up you'll thank me for the backup you did.

If there's a recovery partition preinstalled on your computer, it may refuse to work after any repartitioning process. Don't rely on it.
And last warning: If you have a old computer with MBR(Windows 7 and before uses it) you can have a max of 4 partitions. If you have all 4 full you'll have to delete one) No need for UEFI.

What you need:
2 or 3 USB pendrives, each minimum 4 GB(One for Ubuntu bootable, one for Macrium's recovery environment and one for windows recovery recommended)
The iso file of Ubuntu flavor you want to install (Installation steps are pretty much same for flavors of Ubuntu)
Program Rufus
A big drive to backup (2x empty space of your used diskspace recommended)
Macrium Reflect
If Windows won't let you partition, EaseUS or AOMEI Partition Wizard
TotalMounter
Auslogics Disk Defrag

1.Backup
*Download Macrium Reflect Free(Not a trial)
*Now plug the big drive.
*Install and open the program
*Select the system disk
*"Image this disk..."
*Select a folder in the big drive to put the backup
*Set a plan or add schedule to use backups, for example if you want to do one full backup only you have to add schedule->One time event->This day->2 or 3 minutes later from current time.
*Set it
*It'll ask you to do the backup, hit ok and do something else, it'll take 2-3 hours to do a full backup
*Now you have a backup to wind back when needed, a few more steps to go
*Now plug the HDD out, insert an empty USB or format it
*Click on the "Make a recovery disk for Macrium"
*Next, next, when prompted point your USB
*When it's done plug it out
*Restart once
*Download and install TotalMounter, which will catch the CD image Windows makes
*Navigate to the place where you burn a recovery disk in system settings. 
*Burn to the DVD drive TotalMounter made
*When done get back to the TotalMounter and get the iso file
*Burn to another USB with Rufus or YUMI

2.Partitioning
*Install the defragger(Decline the crapware)
*Defrag once until it's done
*Open cmd with admin, run chkdsk, if problems are found do chkdsk /f and restart and let it do its magic
*Windows Disk Manager, make space for Ubuntu-min 20-25 recommended here but I use 100
*Right click and shrink the disk you want(If Win won't you need to install AOMEI and do things there.)
*Get enough unallocated space
*Restart, defrag+chkdsk
*Burn the Ubuntu iso you got to last USB with Rufus

3. Real thing
Shut the computer down, plug the Ubuntu drive in
Reach to your UEFI/BIOS (Google it if unknown)
Set boot order to boot the USB(Warning: If you use UEFI select EFI boot, if MBR select the one that's not EFI boot)
Try Ubuntu, when ready hit Install Ubuntu
Updates and 3rd party soft optional but 3rd party should be checked
Will ask for what to do that it sees the Win7 there, "Something Else" (For more auto select Install Alongside)
Make 3 disks on free space(for 100 gb 20-25 gb partition for mount point / , equal to your RAM type swap partition, what's left for /home partition)
Install grub on the disk you boot win and ubuntu flavor If you have only one disk it should be something like dev/sda
Make sure everything's okay, next
It'll ask to write the things you made, this is the point of no return and takes much of the courage, when ready hit continue
Choose location and keyboard
Hit Install and have a nice good coffee, you deserved it
Restart, plug the USB out when shut down
If things went straight you should see grub screen. Don't worry if there's 2 windows entries, any one will do but I use the sda2 one
Try to boot into both once and voila you have a dualbooting computer

Again I'll clarify if you choose to go this way, please reply befor beginning so I can guide you better.

---

### Post by bsodx on 2018-04-17
I dualbooted recently and had to dump the driver partition in exchange for an extended one. Works fine

---

### Post by gavincorticontact on 2018-04-18
Of course you can! The method is called dual booting! I see in this article there are a lot of people telling you to use a virtual machine, that is an option but it often times runs much slower in a virtual machine than it does on actual hardware. And desktop preference is up to you. My advice would be to compare and contrast Ubuntu/Kubuntu and decide on which. If you install Ubuntu, go for the LTS versions. With Kubuntu, I prefer the 16.0.4.4 LTS version.

---

### Post by SeijiSensei on 2018-04-19
Installing to a machine that has all its partitions in use, as HP computers often do, is a real pain in the neck.  Have you ever done that?  I have, and that's one reason why I suggested using a virtual machine.

---

