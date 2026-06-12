---
title: "Make Dolphin your default file manager in KDE"
date: 2007-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by ThinkBuntu on 2007-06-25
For those on older computers, or who don't need all of Konqueror's features, or who find that their file manager settings in Konqueror interfere with their browser settings (or vice versa), or simply those who want a KDE 4 preview, here's how to substitute the light-weight Dolphin file manager as your file system default over Konqueror.

First, install Dolphin using the command line, Synaptic, or whatever method you prefer.
```
$ sudo apt-get install dolphin
```
should work just fine.

Then, open KControl (or your KDE configuration tool of choice. Using Pardus, mine is Tasma, but all are equal in this respect) and navigate to the **File Associations** setting. It may be under the Desktop section, but again, this depends on how your KDE is set up.

In the main chart, titled **Known Types**, expand the **inode** category. Select **directory**, and under Application Preference Order, click "Add." You only need to add this if you don't already see Dolphin as an option. Here, either type in "dolphin", or navigate to it in your virtual KMenu, under "Known Applications." In my case, Dolphin was in the System menu. It should automatically become your top choice under directory, and if it isn't, click "Move Up" until it is.

If you already had Dolphin in the Application Preference Order menu, simply click "Move Up" until it's your first choice.

Repeat these steps for inode>system_directory as well, and Dolphin will be your default file manager! To revert to using Konqueror as your file manager, simply go back to these menus and move Konqueror to the top, over Dolphin.

---

### Post by Computer-Geek on 2007-06-27
Thanks man!

---

### Post by Ubivetz on 2007-06-27
Thanks for tip, but Konquerror is better for now.

---

### Post by ThinkBuntu on 2007-07-07
Update: In a vanilla KDE, the **File Associations** menu is located in the **Control Center** (or **Settings** menu), under **KDE Components**

---

### Post by rand0m on 2007-07-17
Any way to do this for Gnome?

Nevermind, got it to work by modding [these scripts.]("http://www.psychocats.net/ubuntu/nonautilusplease")

---

### Post by TheWizzard on 2007-11-18
thanks. i used your method to go back to konqueror as the default file browser. 
the file association can be accesed by: /usr/bin/kcontrol

---

### Post by tdm on 2008-03-15
Thanks - That's great.

I use [Pardus]("http://www.pardus.org.tr/eng/") Linux.  :)

---

### Post by theneoindian on 2010-05-10
> **rand0m said:**
> Any way to do this for Gnome?

Nevermind, got it to work by modding [these scripts.]("http://www.psychocats.net/ubuntu/nonautilusplease")

You can do this by changing the file manager in "System Settings"

---

