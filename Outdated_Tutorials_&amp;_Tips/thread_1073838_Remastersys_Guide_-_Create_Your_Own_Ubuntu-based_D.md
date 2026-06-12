---
title: "Remastersys Guide - Create Your Own Ubuntu-based Distro"
date: 2009-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by grndslm on 2009-02-18
[size=5]NOTE:  Beware of copying and pasting commands with [color=red]< >[/color] brackets as it completely depends on your individual setup.[/size]

**REMASTERSYS RESOURCES**
+ IMPORTANT resources & files:
[list][*][[COLOR=Blue]Remastersys Home[/COLOR]](http://www.geekconnection.org/remastersys/remastersystool.html)
[*][[COLOR=Blue]Remastersys Forum Home[/COLOR]](http://www.geekconnection.org/remastersys/forums/index.php)
[*][[COLOR=Blue]Remastersys Wiki[/COLOR]](http://klikit.pbwiki.com/Remastersys)
[*][[COLOR=Blue]Capink's in-depth explanation[/COLOR]](http://www.remastersys.klikit-linux.com/capink.html) of Fragadelic's Remastersys script
[*]Or if you're a scripter, examine /usr/bin/remastersys.  I tried adding the -noI -noD -noF switches inside the script so that squashfs would be uncompressed, but the boot and install take nearly 40% longer on machines with only 512MB of ram.  That, in addition to wasted disk space and possibly bandwidth, means you should prolly just avoid making that same change.
[*]And when you edit /etc/remastersys.conf, DO NOT change the LIVEUSER variable to "user" or "gdm".
[*]Add one of these repositories, depending on your distro:
[/list]
> # Remastersys Debian
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) debian/

# Remastersys Ubuntu (For Gutsy & Earlier - version 2.0.11-1)
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/

# Remastersys Ubuntu (For Hardy, Intrepid, & Jaunty - version 2.0.12-1)
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

# Remastersys Ubuntu (For Karmic & Newer w/ grub2 support - version 2.0.13-1)
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

**REMASTERSYS NOTES**
[list][*]The only real difference between backup and dist modes is that backup mode copies the /home directory to the CD/DVD.  Dist mode auto-logins to the desktop with the LIVEUSER you create, whereas backup mode stops at GDM, waiting for a specific user on your current machine to login and eventually find their normal desktop on the CD/DVD and the installed system.
[*]Either way, the compressed filesystem will need to be 4GB or less.  No buts about it, unless of course, you're a genius with ample time on your hands.  That also means backup mode will need to include your /home folder in that 4 GB iso.
[*]Run *aptitude clean* to get rid of unnecessary .debs.
[*]When you run *remastersys dist*, you create your dist CDFS, which is eventually converted into your dist ISO.  If you only need to edit one file, such as menu.lst so you can change Grub's timeout... just go to the CDFS chroot ( /home/remastersys/ISOTMP/ ) and you'll see the filesystem layout of your dist CD.  In this example, edit /home/remastersys/ISOTMP/boot/grub/menu.lst and then you'll be ready to run *remastersys dist iso* since there's no reason to run the regular dist command and completely re-create the CDFS.
[*]If you've already run remastersys, and you need to make drastic changes, make sure to run *remastersys clean* before *remastersys dist*.
[*]When you're ready to test the .iso out, use a virtual machine like VMware, VirtualBox, or QEMU... so you don't have to waste any CDs or time burning the CDs.
[*]And just FAIR WARNING:  I would highly consider avoiding Intrepid & Jaunty if you're planning on many, many people using this, particularly machines with Intel-based graphics... as I've found two Intel machines that display a cruddy Xorg immediately after only upgrading default Ubuntu packages (NOT installing anything extra yet)... but I do like most of the software better in Intrepid.  Jaunty is definitely still too new right now.  Debian Lenny might be best for a larger, supported distro as it is now officially stable.
[/list]

**DISTRO PREP**
[list][*]Upgrade and install all your packages.  Google Desktop might be a possible addition to your dist.
[*]Remove all unnecessary packages.  Here is a [[COLOR=Blue]nice guide[/COLOR]](http://ubuntuforums.org/showthread.php?t=820804) with an example of what I've chosen to remove from my system:[/list]
*aptitude purge ubuntu-desktop ttf-arabeyes ttf-arphic-uming ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-thai-tlwg ttf-unfonts-core language-support-en language-support-translations-en language-support-writing-en myspell-en-za openoffice.org-thesaurus-en-au openoffice.org-l10n-en-za openoffice.org-l10n-en-gb openoffice.org-help-en-gb scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket libscim8c2a libchewing3 brltty brltty-x11 gnome-app-install ubufox apturl tracker tracker-search-tool libdeskbar-tracker libtracker-gtk0 deskbar-applet fast-user-switch-applet tomboy*
[list][*]Move all backgrounds to /usr/share/backgrounds/
[*]Move all GDM themes to /usr/share/gdm/themes/
[*]Move all other themes to /usr/share/themes/
[*]Move all icons & cursors to /usr/share/icons/
[*]Likewise, move all usplash themes somewhere in /usr/share/, or splashy themes to /etc/splashy/themes/
[*]Make your graphical changes (GNOME, KDE, etc.).  I use GNOME, and I like to move my volume applet to the top right for easy wheel scrolling of volume.  Everybody I know that uses Ubuntu says that's their favorite part about the way I configure it for them.  I add the weather applet to the left of the volume applet, and then I add the system monitor applet somewhere on the top panel and enable the memory, networking, swap, & hard disk graphs.  I lock the applets and panels.  It's best to organize these applets thru the gconf-editor.  Then, I right-click the applications menu to edit it and do a little trimming.  I use the GNOME Keyboard app to make the CapsLock an extra Ctrl key.  I also edit the GNOME "Sessions" and "Services" apps to trim them down to something I find more reasonable (i.e. - no bluetooth, no automatic upgrade manager, & no "user folders update", among other things).  Then I use sysv-rc-conf to trim some more.  If you want to use Compiz Fusion, it's prolly best to install fusion-icon and switch to metacity right before copying your config files to /etc/skel/.  I make sure Nautilus, Firefox [extensions], and other programs are setup the way I like...
[/list]

**COPY WORTHY CONFIG FOLDERS TO SYSTEM WIDE FOLDERS**
[list][*]Don't copy .xchat/ as it saves your username in the config.
[*]Don't copy .wine/ as it is very problematic, try using the global wine folder, which is (??).
[*]Clear all Firefox cache and GNOME Recent Documents cache right before doing this.
[*]Clearly, you must be a superuser to do this, so don't forget about sudo.  Now might be a good time to use sudo's -s switch so you don't need to type sudo before all these commands:[/list]
[i]sudo -s
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /etc/skel/
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /root/
cd /etc/skel
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/
cd /root
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/[/i]

**GDM**
[list][*]Use GNOME "Login Window" app to select your new theme and login background colors.
[*]Remember the HEX values for the color, as you'll need them later.
[*]Search for the terms GraphicalTheme & GtkTheme in these two files and you'll see 4 variables you need to change your GDM theme, GtkTheme, and 2 background color for pre- and post-login.  Should be near lines 504, 347, & 466.[/list]
[i]sudo [color=red]<EDITOR>[/color] /etc/gdm/gdm.conf
sudo [color=red]<EDITOR>[/color] /etc/gdm.conf-custom[/i]

**BOOT SPLASH**
[list][*]Only way I know of to customize Usplash is to use the Startup Manager program.
[*]Using most Usplash themes was buggy for me on recent versions of Ubuntu.
[*]As long as the theme works on your computer, it should work on both the dist cd & dist install.
[*]Splashy is an easy alternative to Ubuntu's default Usplash.
[*]Splashy allows you to create boot, shutdown, suspend, resume, & error images of your choice with a progress bar.  Just make sure to use PNGs otherwise you'll get an Error -3.
[*]Simply this command to create splashy themes:[/list]
*splashy -c*

**BOOT LOADER**
[list][*]This is only for the CD, it will not copy to the dist install as ubiquity & update-grub create a custom Grub config for the new system during install.
[*]If you want to alter the installed Grub, update-grub must be altered, then the package must be flagged to never upgrade.
[*]You could also choose ISOLINUX if GRUB doesn't work on some extremely rare chipsets.
[*]EDIT the Grub config files in /etc/remastersys/grub/:[/list]
*sudo [color=red]<EDITOR>[/color] menu.lst.gutsyandbefore*  -OR- *menu.lst.hardyandlater*
[list][*]CREATE Grub background & move to proper folder:[/list]
[i]convert infile.jpg -resize 640x480 -colors 14 -depth 8 splash.xpm.gz
mv splash.xpm.gz /etc/remastersys/grub/[/i]
[list][*]If you plan on editing the update-grub script to reflect your changes on the installed system, you can move your splash image to the shared folder:[/list]
*mv splash.xpm.gz /usr/share/grub-installer/splash.xpm.gz*

**PRESEEDING**
[list][*]Preseeding allows you to customize what variables are passed to the Ubiquity installer, but it only works if you use ubiquity's --automatic switch.  I don't need to make it automatic for everybody yet, but whenever I install it I can simply press Alt+F2 and type in "ubiquity --automatic" so that my language, time zone, & keyboard layout are automatically passed to the installer.  I only use this in my config right now, but there are more options available which can be seen here, in this [[COLOR=Blue]example guide[/COLOR]](https://help.ubuntu.com/8.04/installation-guide/i386/appendix-preseed.html).
[*]Eventually remastersys will copy all preseeds from the /etc/remastersys/preseed/ folder for multiple machines and/or purposes.
[*]Until then, just add your own preseed options to /etc/remastersys/preseed/custom.preseed
[/list]
> 
# Locale sets language and country.
d-i debian-installer/locale string en_US

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
#d-i console-setup/modelcode string pc105
d-i console-setup/layoutcode string us
# To select a variant of the selected layout (if you leave this out, the
# basic form of the layout will be used):
#d-i console-setup/variantcode string dvorak

# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean false

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string US/Central

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean true
# NTP server to use. The default is almost always fine here.
#d-i clock-setup/ntp-server ntp.example.com

**STATIC DNS (OpenDNS), EVEN WITH DHCP**
[list][*]EDIT resolvconf:
[/list]
[i]sudo -s
mkdir /etc/resolvconf/resolv.conf/
[color=red]<EDITOR>[/color] /etc/resolvconf/resolv.conf/base[/i]
+ ADD:
> nameserver 208.67.222.222
nameserver 208.67.220.220

[list][*]EDIT the DHCP client:
[/list]
*[color=red]<EDITOR>[/color] /etc/dhcp3/dhclient.conf*
+ REPLACE the "#prepend domain-name-servers" line with this:
> prepend domain-name-servers 208.67.222.222,208.67.220.220;

**RESTRICTED FIRMWARE AND DRIVERS**
[list][*]It's prolly a good idea to add restricted hardware drivers or firmware, especially for wireless networking.
[*]It's also prolly a good idea to let the *jockey-gtk* "Hardware Drivers" app juggle between the multiple Nvidia and ATI drivers *after* installation.  There are older, legacy graphics cards that won't work with the newest drivers from these manufacturers' websites.
[*]I only wanted to support all the wireless cards possible and NTFS support for easy resizing of Windows partitions, so I installed these packages:
[/list]
*sudo aptitude install b43-fwcutter ndisgtk madwifi linux-restricted-modules ntfs-3g ntfs-config*

**USB PERSISTENCE**
[list][*]If using 8.10 or later, simply use the usb-creator tool, which is installed by default in Intrepid.
[*]If using 8.04 LTS, you can add usb-creator by following [[COLOR=Blue]these instructions[/COLOR]](http://ubuntuliving.blogspot.com/2008/11/usb-creator-for-hardy.html)... however, persistence still won't work with the default 8.04 initrd.
[*]As long as you can copy and paste, it might be easier to just ignore this program and follow these manual instructions...  (NOTE: Everything before the fdisk command must be run before remastersys dist to work properly)
[/list]

---- BEGIN PREPARATION ----

[i]sudo -s
[color=red]<EDITOR>[/color] /usr/share/initramfs-tools/scripts/casper[/i] (for 8.04 and earlier ONLY)
+ REMOVE this section: ",mode=755"
*[color=red]<EDITOR>[/color] /usr/share/initramfs-tools/init* (for 8.04 and earlier ONLY)
+ ADD the lines preceded by a + between the lines preceded by a *:
> *	break)
*	break=premount
*	;;
*
+	persistent)
+	PERSISTENT=yes
+	root_persistence=casper-rw
+	home_persistence=home-rw
+	;;
+
*	esac
[list][*]For all versions of Ubuntu, if you'd like to take away the prompt at shutdown to remove the CD from the tray and press ENTER, consider this step [...'cause I'm not positive it's the **right** solution]:[/list]
*chmod -x /etc/rc[06].d/*casper*
[list][*]Now re-run remastersys to implement these new initramfs changes:[/list]
*remastersys clean; remastersys dist*

---- END PREPARATION ----

*fdisk /dev/sd[color=red]<X>[/color]* (replacing [color=red]<X>[/color] with what you believe, 110% sure, is your flash drive)
[list][*]Now, add 2 to 4 partitions depending on the size of your distro, whether you want a separate partition for your home directory, and whether you want a FAT16/32 partition for easy access on Windows machines.  Make sure the first partition is bootable.  Now format and label your partitions:[/list]
[i]mkfs.ext2 -L [color=red]<distroName>[/color] /dev/sd[color=red]<X>[/color]1
mkfs.ext2 -L casper-rw /dev/sd[color=red]<X>[/color]2
mkfs.ext2 -L home-rw /dev/sd[color=red]<X>[/color]3
mkfs.vfat -F 16 -n files /dev/sd[color=red]<X>[/color]4[/i]
[list][*]Now pull out the drive & plug it back in.[/list]
[i]cd /media/cdrom/
cp -R boot boot.catalog casper/ .disk/ md5sum.txt preseed/ README.diskdefines /media/[color=red]<distroName>[/color]/
cd /boot/grub/
cp ./*stage* /media/[color=red]<distroName>[/color]/boot/grub/
[color=red]<EDITOR>[/color] /media/[color=red]<distroName>[/color]/boot/grub/menu.lst[/i]
+ ADD a boot menu along these lines...
> 
default 0
timeout 7

#color cyan/blue white/blue
#splashimage=/boot/splash.xpm.gz

title		Start Ubuntu in Graphical Mode
kernel		/casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper root=/dev/ram rw persistent
initrd		/casper/initrd.gz

#title           Install Ubuntu
#kernel          /casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper root=/dev/ram #only-ubiquity
#initrd		/casper/initrd.gz

title		Start Ubuntu in Demo Mode
kernel		/casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper root=/dev/ram
initrd		/casper/initrd.gz

title		Start Ubuntu in Safe Graphical Mode
kernel		/casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper root=/dev/ram xforcevesa rw persistent
initrd		/casper/initrd.gz

#title           Start Ubuntu in Text Only Mode
#kernel          /casper/vmlinuz file=/cdrom/preseed/custom.seed boot=casper root=/dev/ram #textonly rw persistent
#initrd		/casper/initrd.gz

#title		Check the CD/DVD for defects
#kernel		/casper/vmlinuz boot=casper integrity-check
#initrd		/casper/initrd.gz

title		Memory Test
kernel		/boot/memtest

title		Boot the First Hard Disk
root		(hd1)
chainloader +1
[list][*]Install grub to the MBR of the flash drive:[/list]
*grub*
$ grub > *geometry (hd* [color=red]**<Press TAB key now, making sure to realize which one is your USB>**[/color]
$ grub > *root (hd[color=red]<1>[/color],0)*
$ grub > *setup (hd[color=red]<1>[/color],0)*
$ grub > *quit*

**ADD WUBI TO YOUR DIST**
[list][*]For right now, there's a decent bit of editing to /usr/bin/remastersys and /etc/remastersys.conf.
[*]Just read the [[COLOR=Blue]Remastersys + Wubi Guide[/COLOR]](http://ubuntuforums.org/showthread.php?t=1062504), which I'm thinking could be made simpler by just offering a copy of the edited remastersys script.
[/list]

---

### Post by grndslm on 2009-02-19
Made a couple changes for clarification.

---

### Post by blazemore on 2009-02-19
USB persistance can be achieved with the USB Creator tool in Intrepid. You could make your Debian or Hardy based distro, then use an Intrepid installation to make a persistant bootable USB :)

---

### Post by grndslm on 2009-02-20
> **blazemore said:**
> USB persistance can be achieved with the USB Creator tool in Intrepid. You could make your Debian or Hardy based distro, then use an Intrepid installation to make a persistant bootable USB :)Say Wha?!?

I've had a huge Xorg problem by merely upgrading the default Ubuntu packages from Intrepid & Jaunty on a couple Intel video laptops I have... so I'd like to stick with Hardy or maybe try out Debian whenever I've got a lotta free time.

Soo... how can I use the Intrepid installation to make a Hardy based distro persistent??  I see things like usb-creator and Unetbootin.  Is the tool in Intrepid different from usb-creator?  Does the Intrepid tool make USB persistence from any LiveCD, such as one I create with remastersys??

---

### Post by joborohe on 2009-02-22
Hey Guys

when I follow CapInk's guide on remastersys' website [http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html)

everything work except the home user (after install) has no folder in his directory and if I create one, it goes directly on the desktop. Does anyone have a fix for this?

thanks

---

### Post by blazemore on 2009-02-23
What you can do is this:

1. Make your remastersys distro. It's really easy to do this, you can use the small "tutorial" on the website.

2. Copy your iso onto a USB flash drive or something

3. Boot from the Intrepid LiveCD, move your iso file from the USB to the Desktop, go to System->Administration->Make USB startup disk (or something)

4. Select the iso file, and select the USB stick you want to install to

5. Select how much of the USB stick you'd like to dedicate to persistance. If the USB stick is going to be used exclusively as a liveUSB, you can safely set this to maximum.

---

### Post by darthchaosofrspw on 2009-02-23
I've been messing with Remastersys since Feb. when I created my first remaster of gOS Rocket E. Lately I've been using Remastersys with Xubuntu Hardy to create my own customized XXCE distro. Adding a bunch of web apps and changing all the default graphics and stuff to make it XXCE and not just an Xubuntu ripoff. The last one I did was after I installed LXDE and uninstalled Xfce4. (I also had to remove network-manager and install Wicd.)

---

### Post by grndslm on 2009-02-23
> **blazemore said:**
> 5. Select how much of the USB stick you'd like to dedicate to persistance. If the USB stick is going to be used exclusively as a liveUSB, you can safely set this to maximum.Thanks for the instructions.  I realized that the application in Intrepid is usb-creator, which can be added to Hardy... so I shouldn't need the Intrepid LiveCD.

I did need an explanation of what the slider was for allocating how much persistence space you wanted.  Seems like what isn't used is available for traditional flash drive usage.

---

### Post by grndslm on 2009-02-23
> **joborohe said:**
> Hey Guys

when I follow CapInk's guide on remastersys' website [http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html)

everything work except the home user (after install) has no folder in his directory and if I create one, it goes directly on the desktop. Does anyone have a fix for this?

thanks
You might be better off asking at the remastersys forum, linked to at the top of this guide.  Just curious, tho... what's wrong with just running remastersys backup or remastersys dist... or simply altering the /usr/bin/remastersys script if it isn't exactly what you want??

---

### Post by grndslm on 2009-02-23
UPDATED...

- Fixed /etc/remastersys.conf path.
- Added STATIC DNS (OpenDNS) section
- Added USB PERSISTENCE section.
- Found one more thing for me to look into -- restricted firmware.

I've always bought Intel-based laptops because I knew they had open source drivers.  Yesterday, I ran across a lappy with Broadcom wireless (yucky!).  The firmware and "firmware cutter" were obviously not on the LiveCD, so I couldn't get online.  I'm not around the computer at the moment, but I'm wondering if anybody else has remastered a LiveCD with the firmware already in place at /lib/firmware/ ??  Would Jockey still be needed to enable the driver? ... or would it then be capable of auto-detection on boot from the CD/DVD?

---

### Post by grndslm on 2009-02-23
Supposedly it will automatically be loaded at boot... so that's great news.  Can't wait to test it out tomorrow.

Do you guys know of any other such restricted firmware/drivers, particularly in the networking department (I'm certainly familiar with both NVidia & ATI)??

---

### Post by grndslm on 2009-02-26
UPDATED once more... this is easier than I thought.

---

### Post by JECHO on 2009-02-26
> **joborohe said:**
> Hey Guys

when I follow CapInk's guide on remastersys' website [http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html)

everything work except the home user (after install) has no folder in his directory and if I create one, it goes directly on the desktop. Does anyone have a fix for this?

thanks

i have had that same problem using eeebuntu so im sure the fix is the same... go here: [http://forum.eeebuntu.org/viewtopic.php?f=26&t=783](http://forum.eeebuntu.org/viewtopic.php?f=26&t=783)

and follow the "How to do it yourself" post. :)

---

### Post by grndslm on 2009-03-05
Soo... anybody else find this useful?

Or are there more general tips like these that you feel most people would benefit from?

---

### Post by phpadik on 2009-03-07
Thank you very much for this very informative guide. Our organization is planning to remaster Ubuntu. We are targetting fellow students.

We are planning to make 2 remasters, one for Computer Science/Electrical Engineering/Electronics and Communications Engineering/Computer Engineering students and another one for the other students.

The difference will be the first remaster will have preinstalled IDEs and compilers. Both of them will have the usual apps needed by students.

---

### Post by tsedrey on 2009-03-07
This is a great guide, thank you. 

I have been desperately trying for the last few days to get remastersys to do exactly what I want.

My friends are semi-against linux and they told me that if I could recreate my desktop into a liveCD, they'd try it. So, I installed a fresh copy on a new partition and installed the programs, made some visual tweaks, etc. I've tried both dist and backup options and I am still having trouble with a few things, maybe they aren't possible, maybe they are...I could use some help please. I am also using 8.10, which may be the cause of some of the issues.

-Emerald theme does not work on the liveCD (not that surprising), but it doesn't work after install either.
-I have added conky to sessions, and it works fine for me, but on the liveCD and after the install it doesn't work. 
-I disabled the splash screen, but it still comes up for the liveCD and after install

Basically (and I don't know if this is possible), I want to take an exact snapshot of the partition I have, reproduce it on a liveCD so that my friends can play around with it and then install it if they want with their user name/information. 

Can this be done?
Thanks,
David

---

### Post by grndslm on 2009-03-12
> **phpadik said:**
> We are planning to make 2 remasters, one for Computer Science/Electrical Engineering/Electronics and Communications Engineering/Computer Engineering students and another one for the other students.

The difference will be the first remaster will have preinstalled IDEs and compilers. Both of them will have the usual apps needed by students.
I wish I woulda had an EE distro when I was in college, so I wouldn't have had to install XP.

BTW, Geany was a nice, lightweight semi-IDE.  I liked it at least.

---

### Post by grndslm on 2009-03-12
> **tsedrey said:**
> This is a great guide, thank you. 

I have been desperately trying for the last few days to get remastersys to do exactly what I want.

...

Basically (and I don't know if this is possible), I want to take an exact snapshot of the partition I have, reproduce it on a liveCD so that my friends can play around with it and then install it if they want with their user name/information. 

Can this be done?
Thanks,
DavidRemastersys is definitely the tool for the job.  I've definitely gotten more working with Remastersys than I ever thought I'd be able to do at this point in time.  The key is to understand how all other individual apps work, where their configs go, what's in those configs, etc.  Copy the right ones to /etc/skel/ and you're all set.

A good way to test the /etc/skel/ folder out is to simply create a new user with the adduser command and then login and you should see your dock, etc.  If something doesn't work, the configs aren't setup.

As for the splash screen, I'm assuming you're referring to Usplash, in which case you pretty much must use startupmanager.  It should automatically invoke the "update-initramfs -u" command as you close the app.  If you really want to get rid of usplash, you could certainly "sudo aptitude purge usplash" as well.

May the Force be with you all!

---

### Post by grndslm on 2009-03-12
Also... don't forget that the LiveCD must use a basic window manager, like metacity.  3D Effects, like Compiz, aren't supported because Ubuntu's casper scripts automatically disable the fglrx & nvidia drivers.

---

### Post by munishvit on 2009-03-13
Hey guys
Using 'create a USB startup disk', I installed my distro ISO image to USB. But when trying to use this live USB on my friends system, I get the following message:
> SYSLINUX 3.53 Debian-2007-12-11 EBIOS Copyright (C) 1994-2007 H. Peter Anvin
Could not find kernel image: linux
boot:

Here the detail what I did:
On a fresh installation of Ubuntu 8.04, I ran update-manager, then installed following packages:
Sun java 6 jre (bin gets automatically installed)
Sun java 6 plugin
CHM Viewer
StarDict
VLC
Amarok
Qalculate
ISO Master
Ex Falso
GStreamer ffmpeg video plugin
GStreamer extra plugins
NTFS configuration tool
Advanced Desktop Effects Settings (ccsm)
Gmount-iso
tcsh
build-essential
flashplugin-nonfree
nrg2iso
remastersys

and then uninstalled the following:
Audio CD Extractor
Calculator
F-Spot Photo Manager
XSane Image Scanner

then,
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo -s
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ .openoffice.org2/ /etc/skel/
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ .openoffice.org2/ /root/
cd /etc/skel
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ .openoffice.org2/ 
cd /root
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ .openoffice.org2/

from gui, using 'remastersys backup' tool I picked 'clean' and then 'dist' to get the image. Then finally installed 'usb-creator' and to get live-USB.

but its not working, perhaps because of apt-get autoremove.
Could anyone tell, is there problem in image itself or I need to give some command at boot?
thanks

---

### Post by munishvit on 2009-03-13
> **munishvit said:**
> Hey guys
Using 'create a USB startup disk', I installed my distro ISO image to USB. But when trying to use this live USB on my friends system, I get the following message:
Could anyone tell, is there problem in image itself or I need to give some command at boot?
thanks

Can anybody help me? Please...

---

### Post by grndslm on 2009-03-13
Sorry, dude!!  I just got my 32GB flash drive in the mail today... so I haven't even gotten to that part yet.

I couldn't imagine apt-get autoremove being your problem, and I also don't see why you'd use it after you use apt-get clean.  I think clean should be all you need.

I'm guessing your issue prolly has something to do with the boot loader.  If you really want to figure it out, I'd highly recommend stopping by the [Remastersys forum](http://loscompanion.com/forums/index.php#6) and asking Fragadelic, the Remastersys developer.

---

### Post by munishvit on 2009-03-14
> **grndslm said:**
> Sorry, dude!!  I just got my 32GB flash drive in the mail today... so I haven't even gotten to that part yet.

I couldn't imagine apt-get autoremove being your problem, and I also don't see why you'd use it after you use apt-get clean.  I think clean should be all you need.

I'm guessing your issue prolly has something to do with the boot loader.  If you really want to figure it out, I'd highly recommend stopping by the [Remastersys forum](http://loscompanion.com/forums/index.php#6) and asking Fragadelic, the Remastersys developer.

I would have tried burning the image on CD if it would have been less then 700MB. Well, as I gave all the details about what I did; what do you think, could there be any problem in image itself?
I will try to get it burned on DVD and then try to boot. 
Anyway, thanks for your recommendation.

---

### Post by grndslm on 2009-03-14
You could also try adding a vanilla Ubuntu ISO to the USB for starters... and then go one by one.  It's prolly got something to do with initrd??

---

### Post by munishvit on 2009-03-15
> **grndslm said:**
> You could also try adding a vanilla Ubuntu ISO to the USB for starters... and then go one by one.  It's prolly got something to do with initrd??

I'll try...thanks

Edit:
Customized Live Image was perfectly fine, just had problem with Live-USB...that too is solved using **unetbootin**.
[http://loscompanion.com/forums/index.php?topic=6690.0](http://loscompanion.com/forums/index.php?topic=6690.0)

---

### Post by grndslm on 2009-03-21
I'm about to add some more stuff later today...

Get ready!!

---

### Post by ranch hand on 2009-03-21
This is a great thread and how to.  Thanks a bunch.

I have already made on remaster of 8.10 and am going to do another now that I know what I do not and do like from the first (ain't RW great).  This thread will make my life a lot easier.

---

### Post by grndslm on 2009-03-22
RW *is* great.  I can't get all of my config files to save with USB persistence, tho.  Some things seem to save, while others don't.

Anyway, I updated the USB Persistence section as much as I could tonight (getting tired) and a couple Remastersys links, like the new Remastersys forum home.

Tomorrow, I should be able to add another section on what files are good candidates to remove if you're running outta space... and I'll be trying to see if I can clean the formatting up a bit, but it gets more and more difficult as I add new sections.

---

### Post by grndslm on 2009-03-22
UPDATED...

Added the section on suggested packages to remove and changed formatting for easier readability.

---

### Post by grndslm on 2009-03-23
UPDATED a few minor things... and mostly made the guide more portable between different forums.

---

### Post by grndslm on 2009-04-04
Now the guide lists the new remastersys repositories.

Hopefully within the next week I'll find some time to finish the USB persistence section... like how to customize global Firefox settings/extensions, how to properly disable the prompt at shutdown/reboot to eject the CD and hit enter, pros & cons of fat16, fat32, ext2, & ext3, if compressing a distro customized for usb persistence is actually beneficial, etc.  Stay tuned!

---

### Post by Hybodus on 2009-04-04
I am an admin on a Uk Chat server which does a nightly internet radio show for our chatters. We have quite a few requests to be DJ's but due to microsoft software this is not always possible, software not compatible, driver issues, I'm sure you can understand.
Since I have an interest in linux I was looking for an alternative, which I have found, but would appreciate a little help/pointers to fullfill
I can create a live cd no problem using the following:

Using ubuntu mini I have built a system but I am stuck on automounting local drives. I need automounting due to most of the users been windows based and having them delve into the terminal will result in disaster.

From Ubuntu mini, installed xorg, slim, openbox, fbpanel, thunar, thunar-volman, xfce4-mixer, feh, idjc and its dependents. I can install Remastersys and have a working live cd but for the automounting.

I have a basic system that works and looks reasonable for a newbie but the automounting is stopping further progress. I need all local drives to be automounted so that a user only needs it to be clicked on to activate.
Any pointers would be appreciated, thank you

Hybodus

I changed thunar and thunar-volman for nautilus and gnome-volume-manager and its working as I want now :)

---

### Post by grndslm on 2009-04-07
I have not heard of Ubuntu Mini.  Is it the minimal Ubuntu install... or Ubuntu Mini Remix?

Either way, perhaps you'd wanna tell Fragadelic about it here: [http://loscompanion.com/forums/index.php?topic=3380.0](http://loscompanion.com/forums/index.php?topic=3380.0)

---

### Post by slickvguy on 2009-04-14
> **grndslm said:**
> ... how to properly disable the prompt at shutdown/reboot to eject the CD and hit enter

/etc/rc0.d/S89casper --> /etc/init.d/casper

Not sure if it's "proper", but I commented a few lines and it seems to work ok.

```

#    eject -p -m /cdrom >/dev/null 2>&1

    [ "$prompt" ] || return 0

    stty sane < /dev/console

    # XXX - i18n
#    echo "Please remove the disc and close the tray (if any) then press ENTER: " > /dev/console
#    if [ -x /sbin/usplash_write ]; then
#        /sbin/usplash_write "TIMEOUT 86400"
#        /sbin/usplash_write "TEXT-URGENT Please remove the disc, close the tray (if any)"
#        /sbin/usplash_write "TEXT-URGENT and press ENTER to continue"
#    fi

#    read x < /dev/console

```

---

### Post by chang5562 on 2009-04-16
grndslm:
    I a newbie of ubuntu.  I tried to learn more of LiveCD.  I basically created a LiveCD with remastersys by Backup mode, since I modified my ubuntu 8.10 (kernel 2.6.27) to my need.  I want to create a LiveCD so that I can use it to install on my Desktop.  I tested a little by creating the bootable iso on a USB stick with usb-creator. It booted OK itself.  How can I create a GRUB that have the "Install" menu.  I noticed that the syslinux.cfg file has the term- Install, but it did seem work even I changed the TIMEOUT to 30 secs. It still run the Live mode from the Stick.

    I referenced to your article by creating a /boot/grub and follow the bottom half of your paper, a menu.lst and all stage files into there.  But I still could not do Install. When I run, I got a messaage -"Can't find file" for either kernel /casper/vmlinuz..  initrd /casper/initrd.gz  or without /casper.

   The remastersys create both vmlinuz and initrd under the /casper.   without the adding grub, the USB can boot  my customized Ubuntu.  but I want to install.  Can U help?  I may be missing sth.

---

### Post by grndslm on 2009-04-17
> **billyg said:**
> I am newbie in ubuntu world. And this guide is very usefull for me. really helpful guideThanks a bunch, man!  That's just the kinda inspiration I need to do some more tweaking.

> **slickvguy said:**
> /etc/rc0.d/S89casper --> /etc/init.d/casper

Not sure if it's "proper", but I commented a few lines and it seems to work ok.

```

#    eject -p -m /cdrom >/dev/null 2>&1

    [ "$prompt" ] || return 0

    stty sane < /dev/console

    # XXX - i18n
#    echo "Please remove the disc and close the tray (if any) then press ENTER: " > /dev/console
#    if [ -x /sbin/usplash_write ]; then
#        /sbin/usplash_write "TIMEOUT 86400"
#        /sbin/usplash_write "TEXT-URGENT Please remove the disc, close the tray (if any)"
#        /sbin/usplash_write "TEXT-URGENT and press ENTER to continue"
#    fi

#    read x < /dev/console

```Thanks, man!  That would probly be the proper way, alright.  AWESOME!  I love it when I don't have to do all the work.  I will add it to the guide as soon as I confirm it works the way one would expect it to.

> **chang5562 said:**
> grndslm:
    I a newbie of ubuntu.  I tried to learn more of LiveCD.  I basically created a LiveCD with remastersys by Backup mode, since I modified my ubuntu 8.10 (kernel 2.6.27) to my need.  I want to create a LiveCD so that I can use it to install on my Desktop.  I tested a little by creating the bootable iso on a USB stick with usb-creator. It booted OK itself.  How can I create a GRUB that have the "Install" menu.  I noticed that the syslinux.cfg file has the term- Install, but it did seem work even I changed the TIMEOUT to 30 secs. It still run the Live mode from the Stick.

    I referenced to your article by creating a /boot/grub and follow the bottom half of your paper, a menu.lst and all stage files into there.  But I still could not do Install. When I run, I got a messaage -"Can't find file" for either kernel /casper/vmlinuz..  initrd /casper/initrd.gz  or without /casper.

   The remastersys create both vmlinuz and initrd under the /casper.   without the adding grub, the USB can boot  my customized Ubuntu.  but I want to install.  Can U help?  I may be missing sth.You can use either syslinux or grub.  Once you have the proper syntax in the boot menu  (in grub, that means having "root=/dev/ram rw persistent" in the kernel line for your persistent session), you need to follow the steps to install grub to your hard drive (which must have a partition with a bootable flag).  Syslinux has its own syntax for the boot menu and its own command to install itself to the hard drive.

If you still can't manage to figure it out after that, I would stop by the [Remastersys Forum](http://www.geekconnection.org/remastersys/forums/index.php) and ask the developer of Remastersys, even tho this problem is outside the scope of the Remastersys script.  Somebody there can definitely help you.

Have a good day!

---

### Post by chang5562 on 2009-04-17
grndslm:
    Thanks.  This time I carefully repeated (by typing) the step of creating the menu.lst and the grub steps, it works!!.:D

    But this is not what I really want.  Maybe I did not make clear of my intention.  

    Since I modified my Ubuntu and created an image of it and put on LiveUSB.  I hope I can use this to install onto the HD of my Desktop.  Clearly this LiveUSB only runs in the memory (as /dev/ram).  How can I install the image into the HD, like regular Ubuntu, which has to go through all those installation steps (ie. language, keyboard, partition, assign user...)

    Should Remastersys include sth else?

    Thanks.

---

### Post by dot2kode on 2009-04-17
@grndslm

Very nice guide man..Thanks for taking the time to put this all together...much appreciated... :D

I started using this for full system backup's on dvdrw's with rsync for nightly /home...works great...plus you can have a copy of your system on a dvd/usb to take with with you...very nice application..Keep up the good work bro... =D>

---

### Post by grndslm on 2009-04-20
> **chang5562 said:**
> grndslm:
    Since I modified my Ubuntu and created an image of it and put on LiveUSB.  I hope I can use this to install onto the HD of my Desktop.  Clearly this LiveUSB only runs in the memory (as /dev/ram).  How can I install the image into the HD, like regular Ubuntu, which has to go through all those installation steps (ie. language, keyboard, partition, assign user...)

    Should Remastersys include sth else?
If the live cd works... you should be able to run ubiquity.  I think it's a dependency of remastersys.  Pretty sure there should be an icon on your desktop??

---

### Post by chang5562 on 2009-04-20
grndslm:
    thanks again for ur help.  

    How stupid I was?  I removed the ubuquity.desktop, the install icon disappeared.  However, I am wondering why the "Install" from the grub menu, either set-up from the original syslinux or by the GRUB creation process, did not work? 

    anyway, I am going to run - install, to make sure my modification is still there.

---

### Post by grndslm on 2009-04-20
The boot menu options are a little funny right now, for sure.  I think the text install only works for Debian systems right now or something.  Fragadelic's supposed to release a version of remastersys that enables text installs for Ubuntu, but we can only wait for now.

Ubiquity's the way to go for now.

---

### Post by grndslm on 2009-05-01
Anybody use 9.04 with Remastersys??

---

### Post by grndslm on 2009-05-01
Also, can I add tags to a thread that was already created, like this one??  Just wanted to add a few tags like... remastersys, customization, customize, custom, distro, distribution

Is that possible?

---

### Post by joborohe on 2009-05-13
anyone experience cups problems on your remaster copy?

everytime i do it i have to completely remove cups, manually delete the folder /etc/cups and then reinstall to work.

just wondering if you guys knew how to avoid that.

---

### Post by Fragadelic on 2009-05-19
> **joborohe said:**
> anyone experience cups problems on your remaster copy?

everytime i do it i have to completely remove cups, manually delete the folder /etc/cups and then reinstall to work.

just wondering if you guys knew how to avoid that.

You're using an old version of remastersys.  I believe I fixed it in 2.0.12.  The problem is that the ssl keys are only valid for the actual initial install and the livecd but after it is installed they become invalid.  ssl keys are removed in the 2.0.12 version.

---

### Post by thepianist on 2009-05-24
Hi first of all , thanks for your work !

I read the thread but I couldn't understand how to edit kernel options. 
My problem is that I need to make a dist which contains special option to recognize a touchpad , I need this option in live and in install versions

When I inspect /home/remasterys/remastersys/dummysysv , I didn't finf /boot directory :-(

If you can help me ... Thanks !!

---

### Post by grndslm on 2009-07-19
> **thepianist said:**
> Hi first of all , thanks for your work !

If you can help me ... Thanks !!No problem, man.  

Unfortunately, I can't help you.

I've actually have been away from the keyboard for FAAAAARR too long.  Had a problem with my mobo that was "oxidized", waiting for warranty, didn't go thru, waited to receive mobo to try the "baking method" as seen on Hardforum and OCforums, didn't work, researching a mobo, getting an open box item from Newegg, it didn't work, so i had to wait for them to approve the RMA, blah blah... just ended up getting a cheap board that wouldn't allow me to use all 4 of my memory cards.  I'm kinda pissed.

Anyway, It's gonna take me a lotta time to get back into the groove of things, as I need to merge files between so many different computers and just get my shiz organized again.  Once I'm reorganized, I'll be back in action.  It might take awhile, tho, because I've got a few other large tasks on the plate right now.

Any new tips from more experienced users or experiences from new users are most welcomed!!

---

### Post by grndslm on 2009-08-27
:KS:guitar::KS - shameless bump - :KS:guitar::KS

---

### Post by grndslm on 2009-10-04
:KS:guitar::KS - ONE MO' TIME - :KS:guitar::KS

I'll be updating this whenever Karmic Koala is officially released on October 29th.  WOO HOO! :popcorn:  I'm about to test out the Beta right now to see how things have improved in Ubuntu Land.  I have a laptop that's still using Gutsy, but it's not getting anymore updates... and even Hardy is starting to get a bit long in the tooth.  I skipped Jaunty, so hopefully the Karmic Beta will lift up my spirits again.  I think it will.

I'll get a Karmic refresh on all my computers and then I'm gonna pick up a smartphone with WebOS or Android to keep on geekin' on.  :shock:

---

### Post by grndslm on 2009-11-07
Anybody get any use outta this?

I've been too slammed to think about Remastersys, but oh how I wish I had the time or a spare computer to mess with this stuff again.

---

### Post by kartal on 2009-11-16
Hi

I think I successfully created my .iso. Can I get rid of "ISOTMP and "dummysys"? Would they need to be around the iso at all?

thanks

---

### Post by grndslm on 2009-11-21
As long as you can see the ISO, you should be good to go.  You can add it to a virtual machine or you can go ahead and burn it to test out on another computer.  You might wanna keep the ISOTMP, etc. if you later discover that there's only one file you'd like to edit before actually burning the ISO.  It provides you a way to remake the ISO quicker if you erred.

My DVD burner just broke when I was labeling about 200 CDs I have that weren't labeled to begin with!!  I'll be getting back into this within the next month or two for sure.

Fragadelic has released version 2.0.13 just for Ubuntu Karmic, so you guys might wanna get that if that's what you're gonna use as your foundation.  I'll update the guide to reflect this new version as soon as I get my DVD drive.

](*,)

---

### Post by grndslm on 2009-11-25
BAM!!

Karmic version added to [OP](http://ubuntuforums.org/showthread.php?t=1073838).

Anybody else having any success?  Or even failures?

---

### Post by grndslm on 2009-12-29
Well...

I've got a new DVD burner and an SSD drive for my OS.

:guitar:

Hopefully I can do some work now.

:):):)

---

### Post by grndslm on 2010-02-11
Hmm... no time for me.

How about you?  :D

---

### Post by grndslm on 2010-03-18
You guys don't mean to tell me that NONE of you can create your own customized Linux distribution??

I can... :P

---

### Post by grndslm on 2010-04-27
I feel like an idiot after looking at these past few posts of mine.

I've been using VirtualBox to install other OSes in that downtime from my busted up DVD Burner.... but I never thought about installing my own custom distro's ISO inside VirtualBox.  DOH!

I'm just plain slow sometimes.

---

### Post by grndslm on 2010-04-29
Holy Moley!

Ubuntu 10.04 LTS is out now!!!

Customize a new install to your liking,
Save the state with Remastersys,
Then hand out your custom distribution to all your friends.

How much easier can computing get?  :P

---

### Post by Purplecatty on 2010-05-13
I would like to create remastered CD of Karmic Koala 9.04 for my Dell Mini 10 (1010) netbook which have issue with Intel GMA 500 chipset which was fixed with "Poulsbo" driver.  The biggest problem is that if you update Ubuntu through Update Manager, it'll break Poulsbo driver because it NOT work with Kernel above 2.6.31-19.  I am currently using Kernel 2.6.31-14 and turned off the Update Manager.  Kernel update don't break Broadcom STA Wireless card driver.

Basically, I wanted to make copy and distribute it to friends who have similar type of Netbook like mine.  (Deaf people who use Hand On Video Relay Service "HOVRS" bought Purple 3 renamed Dell Mini 10 are commonplace for Video Relay use).  So that it'll be less headache not to download and compile "Poulsbo" driver and Broadcom STA Wireless card driver (BCM STA driver obtained through Synaptic Package Manager and must have either USB wireless adapter or Ethernet cable plugged in to download it in Synaptic Package Manager). With remastered Ubuntu 9.10 cd, I wanted to have both restricted drivers included so it won't be much hassle to download and install it.  That include if running on LiveCD or boot from USB thumbdrive.

Let me know how it can be done.  

Thanks
Catty

---

### Post by grndslm on 2010-06-09
Purplecatty...

I'm really not sure.  I'd probly take the easy way out and flag the package that your Poulsbo driver comes in ):P ... so that it wouldn't ever get upgraded.  :)

But that's just me.

You could alternatively file a bug report so that Ubuntu understands there's an issue that breaks he Poulsbo driver when you upgrade.

And, you could even use Debian.  In all honesty, I think that Debian might make a better base-distro for those of us who want to make a custom distro... but I have yet to use Debian myself, yet.  Ubuntu's hardware detection and a few other things are hard to beat... so it can go either way, really.

As they say, "Ask 4 Linux users the same question and you'll get 9 different answers."  :lolflag:

---

### Post by ranch hand on 2010-06-16
I need to do this on 10.04 and would just like to make sure that everything is copasetic.

There is a problem with the links in the first post.  Remastersys Home=404.  Link for the newest version=403.

How in flinderation do I get that version?

EDIT
I did get the repo link to work.  Have no idea what the problem was.  Maybe just a bad connection due to the thunder storm we were having then.

I did a trial burn of an ISO of a 10.10 install of mine and it burned.  Will try installing tomorrow and I think that will go well.  If so, it was much easier than it seemed to be back in Hardy the last time I did this.

We will see.  And report.

---

### Post by ranch hand on 2010-06-17
I am later than I wanted but life happened.

Worked great,  nice easy install.  I need to fool with it a bit as I want a different image behind the menu and my desktop settings were not preserved on the install.

Over all I am very impressed with the improvements.  Very nice.

---

### Post by ranch hand on 2010-06-28
Well, I seem to be having a little problem.  I believe this is one of those between the chair and the key board based problems.

I need to modify the desktop configuration and some other settings and have them persist in the Live CD.

I install 10.04 and update it.  I log in through recovery and log in with the text login there and use "sudo startx" to be a root user.  This should give me the persistence I need should it not?  It does not seem to as when I log in as a regular user every thing is at default settings.

Which will come up on the DVD?

---

### Post by sandwormblues on 2010-11-18
greetings y'all,

i'm trying to copy my 10.04 minimal install (mini.iso) to a live cd.  i don't want to install x on the livecd! Is it possible to use remastersys to create a livecd without x11?

---

### Post by amjjawad on 2011-01-10
Sorry if that will sound rude but what so special about this thread if it's totally "copy-paste" from here: [http://www.geekconnection.org/remastersys/info.html](http://www.geekconnection.org/remastersys/info.html)

I don't find it useful, sorry. I was looking for something easier to read and follow.
Even this one is not helpful if you ask me: [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

[http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396)

---

### Post by Repgahroll on 2011-02-01
hey guys... does someone know how to disable the grub menu? I've tried deleting all the other entries and setting timeout to 0, but it doesn't work.

I just want it to boot directly without displaying the menu.

Thank you.

---

### Post by grndslm on 2011-02-12
> **amjjawad said:**
> Sorry if that will sound rude but what so special about this thread if it's totally "copy-paste" from here: [URL]

I don't find it useful, sorry. I was looking for something easier to read and follow.
Even this one is not helpful if you ask me: [url]

[URL]This guide was made here first.  Actually at the old remastersys forum... One of the 2.

The Remastersys dev put that thread in the new forum and locked it for $50 "support".

He does have that one page available, but I think he trims a little and does not give due credits (hard to tell on a phone right now, tho).  He used to say that "he wished he could have created something like that but never had the time".

It tooks me hours/days to assemble this information and he locked it up on the forum.  It's still available here and I'm glad Tony updated his version.  That's what FOSS is all about.  Just hope he gives due credit.  And that one page you linked at geekconnection is not "widely" linked internally on that site the last time I checked.

Crunchbang distro creator copied my guide from here and gives credit.

Check out my Meta-Doctor Guide for webOS, my Crash Course for Motored Bike N00Bs... I'm a teacher. :)

---

### Post by grndslm on 2011-02-12
Oh and if you wanna learn about the law, check out

[Freemen.Freeforums.org]("http://freemen.freeforums.org")

:)

---

### Post by grndslm on 2011-04-12
Bippity Boppity

BUMP!!

Ubuntu is starting to make some drastic changes to the UI.

I hope those changes are ticking enough users off that they start THEIR OWN distro!!  ;)

---

### Post by ranch hand on 2011-04-14
> **grndslm said:**
> Bippity Boppity

BUMP!!

Ubuntu is starting to make some drastic changes to the UI.

I hope those changes are ticking enough users off that they start THEIR OWN distro!!  ;)
I think this may be the case.

I have not tried remastersys since the 10.04 release.  That did not go well at all.  Backup worked fine.  Building a distro CD did not work at all.

Worked fine before that, at least 8.04 through 9.10 (as long as you removed grub2).

That is another question.  Is Remastersys now grub2 friendly?

---

### Post by Jose Catre-Vandis on 2011-04-22
Hi grndslm

from your original post, can you advise on this part:
```
If you want to alter the installed Grub, update-grub must be altered, then the package must be flagged to never upgrade.
```
This is my only sticking point on a 10.04 setup. I have read through the update-grub script and the grub-mkconfig script it points to, but can't see what I need to change to get my modified grub2 to come up on an install from a remastersys iso. I really only need to get the background and text colours to work (this is after installation), so pointers just for that would be great. 

And I guess I flag grub to not be upgraded in synaptic before I make the iso/cdfs ? 

Any help appreciated

[EDIT] 
[COLOR="Sienna"][B]Not to worry, sorted it out myself - nothing to do with editing "update-grub" so the advice on your OP is a bit misleading, more to do with file locations for the grub background and the settings in /etc/grub.d. One does need to update-grub after editing the settings.

Also found another useful snippet along the way: don't use a windows file system for your remastersys backup folder, e.g. ntfs,fat32, only use a linux filesystem, e.g. ext3,ext4, otherwise your sudoers and other special permissions files will get mucked up on the live cd.

I also wanted to use slim for the login manager. This will work, but you need to install gdm for the live cd to work properly, just don't select gdm as your default login manager when offered by gdmsetup

Most tutorials out there for remastersys assume a great deal, if you veer from the path of a straight forward distro you may need to do more hacking that is indicated in order to get your live cd / back up right[/B][/COLOR]

---

### Post by blaguvest on 2011-07-23
I need help

preseedning file set

Adding a new user to bypass the section on
be able to login as root
give root password

custom.seed

```
d-i passwd/root-login boolean true

d-i passwd/make-user boolean false

d-i passwd/root-password password toor
d-i passwd/root-password-again password toor

ubiquity ubiquity/summary note
```I'm sorry, my English is a bit bad

---

