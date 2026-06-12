---
title: "How to create a DOS virtual machine"
date: 2010-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by searchfgold6789 on 2010-10-16
[SIZE=3][B]How to create a MS-DOS virtual machine step by step
by search[/B]
[SIZE=2]
This is an [COLOR=Blue][Ubuntu Forums]("http://ubuntuforums.org/")[/COLOR] HowTo guide.

[/SIZE][/SIZE]
[LIST=1]
[*][SIZE=3][SIZE=2] What this thread is about[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]Virtual machines[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]Downloading files and installing necessary software[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2] Making a virtual hard disk[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]Installing the system[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]Running the system[/SIZE][/SIZE]
[LIST=1]
[*][SIZE=3][SIZE=2]Running the system[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]MS-DOS commands[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]Logs[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]Performance of Virtual Machines
[/SIZE][/SIZE]
[*][SIZE=3][SIZE=2]**Accessing the contents of your virtual hard disk**
[/SIZE][/SIZE]
[/LIST]
 
[*][SIZE=3][SIZE=2]Troubleshooting[/SIZE][/SIZE]
[LIST=1]
[*][SIZE=3][SIZE=2]Assistance[/SIZE][/SIZE]
[*][SIZE=2]Removing the entire thing[/SIZE]
[/LIST]
 
[/LIST]
[SIZE=3][SIZE=2] 

**[SIZE=3][SIZE=2]1.[/SIZE] [/SIZE]**[SIZE=3]What this thread is about[/SIZE]
This HowTo guide will explain the process of using the Microsoft DOS operating system comfortably within the cozy confines of your Ubuntu system. MS-DOS was an early operating system that came out way before Ubuntu (or linux) even started out. It was the staple of all computing when it was still being widely used. It looked like this:
[/SIZE][/SIZE]```
C:\
```[SIZE=2]and the user would type stuff in to, you know, compute. It came with a system utility pack, anti-virus software, and other helpful programs. You could play games and get work done on it, but using MS-DOS was a much simpler computing experience than is offered today.
If you are reading this guide, you probably wish to use MS-DOS to play old games that won't work with wine and PlayOnLinux, or use QBasic, or maybe one of the many accounting or math tools offered at the time.

**2.** [SIZE=3]Virtual Machines[/SIZE]
This thread will explain the process of installing MS-DOS on a *virtual machine*. Virtual machines are exactly what they sound like: using a program, you can invoke the running of another computer using your real computer's resources (like RAM, graphics card, etc.)
The best way to use MS-DOS when you have an Ubuntu system is to run MS-DOS as a virtual machine from within your "host" Ubuntu machine. This guide will explain how to do that and getting you having fun with MS-DOS in no time.

**3.** [SIZE=3]Downloading files and installing necessary software
[SIZE=2]There are some things you have to do before beginning the main part of this tutorial.
[/SIZE][/SIZE][/SIZE][INDENT][SIZE=2]3a. Check which version of Ubuntu you have.[/SIZE][/INDENT][INDENT][INDENT][SIZE=2]If you have 10.10, click _[here]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Emaverick_i386.deb")_ and double-click the file. (_[64-bit]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Emaverick_amd64.deb")_)
If you have 10.04, click _[here]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Elucid_i386.deb")_ and double-click the file. (_[64-bit]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Elucid_amd64.deb")_)
If you have 9.10, click _[here]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Ekarmic_i386.deb")_ and double-click the file. (_[64-bit]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Ekarmic_amd64.deb")_)
If you have 9.04, click _[here]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Ejaunty_i386.deb")_ and double-click the file. (_[64-bit]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Ejaunty_amd64.deb")_)
If you have 8.10, click _[here]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Ehardy_i386.deb")_ and double-click the file. (_[64-bit]("http://download.virtualbox.org/virtualbox/3.2.10/virtualbox-3.2_3.2.10-66523%7EUbuntu%7Ehardy_amd64.deb")_)
If you have a different distribution of linux, you can see the _[list of downloads for VB OSE]("http://www.virtualbox.org/wiki/Linux_Downloads")_.
[SIZE=1]The links will be updated upon request. This tutorial was all tested on 10.04.[/SIZE]
[/SIZE][/INDENT][/INDENT][INDENT][SIZE=2]3b. Double-click the file you downloaded. The GDebi package installer will appear. When it loads completely, click the button that says "Install Package".

3c. You will have to enter in an Administrator's password. After a few seconds the package VirtualBox OSE will install. You may see a window come up complaining that it cannot install kernel modules. I ignored this and my virtual system is working just fine.

3d. Download _[this file]("http://msdos7.hit.bg/dosware/dos71scd.zip")_ and save it to your desktop or home folder. Once it finishes downloading, double-click it, or open it with your favorite archiver. Extract the file called "DOS71CD.ISO" to your home folder.

3e. Download this _[file]("http://www.mat.uniroma1.it/%7Ecaminati/mount_vdi-0.0.tar.bz2")_ too. Save it to your home folder. Make a new folder in you home folder called VDImount. Double-click the downloaded file and extract all of the contents to the new directory you made. Inside *that* directory, make a new folder called Mountpoint.
[/SIZE][/INDENT][SIZE=2]**4.** [SIZE=3]Making a virtual hard disk[/SIZE]
[/SIZE][INDENT][SIZE=2]4a. Open up a terminal. Type in the following: ```
sudo virtualbox
```and enter in the administrator password.

4b. Press the "New" button that has a blue star thing on it.

4c. Click "Next"

4d. In the following window there will be the fields "Name" and "OS Type". Type in a name for your machine (like MS-DOS). If the name includes "DOS" in it, the "OS Type" field will automatically go to the correct settings. Otherwise set the Operating System to Other, and set the Version to DOS. Then click next.

4e. In the next window you will see a bar that lets you select the amount of Memory you want your new virtual system to have available. 32 MB is the perfect amount. Click next.

4f. The next window asks you if you want to create a new virtual hard disk or use an existing one. Make sure the Boot Hard Disk check box is checked, and make sure Create New Hard Disk is selected before clicking Next.

4g. Yet another window will appear, on top of the one you were just using. Click Next.

4h. Select Fixed-sized storage and click next. Do not select Dynamically expanding storage because I will show you how to mount and use the hard disk later, and the tool does not support mounting dynamically expanding Virtual Hard Disks.

4i. Select about 60 Megabytes of hard disk space. Do not click Next.

4j. Set the location of your hard disk. It is best to save it to your home folder to simplify terminal commands used later on. Make note of the location.

4k. Click Next and Finish. Click Finish.

Next I will show you how to run Virtualbox and use your virtual machine directly by just clicking on VirtualBox in the accessories menu. You can skip to chapter 3, but if you do you will have to from now on run virtual box from the terminal like this:```
sudo virtualbox
``` and entering in the administrator password.

4l. Do not run the virtual machine you have just created yet. Close virtualbox. Remember the location of your virtual hard disk file which you made note of earlier. Open up a terminal and type ```
sudo chown <your user name> <location of your virtual hard disk file>
```Also, you can open up the location of your virtual hard disk file and click and drag the .vdi file into the terminal window. The location of it will then be automatically typed in.

4m. Open up VirtualBox OSE from the Accessories menu. You will not have to type in your password and no virtual machines will appear in the program. This is because when you opened up the same program earlier, you were opening it as the Root user and were granting the program permission to see files that normal users are not allowed to see, like the hard disk created by the root user.
Click New. Click next.
Type in a name for your system and select the system type, just as you did before.
Assign the new system's memory usage to the same amount as before, or if you are not sure just set it to 32 MB. Click Next.
This time, select the option to use an existing hard disk rather than create a new one. Click the small yellow folder icon next to the drop down menu that just turned white. A new window will appear; click the Add button.

4n. Navigate to and double-click the Virtual Hard disk file that you created earlier. Click Select. The window will then close. Click next. Click finish.

Your newly created MS-DOS virtual system will appear. \\:D/
[/SIZE][/INDENT][SIZE=2]**5.** [SIZE=3]Installing the system[/SIZE][/SIZE]
[SIZE=2]Double-click the new entry to start the machine up. The viewing area for the new MS-DOS machine will come up. Two things might happen:
Either
[/SIZE][INDENT]
[LIST=1]
[*][SIZE=2]A wizard will show up. If this happens you will have to point it to the DOS71CD.ISO file you downloaded and extracted earlier.[/SIZE]
[*][SIZE=2]A wizard will not show up. If this happens: close the virtual machine, click File, click Virtual Media Manager, go to the CD/DVD Images tab, click Add, and double-click the DOS71CD.ISO file you extracted earlier. Click OK. Start the virtual machine again by double-clicking on it. Hover your mouse over Devices, then over CD/DVD images, and click on the DOS71CD.ISO menu entry. Close the machine and start it up again. Press the F12 key when prompted to select your boot device. Press the C key and press the 1 key.[/SIZE]
[/LIST]
[SIZE=2]You are now ready to begin installing MS-DOS.

[/SIZE]
[LIST=1]
[*][SIZE=2]Ignore any messages that show up complaining about the mouse not being captured. In short, the messages are saying that in order to use the mouse in your virtual machine, you must first click the Ctrl button on the right-hand side of your keyboard. Doing this is recommended. Click "Capture" if prompted. To stop using the mouse from within the virtual system at any time simply press the same Ctrl key again.
[/SIZE]
[*][SIZE=2]Click Next at the MS-DOS 7.10 setup screen.[/SIZE]
[*][SIZE=2]Click Next at the window that explains MS-DOS 7.10's file system support.[/SIZE]
[*][SIZE=2]Read the contents of the next window and press Next. You might have to wait a while for the next window to come up.[/SIZE]
[*][SIZE=2]Click continue. [SIZE=1](Please note that making a new partition in the following sections will NOT affect you real hard disk setup.)[/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Continue.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click "Create a FAT32/16/12 Primary partition"[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Reboot Now.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Wait until setup begins loading and you see another blue screen, or just press 1 when prompted.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Next.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Next again.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Make sure "I agree" is selected and click next. (these will be windows you have seen before)[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click continue.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Now there will be a different window than before. Click Yes to overwrite the MBR of your virtual hard disk.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]A window appears. It asks where you want to store system files for your new machine. Click next.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]At the next window click Yes to create the directory.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Make sure that both Full Installation and Install Addons are selected. Press Next.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Yes to install AccessDos, a program to control keyboard input and other accessibility options.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Review the system to be installed and click OK.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]You will see the setup program "unpack" some files.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Continue to enable the installation of additional MS-DOS features. Doing this is recommended because addons make MS-DOS much easier to use and also because the installation of addons is a part of this tutorial :)[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]In the following windows, click Yes multiple times to install ADDPACK, MMPACK, sound card drivers, more sound card drivers (select No Sound card or none of the above if you are not sure what your sound card is, then confirm), QuickView Pro, MPXPLAY, CDP, SYSTOOLS, antivirus software, MSBACKUP, NORTON, FILEMAN, VOLKOV, GVFM, and maybe CHISYS which you don't really need unless you are Chinese. [SIZE=1](IMPORTANT: If the option appears to run any of these programs on startup, click No.)[/SIZE]
[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]When a window comes up asking if you want to install more addons, click No, because you need a seperate CD for that. Installing more addons is beyond the scope of this tutorial.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]In the next window you are asked if you want the MS-DOS logo to appear whenever you start the machine. Selecting Yes or No will not affect your new system very much.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]The next window inquires as to whether or not you want a file that gives information on previous system boot-ups. If you get the feeling that you might just run into trouble with your system later, click Yes; but if you detect a run of good fortune, or want to save virtual hard disk space, or want a that-much-faster boot up, click No.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Yes on the next window if you are not sure what to click.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Enable UMB Memory at the next window, unless you feel a very strong urge to click something else :)
[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]The next window asks if you want to enable the option to add special CD drives (like USB CD drives) later, or just enable the use of your regular CD drive for now. If you want to add your USB drive later, click "Load Both". If you want to stick with your permanent CD drive, click "Load .SYS Driver Only". If you have no CD drive, click "Don't Load".[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Check off _all_ of the options in the next window and click continue.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]At the next window select code page 437 and click continue.[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click OK. A window will come up asking you to remove the install CD from the drive and reboot. You can "Remove the CD" by clicking on the Devices menu, hovering the mouse over "CD/DVD" drives and un-checking "DOS71CD.ISO".
[/SIZE][/SIZE][/SIZE]
[*][SIZE=2][SIZE=1][SIZE=2]Click Yes to reboot.[/SIZE][/SIZE][/SIZE]
[/LIST]
[SIZE=2]You now have a fully functional working MS-DOS computer that you can run using a program in Linux!!! \\:D/[/SIZE]
[SIZE=1]In only fifty-two short, um... easy... steps...[/SIZE]
[/INDENT]**[SIZE=2]6.[/SIZE]** [SIZE=3]Running the system[/SIZE]

[LIST]
[*][SIZE=2]To run your system: Go to your applications menu, and click on VirtualBox OSE which is under Accessories. Double-click your virtual system.[/SIZE]
[*][SIZE=2]To see a list of DOS's functions, type DOSHELP when you first start the machine. There is a list of resources at your disposal. For the list along with short descriptions, type FASTHELP. If you search the internet for DOS commands, results will come up, but those results will mostly be for earlier versions of DOS and will thus be incomplete.[/SIZE]
[*][SIZE=2]VirtualBox will make log files in your home folder with names like [FONT=Courier New]2010-10-16-13-25-57.042-VirtualBox-7861.log[/FONT][/SIZE][SIZE=2]; you can delete those if you want. All they do is record what VirtualBox did. If you need to troubleshoot, you may need the contents of these logs.[/SIZE]
[*][SIZE=2]It is normal for virtual machines to lag or perform more slowly than the *real* machines being invoked by VirtualBox.[/SIZE]
[*][SIZE=2]Many virtual machine users will want to see, copy, add to, open, or otherwise use the contents of their virtual hard disk. Recall the files you extracted in step 3e. Any time you wish to access your virtual hard disk:[/SIZE]
[LIST]
[*][SIZE=2]Open up a terminal[/SIZE]
[*][SIZE=2]Copy and paste this in:```
'~/VDImount/mount_vdi.sh' <location of the .vdi virtual hard disk you want to mount> '~/VDImount/Mountpoint' 1
```and press enter.[/SIZE]
[*][SIZE=2]Now you can access the contents of your virtual hard disk. They will temporarily be in your home folder, in the VDImount folder, in the Mountpoint folder.
[/SIZE]
[*][SIZE=2]Leave the terminal window open. If you want to stop using your virtual hard disk at any time, type ```
end
``` into the terminal.[/SIZE]
[/LIST]
 
[/LIST]
**[SIZE=2]7. [/SIZE]**[SIZE=2][SIZE=3]Troubleshooting
[/SIZE][/SIZE][INDENT][SIZE=2]If you need help or get stuck, you can join ubuntuforums and put a post on this thread. I will then help you solve your problem. Also, please post on this thread if you find a problem with this tutorial.
It's really easy to create an ubuntuforums.org account.

After this tutorial, if you find it necessary to undo everything you did, open up a terminal window and type this in:```
rm -r ~/VDImount
sudo rm -r /root/.VirtualBox
sudo rm -r ~/.VirtualBox
rm <location of the virtual hard disk you made>
sudo apt-get remove --purge virtualbox-ose
```[/SIZE][/INDENT]Enjoy,
 - search

---

### Post by karthick87 on 2010-11-25
A nice guide :)

---

