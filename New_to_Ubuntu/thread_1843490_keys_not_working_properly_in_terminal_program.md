---
title: "keys not working properly in terminal program"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by dinesh.daultani on 2011-09-13
i had recently installed jdk and all required programs to work on java.
but when i make a new program byr vi programname.java
and when new file open the keyboard keys are not working properly
like when i press scroll up down keys A B is printed and also the backspace is not working.

---

### Post by drmrgd on 2011-09-14
I might be making a poor assumption here, so pardon me if I'm wrong.  But it sounds like you might not be familiar with using vi to write scripts.  It's not as intuitive as you think at first, and you might do better with something like "Nano" to write your scripts.  Just replace the "vi" with "nano" when you're trying to create the script:

```
nano programname.java
```  

Here are the basic vi commands, just in case you're not familiar with how it works:

[http://www.cs.colostate.edu/helpdocs/vi.html]("http://www.cs.colostate.edu/helpdocs/vi.html")

---

### Post by Lars Noodén on 2011-09-14
+1 for nano

If you're going to [use vi](http://www.washington.edu/computing/unix/vi.html), then there are some basics that you have to cover first.  Once you do that, it's a very useful and powerful editor.   It's good to know a little vi because it will always be there on any system you log into.  But for now, nano should be good enough and is much easier.

---

