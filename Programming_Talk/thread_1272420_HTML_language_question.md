---
title: "HTML language question"
date: 2009-09-22
forum: Programming Talk
---

### Post by thelugnut on 2009-09-22
I am just starting to learn this mark-up language.

My question is:

In my "test" web page, written with the text editor, I am trying to write sentences in English and Hebrew.

But my attempt to use any language other than English, the characters are not displayed correctly. Instead of seeing the foreign words, a conglomeration of miscellaneous characters is displayed.
 
If I navigate to some web site that displays foreign language, everything is displayed correctly.

I am using Ubuntu 9.04, Firefox 3.0.14.

Any suggestions?:confused:

---

### Post by bogdan.veringioiu on 2009-09-22
Hi.

Did you try to set the encoding for the page?
Try to put this in the head section:
```
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```

Bogdan

---

### Post by scragar on 2009-09-22
> **bogdan.veringioiu said:**
> Hi.

Did you try to set the encoding for the page?
Try to put this in the head section:
```
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
```

Bogdan

Setting the encoding to UTF-8 does nothing if it's not a UTF-8 file(Or at least according standards, naturally not everyone follows them though(*cough*IE*cough*)).

In the save as box choose UTF-8 for the character encoding.

---

### Post by nvteighen on 2009-09-22
Hm... if you're using XHTML (you better should), you should use:

```

<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<!DOCTYPE html 
          PUBLIC "-//W3C//DTD XHTML 1.1//EN" 
          "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="es">
  <head>
    <!-- This line is absolutely not needed because of the <?xml ...?> tag, but 
         without it IE 7 gets lost about encoding. -->
    <meta http-equiv="Content-Type" content="application/xhtml+xml; 
                                             charset=utf-8"/>
    <!-- ... -->

```

IE 7 (and I guess IE 6 too) is stupid and needs the <meta> tag even when the XML declaration is enough according to the standards (and for the rest of decent web browsers...).

---

### Post by thelugnut on 2009-09-22
to nvteighen:
> Hm... if you're using XHTML (you better should), you should use:
Yes, but not yet. I have started with html with the intention to move on to xhtml later. (I hope!:))

to bogdan.veringioiu and scragar:
I'll give that a go as soon as I can.

Thanks for the responses, for sure!

---------------------------------------------
Okay! That fixed my problem. 
> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
I wonder why this wasn't spelled out. Oh well, probably was and I missed it.
I really appreciate the responses.

---

