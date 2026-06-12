---
title: "Linux Install on USB Hard Drive - Not USB Flash Drive"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-01-28
I'd like to install Linux on a USB Hard Drive rather than a USB Flash Drive or the main computer disk.

Are there any issues with doing this?  Will the install dialogue recognize both hard disks in the system and let me choose the USB hard disk drive?

My objective is to not disturb the main computer disk drive for my initial work with Linux.

Thanks, Ken

---

### Post by C.S.Cameron on 2014-01-28
When installing to USB External Hard Drive I leave the first partition as NTFS so I can also use it as an external on Windows machines.
I use the second partition for /, and the third for /home and put swap at the end.
Make sure the bootloader ends up on root of the external drive.
If the external is set as first HDD in BIOS, you will be able to boot either the internal or external drive from grub.

---

### Post by DuckHook on 2014-01-28
Not only do-able, but recommended. USB HDDs tend to be more robust than USB flash in my experience. I've installed this way a number of times.

The install routine **should** recognize both drives and happily proceed as usual once you define the proper drive. But to head off any possibility of a problem, you ***MUST*** backup everything of importance before you try, and make sure that you have working reinstall disks for Windows and all apps. All it takes is you inadvertently pointing the install process to the wrong drive and—boom—major disaster.

At the point where the install process asks you where you want to install, select "something else" and then change to the proper drive. Internal drives will be *sdx* (where "x" is a letter series starting with "a"). USB drives will likely be *srx* (where "x" is a number series starting with "0" (zero)), but it could also be a different device including *sdb* (assuming your internal drive was *sda*).

Make sure you install grub only to the external drive. This way, when the external drive is not plugged in, no Linux OS will show up and you will just have your old Windows bootloader handling the boot process. If using this method, then when the USB drive is plugged in, you must either change you BIOS to load external drive first, or use whatever fancy key combo that you computer uses to select USB drive first.

---

### Post by KAWill70 on 2014-01-28
Many thanks C.S.Cameron and DuckHook for your replies.

All that information will be a great help and is much appreciated!

One other thought would be to disconnect the Windows hard drive prior to Linux installation on the USB HDD to prevent any possible problem.

I wonder if my BIOS would handle things without change.  I currently have USB HDD set as the first boot device in the BIOS and the computer will boot any Live Linux installation in USB Flash that is plugged in.  Otherwise boot proceeds to the main computer hard drive.

---

### Post by monkeybrain20122 on 2014-01-29
The only thing to be careful about is to install the bootloader at the external drive, the default will install it in your internal drive. Just watch out for that.  Keeping that in mind, you don't need to disconnect the internal hard drive.

---

### Post by oldfred on 2014-01-29
Just to highlight the install of grub2's boot loader to the MBR of your external.

My screenshot shows me installing to a partition on sdc, but combo box at bottom is still at default of drive that is sda, that must be changed to your external drive.

---

### Post by C.S.Cameron on 2014-01-30
I usually recommend disabling the internal drive to people doing this for the first time.
When you boot the external, you can do an update-grub to put the internal drive on the grub boot list.

---

### Post by DuckHook on 2014-01-30
> **C.S.Cameron said:**
> I usually recommend disabling the internal drive to people doing this for the first time.
When you boot the external, you can do an update-grub to put the internal drive on the grub boot list.+1 Excellent strategy.

---

### Post by sudodus on 2014-01-30
> **C.S.Cameron said:**
> I usually recommend disabling the internal drive to people doing this for the first time.
When you boot the external, you can do an update-grub to put the internal drive on the grub boot list.

++1

---

### Post by KAWill70 on 2014-04-07
Here is an update on this thread.  I bought a Seagate 500G USB 3.0 Expansion Drive and now have it working with two versions of Linux on a nine year old desktop computer with USB 2.0 support.

Everything seems to be working. The computer boots into a Grub menu if the USB drive is connected with choices of either Linux system including the Recovery Modes, Windows XP, or Memory Test.

I partitioned the drive with enough logical partitions to handle a /root and /home directory for a total of four Linux installations.  Initially Windows would not recognize the drive until I formatted the remaining space as NTFS.  That was done with GParted while running live at the end of the installation.

I had planned to disconnect the Windows disk during installation but in the end felt confident that I would not disturb that disk.  You really do have to be careful with several opportunities to make a mistake.

A little later I may connect the USB drive to my new Win 7 computer which supports USB 3.0.  I tested the disk using USB 3.0 on Saturday after it arrived and large data transfers were about three times as fast compared with USB 2.0.

Thanks all for the help.

---

### Post by oldfred on 2014-04-07
If just testing installs, I might leave /home inside /, so you only have one partition for each install. But then create a larger /mnt/data partition or use the NTFS data partition(s) for all your data in each /home. Makes it a bit easier to share, but does require extra set-up to give yourself ownership, permissions and to mount data partition(s).

 howto shared data - by  captain_chaos2
[http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581](http://ubuntuforums.org/showthread.php?t=2213485&p=12979581#post12979581)

      
 
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by Double.J on 2014-04-07
+1 
I usually have anything up to around 8 Linux/Bsd installs at a time, plus VM's and around 3 installs will be regularly replaced as I try out new things. I keep my /home inside my / partition. This is because I Want to keep my Hard drive at least a little bit more understandable, also when you have so many installs, all those /home partitions account for a huge amount of reserved data.

With Linux systems you can of course just have one big shared /home partition. it's not pretty or organised because you have to use a different user name in each distro so the settings and such don't conflict. 

I just use an NTFS partition of 800 GB with folders like 'music' 'pictures' downloads' 'thunderbird' 'minecraft' etc sitting on it. 

on my new installs, I then make a new directory in media called data, and put  line in /etc/fstab to mount my ntfs partition there at boot. 

After a restart I use mv to backup an existing directory in /home, and then use ln to create the link:
[CODE]sudo mv /home/bob/Pictures /home/bob/Pictures.bak
sudo ln -s /media/data/pictures/ /home/bob/Pictures[CODE]

Its so much more convenient to manage data - especially downloads! Checking which system you downloaded that file on a week ago is annoying!

You can also Do the same in windows 7 of you upgrade (recommended). by going to computer management->disk management you can tell windows a folder to always mount the external disk at, then add the folders to the windows libraries so that when the linux HDD is plugged in, the pictures, videos, etc appear in Pictures, Videos, etc in windows.

Finally plan ahead - this is all for single user use! if you plan to use multiple users, it'll affect you fstab, as well as having a different user folder for each user on the NTFS. plan this out at the start, or all your soft links will break.

Best of luck!

Jj

---

### Post by sudodus on 2014-04-08
> **KAWill70 said:**
> Here is an update on this thread.  I bought a Seagate 500G USB 3.0 Expansion Drive and now have it working with two versions of Linux on a nine year old desktop computer with USB 2.0 support.

Everything seems to be working. The computer boots into a Grub menu if the USB drive is connected with choices of either Linux system including the Recovery Modes, Windows XP, or Memory Test.

I partitioned the drive with enough logical partitions to handle a /root and /home directory for a total of four Linux installations.  Initially Windows would not recognize the drive until I formatted the remaining space as NTFS.  That was done with GParted while running live at the end of the installation.

I had planned to disconnect the Windows disk during installation but in the end felt confident that I would not disturb that disk.  You really do have to be careful with several opportunities to make a mistake.

A little later I may connect the USB drive to my new Win 7 computer which supports USB 3.0.  I tested the disk using USB 3.0 on Saturday after it arrived and large data transfers were about three times as fast compared with USB 2.0.

Thanks all for the help.

Thanks for sharing your solution :-)

Remember that Windows XP reaches end of life soon (I think today is the last day of support), and you should avoid using it when connected to the internet.

---

### Post by monkeybrain20122 on 2014-04-08
> **sudodus said:**
> 
Remember that Windows XP reaches end of life soon (I think today is the last day of support), and you should avoid using it when connected to the internet.

If I were OP I would just wipe xp off the hard drive, clone the linux installations of the external drive and restore it there.

---

### Post by KAWill70 on 2014-04-08
Thanks all for the additional information.  That's a very good point about wasting disk space with the multiple /home partitions if only testing.  I'll need to study all the other information that was passed along.

I now have four Linux installations on the external USB disk.  WinXP appeared in the Grub2 boot menu after the first two installations and then disappeared after Ubuntu 12.04 LTS was installed.  WinXP then reappeared in the boot menu after the final installation which was Bodhi Linux 2.40.

Does anyone have an explanation for the disappearance and reappearance in the menu list?

---

### Post by 23dornot23d on 2014-04-08
> 
Does anyone have an explanation for the disappearance and reappearance in the menu list?                 


Sometimes it makes a difference when running grub-update ............ if the other file systems have been mounted or not.

One that never used to show for me was Fedora ............ and I asked a similar question on here ...... mounted that partition

and it would then show up ok in the menu .......

Not so sure with XP ....... but I used to notice that some of the debian installs would only show up from a debian install of grub

too ......... often they would go walkabouts when installing grub from ubuntu .

___________________________________________________________

Mandrake/Mandriva used to have a good system of finding things between 2008 - 2010 ...... even linked old grub .97 Menu items - to grub 1.99 - 2 automatically with

a separate menu item to jump across to select and run them from the old format too .

---

### Post by Double.J on 2014-04-09
Hi there!


so, why does the boot menu change after each install? Maybe best to quickly go over what happens at boot:


grub is, by default installed to /dev/sdx (no partition number) this means it will be installed to the very first sector of the hard drive. This area is on every disk and is essential. It's called the MBR and is alays less than 512 bytes. This contains the partition table and is the first place your computer reads at boot.


When you power on, the bios loads from the motherboard, checks the hardware and boot parameters then loads the mbr to ram and hands over. Boot now runs from the disk. On an xp install the mbr will have the windows loader and continue without option. When grub is installed here, it writes over any existing boot loader (well there is only a few hundred bytes of space!). When the bios hands over to grub, it shows you the menu list of all the systems it knows. What these are, are paths to kernels on the computer. Now the linux kernel is currently around 17 million lines of code, so as you can imagine it doesn't fit on the mbr. These are stored in /boot on a partition. Next up, you select an os and grub hands over to the kernel, which loads init and the system boots.




The important parts here are that you can only have one bootloader in the mbr, and that the kernels sit on the partition where /boot is for that system, not the mbr.


The boot loader is usually installed by the distro's installation application, and by default usually gets written to /dev/sdx. This means that it erases the bootloader entry already in the mbr. So if you install ubuntu, then fedora, then suse, it will be suse's bootloader at the mbr. This means that it will be configured however the last install chose to install it, and which partitions were visible to the installer.


for example, some installers need partitions to be mounted to detect, they also have to be able to read the file system. So if xp went away after one install, then came back after the next, that install in the middle either didn't have the ntfs driver to read the partition, or it needed xp mounted, but the next installer saw it okay.


over the life of a release you will receive quite a few kernel updates. To load these, the updater updates grub. If another distro is at the mbr, it will load the kernel it knows about, not the latest. For that reason, it is best to decide which will be your main OS (such as ubunu lts) and install that bootloader to /dev/sdx and then install all subsequent bootloaders to the /boot paetition or / partition of that OS. It means that you will have a chain boot situation at power on, but will always boot from the latest kernel by default.


the other option is to only have the one grub installed to the mbr, but after each new kernel update, you will have to boot into the distro which administers that grub, and update grub.


hope it helps!


Jj

---

### Post by KAWill70 on 2014-04-09
Thanks to 23dornot23d and gnu/mirow for all the additional information.  That is really a great help and much appreciated.

The total overview of boot summarizes the whole process for me and should also be a great resource for others that find this thread.

---

### Post by Double.J on 2014-04-09
You're welcome, glad to be of help! :D

you're extra installs, are they your standard setup, or were you trying out different distros? If you're like me and just like to try a bit of everything, have a search for makulu. I had a play with it last month, it's quite quirky! 

All the best, 
Jj

---

### Post by KAWill70 on 2014-04-10
Re: "Extra installs, are they your standard setup, or were you trying out different distros? If you're like me and just like to try a bit of everything, have a search for makulu."

I'm new to Linux and don't have a standard setup.  With the end of support for WinXP I now have a computer available to try Linux.  Currently using an External USB hard drive for multiple Linux installations.

The computer is nine years old with SIS 661FX motherboard graphics which is a problem for some distributions.  In the case of Ubuntu and variants I often have to use the distribution from early 2012.  However, in some cases I can still boot live by selecting compatibility mode or altering boot parameters.  In some of those cases I can then install successfully on disk while in others I can't.  As an example, Mint 16 Cinnamon might come up in a software rendering mode which runs very slow.  My best solution would probably be adding a video card or just using a later motherboard.

Thanks for the information on makulu.

---

### Post by Double.J on 2014-04-10
Yes linux is often a great solution to older hardware; I'm currently running a 2006 office client, a ppc G4, a 2008 netbook and my home server is a 2004 pentium box that was probably a bargain bucket deal then!

However things must keep going forward, (remember that 17m line kernel? It started out as 175,000! alas a lot of my older hardware has run into issues with the death of gnome 2. I would suggest maybe lxde distro's such as lubuntu? That makulu distro i suggested are also working  on lxde - maybe best to wait for that? Lxde mint is very good too!

---

### Post by KAWill70 on 2014-04-10
Re: Lubuntu

Lubuntu 13.10 is working very nicely in my nine year old PC.  The surprising thing is that I can only boot into live mode if I add nomodeset and xforcevesa to the boot parameters.  However, I can then install on my hard drive and it boots and runs without problem for unknown reasons.

If version 14.04 also works that might be a very good option for me.

One thing I have noticed with Linux is that some versions reboot or shutdown cleanly while others don't.  Sometimes a reset is needed.  I'm guessing that is an issue with the hooks into the motherboard and BIOS.

---

### Post by sudodus on 2014-04-11
Please avoid hard resets. Use

***SysRq R E I S U B***

instead to flush the buffers to files (finish closing the files properly). See this link

[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by KAWill70 on 2014-04-11
Re: SysRq R E I S U B

Thanks for the help.  I had never heard about that feature and it looks as though I would hold down my PrtScn key and then type REISUB in sequence.

Are you suggesting doing that just for those times when the system is having some difficulty?

I was talking about Reboot or Power Off which may or may not work on any given version of Linux with my motherboard.  Or perhaps you are suggesting the PrtScn REISUB command after the failed Reboot or Power Off attempt.

---

### Post by sudodus on 2014-04-11
Yes, often but not always it is ***alt + PrtScrn*** continuously while pressing ***R E I S U B*** slowly maybe one key per second.

And yes, do it only when the system is having some difficulty!

[FONT=courier new]**sudo poweroff**[/FONT] and [FONT=courier new]**sudo reboot**[/FONT] (or the GUI 'buttons') are better when they work.

---

### Post by danholl14 on 2014-09-29
I wonder if i pay have some more help with this ? I basicly want to do what the other chap has done and have it run off an ext 500 gb hdd...

I have booted up with the usb install download and got into the "try" version of ubuntu that boots of the usb but every time i install ubuntu and reboot the system it will not boot off the usb 500gb. 
here is an image of the settings i am using for the partitions .. is it obvious from this what i am doing wrong ? 
[IMAGE]("http://www.anony.ws/image/DVQ0")
Cheers guys and girls
[[IMG]http://www.anony.ws/image/DVQ0[/IMG]]("http://www.anony.ws/image/DVQ0")

---

### Post by KAWill70 on 2014-09-29
> **danholl14 said:**
> The system will not boot off the usb 500gb.
Is your BIOS set up properly to boot from the USB Hard Drive?  Also make sure you remove the Linux CD or Flash Drive used to install Linux before attempting to boot from the USB drive.

Your partitions and boot loader look correct but I think the partitions should also have the format box checked.  I would have a much smaller /root partition but the large size may be OK.

---

### Post by danholl14 on 2014-09-29
Yea, I have made sure it is just booting off the usb ext etc etc..

Ill play around with making the partitions smaller.. see if that helps..

cheers
 I have formatted them several times this is like the 10th time i have tried to install


Is there a good tool you can suggest to load and look to make sure the partitions are setup correctly once install has finished ?

---

### Post by KAWill70 on 2014-09-29
Let us know what happens when you attempt to boot and what is displayed on your screen.  It's also possible that your hardware has some compatibility problem with Ubuntu 14.04.

I typically have the swap partition first followed by root.  A separate home partition is often used if you want to keep those files separate.

---

### Post by oldfred on 2014-09-29
Is system BIOS or UEFI?

Some older systems if not in AHCI mode, or booting from USB drives could only boot from first 100GB or so of a drive. then it is better to have a smaller / (root) of 20 or 25GB and use the rest as /home and/or shared data with your main install on internal drive. 

If system is UEFI you should also install in UEFI mode to external. You must have a BIOS install as you do not have gpt partitioning nor an efi partition. While you can boot when systems are in different boot modes, it is more difficult.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

If you still have issues download Boot-Repair into live installer and run the sumary report. Just post link not full report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by danholl14 on 2014-09-29
Thanks guys I will re read those links.. 

the hdd is a brand new usb 500gb and the laptop is a del m5030 or 3050 i forget which.

---

