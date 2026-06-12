---
title: "having trouble with gtk2-perl and cairo"
date: 2007-02-14
forum: Programming Talk
---

### Post by haricharan on 2007-02-14
i am trying to convert a gtk script from C to perl. I converted most of it except this line
```
cairo_set_operator (cr, CAIRO_OPERATOR_SOURCE);
```
I found its python equivalent in pygtk to be
```
cr.set_operator(cairo.OPERATOR_SOURCE)
```
But i want it in perl. Can someone please tell how this line translates to perl. I checked the gtk2-perl documentation. Its not listed there....

---

### Post by haricharan on 2007-02-15
bump....

---

### Post by haricharan on 2007-02-18
no suggestions?????? :( :( :confused:

---

### Post by slavik on 2007-02-18
why not simply keep it?

check on the details about embedding C code inside Perl code ...

---

### Post by Snargle on 2007-02-18
I'm not familiar with operators, but there's a couple operator functions shown here:

[http://cpan.uwinnipeg.ca/htdocs/Cairo/Cairo.html#cr_gt_set_operator_op](http://cpan.uwinnipeg.ca/htdocs/Cairo/Cairo.html#cr_gt_set_operator_op)

It looks like it takes arguments such as 'over', 'atop', 'in', etc.

A C function wouldn't be easy because it can't be passed $cr, which is a perl hash reference instead of a c struct pointer.

---

### Post by haricharan on 2007-02-19
> **slavik said:**
> why not simply keep it?

check on the details about embedding C code inside Perl code ...

i cant keep it as it.....my whole application is in perl....i wanted to embed windows with alpha masks for it....and important thing i dont know much of python.....i can try in C though..and also lemme try the embedding stuff...thank you anyway... :)

---

### Post by haricharan on 2007-02-19
> **Snargle said:**
> I'm not familiar with operators, but there's a couple operator functions shown here:

[http://cpan.uwinnipeg.ca/htdocs/Cairo/Cairo.html#cr_gt_set_operator_op](http://cpan.uwinnipeg.ca/htdocs/Cairo/Cairo.html#cr_gt_set_operator_op)

It looks like it takes arguments such as 'over', 'atop', 'in', etc.

A C function wouldn't be easy because it can't be passed $cr, which is a perl hash reference instead of a c struct pointer.

thanks for the link..but it doesnt give abt operator in much detail.....lemme try searching more!!

---

### Post by Snargle on 2007-02-19
This works:
$cr->set_operator ('source');

I'm sure it's equivalent to "cairo_set_operator (cr, CAIRO_OPERATOR_SOURCE);"

---

### Post by haricharan on 2007-02-19
> **Snargle said:**
> This works:
$cr->set_operator ('source');

I'm sure it's equivalent to "cairo_set_operator (cr, CAIRO_OPERATOR_SOURCE);"

Thanks a lot it works....i had been trying all kinds of possibilities....but it didnt strike for me to use just 'source'...

---

