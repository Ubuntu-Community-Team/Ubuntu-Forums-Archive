---
title: "How can i get the results of a directory listing in a bash variable?"
date: 2012-10-09
forum: Programming Talk
---

### Post by sefs on 2012-10-09
Hi there

How can i get the result of:

ls /sys/class/net | grep wlan

into a bash variable wX

Thanks.

---

### Post by greenpeace on 2012-10-09
Hi!

Use the backtick (`) character around the command:

```
gp@mariachi:~$ wX=`ls /sys/class/net | grep wlan`
gp@mariachi:~$ echo $wX
wlan0
```

hope that helps

---

### Post by DarkAmbient on 2012-10-09
```

wX=`ls /sys/class/net | grep wlan`
```

edit: greenpeace was a little faster =)

---

### Post by MG&amp;TL on 2012-10-09
Pedantic note: it's better to use $( ) rather than backticks: [http://mywiki.wooledge.org/BashFAQ/082]("http://mywiki.wooledge.org/BashFAQ/082")


As you were!

---

### Post by greenpeace on 2012-10-09
> **MG&TL said:**
> Pedantic note: it's better to use $( ) rather than backticks: [http://mywiki.wooledge.org/BashFAQ/082]("http://mywiki.wooledge.org/BashFAQ/082")

oh cool... didn't know that one!  Excellent pedantic noting, sir!

---

### Post by sefs on 2012-10-09
Thanks fellas :P

---

