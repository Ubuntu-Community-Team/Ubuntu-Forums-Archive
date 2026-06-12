---
title: "Where is the &quot;Application menu&quot;?"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by Curt Carpenter on 2012-12-20
Hello.
I'm using Ubuntu 12.04LS, and keep seeing references to an "application menu" in the help -- but I can't find this menu anywhere.  An application that I just installed using the software center doesn't appear in "Dash home" even after I reboot -- and help tells me that I should find it in the "Applications menu" -- but I can't find that menu it either :(

Can anyone tell me where to look to find the application menu?

Any guidance appreciated.

---

### Post by zombifier25 on 2012-12-20
I think the application menu refers to the menu of individual apps (e.g. File, Edit,...), since AFAIK there's no such thing in Unity. The closest thing to it is navigating apps by categories.

What is the name of this app you installed? When you search for its name in the Dash, does it show up?

---

### Post by 3rdalbum on 2012-12-21
> **Curt Carpenter said:**
> Hello.
I'm using Ubuntu 12.04LS, and keep seeing references to an "application menu" in the help -- but I can't find this menu anywhere.  An application that I just installed using the software center doesn't appear in "Dash home" even after I reboot -- and help tells me that I should find it in the "Applications menu" -- but I can't find that menu it either :(

Can anyone tell me where to look to find the application menu?

Any guidance appreciated.

Go into Dash Home and, at the bottom of the dash, click the small icon 2nd from the left.

---

### Post by arpanaut on 2012-12-21
You can also hit Super + a to get to the application lens.  Super = WIN key
Also press and hold the Super Key and you will be shown a screen of shortcut key combos

---

### Post by deadflowr on 2012-12-21
> **zombifier25 said:**
> I think the application menu refers to the menu of individual apps (e.g. File, Edit,...), since AFAIK there's no such thing in Unity. The closest thing to it is navigating apps by categories.

What is the name of this app you installed? When you search for its name in the Dash, does it show up?

+1
Ubuntu doesn't have a tradtional menu system, so I'm inclined to agree it probably refers to the programs menu, which in Ubuntu(for most programs) takes up the left side of the top panel.

Alternatively to what 3rdalbum posted, you can use the keyboard short super + A to open the dash directly into the applications menu. You can see a whole list of convenient keyboard shortcuts by pressing and holding down the super key. You can also right click the mouse on the dash icon in the launcher to do the same.

---

### Post by deadflowr on 2012-12-21
> **arpanaut said:**
> You can also hit Super + a to get to the application lens.  Super = WIN key
Also press and hold the Super Key and you will be shown a screen of shortcut key combos

Great minds think alike.:p

To the OP, what 'help' is referencing application menus?

---

### Post by arpanaut on 2012-12-21
> Great minds think alike.:razz:
LOL

Forgot about Rt. click on BFB...  Nice!

---

### Post by Curt Carpenter on 2012-12-21
Thank you for the responses.

I used the Ubuntu Software Center to install the Free Pascal SKD Metapackage (search "fpc").  I can't find any information on the Software Center page for fpc to discover where it was installed.

It doesn't show up in Dash, nor when I use the Dash search function to search for it (I search for "fpc", "Free Pascal" and so on with no luck).   If I look at the installed applications list that Dash provides, it's not there...   Also no trace of it in my Home folder.

So I'm stumped :)

(Thanks for the tip on the Windows key.  I'm  learning new things every day!  I'm finding Unity hard to get used to, especially as the Help system seems to still reflect older versions of the OS.   Pretty impressive never the less.)

---

### Post by arpanaut on 2012-12-21
Try this link: [http://www.lazarus.freepascal.org/index.php?topic=17371.5;wap2](http://www.lazarus.freepascal.org/index.php?topic=17371.5;wap2)

Apparently there are some issues getting it to work correctly out of the box.
Did you try searching for lazarus from the dash?

---

### Post by Hylas de Niall on 2012-12-21
Will it launch from the terminal?

---

### Post by deadflowr on 2012-12-21
> **Curt Carpenter said:**
> Thank you for the responses.

I used the Ubuntu Software Center to install the Free Pascal SKD Metapackage (search "fpc").  I can't find any information on the Software Center page for fpc to discover where it was installed.

It doesn't show up in Dash, nor when I use the Dash search function to search for it (I search for "fpc", "Free Pascal" and so on with no luck).   If I look at the installed applications list that Dash provides, it's not there...   Also no trace of it in my Home folder.

So I'm stumped :)

(Thanks for the tip on the Windows key.  I'm  learning new things every day!  I'm finding Unity hard to get used to, especially as the Help system seems to still reflect older versions of the OS.   Pretty impressive never the less.)


Did you install the Lazarus add-on also?

[http://wiki.freepascal.org/Install_on_Ubuntu]("http://wiki.freepascal.org/Install_on_Ubuntu")

---

### Post by Curt Carpenter on 2012-12-21
Hello everyone.

I finally found the Free Pascal IDE and compiler.  It is located at /usr/bin.  In that directory, you'll find fpc-2.4.4 (which is the compiler, not the IDE) and fp-2.4.4 which is the IDE.

I feel like doing a jig:D

I haven't checked to see if it matters, but I can run the IDE as root, and it works great.

Thanks again for the help and suggestions.

---

