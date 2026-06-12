---
title: "How to read through the same file twice with an fstream in C++?"
date: 2009-01-17
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-17
I am trying to use an ifstream to get data out of a file, and I read through once to check how much data there is to get, and then assign the right amount of memory to store it.  The problem is that I can't get to the beginning of the file after reading through the first time.  I have tried declaring and opening a new ifstream, seekg(ios_base::beg), and several other things, but most are ineffectual and with ios_base I get a message saying ios_base has not been declared.  How to fix this?

---

### Post by loganwm on 2009-01-17
> **Zorgoth said:**
> I am trying to use an ifstream to get data out of a file, and I read through once to check how much data there is to get, and then assign the right amount of memory to store it.  The problem is that I can't get to the beginning of the file after reading through the first time.  I have tried declaring and opening a new ifstream, seekg(ios_base::beg), and several other things, but most are ineffectual and with ios_base I get a message saying ios_base has not been declared.  How to fix this?

I haven't messed with C++ much, but look into fseek to set the current  position. I believe it should be quite easy.

Much Luck!

Edit:

fseek(yourstream, offset from reference, reference point)

fseek(stream,0,SEEK_SET)

The second one should do the trick.

rewind probably works as well, but fseek is preferable.

---

### Post by Zorgoth on 2009-01-17
Fixed it, a combination of not using an std:: and forgetting to store a size.  Thanks!

---

### Post by JupiterV2 on 2009-01-17
Please mark as solved.

---

