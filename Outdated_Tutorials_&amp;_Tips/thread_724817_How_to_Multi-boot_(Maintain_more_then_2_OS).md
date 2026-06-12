---
title: "How to Multi-boot (Maintain more then 2 OS)"
date: 2008-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2008-03-15
[SIZE=6][CENTER]How to Multi-boot (Maintain more then 2 OS)[/CENTER]
[/SIZE]

[CENTER][IMG]http://www.i-automatic.com/Product/TRIOS/trios_02_main_img08.gif[/IMG][/CENTER]

[color=darkred]**Be aware this thread is from 2008 and is out of date as it uses grub 1. I have left it for historical reasons, but it is no longer maintained. Links may be broken. Please see any of the grub 2 guides, either on the Ubuntu wiki or forums.**[/color]

[Ubuntu wiki grub2](https://wiki.ubuntu.com/Grub2)
[Ubuntu forums grub 2](http://ubuntuforums.org/showthread.php?t=1195275)
[Grub 2 Tweaks](http://ubuntuforums.org/showthread.php?t=1287602)

Dual booting is fairly straight forward, but what happens when you would like to boot multiple (more then 2) operating systems ?

If you are new to Ubutnu, or wanting "simply" to install Ubuntu and Dual boot with Windows, this is not the best tutorial, although you may find it informative. Please refer to this wiki page:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

In this how-to I will cover primarily booting multiple Operating Systems, primarily Linux Distributions (Versions), using GRUB. For other OS, see the following links :

1. Booting multiple versions of windows can be tricky as you need to "hide" the various windows installs from each other.[INDENT][http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)[/INDENT]2. BSD can bee more cryptic :[INDENT][http://www.ubergeek.co.uk/howtos/grub-freebsd-windowsxp.html](http://www.ubergeek.co.uk/howtos/grub-freebsd-windowsxp.html)[/INDENT]3. NetBSD and OpenBSD : [INDENT][http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)[/INDENT][COLOR=darkred][U]
Note to Vista users[/U]: Please refer to this link (EasyBCD)[/COLOR] [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)


[SIZE=4]_**Contents:**_[/SIZE]
[LIST=1]
[*]Prerequisites ~ "things you should already know".
[*]General overview of the boot process.
[*]Partitioning.
[*]Sharing partitions.
[*]Install a new OS, manually configure GRUB.
[*]Automate maintenance of GRUB with Chain loading.
[indent]Example.[/indent]
[*]Automate maintenance of GRUB with "configfile".
[/LIST]

[color=darkgreen]**To automate maintenance, either chainload or configfile (not both).**[/color]

[SIZE=4]**Prerequisites ~ "things you should already know" :**[/SIZE]

You must have a solid understanding of partitioning and partitioning naming (both Linux and GRUB numbering schemes). While Windows letters partitions ( C:\) , Linux uses /dev/sdxy (or /dev/hdxy) and Grub numbers partitions starting with 0.

If you need a refresher on partitioning terminology see this link :

[Partitioning basics]("http://ubuntuforums.org/showthread.php?&t=282018")

For this tutorial, think of each installation as needing both a root ( / ) partition and a boot directory (or separate /boot partition if using XFS, LVM, or encryption).

You will also find it helpful to have some understanding of grub configuration. **Hermanzone [s]is[/s] was great resource for grub** (The grub 1 information is no longer maintained).[INDENT][http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)[/INDENT]If you understand partitioning and basic GRUB configuration, Mult-booting is not too hard.

Hermanzone grub 2 page is located [here](http://members.iinet.net/~herman546/p20.html)



[SIZE=4]**General overview of the boot process :**[/SIZE]

The details of the boot precess are beyond this tutorial, but here is a nice summary from Wikipedia :

> When a computer is turned on, the computer's BIOS finds the primary bootable device (usually the computer's hard disk) and transfers control to the master boot record (MBR), the first 512 bytes of the hard disk.

The MBR contains GRUB stage 1. Given the small size of the MBR, Stage 1 does little more than load the next stage of GRUB (which may reside physically elsewhere on the disk). Stage 1 can either load Stage 2 directly, or it can load stage 1.5: GRUB Stage 1.5 is located in the first 30 kilobytes of hard disk immediately following the MBR. Stage 1.5 loads Stage 2.

When GRUB Stage 2 receives control, it presents an interface to the user in order to select which operating system to boot. This normally takes the form of a graphical menu, although if this is not available or the user wishes further control, GRUB has its own command prompt, where the user can manually specify the boot parameters. GRUB can also be set to automatically load a particular kernel after a timeout period.

Once boot options have been selected, GRUB loads the selected kernel into memory and passes control on to the kernel. At this stage GRUB can pass control of the boot process to another loader using chain loading if required by the operating system.[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)


[SIZE=2]**/boot**[/SIZE]

The **boot directory** is normally on the root ( / ) partition and contains, amongst other things, your kernel(s), [initrd (initial ram disk)]("http://www.ibm.com/developerworks/linux/library/l-initrd.html"), and grub (particularly menu.lst).

A separate **/boot partition** is required with GRUB if you use XFS, LVM, and/or encryption for your root partition. 

You can not share a /boot partition (the problem is that most distributions will overwrite your /boot partition when you install them).



[SIZE=4]**Partitioning :**[/SIZE]

In general I allocate 512 Mb for a boot partition (if needed), 5-10 Gb for the root partition ( / ), and a separate /data partition for user data (40 - 100 Gb).




[SIZE=4]**Sharing partitions :**[/SIZE]

**[COLOR=darkred]You can not share a /boot partition with multiple distros.[/COLOR]**

[SIZE=2]**Swap**[/SIZE]

Your swap partition can be shared between Linux distors and even BSD (you need only one swap). The problem may be that some distros will automatically format your swap space (during the installation), and if it is formatted, the UUID will change. In this event you will need to edit /etc/fstab (on any old OS) and update the uuid or mount swap using /dev/sdxy . *If you use /dev/sdxy you not need to update fstab if swap is formatted again during a future install*.  [How to fstab]("http://ubuntuforums.org/showthread.php?&t=283131").


[SIZE=2]**Conflicts with a shared /home**[/SIZE]

While the idea of sharing a /home partition may sound good, use caution in doing so. The potential problems include :

[LIST=1]
[*]A "rude" OS (or the wrong click of a mouse) may format or overwrite /home without asking permission first. Although rare these days, such rude behavior (or mistakes) will result in data loss.
[*]Your user is identified to the system by an id number (uid) and not a name. Ubuntu starts numbering users with 1000, but this is not standard. Fedora, for example, starts numbering users with 500. So even if your user name is the same on both Fedora and Ubuntu, you will have different uid. Because the uid are different you will no longer "own home".
[*]The other potential conflict is with your configuration or dot ( . ) files in /home. While you may be able to share these files in different versions of Ubuntu, you may have conflicts with other distros or varying versions of applications (gnome, gimp, etc.).
[/LIST]

This problem can be "solved" by using different user names with each distro, or better a /data partition.

[SIZE=2]**Shared /data partition.**[/SIZE]

I advise you make a shared data partition for data you wish to share across distros and leave /home (and the configuration files) on your root partition. You will likely still have permission problems, but this will eliminate conflicts with configuration files in a shared /home partition.

You can minimize permission problems while maintaining security by making a new group, say "data", and giving ownership of the data partition to root.data with permissions of 770.

**As with a shared home, be careful not to format or overwrite your /data partition.** (or add your data partition to /etc/fstab post-install).




[SIZE=4]**Install a new OS, manually configure GRUB :**[/SIZE]

Normally, when you install a new OS, you will re-install GRUB to the MBR and GRUB will now point to your new OS when loading Stage 1.5. Many times your new OS will find and automatically add your old OS to the grub menu. If not, you will need to manually edit /boot/grub/menu.lst and add in your old OS.

The "problem" with manually editing menu.list is that you will need to manually update the kernel line of the (GRUB) boot stanzas when you upgrade a kernel on the old OS.

A typical grub stanza looks like this:

> title           Ubuntu hardy (development branch), kernel 2.6.24-11-generic
root            (hd0,1)
kernel          /boot/**[COLOR=red]vmlinuz-2.6.24-11-generic[/COLOR]** root=UUID=b485ef35-1e30-4709-91
initrd          /boot/**[COLOR=red]initrd.img-2.6.24-11-generic[/COLOR]**
quietThe highlighted kernel and initrd need to be manually updated with each kernel update (Old OS only).

If you prefer to manually edit /boot/grub/menu.lst with each kernel update, you are done.

You can automate the process if you make use of chainloading (see next section).



[SIZE=4]**Automate maintenance of GRUB with Chain loading :**[/SIZE]


[COLOR=blue]This section is optional, but makes maintenance much easier.[/COLOR]

[color=darkgreen]**To automate maintenance, either chainload or configfile (not both).**[/color]

You probably think of chainloader as a method of booting Windows or BSD, but you can boot Linux via chainloading. 

> As the name implies, GRUB passes the control of the boot sequence to another bootloader, located on the device to which the menu entry points. This can be a Windows operating system, but also any other, including Linux.[INDENT][http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)[/INDENT]The advantage of chainloading includes :

[LIST=1]
[*]The stanzas in menu.lst are greatly simplified
[*]Each OS will automagically update menu.lst (in their respective /boot directories/partitions) and you will not need to manually update the boot stanzas when you upgrade a kernel.
[/LIST]

The "trick" is you need to install GRUB into your (target) root partition.

By far, the easiest way to do this is to install grub BOTH to the MBR and your root (or /boot) partition with each install.

You can manually install grub (as root) like this :

```
sudo grub

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)
grub> setup (hd0,1)
grub> quit
```_Note_: You will need to change (hd0,1) to your root partition (or boot partition if you use XFS, LVM, or encryption). ("setup (hd0)" at the grub prompt installs grub to the MBR).

This greatly simplifies your boot stanzas. For each old OS edit the boot stanza to look like this :> title Fedora 8
root (hd0,0)
chainloader +1
boot_Note_: Again change (hd0,0) to the appropriate (Fedora) root partition (or boot partition if you used the Fedora defaults and set up a LVM).


[SIZE=2]**Configure GRUB (on your old, chainloaded OS)**[/SIZE]

Now when you boot, if you select your new OS, if you select the new OS on the grub screen it will boot directly into the new OS.

If you select an old OS, however, you will get a second grub screen. Select the old OS a second time.

If it is working, you can set the grub defaults for the old OS. First boot the old OS and edit the /boot/grub/menu.lst.

You will want to make sure the "default" is 0 and set the "time out" to 0.

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default         0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout         1**After these changes, when you boot the old OS you will see the second GRUB screen for 1 second (this allows you to select recovery mode if needed).

When you upgrade the old OS to a new kernel the second (chain loaded) GRUB will automatically be updated and no manual edit is needed.




======================


[SIZE=4]**Example: **[/SIZE]

Imagine dual booting Fedora and Ubuntu with the following partitions:[INDENT]/dev/sda1 = boot partition (for Fedora)

/dev/sda2 = LVM = Fedora root ( /)

/dev/sda3 = Ubuntu root (this partition contains the boot directory for Ubuntu).

/dev/sda4 = swap[/INDENT]Walk-through: 

[LIST=1]
[*]Lets start by installing Fedora first, using LVM and thus /dev/sda1 as the Fedora /boot.
[*]Next, from the Fedora live CD, install GRUB into /dev/sda1 (Fedora /boot)
> su

root@fedora# grub



grub > root (hd0,0)
grub > setup (hd0,0)
grub > quit
[*]Now boot and install Ubuntu to /dev/sda3
[*]Again, from the Ubuntu live CD, install grub to /dev/sda3[INDENT]_Note_: This step is not needed at this time, but sets up the Ubuntu OS to be chainloaded if a third OS is installed later.[/INDENT]
[*]Post install boot Ubuntu. Edit /boot/grub/menu.lst to chainload Fedora
> title Fedora 8
root (hd0,0)  **<-- Note Fedora /boot partition**
chainloader +1
boot
[*]Boot Fedora and modify /boot/grub/menu.lst, change the time out to 1
[/LIST]

=====================

[SIZE=4]**Automate maintenance of GRUB with configfile :**[/SIZE]

[COLOR=blue]This section is optional and also makes maintenance much easier.[/COLOR]

[color=darkgreen]**To automate maintenance, either chainload or configfile (not both).**[/color]

I recently learned of this option and IMO it is by far the easiest method. It is similar to chainloading (which is why I left chainloading first), but takes a single line in /boot/grub/menu.lst.

A sample entry looks like : 

```
title        Ubuntu 8.04
configfile   (hd0,0)/boot/grub/menu.lst

title        Fedora 9
configfile   (hd0,1)/boot/grub/menu.lst
```

Caveats : 
[list][*]grub must be installed in the target partition (hd0,1) and (hd0,1) in the above example.
[*]/boot/grub/menu.lst must exist in the target partition.
[*]/boot/grub/menu.lst in the *target partition* must boot the kernel, ie the boot stanza must list vmlinuz and initrd, like this :
```
title Ubuntu hardy 8.04
kernel /boot/vmlinuz-2.6.24-11-generic root=UUID=b485ef35-1e30-4709-91
initrd /boot/initrd.img-2.6.24-11-generic
quiet
```[/list]

Reference : [http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

==================

Next install as many OS as you like, always installing grub into the root ( / ) partition (or /boot partition) of each OS.

Hope this helps making multi-booting a little easier.

[FONT=times][SIZE=4]*Peace be with you,*[/SIZE][/FONT][I]

[IMG]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/IMG][SIZE=4] [COLOR=navy][FONT=times]bodhi.[/FONT][/COLOR][FONT=times][COLOR=darkgray]zazen[/COLOR][/FONT][/SIZE][/I]

---

### Post by Shazaam on 2008-03-15
To add a little tidbit you can also use the same procedure with a virtualized multi-boot if you need the space.

---

### Post by kushykush on 2008-04-02
Bodhi:  The guidance provided by you is too advanced. Could you or someone on this forum provide guidance as to how a newbie could install multiple operating systems?  Here is my scenario:

I have two Sata drives. Vista is on first drive (sda 0,0) which has three partitions.

Ubuntu is on the second Sata drive with its Swap and other partitions. 

Ubuntu installed the GRUB correctly (I do not know where).  The GRUB menu list displays Ubuntu and Windows/longhorn and gives me the option to boot either.

Now, I want to install SUSE (and then Fedora) alongside Ubuntu on the second Sata drive.  What do I do?

I want to leave Vista untouched on the first (0,0) mainly because I do not want anything to happen to it.  Ideally, I would like to install Vista, Ubuntu, Suse and Fedora on the first drive.  But I do not know how to chain install. 

When I go through the SUSE installation CD, it insists on deleting  the Vista partition(s).  When I direct it to one of the empty partitions along side Vista on the first Sata,  it gives me error that it cannot find the root (/) and the boot -- mounts,

When I try to install SUSE on the second Sata (which is currently occupied by Ubuntu), it insists on deleting Ubuntu's partitions.

If I understand the guidance above, what you are saying is that Suse, for example, cannot be installed along side Ubuntu using the usual SUSE install disc?  The only way out is installing it manually?

Before I started to install Ubuntu on my second sata (160 gigs) I had created three partitions in the hope that I will install Ubuntu, Suse and Fedora.  

I started with my favorite Ubuntu.  However, I could not install Ubuntu on the 50 gig partition that I had created because it kept asking me for the root partition and there was nothing in the graphic install program that gave me any guidance as to how that can be done.   Finally, I just did a "guided" install.  The result was Ubuntu wiped out the other two partitions and now occupies all of my second drive. 

Could you please, once again, try to provide guidance in understandable terms or direct me to relevant links?

---

### Post by bodhi.zazen on 2008-04-02
> **kushykush said:**
> Bodhi:  The guidance provided by you is too advanced. Could you or someone on this forum provide guidance as to how a newbie could install multiple operating systems?

LOL Multibooting is moderately complex. If you do not understand what you are doing that is an indication to stop and do some additional reading.

You need to understand basic partitioning, and how both grub and linux refer to partitons.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Next you need to understand how grub works. IMO the easiest is to use chainloader, as outlined above, as that will automate the process greatly.

I advise you re-read my how-to and ask specific questions about what you do not understand. I (or others) can try to explain it better and I can update the how to if needed.

If you like, here is another link using grub and chainloader to boot up to 145 OS:

[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

The other option, of course, it to install away and hope it works (usually it does). You will likely need to sort out a number of pieces with this approach including how to manually update grub with kernel updates and adding grub entries for OS that are not automatically configured at installation of a new OS.

Best grub guide : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)


> Here is my scenario:

I have two Sata drives. Vista is on first drive (sda 0,0) which has three partitions.

Ubuntu is on the second Sata drive with its Swap and other partitions. 

Ubuntu installed the GRUB correctly (I do not know where).  The GRUB menu list displays Ubuntu and Windows/longhorn and gives me the option to boot either.

Grub is installed into your MBR (the start of you first hard drive) and refers you your Ubuntu partition (? on your second hard drive) for stage 1.5 -> stage 2 (stage 2 is the graphical screen where you select which OS to boot). If you select Windows grub uses chainloader to pass the boot process to the Windows boot loader. If you boot Ubuntu grub continues with vmlinux and initrd in /boot on your Ubuntu partition.

> Now, I want to install SUSE (and then Fedora) alongside Ubuntu on the second Sata drive.  What do I do?

I want to leave Vista untouched on the first (0,0) mainly because I do not want anything to happen to it.  Ideally, I would like to install Vista, Ubuntu, Suse and Fedora on the first drive.  But I do not know how to chain install. 

When I go through the SUSE installation CD, it insists on deleting  the Vista partition(s).  When I direct it to one of the empty partitions along side Vista on the first Sata,  it gives me error that it cannot find the root (/) and the boot -- mounts,

When I try to install SUSE on the second Sata (which is currently occupied by Ubuntu), it insists on deleting Ubuntu's partitions.

If I understand the guidance above, what you are saying is that Suse, for example, cannot be installed along side Ubuntu using the usual SUSE install disc?  The only way out is installing it manually?

It should all be doable, it sounds like a problem with either the SUSE installer or possibly your understanding of how to proceed with installing using manual (custom) partitioning (hard to know). It has been a while since I installed SUSE, you will need to understand and use the manual partitioning option (I know SUSE can be installed as you describe as I have done it before). If that fails, I advise you ask for advice on the SUSE forums.

> Before I started to install Ubuntu on my second sata (160 gigs) I had created three partitions in the hope that I will install Ubuntu, Suse and Fedora.  

I started with my favorite Ubuntu.  However, I could not install Ubuntu on the 50 gig partition that I had created because it kept asking me for the root partition and there was nothing in the graphic install program that gave me any guidance as to how that can be done.   Finally, I just did a "guided" install.  The result was Ubuntu wiped out the other two partitions and now occupies all of my second drive. 

Could you please, once again, try to provide guidance in understandable terms or direct me to relevant links?

I assume Ubutnu boots ? If so, it should all work out just fine. If not, then you likely have an issue with your BIOS. Bios is variable, confirm that the second hard drive is recognized by the bios and at least one partition is flagged ab bootable (I do this with fdisk)

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

So again my best advice is to step back and do a little prep work. Again, if you get stuck feel free to ask questions, the more specific the question the better we can assist you.

As an aside, personally I give each OS 10 Gb for the root partition and use a larger shared data partition.

---

### Post by eMxyzptlk on 2008-04-02
> **bodhi.zazen said:**
> [size=4]**Sharing partitions ::**[/size]

**[color=darkred]You can not share a /boot partition with multiple distros.[/color]**


That's not true dude, you can share /boot partition, you just need to know how to do it, I share one /boot between all the distros I use, in each distro I mount the boot partition to /common-boot and I have /boot a symlink pointing to /common-boot/DISTRO with one shared grub under /common-boot/grub, of course mounting to /boot would work perfectly though you'll end up with many files and you probably won't tell which one belongs to which distro :)

I have 2 Linux ( Gentoo/Ubuntu ), One Windows, one Mac os X and on external hdds I have Solaris and FreeBSD all working fine :)

---

### Post by bodhi.zazen on 2008-04-03
> **eMxyzptlk said:**
> That's not true dude, you can share /boot partition, you just need to know how to do it, I share one /boot between all the distros I use, in each distro I mount the boot partition to /common-boot and I have /boot a symlink pointing to /common-boot/DISTRO with one shared grub under /common-boot/grub, of course mounting to /boot would work perfectly though you'll end up with many files and you probably won't tell which one belongs to which distro :)

I have 2 Linux ( Gentoo/Ubuntu ), One Windows, one Mac os X and on external hdds I have Solaris and FreeBSD all working fine :)

I am glad you found a system that works for you (and it is a neat work-around), but

/common-boot != /boot

As a general warning (to others), if you create a partition and, during the installation(s), mount it at /boot there is a high chance it will be formatted and overwritten when you mount it as /boot during your second installation. This will leave your first installation un-bootable.

I know it is a matter of syntax, but I would not call your method a shared /boot partition. As I have tried to warn you, mounting a shared partition at /boot will not work so smoothly.

---

### Post by kushykush on 2008-04-03
OK Bodhi here is some more specificity:

1. What program should I use to create partitions. Gparted does not work from inside Ubuntu.  Therefore, should I get it on a disc or USB?

2. Assuming I am successful in creating two more partitions on my second drive (where Ubuntu resides), how do I begin the installation?  Ubuntu, presumably, already has a boot and swap partition.  So what do I do on the new partitions?

3. Installing Suse and Fedora:  I have these on DVD.  Is there another manual way of installing these OSs?  Because if I follow the OS installers, they do not let me create /, boot, or a swap.  That is my main dilemma. How do you finally install these OSs on the new partitions?

As said I had three, roughly equal, partitions on my second drive.  But when I started to install Ubuntu, it's install program wiped out my partitions.  I could not (or did not know) how to create the / and swap on the first partition.

Plus, keep in mind that Vista is already installed on the first drive's first partition and Ubuntu on the second drive.  Right now Ubuntu's GRUB is working fine as it lets me boot Vista.

If I understand you correctly, I should somehow install Suse and Fedora (after creating new partitions for them) and later do manual manipulation with GRUB.  My only fear there is that nothing will boot so there will be nothing to manipulate.  Unlike Ubuntu, both Suse and Fedora messed up my Vista installation and failed to boot from the hard drive.  

That is the challenge.  Keep Vista and Ubuntu working while venturing to install Suse and Fedora without ending up having no boot. Or worse ending up having my boot loader completely destroyed.

I know Bodhi, you have the solution.  However, anyone is welcome to help and lead me through this process.  I promise if I make it, I will write a step by step easy to understand procedures for multi operating system machines.

---

### Post by bodhi.zazen on 2008-04-04
Sorry for the delayed response.

I think the main problem you have is that you need to set up your partitions (with gparted or fdisk) before you start the installer.

I advise gparted, it is a common tool and will allow you to resize your Ubuntu partitions.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

So ...

1. Boot a live CD (you can not resize ubuntu while running from the hard drive). In general partitions should be managed from a live CD.

2. Unmount all hard drive partitions (including swap).

3. Resize your ubuntu root partition to make additional space.

4. In general, 5-10 Gb is sufficient for your root partitions. So make 3 - 10 Gb partitions, one for Ubuntu (resized), one for SUSE, and one for Fedora. 
[list][*]You can share swap, so make swap = RAM X 2, max 1 Gb or swap = RAM if you have a laptop and wish to suspend / sleep).[/list]

5. The complexity here will be Fedora. By default, fedora will want an additional partition for /boot (Fedora uses LVM). So make a 512 Mb partition for fedora /boot

6. Make a large partition for shared data. You should use ext3 and can share this space with ubuntu, fedora, suse, and windows.

7. After making all these changes you may need to update Ubuntu /boot/grub/menu.lst and /etc/fstab (with your partition changes). Here is a thread that shows the issues : 

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

8. Reboot to hard drive, boot Ubuntu, save /boot/grub/menu.lst to your shared data partition for referance (in case you can not boot windows). Install grub to the Ubuntu root partition.

9. Boot SUSE , start the installer, install using manual partitioning, mount the target root partition as / , swap as swap, and the data partition as what you wish (/mdeia/data). Install grub to the suse root partition (after installing suse).

10. Boot Fedora, install as above (don't forget the boot partition as /boot).

11. Boot Fedora, edit /boot/grub/menu.lst

Make sure the Windows stanza is "OK" (same as the Ubuntu stanza for windows).

Then use these stanzas for Ubuntu / suse (make sure you replace "(hdx,y)" with the correct root partition in grub terminology):

title SUSE
root (hdx,y)
chainloader +1 
boot

title Ubuntu
root (hdx,y)
chainloader +1 
boot

If at any point your swap partition is formatted you may to update /etc/fstab for your previously installed distros. The UUID changes if the partition is formatted and many distros mount with UUID=xxx.yyy.zzz in fstab. Use /dev/sdxy and you will not have this problem.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

If at any point you can no longer boot Windows or Ubuntu, it would be a matter of configuring grub and you can refer to the back up copy of /boot/grub/menu.lst you saved earlier. Installing additional OS, **as long as you do not format old partitions**, will not cause you to "loose" windows or ubuntu.

---

### Post by Herbert_Vaucanson on 2008-04-22
Hallo Bodhi,

thanks for the nice howto. I am planning to reinstall the OSes on my PC soon, and your guide comes handy.

I have already checked some other ones on the net, but no-one is really tackling all the issues. Yours is good and easier to understand than most (after some pain with the partitioning basics), so I would like to ask you a couple of questions.

1) somewhere I read about the possibility of installing GRUB in a partition of his own, OS-agnostic and thusly independent of OS reinstalls: I like to reintall from time to time, and everything that makes it easier is a Godsend to me.
Have you experience/suggestions/opinions on this? I was planning to make a GRUB partition of 100MByte and mount it as /GRUB on my Linuxes (Ubuntu and Gentoo). Whenever I reinstall Windows, the MBR will be brutalized and GRUB will be in need of a reinstall. Can I do it from any Linux release I fancy, independently from the one I choose the previous time? (I plan to follow your advice and chainload my grandma, too)

2) I have a fakeraid setup: southbridge Intel ICH9r, 2 SATA2 drives on mirroring. I know that Linux sotware raid is better but I just want a brute disk mirroring working from Windows, too.
I managed to dual-boot Windows and Gentoo from it, but after the reinstall Ubuntu will be in, too.
Do you recon I will have problems? How is the situation with hardware support on Ubuntu installation disks?

---

### Post by bodhi.zazen on 2008-04-22
To keep this thread on topic I will first comment on a dedicated grub partition. This is very easy to accomplish, but a little terminology may help.

Lets start with a /boot partition. A /boot partition contains grub and your various kernel(s) and [initrd](http://www.ibm.com/developerworks/linux/library/l-initrd.html) , everything you need to boot your linux distro.

If you want to have a dedicated grub partition, make a small partition ( 1 Gb is overkill here), install grub into it, but NOT the kernel or initrd. DO NOT mount the grub partition as a /boot partition (Each distro continues to maintain unique /boot partitions, typically on the root ( / ) partition). The grub partition will have (grub) stage 1.5, stage 2,and a menu.lst. You will need to continue to edit and update the menu.lst (on the grub partition) as you add/remove distros.

Now you can either manually maintain the kernel/initrd in the boot stanzas :

> title Ubuntu hardy (development branch), kernel 2.6.24-11-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-11-generic root=UUID=b485ef35-1e30-4709-91
initrd /boot/initrd.img-2.6.24-11-generic
quiet

Or go with chainloader, as outlined above :

> title Ubuntu hardy
root (hd0,2)
chainloader +1

So that "anatomy" if you will, is as follows. Assume your grub partition is /dev/sda1 or (hd0,0). Your MBR starts the boot process and then passes off to the grub partition where you get a grub menu and select which distro to boot. To set up your MBR (after grub is installed in your grub partition):

With a live CD :

```
sudo grub
```

At the grub prompt :

```
grub > root (hd0,0)
grub > setup (hd0)
```

Now as you install distros :
[list=number][*]First, DO NOT use the grub partition as /boot.
[*]Second DO NOT install grub into the MBR (as you install your distros). If you do, you will need to restore grub. This is the biggest potential "problem" is that some distros will install grub into the MBR without asking permission :rolleyes:.
[indent]Or worse, windows will overwrite your MBR.[/indent]
[*]After you install a distro:[list][*]Restore grub if needed.[*]Mount your grub partition, edit menu.lst, and add the new distro, either manually adding kernel and initrd info or chaninloading as you prefer.[/list][/list]



HTH. Here are a few links for reference :

[Making a Dedicated Grub Partition](http://www.troubleshooters.com/linux/grub/grubpartition.htm)
[Multiboot with GRUB Mini-HOWTO](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

As to fakeraid, I am not sure. I would assume you will need a /boot partition outside of the raid and that setting up Ubuntu would be similar to Gentoo. You may wish to search these forums or start a new thread.

---

### Post by kk0sse54 on 2008-05-08
Quick question I have ubuntu and xp set up as a dual boot but i want to also create a new partition for Mandriva. If i just install Mandriva the normal way on a separate partition and reinstall GRUB and just manually update the list each time I do a kernel update that should be fine right?

---

### Post by bodhi.zazen on 2008-05-08
> **C!oud said:**
> Quick question I have ubuntu and xp set up as a dual boot but i want to also create a new partition for Mandriva. If i just install Mandriva the normal way on a separate partition and reinstall GRUB and just manually update the list each time I do a kernel update that should be fine right?

Should work just fine. Worse case secenario you may need to copy the Windows and Ubuntu stanzas from Ubuntu /boot/grub/menu.lst to Mandriva /boot/grub/menu.lst, but I think the Mandriva installer is reasonably reliable and should do this for you. If you elect not to chainload, you will have to manually update the Ubuntu kernel line in Mandirva /boot/grub/menu.lst , if that makse sense ...

---

### Post by Dedoimedo on 2008-05-09
Hi,

Cloud, I would suggest you backup your Ubuntu GRUB, just in case. Whenever you think of modifying the GRUB, installing new distros, changing partition size etc, it's always a good idea to backup.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

Cheers,
Dedoimedo

---

### Post by kk0sse54 on 2008-05-09
sweet thanks :)

---

### Post by kk0sse54 on 2008-05-16
Another question here for future reference. I know what needs to be done to manually update GRUB and I know how but is there a terminal command that will show me the new kernel I just downloaded and installed so that I will be able to update the GRUB list correctly?

---

### Post by bodhi.zazen on 2008-05-16
```
ls /boot | grep vmlinuz
```

---

### Post by unutbu on 2008-05-20
bodhi.zazen, thank you for writing this tutorial!

Would you please take a look at [klaasvanschelven's method]("http://ubuntuforums.org/showpost.php?p=4864395&postcount=15")?

The main difference is that configfile lines in menu.lst take the place of chainloader +1 commands.
This allows you to avoid having to install GRUB on every OS partition.
The menu.lst on the dedicated grub partition hands off to other OS's menu.lst this way:
```
title        Ubuntu Gusty Gibbon
configfile   (hd0,7)/boot/grub/menu.lst

title        Ubuntu Hardy Heron
configfile   (hd0,8)/boot/grub/menu.lst
```

His placement of the /home partition to the left of (before) the OS's allows new OS's to be added neatly so you end up with 

```
GRUB partition
home partition
...
OS3 partition
OS2 partition
OS1 partition
swap
```

Cons to klaasvanschelven's method:
1) Adding a new OS partition will change GRUB's numbering for all the partitions after it. So adding a new OS would mean having to update menu.lst in a number of places. The only way to avoid this (that I see) is to always add new partitions to the right of all other partitions, but that is not going to work for very long since you would have to always to make the right-most partition your largest partition to give it the ability to be shrunk to make room for the next OS. Most people want /home to be big, not the latest OS... So maybe klaasvanschelven's arrangement is as good as it can get. 

2) He uses a commonly shared /home partition, I see now from this thread that there can be problems with that. However, this is easily fixed. As you already mentioned, just share a /data partition, not /homes.

---

### Post by bodhi.zazen on 2008-05-23
> **unutbu said:**
> bodhi.zazen, thank you for writing this tutorial!

Would you please take a look at [klaasvanschelven's method]("http://ubuntuforums.org/showpost.php?p=4864395&postcount=15")?

The main difference is that configfile lines in menu.lst take the place of chainloader +1 commands.
This allows you to avoid having to install GRUB on every OS partition.

<clip>



Thanks for the comments unutbu. I added the information to my tutorial.

My comments are that :

1. Yes, grub must be installed in the target partition. If you look at [klaasvanschelven's post](http://ubuntuforums.org/showpost.php?p=4864395&postcount=15) grub is installed in the target partition:

> after this, mount sda8 and sda6. I then just copied the whole grub directory (from /boot/grub) to sda6. (sudo cp -R /mnt/sda8/boot/grub /mnt/sda6 )

I then replaced the menu section in the menu.lst (on sda6!) by this: ...

In this case klaasvanschelven installed grub by copying the the grub directory and then manually updating it.

2. Your comments re: partition numbering, both with grub (hd0,0) and linux /dev/sda1 are right on target. That is why I listed "things you should already know".

---

### Post by adrian15 on 2008-05-27
> **bodhi.zazen said:**
> [CENTER]How to Multi-boot (Maintain more then 2 OS)[/CENTER]


Hi bodhi.zazen, you might be interested to update your multiboot howto in the linux part with the Super Grub Disk method:

[Multi Distribution Boot Howto](http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto)

adrian15

---

### Post by logos34 on 2008-07-08
Why didn't you include 'symlink' method?  It directly boots the most recent kernel via the symbolic link in / or /boot, bypassing menu.lst altogether.  No second menu.lst, hence no need to adjust the 'timeout' and 'hiddenmenu' option of each OS.  I use it a lot.

Also, to avoid confusion you might want to distinguish between installing Grub in a partition (i.e. the grub folder with kernel images, menu.lst, various stage files, etc.) vs. writing the Grub **IPL** code to the first/boot sector of the / (or separate /boot) partition:

Your statement in the configfile section:

> Caveats :

    * grub must be installed in the target partition (hd0,1) and (hd0,1) in the above example.


initially confused me (and perhaps also another poster, [unutbu]("http://ubuntuforums.org/showpost.php?p=5003319&postcount=17")) because I thought you were referring to the chainloader requirements ("in" and "into" the "target" partition):

> The "trick" is you need to install GRUB into your (target) root partition.

By far, the easiest way to do this is to install grub BOTH to the MBR and your root (or /boot) partition with each install.

I know you didn't mean to imply that, since the configfile method grabs the menu.lst directly and does not require the Grub IPL to be written to the / or /boot partition -- only the chainloader approach needs it.  But it might be clarified by rewording.  (On the other hand, it won't hurt to write the grub IPL to every partition)

---

### Post by rlgoddard on 2008-07-15
Ok, having read through this thread, what I am wanting to accomplish is the following:

1)  A unified menu.lst for booting to any Linux OS.
2)  No submenus

I have Kubuntu on sda5, and I just installed openSUSE 11.0 on sda6.  The problem is that openSUSE took over the menu.lst and added Kubuntu as a submenu.  How do I create a unified menu.lst for all OS's (I plan to add up to two more later on sda7 and sda8) and where do I edit this?

Thanks for any advice you may have and take care,
Russ

---

### Post by unutbu on 2008-07-15
Let's say you want the menu.lst on sda5 (Kubuntu) to be your unified menu.lst

(1) Boot into Kubuntu. Edit sda5's menu.lst:
```

gksu gedit /boot/grub/menu.lst
```

Add this to your boot stanzas (about 2/3 of the way down the file)
```

title openSUSE
root (hd0,5)
chainloader +1
boot

```
(2) Boot into openSUSE. Edit sda6's menu.lst

```
gksu gedit /boot/grub/menu.lst
```

Make sure you have these settings near the top:
```
default		0
timeout		1       
hiddenmenu
```

"default 0" makes your first boot stanza the default
"timeout 1" makes GRUB wait 1 second before booting the default boot stanza. During that 1 second you can press ESC to get to the GRUB menu -- a useful feature when things go wrong. I suppose you could change it to 0 if everything is working properly however. 
"hiddenmenu" will achieve the "no submenu" effect.

(3) Reinstall GRUB on the MBR so that it will load sda5's menu.lst:

Boot from a LiveCD
```

sudo grub
grub> root (hd0,4)
grub> setup (hd0)          # Writes to the MBR

```
With the above two commands, your boot sequence will read sda5's menu.lst.
```

grub> root (hd0,5)         
grub> setup (hd0,5)        # Writes GRUB to the sda6 partition
grub> quit
```

"setup (hd0,5)" allows the chainloader command to work. When you select openSUSE from sda5's menu.lst, it will hand off to the GRUB you installed on (hd0,5).

(hd0,4) is GRUB-talk for /dev/sda5
(hd0,5) is GRUB-talk for /dev/sda6
(hd0) is GRUB-talk for the sda hard drive

Reboot.

---

### Post by bodhi.zazen on 2008-07-15
> **rlgoddard said:**
> Ok, having read through this thread, what I am wanting to accomplish is the following:

1)  A unified menu.lst for booting to any Linux OS.
2)  No submenus

I have Kubuntu on sda5, and I just installed openSUSE 11.0 on sda6.  The problem is that openSUSE took over the menu.lst and added Kubuntu as a submenu.  How do I create a unified menu.lst for all OS's (I plan to add up to two more later on sda7 and sda8) and where do I edit this?

Thanks for any advice you may have and take care,
Russ

If you would like a "single" menu.lst you need to follow the "manual" method in my first post.

One distro will be the "master" or root, usually the last one installed. Usually the installers of most distros will recognize and add others, but if not you will need to manually edit menu.lst.

The stanzas read :

title Distro
root (hdx,y)
kernel /boot/vmlinuz-xyz root=abc ro splash quiet
initrd /boot/initrd-xyz
boot

The "problem" with this method is you will need to manually update the kernel and initrd lines with each kernel update ...

The "solution" to that problem is to either chainload or use the configfile option. Both solutions are essentially the same in that they pass off the booting process to a new root partition.

Once it is all working, see unutbu's post re: configuring the second menu to be as seamless as possible.

Other then that, do you have a specific question ?

---

### Post by rlgoddard on 2008-07-15
> If you would like a "single" menu.lst you need to follow the "manual" method in my first post.

One distro will be the "master" or root, usually the last one installed. Usually the installers of most distros will recognize and add others, but if not you will need to manually edit menu.lst.

The stanzas read :

title Distro
root (hdx,y)
kernel /boot/vmlinuz-xyz root=abc ro splash quiet
initrd /boot/initrd-xyz
bootI want Kubuntu to be the "master" distro.  With the above example, do I add:
```

title Kubuntu
root (hd 0,4)
kernel /boot/vmlinuz-xyz root=abc ro splash quiet
initrd /boot/initrd-xyz
boot

```to Kubuntu's menu.lst?

> The "solution" to that problem is to either chainload or use the configfile option. Both solutions are essentially the same in that they pass off the booting process to a new root partition.
So, do I add:

```
title openSUSE
root (hd0,5)
chainloader +1
boot
```to Kubuntu's menu.lst to pass it on to openSUSE if I select that option?

Thanks and take care,
Russ

---

### Post by bodhi.zazen on 2008-07-15
> **rlgoddard said:**
> I want Kubuntu to be the "master" distro.  With the above example, do I add:
```

title Kubuntu
root (hd 0,4)
kernel /boot/vmlinuz-xyz root=abc ro splash quiet
initrd /boot/initrd-xyz
boot

```to Kubuntu's menu.lst?

First, there is no need to add an entry for Kubuntu in kubuntu's /boot/grub/menu.lst

Second, but you must manually fill in the kernel and initrd numbers (you can not use "xyz" or "abc", you must specify the kernel, initrd, and root partition). Then you must update the kernel and initrd with each kernel update

> So, do I add:

```
title openSUSE
root (hd0,5)
chainloader +1
boot
```to Kubuntu's menu.lst to pass it on to openSUSE if I select that option?

Thanks and take care,
RussThat works so long as grub has been installed / setup in the opensuse partition.

You can also :

```
title OpenSUSE
configfile (hd0,5)/boot/grub/menu.lst
```

---

### Post by rlgoddard on 2008-07-16
> **bodhi.zazen said:**
> First, there is no need to add an entry for Kubuntu in kubuntu's /boot/grub/menu.lst

Second, but you must manually fill in the kernel and initrd numbers (you can not use "xyz" or "abc", you must specify the kernel, initrd, and root partition). Then you must update the kernel and initrd with each kernel update

So, all I need to do is add openSUSE's entry into Kubuntu's menu.lst and then follow unutbu's earlier post?  Because the kernel and everything is already defined in Kubuntu's menu.lst.

Also, which distro needs their entry manually edited to reflect the update in the kernel?  Kubuntu or openSUSE?

Take care,
Russ

---

### Post by bodhi.zazen on 2008-07-16
Sounds like it is working then ?

With your current set up, you will need to update OpenSUSE with any and all kernel updates.

---

### Post by rlgoddard on 2008-07-16
> **unutbu said:**
> 
```

grub> root (hd0,5)         
grub> setup (hd0,5)        # Writes GRUB to the sda6 partition
grub> quit
```

setup (hd0,5) fails with an error message.  Can't remember the exact wording, but it complained about not finding stage 1 on (hd0,5).  Consequently, chainload or configfile fails.

Take care,
Russ

EDIT:  Never mind... I re-ran setup (hd0,5) and it works.  Curiously, chainloader works, but not configfile.

---

### Post by unutbu on 2008-07-16
Just out of curiosity, when you boot into openSUSE,
what is the path to menu.lst?
Is it /boot/grub/menu.lst, or something else?

---

### Post by rlgoddard on 2008-07-16
> **unutbu said:**
> Just out of curiosity, when you boot into openSUSE,
what is the path to menu.lst?
Is it /boot/grub/menu.lst, or something else?
Yup, you got the path correct.

---

### Post by unutbu on 2008-07-16
Well, I'm flummoxed why configfile did not work, but I'm glad you got the system to work anyway!

---

### Post by Browser_ice on 2008-11-02
In wanting to change my current existing multi-boot, I have encountered a grub error 13.

What I currently have:
Windows XP on sda0
Ubuntu 8.04 for personnal usages on sda5
Ubuntu 8.04 for office remote sages on sda6
Fedora 9 on sda7

The main grub being used for booting is on sda6. I was able to boot to anyone before.

> 
 /boot/grub>sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28842883

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        9963    69545385    f  W95 Ext'd (LBA)
/dev/sda5            1306        3916    20972826   83  Linux
/dev/sda6            3917        6940    24290248+  83  Linux
/dev/sda7            6941        9963    24282216   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000782bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         522     4192933+  82  Linux swap / Solaris
/dev/sdb2             523        4439    31457280+   7  HPFS/NTFS
/dev/sdb3            4440       10965    52420095    b  W95 FAT32
/dev/sdb4           10966       30515   157035375    f  W95 Ext'd (LBA)
/dev/sdb5           10966       14098    25165791    7  HPFS/NTFS
/dev/sdb6           14099       17231    25165791   83  Linux
/dev/sdb7           17232       20491    26185918+  83  Linux
/dev/sdb8           27012       30271    26185918+  83  Linux
/dev/sdb9           30272       30515     1959898+   7  HPFS/NTFS


What I did was change the sda6 grub to :
> title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		 Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01d6cb68-7d80-4bb1-aec0-687034dc8569 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Personnal Ubuntu 8.04.1 (on /dev/sda5)
root		(hd0,4)
chainloader	+1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Fedora (on /dev/sda7)
root		(hd0,6)
chainloader	+1

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

title		 Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode, /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=01d6cb68-7d80-4bb1-aec0-687034dc8569 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

Change the sda5 grub to :
> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c02cec2-58d0-4451-a145-111e40fb2129 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c02cec2-58d0-4451-a145-111e40fb2129 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

And change the sda7 grub to :
> default=0
timeout=2
splashimage=(hd0,8)/boot/grub/splash.xpm.gz
hiddenmenu
title Open Client Fedora 2.20 (Daily) (2.6.25.14-108.fc9.i686)
	root (hd0,8)
	kernel /boot/vmlinuz-2.6.25.14-108.fc9.i686 ro root=UUID=a1a770f9-dfee-4f20-9ef3-432c7da42de6 rhgb quiet
	initrd /boot/initrd-2.6.25.14-108.fc9.i686.img

title Open Client Fedora 2.20 (Daily) (2.6.25.11-97.fc9.i686)
	root (hd0,8)
	kernel /boot/vmlinuz-2.6.25.11-97.fc9.i686 ro root=UUID=a1a770f9-dfee-4f20-9ef3-432c7da42de6 rhgb quiet
	initrd /boot/initrd-2.6.25.11-97.fc9.i686.img



Now what is happening is that I am able to boot to Windows and my sda6 Ubuntu, but when I choose my sda5 ubuntu or sda7 fedora, I get an error 13.

Do I have to write those grub to my sda5 & sda7 ?

**==>> I updated the grubs on those sda5 & sda7 and it now works.**

---

### Post by constantinos1987 on 2008-12-15
Just a question from an inexperienced linux user. I hope it isn't already answered, but I searched and found nothing.

Can one create a dedicated grub partition right from the install? I mean, when you enter the partitioning options, can you create a partition ( something like 10MB of ext2/3 ) with a mount point /boot/grub and install grub there? I think that this way, this partition could be overwritten -if we are sure that the distribution to be installed recognizes all the other operating systems on the hard drives, else we just edit the menu.conf- when you install another distribution because /boot/grub (for all I know) doesn't contain any kernel images, but /boot does. 

I am aware of the tutorial to make a dedicated grub partition. But it instructs to do this after the install. But I would like an XFS filesystem and installing first means that I will need a filesystem compatible with grub and XFS is not. 

Is there any way to do this? It could prove helpful to me :D

---

### Post by unutbu on 2008-12-15
Yes, it is possible to create a dedicated grub partition right from the install:
[list]
[*]When you get to step 4 of the install (entitled "Prepare partitions"), select "Manual" instead of "Guided". 
[*]Use the partition editor to create a 10MB partition at the beginning of your hard disk.
(A grub partition at the beginning of the HD avoids any BIOS address limitations.)

[*]With the 10MB partition selected, click the "Edit" button. 
[*]Select "ext3" for the type of filesystem. 
[*]Below that you will be asked to select a mount point. There is a pull-down menu. But instead of selecting something from the pull-down menu, simply type in /boot/grub.
[/list]

> 
I am aware of the tutorial to make a dedicated grub partition. But it instructs to do this after the install.

It is also possible to partition your hard drive **before** you install: Boot from the LiveCD, go to the Live desktop, click System>Admin>Partition Editor (GParted).

---

### Post by bodhi.zazen on 2008-12-15
> **constantinos1987 said:**
> Just a question from an inexperienced linux user. I hope it isn't already answered, but I searched and found nothing.

Can one create a dedicated grub partition right from the install? I mean, when you enter the partitioning options, can you create a partition ( something like 10MB of ext2/3 ) with a mount point /boot/grub and install grub there? I think that this way, this partition could be overwritten -if we are sure that the distribution to be installed recognizes all the other operating systems on the hard drives, else we just edit the menu.conf- when you install another distribution because /boot/grub (for all I know) doesn't contain any kernel images, but /boot does. 

I am aware of the tutorial to make a dedicated grub partition. But it instructs to do this after the install. But I would like an XFS filesystem and installing first means that I will need a filesystem compatible with grub and XFS is not. 

Is there any way to do this? It could prove helpful to me :D

Well, you need a dedicated boot partition if you wish to use XFS. The grub directory is part of the boot directory, so I seriously doubt you can not split the /boot/grub into xfs with /boot on ext2.

Most people use ext2 for /boot which is likely just fine.

My last warning, you need to take great care with your /boot partition. If you install a new OS and mount this partition at /boot , the new installation will over write everything in /boot

---

### Post by undoIT on 2008-12-30
I have a laptop hard drive and have installed seven different distros. The first primary partition is for grub and I am able to boot to all the distros. The second partition is swap. The third partition is an extended partition and each of the distros is installed into their own logical partitions.

There seems to be a problem with the swap partition. The swap is not on when I boot into Ubuntu / Kubuntu and thus I'm not able to hibernate. I tried turning the swap on and it acts like it is going to hibernate but when I power on, it does not resume, just loads like cold boot. I got the UUID for the swap partition using this command:

```
sudo blkid
```

Then I edited /etc/fstab to the correct UUID. I'm still not able to hibernate.

Can you think of anything else I could do to get hibernation working?

---

### Post by xavier0912 on 2009-08-24
From me also a question:
setup is as followed:
sda1 -> Win7
sdb1 -> GRUB
sdb2 -> Ubuntu 9.04
 
When I install grub on it's own partition on sdb, I can boot windows from it, but for Ubuntu I get an error 13 ...
 
The dedicated grub looks like:
title Windows 7
root (hd0,0)
chainloader +1
 
title Ubuntu
root (hd1,1)
chainloader +1
 
Should I map hd1 hd0 to be able to boot Ubuntu or is mapping only for Windows based OS's ?
 
Any help much appreciated !
Greetz
Xavier
 
forgot to mention:
Installed Win7 first, than Ubuntu with it's grub on it's own disk (sdb).  This worked without a problem, but when activating the dedicated grug, things gone wrong.  I made the Ubuntu grub leading again, and it works agian.
I want the dedicated grub to be able to add other Linux distro's without having to "trouble my wife" too much ;)

---

### Post by unutbu on 2009-08-24
xavier0912, please run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file so we can better understand your boot setup.

---

### Post by bodhi.zazen on 2009-08-24
What do you mean by a "grub partition". A grub partition is a bit more complex then a boot partition.

A boot partition contains things such as your kernel I grub stage 1. A grub partition is then mounted at /boot/grub.

At any rate, take a look at what chainloading is, it passes the booting process off. So if you want to chainload to partition (hd1,1) grub must be installed in partition (hd1,1).

You should probably just specify where the kernel and initrd are.

root (hd1,1)
kernel /boot/vmlinuz-xyz root=/dev/sdb2 ro quiet splash
initrd /boot/initrd-xyz
boot

etc. The stanza will depend on your geometry and you shouldl mount /dev/sdb1 at /boot/grub (assuming it is a grub partition).

---

### Post by xavier0912 on 2009-08-24
Hi all,
Thanks for the replies !
Well, I attached the result.txt file.  Hope this helps!
hat I meant with "grub partition" is a dedicated Grub Partition.  I know ... I should learn to walk before I run, but when I buy a new PC, I want it clean from the beginning.  It will hold Win7 (blame it on the misses) and at least 2 linux distro's.  I want to be ablel to play around with them so it looks like the better option ... .
I think I (kind of) understand chainloading but I find it difficult seeing what is where ... beginners problem I guess.

Thanks for the help anyway !
Xavier

---

### Post by unutbu on 2009-08-24
xavier0912, try this:

Boot Ubuntu, open a terminal and type
```

sudo grub
grub> root (hd1,1)
grub> setup (hd0)
```

This will install GRUB on the MBR of sda, and direct it to boot sdb2 (the boot partition).

While still at the grub> prompt, next type
```

grub> root (hd1,5)
grub> setup (hd1,5)
```

This installs GRUB on the sdb6 partition (your Jaunty installation).
You need this so that when you use the "chainloader +1" command, GRUB on the MBR will hand-off to GRUB on sdb6 to boot Jaunty. For each additional Linux distro that you install, you'll need to install GRUB (using the "root (hdX,Y)" and "setup (hdX,Y)" commands) on that partition too.

Now quit grub:```


grub> exit
```

Next, at the terminal prompt, type
```

sudo mount /dev/sdb2 /mnt
gksu gedit /mnt/boot/grub/menu.lst

```
This should open the menu.lst on sdb2 (the boot partition).

Change 

```

title Ubuntu
root (hd1,1)
chainloader +1
```

to

```

title Ubuntu
root (hd1,5)
chainloader +1
```

since you want to boot sdb6, not sdb2.

Save and exit gedit. Reboot. Let us know how it goes.

---

### Post by xavier0912 on 2009-08-25
Hi unutbu,

Thanks already for the great explanation.
Leaving on a short holiday now so I'll try this next week.  I'll post the results than ok ?

Thanks again,
Greetz
xavier

---

### Post by nitstorm on 2010-04-03
Just found this post now. But it's all with reference to the legacy GRUB... what do I do with GRUB2 ???? Got Karmic Koala.... Please do help...

---

### Post by bodhi.zazen on 2010-04-04
> **nitstorm said:**
> Just found this post now. But it's all with reference to the legacy GRUB... what do I do with GRUB2 ???? Got Karmic Koala.... Please do help...

Aye, this thread is a bit dated now.

In theory grub 2 should now do all this automatically. In practice grub 2 has problems , in my experience most often with a separate /boot partition.

You can either :

1. Install grub legacy.

2. Learn the new grub.

There are many informative threads on grub 2 :

[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 
[Grub 2 - 5 Common Tasks - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1302743") 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)


[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Other then that, if you are having problems I suggest you start a new thread. You will need to describe your problem - what OS are you multibooting and what problem are you having ?

---

### Post by nitstorm on 2010-04-05
Gonna try multibooting this weekend, thanks for the help bodhi.zazen and i have started a new thread on the suggestion of oldfred, here is the link to my thread [http://ubuntuforums.org/showthread.php?t=1446351](http://ubuntuforums.org/showthread.php?t=1446351) , any tips and suggestions for a newbie to multiboot would be more than welcome . Thanks. Cheers!

---

### Post by meka4996 on 2010-05-22
Partition Table Design for Multi Boot Linux Distro, using Grub bootloader
[http://ubuntuforums.org/showthread.php?t=1300461](http://ubuntuforums.org/showthread.php?t=1300461)

Moving from Dual Boot to Multi boot [Dedicated GRUB Partition]
[http://ubuntuforums.org/showthread.php?t=1169648](http://ubuntuforums.org/showthread.php?t=1169648)

---

### Post by TutAmongUs on 2010-08-20
> **kushykush said:**
> Bodhi:  The guidance provided by you is too advanced. Could you or someone on this forum provide guidance as to how a newbie could install multiple operating systems?  Here is my scenario:

I have two Sata drives. Vista is on first drive (sda 0,0) which has three partitions.

Ubuntu is on the second Sata drive with its Swap and other partitions. 

Ubuntu installed the GRUB correctly (I do not know where).  The GRUB menu list displays Ubuntu and Windows/longhorn and gives me the option to boot either.

Now, I want to install SUSE (and then Fedora) alongside Ubuntu on the second Sata drive.  What do I do?

I want to leave Vista untouched on the first (0,0) mainly because I do not want anything to happen to it.  Ideally, I would like to install Vista, Ubuntu, Suse and Fedora on the first drive.  But I do not know how to chain install. 

When I go through the SUSE installation CD, it insists on deleting  the Vista partition(s).  When I direct it to one of the empty partitions along side Vista on the first Sata,  it gives me error that it cannot find the root (/) and the boot -- mounts,

When I try to install SUSE on the second Sata (which is currently occupied by Ubuntu), it insists on deleting Ubuntu's partitions.

If I understand the guidance above, what you are saying is that Suse, for example, cannot be installed along side Ubuntu using the usual SUSE install disc?  The only way out is installing it manually?

Before I started to install Ubuntu on my second sata (160 gigs) I had created three partitions in the hope that I will install Ubuntu, Suse and Fedora.  

I started with my favorite Ubuntu.  However, I could not install Ubuntu on the 50 gig partition that I had created because it kept asking me for the root partition and there was nothing in the graphic install program that gave me any guidance as to how that can be done.   Finally, I just did a "guided" install.  The result was Ubuntu wiped out the other two partitions and now occupies all of my second drive. 

Could you please, once again, try to provide guidance in understandable terms or direct me to relevant links?Try examining this thread.  It explains using a single drive, but it also works to "point at" other physical volumes as well.  It only needs to be set up on one drive.[http://www.zotacusa.com/forum/topic/3341-zotac-h55itx-a-e-wont-start-please-help/page__pid__9012#entry9012](http://www.zotacusa.com/forum/topic/3341-zotac-h55itx-a-e-wont-start-please-help/page__pid__9012#entry9012)

 It allows drive ordering to be reconfigured, and drives to be hidden (when Windows installations are picky).  You want to read on from the capitalized "SO" entry point.
If your drives already contain an OS, you may want to consider backing one up, so you can shove one of the volumes aside far enough for the 31MB space for the bootloader.

---

### Post by amjjawad on 2010-10-06
> **bodhi.zazen said:**
> 
In theory grub 2 should now do all this automatically. In practice grub 2 has problems , in my experience most often with a separate /boot partition.

You can either :

1. Install grub legacy.

2. Learn the new grub.

There are many informative threads on grub 2 :

[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 
[Grub 2 - 5 Common Tasks - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1302743") 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)


[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Other then that, if you are having problems I suggest you start a new thread. You will need to describe your problem - what OS are you multibooting and what problem are you having ?

Hello bodhi,

I don't have a problem but I'm so much obsessed of "Multi-booting". I've a crazy scenario and I spent two days with 3 hours of sleeping only to solve it. Of course I got some help from here and mainly from Fedora's forum.

Long story short, I made this and WHENEVER you got some time, please have a look and correct me if there's something wrong.

[http://ubuntu-beginnersguide-unofficial.blogspot.com/](http://ubuntu-beginnersguide-unofficial.blogspot.com/)

I was skimming your thread because I knew from the beginning it's about GRUB not GRUB2.
In 3 words only "sudo update-grub", I was able to boot from 3 OS's (Ubuntu, Fedora and XP).
I read somewhere that configuring GRUB is much easier than configuring GRUB2 but what happened with me lately is telling me (IMO) that GRUB2 is easier.
I've always wondered why Linux can't be sometimes "simple" as Windows but in the same time, I disagree with myself and say if it was easy as Windows, then one will never learn much about OS's. When I say easy I mean the installation, etc. I spent 10 years with Window, never had to know all these things. Now, I regret that I spent 10 years away from all this.

Please, take your time but don't forget to get back to me.
I didn't lose my mind yet to install 145 OS's :P I just want to learn more about this great world. 

God bless Linux :)

---

