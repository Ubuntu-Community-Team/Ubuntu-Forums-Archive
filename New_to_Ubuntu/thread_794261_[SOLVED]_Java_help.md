---
title: "[SOLVED] Java help"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by takuhii on 2008-05-14
I have SUN JAVA 6 installed, but according to ubuntu, I also have GIJ-4.2 (???) installed and SUN OPENJDK.

My question is this... I am quite happy using SUN JAVA, can I get rid of GIJ and OPENJDK?

If so how, in laymans terms please, as I don't want to break anything...

Cheers

---

### Post by Xiong Chiamiov on 2008-05-15
You can do a search for java in Synaptic, then remove the packages you don't want.  Before committing changes, do 2 things:
1)  Look over the packages you *do* want, and make sure none of them are being removed with the ones you want gone.  If they are, cancel changes and go through slowly to see which package(s) are required and which aren't.
2)  Write (or type) down the packages you're removing.  That way, if something goes wrong, you know which packages to reinstall.

---

