---
title: "HTML/XHTML: ignoring tags in a section"
date: 2008-04-29
forum: Programming Talk
---

### Post by WebDrake on 2008-04-29
A website I'm working on is reading text from a database which unfortunately contains some 'accidental' HTML tags.  Imagine for example <s>, meaning "the average of s" ... and which is instead interpreted as a 'strikethrough' tag which never gets closed.

Is there a way I can get my page to ignore these unintended tags and display the text as just text (but with my site's usual text style)?

---

### Post by Zugzwang on 2008-04-29
Sure there is but this has to be done in the server-side script retrieving the data and making the page from it. What language are you using?

---

### Post by CptPicard on 2008-04-29
Just a wild thought, but how are CDATA sections handled in XHTML?

---

### Post by andyrue304 on 2008-04-29
I think you can do it without server-side scripting by amending the database so that it uses

```
&gt;
``` and ```
&lt;
```

for the greater than or less than symbols. Browsers will display these as the correct symbols and you won't get a problem with any mis-reads.

---

### Post by Samhain13 on 2008-04-29
If the field you're getting the data from doesn't really have HTML (except those that you say are "accidental") and you're using PHP, [htmlspecialchars](http://www.php.net/htmlspecialchars) may be the right tool for you. It basically does what andyrue304 said but without you having to manually alter the data in the database.

But if the field is expected to contain "real" HTML, I guess there's no way you can go around the manual editing of the database entries.

---

### Post by WebDrake on 2008-04-29
Thanks for all the replies! :-)

I'm working with PHP so I'll check out the htmlspecialchars function -- will confirm tomorrow whether or not it works.

Thanks again!

---

### Post by clasificado on 2008-04-29
> **CptPicard said:**
> Just a wild thought, but how are CDATA sections handled in XHTML? This is, technically, an elegant solution.

But IE Desnt process xhtml, so no way josé.

clasificado

---

### Post by WebDrake on 2008-04-30
htmlspecialchars worked great.  Thanks very much! :KS

---

### Post by WebDrake on 2008-04-30
> **Samhain13 said:**
> If the field you're getting the data from doesn't really have HTML (except those that you say are "accidental") and you're using PHP, [htmlspecialchars](http://www.php.net/htmlspecialchars) may be the right tool for you. It basically does what andyrue304 said but without you having to manually alter the data in the database.
Worked like a dream.  Thank you very much! :-)

---

### Post by Samhain13 on 2008-04-30
I use it often myself also. You're welcome. :D

---

