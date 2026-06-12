---
title: "[SOLVED] Can't add new C++ class to project in NetBeans 6.5"
date: 2009-01-02
forum: Programming Talk
---

### Post by jyaan on 2009-01-02
When I try to add a new C++ class to my project, I get the error 'Called DataObject.find on null' at the bottom of the window, which (I'm assuming) means a file is missing. I deleted one of the templates since it was in lower-case (meaning I thought I accidentally created it myself), and I think this is the reason. What can I do to fix it? I tried uninstalling and reinstalling the IDE and C/C++ plugins, but this made no difference. Where can I get the file? I can't seem to find it anywhere on the site. Or is it something else?

---

### Post by jyaan on 2009-01-02
Deleting ~/.netbeans worked. Annoying that I had to lose my config though. =/

---

### Post by mike_g on 2009-01-02
AFAIK Netbeans stores user data in a hidden folder in your home directory called ".netbeans" if you delete that folder then reinstall netbeans it will create a new one from scratch. Thats is thats where your problem is. I take it that you are adding the class to a C++ project and not a Java one.

---

