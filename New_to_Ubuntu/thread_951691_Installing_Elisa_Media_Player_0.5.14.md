---
title: "Installing Elisa Media Player 0.5.14"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by vtech81 on 2008-10-18
There's a .tar.gz on the Elisa website. I've extracted it, but there's no install file. There's a readme, but it doesn't say how to install (and if it does then I'm to stupid to have seen it). I've tried using a terminal to install it, didn't work. I know I could easily install the older version, but it's a little buggy IMO. Btw, I'm running Ubuntu 8.04.

---

### Post by cariboo on 2008-10-18
The file you are looking for is called:

```
setup.py
```

You will need to be root to install the program:

```
sudo ./setup.py
```

Make sure you have all the dependencies installed that are listed in the readme file.

Jim

---

### Post by vtech81 on 2008-10-18
Thanks. It didn't work at first, but going into the readme I found that the correct code was 

$ sudo python setup.py install

But now for some reason, when I try to open Elisa, the splash screen shows up for a couple seconds, but it will not start.

---

### Post by Paqman on 2008-12-18
The Elisa developers have their own mini repo (called a ppa) that will give you the very latest version.

Add this to System > Admin > Software Sources > 3rd Party > Add:
```
deb http://ppa.launchpad.net/elisa-developers/ubuntu hardy main

```

Reload your repos and you should be able to get Elisa through Add/Remove or Synaptic.

---

