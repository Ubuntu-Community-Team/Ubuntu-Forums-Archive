---
title: "VirtualBox won't open any OSes, gives weird error"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by duncan12 on 2012-08-14
I want to run VirtualBox on Ubuntu, it used to work a while ago but I can't remember when or why. However when I double-click on an OS to run, it tries to start - opens a window for the virtual OS, gives the "host key" message, but then 5 seconds later closes the OS window and gives this error:

```
Failed to load VMMR0.ro (VERR_SUPLIB_OWNER_NOT_ROOT)


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
```
If I run it with sudo virtualbox I still get the same problem. I've tried sudo apt-get purge virtualbox then sudo apt-get install virtualbox. I notice during the re-installation I get this amongst all the other output on the console:

```
Setting up virtualbox (4.1.12-dfsg-2ubuntu0.1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules
 * No suitable module for running kernel found                           [fail]
```

Any ideas?
Thanks

---

### Post by NikTh on 2012-08-14
Hi , 
try to remove VirtualBox-OSE and install virtualbox from Oracle's site. I know it is a closed source , but unfortunately some times is better. (and newer version)

```
sudo apt-get purge virtualbox-ose virtualbox-ose-dkms 
sudo apt-get install dkms
``` 
Then go here --> [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) , download the appropriate version and install it with 
```
sudo dpkg -i <package.deb>
``` 
<package.deb> = package name of virtualbox. 

Thanks

---

### Post by duncan12 on 2012-08-15
@NikTh For both virtualbox-ose and virtualbox-ose-dkms I got not installed so not removed, but I just ran sudo apt-get purge virtualbox and it uninstalled, then sudo apt-get install dkms (which it said was already installed). I then downloaded and installed VirtualBox 4.1 from that link you gave.

Unfortunately I still get the same error :(

Thanks though

---

### Post by jemadux on 2012-08-15
or go to [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) and follow the instructions and will work

---

### Post by duncan12 on 2012-08-17
@jemadux I have installed VirtualBox fine, but am getting errors when using it. Is this what you meant?

---

### Post by NikTh on 2012-08-17
Hi , 
I searched your problem (google) and found a lot same problems like yours. It seems specific problem with permissions in /usr/lib/virtualbox. (specific the VMMR0.ro)
VirtualBox complains that this must be a root owner . 
So try to change the owner recursively with below commands
```
sudo chown -R root:root /usr/lib/virtualbox
sudo chmod 4711 /usr/lib/virtualbox/VirtualBox
```Thanks

---

### Post by duncan12 on 2012-08-17
@NikTh Ran those, still getting the same error, both with gksudo virtualbox and just opening it normally :(

Thanks for the ideas though

---

### Post by duncan12 on 2012-08-17
```
ls -ld /usr
drwxr-xr-x  13 2000  513   4096 Apr 19 21:15 /usr
```

[Another post]("http://ubuntuforums.org/showthread.php?t=1857854") in this forum regarding the same error suggests to change this to root:root, but I don't feel comfortable changing the permissions of my entire /usr directory. Should I be?

---

### Post by NikTh on 2012-08-17
Hi , 
give the results of this command 
```
ls -l /usr/lib/virtualbox
``` 

Put the results inside [CODE] tags , by highlighting the output and click the **#** button on message toolbar.
Thanks

---

### Post by duncan12 on 2012-08-17
ls -l /usr/lib/virtualbox
```
total 45708
drwxr-xr-x 2 root root     4096 Aug 15 19:01 components
drwxr-xr-x 2 root root     4096 Jun 21 02:44 ExtensionPacks
-rwxr-xr-x 1 root root   430252 Jun 21 02:44 kchmviewer
-rw-r--r-- 1 root root   112588 Jun 21 02:44 libvboxjxpcom.so
drwxr-xr-x 3 root root     4096 Aug 15 19:01 sdk
-rw-r--r-- 1 root root    18032 Jun 21 02:44 VBoxAuthSimple.so
-rw-r--r-- 1 root root     9612 Jun 21 02:44 VBoxAuth.so
-rwxr-xr-x 1 root root    88120 Jun 21 02:44 VBoxBalloonCtrl
-rw-r--r-- 1 root root    96372 Jun 21 02:44 VBoxDbg.so
-rw-r--r-- 1 root root    18352 Jun 21 02:44 VBoxDD2GC.gc
-rw-r--r-- 1 root root    20084 Jun 21 02:44 VBoxDD2R0.r0
-rw-r--r-- 1 root root   169372 Jun 21 02:44 VBoxDD2.so
-rw-r--r-- 1 root root   151160 Jun 21 02:44 VBoxDDGC.gc
-rw-r--r-- 1 root root   153068 Jun 21 02:44 VBoxDDR0.r0
-rw-r--r-- 1 root root  2425660 Jun 21 02:44 VBoxDD.so
-rw-r--r-- 1 root root   298696 Jun 21 02:44 VBoxDDU.so
-rw-r--r-- 1 root root  2031616 Jun 21 02:42 VBoxEFI32.fd
-rw-r--r-- 1 root root  2031616 Jun 21 02:42 VBoxEFI64.fd
-rwxr-xr-x 1 root root    51192 Jun 21 02:44 VBoxExtPackHelperApp
-rw-r--r-- 1 root root    13744 Jun 21 02:44 VBoxGuestControlSvc.so
-rw-r--r-- 1 root root    26080 Jun 21 02:44 VBoxGuestPropSvc.so
-r-x--x--x 1 root root    26152 Jun 21 02:44 VBoxHeadless
-rw-r--r-- 1 root root    83780 Jun 21 02:44 VBoxHeadless.so
-rw-r--r-- 1 root root    54300 Jun 21 02:44 VBoxKeyboard.so
-rwxr-xr-x 1 root root   764264 Jun 21 02:44 VBoxManage
-r-x--x--x 1 root root     9696 Jun 21 02:44 VBoxNetAdpCtl
-r-x--x--x 1 root root    26148 Jun 21 02:44 VBoxNetDHCP
-rw-r--r-- 1 root root    34348 Jun 21 02:44 VBoxNetDHCP.so
-rw-r--r-- 1 root root   137160 Jun 21 02:44 VBoxOGLhostcrutil.so
-rw-r--r-- 1 root root   137996 Jun 21 02:44 VBoxOGLhosterrorspu.so
-rw-r--r-- 1 root root   121448 Jun 21 02:44 VBoxOGLrenderspu.so
-rw-r--r-- 1 root root   185196 Jun 21 02:44 VBoxPython2_7.so
-rw-r--r-- 1 root root   185192 Jun 21 02:44 VBoxPython.so
-rw-r--r-- 1 root root   613488 Jun 21 02:44 VBoxREM32.so
-rw-r--r-- 1 root root   781424 Jun 21 02:44 VBoxREM64.so
-rw-r--r-- 1 root root    13576 Jun 21 02:44 VBoxREM.so
-rw-r--r-- 1 root root  1138340 Jun 21 02:44 VBoxRT.so
-r-x--x--x 1 root root    26144 Jun 21 02:44 VBoxSDL
-rw-r--r-- 1 root root   153700 Jun 21 02:44 VBoxSDL.so
-rw-r--r-- 1 root root    46676 Jun 21 02:44 VBoxSharedClipboard.so
-rw-r--r-- 1 root root   830376 Jun 21 02:44 VBoxSharedCrOpenGL.so
-rw-r--r-- 1 root root    34320 Jun 21 02:44 VBoxSharedFolders.so
-rwxr-xr-x 1 root root   115296 Mar 10 09:34 vboxshell.py
-rw-r--r-- 1 root root   124951 Aug 15 19:01 vboxshell.pyc
-rwxr-xr-x 1 root root  2357192 Jun 21 02:44 VBoxSVC
-rwxr-xr-x 1 root root    91868 Jun 21 02:44 VBoxTestOGL
-rw-r--r-- 1 root root  1905260 Jun 21 02:44 VBoxVMM.so
-rwxr-xr-x 1 root root 11722028 Jun 21 02:44 vboxwebsrv
-rw-r--r-- 1 root root    30376 Jun 21 02:44 VBoxXPCOMC.so
-rwxr-xr-x 1 root root    26396 Jun 21 02:44 VBoxXPCOMIPCD
-rw-r--r-- 1 root root  1022740 Jun 21 02:44 VBoxXPCOM.so
-rws--x--x 1 root root    26148 Jun 21 02:44 VirtualBox
-rw-r--r-- 1 root root  5288732 Jun 21 02:44 VirtualBox.so
-rw-r--r-- 1 root root   541244 Jun 21 02:44 VMMGC.gc
-rw-r--r-- 1 root root   694324 Jun 21 02:44 VMMR0.r0
-rwxr-xr-x 1 root root  9185516 Jun 21 02:44 webtest

```

---

### Post by NikTh on 2012-08-17
Hi, 
all permissions seems correct (compared with mine output) . 

This error occurs when you try to open VirtualBox , or when you try to load the O.S you created in virtualbox ? 
A solution might be to delete the Virtual Drive , ( 2 VirtualBox files in your home. One is hidden)
but you will lose the OS you created . You must re-create the OS (inside virtualbox). 

I would not recommend to play with entire /usr folder and permissions. 
Thanks

---

### Post by duncan12 on 2012-08-17
> **NikTh said:**
> This error occurs when you try to open VirtualBox , or when you try to load the O.S you created in virtualbox?

When I try to load the OS I created. Have tried many different ISOs, and have tried deleting all the config and disk image files I could find, and starting from scratch. It still gives the error (just after the host key message.)

---

### Post by NikTh on 2012-08-17
Hi , 
ok , as I told you before , I would not suggested to "play" with /usr folder just to make VirtualBox starts. 

You can try another thing. 
Remove completely virtualbox 
```
sudo apt-get purge virtualbox* 
```and remove the config files also .. 
```
rm -r .VirtualBox
```Then go again here --> [https://www.virtualbox.org/wiki/Download_Old_Builds_4_1](https://www.virtualbox.org/wiki/Download_Old_Builds_4_1) and download an older build 4.1.14 (download the appropriate version Architecture and OS) .
Install it again and see if this works. 

If you want give the results of 
```
ls -l /usr/
``` just from curiosity. 
Thanks

---

### Post by duncan12 on 2012-08-17
Yes, I haven't done anything to /usr. Here's the output of those commands (given in the order I ran them):

```
duncan@Duncan-Linux:~$ sudo apt-get purge virtualbox*
[sudo] password for duncan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'virtualbox-dbg' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-x11' for regex 'virtualbox*'
Note, selecting 'virtualbox' for regex 'virtualbox*'
Note, selecting 'virtualbox-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-x11' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-2.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-3.2' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.0' for regex 'virtualbox*'
Note, selecting 'virtualbox-4.1' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-utils' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-additions-iso' for regex 'virtualbox*'
Note, selecting 'virtualbox-dkms' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-additions' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-qt' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-dbg' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-fuse' for regex 'virtualbox*'
Note, selecting 'virtualbox-qt' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-source' for regex 'virtualbox*'
Note, selecting 'virtualbox-fuse' for regex 'virtualbox*'
Note, selecting 'virtualbox-guest-utils' for regex 'virtualbox*'
Note, selecting 'virtualbox-ose-guest-dkms' for regex 'virtualbox*'
Package virtualbox-guest-additions is not installed, so not removed
Package virtualbox-guest-additions-iso is not installed, so not removed
Package virtualbox is not installed, so not removed
Package virtualbox-dbg is not installed, so not removed
Package virtualbox-dkms is not installed, so not removed
Package virtualbox-fuse is not installed, so not removed
Package virtualbox-guest-dkms is not installed, so not removed
Package virtualbox-guest-source is not installed, so not removed
Package virtualbox-guest-utils is not installed, so not removed
Package virtualbox-guest-x11 is not installed, so not removed
Package virtualbox-ose is not installed, so not removed
Package virtualbox-ose-dbg is not installed, so not removed
Package virtualbox-ose-dkms is not installed, so not removed
Package virtualbox-ose-fuse is not installed, so not removed
Package virtualbox-ose-guest-dkms is not installed, so not removed
Package virtualbox-ose-guest-source is not installed, so not removed
Package virtualbox-ose-guest-utils is not installed, so not removed
Package virtualbox-ose-guest-x11 is not installed, so not removed
Package virtualbox-ose-qt is not installed, so not removed
Package virtualbox-ose-source is not installed, so not removed
Package virtualbox-qt is not installed, so not removed
Package virtualbox-source is not installed, so not removed
The following packages will be REMOVED:
  virtualbox-4.0* virtualbox-4.1*
0 upgraded, 0 newly installed, 2 to remove and 12 not upgraded.
After this operation, 129 MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 397617 files and directories currently installed.)
Removing virtualbox-4.0 ...
Purging configuration files for virtualbox-4.0 ...
Removing virtualbox-4.1 ...
WARNING: All config files need .conf: /etc/modprobe.d/dazuko, it will be ignored in a future release.
WARNING: /etc/modprobe.d/dazuko line 2: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/dazuko line 3: ignoring bad line starting with 'modprobe'
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Purging configuration files for virtualbox-4.1 ...
dpkg: warning: while removing virtualbox-4.1, directory '/usr/share/icons/hicolor/20x20/apps' not empty so not removed.
dpkg: warning: while removing virtualbox-4.1, directory '/usr/share/icons/hicolor/20x20/mimetypes' not empty so not removed.
Processing triggers for ureadahead ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
duncan@Duncan-Linux:~$

```

```
duncan@Duncan-Linux:~$ rm .VirtualBox
rm: cannot remove `.VirtualBox': Is a directory
duncan@Duncan-Linux:~$ rm -r .VirtualBox
duncan@Duncan-Linux:~$ 
```

```
duncan@Duncan-Linux:~$ dpkg -i '/home/duncan/Downloads/virtualbox-4.1_4.1.14-77440~Ubuntu~precise_i386.deb'
dpkg: error: requested operation requires superuser privilege
duncan@Duncan-Linux:~$ sudo dpkg -i '/home/duncan/Downloads/virtualbox-4.1_4.1.14-77440~Ubuntu~precise_i386.deb'
Selecting previously unselected package virtualbox-4.1.
(Reading database ... 396874 files and directories currently installed.)
Unpacking virtualbox-4.1 (from .../virtualbox-4.1_4.1.14-77440~Ubuntu~precise_i386.deb) ...
Setting up virtualbox-4.1 (4.1.14-77440~Ubuntu~precise) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
WARNING: All config files need .conf: /etc/modprobe.d/dazuko, it will be ignored in a future release.
WARNING: /etc/modprobe.d/dazuko line 2: ignoring bad line starting with 'modprobe'
WARNING: /etc/modprobe.d/dazuko line 3: ignoring bad line starting with 'modprobe'
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS           [ OK ] 
 * Starting VirtualBox kernel modules                                    [ OK ] 
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-central ...
duncan@Duncan-Linux:~$ 
```

```
duncan@Duncan-Linux:~$ ls -l /usr
total 320
drwxr-xr-x   2 2000  513 110592 Aug 18 08:58 bin
drwxr-xr-x   6 root lp     4096 Apr 19 21:15 Brother
drwxr-xr-x   2 root root   4096 Aug  4 09:39 games
drwxr-xr-x   3 root root   4096 Feb 12  2011 google
drwxr-xr-x   3 root root   4096 Nov 27  2011 i686-linux-gnu
drwxr-xr-x  63 root root  20480 Aug 12 09:31 include
drwxr-xr-x 287 root root 122880 Aug 18 08:58 lib
drwxr-xr-x  14 root root   4096 Feb 20 07:27 local
drwxr-xr-x   2 root root  20480 Aug 17 20:44 sbin
drwxr-xr-x 477 2000  513  20480 Aug 18 08:58 share
drwxrwsr-x  16 root src    4096 Aug 18 08:58 src
duncan@Duncan-Linux:~$
```

Thanks for your help.

---

### Post by duncan12 on 2012-08-17
I am going away now, will get back to you later with if it worked.

---

### Post by androssofer on 2012-08-17
> **duncan12 said:**
> I am going away now, will get back to you later with if it worked.

are you on an HP laptop?

---

### Post by duncan12 on 2012-08-17
> **androssofer said:**
> are you on an HP laptop?

Nope, Acer Aspire 5534.

---

### Post by NikTh on 2012-08-17
Hi , 
what happened with older version of virtualbox ? worked ? 

And what is this file you have.. 
> ```
/etc/modprobe.d/dazuko
``` 
can you provide more info about this file ? 
Thanks

---

### Post by JKyleOKC on 2012-08-17
It seems to be a (currently unmaintained) filesystem. Here's one description of it: [https://help.ubuntu.com/community/DazukoTroubleshooting](https://help.ubuntu.com/community/DazukoTroubleshooting)

I've used VirtualBox for a number of years now, and never heard of the dazuko project before. It apparently has to be installed from source rather than from the repositories, so it's a bit of a mystery how it comes to be on the OP's system...

---

### Post by duncan12 on 2012-08-18
> **NikTh said:**
> And what is this file you have.. 

/etc/modprobe.d/dazuko
 
can you provide more info about this file ? 
Thanks
Here's literally the entire content of that file:

```
install dazuko modprobe -r capability;\
modprobe -i dazuko; \
modprobe -i capability
```

Mystery to me too...

And I can confirm now the forums are back up that after all the commands I ran previously, and after setting up the virtual OSes again, I am still having the same problems :(

Maybe worth noting is the exact behaviour: I do get to the "first run wizard" and the "host key" message, but after I click OK to the "host key" message, the OS immediately closes, and a couple of seconds later the error appears. The next times I run it obviously I don't get the first run wizard, just the host key message, then it closes, then I get the error a couple of seconds later.

---

### Post by NikTh on 2012-08-18
> **duncan12 said:**
> Here's literally the entire content of that file:

```
install dazuko modprobe -r capability;\
modprobe -i dazuko; \
modprobe -i capability
```Mystery to me too...

And I can confirm now the forums are back up that after all the commands I ran previously, and after setting up the virtual OSes again, I am still having the same problems :(

Maybe worth noting is the exact behaviour: I do get to the "first run wizard" and the "host key" message, but after I click OK to the "host key" message, the OS immediately closes, and a couple of seconds later the error appears. The next times I run it obviously I don't get the first run wizard, just the host key message, then it closes, then I get the error a couple of seconds later.
Hi , 
what is the content of this file ? 
```
cat /etc/modprobe.d/dazuko
```is it save to remove it ? (I don't know) 

Maybe is the time to consider to change the permissions is /usr folder ? 
I can see these folders 
```
drwxr-xr-x 477 2000  513  20480 Aug 18 08:58 share 
drwxrwsr-x  16 root src    4096 Aug 18 08:58 src
```and compared with mine 
```
rwxr-xr-x 338 root root 12288 Jul  9 20:49 share
drwxr-xr-x   8 root root  4096 Aug 18 20:27 src
```there is a difference. 

You can do it with your own risk.. I think you know the command (chown) . 
Thanks

p.s : This problem with VirtualBox appeared with any OS ? maybe consider the case of OS's  responsibility ?

---

### Post by duncan12 on 2012-08-18
> **NikTh said:**
> Hi , 
what is the content of this file ? 
```
cat /etc/modprobe.d/dazuko
```is it save to remove it ? (I don't know) 

Maybe is the time to consider to change the permissions is /usr folder ? 

...

You can do it with your own risk.. I think you know the command (chown) . 
Thanks

p.s : This problem with VirtualBox appeared with any OS ? maybe consider the case of OS's  responsibility ?

The content of that file is:
```
install dazuko modprobe -r capability;\
modprobe -i dazuko; \
modprobe -i capability
```

Don't ask me what it does or why it's there :)

Yes it happens with any OS, I've tried lots of them.

Could someone else please also give some advice on permission change - stuff [like this]("http://askubuntu.com/questions/143554/sudo-not-working-after-changing-the-permissions-of-usr-directory") makes me worried and this is a valuable system.

Thanks

---

### Post by JKyleOKC on 2012-08-18
That listing of your /usr directory raises all sorts of red flags with the "2000 513" values for owner and group. Appearance of the numbers instead of user/group names indicates that the user and group do not exist in your system. Additionally, "2000" is a most unlikely user id for any flavor of Ubuntu. Non-system UIDs and GIDs start at 1000 and go up from there one at a time; to reach 2000 you would have to have added a thousand additional users! Similarly, system UID/GID numbering starts at 0 (which is "root") and seldom goes as high as 200.

Does your system have any other users? If so, is it likely that one of them could have been doing unusual things without your knowledge?

When any of my systems show such unlikely happenings, my first thought is to back up all critical data, then nuke the box and reinstall everything from scratch. While all flavors of Linux are much less vulnerable than some more widely used systems, mischief is always a possibility -- and gremlins can cause corruption of files without any human mischief being involved. You describe the system as "valuable" so a good backup needs to be available at all times anyway, before you make any attempt to fix things.

The unknown dazuko package appears to be some sort of file system; it's available in the repositories so is probably not malicious in itself, but I would question how it got into your system since it's definitely NOT part of the standard VirtualBox packages...

---

### Post by NikTh on 2012-08-18
Hi , 
I would suggest same thing but JKyleOKC beat me :) 
Backup your important data and prepare for re-installation. Or first you can try to change the ownership of "infected" folders. 
I totally agree with JKyleOKC's post. 
Thanks

---

### Post by duncan12 on 2012-08-18
> **JKyleOKC said:**
> Does your system have any other users? If so, is it likely that one of them could have been doing unusual things without your knowledge?

Nope, it's my own laptop and I'm the only user account. If there's any way to track down what happened I'd be interested but I presume there isn't.

> **JKyleOKC said:**
> When any of my systems show such unlikely happenings, my first thought is to back up all critical data, then nuke the box and reinstall everything from scratch.

I guess I'll reinstall then. To be honest I should have a while ago so this will help me get around to it :)

After reinstalling I'm pretty sure VirtualBox will work (since it's errors seem related to permissions and here are the weird permissions) so I'll mark it solved.

Thanks for the help everyone!

---

