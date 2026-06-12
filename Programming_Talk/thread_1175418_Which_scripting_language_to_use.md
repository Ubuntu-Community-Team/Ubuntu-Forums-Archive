---
title: "Which scripting language to use?"
date: 2009-06-01
forum: Programming Talk
---

### Post by Richard_ on 2009-06-01
I have recently dabbled in a bit of bash scripting, but I'd like to get some input from experienced users as to what scripting languages you guys use most often, and why. I've heard of people using python as well as php. Any advice? I have no specific use, basically just day-to-day automation.

---

### Post by sujoy on 2009-06-01
sed, awk, bash, perl, python, ruby, ...

for me, anything that goes beyond 50 lines, gets converted to perl,python or ruby, based on the problem. otherwise bash is fine

---

### Post by Tibuda on 2009-06-01
> **sujoy said:**
> for me, anything that goes beyond 50 lines, gets converted to perl,python or ruby, based on the problem. otherwise bash is fine

That's a good advice.

---

### Post by CptPicard on 2009-06-01
And I would suggest that out of those three, you pick your poison and stick to it until you're good. They can serve the same purpose yet are different, and bouncing back and forth is not going to be of much use. My personal preference is Python as it scales to other stuff than scripts too...

---

### Post by Volt9000 on 2009-06-01
I've just starting getting into bash scripting myself, and I'm finding that sed and awk are pretty important/powerful.

I'm also getting into Python, which is also quite useful, as it's a very high-level structured language.

---

### Post by ghostdog74 on 2009-06-02
> **Volt9000 said:**
> I'm finding that sed and awk are pretty important/powerful.
i can safely tell you that if you learn awk throughly (not just for one liners), you can forget about sed.(or even grep/cut/wc). this will greatly reduce your learning curve with shell scripting.

---

### Post by Bodsda on 2009-06-02
I  use python usually, but I find myself only using python for flow control and then using the os module a lot.

Suppose I should just bite the bullet and learn bash -- or can python perform day-to-day tasks like moving files, deleting things, renaming etc. without excessive use of the os module?

---

### Post by CptPicard on 2009-06-02
> **Bodsda said:**
> I  use python usually, but I find myself only using python for flow control and then using the os module a lot.

Which I tend to do as well...

> 
Suppose I should just bite the bullet and learn bash -- or can python perform day-to-day tasks like moving files, deleting things, renaming etc. without excessive use of the os module?

Bash is "often useful" and my view on it would be that you can learn it as you go about doing your stuff, but what is this aversion to using the os module? It is there to be used...

---

### Post by sujoy on 2009-06-02
while there is no reason why the os module shouldnt be used, may i still recommend shutil for file transfer (copy, move, etc), since it aims to be a bit more portable.

---

### Post by wmcbrine on 2009-06-02
> **Bodsda said:**
> can python perform day-to-day tasks like moving files, deleting things, renaming etc.Of course.

> *without excessive use of the os module?*That makes no sense. Naturally these functions are in the os module, and there's nothing wrong with that. If you just don't want to bother typing "os.", then do "from os import *". (You can do that with any module.)

But I wonder if what you really mean is "... without using os.system()" (or, better, the subprocess module)? Then the answer is, again, yes.

---

### Post by hanniph on 2009-06-04
> **sujoy said:**
> sed, awk, bash, perl, python, ruby, ...

for me, anything that goes beyond 50 lines, gets converted to perl,python or ruby, based on the problem. otherwise bash is fine

I know basics of python and I am currently reading about ruby, just out of curiosity, what kind of projects you are likely to code in ruby rather in python and vice versa?

---

### Post by Vadi on 2009-06-04
Lua here. Fast, simple.

---

