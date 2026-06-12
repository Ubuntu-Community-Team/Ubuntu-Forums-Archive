---
title: "How to setup a multiboot system with multiple partitions and HDDs for a Desktop"
date: 2010-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Manolicious on 2010-01-11
We will be work with Ubuntu 9.10, which comes with grub2 (referred to here as just grub), the boot loader program we will be working with.  Using its Live CD, use GParted to make your partition table.  It is advisable that you use a ext3 format for all your linux partitions, at least for the ones that will primarily be using Ubuntu.  When setting up a partition table, try to keep your OSs on the SATA hard drive as the ATA HDDs (HDD = hard drive) can be slower at reading, writing, and loading data. Feel free to put things anywhere you like, with the following constraints.

-any partition for a Windows OS (2000,XP,Vista) must be on a primary partition, where linux OSs can be on primary partition or on an extended partition's logical partition.

-you must have one linux swap partition in size greater than the size of your total RAM. When installing any linux OS you may direct them to use this same swap partition.

-you must set aside 250MB to 500MB for the boot partition, which will be what grub will be configured to work with. This will contain the addresses of the kernels that your computer will need in order to boot from one of them.

-it is advisable that you make separate partitions for the / (the root directory) and /home directory for each linux OS you plan to install.  

-it is also advisable you make each of your partitions a unique size, so you will be able to easily tell what the partition is or what you plan to do with it latter when looking at them through different terminals and prompts.

Once done, click on the Install icon to install Ubuntu 9.10.  Be aware what I'm advising you to do will wipe clean your / and /home partitions (though Ubuntu now seems capable of inheriting previous user accounts, even from Windows OSs, at one step of the installation, but these accounts can easily disappear if you should botch the installation).

SIDE NOTE: If you want to try to keep your system settings, like the bookmarks in your web browser, or your xmms skin, or what have you, these are normally stored as hidden files underneath /home in your own personal user name folder, like /Lucifer or /home/Lucifer.  These hidden files are presided by a period in their file names, so you can list them in the terminal with 'ls .*'.  These are the files you want to back up in the hopes you can use them to overwrite the hidden files the Live CD installs by default under /home/Lucifer.  You might also consider backing up two specific files, package.selections and sources.list, to backup all the programs you installed (at least those you installed using synaptic) and other system settings.

Go through the motions of the Ubuntu 9.10 Installation program, but when it gets to the partition setup, select the advanced-manual partition setup, which should be something like the 3rd option on the list.  Here the Installer should already be able to spot your swap partition.  Click on the 250MB-or-so partition you want your boot loader installed to, then click Change, then indicate to the Installer you want /boot to be installed to it through the drop down menu.  Do the same thing for the partition you want the OS installed to, but this time selecting / from the drop down menu.  Do the same thing for the partition you want your /home directory to be at, selecting /home from the drop down menu (you can also do this with /usr/local as well).  

EXTRA SIDE NOTE: You might be able to backup your programs even better by copying your entire /usr/local directory, which you can even direct Ubuntu 9.10 to install on a separate partition.

If for some reason you had a botched previous installation on your boot or root partitions, you can wipe them clean by selecting the option to reformat them in that same Change menu, though this will wipe out any previous user accounts on you root partition.  Finish up the installation wizard and let Ubuntu install.  

Afterwards, stay in the Live CD and go to the terminal and input the following command.  

```
sudo fdisk -l
```

This will show all of your partitions, their address under /dev (Device Boot), their size under Blocks (in bytes) and their file system under System.  Under System you can easily see which partition is for linux, which is the swap, and which has a Windows OS on it by the one marked with the HPFS/NTFS file system.

WARNING NOTE:  If you really rearranged your partitions, copying and pasting them to other HDDs, it might confuse grub as to where everything is, resulting in a grub error 17 message.  The only way out of this is to reinsert the Live CD, do a hard reboot (hit the restart button or unblock your power cord), then go to the terminal in the Live CD.  There you type a command which I've forgotten, but what ever it does it reorders your partitions for grub to read better.  Doing this reduced my grub error 17 to a grub error 15, where I had to follow the steps I'm writing here.  Search the web under "grub error 17" and you should find the command somewhere

EDIT: Here's the command I was talking about.
[QUOTE=http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/]
To fix the disk order.

```
sudo fdisk /dev/hda
```

Please note it&#8217;s hda not hda1 or hda3. No numbers we are working on entire disk. It&#8217;ll take you to fdisk prompt. Be careful here.

choose option x (extra functionality (experts only)) and enter.
 then select f (fix partition order) and enter.
 then select option w (write table to disk and exit), and enter.

X F W in short. Don&#8217;t do anything else unless you know what you are doing.[/QUOTE]

After using the sudo fdisk -l command, you should write down the /dev/**** address of all of your partitions, and mark down what you plan to do with which.  It is critical you mark down which of these address refer to your /boot, /, and /home partitions for Ubuntu 9.10.  Each hard drive is typically marked as sda, sdb, and sdc in Ubuntu, though Slackware refers to them as hda, hdb, and sda respectively, for an example system with three HDDs.  Then each partition is labeled with a number afterwards, such as sda1, sda2, and so on.  Note an extended partition has its own address, even though its logical partitions have their own addresses.

Now to install grub.  While in the Live CD, type the following commands into the terminal.

```
sudo mount /dev/sdc7 /mnt
sudo mount /dev/sdc6 /mnt/boot/
sudo grub-install --root-directory=/mnt/ /dev/sdc
```

In this example, sdc refers to the hard drive where I've installed Ubuntu 9.10, with sdc7 referring to the root partition (/), and sdc6 referring to the boot partition (/boot).  The last command is very special, and it is what installs grub to a place called the Master Boot Record (MBR) or boot sector, a place on each hard drive you cannot see or touch in GParted.

SIDE NOTE: When using multiple hard drives, make sure your BIOS menu knows the order in priority in which you would like to boot from them, with the hard drive you have your boot partition on being before the others (always keep your optical or CD/DVD drive the first in priority).  The BIOS menu is another special place located in a flash drive on your very motherboard, and contains information on all the devices connected to it.  You can usually access this menu by slamming on F1 immediately upon boot up, though your first splash screen indicating what motherboard your using usually tells you what to press to get to BIOS.  

ANOTHER SIDE NOTE: I remember hearing on a thread some where related to multiboots that in BIOS you should set for each hard drive's configuration to TYPE: User and each MODE to AUTO.  This is what I did for my system.

Now after executing those commands, restart and take out the Live CD.  You should now see the grub OS menu and be able to either boot into Ubuntu or one of your Windows OSs.  Other places you could end up are the grub error 17 screen (see WARNING note above) a grub error 15 screen, a grub-rescue prompt, or a normal grub-prompt, which you can go to from the OS menu by pressing 'c'.  If you get an error 15, reinsert the Live CD and do a hard reboot.  If you get a grub-rescue prompt, reinsert the Live CD and do a hard reboot, as grub-rescue is worth crap.  If you end up in a normal grub prompt, usually looking like sh:gurb>, then there is still a possibility of booting into a linux distribution, or at the very least you can reinsert the Live CD and use the 'reboot' command in the grub-prompt to do a polite restart.  Note the grub-prompt comes with its own commands which are rather different from the ones you may be used to in the terminal or bash-prompt.

To boot into a linux distribution from the grub-prompt you will need to use the following three commands.

```
linux  (hd0,6)/vmlinuz root=/dev/sdc7
initrd  (hd0,6)/initrd.img
boot
```

In this example, sdc7 refers to my root partition /, while (hd0,6) refers to my boot partition /boot.  Note how this address looks nothing like sdc6, the address Ubuntu refers to my boot partition as.  This is how grub sees your partitions, (hd*,#), with * referring to a specific hard drive, and # referring to a specific partition.  To figure out which partition is which as grub understands them is a bit of a guessing game.  Enter the command 'ls' in grub will give a concise list of all of your partitions.  Entering 'ls -l' or 'ls -lh' gives a bit more comprehensive list, but it may still not be clear which is which.  The best way is to guess (by hoping grub associates # with the corresponding partition number Ubuntu knows them as) and use the following command on each partition.

```
ls -lh (hd*,#)/
```

Please not the / slash here is critical if you want to see the contents of each partition.  The root partition should be obvious by the recognizable root file structure of a Ubuntu (or any linux?) OS.  The boot partition should have a grub directory and a couple of files starting with vmlinuz.  Once you found the boot partition, use the linux, initrd, and boot commands I've given above, but make sure you press the TAB key after typing vmlinuz and initrd.  This will help you zero in on the exact kernal grub will boot up from, for instance vmlinuz can look like vmlinuz-huge-smp-2.6.29.6-smp.

If you had to use those commands to boot into Ubuntu from grub, go into the terminal of your freshly installed Ubuntu 9.10 OS and type the following command

```
sudo update-grub
```

You can also try what some consider a more serious version of this command, though you might need to chroot into something.

```
sudo grub-mkconfig
```

With either command, you should watch the terminal print out each of your lovely OSs, or build the complicated grub.cfg file you might have heard so much of (in grub2 of course, this was known as the menu.list-something in the original grub, now called GRUB Legacy).  Afterward reboot and you should see the OS menu now in grub [otherwise I guess it's back to the IRC chatrooms with YOU].

**Dealing With Other Linux Distributions:**

Now (hopefully) you got a dual boot system going with Ubuntu 9.10 and your favorite Windows OS, complete with your own separate boot partition.  Now let's talk about making this a multiboot system with another linux distribution.  A lot of distributions seem to like installing their own boot systems, like grub or LILO, to their own root partitions, or worse, overwriting your grub installation in MBR.  Do your best to keep their dirty fingers away from MBR during installation, but having a separate boot partition should help in this regard, or at best recovering from it, which you can do by reinserting that Ubuntu 9.10 Live CD and repeating the actions I've listed above (and be sure to backup incase things go south).  Another thing you might avoid is having each distribution use the same /home partition, as their user settings might conflict with each other, and we all know how scary those .dmrc errors are.

Now let say you installed a linux distribution, say Absolute Linux, which is built on Slackware, and you made sure to direct its root partition / to its own blank partition.  Pulling out the installation CD and rebooting, you will notice that the OS does not show up on the grub OS menu.  Boot into your installed Ubuntu 9.10 and type the sudo upgrade-grub command and you should see the distribution pop up in the terminal.  Reboot and you should see the distribution (or the kernel it is based off of) pop up in the OS menu.  However if you used the distro I used and tried to boot into it, you might watch grub go into a kernel panic, which your keyboard might indicate to you by having every light on it blink. 

If you look carefully at the screen, you might see what the exact error was.  Study it carefully and when you are ready do a hard reboot.  The problem I had was Ubuntu refers to my three hard drives as sda, sdb, and sdc (with sdc where I'm installing all my OSs to), where as Slackware refers to them as hda, hdb, and sda, respectively.  So when Slackware boots, it sees sdc and doesn't know what the hell's going on.

A way to fix this is to boot into your installed Ubuntu 9.10 and head to the terminal.  Notice that your boot partition should be automatically mounted to the Ubuntu file system as /boot from the terminal.  You want to open the file grub.cfg.  One way to do this is with the following command.

```
gedit /boot/grub/grub.cfg &
```

The & should let you continue using that prompt window even after the gedit text editor loads.  As the file head says, you should not edit this file.  Then, use the following command to open the 40_custom file located in /etc of your Ubuntu OS.

```
sudo gedit /etc/grub.d/40_custom
```

I asked you to use sudo here so we can edit this file.  Now carefully look through grub.cfg and you should see each OS system that pops up on the grub OS menu as well as the information to load that OS's kernel.  Notice how some of these commands look a lot similar to the linux, initrd, and boot commands you have to enter in the grub-prompt to boot into an OS from there.  Towards the bottom you should see the name of the kernel the second linux distribution you're trying to install uses.  It should appear on a line beginning with 'menuentry' and ending with a { bracket.  You want to copy this whole entry, including menuentry and everything after the kernel name and within the {} brackets, which look like grub commands.  Paste this into the 40_custom file after the line beginning with 'exec'.

Now look at this entry in the 40_custom file and focus your attention on the line beginning with 'linux' within the {} brackets.  Towards the end you will notice something written like "root=/dev/sdc3", where in this example sdc3 would be the partition I installed Slackware's / to, but since Slackware recognizes this as sda3 as in my case, it should be edited as such.  Another prudent edit is to delete the stuff on that same line after the name vmlinuz, for example cutting down 'vmlinuz-huge-smp-2.6.29.6-smp' to just 'vmlinuz'.  You will remember a vmlinuz file also exists in certain linux OSs' /boot folders alongside a file with the same but longer name, like vmlinuz-huge-smp-2.6.29.6-smp, though they are still the same file size.  vmlinuz is what's called a symlink, and will link to vmlinuz-huge-smp-2.6.29.6-smp or whatever vmlinuz-* file gets added with a kernel update.  

If you have a Windows OS, you should also be able to see its menuentry toward the end of the grub.cfg file.  Copy this entire entry too to 40_custom (I placed mine on the line after exec but before the Slackware entry) but change nothing in it.

Save the edited 40_custom file (overwriting the previous version) and run sudo update-grub once more, and reboot.  You may now notice two entries of the same second linux distribution you're trying to run.  One of them will boot into a kernel panic, but the other should actually boot into its OS.  You can remove bad kernel entires from the grub OS menu by going into your Ubuntu installation and using the command

```
sudo chmod -x /etc/grub.d/30_os-prober
```

Then sudo update-grub once more.  

Note that if you didn't copy the Windows OS menuentry to 40_custom the above chmod command will also knock out your Windows OS from the grub OS menu.  To restore things back the way they were with the panicking Slackware kernal, boot back into the installed ubuntu and enter

```
sudo chmod +x /etc/grub.d/30_os-prober
```

Then sudo update-grub once more.  

However if you did copy the Windows OS menuentry, everything should be dandy.  That should be it.


THANKS!
On the Kubuntu IRC server in the #grub channel, much thanks to Jordan_U for helping me out with this and all the credit for this tutorial should go to him.  Daskreech on the #kubuntu channel also deserves some credit for helping me with some of the background info.

---

