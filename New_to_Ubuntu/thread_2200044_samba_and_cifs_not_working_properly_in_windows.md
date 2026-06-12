---
title: "samba and cifs not working properly in windows"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by skylab2 on 2014-01-17
Hi, this is my first thread and I'm sorry if I wrote in a wrong section.
I used [this]("http://ubuntuforums.org/showthread.php?t=288534") tutorial to share a CIFS folder in a windows based network.

My smb.conf:
```

[prova]
   comment = Test shared folder
   create mask = 0777
   directory mask = 0777
   browseable = yes
   comment = Public Share
   writeable = yes
   public = yes
   path = /mnt/prova

```

My fstab file:
```

# Shared CIFS folder
//192.168.1.9/prova /mnt/prova/ cifs username=Clemiteck_01,password=XXXXX,uid=skylab,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm,nounix 0 0

```

smbd and nmbd daemons are running and in windows OS I can find prova folder and I can see files and folders in it. Problems come when I copy and paste a generic file in the shared folder. I receive a windows error "Could not find this item

This is no longer located in <xyz remote shared folder>. verify the item's
location and try again."

Another problem is that the folders inside the shared folder are viewed as files instead folder.

How can I solve my problems?

Thank you very much!

Skylab

---

### Post by SeijiSensei on 2014-01-17
What are the permissions on the mount point, /mnt/prova?  Before you mount the share, try setting /mnt/prova to 777 permissions with the command "sudo chmod 777 /mnt/prova".  Does that help?

---

### Post by TheFu on 2014-01-17
What do the samba log files show?  It is possible to turn up the logging level.

---

### Post by skylab2 on 2014-01-17
Hi SeijiSensei, folder /mnt/prova has "777" permissions and owner "userone" as shown below:
```

drwxrwxrwx  2 userone root 4096 gen 17 13:06 prova/

```

Hi TheFu,
/var/log/samba/log.smbd:
```

[2014/01/17 16:16:14,  0] smbd/server.c:1072(main)
  smbd version 3.6.18 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2014/01/17 16:16:14.729326,  0] param/loadparm.c:8004(lp_do_parameter)
  Global parameter log level found in service section!
[2014/01/17 16:16:14.736590,  0] param/loadparm.c:8004(lp_do_parameter)
  Global parameter max log size found in service section!
[2014/01/17 16:16:14.739757,  0] param/loadparm.c:8004(lp_do_parameter)
  Global parameter debug timestamp found in service section!
[2014/01/17 16:16:14.744269,  0] smbd/server.c:1128(main)
  standard input is not a socket, assuming -D option

```

/var/log/samba/log.nmbd:
```

[2014/01/17 16:16:17,  0] nmbd/nmbd.c:66(terminate)
  Got SIGTERM: going down...
[2014/01/17 16:16:17,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.18 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2014/01/17 16:16:17,  0] nmbd/nmbd_nameregister.c:492(register_name)
  register_name: NetBIOS name SKYLAB-VIRTUALBOX is too long. Truncating to SKYLAB-VIRTUALB
[2014/01/17 16:16:17,  0] nmbd/nmbd_nameregister.c:492(register_name)
  register_name: NetBIOS name SKYLAB-VIRTUALBOX is too long. Truncating to SKYLAB-VIRTUALB
[2014/01/17 16:16:17,  0] nmbd/nmbd_nameregister.c:492(register_name)
  register_name: NetBIOS name SKYLAB-VIRTUALBOX is too long. Truncating to SKYLAB-VIRTUALB
[2014/01/17 16:16:41,  0] nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****

  Samba name server SKYLAB-VIRTUALBOX is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.11

  *****

```

No other log files are writed by samba. So I tried to add some lines in my smb.conf file:
```

[prova]
   comment = Directory condivisa di prova
   create mask = 0777
   directory mask = 0777
   browseable = yes
   comment = Public Share
   writeable = yes
   public = yes
   path = /mnt/prova

   #New Lines
   log level = 2                  
   max log size = 50
   debug timestamp = yes

```

and in /var/log/samba/ samba wrote new file named as the remote Windows PC name "log.kay-pc":
```

[2014/01/17 16:20:15.553729,  0] param/loadparm.c:8004(lp_do_parameter)
  Global parameter log level found in service section!
[2014/01/17 16:20:15.559663,  0] param/loadparm.c:8004(lp_do_parameter)
  Global parameter max log size found in service section!
[2014/01/17 16:20:15.559903,  0] param/loadparm.c:8004(lp_do_parameter)
  Global parameter debug timestamp found in service section!

```

Thanks for your replies.

---

### Post by skylab2 on 2014-01-21
Hi,
I tried to mount an usb hard disk and share it with samba and I had no problem with it in Windows. I copied, pasted, renamed and deleted folders and files without any problem.
When I use cifs I can't paste and rename and folders become files.

I don't know if the problem is cifs or windows.

Thank you

Skylab

---

### Post by skylab2 on 2014-01-21
In [this]("http://social.technet.microsoft.com/Forums/windowsserver/en-US/349725b7-868d-47ca-a4b3-fbbe3031ffc3/samba-folder-visibility-issue-windows-2008-r2?forum=winservergen") web site Andrew Hodes says: " [COLOR=#0000cd]*It appears that adding the line 'host  msdfs = no' to the globals section in the smb.conf file resolved the issue.*[/COLOR] " but this not resolve my problem.

Friends, any ideas? [IMG]http://ubuntuforums.org/images/smilies/icon_neutral.gif[/IMG] [IMG]http://ubuntuforums.org/images/smilies/confused.gif[/IMG]

skylab

---

