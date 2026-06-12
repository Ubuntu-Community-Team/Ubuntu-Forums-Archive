---
title: "Remove window borders"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by crowhill on 2008-09-21
Hi there

On my laptop, I can remove the window borders by going to the settings in Compiz and then to the windows decoration menu (choose no decoration).

On my desktop PC at work, I'd like to remove the windows borders as well. Unfortunately, there, I don't have Compiz (no graphics card).

Is there a way to remove the window borders without having Compiz?

Thanks a lot in advance,
cheers,
crowhill.

---

### Post by billgoldberg on 2008-09-21
> **crowhill said:**
> Hi there

On my laptop, I can remove the window borders by going to the settings in Compiz and then to the windows decoration menu (choose no decoration).

On my desktop PC at work, I'd like to remove the windows borders as well. Unfortunately, there, I don't have Compiz (no graphics card).

Is there a way to remove the window borders without having Compiz?

Thanks a lot in advance,
cheers,
crowhill.

I don't know if you can remove the metacity window borders.

--

If you really want that feature, but the pc can't handle compiz fusion, I suggest you try out fluxbox (link to guide in signature) or openbox.

With those it's easy to do.

---

### Post by crowhill on 2008-09-21
Thanks a lot for this message. However, I have no intention to leave Gnome since I came to like it quite a lot.

Thanks anyway.

Cheers,
crowhill.

---

### Post by Sorivenul on 2008-09-21
> **crowhill said:**
> Thanks a lot for this message. However, I have no intention to leave Gnome since I came to like it quite a lot.

You can use both OpenBox and Fluxbox in Gnome as the window-manager instead of Metacity, I believe.  Simply install one (or both), then:
```
fluxbox --replace
```
Or replace "fluxbox" with "openbox".  To get back to the way things were, just use:
```
metacity --replace
```
Voila, the best of both worlds!

---

### Post by Noob Programmer on 2009-08-27
Did you ever get this working without a graphics card?

---

### Post by crowhill on 2009-08-27
hi there

indeed, i (or rather somebody else) did. somebody managed to create a simple theme (that i slightly modified) for metacity that does the trick. see the attachment.

cheers,
crowhill.

---

### Post by Noob Programmer on 2009-08-27
Perfect. How would I apply this to a single window?

---

### Post by crowhill on 2009-08-27
i'm sorry, i don't know about that. it's either all windows or none. this is what i have and i'm doing perfectly fine with it - i love it. you'll get used to it and you'll wonder why people waste space with any boarders at all :)

---

