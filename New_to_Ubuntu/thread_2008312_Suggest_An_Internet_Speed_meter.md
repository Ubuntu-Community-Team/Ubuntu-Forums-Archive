---
title: "Suggest An Internet Speed meter"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by rafsuntaskin on 2012-06-22
Hello there I would like to know from you guys that is there any **internet speed checking utility** for ubuntu **12.04** like **DU meter** of windows, that keeps telling you the curent **bandwith usage** of your COmputer.

Thanks in advance ):P

---

### Post by SlugSlug on 2012-06-22
iftop
nethogs
iptraf


or config conky :)

---

### Post by blackbird34 on 2012-06-22
For a quick graphical tool, there is the "System Load Indicator", it's an indicator applet that can be found in the Software Center I think (if not so, definitely  in a ppa).
Or else ```
 sudo apt-get install indicator-multiload
```

Reports on net bandwidth (up and down), CPU, Ram, and a few other things...

---

### Post by rafsuntaskin on 2012-06-22
> **SlugSlug said:**
> iftop
nethogs
iptraf


or config conky :)


okay I tried Conky I have installed conky through software center, But I can't use it  :mad:

---

### Post by The Cog on 2012-06-22
> **SlugSlug said:**
> iftop
nethogs
iptraf


or config conky :)

or etherape

---

### Post by Henkdroid on 2012-06-22
> **rafsuntaskin said:**
> okay I tried Conky I have installed conky through software center, But I can't use it  :mad:
Conky's a bit funny. You need to run it in a Terminal and then a window will pop up. It's a useful tool and you should probably read up on it. You can monitor pretty much anything. If you use compiz (unity 3D) then you can make compiz run on the widget layer, so if you press f9 then it will show you it and it doesn't get in your way.

---

