---
title: "How to play mp3/vlc from terminal window?"
date: 2016-12-31
forum: New to Ubuntu
---

### Post by 1ritesh on 2016-12-31
Hello,
i want to play file from terminal window how to do this?
[ATTACH=CONFIG]272926[/ATTACH]

---

### Post by lisati on 2016-12-31
Seriously?
[https://help.ubuntu.com/community/PlayMusicFromCommandLine](https://help.ubuntu.com/community/PlayMusicFromCommandLine)

---

### Post by vasa1 on 2016-12-31
Are you sharing your computer with anyone else?

---

### Post by 1ritesh on 2016-12-31
hello sir,
not working[ATTACH=CONFIG]272927[/ATTACH]

---

### Post by 1ritesh on 2016-12-31
> Are you sharing your computer with anyone else?
How to share i dont know sir.

---

### Post by vasa1 on 2016-12-31
Try this exactly:
```
vlc "Nashe .mp3"
```

---

### Post by lisati on 2016-12-31
> **1ritesh said:**
> hello sir,
not working
Again, seriously? There are already many threads available on the forum which deal with fixing broken dependencies.

It might also be useful to us if instead of screenshots, you were to copy and paste the output of the commands, and enclose the output with [noparse]```
 and 
```[/noparse].

---

### Post by vasa1 on 2016-12-31
Have you installed restricted-extras? Maybe that's what is needed (providing the filenames don't have spaces or other odd characters in them).

```
sudo apt-get install ubuntu-restricted-extras
```

If your filenames have spaces or anything else than a-z, A-Z, 0-9, - and _, some programs may have difficulty.

In such cases, enclose the entire filename in double quotes like this: "Nashe .mp3". If you don't, the program will look for one file called Nashe and another file called .mp3.

---

### Post by 1ritesh on 2016-12-31
vlc "Nashe .mp3"

hello sir thanks it is working

---

### Post by SeijiSensei on 2016-12-31
Files with spaces in their names are always troublesome.  I suggest renaming files and replacing blanks with dots, dashes or underscores.

Another useful trick is "tab completion."  If you were to type "vlc Nas" and hit the tab, it will complete the filename with the spaces "escaped" with the backslash like this:
```
vlc Nashe\ .mp3
```
Escaping the spaces eliminates the need for quotes, but using quotes is more intuitive.  Still tab-completion conquers all.

---

### Post by mc4man on 2016-12-31
> **1ritesh said:**
> Hello,
i want to play file from terminal window how to do this?
[ATTACH=CONFIG]272926[/ATTACH]
for play (sox)

```
sudo apt-get install libsox-fmt-mp3
```
or 
```
sudo apt-get install libsox-fmt-all
```

---

