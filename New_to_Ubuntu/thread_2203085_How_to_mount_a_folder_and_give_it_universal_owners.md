---
title: "How to mount a folder and give it universal ownership/permissions?"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by daner2 on 2014-02-01
I am trying to run Ubuntu 12.04 in a Virtual Box vm (Host is windows 7) and I have a shared folder at /media/sf_data.

This is a followup to an issue I first tried to address here: [http://ubuntuforums.org/showthread.php?t=2202446](http://ubuntuforums.org/showthread.php?t=2202446)

I need to give MySQL ownership of sf_data. I don't know how to do this - I couldn't do it by right clicking on the folder and changing ownership to MySQL. The gui wouldn't let me, for whatever reason.

Can someone tell me the command to do so? Better yet, if there is a command to give ownership and permissions of the file to everything. I'm more than little lost on the command line... I think I need to change the fstab file or whatever folder tells Ubuntu to mount the folder on boot and tell it to also mount it with certain ownership or permissions. (This is just a dev environment and everything is backed up 3x over so I am not very worried about security.)

---

### Post by bab1 on 2014-02-01
> **daner2 said:**
> I am trying to run Ubuntu 12.04 in a Virtual Box vm (Host is windows 7) and I have a shared folder at /media/sf_data.

This is a followup to an issue I first tried to address here: [http://ubuntuforums.org/showthread.php?t=2202446](http://ubuntuforums.org/showthread.php?t=2202446)

I need to give MySQL ownership of sf_data. I don't know how to do this - I couldn't do it by right clicking on the folder and changing ownership to MySQL. The gui wouldn't let me, for whatever reason.

Can someone tell me the command to do so? Better yet, if there is a command to give ownership and permissions of the file to everything. I'm more than little lost on the command line... I think I need to change the fstab file or whatever folder tells Ubuntu to mount the folder on boot and tell it to also mount it with certain ownership or permissions. (This is just a dev environment and everything is backed up 3x over so I am not very worried about security.)
What you are trying to do requires root user permissions.  Therefore you can't easily do this using your login GUI file manager.  The terminal (CLI) is more precise for this kind of file or directory manipulation.  Sudo provides root user commands.

The command to change ownership of a file or directory is```
sudo chown <user>:<user>  <file_or_directory>
```...where <var> is replaced with the specific user and file or directory.  

This only changes the ownership.  To change the permissions you need to use ```
sudo chmod <permisiions_mode>  <file_or_directory>
```...the mode can be octal (777) or symbolic (a=rwx).

In addition these only work on the files and directories you modify.  If you want inheritance of these setting with multiple users, you will need to set that also.

---

### Post by Morbius1 on 2014-02-01
Sorry for the interruption but isn't /media/sf_data forced to 770 with ownership set to root and group to vboxsf? I'm not sure changing the permissions of that folder would survive a reboot since VBox mounts it sort of like a samba share. I actually don't know - never tried to change it.

Why not add the mysql user to the vboxsf group:
```
sudo gpasswd -a mysql vboxsf
```
I think you'll need to logout ( of the guest ) and login again for the change to take affect.

---

### Post by bab1 on 2014-02-01
> **Morbius1 said:**
> Sorry for the interruption but isn't /media/sf_data forced to 770 with ownership set to root and group to vboxsf? I'm not sure changing the permissions of that folder would survive a reboot since VBox mounts it sort of like a samba share. I actually don't know - never tried to change it.

Why not add the mysql user to the vboxsf group:
```
sudo gpasswd -a mysql vboxsf
```
I think you'll need to logout ( of the guest ) and login again for the change to take affect.
Heck, I don't know either.  I just responded the OP's question about how to change ownership and permissions on a file.  ;-)

[COLOR="#0000FF"]Edit:  I don't know much about VM's.  Maybe you are better off at answering the OP's *entire* problem.[/COLOR]

---

### Post by steeldriver on 2014-02-01
Another option might be to explicitly mount the share as /var/lib/mysql with the desired UID, GID and masks (as far as possible - given the limitations of the parent filesystem). I haven't tested this thoroughly but it *seems* to work (i.e. the mysql service starts OK after, and I can connect to the server using 'mysql -u root -p mysql'):

1. rename the existing /var/lib/mysql directory

```

sudo service mysql stop

sudo mv /var/lib/mysql /var/lib/mysql_orig

```

2. create the vboxsf share in the normal way, checking the box for Permanent but leaving the box for Auto-mount unchecked

[ATTACH=CONFIG]250008[/ATTACH]

3. edit your /etc/fstab adding

```

mysql    /var/lib/mysql    vboxsf    uid=mysql,gid=mysql,dmode=700,fmode=660,dmask=077,fmask=007    0    0

```

where mysql is the name of the share (folder) from step 2. TBH I'm guessing about the 'dump' and 'pass' fields here. I think this is about as close as you can get to the correct UID, GID, and permission masks given a non-native partition - hopefully it is enough to keep mysqld / apparmor happy.

4. you should now be able to make a new mountpoint and mount the directory there

```

sudo mkdir /var/lib/mysql

sudo mount -a

```

5. finally you can copy the original mysql installation to the new mounted vbox filesystem

```

sudo -i
cp -a /var/lib/mysql_orig/* /var/lib/mysql/
exit

```

If everything proceeds OK, the service should happily restart

```

sudo service mysql start

```

---

