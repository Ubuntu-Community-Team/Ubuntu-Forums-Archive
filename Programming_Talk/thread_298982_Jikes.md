---
title: "Jikes"
date: 2006-11-13
forum: Programming Talk
---

### Post by nikolaos on 2006-11-13
With Jikes:
Do i have to define the directory where 'classes.jar' is, as a $CLASSPATH in order to make it permanent?
Why javac finds 'classes.jar' although it is not in the $CLASSPATH and jikes can't?

What i really want is to avoid wrighting ```
jikes -bootclasspath 'a very long string' file.java 
```
whenever i compile.

Any suggestions?

---

### Post by earobinson on 2006-11-13
you could write a shell script to do it
```
echo jikes -bootclasspath 'a very long string' file.java > quick.sh
```then just do ```
sh quick.sh
``` or just use the up arrow in the terminal to go to the last command

---

### Post by nikolaos on 2006-11-13
Can i do that once or every time i rerun the terminal?

---

### Post by earobinson on 2006-11-13
which one I have you 2 options the first one will make a file named quick.sh in your current directory and any time you are in that directory you can do a ```
sh quick.sh
``` and the second (up arrow) can be done any time your in the terminal and it should work if you close and open the terminal.

---

### Post by nikolaos on 2006-11-13
I am sorry i should have been more specific from the beggining.

i mean the one with quick.sh

The thing is that this way the problem is not solved, by doing ```
sh quick.sh
``` i just recompile the file.java. i want the -bootclasspath to become permanent so i can write just```
jikes file.java 
``` and compile 
and then jikes ```
file2.java 
``` and compile another java file. 
i.e. to make the ```
-bottclasspath 'very long string'
``` option permanent.

---

### Post by shining on 2006-11-13
You just need to edit the quick.sh slightly so that it takes arguments, instead of a fixed filename:
```

echo jikes -bootclasspath 'a very long string' "$@" > quick.sh

```

then you can do 
sh quick.sh file1.java
sh quick.sh file2.java
...

---

### Post by earobinson on 2006-11-13
> **shining said:**
> You just need to edit the quick.sh slightly so that it takes arguments, instead of a fixed filename:
```

echo jikes -bootclasspath 'a very long string' "$@" > quick.sh

```

then you can do 
sh quick.sh file1.java
sh quick.sh file2.java
...
that will work :)

---

### Post by nikolaos on 2006-11-13
I think that solves it. Thanks

---

### Post by nikolaos on 2006-11-13
can i just ask what is the use of "$@"?

---

### Post by shining on 2006-11-13
> **nikolaos said:**
> can i just ask what is the use of "$@"?

It expands to the list of arguments.
If you call the script like that:
quick.sh foo1 foo2 foo3
It'll do:
jikes -bootclasspath 'a very long string' foo1 foo2 foo3

That allows you to add other jikes option when calling it via quick.sh, or calling it on several filenames, if it's possible.

---

### Post by skymt on 2006-11-13
A shell script is overkill. Just add this line to the end of "/home/username/.bashrc":```
alias jikes="jikes -bootclasspath 'a very long string'"
```

Then, when you type "jikes aJavaClass.java", the shell will run "jikes -bootclasspath 'a very long string' a JavaClass.java". If you want to keep the jikes command available, assign the string to a different alias ("jike=", "javaize=", "ezjava=", etc).

---

### Post by nikolaos on 2006-11-14
this is exactly what i needed, thanks.

---

### Post by kumoshk on 2009-06-06
Might I ask for a real working example of what such as the very long string was in your case? Which java did you use?

---

