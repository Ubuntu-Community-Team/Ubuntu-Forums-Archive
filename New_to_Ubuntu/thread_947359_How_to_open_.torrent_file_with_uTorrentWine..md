---
title: "How to open .torrent file with uTorrent/Wine."
date: 2008-10-14
forum: New to Ubuntu
---

### Post by GXice on 2008-10-14
As per thread title. After saving a .torrent file to the desktop, it opens with Transmission...

I've just migrated from Windows. Can I make it open with uTorrent by default? Clicking the "Associate with .torrent files" in uTorrent doesn't help.

Where's the "Open With.." option? :D

---

### Post by hyper_ch on 2008-10-14
why do you want to continue using utorrent while there are excellente torrent clients available on linux?

---

### Post by cairnzi on 2008-10-14
you are better using azureus for linux, its better than utorrent anyway, as hyper_ch said there are plenty linux based torrent programs out there. :)

---

### Post by Jive Turkey on 2008-10-14
The context menu (right click) should have an option "Open with other application" I like the azureus/vuze client myself, but transmission works well also.  You can laso right click the file and choose "properties" and there is an "Open with" tab on the properties dialog.

---

### Post by GXice on 2008-10-14
> **hyper_ch said:**
> why do you want to continue using utorrent while there are excellente torrent clients available on linux?

uTorrent is the only common one that is supported by all the private trackers I use. The rest are varied. And Azureus is a bit of a resource hog and requires Java Runtime, which I have no intention of installing. uTorrent is flawless for me, other than this one problem.

---

### Post by GXice on 2008-10-14
> **Jive Turkey said:**
> The context menu (right click) should have an option "Open with other application".  You can laso right click the file and choose "properties" and there is an "Open with" tab on the properties dialog.

I've tried this, and selected Wine Windows Program Loader. However, it does nothing, it doesn't open the .torrent file.

---

### Post by RyanJones187 on 2008-10-14
> **GXice said:**
> I've tried this, and selected Wine Windows Program Loader. However, it does nothing, it doesn't open the .torrent file.

Try [this](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml), it's old but the method may still work.

---

### Post by MrWES on 2008-10-14
Why not make Firefox open it by default:

[http://ubuntuforums.org/showthread.php?p=5889354#post5889354](http://ubuntuforums.org/showthread.php?p=5889354#post5889354)

---

### Post by GXice on 2008-10-15
> **RyanJones187 said:**
> Try [this](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml), 

That link has nothing to do with what the topic is asking, sorry.

> **MrWES said:**
> Why not make Firefox open it by default:
[http://ubuntuforums.org/showthread.php?p=5889354#post5889354](http://ubuntuforums.org/showthread.php?p=5889354#post5889354)

Doesn't work either, torrent isnt in the list of applications at all.

Is there no solution? Bummer. :( Maybe they'll fix this bug in the next release...

---

### Post by cozmicharlie on 2008-10-15
It will not be in the list of applications.  You need to follow jive turkeys instructions.  When the dialog box pops up select "open with" and in the pull down menu select "other".  It will open your file manager.  Go to the utorrent executable (I am not sure where that is in wine but you should be able to find out by looking at the launcher in the applications menu) and select it then select "do this automatically with files like this".

---

### Post by Aero-Z on 2008-10-15
Deluge for the win!
```
sudo apt-get install deluge
```
It's like simplified uTorrent. Looks nice and familiar with uTorrent.

---

### Post by sillyfofilly on 2008-11-09
This is the script I use

```

#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/uTorrent
if [ "$1" != "" ]; then
	var="`echo E:$1 | sed 's/\//\\\/g'`"
	wine utorrent.exe "$var"
else
	wine utorrent.exe
fi

```

Save this to /usr/bin/utorrent
and make it executable with
```
sudo chmod +x /usr/bin/utorrent
```

Open up "Configure Wine", and on the "Drives" tab, make sure that E: is mapped to /

---

