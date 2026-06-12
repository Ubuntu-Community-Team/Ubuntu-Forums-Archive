---
title: "Konquest in Gnome"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by HieroPosche on 2008-07-23
I've been using slackware 12 for a while, but decided to swap back to Ubuntu since I was having issues getting my BCM4309 working properly. (I used Ubuntu before Slack and never had issues getting the wireless to work)

But one thing I can't do without from KDE is the Konquest. For some reason I just love that game.e proper 

I grabbed it from the Add/Remove Programs list, but it didn't install into the games menu as I expected it to. There is a file in 

```
/usr/share/app-install/desktop
```

and an icon for it in

```
usr/share/app-intall/icons
```

I added a path to the file in the games menu, but recieve message that I don't have permissions to the path. (I also cannot change the icon for the path to the one in the /usr/share/app-install/icons folder as it doesn't seem to recognize any of the many many icons there for some reason...)

I'm not sure if a chmod command to change the permissions on the file would allow me to execute it, but still being somewhat noobish I wanted to find out for sure before I started messing around with permissions.

Any help would be greatly appreciated.

---

### Post by LaRoza on 2008-07-23
Try running it from the command line:

```

konquest

```

If it works, run a:

```

which konquest

```

and make a shortcut to that file.

If it doesn't, post the errors here.

---

### Post by HieroPosche on 2008-07-23
Worked like a charm, thank you.

---

### Post by CurtM on 2010-06-28
> **LaRoza said:**
> Try running it from the command line:

```

konquest

```If it works, run a:

```

which konquest

```and make a shortcut to that file.

If it doesn't, post the errors here.

Hi!  I did part of what you said, but I'm not sure what to do next.  When I try to run Konquest (from the menu), the disc drive runs for a few seconds, but nothing happens.  I don't get any error message.

I took your advice and ran Konquest from a terminal window, and it runs great.  I then typed "which konquest" and got "/usr/games/konquest"

I can't seem to edit the Konquest entry in the menu.  I can right click on Konquest in the menu, and change the properties (command).  I can then click cancel or ok.  I click "ok" but it doesn't save my changes.

I am running Lubuntu 10.04.  Do you know what I should do?  Perhaps I need to be logged in as root?  How do I do that?  Thanks for your help.
CurtM

---

