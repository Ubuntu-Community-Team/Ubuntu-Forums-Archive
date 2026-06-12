---
title: "Desktop directory has moved - how do I move it back?"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by blackmilk on 2012-08-07
Hi all,

I have somehow managed (don't ask me how) to move my desktop directory into the Video folder. Which is a huge inconvenience, although technically everything still works fine. But I cannot move it back - when I try to do so, I get a message saying I don't have that privilege.

For clarity, I should probably add that I am using a German-language version of Ubuntu 12.04 and that the desktop is called Arbeitsfläche in German. Anyhow, here's a screenshot:

[IMG]http://files.myopera.com/caad5/albums/6486352/desktop.png[/IMG]

---

### Post by Zvlwab on 2012-08-07
You should edit the file .config/user-dirs.dirs
Find the line
```
XDG_DESKTOP_DIR="some/path"
```
and change it to whatever suits you, probably
```
XDG_DESKTOP_DIR="$HOME/Arbeitsfläche"
```

---

### Post by cool110 on 2012-08-07
Just run this command in a terminal. If you get permission errors prefix it with sudo.
```
mv ~/Videos/Arbeitsfläche/ ~/Arbeitsfläche/
```

---

### Post by mcduck on 2012-08-07
...and the full answer is to do both of the above, first move the Desktop directly back t o it's correct place, and then update the user-dirs file to use the correct location (as it's entry was probably removed when you moved the directory to different place)

---

### Post by Kalanac on 2012-08-07
If you get a permission error on the mv, use sudo :)

EDIT: Ack, that was suggested already, I should really stop skim reading :S

---

### Post by wojox on 2012-08-07
If you sudo it [COLOR="Red"]root[/COLOR] will own it. :(

---

### Post by Kalanac on 2012-08-08
if that happens use

```
sudo chown yourusername:yourusername ~/Arbeitsfläche/
```

to set the permissions back to the correct user.  The reason for the colon and stating yourusername twice is to set the group too.

---

### Post by blackmilk on 2012-08-08
Thank you!
This forum is a wealth of information. Moving it in the terminal worked (no permission errors btw). I also edited the user-dirs.dirs file and in the process also learned where to go if I want to change the default download directory.

---

