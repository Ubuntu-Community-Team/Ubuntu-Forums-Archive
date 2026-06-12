---
title: "Change background GDM + after login"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by helino on 2008-04-27
Hi, I was wondering if there's an easy way to change the background at the login window? I was also wondering if it's possible to change the brown color after login to your wallpaper?


Thanks for your help!

---

### Post by KillerKiwi on 2008-04-27
> **helino said:**
> Hi, I was wondering if there's an easy way to change the background at the login window? I was also wondering if it's possible to change the brown color after login to your wallpaper?


Thanks for your help!

GDM is controlled by themes.. see System -> Administration -> Login Window

There are extra themes in synaptic search for "gdm"

---

### Post by helino on 2008-04-27
Thanks for the answer, I've managed to find a theme and change the background to my own wallpaper. I'm still wondering if it's possible to have your wallpaper instead of the brown color once you logged in, but still haven't loaded the desktop?

---

### Post by rubicon on 2008-04-27
Reread your post :) 

You ask to have wallpaper on your desktop *before* your desktop loads ;)

---

### Post by fallenshadow on 2008-04-27
This problem is sorted in the 8.04 release so I am presuming that you are using Ubuntu 7.10 because I think I had the same problem.

Copy and paste this into a terminal:

```
sudo gedit /etc/gdm/PreSession/Default
```

Then change Backcolor to #000000 for black or put in a different value if you like. Gcolor2 can help you find the values for other colours. Install from "Add/Remove".

I hope that helps.

---

### Post by forrestcupp on 2008-04-27
I know what you're saying, and no, that's not possible.  The best you could do is change the solid color to something closer to your wallpaper instead of that brown color.

---

### Post by helino on 2008-04-27
I'm using 8.04. Isn't it possible to load some really lightweight application like feh in my initrc and let it show a picture?

---

### Post by chris.olsen on 2008-04-27
> **helino said:**
> I was also wondering if it's possible to change the brown color after login to your wallpaper?

I am also trying to change the ugly light brown that appears after logging in.  I have tried to change it in the login settings, but the color update does seem to save, because after I close the window, and reopen the login setting it is back to the light brown.

I have changed the default value in the PreSession/Default, but that doesn't seem to work either.

Thanks for the help.

---

### Post by kmack1023 on 2008-06-03
still no luck on this?  I was curious about it too after installing a much prettier login window than the ubuntu default...and even seeing that ugly brown for just a second is enough to make me throw up in my mouth a little bit...  (ok that's just me exaggerating...)

---

### Post by luisjorge on 2008-06-13
Hi everyone! This is the answer: [http://ubuntuforums.org/showthread.php?t=753261&highlight=wallpaper+on+login](http://ubuntuforums.org/showthread.php?t=753261&highlight=wallpaper+on+login)

I use it myself and works like a charm. I think it's what you're looking for.

Luis Jorge.

---

### Post by helino on 2009-04-14
A little bit late, but thanks a lot for your answer! This should definitely be the default behavior when logging in, the login experience feels much more consistent.

---

