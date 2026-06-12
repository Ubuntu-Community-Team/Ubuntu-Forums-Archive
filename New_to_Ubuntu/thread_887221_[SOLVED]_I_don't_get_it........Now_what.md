---
title: "[SOLVED] I don't get it........Now what?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by dbr1968 on 2008-08-11
I don't get it. I installed 8.04 server off if a disc I burned (the disc checked out). It appeared to install correctly. It asks for login and password, when I put those in they are excepted. Then I get the promt which is [username@servername]:~$
Now what? Where is the welcome screen and desktop stuff? 
On top of all that....I guess I screwed somthing up and now the cd drive isn't being recognized so I can't even boot from the cd!
Help me please!:confused:

---

### Post by tech0007 on 2008-08-11
Get the desktop iso if you want the gui.

---

### Post by Victormd on 2008-08-11
The server version does not come with a GUI, only the desktop edition. An alternative is to install it:
```
sudo apt-get install ubuntu-desktop 
```
if you want ubuntu or if you want kubuntu
```
sudo apt-get install kubuntu-desktop
```
After install, type
```
startx
```

---

### Post by damis648 on 2008-08-11
The server edition doesn't have a GUI. If you want a server with a GUI, run the command:
```
sudo apt-get install ubuntu-desktop
```
If this computer will be used as a normal desktop, you would do good to install the Desktop edition.

EDIT: Also, about the CD booting, you CD must be bad OR BIOS OR your CD drive.

---

### Post by BTMark on 2008-08-11
Edit: Nevermind, was beat to the punch!

---

### Post by dbr1968 on 2008-08-11
Can I use the server edition with the desktop edition?

---

### Post by damis648 on 2008-08-11
> **dbr1968 said:**
> Can I use the server edition with the desktop edition?

What exactly do you  mean? Do you want a GUI on the Server Edition? For that, run:
```
sudo apt-get install ubuntu-desktop
```

**But**, AGAIN, if this will be used as a desktop, install the Desktop Edition.

---

### Post by mc4100 on 2008-08-11
Edit: Nevermind. Totally Wrong.

---

