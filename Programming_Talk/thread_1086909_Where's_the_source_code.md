---
title: "Where's the source code?"
date: 2009-03-04
forum: Programming Talk
---

### Post by Znupi on 2009-03-04
I'm trying to find the source code for any of these: top, gnome-system-monitor or the system monitor gnome panel applet. It seems I am unable to do that (I really don't know where to search -- tried Google but to no avail). Why I'm trying to do this is because I want to create a better alternative to `free'. For this, I need to know if there's any other way of reading available / used / total RAM (and maybe swap) memory than parsing **/proc/meminfo**.
Thanks.

---

### Post by Majorix on 2009-03-04
What about the output from executing "free"?

---

### Post by Tibuda on 2009-03-04
You can download the source code for any program in the repositories with apt-get source:```
apt-get source packagename
```

---

### Post by Znupi on 2009-03-04
> **danielrmt said:**
> You can download the source code for any program in the repositories with apt-get source:```
apt-get source packagename
```
Thanks! I still can't find the source code for top or free, but I am able to find the source code for gnome-system-monitor. Do you have any idea where I can find the source code for top? If not, I'll just have to dig in the system monitor source :D

**Majorix:** did you read my post? I want to build a better alternative to free, or maybe even improve it (if there's no other way to read the free memory than parsing /proc/meminfo). What I don't like about it is the way it rounds up numbers when using different switches. And I would like to add a "-h" option (like ls -h) that would display sizes in a "human-readable" format.

---

### Post by cabalas on 2009-03-04
You can find top at sourceforge here: [http://sourceforge.net/projects/unixtop/](http://sourceforge.net/projects/unixtop/)

---

### Post by geirha on 2009-03-04
```

$ which top              # To get the full path of the command
[COLOR="Green"]/usr/bin/top[/COLOR]
$ dpkg -S [COLOR="Green"]/usr/bin/top[/COLOR]   # Search for the package that installs that file
[COLOR="Blue"]procps[/COLOR]: /usr/bin/top
$ apt-get source [COLOR="Blue"]procps[/COLOR]  # Get the source

```

---

### Post by Znupi on 2009-03-04
Wow, thanks for the tips everyone! :)

---

### Post by monkeyking on 2009-03-04
just out of curiosity what do you want to add to top?

I think /proc/meminfo is the base of every other memory monitor program on linux.
The same with /proc/cpuinfo

---

