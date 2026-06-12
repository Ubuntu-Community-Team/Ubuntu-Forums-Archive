---
title: "Checking battery state. Help"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by mblurryy on 2013-02-04
i have ubuntu 10.10..tried to do some updates or whatever..i had several windows open and suddenly everything froze..so i just forced the shut down..and now when i try to restart my laptop, all im getting is this weird message, that some audiopulse disabled..and checking battery state... and nothing happens..when ctrl alt 2, i manage to login, but that gets me nowhere..still no desktop..nothing..just a black screen and terminal waiting for my commands?? HELP?? 

so much for trying to update my ubuntu and browsers etc. ugh.  still 10.10 and now i cant even access the desktop. 

PLEASE HELP :(

---

### Post by UAdnan on 2013-02-04
I faced this error just yesterday. I hope that we're the same case. 
It turned out that my hard disk was getting full, which caused problems.
You should type the following command:
**df -TH**  and see if your Ubuntu partition is full or not. In my case I had 3GB left when it broke down. If that's the case with you, type the following command:
**du -h / | grep ^[0-9.]*** will find the biggest files you have, you can either try to remove the ones you don't need, or run these two to attempt an automatic clean-up of some unwanted files such as already installed .deb packages:
[B]sudo apt-get autoremove
 sudo apt-get clean[/B]

If you find a big file you don't need, run:
**sudo rm -r filename**

Good luck.

---

### Post by DuckHook on 2013-02-04
DO NOTHING till you backup your important data files. If already backed up, then need far more info:

> **mblurryy said:**
> ...tried to do some updates or whatever..

What was the "whatever"? These details are critically important! Were you just updating or were you upgrading? If updating, what updates were they? If upgrading, to which version? 10.10 is either no longer supported or nearing end of life, so I'm dredging up old memorized knowledge here, but it is possible to backup even now using nothing but the command line, so first things first: tell us your backup status.

> i had several windows open and suddenly everything froze..so i just forced the shut down.....and possibly corrupted some files that your GUI needs in order to run properly. Forcing a shutdown will do that.

> and now when i try to restart my laptop, all im getting is this weird message, that some audiopulse disabled..and checking battery state... and nothing happensThe complete output is very important because error messages tell us a lot about what is going on. Please post precisely what is on screen when the system refuses to move on.

> ..when ctrl alt 2, i manage to login, but that gets me nowhere..still no desktop..nothing..just a black screen and terminal waiting for my commandsThe fact that you can switch consoles to TTY2 is much better news than you take it to be. It means that your base system is still fine and accessible. It is likely only the GUI that is corrupt, but your data is still preserved and can be copied for safe keeping.

> PLEASE HELP I'll be frank. Given your stated aversion to the command line, the best strategy here is to give you just enough commands to get your data off good and safe and then do a new virgin install using Ubuntu 12.04. Since this version is LTS and now quite stable, it should prove very suitable for your needs. But to be sure, tell us about your system expecially CPU, amount of RAM, graphics chip and graphics RAM. These are the four critical items to determining which flavour of Ubuntu would be best for you.

Alternatively, if you would like to try playing detective using only the command line, then this can also be done, but will likely take as much time as a virgin install. It's your choice.

P.S. With all due respect to @UAdnan, do not try to fix with *sudo rm -r anything* given that you do not know how to use the command line. This has the potential to totally nuke your system unless you know exactly what you are doing.

---

### Post by mblurryy on 2013-02-05
I have Dell Inspiron N5040

RAM Included 			4 GB 		 			RAM Type 			DDR3 		 			Memory Details 			4GB Single Channel DDR3 Memory
Hard Drive Speed 			5,400 RPM 		 			Hard Drive Capacity
 			500 GB 		 			Hard Drive Technology 			Hard Disk
Graphics Card Brand 			Intel 		 			Graphics Card 			Intel HD Graphic 		 			Optical Drive 			DVD±RW 		 			Optical Drive Details 			Tray-load DVD+/-RW (SATA)
how do i know the graphics RAM? sorry im such a newbie :D

Ok, so first things first. I dont have any backup i think. So how can I backup my files using the terminal?

And the full story is that my update manager wanted me to upgrade to ubuntu 11.04 for a long time. but when i tried to tick and install all the updates, it didn't let me. it said, that the authentification failed. and that the 11.04 version is not supported anymore. The main reason i tried to upgrade in the first place, was the fact that i had some trouble with Facebook and Tumblr. I couldnt reblog stuff, create posts..and I couldnt download the latest adobe flash player..So i thought i should upgrade my mozilla browser. but didnt know exactly how, so i thought i would try to upgrade to ubuntu 11.04 first. but since that didnt work either, i tried to install Chromium. but Chromium wouldnt install, it said: Waiting for natty to exit. so i went to Synaptic Package Manager. and tried to remove some lib..package, i cant remember exactly what it was..and with that there were some other packages installed..there were many packages named natty..over there..so im not quite sure anymore :(..and thats when suddenly everything froze and i forced the shut down..

And now I am stuck in the Restart progress. Sometimes when I restart, nothing comes up anymore, just my frozen mouse and I cant do anything. I already did the sudo apt-get autoremove too :/. But now I managed to get the terminal back on. Actually here's what I did: the laptop was restarting..and i did ctrl alt del..so the following choices came up: Ubuntu with Linux 2.6.35-27-generic...then generic (recovery mode)..35-22-generic, 35-22-generic (recovery mode), Memory test..and Restore Ubuntu 10.10 to factory state..so i chose 35-27-generic (recovery mode)

and now theres a window in the middle of the blue screen, where are following choices: resume normal boot; clean; dpkg (repair broken packages); failsafeX; grub (update grub bootloader); metroot (drop to root shell prompt with networking)..and the first choice is red..but when i press enter, nothing happens..and below the window is following:

rc-sysinit start/running, process 1472
speech-dispatcher disabled; edit /etc/default/speech dispatcher
*PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
*Enabling additional executable binary formats binfmt-support
*Checking battery state...

Ubuntu 10.10 merit-Inspiron-N5040 tty1

merit-Inspiron-N5040 login:

So, what should I do next? :(

---

### Post by DuckHook on 2013-02-05
<edit>
read next post first/this one only for interest.
</edit>

<sigh> removing lib packages was... uhm, brave. It is not possible to reconstruct your system at this point and you are in salvage mode. You will have to buy an empty USB stick or USB drive if you don't have one already. If buying a stick, buy one with the largest capacity available. A drive is a better investment and a much better idea because it will have the capacity to allow you to make future backups as well. This is probably a lesson that you have learned by now, but it doesn't hurt for me to emphasize it--if you value your data, back it up routinely and always before you do anything major to your system like upgrading. The first order of business is to plug in the stick/drive and see if your system recognizes it.

1. Once plugged in, at the command line, do:
```
ls /media
```If this command produces any output, you are in good shape. It means that your system recognizes the stick as another drive and can write to it. If no output whatsoever, then reboot your computer with the USB stick/drive plugged in and repeat above. We are looking for something like the following:

```
DuckHook@Big_Papa:~$ ls /media
Fairmont
```In my case, the name of my USB stick is "Fairmont". If you have this result, then note the name of the drive and proceed to step 5 below.

2. If no response to 1 above then do:

```
cat /proc/partitions
```This gives you a list of all the drives attached to your system. The sd[x] devices are what we are looking for. Your primary hard drive is likely sda and subsequent drives like USB sticks/drives will likely be sdb, sdc, sdd etc. Ignore any drives designated with sr[x]. If you have more than one hard drive attached to your system, The number on the third column is the size of the device in bytes, which serves as a very important double-check to make sure that we are referencing the proper drive. This is critical because the following steps may involve creating a filesystem on the USB stick/drive, and we want to make sure that we are doing so only on the USB drive. If you inadvertently format any other drive, you may delete the very data that you are trying to recover. Therefore, find the line that corresponds to the USB drive size you have and note the label under "name". This will likely be sdb, but it could be a higher letter.

3. These next procedures use the *parted* command, which is very powerful and must be used with care. It has the potential to nuke your system, so read each command twice to make sure they precisely match the instructions here before pressing <Enter>.

Do:
```
sudo parted sd? print
```replacing the ? with whichever letter designates your USB stick. If you get an output that looks something like this:

```
Model: General USB Flash Disk (scsi)
Disk /dev/sdg: 1008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  1008MB  1008MB  primary  fat16        boot
```then all is well and we just need to do:

```
sudo mkdir /media/usb
``````
sudo mount /dev/sd?1 /media/usb
``` replacing ? with the letter for your USB drive. Then skip to step 5.

4. If the output looks more like this:

```
Model: General USB Flash Disk (scsi)
Disk /dev/sdg: 1008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags
```...with missing info in the second stanza, then your stick/drive is unpartitioned and you must partition it and give it a filesystem. Do the following in the stated order:

```
sudo parted /dev/sd?
```You are now in the GNU partition editor. It no longer prefaces lines with your shell info but instead says: "(parted)" Do the following:
```
(parted) mklabel
```then:
```
Warning: The existing label on sdx will be destroyed and all 
data on this disk will be lost. Do you want to continue?
Yes/No: yes
New disk label type? msdos
```next:
```
(parted) mkpartfs
```then:
```
Partition type? primary/extended? primary
File system type? [ext2] fat32
Start? 1
End? -1
```finally:
```
(parted) quit
``````
sudo mkdir /media/usb
``````
sudo mount /dev/sd?1 /media/usb
``` replacing ? with the letter for your USB drive.

5. Whether we got here from step 1, 3, or had to detour through step 4, you now have a writable USB stick/drive that can be used to copy your /home directory. Your /home directory is where all of your personal data files are. If you know what these files are, then you can copy them individually or by whole directories to the usb stick that you have just mounted with the cp command. If your USB stick/drive is large enough to take your whole /home directory, then it may be easier to just copy your whole /home directory with:

```
cp -a ~/* /media/usb
``` If proceeding directly from step 1 above, then substitute the actual name of your USB stick instead of "usb" in the above code. If you got here going through steps 3 or 4, then you will have already defined this share as "usb" and the code should work without change.

Also, you must not do this last command unless you are sure that your USB media is large enough to hold your whole /home directory--another reason to invest in a USB drive. The cp command is not smart enough to do a sanity check beforehand, so if your media is not large enough, it will simply copy to the point where it runs out of space and then die. The form of the cp command is similar if you wish to go through file by file. Instructions and examples for using the cp command can be found [here]("http://www.computerhope.com/unix/ucp.htm").

Enough for now. Let's get your data safe before proceeding onwards to making your system usable again.

---

### Post by DuckHook on 2013-02-05
Complete, utter and total braincramp. A better alternative to the convoluted and gruelling technique in my last post, especially for people uncomfortable with the command line, is to do the following:

1. Download a fresh new LiveCD of 12.04 from [here]("http://www.ubuntu.com/download/desktop") and burn it to CD/DVD.

2. Plug in your USB drive/stick, for same reasons as my prior post. Henceforth we will assume it's a drive.

3. Insert CD and boot with it.

4. Choose "Try Ubuntu". ****WARNING****: Make sure that you choose the live session without installing. Installing will overwrite all of the files that you are trying to save. If you chose wrong method, cancel and start again. Pull the plug if you have to.

5. When the Live session comes up, with any luck, both the hard disk from which you are trying to recover data, and the USB drive will already be mounted and we can use Nautilus to copy files from one drive to the other. Nautilus is the graphical file manager that you are already familiar with.

6. Open Nautilus (it will be the file icon on your launcher). Open your HDD and navigate to /home/your_name. You will see all of your files laid out in a nice recognizable graphical layout.

7. Do <Ctrl>+<h> to reveal hidden files.

8. Do <Ctrl>+<n> to open another instance of Nautilus.

9. On the second Nautilus Window, navigate to the USB Drive.

10. Drag and drop all of the data files you want to preserve from your HDD to the USB drive.

Voila, you have salvaged your critical data. If the USB drive is big enough, simply drag your entire /home directory over. If you must pick and choose, then pay especially attention to the non-obvious hidden files like .thunderbird (hidden files begin with a dot) or whichever e-mail client you use. .mozilla contains your Firefox settings, preferences, bookmarks, etc.

11. Check to make sure that your USB drive is readable and contains everything you want by trying to read it on another machine.

12. Once you are certain that your data is safe, make a clean virgin install of 12.04 on your machine using the same disk you've already burned. When you deleted lib files without knowing which they were, you basically hosed your old system to the point where it makes no sense trying to reconstruct it.

Apologies for the head-spinning instructions in my prior post. This is likely to be a far easier way to recover your data and start out new and fresh.

Good Luck!

---

### Post by mblurryy on 2013-02-06
Thanks! :)

---

