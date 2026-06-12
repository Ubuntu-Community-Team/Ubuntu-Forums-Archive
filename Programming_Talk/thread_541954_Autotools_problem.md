---
title: "Autotools problem"
date: 2007-09-03
forum: Programming Talk
---

### Post by niklas-komani on 2007-09-03
I'm currently learing gtkmm and as recommended I will use Autotools for it. So as to get used to Autotools I tried creating a minimal Autotools project, which should compile a HelloWorld program written in C++.
I've got Autotools to create a configure file and a Makefile but the problem is that the Makefile doesn't work because there is a \ inserted which makes the line which should compile the sources to object files useless. 
e.g.
```

.cpp.o:
#   if $(CXXCOMPILE) -MT $@ -MD -MP -MF "$(DEPDIR)/$*.Tpo" -c -o $@ $<; \
#   then mv -f "$(DEPDIR)/$*.Tpo" "$(DEPDIR)/$*.Po"; else rm -f "$(DEPDIR)/$*.Tpo"; exit 1; fi
   source='$<' object='$@' libtool=no \
   DEPDIR=$(DEPDIR) $(CXXDEPMODE) $(depcomp) \
   $(CXXCOMPILE) -c -o $@ $< 

```

The thing is I don't know what causes this behavior the complete test project I use is downloadable here:
[http://niklas.sceneproject.org/informatik/gtk-test2.tar.gz](http://niklas.sceneproject.org/informatik/gtk-test2.tar.gz) 

I appreciate your tips and ideas 
Nik

---

### Post by geraldm on 2007-09-03
The \ is used to indicate that the next line is to be appended to this 
line in place of \
If you do not want to use \, then just edit it out and join the two lines into one line.
In the context, it is difficult to figure out with some lines commented,
so some experiments may be in order.

Gerald

---

### Post by niklas-komani on 2007-09-04
I know what the \ does, the problem is it stops the Makefile from working and since it's not a handwritten Makefile but created by Autotools I can't simply edit it, because then the problem will get back everytime autotools regenerates it, which makes Autotools kind of useless.
Thereof I need to find out what causes automake to insert this sign.

---

