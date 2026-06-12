---
title: "How to Install WinXP after Ubuntu with Gparted"
date: 2009-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by aravindc26 on 2009-06-02
[LEFT]First, download a copy of the Gparted Live CD ISO and burn it to a CD.  The ISO image can be found[ here.]("http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-11.iso")
To burn an ISO file with Ubuntu, simply right click on it and click “Open with CD/DVD creator”, then click Burn. After burning the ISO to a CD, restart your computer with the CD in the drive. If you have your BIOS boot order configured to boot from CD, the CD should load a menu presenting you with many options, as seen below (if not, do some googling to find out how to change your booting device order within your bios or via a hotkey during POST so it will boot from your CD-Rom drive first):



When the CD boots, you’ll be given a menu like the one shown above. You should go ahead and select the default option that is highlighted at the top of the menu. The other options in the list are for use if you have problems with the your video card, and need to use legacy drivers (try to Force VESA first if you have a video driver problem later). After selecting a menu item and pressing enter, Gparted will begin to load. At some point, this screen will appear:

[IMG]http://www.davestechsupport.com/blog/images/gparted0.png[/IMG]

Simply hit the Enter key to select US English default.  Another screen will show up:

[IMG]http://www.davestechsupport.com/blog/images/gparted1.png[/IMG]

If you’re speaking English, then hitting the Enter key at this point will select it for you. Otherwise you’ll need to type the corresponding number to your language first, then press enter.
 Once it’s finished loading, you’ll either be looking at a GUI (below), or be stuck at a command prompt with a complaint about your video card. If the latter happens, try again by selecting the Force VESA option from the main Gparted boot menu as mentioned earlier.
 The GUI looks like this:


[/LEFT]
[IMG]http://www.davestechsupport.com/blog/images/gparted2.png[/IMG]
[LEFT] 


You’ll see the main Gparted application already loaded with a hard drive selected (Note: The hard drive it has selected may not be the one you want selected, if your system has more than one hard drive in it. Fortunately, hard drive size is shown in the hard drive selection button in the upper-right corner, and you can use it to tell different hard drives apart if you know which has what on it).
 **In the above example, the wide blue border box that contains the device name “/dev/sda1&#8243; is the primary Linux ext3 partition**, and all partitions present on the drive are graphically represented here. So we can see that we have a primary ext3 partition which contains Ubuntu, along with an extended swap partition that Ubuntu also needs to keep intact (highlighted with a red border). What we want to do is shrink the size of the primary ext3 partition, and then insert a new NTFS partition in place of the newly unallocated space. There will be cake at the end 
 Start by clicking on the ext3 partition (either the dark-blue box in this example, or from the partitions table listing just below it), and then click the “Resize/Move” button at the top. A new window will appear:


[IMG]http://www.davestechsupport.com/blog/images/gparted3.png[/IMG]
We see the entire ext3 partition here represented as a box, and in the background, you can see just behind the bottom edge of this new window that the partition we’re dealing with is also highlighted in gray. The used portion of this partition is represented by the yellow area in the box, and the available free space is represented by the white. What we want to do is free some of this white space up. Start by clicking on the arrow-looking handle on the right hand side of the box, and drag it toward the center, like this:
 [/LEFT]
[IMG]http://www.davestechsupport.com/blog/images/gparted4.png[/IMG]

[LEFT]You’ll want to leave a little white left for Ubuntu to use, otherwise you may have free hard drive space problems next time you run it and be required to delete files. The gray area that is revealed on the right is going to become un-allocated space, which we’ll use for a new NTFS partition in just a moment. At this point, click the “Resize/Move” button in the lower right corner. You’ll see the changes you’ve made represented immediately, but this is just for visual reference. A “to-do list” will also appear at the bottom, queuing up changes as you go. They will not actually take effect until you click the Apply button at the top, which we don’t want to do just yet…

[IMG]http://www.davestechsupport.com/blog/images/gparted5.png[/IMG]

Next, we’ll click on the unallocated gray space which we created by shrinking our ext3 partition, and then click the “New” button.


 [/LEFT]
[IMG]http://www.davestechsupport.com/blog/images/gparted6.png[/IMG][LEFT]
This will show us the unallocated space represented in white. What we need to do here is tell Gparted that we want to create an NTFS partition here, and we can do that by clicking on the Filesystem drop-down menu, and selecting “ntfs” from the list (as shown above). Once this is done, you can click the “Add” button….
 [/LEFT]
[IMG]http://www.davestechsupport.com/blog/images/gparted7.png[/IMG]

[LEFT]…and then click the Apply button at the top of the main Gparted window. It will probably take several minutes for the changes to apply and take effect (go eat a sandwich and watch some TV). Once finished, the system will need to be rebooted. Upon reboot, you’ll not see any difference in your startup on your Ubuntu system, other than your free hard drive space being reduced. Grub will load normally, and you’ll boot into your login screen as usual.
 Now that we have an NTFS partition on the hard drive, we can begin to install Windows XP as you normally would by inserting the XP install CD and booting from it. ([Here]("http://www.petri.co.il/install_windows_xp_pro.htm") is a guide for installing XP, just for quick reference.  Read the rest of this first).
 At some point during the Windows XP install, you’ll get to a screen that is somewhat similar to this one:
 

***I need to stress that your screen will look a little different ***(I couldn’t find a good enough screen shot online so I had to Gimp the one above to be somewhat more accurate to what we’re doing here. I’ll replace it with a better one tonight). This screen appears during the Windows XP install when it’s asking you to select a location for Windows XP to install itself. Chances are, you’ll see one partition on your screen that has the letters “NTFS” next to it. THAT partition is the one you just created after resizing one of the others and it’s where we want to install Windows. The ext3 partitions will also be listed here, but likely be listed as “Unknown” because Windows XP is incapable of reading ext3. DO NOT SELECT ANY OTHER PARTITION than the NTFS partition (there should only be one NTFS partition listed anyway).
 You will want to select this NTFS partition and press enter. It will then ask you if you want to format it to FAT32 or NTFS, or make no changes to the partition. **Select “Leave file system intact (no changes)”**.  Proceed with the rest of the install as usual.
 After the installation is complete, your system will reboot and you’ll notice that your Grub menu is missing. In fact, you’ll notice you can’t access your Ubuntu system at all. “Oh crap!” you might say. Don’t worry. We’re about to repair the Grub menu, and then modify it so it will have an entry for your newly installed Windows partition as well.
 Insert your Ubuntu Live CD and them immediately restart your computer (so as to boot from the Ubuntu CD). Once the Ubuntu Live environment is up and loaded, click Applications>Accessories>Terminal. At the prompt type:
 
[LIST]
[*][COLOR=#ff0000]sudo grub[/COLOR]
[/LIST]
 This will take you to a grub prompt that looks like this:
 
[LIST]
[*]grub>
[/LIST]
 At grub>. enter these commands:
 
[LIST]
[*]grub> [COLOR=#ff0000]find /boot/grub/stage1[/COLOR]
[/LIST]
 This will return a location output, that will look something like “(hd0,1)”. Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands…also be sure to **include **the parenthesis).
 
[LIST]
[*]grub> [COLOR=#ff0000]root (hd0,1)[/COLOR]
[*]grub> [COLOR=#ff0000]setup (hd0)[/COLOR]
[*]grub> [COLOR=#ff0000]quit[/COLOR]
[/LIST]
 What we’ve basically done here is restored grub. Unfortunately, the grub menu doesn’t have a Windows entry in it. You’ll find that when you reboot your computer, Ubuntu will load normally, but grub will not present you with an option to boot into Windows. We have to add that entry manually.
 Now in Ubuntu, open another Terminal window like we did before.  Now type:
 
[LIST]
[*][COLOR=#ff0000]sudo fdisk -lu[/COLOR]
[/LIST]
 You’ll get some output that looks like this:




```
username@username-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x994a994a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    89048294    44524116   83  Linux
/dev/sda2        89048295    92952089     1951897+   5  Extended
/dev/sda3   *    92952090   117210239    12129075    7  HPFS/NTFS
/dev/sda5        89048358    92952089     1951866   82  Linux swap / Solaris
username@username-laptop:~$
```In the above example, the third partition in the list is the one containing our NTFS partition, and thus, Windows XP. We need to add an entry based upon this information to the grub menu so we can select it for booting. Still within Terminal, type the following:
 
[LIST]
[*][COLOR=#ff0000]sudo gedit /boot/grub/menu.lst[/COLOR]
[/LIST]
 [COLOR=#000000]This will open up your Grub configuration file.  Scroll down to the bottom of it, and paste in the following text:[/COLOR]
 # This entry was added by username for a non-linux OS
# on /dev/sda3
title        Microsoft Windows XP Home Edition
root        [COLOR=#ff0000](hd0,2)[/COLOR]
savedefault
makeactive
chainloader    +1 In the above text, note the “[COLOR=#ff0000](hd0,2)[/COLOR]“. This statement is based upon the NTFS partition being listed as the third on this hard drive. It says “Hard Drive 0, Partition 2&#8243; which in human speak actually means “First hard drive, third partition.” If the fdisk -lu output had shown the NTFS partition listed as the second partition (for example) the notation would be “(hd0,1)”. If you had installed Windows XP on a separate hard drive, say a slave hard drive on the primary IDE/SATA channel, it would be listed as (hd1,0), which means “Second hard drive, first partition” in human speak. Modify your entry in the additional text above accordingly, paste it to the bottom of your menu.lst file in Gnome Text Editor, and then save the file.
 When you reboot, Grub should now have a new entry which will list Windows XP as an option. Note that the text displayed for this option is based upon what you typed in the above text. You can modify it if you need to (for example, if you have the Professional version of XP, instead of the Home edition and you want it to say that).
 And that’s it!  Now get some sleep, we’ve had a long day.


[SIZE=5]SOURCE : [DAVE's Tech Blog]("http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/")[/SIZE][/LEFT]

---

