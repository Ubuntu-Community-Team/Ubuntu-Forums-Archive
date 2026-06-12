---
title: "Java Tutorial Compiling Error"
date: 2014-05-04
forum: Programming Talk
---

### Post by Knax0815 on 2014-05-04
Hi guys,

so I started reading a online book about programming and was starting to do some coding but I bounced into a for me unsolveable error.

The Book, [http://www.javacoffeebreak.com/books/extracts/javanotesv3/index.html](http://www.javacoffeebreak.com/books/extracts/javanotesv3/index.html)

TextIO.class [http://www.javacoffeebreak.com/books/extracts/javanotesv3/source/TextIO.java](http://www.javacoffeebreak.com/books/extracts/javanotesv3/source/TextIO.java)

My Problem, when I am compiling the TextIO.java 

```

javac TestIO.java
```

I get this error msg.

```

TextIO.java:536: error: unreachable statement
            throw new RuntimeException("End-of-file on standard input.");;
                                                                         ^
1 error
```



So I am quiet puzzled, is there some bug in the sourcecode ? Which I can hardly imagine.
I think my problem lies how i copy the text from the webseite into my .java file ? Or any other suggestions how I could fix this problem or where I am doing something wrong.

Here is how I created the file.

```
touch TextIO.java
```

After that I opend the file with the standard texteditior of ubuntu and pasted the code.

Thanks for all help, I hope I explained myself good enough...

---

### Post by dwhitney67 on 2014-05-04
Remove the extra semi-colon at the end of the statement.  Only one semi-colon is needed to terminate a statement.

---

### Post by Knax0815 on 2014-05-04
Hm, okay that solves it. 

Thanks :D

---

