---
title: "Putting the terminal window on desktop?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by xsabrewulf on 2008-07-17
I use the terminal window a lot


Is there a way I can make the terminal window part of the desktop so I dont have to keep going to open the program up?

---

### Post by iaculallad on 2008-07-17
> **xsabrewulf said:**
> I use the terminal window a lot


Is there a way I can make the terminal window part of the desktop so I dont have to keep going to open the program up?

You mean an easier access to Terminal?

```
sudo apt-get install nautilus-open-terminal
```

From there, you could just right-click on your desktop to access the gnome-terminal.

---

### Post by Canis familiaris on 2008-07-17
Perhaps this may help

[http://ubuntuforums.org/showthread.php?t=860106](http://ubuntuforums.org/showthread.php?t=860106)

---

### Post by era86 on 2008-07-17
Did you want it as a complete wallpaper?  Or did you want just a small section of your desktop?  There was an old tutorial using devilspie that can give you any size terminal in the background.  I'll do some searching.

---

### Post by adobrakic on 2008-07-17
I just use Screenlets.

[http://www.screenlets.org/index.php/Download](http://www.screenlets.org/index.php/Download)

and it'll look like this:

[[IMG]http://img145.imageshack.us/img145/7803/snapshot1hk0.th.png[/IMG]](http://img145.imageshack.us/my.php?image=snapshot1hk0.png)

---

### Post by xsabrewulf on 2008-07-17
Just a part of the desktop

I am a total noob I don't know how to download and install anything.

---

### Post by reddox on 2008-07-17
> **era86 said:**
> Did you want it as a complete wallpaper?  Or did you want just a small section of your desktop?  There was an old tutorial using devilspie that can give you any size terminal in the background.  I'll do some searching.

The link Anurag_panda has this tutorial.

---

### Post by adobrakic on 2008-07-17
> **xsabrewulf said:**
> Just a part of the desktop

I am a total noob I don't know how to download and install anything.

If you want what I posted in my previous post, go to:
System > Admin. > Synaptic Package Manager, and then search for screenlets. Checkmark 'screenlets' and press "apply."

This is the easiet way (for me) to get my terminal on my desktop. I've tried the devilspie tutorial and had no success.

---

### Post by king leoric on 2008-07-17
> **xsabrewulf said:**
> Just a part of the desktop

I am a total noob I don't know how to download and install anything.

do you mean an icon or shorcut for terminal on the desktop? Maybe this will help. Click applications-accesories-then right click terminal, then select add this launcher to desktop. Hope this helps:)

---

### Post by xsabrewulf on 2008-07-17
ok I got screenlets

I don't see the terminal in there so I went to more screenlets and there is terminal and terminals..

which one

---

### Post by Locutus_of_Borg on 2008-07-17
autostart gnome-terminal with a delay

```
touch .terminalstart
echo "!#/bin/bash" >> .terminalstart
echo "sleep 8 && gnome-terminal" >> .terminalstart
chmod +x .terminalstart
```

put .terminalstart into sessions > autostart

then in compiz give it gnome-terminal a fixed window placement plus whatever other options you want (size, opacity, window options, etc.)

---

### Post by Harpoon on 2008-07-17
Another good (and relatively painless) choice is to install tilda.  It is in the repos, and you can simply search for that name in synaptic.  Or, you can run

sudo apt-get install tilda

It has transparency, and you can configure it to suit your purposes.  Try searching for "configure tilda" and you should get plenty of easy to follow instructions.

---

### Post by era86 on 2008-07-17
Here is a somewhat dated tutorial on how to implement a terminal background.  Used it some time ago.

[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop)

---

### Post by cariboo on 2008-07-17
I just right click on the terminal entry in the accessories menu and add the laucher to the to panel.

Jim

---

