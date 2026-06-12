---
title: "Let's try this again, I need help"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Jester's Mask on 2008-09-01
Ok, some rude person deleted my clay man account.

I want to get familiar with Ubuntu to actually do things on it, but I need help.

First off, if there's any good documents to start me off well in ubuntu, please post them for me.

Second, I asked how to install this game called Graal.  It has a linux port so it should work on here, but I am not familiar on how to install it on ubuntu.

here's the downloads:
[http://graalonline.com/kingdoms/downloads/](http://graalonline.com/kingdoms/downloads/)

I don't know what to do with the "graal4setup" file, and it appears to have no format whatsoever.

a fellow had a screenshot with the file, having a different icon so he can actually use the file:

[http://img168.imageshack.us/img168/5238/screenshotdt2.png](http://img168.imageshack.us/img168/5238/screenshotdt2.png)

Please help, that's all I really ask.

---

### Post by JC Cheloven on 2008-09-01
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Have fun :-)

---

### Post by cdtech on 2008-09-01
make a directory for graal4setup:
```
mkdir ~/graal
```
download graal4setup into that directory. Then:
```
chmod +x ~/graal/graal4setup
```
Then just run it:
```
cd ~/graal
./graal4setup
```

---

### Post by Jester's Mask on 2008-09-01
> **cdtech said:**
> make a directory for graal4setup:
```
mkdir ~/graal
```
download graal4setup into that directory. Then:
```
chmod +x ~/graal/graal4setup
```
Then just run it:
```
cd ~/graal
./graal4setup
```

Thank you, just need to know how I run these codes.

---

### Post by cdtech on 2008-09-01
Open a terminal Accessories > Terminal

Yes once you make it executable using the "chmod" command then just cd into that directory and run the install with just "./graal4setup" that will start the install.........

---

### Post by benerivo on 2008-09-01
Try right clicking on the downloaded file, and going to 'Properties', then 'Permissions', then ticking 'Allow executing file as program'. Then open a terminal window and drag the icon in to it, and press the enter key.

---

### Post by Jester's Mask on 2008-09-01
Thank you all.

[https://help.ubuntu.com/8.04/add-applications/C/advanced.html#apt](https://help.ubuntu.com/8.04/add-applications/C/advanced.html#apt)

And I found this too.
I'll try it out in a little.

---

### Post by cdtech on 2008-09-01
welcome........

---

