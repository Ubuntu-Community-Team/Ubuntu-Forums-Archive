---
title: "[SOLVED] Windows Favorites --&amp;gt; FireFox Bookmarks"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by ingeva on 2008-08-02
I have tried several methods to transfer my rather large Favorites folder to FireFox.
I have made an html file from Windows, so I have saved all bookmarks there, but they can't be imported directly.

I installed FireFox in Windows and imported Favorites into it. I then copied the complete "Mozilla" directory to my Ubuntu. It also has a subdirectory called FireFox, and several files indicating they have something to do with "bookmarks".

But I can't find the right files to copy. I have tried several alternatives, but nothing seems to help. The existing bookmarks are unchanged, and there are no new ones.

HELP please?

---

### Post by Rab22 on 2008-08-02
Does your Windows Firefox import all the bookmarks correctly?

---

### Post by sailor2001 on 2008-08-02
click "manage book marks' and "export" to a flash drive and then "import" from the flash drive (manage bookmarks)

---

### Post by aysiu on 2008-08-02
> **ingeva said:**
> 
I installed FireFox in Windows and imported Favorites into it. I then copied the complete "Mozilla" directory to my Ubuntu. It also has a subdirectory called FireFox, and several files indicating they have something to do with "bookmarks".

But I can't find the right files to copy. I have tried several alternatives, but nothing seems to help. The existing bookmarks are unchanged, and there are no new ones. I believe the folder translation is

C:\Documents and Settings\*username*\Application Data\Mozilla Firefox

to

/home/*username*/.mozilla

---

### Post by ingeva on 2008-08-02
> **aysiu said:**
> I believe the folder translation is

C:\Documents and Settings\*username*\Application Data\Mozilla Firefox

to

/home/*username*/.mozilla

Yes I knew that. I just didn't copy the correct files! :)

There were two files that I copied, and I had to edit the "profiles.ini" a little.
The other file was the .default file that profiles.ini was pointing to.

After I copied these two files, the favorites were OK but some initializing of FireFox needed to be done again. No matter; it was done in a minute.

Thanks -- even if I found out myself, but if I hadn't ask I would still have the same problem! :)

What astounds me is I have received several good answers in just a couple of minutes. This forum is invaluable for a new Ubuntu user!

---

### Post by ingeva on 2008-08-02
> **ingeva said:**
> After I copied these two files, the favorites were OK but some initializing of FireFox needed to be done again. No matter; it was done in a minute.


I'm glad I didn't do too much tweaking of the user interface, because that also needed to be redone.... :)

---

