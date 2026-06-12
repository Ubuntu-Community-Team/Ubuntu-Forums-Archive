---
title: "[java] importing classes help"
date: 2010-03-01
forum: Programming Talk
---

### Post by Xender1 on 2010-03-01
This is a pretty scrub question, but I have searched google and these forums and still am confused as to what I am suppose to do. So I have a three files, all .java. One of these files is the one with the main and the other ones are just classes I made. I am really really stuck on importing these into my main class. I tried to do it as a package and had them all in the same directory and in all of them did package myfolder; but that did not work. also doing import nameoffile or anything along those lines also didnt work. Any help?

---

### Post by Simon17 on 2010-03-01
If they're all in the same directory, it should find them.

Dumb question, but you didn't make the classes private did you?

You might need to set your classpath. Try: 
javac -cp . <whatever>

---

### Post by Xender1 on 2010-03-01
Heh... so I got it to work. Yea turns out I did not need any import statements for them since they are all in the same directory. I also did the -cp . just to make sure and everything worked. Thanks. (solved)

---

