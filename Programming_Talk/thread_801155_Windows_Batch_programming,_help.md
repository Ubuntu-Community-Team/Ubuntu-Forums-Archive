---
title: "Windows Batch programming, help"
date: 2008-05-20
forum: Programming Talk
---

### Post by Luke has no name on 2008-05-20
Does anyone have some good links for learning batch scripting?

I have to write a script that tests IP addresses from a text file (line-delimited) to ping them and see if they are online, then append to a file.
 
I could much more easily do this in C++, but my employer does not allow "unauthorized downloads".

---

### Post by Phenax on 2008-05-20
Easy one-liner in batch.
```

FOR /F %%i IN (C:\input.txt) DO @ping %%i >> "C:\output.txt"
```

---

### Post by LaRoza on 2008-05-20
> **Luke has no name said:**
> Does anyone have some good links for learning batch scripting?

I have to write a script that tests IP addresses from a text file (line-delimited) to ping them and see if they are online, then append to a file.
 
I could much more easily do this in C++, but my employer does not allow "unauthorized downloads".

My wiki. For something like this, a scripting language is well suited. C++ is way overkill.

---

### Post by Majorix on 2008-05-20
> **Luke has no name said:**
> I could much more easily do this in C++, but my employer does not allow "unauthorized downloads".

You should tell him about your situation and perhaps ask for his permission, then it will be an "authorized download".

Seriously, it would be tough work to do that without a real language to program in.

---

### Post by LaRoza on 2008-05-20
> **Majorix said:**
> You should tell him about your situation and perhaps ask for his permission, then it will be an "authorized download".

Seriously, it would be tough work to do that without a real language to program in.

Batch and the WSH are the tools that are available. Both are well suited for this task.

C++ isn't the tool for such a task. Note, the one line Batch verses how many lines of C++ code needed?

If one really wanted to use C++, one could use DevC++ portable from portableapps.com.

---

