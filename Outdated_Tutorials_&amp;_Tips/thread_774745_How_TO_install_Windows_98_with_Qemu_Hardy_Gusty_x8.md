---
title: "How TO install Windows 98 with Qemu Hardy/ Gusty x86/ AMD64"
date: 2008-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by regor210 on 2008-04-29
Wine is a compatibility layer for running Windows programs in Linux/Ubuntu, And is my first choice when running Windows only software.
$   sudo apt-get install wine

Duel booting is out of the question with Win98 and my AMD64x2 so its Qemu  to the rescue. Note this guide will work on most x86 computers.
 
**Gamers **unfortunately 3d acceleration is not yet supported on virtual machines. 
[http://ubuntuforums.org/showthread.php?t=750445](http://ubuntuforums.org/showthread.php?t=750445)
[http://ubuntuforums.org/showthread.php?t=601058](http://ubuntuforums.org/showthread.php?t=601058)
Oddly The Sims 1 ran well with the Universal VESA/VBE Video Display Driver VBE 3.0 I tested in Windows 2000 with Qemu & Kqemu. That said if you are going to install Win2k or higher I suggest duel booting or Virtualbox.
 
-----------------------------------------
**Update, In Ubuntu 9.10 Karmic** kvm/Qemu has been merged together. To use Qemu alone you may have to use -no-kvm. My start command now looks like.
$ qemu -cpu pentium3 -hda win98.img -m 256 -soundhw sb16 -localtime -cdrom /dev/cdrom -no-acpi -no-kvm

KVM (for Kernel-based Virtual Machine)
[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)
------------------------------------------

How to install Windows 98 with Qemu

Install Qemu if you do not already have it.
$   sudo apt-get install qemu

**Make a virtual Drive.**
-f qcow2 will make an expandable virtual Hard-drive. 10G limits the size to 10 Gig, feel free to add as many Gigs as you want up to 32 Gigs. The win98.img will only take as much space as it needs. Mine is now 64.7Mb less than a gig fully installed but will grow as needed. You can go higher than 32 Gig but scandisk will corrupt large disks unless you disable it.
$  qemu-img create -f qcow2 win98.img 10G

If you want to install from a boot disk, read down to BOOT DISK.

If you have to install Dos and upgrade, use this guide 1st.
[http://ubuntuforums.org/showthread.php?t=773327](http://ubuntuforums.org/showthread.php?t=773327)

Place your Windows 98 cdrom in your cd/dvd drive. The -m 256 is telling Qemu to use 256Mb of ram. you can change to 128 or 64 or 32 if you like.
$  qemu -localtime -cdrom /dev/cdrom -m 256 -boot d win98.img

If you have 2 cd/dvd drives you my need to use this. Note the 1 next to the cdrom could be 0 for your other drive.
$  qemu -localtime -cdrom /dev/cdrom1 -m 256 -boot d win98.img

If the instillation hangs just restart using  your choice of the last 2 lines starting with $. Pressing Ctrl+Alt will get you out of the box. Note. If for some reason Qemu freezes your desktop try Ctrl+Alt+ BackSpace to log out.
------------------------------------
Update 2/19/09
Floppy users if you are using Ubuntu 8.10 Floppy drives are no longer supported by default. 
To make your floppy work you will need to 1st make a place for the floppy to mount to. 

$sudo mkdir /media/floppy0

Next start your floppy. Note you will have to use the next 2 command every time you start your computer and want to use Qemu+floppy. Note Qemu will not start if you have this in the start command -fda /dev/fd0 and DON'T have Ubuntu floppy support started. So if you want to start Qemu without floppy support  remove -fda /dev/fd0 from your start command. 

$ sudo modprobe floppy

Now mount your floppy in ubuntu . Click on Places>floppy

$ sudo chmod  a+rw /dev/fd0

fd0 has no read permissions and will not keep permissions on restart.
-----------------------------------

**Do not overheat your CPU.**
[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC51](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC51)
3.12.2.2 CPU usage reduction
Windows 9x does not correctly use the CPU HLT instruction. The result is that it takes host CPU cycles even when idle. You can install the utility from [http://www.user.cityline.ru/~maxamn/amnhltm.zip](http://www.user.cityline.ru/~maxamn/amnhltm.zip) to solve this problem. Note that no such tool is needed for NT, 2000 or XP. 

**amnhltm.zip** Using Ubuntu download here if the other link is still dead.
[http://fly.isti.cnr.it/pub/software/w95/](http://fly.isti.cnr.it/pub/software/w95/)

Right click on the amnhltm.zip icon and Extract it.
If you can not Extract it, try installing.
$  sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller. 

Burn it to a cd or Place the amnhltm file on a floppy and unmount and mount to wright on disk. Start win98 with 
( do not forget the 1 if you need it,cdrom1)
No floppy $  qemu -localtime -cdrom /dev/cdrom -m 256 -boot c win98.img

yes floppy $  qemu -fda /dev/fd0 -cdrom /dev/cdrom -m 128 -boot c win98.img -localtime

open the amnhltm file and click on the amnhlt dos icon to install, and  yes wright it to the registry.  Restart Win98.

You can test to see if the(CPU cooler) is working. In Ubuntu System>Administration>System Monitor>Resources
Before, will show 90% to 100% CPU usage at idle.
After , will show close to normal CPU usage at idle. 

If this all went well you can start Win98 with. ( If you have 2 cdrom/dvd add a 1 or 0 to the end of this command (/dev/cdrom1))
$  qemu -hda win98.img -m 256 -soundhw sb16 -localtime -cdrom /dev/cdrom

If you have a floppy drive use (do not forget the cdrom1 if you need it)Note. you will have to place a floppy in the drive when starting Qemu so it can find the hardware.
$  qemu -hda win98.img -m 256 -soundhw sb16 -localtime -cdrom /dev/cdrom -fda /dev/fd0

The QEMU PC System emulator is now simulating  the following peripherals:
    * i440FX host PCI bridge and PIIX3 PCI to ISA bridge
    * Cirrus CLGD 5446 PCI VGA
    * PS/2 mouse and keyboard
    * 2 PCI IDE interfaces with hard disk and CD-ROM support
    * Floppy disk
    * Creative SoundBlaster 16 sound card

Win98 should find and install your drivers automatically.

 Use Ctrl + Alt + f to toggle to and from full screen.
 Use Ctrl + Alt  to work outside of the box.

You can learn about changing or adding to the Peripherals here> 
[http://fabrice.bellard.free.fr/qemu/user-doc.html](http://fabrice.bellard.free.fr/qemu/user-doc.html)

Drivers can be found here.
[http://www.claunia.com/qemu/drivers/index.html](http://www.claunia.com/qemu/drivers/index.html)
[http://oldfiles.org.uk/powerload/cdrom.htm](http://oldfiles.org.uk/powerload/cdrom.htm)

You can get 10 years of up dates for Windows 98 Second Edition here.
Auto-Patcher for Windows 98SE
December 2007 Final (FULL):
[http://soporific.dsleague.com/main/?page_id=7](http://soporific.dsleague.com/main/?page_id=7)
Download with Ubuntu and burn Auto-Patcher.EXE  to a CD or use the iso trick(see below).  
(Note. I had to restart my Unbuntu Desktop twice when updater locked up win98. Seems worth it as  Auto-Patcher did a thorough job updating. It would be a good idea to backup your win98.img file in your home folder just in case something go's wrong.)

**BOOT DISK**
Boot disk can be found here.
[http://www.allbootdisks.com/download/98.html](http://www.allbootdisks.com/download/98.html)
[http://www.bootdisk.com/](http://www.bootdisk.com/)
Download the Windows98.img to your home folder and put an empty floppy in the drive( note kfloppy is a nice floppy formatter, works in Gnome)
$  sudo dd if=~/Windows98.img  of=/dev/fd0

Then you would start up the boot disk with (  Do not forget to make a  virtual drive 1st.)( Do not forget the 1 if you need it,cdrom1)( Put your Windows98 cdrom in and let it mount before starting)
$  qemu -fda /dev/fd0 -cdrom /dev/cdrom -m 128 -boot a win98.img -localtime

Run fdisk, restart, format c:  ,e:\  , setup

Now you can Boot from your hard-drive using(cdrom1 ?)
$  qemu -hda win98.img -m 256 -soundhw sb16 -localtime -cdrom /dev/cdrom -fda /dev/fd0

[http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QuickStartGuide](http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QuickStartGuide)

If you have files you would like to move from Ubuntu to win98 without burning a CD you can make then mount an iso.
**How to create Image (ISO) files** from folders or CD/DVD

This will make a folder called winrom in you Home Folder.  
$  mkdir  winrom

Place the files you want access to in the folder called winrom.

Make the iso. (Note. This will over write any previous winrom.iso in your Home Folder) 
$  mkisofs -r -o winrom.iso  winrom

To mount as a cd (Read only) in Qemu/win98 Note. Long file names will be changed by win98.
Remove 
-cdrom /dev/cdrom 

from Qemu/win98 start command. Then Add 
-cdrom winrom.iso

Start Qemu/win98

If you want view an iso image file in Ubuntu. 
To mount in Ubuntu (read only) You only need to use this line once.
$  sudo mkdir /media/isoimage

then
$  sudo modprobe loop
$  sudo mount winrom.iso /media/isoimage/ -t iso9660 -o loop

To unmount
$  sudo umount /media/isoimage

Use this to make an iso file out of whatever CD/DVD you have in your cd/dvd drive
$  mkisofs -r -o winrom.iso /media/cdrom0

**Improved performance, Hardy/Intrepid only**
On my AMD64X2 computer I was able to boost the Performance of Win98 using the -cpu pentium3 option. You can see what Processors are available on your system using
$  qemu  -hda win98.img -cpu ?

My Qemu start command looks like
$  qemu  -hda win98.img -m 128 -soundhw sb16 -localtime -cdrom /dev/cdrom -fda /dev/fd0 -cpu pentium3

 The difference is not night and day but it is noticeable.

**Virtual Hardware**
This part of my HOW TO is only dealing with Windows 98 Hardware problems.

**WARNING!** Taking Windows 98 on the Internet poses a grate security risks!  some people like to file share with there host so here it is. 

If you have no Internet/Network or other hardware problems.
Try adding 
 -net nic -net user -no-acpi
to the end of your Qemu start command, like

$  qemu -hda win98.img -m 256 -soundhw sb16 -localtime -cdrom /dev/cdrom -fda /dev/fd0 -net nic -net user -no-acpi

Start win98 then go to Start>Programs>MS-DOS Prompt and type in
C:\WINDOWS>ping 10.0.2.2

Your output should look something like this.

Ping statistics for 10.0.2.2:
Packets: sent = 4,  Received =4 Lost = 0 (0% loss),
Appoximate round trip times in milli-second:
 Minium = 1ms, Maximum = 5ms, Average = 2ms

If Lost=4  chances are your Win98 Network card driver is not set up.
goto an Ubuntu Terminal and type
$  qemu -hda win98.img -net nic,model=?

You will see something like this.

qemu: Supported ISA NICs: ne2k_isa
qemu: Supported PCI NICs: i82551 i82557b i82559er ne2k_pci pcnet rtl8139

If you see ne2k_pci move on to Warning. If not you need to try another driver. Pick one from your list and  place it at the end of your Qemu start command.(note I have placed rtl8139 from my list after model=)
-net nic,model=rtl8139 -net user

Now your Qemu start command would look something like this.
$  qemu -cdrom /dev/cdrom -m 256 win98.img -fda /dev/fd0 -net nic,model=rtl8139 -net user  

Start Win98 to see if this worked.

WARNING
This last step may make Window 98 unusable and or crash your Ubuntu desktop or make you restart your computer!
If your desktop locks up try restarting with Ctrl+Alt+Back space. If you have the Hard-drive space it would be a good idea to make a backup.  Go to your home folder. Right click on the win98.img file and click copy. Then past it to your desktop.
 
In Windows 98 goto My Computer>Control Panel>System>Device Manager>

Is there a yellow ! next to Plug and Play BIOS(fail safe) ?If so double click on it.

Update Driver>Next>mark Display a list of all drivers....>mark Show all hardware,>click on PCI bus>Next>The driver that you have chosen was not.... CLICK Yes>Next>The driver you have chosen is older than....CLICK Yes>Finish> Yes Restart

If this worked you are good to go. If not you need to reinstall Windows 98 or restore from backup by renaming the win98.img file in your Home folder, Then copy your backup on your desktop into your home folder. Note you will need the HD space to use this option.  The 1st time I tried the PCI bus option it made windows 98 unusable. the 2nd, 3rd and 4th time it worked fine. Good luck.

Here are some web-sites I used in the making of this part of the guide.
[http://qemu-forum.ipi.fi/viewtopic.php?f=9&t=3072](http://qemu-forum.ipi.fi/viewtopic.php?f=9&t=3072)
[http://lists.alioth.debian.org/piper...er/020390.html](http://lists.alioth.debian.org/piper...er/020390.html)

**Display**
The  default diver Cirrus Logic 5446 PCI  (4m) is capable of 24-bit color up to 1024x768 pixels, or 16-bit up to 1280x1024.
-cirrusvga 

If you have 2 drivers in your Device Manager
-,,,Display adapters
.                ... Cirrus
.                ...!Cirrus Logic 5446 PCI
Disable the one marked with a yellow!
Shut down and restart (twice) then enable again. Shut down and restart (twice)
If still no luck remove it and restart to auto install. Then restart x2
It should work if you play with it a bit. 

-std-vga
VESA VBE virtual graphic card is capable of SVGA. Not all new video cards have a full set of VBE 2.0  instructions. Mine is VBE 3.0 compatible. To my knowledge there is no universal VBE 3.0 driver for windows 98. So -std-vga and -vmwarevga may not work for you. There is a (8M)driver that did not work with my hardware here. 
 [http://www.geocities.com/bearwindows/vbe9x.htm#2](http://www.geocities.com/bearwindows/vbe9x.htm#2)
Here are some more drivers you may be able to use
[http://www.scitechsoft.com/ftp/sdd/](http://www.scitechsoft.com/ftp/sdd/)

**Experimental SVGA**
-vmwarevga 
[http://www.geocities.com/bearwindows/vbe9x.htm#2](http://www.geocities.com/bearwindows/vbe9x.htm#2)
Hardy uses Qemu version 0.9.1. This gives us access to the -vmwarevga option. Making my Qemu start command look like 
$  qemu -hda win98.img -m 128 -soundhw sb16 -localtime -cdrom /dev/cdrom -fda /dev/fd0 -vmwarevga
Goto [http://www.geocities.com/bearwindows/vbe9x.htm#2](http://www.geocities.com/bearwindows/vbe9x.htm#2)
and dowload the Vbmep9x.zip driver. Extract it. Put it on a Disk. 
Install the UNI driver in win98 goto My Computer>Control Panel>System>Device Manager>click Display adapter>click on your adapter>Properties>Driver>Update Driver>Next>click Display a list.....>Next>Have Disk>Browse.. find where you have placed Vbe9x and install the UNI driver. Restart
Now you can goto the Control Panel>Display Properties>Settings and change your Colors and Screen area to what ever you like. Up to (32 bit)1600x1200. (note. If you make your screen size too large you will not be able to toggle to and from full screen using(Ctrl+Alt+f)
[http://fabrice.bellard.free.fr/qemu/changelog.html](http://fabrice.bellard.free.fr/qemu/changelog.html)
version 0.9.1:
 - VMware SVGA II graphics card support (Andrzej Zaborowski)

**CDROM/DVD** disk change
On my hardware changing cd's can some times bug the pipeline from Ubuntu to Qemu/win98. It has been bad enough at times to make me restart my computer. If you can always mount a CD/DVD in Ubuntu before starting Qemu/win98. If you have trubble changing disks with win98 running see this guide. Try using those Disk change tactics with your CDROM, worked for me.
[http://ubuntuforums.org/showthread.php?t=773327](http://ubuntuforums.org/showthread.php?t=773327)

**10/07/2008**
**USB**
Note the Qemu's win98.iso is portable. Portable as, when I changed computers I simply cut & pasted my win98.iso in my home folder to a USB stick and then placed it in my new computers home folder. Qemu's USB support for your computer + win98.iso is not portable. So if you move your win98.iso you will have to reconfigure your USB. That said keep in mind The Microsoft License Agreement. Only have Windows 98 installed on as many computers as you are licensed to use it on. 

USB
1st make sure you ether have the 10 years of updates mention above or your windows 98 usb drivers.  

**Update**&#65279;Ubuntu 8.10 Intrepid Ibex Beta worked well but as of 10/31/08 USB is not working. I will update at a later date. 

Enable old LINUX USB support. 

Place this command in a Terminal and run it to back up mountdevsubfs.sh just in case.

$ sudo cp /etc/init.d/mountdevsubfs.sh /etc/init.d/copy-mountdevsubfs.sh

Edit
$ sudo gedit /etc/init.d/mountdevsubfs.sh

Scroll down to 

	# Magic to make /proc/bus/usb work
	#
	#mkdir -p /dev/bus/usb/.usbfs
	#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	#ln -s .usbfs/devices /dev/bus/usb/devices
	#mount --rbind /dev/bus/usb /proc/bus/usb
}

Uncomment these 4 lines under #Magic.... By removing the #.

# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
}

Save it and restart mountdevsubfs.sh using

$ sudo /etc/init.d/mountdevsubfs.sh start

Set permissions 
With Hardy you will have to run 

$ sudo chmod -R a+rw /proc/bus/usb

every time you restart your computer as  /proc/bus/usb has issues with permissions. Intrepid dos not have this problem.

Note. With Hardy you have to use the same port on your computer when starting Windows. In other words place your USB drive in the same hole every time you start your computer. 

**Add** -usb to your win98 start command making it look something like this

$ qemu -hda win98.img -m 512 -soundhw sb16 -localtime -cdrom /dev/cdrom -fda /dev/fd0 -usb 

While in Windows 98 press Ctrl+Alt+2 to bring up a Qemu terminal. Type in   info usbhost  .  You should see something like.

Device 2.4 speed 480 mb/s
    Class 00: USB device 0781:5406, U3 Cruzer Micro
Device 1.6 speed 1.5 mb/s
    Class 00: USB device 06a3:8020, Saikek Eclips Keyboard

Find your device number. Mine is 0781:5406 for my USB drive. Note if you Ctrl+Alt then hit Prt Scrn you can take a picture.

 Press Ctrl+Alt+1 and shutdown Windows. Add -usbdevice host:"your device number" to your Qemu start command mine looks like this

$ qemu -hda win98.img -m 512 -soundhw sb16 -localtime -cdrom /dev/cdrom -fda /dev/fd0 -usb -usbdevice host:0781:5406

Note. you will have to have your USB drive plugged in and mounted before starting Windows. 

Note. When asked by windows whether  to keep a new file or replace it with an older one? I recommend keeping the newer file.

Note. When asked for the location of USB driver I checked the box for the Windows 98 setup CD.

Note. I had to reformat my USB drive to Fat16 for Windows 98 to read it. Fat32 may have worked.  I did not try it as my USB drive was to suppose to have already been Fat32. I use Gparted to format it in Ubuntu. Use Gparted with caution as reformatting the wrong drive will be a disaster!
$ sudo apt-get install gparted 

You should be good to go if not try restarting Ubuntu to make sure the changes take affect.

---

### Post by spydon on 2008-05-05
Why use qemu when there is for example virtualbox?
I admit that qemu is very nice, but only for smaller operatingsystems like OpenMoko.

---

### Post by regor210 on 2008-05-05
**Virtualbox**
After making some adjustments I was able to get Win98 running on Virtualbox with 
CPU Unknown ,2100 MHz
Memory Write speed 329 MB/s
That said I was not able to find working win98 video and sound drivers that worked with my hardware.
I tried here
[http://virtualbox.org/wiki/User_FAQ](http://virtualbox.org/wiki/User_FAQ)
[http://www.bearwindows.boot-land.net/vbe9x.htm](http://www.bearwindows.boot-land.net/vbe9x.htm)

If anyone knows of a place to find Virtualbox drivers for win98 that work please share.

Qemu's virtual hardware is supported by the windows 98/98SE setup cdrom.   Making it somewhat easy to setup. 

Here is a fun place.
[http://www.oszoo.org/wiki/index.php/Category:OS_images](http://www.oszoo.org/wiki/index.php/Category:OS_images)

---

### Post by noabody on 2008-10-04
This post was invaluable in helping me to install Windows 98.  Using this information I successfully installed Windows 98 Second Edition about seven times (using Qemu Manager running in Windows XP).

I wanted to add that Qemu seems to be picky about the file structure of some CD's and ISO images.  In my case I couldn't progress beyond 75% file copy using a slightly modified 98 SE CD (added msbatch.inf to automatically input the CD-Key).  I had to image an original disc to get it working.

The install always crashed once during hardware auto detection and I ended up having a fail safe Plug and Play BIOS.  I also had two instances of the Cirrus video driver after installing the PCI bus.  I found that removing the Cirrus driver, ignoring the prompt to reboot, and then updating the fail safe BIOS using PCI bus resulted in only one instance of the Cirrus driver.

Installing PCI bus for me was like doing the entire hardware autodetection phase of setup.  It installs all of the computer related peripherals including the IDE bus.  I found that caused problems because the computer would look for the CD-ROM to install some of the drivers while the IDE bus had not yet been installed.

To simplify the procedure and guarantee success I setup Windows 98 by booting the ISO and choosing CD-ROM and then start the computer with CD-ROM support.  This drops out to a DOS prompt where I fdisk then format the C: drive.  With C:\> as the prompt I ran these commands:
mkdir WINDOWS
mkdir WINDOWS\CABS
D:            (drive letter for CD-ROM)
cd WIN98
copy *.* C:\WINDOWS\CABS\*.*
C:
cd WINDOWS\CABS
setup

This copies the setup files from the CD image to the hard disk image and begins setup from the hard disk.  During installation of the PCI bus the system never loses connection to the hard disk and the drivers are stored there so the installation goes without incident.  It takes more time to do it this way but is maybe a little more reliable.

I only botched the PCI bus installation the first time and never again.

---

### Post by lindylex on 2008-11-14
regor210, this was perfect, thanks.  I ran into some problems installing Windows 98 not documented here.  I will document the solutions later today.

Thanks

---

### Post by lindylex on 2008-11-14
**Fix Windows 98 "error messages vnetsup.vxd,vredir.vxd,dfs.vxd and another error pops up before windows loads msnp32.dll"**

"...choosusr.dll and dfs.vxd are on my Win98SE CD. The other two .vxd's are not. It is possible that your 98 CD may be scratched or need cleaning. The two .vxd files that are not on the Win98 CD are specific to your Ethernet card or modem and should be on the motherboard CD."

"If you were to go to Start>Run and type in sfc you will bring up System File Checker. This is a Windows utility that looks for files that have changed or been corrupted. It also allows you to Extract files that you need from your 98 CD. If you were to click on Extract and then type in the file you are looking for, say dfs.vxd, and click Start, another box will pop up asking you where to extract from and where to extract to. In the Restore From box you would browse to the 98 CD and in the Save file in box you would browse to, in this case, C:\Windows\System."

"You can run SFC periodically to look for changed or corrupted files, but it can be a confusing exercise as files are changed all the time through updates, program installations and the like."

"More information on System File Checker can be found here."

Solutiuon from here:

[http://www.bleepingcomputer.com/forums/lofiversion/index.php/t9236.html](http://www.bleepingcomputer.com/forums/lofiversion/index.php/t9236.html)

**Fix Windows 98 "pops up before Windows loads msnp32.dll"**

Go to Control Panel | Network and see if Client for Microsoft Networks is installed. If it isn't, uninstall it, reboot then go back to the same place a reinstall it.

---

