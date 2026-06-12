---
title: "How to scroll back in the terminal?"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by kramer65 on 2012-01-05
Hello,

I've got a python script which outputs some stuff on the command line. When I want to scroll back though, after some "pages" I can't scroll further to the top. It simply ends and I can't read the rest of the script.

Does anybody have any idea how I can scroll back further? Or does the command line simply forget the output somehow..?

---

### Post by 2F4U on 2012-01-05
You need to increase the scroll buffer in the profile preference for the terminal application. Edit -> Profile Preferences -> Scrolling.

---

### Post by Stovey on 2012-01-05
Also, you can send the output to "more", so the text stops after one page.  Then you press the space bar to see the next page (eg more).

ie pythonscript | more

You can also use less, less is more.

---

### Post by kramer65 on 2012-01-05
Ah, those are both great tips!

Thanks a lot!

---

