---
title: "Need to generate jpg attachment to mail"
date: 2008-07-08
forum: Programming Talk
---

### Post by JimGvo on 2008-07-08
I'm currently exec'ing sendmail and writing raw email commands to send email from a C++ program.  I've been asked to also send one or two attached jpgs.  I can go through the RFCs and figure out how to encode them and wrap them, but I figured someone must have done this before.  I found the mimetic library, but the documentation is too sparse to make head nor tail from it.  

Anyone know of a library or code snippets?

Thanks,
Jim.

---

### Post by konungursvia on 2008-07-08
I can't help fully, but compare this batch pdf creation command I found after fiddling around a bit: 
```
ooffice -norestore -nofirststartwizard -nologo -headless -pt Cups-PDF *.doc
```

There is likely a very similar way to call up your jpeg creation program, whether using oofice or gimp or something else.

---

### Post by tamoneya on 2008-07-08
ive done it in python before similarly to this guy: [http://snippets.dzone.com/posts/show/757](http://snippets.dzone.com/posts/show/757). 
Python should be easy enough to read if you know C and I think that code should be easily portable.

---

