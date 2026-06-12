---
title: "Howto: Kubuntu - Add to &quot;Menu of Important System Places&quot;"
date: 2007-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by barney_1 on 2007-02-10
Hi All,

I have wanted to have a few of my mounted folders under the "Menu of Important System Places" on my dock for a while now.  Today I decided to figure it out and thought I'd share in case anyone else would like to know how.


Background:  The items in this menu are Whatever.desktop files in the directory /usr/share/apps/systemview.  The order in which these are displayed in the menu is alphabetically by filename, therefore, I used a naming convention with this in mind.

**1.**  Open up a console window, navigate to /usr/share/apps/systemview and list the files in that directory:
```
mike@krusty:~$ cd /usr/share/apps/systemview
mike@krusty:/usr/share/apps/systemview$ ls -l
total 24
-rw-r--r-- 1 root root 1795 2007-02-07 20:01 documents.desktop
-rw-r--r-- 1 root root 1995 2007-02-07 20:01 home.desktop
-rw-r--r-- 1 root root 2069 2007-02-07 20:01 media.desktop
-rw-r--r-- 1 root root 1894 2007-02-07 20:01 remote.desktop
-rw-r--r-- 1 root root 1917 2007-02-07 20:01 users.desktop
mike@krusty:/usr/share/apps/systemview$
```

For some reason the documents.desktop link doesn't show up in my menu, but that doesn't really matter to me.  The important part is that I want to have my links at the bottom of this menu, so I will prefix each with z and a number: z#-filename.desktop.

**2.** Let's create a .desktop file:
```
sudo nano z1-flanders.desktop
```

Here is a simple format for this type of file:
```
[Desktop Entry]
Encoding=UTF-8
Type=Link
URL=/Your_Directory_Here
Name=Name_Shown_On_Menu
Icon=Your_Icon_Path_And_Name_Here

```

For my file I'm linking to a folder called Flanders and using a custom icon for this folder.  Please note, the value in the "Name=" field is what shows up on the menu, not the name of the .desktop file we are creating:
```
[Desktop Entry]
Encoding=UTF-8
Type=Link
URL=/Flanders
Name=Flanders
Icon=/Flanders/My Documents/Icons/Flanders.png

```

Save this file (ctrl-X)

**3.** Let's set the permissions for this file just to make sure they're right:
```
sudo chmod 644 z1-flanders.desktop
```

**4.** Repeat steps 2 and 3 until you have all the links you would like.

Here is my directory list with all of the .desktop files in it:
```
mike@krusty:/usr/share/apps/systemview$ ls -l
total 36
-rw-r--r-- 1 root root 1795 2007-02-07 20:01 documents.desktop
-rw-r--r-- 1 root root 1995 2007-02-07 20:01 home.desktop
-rw-r--r-- 1 root root 2069 2007-02-07 20:01 media.desktop
-rw-r--r-- 1 root root 1894 2007-02-07 20:01 remote.desktop
-rw-r--r-- 1 root root 1917 2007-02-07 20:01 users.desktop
-rw-r--r-- 1 root root  116 2007-02-10 13:54 z1.flanders.desktop
-rw-r--r-- 1 root root  108 2007-02-10 14:23 z2.lenny.desktop
-rw-r--r-- 1 root root  116 2007-02-10 14:24 z3.milhouse.desktop
-rw-r--r-- 1 root root  113 2007-02-10 14:25 z4.skinner.desktop

```

**5.** Log out and back in again to see the changes you have made to this menu.

---

### Post by dancarmon on 2010-07-26
Hey
Great post. This is exactly what I wanted to do; unfortunately for me, I have no such "systemview" folder under /user/share/apps/.
What should I do?

thanks...

---

