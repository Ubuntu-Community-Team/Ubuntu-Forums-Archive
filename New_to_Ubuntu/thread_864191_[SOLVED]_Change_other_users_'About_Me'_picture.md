---
title: "[SOLVED] Change other users 'About Me' picture"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by ubername on 2008-07-19
Hi

I have a handful of users (family) on my machine and in the process of 'fixing' the machine I have managed to lose all their 'About Me' settings. Any clues how I can restore, or, running as Admin, somehow edit their configs to reset, e.g. the pictures that show on the login list (I use a login screen with faces). I guess I am asking where these data are stored. I could just login to each account but that seems the cowards way out!

TIA

---

### Post by Vivaldi Gloria on 2008-07-19
> **ubername said:**
> Hi

I have a handful of users (family) on my machine and in the process of 'fixing' the machine I have managed to lose all their 'About Me' settings. Any clues how I can restore, or, running as Admin, somehow edit their configs to reset, e.g. the pictures that show on the login list (I use a login screen with faces). I guess I am asking where these data are stored. I could just login to each account but that seems the cowards way out!

TIA

I think they are stored in the /home/<username>/.face where .face is a jpg or png or ...

---

### Post by ubername on 2008-07-19
> **Vivaldi Gloria said:**
> I think they are stored in the /home/<username>/.face where .face is a jpg or png or ...

Thanks, It took me a minute to understand your advice ( I was looking for a folder called .face) but I've got it now!

---

### Post by Vivaldi Gloria on 2008-07-19
> **ubername said:**
> Thanks, It took me a minute to understand your advice ( I was looking for a folder called .face) but I've got it now!

You're welcome.

---

### Post by ubername on 2008-07-19
> **Vivaldi Gloria said:**
> You're welcome.

Perhaps I still need to learn some more.

I did

fred@machine:/usr/share/pixmaps/faces$ sudo cp energy-arc.jpg /home/dave/.face

and although there is now a file called .face in /home/dave it doesn't want to work with the 'faces' login (I still see the default picture)

---

### Post by ubername on 2008-07-19
> **ubername said:**
> Perhaps I still need to learn some more.

I did

fred@machine:/usr/share/pixmaps/faces$ sudo cp energy-arc.jpg /home/dave/.face

and although there is now a file called .face in /home/dave it doesn't want to work with the 'faces' login (I still see the default picture)

Sorted, it was a permissions thing (for some reason the various copied pictures had permissions associating them with (apparently random) other users).

---

### Post by Vivaldi Gloria on 2008-07-19
> **ubername said:**
> Sorted, it was a permissions thing (for some reason the various copied pictures had permissions associating them with (apparently random) other users).

Well, you scared me there for a moment. I was looking left and right to find out why it's not working. ;) Anyway, glad that it's working now.

---

