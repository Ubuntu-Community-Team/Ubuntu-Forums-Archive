---
title: "Desktop and Nautilus, some file types opening with GEdit?"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-10-03
All of a sudden, when I booted up the other day, my .desktop files were unassociated as launchers. 

[img]http://img377.imageshack.us/img377/7122/03octfri2042ap3.png[/img]

.mp4, .zip, .odt, .abw, .7z, .doc, and other files did the same thing. This was after I uninstalled some KDE packages. Which ones should I reinstall, if this is the case? The icons don't show up, and double clicking doesn't open with the normal application associated with the extension. Please help me. Thanks.

---

### Post by bhadotia on 2008-10-03
> **linkmaster03 said:**
> All of a sudden, when I booted up the other day, my .desktop files were unassociated as launchers. 

[img]http://img377.imageshack.us/img377/7122/03octfri2042ap3.png[/img]

.mp4, .zip, .odt, .abw, .7z, .doc, and other files did the same thing. This was after I uninstalled some KDE packages. Which ones should I reinstall, if this is the case? The icons don't show up, and double clicking doesn't open with the normal application associated with the extension. Please help me. Thanks.

I did not get the meaning of " my .desktop files were unassociated as launchers."
What do you mean by that . I thought .desktop files were links to applications only found in hidden configuration folders in the home directory or in other system configuration directories.

---

### Post by linkmaster03 on 2008-10-03
As you can see, my .desktop files (launchers) are being treated as text. They should have an icon and run like a normal launcher.

---

### Post by bhadotia on 2008-10-04
> **linkmaster03 said:**
> As you can see, my .desktop files (launchers) are being treated as text. They should have an icon and run like a normal launcher.

If your apps are launching fine you don't need to worry about the icons. The .desktop are in actual executable text files. Check to see if they have execution permissions. If this is the case then its fine.

EDIT: Also look at your mimetypes in ~/.localshare/applications and /etc/gnome/defaults.list.

---

### Post by linkmaster03 on 2008-10-04
Well the launchers DON'T work. In fact, I just found out that if I double click ANYTHING through a Nautilus browser (including Desktop) that it tries to open with GEdit. Thumbnails only appear if they were generated before this started happening.

[img]http://img522.imageshack.us/img522/3465/04octsat1355xf7.png[/img]
[img]http://img524.imageshack.us/img524/4406/04octsat1355ck5.png[/img]
[img]http://img50.imageshack.us/img50/7631/04octsat1356eq7.png[/img]

Meaning I can't double click any files, and they seem unassociated with any app. ~/.localshare/applications is empty, and /etc/gnome/defaults.list looks perfectly fine. Please help me, this is really aggravating.

---

### Post by bhadotia on 2008-10-05
> **linkmaster03 said:**
> Well the launchers DON'T work. In fact, I just found out that if I double click ANYTHING through a Nautilus browser (including Desktop) that it tries to open with GEdit. Thumbnails only appear if they were generated before this started happening.

Meaning I can't double click any files, and they seem unassociated with any app. ~/.localshare/applications is empty, and /etc/gnome/defaults.list looks perfectly fine. Please help me, this is really aggravating.

Well ~/.local/share/applications being empty is no problem it contains a file only if you define some custom file associations.
And your defaults.list file is also fine, you say, then I think you are right you might be missing some package. 
If you uninstalled the KDE packages through the terminal look in the history  (press ctrl+r and start typing to find a matching command) to find the command you used and post here.

Otherwise if you used synaptic you can check system logs (System>Administration).

You might also try installing the ubuntu-desktop package (to bring basic gnome functionality (if its lost)):
```
sudo apt-get install ubuntu-desktop
```

If nothing works out delete all your personal configuration file (hidden files in home directory) and start afresh, you might want to back them up before doing this (e.g., if you use evolution or thunderbird you will loose your email; if you use tomboy you will loose your notes- so I recommend backing up before doing this)

---

### Post by linkmaster03 on 2008-10-05
I found this is the command I ran:

```
sudo aptitude purge kdebase-bin-kde4 kdebase-dev-kde4 kdebase-kde4 kde4libs-bin
```

But I installed them again and it did nothing. I'm not ready or willing to fresh install. That's the Windows way out of things. I also have a lot of things configured.

Also, I can't save in gThumb or open in Evince I found. It says it doesn't support [mime-type here].

---

### Post by bhadotia on 2008-10-05
> **linkmaster03 said:**
> I found this is the command I ran:

```
sudo aptitude purge kdebase-bin-kde4 kdebase-dev-kde4 kdebase-kde4 kde4libs-bin
```

But I installed them again and it did nothing. I'm not ready or willing to fresh install. That's the Windows way out of things. I also have a lot of things configured.

Also, I can't save in gThumb or open in Evince I found. It says it doesn't support [mime-type here].

Alright I think that means that your mime-types settings are messed up. I think your problem can be  solved by deleting your configuration files of mime-types. But all I know is that ~/.config ~/.local are the directories that contain such info. So make a backup of these directories and wipe them. Restart the computer (or restart X) and see if it works.

EDIT:
There may also be some hidden files relating to mime-types do look out for them too.

---

### Post by linkmaster03 on 2008-10-06
I tried removing ~/.config/ and ~/.local/ and restarting GNOME. No luck.

---

### Post by Kellemora on 2008-10-08
Hi Linkmaster

Have you tried right clicking on the files, selecting properties, then OPEN WITH and re-establishing the links?

I had this problem myself when I first started because I was trying out both KDE and Gnome GUI's.  When I changed from one to the other, I lost all of my current desktop links.

Good Luck

TTUL
Gary

---

### Post by linkmaster03 on 2008-10-08
Even when I do that, the icons/thumbnails aren't there. Also, right-click options associated aren't there. (extracting archives, resizing pics)

---

### Post by linkmaster03 on 2008-10-08
I solved the problem by:

```
sudo apt-get reinstall shared-mime-info
```

and then restarting GNOME. (Ctrl+Alt+Backspace)

YES!!!!!

---

### Post by PsiBer on 2008-10-13
perhaps someone here could help get this thing to forget some of these options... when I double click a .exe file to launch an application thru Wine (any .exe file) it would try to start my windows Steam application thru Wine... so I was like OK, we got a file association problem here just right-click any .exe file and select 'Open With Other Application' and change its association to 'Wine Windows Program Loader' but when I scroll thru the list looking for 'Wine Windows Program Loader' I see several entries that just say 'Wine'... those extras need to go! anyone here know how to remove those unwanted items from the list of options?

---

### Post by f-schaefer on 2009-08-08
> **linkmaster03 said:**
> I solved the problem by:

```
sudo apt-get reinstall shared-mime-info
```and then restarting GNOME. (Ctrl+Alt+Backspace)

YES!!!!!

That helped me so much!

Thank you.

The problem also occured when upgrading a kde install in parallel with gnome (on a OpenSuse installation).

Greets

---

