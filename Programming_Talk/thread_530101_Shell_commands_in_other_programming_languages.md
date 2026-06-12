---
title: "Shell commands in other programming languages"
date: 2007-08-20
forum: Programming Talk
---

### Post by rharriso on 2007-08-20
I feel like I should know this, but its never come up.

Is it possible to take advantage of the shell commands in languages such as C++ and Java? If so how?

---

### Post by Wybiral on 2007-08-20
> **rharriso said:**
> I feel like I should know this, but its never come up.

Is it possible to take advantage of the shell commands in languages such as C++ and Java? If so how?

Define "take advantage".

I assume by shell commands you mean "system"?

---

### Post by Ramses de Norre on 2007-08-20
Java: **Runtime.getRuntime().exec(*command*);**

C: **system(*command*);**

In Java to catch the output you've got a little more work:
```
InputStream is=Runtime.getRuntime().exec("ls /").getInputStream();
Scanner scan=new Scanner(is);
String out="";
while(scan.hasNext())
{
    out+=scan.nextLine()+"\n";
}
```

In C you can do this by using popen(), but I don't know exactly how to do so.

---

### Post by pmasiar on 2007-08-20
> **Wybiral said:**
> Define "take advantage".

IMHO OP wanted to use OS/shell commands.

This home turf of so called "scripting" languages, like Perl and Python.

---

### Post by rharriso on 2007-08-20
Exactly, I know how to do that in Pearl, but I much prefer C++ and Java. 
I wanted to know how to, I'm going to say output, shell commands from a C++ script.

---

### Post by Mr.Carramba on 2007-08-20
> **Ramses de Norre said:**
> Java: [B][snip]
[/B]In C you can do this by using popen(), but I don't know exactly how to do so.

it's actualy not pure c.. it's POSIX (thread programing), in 
u start new thread were you "save" input or directly pass it to another thread or your maine program

---

### Post by rharriso on 2007-08-20
I tried simply using the system() function in C++. Thats worked with a couple of the commands. Has anyone run into trouble with that method?

---

### Post by Mr.Carramba on 2007-08-20
it is depend what you want to do...
since system() return value is allmost useless for controlling exit status of started aplication

---

