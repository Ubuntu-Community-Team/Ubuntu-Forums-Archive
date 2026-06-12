---
title: "Install sidebar"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by CrossS on 2008-06-23
Hi

I'm trying to install sidebar's from

[http://gnome-look.org/?xcontentmode=6700]("http://gnome-look.org/?xcontentmode=6700")

But I don't know how to install downloaded .bz2 files :/

---

### Post by Duck2006 on 2008-06-23
This may help.

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by CrossS on 2008-06-23
> **Duck2006 said:**
> This may help.

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

didn't get './configure' or 'make' to work

trying to install this:
[http://gnome-look.org/content/show.php/Sidebar+Screenlet+(with+docking)?content=63172]("http://gnome-look.org/content/show.php/Sidebar+Screenlet+(with+docking)?content=63172")

---

### Post by Troll_the_Great on 2008-06-23
This link could be useful to:[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by the_doc on 2008-06-23
> **CrossS said:**
> didn't get './configure' or 'make' to work

trying to install this:
[http://gnome-look.org/content/show.php/Sidebar+Screenlet+(with+docking)?content=63172]("http://gnome-look.org/content/show.php/Sidebar+Screenlet+(with+docking)?content=63172")

I'm not sure which version you are trying to download, but isn't there a python script you have to run?  Can you list the contents of the extracted directory?

---

### Post by CrossS on 2008-06-23
> **the_doc said:**
> I'm not sure which version you are trying to download, but isn't there a python script you have to run?  Can you list the contents of the extracted directory?

menu.xml
SidebarScreenlet.py
icon.png
SidebarScreenlet_backup.py
startup     (directory)
themes      (directory)

---

### Post by the_doc on 2008-06-23
Have you got a ~/.screenlets directory, try dropping it in there.

---

### Post by CrossS on 2008-06-23
> **the_doc said:**
> Have you got a ~/.screenlets directory, try dropping it in there.

I don't know what you mean.. sorry. I'm a complete noob :S

---

### Post by Duck2006 on 2008-06-23
Did you cd to where this file you download was and then run the ./configure

cd ~/Desktop

the extract it and cd ~/Desktop/<name for folder>.

then run the commands.

---

### Post by the_doc on 2008-06-23
> **Duck2006 said:**
> Did you cd to where this file you download was and then run the ./configure

cd ~/Desktop

the extract it and cd ~/Desktop/<name for folder>.

then run the commands.

It isn't source code, more like a theme directory.

Try this.

[http://www.screenlets.org/index.php/FAQ#How_do_I_install_new_Screenlets.3F]("http://www.screenlets.org/index.php/FAQ#How_do_I_install_new_Screenlets.3F")

---

### Post by Duck2006 on 2008-06-23
> It isn't source code, more like a theme directory.

Then don't you just drop it in to the theme folder?

---

### Post by the_doc on 2008-06-23
More or less.  According to the FAQ:

> You need to copy the Screenlet's directories to either your ~/.screenlets directory (if it doesn't exists, just create it) or to /usr/local/share/screenlets (for system-wide access).

---

### Post by CrossS on 2008-06-23
I'm in the right directory Duck2006..

I don't have screenlets installed. So I haven't got System - Preferences - Screenlets

---

### Post by the_doc on 2008-06-23
Then I guess you need to install it!

[http://www.screenlets.org/index.php/FAQ#Ubuntu_.28Edgy.2F_Feisty.2F_Gutsy.2F_Hardy.29]("http://www.screenlets.org/index.php/FAQ#Ubuntu_.28Edgy.2F_Feisty.2F_Gutsy.2F_Hardy.29")

---

### Post by phoenix_abhi on 2008-06-23
Install screenlets first. from its manager u can add new widgets

---

### Post by CrossS on 2008-06-23
Think I have installed it but I'm not sure :S 
It still ain't in System - Preferences - Screenlets

---

### Post by Duck2006 on 2008-06-23
If it install write it will be there.
I used Synaptic Package Manager to install it.

---

### Post by the_doc on 2008-06-23
Do you have a screenlets directory in your home directory?


EDIT:

Sorry, I meant .screenlets.  You may have to go to **View** > **Show Hidden Files**.

---

### Post by CrossS on 2008-06-23
> **the_doc said:**
> Do you have a screenlets directory in your home directory?

No. 
Trying to reboot..

---

### Post by CrossS on 2008-06-23
I used Synaptic Package Manager to install it, and now I have rebooted but it still ain't in System - Preferences - Screenlets
and I haven't got a .screenlets directory in my home directory, but I can create one :/


But now it's getting late and I'm going on vacation tomorrow so I have to resume this when I'm coming back.

sorry for all the trouble and for being a complete noob :(


Thx for all your help!

---

### Post by Duck2006 on 2008-06-23
> **CrossS said:**
> I used Synaptic Package Manager to install it, and now I have rebooted but it still ain't in System - Preferences - Screenlets
and I haven't got a .screenlets directory in my home directory, but I can create one :/

You set up the folder when you run it for the first time.

---

### Post by the_doc on 2008-06-23
Sorry it didn't work out.  Post again when you get back and we'll get you sorted out!

---

