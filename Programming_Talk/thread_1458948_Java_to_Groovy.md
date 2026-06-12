---
title: "Java to Groovy"
date: 2010-04-20
forum: Programming Talk
---

### Post by Ravenshade on 2010-04-20
Haskell == useless();

That's all I have to say on Haskell. (I don't get it, it doesn't gel well with me in my current mind state...I'll get back to it later. 

On the other hand, I have Groovy, now, since I managed to get groovy to install on Ubuntu, I've been overjoyed with the possibilities. A mere scripting language appears to have all of the advantages of Haskell and Java without either of the disadvantages. (That being said, I've only been in Groovy for five minutes, and I know for sure I'll disprove that last statement). 

Now the code below, with tweaking, works in Java. 

The output is 2, 3, 17, 45.. repeated indefinitely which is somewhat ticking me off.  No idea why 

Could someone highlight the line causing the problem? 

problem 1: It's putting them order...nice but I need the numbers in the original order. 
problem 2: Repeating indefinitely. No end. 
problem 3: What about the rest of the none dupes? :confused:

Sorry for the trouble. 

```
//Code to strip dupes from a list. 

numeral = [17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12]
finalNum = [] //empty destination!

numDuplicated = 0

for(i=0; i<numeral.size; i++) {
    hasBeenCopied = false
    for(j=0; j<numDuplicated; j++) {
        if(numeral[i] == finalNum[j]){
            hasBeenCopied = true
            break
        }
    }
    
    if(!hasBeenCopied) {
        finalNum[numDuplicated++] = numeral[i]
    }
    i = 0 //reset i!
    
    for (i=0; i<numDuplicated; i++) {
        println finalNum[i]
    }
}
```

---

### Post by CptPicard on 2010-04-20
Just some commentary, too tired to read code...

> **Ravenshade said:**
> Haskell == useless();

That's all I have to say on Haskell. (I don't get it, it doesn't gel well with me in my current mind state...I'll get back to it later.

It's a different mindset, that's why learning a functional language at some point is important. 

The "geling" with mind effect is real mind you... [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)  see what he says about "Blub".
 
> I've been overjoyed with the possibilities. A **mere** scripting language

There is nothing "mere" about them. Programming is not just about  static types and pointers.

---

### Post by Ravenshade on 2010-04-20
The gel effect is real O_O omfg. 

If I knew what static types and pointers were, I'd more than likely agree with you ^_^; 

Thanks.

---

### Post by CptPicard on 2010-04-20
> **Ravenshade said:**
> 
If I knew what static types and pointers were,

Typical stuff scripting languages do not incorporate in their design, which then is made a lot of noise about by those who do not believe that scripting languages are "real" programming languages... :)

---

### Post by Ravenshade on 2010-04-20
I see...

update on the code situation. After running a test or three I think I've found the code that causing the problem. 

The first if statement. Apparently, groovy doesn't like 'numeral[i]' or it doesn't like 'finalNum[j]' or both, not sure on that score. 

It keeps throwing an out of bounds error.

---

### Post by Ravenshade on 2010-04-20
Code semi working... but I have an issue with arrays. Major problems solved. New thread time. 

Working Code (partially)
```


//testFile

int[] a1 = [15, 3, 2, 15, 2, 1]
int[] b1 = [0, 0, 0, 0, 0, 0] //Cowboy builders at work here!



i=1
j=1
hasBeenCopied = false
int duped = 0
 

for (i in 0..<a1.size()) {
   println "Test1"
        
        hasBeenCopied = 0
        
        for (j in 0..< duped) {
            println "test2"
            
            if (a1[i] in b1[j]) {
                println "test3"
                hasBeenCopied = true
                break
            }
           
        }
        
        if (hasBeenCopied== true) { //Apparently Groovy counts spaces as part as the variable name. O.o
            println "test4"
        } else {
            println "test5"
           
            b1[duped++] = a1[i]
        }
        
       

      
}
i=0
for (i in 0..< duped) {
          println b1[i]
       }
```

---

