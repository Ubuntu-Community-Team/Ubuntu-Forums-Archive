---
title: "BASH Scripts -- my first and ideas for more"
date: 2007-03-27
forum: Programming Talk
---

### Post by trevorv on 2007-03-27
Hiya!

I'm learning BASH scripting at the moment, and I've just written my first script to display a random background image -- I didn't like any of the existing scripts which did the same job, the ones I've seen seem to needlessly deal in temporary files and excess functions. Anyway, I thought I'd post it here, and ask anyone to point out anything wrong with it -- I don't want to get into bad habits this early!

```
#set $bgdir to dir containing background images                       
bgdir=~/images

#set $bgs to a list of background images                                      
bgs=($bgdir/*)

#set $bgnum to amount of backgrounds                                                   
bgnum=${#bgs[@]}

#set random number                                                  
random=$RANDOM
let "random %= $bgnum"

#set background image    
feh --bg-scale ${bgs[$random]}
```

Also, I was hoping you guys could suggest some interesting scripts to write that might actually come in useful, it's all well and good trawling through the examples in the books and howtos, but it's a lot more interesting if you get something out of it at the end.

Thanks!

---

### Post by Poisson_Pilote on 2007-03-27
What's that "feh" instruction you used ? :?

---

### Post by trevorv on 2007-03-27
> **Poisson_Pilote said:**
> What's that "feh" instruction you used ? :?

feh is an image viewer which can be used to display background images. I use a very minimal desktop (Rat Poison most of the time), and that's what I use for background images :-)

---

### Post by Poisson_Pilote on 2007-03-27
You should document line of codes using non standard programs like that. ;)

---

### Post by Mr. C. on 2007-03-27
This looks pretty good.

You should catch the case where bgnum = 0, otherwise:

```
let "random %= 0"     
-bash: let: random %= 0: division by 0 (error token is "0")
```

The "let" statement is very, very rarely used in shells scripts.  You can just use the arithmetic constructs:

```
(( random %= $bgnum ))
```

Here's a bunch of shell programming tutorials and solid problems (with answers if needed too) I created for students some years ago :

[https://sites.google.com/a/cappella.us/courses/](https://sites.google.com/a/cappella.us/courses/)

MrC

---

### Post by trevorv on 2007-03-28
> **Mr. C. said:**
> You should catch the case where bgnum = 0

Thanks for that, I'll add in a condition to check for that.

And thanks for the advice and links, they look useful at a glance, I'll have a more in depth read later :-)

Cheers!

---

### Post by zanzes on 2011-03-13
[http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

"can't find the server at cis68b1.mikecappella.com"

please update link

---

### Post by Vaphell on 2011-03-13
4 years, nice :D
why don't ubuntuforums lock threads automatically after n days/months/years of inactivity?

---

### Post by Mr. C. on 2011-03-13
I retired the site over a year ago, but moved the content at the request of others.

Link updated: [https://sites.google.com/a/cappella.us/courses/](https://sites.google.com/a/cappella.us/courses/)

---

### Post by zanzes on 2011-03-15
thx :)

---

