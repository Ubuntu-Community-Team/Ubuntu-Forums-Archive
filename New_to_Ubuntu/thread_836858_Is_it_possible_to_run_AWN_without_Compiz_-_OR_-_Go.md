---
title: "Is it possible to run AWN without Compiz - OR - Google Earth with Compiz???"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by the8thstar on 2008-06-21
Hello,

I use AWN as my dock. I enjoy it very much, however it seems to work only when Compiz is enabled.

If Compiz is enabled, Google Earth flickers alot, to the point that it's almost impossible to see anything in the window. However Google Earth works seamlessly with Metacity.

So, my questions are:

1. Is there a way to run AWN without Compiz?
2. Is it possible to run Google Earth "normally" with Compiz enabled?

Thanks for your help.

---

### Post by Vadi on 2008-06-21
1. Is there a way to run AWN without Compiz?

I don't believe so, but I think AWN is working on that

2. Is it possible to run Google Earth "normally" with Compiz enabled?

Yes, if you have a different video card. afaik that issue affects some intel / ati cards. Google Earth has no flickering on nVidia.

---

### Post by Victormd on 2008-06-21
No, you need a composite manager for AWN to run...

---

### Post by moonbeam on 2008-06-21
> **the8thstar said:**
> Hello,

1. Is there a way to run AWN without Compiz?


Yes. Compiz is not required.  All you need is a compositor.

An incomplete list.
1) Compiz... of course
2) Metacity (v2.22+).... just enable the composite support.  IMO it's still not as good as xfwm4 support.
3) Xfwm4.... just enable the composite support.
4) xcompmgr...  more or less works fine even though it's just proof of concept code.
5) kwin4 should work also... 
6) Some people have luck with cairo compmgr...  Depending on the platorm it may or may not be stable.

My suggestion is try out metacity composite support.

gconftool &#8211;type=bool -s /apps/metacity/general/compositing_manager 1

to enable

and

gconftool &#8211;type=bool -s /apps/metacity/general/compositing_manager 0

to disable

If that acts up for you then try xcompmgr.

---

### Post by the8thstar on 2008-06-22
Thanks guys.

Well, I'm in the pit if this a graphics related issue. I tried:

> gconftool –type=bool -s /apps/metacity/general/compositing_manager 1

but it doesn't change anything, even after a restart: AWN doesn't show up. I guess I have to install xcompmgr. Are there any drawbacks though?

---

### Post by the8thstar on 2008-06-26
Okay, I installed. The problem remains.

---

### Post by the8thstar on 2008-06-28
Bump

---

### Post by Zopiac on 2008-06-28
i cant get google earth to install with compiz either (havent tried w/o)

---

### Post by oldos2er on 2008-06-28
Yes, it's possible to run Googleearth with compiz-fusion; i do it all the time.

 How are you trying to install Googleearth? What if any error messages do you get?

---

### Post by lunatico on 2009-03-22
Anyone figured out how to run googleearth without having to disable compiz?

---

### Post by Bölvaður on 2009-03-22
yes I got it working by buying more powerful graphical card.

---

### Post by lunatico on 2009-03-22
> **Bölvaður said:**
> yes I got it working by buying more powerful graphical card.

I don't think hardware is my problem as it worked fine on 8.04...

---

### Post by Bölvaður on 2009-03-22
ok run google from terminal to see the error it spews out.
I would guess it has something to do with ssl -.-

---

