---
title: "grub messed up"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by cmcanulty on 2013-04-14
I did a regular update and now am getting all of these grub errors apparently I now have grub for quantal but am running precise and want to keep precise. I don't get a grub splash screen to edit either just a huge amount of scrolling text with a black background, see the end of the ud log below. I already tried configure -a to no result
```

cmcanulty@darcytech:~$ ud
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise Release.gpg                 
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://security.ubuntu.com precise-security Release              
Hit http://archive.canonical.com precise Release                     
Hit http://us.archive.ubuntu.com precise Release                      
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]  
Hit http://extras.ubuntu.com precise Release                                  
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources             
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main amd64 Packages            
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com precise-security/main i386 Packages    
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://archive.canonical.com precise/partner i386 Packages        
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:3 http://us.archive.ubuntu.com precise-updates/main Sources [377 kB]       
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en    
Hit http://security.ubuntu.com precise-security/restricted Translation-en    
Hit http://security.ubuntu.com precise-security/universe Translation-en       
Ign http://archive.canonical.com precise/partner Translation-en_US            
Ign http://extras.ubuntu.com precise/main Translation-en_US                  
Ign http://archive.canonical.com precise/partner Translation-en
Get:4 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:5 http://us.archive.ubuntu.com precise-updates/universe Sources [83.4 kB]
Ign http://extras.ubuntu.com precise/main Translation-en
Get:6 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,562 B]
Get:7 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [598 kB]
Get:8 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [193 kB]
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/main i386 Packages [610 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [196 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,167 kB in 5s (413 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.5.0-27-generic (3.5.0-27.46~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-27-generic...
P: Writing config for /boot/vmlinuz-3.5.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
/usr/sbin/grub-mkconfig: 39: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-27-generic; however:
  Package linux-image-3.5.0-27-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-image-3.5.0-27-generic
 linux-image-generic-lts-quantal
E: Sub-process /usr/bin/dpkg returned an error code (1)
cmcanulty@darcytech:~$ 

```

---

### Post by fantab on 2013-04-14
I had a similar issue and I fixed it with:

sudo dpkg-reconfigure grub-pc

If you haven't noticed already, there seems be a 'bad' install of 3.5.0-27 generic. Try removing it and run apt-get update followed by dist-upgrade.

---

### Post by cmcanulty on 2013-04-14
that gave me an error, am I risking the whole install by removing, the kernel?

```
cmcanulty@darcytech:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for cmcanulty: 
/var/lib/dpkg/info/grub-pc.config: 39: /etc/default/grub: Syntax error: EOF in backquote substitution
cmcanulty@darcytech:~$
```

the removing got this error

```
E: linux-image-3.5.0-27-generic: subprocess installed post-installation script returned error exit status 2
```

then dist upgrade just reinstalls the same grub 3.5.0-27 with the same errors, how do I get a previous grub?

```
cmcanulty@darcytech:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for cmcanulty: 
/var/lib/dpkg/info/grub-pc.config: 39: /etc/default/grub: Syntax error: EOF in backquote substitution
cmcanulty@darcytech:~$ ^C
cmcanulty@darcytech:~$ sudo dpkg-reconfigure grub-pc
/var/lib/dpkg/info/grub-pc.config: 39: /etc/default/grub: Syntax error: EOF in backquote substitution
cmcanulty@darcytech:~$ sudo dpkg-reconfigure grub-pc
/var/lib/dpkg/info/grub-pc.config: 39: /etc/default/grub: Syntax error: EOF in backquote substitution
cmcanulty@darcytech:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                      
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                              
Hit http://us.archive.ubuntu.com precise Release                                            
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                        
Hit http://security.ubuntu.com precise-security Release.gpg                                 
Hit http://archive.canonical.com precise Release.gpg                                        
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://security.ubuntu.com precise-security Release                                     
Hit http://archive.canonical.com precise Release                                            
Hit http://us.archive.ubuntu.com precise/main Sources                                       
Hit http://us.archive.ubuntu.com precise/restricted Sources                                 
Hit http://us.archive.ubuntu.com precise/universe Sources              
Hit http://us.archive.ubuntu.com precise/multiverse Sources                                 
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                                
Hit http://extras.ubuntu.com precise Release                                                
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages                          
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages      
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                             
Hit http://security.ubuntu.com precise-security/main Sources                                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                           
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                              
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                        
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                        
Hit http://archive.canonical.com precise/partner amd64 Packages                             
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                          
Hit http://extras.ubuntu.com precise/main amd64 Packages                                    
Get:3 http://us.archive.ubuntu.com precise-updates/main Sources [377 kB]                    
Hit http://security.ubuntu.com precise-security/restricted Sources                          
Hit http://security.ubuntu.com precise-security/universe Sources                            
Hit http://security.ubuntu.com precise-security/multiverse Sources                          
Hit http://security.ubuntu.com precise-security/main amd64 Packages                         
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                   
Hit http://security.ubuntu.com precise-security/universe amd64 Packages      
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages    
Hit http://security.ubuntu.com precise-security/main i386 Packages           
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                    
Hit http://security.ubuntu.com precise-security/universe i386 Packages                      
Hit http://archive.canonical.com precise/partner i386 Packages                              
Ign http://archive.canonical.com precise/partner TranslationIndex                           
Hit http://extras.ubuntu.com precise/main i386 Packages                                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                                  
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                    
Hit http://security.ubuntu.com precise-security/main TranslationIndex                       
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                 
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex   
Hit http://security.ubuntu.com precise-security/universe TranslationIndex     
Hit http://security.ubuntu.com precise-security/main Translation-en           
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                   
Hit http://security.ubuntu.com precise-security/restricted Translation-en                   
Hit http://security.ubuntu.com precise-security/universe Translation-en                     
Get:4 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:5 http://us.archive.ubuntu.com precise-updates/universe Sources [83.4 kB]
Get:6 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,562 B]             
Get:7 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [598 kB]             
Ign http://archive.canonical.com precise/partner Translation-en_US                          
Ign http://extras.ubuntu.com precise/main Translation-en_US                   
Ign http://extras.ubuntu.com precise/main Translation-en                      
Ign http://archive.canonical.com precise/partner Translation-en
Get:8 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [193 kB]
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/main i386 Packages [610 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [196 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,167 kB in 3s (573 kB/s)
Reading package lists... Done
cmcanulty@darcytech:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.5.0-27-generic (3.5.0-27.46~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.5.0-27-generic...
P: Writing config for /boot/vmlinuz-3.5.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
/usr/sbin/grub-mkconfig: 39: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.5.0-27-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
cmcanulty@darcytech:~$ 
```

---

### Post by fantab on 2013-04-14
You can check the kernel in use with:

```
uname -r
```

You can boot into an older kernel from Grub-Menu -> advanced options; select an older kernel and boot.

N.B. Do not remove the kernel in use.

Also there seems to be a syntax error in /etc/default/grub check that as well or post here and we'll have a look.

---

### Post by cmcanulty on 2013-04-14
cmcanulty@darcytech:~$ uname -r
3.5.0-23-generic
cmcanulty@darcytech:~$
Do I risk this mess now every day when I run updates or dist-upgrade? 
Grub, I just found an additional quote I took out I missed it before as it was on the next line so see if this looks ok now, the extra " was after

```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

Here is my grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

export GRUB_COLOR_NORMAL="blue/white"
export GRUB_COLOR_HIGHLIGHT="light-green/red"
GRUB_FONT="/boot/grub/unicode.pf2"
```

OK now it is working OK thsnks for all your help, I just logged in and out, duh! PS the mark thread as solved is missing from my menu now

---

### Post by fantab on 2013-04-14
The problem is supposedly in line 39 (or so I think), which is, GRUB_FONT="/boot/grub/unicode.pf2". Comment the line out and see if it helps.

Since you are using Kernel: 3.5.0-23-generic you can remove** linux-image-3.5.0-27-generic**. Remove it with Synaptic, there will be 3 or 4 packages for the kernel version 3.5.0-27 remove them all. Then in Synaptic select "Not installed (residual config), it will show residual pkgs. or libs. remove them too. Also 'fix broken packages' from Synaptic.

sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by cmcanulty on 2013-04-14
OK thanks that worked how do I prevent this from happening next time I do 
```
sudo apt-get update && sudo apt-get dist-upgrade 
```

---

### Post by fantab on 2013-04-14
It just happens. I am not sure why though.

If it happens again? Just remove the faulty package and repeat the code.

The relavant parts of the error:
```
.....

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 1 not fully installed or removed.

...

Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-27-generic.postinst line 1010. dpkg: error processing linux-image-3.5.0-27-generic (--configure):  subprocess installed post-installation script returned error exit status 2 Errors were encountered while processing:  linux-image-3.5.0-27-generic
```

So you will know what package is causing the problem.

---

### Post by cmcanulty on 2013-04-14
Thanks!

---

