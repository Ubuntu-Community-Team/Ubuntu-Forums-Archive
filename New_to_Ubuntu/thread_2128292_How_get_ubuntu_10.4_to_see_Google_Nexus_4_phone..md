---
title: "How get ubuntu 10.4 to see Google Nexus 4 phone."
date: 2013-03-22
forum: New to Ubuntu
---

### Post by mawil1013 on 2013-03-22
((Forward: I have primitive command line skills.  If you have a solution that can only be performed via command line, please, please, try to give as much step by step if possible. Sincerely grateful.))

I have a laptop running ubuntu 10.4,, no higher version will run on it, I've tried several times so that's not an option.  I have a Google Nexus 4 running Jelly Bean.

When I plug the two together via USB, I go into, 'computer', there is no icon for the phone.  I want to transfer songs from the laptop over to the phone via USB.

Is it possible to resolve this?

Michael.aw

---

### Post by DuckHook on 2013-03-22
With the advent of Honeycomb (I believe), Google dropped support for USB file transfer and went to MTB. This format is not native to 10.04 and you won't be able to read it. 13.04 is supposed to have GVFS-MTB support, but you've already stated that you can't run anything later than 10.04. Perhaps you can consider dropbox. Others have reported success using ftp (which requires you to load a ftp app onto your Nexus). ftp is native to Ubuntu and aleady exists on the command line, but it's best for you to use Filezilla, a great GUI app that makes using ftp a breeze. You can find it in the Software Center.

On a related note, you may wish to consider a different distro like Crunchbang which should still run your HW but will be kept updated. As I'm sure you know, support for 10.04 will end in a few days time and an unpatched OS is just asking to get owned.

---

### Post by 3rdalbum on 2013-03-23
Duckhook is right, but just because 12.04 doesn't run on your computer doesn't mean 13.04 won't.

MTP is included in 10.04 but it is always buggy and therefore wont see any Android 4 devices. Your best option is to install an FTP server on the Nexus.

10.04 will be unsupported on the desktop in a month, you really need to update, even if to a different distro or a modern lightweight distro.

---

### Post by vanadium on 2013-03-23
go-mtpfs may work under 10.04 ([http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)). gvfs with mpt support will be included in 13.04, but can be installed in 12.04 or 12.10 also ([http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)). It will indeed be difficult indeed to both run 10.04 *and* catch up with the new features. I also second that setting up an ftp server on your nexus probably is the best solution if you need to stick with 10.04.

---

### Post by Isamu715 on 2013-03-23
You may try connecting your phone as a camera, I believe Android lets you choose how you want to connect your phone. A dialog stating "Connected as a multimedia device" should appear in the phone notification area, click it and switch to "Connect as a digital camera(PTP)". Chances are the system will be able to recognize your phone and although you will only have access to the "Pictures" folder you can always move files on the phone later.

---

### Post by CDR Services on 2013-03-25
There is an free android app called WiFi File browser it sets up a switchable web address on the phone and you can transfer files through any web browser.

---

### Post by alphasoup on 2013-10-20
Have been watching this thread for 9 month...
When MTPFS began to fail from Ubuntu 10.4 to Nexus.
Then I followed instructions to install go-mtpfs from Vanadium link above: 
[https://github.com/hanwen/go-mtpfs](https://github.com/hanwen/go-mtpfs)
While there were issues compiling on Ubuntu 10.4, after hardcoding missing data, the following got it working as in Examples below.
> Disclaimer: do at your own risk (this just happened to work for me)...

A) First install go and check that it works:
[http://golang.org/doc/install](http://golang.org/doc/install)
I also needed to install: git package (e.g. selected git-gtk from Synaptic, and installed it)

B) Install libusb version that is supported on Ubuntu 10.4:
 sudo apt-get install libusb-1.0-0-dev

C) Follow instructions from link go-mtpfs: [https://github.com/hanwen/go-mtpfs](https://github.com/hanwen/go-mtpfs)
when install go-mtpfs fails during compile 
> Edit this file in <your install dir>/go-mtpfs/go/src/github.com/hanwen/go-mtpfs/usb/
Change file: usb.go
1) hardcode enum values:
Note: for beginners at editing, this is output from "diff -c original_file new_file", the "!" at beginning of line is to mark a line that needs to change, do not include that "!" in the code...
> 
! const SPEED_UNKNOWN = 0 //C.LIBUSB_SPEED_UNKNOWN
! const SPEED_LOW = 1 //C.LIBUSB_SPEED_LOW
! const SPEED_FULL = 2 //C.LIBUSB_SPEED_FULL
! const SPEED_HIGH = 3 //C.LIBUSB_SPEED_HIGH
! const SPEED_SUPER = 4 //C.LIBUSB_SPEED_SUPER
  
  var SPEED_names = map[byte]string{
!       0 /*byte(C.LIBUSB_SPEED_UNKNOWN)*/: "UNKNOWN",
!       1 /*byte(C.LIBUSB_SPEED_LOW)*/:     "LOW",
!       2 /*byte(C.LIBUSB_SPEED_FULL)*/:    "FULL",
!       3 /*byte(C.LIBUSB_SPEED_HIGH)*/:    "HIGH",
!       4 /*byte(C.LIBUSB_SPEED_SUPER)*/:   "SUPER",
  }
  
  type ControlSetup C.struct_libusb_control_setup


2) hardcode this error function (section from: diff -c):
> *** 118,124 ****
  type Error int
  
  func (e Error) Error() string {
!       return C.GoString(C.libusb_error_name(C.int(e)))
  }
  
  func toErr(e C.int) error {
--- 118,124 ----
  type Error int
  
  func (e Error) Error() string {
!       return /*C.GoString*/("Unknown error: C.libusb_error_name(C.int(e))")
  }
  
  func toErr(e C.int) error {
***************


3) Then hardcode second one (section from diff -c)
-- I just picked a number 30000 -- worked for me:
> *** 521,527 ****
  
  // Get the negotiated connection speed for a device.
  func (d *Device) GetDeviceSpeed() int {
!       return int(C.libusb_get_device_speed(d.me()))
  }
  
  // Convenience function to retrieve the MaxPacketSize value for a particular endpoint in the active device configuration.
--- 521,527 ----
  
  // Get the negotiated connection speed for a device.
  func (d *Device) GetDeviceSpeed() int {
!       return /*int(C.libusb_get_device_speed(d.me()))*/ 30000
  }
  
  // Convenience function to retrieve the MaxPacketSize value for a particular endpoint in the active device configuration.


After this go-mtpfs should build and work ok, except I had to rely on sudo to access my device (even to list the device directories).

D) Ensure your device is recognized:
1) First thing first:
[Note: I had Ubuntu MTPFS setup before, used to work, got broken with updates]:
[http://forum.manjaro.org/index.php?topic=1672.0](http://forum.manjaro.org/index.php?topic=1672.0)
"On the Nexus7 make sure that USB debugging is ticked.(Go to Developers options in Android 4.1 and if you have Android 4.2 you will have to go to Settings/About tablet/then tap Build number 7 times and the Developer option will appear in Settings menu)"

sudo lsusb #-- find your device
Example:
USB:
   idVendor: 18d1
   idProduct: 4e41

SUBSYSTEM=="usb", ATTR{idVendor}=="VENDORID", ATTR{idProduct}=="PRODUCTID", MODE="0666"

2) If your device is not already present, add this line into (replace with values for your device):
/etc/udev/rules.d/51-android.rules

SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e41", MODE="0666"

E) Access your device via go-mtpfs:
On Ubuntu 10.4 plug in USB your Nexus, then:
1) mkdir -p /media/GalaxyNexus
2) To connect device (in a terminal)
   > sudo ~/go-mtpfs/go/bin/go-mtpfs /media/GalaxyNexus 
   [sudo] password for <username>: 
   2013/10/19 23:51:47 starting FUSE.

3) To copy a new album use another terminal:
Example:
> 
   cd ~/Music/Led\ Zepplin/Mothership\ CD\ 1/

   album="${PWD##*/}"
   upone="${PWD%%/$album}"
   artist="${upone##*/}"
   for f in *mp3; do sudo cp "$f" /media/GalaxyNexus/Internal\ storage/Music/"$artist - $album $f"; done


Note: My Nexus was not accessible from Rhythmbox so I copied  files directly (via sudo) to the device storage from ~/Music folder.

3) To disconnect device:

   > sudo fusermount -u /media/GalaxyNexus

---

### Post by abdulmajid on 2013-12-22
Hi,

I have ubuntu 12.04 with an encrypted home drive. I have an ftp client on my Nexus 4 (X-plore) but since my home drive is encrypted the login from ftp client wont unlock my passphrase. How can I get my passphrase to unlock from ftp login or samba login?

---

### Post by Isamu715 on 2013-12-22
This is an entirely different issue, please start a new thread.

---

### Post by efflandt on 2013-12-22
Useful apps for Android: **ConnectBot** (ssh client), **AndFTP** (sftp client), **SSHServer**. I don't know if that would work "to" Ubuntu with encrypted partition (I have never done that), but at least "from" Ubuntu you could connect sftp or nautilus (file manager) using sftp to your phone on WiFi. I use my Linux ssh keys on the phone. I never could get MTP or PTP working in 12.04 with my S3 (works in 13.10 on new laptop).

---

