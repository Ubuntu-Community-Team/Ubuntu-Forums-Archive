---
title: "HowTo: BitTornado with GTK2"
date: 2005-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Arktis on 2005-11-04
BitTornado is one of the best Bittorrent clients out there, but it's so dang ugly!  Well, not anymore.  Now it uses gtk2!  This guide shows you how to get it up and running on your system.

If you've got bittornado installed already from the repos, get rid of it.
```
sudo apt-get remove bittornado bittornado-gui
```
Optionally, I've also removed the default client.
```
sudo apt-get remove gnome-btdownload bittorrent
```
Again, optionally, I've removed wxgtk2.4.
```
sudo apt-get remove python-wxgtk2.4 libwxgtk2.4-1
```
Now you want to install 2.6
```
sudo apt-get install python-wxgtk2.6 libwxgtk2.6-0
```
Now, down to buisness. Time to download bittornado from [http://bittornado.com/download.html](http://bittornado.com/download.html) .  You have two choices.  The stable version, and the testing version.  The stable version has a bug we'll need to fix... I'll go into that later.  The unstable version is what works for me so I'll cover that first.

**Unstable Version:**

Download the unstable version (BitTornado-0.3.14.tar.gz at the time of this posting) and extract it somewhere in your home directory.  Open up a terminal and cd to that location.  First, make sure it is running properly for you.
```
python btdownloadgui.py
```
If it segfaults on exit, don't worry.  It does that for me too, but everything works perfectly.  Now it's time to install.
```
sudo python setup.py install
```
The final step is to add a line to /etc/mailcap.
```
sudo gedit /etc/mailcap
```
add **application/x-bittorrent; /usr/bin/btdownloadgui.py %s; test=test -n "$DISPLAY"** to the end, save and quit.  Close any web browsers you have open and re-open them for the changes to take effect.

If you want to associate .torrent files so that when you double-click on them from nautilus, they will be opened by bittornado, that's easy.

Open up nautilus and go to where you have saved a .torrent file.  Right-click on it and select properties.  Select the "open with" tab and click the "add" button.  Click the arrow next to "use a custom command" and in the box, type "btdownloadgui.py" without the quotes.  Click "add" and you're done.

**Stable version:**

Now I'll cover the stable version.  I couldn't get this version to connect to ANY trackers, but perhaps others will have better luck.  As with the unstable version, download it (BitTornado-0.3.7.tar.gz at the time of this posting) and extract it somewhere in your home directory.  Open up a terminal and cd to that location.  First, check to see sure how it runs.
```
python btdownloadgui.py
```
...which should output:
```
Traceback (most recent call last):
  File "btdownloadgui.py", line 29, in ?
    from BitTornado.ConfigReader import configReader
  File "/home/arktis/src/BitTornado-CVS/BitTornado/ConfigReader.py", line 40, in ?
    _CHECKINGCOLOR = ColorToHex(wxSystemSettings_GetColour(wxSYS_COLOUR_3DSHADOW))
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc.py", line 187, in SystemSettings_GetColour
    return _misc_.SystemSettings_GetColour(*args, **kwargs)
wx._core.PyNoAppError: The wx.App object must be created first!
```
Holy crap!  That's an ugly error message, isn't it?  We need to fix that, don't we?  To do this, you need to change to the BitTornado subfolder and open a file for editing.
```
cd BitTornado
gedit ConfigReader.py
```
Go down to lines 40 and 41 (turn on the showing of line numbers from your preferences if you need to).  The lines should look like this:

[b]_CHECKINGCOLOR = ColorToHex(wxSystemSettings_GetColour(wxSYS_COLOUR_3DSHADOW))
_DOWNLOADCOLOR = ColorToHex(wxSystemSettings_GetColour(wxSYS_COLOUR_ACTIVECAPTION))[/b]

Change them to this:

[b] _CHECKINGCOLOR = ColorToHex(wxColour(155,156,157))
_DOWNLOADCOLOR = ColorToHex(wxColour(1,1,1))[/b]

Save the file and exit.  Go up one level back to where you were before.
```
cd ..
```
Now check again to make sure it runs.
```
python btdownloadgui.py
```
From this point on, you can follow the exact same steps I outlined for getting the unstable version to work, starting with the running of setup.py.

Like I said, the stable version won't work for me because it doesn't connect to any trackers and doesn't throw any specific error messages I can use to trace the problem.  If anyone has any success in getting it to work, please let me know.

---

### Post by goyan on 2005-11-04
I am new to Linux, I got an error when I tried to install the BitTorado unstable version:

```
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)
```

What have I done wrong?

Goyan

---

### Post by bionnaki on 2005-11-04
screenshots?

---

### Post by bored2k on 2005-11-04
I don't get this whole HOWTO. I just install wxgtk and wxpython 2.6 from the .gz file and run it. Easy as cake.

[[IMG]http://img312.imageshack.us/img312/3011/screenshot18ea.th.png[/IMG]](http://img312.imageshack.us/my.php?image=screenshot18ea.png)[/CENTER]

---

### Post by Arktis on 2005-11-05
[QUOTE=goyan]I am new to Linux, I got an error when I tried to install the BitTorado unstable version:

```
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)
```

What have I done wrong?

Goyan[/QUOTE]

Install python2.4-dev.

[quote=bored2k]I don't get this whole HOWTO. I just install wxgtk and wxpython 2.6 from the .gz file and run it. Easy as cake.[/quote]

This howto is about getting it set up properly and associating it in your browser and file manager, and also how to do the proper fix for the stable version's annoying bug.  If you don't want it to work that way, fine, run it directly from your home folder.  If you're like me and only use one bittorrent client and want it properly set up on your system, then I've spelled out exactly how to do it.  The critique you should really be making is why an installer was included in the first place if you really think nobody should use it.  But then again, not everybody does things like you.

---

### Post by absolut on 2005-11-05
Thanks! works great now.  :cool:

---

### Post by lzfy on 2005-11-08
It does everything you said but then what??? I mean i don' t see a link for Bittornado at the Apps menu. I didn't remove the default client so when i double click a torrent file it opens that client. Can you please help me?

Thanks

---

### Post by PsychoTrauma on 2005-11-09
[QUOTE=lzfy]It does everything you said but then what??? I mean i don' t see a link for Bittornado at the Apps menu. I didn't remove the default client so when i double click a torrent file it opens that client. Can you please help me?

Thanks[/QUOTE]

You need to make it yourself:

```
/usr/bin/btdownloadgui.py
```

is where you need to link to.

---

### Post by benplaut on 2005-11-09
official client still rocks :D

---

### Post by tedddee on 2005-11-12
[QUOTE=bored2k]I don't get this whole HOWTO. I just install wxgtk and wxpython 2.6 from the .gz file and run it. Easy as cake.

[[IMG]http://img312.imageshack.us/img312/3011/screenshot18ea.th.png[/IMG]](http://img312.imageshack.us/my.php?image=screenshot18ea.png)[/QUOTE]

how do I get my apps looking like that  :confused: 

mine: [http://members.cox.net/tedddee/bitt.jpg](http://members.cox.net/tedddee/bitt.jpg)

---

### Post by WetWilly on 2005-11-13
sudo apt-get remove python-wxgtk2.4 libwxgtk2.4-1

This breaks my vlc player :(

---

### Post by lzfy on 2005-11-13
[QUOTE=PsychoTrauma]You need to make it yourself:

```
/usr/bin/btdownloadgui.py
```

is where you need to link to.[/QUOTE]

Thanks :p

I have another question, can i make i .deb file of the new GTK Bittornado so the next time i don't have to recompile everything, or is that not possible?

---

### Post by Arktis on 2005-11-14
> **WetWilly]sudo apt-get remove python-wxgtk2.4 libwxgtk2.4-1

This breaks my vlc player :([/QUOTE]

Well as I said, that's an optional step.  You don't need to do it.  said:**
> 
how do I get my apps looking like that

mine: [http://members.cox.net/tedddee/bitt.jpg](http://members.cox.net/tedddee/bitt.jpg)

That's what this howto does.  It makes bittornado look like bored2k's screenshot.

[quote=lzfy]I have another question, can i make i .deb file of the new GTK Bittornado so the next time i don't have to recompile everything, or is that not possible?[/quote]

Hmm... I don't know how.  If this came with a make script, you could use checkinstall, but it doesn't.   I'll look into it.

---

### Post by Cashel on 2005-11-17
Thanks! 
Exactly what the doctor ordered... Ignore the heathens :)

I agree about the original client being fine.. it is.. but some trackers are jerks about it.. you can add the --minport --maxport to much higher ports to fool them, but I decided I wanted a manager style downloader and BitTornado it is :)

Thanks Again,
Cashel

---

### Post by tHub on 2005-11-19
i installed the unstable version and its having trouble to find peers in a file that has over 1k peers according to Azureus, it will only show like 5 or 6 and the download rate wont go over 1kB/s
edit: i'm not sure if the problem is BitTornado or my router modem, but i did some port forwarding and it seems to be ok now.

---

### Post by bluevoodoo1 on 2006-01-07
The unstable version of BitTornado installed perfectly with this HowTo! thanks!

---

