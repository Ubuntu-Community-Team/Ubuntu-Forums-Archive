---
title: "how to make desktop shortcuts?"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by jcdenton_riseup on 2011-10-02
any input would be much appreciated. I've been browsing the net and playing around for about two hours and still failed.

---

### Post by Rubykuby on 2011-10-02
Go to the folder with the file you want a shortcut to.
Right-click the file.
Press "make link" and a new file will appear in the folder
Cut the new file
Paste it on your desktop

Enjoy!

---

### Post by dcsoldschool53 on 2011-10-02
Another way to do this, is to open a terminal. Type ```
ln -s /path/to/file ~/Desktop
```This will create a shortcut from the file to your Desktop. You can also do this with directories too. 

The first letter in (ln) is a small L, and what I wrote will create a  symbolic link to your file to be placed on Desktop. All you need to do is fill in the path to your document, or directory.

You can also write it out this way too.```
ln -s /home/your user  name/path/to/file /home/your user name/Desktop
```Hope this help you.

---

### Post by Rex Bouwense on 2011-10-02
According to the Lubuntu documentation see here:
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_can_I_create_a_shortcut_on_the_Desktop](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_can_I_create_a_shortcut_on_the_Desktop)

In short the answer is:
How can I create a shortcut on the Desktop

Launch LXTerminal and move to your Desktop directory

lxshortcut -o application_name.desktop

(Of course you will want to change "application_name" to something else).

A dialog will appear and you can choose the name or the icon, set the path to the file. 
Enjoy.:popcorn:

---

### Post by mijdrawoh on 2011-10-02
The simplest way:
Right click on an open area of the desktop
Select "Create launcher"
If application; click "browse"
Drill down to find the file 
Click Open
Give it a name
Click OK
If URL
Copy address
Right click on an open area of the desktop
Select "Create launcher"
Select "Location"
Paste address
Give it a name
Click OK
This will put icons on your desktop.
DM!

---

### Post by kerry_s on 2011-10-02
> **mijdrawoh said:**
> The simplest way:
Right click on an open area of the desktop
Select "Create launcher"
If application; click "browse"
Drill down to find the file 
Click Open
Give it a name
Click OK
If URL
Copy address
Right click on an open area of the desktop
Select "Create launcher"
Select "Location"
Paste address
Give it a name
Click OK
This will put icons on your desktop.
DM!

Never used lubuntu have you?

Just go to /usr/share/applications & copy/paste the app shortcuts you want to the desktop. 
For custom use that lxshortcut command above.

---

### Post by dcsoldschool53 on 2012-01-08
I think this will help. In a terminal, type```
gnome-desktop-item-edit --create-new ~/Desktop
```This will open up the launcher so that you can create a shortcut to your desktop.

---

### Post by kerry_s on 2012-01-08
> **dcsoldschool53 said:**
> I think this will help. In a terminal, type```
gnome-desktop-item-edit --create-new ~/Desktop
```This will open up the launcher so that you can create a shortcut to your desktop.

that works in lubuntu? lubuntu's desktop is done with pcmanfm.

---

### Post by Morbius1 on 2012-01-08
I haven't used LXDE for a while but does this still work:

Install lxshortcut:
```
sudo apt-get install lxshortcut
```Then in a terminal to create a shortcut to ... say... firefox:
```
lxshortcut -o ~/Desktop/firefox2
```This will launch a gui app that will ask for the command and icon you wish to use.

[COLOR=Blue]**EDIT**[/COLOR]: I'm an idiot for not actually reading the entire thread. It seems this was proposed some time ago by [Rex Bouwense]("http://ubuntuforums.org/member.php?u=767164"). Sorry about that.

---

### Post by kerry_s on 2012-01-08
yeah, that will work. no need to install, it's included.
just need to add .desktop to the end of that Firefox

---

