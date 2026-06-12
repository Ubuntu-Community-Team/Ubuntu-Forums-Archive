---
title: "Java and Swing Textboxes"
date: 2008-10-25
forum: Programming Talk
---

### Post by loganwm on 2008-10-25
I've begun studying Java and I can honestly say that I am quite amazed by the portability and the syntax.

I've been learning the ins and outs of the Swing classes and I have been unable to find how to create a simple, single line textbox that I can use for short input.

Anyone have any ideas on how to accomplish this?


And if you have not messed with Java before, you might want to consider at least trying it out to see the neatness of the bytecode-vm model.  It's really "cool" in my opinion.

---

### Post by CptPicard on 2008-10-25
JTextField?

And yeah, the bytecode model is indeed cool and the JVM is quite an optimized piece of code to boot. Java the platform is the interesting part, not so much Java the language, which I consider fairly boring and pedestrian in style really... it's just a simplified C++ with garbage collection :)

But, the good bit is that you can run something like Clojure and Groovy on the same JVM, with full access to the standard class libraries... this is where stuff gets *really* interesting.

---

### Post by drubin on 2008-10-25
If you want an input dialog. (but this would be a pop up) Use 
```
JOptionPane.showInputDialog(....)
```

---

