---
title: "How to align text to center of the image"
date: 2015-06-12
forum: Programming Talk
---

### Post by satimis on 2015-06-12
Hi,

I couldn't figure out how to align "Ramekins" in the center of its image.  Now it is at the bottom.

[http://bakery.satimis.com/pudding/](http://bakery.satimis.com/pudding/)
(Wordpress site)

Please help.  Thanks

Regards
satimis

---

### Post by achuthpnr on 2015-06-12
What you are probably looking for is this:

```
<p align="left|right|center|justify"> Your text </p>
```

---

### Post by SeijiSensei on 2015-06-12
Try this:

<p><a href="http://bakery.satimis.com/wp-content/uploads/2015/02/remarkins16.jpeg"><img class="alignnone size-full wp-image-977" src="http://bakery.satimis.com/wp-content/uploads/2015/02/remarkins16.jpeg" alt="remarkins16" height="164" width="327">
<br/><span style="**text-align: center; font-weight: bold;** color: #00ccff;">Ramekins</span></a></p>

You can center text with the tools in the WP editor as well.  The alignment buttons are in the top bar of the main editing window.

For reference, to center an object vertically, use "vertical-align:middle".

If you're asking about how to center the text on top of the image, I'd do that in GIMP.  Create a new layer on top of the image, then use the text tool to enter the text itself.  You can probably do it with CSS by using a <div> as well.

---

### Post by satimis on 2015-06-12
> **achuthpnr said:**
> What you are probably looking for is this:

```
<p align="left|right|center|justify"> Your text </p>
```
Hi,

Thanks for your advice.  It can't work.  (see attached screenshot)

Coding```

<span style="color: #00ccff;"><p align="center"><strong>Ramekins</strong></p>     <a href="http://bakery.satimis.com/wp-content/uploads/2015/02/remarkins16.jpeg"><img class="alignnone size-full wp-image-977" src="~/remarkins16.jpeg" alt="remarkins16" width="327" height="164" /></a></span>

```

satimis

---

### Post by satimis on 2015-06-12
> **SeijiSensei said:**
> Try this:

<p><a href="http://bakery.satimis.com/wp-content/uploads/2015/02/remarkins16.jpeg"><img class="alignnone size-full wp-image-977" src="http://bakery.satimis.com/wp-content/uploads/2015/02/remarkins16.jpeg" alt="remarkins16" height="164" width="327">
<br/><span style="**text-align: center; font-weight: bold;** color: #00ccff;">Ramekins</span></a></p>


Hi,

Thanks for your advice.  Still can't work for me.  Please refer to screenshot_02

What I need to achieve is screenshot_03

Regards
satimis

---

### Post by Holger_Gehrke on 2015-06-13
Try it like this:
```

<p>Ramekins <img style="vertical-align:middle" src="http://bakery.satimis.com/wp-content/uploads/2015/02/remarkins16.jpeg" /></p>

```

Vertical alignment is a bit counter-intuitive; align the (vertically) bigger element on the baseline of the smaller.

---

### Post by satimis on 2015-06-13
> **Holger_Gehrke said:**
> Try it like this:
```

<p>Ramekins <img style="vertical-align:middle" src="http://bakery.satimis.com/wp-content/uploads/2015/02/remarkins16.jpeg" /></p>

```

Vertical alignment is a bit counter-intuitive; align the (vertically) bigger element on the baseline of the smaller.
Hi,

You advice works here.  Thanks

Regards
satimis

---

