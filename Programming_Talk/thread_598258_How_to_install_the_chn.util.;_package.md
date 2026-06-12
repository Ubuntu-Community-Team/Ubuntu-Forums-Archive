---
title: "How to install the chn.util.*; package?"
date: 2007-10-31
forum: Programming Talk
---

### Post by xyz_cityhunter on 2007-10-31
As you can see my question is how to install the chn.util.*;
I quite noob in this and so the ones who wants to help me might need to explain in detail or not donno what i should do....
I have read the thread [http://ubuntuforums.org/showthread.php?t=330205](http://ubuntuforums.org/showthread.php?t=330205) but i cannot understand a thing there...:(
I have the ZIP file for the chn.util which contain chn and META-INF folder but i donno where should i put it to make it work...:lolflag:
Ths 1st for anyone who's willing to help or try to help me...:popcorn:

---

### Post by Zugzwang on 2007-11-07
You don't want to "install" Java packages, but rather copy them into some directory related to your application and make them usable by Java. How to do this depends on the IDE you are using. Or are you using the command line?

---

### Post by xyz_cityhunter on 2007-11-08
Well i know that i can use the Project to include that chnuti.zip into one of the code when compiling using JCreator but the problem is in my collage PC doesn't have JCreator... so how to compile and run it safely just by the command prompt?

---

### Post by jespdj on 2007-11-09
You should put the zip file in your classpath.
By the way, why is it in a zip file instead of a jar file?

When you compile:

javac -cp chnuti.zip MyProgram.java

When you run:

java -cp chnuti.zip MyProgram

For more info on what the classpath is:
[http://en.wikipedia.org/wiki/Classpath_(Java)](http://en.wikipedia.org/wiki/Classpath_(Java))

---

### Post by xyz_cityhunter on 2007-11-13
Ok... i can compile using that method but when i tried to run it it came out NoClassDefFoundError...
[http://i142.photobucket.com/albums/r113/xyz_cityhunter/chnutilproblem.jpg](http://i142.photobucket.com/albums/r113/xyz_cityhunter/chnutilproblem.jpg)

---

