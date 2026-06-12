---
title: "[SOLVED] Put Folders on Desktop?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Kellemora on 2008-09-09
Hi Gang

Ok, so I'm OLDE and GREEN too!

I would like to put two folders on my Desktop, one for Documents and a folder for Shared on the LAN documents.

Other Distro's have folders marked Desktop, Home, Trash on the desktop, not that I like it that much.
My Ubunto has NOTHING on the desktop!  But I can use the pull-down to get to the folders.

It might help if I KNEW the correct terminology (name) for the blank screen I am seeing too.  In WinDOZE what you SEE IS the Desktop!
In Linux, it's something else, what I don't know.  Because Desktop is a folder, therefore everything that should be ON your desktop should be inside that folder, and when I open IT, is should have a desktop, right?

And YES I've searched the forums and the web until I'm blue in the face!

The ONLY things I find is copy folder to desktop, which is another folder itself.  But THAT folder is not ON my screen (desktop in Doze).

I did find the answers to other problems I was having, and most of them were presented with such clarity that this old geezer could understand them, hi hi........

Thanks
Gary


Now, how do I get the Desktop folder on TOP of the screen I see when Ubunto is running and I'm logged in?????

---

### Post by wolfen69 on 2008-09-09
i'm confused. you can't copy a folder onto itself. if i understand correctly, you want a desktop folder on your desktop? why? you are already there. i think you need to be more specific.

---

### Post by Separ on 2008-09-09
1. It's not Ubunto, its Ubuntu.

2. Right click desktop (or in any folder for that matter) and select Create Folder.

EDIT: 3. You can also create symbolic links to folders from your desktop by doing ```
ln -s /Dir/To/Link/To ./Target_Dir
```

---

### Post by Zip247 on 2008-09-09
see this thread 

[http://ubuntuforums.org/showthread.php?t=630090](http://ubuntuforums.org/showthread.php?t=630090)

---

### Post by whitethorn on 2008-09-09
Hi, you want to create two folders on you Desktop, in Ubuntu we call what you see, the desktop as well.  To create a folder just right click on you Desktop and and choose Create Folder from the menu.  You can find your desktop under

> /home/yourusername/Desktop

This is where everything you have on your screen should be.  If you want to get a trash can and maybe a My Computer on your desktop you can enable this by pressing ALT+F2 and type in

```
gconf-editor
```

This is pretty much the equivalent of regedit.exe from windows.  Here you can change a whole bunch of stuff.  Now go into  apps -> nautilus -> desktop -> 

Here you can enable 
Computer_icon_visible (puts a My Computer on ur Desktop)
and trash_icon_visible to get a trash icon

---

### Post by Kellemora on 2008-09-09
Hi Wolfen

I DON'T want a folder named Desktop ON my Desktop, like those OTHER lowly Distro's DO............. They serve no purpose there!

I want to PUT a folder named DOCUMENTS and another folder named SHARED STUFF into my Desktop folder and have them APPEAR on my Desktop!  Like they do in OTHER Disto's.

I DON'T WANT the folders named Desktop or Home to appear on my desktop like they do in other Disto's though.

Currently, my Desktop is BLANK, unless I MOUNT a shared folder from another computer, THEN that folder appears on my Desktop until I unmount it.

That's why I don't think I'm looking at my Desktop, I'm looking at a Screen with a tall BIRD on it!
It CAN'T be the Desktop, because I didn't OPEN the folder named Desktop yet!

If I open /HOME, I see a folder named Desktop, Documents, Public, etc. etc. etc.  BUT the folder Desktop, if I open it, it's EMPTY.

NEVERMIND, I JUST FIGURED IT OUT!  
I MOVED the folders from HOME into the Folder named Desktop and it WORKED this time.

TTUL
Gary

---

