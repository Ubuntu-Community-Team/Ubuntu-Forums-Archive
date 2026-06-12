---
title: "Want that all folders and sub-folder created for group be accessible to group members"
date: 2019-01-15
forum: New to Ubuntu
---

### Post by cenriq on 2019-01-15
Hi all,

First post here. Created a File server by installing Ubuntu Server 16.04 and configuring Samba. Added 5 users. One user has "sudo" permission. So far all users have access to their home folder and a shared folder. I created another folder that I would like to be a group share for only two users. I created the group and added the 2 users. Using Webmin's folder manager, I changed the ownership of the required folder to the group and selected "R" to make it recurrsive. However that doesn't seem to be working because whenever either of the 2 group users create sub-folders in the main folder the other user does not have permission to access the sub-folder.

The user that has "sudo" rights is not a member of the 2 member group. I tried to issue this code from terminal: chmod g+s . while inside the required folder but was not allowed because of permission issues.

What I need is that the 2 user group shared folder be fully accessible to the 2 members.

Hope someone understands my problem and can advise. TIA

---

### Post by suzukawa on 2019-01-16
Maybe an entry in fstab using bindfs?

---

### Post by cenriq on 2019-01-21
Thanks for the response. I just had time over the pass weekend to get back to this server. I have solved my initial issue by setting the correct "directory permissions." Did some more reading over the weekend.

Now I have another problem. I had copied some files and folders from a windows machine and placed them in the 2 member group share. Is there a way to easily change the copied directory and files permissions to a certain value, maybe automatically, or I have to do them manually? Surely a lot to do! TIA

---

### Post by Holger_Gehrke on 2019-01-21
You can use 'chown' to set user and group and 'chmod' to set permissions. Both commands accept a flag '-R' or '--recursive' to change subdirectories and the files contained in them. Take a look at the manual pages for both ('man chown' and 'man chmod') for more details.

Holger

---

### Post by cenriq on 2019-01-25
Thanks for replies. The "-R" did the trick. I still had to change a few directories and files manually, but for most part is was done with the "-R".

---

