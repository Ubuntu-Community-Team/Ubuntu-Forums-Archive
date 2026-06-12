---
title: "Where Is Lua.dll?"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by steadi on 2012-11-18
Hello There,

I recently installed lua 5.2.0 on my linux (Ubuntu) laptop and I can confirm this by entering "lua" into the terminal. However, I have been looking around and cannot find the lua.a or lua.dll file.

Where is this file located after lua is installed?

Thanks,
Matt

---

### Post by mlentink on 2012-11-18
Even though i don't know what LUA is, i don't think you'd be able to find a dll on a linux box. "DLL" stands for "Dynamic Link Library" and is a windows thingy.
You can find out where LUA is by typing 
```
which lua
```
in a terminal window

---

### Post by jerome1232 on 2012-11-18
Usually dynamic libraries in Linux end with a .so extension, you can list all files installed by a package with the below code, change the red part to what the actual package name is.

```
dpkg -L *[COLOR="Red"]packagename[/COLOR]*
```

---

### Post by Wim Sturkenboom on 2012-11-18
```

sudo updatedb
locate lua

```
The first command updates a database of files on your computer.
The second command finds anything with lua in that database; you can make that _locate lua.dll_ or _locate lua.a_

---

### Post by ibjsb4 on 2012-11-18
xxx

---

### Post by mlentink on 2012-11-18
> **Wim Sturkenboom said:**
> ```

sudo updatedb
locate lua

```
The first command updates a database of files on your computer.
The second command finds anything with lua in that database; you can make that _locate lua.dll_ or _locate lua.a_

Baie dankie Wim!
Didn't know that, but one learns every day.

---

### Post by Wim Sturkenboom on 2012-11-18
> 
Baie dankie Wim!


In mijn moedertaal: graag gedaan :lol:

---

### Post by deadflowr on 2012-11-18
If I was to guess, the lua.dll is probably in /home/username/.wine folder. Or it's floating around uselessly in some directory.
If you want to run lua in Unix/Linux you should install the linux version.

[http://www.lua.org/manual/5.2/readme.html]("http://www.lua.org/manual/5.2/readme.html")

DLLs as said earlier are windows, which is why I say they are most likely in the wine subfolder or floating around aimlessly.

Wine is a windows compatibility program for unix/linux systems to run windows programs.

The dot in the file name signifies it's a hidden folder/file. You can access it from the terminal by typing ls -a, or from the home folder by typing ctrl+h.

---

