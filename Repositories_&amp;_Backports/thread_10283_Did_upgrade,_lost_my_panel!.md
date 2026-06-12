---
title: "Did upgrade, lost my panel!"
date: 2005-01-06
forum: Repositories &amp; Backports
---

### Post by AndyGates on 2005-01-06
Finally we got broadband, so I tried doing a system upgrade: sudo apt-get upgrade.  It failed at first and suggested that I ran it with a --fix flag (don't remember the exact flag, sorry!).  So I ran it with that flag and it chugged away, ultimately finished, but now on restart I've lost my Gnome panels!

(I can get stuff up with right-clicking the desktop, opening a terminal, and going command-line, but it ain't convenient!)

How can I get my panels back?  What did I do wrong?

---

### Post by labbe on 2005-01-06
I have kind of same problem.
I lost my default upper panel, and made a new one.....
But now, when I'm logging into GAIM, the icon wont come up on the panel anymore,..
Anyone that can help me with getting the default panel back..?

---

### Post by Rancoras on 2005-01-06
I dropped to CLI by pressing CTRL+F1 and issued
```
sudo apt-get install --reinstall gnome-panel
```
Then rebooted.  Not sure what happened to cause it, but that fixed it.

---

### Post by wallijonn on 2005-01-06
Did you enable the Hoary repositories while using Warty? Did you install gDesklets? (see my notes in the gDeslets HOWTO, [http://www.ubuntuforums.org/showthread.php?t=3012&page=6&pp=10](http://www.ubuntuforums.org/showthread.php?t=3012&page=6&pp=10) ). 

You guys may want to list what Ubuntu version you're using in your signatures.

```

apt-get install gnome-panel
apt-get install gnome-core

```

---

### Post by labbe on 2005-01-06
It Didnt Worked for me..but mine problem is that for example Gaim doesnt have an icon in the upper right....
I can make a new panel, but It wont work...

---

### Post by AndyGates on 2005-01-07
[QUOTE=Rancoras]I dropped to CLI by pressing CTRL+F1 and issued
```
sudo apt-get install --reinstall gnome-panel
```
Then rebooted.  Not sure what happened to cause it, but that fixed it.[/QUOTE]
 Rancoras, this worked to get my panel back: thanks!

For reference, I'm using Ubuntu 5.04 Hoary but I think it's a ghastly hybrid blend as I've updated piecemeal from the original Warty CD image.

---

### Post by CompShrink on 2005-01-07
[QUOTE=labbe]It Didnt Worked for me..but mine problem is that for example Gaim doesnt have an icon in the upper right....
I can make a new panel, but It wont work...[/QUOTE]
To see the runnign apps, you need a 'notification area.' Simply right click on an empty part of the panel you made, and click "Add to Panel..." and scroll down to select "Notification Area."

You can also get the clock back this way. And the gnome menus, etc.

BTW, once you add the notification area, the icons of your current programs, such as gaim, won't show up until you restart them. Just turn gaim off then back on and you'd be back to normal.

Also, I'd suggest doing any future upgrades in Synaptic (in the menu panel: Computer > System Configuration > Synaptic Package Manager). First, go to Settings > Repositories and uncheck everything except archive.ubuntu.com and security.ubuntu.com with "main restricted" sections. 

DO turn off the universe and multiverse sections of archive.ubuntu.com, and any other URI that is there, or you may have an unstable upgrade, depending on your pinning. Everything but security is rarely, in fact I believe never, updated once there is the final release of that version, but of course hoary does get updated.

---

### Post by CanadianLinux on 2008-01-20
> **AndyGates said:**
> Rancoras, this worked to get my panel back: thanks!

For reference, I'm using Ubuntu 5.04 Hoary but I think it's a ghastly hybrid blend as I've updated piecemeal from the original Warty CD image.

Also worked for me, for some reason I was in the panel properties  changing the backround of the panel. It then crashed and on reboot didn't return. After reinstall gnome-panel all issues resolved. I love the Ubuntu Community!!! Thanks man

---

