---
title: "[SOLVED] Cannot delete imported files and folders"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-10-22
Hi,

I just imported (via DVD) to my new Hardy some folders containing files I used in Feisty - documents, images and so on.

I cannot erase those files now, and cannot alter the permissions even though the user is the same...

Please help...

Udi

---

### Post by wardrich on 2008-10-22
You can't even # chmod 777 them?

---

### Post by taseedorf on 2008-10-22
hm....
try
sudo rm filename
to delete
or 
sudo chmod +r

?

---

### Post by Udibuntu on 2008-10-22
Thanks guys, but I'd hate starting rm'ing stuff that is too close to home...I'm not secure enough on paths etc.

Isn't there a GUI based method?

---

### Post by stephanvaningen on 2008-10-22
Suppose the root folder you copied on the system is /home/myname/imported, I'ld suggest the following:

Change the ownership:
 ```
sudo chown -R myname:users /home/myname/imported
```
*Ignore errors of access denied to .gvfs, that's a known bug not resolved yet in 8.04/8.10*

Then change default access to these folders:
 ```
sudo chmod -R 755 /home/myname/imported
```
Or similar:
 ```
sudo chmod -R u=rwx,g=rx,o=rx /home/myname/imported
```

Where 755 means user:7 (read,write,execute), group:5 (read,,execute), others:5 (read,,execute). If you require other access, change it to your needs (*info: man chmod*).

---

### Post by OldGrey on 2008-10-22
If you want a gui method you can try opening a terminal - Alt F2 - and running gksudo nautilus. That will run Nautilus with root permissions, but be very careful what you delete.

---

### Post by stephanvaningen on 2008-10-22
> **Udibuntu said:**
> Thanks guys, but I'd hate starting rm'ing stuff that is too close to home...I'm not secure enough on paths etc.

Isn't there a GUI based method?

Yes, there's a GUI-based method too, **but beware that you will be starting a file manager with root rights which can cause you big problems if clicking on a wrong spot somewhere**:
[LIST]
[*]Right-click the menu-bar in the top-left area of the Gnome screen (Applications,Places,System-part)
[*]Choose option 'Edit Menus'
[*]In the Menus panel, select Accessories
[*]In the right-part of the window click the button 'New Item': a new window with the name 'Launcher properties' appears, enter these fields:
[*]**Type:**Leave it on the default value 'Application'
[*]**Name:**Name it i.e.: "Root file manager" *(without the quotes "")*
[*]**Command:** type "gksu nautilus" *(without the quotes "")*
[*]**Comment:**type "Root file manager (CAUTION)" *(without the quotes "")*
[*]Press close
[/LIST]

If you now go to Applications -> Accessories, you see a new option Root File Manager. When starting it, after a second or two, Ubuntu will ask you to give your password, because 'nautilus' will be started with root privileges.

I repeat: **handle with care!**, but you can do anything you want on files with this window now...

---

### Post by stephanvaningen on 2008-10-22
Sorry, you were a bit quicker than me - duplicate post therefore ;-)
> **OldGrey said:**
> If you want a gui method you can try opening a terminal - Alt F2 - and running gksudo nautilus. That will run Nautilus with root permissions, but be very careful what you delete.

---

### Post by Udibuntu on 2008-10-22
Thank you all.

GUI is important for me in this case since what I want to delete are folders that are named home and udi (I copied them before installing hardy).

I'll see if I can use the terminal method and delete the files from trash, it looks safes than to start pathing in my home partition.

will update, and thanks again all.

---

### Post by Udibuntu on 2008-10-22
> **OldGrey said:**
> If you want a gui method you can try opening a terminal - Alt F2 - and running gksudo nautilus. That will run Nautilus with root permissions, but be very careful what you delete.


Moved folder I want to delete to trash, but got this when tried to look into trash as root - 

> Operation not supported by backend

OK, I'll try rm. what is the correct command if file name is home and it is in the trash? Also, how can I make sure I don't get the above error from files that are in this folder?

---

### Post by Udibuntu on 2008-10-22
Solved.

Used this command:

> rm -rf ~/.local/share/Trash/*

I added sudo to get it done (bypass permission denied messages).

Found it here - [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Thank you all for helping me.

Udi

---

