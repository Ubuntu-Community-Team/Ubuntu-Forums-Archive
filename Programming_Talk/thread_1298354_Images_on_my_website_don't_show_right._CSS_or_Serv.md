---
title: "Images on my website don't show right. CSS or Server problem?"
date: 2009-10-22
forum: Programming Talk
---

### Post by sideffects on 2009-10-22
Hi, I'm currently working on a website and the images (in *.gif format if it matters) appear as what I would describe as white noise. The thing is, however, not all of them appear this way. Does anyone know what could be causing this? I've been working on it ALL DAY! Thanks in advance for any help!
I've attached screenshots for reference. Thanks!

---

### Post by Can+~ on 2009-10-22
I can't see what you mean with "white noise" in the picture.

Are the images supposed to be transparent? Because .gif can only handle binary transparency (transparent, or not), so most graphic editors fill the half-transparent with a solid color, usually white.

Try using png-32 with Transparency enabled.

---

### Post by OpenGuard on 2009-10-23
What's the url of your website ( thumbnail is too small to see what's going on there ) ?

---

### Post by sideffects on 2009-10-23
> **OpenGuard said:**
> What's the url of your website ( thumbnail is too small to see what's going on there ) ?
Sorry, it doesn't look like that anymore. The same effect isn't happening since I converted the gifs to pngs. Does anyone know why that would make a difference?

---

### Post by Zugzwang on 2009-10-23
> **sideffects said:**
> Sorry, it doesn't look like that anymore. The same effect isn't happening since I converted the gifs to pngs. Does anyone know why that would make a difference?

Probably you have chosen "dithering" or something like that for colour reduction (GIF images only have 256 colours).

---

### Post by sideffects on 2009-10-23
> **Zugzwang said:**
> Probably you have chosen "dithering" or something like that for color reduction.

Where would I have chosen that?

---

### Post by Zugzwang on 2009-10-23
> **sideffects said:**
> Where would I have chosen that?

Depends on the program used. When using GIMP, for example, you get a warning when saving a 24-bit colour picture as a GIF file. This warning can be circumvented by reducing the colour number using the command in the menus beforehand. When doing so, a windows pops up with options on the conversion.

---

### Post by sideffects on 2009-10-23
> **Zugzwang said:**
> Depends on the program used. When using GIMP, for example, you get a warning when saving a 24-bit colour picture as a GIF file. This warning can be circumvented by reducing the colour number using the command in the menus beforehand. When doing so, a windows pops up with options on the conversion.

Okay, but I downloaded the template.

---

### Post by sideffects on 2009-10-23
You can see what I mean by going to [http://jibbli.com/test/](http://jibbli.com/test/)

---

### Post by Can+~ on 2009-10-23
Seems like corrupted files.

Where did you download this template?

---

### Post by OpenGuard on 2009-10-23
[CLICK HERE]("http://jibbli.com/test/images/right-top-corner.gif") - don't waste your time .. it have nothing to do with CSS or any other scripting/programming/markup language.

---

### Post by sideffects on 2009-10-23
> **Can+~ said:**
> Seems like corrupted files.

Where did you download this template?
Template Monster.
The stupid rep won't answer my questions. Idiot.

---

### Post by prasadchalasani on 2009-10-23
yeah **Can+~** is right. graphics are **corrupted**. when I try to view the background images the browser says like 
[IMG]http://jibbli.com/test/images/right-bot-corner3.gif[/IMG][IMG]http://jibbli.com/test/images/right-bot-corner3.gif[/IMG]the image cannot be displayed because it contains errors.
[IMG]http://jibbli.com/test/images/right-bot-corner3.gif[/IMG]

---

### Post by sideffects on 2009-10-23
Okay, I got it taken care of. Apparently, I was uploading the images in ASCII mode instead of Binary. That took entirely too long to figure out. Thanks guys!

---

### Post by prasadchalasani on 2009-10-23
when I reloaded the page its shows fine

---

### Post by sideffects on 2009-10-23
> **prasadchalasani said:**
> when I reloaded the page its shows fine
Yeah, I just fixed it. (See previous post)

---

