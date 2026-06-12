---
title: "installing 14.04 software on 16.04"
date: 2017-06-18
forum: New to Ubuntu
---

### Post by wintersonata9 on 2017-06-18
So I was able to install dual-booting Crouton [using these instructions]("https://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/"). I have a Samsung Chromebook XE303C12 - somehow still kickin' after five years!

Crouton uses the new Ubuntu build Xenial 16.04.02 and I'm trying to install [a game]("http://www.unrealworld.fi/urw_linuxmirror.html") built for 14.04. I have downloaded both the 32-bit and 64-bit DEB files, but when I double click, I get the error message "wrong architecture."

Am I doing something wrong, or am I unable to install this game because I'm using a new version of Ubuntu? Thanks.

---

### Post by TheFu on 2017-06-18
That chromebook is ARM, not Intel according to web searches.
Crouton is a chroot method, not a dual boot method, BTW.  It runs using the google ARM kernel.

Additionally, most programs have specific dependencies, so running a packaged program designed for 1 release on another usually means at least a few incompatible libraries are involved.

If you were running a normal Ubuntu, then using something like a "snap" would be an option. I don't know if this is viable for crouton or ARM-based programs. [https://www.ubuntu.com/desktop/snappy](https://www.ubuntu.com/desktop/snappy) has more info. I haven't read it.

---

### Post by wintersonata9 on 2017-06-19
Thanks for clearing those things up for me, TheFu.

I will probably abandon the Crouton idea and experiment with[ running Linux from a USB drive]("http://www.pcworld.com/article/2873561/google-just-made-it-easier-to-run-linux-on-your-chromebook.html") instead.

---

### Post by TheFu on 2017-06-19
Until the physical CPU is changed in the machine from ARM to x86, I don't think you will have any luck.  BTW, that isn't possible.

Of course, if you ever had the game running on the machine before then I'm completely wrong.

---

### Post by him610 on 2017-06-21
Hello wintersonato9,

Before you give up, you might want to read this article....[https://www.linux.com/learn/4-fine-linux-arm-distros]("https://www.linux.com/learn/4-fine-linux-arm-distros")

---

