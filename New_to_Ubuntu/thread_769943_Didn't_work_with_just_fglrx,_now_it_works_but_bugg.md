---
title: "Didn't work with just fglrx, now it works but buggy and super slow with fglrx + xgl"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by rmksd on 2008-04-27
So for awhile now I really wanted to try Ubunut but since Feisty I've been trying to get Compiz[Fusion] to work with no such luck. When Heron came out I figured I might have another go at it since I remember hearing something about the ati fglrx drivers allowing easy access to compiz fusion effects.
But whenever I tried the Ati driver 
via System > Administration > Hardware Drivers
&
via Envy

Using either one the screen would blip then turn white when turning on desktop effects or typing compiz in terminal.

So I read that some have had luck with enabling "xserver-xgl" so I did and now desktop effects DO work BUT it's super slow as well as buggy when I first login (I get a black screen and an 'X' cursor for a moment after login)

this is the output when I enable compiz in terminal:
```
ken@RMKSD:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

and it would probably help if I also state that my graphics card is an ATI r9550

any ideas? :confused:

---

### Post by 123456789123456789123456 on 2011-03-25
I was going to ask the version of ubuntu, but from the date I am guessing it was 8.04.  have you upgraded since then?  is it still giving problems?
I know 10.10 has the drivers a little better, and 11.04 is supposed to be even more compatable.

---

### Post by 5149.5 on 2011-03-25
Holy necro-thread batman.

---

### Post by overdrank on 2011-03-25
Thread closed :)

---

