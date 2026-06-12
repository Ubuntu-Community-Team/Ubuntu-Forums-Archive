---
title: "Quad-Ren, my resolusion independant 2D graphics engine, looking for feadback."
date: 2009-01-25
forum: Programming Talk
---

### Post by hessiess on 2009-01-25
Quad-Ren is a free, open source(LGPL), resolution independent 2D graphics
engine with the primary focuses being on simplicity and minimalism.
It was developed primarily for creating 2D games, with features such
as built in support for animations. Though there is nothing to
prevent it from being used for the development of other 2D applications
which rely heavily on bitmap images, and should function the same regardless
of screen resolution.

Quad-Ren is programmed in, and usable from the C++ programming language,
though it is highly likely that future versions will also feature an
integrated scripting language for defining quad behaviours. 

Features[list]
[*]Resolution independence: Applications created with Quad-Ren will
    function the same regardless of screen resolution or aspect ratio,
unlike other 2D engines, which all seem to be resolution dependant.
    Aspect independence is achieved via the use of letter boxing, This is
    the only(IMO) way to achieve this, as stretching the image to fit looks
    ugly and simply showing more of the scene is likely to be an unfair advantage.

[*] Bilinear filtered rotation: and scaling: Quads can be scaled and rotated
      smoothly, without the shimmering associated with nearest neighbour filtering.

[*] Only alpha transparency: Only alpha transparency is supported, to allow for
      nice looking anti-aliased graphics and discourage the use of aliased images.

[*] Free camera:Allows for easy scrolling around large scenes.
[/list]
The current SDK can be downloaded [here](http://www.hessiess.com/resorces/quad-ren-0.1.tar.gz). Any crits, suggestions for improvements, or feature suggestions?

---

### Post by hessiess on 2009-01-30
Quad-Ren is now avalable on sourceforge[URL="https://sourceforge.net/projects/quad-ren/"].
https://sourceforge.net/projects/quad-ren/[/URL]

---

### Post by hessiess on 2009-02-28
Updated the documentation on the website.

[http://quad-ren.sourceforge.net/index.php?section=API%20Documentation&page=NULL](http://quad-ren.sourceforge.net/index.php?section=API%20Documentation&page=NULL)

---

### Post by jimi_hendrix on 2009-02-28
havnt tried it (i will look into using it sooner or later), but it seems simple enough and i like the color scheme of your website

---

