---
title: "[SOLVED] Font Issue: Black Squares behind Letters"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by phyrewall on 2008-07-17
I hate to start a new thread, but I've searched repeatedly for an answer and I'm coming up short. Can anyone please tell me what's going on here and how to fix it? It happens in web pages, the title of the Compiz "Window Previews", and elsewhere.

Thanks for any assistance.

---

### Post by nowshining on 2008-07-17
in the terminal - become root - issue:

```
pango-querymodules > '/usr/local/etc/pango/pango.modules'
```

restart all apps,

if that doesn't work:

in the firefox prefs - content - advanced - and change the charset encoding to windows 1252 or iso8859-1 and reload the page.

---

### Post by phyrewall on 2008-07-17
I had to install Pango-Graphite, and then my spaces become huge. This is affecting Firefox and Compiz.

---

### Post by phyrewall on 2008-07-26
Bump for justice!

I'm still having this error. Can someone please help?

---

### Post by phyrewall on 2008-08-01
SOLVED: The issue is caused by Compiz Render Text plugin. It fixed itself after re-installation.

---

