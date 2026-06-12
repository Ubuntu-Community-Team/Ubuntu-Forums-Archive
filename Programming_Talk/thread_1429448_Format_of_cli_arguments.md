---
title: "Format of cli arguments"
date: 2010-03-14
forum: Programming Talk
---

### Post by matmatmat on 2010-03-14
Hello everyone, I am making a todo list program that will need to take in more than piece of data, eg adding the todo item will need to input the project, todo summary and priority. My question is how should they be inputted? At the moment I'm using:
```

./program -a "Program this" "Implement everything" 1 # Project, Summary, Priority

```
But I've never seen this done on any other program.

---

### Post by Barriehie on 2010-03-14
Is this a BASH script???

---

### Post by matmatmat on 2010-03-14
No, a c program

---

### Post by Barriehie on 2010-03-14
> **matmatmat said:**
> No, a c program

whoops,  no help here!  (rediscovering C++ but I'm not moving very fast)

---

### Post by Lux Perpetua on 2010-03-14
You define main() as ```
int main(int argc, char *argv[]) { ... }
```When you execute your program, argc is set to the number of arguments (including the program name), and argv is an array of the arguments, with argv[0] being the name of the program. In your example, you'd have argc = 5, argv[0] = "program", argv[1] = "-a", argv[2] = "Program this", etc.

---

### Post by matmatmat on 2010-03-14
I know, sorry for not being clear. My question is not how you get them but what format are they in. (eg dd has of=/if= but grep uses -i, -v -- which way should I use)

---

### Post by jwbrase on 2010-03-14
I'm not sure that there's "one format to rule them all". Just do whatever works, and if you distribute your program for other's to use, be sure to document your input format.

---

### Post by Compyx on 2010-03-14
I would use the dashes form: '-v', '--verbose', etc. dd's way of specifying options is unusual and only used by dd, as far as I know.

But to be honest, the kind of program you're making would benefit more from using a GUI than from using command line arguments.

---

### Post by nvteighen on 2010-03-14
The thing is people use getopt() from unistd.h... which has that -c (c = character) --string convention... Then, getopt() has been ported to other languages like in Python getopt or Getopts in Perl... Use whatever you like at most, but getopt() automates lots of the manual string processing.

---

