---
title: "make install and make datainstall"
date: 2009-12-27
forum: Packaging and Compiling Programs
---

### Post by fabrixx on 2009-12-27
I have to make a .deb with checkinstall.

A program requires two separates commands:

*make install*

*make datainstall*  (to install additionals directory)


How tu use checkinstall in this case?

I  run *checkinstall* after *make install* but program installation result incomplete.


I [read]("http://manpages.ubuntu.com/manpages/karmic/en/man8/checkinstall.8.html") of **--include** option, is that the correct mode ?

---

### Post by andrew.46 on 2009-12-27
Hi fabrixx,

I have not tested this but have you tried:

```
sudo checkinstall make install && make datainstall
```

I will admit that I have not used checkinstall in precisely this manner before though :). The syntax is:

```
checkinstall [options]  [install command]
```

so I guess it is just a matter of fine tuning the [install command] section...

Andrew

---

### Post by fabrixx on 2010-01-04
Thank youandrew  :)

I will try and write here if is correct for me

---

