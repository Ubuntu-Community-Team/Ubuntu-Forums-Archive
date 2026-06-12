---
title: "obfuscating python3 programs"
date: 2011-09-28
forum: Programming Talk
---

### Post by serafim on 2011-09-28
Hi,
I am a teacher at a technical university and when I give my students programming tasks I also want to give them a runnable example of what they are supposed to create.

So I want to be able to obfuscate my own solution into a runnable that that does not reveal the underlying code.

I have done it in Java, C, C++, Pascal, and even different flavours of Lisp. But I can't figure out how to do it in Python 3.

Any ideas? I'm kind of new to Python myself.

All student computers use Ubuntu Linux.

---

### Post by Smart Viking on 2011-09-28
The simplest answer is that you can't.

If the programs are simple and the students aren't supposed to know how it works, why not create them in another language and obfuscate that?

---

### Post by mcduck on 2011-09-28
Write the programs in Perl instead to make them unreadable? ;)

Python isn't really something you could obfuscate very well. I suppose compiling your example into bytecode would help a bit, but even then it can be disassembled back to source. Same goes for bundling the program into a .exe/.app.

Actually I agree with Smart Viking, if the students aren't even supposed to be able to read the example code to see how it works, does it really make any difference what language you use for the example?

---

### Post by ofnuts on 2011-09-28
> **serafim said:**
> Hi,
I am a teacher at a technical university and when I give my students programming tasks I also want to give them a runnable example of what they are supposed to create.

So I want to be able to obfuscate my own solution into a runnable that that does not reveal the underlying code.

I have done it in Java, C, C++, Pascal, and even different flavours of Lisp. But I can't figure out how to do it in Python 3.

Any ideas? I'm kind of new to Python myself.

All student computers use Ubuntu Linux.
Not too much expert in this, but you can deliver python modules in "compiled" form (.pyc). So you can split your code into some trivial main (let's call it "main.py") that remains in the clear and imports the compiled module where your real code is (source in, say, "module.py"). When executing, if you have R/W rights, python will automatically create a "module.pyc" file (it recompiles if it finds that module.py is more recent than module.pyc). The trick is that once your code works, you can deliver main.py with module.pyc and keep module.py for yourself.

---

### Post by serafim on 2011-09-28
Thanks all, I have all the answers I need.

---

### Post by juancarlospaco on 2011-09-28
PyOfuscate, but i dont agree the idea...

---

### Post by DangerOnTheRanger on 2011-09-28
> **juancarlospaco said:**
> PyOfuscate, but i dont agree the idea...

The OP author wants to obfuscate his/her Python code so the university students they teach cannot reverse-engineer his/her example problem solution, that's all.

---

### Post by juancarlospaco on 2011-09-28
> **DangerOnTheRanger said:**
> The OP author wants to obfuscate his/her Python code so the university students they teach cannot reverse-engineer his/her example problem solution, that's all.

Ive read, but thanks DangerOnTheRanger...   :)

---

### Post by DangerOnTheRanger on 2011-09-28
> **juancarlospaco said:**
> Ive read, but thanks DangerOnTheRanger...   :)

OK, just making sure :)

---

### Post by nvteighen on 2011-09-29
If you are a programming teacher in a technical university, please, use the technical terms. Obfuscation doesn't mean compilation and I'm not sure what a runnable is, specially in a UNIX/Unix-like system, where a shebang makes almost anything "runnable". So, do you want to obfuscate the code, compile Python code and provide an executable or what?

Obfuscating Python code is hard, because the language was designed to make everything clear and tidy; it's part of its core design. In other languages, clearness and tidiness is the programmer's responsability, so you can obfuscate code more easily in them. But I wonder, why would you provide an obfuscated source file to your students? If you just want to give them something that's executable, compile and that's it... Obfuscated code can still be read by a human and it may even teach your students very bad programming. (Mainly, obfuscation is a very bad practice: code should be easily readable, for better mantaining).

If you're talking about compiling Python, you should do what ofnuts has alreadytold you: give them the .pyc files. You can generate it by **importing** the module at the Python shell.

Now, wouldn't it be more senseful to just give your students a regular assignment and then give them your solution in class, after they submitted their own (so that reading your class cannot have any effects on them doing their work)? In my little paedagogical experience at university, the less concocted the teaching method, the better.

---

### Post by juancarlospaco on 2011-09-29
Also Python can run code compressed like standard .ZIP files...

---

