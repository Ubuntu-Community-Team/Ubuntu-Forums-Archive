---
title: "Qt problem with GUI application error:&quot;collect 2: ld&quot;"
date: 2010-04-17
forum: Programming Talk
---

### Post by hakermania on 2010-04-17
Hi all!
I am new to GUI programming.
I am trying to link files, headers, etc in C++ using QtCreator but I always take this error:
```
:-1: error: collect2: ld returned 1 exit status
```
This never happens when files aren't linked.
This error is followed by the following notes:
```
/home/alex/Qt/test2/main.cpp:40: undefined reference to `LCDRange::setValue(int)'
/home/alex/Qt/test2/main.cpp:26: undefined reference to`CannonField::CannonField(QWidget*)'

```
and some similar.....I know that ld is a unix consol command but 'man ld' doesn't helped me a lot to solve my problem....
Can I rely on you?:)?

---

### Post by Zugzwang on 2010-04-17
The error messages mean that you declared the functions "LCDRange::setValue(int)" and "CannonField::CannonField(QWidget*)" in your code and use them, but you did not include any source/object file that contains the *definitions* for these functions. Thus, the executable cannot be linked, which results in "ld" giving this error. It has nothing to do with QT, though.

---

### Post by hakermania on 2010-04-17
The program I try to make was taken from a very good site.
It can't be wrong.
I made all the source files and tried to compiling it and I came with all these errors.
It hasn't to do with errors of the code.....
To access the program I am trying to make follow this link:
[http://doc.trolltech.com/4.3/tutorial-t8.html](http://doc.trolltech.com/4.3/tutorial-t8.html)
I have made the program.See screenshot:
[IMG]http://i39.tinypic.com/16hvva0.png[/IMG]

So I don't believe that there is my wrong...
Something generally goes wrong...

---

### Post by Zugzwang on 2010-04-17
How does the "test2.pro" look like? Did you made it yourself? Does it include the two other source files in the source file list? If not, fix this!

---

### Post by gmargo on 2010-04-17
That tutorial lists 5 files, and you have included only one of them in your project.  Include the "lcdrange.cpp" & .h, and "cannonfield.cpp" & .h in your project as well.

---

### Post by hakermania on 2010-04-17
Ok, lets see the tutorial No 7 in which there are only 2 additional files (I have the same error but only 2 notes)
This is the tutorial:
[http://doc.trolltech.com/4.3/tutorial-t7.html](http://doc.trolltech.com/4.3/tutorial-t7.html)
This is the main.ccp:
[http://doc.trolltech.com/4.3/tutorial-t7-main-cpp.html](http://doc.trolltech.com/4.3/tutorial-t7-main-cpp.html)
This is the lcdrange.h:
[http://doc.trolltech.com/4.3/tutorial-t7-lcdrange-h.html](http://doc.trolltech.com/4.3/tutorial-t7-lcdrange-h.html)
This is the lcdrange.cpp:
[http://doc.trolltech.com/4.3/tutorial-t7-lcdrange-cpp.html](http://doc.trolltech.com/4.3/tutorial-t7-lcdrange-cpp.html)

I have created both lcdrange.h and lcdrange.cpp.
I have made with QtCreator the main.cpp. See the screenshot:
[IMG]http://i41.tinypic.com/2z7ero6.png[/IMG]
Now...As you can see I have copy-pasted the code and all the needed files.
The error exists. Why?
EDIT: And when I include lcdrange.cpp ( #include "lcdrange.cpp" ) there is the same error with 2 additional notes....
EDIT2: As for the test2.pro was created automatically by QtCreator and looks like this:
   ```
#-------------------------------------------------
 #
 # Project created by QtCreator 2010-04-17T17:23:20
 #
 #-------------------------------------------------
 
 QT       += script webkit xml xmlpatterns testlib dbus
 
 TARGET = test2
 CONFIG   += console
 CONFIG   -= app_bundle
 
 TEMPLATE = app
 
 
 SOURCES += main.cpp
```

---

### Post by Zugzwang on 2010-04-17
You see the line
```

SOURCES += main.cpp

```
in your project file, right?

Change it to:

```

SOURCES += main.cpp cannonfield.cpp lcdrange.cpp

```

...because without this line, "cannonfield.cpp" and "lcdrange.cpp" are totally ignored by the compiler/linker. QTDevelop does not automatically add anything to your project, you have to do it yourself.

---

### Post by hakermania on 2010-04-17
I changed it as you told me with lcdrange.h and lcdrange.cpp because these are used in tutorial No7. The lcdrange.h and lcdrange.cpp can now be shown adn accessed in the left. Although the same error message exists.See screenshot plZ:
_[IMG]http://i43.tinypic.com/4rqqvs.png[/IMG]_

---

### Post by hakermania on 2010-04-18
Any other suggestion ?

---

### Post by Zugzwang on 2010-04-18
Note that it is not the same error message as before! "ld returned 1 exit status" only tells you that linking failed. But the lines before tell you *what* actually went wrong. Always start reading the error messages from the first line! You will see that the error message has changed from "undefined reference to LCD..." to "undefined reference to vtable". This message usually occurs if you forgot to define some virtual functions that you declared in your program. And yes, that error message is not particularly helpful.

Google for that error message for details. Perhaps you want to paste your "lcdrange.cpp" and "lcdrange.h" here, so we can tell you what is wrong?

---

### Post by gmargo on 2010-04-18
Are you using the correct version of lcdrange.cpp?  Note that both Tutorials 7 & 8 have an lcdrange.cpp (and .h) file but they are different.

---

### Post by hakermania on 2010-04-18
[Zugzwang]("http://ubuntuforums.org/member.php?u=403348") thx I'll do so soon and i'll let you know...
[gmargo]("http://ubuntuforums.org/member.php?u=1009937") good thought but I doubled checked it. Alright.

---

### Post by gmargo on 2010-04-18
I can confirm now that both tutorials 7 & 8 work as distributed.  I was able to compile both on the command line using qmake and make.

I had a hard time finding the source for those tutorials in an easily downloadable form.  If there's a link on the tutorial page you linked to, I didn't see it.  Ultimately I got them from the qt4-doc package for Hardy.

---

### Post by hakermania on 2010-04-20
> **gmargo said:**
> 
I had a hard time finding the source for those tutorials in an easily downloadable form.  If there's a link on the tutorial page you linked to, I didn't see it.  Ultimately I got them from the qt4-doc package for Hardy.

What do you mean? The files were below the header of each example! You copied/pasted them in an editor and saved it with the specific filename.....I cannot steal do nothing about compiling the programs. Same error...

---

### Post by gmargo on 2010-04-20
> **hakermania said:**
> What do you mean? The files were below the header of each example! You copied/pasted them in an editor and saved it with the specific filename.....I cannot steal do nothing about compiling the programs. Same error...

Why would I waste my time copy/pasting when I can download it? Did you ever get the original unmodified tutorial #7 code to compile?

---

### Post by hakermania on 2010-04-21
Not really........but this haven't to do with....
I have tried with almost 55 GUI programs using QTCreator and I have always the same and same problem......
I even tried with the e-book C++ GUI Programming With QT 4 (second edition) and I stuck in the first chapter-example that uses one .h and one .cpp file linked. I tried everything.
The thing is that I like programming and I'll not give up till I find a solution in this problem. But I need your help because I have really tried EVERYTHING

---

### Post by Zugzwang on 2010-04-21
Again, would you mind pasting the files "lcdrange.h", "lcdrange.cpp", "main.cpp" and the project file here? Then we can have a look.

---

### Post by gmargo on 2010-04-21
> **Zugzwang said:**
> Again, would you mind pasting the files "lcdrange.h", "lcdrange.cpp", "main.cpp" and the project file here? Then we can have a look.

Attached is a compressed tar archive of the four files from tutorial #7, from the Hardy qt4-doc package:

```

$ ls -lGg
-rw-r--r-- 1  2911 Feb 19  2008 lcdrange.cpp
-rw-r--r-- 1  2466 Feb 19  2008 lcdrange.h
-rw-r--r-- 1  3313 Feb 19  2008 main.cpp
-rw-r--r-- 1   370 Feb 19  2008 t7.pro

```

---

### Post by Zugzwang on 2010-04-22
> **gmargo said:**
> A
```

$ ls -lGg
-rw-r--r-- 1  2911 Feb 19  2008 lcdrange.cpp
-rw-r--r-- 1  2466 Feb 19  2008 lcdrange.h
-rw-r--r-- 1  3313 Feb 19  2008 main.cpp
-rw-r--r-- 1   370 Feb 19  2008 t7.pro

```

These are obviously not the "lcdrange.cpp" and "lcdrange.h" files that the OP has (see screenshot).

@OP: Would you mind posting your files?

---

### Post by gmargo on 2010-04-22
> **Zugzwang said:**
> These are obviously not the "lcdrange.cpp" and "lcdrange.h" files that the OP has (see screenshot).

@OP: Would you mind posting your files?

He cut/pasted and omitted the copyrights, so the size won't even be close.

---

