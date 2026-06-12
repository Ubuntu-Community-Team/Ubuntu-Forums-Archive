---
title: "Apt-Get versus Aptitude Kernels Installed and Uninstalled"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-15
About 18 months ago, maybe 24 months, the video card in this 'puter had a bad dvi out. I wanted to run dual monitors. The card went back to the maker. During that time, I set the built-in motherboard video driver up via the BIOS. Something was a mess and from advice, this forum, I re-configged the 'VGA' resolution, so that the GRUB boot time stuff wasn't scrolling off screen. After the repaired video card was re-installed, I couldn't reset the resolution. I posted about this at the IRC for GRUB, but never got a response.

After making that change, I had to use GRUB Recovery to make a new grub.cfg file. That was the beginning of a problem that has only resolved itself partially, today.

I did not know that the old kernels kept getting added to in /boot, I didn't realize that my 16 gig /sda3 was actually getting near full. When the OS crashed and could not boot, the /sda3 had 1.8 gig of free space. (about 14 gig used)

Now this non-booting could have been caused by maybe two or three problems. The /sda3 being too full. Or it could have been a recent install of MythTV/MythBuntu, of which more in a moment. Then there was the problem with using a thumbdrive to store passwords and other sensitive data on. Someone, this forum, helped me mount the drive so that it could run executable files. In the course of the last few days before the complete crash, the thumbdrive, mounted in the filesystem as /LEXAR under /, and would have a hissy-fit at boot time and ask "S"kip, "M"ount or "M"anual mount or some such. Then one day, I forgot that the /LEXAR was mounted in a non-conventional manner, and pulled the device out of it's usb port. That pretty much finished the OS.

What I want to do is find what happened to GRUB that the GRUB "Recovery Menu" won't work. And by won't work, I mean that if I select "Recovery" at boot time, the screen goes to blank. Or black. Now, having said that, the selectable options are there, but you cannot see them. So, if I tab and enter after waiting a while for the filesystem to load fully, the OS will boot and eventually the login screen will come up. But I cannot fsck, update grub, clean, drop to #root, networking etc. Nothing can be seen.

So, back to MythTV/Buntu. After that install, and un-install and re-install and back and forth, I have a 80% working Myth. Myth also was installed just before the big OS crash. I never saw much of a problem. Until I thought that Myth had some corrupted bits and pieces. 

I use Aptitude. Early on I came to believe that Aptitude was a little better than apt-get. It keeps better track of either dependencies, or cached files. It's so long ago, I don't quite remember. So, when I wanted to try get a look at the problem, I 

[COLOR="Red"]sudo aptitude install -f[/COLOR]. The terminal ran and told me I had to download 1 gig of updates and then that would use 3 gig of disk space, once it was installed. An hour later, the terminal returned to the user prompt and I saw no errors or even warnings.

I didn't want those kernels, they were all outdated. And some of the terminal output talked about LIRC. So, I figured that Myth hadn't installed completely and sure enough, during the aptitude run, I got a chance to install the LIRC that comes up in the terminal window and allows selecting a remote control, etc.

This is how I learned that Myth was a mess:

usSetting up mythtv (2:0.26.0+fixes.20130205.a1b9b1f-0ubuntu0mythbuntu1) ...
Setting up mythtv-backend-master (2:0.26.0+fixes.20130205.a1b9b1f-0ubuntu0mythbuntu1) ...
Setting up php-mythtv (2:0.26.0+fixes.20130205.a1b9b1f-0ubuntu0mythbuntu1) ...
Setting up mythweb (2:0.26.0+fixes.20130205.a1b9b1f-0ubuntu0mythbuntu1) ...
Action 'configtest' failed.
The Apache error log may have more information.
Your apache2 configuration is broken, so we're not restarting it for you.
Processing triggers for libc-bin ...ed 

So was I surprised to see that aptitude had found an unrelated problem with the LIRC and fixed it. Yikes, POWERFUL!

Now with much riding on it, I ran the [single line command]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/") to remove all the old kernels, and this is where it's get's interesting, the terminal output, eventually showed:

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.2.0-36-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-37-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-37-generic...
P: Writing config for /boot/vmlinuz-2.6.35-28-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae

AND A MOMENT LATER


-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 295.40
Kernel:  3.2.0-36-generic-pae (i686)
-------------------------------------
 
Status: Before uninstall, this module version was ACTIVE on this kernel.
 
nvidia_current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-36-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
 
depmod........
 
DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-36-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-37-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-37-generic...
P: Writing config for /boot/vmlinuz-2.6.35-28-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.2.0-36-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-37-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-37-generic...
P: Writing config for /boot/vmlinuz-2.6.35-28-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic-pae /boot/vmlinuz-3.2.0-36-generic-pae
mark@Lexington-19:~$

SO, now all that is left of the 3 wasted gigs is:

mark@Lexington-19:~$ dpkg --list | grep linux-image
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic-pae       3.2.0-37.58                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.37.45                                         Generic Linux kernel image
ii  linux-image-generic-pae                3.2.0.37.45                                         Generic Linux kernel image

Lastly, if I chose to use the "e" option during GRUB -boot normally- or -boot recovery- and change the vga=769 (current GRUB state) to vga-761 and then F10 to boot from there, I get the GRUB recovery screen, even though GRUB says, the vga=769 is deprecated on the next screen. Go figure. 

What I would like to do is fix GRUB so that it find's the correct nvidia.ko.

If you want to see the runs that aptitude performed I have them at pastebin. They are not the whole runs of terminal text. It was quite repetitive and I've posted a lot, but have the relevant stuff near the very bottom. You are warned.

[http://pastebin.com/bmAKW3C5](http://pastebin.com/bmAKW3C5)

---

### Post by schragge on 2013-02-15
Try to *sudo dpkg-reconfigure nvidia-current*. The kernel module *nvidia_current.ko* gets built by DKMS each time a new kernel is being installed, DKMS then puts it in the *modules* directory for that kernel. I guess you can force rebuilding the module for the current kernel with *dpkg-reconfigure*.

---

### Post by Mark_in_Hollywood on 2013-02-15
It did not allow for a viewable screen of GRUB Recover options (Resume, Clean, fsck, Repair Packages, terminal, networking). On the other hand, I'm here at the forum responding and the video is working otherwise.

Terminal output:

mark@Lexington-19:~$ sudo dpkg-reconfigure nvidia-current
[sudo] password for mark: 
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic-pae
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match MSI with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match MSI with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-295.40 DKMS files...
Building only for 3.2.0-37-generic-pae
Building for architecture i686
Building initial module for 3.2.0-37-generic-pae
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-37-generic-pae/updates/dkms/

depmod....

DKMS: install completed.

Please note that if I the e to enter edit the Grub Recovery kernel, and change vga=769 to vga=761, I can see the Recovery screen options.

---

### Post by schragge on 2013-02-15
Well, what is in your */etc/default/grub*?
```

grep '^[^#]' /etc/default/grub

```

I guess either GRUB_CMDLINE_LINUX or GRUB_CMDLINE_LINUX_DEFAULT in that file sports "vga=769". Change it there and
```

sudo update-grub

```
then reboot

---

### Post by Mark_in_Hollywood on 2013-02-15
That went well. This 'puter is back to it's original perfection. 

for reference:

mark@Lexington-19:~$ sudo dpkg-reconfigure nvidia-current
[sudo] password for mark: 
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic-pae
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match MSI with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match MSI with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-295.40 DKMS files...
Building only for 3.2.0-37-generic-pae
Building for architecture i686
Building initial module for 3.2.0-37-generic-pae
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-37-generic-pae/updates/dkms/

depmod....

DKMS: install completed.


========================

mark@Lexington-19:~$ grep '^[^#]' /etc/default/grub
[COLOR="Red"]G[/COLOR]RUB_DEFAULT=0
[COLOR="red"]G[/COLOR]RUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR="red"]G[/COLOR]RUB_TIMEOUT=10
[COLOR="red"]G[/COLOR]RUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="red"]G[/COLOR]RUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[COLOR="red"]G[/COLOR]RUB_CMDLINE_LINUX=" **vga=769**"
[COLOR="Red"]G[/COLOR]RUB_GFXMODE=640x480

  GNU nano 2.2.6           File: /etc/default/grub                              

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=761"
GRUB_GFXMODE=640x480
## line: GRUB_CMDLINE_LINUX=" vga=769" changed to 761 by mp 15-2-13
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

mark@Lexington-19:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done


and rechecking the /etc/default/grub

  GNU nano 2.2.6           File: /etc/default/grub                              

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=761"
GRUB_GFXMODE=640x480
## line: GRUB_CMDLINE_LINUX=" vga=769" changed to 761 by mp 15-2-13
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

---

