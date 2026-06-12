---
title: "php : can't get ob_start('ob_gzhandler') to work, extension_loaded('zlib')===true"
date: 2018-08-12
forum: Programming Talk
---

### Post by ReneVeerman on 2018-08-12
what do i check next?

i already googled it..

seems to be something new.

oh, and i re-installed everything onto a clean disk today (ubuntu 18.04, apache2, php7.2)

---

### Post by ReneVeerman on 2018-08-15
oops, i was doing an ob_flush() followed by a regular ob_start() elsewhere in that code..

this used to work, but not anymore.

anyways, if you ever have this problem, check your code for any ob_flush, ob_start sequences, coz i think you can't even ob_flush() and then ob_start('ob_gzhandler') a second time.

---

### Post by howefield on 2018-08-15
Thread moved to the "*Programming Talk*" forum for a better fit.

---

