---
title: "update manager error report"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by bonehunter on 2012-11-20
Hi guys thanks for your time,

my problem since I installed cinnamon desktop environment my update manager is giving me an error message and I can´t update.

What I´ve got is this:

```

installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 228295 files and directories currently installed.) 
Preparing to replace python-keyring 0.7.1-1fakesync1 (using .../python-keyring_0.9.2-0ubuntu0.12.04.2_all.deb) ... 
Unpacking replacement python-keyring ... 
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Not updating initrd symbolic links since we are being updated/reinstalled  
(3.2.0-23.36 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(3.2.0-23.36 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found. 
Please install the linux-headers-3.2.0-23-generic package, 
or use the --kernelsourcedir option to tell DKMS where it's located 
Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found. 
Please install the linux-headers-3.2.0-23-generic package, 
or use the --kernelsourcedir option to tell DKMS where it's located 
Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found. 
Please install the linux-headers-3.2.0-23-generic package, 
or use the --kernelsourcedir option to tell DKMS where it's located 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-23-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-33-generic (3.2.0-33.52) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-33-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-33-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-33-generic; however: 
  Package linux-image-3.2.0-33-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.2.0.33.36); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up python-keyring (0.9.2-0ubuntu0.12.04.2) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 linux-image-3.2.0-23-generic 
 linux-image-3.2.0-33-generic 
 linux-image-generic 
 linux-generic 
Error in function:  
Setting up linux-image-3.2.0-33-generic (3.2.0-33.52) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic 
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-33-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-33-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-33-generic; however: 
  Package linux-image-3.2.0-33-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Not updating initrd symbolic links since we are being updated/reinstalled  
(3.2.0-23.36 was configured last, according to dpkg) 
Not updating image symbolic links since we are being updated/reinstalled  
(3.2.0-23.36 was configured last, according to dpkg) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
Error! Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found. 
Please install the linux-headers-3.2.0-23-generic package, 
or use the --kernelsourcedir option to tell DKMS where it's located 
Your kernel headers for kernel 3.2.0-23-generic cannot be found. 
Please install the linux-headers-3.2.0-23-generic package, 
or use the --kernelsourcedir option to tell DKMS where it's located 
Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found. 
Please install the linux-headers-3.2.0-23-generic package, 
or use the --kernelsourcedir option to tell DKMS where it's located 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic 
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-23-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.2.0.33.36); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 

```

I tryed already ppa manager did not help, also that tweak tool "advanced settings" from ubuntu software center. So far I don´t know what to do to get my lovely Ubuntu to get back to work proper. Through my search on Google I could not find something helpful.

Thanks a lot guys for spending your time on my issue!!!

Greating

---

### Post by Sealbhach on 2012-11-20
Hi, first try running in a terminal

```
sudo dpkg --configure -a
```It's also telling you "please install the linux-headers-3.2.0-23-generic package" so install that
```

sudo apt-get install linux-headers-3.2.0-23-generic
```


.

---

### Post by bonehunter on 2012-11-21
thanks for your quick replay but unfortunately both did not work, that is what I got as result below is the second code, again thanks for your time guys!

[the first code]


smart@smart-Aspire:~$ sudo dpkg --configure -a
[sudo] password for smart: 
Setting up linux-image-3.2.0-33-generic (3.2.0-33.52) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-33-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-33-generic; however:
  Package linux-image-3.2.0-33-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found.
Please install the linux-headers-3.2.0-23-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found.
Please install the linux-headers-3.2.0-23-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.2.0-23-generic cannot be found.
Please install the linux-headers-3.2.0-23-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.33.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-33-generic
 linux-image-generic
 linux-image-3.2.0-23-generic
 linux-generic



[second code]


smart@smart-Aspire:~$ sudo apt-get install linux-headers-3.2.0-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.2.0-23
The following NEW packages will be installed:
  linux-headers-3.2.0-23 linux-headers-3.2.0-23-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 12.4 MB of archives.
After this operation, 67.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) precise/main linux-headers-3.2.0-23 all 3.2.0-23.36 [11.4 MB]
Get:2 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) precise/main linux-headers-3.2.0-23-generic amd64 3.2.0-23.36 [947 kB]
Fetched 12.4 MB in 7s (1,622 kB/s)                                             
Selecting previously unselected package linux-headers-3.2.0-23.
(Reading database ... 228333 files and directories currently installed.)
Unpacking linux-headers-3.2.0-23 (from .../linux-headers-3.2.0-23_3.2.0-23.36_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-23-generic.
Unpacking linux-headers-3.2.0-23-generic (from .../linux-headers-3.2.0-23-generic_3.2.0-23.36_amd64.deb) ...
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-33-generic (3.2.0-33.52) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-33-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-33-generic; however:
  Package linux-image-3.2.0-33-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.33.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.2.0-23 (3.2.0-23.36) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Setting up linux-headers-3.2.0-23-generic (3.2.0-23.36) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Errors were encountered while processing:
 linux-image-3.2.0-23-generic
 linux-image-3.2.0-33-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by varunendra on 2012-11-22
@*bonehunter,*
First, a humble advice to make your posts look cleaner and more readable (please make it a habit for future posts) -

Please edit your above post to wrap the output codes in **'Code'** tags by highlighting the output part with your mouse cursor, then (in advance editing mode) clicking on **#** at the top of the edit box in which you create new posts. It will put the selected text in a nice box like *sandyd* has done for you in the first post.

It not only makes your post compact, but also preserves the output formatting, thus making it more readable.

You can also do it by manually typing [noparse]```
 at the beginning and 
```[/noparse] at the end of the output part.


Onto your problem now -

> **bonehunter said:**
> 
```
..
..
**/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: [COLOR=Red]EOF in backquote substitution[/COLOR] **
..
[B]Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010. 
dpkg: [COLOR=Red]error processing linux-image-3.2.0-23-generic[/COLOR] (--configure): [/B]
 subprocess installed post-installation script returned error exit status 2 
..
.. [COLOR=Red](and similar errors ... leading to further errors like -)[/COLOR]
..
**dpkg: error processing linux-image-3.2.0-33-generic (--configure)**: 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
[B] linux-image-generic depends on linux-image-3.2.0-33-generic; however: 
  Package linux-image-3.2.0-33-generic[COLOR=Red] is not configured yet[/COLOR].[/B] 

Same in the next attempt-
> **bonehunter said:**
> 
[the first code]..
..
**/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: [COLOR=Red]EOF in backquote substitution[/COLOR]**
..
(and so on....)
I could recommend to just clean downloaded archives *(apt-get clean)* and delete existing package lists *(/var/lib/apt/lists)* then redo update, but let's first take a look at your /etc/default/grub file plus current kernel in use.

Please post outputs of -
[CODE]cat /etc/default/grub
uname -mr
```

---

### Post by bonehunter on 2012-11-22
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
smart@smart-Aspire:~$



3.2.0-32-generic x86_64


Thanks!
P.s I read your advice but as a beginner I´m not sure if I will sort it out proper.

---

### Post by varunendra on 2012-11-22
**[COLOR="Red"]EDIT :[/COLOR]** To see an example of **[COLOR="Navy"]How To Use Code Tags[/COLOR]**, skip to the "**PS:**" part of the post below.

> **bonehunter said:**
> GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
....
*(blah-blah-blah-...)*Are you sure this was ALL the output and nothing left out on top from being copied ? It's not good if so. Here's mine for reference -
```
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
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
Accordingly, please post a copy of the "grub" file itself so we can be sure. It is located at **/etc/default** directory.


[size=3]**[COLOR="Navy"]PS :[/COLOR] [COLOR="DarkRed"]Example of Code Tags[/COLOR]**[/size]
> **bonehunter said:**
> P.s I read your advice but as a beginner I´m not sure if I will sort it out proper.Ah, let me then try with an example of *'free -m'* command -
Without the tags (your current style), its output will look like -
~$ free -m
             [COLOR=Navy]total       used       free     shared    buffers     cached
Mem:          3857       3649        208          0        143       1417
-/+ buffers/cache:       2087       1770
Swap:         6168        467       5701[/COLOR]

*[COLOR="#808080"]Hmm.. nice puzzle up there ^^ ! (scratches head and pulls out some hair..)[/COLOR]*

Now after copy-pasting above in my post, if I type [COLOR="#FF0000"]**[noparse]```
[/noparse]**[/COLOR] in its beginning, and [COLOR="#FF0000"]**[noparse]
```[/noparse]**[/COLOR] at the output's end like this -

[COLOR="#FF0000"]**[noparse]```
[/noparse]**[/COLOR]
~$ free -m
             [COLOR=Navy]total       used       free     shared    buffers     cached
Mem:          3857       3649        208          0        143       1417
-/+ buffers/cache:       2087       1770
Swap:         6168        467       5701[/COLOR]
[COLOR="#FF0000"]**[noparse]
```[/noparse]**[/COLOR]

Then 'After' clicking on "Submit Reply" button to post it, it will look like this -
```
[COLOR=Navy]~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3857       3649        208          0        143       1417
-/+ buffers/cache:       2087       1770
Swap:         6168        467       5701[/COLOR]

```Looks better ? (you may also use "Preview Post" button to see how it will finally look in your post)

This pair of [noparse][CODE][/noparse] tags can be automatically generated around a selected portion of text by highlighting the text with mouse pointer, then clicking on **#** at the top of the Advanced edit box in which you create new posts.
[ATTACH=CONFIG]245871[/ATTACH]

Alternatively, you can copy an output code > generate the tags > press ctrl-V to paste the copied text in-between the tags. That's a bit quicker.

Hope you find it useful. :)

---

### Post by bonehunter on 2012-11-22
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```cool thanks was very helpful

---

### Post by varunendra on 2012-11-22
Glad you liked it.

Assuming this is your actual grub file, there is a minor error (with HUGE consequences !!)
> **bonehunter said:**
> ```

GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT=[COLOR=Red]”[/COLOR]**quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
Notice the double-quote (**[COLOR=Red]”[/COLOR]**) highlighted in [COLOR=Red]**red**[/COLOR] in the emboldened line. That is the culprit. The one at the end of the same line is correct one. Just overwrite the highlighted one by copy-pasting the last one.

Proofread, save and close. Then try -
[CODE]sudo update-grub
```
If it updates without errors, you may proceed with the original system update you were attempting.

---

### Post by bonehunter on 2012-11-25
Hi [varunendra]("http://ubuntuforums.org/member.php?u=1043629")

it is solved I owe you something, thanks a lot for sharing your knowledge with me.

take care

---

### Post by varunendra on 2012-11-25
> **bonehunter said:**
> Hi [varunendra]("http://ubuntuforums.org/member.php?u=1043629")

it is solved I owe you something, thanks a lot for sharing your knowledge with me.

take care
I shall, and you are most welcome :)

[I][Ha..! 6:30 in the morning, opens eyes in front of his never resting laptop screen, and is greeted with "Success" !! What can be a better morning !:) Good Morning from India, & Thank YOU too ..]
[/I]

---

### Post by Sealbhach on 2012-11-27
Well done varunendra. It's also nice when the OP takes the trouble to say thanks. :)

.

---

### Post by varunendra on 2012-11-27
> **Sealbhach said:**
> It's also nice when the OP takes the trouble to say thanks. :)

Certainly! And even nicer when a colleague comes down to compliment you! Thank you, I feel more energetic now.. :)

---

