---
title: "How can I run JOGL in Eclipse on Ubuntu 10.10"
date: 2011-01-19
forum: Packaging and Compiling Programs
---

### Post by Bor1s on 2011-01-19
I have downloaded the gluegen-rt.jar and jogl.jar plus libgluegen-rt.so, libjogl.so, lobjogl_awt.so, libjogl_cg.so. 
I have the latest version of Eclipse, Java and Ubuntu. 
I created a new project 
I created a lib folder, where I copied the JARs and in the root of the project I copied the *.so files.
I added the JARs in my project through Properties->Build Path->Add External JARs
I tried to build and run the app but I got Exception in thread "main" java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path . So I set the Native Library Locations for both JARs to be myproject/lib.

Same difference...what am I missing? I will add that I actually got it running once...and that was it...I don't know how, nor why it didn't run the second time. The OpenGL is ok, because I have no problem running it in C/C++.

---

### Post by lykeion on 2011-01-19
I think this page methods of adding internal jars to build path in Eclipse should work: [http://www.wikihow.com/Add-JARs-to-Project-Build-Paths-in-Eclipse-%28Java%29](http://www.wikihow.com/Add-JARs-to-Project-Build-Paths-in-Eclipse-%28Java%29)
I say think, because I don't use Eclipse that often, because I prefer IntelliJ as IDE for Java development.

---

### Post by Bor1s on 2011-01-19
Dude this was amazing! Not only was your answer quick but also very helpful! It actually solved my problem. Thank you very much sir :).

P.S. Duly noted. Eclipse is either very complicated or buggy. I was trying to add the libs using a very intuitive method, by clicking on Add JARs. And the build path menu looked exactly the same and it still wasn't working. So can somebody please explain to me how is this different from right clicking on the library and selecting Add To Build Path?

---

### Post by Bor1s on 2011-01-19
Dude this was amazing! Not only was your answer quick but also very helpful! It actually solved my problem. Thank you very much sir :).

P.S. Duly noted. Eclipse is either very complicated or buggy. I was trying to add the libs using a very intuitive method, by clicking on Add JARs. And the build path menu looked exactly the same and it still wasn't working. So can somebody please explain to me how is this different from right clicking on the library and selecting Add To Build Path?

---

### Post by Bor1s on 2011-01-19
Dude this was amazing! Not only was your answer quick but also very helpful! It actually solved my problem. Thank you very much sir :).

P.S. Duly noted. Eclipse is either very complicated or buggy. I was trying to add the libs using a very intuitive method, by clicking on Add JARs. And the build path menu looked exactly the same and it still wasn't working. So can somebody please explain to me how is this different from right clicking on the library and selecting Add To Build Path?

---

### Post by Bor1s on 2011-01-19
I apolagize to the users and the moderators of this forum, there seems to be something wrong with the way my Chromium sends requests to the servers of ubuntuforums.org so everytime I try to post something it looks like a crash so I refresh. In order to prevent triple posts I keep another tab opened to view wether I have submited the post but it didn't show anything. So from now onI will use Firefox. I don't want to get banned this forum is way to helpful.

---

