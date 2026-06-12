---
title: "Shell scripting/piping for c++ input"
date: 2010-07-19
forum: Programming Talk
---

### Post by RocketmanOU on 2010-07-19
I'm working on an automatic grading script to compile and run very simple c++ programs, enter some standard inputs and record the standard output to a file. Essentially, the programs I'm working with all require (in the exact same order) user input via cin >>, and output (text) results via cout <<. How can I get a shell script to execute the program, enter (serially) multiple input values, and still get the output? Thanks!

---

### Post by Bachstelze on 2010-07-20
No need for a shell script, this can be done directly on the command-line with a one-liner:

```
while read line; do echo "$line" | program; done
```

Ctrl+D to quit.

Bonus: you can have your input in a text file so you don't have to enter it repeatedly:

```
firas@tsukino ~ % cat input.txt 
foo
bar
foobar
foobaz

firas@tsukino ~ % while read line; do echo "$line" | sed s/foo/goo/; done < input.txt
goo
bar
goobar
goobaz


```

---

### Post by MadCow108 on 2010-07-20
you may want to have a look at expect which is a tool to interact and test interactive programs
[http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)

---

### Post by trent.josephsen on 2010-07-20
> **Bachstelze said:**
> No need for a shell script, this can be done directly on the command-line with a one-liner:

```
while read line; do echo "$line" | program; done
```

Ctrl+D to quit.

Erm...  Isn't that identical to

```
$ cat | program
```

Which, unless the program tests the type of its input stream, is the same as just

```
$ program
```

Redirection is as easy:

```
$ program <input.txt
```

---

### Post by Bachstelze on 2010-07-20
> **trent.josephsen said:**
> Erm...  Isn't that identical to

```
$ cat | program
```

Which, unless the program tests the type of its input stream, is the same as just

```
$ program
```

Redirection is as easy:

```
$ program <input.txt
```

No.  In your version, the input is piped to the program in one block, while mine reads the input line-by-line, and pipes each line separately to a different instance of the program.  Using the same file I used above:

```
firas@tsukino ~ % cat input.txt 
foo
bar
foobar
foobaz

firas@tsukino ~ % cat test.c 
#include <stdio.h>

int main(void)
{
        char s[10];
        scanf("%s", s);
        printf("Input: %s\n", s);
        return 0;
}

firas@tsukino ~ % cc -o test test.c
firas@tsukino ~ % ./test < input.txt 
Input: foo
firas@tsukino ~ % while read line; do echo "$line" | ./test; done < input.txt 
Input: foo
Input: bar
Input: foobar
Input: foobaz
Input: 

```

Of course, whether you use one method or the other depends on how the program behaves (i.e. whether it accepts only one or any number of input lines).  I understood the OP as saying input must be piped to the program one line at a time, but I might be wrong.

---

### Post by trent.josephsen on 2010-07-20
*facepalm*

Of course, you're right.  I was reading it as

```
while read line; do echo "$line"; done | program
```

which acts as I described.  But then I interpreted the OP's request differently, which explains why I was expecting something else.

---

