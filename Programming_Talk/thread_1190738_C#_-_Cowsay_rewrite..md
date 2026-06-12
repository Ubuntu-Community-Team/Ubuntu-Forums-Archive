---
title: "C# - Cowsay rewrite."
date: 2009-06-18
forum: Programming Talk
---

### Post by -grubby on 2009-06-18
I'm rewriting cowsay in C# as a practice exercise, and I have this functioning code: [http://pastebin.com/m89f6851](http://pastebin.com/m89f6851). However, in my crusade to be a perfectionist, I've written this code: [http://pastebin.com/m2cace2df](http://pastebin.com/m2cace2df)

This code fails to compile, returning this error:

```

cowsay.cs(15,9): error CS1002: Expecting `;'
cowsay.cs(16,9): error CS1002: Expecting `;'
Compilation failed: 2 error(s), 0 warnings

```

I can't quite figure out what's wrong.

EDIT: Solved.

---

### Post by Zugzwang on 2009-06-18
I don't know C#, but I think that it does not make sense to declare a variable that is only visible inside a code block (void Main) to be private. You might need to put the "private string text" outside the main function and replace that line by "text = ....". Same for the next line.

---

### Post by Habbit on 2009-06-18
You are trying to declare local variables as "private". This makes no sense, but I don't know why the compiler is complaining that it was expecting end-of-statement.

---

### Post by -grubby on 2009-06-18
> **Habbit said:**
> You are trying to declare local variables as "private". This makes no sense, but I don't know why the compiler is complaining that it was expecting end-of-statement.

I got this crazy idea that would declare them as variables only accessible from the current class. Should I use 

```

string this.text = string.Join(" ", args);
int this.length = this.text.Length + 2;

```

instead?

---

### Post by Habbit on 2009-06-18
First of all, "Main" is a _static_ method. You don't have access to "this" because there is no current instance. It doesn't matter that you put Main in the Cowsay class: if you want a Cowsay object you have to create it. Second, class variables, either instance or static, must be declared at class scope, not within methods of the class.

---

### Post by -grubby on 2009-06-18
> **Habbit said:**
> First of all, "Main" is a _static_ method. You don't have access to "this" because there is no current instance. It doesn't matter that you put Main in the Cowsay class: if you want a Cowsay object you have to create it. Second, class variables, either instance or static, must be declared at class scope, not within methods of the class.

Yeah, excuse my mistakes, I feel like I'm trying to write Python code in C#. Anyways, can you post some example code for me? I've looked through a lot of tutorials, and they confused me.

---

### Post by -grubby on 2009-06-18
Well, after some program restructuring, I've come up with a new solution: [http://pastebin.com/m3ffe098a](http://pastebin.com/m3ffe098a). 

Any critique would be nice, too.

---

