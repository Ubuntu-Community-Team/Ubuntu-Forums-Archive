---
title: "Java basic"
date: 2011-01-01
forum: Programming Talk
---

### Post by Gopal Mondal on 2011-01-01
[I][FONT=Times New Roman][SIZE=4][COLOR=Blue]Hello,

I am new user of ubuntu..
I want to know how to open a file of java in terminal (like in c it is emacs programname.c)
& how to compile(like in gcc its cc programname.c -o object name)
& how to run(like in c ./object name or ./ a.out).

Thank you i advance[/COLOR][/SIZE][/FONT][/I]

---

### Post by SNYP40A1 on 2011-01-01
Check out the Eclipse project.  They have a great Java IDE.  If you simply want to view the Java file, try gedit.  To compile, you will need to have a Java SDK installed.  Not sure if OpenJDK is installed by default.

[http://www.eclipse.org/](http://www.eclipse.org/)

---

### Post by Nytram on 2011-01-01
> **Gopal Mondal said:**
> [I][FONT=Times New Roman][SIZE=4][COLOR=Blue]Hello,

I am new user of ubuntu..
I want to know how to open a file of java in terminal (like in c it is emacs programname.c)
& how to compile(like in gcc its cc programname.c -o object name)
& how to run(like in c ./object name or ./ a.out).

Thank you i advance[/COLOR][/SIZE][/FONT][/I]

Hi Gopal,

1. To open a file of java in the terminal you can use the same command as for a C file, although the file extension should be .java.

[PHP]
emacs Filename.java
[/PHP]

2. To compile it

[PHP]
javac Filename.java
[/PHP]

3. To run

[PHP]
java Filename
[/PHP]

---

