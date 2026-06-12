---
title: "[SOLVED] Synaptic can't install Kernel Image"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by fidamehran on 2008-06-24
**3 Weeks Ago:**

Dear All,
I have continued getting Updates automatically through the notification on top and installing them without worrying too much about what they are and what they do. Being a completely new user, I guess it's not uncommon.

Yesterday I received update notification and updated. But one item, "Linux-image-2.6.24-19-generic" cannot be installed by the Synaptic. It downloaded the file and starts installing.
But in the end says, "An Error Occurred: The Following Details Are Provided: [E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version]".

I attached the screenshot.

What is the problem? My Ubuntu is starting okay, and the update available icon is still flashing on the taskbar.
Any help?


**Now, even after 3 Weeks:**

**Back with the same problem once again.**
Looks like nothing was solved. I also don;t know if anybody is having the problem or not.
If somebody new to the thread doesn't know what those 5 pages are about, then let me tell you.
My update manager downloaded updates of Kernel Image 2.6.24-19-xx and tried installing it. But every time it tries to install, an error occurs, saying, 

"E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version".

I tried simply going to the file location (cache folder) and tried to install it manually and got a somewhat similar message. You can find find that in the attachment. You could give me some ideas about the problem.

---

### Post by fahadsadah on 2008-06-24
Please open a terminal and type: ```
sudo aptitude update && sudo aptitude upgrade
```
This may take a while, and you will be asked for a password.

If this also causes an error, please post said error here.

---

### Post by avtolle on 2008-06-24
If you get the same error, then try```
df -h
```and see whether your boot partition is full. If it is, go to Synaptic and delete older versions of the kernel (search under linux-image). If you've not a boot partition, and there are no room problems in the / (root) partition, then it would appear to me that there may be a corrupt file being downloaded from the mirror you are using. Try switching to a different mirror ("download from" on first page of Synaptic), and try to update again.

---

### Post by fidamehran on 2008-06-24
This is what I got:


Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]   
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [258kB]          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6623B]    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [75.5kB]          
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [910B]      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [59.6kB]     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [12.8kB]      
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [12.0kB]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [1943B]    
Fetched 486kB in 46s (10.4kB/s)                                                 
Reading package lists... Done
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libawn0 
The following packages will be upgraded:
  linux-image-2.6.24-19-generic python-central 
2 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 41.1kB/18.4MB of archives. After unpacking 164kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main python-central 0.6.7ubuntu0.1 [41.1kB]
Fetched 41.1kB in 3s (11.0kB/s)        
(Reading database ... 169006 files and directories currently installed.)
Removing libawn0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 168999 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.33 (using .../linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace python-central 0.6.5ubuntu1 (using .../python-central_0.6.7ubuntu0.1_all.deb) ...
Unpacking replacement python-central ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-central (0.6.7ubuntu0.1) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

I        
I guess the problem remained, right?

---

### Post by fidamehran on 2008-06-24
df -h: gave this. I think boot partition is not full.



Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      2.8G  1.5G  1.2G  56% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M   56K  502M   1% /proc/bus/usb
udev                  502M   56K  502M   1% /dev
devshm                502M   12K  502M   1% /dev/shm
lrm                   502M   38M  465M   8% /lib/modules/2.6.24-19-generic/volatile
/host/ubuntu/disks/usr.disk
                      3.7G  2.5G  1.1G  71% /usr
gvfs-fuse-daemon      2.8G  1.5G  1.2G  56% /home/fida/.gvfs
/dev/sda6              21G   19G  1.7G  92% /media/disk
/dev/sda7              23G   11G   12G  47% /media/disk-1

---

### Post by ukripper on 2008-06-24
Can you do follwoing and update again:
```
sudo apt-get clean
```
```
sudo apt-get autoclean
```

this will clean your /var/cache/apt/archives directory for cached deb packages and partial ones.

then do 
```
sudo aptitude update
```

---

### Post by fidamehran on 2008-06-24
I got this:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

But Update icon is still there.

---

### Post by ukripper on 2008-06-24
can you run ```
sudo update-grub
```
and see if new kernel gets listed there

---

### Post by avtolle on 2008-06-24
After```
sudo aptitude update
``` do ```
sudo aptitude safe-upgrade
```to see if it will now download and install the updates.

---

### Post by fidamehran on 2008-06-24
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Also attaching my Menu.lst file

---

### Post by fidamehran on 2008-06-24
> **avtolle said:**
> After```
sudo aptitude update
``` do ```
sudo aptitude safe-upgrade
```to see if it will now download and install the updates.
Ok, now it's Re-downloading. Getting back to you after the update. My net is pretty slow. Should take ~ 30 minutes.

---

### Post by avtolle on 2008-06-24
Let us know how it goes.

---

### Post by fidamehran on 2008-06-24
> **avtolle said:**
> After```
sudo aptitude update
``` do ```
sudo aptitude safe-upgrade
```to see if it will now download and install the updates.
After giving previous update and safe upgrade command, this was what I got.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  linux-image-2.6.24-19-generic 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.4MB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-19-generic 2.6.24-19.34 [18.4MB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-19-generic 2.6.24-19.34 [18.4MB]
Fetched 11.1MB in 39min39s (4659B/s)                                            
(Reading database ... 168999 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.33 (using .../linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      


Should I clean the cache again and restart the computer?

---

### Post by fidamehran on 2008-06-24
One more thing. Menu.lst shows I already have Kernel 2.6.24-19. Why is the OS asking me to update again?

---

### Post by avtolle on 2008-06-24
There was an update to the .19 kernel (I don't recall the sub number). It looks like from the error message that the file that is being downloaded from the mirror you are using has an error in it (see the discussion about a broken pipe). Clear the cache as before, and restart if you want. 

As earlier posted, I'd try to change my download source from what you have it now set to, reload, and try again.

---

### Post by fidamehran on 2008-06-24
> **avtolle said:**
> If you get the same error, then try```
df -h
```and see whether your boot partition is full. If it is, go to Synaptic and delete older versions of the kernel (search under linux-image). If you've not a boot partition, and there are no room problems in the / (root) partition, then it would appear to me that there may be a corrupt file being downloaded from the mirror you are using. Try switching to a different mirror ("download from" on first page of Synaptic), and try to update again.
Where do I get "Download From" option in Synaptic. I seem to find no such option.

However, I marked the 19.33 for upgrade to 19.34 and clicked Apply. It is now downloading the 19.34 kernel again. But I very much suspect that it will do the same thing again.

---

### Post by avtolle on 2008-06-24
Sorry, I gave you the wrong application (this can be done from Synaptic as well, but this is easier). Go to Software Sources and change the "download from" window (you can click on it and it will give you Main Server, etc.) and select another source. In Synaptic, you click on "Settings" then select Repositories, which gets you to Software Sources.

---

### Post by fidamehran on 2008-06-24
Thanks a million, friend. It's bed time here in Bangladesh.
I finally found the "Download from" option. Missed it out completely at first. I'll see what happens subsequently tommorrow. Hope to see you around tommorrow also. Have a nice day.

---

### Post by fidamehran on 2008-06-25
Still in office using Windows XP (office believes in genuine paid Windows XPs). Get back to you when I get home (1500 GMT).

{By the way, after clearing everything yesterday, the update icon was still flashing, and whichever way i tried to install the kernel image, it did not delete the downloaded file in Synaptic, rather tried (and failed) to install the same file over and over again}

Anyway, hope to reach you at around 1500 GMT today. (25 June)

---

### Post by ukripper on 2008-06-25
> **fidamehran said:**
> Still in office using Windows XP (office believes in genuine paid Windows XPs). Get back to you when I get home (1500 GMT).

{By the way, after clearing everything yesterday, the update icon was still flashing, and whichever way i tried to install the kernel image, it did not delete the downloaded file in Synaptic, rather tried (and failed) to install the same file over and over again}

Anyway, hope to reach you at around 1500 GMT today. (25 June)

Ok try this command when you get home:

```
sudo dpkg --configure -a 
```
this will check for any broken packages and fix it for update manager.

and then run 
```
sudo aptitude update
```

---

### Post by fidamehran on 2008-06-25
> **ukripper said:**
> Ok try this command when you get home:

```
sudo dpkg --configure -a 
```
this will check for any broken packages and fix it for update manager.

and then run 
```
sudo aptitude update
```
(Actually the new update is still there, downloaded, and no matter what, the Synaptic/Update Manager is always trying to install that downloaded corrupt file{!})

This is what happenned:

fida@fida-desktop:~$ sudo dpkg --configure -a
[sudo] password for fida: 
**{This (below) came up pretty swift. Didn't take time as if checking for broken updates &/or fixing....}**
fida@fida-desktop:~$ sudo aptitude update 
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy Release.gpg                     
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/main Translation-en_US          
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/restricted Translation-en_US     
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/universe Translation-en_US                     
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/multiverse Translation-en_US                   
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates Release.gpg              
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/main Translation-en_US                 
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/restricted Translation-en_US           
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/universe Translation-en_US             
Ign [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/multiverse Translation-en_US
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy Release                                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US        
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                 
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/main Packages    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/restricted Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/main Sources     
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/restricted Sources
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/universe Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/universe Sources 
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/multiverse Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy/multiverse Sources
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/main Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/restricted Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/main Sources
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/restricted Sources
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/universe Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/universe Sources
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/multiverse Packages
Hit [http://ftp.jaist.ac.jp](http://ftp.jaist.ac.jp) hardy-updates/multiverse Sources
Reading package lists... Done
fida@fida-desktop:~$ 

Is there no way to completely remove the downloaded corrupted update file (kernel image) and fresh download it?

---

### Post by fidamehran on 2008-06-25
By the way, as instructed before, I changed the Mirror from "Mirrors in US" to a mirror in Japan (me being in Asia, thought, Japan server would be better).

---

### Post by fidamehran on 2008-06-25
When I started the PC today, I tried to download a fresh copy of the Kernel Image through Synaptic (from the Japan mirror), as if I had no previously downladed image. It did start to download the file once again, but halfway through download, started installing and managed to get hold of the older one (corrupted). I downloaded the first one from a US server.
One more thing, can we be sure that the package downloaded earlier is really corrupted, and the problem is not elsewhere?

---

### Post by avtolle on 2008-06-25
I concluded the earlier package might be corrupted due to the error message about the broken pipe. 

You say that half-way through the download, there was an installation? If so, did the same error message occur?

---

### Post by fidamehran on 2008-06-25
> **avtolle said:**
> I concluded the earlier package might be corrupted due to the error message about the broken pipe. 

You say that half-way through the download, there was an installation? If so, did the same error message occur?
The very o-l-d same. Things are starting to bore you guys, I guess?

---

### Post by avtolle on 2008-06-25
Not bored; perplexed, perhaps. Do```
sudo apt-get clean
```and```
sudo apt-get autoclean
```again to try to clear out the cache. I've got to go take a look at another command to get the syntax correct which may work, be back in a bit.

---

### Post by avtolle on 2008-06-25
Try from the console```
sudo dpkg -P
``` to see if this purges the package.

EDIT: Better, I think```
sudo dpkg --purge linux-image-2.6.24.19-generic_2.6.24.34_i386.deb
```

---

### Post by fidamehran on 2008-06-25
Done. although don't know what to do next.

---

### Post by fidamehran on 2008-06-25
> **fidamehran said:**
> Done. although don't know what to do next.
fida@fida-desktop:~$ sudo dpkg -P
dpkg: --purge needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
fida@fida-desktop:~$

---

### Post by avtolle on 2008-06-25
See my edit.

---

### Post by fidamehran on 2008-06-25
> **avtolle said:**
> See my edit.
fida@fida-desktop:~$ sudo dpkg --purge linux-image-2.6.24.19-generic_2.6.24.34_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

**Then I gave:**

fida@fida-desktop:~$ sudo dpkg --purge linux-image-2.6.24.19-generic_2.6.24.34
dpkg: status database area is locked by another process
fida@fida-desktop:~$

---

### Post by fidamehran on 2008-06-25
Locked should mean the Notification icon flashing on top, I guess.

---

### Post by avtolle on 2008-06-25
I fear my lack of experience with the purge command caused the latest round of problems. Try your second command again after waiting a bit, while I try to educate myself a bit more.

---

### Post by avtolle on 2008-06-25
From terminal do this to see if the kernel package that is causing all the trouble shows up```
sudo dpkg -l | grep -v ^ii
```

---

### Post by fidamehran on 2008-06-25
Even after long wait, I gave my 2nd command. Same result.

fida@fida-desktop:~$ sudo dpkg --purge linux-image-2.6.24.19-generic_2.6.24.34
dpkg: status database area is locked by another process
fida@fida-desktop:~$ 

I also tried after force quitting the update notification from System--> Administration--> System Monitor--> Processes.
:-(

---

### Post by fidamehran on 2008-06-25
> **avtolle said:**
> From terminal do this to see if the kernel package that is causing all the trouble shows up```
sudo dpkg -l | grep -v ^ii
```
fida@fida-desktop:~$ sudo dpkg -l | grep -v ^ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                            Description
+++-==========================================-==================================================-============================================
rc  libawn0                                    0.2.1-0ubuntu2                                     library for avant-window-navigator
fida@fida-desktop:~$

**Note: I installed AWN much earlier, and later uninstalled it.**

---

### Post by avtolle on 2008-06-25
Wondering if there was a problem with uninstalling AWN? 

Anyway, I'm working on a hypothesis. Please```
cd /var/cache/apt/archives
ls
```and post results.

---

### Post by fidamehran on 2008-06-25
> **avtolle said:**
> I fear my lack of experience with the purge command caused the latest round of problems. Try your second command again after waiting a bit, while I try to educate myself a bit more.
Input-ing the command again gave this:

fida@fida-desktop:~$  sudo dpkg --purge linux-image-2.6.24.19-generic_2.6.24.34
dpkg - warning: ignoring request to remove linux-image-2.6.24.19-generic_2.6.24.34 which isn't installed.
fida@fida-desktop:~$

---

### Post by fidamehran on 2008-06-25
> **avtolle said:**
> Wondering if there was a problem with uninstalling AWN? 

Anyway, I'm working on a hypothesis. Please```
cd /var/cache/apt/archives
ls
```and post results.
fida@fida-desktop:~$ cd /var/cache/apt/archives
fida@fida-desktop:/var/cache/apt/archives$ ls
lock  partial
fida@fida-desktop:/var/cache/apt/archives$

---

### Post by avtolle on 2008-06-25
That result is what I anticipated. OK, if you are still in /var/cache/apt/archive, do cd partial and ls and post results.

---

### Post by fidamehran on 2008-06-25
> **avtolle said:**
> That result is what I anticipated. OK, if you are still in /var/cache/apt/archive, do cd partial and ls and post results.
Nothing happens

fida@fida-desktop:/var/cache/apt/archives$ cd partial
fida@fida-desktop:/var/cache/apt/archives/partial$ ls
fida@fida-desktop:/var/cache/apt/archives/partial$

---

### Post by avtolle on 2008-06-25
OK, that confirms what I've been thinking here for a bit. The problem is that your system still sees the file, but it is not installed at all. Clearing the cache, as we tried to do before, should have taken care of it. The other commands I suggested were to see if, somehow, there was a partial installation of the kernel. The output of the latest set confirm it was not installed. 

When one downloads an update, it is cached "locally" for installation. Then, the system installs the updates from the cache. There is nothing showing up in the cache, as nearly as I can ascertain, related to the file that is causing the problem. 

For what it is worth, have you restarted your computer lately? Or, better yet, totally turned it off and let it sit for about 10 minutes, then powered it back up? If you've mentioned that you have done this, I missed it. If you haven't, I'd do that, power back up, and then try to download the kernel update again.

In removing AWN, how did you do this? By going to Synaptic and marking it for total removal? Just wondering if there's some stray configuration file which is causing the trouble as well.

---

### Post by fidamehran on 2008-06-25
AWN removal? Ya, I did that through Applications-->Add/Remove.

And.. I have been doing all this for the last 2 Hr and 30 min. That is the duration I haven't restarted. I'm restarting now and getting back to you.

---

### Post by fidamehran on 2008-06-25
Restarted. Gave the cleaning, purging, autocleaning, updating commands once again, one by one.

Still the Update Notification on top. And once I click it the update window comes (attachment).

Now, as I click, Install Updates, it's downloading again.

Let me see. I'll tell you if it stops half way and tries the customary Erroneous failed install. 

P.S.: As I said before, I download @4-5 KB/sec, so if the file manages to download completely, it'd take ~ 30 min.

So, hang in there, please.

---

### Post by avtolle on 2008-06-25
Unfortunately, my ability to stay here and help is at an end, time wise. If restarting doesn't resolve the problem, then I'm out of ideas. 

Ironically, with all the time you have taken in trying to resolve this problem, you could have done a total fresh install on your computer and gotten it tweaked as you want. This may be what you will need to do if someone else cannot come up with a way to resolve this problem; a general "cure all" for whatever ails you is to do a fresh install with all updates downloaded. Good luck.

---

### Post by avtolle on 2008-06-25
OK, I'll check back in a bit.

---

### Post by fidamehran on 2008-06-25
Please, there is no need to strain yourself. It was really cool talking to you and learning so much from you.
Yeah, I guess you're right. I could've done a fresh install by now. (I have been bugging you since day before yesterday, I guess.)
Let me see what happens after the now running download. I guess, I can also live with a flashing update icon until the next Kernel update comes along.

Thanks again and again for all the help and knowledge.

I will however post the final findings hopefully within half an hour, and close the thread.

I do hope to become more knowledgable like you people one day.

---

### Post by fidamehran on 2008-06-25
No use.

Same old message after I start installing the file.

E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

It was a good time spent with you. I won't post any further problems in this thread. The thread will remain open, so comment/advice from other friends will help a lot. At least I can learn something new.

See you in another thread.

---

### Post by fidamehran on 2008-06-26
Got rid of the problem. Changed the download mirror once again as I found the Japan server also not working for me. I went to the Repositories Option and asked it to select the best server/mirror for me. It selected one in UK. I selected that.
Then I tried to clean and purge the kernel image that has been downloaded but if failing to install for the long time.
Finally, I decided to get rid of the downloaded file in cache. So I typed
> sudo rm /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb
meaning to remove the file downloaded. What could be the worse that could happen?
Being a new Ubuntu user, and seeing Warning signs all over the forums for not using "sudo rm anything", it was a desperate thing for me to do. Guess I thought, it's cache, so what harm can it do?
It didn't do any harm of course. I reladed the repository and gave fresh update order at the Update Manager. I am not sure what it did, but now there is no more nnpdate Notification icons flashing at the top. Cheers.

---

### Post by avtolle on 2008-06-26
Outstanding work on your part. Please mark the thread "solved" if you would.

---

### Post by fidamehran on 2008-07-17
**Back with the same problem once again.**
Looks like nothing was solved. I also don;t know if anybody is having the problem or not.
If somebody new to the thread doesn't know what those 5 pages are about, then let me tell you.
My update manager downloaded updates of Kernel Image 2.6.24-19-xx and tried installing it. But every time it tries to install, an error occurs, saying, 

"E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version".

I tried simply going to the file location (cache folder) and tried to install it manually and got a somewhat similar message. You can find that in the attachment. You could give me some ideas about the problem.

---

### Post by ukripper on 2008-07-17
> **fidamehran said:**
> **Back with the same problem once again.**
Looks like nothing was solved. I also don;t know if anybody is having the problem or not.
If somebody new to the thread doesn't know what those 5 pages are about, then let me tell you.
My update manager downloaded updates of Kernel Image 2.6.24-19-xx and tried installing it. But every time it tries to install, an error occurs, saying, 

"E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version".

I tried simply going to the file location (cache folder) and tried to install it manually and got a somewhat similar message. You can find that in the attachment. You could give me some ideas about the problem.

in terminal use following and paste output here:
```
du -sh /var
```

and 

```
sudo fdisk -l
```

---

### Post by fidamehran on 2008-07-17
> **ukripper said:**
> in terminal use following and paste output here:
```
du -sh /var
```

fida@fida-desktop:~$ du -sh /var
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/spool/cron/atjobs': Permission denied
du: cannot read directory `/var/spool/cron/atspool': Permission denied
du: cannot read directory `/var/spool/cron/crontabs': Permission denied
du: cannot read directory `/var/spool/cups': Permission denied
du: cannot read directory `/var/run/sudo': Permission denied
du: cannot read directory `/var/run/samba/winbindd_privileged': Permission denied
du: cannot read directory `/var/run/cups/certs': Permission denied
du: cannot read directory `/var/cache/system-tools-backends/backup': Permission denied
du: cannot read directory `/var/cache/ldconfig': Permission denied
du: cannot read directory `/var/lib/PolicyKit': Permission denied
du: cannot read directory `/var/lib/gdm': Permission denied
379M	/var



and 

> **ukripper said:**
> ```
sudo fdisk -l
```

fida@fida-desktop:~$ sudo fdisk -l
[sudo] password for fida: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfe8cfe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8393931    7  HPFS/NTFS
/dev/sda2            1046        9728    69746197+   f  W95 Ext'd (LBA)
/dev/sda5            1046        4232    25599546    b  W95 FAT32
/dev/sda6            4233        6845    20988891    b  W95 FAT32
/dev/sda7            6846        9728    23157666    b  W95 FAT32
fida@fida-desktop:~$

---

### Post by fidamehran on 2008-07-17
"Permission Denied"??? Who's PC is this? Mine?

**Additional Information:**
I installed Ubuntu from Windows through Wubi.

---

### Post by Oli1234 on 2008-07-17
Hi,

I have exactly the same problem, and I also install Ubuntu through Wubi !

I don't found any solution yet unfortunately... :(

Olivier

---

### Post by fidamehran on 2008-07-17
I'm not sure using Wubi to install Ubuntu has any relation with this. Just thought needed to tell the doctor about all problems like a good patient. There looks lhke existence of some authority problems.

---

### Post by fidamehran on 2008-07-19
Anybody....? Any help?

---

### Post by ukripper on 2008-07-21
can you do this in terminal :

```
sudo df -h
```

i just want to check space for directories

---

### Post by fidamehran on 2008-07-21
> **ukripper said:**
> can you do this in terminal :

```
sudo df -h
```

i just want to check space for directories

Good to have you back, Dear Ukripper! I thought I'd lost you. Nobody's helping me out on this one. I'm running the OS okay, but the update icon is bugging me, and the fact that I can't solve it.

Anyway,
 Your command brings:

fida@fida-desktop:~$ sudo df -h
[sudo] password for fida: 
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      2.8G  1.5G  1.3G  55% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M   60K  502M   1% /proc/bus/usb
udev                  502M   60K  502M   1% /dev
devshm                502M  164K  502M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
/host/ubuntu/disks/usr.disk
                      3.7G  2.5G  1.1G  72% /usr
fida@fida-desktop:~$ 

-----
Looks like space is ample.

Appreciate your help, and anticipating your reply soon.

(P.S.: I don't get the authority part in one of the previous outputs. Am I not an administrator?)

---

### Post by bumanie on 2008-07-21
I have the same problem. I have put a bug report into launchpad, there was also a report from a kubuntu user re the same issue. Haven't really worried about it as the computer still operates fine on 2.26.18.xxx kernel. May be you should add to the bug report. The more reports they get, the more likely thay are to look at it and fix it.

---

### Post by fidamehran on 2008-07-22
> **bumanie said:**
> I have the same problem. I have put a bug report into launchpad, there was also a report from a kubuntu user re the same issue. Haven't really worried about it as the computer still operates fine on 2.26.18.xxx kernel. May be you should add to the bug report. The more reports they get, the more likely thay are to look at it and fix it.

Thanks a MILLION. I thought I was one of the very very few in the whole world with this problem. I also thought this was an issue a newbie like me could solve with a few alterations. Thanks for helping me with the bug information. I'll send a bug information. In fact I think I already did, the first time the error occurred.

Have a nice day.

---

### Post by fidamehran on 2008-08-31
I installed the 2.6.24-21 kernel on my 2.6.24.19 and then did the amateur thing. Chopped the head off to cure the headache. Uninstalled the 2.6.24-19 kernel from Synaptic. Head chopped, problem solved.

(People with same problem may try the stuff on "[https://bugs.launchpad.net/ubuntu/+bug/254711]("https://bugs.launchpad.net/ubuntu/+bug/254711")"
or
"[https://bugs.launchpad.net/wubi/+bug/252900]("https://bugs.launchpad.net/wubi/+bug/252900")"

Good luck.

---

