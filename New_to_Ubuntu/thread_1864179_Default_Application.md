---
title: "Default Application"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-10-18
Been thinking i am going crazy here. Ever since i upgraded to 11.10 i have had a problem opening Folders.

I am using the Gnome Classic Desktop. When i click Places at the top of the screen, and choose to open my Home Folder (or any other one) it tries to open it using KolourPaint and i get
> Could not open "ian" - unsupported image format.
 The file may be corrupt.
I love using KolourPaint for simple picture editing, by why all of a sudden is it trying to open Folders with it ??

Thanks in advance anyone :)

---

### Post by Frogs Hair on 2011-10-18
Try this command or right click a folder > open with another application > select file browseR >  check remember this application .

```
 gedit ~/.local/share/applications/mimeapps.list 
```

---

### Post by MadMonkey1966 on 2011-10-18
> **Frogs Hair said:**
> Try this command or right click a folder > open with another application > select file browseR >  check remember this application .

```
 gedit ~/.local/share/applications/mimeapps.list 
```

I tried right-clicking on a folder in the list, BUT it does not do anything, just tries to  open the Folder with KolourPaint again. I cant even get a Folder open :(

I just tried that command, and it gave me this list of stuff in the text editor. 
> 
[Added Associations]
inode/directory=kde4-kolourpaint.desktop;
x-scheme-handler/http=firefox.desktop;alacarte-made.desktop;
x-scheme-handler/https=alacarte-made.desktop;firefox.desktop;
x-scheme-handler/ftp=alacarte-made.desktop;
x-scheme-handler/chrome=alacarte-made.desktop;
text/html=alacarte-made.desktop;
application/x-extension-htm=alacarte-made.desktop;
application/x-extension-html=alacarte-made.desktop;
application/x-extension-shtml=alacarte-made.desktop;
application/xhtml+xml=alacarte-made.desktop;
application/x-extension-xhtml=alacarte-made.desktop;
application/x-extension-xht=alacarte-made.desktop;
x-scheme-handler/mailto=thunderbird.desktop;
text/calendar=gedit.desktop;
audio/x-vorbis+ogg=banshee.desktop;
video/x-ogm+ogg=totem.desktop;
image/jpeg=eog.desktop;kde4-kolourpaint.desktop;

[Default Applications]
inode/directory=nautilus-folder-handler.desktop
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
x-scheme-handler/ftp=alacarte-made.desktop
x-scheme-handler/chrome=alacarte-made.desktop
text/html=alacarte-made.desktop
application/x-extension-htm=alacarte-made.desktop
application/x-extension-html=alacarte-made.desktop
application/x-extension-shtml=alacarte-made.desktop
application/xhtml+xml=alacarte-made.desktop
application/x-extension-xhtml=alacarte-made.desktop
application/x-extension-xht=alacarte-made.desktop
x-scheme-handler/mailto=thunderbird.desktop
image/jpeg=kde4-kolourpaint.desktopDo i have to change something in there ?

---

### Post by MadMonkey1966 on 2011-10-19
No matter what i click on in the Places Menu (Home Folder, Desktop, Computer or any of the Folders in Bookmarks) it just open KolourPaint [-(

---

### Post by gordintoronto on 2011-10-19
Right click the desktop and select "create folder." Right click the folder and select "open with another application." Select file browser from the menu, and make sure "remember this application" is checked. Remove the folder when finished.

---

### Post by MadMonkey1966 on 2011-10-19
> **gordintoronto said:**
> Right click the desktop and select "create folder." Right click the folder and select "open with another application." Select file browser from the menu, and make sure "remember this application" is checked. Remove the folder when finished.

Yeah, it did not actually give me the "remember this application" option. I just selected 'Open as Folder' and it worked. I have checked 3 others and all is back to normal again.

Many Thanks for you help & time gordintoronto :D

---

### Post by PPN13 on 2011-10-19
inode/directory=kde4-kolourpaint.desktop; under [Added Associations] was the culprit. Deleting that would allow the default program (Nautilus) to open folders.

---

### Post by mc4man on 2011-10-19
> **PPN13 said:**
> inode/directory=kde4-kolourpaint.desktop; under [Added Associations] was the culprit. Deleting that would allow the default program (Nautilus) to open folders.

It may until another Added Associations for directories is added from the r. click contest menu

The problem is actually

[Default Applications]
[COLOR="Red"]inode/directory=nautilus-folder-handler.desktop[/COLOR]

1st. 11.10 no longer writes a inode/directory= for Default, nautilus is locked in
2nd.  nautilus-folder-handler.desktop no longer exists. So when anything that tries to use the Default it can't & then uses what's in The Added section, using the 1st. listed .desktop in the inode/directory line

In classic this affects places, in unity it affects the trash & drive icons in launcher, automounted usb drives, & 'open containing folder' from firefox
In Classic the best solution is to change that line to this in [Default Applications]

```
inode/directory=nautilus-home.desktop
```

For unity* one can do the above or just  delete the red line

---

