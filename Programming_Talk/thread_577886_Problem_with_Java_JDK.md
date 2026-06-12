---
title: "Problem with Java JDK"
date: 2007-10-16
forum: Programming Talk
---

### Post by dansued on 2007-10-16
For one of my classes, I wrote a simple java program that would display a group of smiley faces in a window. I wrote this program on one of the windows machines on campus. It compiles and runs perfectly.

However, when I copy the same source files onto my computer, a problem emerges. It will compile with no error but upon running, the window that comes up is just a grey background.

My professor is guessing that either the version of java that I have is different or that the graphics library has some incompatibility. The version of java I have is 1.6.0, installed from synaptic.

If anybody has a few minutes to compile and try to run my program, it would be much appreciated. I've attached a zip with all the source files.

```

javac *.java
java Smiley
```If it isn't immediately apparent, I have about 1 week of java  experience.

---

### Post by andyrobo60 on 2007-10-16
Are you running compiz fusion or something like that? I know that can cause the problem you are having when using GUIs made in java's swing. 

If you are using compiz fusion, compiz or beryl try this. 

[http://ubuntuforums.org/showthread.php?t=362821](http://ubuntuforums.org/showthread.php?t=362821)

---

### Post by dansued on 2007-10-16
it works! or so it seems. My program works as expected but this message comes up in the terminal

```

Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
```

Should I just ignore this?

---

### Post by andyrobo60 on 2007-10-16
I get that message as well. I just ignore it.

---

