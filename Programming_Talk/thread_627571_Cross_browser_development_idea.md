---
title: "Cross browser development idea?"
date: 2007-11-30
forum: Programming Talk
---

### Post by ICEcoffee on 2007-11-30
I had and idea that might be a longterm aid to developing cross browser web applications, ON AS MANY BROWSERS AND VERSIONS AS REQUIRED.

Obviously this sounds fantastic for the Linux bound developer, but it may be nothing because I have absolutely no idea on what is involved in developing (any) browser, proper.

What would be involved to build a "generic browser" which was built upon feedback from the community?

An example contribution from "anon"  developer: 
"I just tested my web app, which holds to strict standards, viewed in ie6, it does XXXX, when rendering XXXX code".

this info is taken and then added to "simulate" the response for that browser.

This might be dismissed out of hand, and people might say it's impossible, but I just thought it would be an ongoing solution that would allow developers to develop without worrying about some other browsers real code, and no licensing concerns either (assuming it was feasible).

---

### Post by twistedtwig on 2007-11-30
could have the wrong end of the stick but are you saying you want to build a browser that acts as all browsers at once?

---

### Post by ICEcoffee on 2007-11-30
no, The whole browser component would be able to do that, but you could select tabs "per browser" emulation, to test the same page.

---

### Post by LaRoza on 2007-11-30
A single app cannot replicate the flaws of all the other apps.

You can, however, test your sites in as many browsers as possible, with IE6 as the lowest standard. It should render well in IE7, FF2, Opera 9, Safari, and Konqueror and be logical in Lynx.

Build sites to degrade gracefully, and follow the standards.

My site: [http://laroza.freehostia.com](http://laroza.freehostia.com) will render well in all of the above browsers, but will loose non essential enhancements with IE6.

---

