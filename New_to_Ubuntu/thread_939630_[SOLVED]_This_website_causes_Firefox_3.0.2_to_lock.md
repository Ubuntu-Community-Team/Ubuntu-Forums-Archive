---
title: "[SOLVED] This website causes Firefox 3.0.2 to lock up - Any help?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by crjackson on 2008-10-06
[http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

I just did a clean install of 8.04.1 yesterday and can't read this page. It locks up right after loading.

I tried using the Flock browser too with same results.

Any ideas what could be causing this?

---

### Post by SteelCore on 2008-10-06
I'm using 8.04 and it opened normally with me.

---

### Post by lazyart on 2008-10-06
Works fine with 3.0.3 64bit.... Update your system and try again?

---

### Post by t0p on 2008-10-06
I'm using FF 3.0.3 on Hardy and it loads that page fine.  So an upgrade from 3.0.2 to 3.0.3 might be the solution...

If you start firefox by opening a terminal and typing in

```
firefox
```

then going to that webpage: when ff freezes, you might get some useful output in the terminal.

---

### Post by crjackson on 2008-10-06
Actually that was a typo - it is 3.0.3

---

### Post by crjackson on 2008-10-06
> **t0p said:**
> I'm using FF 3.0.3 on Hardy and it loads that page fine.  So an upgrade from 3.0.2 to 3.0.3 might be the solution...

If you start firefox by opening a terminal and typing in

```
firefox
```

then going to that webpage: when ff freezes, you might get some useful output in the terminal.

I'll give that a try tonight.

---

### Post by crjackson on 2008-10-06
> **lazyart said:**
> Works fine with 3.0.3 64bit.... Update your system and try again?

it's completly updated already.

---

### Post by crjackson on 2008-10-06
The only thing I've done besides updating is an icon theme and a browser theme. Could either of those cause the problem?

Funny thing is that it does this in Flock browser too where there is no theme change.

It's hard to think that system icon themes could cause this...

---

### Post by crjackson on 2008-10-07
SOLVED - 

This is strange.  The fix was to change the system theme which fixed it. Then I switched back and problem was back. Then I just changed away from the MacUltimate icon theme to Human and problem went away again.

THEN - I switched back to the MacUltimate icon theme and the problem was STILL GONE.

Now it's working fine, and I'm using the Icon theme I want.  It seems that after installing the icon theme, I need to switch away from it, and then back again to avoid the problem.  I don't know why it works, but it does.

Thanks

---

