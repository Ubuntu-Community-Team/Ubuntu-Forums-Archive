---
title: "Providing NAS function to Windows network"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by fredfillis on 2013-02-03
Hi all,

I've been messing around with Ubuntu for only two weeks, mainly checking out XBMC and Mythtv. I'm going to be doing a DIY NAS pretty soon. I'll be starting off with an SSD as a boot drive and a single 2TB drive as shared storage for up to 3 windows 7 machines. After I get up and running I may add more drives and FlexRaid.

My initial dilemma is how to set up the drive dedicated to storage. I've found though my experiments to date that if I share a folder under Ubuntu and copy a file to that folder using Windows, that no owner is assigned and the file can't be deleted from  Ubuntu. Clearly this is not good for a NAS.

Being a noob, I have no idea how to prepare my dedicated storage drive (format) nor how to set up the share in such a way that all the machines that access the storage will have full access (control) of all files.

So, should the drives be formatted with NTFS and is there a special way to mount / share the drives?

Thanks!

---

### Post by Morbius1 on 2013-02-03
> I've found though my experiments to date that if I share a folder under  Ubuntu and copy a file to that folder using Windows, that no owner is  assigned and the file can't be deleted from  Ubuntu.We really need to see how your shares are set up but it's not that no owner is assigned it's that the user "nobody" has been assigned. "nobody" is an actual user name in Linux and is created by default.

Anyway, if you post the output of the following commands it will help in determining the next course of action:
```
testparm -s
``````
net usershare info --long
```

---

### Post by Paqman on 2013-02-03
> **fredfillis said:**
> 
So, should the drives be formatted with NTFS and is there a special way to mount / share the drives?


If the NAS is a Linux machine it'll be far easier to use a proper Linux filesystem such as Ext4 (Ubuntu's default filesystem). 

When you share a drive over your network the underlying filesystem is unimportant to the client end. As long as the client can handle the protocol used to share it, you're good. In your case you'd be sharing using a Windows protocol (SMB/CIFS) through Samba. The Windows machines would see that as a normal Windows share, while the server itself would be handling a normal Linux filesystem locally. Best of both worlds.

---

### Post by fredfillis on 2013-02-04
> **Paqman said:**
> If the NAS is a Linux machine it'll be far easier to use a proper Linux filesystem such as Ext4 (Ubuntu's default filesystem). 

When you share a drive over your network the underlying filesystem is unimportant to the client end. As long as the client can handle the protocol used to share it, you're good. In your case you'd be sharing using a Windows protocol (SMB/CIFS) through Samba. The Windows machines would see that as a normal Windows share, while the server itself would be handling a normal Linux filesystem locally. Best of both worlds.

Thanks Paqman. Is windows compatibility an issue?  [http://en.wikipedia.org/wiki/Ext4#Compatibility_with_Windows_and_Macintosh](http://en.wikipedia.org/wiki/Ext4#Compatibility_with_Windows_and_Macintosh)

Otherwise, sounds like a plan. So I would install the drives and then format under Ubuntu as Ext4. If I needed to recover data from an Ext4 formatted drive, assume that could only be done under a Linux OS? Which I suppose is no problem given a boot-able usb stick.



And thanks too, Morbius1. I'll give that a shot when I'm in front of the machine shortly.

---

### Post by mastablasta on 2013-02-04
> **fredfillis said:**
> Thanks Paqman. Is windows compatibility an issue? [http://en.wikipedia.org/wiki/Ext4#Compatibility_with_Windows_and_Macintosh](http://en.wikipedia.org/wiki/Ext4#Compatibility_with_Windows_and_Macintosh)
 
 
no. most interent uses linux file systems and as you can see they work just fine and are compatible with other OS...
 
> 
Otherwise, sounds like a plan. So I would install the drives and then format under Ubuntu as Ext4. 

yeah ext 4 should be fine.
> 
If I needed to recover data from an Ext4 formatted drive, assume that could only be done under a Linux OS? Which I suppose is no problem given a boot-able usb stick.

 
exactly. well no problem depends why you need to recover it. i mean if the disk is broken you might need osmehting more than just botoable USB. which is why peopel usually create RAID array. one disk goes bad, you just replace it and data copies on it from the other disk that is still ok.
 
why do you plan the SSD? i mean the server will be always on so what is the benefit of SSD in this case? well unless you have extra money lying arround... you could put the system to USB stick.
 
by the way have a look at O**penMediaVault**. it's debian based and has a nice GUI interface that you access via browser from your windows maschine. it's basically made for NAS and such.
 
other OS with nice GUI interfaces:
**Zentyal** (Ubuntu based, free community edition, more oriented towards small business server)
**ClearOS** (Red Hat based, also more oriented towards bussiness servers, but can also be sued for home)
**Webmin **- this is only GUI you simply install on your Ubuntu server and then you can access it from your windows mashcines.
**FreeNAS** (this one is based on BSD not linux, but it is good, fast and free).

---

### Post by fredfillis on 2013-02-04
> **Morbius1 said:**
> We really need to see how your shares are set up but it's not that no owner is assigned it's that the user "nobody" has been assigned. "nobody" is an actual user name in Linux and is created by default.

Anyway, if you post the output of the following commands it will help in determining the next course of action:
```
testparm -s
``````
net usershare info --long
```

```
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Videos]"
Processing section "[Pictures]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Videos]
    path = /home/ray/Videos
    read only = No
    guest ok = Yes

[Pictures]
    path = /home/ray/Pictures
    read only = No
    guest ok = Yes

[Music]
    path = /home/ray/Music
    read only = No
    guest ok = Yes

``````
net usershare info --long
[Music]
path=/home/ray/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Pictures]
path=/home/ray/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Videos]
path=/home/ray/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

---

### Post by fredfillis on 2013-02-04
Hey thanks for the tips mastablasta. You're right on the SSD, was intended for another build. 

I'll certainly be checking out OpenMediaVault and Webmin at least. My ultimate 
"plan" is to add some more storage and use FlexRaid and possibly some Crashplan for partial backup.

I did have a look at FreeNAS a while back. Yep, it was free. But the possibilities of FlexRaid have sucked me in.

---

### Post by Morbius1 on 2013-02-04
All of your shares allow guest access and all of them point to your home directory.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section under the workgroup line:
```
force user = ray
```Save the file and restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down after a samba restart and then access the share again. The remote user who will come across as "nobody" will be converted to "ray" when he access the share.

[COLOR=Blue]* BTW, you created samba shares using 2 different methods. At the moment their share definitions match so no harm but in the future choose one method or the other.*[/COLOR]

---

### Post by fredfillis on 2013-02-05
> **Morbius1 said:**
> All of your shares allow guest access and all of them point to your home directory.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section under the workgroup line:
```
force user = ray
```Save the file and restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down after a samba restart and then access the share again. The remote user who will come across as "nobody" will be converted to "ray" when he access the share.

[COLOR=Blue]* BTW, you created samba shares using 2 different methods. At the moment their share definitions match so no harm but in the future choose one method or the other.*[/COLOR]

Thanks again Morbius1. Yes, I probably did try two different ways as initially I was having trouble seeing the windows machines from ubuntu. So how could you tell?

---

### Post by Morbius1 on 2013-02-05
> **fredfillis said:**
> Thanks again Morbius1. Yes, I probably did try two different ways as initially I was having trouble seeing the windows machines from ubuntu. So how could you tell?
"testparm -s" shows you what your classic Samba shares look like. They are defined in /etc/samba/smb.conf and one of them is this:
> [Videos]
    path = /home/ray/Videos
    read only = No
    guest ok = Yes"net usershare info --long" shows you all of your Samba usershares which are created via Nautilus. Those shares are defined in /var/lib/samba/usershares and one of them looks like this:
> [Videos]
path=/home/ray/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=yTwo different ways to create a samba share. Two different places where they are defined. Both of them sharing the same directory. At the moment they are defined the same way but in general this is a bad idea. Use one method or the other not both on a given directory.

---

### Post by fredfillis on 2013-02-05
Thanks again Morbius1. Will remember not do that again. 99.999% windows  user so right click and share is probably the way I would go. Having had  a play, I see I can remove the share also by right clicking on the folder and selecting sharing options.

Is there any advantage in creating shares via the Samba Server Config tool over creation via Nautilus?

---

### Post by Morbius1 on 2013-02-05
>  Is there any advantage in creating shares via the Samba Server Config tool over creation via Nautilus?Flexibility.

_Userhshares ( via Nautilus ) Pros:_
** The *right-click > Share this thing* mechanism is nearly identical to creating a "simple share" in WInXP.
** It automatically modifies Linux permissions on the target folder so that it is consistent with the options you selected in setting up the samba share.
** It does all this without restarting the smbd service so changes are more or less immediate.
_Usershare Cons:_
** You are confined to creating Public or Private shares with or without write access.

_Classic Shares Pros:_
** An unbelievable amount of specificity can be applied to the share which can limit who can access, with what privileges, and even from where.
_Classic Shares Cons:_
** Since it is changing smb.conf directly you ( or the app ) must restart the smbd service and in doing so the network has to readjust causing delays in determining if the share definition works.
** Depending on the type of share being created the user might have to make changes outside of smb.conf / or the app to make it work.

An example: You want to create a share of your Videos directory and allow everyone in the LAN to have write access.

[COLOR=Blue]*Classic Samba:*[/COLOR]

You create a share that looks like this:
```
[Videos]
path = /home/morbius/Videos
read only = No
guest ok = yes
```You restart smbd, wait a few minutes, and a remote guest tries to write to the share. What happens - Access Denied. Why? Because the Linux permissions are set at 775 and guests can only read. So you chave to change permissions of the target folder to accomodate a guest write by setting the permissions to 777.

[COLOR=Blue]*Usershares:*[/COLOR]

Right click /home/morbius/Videos, select all the boxes, and it asks you if you want it to modify permissions. Selecting yes changes permissions for you and you are done.

So it's ease of use vs flexibility.

---

### Post by wlraider70 on 2013-02-05
There are lots of options you can use in the smb.conf

[Videos]
    path = /mnt/files
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0666  #create mask: determines the permissions new files will have when created.
    directory mask = 0777
    force user = jimmy


check this out
[https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

---

