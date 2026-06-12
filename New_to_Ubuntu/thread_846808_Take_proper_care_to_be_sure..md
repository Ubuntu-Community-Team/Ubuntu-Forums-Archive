---
title: "Take proper care to be sure."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by JillSwift on 2008-07-01
[CENTER][B][U][SIZE=3]From the *"Learn from my mistakes"* department:[/SIZE]
[/U][/B][/CENTER]

GNU/Linux command line programs are very powerful things that happily do exactly what you tell them to.

So, when I decided to move all the files from subdirectories into the next directory up (while re-organizing a collection of videos I've made over the years) I used the following command:

mv ./*/* ./
[SIZE=1][COLOR=Silver](move all files from all subdirectories in the current directory into the current directory)[/COLOR][/SIZE]

I really should have made use of the following command *first*:

pwd
[SIZE=1][COLOR=Silver](print working directory, ie. what is the current directory?)[/COLOR][/SIZE]

since, as it turns out, my current directory was not [COLOR=DarkRed]~/Videos/projects/raw[/COLOR], but was instead [COLOR=DarkRed]~/[/COLOR]

ouchies.

Just hoping to spare you my pain =^_^=

---

### Post by tjwoosta on 2008-07-01
ouch indeed

---

### Post by camccall on 2008-07-01
Ouch!

---

