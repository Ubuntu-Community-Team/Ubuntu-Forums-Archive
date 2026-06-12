---
title: "[PHP] XML raw data dump on selected elements."
date: 2010-01-28
forum: Programming Talk
---

### Post by JohnLM_the_Ghost on 2010-01-28
So I'm doing some PHP for my site, and I keep my content data separately in nice XML to be inserted into HTML by PHP.

Well it is fairly straight-forward, but I don't really understand how to dump raw data from predefined tags.

```
<post>
<p>blah blah <a href="somewhere">link</a></p>
</post>
```

So obviously I want everything between <post> (without tag endings themselves) inserted into HTML, and I want it unaltered. Is this possible without some elaborate hacks with good ole Expat parser?

---

### Post by Hellkeepa on 2010-01-28
HELLo!

I recommend having a look at the [SimpleXML](http://no.php.net/simplexml), it'll do what you're looking for. At least as far as I understood your post.

PS: Do remember to add cdata comments around the HTML code, otherwise it'll be interpreted as a part of the XML code itself.

Happy codin'!

---

### Post by JohnLM_the_Ghost on 2010-01-28
Cheers mate! SimpleXML worked like a charm! And also my code is three times shorter.

Now for the record... to process that XML snippet given before all I did was this.
```
/* Some code */
if ($x->getName()=="post")
foreach($x->children() as $y) {echo $y->asXML();}
```
where *$x* is the *SimpleXMLElement* object from code before.
It couldn't really be much simpler.

---

### Post by Hellkeepa on 2010-01-29
HELLo!

Yep, it really is simple. ;-)
Glad it worked out, and you're welcome.

Happy codin'!

---

