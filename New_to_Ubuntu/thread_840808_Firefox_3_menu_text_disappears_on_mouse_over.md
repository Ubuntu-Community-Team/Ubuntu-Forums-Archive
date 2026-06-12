---
title: "Firefox 3 menu text disappears on mouse over?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-06-25
For some reason my Firefox 3 menu bar text disappears on mouse over:confused: i presume this has something to do with the text changing to the background colour? is there a fix for this?


Thanks in advance:lolflag:

also is there an add-on to change the menu background to an image?

---

### Post by kamitsukai on 2008-06-26
<bump>

---

### Post by Wicked-Cricket on 2008-06-27
Same issue here. I am now considering reinstalling Firefox to see if that clears it up. On my end, it seems to have started after I installed some add ons (themes, Adblock Plus, etc).... unfortunately I don't remember which, if any, caused the issue.

---

### Post by y-lee on 2008-06-27
> **kamitsukai said:**
> For some reason my Firefox 3 menu bar text disappears on mouse over:confused: i presume this has something to do with the text changing to the background colour? is there a fix for this?

That most likely has something to do with the theme you are using. Try changing themes. If that doesn't work create a new firefox profile and see if you have the same problem.

```
firefox -P
```

---

### Post by y-lee on 2008-06-27
> **kamitsukai said:**
> also is there an add-on to change the menu background to an image?

Don't know about an add on but there is an userchrome hack. I haven't tried it and besides I still use firefox 2.

See [Use a Background Image for Toolbars]("http://www.lifespy.com/2007/firefox-quick-tip-use-a-background-image-for-toolbars/")

Note this code changes several toolbars, I would say ya may be able to change it too

```
/*Use a custom background image for the toolbars:*/
menubar {background-image: url("background.gif") !important;background-color: none !important;}
```

to just effect the menu bar but i may be wrong. feel free to experiment. Good Luck.

---

### Post by Wicked-Cricket on 2008-06-29
Indeed, it was one of the add-on themes. A few work, a few don't. Simple fix though on my end. Good luck!

---

### Post by dodle on 2008-07-04
I'm having the same issue but haven't found a theme that fixes it.  Firefox 3 doesn't have many compatible addons.

---

### Post by crjackson on 2008-07-04
The same thing happens to me on all but a few themes.  The default theme works fine though.

---

### Post by Victormd on 2008-07-04
Of the themes I use, only the default theme works, all the others show this problem...

---

### Post by abu salma on 2009-05-19
tank it very useful for me i have same problem i try to fresh install firefox, and fail until i type firefox -P in my terminal. it just ok, tank for that suggest.

---

