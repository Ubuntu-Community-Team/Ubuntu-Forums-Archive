---
title: "Can I just replace the wallpaper file?"
date: 2016-01-26
forum: New to Ubuntu
---

### Post by anotherChris on 2016-01-26
I wanted to change the log-in screen background since Lubuntu 15.10's "purple geodesic" design is so ugly.  There's lots of advice about changing .conf files, etc on the web.  Can I just go into **usr/share/lubuntu/wallpapers/** and change the **1510-lubuntu-default-wallpaper.png** file to a different image with that same name?

---

### Post by Dennis N on 2016-01-26
> **anotherChris said:**
> I wanted to change the log-in screen background since Lubuntu 15.10's "purple geodesic" design is so ugly.  There's lots of advice about changing .conf files, etc on the web.  Can I just go into **usr/share/lubuntu/wallpapers/** and change the **1510-lubuntu-default-wallpaper.png** file to a different image with that same name?

Yes, but I would back up 1510-lubuntu-default-wallpaper.png by copying it to something like 1510-lubuntu-default-wallpaper.png.bak first, then replace the file with the background you want - another .png would be needed.

I am not looking at Lubuntu at the moment, but I also recall there are some symbolic links in there that can be redirected to use a different background image. I will give a look.

---

### Post by toxx on 2016-01-26
The conf file modification to change your login screen bg is very simple

```
sudo nano /etc/lxdm/default.conf
```

```

[display]
...
bg=/usr/share/backgrounds/.../something.png [COLOR=#000000][FONT=Monaco]#modify this line to point to the absolute path of the image file of your choosing[/FONT][/COLOR]

```

---

### Post by Dennis N on 2016-01-26
I looked at Lubuntu 14.04, and see I had changed the greeter (login screen) background by:

Editing [FONT=Courier New]/etc/lightdm/lightdm-gtk-greeter.conf[/FONT] 

and change the default:

[FONT=Courier New]background=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png[/FONT]

to an image of my choice placed in the same folder:

[FONT=Courier New]background=/usr/share/lubuntu/wallpapers/energy-pulse.png[/FONT]

So this is another way. The symbolic link lubuntu-default-wallpaper.png is in the wallpaper folder as I thought, but no need to get into that. This or your idea will work fine.

---

### Post by anotherChris on 2016-01-26
Thanks. I have never changed a .conf file before.  I guess, no time like the present!

I ended up having to do something a little different from suggested.  I'm guess 15.10 is changed since 14.04...

First, I had to install gedit (I thought it came installed...?!).  Then...

```
anotherChris@anotherPC:~$ sudo gedit /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf


** (gedit:10643): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files


(gedit:10643): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
anotherChris@anotherPC:~$ 

```

I don't understand those error messages.  I hope they aren't important!!

Anyhow, the wallpaper was successfully changed.

---

### Post by vasa1 on 2016-01-28
> **anotherChris said:**
> I ended up having to do something a little different from suggested.  I'm guess 15.10 is changed since 14.04...

First, I had to install gedit (I thought it came installed...?!).  Then...

```
anotherChris@anotherPC:~$ sudo gedit /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf


** (gedit:10643): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files


(gedit:10643): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
anotherChris@anotherPC:~$ 

```

I don't understand those error messages.  I hope they aren't important!!

Anyhow, the wallpaper was successfully changed.

1. **Dennis N**'s first suggestion of just replacing the wallpaper png worked for me.
2. Gedit isn't present in Lubuntu as a default. Leafpad is Lubuntu's default GUI text editor. You need to install gedit if you want it. And, if you weren't careful, you'd have pulled in quite a few extras (recommends).
3. When you run a GUI application from a terminal, you may see various messages. If the program works as expected, you can ignore those messages. Check out this answer: [http://askubuntu.com/a/422400](http://askubuntu.com/a/422400). In short, most messages can be ignored by you and me if we aren't developers of the application/theme ;)
4. There's a whole can of worms behind *sudo whichever_graphical_application*. Explaining that and *gksudo* and *pkexec* is beyond me.

---

### Post by Dennis N on 2016-01-28
Adding a bit to vasa1's comments,

In the future, I suggest you spend a little time learning how to use the terminal-based text editor **nano**, especially for a simple text file edit job when you are replacing only a few words. It will make many editing jobs quicker and easier.

[http://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/](http://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/)

Give it a try.

---

