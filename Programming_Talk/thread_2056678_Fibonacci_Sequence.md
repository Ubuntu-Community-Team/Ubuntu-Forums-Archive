---
title: "Fibonacci Sequence"
date: 2012-09-11
forum: Programming Talk
---

### Post by gavv on 2012-09-11
Hi guys, I've been learning how to program recently by watching youtube videos, studying books, and of course, solving simple, yet sometimes difficult, problems. I haven't gotten to anything too complicated, but here's a sample of what I've been doing (using the java acm.program library).  

```
import acm.program.*;

/*
 * The following program lists the Fibonacci numbers to 10,000.
 */
public class FibonacciSequence extends ConsoleProgram{
    
    private static final int MAX_TERM_VALUE = 10000;
    
    public void run() {
        println("This program lists the Fibonacci Sequence to 10,000.");
        
        int term0 = 0;
        int term1 = 1;
        println(term0);
        println(term1);
        
        int olderTerm = term0;
        int oldTerm = term1;
        int term = oldTerm + olderTerm;
        
        /*
         * term, oldTerm, and olderTerm can be thought of as an, an-1, and an-2 respectively
         */
        while (term < MAX_TERM_VALUE) {
            println(term);
            olderTerm = oldTerm;
            oldTerm = term;
            term = oldTerm + olderTerm;
        }
    }
}
``` As you can see, the output is the Fibonacci Sequence. Of course, there are betters ways to solve this problem, but I'm wondering if what I did is generally okay. While trying to solve it, I tried approaching it using recursion, but that didn't turn out so good (I haven't really learned or done much of it). Anyways, some input or ideas would be great if you have any.

(If you want to talk about some of the resources I'm using or some other problems, just send me a PM)

---

### Post by uRock on 2012-09-11
Moved to ***Programming Talk***

---

