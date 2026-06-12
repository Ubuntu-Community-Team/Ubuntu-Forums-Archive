---
title: "building python script"
date: 2007-03-11
forum: Programming Talk
---

### Post by soul814 on 2007-03-11
I was bored so I decided to mess around with python, I figured out how to build the script into an exe files using windows. How do you build the file in linux and make it accessible on other operation systems / computers if they do not have python installed?

---

### Post by pmasiar on 2007-03-11
> **soul814 said:**
>  How do you build the file in linux and make it accessible on other operation systems / computers if they do not have python installed?

Most linux distros do have Python installed - all mainstream distros do, but possibly some obscure/memory restricted distros may not. You can distribute your code as plain source, should work on any Linux platform with required libraries. For more sophisticated distribution of Python code, look up Python egg package format.

---

