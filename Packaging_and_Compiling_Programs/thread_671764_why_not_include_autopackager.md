---
title: "why not include autopackager?"
date: 2008-01-18
forum: Packaging and Compiling Programs
---

### Post by corn13read on 2008-01-18
I've just read an article about autopackage here: [http://www.linux.com/feature/124325](http://www.linux.com/feature/124325)

Is Ubuntu planning on including this with their future releases? This looks like a solid project and something that is needed by all linux distros for the future. Anyone have any other thoughts on this subject?

---

### Post by geraldm on 2008-01-19
The needs of a distribution are different from that packager.  There is no standard for packaging, and some packaging frameworks are quite entrenched.  Debian's deb packaging is quite simple and it is easy to vary from *.deb if a person chooses to do so.  Using rpm packaging is also established, and there are helper programs like alien to integrate it into debian-like system.
I think autopackage would need to be more flexible in adapting its installation to allow for alternative installation styles.  Providing a heirarchical installation format, such as what GNU stow uses, can be easier to adjust to local system format.
In summary, I do not see this packager to be adopted by many distros.

Gerald

---

