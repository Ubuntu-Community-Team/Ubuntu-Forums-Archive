---
title: "[SOLVED] Vector String array"
date: 2008-04-21
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-21
C++: I have a vector array of strings (std::vector<std::string> text), and I was wondering how exactly I would access things in them? Would I just use text[][]... the first one being in the vector and the second one being in the string? I thought I should ask because I don't want to make an assumption and then be confused by errors later on.

---

### Post by Zugzwang on 2008-04-21
Right. Taking "text[i]" is actually a function call returning a reference to the string object, which in turn you can access using the overloaded [] operator again. So in fact "text[numberofstringinlist][characterofthestring]" accesses the characterofthestring'th character of the numberofstringinlist'th string in the vector.

BTW, please don't forget to include a hint that you're dealing with C++ in the caption next time. :)

---

### Post by Zeotronic on 2008-04-21
> BTW, please don't forget to include a hint that you're dealing with C++ in the caption next time. 
:( But my opening line started with "C++:", and I don't know about you I suppose, but I can see part of the opening statement of a thread when I put my cursor over it. (which is why I always start my programming threads with a list of things of major relevance)

Anyways, thank you.

---

