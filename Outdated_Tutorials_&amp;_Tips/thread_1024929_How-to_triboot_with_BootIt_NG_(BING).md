---
title: "How-to: triboot with BootIt NG (BING)"
date: 2008-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Jammanuser on 2008-12-29
[SIZE="6"]**This is the complete tutorial for tri-booting Ubuntu 8.10, Vista, and XP using BootIT Next Generation (BING):**
[/SIZE]

This is the only way to get the thoughts out of my head, and is a little something I typed up after spending a great deal of time attempting to tri-boot Win Vista (pre-installed), XP, and Ubuntu 8.10 using the BootIT NG partitioning program. In my case, it took very long to finally get it working, using the program...but only because I did not previously fully understand the process of dual-booting, or in my case triple booting! For others who might want to use the program, but are a little hesitant of trying something **&#8220;new&#8221;**, and **&#8220;untested&#8221;**,  or have little or no experience in this field...rest assured that someone before you (that is, me) has **successfully** tri-booted with the program, and so don't be deterred by thoughts of fear that you might mess something up, or that you lack experience, or because someone else (who has never used the program, and fears to do  something he has not tried before) has filled your head with things like &#8220;**Gparted is better for partitioning...and its FREE!**&#8221; or &#8220;**BootIT NG doesn't have any documentation, or any kind of support...don't use it!**&#8221;. For the last possible saying, which is of course wrong, I can personally tell you that BootIT NG does INDEED have documentation, and support...the people that say it doesn't are the ones that were simply too afraid to spend a little money on a program that has far more options on tri-booting (not to mention the fact that it can create over 200 **primary** partitions...and enable booting from them as well!) than Gparted. Please don't take this as an insult...I meant it in the nicest of ways. I'm not dissing Gparted by any means...personally I think it is great, and a awesome tool for the &#8220;price&#8221;! But, as much as I like Gparted...it has limitations for people like me who want to tri-boot, while BootIT NG does not! For that reason I made up my mind to use BootIT NG, instead of Gparted (no offense to the Gparted users!) for the express purpose of tri-booting my Dell Studio 1535 laptop. 

Before we begin, I just want to point out that I did my best to explain things, using as few words as possible...but for some things, there is no way around lots of words. I also made an effort to proof-read   my tutorial, to try to iron out any errors or typos, but...I make no guarantees that there might not be at least **one** typo! If there is, then please forgive me! I take personal responsibility if there is any typos in the text. However, I will take none, if something happens to go wrong due to users' misreading, or other possible mistakes that might go wrong on the partitioning process. Like all who may have written similar tutorials, I advise strongly that you first backup all your data before beginning Step #2 in the tutorial...HECK! :laugh: It would be even better if everyone backed up their data before even installing BootIT NG! As this process is potentially dangerous to the user's computer, even though I did my best to make it as safe and foolproof as it could possibly be, there are so many things that could go wrong on a tri-boot...due to whatever reason! And so I will take absolutely NO responsibility if something goes wrong...although I will help you pick up the pieces afterwards! :D 

So consider yourself warned... /end rant

Now on to the steps.

[SIZE="5"]Pre-Step (Checking documentation):[/SIZE] 

This is of course a move that one does not have to do, for this tutorial at least, if he or she doesn't want to, and is simply one that I am providing for the simple purpose of backing up my claim that there is documentation for BootIT NG, and also in case anyone first wants to learn about the neat little tricks BootIT NG can do, before attempting to tri-boot with the
steps I outline below. It would be perfectly understandable though, if you're impatient, and would like to get the tri-booting process over with as soon as possible...in that case, you can then just follow the steps in this tutorial, as they're complete for what you're trying to do, and you will then have a working tri-boot!

See [http://www.terabyteunlimited.com/downloads/bootitng.pdf](http://www.terabyteunlimited.com/downloads/bootitng.pdf) for the BootIT NG manual. 

**And here is a few more documentation links:**

[http://www.terabyteunlimited.com/howto/index.htm](http://www.terabyteunlimited.com/howto/index.htm) (tutorials and videos)
[http://www.terabyteunlimited.com/kb/category.php?id=8](http://www.terabyteunlimited.com/kb/category.php?id=8) (FAQ)
[http://www.terabyteunlimited.com/kb/category.php?id=52](http://www.terabyteunlimited.com/kb/category.php?id=52) (problem solving)
[http://www.terabyteunlimited.com/kb/category.php?id=47](http://www.terabyteunlimited.com/kb/category.php?id=47) (general information)
[http://www.terabyteunlimited.com/webnews.htm](http://www.terabyteunlimited.com/webnews.htm) (newsgroup forums)

**You can also get support by email:**

Technical Support | [email]support@terabyteunlimited.com[/email]
General Inquiries | [email]corporate@terabyteunlimited.com[/email]

**Quick links to common issues:**

[COLOR="Blue"]*Partitions do not show up in the OS*[/COLOR] | [http://www.terabyteunlimited.com/kb/article.php?id=043](http://www.terabyteunlimited.com/kb/article.php?id=043) 
[COLOR="Blue"]*Image validation failures*[/COLOR] | [http://www.terabyteunlimited.com/kb/article.php?id=079](http://www.terabyteunlimited.com/kb/article.php?id=079) 
[COLOR="Blue"]*Message: HAL.DLL or NTOSKRNL missing or corrupt*[/COLOR] | [http://www.terabyteunlimited.com/kb/article.php?id=208](http://www.terabyteunlimited.com/kb/article.php?id=208) 
[COLOR="Blue"]*System hang when SATA-AHCI option enabled*[/COLOR] | [http://www.terabyteunlimited.com/kb/article.php?id=362](http://www.terabyteunlimited.com/kb/article.php?id=362) 

**[SIZE="5"]Things to check before beginning: [/SIZE]**

Before beginning with this tutorial, first make sure that you have a working Ubuntu 8.10 Desktop CD (also known as a LiveCD),  along with a Super Grub Disk, in the rare case that something goes wrong, and you're no longer able to boot into any of your installed Oses. If you don't have either one, then simply download the Ubuntu ISO from here: [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/) 
Either choose the 32-bit version (intel x86), or the 64-bit version (amd64), depending on your PC's architecture. Then download the InfraRecorder program > [http://infrarecorder.org/](http://infrarecorder.org/) and use it to burn the ISO image onto a CD. For detailed instructions on how to do this, visit: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 

The Super Grub Disk can be downloaded from here: [http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html](http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html) and also burned to a CD with InfraRecorder. 

At any rate, make sure to have both CDs at hand before you begin the first step of this tutorial! 

You will also need an XP installation CD, in order to install XP. Unfortunately, if you don't have one of these, you wont be able to install XP on your computer...at least not until you purchase one from Microsoft.

**[SIZE="5"]Step #1 (Downloading and installing BootIT NG): [/SIZE]**

Time to get that tri-boot working with BootIT NG! So what you're first going to do (if you have not done already) is install BootIT NG, of course! :grin: The link to download from is: [http://www.terabyteunlimited.com/downloads-bootit-next-generation.htm](http://www.terabyteunlimited.com/downloads-bootit-next-generation.htm) 
Once the download is complete, use the following sub-step to install it. 

[B][COLOR="Blue"][SIZE="4"][SIZE="4"]Sub-step #1 (Installing BootIT NG): 
[/SIZE][/SIZE][/COLOR][/B]
(The following has been copied from the BootIT NG manual itself with a bit of editing done by me to make it more readable...however, the content and the processes themselves remain essentially unchanged)


Before you install BootIt NG, take a moment to read about BootIt NG&#8217;s limitations and system requirements. Then, complete the procedures in *Before You Begin*. Finally, create the boot disk or ISO image as described in *Creating the boot disk or ISO image*, and then install BootIt NG on your hard disk as described in *Installing BootIT NG on Your Hard Disk*. 

**_Limitations_** 

BootIt NG relies on the basic input/output system (BIOS) for processing disk functions. If your computer BIOS limits access to the hard drive for any reason and no Master Driver Table (MDT) driver is available to correct the limitation, BootIt NG is also limited. BootIt NG supports BIOS LBA Mode and Interrupt 13h extensions. 

**_System Requirements _**

**Verify that your system meets the following minimum requirements: **

IBM-compatible personal computer 
i80386-compatible microprocessor 
16 megabytes (MB) of random access memory (RAM) 
Video graphics adapter (VGA) 
Floppy disk drive, CD/DVD drive, or USB Flash Drive (booting in floppy mode) 
BIOS-accessible hard disk 

**_Before You Begin _**

TeraByte Unlimited has taken every effort to make BootIt NG as safe as possible; however, it is not possible to provide a 100-percent guarantee of safety. 

It is extremely important that you do not use any partitioning software (such as FDISK) if you are not limiting the number of primary partitions (Limit Primaries Option). If you ignore this warning, you are taking a serious risk of data corruption. 
Before using BootIt NG on any system for the first time, back up all data on all hard drives. It&#8217;s better to be safe than sorry. 
It&#8217;s always a good idea to have a system disk&#8212;such as an MS-DOS startup disk or Windows 95 startup disk&#8212;that can be used to restart your system should something ever go wrong. You should configure the disk to give you all the functionality you may need by adding any drivers or utilities as well as configuring the configuration files. The next paragraph explains how you can create a startup diskette. 

_**Create a Windows XP/Vista startup disk **_

**1** From within Windows Explorer, right-click 3½ Floppy (A), and then click Format. 

**2** Select Create an MS-DOS startup disk, and then click Start. 

**[COLOR="Blue"]Note:[/COLOR]** If you don't have a floppy drive (either internal or external), then simply skip this sub-step.


**_Review the two-step installation process _**

**1** Create either the installation floppy boot disk or bootable international standards organization (ISO) image CD/DVD disc as described in Creating the Boot Disk or ISO Image. 

**2** Use either the floppy disk or CD/DVD disc to install BootIt NG on your hard disk as described in Installing BootIt NG on Your Hard Disk. 


[SIZE="3"]**Step 1 (Creating the Boot Disk or ISO Image):**[/SIZE]

The first of two steps in setting up BootIt NG from a downloaded copy of the software is to create the installation floppy boot disk or bootable CD/DVD disc; therefore, you need either one formatted floppy disk that matches the floppy disk drive A of the computer that will have BootIt NG installed, or one blank, writable CD/DVD disc. If you are installing on multiple computers, each computer should have its own Setup disk and license. If the computer does not have a floppy disk drive, then you must create a bootable CD/DVD disc or use a USB flash drive. Depending upon your version of Windows, you can either use Windows Explorer or File Manager to complete the following procedure. 

[U]**Create the boot disk using the MakeDisk utility (Windows users):**
[/U]
**1** Extract the contents of BootItNG.zip to a folder of your choice. 

**2** Run MakeDisk.exe from the folder of step 1. The MakeDisk welcome screen appears. 

**3** Click Next on the MakeDisk welcome screen. The BootIt NG license agreement screen appears. 

**4** Read the BootIt NG license agreement, and if you accept it, select the &#8220;I accept the agreement&#8221; button and click Next. The BootIt NG Mouse Support option screen appears. 

**5** Choose the appropriate option to either enable or disable mouse support, and then click Next. The BootIt NG Video Options screen appears. 

**6** Keep the default selection, &#8220;VESA Video&#8221;, unless you know for certain that you need to use one of the other video options. Click Next. The Boot Options screen appears. 

**7** Keep the &#8220;normal&#8221; option selected unless you plan on using Partition Work without installing. Click Next. The Default Device Options screen appears 

**8** Make any desired changes to the default device options BootIt NG will use when booting this disk on a system that does not have BootIt NG installed. The exception is the USB Controller and USB Device fix options which only apply to the command line which starts the BootIt NG program. Both of the &#8220;USB Fix&#8221; options may result in slower USB access, but will prevent hangs with certain controllers and/or devices. Click Next. The BootIt NG registration screen appears. 

**9** If you have purchased a BootIt NG license, enter the registration information you were provided with in the text boxes shown on this screen. If you wish to use the trial version of BootIt NG, simply leave the text boxes empty, which will result in BootIt NG operating in a 30-day time-limited trial mode. Click Next. The &#8220;Select Target&#8221; screen appears. 

**10** Choose the target that MakeDisk should use. If you choose the &#8220;ISO File&#8221; option, you must supply an ISO file name. Click Finish, and respond to subsequent prompts as necessary. MakeDisk will then create your bootable media or ISO image. When it is done, the success screen should appear. Once you have done that, proceed to *Step 2 (Installing BootIt NG on Your Hard Disk)*. 

**_Create the boot disk or ISO image (DOS users)_**
**1**
Uncompress the contents of BootItNG.zip to its own folder on your hard disk, and then locate (or change to) that folder.
**2**
Double-click BootItNG.exe (or type BootItNG.exe and press Enter).
**3**
If you accept the license agreement, select the appropriate build option from the menu, and then press Enter.
**4**
Do one of the following:
&#8226;
To create the floppy boot disk, insert the disk in the appropriate disk drive, and then press Enter. After about 1 minute, a message indicates whether or not the boot disk was created. (If the disk was bad, insert a new disk into the drive, and then press Enter.)
&#8226;
To create the bootable CD/DVD disc, insert the CD/DVD disc in the appropriate drive, and then use BurnCDCC&#8482; or your CD/DVD burning program to burn the BootItNG.iso image file (that was created in step 3) from its folder to the CD/DVD. If using NERO, on the File menu, click Burn Image, and then change the File Type to ISO to locate BootItNG.iso. If using Easy CD Creator, on the File menu, click Create CD from CD Image, and then change the File Type to ISO to locate BootItNG.iso. If using other CD/DVD-copying programs, refer to their help systems for copying an ISO image file to a CD/DVD disc.
**5**
Proceed to *Step 2 (Installing BootIt NG on Your Hard Disk)*.

_**Create the boot disk or ISO image (Linux users)**_
**1**
Uncompress the contents of BootItNG.zip to its own directory on your hard disk, and then change to that directory.
**2**
Do one of the following:
&#8226;
To create the floppy boot disk using the cp or dd command (if you accept the license agreement), verify that the disk is not mounted and that you are signed on as root, and then type: cp DISKIMG3.DAT /dev/fd0 or dd if=DISKIMG3.DAT of=/dev/fd0 bs=1024
&#8226;
To create the bootable CD/DVD disc (if you accept the license agreement): Type: mkisofs -o bootitng.iso -V BootitNG -c boot.cat -b DISKIMG3.DAT DISKIMG3.DAT Then type: cdrecord &#8211;v speed=8 dev=1,0 BOOTITNG.ISO (Be sure to adjust dev= to the appropriate value)
**3**
Proceed to *Step 2 (Installing BootIt NG on Your Hard Disk)*.

[SIZE="3"]**Step 2 (Installing BootIt NG on Your Hard Disk):**[/SIZE]

In this step, you will install BootIt NG onto your hard disk, using either the installation media that you created in *Create the boot disk using the MakeDisk utility (Windows users)*, or the installation media that was included with your BootIt NG purchase (if any). 

**_Boot from the floppy disk or CD/DVD _**

**1** Consider doing the following: 
From within BIOS (basic input/output system) setup, verify that your system boot up sequence is correct: For the floppy disk drive, it should be something similar to: A:/C: and not C:/A: For the CD/DVD drive, it should be something similar to: CDROM/C: For the USB flash drive, it should be something similar to USB-FDD or USB-ZIP. 
Disable the boot-sector/mbr virus protection option. If you leave the virus protection option enabled, it may cause issues. 

**2** Shut down and turn off your computer. 

**3** Insert the BootIt NG Setup media in the correct drive, and then turn on your computer. 

 [LIST]
[*]BootIt NG should begin loading from the floppy disk, CD/DVD, or USB flash drive. 

[*] If BootIt NG doesn&#8217;t seem to load and your system starts as it normally does, double-check that you configured the BIOS correctly. 

[*] An &#8220;EMBRL Missing&#8221; message when booting from floppy typically means a bad diskette. The same message for CD/DVD typically means a bad disc or the BIOS doesn&#8217;t properly maintain 1.44MB emulation. Contact the BIOS manufacturer for a BIOS update.
[/LIST]

**Note** 
If you&#8217;re booting a flash drive via USB, you can only install BING if the BIOS boots the flash drive in Floppy mode and not in hard drive mode. If you boot the flash drive and a Boot Menu shows up then the system is booting the flash drive as a hard drive and BootIt will think it&#8217;s already installed. 
If you use a CD or DVD drive and receive a warning that the backups fail and the creation of the transfer file fails, that&#8217;s because the CD/DVD is not writable. 

**_Install BootIt NG for the first time _**

**1** After you boot from the BootIt NG Setup media, at the Welcome to setup prompt, click OK. 

**2** When asked if you want to enable more than four primary partitions, click Yes or No. If you click Yes, then you must partition your hard drives only using BootIt NG. If you click No, then you can continue to use any other partitioning software such as FDISK. (My advice is to click Yes, since you will most likely need more than 4 primary partitions)

**3** When asked how you want the partition chosen, click Yes to have Setup choose the partition for you or click No to choose the partition manually as described on page 10. (I chose No, as I wanted to make sure it installed to the correct partition, and wouldn't overwrite anything important...
If you need help resizing your existing partition, and then using the free space to create a new partition to install BootIT NG on, please refer to Sub-step #2, which is after Step #2)

**4** When asked if you want to install BootIt NG to its own partition, click either Yes or No. Installing BootIt NG to its own partition requires unpartitioned space and takes up one primary partition which could be an issue if you chose not to enable support for more than four primary partitions. If Setup can&#8217;t accommodate your choice, it notifies you later and gives you the option to change selection. If you don&#8217;t want to change your selection and need further help, review the first part of tutorial one by visiting: [http://www.terabyteunlimited.com/bootit-next-generation-tutorials.htm](http://www.terabyteunlimited.com/bootit-next-generation-tutorials.htm) 
(Again, it is advised to choose Yes, and create another partition to install BootIT NG on...once again refer to Sub-step #2, which is after Step #2. Also refer to step #3, which describes how to create a partition out of the free space you now have after resizing)

**5** When Setup indicates that it has all of the needed information, click OK to begin copying files to your hard disk, and then refer to Complete the installation.  

**_Complete the installation_** 

**1** Use your operating system&#8217;s disk copy feature to create a backup copy of the startup disk and keep it in a safe place. You will need the startup disk to recover from any problems or situations that may arise in the future. If you ever update your startup disk or use a new one, be sure to update your backup disk as well. 

**2** Consider changing the boot sequence to boot from drive C first if your BIOS can change the boot sequence to C:/A:. If you have a CD or DVD drive, consider setting up the sequence to be C/CDROM/A so that you can use the Next BIOS Device option in BootIt NG. 

Now proceed to next step.

**[SIZE="5"]Step #2 (Defraging and resizing your main partition): [/SIZE]**
Ok, so first we're going to defrag Vista's partition before we resize it, so the process will take a lot quicker, since all the files will now be at the front of the partition, instead of scattered here, there, and yonder, as it is when your hard drive is badly fragmented! So click on this direct download link while booted in Vista > [http://www.download.com/3001-20_4-10567503.html?spi=dc2a7091a997e996b4766bd726fd0ea4](http://www.download.com/3001-20_4-10567503.html?spi=dc2a7091a997e996b4766bd726fd0ea4) to download the Auslogics Disk Degrag tool, which is probably the best degrag tool for Windows, in my opinion. Once it has downloaded, open up your Downloads folder located at *Username*>Downloads, and double click on "disk-defrag-setup" to begin the install of the program. Hit Next, read the license agreement, and if you accept, click Next again, and choose where to install the program. Then click Next, and Next again, and then after first verifying that the box titled "Create a desktop icon" is checked, click Next one last time to complete the installation. Once it is done, push Finish, and the program should start up automatically providing of course you left the box called "Launch Auslogics Disk Defrag" checked. Now, once the program starts up, click Next to begin defragmentation of the selected disk. This process will likely take a while, if you haven't done a defrag in a while, or worse than that, have **never** run a disk defrag on your computer! Be patient, and wait until it has completed (be aware that it might take hours...), and then once it is done, we can now proceed to partition your hard drive, so we can install XP and Ubuntu 8.10. 

Now that BootIT NG is installed on your computer, and the disk-defrag is done, you can now proceed to partition your hard drive with it. First reboot, and if the install went ok, you should now see the BootIT NG boot menu at startup. If you look at the bottom of this, you will see a button titled &#8220;Maintenance&#8221;. Click on this, and this will send you to the BootIT NG desktop. Once there, open up &#8220;Partition Work&#8221;, where you will see a nice orderly layout of your computer's existing partitions...this is where you will perform all the resizing, moving, and otherwise operating procedures on your partitions! :D Select the partition that you want to resize...this will most likely be the partition that your OS is installed on, so make sure to backup all your data before going through with this step! BootIT NG has a reputation for its resizing, creating, moving, etc. procedures being exceptionally safe...but is always wise to make precautions! Fail to do this all-important step, and you will be the only one to blame if something goes wrong on the resizing process! So once again, I stress this: **BACKUP ALL YOUR DATA FIRST!!!** 
For a detailed procedure on how to resize it with BootIT NG, see the below sub-step...otherwise, skip ahead to the next step! 

[SIZE="4"]**[COLOR="Blue"]Sub-step #2 (Resizing a partition): [/COLOR]**[/SIZE]

(The following has been copied from the BootIT NG manual, and has been in no way modified)

_Resize a partition or volume _

**1** On the desktop, click Partition Work. 

**2** In the Partitions list, select the partition or volume that you want to resize, and then click Resize under Actions. 

**3** In the Resize dialog box, click OK to error check the file system. The error-checking process can take a long time. If the hard disk indicator light continues flickering, the error check is progressing. When the error check is complete, in the Resize dialog box you may review the Partition Information (such as Name, Type, and Size) to verify that you are resizing the correct partition. 

**4** Review the Min Size and Max Size, and then increase or decrease the New Size of the selected partition using the up or down arrows respectively. 

**5** Click OK, and then (if you've already backed up your hard disk) click Continue. The Resize status bar indicates progress. This process can take a long time when BootIt NG needs to move your existing data in order to resize the partition. BootIt NG checks for errors once again, after which the Resize dialog box displays a message that the resize is complete. 

**6** Click Close. 


[SIZE="5"]**Step #3 (Creating the necessary partitions): **[/SIZE]
This step is assuming that you successfully resized your main partition, and now have the pre-ordained size (in MBs) that you chopped off of the partition as &#8220;Free Space&#8221; in the space right below the partition that you resized, looking at the Partition Work window (Note that a gigabyte is approximately 1000 MBs, in the likely case that you are more familiar with judging size in terms of GBs rather than MBs). Select this free space by left clicking on it, and then look at the right side of the window. You will see a button called &#8220;Create&#8221; at the top...this is of course the button that allows you to create partitions (formatted at your choosing, with whatever File System type you want...BootIT NG has several options) out of the free space. Click on the Create button, which will bring you to a dialog box showing you all of the different options you can use on your soon-to-be partition. From here, select whatever filesystem type you want (choices for XP are NTFS or Fat 32...although Fat 16 would also work if you want to give XP only very limited space for all its system files and included programs...which I'm assuming you most probably wont!). You can also choose the size you want the partition to be...this is particular useful in case you don't want to use up all of the free space that you took from your main partition, and want to have space left over for another partition for Ubuntu 8.10, which is what I did. Select the size and the File System type you want (In my case, I chose &#8220;12/Ch: Fat-32&#8221; File System for XP, with a 20 GB/20000 MB size). In the &#8220;Name:&#8221; field, enter &#8220;WinXP&#8221; without the quotes, and press &#8220;Ok&#8221;. You should now see a partition where the free space was previously...and if you left space for your Ubuntu 8.10 partition, the remaining free space should be right below the newly-created partition. Assuming that you did leave enough space for your Ubuntu 8.10, now proceed to create a &#8220;Linux Native&#8221; partition out of the free space, using the exact same procedure outlined above, only naming your Ubuntu partition &#8220;Ubuntu-real&#8221; without the quotes. But again, do not use up all the space, as you will also need a swap partition greater in size than your RAM (in my case, my RAM was 4GBs, so I made the swap 4500 MBs in size, or 4.5 GBs). So create a swap partition (with &#8220;Linux Swap/Solaris&#8221; File System), and name it &#8220;Linux swap&#8221; without the quotes. Now proceed to next step...

**Note:** While still in the Partition Work window, click on the &#8220;View MBR&#8221; button on the left side of the window, and check to make sure that it shows the following entries in the MBR, in the exact order:

[COLOR="Blue"]WinXP [/COLOR]
[COLOR="Blue"]Linux swap[/COLOR]
[COLOR="Blue"]OS-2[/COLOR] (or "OS"-this will be your Vista partition)
[COLOR="Blue"]Ubuntu-real[/COLOR] (your real Ubuntu partition)
 
If it looks in any way different, then make sure to change it so that it displays the same thing as above. To do this, press the &#8220;Move Up&#8221; or &#8220;Move Down&#8221; buttons as appropriate to move the entries either up or down, respectively. If necessary, insert the correct entries by clicking on the &#8220;Insert&#8221; button, and then choosing the partition entry that you want to insert, and pressing Ok. When you are done, press Apply to save the changes, and exit the &#8220;View MBR&#8221; window.

**[SIZE="5"]Step #4 (Hiding your Vista partition): [/SIZE]**
This step is essential to installing XP correctly (which I will explain in the next step), so make sure to pay close attention! While still in Partition Work in BootIT NG, look at the right side of the window where there is a row of buttons. The bottom one is called &#8220;Properties&#8221;. This is where it tells you all of the information on a selected partition, e.g. filesystem type, size, specific place on your hard drive, etc. This is also where you can hide/unhide selected partitions. So first select the partition that Vista is installed on...it will probably be called something like &#8220;OS&#8221; by default, and will most likely be a NTFS partition. Now with the Vista partition selected, click on the Properties button already mentioned, which will open up a dialog box showing you the information on the selected partition. Now click on the &#8220;Hide&#8221; button, which will then hide Vista from your XP installation, allowing you to install XP correctly. Now simply push &#8220;Ok&#8221;, to accept this setting.

Now proceed to next step.

**[SIZE="5"]Step #5 (Making the XP partition active):[/SIZE]**
Here we will make the XP partition active, before installing XP, simply because (if you don't) it will likely install its boot files to Vista's partition, since it would be "active" in that case, and you would not be able to stand-alone boot XP with BING. So that is why we want to mark it as "active" before installing XP.

So here is what you're going to do:

Click on the "View MBR" button on the left side of the Partition Work window, and now select the XP partition. Now push the "Set Active" button to make the XP partition active. DONE! 
Now you can proceed to install XP in the next step.

**[SIZE="5"]Step #6 (Installing XP): [/SIZE]**
Now that you have partitioned your hard drive correctly, leaving partitions for both your XP and Ubuntu 8.10 OSes, insert your XP CD, after first putting the CD/DVD drive first in the BIOS! To do this, simply push F2 at startup, when its still at your computer manufacturer's screen (in my case, it is the Dell screen) to enter the BIOS. Once in there, go to &#8220;Boot Sequence&#8221;, and push Enter to edit the drive order. Select your CD/DVD drive, which will probably be something like the fourth entry down, and then push &#8220;u&#8221; to move it up. Move it up all the way to the top, so that your CD/DVD drive is first in the drive order, and then push Enter to save this setting. Now simply go to &#8220;Save/exit&#8221; to save the settings of the BIOS, and quit. Now right after this, if your XP CD is in the CD drive, you should see &#8220;Push any key to boot off the CD&#8221;. So push any key to boot off the XP CD, and to begin your XP installation. You will now see XP go through a long process of &#8220;installing&#8221; drivers for the installation, after which you will eventually get to a screen where you can tell it to install XP, and then get to another screen where you can select the partition you want to install XP to. Note however that you should have hid Vista first, using BootIT NG, so as to prevent the XP installation setup from selecting a drive letter other than C: for XP, when it is booted, which might impar things later on down the road, due to some programs having the &#8220;C&#8221; drive letter hard coded in their installation script, which means if you don't hide Vista, when you try to install such programs on XP, you wont be able to, due to the fact that it will install to &#8220;C&#8221;, which would be Vista, instead of to the XP partition, which is what you really want. So make sure to **HIDE** it!!! If everything goes according to plan, and the correct partition is selected to install XP on (note the partition size while still back at BootIT NG...this should allow you to make the correct choice when installing XP!), then when you complete the setup of XP, and boot into it for the first time, you should now see the XP partition with the correct drive letter, i.e. &#8220;C&#8221;, in My Computer. At this point (since Vista, if you did everything correct, will be hidden) Vista should not be visible. However, once making the Vista partition active again, XP will assign the &#8220;D&#8221; letter to it, so now XP will be on &#8220;C&#8221;, and Vista will be &#8220;D&#8221; in XP; and Vista should also be &#8220;C&#8221; in Vista, with XP as &#8220;D&#8221;! :D
Now reboot again, and proceed to next step.

**Note:** For some users, like me, you might first have to swap your SATA controller's operating modes, in order to install XP. To do this, go to &#8220;Onboard Devices&#8221;, and select &#8220;Flash Cache Module&#8221;. Your factory default setting should be set to &#8220;Enable&#8221;. If so, then change it to &#8220;Off&#8221; in order to disable it. Next go to &#8220;SATA Operation&#8221;, also in Onboard Devices, and change the operating mode from &#8220;AHCI&#8221; to &#8220;ATA&#8221;. You will receive a warning message that some operating systems may not work if you change this setting...ignore this message, and push OK, anyway, because that is what we need to do, in order to see XP successfully installed. Now go to &#8220;Save/exit&#8221;, and quit your BIOS.  

It would also be good if you put your XP entry first in the MBR, in the BootIT NG &#8220;View MBR&#8221; window, back at Partition Work. To do this, simply move it up by pushing the &#8220;Move Up&#8221; button which you will find in the &#8220;View MBR&#8221; dialog box. This move will help things later on in the tutorial, as the menu.lst file (if you replace what's currently in it with the new text that I provide in sub-step #4) will be configured correctly, and will prevent the need of having to edit it again, if the XP entry is somewhere else in the MBR entry order.

**[SIZE="5"]Step #7 (Reactivating BootIT NG, and changing the BIOS back to normal):[/SIZE]** 
Now with XP installed, you should enter the BIOS once again at reboot. This is simply to prevent the computer from booting into XP again, and so as to allow you to insert the BootIT NG CD. Once inserting, exit the BIOS, without changing anything, and your computer should now boot off of the BootIT NG CD. You should now see a dialog box where the option to &#8220;Reactivate BootIT NG&#8221; is enabled. Select this option to reactivate it, as it got deactivated during the XP installation. Then reboot, enter into BIOS once again, eject the BootIT NG CD, change the drive order back to normal, by simply lowering the CD/DVD drive entry back to its former place, which will in turn raise the other entries back to their previous spaces. And re-enable the Flash Cache Module, and then change the operating mode of the SATA controller back to AHCI, so you can boot into Vista again. Now exit the BIOS, which should boot into the BootIT NG boot menu again, as the program is now reactivated...and proceed to next step.

**[SIZE="5"]Step #8 (Un-hiding Vista): [/SIZE]**
Now that you are once again in BootIT NG...go to Partition Work again, and make Vista unhidden by going to Properties, which again is the bottom button on the right-hand side of the Partition Work window, and then clicking the &#8220;Unhide&#8221; button, and then &#8220;Ok&#8221;, and &#8220;Close&#8221; to close the Partition Work window. And then proceed to next step...

**[SIZE="5"]Step #9 (Installing Ubuntu 8.10):[/SIZE]** 
On this step I'm going to give the option to either install Ubuntu as a normal install, i.e. with the Ubuntu 8.10 Desktop CD, or to simply transfer your Wubi install to the partition that you created for Ubuntu...this is will of course function as a real install, and has the advantage of being already installed on top of your Windows installation, with no doubt your favorite programs and data already installed on it. That is what I did...however, since obviously each individual's case is going to be a bit different, without doubt, I am offering the option to install the regular way, with the Ubuntu CD.  Since I am more familiar with transferring Wubi over to a dedicated partition with LVPM, instead of doing the normal install with the CD, I will only describe how to transfer your Wubi install of Ubuntu 8.10, as I am sure anyway that most people who use the CD will have no doubt used the CD before, and be familiar with the process. So, assuming that you're still at the BootIT NG Partition Work window, now reboot by simply closing that window and pushing the Restart button at the bottom right of the desktop. This time, when you reach the BootIT NG boot menu, push the &#8220;Windows Vista&#8221; button in order to boot into Vista, using BootIT NG. However, if you're using Wubi, at least, you should now get to the Vista bootloader menu, where you have the option to either boot into Ubuntu or Vista. Choose Ubuntu, and once you're in it, go to this page: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)  
and navigate to the download page, where you will download LVPM. Once the download is complete, the installation process should begin automatically...if it doesn't, then go to the dir or location where you downloaded it to, and simply double-click on it in order to begin the install. Provided you have all the dependencies of the program, you should be able to just click on the &#8220;Install Package&#8221; button in order to install it. However, in my case, I was missing &#8220;os-prober&#8221;, and I could not find it either in Synaptic or Add/Remove Programs, and I had to manually download it from a site I found after entering it in the Firefox search box. I will save you the trouble of having to do the same, though, and I will simply give you the link: [http://packages.debian.org/unstable/utils/os-prober](http://packages.debian.org/unstable/utils/os-prober) 
Once there, download it, and install. The dependencies of that program, in my case, were met, fortunately, and I was able to install LVPM right after that. Hopefully it will be the same for you...
Now with LVPM installed, you can proceed to the following sub-step where I show you how to transfer your Wubi install over to the partition that you created for it.

[SIZE="4"][COLOR="Blue"]**Sub-step #3 (How to transfer Wubi using LVPM): **[/COLOR][/SIZE]
Now go to Applications>System Tools>LVPM and open up the LVPM application. You should now see a dialog box where you have either of 3 options: transfer, resizehome, resizeroot
Obviously, we will want to choose the &#8220;transfer&#8221; option as we don't want to resize the Wubi root.disk at this point... :D So pick &#8220;transfer&#8221; which will send you next to another dialog box, where you will see the existing partitions on your hard drive...shown as &#8220;sda1&#8221;, &#8220;sda2&#8221;, &#8220;sda3&#8221;, and so forth. Make sure not to choose the partition that the host OS is on, i.e. Vista, as this will ruin your Vista installation, and of course also delete or overwrite Wubi in the process! And I'm assuming that you don't want that...
If you're unsure which partition is which...then it would be a good idea at this point to run &#8220;sudo fdisk -l&#8221; in a terminal (and that last letter is a lowercase L, not a capital i), and after that type your user password, without visual confirmation of what you're typing (this is to prevent someone who may be looking over your shoulder while you type from seeing what your password is), which will show you a list of your existing partitions, complete with &#8220;sdxy&#8221; notation beside it, to show you which partition is the partition that you want to transfer Wubi over to. If the output seems kind of foreign to you, then let me explain a little how it all works...the first line shows your hard drive itself, known as &#8220;/dev/sda&#8221; without the quotes, which simply amounts to Disk (or harddrive) 0. Remember that the counting in this case, at least, begins at 0, instead of 1, and that &#8220;a&#8221; is equivalent to 0. 

You should also see on the first line of the output of &#8220;sudo fdisk -l&#8221;, after you type your password, the total size (shown in GBs) of your hard drive ....skip down to the line where you see &#8220;Device Boot&#8221;. Right below this phrase, you will see a list of your existing partitions, shown as &#8220;/dev/sda1&#8221;, &#8220;/dev/sda2&#8221;, and so on. Note the &#8220;1&#8221; and 2&#8221; numbers right beside &#8220;sda&#8221;...these are simply the partition (or specified hard disk sectors of your hard drive) numbers of each individual partition. Now if you look more to the right on the same line as &#8220;Device Boot&#8221;, you will see an entry named &#8220;System&#8221;. Right below &#8220;System&#8221;, on each individual line indicating a partition, it gives the filesystem type of each partition...i.e. FAT32, or Linux, or HPFS/NTFS, etc. You should have little trouble finding the correct partition that you want Ubuntu installed on, provided of course you followed the directions in Step #3, where I said to choose &#8220;Linux Native&#8221; File System type for the Ubuntu partition, and to make sure that partition existed in the MBR. You will see the partition as simply &#8220;Linux&#8221; filesystem type in fdisk. Make a note of what device string that partition is...i.e. &#8220;sda1&#8221;, or &#8220;sda2&#8221;, etc. And then simply use that device string in LVPM to select the correct partition to transfer to. Once you select it, then simply push &#8220;Ok&#8221;, which will then send you to another dialog where you will have to confirm that this is what you want to do, after which the transferring process will begin. Depending on your RAM and processor speed, this process might take a while...make sure to prepare for a long wait before undertaking this step. Once the transfer finishes, it should then give you a message saying you need to reboot in order to your newly upgraded Ubuntu install. And so reboot, which should then bring you to the Grub menu instead of to BootIT NG...but don't worry. You will have to reinstall BootIT NG again, in order to get it to boot from it again at bootup, instead of Grub, due to the EMBR being partially overwritten when Grub got installed...but that part is easy and only takes a few seconds to complete. For now, boot into your newly-transferred Wubi install by pushing Enter (assuming of course you're in Grub) just to take a look around, and to make sure all your files, programs, and settings have been successfully transferred over to the partition, and nothing is missing. And then reboot and proceed to Step #7 where I describe how to reinstall BootIT NG...or if the boot to Ubuntu failed, refer to the following sub-step.

**Note:** As with XP, the location of the Ubuntu entry in the &#8220;View MBR&#8221; window in BootIT NG is important. You need to have it occupying the fourth place in the MBR (if you count from top to bottom, that is!). This is to prevent having to needlessly (that is, needlessly, because you wouldn't have had the need if you followed this important tip!) edit your Ubuntu menu.lst file again, (since you will have already edited it once, if you follow the next sub-step) a second time. 

[SIZE="4"][COLOR="Blue"]**Sub-step #4 (How to recover from an error 17):**[/COLOR] [/SIZE]
If you get error 17 (cannot mount partition) when selecting the real installation of Ubuntu 8.10 (transferred version) to boot from in Grub, like I did, it is because your Ubuntu menu.lst (located at: /boot/grub/menu.lst) is configured wrong...most likely lacking any partition number in ( ) at the place where it mentions the title, as well as most probably the recovery mode, and memtest. If that is the case, then simply boot from the LiveCD again, open up the Terminal, run &#8220;gksu nautilus&#8221; without the quotes, and then navigate to your menu.lst file which is on your Ubuntu-real partition, and replace the text in the menu.lst file with the following text (which is a complete menu.lst file, configured correctly):
```

# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not use 'savedefault' or your 
# array will desync and will not let you boot your system. 
default		0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		2 

## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
hiddenmenu 

# Pretty colours 
#color cyan/blue white/blue 

## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line)  and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 

# 
# examples 
# 
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
# 

# 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 

### BEGIN AUTOMAGIC KERNELS LIST 
## lines between the AUTOMAGIC KERNELS LIST markers will be modified 
## by the debian update-grub script except for the default options below 

## DO NOT UNCOMMENT THEM, Just edit them to your needs 

## ## Start Default Options ## 
## default kernel options 
## default kernel options for automagic boot options 
## If you want special options for specific kernels use kopt_x_y_z 
## where x.y.z is kernel version. Minor versions can be omitted. 
## e.g. kopt=root=/dev/hda1 ro 
##      kopt_2_6_8=root=/dev/hdc1 ro 
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,3) 

## should update-grub create alternative automagic boot options 
## e.g. alternative=true 
##      alternative=false 
# alternative=true 

## should update-grub lock alternative automagic boot options 
## e.g. lockalternative=true 
##      lockalternative=false 
# lockalternative=false 

## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash 

## should update-grub lock old automagic boot options 
## e.g. lockold=false 
##      lockold=true 
# lockold=false 

## Xen hypervisor options to use with the default Xen boot option 
# xenhopt= 

## Xen Linux kernel options to use with the default Xen boot option 
# xenkopt=console=tty0 

## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery) single 
# altoptions=(recovery mode) single 

## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the 
## alternative kernel options 
## e.g. howmany=all 
##      howmany=7 
# howmany=all 

## should update-grub create memtest86 boot option 
## e.g. memtest86=true 
##      memtest86=false 
# memtest86=true 

## should update-grub adjust the value of the default booted system 
## can be true or false 
# updatedefaultentry=false 

## should update-grub add savedefault to the default options 
## can be true or false 
# savedefault=false 

## ## End Default Options ## 

title		Ubuntu 8.10, kernel 2.6.27-7-generic 
root		(hd0,3) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
root		(hd0,3) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, memtest86+ 
root		(hd0,3) 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


title Windows XP 
root (hd0,0) 
chainloader +1 


title Windows Vista/Longhorn (loader) 
root (hd0,2) 
chainloader +1

```
Also note that having the extra boot entry in your Ubuntu menu.lst for XP will allow you to boot into XP from Grub, although you will have to press Esc at this spot in order to access the Grub menu, where you can either select Ubuntu or XP (as well as your default OS, Vista), or else it will boot right into Ubuntu after 2 seconds, because that is what the timeout is set to.
Then in a terminal, run:
```

sudo update-grub

```

**Note:** Obviously the kernel versions mentioned in the menu.lst will have to be changed to mirror the particular user's version. But other than that, the rest of the menu.lst file should be correct for everyone,  provided of course they followed my directions in Step #5, and Sub-step #3, where I explain precisely where both OS entries should be in the &#8220;View MBR&#8221; window in BootIT NG, namely XP at the first space, and Ubuntu at the fourth space. This means that XP is located at sda1 (hd0,0), while Ubuntu is located at sda4 (hd0,3).

**[SIZE="5"]Step #10 (Reinstalling BootIT NG): [/SIZE]**
Reinstalling BootIT NG is necessary, though unfortunate. There is simply no way around it...at least if you want BootIT NG up and running again, which I will assume you do. Until you reinstall it, you will no longer be able to boot into the program at startup. This is due to the EMBR being overwritten, at least partially, by Grub, when transferring your Wubi install over to the dedicated partition with LVPM. At the moment, I know no workaround to this problem, though it may be possible, via the command line in Wubi, to instruct LVPM to install Grub to the boot sector of the partition, rather than to the MBR, though if there is, I don't know it at the moment. (If anyone has the solution to this, please let me know, and I will update my tutorial to describe this solution)

Once your computer reboots, enter BIOS again by pushing F2 at startup, while still at the manufacturer's startup page. Now put the CD/DVD drive first in the drive order again, by selecting it again, and pushing &#8220;u&#8221; until it is first in the drive order. Now insert the BootIT NG CD again, and boot off it...and this time, you should get to a menu where all the options are grayed out except for reinstalling BootIT NG. So choose this option, and push Ok. Go through the proceedure again of choosing &#8220;No&#8221; when it asks you if you want it to automatically pick the drive to install to, and then &#8220;Yes&#8221; when it asks you if you want to do a manual install, and then &#8220;Yes&#8221; when it asks you if you want to choose the drive for installation. Once again, create the EMBR by clicking on the &#8220;Create EMBR&#8221; button on the left side of the Partition Work window. When &#8220;Undo EMBR&#8221; displays in its place, you know that it worked. Now select again the partition that BootIT NG is installed on...and push the Setup button on the right side of the Partition Work window, which should be all the way at the bottom, below the other buttons, and once again install BootIT NG on this partition. Now reboot, and if it boots into BootIT NG at startup instead of Grub, you know it worked...if it doesn't, however, and it still goes to Grub, then you did something wrong, and you will need to try reinstalling it again! Note however, that now you wont be able (temporarily) to access the Grub menu anymore...it will go straight to the Vista bootloader menu, after you choose &#8220;Windows Vista&#8221; in BootIT NG. That is simply because it got overwritten when reinstalling BootIT NG, just like BootIT NG EMBR got overwritten when installing Grub! That is not really a problem, though, since we will simply reinstall Grub in the next step...so now proceed to Step #10 to reinstall it!

**[SIZE="5"]Step #11 (Reinstalling Grub): [/SIZE]**
Now it is time to reinstall Grub, though this time we will install it to the boot sector of the Ubuntu partition, rather than to the MBR, which is what LVPM does. Plop in now the Ubuntu 8.10 Desktop CD, and boot from it. When you get to where you're supposed to choose the language, pick English, or whatever language you're most familiar with, and then select &#8220;Try Ubuntu without making any change to my computer&#8221; if not already selected, and push Enter. Once you get to the desktop, open up a terminal by going to Applications>Accessories>Terminal and then type the following commands, and push Enter or Return after the end of each command, which is indicated by going to the next line (Note that the &#8220;#&#8221; sign indicates a comment on the command, and doesn't indicate something to be entered in the terminal):

```
 sudo grub
find /boot/grub/stage1
root (hdx,y)  # x = whatever hard drive you want to install Grub to, which in most cases, would be drive 0, or (hd0), and y=the partition number to be entered, to which you obtained in the &#8220;find&#8221; command. For example, (hd0,3), where '3'  is equilvalent to '4' in &#8220;sda4&#8221;. Always remember that when you're going by (hdx,y), the y integer is always going to be one number behind the y in the &#8220;sdxy&#8221; notation. #End comment
setup (hdx,y)
quit

```

Now reboot, and you will most likely not see any *immediate* results. You will most likely have to reinstall BootIT NG again (I know...its a bummer, isn't it?), which is what I had to do. Once reinstalling, you should now see a new boot entry in the BootIT NG boot menu, titled &#8220;Linux Native&#8221; or something to that effect. Select that, and you should now be able to boot into Ubuntu 8.10 fine from BootIT NG. Congrats! You have successfully completed one phase of tri-booting! Now time to complete the next ten phases! Or was it eleven? I don't remember...

So now proceed to Step #12.

**Note:** Now that I think about it, you should be able to add a boot entry to the BING boot menu for Ubuntu that should work at this point, but I really don't know this for sure, because in my case I simply reinstalled BING again, at this part, because this thought didn't occur to me at the time. If anyone wants me to add a detailed description on how to do this, please let me know. But for now, though, I will simply state the possibility that it might work by doing this, instead of reinstalling BING again.

**[SIZE="5"]Step #12 (Configuring the Vista bootloader to boot all 3): [/SIZE]**
Now that you are able to boot fine into Ubuntu, as well as XP, through BootIT NG, it is time now to configure your Vista bootloader to tri-boot all 3! If you're happy with it only tri-booting through BootIT NG itself (which I imagine might be the case for some), then you can simply skip this step...there's no real need to get them booting from the Vista bootloader, anyway, since BootIT NG is able to boot all 3, without hassle. But I'm the type of person that likes to have a backup option (or option**s**!), a wild card to play, in case anything goes wrong...no need to take any chances, I say! I prefer not to put my trust in any one single thing as a matter of habit, and this is why I set out to get all 3 booting from the Vista bootloader as well. If you're like that too, then this step if for you...

Boot into Vista. Download and install EasyBCD from here: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) 
And then open it up, and select the NeoGrub tab in the &#8220;Add/Remove Entries&#8221; section of EasyBCD, and push the &#8220;Install NeoGrub&#8221; button, which should then change to display &#8220;Remove NeoGrub&#8221; in its place. Now right beside &#8220;Remove NeoGrub&#8221;, you should see a button called &#8220;Configure Neogrub&#8221;. Click this button, and the NeoGrub menu.lst file should open, which is where we will add Ubuntu to the Vista bootloader, via NeoGrub. If you did everything right, you should now see something like this in the NeoGrub menu.lst file:
```

# NeoSmart NeoGrub Bootloader Configuration File 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 

#This is a comment. Comments are prefixed with a '#' 

default 0		#Pick the task to be run if the user doesn't pick one within the time limit. 
timeout 10		#Give the user 10 seconds to choose a task. 

#We use the "title" keyword to indicate a new entry in the menu.

```

Now what you're going to do here is add both Windows XP and Ubuntu 8.10 to the NeoGrub menu.lst. We will also add an boot entry for XP in the Vista bootloader itself, which will allow you to boot directly from the Vista bootloader, instead of having to go through the NeoGrub boot menu, which means the direct boot entry is more convenient, and technically means you don't really need to have an entry for XP in the NeoGrub menu.lst file...but to my way of thinking, at least, its better to have as many methods of booting at the same time as you possibly can, just so you'll always have a backup in case something ever goes wrong. And of course there's also the added advantage of being able to go to either XP or Ubuntu from NeoGrub, meaning that if you change your mind on which you want to boot into, after selecting NeoGrub, you wont have to reboot in order to boot into XP....you'll be able to boot into the other one from within the NeoGrub boot menu, making it far more convenient! The same thing can also be said about the BootIT NG boot menu. You can choose to boot directly into any of the 3, or you can choose Vista, which will send you to the Vista bootloader, and from there, if you change your mind about which one you want to boot, you will be able to boot into either Ubuntu or XP, without having to reboot!

Now you're going to enter the following text in your NeoGrub menu.lst, right after the above code. You can either manually type it (as long as you make sure that you copy it word for word) or can simply copy it and paste it in your NeoGrub menu.lst on the line right below the above code, which is of course easier. Copy this:
```

title 		Windows XP	#This is our first entry - it's number 0 
find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root. 
makeactive  			#Make this the active partition 
chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader 
#If we're using a menu, we don't need to use the `boot` command - it's automatically implied. 

#This is our second entry 
title Ubuntu Linux 
root (hd0,3) #Load Ubuntu from the 1st harddrive's 4th partition. 
chainloader +1 
#End Ubuntu entry 

#That's it! 

```

Now save the file, and then exit it, and then reopen EasyBCD (if you closed it). Now once again go to &#8220;Add/Remove Entries&#8221;, only this time choose the Windows tab, and then pick &#8220;Windows NT/2k/XP/2k3&#8221; in the drop-down menu, and then push the &#8220;Add entry&#8221; button, which should then create a boot entry for XP in your Vista bootloader. At this point, you should check your boot entries by clicking on the &#8220;View settings&#8221; tab, and then looking at the window on the right, which will display an orderly layout of the entries in your Vista bootloader, shown as &#8220;Entry #1&#8221;, &#8220;Entry #2&#8221;, etc. Verify that both the XP entry and the NeoGrub bootloader entries exist in this window, and then close EasyBCD.

Now open up &#8220;Computer&#8221; in the Start menu, and navigate to your D drive, which houses your XP installation, and find your &#8220;boot.ini&#8221;, &#8220;ntldr&#8221;, and &#8220;NTDETECT.COM&#8221; files, which should be in the main folder of that dir. Now copy this over to your C drive, which houses Vista, and place it in the main dir of C. Now close your &#8220;Computer&#8221; window, and then open up your Notepad application, in the Start menu, located in the &#8220;Accessories&#8221; folder in your &#8220;All Programs&#8221; menu. Only run it as Administrator, by right-clicking on it, and selecting &#8220;Run as Administrator&#8221; in the drop-down menu. Next, go to the File tab in the Notepad application and click &#8220;Open&#8221;, and in the dialog box that opens navigate to your C:/ root directory, and then open up your boot.ini file. In Vista, I believe it only shows the filename, though, not the extension, and so you're probably looking for the &#8220;boot&#8221; System Configuration File, rather than &#8220;boot.ini&#8221;, though that's actually what it shows in XP. Now replace (not add) what's in it with this:

```

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
/NOEXECUTE=OPTIN /FASTDETECT

```

[COLOR="Green"](It is now possible with EasyBCD 2.0, Build 53 (or later) to have EasyBCD automatically configure your boot.ini for you, by simply going to Tools>Auto configure boot.ini, and clicking 'Yes' when it asks you if you want it to automatically configure boot.ini for you, which is highly recommended.
Here's the link: [http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642))
[/COLOR]
Save and exit the file. Now let me explain what you just did in as simple of terms as possible...

You instructed the EasyBCD engine to add two new boot entries to your Vista bootloader...one for XP, and the other one for Ubuntu (using NeoGrub). And then you configured them, so that each would point to their respective partition to boot from. By adding the above text to the NeoGrub menu.lst file, you instructed NeoGrub on how to find the correct partitions, and their boot files. And of course by replacing what was in the boot.ini file (which was originally in XP), which you copied over to Vista, with the new text, you told boot.ini to pass over the &#8220;baton&#8221;, if you will, to the next step in the boot process, specifically the &#8220;ntldr&#8221; file in Vista, which then boots the XP partition, with the help of the NTDETECT.COM file which detects and configures access to the various hardware components of your machine. However, if the partition numbers (e.g. &#8220;partition(1)&#8221; without the quotes, in the above text for boot.ini) in boot.ini were incorrect, your computer wouldn't be able to find the all-essential &#8220;ntldr&#8221; file in Vista, at startup, due to the wrong partition numbers being entered...which would of course result in one of the 3 following errors:

**1.** _Ntoskrnl.exe is missing or corrupt_ 

"[COLOR="Sienna"]Windows could not start because the following file is missing or corrupt:

<Windows root>\system32\ntoskrnl.exe.

Please re-install a copy of the above file[/COLOR]"

This means the ARC paths in the [operating systems] section or the default entry in BOOT.INI is incorrect. Double-check that multi() and disk() are both set to 0, and verify that rdisk(x)partition(y) points to the correct partition where Windows XP is installed. Instructions on the correct configuration of boot.ini can be found [here]("http://neosmart.net/wiki/display/EBCD/Rebuilding+Boot.ini").
**2.** _Hal.dll is missing or corrupt_

&#8220;[COLOR="Sienna"]Windows\System32\Hal.dll missing or corrupt:

Please re-install a copy of the above file.[/COLOR]&#8221;

This means the ARC paths in the [operating systems] section or the default entry in BOOT.INI is incorrect. Double-check that multi() and disk() are both set to 0, and verify that rdisk(x)partition(y) points to the correct partition where Windows XP is installed. Instructions on the correct configuration of boot.ini can be found [here]("http://neosmart.net/wiki/display/EBCD/Rebuilding+Boot.ini").
(Actually, in my case this error was due to a corrupt &#8220;ntldr&#8221; file in XP, though I was trying to boot from BootIT NG, which depends on the boot files in XP, instead of from the Vista bootloader entry created by EasyBCD, which depends on the boot files in Vista, copied over from XP)

**3.** [U]Windows could not start because of a disk hardware configuration problem
[/U]
&#8220;[COLOR="Sienna"]Windows could not start because of a computer disk hardware configuration problem. Could not read from the selected boot disk.

Check boot path and disk hardware. Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.[/COLOR]&#8221;

This means the ARC paths in the [operating systems] section or the default entry in BOOT.INI is incorrect. Double-check that multi() and disk() are both set to 0, and verify that {{rdisk(x)partition(y)}}points to the correct partition where Windows XP is installed.
Generally speaking, this particular error message means that the partition referenced in the ARC paths in boot.ini does not exist, so check the partition() number first. If you're sure the partition() value is correct then try different rdisk() values until you get a working configuration. Further instructions on the correct configuration of boot.ini can be found [here]("http://neosmart.net/wiki/display/EBCD/Rebuilding+Boot.ini").

(In my case, this particular error was due to a partition number being entered in boot.ini, which did not exist...or at least in the MBR. I had placed &#8220;partition(6)&#8221; there, while I was still trying to figure out how to get it working, because it was the actual sixth partition, speaking of course in terms of hard drive sectors. It was not until later that I learned that boot.ini goes solely by the MBR, so one would have to enter the number of the partition in the MBR in boot.ini, e.g. partition 1, counting of course from top to bottom in the &#8220;View MBR&#8221; window in BootIT NG)

There is also an alternate method of adding Ubuntu to the Vista bootloader, which I describe in the following sub-step.

[SIZE="4"][COLOR="Blue"]**Sub-step #5 (How to add Ubuntu to the Vista bootloader, as a direct boot entry): **[/COLOR][/SIZE]
Here's an alternate method of booting Ubuntu from the Vista bootloader...directly, without  using NeoGrub, which requires another menu to get through (which can sometimes become annoying). While still in Vista, open up EasyBCD again (if you closed it), and navigate to the "Useful Utilities" section of EasyBCD, and click on the "Power Console" button. Now run the following commands (being sure of course to push Enter after each one) in the Command Prompt that opens up:
```

bootpart
bootpart 4 C:\ubuntu.lnx Ubuntu Linux

```
This should tell the Bootpart application that came along with the EasyBCD package where to find Ubuntu, when you select the entry you just created, at startup. Now reboot, select Windows Vista to boot from, in the BootIT NG boot menu, and you should see the following entries in the Vista boot menu:

[COLOR="Blue"]Microsoft Windows Vista[/COLOR]
[COLOR="Blue"]Ubuntu[/COLOR] (if you had Wubi, that is)
[COLOR="Blue"]Microsoft Windows XP[/COLOR]
[COLOR="Blue"]NeoGrub Bootloader[/COLOR]
[COLOR="Blue"]Ubuntu Linux 
[/COLOR]
The last entry should boot right into your real (not Wubi) Ubuntu, when you select it. The Window XP entry should of course allow you to boot directly into XP as well, though (depending on how new your computer is) you might get a BSOD &#8220;stop error&#8221; the first time you attempt it. If you do, it is because your XP installation doesn't support AHCI operating mode of your SATA controller, which is why I described how to change the setting from AHCI to ATA in Step #4. To fix this (since you will be using AHCI at this point) you will need to change back (at least, temporarily) to ATA operating mode, which will then allow you to boot into XP, but not into Vista...which is of course a serious drawback, and one to which I am still trying to find a solution for. Hopefully, though, in your case, you will not have this problem, and your XP CD will either come with the AHCI driver for XP already included (which in my case it didn't), or you will simply not have AHCI, which means your Vista installation will probably have a ATA driver pre-installed, and so you will simply be able to install XP and boot into it without all the hassle of having to change the SATA settings in BIOS.

The NeoGrub boot entry will bring you to another boot menu, specifically NeoGrub, which should now have two boot entries to select from: Windows XP and Ubuntu Linux

[SIZE="5"]**How to revert back (if necessary):**[/SIZE] I'm providing this step in order to meet the criteria specified in the sticky in the "Tutorials and Tips" forum for tutorials. I will explain how to undo all the changes you made to your computer (including installing XP and transferring Ubuntu to a dedicated partition) when you tri-booted, so that it will be the same as before following this tutorial. Fortunately, the process of undoing the changes you made is much easier than making the changes in the first place! And so this will only take a few minutes. Ok, so here is what you're going to do:

[B][U]Use EasyBCD to delete the entries in the Vista bootloader
[/U][/B]
[LIST=1]
[*]Boot into Vista
[*]Open up EasyBCD
[*]Go to Add/Remove Entries
[*]Select the XP entry
[*]Click the "Delete" button to remove the entry for XP
[*]Select the Ubuntu (real, not Wubi) entry 
[*]Remove it as well
[*]Select the NeoGrub tab
[*]Click the "Remove NeoGrub" button to remove NeoGrub
[/LIST]
**_Delete your XP boot files that you copied to Vista_**

Go to your "C" drive, root directory, and simply delete the "boot.ini", "ntldr", "NTDETECT.COM" files

**_Delete your XP and Ubuntu partitions_**

[LIST=1]
[*]Reboot, and enter into "Maintenance" mode again in BootIT NG
[*]Open up Partition Work
[*]Select your XP partition
[*]Click the "Delete" button on the right side of the window to delete it, after which it will become "free space"
[*]Select the Ubuntu partition
[*]Delete it as well
[*]Remain in Partition Work, and proceed to next step
[/LIST]

**_Expand your Vista partition so that it reclaims the free space_**

[LIST=1]
[*]Select your Vista partition, while still in Partition Work
[*]Click the "Resize" button on the right of the window
[*]Select the Max size to resize it to, which will be displayed in the "Resize" dialog box
[*]Click "Ok" and then "Continue" to resize it
[*]Reboot
[/LIST]

[B][U]Uninstall BootIT NG
[/U][/B]
[LIST=1]
[*]Enter the BIOS
[*]Put the CD/DVD drive first in the drive order
[*]Insert the BootIT NG CD
[*]Select Save/Exit in the BIOS to quit the BIOS
[*]Once your computer boots with the BootIT NG CD, select the "Uninstall BootIT NG" option to uninstall
[*]Reboot
[*]Enter the BIOS
[*]Eject the CD
[*]Put the CD/DVD drive back to its former place in the drive order
[*]Select Save/Exit to quit the BIOS again
[/LIST]
**_Check to make sure everything is like it was before_**

[LIST=1]
[*]Once leaving the BIOS, you should go straight to the Vista bootloader menu, since you uninstalled BootIT NG
[*]Boot into Vista
[*]Check to see if everything looks ok
[*]Reboot
[*]Boot into your Wubi install of Ubuntu (assuming of course you didn't uninstall it, after transferring your Wubi install to a dedicated partition)
[*]Check to make sure everything's ok in Ubuntu
[/LIST]

That's it! You should now have everything the way it was before following this tutorial! 

**[SIZE="5"]Sources:[/SIZE]** 

Here's a list of the sources where I obtained a lot of this information...just to give credit! :D 

At:

[http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub) (the EasyBCD documentation on NeoGrub)
[http://neosmart.net/wiki/display/EBCD/Windows+XP](http://neosmart.net/wiki/display/EBCD/Windows+XP) (Windows XP - NeoSmart Technologies Wiki)
[http://neosmart.net/wiki/display/EBCD/Troubleshooting+Windows+XP](http://neosmart.net/wiki/display/EBCD/Troubleshooting+Windows+XP) (Troubleshooting Windows XP - NeoSmart Technologies Wiki)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) (Ubuntu - NeoSmart Technologies Wiki)
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) (A screenshot-based guide on how to install LVPM, and transfer a Wubi install with it)
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) (A tutorial on transferring Wubi with LVPM)


[SIZE="4"]**Tested on:**[/SIZE] This tutorial was tested on a newish Dell Studio 1535 laptop by me personally, so I know these procedures will work. Obviously though, each individual's situation might be different, and require slight modification of the steps described in the tutorial, in order to make it work. Vista was pre-installed on my laptop, and XP was installed later as a dual boot, and then even later my Wubi install was transferred to a dedicated partition with LVPM, and the Vista bootloader configured to boot all 3...though getting one OS to boot fine was not necessarily done at the same time as the other. Actually, to tell the truth, I can't recall exactly in the order that these steps were taken, but this tutorial was written with the objective of making the process as easy as possible...that is why the order of the steps might have been slightly different when used by me, but only because back then I was still learning. Now with all that behind me, I wanted to make the tutorial as easy to follow, and the least difficult as possible, which means the order that the steps were done might be slightly different than the order that I did them in, though the processes are the same.

[SIZE="4"]**Credits:**[/SIZE] A special thanks goes to Meierfra, Mkoyle, Makaveli213, Terry60, PC Eye, and others who assisted me with tri-booting my own computer, using BootIT NG.

[SIZE="4"]**Disclaimer:**[/SIZE] This is by no means an advertisement for BootIT NG in any way, nor is it an attempt to get users to prefer BootIT NG over Gparted. Rather it is an accounting of my own (good) experiences with tri-booting, using the program, and which I typed up for the purpose of helping others achieve the same goal with less trouble. I support open-source software as much as the next person, and I also think Gparted is great for most purposes. However, in my opinion, at least, it didn't fit the requirements that I requested of it, and that is the reason I chose to use BootIT NG (a commercial product) instead. Anyone who reads this tutorial should not get offended, or feel any need to point out that Gparted is free, while BootIT NG isn't...because I already know that very well. Again, I think Gparted is great, and that most users should continue to use it. With that said, I can safely say this tutorial was only written for the intent of helping others who may also wish to use it for the same purpose I did. I am by no means trying to elevate BootIT NG above Gparted in terms of value. Users on this forum can use what they like. 

**[SIZE="5"]Feedback:[/SIZE]** Feel free to report back with any questions or comments that might be on your mind, or anything that you feel needs any changing in my tutorial. I will gladly assist you in any way I can, to resolve any problems that might come up.

------------------------------------------------------------------------------------------------------------


[B][SIZE="6"]Addition to original tutorial (How to do other things with BING):[/SIZE]
[/B]
This is an addition to the original tutorial, and can be considered as add-ons to my original theme of thought. :smile: I will continue to provide information for other aspects of booting with BING here in this section for the purpose of expanding my tutorial, and providing the means of doing other things with BING not previously discussed. If someone wishes me to add how to do a particular something to the tutorial, this is where I'll put it, nowhere else. I imagine you'll see quite a few new things here in the next few days... 
You would be surprised at all the different things BING can do! It is not merely a bootmanager, with the capability to also do partition work. There's tons of more things it can do, some I have not even discovered yet. I will add more things here as I learn about them.

Well, here's the first few...

**[SIZE="5"]How-to boot an OS on an alternate hard drive with BING:[/SIZE]**

If anyone wants to know how to use BING to boot OSes on other drives, here are the steps:

(I will assume the OS(es) has/have already been installed, and you did not limit primaries)
_**Step 1:**_ Install BootIT NG if its not already installed. See Step #1 of the original tutorial above on how to install it.

_**Step 2:**_ Reboot, and when you get to the BING boot menu, click on the "Maintenance" button to get to the BING desktop. From there, click on "Boot Edit".

_**Step 3:**_ In the dialog box that appears after clicking on the Boot Edit button on the BING desktop, click "Add" which will open up another dialog box in which you can select all the various options for the new boot entry you're creating in the boot menu. 

_**Step 4:**_ Click on the appropriate drive (I chose Drive 1 for this example) under "Drive" on the left, so that the radio button gets placed on that drive instead of Drive 0. Now, in the "Boot" field you see also on the left side of the window, click on the downward arrow to open up a drop-down menu which displays all the available partitions on that hard drive (whether primary or logical). Next, simply select whatever partition contains your OS (or in the case that the boot files for the OS is on a separate partition, then select the partition that contains the boot files instead), and in the "Name" field above it, fill in whatever name you wish the new boot entry to have. Next, in the "MBR Details" section on the right, you will see the partitions that "exist" currently for that entry in the MBR (theoretically, of course...since the MBR doesn't actually get updated to match those MBR Details shown there until you select that boot entry at boot time), which should just be the boot partition. Now select the top space of Drive 1, and click on the "Fill" button on the far side of the window, on the right, next to the MBR Details, which will open up another dialog box showing the available partitions you can add to that particular slot in the MBR. Select whatever partition you want to add to that slot, and click Ok. Now do the same for the other 2 slots remaining for Drive 0, and add two more partitions for this entry. Keep in mind that the partitions added here will affect which partitions get shown in the booted OS. If you don't want a particular partition (such as Vista's) to show up in the booted OS (such as XP), then just refrain from adding it in the MBR Details for that entry, and it will not show up in the OS. Conversely, of course, the partitions you **do** want to show up in the OS will need to be of course added to the slots of drive 1 in the "MBR Details". Move the entries up or down as deemed appropriate, taking care to note the particular slot each partition is in, which could benefit you later. Up to 4 partitions can exist in the MBR of a particular drive at a time (in this example drive 1). Do the same for Drive 0, only in this case you can leave **all** of the slots empty, if you wish, since it is Drive 1 you will be booted from, and the boot partition is on Drive 1. Next, check the box titled "Swap", and you're done. When you're satisfied with the details you selected for that particular boot entry, click "Ok" at the bottom of the Boot Edit window to accept the configuration and add the entry. Click "Resume" on the BING desktop to access the boot menu again, and then click on the new entry you created to boot into the OS.

DONE! :lolflag: 
Remember though that those steps are for booting OSes that have *already* been installed. If you still needed to install the OSes you wanted to boot with BING, then the steps would be a bit different, and I would advise you differently, since BING has its own special procedure it can perform that is best for that case. Also, keep in mind that those steps only work if the boot files (such as boot.ini in the case of XP) have been configured correctly before-hand, and are in the correct place needed in order to boot the OSes. BING has the capability to allow editing of important boot files (such as boot.ini or the BCD store that Vista uses) **directly** from the program, so any necessary changes can be made from BING itself. To learn more about these features, read the following two sections. 

**_To edit boot.ini or other small text files from within BING itself:_**

    1.  Go to the BootIt NG desktop (by clicking on the "Maintenance" button found at the bottom of the boot menu you see when you reboot), and click on the **Partition Work** icon.  The "Work with Partitions" window appears.

    2.  Using the radio buttons on the left side of the Work with Partitions window, select the appropriate hard drive.

    3.  Double click the partition that contains the text file you would like to edit (or click the partition once to select it, and then click the Properties button). For this example, select the partition that contains an XP installation. The Properties dialog appears.

    4.  Click the **Edit File** button on the Properties dialog.  The Open dialog appears.

    5.  Select the desired text file, either by manually entering the desired path and/or file name (using the MS-DOS 8.3 file naming convention), or by double clicking the appropriate folder and/or file names. For this example, pick the file called "boot.ini" without the quotes. The "Edit File" window appears.

    **Note:** If you see the message "File Truncated!" upon trying to open a file, it means that the selected file was either in binary format, or over 32-KB in size.  In this case, your only option is to click **Cancel**.

    6.  View or edit the file as desired.  Click **OK** to save your changes, or click **Cancel** to abandon them.

[B][U]To edit the BCD file from within BING itself
[/U][/B]
   1. Click the **Partition Work** icon on the BootIt NG desktop (or press Alt+W).  The "Work with Partitions" window appears.

   2. Select the appropriate drive using the radio buttons on the left side of the "Work with Partitions" window.

   3. Select the appropriate partition (it will usually be the topmost one), and then click the **Properties** button (or double click the partition).  The partition's "Properties" window appears.

          * If the correct partition has been selected, a **BCD Edit** button will appear near the bottom of the "Properties" window.  If the **BCD Edit** button does not appear, the partition does not contain a BCD.

   4. Click the **BCD Edit** button.  The "BCD Edit" window appears.

[B][COLOR="Red"]Important BCD Settings
[/COLOR][/B]
To boot Windows Vista, ensure that your BCD is configured as follows:

[U][B][COLOR="Blue"]Menu Entries
[/COLOR][/B][/U]
   1. Select the "Menu" radio button on the left side of the "BCD Edit" window.  An entry titled "Microsoft Windows Vista" should appear in the "Items" list.

   2. Select the Microsoft Windows Vista item, and then click the **Edit** button (or double click the "Microsoft Windows Vista" item).  The properties of the "Microsoft Windows Vista" item will appear in a new window.

   3. Select the "Device" entry from the list of Properties, and then click the **Edit** button (or double click the Device entry).  The "Edit" window appears.

   4. In the upper "Type" drop-down list, select the hard drive number on which Windows Vista is installed.

   5. In the lower "Type" drop-down list, select the partition on which Windows Vista is installed.

   6. Click **OK** in the "Edit" window.  You will be returned to the window showing the properties of the "Microsoft Windows Vista" item.

[COLOR="Red"]**Note:**[/COLOR] Repeat steps 3 - 6 for the OS Device entry (i.e. in step 3, select the OS Device entry).  When done, click **Close** to return to the BCD Edit window.

[U]**[COLOR="Blue"]Boot Entry[/COLOR]**
[/U]
   1. Select the "Boot" radio button on the left side of the BCD Edit window.  An entry titled "Windows Boot Manager" should appear in the "Items" list.

   2. Select the "Windows Boot Manager" item, and then click the **Edit** button (or double click the "Windows Boot Manager" item).  The properties of the "Windows Boot Manager" item will appear in a new window.

   3. Select the "Device" entry from the list of Properties, and then click the **Edit** button (or double click the "Device" entry).  The "Edit" window appears.

   4. Generally, you should have **{boot}** selected in the upper "Type" drop-down list.  In this case, the lower "Type" drop-down list will be unused and inaccessible.  However, if necessary, you may use the upper "Type" drop-down list to select the hard drive number on which the BCD resides (i.e. the hard drive where the file bootmgr can be found).

   5. If you have a specific hard drive selected in the upper "Type" drop-down list, you must also select the partition on which the BCD resides for the lower "Type" drop-down list.

   6. Click **OK** in the "Edit" window.  You will be returned to the window showing the properties of the "Windows Boot Manager" item.

When done, click **Close** in the Windows Boot Manager properties window, click **Close** on the "BCD Edit" window, and then click **OK** in the partition "Properties" window.


[SIZE="5"]**How-to protect Vista's system restore points from XP (by hiding Vista's partition, of course):**[/SIZE]

If anyone wants to know how to protect Vista's system restore points from XP (since XP deletes them), here's the procedure:

**_If you want to know how to install XP with Vista hidden from both the XP installation setup, and also the installed XP when it is booted_**
[LIST=1]
[*]Reboot
[*]Press F2 or similar at startup to access your system BIOS
[*]Put your main internal hard drive as **first** in the boot sequence order
[*]Put your CD/DVD drive as **second** in the boot sequence order
[*]Save the changes, and exit the BIOS
[*]When you get to BING's boot menu, click on the "Maintenance" button to get to the BING desktop
[*]Click on "Partition Work"
[*]In the "Work with Partitions" window that appears, select a partition you can afford to lose a little free space of
[*]Click on the "Resize" button on the right-hand side of the "Work with Paritions" window
[*]Resize the partition to a size of your choosing
[*]Create a new FAT 32 or NTFS partition out of the space you created
[*]Exit the "Work with Partitions" window
[*]On the BING desktop, click on "Boot Edit"
[*]In the dialog box that appears, click on "Add"
[*]Select the partition that you just created in the "Boot:" field
[*]In the "MBR Details" of that window, select an empty slot, and click on the "Fill" button
[*]Add the partition of your choosing to that empty slot (after first verifying that it is not Vista's partition)
[*]Do the same for the other 2 empty slots for that drive in the "MBR Details", taking care **not** to add Vista's partition
[*]Select the "Swap" option
[*]Click Ok to create the new entry
[*]On the BING desktop, select "Resume" to access the boot menu again
[*]Insert the XP installation CD
[*]Select the new entry you just created, and push Alt + N to use the **Boot Next Device** function
[*]When your computer gives you the message "Press any key to boot from the CD" press a key
[*]When the XP installation setup gets to the point when you select a partition, select the partition you created in BING for, and choose to install XP there
[*]After XP is installed, go to "My Computer" in the Start menu to verify that Vista's partition does indeed not show up there. If it doesn't, then you know you are in business. If for some reason, though, Vista's partition is indeed shown there, then you did something wrong, and did not follow my specific instructions. Assuming you did everything right, Vista's partition should not exist in "My Computer", and every time you select that entry at boot time, Vista will be hidden, and therefore its restore points will remain safe
[/LIST]
**Note:** The above instructions are only for installing XP to the main internal hard drive. The steps would be a bit different if you wished to install to an alternate hard drive. Also, keep in mind that those instructions are for hiding Vista from XP when you are **not** limiting primaries.

**_If you wish to know how to hide Vista from an existing XP when XP is booted, so as to protect Vista's system restore points, and you DO happen to be limiting primaries, so that you can only have 4 primary partitions per hard drive_**

[LIST=1]
[*]Reboot
[*]At the BING boot menu, click on the "Maintenance" button to get to the BING desktop
[*]Click on "Boot Edit"
[*]In the dialog box that appears, select the existing XP entry
[*]Click on the "Edit" button on the right
[*]In the window that appears, select the Vista partition shown in the "MBR Details" on the right-hand side
[*]Click the "Hide" button to hide Vista's partition from XP when that entry is booted
[*]Click Ok to accept the changes, and exit the window
[*]Click on "Resume" on the BING desktop to get to the boot menu again
[*]Select the XP entry, and push Enter
[*]When XP is booted, go to "My Computer" in the Start menu, and verify that Vista's partition does not show up there. If it does, then you must have selected the wrong partition to hide, and you will need to perform the whole outlined procedure again, this time making sure it is **Vista's** partition you are hiding, and not some other partition. If it is hidden, then you know it worked, and you are finished.
[/LIST]

---

### Post by creek23 on 2009-01-03
Tremendous, detailed tutorial. I see you really gave effort for this tutorial.

But I don't see why people would tri-boot Ubuntu with XP and Vista. An Ubuntu, XP and Opensolaris, would be better.

---

### Post by Jammanuser on 2009-01-03
> **creek23 said:**
> Tremendous, detailed tutorial. I see you really gave effort for this tutorial.
Thanks for the compliment. :D I tried to make it as detailed as possible, and its nice to hear someone else feels the same way. :) 
> **creek23 said:**
> 
But I don't see why people would tri-boot Ubuntu with XP and Vista. An Ubuntu, XP and Opensolaris, would be better.

That is just what i did. I figure that if someone wants to use different OSes, then they can always ignore the specific instructions for installing XP and/or Ubuntu, and simply follow the rest of the tutorial. I certainly hope that someone finds something of value in this tutorial...especially since i spent a great deal of time typing it up! ;)

Cheers! :)

-Jam man

:guitar:

---

### Post by jpeddicord on 2009-01-12
Moved to Tutorials & Tips. [(ref)]("http://ubuntuforums.org/showthread.php?p=6539236#post6539236")

---

### Post by Jammanuser on 2009-01-12
> **jacobmp92 said:**
> Moved to Tutorials & Tips. [(ref)]("http://ubuntuforums.org/showthread.php?p=6539236#post6539236")

Great! Thank you very much. :D

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-12
Update: I just added the defraging process to the tutorial, since i realized i had forgotten to include it before! :) Defraging your Vista partition is **essential** before resizing it, as #1 it will help prevent data loss, and #2 make the resizing process that much quicker.

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-01-17
Update: I forgot to mention before to download Bootpart and extract to C: before running the bootpart commands in the Command Prompt, as they will not work with the version of Bootpart that is included in the EasyBCD package. 

-Jam man

:guitar:

EDIT: Never mind...I found out how to use the one that's installed with EasyBCD. Updated tutorial.

---

### Post by Jammanuser on 2009-02-16
Updated tutorial again. :) EasyBCD (2.0 Beta, Build 53) can now **automatically** configure boot.ini for you, so you wont have to. Additionally, if it detects that boot.ini is not in the "system" root, it will create its own boot.ini (and configure it correctly, automatically), placing it in the correct place, and also give you the link to download the "ntldr" and "NTDETECT.COM" files from the NeoSmart site, in case you're missing them.

Will keep everyone posted of further developments.

-Jam man

:guitar:

---

### Post by jimscafe on 2009-02-22
I have been using BootIT NG for 2 years now and I love it.

In fact I have a 500GB hard drive with 5 versions of XP installed. 
One for my work (python development)
One for accessing the intnernet - no risk of avirus on my work XP
One for games etc - no firewall needed to play lan games
One for experimentation - which can easily be discarded
One as a 'vanila' install with alldrivers etc so I can easily re-create any of the above.

Then I have slackware linux installed which I find very good as a server

I want to install ubuntu but I need to be able to install grub to the boot partition (like I did with lilo in slackware) and not the mbr. I think your tutorial has explained how to do that - by first installing to the mbr, re-instal bootit ng then go into ubunut via the cd and put grub into the boot sector.

Not sure why ubuntu doesn'r provide this option at normal instal.

---

### Post by Jammanuser on 2009-02-22
> **jimscafe said:**
> I have been using BootIT NG for 2 years now and I love it.

In fact I have a 500GB hard drive with 5 versions of XP installed. 
One for my work (python development)
One for accessing the intnernet - no risk of avirus on my work XP
One for games etc - no firewall needed to play lan games
One for experimentation - which can easily be discarded
One as a 'vanila' install with alldrivers etc so I can easily re-create any of the above.

Then I have slackware linux installed which I find very good as a server

I want to install ubuntu but I need to be able to install grub to the boot partition (like I did with lilo in slackware) and not the mbr. I think your tutorial has explained how to do that - by first installing to the mbr, re-instal bootit ng then go into ubunut via the cd and put grub into the boot sector.

Not sure why ubuntu doesn'r provide this option at normal instal.

Hi. :) Isn't BootIT NG AWESOME?! If only it got the credit it deserves...;)
Grub installs to the MBR when you're using *LVPM* to transfer a Wubi install to a dedicated partition. That is the default behavior of LVPM, and so far I have not learned of a way to change it. As you seem to be aware of, that will make BING unbootable, because the bootloader (as well the EMBR-extended master boot record) that BING uses gets overwritten by Grub, since they apparently both occupy the same place in the MBR. That I learned the hard way (though now after having read the Terabyte Unlimited articles on BING, I learned that that was covered there; if I only had read it before...:o). 
You can specify where to install Grub if you're using a LiveCD to install Ubuntu, and not an Alterate CD, by selecting the "Advanced" option at installation of Ubuntu. Choose a location like /dev/sda**1** and not just /dev/sda because the first specifies the first partition of the first drive, while the second only says install it to the first drive, and doesn't specify a partition, so it gets installed to the MBR by default. See this article for more information on installing Ubuntu when using BING:
[http://www.terabyteunlimited.com/kb/article.php?id=279](http://www.terabyteunlimited.com/kb/article.php?id=279)

GL and let me know if you have any problems. :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2009-03-02
Edited first post with this post's information.

---

### Post by Jammanuser on 2009-03-03
Update: added two new how-tos to tutorial. See Post #1.

---

### Post by Jammanuser on 2009-03-04
I just realized I had forgotten to include in the original tutorial how to create the bootable disk for BING in Linux, as well as Windows. :shock: Problem fixed and tutorial updated...once again. :rolleyes:

-Jam man

:guitar:

---

### Post by peakpc on 2010-07-10
I've been using Bootit NG for more years than Ubuntu (10). It's a great backup, imaging tool that can be used for free (live cd) if you don't load it. I have loaded it ($35) and use it as bootloader for all dual booting (2,3 or 4 OS'es at times) it also allows for more than 4 primary partitions (can't use gparted if you do). I like to make regular images before major updates so, if something goes wrong I can just roll it back. This is good for experimentation and a good fresh start for windows (about once a year).

---

### Post by Jammanuser on 2010-07-10
Wow, this thread is like ancient... :D
I'm learned so much more about multibooting (not just with BING, but with the Microsoft boot manager as well as Grub) by now. 
I probably could rewrite this thread from scratch, and make it a more generic tutorial (i.e. not for just multibooting Windows with Ubuntu). I may do that too, when I get the time.

@peakpc: I'm glad that you think its a cool tool too. I really like it, but I know that it being propriety software may discourage some people from trying it. Some day I may make my own (free) software similar to BING, once I get really good at programming in C++ as well as other languages.

Cheers.

-Jam Man

:guitar:

---

### Post by foobaka on 2010-11-21
dead thread i suppose. hopefully by chance through this, i can grab some help. 

basically uh, i have a netbook with ubuntu 10.10 installed on it, i recently used BootIt NG to attempt to clear the ubuntu partitions on it. 

though, now i'm clueless as to how to set the file system up for a harddrive [initial intent is to make it for a windows xp OS]. i've tried creating a 11/bh fat32 and a 7/7bh ntfs but had no luck. when i booting windows xp from cddrom drive, it inspects drivers and such but comes to a screen where it says, 'setup did not find any hard disk drives installed in your computer'. i think the harddrive may need to be reconfigured. ~ thanks in advance, foo. :o

---

### Post by Jammanuser on 2010-11-23
> **foobaka said:**
> dead thread i suppose. hopefully by chance through this, i can grab some help. 

basically uh, i have a netbook with ubuntu 10.10 installed on it, i recently used BootIt NG to attempt to clear the ubuntu partitions on it. 

though, now i'm clueless as to how to set the file system up for a harddrive [initial intent is to make it for a windows xp OS]. i've tried creating a 11/bh fat32 and a 7/7bh ntfs but had no luck. when i booting windows xp from cddrom drive, it inspects drivers and such but comes to a screen where it says, 'setup did not find any hard disk drives installed in your computer'. i think the harddrive may need to be reconfigured. ~ thanks in advance, foo. :o
Interesting. 
I'm going to need more info:

1. You said you used Bootit NG to "attempt" to clear the ubuntu partitions on your netbook. Does that mean it failed?
2. Please explain the layout of your system (i.e. how many hard drives you have connected and/or inside your netbook, how many partitions on each HDD, etc.). 
3. When you used BootIt NG, I'm assuming you used it directly from the CD and did not install it to your hard drive? 
4. If BING succeeded in wiping Ubuntu off of your system, is there any other OS on there at the moment (in other words, were you multibooting before removing Ubuntu)?
5. Please give a detailed description of the procedure you did with BING, not just simply say that you attempted to wipe the Ubuntu partitions with it. Since BING is a powerful program, and has many features, not just the ability to wipe a partition, I want to know what else you may have done with BING, if anything. I also want to know if you deleted the partition(s) or if you just reformatted them.

That will give me a fairly good idea of your situation, and may help me help you solve your problem. ;) Keep in mind that if there are no partitions left on your computer, you can always use BING from the CD to create one, format it as FAT 32, and then you'll be able to install Windows XP onto it.

Cheers.

---

### Post by foobaka on 2010-11-24
hi, yey it's not a dead thread yet. =P thanks so much for your response. and sorry for the late response, kind of lost hope due to lack of responses since my first post on this thread. 

> 
1. You said you used Bootit NG to "attempt" to clear the ubuntu partitions on your netbook. Does that mean it failed?
*** #01. ***
well, i used it to clear the ubuntu partitions, and successfully did clear them, however i may have deleted ones that i shouldn't have? i don't know. there were 4 or 5 entries being Linux and linux native in the Partition_Work menu when i launched BootIt NG. i thought i just had to clear them all and then just create a new entry for windows ntfs. after clearing those, i've been attempting to re-create a single entry that's ntfs partition and thus the windows installation screen unsuccessful follows. 


> 
2. Please explain the layout of your system (i.e. how many hard drives you have connected and/or inside your netbook, how many partitions on each HDD, etc.).
*** #02. ***
the layout of the system is: it has (1) SATA 160GB internal as primary. it used to have 4 or 5 partitions, but currently only 1, and i intend to have only 1, i just wanted windows partition. in bios though, it does not show the hard drive at all. strangely enough, i've come across this second netbook that does not display hard drive information in bios. 

*the netbook Specifications:*
Brand: HP Mini
Model: 311-1000 NR
Processor Type: Intel (R) Atom(TM) CPUN270 @ 1.60GHz
Processor Speed: 1600 Mhz
Total Memory 1024 MB
Hard Drive: SATA 160GB Internal
Cd-Rom Drive: No


> 
3. When you used BootIt NG, I'm assuming you used it directly from the CD and did not install it to your hard drive?
*** #03. ***
the netbook i have does not have a cdrom drive, so i used a 2GB USB drive to run the BootIt NG off of, and i did not install it [read couple times in many places that they said you shouldn't try to install it on your hard drive whether they mean hard drive or usb i assumed it was the same in this case]. and the method i use to install  windows is that: since netbook does not have a cdrom drive, i use a usb to ide adapter and connect a ide cdrom drive into the usb port. and run the windows installation cd from there. 


> 
4. If BING succeeded in wiping Ubuntu off of your system, is there any other OS on there at the moment (in other words, were you multibooting before removing Ubuntu)?
*** #04. ***
there are no OS's on there at the moment, only a partition that i keep re-creating in hope that windows installation setup would work. the question of was i multi-booting, i cannot answer that since my friend's friend owned it but i bought it for cheap since he said he had linux installed on it and he didn't want to go to the hassle of uninstalling it linux and putting windows back. 


> 
5. Please give a detailed description of the procedure you did with BING, not just simply say that you attempted to wipe the Ubuntu partitions with it. Since BING is a powerful program, and has many features, not just the ability to wipe a partition, I want to know what else you may have done with BING, if anything. I also want to know if you deleted the partition(s) or if you just reformatted them.
*** #05. ***
well, on my PC, i downloaded bootit ng and made it to be bootable on usb drive. now, the netbook initially had ubuntu 10.10 netbook edition on it. so after booting up with the usb drive, it launched bootit ng, the screen that popped up was the Parition_Work. in there, there were about 4 or 5 MBR entries listed, majority being Linux or Linux Native. so i clicked Delete on _**all**_ the entries. after i cleared all, i created a new entry called, 'MBR Entry 0' and made the File System: 7/7h HPFS/NTFS and under additional information it said Bootable: NTFS and Cluster Size as 4096 bytes. after that, i clicked View MBR and clicked Set Active and Std MBR, and clicked Apply. afterwards, i clicked close, and rebooted the pc with the USB to IDE adapter and launched the setup for windows. 

it went to this screen first:
[http://i.imgur.com/4oTGj.png](http://i.imgur.com/4oTGj.png)

then it went to this screen: 
[http://imgur.com/9uvrS.png](http://imgur.com/9uvrS.png)

and with a different windows installation cd, 
it went to the first screen then this screen:
[http://i.imgur.com/eTSNB.png](http://i.imgur.com/eTSNB.png)

it kept doing that and so each time i tried something new and created a new MBR Entry after deleting the old entry that did not work, and this time used a different File System like for example: to 11/Bh: FAT-32 and so forth. 

couple um notes, i have not reformated the hard drive yet though only deleted partitions after creating and deleting. 

currently i created MBR ENTRY 0 and this is the screen shots for View MBR and Properties of the Entry.
[http://imgur.com/XkcSj.jpg](http://imgur.com/XkcSj.jpg)
[http://imgur.com/gexhY.jpg](http://imgur.com/gexhY.jpg)

also, i am able to unplug the SATA hard drive and plug it into my desktop as secondary / slave. the only folder that was on the hard drive was, 'System Volume Information'. so basically the hard drive can be read as a storage device but currently NOT as a primary hard drive. [i think the MBR is either corrupted / incomplete / and or invalid due to my idiocy].  

and, at some point, after plugging the hard drive as secondary in my dekstop pc, i ran TestDisk 6.1. and after a deep search it did  find the deleted linux partitions but it said it wasn't recoverable  anymore [i do not know why i had ran that or what my intent was].

heh, hope this is detailed enough. =P
thanks again!!! =P
~ foo

---

### Post by Jammanuser on 2010-11-26
> **foobaka said:**
> hi, yey it's not a dead thread yet. =P thanks so much for your response. and sorry for the late response, kind of lost hope due to lack of responses since my first post on this thread. 

*** #01. ***
well, i used it to clear the ubuntu partitions, and successfully did clear them, however i may have deleted ones that i shouldn't have? i don't know. there were 4 or 5 entries being Linux and linux native in the Partition_Work menu when i launched BootIt NG. i thought i just had to clear them all and then just create a new entry for windows ntfs. after clearing those, i've been attempting to re-create a single entry that's ntfs partition and thus the windows installation screen unsuccessful follows. 

Hmm...too bad. I would have kept Linux on there, and just resized one of your Linux partitions to make room for your Windows partition, and multibooted. With BING as your boot manager (though you would have needed to install it your HDD) you could have easily created a boot menu which would have given you options to boot into either Windows or one of your Linuxes at startup (since Linux is more reliable and stable than Windows ;) ). But oh well.
> 
*** #02. ***
the layout of the system is: it has (1) SATA 160GB internal as primary. it used to have 4 or 5 partitions, but currently only 1, and i intend to have only 1, i just wanted windows partition. in bios though, it does not show the hard drive at all. strangely enough, i've come across this second netbook that does not display hard drive information in bios. 

*the netbook Specifications:*
Brand: HP Mini
Model: 311-1000 NR
Processor Type: Intel (R) Atom(TM) CPUN270 @ 1.60GHz
Processor Speed: 1600 Mhz
Total Memory 1024 MB
Hard Drive: SATA 160GB Internal
Cd-Rom Drive: No


*** #03. ***
the netbook i have does not have a cdrom drive, so i used a 2GB USB drive to run the BootIt NG off of, and i did not install it [**read couple times in many places that they said you shouldn't try to install it on your hard drive whether they mean hard drive or usb i assumed it was the same in this case**].

That's ridiculous. I don't know who wrote that, but they were wrong. I have had BING installed on my own laptop's built-in HDD for about a year and a half now, and it has made my life a lot easier, and made multibooting Vista, XP, and Ubuntu 8.10 together much easier. Plus, its nice to have the ability to work on your partitions if you need to right before you boot into an OS, and not have to worry about finding and putting in the CD. To do that, all you have to do is click "Maintenence" on the BING boot menu, which will take you immediately to the BING desktop, then you just click "Partition Work" and it will bring up a dialog which will give you options to Create, Delete, Resize, Format, Move, as well as image. Not to mention, with BING as your boot manager, you can have more than 4 primary partitions on one HDD, and can boot into any one of them that has an OS installed onto it with BING. 
> 
 and the method i use to install  windows is that: **since netbook does not have a cdrom drive, i use a usb to ide adapter and connect a ide cdrom drive into the usb port. and run the windows installation cd from there.** 


*** #04. ***
there are no OS's on there at the moment, only a partition that i keep re-creating in hope that windows installation setup would work. the question of was i multi-booting, i cannot answer that since my friend's friend owned it but i bought it for cheap since he said he had linux installed on it and he didn't want to go to the hassle of uninstalling it linux and putting windows back. 


*** #05. ***
well, on my PC, i downloaded bootit ng and made it to be bootable on usb drive. now, the netbook initially had ubuntu 10.10 netbook edition on it. so after booting up with the usb drive, it launched bootit ng, the screen that popped up was the Parition_Work. in there, there were about 4 or 5 MBR entries listed, majority being Linux or Linux Native. so i clicked Delete on _**all**_ the entries. after i cleared all, i created a new entry called, 'MBR Entry 0' and made the File System: 7/7h HPFS/NTFS and under additional information it said Bootable: NTFS and Cluster Size as 4096 bytes. after that, i clicked View MBR and clicked Set Active and Std MBR, and clicked Apply. afterwards, i clicked close, and rebooted the pc with the USB to IDE adapter and launched the setup for windows. 

it went to this screen first:
[http://i.imgur.com/4oTGj.png](http://i.imgur.com/4oTGj.png)

then it went to this screen: 
[http://imgur.com/9uvrS.png](http://imgur.com/9uvrS.png)

and with a different windows installation cd, 
it went to the first screen then this screen:
[http://i.imgur.com/eTSNB.png](http://i.imgur.com/eTSNB.png)

it kept doing that and so each time i tried something new and created a new MBR Entry after deleting the old entry that did not work, and this time used a different File System like for example: to 11/Bh: FAT-32 and so forth. 

couple um notes, i have not reformated the hard drive yet though only deleted partitions after creating and deleting. 

currently i created MBR ENTRY 0 and this is the screen shots for View MBR and Properties of the Entry.
[http://imgur.com/XkcSj.jpg](http://imgur.com/XkcSj.jpg)
[http://imgur.com/gexhY.jpg](http://imgur.com/gexhY.jpg)

also, i am able to unplug the SATA hard drive and plug it into my desktop as secondary / slave. the only folder that was on the hard drive was, 'System Volume Information'. so basically the hard drive can be read as a storage device but currently NOT as a primary hard drive. [i think the MBR is either corrupted / incomplete / and or invalid due to my idiocy].  

and, at some point, after plugging the hard drive as secondary in my dekstop pc, i ran TestDisk 6.1. and after a deep search it did  find the deleted linux partitions but it said it wasn't recoverable  anymore [i do not know why i had ran that or what my intent was].

heh, hope this is detailed enough. =P
thanks again!!! =P
~ foo
I'm thinking that the IDE CD ROM->IDE-to-USB setup you're using is the reason why the Windows setup CD does not see any hard drives. From your description, it sounds like you did almost everything else right, in regards to BING and everything (even though, in my opinion, you should have multibooted Linux with Windows rather than tried to replace Linux). 

Have you tried using a straight USB CD rom drive instead? Maybe you'll have better luck with that. Its too bad your netbook doesn't have a CD rom drive built in.

---

