---
title: "Gdm  group not known"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Blackcabs on 2008-10-05
Can anyone help, recently i went to reboot my system and for some reason unbeknown  to me, i got a message saying gdm group unknown please correct gdm and reboot. Now i can only boot into a command prompt window and i have no desktop, i have searched for the gdm files with nano from the command prompt window, but i am told no gdm files exist. I am totally lost and have no idea what to do,, please can anyone help :confused:

---

### Post by shifty_powers on 2008-10-05
from [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/6931](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/6931)

apt-get remove gdm

(change my /etc/apt/source.list to point to the "stable" debian release)

apt-get install gdm

---

### Post by Blackcabs on 2008-10-13
Thanks for the reply Shifty but in the end i had to reload the operating system as the gdm group wasn't the only one reporting errors, Did not lose any data so im happy enough

---

