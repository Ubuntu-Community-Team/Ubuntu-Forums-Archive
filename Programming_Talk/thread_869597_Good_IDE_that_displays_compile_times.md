---
title: "Good IDE that displays compile times"
date: 2008-07-25
forum: Programming Talk
---

### Post by coreyxjessica on 2008-07-25
I would like some recommendations on some good IDEs that support many languages (python at least) and also display the time to compile. Thanks in advance.

---

### Post by slavik on 2008-07-25
you mean how long it will take to compile or how long it took to compile?

---

### Post by mssever on 2008-07-25
You said that you're looking for an IDE that at least supports Python. Compilation time for Python is insignificant. So...

---

### Post by coreyxjessica on 2008-07-25
> **slavik said:**
> you mean how long it will take to compile or how long it took to compile?
How long it will take to write a program in a programming language in the IDE. Like say I write Hello World, it'll say compiled in 0.2ms and I can use that information to see what algorithms provide more efficient code. Hope that clears things up. :)

---

### Post by slavik on 2008-07-25
umm, you want to use a benchmarking module if Python has one (I am not exactly experienced with Python). but I could easily provide an example where compilation is very short but run time is very long.

you have to understand that with most/all scripts, compilation and execution are two distinct steps made to look like one.

---

### Post by coreyxjessica on 2008-07-25
> **slavik said:**
> umm, you want to use a benchmarking module if Python has one (I am not exactly experienced with Python). but I could easily provide an example where compilation is very short but run time is very long.

you have to understand that with most/all scripts, compilation and execution are two distinct steps made to look like one.

Oh okay then let me add time to compile and execute the code. I'm kind of getting back into programming and a lot of this is fuzzy to me. I essentially want some IDE to be able to benchmark my code.

---

### Post by slavik on 2008-07-25
no IDE that I know of. look up the time command though :)

---

### Post by mssever on 2008-07-25
> **coreyxjessica said:**
> Oh okay then let me add time to compile and execute the code. I'm kind of getting back into programming and a lot of this is fuzzy to me. I essentially want some IDE to be able to benchmark my code.
 In Python, modules you import are compiled to bytecode and saved, so you only pay that penalty once. I'm sure there is a profiling tool.


In Ruby (which I know better than Python), you can do ```
require 'profiler'
```
Then, when you run your code, Ruby will spit out a bunch of profiling data, though the act of profiling slows down the program quite a bit. I'm guessing Python has a similar module that you can import. Look through the standard library.

---

