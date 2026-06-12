---
title: "video in 25 part .rar files...?"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by RotorRick on 2011-10-05
downloaded a video, only to see that it seems to be a folder with little .rar files numbered from 1 to 25... how do I go about putting them together to watch this?

---

### Post by collisionystm on 2011-10-05
Usually with Windows you use Win-Rar, Unzip the first one and it automatically looks for the next 24. Your going to need a similar program I guess

---

### Post by ubupirate on 2011-10-05
> **collisionystm said:**
> Usually with Windows you use Win-Rar, Unzip the first one and it automatically looks for the next 24. Your going to need a similar program I guess

I believe Ubuntu will also do this too with the right click extract option on the first rar file, which is usually a double zero 00 in the list.

If not already done so OP:

```
sudo apt-get install rar p7zip-full
```

Which will install both ability to extract RAR and 7z formats.

---

### Post by seawolf167 on 2011-10-05
Use unrar (start with the first part whatever it is numbered)

```
unrar x filename.part1.rar
```manual can be accessed by

```
man unrar
```or 7zip

```
sudo apt-get install p7zip-full
man 7z
```

---

### Post by RotorRick on 2011-10-05
Solved!

I just selected all the .rar files, then right-clicked on Archive Manager to unpack them all, and it completed it in under a minute...then I had a lot of little Archive windows to close, but it worked and tested the video just fine.

---

### Post by seawolf167 on 2011-10-05
> **collisionystm said:**
> Usually with Windows you use Win-Rar, Unzip the first one and it automatically looks for the next 24. Your going to need a similar program I guess

Win-Rar? Ick! Use [7zip]("http://www.7-zip.org/")!

---

