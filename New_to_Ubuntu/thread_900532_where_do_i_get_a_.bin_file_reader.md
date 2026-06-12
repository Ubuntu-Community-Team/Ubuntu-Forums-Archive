---
title: "where do i get a .bin file reader"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by angrylemon on 2008-08-25
when i try and click on .bin files this message comes up:
 there is no application installed for this file type.
Sorry if im being stupid but only got Linux a few days ago
 plz can anyone help

---

### Post by Thelasko on 2008-08-25
.bin files are executibles (like a .exe in Windows).  You typically can't edit them.  May I ask, what are you trying to do?

---

### Post by tuxxy on 2008-08-25
Open a Terminal

Change to the dir that the .bin was downloaded to, EG Desktop

```
cd Desktop
```

Now you are in the directory, type 

```
sudo chmod +x filename.bin
``` 

This will change your bin to an executable

Finally type this to run the .bin

```
./filename.bin 
```

Make sure you edit the name to the correct name of your .BIN file

---

