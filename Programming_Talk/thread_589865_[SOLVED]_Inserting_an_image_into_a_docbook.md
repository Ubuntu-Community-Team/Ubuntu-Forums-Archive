---
title: "[SOLVED] Inserting an image into a docbook"
date: 2007-10-24
forum: Programming Talk
---

### Post by Vadi on 2007-10-24
I need to insert an image into the docbook I'm helping write, but for the life of me, I can't! It compiles fine, but it seems to skip over the actual image part (there's nothing about it in the html source). 

Could someone help me out?

The code that I got is the following:

```
<para>
<screenshot>
<screeninfo>Sample screenshot;</screeninfo>
  <mediaobject>
    <imageobject>
      <imagedata fileref="kmuddy.jpeg" format="JPEG"/>
    </imageobject>
  </mediaobject>
</screenshot>
</para>
```

And the image is in the same directory as the docbook also. What am I doing wrong?

---

### Post by Vadi on 2007-10-24
Ignore that, I forgot I need to do "meinproc index.docbook" and not just "make". The code works.

---

