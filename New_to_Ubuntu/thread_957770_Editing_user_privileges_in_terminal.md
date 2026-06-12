---
title: "Editing user privileges in terminal"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by avalenc on 2008-10-24
So, I'm trying to set up wireless printing through Pharos, and using the tutorial at byui.edu/wireless/linuxprint.htm I managed to get a printer going and identified, and I managed to add a new user so that, in principle, I would be able to print through that user's account.

However, my university uses numeric-only user ids, which it wouldn't let me add.

I looked in the forums and found a thread (long since closed) on creating numeric users in the terminal, which seemed to go alright. But now I need to edit the user privileges for the new numeric-only user (which under the system -->administration -->users and groups menu is greyed-out) so  that that user can actually _do things._ 

All of the options for that user (in the GUI user information box) were unchecked; checking them generates the message that the user is invalid and must consist of a lower-case letter followed by other lower-case letters and numbers.

What's the workaround?

Do I edit user privileges in terminal? How do I do that?

OR is there a way to trick it and _add_ a new alpha-numeric user whose name then gets changed (somehow) to be numeric-only?

Thanks!

---

### Post by beno1990 on 2008-10-24
If the other users (other than your own account) on the users and groups menu are grayed out, you can click unlock and enter the sudo password to enable them.

---

### Post by avalenc on 2008-10-24
Right, I can enter the sudo password when I'm in system -->administration --> users and groups, _but_ I'm using a numeric-only username (so that I can set up wireless printing through pharos through a university-assigned username, and there is no way to have the user name changed to be alpha-numeric.) 

There is another thread somewhere (here: [http://ubuntuforums.org/showthread.php?t=30351&highlight=numeric+user](http://ubuntuforums.org/showthread.php?t=30351&highlight=numeric+user) ) about setting up numeric user names, but there they point out (and I have confirmed this) that it's then impossible to edit the numeric user's privileges through the GUI: it produces an error message _demanding_ a user name beginning wiht a lower-case letter.

So what I need to know how to do is find the config file for users and edit it through CLI. I have no idea where to find it, or what lines to edit (and how to edit them.)

Alternately, to know how to force-change a user name would work, since then I could set up the user that I need to be numeric with an alpha-numeric name and then change the name. But I don't know how to do that either. 

Thanks!

---

### Post by avalenc on 2008-10-28
Um, bump.

But, maybe to phrase more detailed questions:
Where is the config file for user privileges?
What is it called?
What, exactly, would I edit to give a particular user (with a numeric id) administrator privileges?

I remark that I need to edit the user config in CLI and _not_ in GUI because in GUI, it returns an error for numeric users. Or is there a workaround so that it won't return that error anymore?

Thank you!

---

### Post by dracayr on 2008-10-28
there isn't ONE big config file with all the user information in it. to give the user administrative rights (which means, give him the right to sudo), add him to the admin group:```
adduser *username* admin
```

dracayr

---

### Post by Sarmacid on 2008-10-28
I have been able to add numeric users to an Ubuntu machine. To do it, first create the user with any name you want, but a legal name, and set a password for it.```
sudo useradd a1234
sudo passwd a1234
```
You can then modify whatever you want with the GUI. After doing it you must change the username in shadow and passwd```
sudo gedit /etc/passwd
sudo gedit /etc/shadow
```
Look for the line containing the user you created earlier and change it to whatever you want.

I'm not sure what are the consequences of doing this, but so far nothing bad has happened to me :confused:

---

### Post by avalenc on 2008-10-28
Dracayr--

So, is there a different config file for allowing the user to have access to printing?

And Sarmacid--

Do I have to change the home directory somewhere as well from the old to the new user name? And how/where would I do that?

Thanks to both of you! I still haven't tried either solution yet, but I'll post back later.

---

### Post by Sarmacid on 2008-10-29
The home directory would still have the name of the user created into first place, but if you want that to change too, you can modify that into the files I said before and change the folder's name```
mv /home/a1234 /home/1234
```

---

