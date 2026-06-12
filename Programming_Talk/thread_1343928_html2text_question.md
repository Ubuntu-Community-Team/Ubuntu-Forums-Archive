---
title: "html2text question"
date: 2009-12-02
forum: Programming Talk
---

### Post by Jefferythewind on 2009-12-02
Hi Everyone, 
  I am using html2text to convert an html document to a text document.  Sounds pretty simple huh?  Well i am getting the conversion with this command:
```
html2text ~/inputfile.html > ~/output.txt
```

I am getting the output file, but inside the output file there are many strange symbols throughout the document, like this:


_G_o_ _t_o_ _M_a_i_n_ _C_o_n_t_e_n_t
************ UUVVMM WWWWWW IInnffoorrmmaattiioonn SSyysstteemm ************

If i don't want to go through the text file and take all this stuff out one by one, how would i clean this up?

Thanks

---

### Post by wmcbrine on 2009-12-02
I'm not familiar with html2text, but what those are, are backspaces, which it's using to implement underlining (underscore, backspace, character) and boldface (character, backspace, character).

---

### Post by Arndt on 2009-12-02
> **Jefferythewind said:**
> Hi Everyone, 
  I am using html2text to convert an html document to a text document.  Sounds pretty simple huh?  Well i am getting the conversion with this command:
```
html2text ~/inputfile.html > ~/output.txt
```

I am getting the output file, but inside the output file there are many strange symbols throughout the document, like this:


_G_o_ _t_o_ _M_a_i_n_ _C_o_n_t_e_n_t
************ UUVVMM WWWWWW IInnffoorrmmaattiioonn SSyysstteemm ************

If i don't want to go through the text file and take all this stuff out one by one, how would i clean this up?

Thanks

Do you have the manual page for the program?

---

### Post by Jefferythewind on 2009-12-02
yeah, you can get the manual by typing:
```
man html2text
```

it can also be found here:
[http://www.mbayer.de/html2text/html2text1.shtml](http://www.mbayer.de/html2text/html2text1.shtml)

I took a look at that and couldn't really find anything that looks like the problem I have, but if you all can see something that would be awesome.

---

### Post by laceration on 2009-12-02
try this
```
html2text ~/inputfile.html | strings > ~/output.txt
```

---

### Post by wmcbrine on 2009-12-02
> **Jefferythewind said:**
> it can also be found here:
[http://www.mbayer.de/html2text/html2text1.shtml](http://www.mbayer.de/html2text/html2text1.shtml)

I took a look at that and couldn't really find anything that looks like the problem I haveFrom that page, the -nobs option is what you want. And dude, seriously, the description is exactly what I told you in #2.

---

### Post by openuniverse on 2009-12-03
.

---

### Post by Jefferythewind on 2009-12-03
wmcbrine, 
  sorry man, you're right, but thanks a lot for the help, i was a little lazy on that one.

---

