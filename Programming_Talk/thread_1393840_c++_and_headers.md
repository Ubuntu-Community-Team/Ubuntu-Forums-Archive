---
title: "c++ and headers"
date: 2010-01-29
forum: Programming Talk
---

### Post by savagetwinky on 2010-01-29
Ok i know this information should be easily available, but, i'm having issues finding it, if someone can help it would be greatly appreciated. I'm having a really hard time understanding the header files trying to do what i want to do so i'll just give a brief example.
 
I have my main.cpp, a.cpp, b.cpp, c.pp, project.h, I want to make a class that use functions a, b, c, and a data structure. How do i put that all into 1 header.
 
I'm using seperate files due to needing them to be able to interact with each other, a write something, b will read it, and c will do something based off of what b reads. They both read and write to the data structure.
 
so my main will look something like this, 
 
main{
     setups and other garbage
     a(my data struct) //or preferably something that doesn't need to be passed
     result = b(my data struct)
     if (result)
       c()
     else cry alot
}
 
i want to keep a, b, c seperate because me and some other people will be working on each of those individually, I KNOW c++ is able to do this, or something similar if i'm doing it wrong, but i can't seem to find it. It doesn't have to be a class, but it seems like it would be a good place to use the constructor to do my setting up since when i call this i need hardware to be started and then a gathers data from the hardware and writes it to my struct.

---

### Post by Simon17 on 2010-01-29
Can I ask why you want everything in a single header?
Typically, you would have a .h file for a corresponding .cpp file (excluding main.cpp and templates).

---

### Post by savagetwinky on 2010-01-29
will 1 data type pas easily between them? in otherwords i'm only going to be workign with sending a pointer through to a, then i want b to use that pointer to make a decision, it can call c or return a result and call c. 
 
Right now we have it returning a result and then starting or reseting a timer, if the timer reaches a certain time because b returned a false a bunch of times it calls c. I'd like to keep a, b, seperate from main, and c because they are being build ontop of our actual project. C will actually interface with some custom hardware that my friend is handling, so for now, its basicaly, void c() return 0 //win

---

### Post by Simon17 on 2010-01-29
Yes, you would be able to do that.

I want to advise you not to use a timer though because you cannot predict how long it will take for your code to run. The time it takes to run greatly depends on the machine, other processes, free resources and the will of the operating system. I assure you there is a much better way to do it. You can post parts of your code here and ask for help designing something that works.

---

### Post by savagetwinky on 2010-01-29
the timer is going to be necessary unfortunally, its a senior project, hardware sends data in and we need to be able to respond with a hardware alarm thats custom made, within 5 secs or so, probably less, so b, our analysis, we need to keep track of how long it starts failing and respond as quickly as possible. And alot of this project is writing code that can do that, and we'll have to port it to a micro itx board(via c3 woohoo) so we are basicly screwed but we'll get to that when we get to that.
 
so i can make multiple header files,  and still have them all talk to each other,

---

### Post by Simon17 on 2010-01-29
Of course you can.

---

### Post by savagetwinky on 2010-01-29
> **Simon17 said:**
> Of course you can.
 could you point me in the right direction, i'm having a hard time of finding a good example of multple files with headers and how to tie them in together

---

### Post by Simon17 on 2010-01-29
Search for "multiple source files in C++" or something like that.

If you showed part of your code, I could give you more specific advise.

---

### Post by savagetwinky on 2010-01-29
ah, that did help, i think i wasn't getting the wording right, but as soon as i typed that in i found one that was making 1 header, 1 class, and using multiple c files for, i didn't think source files, just fucntions and got garbage.

---

### Post by savagetwinky on 2010-01-29
where would i use a header if my class uses another module based plugin,

---

### Post by Simon17 on 2010-01-29
Can you be more specific or give me a small example? Without that, the best I can tell you is "wherever it's required".

---

