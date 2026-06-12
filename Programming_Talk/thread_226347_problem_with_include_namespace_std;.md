---
title: "problem with include namespace std;"
date: 2006-07-31
forum: Programming Talk
---

### Post by dynamicron on 2006-07-31
I am new to linux and programming for that matter, so I was wondering if I could get some help on a few questions
1. my compiler isn't recongnizing the line include namespace std;, but if I type it manually on each line ex. std::cout<<, but this is rather timeconsuming when I have a lot of cout statements
2.I cannot get any of my makefiles or configure scripts to work, they all always pop up errors when I try.
3.I am using a Hewlett Packard any help you can give me on this subject would be much appreciated 
Thanks

---

### Post by RafG on 2006-07-31
That should be

```
**using** namespace std;
```

---

### Post by thumper on 2006-07-31
You'd need to give examples of your makefiles, the commands you are typing in to invoke them, and all the output it generates.

Without those everyone is really guessing to what your problem is.

---

