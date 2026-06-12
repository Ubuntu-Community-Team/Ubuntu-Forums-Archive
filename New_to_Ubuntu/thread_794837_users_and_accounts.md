---
title: "users and accounts"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by tone33 on 2008-05-15
So i'm running ubuntu 8.04 and I've created another user for my wife, and want to give her admin priveleges - how do I do that?  I still want to be prompted for password as I am with my root account.

---

### Post by unutbu on 2008-05-15
Go to the gnome panel menu bar.
Click System>Administration>Users and Groups
Click on wife's user name.
Click Properties button.
Click User Privileges tab.
Click 'Administer the system' check box.

---

### Post by Xiong Chiamiov on 2008-05-15
Your account isn't really root - it just has root priviledges sometimes.  It's rather confusing, I know.  If you feel like it, you can read up on it [here]("https://help.ubuntu.com/community/RootSudo").

As for how to change the permissions, I'll have to switch over to Gnome to check, or let someone else tell ya.

---

### Post by tone33 on 2008-05-15
> **unutbu said:**
> Go to the gnome panel menu bar.
Click System>Administration>Users and Groups
Click on wife's user name.
Click Properties button.
Click User Privileges tab.
Click 'Administer the system' check box.

The properties icon is grayed out when i click on her name.

---

### Post by angry_johnnie on 2008-05-15
> **tone33 said:**
> The properties icon is grayed out when i click on her name.

Try Alt+F2 and then 

```
gksu gnome-control-center
```

and then look for users and groups, and try the same steps.

---

### Post by tone33 on 2008-05-15
tried that, but same thing.  and actually, I can't change any privileges for my account, can't add new users, or manage groups.  Although my name is not grayed out. 

There are three user accounts:

Andrea /home/andrea (the wife)
root /root
Tone /home/tone (mine)

Mine is the only one not grayed out.  If I click manage groups all the options are grayed.  This is a clean install and I haven't done anything with users and groups other than add my wifes account.

---

### Post by unutbu on 2008-05-15
What happens if you open a terminal and type

```
gksudo gedit /etc/group
```

Assuming you get a gedit window, go to the line that looks like

```
admin:x:110:tone
```

and change it to
```

admin:x:110:tone,andrea
```

---

### Post by eldragon on 2008-05-15
do it the old fashioned way.

open a terminal and edit /etc/group
search every line where your username is added (except for the one which starts with your username) and add your wife's username next to it separated by a comma.

save.

log out, log in. done

you need sudo privileges to edit that file.

---

### Post by Cadmus on 2008-05-15
This may be a too-British view of sudo to be useful to most new users, but I always think of sudo as 'putting on root's hat', you're still mostly you, but you get treated differently.

---

### Post by gerben1 on 2008-05-15
> **tone33 said:**
> The properties icon is grayed out when i click on her name.

When you are at:
System>Administration>Users and Groups

click on "Unlock" enter your password and continue

---

### Post by sisco311 on 2008-05-15
Editing files can be difficult. Here is a command to add a user to the admin group:
```
sudo addgroup <username-here> admin
```
example:
```
sudo addgroup andrea admin
```

Note:In Hardy click the Unlock button in Users and Groups then follow the above instructions

---

### Post by tone33 on 2008-05-15
> **gerben1 said:**
> When you are at:
System>Administration>Users and Groups

click on "Unlock" enter your password and continue

Hey that worked! Not sure how or why I didn't see or think to click on that big unlock button before - couldn't see the forest for the trees I suppose.  Well i learned some linux user accounts stuff in the process - thanks for all the responses.

---

