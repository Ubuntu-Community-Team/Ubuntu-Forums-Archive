---
title: "Download Pokies Online"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Bruce2 on 2008-09-21
Hi all.....

Im trying to download Pokies on line. Its a file named SpinPalace.exe

When I try and open it I get a message saying "No application suitable for automatic installation is avialable for handling this kind of file".

Does anyone know how to down load this for Ubuntu?

Thanks..

---

### Post by perlluver on 2008-09-21
> **Bruce2 said:**
> Hi all.....

Im trying to download Pokies on line. Its a file named SpinPalace.exe

When I try and open it I get a message saying "No application suitable for automatic installation is avialable for handling this kind of file".

Does anyone know how to down load this for Ubuntu?

Thanks..

That is a Windows file, you might be able to get it to run under WINE, but there are no guarantees it will run.  Ubuntu and Debian, use .deb files.

---

### Post by dhtseany on 2008-09-21
```
sudo apt-get install wine
```

It is a native Winodows app so you're only real chance of running it is through wine.

Peace
Sean

---

### Post by justtempest on 2008-09-21
Do you have wine installed ?

---

### Post by Bruce2 on 2008-09-21
> **justtempest said:**
> Do you have wine installed ?

I think I do. Under Applications, System Tools, its got Wine Software Uninstaller.

Does that mean ive got Wine?

---

### Post by dhtseany on 2008-09-21
Yes, I believe it does. 

Try going to the terminal and try typing:

```
wine /blah/blah/file.exe
```

and see if that will do anything.

Peace
Sean

---

### Post by Bruce2 on 2008-09-21
> **dhtseany said:**
> Yes, I believe it does. 

Try going to the terminal and try typing:

```
wine /blah/blah/file.exe
```

and see if that will do anything.

Peace
Sean

Sorry, I am pretty computer illiterate....

Do you mean copy and paste that code or write it with the relevant bits that I need?

I tried this : "wine /blah/blah/file.exe"................and it said "cannot find  '/blah/blah/file.exe'"

AND

"wine /SpinPalace/file.exe"

and to the second one it said "no such file or directory"

---

### Post by Bruce2 on 2008-09-21
bump

---

### Post by Patrick793 on 2008-09-21
Where did you save the file? For example, if you saved it on the desktop, you would do
```
wine ~/Desktop/SpinPalace.exe
```

---

### Post by Bucky Ball on 2008-09-21
wine /path_to_your_file/SpinPalace.exe

You may need to put 'sudo' before this command. Don't know, don't use wine. Best idea to find your .exe file in a file browser then copy the address and paste it into the terminal after wine ...

---

### Post by Bruce2 on 2008-09-21
Thanks Patrick and everyone else....it seems to be working now..!

---

### Post by Bruce2 on 2008-09-21
Hmmm....it downloaded it and its saying "download complete!" but its just got a blank screen with the website logo up the top.

It told me to install Gecko or somthing which i did.

---

### Post by Bruce2 on 2008-09-21
Ok, I got it to work but when i click on a pokie game, it comes up with a little square box saying:

"ERROR LOADING MODULE"

"The module you tried to run could not be loaded.
Please contact the help desk for assistance"

(Meaning please contact the site help desk for assistance)

---

### Post by twitch2197 on 2008-09-21
my guess is it requires a .dll that you don't have since you're not ACTUALLY using windows.

---

### Post by Bucky Ball on 2008-09-21
Not all windoze programs will work with WINE, or only randomly, or with bits missing or just plain glitchy. Others work like a charm.

---

