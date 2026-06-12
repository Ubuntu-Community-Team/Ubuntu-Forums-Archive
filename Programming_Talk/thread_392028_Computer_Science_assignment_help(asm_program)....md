---
title: "Computer Science assignment help(asm program)..."
date: 2007-03-24
forum: Programming Talk
---

### Post by nite owl on 2007-03-24
Hi im currently a comp science student and I have posted here before about the made-up language we have been given in our classes instead of using a real-world assembly language and the total lack of references for it. Anyway it has come that time for my first assignment and I have only gotten so far, and now I am stuck. The object of the assignment is to create a program that calculates the hamming distance between two one byte codewords. I have gotten as far as displaying the two codewords in there CHAR form and I am trying to create a module now called 'hamming' to operate on those two words and calculate the hamming distance between the two and display it. Here is what I have so far:

```
load R1, codeWord1 ;load the contents of codeWord1 into register 1
load R3, codeWord2 ;load the contents of codeWord2 into register 3
load R2, 1 ;string increment
load R0, 0 ;string terminator

firstString: load RF, [R1] ;load the contents of R1 and display it
        addi R1, R1, R2 ;increment R1 by R2
        jmpEQ RF=R0, nextChar ;if RF=R0 then jump to nextChar
        jmp firstString ;otherwise jump back to firstString    

codeWord1: db 01011011b, 0
codeWord2: db 01000111b, 0



nextChar: load RF, [R3] ;load the contents of R3 and display it
        addi R3, R3, R2 ;increment R3 by R2
        jmpEQ RF=R0, Hamming ;if RF=R0 then jump to Hamming
        jmp nextChar ;otherwise jump back to nextChar    

Hamming:xor R5, R1, R3 ;XOR the content of R1 and R3
    load RF, [R5]
    jmp end
end: halt

```
.....I am totally lost on how to XOR codeWord1 and CodeWord2 and to find the hamming distance and display it. I thought I could do it myself, but due to there being no tuts on it I am completley lost and panicked because its due in 2 days lol. If needed the less the adequate references to the language made by the creator can be found here [http://www.anne-gert.nl/projects/simpsim/](http://www.anne-gert.nl/projects/simpsim/)  Thankyou in advance guys :)

---

### Post by rickardg on 2007-03-24
Well, I'm no assembly expert, but doesn't the stuff at Hamming: XOR the codewords (and put the result in R5?) Now, you only have to interpret this bitpattern as a Hamming distance and display it.

---

### Post by rplantz on 2007-03-24
From a quick look at the brief description of this assembly-like language, I think you need to do something like:
```

     load    R1, codeWord1   ; load the values into
     load    R3, codeWord2   ;      the registers
     xor     R5, R1, R3      ; xor them, with result in R5

```
I programmed in assembly language (in industry) for ten years, then taught it for another 25. I hate these books that use fake assembly languages. You will probably never program in assembly language when you get out of school, but you may wish to read it a little. Might as well learn a real assembly language.

I'm writing the final chapter (on I/O devices) for my book on assembly language. The entire book is based on linux. I use the gnu assembler. Almost all my examples start with the C solution, then show the assembly language "under the hood." Hopefully, I can start publishing the book through lulu this summer.

---

### Post by rickardg on 2007-03-24
You mean like here? :-)

> **nite owl said:**
> 
```

Hamming:xor R5, R1, R3 ;XOR the content of R1 and R3
    load RF, [R5]
    jmp end
end: halt

```
.....I am totally lost on how to XOR codeWord1 and CodeWord2 and to find the hamming distance and display it. 

Now all that remains is to count the differences. ;-)

---

### Post by nite owl on 2007-03-24
hi thanks so much for all your replies guys. Would anyone be able to write or explain the code i would need to write next in regards to counting the differences from the xor operation and then displaying it???? Thanks :)

---

### Post by rickardg on 2007-03-25
Right, I'm not going to do your homework for you but here are a few hints.

XOR sets the bits where the two input values are different, eg 
```

0011
0110
-------
0101

```

That is, the number of set bits in the result is the Hamming distance, count them and you're done. This is in fact a common job interview question so there are a lot of solutions on the web (probably not in SimpSim though).

---

