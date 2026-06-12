---
title: "Can you recommand a good tool to read source code?"
date: 2012-06-26
forum: Programming Talk
---

### Post by qiushuichangtian on 2012-06-26
Hello everyone! I want to read source code such as linux kernel. Can you recommand a good tool to use? I know that we can use SourceInsight to do that. Of course it is convient. But what tool can we use when we work in Ubuntu 11.10?:(

---

### Post by Zugzwang on 2012-06-26
The most commonly used tool is **doxygen**. It will create call graphs and other documentation for your code, that can then be read using a web browser.

---

### Post by 11jmb on 2012-06-26
Generating a call graph with doxygen or a profiling tool is useful for getting to know the code, but for doxygen to really serve its purpose in generating documentation pages, your code needs to be commented in a certain way.

Another useful tool for reading source code is a good editor/IDE which does syntax highlighting and code folding. IDE's will have other advanced features that may help your experience of reading the source code. For example, in Eclipse, you have the ability to navigate to the definition of a function being called, which is extremely useful.

---

### Post by trent.josephsen on 2012-06-26
I recommend using your eyes. A good editor helps too. I like Vim.

---

### Post by MG&amp;TL on 2012-06-26
```
for file in $(find .)...
```

;)

No, seriously, I usually go through directories recursively and open every file in that directory up with my favourite editor, then close it again and move on. I find that the major functionality is in the toplevel directory, and other stuff is in subdirectories. So you slowly build up a picture.

---

### Post by ksprasad on 2012-06-26
Hi,
 
If you use vim, then i recommand  **exuberant-ctags. **
This is helpful to navigate between function calls.
 
Regards,
ksprasad

---

### Post by Simian Man on 2012-06-26
cscope is a great tool for this.  It lets you look up definitions, find which functions call, or are called by, a given function and more.

---

