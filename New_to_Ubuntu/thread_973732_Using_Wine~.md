---
title: "Using Wine~"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by DarkMage2303 on 2008-11-07
I've installed Wine 1.1.7 and I am trying to use Warcraft III and World of Warcraft and I get

```
[/media/Maxtor 80GB/Games/Warcraft III/Frozen Throne.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/Maxtor 80GB/Games/Warcraft III/Frozen Throne.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/Maxtor 80GB/Games/Warcraft III/Frozen Throne.exe or
          /media/Maxtor 80GB/Games/Warcraft III/Frozen Throne.exe.zip, and cannot find /media/Maxtor 80GB/Games/Warcraft III/Frozen Throne.exe.ZIP, period.
```

EDIT: The games are already installed on my External Hard drive from previous OS's.

---

### Post by B34ST1Y on 2008-11-07
that could be why it wont run. Wine is very picky when it comes to running games. While Windows may run the game just fine...you may actually need to install the game via wine.

bear in mind, everything is emulated...not run natively.

---

### Post by resander on 2008-11-09
Right-click the setup.exe file and select Open with Wine from menu that pops up.

---

### Post by jespdj on 2008-11-09
> **B34ST1Y said:**
> bear in mind, everything is emulated...not run natively.
Not really. Do you know what WINE stands for? **W**ine **I**s **N**ot an **E**mulator. WINE is not a processor emulator, it's an implementation of the Windows API on Linux.

---

### Post by Kellemora on 2008-11-09
Hi DM

I thought I just answered this yesterday, but I see it's not here!

I'm not sure if the programs you want to run are compatable with Wine.

But, there is a way to get many programs to run in wine that sometimes don't from the zipped files.

On your Doze machine, make a single folder for the game, unzip it to that folder first, then move that folder into your shared directory ON your Doze machine, DON'T move it TO a shared folder on your Linux Box.

Now go to your Linux box and FETCH the folder from your shared directory on your Doze machine.  Doing it this way preserves the permissions the game needs.

Now you can copy the folder from the Linux Box into the .wine directory.
Look for the install.exe or setup.exe file and you should be home free.
EXCEPT, Wine was designed to run self-contained programs, where all the necessary dependencies are either in that folder or in a dependencies folder that already exists in Wine.

If your program makes certain peeks n pokes or calls outside the API, it won't run and go crash, as in fall down and go boom, hi hi.........

Many gaming programs use resources outside the API, which is why they won't work in Wine.

TTUL
Gary

---

