---
title: "jEdit fonts rendering looks ugly"
date: 2007-06-02
forum: Programming Talk
---

### Post by OOzypal on 2007-06-02
I just installed jedit using. deb pakg. The interface (menu, buttons) fonts are nice however, the text/script  area fonts look ugly. 

I installed several different fonts but still no help.

---

### Post by nephish on 2007-06-08
there is a folder that jedit uses to get fonts out of in your ubuntu box.
place your fonts in this folder 
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/fonts

and the next time you restart JEdit, it should see them. 

i installed some fonts for my desktop manually by downloading them from the internet, putting them in a folder called /home/me/.fonts  
then running fc-cache from the terminal.

just copy the same font files over to the above folder ( the jvm one) 

hope this helps

---

### Post by dwblas on 2007-06-08
I have the same complaint about jEdit.  Fonts that look good in Bluefish or some other editor appear washed out in jEdit.  I stick with jEdit because just about anything can be configued by the user.

---

