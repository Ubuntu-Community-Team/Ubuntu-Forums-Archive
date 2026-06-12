---
title: "help with Ubuntu usershare folder"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by wintersnows on 2008-09-11
hiya, I am trying to create a share folder. I have install: sudo apt-get install smb in Terminal. When I right click Sharing Option and ticked on both share this folder, allow others people to write in this folder, it then prompt out a box:

The folder "smb" needs the following extra permissions for sharing to work:

Nautilus need to add some permissions to your folder "smb" in order to share it
- write permission by others
Do you want Nautilus to add these permissions to the folder automatically?

I click add automatically, it gives me error:

net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

I also tried to Emblems tab, ticked share but it doesn't work at all.

could someone tell me how to solve this problem?

Thanks in advanced

---

### Post by wintersnows on 2008-09-11
Is it means I need to create a sharefolder?

I have tried: usersharedir /home/username/Makeusersharedir

but command bash not found.

---

### Post by photek1000 on 2008-09-11
When I had this issue, I believe after clicking the auto option and getting the error, I simpley restarted the machine and logged in and tried again, this time all the permissions were set to allow me to share the folder I wanted to within my /home/user-name area.

---

### Post by wintersnows on 2008-09-11
yes. I tried as your mentioned but I still getting the same problem. What is others method?

---

### Post by superprash2003 on 2008-09-11
there could have been some mistake while initially configuring samba, you normally have to add a samba user to smbusers file.Follow this [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by kylebridge on 2008-09-11
I've been having that problem too.  I'm actually reinstalling Hardy right now because I wanted the partitions set up differently, but as soon as I try that out, I'll let you know if it worked for me.

---

### Post by b0b138 on 2008-09-11
You have to add an smb user

sudo smbpasswd -a username

---

### Post by kylebridge on 2008-09-11
I followed the link above and added the smb user, but when I right-click on a folder and click sharing options I get the message for Nautilus to apply permissions automatically, I click apply, and I get this error-

"'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission Denied You do not have permission to create a usershare.  Ask your administrator to grant you permissions to create a share."

The only way I can get a folder to share is to enable the root account and log on as root.  This is my second day using Ubuntu though, so I'm sure I'm doing something dumb.

---

### Post by wintersnows on 2008-09-11
> **b0b138 said:**
> You have to add an smb user

sudo smbpasswd -a username

I did create a user and do as above. When I comes into: Edit /etc/samba/smb.conf  I got error.

---

### Post by stefanb on 2008-09-11
kylebridge: You should probably logout and login again. This is a reported bug: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/245493](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/245493).

---

### Post by b0b138 on 2008-09-12
go into system/administration/users and groups and make sure youre a member of the sambashare group

---

