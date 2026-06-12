---
title: "Apache2 not serving page properly"
date: 2009-10-27
forum: Programming Talk
---

### Post by bryce4president on 2009-10-27
I have a basic html page with some javascript libraries.  When I open the page using firefox using the File -> Open the page loads and works as expected.  But when I try to load it via my apache2 server it doesn't load properly.  I type localhost/inaglaze/custom.html  This opens the page up, but it doesn't run the javascript.  What am I missing?

---

### Post by bryce4president on 2009-10-28
anybody?

---

### Post by Zugzwang on 2009-10-28
Did you had a look at for example the firefox error console? Maybe there's information for you.

---

### Post by CyberJack on 2009-10-28
Without a bit of source code I don't think anybody will be of great assistance.
Can you show the part where you load the javascript?

My guess is that the javascript may be loaded from a hardcoded path like so:
```

<script type="text/javascript" src="/home/<user>/<path>/javascript"></script>

```

That does work when loading the html file with "file -> open" but does not work when loading the javascript though apache.

---

### Post by Reiger on 2009-10-28
... Because Apache serves a &#8216;virtual directory tree&#8217; to the world which does not have its root at / but rather at the directory Apache is configured to serve (e.g. /var/www/).

---

