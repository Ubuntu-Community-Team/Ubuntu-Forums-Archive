---
title: "System Monitor?"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-31
Hi,

Is there any app  that displays system internals like swap, CPU temps, HDD health etc?

Thanks.

---

### Post by dniMretsaM on 2012-11-01
There should be a program called "System Monitor" installed.

---

### Post by Yezinki on 2012-11-01
Thanks dniMretsaM.

I mean some thing on screen display like conky I think.....?

---

### Post by zombifier25 on 2012-11-01
If you don't want to use Conky, there's Screenlets, which are easy to setup, albeit not as customizable as Conky, but it should do what you want.

---

### Post by Yezinki on 2012-11-01
Thanks zombifier25 for your expert reply.

How do I install Screenlets?

---

### Post by jerome1232 on 2012-11-01
I use the simple indicator-multiload, it puts a very simple graph in your top panel.

See the attached screenshot, mine just shows memory and cpu usage, but you can display more than that.

---

### Post by Yezinki on 2012-11-01
Thanks jerome1232, but how does one install it?

---

### Post by jerome1232 on 2012-11-01
Pop open a terminal with ctrl+alt+t, type in the below code (or just copy paste it), it will prompt for password just type it in, it won't echo back astrisks or anything that's normal. Once installed you can search in your dash for it to run it. Once again this isn't anything fancy smancy, it's simple and out of the way.

```
sudo apt-get install indicator-multiload
```

If you decide you like it set it to auto run by clicking the cog in the upper right corner of your screen, clicking startup applications,  new, type in "Sytem Monitor" for the name and "indicator-multiload" for the command, click save.

---

### Post by Yezinki on 2012-11-01
Thanks & it's nice, very compact. How accurate is it?

---

### Post by jerome1232 on 2012-11-01
> **Yezinki said:**
> Thanks & it's nice, very compact. How accurate is it?
 
/shrug, seems to correspond well to what any other system monitor shows me.

top, htop, and Ubuntu's system monitor all agree roughly with indicator-multiload, it's seem to estimate the ram usage slightly higher than the rest of them, but I'm not exactly using it for pinpoint precision either, it's just a graph I can keep an eye on in the corner of my screen.

---

### Post by Yezinki on 2012-11-01
This is how screenlets looks but has a lot of crap with it lol

```
sudo apt-get install screenlets
```

---

### Post by Yezinki on 2012-11-01
@ zombifier25 any app more specific than Screenlets?

Thanks.

---

### Post by HiImTye on 2012-11-01
what specifically don't you like about conky?

---

### Post by Yezinki on 2012-11-01
Similar kind of a display with temps........

Thanks.

---

