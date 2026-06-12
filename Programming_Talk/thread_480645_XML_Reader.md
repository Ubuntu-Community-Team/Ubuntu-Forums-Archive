---
title: "XML Reader"
date: 2007-06-21
forum: Programming Talk
---

### Post by ShareBuntu on 2007-06-21
Hi folks,

I'm looking at creating a basic XML reader that'll end up working with a lot of feeds. I've got a basic Perl mock-up working but it seems rather slow. I'm almost positive this is because of my internet connection speed.

My question is, how would Perl compare to other languages like C and Python in terms of pulling feeds from the net and doing other things like string comparison and manipulation?

---

### Post by pmasiar on 2007-06-21
Python has elementtree XML parser which is stroke of pure genius! Converts XML to tree of dictionaries (with search functions). Very intuitive, simple and pythonic. And fast - deep inside it is C code. Standard library in Py2.5 in feisty.

---

### Post by ShareBuntu on 2007-06-21
> **pmasiar said:**
> Python has elementtree XML parser which is stroke of pure genius! Converts XML to tree of dictionaries (with search functions). Very intuitive, simple and pythonic. And fast - deep inside it is C code. Standard library in Py2.5 in feisty.
Thank you for the reply. I rewrote the reader in Python and it seems a lot faster than Perl. I considered PHP but I don't really think that'll add up from a performance perspective. Looks like my technologies of choice are shifting toward PHP, Python and MySQL. :D

---

