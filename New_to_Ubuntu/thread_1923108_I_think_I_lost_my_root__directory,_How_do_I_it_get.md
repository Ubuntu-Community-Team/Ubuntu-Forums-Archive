---
title: "I think I lost my root  directory, How do I it get?"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by adnon on 2012-02-09
Ok I think I lost my root directory
now whenever I try to do the update manager, install updates. I get the following error

"E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2: No such file or directory)"

I also can't open up root terminal it sits there for a few seconds like it"s opening up then just disappears. 

I can do a ctrl-alt -F4 and log in but it's to my home directory and I can't seem got get out of it I've tried cd .. and cd / but I always end up in my home directory or the desktop directory. 

I can also open up the regular terminal (windows/user gui like ver) 

but again I'm left at my home or desktop dir.

How do I get to the root and or make a new root directory?  

TIA

---

### Post by shakabra on 2012-02-09
Take a look here. [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/198172](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/198172)
Aloha

---

### Post by adnon on 2012-02-10
Mahalo shakabra, 

when I go to the user groups window I only see KN (me the current login user) and no other users. 

KN properties are set to custom 
KN home directory is set to /home/kn, 
Shell is set to /bin/bash,
Main group is set to kn


should I set KN home directory to /root or do I add a new user called "Root" and set that Root users home address to /root?  

Mahalo Nul Loa

---

### Post by adnon on 2012-02-11
Ok I looked at that bug report and it's not helping me. I've made new users and they have the same error. when I change the home directory from /home/root to /root it seem to change it but later when I go back into the user and group app it reverts back to /home/root

another thing to add to this issue. Before this stated to happen. I thought I had a directory called "root", it was a folder with a small x in it that I could not access cause it said I didn't have permissions to it, I also have a folder call lost+found with the same properties, but now I no longer see that "root" folder with the small x on it. 

any help please? my updates are backing up big time

---

### Post by cryptotheslow on 2012-02-11
I'm not sure if it is even possible - but maybe you deleted the user "root". Or inadvertently moved its home directory from /root to /home/root (which is the symptom of that bug highlighted earlier).

Can you paste up the output to the command:
```
cat /etc/passwd | grep root
```and also

```
ls /home
```

---

### Post by adnon on 2012-02-12
hi cryptotheslow


after I ran the first command you wanted it reports

kn@kn-desktop:~$ cat /etc/passwd | grep root
root:x:0:0:root:/root:/bin/bash
roo:x:1002:1002:root,,,,:/home/roo:/bin/bash
kn@kn-desktop:~$ 

and the second command 

kn@kn-desktop:~$ ls /home
kn  roo  user
kn@kn-desktop:~$ 

note I made a user call "root" which said some thing about giving it a short name call roo 
also I didn't make that user "root" till after I posted my question to shakabra above

thks in adv

---

### Post by adnon on 2012-02-12
that's weird 
when I posted the above it didn't have any smiley faces
so for  
root:x:0:0:root:/bin/bash

substitute (both lines)

root colon x colon 0 colon 0 colon root colon/root colon/bin/bash
roo colon x colon 1002 colon 1002 colon root....colon/home/roo colon/bin/bash

somehow colon x seems to make a sad smiley face (kind of ironic since I'm sad that my pc is acting this way) 


:x :x

one of these days I'll know this stuff and why (just hope I live that long)

---

### Post by coffeecat on 2012-02-12
> **adnon said:**
> that's werid 
ahen I posted the above it didn have any smily faces

Click on "Disable smilies in text" under additional options below the message field before you post, or use [noparse][noparse][/noparse][/noparse] tags to prevent the forum software parsing the text - see the link about BBCode in my sig.

Without noparse tags - :x

With noparse tags - [noparse]:x[/noparse]

---

### Post by cryptotheslow on 2012-02-12
OK - so the root user still exists and expects its home directory to be at /root  -  which you have said no longer exists.

Can you paste up the output to
```
ls -al /
```So we can be sure it has been deleted or moved - rather than just hidden.

Also these two commands:
```
sudo updatedb
locate /root

```

If it really isn't there then we should be able to recreate it.

---

### Post by adnon on 2012-02-13
here it it Cryptotheslow

kn@kn-desktop:~$ ls -al /
total 100
drwxr-xr-x  21 root root  4096 2012-02-06 19:52 .
drwxr-xr-x  21 root root  4096 2012-02-06 19:52 ..
drwxr-xr-x   2 root root  4096 2012-02-01 07:36 bin
drwxr-xr-x   3 root root  4096 2012-01-24 07:35 boot
drwxr-xr-x   2 root root  4096 2010-07-11 06:24 cdrom
drwxr-xr-x  17 root root  4500 2012-02-12 23:12 dev
drwxr-xr-x 142 root root 12288 2012-02-12 23:12 etc
drwxr-xr-x   5 root root  4096 2012-02-11 08:30 home
lrwxrwxrwx   1 root root    33 2012-01-24 07:35 initrd.img -> boot/initrd.img-2.6.32-38-generic
lrwxrwxrwx   1 root root    33 2011-12-19 19:28 initrd.img.old -> boot/initrd.img-2.6.32-37-generic
drwxr-xr-x  21 root root 12288 2011-12-15 07:22 lib
drwx------   2 root root 16384 2010-07-11 06:09 lost+found
drwxr-xr-x   4 root root  4096 2012-02-12 23:12 media
drwxr-xr-x   2 root root  4096 2010-04-23 03:11 mnt
drwxr-xr-x   2 root root  4096 2010-04-29 05:17 opt
dr-xr-xr-x 191 root root     0 2012-02-12 15:11 proc
drwxr-xr-x   2 root root  4096 2012-02-01 07:36 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 13:55 selinux
drwxr-xr-x   2 root root  4096 2010-04-29 05:17 srv
drwxr-xr-x  12 root root     0 2012-02-12 15:11 sys
drwxrwxrwt  15 root root  4096 2012-02-12 23:13 tmp
drwxr-xr-x  12 root root  4096 2010-07-10 22:09 usr
drwxr-xr-x  15 root root  4096 2010-04-29 05:26 var
lrwxrwxrwx   1 root root    30 2012-01-24 07:35 vmlinuz -> boot/vmlinuz-2.6.32-38-generic
lrwxrwxrwx   1 root root    30 2011-12-19 19:28 vmlinuz.old -> boot/vmlinuz-2.6.32-37-generic


and the next 2 (it's a long one)
kn@kn-desktop:~$ sudo updatedb
[sudo] password for kn: 
locate /root
kn@kn-desktop:~$ locate /root
/home/kn/.local/share/gvfs-metadata/root
/home/kn/.local/share/gvfs-metadata/root-40654128.log
/usr/include/X11/bitmaps/root_weave
/usr/lib/openoffice/basis3.2/program/root3.dat
/usr/lib/openoffice/basis3.2/program/root4.dat
/usr/lib/openoffice/basis3.2/program/root5.dat
/usr/lib/pymodules/python2.6/wadllib/tests/data/root.json
/usr/lib/python2.6/dist-packages/twisted/names/root.py
/usr/lib/python2.6/dist-packages/twisted/names/root.pyc
/usr/lib/python2.6/dist-packages/twisted/python/roots.py
/usr/lib/python2.6/dist-packages/twisted/python/roots.pyc
/usr/sbin/rootflags
/usr/share/app-install/desktop/root-system-bin.desktop
/usr/share/app-install/desktop/rootstock.desktop
/usr/share/app-install/icons/root-system-bin.png
/usr/share/app-install/icons/rootstock_64.png
/usr/share/apps/ksgmltools2/docbook/xsl/params/root.filename.xml
/usr/share/apps/ksgmltools2/docbook/xsl/params/root.properties.xml
/usr/share/apps/ksgmltools2/docbook/xsl/params/rootid.xml
/usr/share/doc/python-mako/examples/wsgi/templates/root.html
/usr/share/doc/python-twisted-web/examples/rootscript.py
/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/root.filename.xml
/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/root.properties.xml
/usr/share/kde4/apps/ksgmltools2/docbook/xsl/params/rootid.xml
/usr/share/man/man8/rootflags.8.gz
/usr/share/pyshared/twisted/names/root.py
/usr/share/pyshared/twisted/python/roots.py
/usr/share/pyshared/wadllib/tests/data/root.json
/usr/share/recovery-mode/options/root
/usr/src/linux-headers-2.6.32-21/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-21-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-21-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-21-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-21-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-21-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-23/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-23-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-23-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-23-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-23-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-23-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-24/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-24-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-24-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-24-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-24-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-24-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-25/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-25-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-25-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-25-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-25-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-25-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-26/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-26-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-26-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-26-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-26-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-26-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-27/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-27-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-27-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-27-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-27-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-27-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-28/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-28-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-28-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-28-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-28-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-28-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-29/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-29-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-29-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-29-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-29-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-29-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-30/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-30-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-30-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-30-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-30-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-30-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-31/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-31-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-31-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-31-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-31-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-32/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-32-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-32-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-32-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-32-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-32-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-33/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-33-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-33-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-33-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-33-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-33-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-34/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-34-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-34-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-34-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-34-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-34-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-35/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-35-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-35-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-35-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-35-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-35-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-36/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-36-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-36-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-36-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-36-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-36-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-37/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-37-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-37-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-37-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-37-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-37-generic/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-38/include/linux/root_dev.h
/usr/src/linux-headers-2.6.32-38-generic/include/config/eisa/virtual/root.h
/usr/src/linux-headers-2.6.32-38-generic/include/config/usb/ehci/root
/usr/src/linux-headers-2.6.32-38-generic/include/config/usb/ehci/root/hub
/usr/src/linux-headers-2.6.32-38-generic/include/config/usb/ehci/root/hub/tt.h
/usr/src/linux-headers-2.6.32-38-generic/include/linux/root_dev.h


So from what I gather I did deleted the "/root" directory ? 
how could I have done that if I couldn't even open it up originally?  
TKS Cryptotheslow 

OBTW thanks coffeecat for the smiley face tip

---

