---
title: "g++ to upper case"
date: 2006-11-14
forum: Programming Talk
---

### Post by rvickers on 2006-11-14
How do you convert a string to upper case using g++?
Thanks

---

### Post by ansi on 2006-11-14
If you mean C++'s std::string, then try to read [here]("http://www.devx.com/getHelpOn/Article/9702/1954?pf=true")

---

### Post by rvickers on 2006-11-14
My problem is I can't find toupper in g++, I know it exist in b++...
Thanks

---

### Post by DavidBell on 2006-11-14
If you mean with char* it's strupr()

If you mean with std::string I don't think it has an upper function, you have to write your own.

DB

---

### Post by rvickers on 2006-11-14
"If you mean with std::string I don't think it has an upper function, you have to write your own."

That's what I was curious about. Writing one's no biggie since strupr() is not ansi standard.
Thanks :)

---

