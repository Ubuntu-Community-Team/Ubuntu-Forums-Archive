---
title: "?_Make current user a member of Vboxusers Group - USB does not work"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by Rekhillbill on 2013-05-20
Hello,

I have 13.04 upgared from 12.10.

VirtualBox version is 4.2.12 r84980

I successfully installed the Oracle_VM_VirtualBox_Extension_Pack-4.2.12-84980.vbox-extpack.

Another thread says to do the following:

"...
[FONT=Times New Roman]Go to System &#8594; Administration &#8594; Users & Groups. Unlock "Users Settings" then click on “Manage Groups”

Select the “vboxusers” group then click on the “Properties” button. Write down the Group ID number.

Open a terminal and type "gksudo gedit /etc/fstab" (without the quotes). Add the following lines to the end of the file:

     Code:
     
# For USB access with Virtualbox none    /proc/bus/usb    usbfs    devgid=1001,devmode=664    0  0 

IMPORTANT: Replace 1001 with the Group ID number that you wrote down earlier. Save the edited file and exit gedit.
[/FONT]..."

I can open and edit /etc/fstab, BUT I can't find a way to determine my "Group ID #"?

Reference the following:

bill@bill-Satellite-L500D:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:bill
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:bill
floppy:x:25:
tape:x:26:
sudo:x:27:bill
audio:x:29:pulse
dip:x:30:bill
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:bill
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
avahi-autoipd:x:106:
lpadmin:x:107:bill
ssl-cert:x:108:
netdev:x:109:
whoopsie:x:110:
mlocate:x:111:
ssh:x:112:
utempter:x:113:
rtkit:x:114:
bluetooth:x:115:
scanner:x:116:
colord:x:117:
lightdm:x:118:
nopasswdlogin:x:119:
avahi:x:120:
pulse:x:121:
pulse-access:x:122:
saned:x:123:
bill:x:1000:
sambashare:x:124:bill
vboxusers:x:125:
vboxsf:x:126:
bill@bill-Satellite-L500D:~$ 

Also, when I go to "System" in 13.04 I can't find the way to get to "Manage Groups"

If one of the above group is the one to replace 1001, then do I just type in the number, for example ( 4 )?

Any help would be greatly apprecaited.

Thanks,
Bill

---

### Post by Derek Karpinski on 2013-05-20
I've never had to mess with fstab for USB access to vbox.

```
sudo usermod -a -G vboxusers bill
```

will add user 'bill' to the vboxusers group.

You'll have to log out, and back in.

at a terminal you can check which groups user 'bill' is in:

```
groups bill
```

or if you are user 'bill', simply type:

```
groups
```

You may or may not have to install guest additions for USB to work.

---

### Post by ekohardi47 on 2013-05-20
maybe this post can help you to figure it out your vbox group problem. [http://lucidlynxuser.wordpress.com/2013/03/07/solved-ubuntu-12-04-authentification-password-always-failed/](http://lucidlynxuser.wordpress.com/2013/03/07/solved-ubuntu-12-04-authentification-password-always-failed/)

---

### Post by Rekhillbill on 2013-05-21
Derek,

I followed your suggested code and was able to add myself to the vboxusers group.

As you suggested, I needed to to download the following ISO:

VBoxGuestAdditions.iso

This is the Link for the ISO:
 [http://download.virtualbox.org/virtualbox/4.2.12/](http://download.virtualbox.org/virtualbox/4.2.12/)

Reference my original post this is the link for the Virtualbox and the Extension pack:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)  

I burned the ISO to a DVD and this is the terminal output from the VBoxGuestAdditions.iso:

 Code:> Terminal:

 

 Verifying archive integrity... All good. 
 Uncompressing VirtualBox 4.2.12 Guest Additions for Linux............ 
 VirtualBox Guest Additions installer 
 You appear to have a version of the VBoxGuestAdditions software 
 on your system which was installed from a different source or using a 
 different type of installer.  If you installed it from a package from your 
 Linux distribution or if it is a default part of the system then we strongly 

 recommend that you cancel this installation and remove it properly before 
 installing this version.  If this is simply an older or a damaged 
 installation you may safely proceed. 
  
 Do you wish to continue anyway? [yes or no] 
  


I was confused and uncertain as to what to do at this point, considering the above terminal warning ?

But, I decided, since the version of the Guest Additions was the same as the Virtualbox and since they both seemed to come from Oracle, to say YES!

All went OK and I am now able to install a  USB scanner driver in Windows 7 (64bit) running in the VirtualBox with no further issues about the "Group".

Thanks, Derek, for you input, it really helped.

I hope the above helps any one else with the same issues.

Thanks again to everyone who has helped,
Best,
Bill

---

### Post by holycow131415 on 2013-05-21
If you originally installed vb and its additions from the ubuntu software center / repos, then you should uninstall it before installing the vb and additions you downloaded through the website.

---

### Post by Rekhillbill on 2013-05-21
> **holycow131415 said:**
> If you originally installed vb and its additions from the ubuntu software center / repos, then you should uninstall it before installing the vb and additions you downloaded through the website.

holycow131415

Yes.  I forgot to mention this at the beginning.

I had downloaded the VirtualBox originally from the Ubuntu Software Center.

I used the GDebi Package Installer to install Virtualbox-4.2.12-84980~Ubuntu~raring_amd64.deb, after I had used the Ubuntu Software Center to "first" Remove the original Virtualbox.

This removal of the original, did not remove the VirtualBox VMs folder, in the Home folder.

So, I was able to pick up where I left off, after installing the new downloaded version from Oracle, i.e., I did not have to re-install Windows 7.

Thanks,
Best,
Bill

---

### Post by Rekhillbill on 2013-05-21
Another point to note is that I had installed, via Synaptic Package Manager, some x86 headers in an attempt to get the VirtualBox working, that I had originally downloaded from the Ubuntu Software Center.  See the following Thread:

[http://ubuntuforums.org/showthread.php?t=2145757](http://ubuntuforums.org/showthread.php?t=2145757)

GDebi Packager Installer, didn't like the x86 headers and would not proceed.

So, I had to go back to Synaptic Packager Manager and remove them.

Once, I completed the removal, I had no further installation issues with Virtualbox version 4.2.12 r84980

Best,
Bill

---

