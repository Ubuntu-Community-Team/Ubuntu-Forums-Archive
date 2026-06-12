---
title: "Wine Help"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-14
I am trying to install Steam into Wine so i can play Cs:s but when i download steam off of steampowered.com i click download ant then for open with i choose browse but where do i find wine at (search wont find it)

---

### Post by Thirtysixway on 2008-05-14
You should save it somewhere, like your home folder.  Then, double click the .exe and if wine is installed, it should run.  Or, right click the file and click Open with Wine.  You can also type in Wine yourexehere.exe in terminal to start it.

You need to save it to disk first, not open it from the download dialog.

---

### Post by RequinB4 on 2008-05-14
Do you even have Wine installed?

```

sudo apt-get install wine

```

You can also navigate to the directory the .exe is in
```

cd /path/to/exe/

```

Then execute the program
```

wine EXECUTABLE.exe

```

If it can't find wine, you don't have it installed, by the way.

Good luck with steam - remember to take a look at the Steam AppDB (Google "wine appdb")

---

