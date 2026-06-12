---
title: "C++ Private member variable and references to it"
date: 2012-04-24
forum: Programming Talk
---

### Post by akvino on 2012-04-24
Recently I had an interesting question asked, and since I couldn't think of all possible answers, I thought of asking the question here.

If the class member is private, what are the possible ways of misuse of the private member, which would allow you to modify the private member without accessor function?

---

### Post by Tony Flury on 2012-04-24
you could in theory work out the offset of the private member from the start address of the instance - and use direct memory access to modify the value.

Also don't classes have access to private members of their friends - so you could use another object as a proxy ?

I am not a C++ expert but they are the two I thought of.

---

### Post by ofnuts on 2012-04-24
> **akvino said:**
> Recently I had an interesting question asked, and since I couldn't think of all possible answers, I thought of asking the question here.

If the class member is private, what are the possible ways of misuse of the private member, which would allow you to modify the private member without accessor function?
If you distribute a class library, and provide a header file that describes the members including the private ones, then someone can make its own copy, change the private members to public, and compile his code with that to gain access to them. You can however distribute "equivalent" header files (with obfuscated names for the private members, or all data members kept together and replaced by a suitably sized array and all non virtual private methods removed) which would make this technique unusable.

---

