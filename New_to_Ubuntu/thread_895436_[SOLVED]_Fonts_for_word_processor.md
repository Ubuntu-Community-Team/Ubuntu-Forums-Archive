---
title: "[SOLVED] Fonts for word processor?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Camilia on 2008-08-20
I am having trouble finding a font for the word processor that gives lines spacing as when I am writing here. Anybody got any suggestions?

---

### Post by mlentink on 2008-08-20
I'm not sure I understand what you mean.
Which word processor? Most wordprocessors will allow you to specify the amount of spacing (either in points or lines) between lines. Such spacing would apply to all installed fonts.

---

### Post by Camilia on 2008-08-20
> **mlentink said:**
> I'm not sure I understand what you mean.
Which word processor? Most wordprocessors will allow you to specify the amount of spacing (either in points or lines) between lines. Such spacing would apply to all installed fonts.

I am using the open office.org wordprocessor. I have noticed different fonts have different spacing, thus thought it was the font I needed.

Help of the processor for line spacing gives me this:
To access this command... 
Open context menu - choose Line Spacing - Single 
I don't see this? Where is it?
Is there a way to get fonts that are in windows for ubuntu?

---

### Post by Elfy on 2008-08-20
You can install msttcorefonts, either search in synaptic and install there or open a terminal and run
```
sudo apt-get install msttcorefonts
```

Which will install a lot of the ms fonts

---

### Post by Camilia on 2008-08-20
> **forestpixie said:**
> You can install msttcorefonts, either search in synaptic and install there or open a terminal and run
```
sudo apt-get install msttcorefonts
```

Which will install a lot of the ms fonts

It didn't work. Can't find anything in synaptic. Searched for msttcorefonts, fonts, ms.

---

### Post by kpkeerthi on 2008-08-20
> **Camilia said:**
> It didn't work. Can't find anything in synaptic. Searched for msttcorefonts, fonts, ms.

Do you have 'Multiverse' repository enabled under System -> Admin -> Software Sources?

EDIT: [http://packages.ubuntu.com/hardy/msttcorefonts](http://packages.ubuntu.com/hardy/msttcorefonts)

---

### Post by Camilia on 2008-08-20
Clicked this link apt://msttcorefonts given by Separ and now have the fonts.

One more problem with open office processor.
Now when I type I get a - between the words. Tried to get rid of it in tools.

---

