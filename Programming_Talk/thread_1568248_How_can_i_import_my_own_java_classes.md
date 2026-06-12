---
title: "How can i import my own java classes?"
date: 2010-09-04
forum: Programming Talk
---

### Post by BlackSwordD2 on 2010-09-04
im using Netbeans an di have several programs that a related that i wish to combine into a larger program.

they are all separate packages and stand alone as it is. instead of simply rewriting and copy-pasting to make what i want, i want to create more of an umbrella program to merge them.

for example one program i wish to use is a RandomNameGen.java and i want to place it in Umbrella.java what's the syntax to import RandomNameGen.java?

---

### Post by hanniph on 2010-09-04
Java libraries are usually distributed in a form of .jar files. So one way you can do this is to create .jar file from the code you want to import and then add generated .jar file to your build path.

---

### Post by BlackSwordD2 on 2010-09-04
how would i do that?

---

### Post by KdotJ on 2010-09-05
You can just import the package, if it's in a sub folder of the umbrella package surely?

Say the folder is called randomgen, you would import it like so...

```
import randomgen.*;
```

With the rest of your imports at the top. 

Note. I may be a little wrong, someone will correct me if I am. It's been a while since I worked with seperate packages, and even longer since I read it in a java book

---

