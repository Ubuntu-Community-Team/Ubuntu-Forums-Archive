---
title: "can't delete folder from trash ?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by imT on 2008-05-21
i'm using hardy, and i believe the folder(with files in it) is in /home,
when i try to empty trash nothing happens, when i try to Shift+Delete it gives me <Error removing file: Permission denied> and i can't change them.
another thing, can anyone tell me where the trash is located in /home partition (i have a separate partition for home and i can't find it, it's not under /home or /home/user)?

---

### Post by drs305 on 2008-05-21
In hardy, User trash is in /home/username/.local/share/Trash

Root trash is in  /root/.local/share/Trash

There are usually 2 subfolders in each of these, 'files' and 'info'

---

### Post by aktiwers on 2008-05-21
```
gksudo nautilus /home/USERNAME/.trash
```
Change USERNAME with your ubuntu username.

And then right-click and change permission on the folder in the trash. Change it so your user has rights to do anything, under the "permission" tab.

Now you should be able to empty the trash.

---

### Post by Helgiks on 2008-05-21
> **imT said:**
> i'm using hardy, and i believe the folder(with files in it) is in /home,
when i try to empty trash nothing happens, when i try to Shift+Delete it gives me <Error removing file: Permission denied> and i can't change them.
another thing, can anyone tell me where the trash is located in /home partition (i have a separate partition for home and i can't find it, it's not under /home or /home/user)?

I think it is either in "~/.Trash" or somewhere under "~/.gnome2". Try $ find /home/$USER -type d -name ".Trash"
and you should find it. When you do you can just use "sudo rm -riv PATHTOTRASH" (the i asks question about weather you want to delete or not, and the v is to make it verbose, just for security purposes if someone who doesn't know what it does decides to try it out)

---

### Post by imT on 2008-05-21
> **drs305 said:**
> User trash is in /home/username/.local/share/Trash

Root trash is in  /root/.local/share/Trash

There are usually 2 subfolders in each of these, 'files' and 'info'

thanks, 
i change the permissions from home/username/.local/share/Trash and then Shift+Delete :)
i had no idea that the trash location has changed in hardy .

---

### Post by aktiwers on 2008-05-21
Hey me neither!!

---

### Post by xMoDx on 2008-05-21
> **drs305 said:**
> User trash is in /home/username/.local/share/Trash

Root trash is in  /root/.local/share/Trash

There are usually 2 subfolders in each of these, 'files' and 'info'


thanks this works :)

---

