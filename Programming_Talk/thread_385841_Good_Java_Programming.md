---
title: "Good Java Programming"
date: 2007-03-16
forum: Programming Talk
---

### Post by Loft on 2007-03-16
A while ago I started a computer science course at university, but ended up dropping out to take a job in another sector.  Having enjoyed programming in Java, I decided to start again for my own enjoyment.  I stupidly threw out my old notes, but vaguely remember a good practice to do with a runIt() method.  Can anyone look at this code and let me know if it's a good way to run programs in Java? (Excuse the layout!) Thanks.

```
public class CLASSNAME{
                  [INDENT]void runIt(){[INDENT][INDENT]//METHOD BODY[/INDENT][/INDENT][/INDENT]
[INDENT]}[/INDENT]

[INDENT]public static void main(String [] args){[/INDENT]

[INDENT][INDENT]CLASSNAME OBJECTNAME = new CLASSNAME();   //CONSTRUCTOR[/INDENT][/INDENT]
[INDENT][INDENT]OBJECTNAME.runIt();[/INDENT][/INDENT]
[INDENT]}[/INDENT]
}
```

---

### Post by Tomosaur on 2007-03-16
The runIt idea is a general ease-of-understanding convention, and not one which is widely followed or even used, because in some applications it's impractical, and in others it's completely pointless. For example, what if your class constructor takes input and decides what to do using a switch statement? Should you put the switch in a runIt() statement, thereby needlessly increasing the length of the source file, or should you put the switch statement into the constructor / main method, and have a bunch of different runIt() methods depending on each case? Or, should you just do all processing inside the constructor, and just call methods as and when you need them? In some cases, where there is only one possible course of action, and where the procedure is sequential and pretty long, then yes, a runIt() method could be useful, because it would allow you to avoid a long constructor / main method.

However, it really depends on the application. Sometimes yes, sometimes no. Aside from personal preference, there is no real necessity to do it. The whole point of Java is to group logically related things together - you should be doing the same with your methods. Rather than having one big runIt() method doing everything, you should divide each operation into it's own method. If your method is longer than one 'page' of source code, then it probably is doing too many things. Split it up, and your code will be more understandable, extensible, and maintainable.

---

### Post by Ramses de Norre on 2007-03-16
We always get the advice at university to split up methods as soon as they become longer than 10 lines... Our professor does like many little methods ;)
But I have to admit that it also makes the code very easy to change.

---

### Post by pmasiar on 2007-03-16
[TDD](http://en.wikipedia.org/wiki/Test_driven_development) suggest to start with tests - which will nudge you to create API with small, testable methods. If method cannot be printed on single page, or you have 'and' in description, or you have more than 3-4 levels if indent (for/if), it might be too complex. But giving them all good names is also hard: you do not want hundreds of bite-size methods with meaningless names.

---

