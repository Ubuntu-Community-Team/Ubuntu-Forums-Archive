---
title: "utf8 no bom"
date: 2007-09-11
forum: Programming Talk
---

### Post by niceguy123 on 2007-09-11
I need to save files in utf8 no bom can that be done in gedit or do I need something else? Before I moved to Ubuntu I was using notepad++

Thanks

---

### Post by Vadi on 2007-09-12
Use notepad++ in ubuntu too.

Works great with wine :)

---

### Post by niceguy123 on 2007-09-16
I installed Bulefish (which looks really nice). But again I can't find the NO BOM. Is there an option or should I go back to Notepad++ using wine?

---

### Post by aks44 on 2007-09-16
Kate by default saves as UTF-8 without BOM, but you can switch to most other common encodings too.

FWIW it also handles Unix / MS / Mac line endings amongst many other features.

I don't have any experience with gedit, but I'd be very surprised if it wasn't able to do the same...

---

### Post by Vadi on 2007-09-16
> **niceguy123 said:**
> I installed Bulefish (which looks really nice). But again I can't find the NO BOM. Is there an option or should I go back to Notepad++ using wine?

Let's content ourselves that Npp is open source :KS

---

### Post by willywongi on 2008-06-15
I know this won't be the optimal solution, but I tried, and it worked for me. Open your file with Bluefish, change the character set to another one, rewrite some two characters at the very beginning of the document (in order to erase the invisible BOM characters), then save it. It should have stripped the bom. 

I had a php page in iso-8859-15, and when I include the fck editor, a pair of strange character showed up. In order to delete them I had to strip the bom from some of the fckeditor documents.

---

### Post by Vadi on 2008-06-15
I converted to Geany now btw. It's has features similar to npp, and even better ones, and has the gtk look that integrates well.

---

### Post by zyx386 on 2008-07-21
> **Vadi said:**
> I converted to Geany now btw. It's has features similar to npp, and even better ones, and has the gtk look that integrates well.

geany is great but you can kill the UTF-8 file with Vi or VIM to
also
```
:set nobomb
```
worked fine

:)

---

### Post by The Cog on 2008-07-21
+1 for geany

---

