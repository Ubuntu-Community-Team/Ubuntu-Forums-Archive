---
title: "managing partitions"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by vitor.rca on 2013-11-14
hi, I just installed ubuntu for the first time. I'm on an old PC with 80Gb HD. During the installment, I was asked to give some space to ubuntu 13.10 and also some space to something else (don't remember if it was a kind of ubuntu developer). I gave almost my whole HD (70Gb) to ubuntu 13.10 and only 8Gb to the something else.
But now, when I go to 'about this computer', it shows Disk: 8.4Gb.
I don't know if that's the reason, but the computer is slow. It's a 10-year-old computer, but equiped with a AMD Athon 64 CPU and 1Gb of RAM.
Did I do something wrong?
Thanks

---

### Post by heir4c on 2013-11-14
Open a terminal via the Dash (UbuntuLogo on the top left or with keyboard: Ctrl+Alt+T)
Type the following command:
```
sfdisk -l
```
Copy/Paste the text and post it here. (You can select the text with the mouse and then rightclick on the selected text and choose 'Copy')

---

### Post by vitor.rca on 2013-11-14
Actually nothing happens when I do that.
nghm@nghm-HP-Compaq:~$ sfdisk -l
nghm@nghm-HP-Compaq:~$

---

### Post by Bucky Ball on 2013-11-14
Welcome. Little off topic but you will speed things up with something lighter, Xubuntu or Lubuntu perhaps. If you haven't gotten too far with this I suggest you try one.

Fixing this issue I doubt will speed anything up. To the issue, open Gparted and see what that says. Does that show the two partitions correctly?

---

### Post by heir4c on 2013-11-14
You can try:
```
fdisk -l
```

Or like Bucky Ball say: Open gParted. (In live-session you find it via the Dash.) 
In your installed Ubuntu you can't because it is not installed yet.

And maybe Bucky Ball is right. Install Lubuntu or Xubuntu (or Zorin or Bodhi (both based on Ubuntu)).

---

### Post by oldfred on 2013-11-14
I think you need the sudo before the sfdisk or the fdisk commands if in working system.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by heir4c on 2013-11-14
No, you don't but you can. :)

---

### Post by thesleash on 2013-11-15
perhaps you could try puppy linux

---

