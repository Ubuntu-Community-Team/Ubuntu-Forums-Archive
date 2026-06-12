---
title: "Where are the header files in 11.10?"
date: 2011-10-07
forum: Programming Talk
---

### Post by bikewrecker on 2011-10-07
Hi everybody. Sorry if this was already posted, but I looked around for the answer and couldn't find it. 
I'm relatively new to ubuntu and programming in C, and I'm looking at someone elses code for an internship I'm working on. I dont understand the "geometry.h" header file and I was wondering where I should look to see the source code. 

Thanks a bunch!

---

### Post by karlson on 2011-10-07
> **bikewrecker said:**
> Hi everybody. Sorry if this was already posted, but I looked around for the answer and couldn't find it. 
I'm relatively new to ubuntu and programming in C, and I'm looking at someone elses code for an internship I'm working on. I dont understand the "geometry.h" header file and I was wondering where I should look to see the source code. 

Thanks a bunch!

```

sudo updatedb
locate geometry.h

```

---

### Post by bikewrecker on 2011-10-07
Ok thanks. I typed that but nothing happened so I dont think I have it, but thats really good to know, thank you.
Know how to get header files? i tryed sudo apt-get install geometry.h but it didnt work :(... I'm such a noob.

---

### Post by karlson on 2011-10-07
> **bikewrecker said:**
> Ok thanks. I typed that but nothing happened so I dont think I have it, but thats really good to know, thank you.
Know how to get header files? i tryed sudo apt-get install geometry.h but it didnt work :(... I'm such a noob.

Header files are normally distributed with the development libraries or are a part of the software development project you are working on, so if it's standardized then locate should be able to pick it up.

If it's not then I'd search the source tree of your project.

---

### Post by Bachstelze on 2011-10-07
There's a lot of packages that provide a geometry.h header:

[http://packages.ubuntu.com/search?searchon=contents&keywords=geometry.h&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=geometry.h&mode=exactfilename&suite=natty&arch=any)

So if you know which of those you need, install it. If you don't, ask the person who wrote the code, or look in the documentation if there's any.

---

### Post by bikewrecker on 2011-10-07
Alright. Thanks guys. I think I've got it figured out now. I really appreciate your help!

---

