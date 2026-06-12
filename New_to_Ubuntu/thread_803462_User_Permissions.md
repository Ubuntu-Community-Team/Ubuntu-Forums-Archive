---
title: "User Permissions"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by ryanparrish on 2008-05-22
Hello, 

I searched the user forums and I found it in the Ubuntu user guide. Although I did not understand what the user guide was saying. I installed VirtualBox OSE and when I run a Virtual box the program gives me an error that the virtual kernel does not have the correct permissions. When I went to check the permissions the virtualbox user group does have permissions to read and write. Although my user account does not have user permissions and the file is owned by root. Therefore I can not change the permissions on the root file how do I change the permission on root a owned file? 

[IMG]http://farm4.static.flickr.com/3227/2513161483_45d4cd133b_o.png[/IMG]

[IMG]http://farm3.static.flickr.com/2007/2514001100_b0bd83ea9b_o.png[/IMG]

And does anyone know of a good player to play DVD's not all of them will play and I tried VLC it doesn't work but better results then Totem movie player.

---

### Post by shifty_powers on 2008-05-22
```
sudo adduser **your username** vboxusers
```

in a terminal will solve it for you ;)

---

### Post by Maestro23 on 2008-05-22
[http://ubuntuforums.org/showthread.php?t=802946&highlight=virtualbox+permissions](http://ubuntuforums.org/showthread.php?t=802946&highlight=virtualbox+permissions)

---

### Post by alacrityit on 2008-05-22
I haven't used virtualbox myself but you can run anything as root as follows:

sudo <command>
ie: sudo virtualbox

It'll ask you for your password and so long as your a sudoer, which you should be if it's the first user you created on the machine it'll execute as root.

---

### Post by shifty_powers on 2008-05-22
no need to do that, or change permissions.

all he needs to do, as documented by sun, who make virtualbox, is to add himself to the vboxusers group, which will give him the right access...

---

### Post by sisco311 on 2008-05-22
Add your user to the vboxusers group. 
```
sudo usermod -a -G vboxusers **you-user-name**
```Log out and log in or reboot the computer.

Or you can add your user to the group from system->admin->users and groups.

Read[ this ]("https://help.ubuntu.com/community/FilePermissions")about permissions.

---

### Post by pdtpatrick on 2008-05-22
Lol virtual box is quite the program but i probably like vmware better. 

Anyway like the others stated.. first of all, add yourself in the sudoers file then run

sudo usermod -G youruser vboxusers

then run your application

---

### Post by pdtpatrick on 2008-05-22
okay sorry got it backwards -- 

sudo usermod -G vboxusers yourusername

---

### Post by spiderbatdad on 2008-05-22
Dvd playback has some issues regarding digital rights management and restricted formats, therefore isn't included in the default installation. Check out medibuntu:[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by sisco311 on 2008-05-22
> **pdtpatrick said:**
> okay sorry got it backwards -- 

sudo usermod -G vboxusers yourusername

Don't forget the **-a** (append) option from the command.

---

### Post by ryanparrish on 2008-05-22
Thank You for all the answers in such a short amount of time :) you guys are great and so is ubuntu.

---

