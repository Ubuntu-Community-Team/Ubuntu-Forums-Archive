---
title: "Ubuntu Doesn't Support My Monitor Resolution?"
date: 2017-01-27
forum: New to Ubuntu
---

### Post by ryantwt on 2017-01-27
Hello, so I recently installed Ubuntu on my desktop computer. After installing I went to display settings to change my resolution. But after looking at the options I noticed my native resolution wasn't their. Is there a way to manual change it to what I want. Not sure if its relevant but my native res is 1280x768 and the brand is HP.

---

### Post by Autodave on 2017-01-27
Did you check for any drivers that are available for you video card? Go to Settings -> Software & Updates -> Additional Drivers. It will search and recommend any drivers it finds. Try the recommended one first: it is almost always the best choice.

---

### Post by ryantwt on 2017-01-27
Yes I just tried that, all it noticeably did was make my mouse cursor not existent.

---

### Post by mörgæs on 2017-01-27
Hi, welcome to the fora.

We need to know the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Impavidus on 2017-01-27
And which release of Ubuntu have you installed? 16.04 and 16.10 should be fine in most cases., but older releases may lack support for recent graphics hardware.

---

