---
title: "Desktop delete"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Newbi on 2008-06-12
I use ubuntu 7.10 (Gutsy gibbon)

I accidentally deleted my desktop folder

Now ubuntu shows my home folder on the desktop and has designated it as a desktop folder

I made a new folder in my home folder as “Desktop”

How do I designate the “Desktop” folder as the default desktop????

---

### Post by Gannon8 on 2008-06-12
I think it would have to do with the directory variables, but I don't know how to edit them.

Deleting the desktop folder makes the desktop display your home folder? Cool!

---

### Post by drs305 on 2008-06-12
> **Newbi said:**
> I use ubuntu 7.10 (Gutsy gibbon)

I accidentally deleted my desktop folder

Now ubuntu shows my home folder on the desktop and has designated it as a desktop folder

I made a new folder in my home folder as &#8220;Desktop&#8221;

How do I designate the &#8220;Desktop&#8221; folder as the default desktop????

Have you looked in your Trash folder to see if your original Desktop is there?  I think in Gutsy the trash was located in ~/.Trash  You might be able to open nautilus and restore it. Before doing this, rename you newly-created Desktop folder to something else (.e.g DesktopX). Don't delete it, as this might just make things more confusing. ;-)

---

### Post by forestpixie on 2008-06-12
Open gconf-editor from Alt+F2

Navigate to Apps > Nautilus > Preferences - in the right hand panel find

desktopo_is_home and disable it I think

---

### Post by Nikitas350 on 2008-06-12
Create a new user called test (Use System--->Administration--->Users and group). Login one time to user "test" and then login to default user. Then run the following commands:

sudo cp -r /home/test/.gconf ~/.gconf
sudo chown -R current_user:current_youruser ~/.gconf

(replace the courrent_user with the username you use) [example "sudo chown -R nikitas:nikitas ~/.gconf" ]

---

### Post by Gallienus on 2008-06-12
I've never been in your situation before, but this might be worth trying:

1) Open the configuration editor by typing 'gconf-editor' into the terminal.

2) Find your way to apps -> nautilus -> preferences.

3) Make sure that the 'desktop_is_home_dir' option is NOT selected.

Good luck, hope it works! :)

Edit: Yikes, just noticed that forestpixie had already suggested this.

---

### Post by Vadi on 2008-06-12
Try using Ubuntu Tweak ([click]("http://ubuntu-tweak.com/")), it has an option to set that.

---

### Post by frodon on 2008-06-12
Duplicate threads merged.

Newbi, please do not open more than one thread for a question.

---

### Post by Newbi on 2008-06-13
Problem Solved

Thanks to everyone above

1. I used Alt+F2 to open &#8220;gconf-editor&#8221; 

2. I navigated to Apps > Nautilius > Desktop and checked &#8220;home folder is desktop&#8221; option.

3. Logged out and went to my administrator account and gave my user also permission to administer the system. Did this by going to in System>Administration>Users and changing preferences for my user ( I need this step , as my administrator account and user account are different).

Gave my user administrative rights.

4. Logged in to my user

5. Created a new Desktop folder in home folder

6. Ran the command &#8220;sudo gedit ~/.config/user-dirs.dirs&#8221; from terminal and scrolled down and edited the line to read: XDG_DESKTOP_DIR="$HOME/Desktop&#8221;. Saved and closed the file.

7. Opened &#8220;gconf-editor&#8221; as above ,  navigated to Apps > Nautilius > Desktop and unchecked &#8220;home folder is desktop&#8221; option

8. Desktop is normally displayed

I logged out to administrator account to change my user&#8217;s permissions (this is for me only). Your desktop shall be normally displayed nonetheless.

Thanks to everyone, especially in a related thread :
ubuntuforums.org/showthread.php?t=581498
Thanks to everyone on that post too.

---

### Post by dinesh2n on 2008-06-13
Running the command “sudo gedit ~/.config/user-dirs.dirs” from terminal and edited the line to read: XDG_DESKTOP_DIR="$HOME/Desktop”. Saved and closed the file
also worked for me 
Thanks you!

---

