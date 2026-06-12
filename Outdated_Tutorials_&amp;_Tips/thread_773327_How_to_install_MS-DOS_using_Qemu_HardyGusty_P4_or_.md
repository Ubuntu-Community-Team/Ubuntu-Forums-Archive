---
title: "How to install MS-DOS using Qemu Hardy/Gusty P4 or AMD64"
date: 2008-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by regor210 on 2008-04-28
What do you need MS-DOS for?
Here are some better choices before we start.

DOS Emulator is in the Repository, and it is easy to use.
$ sudo apt-get install dosemu

DosBox is also nice and has SoundBlaster support for dos sound. 
$  sudo apt-get install dosbox

Freedos is Grate!
I used this guide to install Freedos.
[http://linuxhelp.blogspot.com/2006/09/concise-guide-to-installing-and-using.html](http://linuxhelp.blogspot.com/2006/09/concise-guide-to-installing-and-using.html)
You will need Dosidle. See below.
-----------------------------------------
Update, In Ubuntu 9.10 Karmic kvm/Qemu has been merged together. To use Qemu alone you may have to use -no-kvm. My start command now looks like.
$ qemu -cpu pentium3 -hda win98.img -m 256 -soundhw sb16 -localtime -cdrom /dev/cdrom -no-acpi -no-kvm

KVM (for Kernel-based Virtual Machine)
[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)
------------------------------------------
Update 2/19/09
Floppy users if you are using Ubuntu 8.10 Floppy drives are no longer supported by default. 
To make your floppy work you will need to 1st make a place for the floppy to mount to. 

$sudo mkdir /media/floppy0

next start your floppy. Note you will have to use the next 2 command every time you start your computer and want to use Qemu+floppy. Note Qemu will not start if you have this in the start command -fda /dev/fd0 and DON'T have Ubuntu floppy support started. So if you want to start Qemu without floppy support  remove -fda /dev/fd0 from your start command. 

$ sudo modprobe floppy

now mount your floppy in Ubuntu . Click on Places>floppy

$ sudo chmod  a+rw /dev/fd0

fd0 has no read permissions and will not keep permissions on Ubuntu restart.
Note, on my system Qemu will not boot 720k 3.5 disk, 1.440k or 1.5m boot fine.
----------------------------------------------------------

You do not need MS-DOS to play old games so use this guide as needed. This guide Worked on my AMD2X64  2.1Ghz and my Intel P4 2.0Ghz
Note.  The disks I purchased new back in 1994 would not boot. Having already paid for the license , I Googled msdos622.zip and found a zip file with 3 mdos.img. Need help unziping? See below. I burned the img files to floppys with (replace freedos with your img name)
$  sudo dd if=~/freedos.img  of=/dev/fd0

To my knowledge MS-DOS is not freeware [http://support.microsoft.com/kb/79747](http://support.microsoft.com/kb/79747)   You can find new unopened packages for sale on eBay for $10 to $20 US.

If you have not installed Qemu do so now. Open a Terminal click Applications>Accessories> Terminal. Then cut and past or type in this command and press Enter.
$  sudo apt-get install qemu

make a drive, the -f qcow will make a magic drive just the size you need up to 1Gig. mine is 6.3 Mb but it can grow as needed.
$  qemu-img create -f qcow dos.img 1G

Note. you will have to place a floppy in the drive when starting Qemu so it can find the hardware.

place MSDOS disk one in the floppy drive.
Note -m 128 is 128 MB of ram you may want to use less ram replace 128 with what ever you want 8,16,32,64.
$  qemu -fda /dev/fd0 -m 128 -boot a dos.img -localtime

click install so f-disk can set up your drive "it may hang if so no problem"
Close the window and restart, Ctrl+Alt will get you out.
$  qemu -fda /dev/fd0 -m 128 -boot a dos.img -localtime

Install.

If  Qemu hangs at Disk change try this otherwise  
skip this if you can and go to Idle
When a disk change is requested by the DOS setup you may need to swap to a different QEmu virtual floppy drive by pressing Ctrl + Alt + 2 
(qemu)eject -f fda
Enter then Ctrl + Alt + 1, then Enter. see if it worked, if not go back and try.
 (qemu) change -f fda
or
  (qemu) change fda A:\
Enter then Ctrl + Alt + 1, then Enter. see if it worked, if not try.
Ctrl + Alt + 2
Now back in Ubuntu unmount Disk 1 and mount Disk 2.
Right click on floppy icon and unmount.
On the tool-bar ,Places> DISK 1 , to mount.
Click on Qemu, Ctrl + Alt + 1  and start Disk2. 

If still its still not working try restarting the install with. Note when the little Qemu-Control-Main panel pops up. Click connect>floopy A> Eject to swap disks.
$  sudo apt-get install qemuctl
then
$  qemuctl -fda /dev/fd0 -m 128 -boot a dos.img -localtime
[B]
Idle[/B]

3.12.3 MS-DOS and FreeDOS
3.12.3.1 CPU usage reduction
DOS does not correctly use the CPU HLT instruction. The result is that it takes host CPU cycles even when idle. 
What they are trying to say is, you need a program to keep your CPU from over heating.
Get here if you have to **dosidle210.zip**
[http://www.boche.net/dropbox/dosidle210.zip](http://www.boche.net/dropbox/dosidle210.zip)

download
Right click on the dosidle.zip icon and Extract it.
If you can not Extract it, try installing.
$  sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller

Place DOSIDLE.EXE on a floppy and unmount and mount to wright on disk
start your new Qemu DOS drive with
$  qemu -fda /dev/fd0 -m 128 -boot c dos.img -cdrom /dev/cdrom  -localtime -soundhw sb16

If you have 2 cdrom/dvd you may need to use this(note. You could replace the 1 in dev/cdrom1 with a 0 for your other cd/dvd drive)
$  qemu -fda /dev/fd0 -m 128 -boot c dos.img -cdrom /dev/cdrom1  -localtime -soundhw sb16

Note the c tells Qemu to boot from your Hard-Drive.
now do this in DOS
C:\a:
A:\copy dosidle.exe c:\
A:\c:
C:\edit autoexec.bat
scroll down to a new line and type
C:\dosidle.exe
hit Alt, then save and exit
Restart Qemu and you should see (DOSidle installed successfully.)

You can test to see if the(CPU cooler) is working. In Ubuntu System>Administration>System Monitor>Resources
Before, will show 90% to 100% CPU usage at idle.
After , will show close to normal CPU usage at idle. 

If you want a start Icon on your desktop right click on desktop>Create Launcher. Name ( MS-DOS ). Command (  qemu -fda /dev/fd0 -m 128 -boot c dos.img -cdrom /dev/cdrom  -localtime -soundhw sb16  ).> OK. Note. if you cut and pates you may have to Back Space over the little box at the end of the Qemu start command.
If you have 2 cdrom use ( qemu -fda /dev/fd0 -m 128 -boot c dos.img -cdrom /dev/cdrom1  -localtime -soundhw sb16 )  or change the 1 in -cdrom /dev/cdrom1 part to 0 to use the other cdrom/dvd drive. 

Use Ctrl + Alt + f to toggle to and from full screen.
Use Ctrl + Alt  to work outside of the box.

You now have the  QEMU PC System emulator simulating the following peripherals:
    * Cirrus CLGD 5446 PCI VGA card .
    * PS/2 mouse and keyboard
    * 2 PCI IDE interfaces with hard disk and CD-ROM support
    * Floppy disk 
    * Creative SoundBlaster 16 sound card
You can learn about changing or adding to the Peripherals here> 
[http://bellard.org/qemu/user-doc.html](http://bellard.org/qemu/user-doc.html)

The drivers can be found here.
[http://www.claunia.com/qemu/drivers/index.html](http://www.claunia.com/qemu/drivers/index.html)
[http://oldfiles.org.uk/powerload/cdrom.htm](http://oldfiles.org.uk/powerload/cdrom.htm)

Note. you will have to place a floppy in the drive when starting Qemu so it can find the hardware.
I do not think you will need to add this to the launch Command but here it is all the same  -no-fd-bootchk

**Installing Windows 3.x** is simple as win3.X is a Gui for Dos.
Window 3.x uses 100% of your CPU at idle so use
WQGHLT You can get it here.
[http://www.weiqigao.com/software/index.html](http://www.weiqigao.com/software/index.html)

**Installing Windows 95 Upgrade.** You may want to add -std-vga to the end of your Qemu start command if your copy of win95 does not have a Cirrus Logic GD5446 driver, this will stop the error message at start but will not give you better video.
Or use the driver from here. (look at the bottom of the page)
[http://toogam.com/software/archive/drivers/videodrv/videodrv.htm](http://toogam.com/software/archive/drivers/videodrv/videodrv.htm)
Cirrus Logic 5446 version 1.41 for Windos 9x

3.12.2.2 CPU usage reduction
Windows 9x does not correctly use the CPU HLT instruction. The result is that it takes host CPU cycles even when idle. Note that no such tool is needed for NT, 2000 or XP.

Dowload it here if you have to

[http://fly.isti.cnr.it/pub/software/w95/](http://fly.isti.cnr.it/pub/software/w95/)
amnhltm.zip
In other words you do not want your CPU to over heat. Right click on the amnhltm.zip icon and Extract it. Burn it to a cd or place the amnhltm file on a floppy and unmount and mount to wright on disk. Start win95. Open the amnhltm file and dbl click on the amnhltm dos icon to install. And yes wright it to the registry. Dosidle will not work when Windows is running, so yes you need Amnhltm. 


Your good to go. Have fun.

---

### Post by lindylex on 2008-11-11
regor210, your QEMU solutions here are simple the best.
I was looking for Realtek 8139 network adapter drivers for Window 95 guest on Debian Etch host for two days and your link [http://www.claunia.com/qemu/drivers/index.html](http://www.claunia.com/qemu/drivers/index.html)

Have all the drivers you will ever need, you the man!

Thanks Lindylex

---

