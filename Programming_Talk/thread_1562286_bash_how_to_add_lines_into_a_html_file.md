---
title: "bash: how to add lines into a html file?"
date: 2010-08-27
forum: Programming Talk
---

### Post by honeybear on 2010-08-27
hello,

I have an HTML file of not containing any line feed, how can I add some to a fully non lined file content ?

" ... rea(this);"><table cellpadding="3" cellspacing="0" border="0" width="100%"><tr><td><a href="/user .."

thanks

---

### Post by PryGuy on 2010-08-27
Do you want to have multiple lines? Use <br /> then.

---

### Post by spjackson on 2010-08-27
> **honeybear said:**
> 
I have an HTML file of not containing any line feed, how can I add some to a fully non lined file content ?

" ... rea(this);"><table cellpadding="3" cellspacing="0" border="0" width="100%"><tr><td><a href="/user .."

If it's a one-off, you could place a newline after every > like this:
```
 sed 's/>/>\
/g' input.html > output.html

```For a better solution I'd suggest using the HTML tidy program, [http://tidy.sourceforge.net/](http://tidy.sourceforge.net/) , e.g.
```
tidy -i -wrap 75 input.html > output.html
```This will output nicely indented tags, wrapping text at column 75.

---

