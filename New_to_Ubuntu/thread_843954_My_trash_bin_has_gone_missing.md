---
title: "My trash bin has gone missing"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by 89vision on 2008-06-28
This is really strange, I hope somebody can help.  I just got done deleting close to 75 gigs of media files to my trash bin from nautilus.  I do a 'sudo rm -rf /home/myhomedir/.Trash/*' and nothing happens.  Then I noticed my .Trash directory isn't even there!  Now I cant find the 75 gigs of video and music files I deleted and my system is still showing that I still only have 1.4 GB left.  I've googled and can't find any help.  Does anybody have any ideas?

---

### Post by drs305 on 2008-06-28
Run these commands to find your computer's trash folders:
```

sudo find / -type d -iname Trash

```

This will located all the Trash folders. The actual deleted files and folders are in a subfolder named files. If the trash is not owned by you, you can use a "sudo rm" command but it is very dangerous and you could delete system files. 

I prefer to changed the folders so you own them and delete them that way.
```

sudo chown -R username:username /pathto/Trash/Files
rm -r /pathto/Trash/Files

```
You can also track down the trash files with nautilus or another fifle manager. If some of the trash won't delete or you know it is owned by root, open the file manager with gksudo:
```

gksudo nautilus

```


**Added:**
Your trash on ext3 partitions should be in ~/.local/share/Trash/Files
Root's trash should be in /.local/share/Trash/Files
ntfs trash may be called Trash-1000, with the number being the user's uid.

---

### Post by 89vision on 2008-06-28
Thanks for the quick reply!  That first command you gave me worked perfectly.  It looks like they have changed things a little bit in Hardy.  Thanks again!

---

### Post by aktiwers on 2008-06-29
Yeah I guess trash has been moved to:
~/.local/share/Trash

In hardy

---

### Post by LuisGMarine on 2008-06-29
Here's some extra info, in case you like:

Ubuntu-Tweak

Great application to add some nice little "tweaks" to your system.  I'm not 100% sure how to add your Trash Icon on your desktop from a straight installation, but I know that Ubuntu-Tweak has the option to do so.

Install Ubuntu-Tweak by following these steps.

Add the repos to your sources.list, run this command in terminal:
```

sudo gedit /etc/apt/sources.list
```

paste the following at the bottom of the file, save and quit after you are done:

```
#UBUNTU TWEAK
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
```

Next update your sources list with:

```
sudo apt-get update
```

Now you can install and keep ubuntu-tweak to its newest version.

```
sudo apt-get install ubuntu-tweak
```

Once Ubuntu-Tweak is installed, you can access it by going to 


***Applications > System Tools > Ubuntu Tweak***

Once Ubuntu Tweak is up and running you can navigate on the left hand side to:
[I][B]
Desktop > Desktop Icon[/B][/I]

Then click on the Trash icon.  Also make sure that "Show Desktop Icons" button is check, its at the top.



The other option, and the easy one if you ask me.  It's very simple, fire up nautilus and in the address bar just type in:
```

trash:///
```

Viola!

-xkill

---

### Post by 89vision on 2008-06-29
> **LuisGMarine said:**
> 
The other option, and the easy one if you ask me.  It's very simple, fire up nautilus and in the address bar just type in:
```

trash:///
```

Viola!

-xkill

I never knew about that. Thanks!

---

### Post by mcduck on 2008-06-29
Trash bin, just like other desktop icons, can be enabled without installing any extra software. The Configuration Editor is your friend. :)

Press Alt-F2 and run "gconf-editor". Then browse to apps/nautilus/desktop and enable which ever icons you want to show on your desktop (Computer, Home, Network, Trash and mounted volumes). You can also change their names in the same place.

---

### Post by drs305 on 2008-06-29
And then there's always:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"

```

:)

---

### Post by RGPerson on 2009-02-17
> **mcduck said:**
> Trash bin, just like other desktop icons, can be enabled without installing any extra software. The Configuration Editor is your friend. :)

Press Alt-F2 and run "gconf-editor". Then browse to apps/nautilus/desktop and enable which ever icons you want to show on your desktop (Computer, Home, Network, Trash and mounted volumes). You can also change their names in the same place.

Tried this and I still don't have a Trash icon in a panel or on my desktop.

Gabrielle

---

### Post by drs305 on 2009-02-17
> **RGPerson said:**
> Tried this and I still don't have a Trash icon in a panel or on my desktop.

Gabrielle

Here's another thing you can try - reinstalling the app that contains the trash applet and retry setting up the trash icon on the desktop:
```

sudo apt-get update && sudo apt-get install --reinstall gnome-applets
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"

```

---

### Post by Francewhoa on 2009-08-23
Thanks mcduck it works. Same answer with screenshots at [http://ubuntuforums.org/member.php?u=55317](http://ubuntuforums.org/member.php?u=55317)

---

