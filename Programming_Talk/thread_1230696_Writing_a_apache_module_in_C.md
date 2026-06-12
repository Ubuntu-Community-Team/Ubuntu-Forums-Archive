---
title: "Writing a apache module in C"
date: 2009-08-03
forum: Programming Talk
---

### Post by ittiam on 2009-08-03
I have written an apache module in C. But my question if how do I form the URL, for example if send a request like

```
http://domain.com?name=abcd
```

it is giving me document access forbidden.

I assume generally u give the script that is to process the httpr request in the url or part of the form tag with the action attribute set...

```
http://domain.com/test.php?name=abcd
```.

But for me there is no script, it is an apache module written in C that needs to take care of HTTP request.

Any ideas?

---

### Post by slavik on 2009-08-03
Apache modules do not serve requests (well, they aren't supposed to), cgi "scripts" do (scripts because you can have cgi pages written in C and then compiled).

---

