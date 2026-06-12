---
title: "sharing files over network"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by Bubbelgum on 2015-01-25
i have followed ubuntus guide to get this to work found at
 [HTML]https://help.ubuntu.com/lts/serverguide/samba-fileserver.html[/HTML]

and added my share map to the smb.conf file, the other computer can see the map but not open it. not allowed. 
And at this point i dont know what to do this is what i added to smb.conf 
```
[Filmer]
    comment = Filmer
    path = /Ny_volym/Download/Klara/Film
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```

the problem i can think of is that the hard drive in question is called "Ny volym" and i dont know if there can be a blanck space in path or if i have to writ it as i did "Ny_volym" So i desided to try and change the label of that harddrive whit did not work i read and followed [HTML]http://ubuntuforums.org/showthread.php?t=1113236[/HTML] installing gparted but the option in the menu is grayed out and not klickeble so i dont know what to to there. i did practie on a usb flash drive to see how it worked and it worked great. 

any idé on what iam doing wrong?

---

### Post by mooreted on 2015-01-25
Use quotes:

path = "/Ny volym/Download/Klara/Film"

Or use the Unix designation for a space:

path = /Ny\ volym/Download/Klara/Film

---

### Post by jorge8 on 2015-01-25
Another option is to install webmin: [http://www.webmin.com](http://www.webmin.com)
Webmin provides you with a web UI to configure many system settings... including Samba, NFS, etc.

---

### Post by Bubbelgum on 2015-01-25
> **mooreted said:**
> Use quotes:

path = "/Ny volym/Download/Klara/Film"

Or use the Unix designation for a space:

path = /Ny\ volym/Download/Klara/Film

i have tryed both of em, and none work. The Windows computer say network path not found is it because "ny volym" is a an other harddrive and not the one OS is installed to 
and i have to link mount point or something?

---

### Post by Bubbelgum on 2015-01-25
I did install webadmin 

```
Webmin install complete. You can now login to https://BadHabit:10000/
as root with your root password, or as any user who can use sudo
to run commands as root.
Hanterar utlösare för ureadahead (0.100.0-16) ...


```

i go to the weblogin enter root as username and my password. but it says faild login.

---

### Post by Morbius1 on 2015-01-25
Put your path the way you had it. smb.conf accepts spaces in the path just as you originally wrote it. It doesn't have to be in quotes or have any other escapes.

See if it's a Linux permissions problem along the entire path to the target shared folder - -- now you need quotes:
```
ls -dl "/Ny volym"
```
```
ls -dl "/Ny volym/Download"
```
```
ls -dl "/Ny volym/Download/Klara"
```
```
ls -dl "/Ny volym/Download/Klara/Film"
```

If you followed that goofy tutorial "nobody" has to be able to open every folder along the path. A drwxr-xr-x at "Ny volym", Download, and Klara is enough to do that.

---

### Post by jorge8 on 2015-01-25
Try whichever account you use to configure your system, likely that account has admin permission to use sudo.

---

### Post by Bubbelgum on 2015-01-25
This is ridiculous now they show up and all and works as far as i need to login to open the share. i have set webadmin to allow guest. i have even tryed to login whit the account iam using on ubuntu and nothing works. growing tierd of this. 
all work and no play :mad:

---

### Post by jorge8 on 2015-01-25
How did you install webmin?  I found [this]("http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html") to be the easiest and most reliable way.  You may want to uninstall and purge your current installation first (sudo apt-get remove --purge webmin), then proceed with [their]("http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html") instructions.

Hope this helps!

---

### Post by jorge8 on 2015-01-25
I just looked, and the recent version of webmin is 1.730... so you can use the following steps:

```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python

wget http://sourceforge.net/projects/webadmin/files/webmin/1.730/webmin_1.730_all.deb

sudo dpkg -i webmin_1.730_all.deb
```

---

### Post by Morbius1 on 2015-01-26
We need facts about the partition where the shared folder resides.

Please post the output of the following commands:
```
cat /etc/fstab
```
And just in case we need to fix things post the output of this command as well:
```
sudo blkid -c /dev/null
```

On a hunch I looked at what "Ny volym" means and apparently it means "New Volume" in english? Sounds like a Microsoft thing to me so I'm guessing it's an NTFS partition. It's quite possible given your description of the problem that it's either not being mounted at boot or mounting with permissions inconsistent with how you want your share to work.

---

### Post by Bubbelgum on 2015-01-26
> **jorge8 said:**
> I just looked, and the recent version of webmin is 1.730... so you can use the following steps:

```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python

wget http://sourceforge.net/projects/webadmin/files/webmin/1.730/webmin_1.730_all.deb

sudo dpkg -i webmin_1.730_all.deb
```


This is how i did it, i followd the guide on thier own webpage

---

### Post by Bubbelgum on 2015-01-26
```
christian@BadHabit:/media/christian$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e4791400-2c69-4e4f-b2be-602faba5cdcc /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
christian@BadHabit:/media/christian$ sudo blkid -c /dev/null
/dev/sda2: LABEL="Ny volym" UUID="5C8EA8018EA7D1B6" TYPE="ntfs" 
/dev/sdb1: UUID="e4791400-2c69-4e4f-b2be-602faba5cdcc" TYPE="ext2" 
/dev/sdb5: UUID="76B3Wt-Exws-mu1l-sl7G-52e5-sO8d-9eGJpO" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="d9c96bd0-e84e-498a-97e7-0a8c9a2cb7ac" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="ca611caf-9dcc-4769-b1d5-7849fc188fb1" TYPE="swap" 


```

Ubuntu cant even open it&#347; own share thrue netwrok, when i klick browse network and the on the cubuntu computer i can see the share but i cant open it faild to mount: no access

---

### Post by Morbius1 on 2015-01-26
As far as I can make out you are not automounting the NTFS partition.

Based on the blkid command:
> /dev/sda2: LABEL="Ny volym" UUID="5C8EA8018EA7D1B6" TYPE="ntfs" 

*** Create a mount point:
```
sudo mkdir /Data 
```
*** Edit /etc/fstab and add the following line at the bottom of the file:
```
UUID=5C8EA8018EA7D1B6 /Data ntfs defaults,nls=utf8,umask=000,uid=1000 0 0
```
*** Save fstab

*** [COLOR=#0000cd]The only thing I don't know right now is if you manually mounted or mounted the partition through nautilus. If you did then unmount it.
[/COLOR]
*** Then run this command to mount the partition with the new fstab instructions:
```
sudo mount -a
```
*** Verify that you can access the mounted partition at /Data

*** Now edit /etc/samba/smb.conf and change your share definition to this:
> [Filmer]
    comment = Filmer
    [COLOR=#0000cd]**path = /Data/Download/Klara/Film**[/COLOR]
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
*** Then restart smbd:
```
sudo service smbd restart
```
*** Then access your own share from a terminal this way:
```
nautilus smb://badhabit.local/filmer
```
Can you read / write / whatever the share?

---

