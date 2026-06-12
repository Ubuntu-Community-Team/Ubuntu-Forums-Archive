---
title: "Dropbox pins down my pc for the first 5 mins of booting!"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by vagelism on 2013-03-06
Hello to all.
I have an old pc, ACER TRAVELMATE 4070, just formatted and dual boot with win8 and Ubuntu 12.04 .
When the dropbox is activated and synchronize on my linux system it pins down my pc for the first 5 mins... the hard drive works like crazy and everything is slow down till the synchronization finish.
Even the dropbox folder doesn't have any changes from the last boot! The same procedure on windows boot takes about a min with no significant delay.
I find this strange since the linux system is by far more stable and fast except this little part. Any one has the same experience and any solution?
Thank you for your replies!

---

### Post by gordintoronto on 2013-03-06
My laptop is no powerhouse, but it synchs Dropbox "instantly."

How much memory do you have? How much is being used? Is it possible that the delay is due to paging?

---

### Post by vagelism on 2013-03-07
> **gordintoronto said:**
> My laptop is no powerhouse, but it synchs Dropbox "instantly."

How much memory do you have? How much is being used? Is it possible that the delay is due to paging?

My laptop is six years old! It has 2 GBytes of memory! When it is idle I have usage of memory about 12%.

---

### Post by black veils on 2013-03-07
set it to have a delayed start, either edit the current startup application or remove it and create a new one with the launch command as ```
sh -c "sleep 5m; dropbox start -i"
```change 5 to what you would prefer.

maybe also something else is in your startup applications causing the slowness?

---

### Post by vagelism on 2013-03-07
Where do I have to put this line ?

---

### Post by black veils on 2013-03-07
search startup applications, then look for dropbox

---

