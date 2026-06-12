---
title: "Is Java Source code viewable?"
date: 2012-10-11
forum: Programming Talk
---

### Post by ki4jgt on 2012-10-11
If I write a java applet for my website, is the source code viewable by my users? Also, are memory dumps possible? I have variables in my program which I wish to keep a secret.

---

### Post by xytron on 2012-10-11
> **ki4jgt said:**
> If I write a java applet for my website, is the source code viewable by my users? Also, are memory dumps possible? I have variables in my program which I wish to keep a secret.

No they can't view your source code directly, but it will probably be easy to download the class file and then use a decompiler to get the source code.

There are many Java decompiler tools around some are good (expensive) and others of varying quality.  If you really want to protect your Java class files from being reverse engineered, look for a Java obfuscator tool.

Obfucators protect .class files from reverse engineering by replacing package, class, method, and field names with inexpressive characters. If someone decompiles the obfuscated .class files it will be very difficult to make sense of the original purpose of the obfuscated code. 



There would have to be some good reason for someone to actually want to decompile your code.

---

### Post by ki4jgt on 2012-10-11
> **xytron said:**
> No they can't view your source code directly, but it will probably be easy to download the class file and then use a decompiler to get the source code.

There are many Java decompiler tools around some are good (expensive) and others of varying quality.  If you really want to protect your Java class files from being reverse engineered, look for a Java obfuscator tool.

Obfucators protect .class files from reverse engineering by replacing package, class, method, and field names with inexpressive characters. If someone decompiles the obfuscated .class files it will be very difficult to make sense of the original purpose of the obfuscated code. 



There would have to be some good reason for someone to actually want to decompile your code.

Thanks :) What about singling out specific variables? Is this possible with a decompiler? Like say I permenantly set x = 5. Could a decompiler find this information?

---

### Post by xytron on 2012-10-11
> **ki4jgt said:**
> Thanks :) What about singling out specific variables? Is this possible with a decompiler? Like say I permenantly set x = 5. Could a decompiler find this information?

It is certainly possible if the code is not obsfucated.

But I can't really say, I've never tried to decompile Java source code.

Why don't you download some of the free Java decompilers and do some tests to see what you get back.

---

### Post by ki4jgt on 2012-10-11
> **xytron said:**
> It is certainly possible if the code is not obsfucated.

But I can't really say, I've never tried to decompile Java source code.

Why don't you download some of the free Java decompilers and do some tests to see what you get back.

Will do. Thanks.

---

### Post by spjackson on 2012-10-11
> **ki4jgt said:**
> Like say I permenantly set x = 5. Could a decompiler find this information?
The value 5 is definitely visible.

Can the reader associate it with a variable named x? If x is a class member, then definitely because that's how reflection works. If x is a variable local to a function, then in theory the bytecode doesn't need to contain the original variable name. I don't know whether it does in practice or not.

---

### Post by PaulM1985 on 2012-10-11
I have used some java decompilers on my own code and I have to say they are very good.  The output was very similar to the original source.  

I continued with making my applet because of the time constraints I had to finish the project.  However, if this is for some personal development project I would suggest that you maybe use something different to an applet if possible, maybe HTML5?  I found lots of browser compatibility issues meaning that people weren't able to play my game.

Paul

---

### Post by Bachstelze on 2012-10-11
Bottom line: if it runs on the user's computer, you should assume the user knows everything about it.

---

