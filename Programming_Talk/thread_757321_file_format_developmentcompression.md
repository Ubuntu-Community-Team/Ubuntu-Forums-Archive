---
title: "file format development/compression"
date: 2008-04-16
forum: Programming Talk
---

### Post by &amp;)ky#)^ on 2008-04-16
Hello, Ubuntu people.  I'm currently writing an application in Java and I have to make up a file format to store my data.  The only data I have to store is a three-dimensional integer array.  So, it's probably going to get big, fast.  My question is if anyone has a recommendation for how I should save it?  I was thinking of using XML so that I can expand on it later if I want, but plaintext isn't the most concise.  How can I save this thing so it stays relatively small?

---

### Post by dwhitney67 on 2008-04-16
Try storing the data within a file in a binary format, that way each integer (i.e. an 'int') value will take up 4 bytes.  So take the number of integers you are expecting to have and multiply by 4 bytes, and this will give you an estimate of the size of the file you will end up with.

P.S.  If you plan use your stored data on dissimilar architectures (e.g. Intel and PPC), then perhaps the XML format will be useful. Nevertheless, the plain-text format (w/o XML tags) will take up less space.

---

### Post by slavik on 2008-04-16
see if a compression library is available and store it in a compressed xml.

---

### Post by &amp;)ky#)^ on 2008-04-16
Thanks for the tip.  I did consider storing in binary, but I don't want it to fail if it does end up on some other architecture.

---

### Post by pmasiar on 2008-04-16
XML - result will be less than compressed, no? :-)

---

### Post by mssever on 2008-04-16
[YAML]("http://yaml.org/") is awesome, though you might want to compress it.

---

### Post by nanotube on 2008-04-16
> **bluej774 said:**
> How can I save this thing so it stays relatively small?

do whatever you want - but then zip it up. 
text generally compresses very well - so whether you choose plain text, xml, or anything else text-based, your zipped file will be small.

---

### Post by &amp;)ky#)^ on 2008-04-18
> **mssever said:**
> [YAML]("http://yaml.org/") is awesome, though you might want to compress it.

YAML looks really cool.  It's even cooler once I realized that the home page of the website is in their markup format.  YAML seems really straight forward.

If YAML is so cool and so humanly readable and has been around for so long, why has XML been getting so much more attention?

---

### Post by mssever on 2008-04-18
> **bluej774 said:**
> If YAML is so cool and so humanly readable and has been around for so long, why has XML been getting so much more attention?

Well, XML has been around for longer, it has influential backers (Microsoft, the Java community, the web community (AJAX, etc.)), and its more flexible. There are things you can do with XML that you can't do with YAML. But honestly, I've never needed those things. Both Rails and Django use YAML as their configuration file format, as do a number of other projects.

---

### Post by &amp;)ky#)^ on 2008-04-18
Well, here's the drawback.  I don't need my data to be human-readable and I've decided against XML as well.  Isn't there a way to encode it in host unspecific binary?  That way, it's in binary but it can be read in regardless of host architecture or JVM version.

---

### Post by dwhitney67 on 2008-04-18
Encode it as binary.  If you are dead-against XML, then that's fine.  If someday you need to port the data to a system hosting a different architecture, then maybe you will need to "play around" with the data as you read it in.  Long before XML was around, many applications had to deal with the same issue.  Thus for now, I wouldn't worry about it.

BTW, you should read this wiki-doc concerning endianess:  [http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

---

