---
title: "Parsing config files in C++"
date: 2007-09-23
forum: Programming Talk
---

### Post by maddog39 on 2007-09-23
Hello All,

Im writing an application in C++ and having trouble finding a way to use/parse text configuration files to save user settings. The configuration files will be in the following format:
```

# id=value
mysetting=this is my value

```and each line is delimited by a line break. Just curious if anyone has suggestions as to what's the best way to parse this so that I can just store the id's and values vectors or something for easy access from within the application.

Thanks!
-maddog39

---

### Post by aks44 on 2007-09-23
[boost::spirit]("http://spirit.sourceforge.net/") is a good parser for such tasks IMHO.

> Spirit is an object oriented recursive descent parser framework implemented using template meta-programming [1] techniques. Expression templates [2] allow us to approximate the syntax of Extended Backus Normal Form [3] (EBNF) completely in C++. Parser objects are composed through operator overloading and the result is a backtracking, top down parser that is capable of parsing rather ambiguous grammars.

The Spirit framework enables a target grammar to be written exclusively in C++. Inline EBNF grammar specifications can mix freely with other C++ code and, thanks to the generative power of C++ templates, are immediately executable.

---

### Post by gnusci on 2007-09-23
check this thread first:

[http://ubuntuforums.org/showthread.php?t=551926](http://ubuntuforums.org/showthread.php?t=551926)

---

### Post by hod139 on 2007-09-23
Boost::Spririt may be a bit overkill.  If all you want is a simple tokenizer, boost also provides that.  [http://www.boost.org/libs/tokenizer/index.html](http://www.boost.org/libs/tokenizer/index.html)

---

### Post by maddog39 on 2007-09-23
> **hod139 said:**
> Boost::Spririt may be a bit overkill.  If all you want is a simple tokenizer, boost also provides that.  [http://www.boost.org/libs/tokenizer/index.html](http://www.boost.org/libs/tokenizer/index.html)
Tokenizer is exactly what I'm looking for, thanks. I looked at boost::spirit and I would agree, its far too much for what I need.

---

### Post by bunker on 2007-09-23
> **aks44 said:**
> [boost::spirit]("http://spirit.sourceforge.net/") is a good parser for such tasks IMHO.

Thanks for that link - it's exactly what *I* was looking for!  [Aside:] Good grief I'm sitting here getting confused by pointer ownership in a lock-file abstraction and there are ways of representing a full BNF entirely with c++'s operators.  I clearly have some things to learn ;).

---

