---
title: "HOWTO: Windows-y Start Menu on panel"
date: 2006-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by escape on 2006-04-07
**What it is**
If you really miss Windows, and miss the iconic start menu on the bottom left corner of the screen, then this is for you. I basically made an icon to replace the Main Menu applet with something that looks more like the Windows start menu, but with an ubuntu-y feel. Note this doesn't change the content of the menu itself, just the picture for it.

Disclaimer: If you have a panel > ~25 pixels tall, or you don't keep your main menu on the bottom left corner, it might look a bit weird. Here's a preview:

[img]http://ubuntuforums.org/gallery/files/6/3/1/4/5/distributor-logo.png[/img]

**How to install it:**
```
wget http://ubuntuforums.org/gallery/files/6/3/1/4/5/distributor-logo.png
cd /usr/share/icons/hicolor/48x48/apps/ 
sudo cp distributor-logo.png distributor-logo.old.png
sudo cp ~/distributor-logo.png .
rm -f ~/distributor-logo.png
killall gnome-panel
```
FYI, The old picture is backed up as distributor-logo.old.png in the /usr/share.../apps/ directory if you want to change it back. Also, any time ubuntu-artwork is updated, you will have to redo this. I'm experimenting with chmod'ing the file to no write permissions to anyone, assuming it doesn't bork the ubuntu-artwork installation.


**Alternate Option - less "permanent"**
Go to gconf-editor, apps, panel, objects, menu. Change the setting so it uses a custom icon, and set the path of the custom icon to be wherever the custom icon is. As a side note, this doesn't work for me, thus I've posted what I have above.

---

### Post by GoA on 2006-04-07
Thanks, I love it. :)

---

### Post by mc_bizon on 2006-04-08
Is it possible to change the button only for one user and keep the normal one for others?

---

### Post by escape on 2006-04-08
[QUOTE=mc_bizon]Is it possible to change the button only for one user and keep the normal one for others?[/QUOTE]

I think so. But it's a different process. Go to gconf-editor, apps, panel, objects, menu. Change the setting so it uses a custom icon. Set the path of the custom icon to be wherever the custom icon is; don't copy the custom icon into the /usr/share/icons/hicolor... etc directory. This might still be all users, but there's a chance it will work for one user.

---

### Post by benplaut on 2006-04-09
this should really be done as to change the gconf key, instead.

it's cleaner, isn't permanent, and is per user.

`man gconf`

---

### Post by escape on 2006-04-10
[QUOTE=benplaut]this should really be done as to change the gconf key, instead.

it's cleaner, isn't permanent, and is per user.

`man gconf`[/QUOTE]

I'm aware of that option, as I posted in my reply, but I can't get it to work on my system; that is, it still shows the default picture :confused: . Thus the impetus for posting what I did. I have, though, because of what you said, added my reply to the original post.

---

### Post by mc_bizon on 2006-04-11
[QUOTE=escape]I think so. But it's a different process. Go to gconf-editor, apps, panel, objects, menu. Change the setting so it uses a custom icon. Set the path of the custom icon to be wherever the custom icon is; don't copy the custom icon into the /usr/share/icons/hicolor... etc directory. This might still be all users, but there's a chance it will work for one user.[/QUOTE]
thank you

---

### Post by benplaut on 2006-04-11
there's also a boolean that tells it to use the custom icon. It's in the same dir

---

### Post by Don_Toni on 2006-04-12
How can I remove it?

---

### Post by mc_bizon on 2006-04-15
here is a picture that looks more windows-y

---

### Post by GoA on 2006-04-17
I also have problem with this. I decided to go back with the old one because it also vhanged the menu bar icon. However, even if I removed the one you made, renamed the backed up version to distributor-logo.png, it doesn't affect on menubar. Main menu icon has changed but not the menubar. I have tried to reinstall ubuntu-artwork and do a lot of killall gnome-panel but nada. Any suggestions?

---

### Post by BobSongs on 2006-05-16
hehehe

Thought I'd contribute this.

BTW: it's 30 pixels high. And it's a .png so the right edge is rounded (transparent).

---

