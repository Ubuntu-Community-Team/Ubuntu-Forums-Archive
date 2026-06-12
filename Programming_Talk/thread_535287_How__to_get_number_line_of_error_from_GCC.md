---
title: "How  to get number line of error from GCC ?"
date: 2007-08-26
forum: Programming Talk
---

### Post by engineerball on 2007-08-26
How i can get number line of error from GCC ?
If I compile my program and have more errors. How can i got its.
Ex.
after I compile source code and it have errors.

```
read_str.cpp:5: error: &#8216;string&#8217; was not declared in this scope
read_str.cpp:6: error: variable or field &#8216;Convert2D&#8217; declared void
read_str.cpp:6: error: &#8216;string&#8217; was not declared in this scope
read_str.cpp:7: error: &#8216;string&#8217; has not been declared
read_str.cpp: In function &#8216;int main(int, char**)&#8217;:
read_str.cpp:25: error: &#8216;CountLine&#8217; cannot be used as a function
read_str.cpp:26: error: &#8216;cout&#8217; was not declared in this scope
read_str.cpp:26: error: &#8216;endl&#8217; was not declared in this scope
read_str.cpp:29: error: cannot convert &#8216;std::string&#8217; to &#8216;int&#8217; for argument &#8216;2&#8217; to &#8216;void FindLastLine(int*, int)&#8217;
read_str.cpp:36: warning: comparison between signed and unsigned integer expressions
```

I want 6, 7, 25, 26, 29, 36. 

Can it get number from GCC direct ?

Sorry I'm very poor in English.
Thank you.

---

### Post by CptPicard on 2007-08-26
Sorry, but I don't understand your question... aren't you already getting the line numbers of compilation errors from gcc's output as demonstrated?

---

### Post by Lux Perpetua on 2007-08-26
Do I understand correctly that you want a program to parse the GCC error output and simply display the line numbers? 

This may get you started: ```
g++ yourfile.cpp 2>&1 1>/dev/null | sed --quiet 's/\(.*:\)\([0-9]*\)\(:.*\)/\2/p'
```More on sed: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

