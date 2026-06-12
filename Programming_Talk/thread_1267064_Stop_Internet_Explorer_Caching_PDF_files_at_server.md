---
title: "Stop Internet Explorer Caching PDF files at server end?"
date: 2009-09-15
forum: Programming Talk
---

### Post by Johnsie on 2009-09-15
I have a link to a file:

[http://example.com/148.pdf](http://example.com/148.pdf)

[PHP]
<a href="http://example.com/148.pdf">ClickY</a>
[/PHP]



The problem is that when some people click the link they get an older version of the file that they've cached on their machine. Is there any way to make sure the version they get is the latest version? 

I've thought about generating random filenames. Any other suggestions?

I can do PHP or javascript.

---

### Post by hessiess on 2009-09-15
Set the Expires HTTP header to some date in the past and use HTTPS (Encrypted pages shouldn't cache).

---

### Post by Johnsie on 2009-09-16
I decided just to append a random number to the filenames. I was going to try using https but it looks like it could take a while to set up and I was pushed for time.

---

