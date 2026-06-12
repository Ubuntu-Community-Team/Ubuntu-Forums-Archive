---
title: "Py2Exe &amp; PyQt"
date: 2011-01-07
forum: Programming Talk
---

### Post by Sailor5 on 2011-01-07
Greetings!
  So I've made a Python application that uses the ever so great PyQt as  it's interface. Now if I was to specify the --bundle 0 option for  Py2Exe the resulting compiled executable file works fine! But with all  the needed files, the folder gets cluttered up. So I tried passing 1 and  2 for the --bundle option. One packs everything into file file whilst  the other packs everything except the Python dll. However both of those  options results in the executable file exiting upon execution. No errors  are chucked back.

  A question on stackoverflow said to supply the "--includes sip"  parameter for py2exe however that does not solve this issue. The sip  module was already being included in all builds of the application so I  can't think it has anything to do with sip.

  Is such a common problem?
  
Thanks bye!

---

### Post by lykwydchykyn on 2011-01-07
I've never had much luck with those options on my pyqt apps.  In fact, I usually get an error during compilation when I try to use "--bundle".  I don't know if it has anything to do with qt or if it's just pyqt.

---

### Post by Sailor5 on 2011-01-08
Stackoverflow can't help. Your my last chance ubuntuforums.org!

---

