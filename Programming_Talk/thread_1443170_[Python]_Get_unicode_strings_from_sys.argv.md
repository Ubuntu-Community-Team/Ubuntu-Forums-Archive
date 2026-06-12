---
title: "[Python] Get unicode strings from sys.argv"
date: 2010-03-30
forum: Programming Talk
---

### Post by durand on 2010-03-30
Hi,

Is it possible to give a python script a unicode string from a commandline argument? I've tried searching for a way how but I've only managed to find a windows method to do it, and not for linux. Is this possible?

Thanks!

---

### Post by wmcbrine on 2010-03-30
I get UTF-8 strings from sys.argv in Ubuntu, if that's what I pass to it. (UTF-8 is the normal system encoding for Ubuntu.) So, for example, if you want a Unicode string from the first argument, it would be "unicode(sys.argv[1], 'utf-8')" or "sys.argv[1].decode('utf-8')".

---

### Post by durand on 2010-03-30
> **wmcbrine said:**
> I get UTF-8 strings from sys.argv in Ubuntu, if that's what I pass to it. (UTF-8 is the normal system encoding for Ubuntu.) So, for example, if you want a Unicode string from the first argument, it would be "unicode(sys.argv[1], 'utf-8')" or "sys.argv[1].decode('utf-8')".

Thanks! I eventually realised that sys.argv[1].decode('utf-8') does the trick. I still don't understand unicode properly but anyway, that can wait :). Thanks again!

---

### Post by Can+~ on 2010-03-30
Then you have some reading to do:

"Friendly" explanation (2003):
[http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html)

Mostly technical explanation of how unicode works:
[http://www.cl.cam.ac.uk/~mgk25/unicode.html#utf-8](http://www.cl.cam.ac.uk/~mgk25/unicode.html#utf-8)

---

### Post by durand on 2010-03-31
I do understand unicode in general, I meant that I don't understand how python deals with it. My understanding is that python 3 treats them as normal strings where as python 2 treats them as a separate type. When decoding a string, the encoding you pass to the function is the encoding of the string itself, am I right? I would have thought that python would be able to automatically get the string's encoding?

---

### Post by wmcbrine on 2010-03-31
> **durand said:**
> I would have thought that python would be able to automatically get the string's encoding?How? That information is not recorded within the string.

Now, you can do a semi-automatic UTF-8 recognition by relying on the fact that most non-ASCII, non-UTF-8 text will not validate as UTF-8, but you have to choose a fallback encoding, such as ISO8859-1:

```
try:
    utext = unicode(text, 'utf-8')
except:
    utext = unicode(text, 'iso8859-1')
```

---

### Post by durand on 2010-03-31
Well, the input would be japanese kanji such as &#39340;&#23665;&#26408;&#28779; so it will most likely be utf-8. I don't think it would matter much anyway as this script is just for me but I'll keep that in mind for the future. Thanks.

---

