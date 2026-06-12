---
title: "Image file size in real life website."
date: 2010-02-10
forum: Programming Talk
---

### Post by aklo on 2010-02-10
Just wonder if every byte counts in a real working website?

I am doing a template and i am deciding whether to simply use the entire menu picture which is like 1.6KB or should i cut out a 1px width x image height and then do background-repeat

Is the bandwidth saved worth it? I mean 1.6KB is definitely small enough but if i cut and do a repeating background, my image will be like under 1KB...which is better?

---

### Post by Grenage on 2010-02-10
Efficiency is great, but not as important as it used to be (consider the mass of junky flash s[s]h[/s]ites).  A couple of Kb won't make much difference; prioritise on cross-browser compatibility and easy of management.

---

### Post by Hellkeepa on 2010-02-10
HELLo!

I'd go for the repeat, not because of the bandwidth saved, but because it'd allow for a dynamic layout. Fixed sized images for backgrounds, and such, tends to give an aburpt and ugly end on different circumstances.

Happy codin'!

---

### Post by hessiess on 2010-02-10
If you only need 1 pixel of height, get rid of the rest of the image and tile it.

---

### Post by aklo on 2010-02-10
Thanks for the suggestions but i think i will go for using the entire image as a menu since i have rounded corners, to title the background, i will have to again cut seperate image for the 4 corners which is more troublesome.

---

### Post by Hellkeepa on 2010-02-11
HELLo!

Using the Sliding Doors technique, the rounded corners are easy to accomplish. You'll find lots of elegant techniques if you search for "rounded corners css".

Happy codin'!

---

