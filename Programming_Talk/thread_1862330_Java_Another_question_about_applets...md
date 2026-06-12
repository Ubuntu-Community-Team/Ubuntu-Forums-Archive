---
title: "Java: Another question about applets.."
date: 2011-10-16
forum: Programming Talk
---

### Post by fallenshadow on 2011-10-16
I have an applet that runs perfectly through the use of Netbeans... however when I put it on a webpage it fails to run... why is this?

Error in java console:
> java.lang.NoClassDefFoundError: Test1 (wrong name: test1/Test1)

---

### Post by Ghostmn on 2011-10-16
> **fallenshadow said:**
> I have an applet that runs perfectly through the use of Netbeans... however when I put it on a webpage it fails to run... why is this?

Error in java console:

Just looking at the error, you didn't declare something properly.

Can you make a tarball of your source and attach it to a reply?

---

### Post by PaulM1985 on 2011-10-17
I would guess that when you created your applet in Netbeans you had it in a package.  When you are trying to use your class in the webpage, your folder structure does not match your package structure.

Paul

---

### Post by ballantony on 2011-10-19
How are you putting it on the webpage?  Something like this?

<APPLET  code="Test1/test1.class" width=350 height=200></APPLET>

---

