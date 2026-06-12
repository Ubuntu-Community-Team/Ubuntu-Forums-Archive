---
title: "HTML 3D example"
date: 2010-06-04
forum: Programming Talk
---

### Post by kahumba on 2010-06-04
Hi,
I just saw it on Apple's site and they don't seem to be using WebGL, yet it rotates like a true 3D scene, does anyone know **how** it works?
[http://developer.apple.com/safaridemos/showcase/threesixty/](http://developer.apple.com/safaridemos/showcase/threesixty/)

---

### Post by SoFl W on 2010-06-04
[HTML]<title>Safari Technology Demo - 360°</title>
	<meta name="omni_page" content="HTML5 - 360°" />
	<meta name="Category" content="" />
	<meta name="Description" content="" />
	<script src="/safaridemos/showcase/global_html5/scripts/lib/prototype.js" type="text/javascript" charset="utf-8"></script>
	<script src="/safaridemos/showcase/global_html5/scripts/lib/scriptaculous.js" type="text/javascript" charset="utf-8"></script>
	<script src="/safaridemos/showcase/global_html5/scripts/browserdetect.js" type="text/javascript" charset="utf-8"></script>
	<script src="/safaridemos/showcase/global_html5/scripts/apple_core.js" type="text/javascript" charset="utf-8"></script>
	<script src="/safaridemos/showcase/global_html5/scripts/search_decorator.js" type="text/javascript" charset="utf-8"></script>
	<script src="/safaridemos/showcase/global_html5/scripts/vr.js" type="text/javascript" charset="utf-8"></script>
	<script src="/safaridemos/showcase/scripts/library.js" type="text/javascript" charset="utf-8"></script>
	<script src="/safaridemos/showcase/threesixty/scripts/threesixty.js" type="text/javascript" charset="utf-8"></script>
	<link rel="stylesheet" href="/safaridemos/showcase/global_html5/styles/base.css" type="text/css" />
	<link rel="stylesheet" href="/safaridemos/showcase/global_html5/styles/blackout.css" type="text/css" media="screen" />
	<link rel="stylesheet" href="/safaridemos/styles/html5.css" type="text/css" media="screen" />
[/HTML]

---

### Post by kahumba on 2010-06-04
That doesn't answer anything, I can see the source code myself, I'm wondering what exactly are they doing to achieve this effect, for example is it a huge pile of images shown in turn or something else?

---

### Post by Reiger on 2010-06-04
Something like that. See the “vr.js” linked script for source code of the object that handles the animation.

---

### Post by soltanis on 2010-06-05
I only seem to be able to rotate the images through certain discrete angles, so I am guessing you're on the money with the guess that they're just swapping out photographs of the same items from different angles.

---

### Post by randomizer101 on 2010-06-05
That's what they're doing. Each image is labelled Seq_v04_640x378_**XX**.jpg

---

### Post by ja660k on 2010-06-05
html 5...
sign up to developer.apple.com
you'd be surprised, its not just apple only languages...

---

### Post by kahumba on 2010-06-05
> **randomizer101 said:**
> That's what they're doing. Each image is labelled Seq_v04_640x378_**XX**.jpg
I see, then that's not really HTML5 stuff, but rather a blunt cheap hoax, for "real 3D" rotation see
[http://people.mozilla.com/~vladimir/webgl/spore/sporeview.html](http://people.mozilla.com/~vladimir/webgl/spore/sporeview.html)
using the daily build of Chrome or Firefox, that's WebGL in action.

---

