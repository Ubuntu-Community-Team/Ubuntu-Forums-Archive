---
title: "[SOLVED] kdevelop autoconf error"
date: 2007-10-11
forum: Programming Talk
---

### Post by andrewoftheelves on 2007-10-11
hello, i am very new to programming, I have ubuntu studio mix. so i downloaded kdevelop through add/remove, and started it, went to new programms=>c++ => kde=> simple kde application, filled everything out, and then when i do build/ run automake and friends i get this message:

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

I tried installing autoconf through the synaptic package manager, but i still cant get it to work, if anyone could help i would greatly appreciate it.

---

### Post by LarsO on 2008-02-12
I was struggling with the same problem for a while and found that this solved it:
sudo apt-get install libtool
sudo apt-get install automake

---

