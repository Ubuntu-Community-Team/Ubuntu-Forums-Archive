---
title: "Live CD question"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by ralphz on 2008-05-31
Hi

When I start form Live CD i get a lot of configuration files in /home/ubuntu user folder. Where are they coming from? I unpack the squash filesystem but i see no files or folders in the /home folder. So those files are created during LiveCD boot process. Can you point me in the right direction how those files are created and what is responsible for it.

Also I don't see any ubuntu user (/etc/password) in squashed file system so I think there are some scripts that create whole user environment and set all the permissions.

What I'm trying to do here is to be able to edit come gnome menus and permissions. 

Can anyone help me with this? I need to prepare this custom cd quick...

Ralph

---

### Post by Rocket2DMn on 2008-05-31
All the configuration files and folders start with a period and are generally hidden unless you do CTRL+H in nautilus (the file browser).  Many programs generate these automatically, then you configure them through use of the program(s).

Password hashes are now stored in /etc/shadow instead of /etc/passwd (you need root privileges to view /etc/shadow).

You can edit the gnome menus by right clicking that area of the panel and hitting Edit Menus.

---

### Post by ralphz on 2008-05-31
Hi

Thanks for replay but I think you did not understand my question. 

I want to customize Ubuntu Live CD. i don't want to start it and do some customization I know how to do it. I want to customize squashed file system from Ubuntu Live CD so every time I start it it has my settings.

So my question is when i unsquash the file /casper/filesystem.squashfs where do I look for scripts that create and populate folder /home/ubuntu when you start from Live CD

Ralph

---

### Post by Rocket2DMn on 2008-05-31
To do this you need to make your own LiveCD with the configurations already in place.  You should have a look here - [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
I've never tried it myself (but maybe I should!), that guide seems fairly in depth.

---

### Post by ralphz on 2008-06-01
Thank you Rocket2DMn.

I went with the tutorial and iso is working. But what files do I edit when I'm in chroot to change the menus in gnome or maybe even restrict the user that runs live CD?


Ralph

---

### Post by Rocket2DMn on 2008-06-01
I've never done this before, but what if you run a chroot from a tty then startx from there.  You should then be editing the configuration of the setup you want to put onto the LiveCD, so you should be able to just right click the panel area and hit Edit Menus.
Digging around configurations seems to show that menu data is stored in ~/.local/share/applications with two files - defaults.list and mimeinfo.cache.  I'm not really sure how these files work though, and they don't appear to help you configure the Places menu or the System menu.

---

### Post by ralphz on 2008-06-01
Hi

I did that but I got bunch of errors and was not able to start GNOME :(

Now I'm trying to get to know initramfs-tools and casper to get to the bottom of the live cd creation. hope i can get some results for Monday presentation :)

---

### Post by LaRoza on 2008-06-01
> **ralphz said:**
> Hi

When I start form Live CD i get a lot of configuration files in /home/ubuntu user folder. Where are they coming from? I unpack the squash filesystem but i see no files or folders in the /home folder. So those files are created during LiveCD boot process. Can you point me in the right direction how those files are created and what is responsible for it.

Also I don't see any ubuntu user (/etc/password) in squashed file system so I think there are some scripts that create whole user environment and set all the permissions.


They are created by the programs starting. For example, if you delete the .mozilla directory (don't do it unless you don't mind losing any custom Firefox settings) and start Firefox, a new one will be created.

The GNOME and other configs are created when the service starts.

---

### Post by nhandler on 2008-06-01
What changes do you want to make to the applications menu? Are you trying to add items to it? If so, the .desktop files (These contain all the information about the menu item) are stored in /usr/share/applications. By modifying the .desktop file, you can change the name shown in the applications menu, the command it executes when you click on it, the icon displayed, and the comment that is shown when you hover over the menu entry.

Also, you might find this [guide]("http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd") helpful. You can also look at [reconstructor]("http://reconstructor.aperantis.com/") or [remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html"). Those apps and the guide should help you create your custom live cd.

---

### Post by Oldsoldier2003 on 2008-06-04
placing the config files in /etc/skel before you build the squashfs filesystem will make customizations to the desktop and menus of the live cd user.

/etc/skel/Desktop for desktop icons and files to be placed on the desktop ...etc

---

### Post by ralphz on 2008-06-04
Thanks for replay.

I will try that today.

Ralph

---

