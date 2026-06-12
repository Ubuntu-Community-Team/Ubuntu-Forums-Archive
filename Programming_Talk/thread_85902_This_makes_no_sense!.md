---
title: "This makes no sense!"
date: 2005-11-03
forum: Programming Talk
---

### Post by rock freak on 2005-11-03
> if(m=='y'){
         i=0;
}
else{
         i=1;
}

gives me this error on compiling
warning: comparision between pointer and interger

But i cant see why!! its doing my head in

---

### Post by tehwa on 2005-11-03
which language?

---

### Post by rock freak on 2005-11-03
Dont worry all sorted just tooka  quick break from it.  went back to it and saw it straight away!

---

### Post by rock freak on 2005-11-03
the rand function in C is totally usless for getting random numbers. and the srand is great

anyone know how to make totally or near to it random number generator? this is the code im using at the mo
> 
srand((unsigned)time(NULL));
random=rand()%10


---

### Post by ltmon on 2005-11-03
All (well all standard) computerised random-number generators are really just psuedo-random.  It's just a mathematical function that produces numbers in a sequence.

srand helps because it has a seed (in your case you are using the time) which will cause it to be different every time.  rand doesn't have a seed, so the sequence of "random" numbers will be identical every time you run your program.

You may have seen some programs that make you move the mouse around the screen while it generates the number.... this is because it is using your mouse movements as the seed.

Other (high level) generators use static electricity or electron states as seeds, but that is beyond what a PC can do without special hardware :)

Unless you are going for some military-grade cryptography, using the current time as a seed should be fine.

L.

---

