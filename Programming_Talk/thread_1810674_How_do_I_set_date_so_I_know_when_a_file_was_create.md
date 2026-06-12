---
title: "How do I set date so I know when a file was created"
date: 2011-07-23
forum: Programming Talk
---

### Post by anden.d on 2011-07-23
Hi
I've been working with a script in ubuntu 11.04 it's basicly very simple but I got problem with a single line of code: cat /etc/passwd > passwd´date +%Y%m´
The results I expect should be  a readable  file something like this example: passwd201106
Do you know what I have done wrong or do you have a better solution?
I'm a more used to red hat 2.0 so i wounder if it's just a minor difference between two linux systems?:confused:

---

### Post by Bachstelze on 2011-07-23
You are using the wrong kind of "apostrophes":

```
firas@itsuki ~ % cat /etc/passwd > passwd`date +%Y%m`
firas@itsuki ~ % ls passwd*       
passwd201107

```

You can also use $(), which is less confusing:

```
firas@itsuki ~ % rm passwd201107
firas@itsuki ~ % cat /etc/passwd > passwd$(date +%Y%m)
firas@itsuki ~ % ls passwd*
passwd201107

```

---

### Post by anden.d on 2011-07-23
Thank you Newbie mistake but i't would probably take me days to figur it out thanks once again!:D

---

