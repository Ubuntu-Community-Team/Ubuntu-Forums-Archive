---
title: "The taskbars have gone awol!"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Helged on 2008-05-14
My ubuntu crashed, as usual, and when i logged in again, the taskbars, both the one at the top, and the one at the bottom was gone. I've searched around a bit, and tried some tings,but nothings seems to work...

how can i get the taskbars back? This seriously reduces my effectiveness!

---

### Post by dje on 2008-05-14
Can you press Alt+F2 to get a run dialog, if so try these commands in the run dialog:
```
gnome-panel
```
if that doesn't work try:
```
metacity --replace
```

hope that helps,
dje

---

### Post by Helged on 2008-05-14
Nothing happens when i push alt+f2..

So i have nowhere to write the commands..

---

### Post by dje on 2008-05-14
I think that the quickest way to solve this problem will be to create a new user and copy your files/settings across

Ok push Ctrl+Alt+F1 and login with your username and password
Then do the following:
```
sudo adduser *name*
```
Where name is what the user will be called (ie. login name)
Follow the instructions and 'UNIX password' is just the password of the user

hope that helps,
dje

---

### Post by PartisanEntity on 2008-05-14
And by the way, they are not called taskbars but panels :)

---

### Post by Helged on 2008-05-14
ok, sorry for my lack of knowledge..

how do i copy my settings? And the files that now lies in my homefolder, they will remain untouched?

And there is no other way, but to make a new user? I like the loginname i have now.. :/

---

### Post by dje on 2008-05-14
I helped someone a while back whos panels froze and nothing worked except making a new user
If you don't delete your current user then the home folder won't be deleted
To copy settings open up your current home folder and press Ctrl+H and copy the folders with a . in front (hidden folders) which are named like a program you want the settings for. For example firefox settings are stored in .mozilla. Once you're sure you have all your files and settings you can delete your broken user and change the login name of the new user to match that of the old broken one

hope that helps,
dje

---

### Post by Helged on 2008-05-14
I dont have access to the folders and files, and ubuntu denies me to copy them..

---

### Post by N.N. on 2008-05-14
> **Helged said:**
> I dont have access to the folders and files, and ubuntu denies me to copy them..

I believe you have to add your newly created user to a number of existing groups before you can do that. If you can't gain sudo/root access when logged in as the new user, hit Ctrl+Alt+F1 and login with your original user name and password. Then use the following command to add your newly created user to the appropriate groups: ```
sudo adduser <username> adm,cdrom,audio,dip,video,plugdev,admin,netdev,powerdev
``` where <username> is the name of the new user.

Anyway, if the panels work when logged in as the new user, the problem you have described is probably related to the GNOME settings of the original user. To reset these to the default values, delete (or rename) the following hidden folder which are located in the home directory of your original user, i.e. in /home/<original_user>:

[LIST]
[*].gnome
[*].gnome2
[*].gconf
[*].gconfd
[*].metacity
[/LIST]

You should be able to do this after hitting Ctrl+Alt+F1 and logging in with the user name and password of the original user. Use the following command to rename the folders from the command line: ```
mv ~/.gnome ~/.gnome_old && mv ~/.gnome2 ~/.gnome2_old && mv ~/.gconf ~/.gconf_old && mv ~/.gconfd ~/.gconfd_old && mv ~/.metacity ~/.metacity_old
```

I normally advise deleting these folders, but renaming them should work as well. Once you've renamed them, GNOME should revert the settings of the original user to the default configuration upon next login.

---

### Post by Inxsible on 2008-05-14
You can simply right click on the desktop and select Create Launcher. Type in gnome-terminal as the command and then you will be able to access the terminal.

Once you get to the terminal, you can simply type in```
gnome-panel
```and you should have your panels. You will need to add all the apps to the panels and then save the session.

---

