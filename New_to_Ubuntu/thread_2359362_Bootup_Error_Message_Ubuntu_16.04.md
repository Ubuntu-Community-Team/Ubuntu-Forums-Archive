---
title: "Bootup Error Message Ubuntu 16.04"
date: 2017-04-23
forum: New to Ubuntu
---

### Post by eddiecalvert on 2017-04-23
Hello, I am very new to Ubuntu 16.04 and to the forum. 

I have been using Ubuntu 16.04 since October 2016, and learning more and more each day.

However, I recently received this error message when starting up my machine, a Lenovo Edge 15, "load ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'  " when starting from a cold boot. My system is a dual boot system with Windows 7 Professional installed and I am running Ubuntu 16.04 as my primary system. 

The system then ignores the error message, and after a few seconds of display, the boot up proceeds normally and the login screen is presented. I receive no other errors, other than this, which is a visual nuisance for now. 

Can anyone please help?

---

### Post by RobGoss on 2017-04-23
Hello and welcome to the forum, Please see this post with what looks like the same issue you have, might help with your issue [https://askubuntu.com/questions/290884/blacklist-conf-ignoring-bad-line-boot-prompt](https://askubuntu.com/questions/290884/blacklist-conf-ignoring-bad-line-boot-prompt)

---

### Post by eddiecalvert on 2017-04-23
Hello Rob, thanks so much for your quick response and assistance, mainly for pointing to what seems to be a similar issue, but I could not see anything in the "kernal /etc/modprobe.d/blacklist.conf",that addresses my problem, details of contents pasted below:

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist acer-wmi

I had a problem previously with "acer-wmi" showing with the boot-up, which cleared the problem after I "blacklisted" it in /etc/modprobe.d/blacklist.conf, but then this error then appeared when booting up, then after a few seconds it clears, "libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper' ".

I also searched all forums, but found nothing that could explain to me how to resolve it. I also blacklisted 'drm_kms_helper', and even removed it from the file and that did nothing as well. I also checked                         [FONT=Arial][SIZE=3][B]cat -n /etc/modprobe.d/local.conf
[/B][/SIZE][/FONT]                         
[FONT=Arial][SIZE=3][B]
drm_kms_helper[/B][/SIZE][/FONT]

 [FONT=Arial][SIZE=3]**options drm_kms_helper poll=N**[/SIZE][/FONT]


is all that I found.

I also tried "sudo apt-get --reinstall -o Dpkg::Options::="--force-confask" install kmo", and this error was returned.

                        Adding library /lib/x86_64-linux-gnu/libdevmapper.so.1.02.1
 libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
 libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
 Building cpio /boot/initrd.img-4.4.0-72-generic.new initramfs
  
Any further assistance to this newbie will be appreciated.

---

### Post by RobGoss on 2017-04-23
Is this a freshly installed system if so when did you install it?

---

### Post by eddiecalvert on 2017-04-23
Hi Rob,

Thanks again for coming back.

Maybe some background, no it was reinstalled about week ago with Windows 7 as well (a dual boot), and it ran really very smoothly with no issues, but then I also needed to re-install Windows 7 again to do a repair after MS (the virus updates) caused that OS to crash. So I just done a re-install again (btw hated having to make this choice), but I really needed to run some expensive Business Planning SW that I cannot run on Linux, (and I did not like the WINE solution either), in that when I bought the business application SW a few years ago, I did not realize that it can only run on MS).

 So the MS reinstall was done a week ago, but when I did that, the Windows install "high-jacked" the Ubuntu boot GRUB .So had to do a GRUB Repair/Re-Install which was successful.

However, I am not 100% sure, but it was only after that, I think (i.e the Windows install) and after the GRUB reinstall that I noticed this single line error displayed with the system boot up.

Something tells me it may have even have something to do with the system BIOS, but I did a default BIOS reset, but it did not solve the problem.

Looks like I will have to do fresh reinstall. but I really, really would like to avoid doing that as everything else works super fine, runs fantastic performance wise and updates with zero errors, fast processing,etc, could not ask for more, once the system is booted up.

I really hope I can fix this though.

Thanks in advance.

---

### Post by RobGoss on 2017-04-23
I would hold off on the re-installation until maybe someone else might know what's producing this error on startup,  I say this because you say your system is running good, in most cases we would really like to know what's causing these types of issues. If I find a fix for this I'll post it for ya

---

### Post by eddiecalvert on 2017-04-24
Thanks so much, I am happy to hold off on a re-installation in the meantime. I agree it will be beneficial for the community as well.

---

### Post by eddiecalvert on 2017-04-24
Hello Rob, I ran the Ucaresystem-core cleanup script, and it very interestingly picked up the problem that I am experiencing, but I am not technically experienced enough to make sense of the below mentioned. 

I hope that this might point us on the right direction. I have highlighted the main errors which repeats on bold font for your benefit.
  	 	 	 	   **Running depmod.**
 **update-initramfs: deferring update (hook will be called later)**
 **Examining /etc/kernel/postinst.d.**
 **run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic**
 **run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic**
 **run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic**
 **update-initramfs: Generating /boot/initrd.img-4.4.0-75-generic**
 **libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'**
 **libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper' (REPEATs MANY LINES)**

  
Then moves onto the following:

  	 	 	 	   Generating grub configuration file ...
 Found linux image: /boot/vmlinuz-4.4.0-75-generic
 Found initrd image: /boot/initrd.img-4.4.0-75-generic
 Found linux image: /boot/vmlinuz-4.4.0-72-generic
 Found initrd image: /boot/initrd.img-4.4.0-72-generic
 Found linux image: /boot/vmlinuz-4.4.0-31-generic
 Found initrd image: /boot/initrd.img-4.4.0-31-generic
 Found Windows 7 (loader) on /dev/sda2
 Found Windows 7 (loader) on /dev/sda3
 done
 Setting up linux-image-generic (4.4.0.75.81) ...
 Setting up linux-headers-4.4.0-75 (4.4.0-75.96) ...
 Setting up linux-headers-4.4.0-75-generic (4.4.0-75.96) ...
 Examining /etc/kernel/header_postinst.d.
 run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
 Setting up linux-headers-generic (4.4.0.75.81) ...
 Setting up linux-generic (4.4.0.75.81) ...
 Setting up linux-libc-dev:amd64 (4.4.0-75.96) ...
 
 
 ###############################################
 Finished updating packages and system libraries
 ###############################################
 
 
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following packages will be REMOVED:
   linux-headers-4.4.0-31* linux-headers-4.4.0-31-generic*
   linux-image-4.4.0-31-generic* linux-image-extra-4.4.0-31-generic*
 0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
 After this operation, 295 MB disk space will be freed.
 (Reading database ... 428414 files and directories currently installed.)
 Removing linux-headers-4.4.0-31-generic (4.4.0-31.50) ...
 Removing linux-headers-4.4.0-31 (4.4.0-31.50) ...
 Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
 run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
 Error! Your kernel headers for kernel 4.4.0-31-generic cannot be found.
 **Please install the linux-headers-4.4.0-31-generic package,**
 **or use the --kernelsourcedir option to tell DKMS where it's located**
  
Then completes the clean up, but the problem still persists.

---

### Post by RobGoss on 2017-04-24
After doing a search I've seem to come across this bug report from Launchpad, [https://bugs.launchpad.net/ubuntu/+source/pptpd/+bug/1571295](https://bugs.launchpad.net/ubuntu/+source/pptpd/+bug/1571295)
There seems to be a few people effected by the same issue

---

### Post by eddiecalvert on 2017-04-25
Thanks looked at the feedback and narrative, so it looks, like a release was done in August 2016, but given my situation, looks like the only resolution is a rebuild? Whats your thoughts and recommendations from a most practical point of view, live with it or rebuild? BTW tried the Maartens work around, [Maarten Fonville (maarten-fonville)]("https://launchpad.net/%7Emaarten-fonville")             wrote             on 2016-04-17:[TABLE]
[TR]
[TD][/TD]
[TD="class: bug-comment-index"]           [ #1]("https://bugs.launchpad.net/ubuntu/+source/pptpd/+bug/1571295/comments/1")           [/TD]
         [/TR]
            [/TABLE]
                               The workaround fix is: sudo mv /etc/modprobe.d/pptpd.conf /lib/modules-load.d/

              
I got a response 
"libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
root@eddie-ThinkPad-Edge:/home/eddie# sudo mv /etc/modprobe.d/pptpd.conf /lib/modules-load.d/
mv: cannot stat '/etc/modprobe.d/pptpd.conf': No such file or directory"

Any thoughts on this?

---

### Post by RobGoss on 2017-04-25
I guess that depend on how much work it would be for you and your data

I know how it is when a system is producing errors it's very annoying, I'm currently running 16.04.2 on this machine and it runs flawless. If it were me I would just do a fresh installation and see how that goes seeing it's a know bug

---

### Post by RobGoss on 2017-04-25
I'm also running 16.04.2 and it runs well, seeing it's a know bug I would try a fresh installation and see how that goes

I know it's annoying getting boot errors on startup hopefully they will have a fix for this issue soon

---

