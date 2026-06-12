---
title: "Epiphany extension help"
date: 2007-06-24
forum: Programming Talk
---

### Post by justinjstark on 2007-06-24
I am trying to make an epiphany extension to remove all target="_blank" from links.

I have found that I can connect to ge_content_change like so:

```
def attach_tab(window, tab):
embed = tab.get_embed()
sig = embed.connect('ge_content_change', _content_cb)
embed._python_sample_location_sig = sig
```

But all that is passed to _content_cb is the url.  I don't know how to go about changing the actual html on the page.

Does anybody know anything about epiphany extensions and can help?

---

### Post by duff on 2007-06-24
Wouldn't the grease monkey extension better serve you?

---

### Post by justinjstark on 2007-06-24
Maybe...if I can figure out how to use it!?

---

### Post by justinjstark on 2007-06-24
Nevermind, I figured it out.  But, epiphany could really be more user friendly.

---

### Post by ankursethi on 2007-06-25
I'm using it right now. It's faster and more responsive than FF, bit sadly I have to do all my configuration from about:config.

Where can I find documentation on writing Epiphany extensions? Probably I can write something half-decent that allows me to use the GUI to change most preferences.

---

### Post by justinjstark on 2007-06-25
> **ankursethi said:**
> I'm using it right now. It's faster and more responsive than FF, bit sadly I have to do all my configuration from about:config.

Where can I find documentation on writing Epiphany extensions? Probably I can write something half-decent that allows me to use the GUI to change most preferences.

Like with most gnome applications, you have to hunt through source code and figure things out for yourself.

The documentation is here:

[http://www.gnome.org/projects/epiphany/documentation/extensions/index.html](http://www.gnome.org/projects/epiphany/documentation/extensions/index.html)

If you look in the source code for epiphany, you will find (somewhere) a file that has the gsignals that you can connect to.  It will allow you to write callback functions for various things, such as location changes.

That's as far as I got.

Good luck to you, sir.  ;)

---

### Post by ankursethi on 2007-06-26
Okay, thanks.

---

### Post by justinjstark on 2007-06-27
For anyone interested, I found a greasemonkey script that changes all target="_blank" to target="_self".  Yay!  I can finally control my own links.  :)

[http://meddle.dzygn.com/v3/js/killblank.user.js](http://meddle.dzygn.com/v3/js/killblank.user.js)

It was rewritten as an opera extension and posted here:

[http://www.xs4all.nl/~vangeijt/opera/userjs-collection.html](http://www.xs4all.nl/~vangeijt/opera/userjs-collection.html)

I did the best of both worlds and wound up with:

```
// ==UserScript==
// @name           No target
// @namespace      http://meddle.dzygn.com, http://www.justinjstark.com
// @description    Removes target="_blank" from links
// @include        *
// ==/UserScript==

/*
Script source:
  'Destroy Target' Greasemonkey script
  http://meddle.dzygn.com/eng/weblog/destroy.target/

Changes:
  Rewritten by liorean, 2005-03-20. Repackaged by Rijk.
  Rewritten for Greasemonkey by justinjstark, 20070627.
*/

(function() {
	var ele, i = 0, external = document.links;
	while ( ele = external.item ( i++ ) )
		if ( ele.href && ( /_blank|_userwww/.test ( ele.target ) ) )
			ele.target = '_self';
})();
```

---

### Post by jrib on 2008-01-12
[http://www.gnome.org/projects/epiphany/documentation/extensions/index.html](http://www.gnome.org/projects/epiphany/documentation/extensions/index.html) is documentation on writing epiphany extensions. [http://www.adamhooper.com:4242/epiphany-extensions/python-console.xhtml](http://www.adamhooper.com:4242/epiphany-extensions/python-console.xhtml) is a good idea to read too if you are using python.  And of course reading other extensions helps: [http://live.gnome.org/Epiphany/ThirdPartyExtensions](http://live.gnome.org/Epiphany/ThirdPartyExtensions).

Also, changing the actual html using a python extension isn't doable atm.  From the second link:
"The Python Console can do everything a Python-based Epiphany extension can
   do. At the moment this document was written, Epiphany does not come with an
   interface to XPCOM; this means that while the Python Console can access all
   of the Epiphany API (and all other Python libraries, for that matter), it
   has no control over the Mozilla API. Since Mozilla is used to render web
   pages, the end result is that the Python Console cannot change colors, add
   or remove HTML elements, or listen to arbitrary Mozilla signals. This
   limitation applies to Python extensions, as well."

---

### Post by Kapitän Rotbart on 2008-03-03
Anyone know how to get the extensions working in Epiphany in Gutsy after the package update? I stick with the official repositories and ended up updating the epiphany-browser package, yet there was no update for the epiphany-extension package... has anyone figured out how to fix this? I'd really appreciate some help because it would be my browser of choice if I could get the extensions to work again.

I have a lot of problems with FireFox... for some reason, loading certain pages for the first time in FireFox will automatically disconnect my WLAN connection, and considering the awfulness of the driver (RALink), I'm usually best off rebooting the computer in the hopes of getting the fastest reconnect to the Internet. These problems would be greatly reduced if I weren't stuck with such an obnoxious browser... please help!

Edit: never mind. The repos have been corrected and no longer break the compatibility between the browser and extensions packages, and the kernel dev. has fixed my WLAN issue.

---

