---
title: "How to recompile one java class after decompiling it"
date: 2007-10-11
forum: Programming Talk
---

### Post by twistedtwig on 2007-10-11
Hi all,

Its been a while since I have used Java at all.. But I have never done this sort of thing.  I had a java prgram (class files) that was written by someone else.  I wanted to slightly change the dehaviour of one of the methods so I used JAD to decompile the class.

I found the offending method and have made some changes. I am now trying to recompile the class so it can be used in the place of the old one.  But I get a TON of errors:

```
Chameleon.java:886: cannot resolve symbol
symbol  : variable window 
location: class Chameleon
        if(window != null)
           ^
Chameleon.java:887: cannot resolve symbol
symbol  : variable window 
location: class Chameleon
            window.messageBox(s);
            ^
Chameleon.java:898: cannot resolve symbol
symbol  : variable rootOutputDirectory 
location: class Chameleon
            afile = engine.listFiles(file, true, rootOutputDirectory);
                                                 ^
Chameleon.java:898: cannot resolve symbol
symbol  : variable engine 
location: class Chameleon
            afile = engine.listFiles(file, true, rootOutputDirectory);
                    ^
Chameleon.java:1174: cannot resolve symbol
symbol  : method get (java.lang.String)
location: class Chameleon
        if((obj = get(s)) == null)
                  ^
Chameleon.java:1175: cannot resolve symbol
symbol  : variable engine 
location: class Chameleon
            if(engine.getSkinVariables().containsKey(s))
               ^
Chameleon.java:1176: cannot resolve symbol
symbol  : variable engine 
location: class Chameleon
                obj = engine.getSkinVariables().get(s);
                      ^
Chameleon.java:1178: cannot resolve symbol
symbol  : variable engine 
location: class Chameleon
                obj = engine.getUserVariables().get(s);

```

Above is a quick glimpse of them.  There are 57 .class files in total in the folder where I got my orginal class, I am presuming they all reference each other.

How can I get this to recompile.  I presume the code is ok.. would seem to be.  I think it is all references that is the issue.

Thanks for any and all advice

---

### Post by twistedtwig on 2007-10-12
I realized that I didn't give the commands I used.

```
Jad classfile.class
```
this made the .jad file

I renamed this to .java and did 

```
javac classfile.java
```

---

