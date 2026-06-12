---
title: "xorg:  resetting defaults; how to"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-07-27
I`ve caused some funny keyboard changes that I think resulted from fiddling with xorg. (ie: SHIFT + 2 = " instead of at symbol; some others too)
So I think there is a way to reset the keyboard to the default I used to have but can`t remember how.  (fyi: North American standard laptop keyboard)
thanks.

---

### Post by Locutus_of_Borg on 2008-07-27
```
dpkg-reconfigure xserver-xorg
```
might help...

---

### Post by flyingsolo on 2008-07-27
I think this is what I need but can you tell me is the standard laptop keyboard pc101 or pc104.

---

### Post by Locutus_of_Borg on 2008-07-27
they are both essentially the same i believe

i am using 104 and i live in the US and have no problem with anything

---

### Post by flyingsolo on 2008-07-27
I think I just fixed it; I had tried the reconfiguring and testing it which seemed not to work but after a restart, it looks like the settings have 'taken'.  I had chosen pc104.
(ps:  in my last post above, I couldn't use a question mark to end the question but, see (?) now it works & so does the @ symbol!  Yeah!)

Thank you

---

