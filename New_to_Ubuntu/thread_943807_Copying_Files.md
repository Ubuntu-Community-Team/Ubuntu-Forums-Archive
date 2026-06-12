---
title: "Copying Files"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Tux.Ice on 2008-10-10
OK, i am trying to write a script that copys files found in /home/tuxice/Angela to a flash drive located at a windows machine at smb://angela-desktop/flash%20drive%20angela/ recursively and update modes, so for example a cp command would look like this:

cp -ru "/home/tuxice/Angela" "smb://angela-desktop/flash%20drive%20angela/"

however the above command does not work.

How can i make a script that does this? Is it possible?

---

### Post by newlinux on 2008-10-10
I think you will need to mount the window share. I don't think the smb protocol will work commandline.

---

### Post by aeiah on 2008-10-10
yea im pretty sure the problem lies with smb://. you can always mount / unmount the share within the script too of course. it'll need sudo though, so you'd have to echo your password to the sudo command, which isn't very secure because it means your root password is stored in plaintext within the script

---

### Post by Tux.Ice on 2008-10-10
What would the command be to mount it as /media/afd?

---

### Post by aeiah on 2008-10-10
smbmount //computer/sharename /mnt/point

make sure that the mount point exists first. in your case:
```

sudo mkdir /media/afd

```



 if you need username and password, you can add these to the command

---

