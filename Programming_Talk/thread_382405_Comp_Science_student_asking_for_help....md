---
title: "Comp Science student asking for help..."
date: 2007-03-12
forum: Programming Talk
---

### Post by nite owl on 2007-03-12
Hi everyone, I apologise in advance for this off topic post, however I have searched for a couple of days now and have come up with no answers, and this community has always been good to me for answers.

I'm into my third week of my computer science course and for one of my subjects we have started coding in assembly language. However what we are using seems to be foreign to all the tutorials on the internet, even my lecturer dosent seem to have it fully grasped, why he would choose this is beyond me(if it helps we are using a compiler called SimpSim)???... here's a sample piece of the code:
```


    
        load    R2,0
         jmp     Print       ;Print number in R2

         org     60h
Print:
; Put the number in R2 in the output window
; Changed registers: R0, RA, RB, RC, RE, RF
         load    R0,39h      ;ASCII-code of '9'
         load    RA,30h      ;ASCII-code of '0'
         load    RB,7        ;'A'-'0'+10  (correction from numbers to letters)
         ; determine high nibble
         load    RC,0F0h     ;filter high nibble
         and     RE,R2,RC    ;high nibble of R2 in RE
         ror     RE,4        ;shift to low nibble
         addi    RE,RE,RA    ;make it ASCII
         jmpLE   RE<=R0,isNum1    ;is an ASCII number
         addi    RE,RE,RB         ;correct to ASCII letter
isNum1:  store   RE,[HiNibble]    ;put high nibble on its place
         ; determine low nibble
         load    RC,0Fh      ;filter low nibble
         and     RE,R2,RC    ;low nibble of R2 in RE
         addi    RE,RE,RA    ;make it ASCII
         jmpLE   RE<=R0,isNum2    ;is an ASCII number
         addi    RE,RE,RB         ;correct to ASCII letter


```


.........I mostly am seeking help in understanding what these different registers mean i.e RC, RB etc. I only found out in passing that the RF register means just to display to standard output('cout <<' in c++ terms). Anyway Im completley lost, including my fellow students in my classes. Any help at all would be greatly appreciated!!! thankyou


B.T.W this piece of code is incomplete and writing after the ';' symbols are comments

---

### Post by Najand on 2007-03-12
This is not an Assembly Language Forum. I think it is completely unrelated to Ubuntu. Please check web for your appreciated forum.

---

### Post by Sef on 2007-03-12
Moving to Programming Talk.

---

### Post by Najand on 2007-03-12
Thanks Sef

---

### Post by WW on 2007-03-12
nite owl,

There are probably some folks here who would be happy to help you.  Just a suggestion: When you include source code in a forum post, enclosed it in [ code ] and [ /code ] tags. This will put the code in a box, and preserve the indentation. When you edit your post, do this:

[ code ]
... your code here ...
[ /code ]

but do not include the spaces inside the square brackets--I included those so the tags would *not* be processed by the forum software.

---

### Post by nite owl on 2007-03-12
Thanks for the suggestion WW

---

### Post by slimdog360 on 2007-03-12
that code would be unique to the computer architecture, now if you were asking about the intel c8051 microcontroller series I could be of some help. But since you look desperate I could guess as to what they refer to. I would assume that RB would just be another name for Register2, similarly for RC and Register3 etc. these are placed right at the start of the memory. But I couldn't be to sure. Some registers are linked to 
various things, such as your RF register, on the next clock tick that code will get passed to the screen via the processor. These things you just have to know.

If you haven't already seen one it may be useful to ask for a 'memory map' of the system, which can let you visually grasp at what is going on.

hmm, I just read your post once again, you do actually know what a register is right? In case you dont, its place in memory. You can refer to the registers by hexadecimal numbers or what is better by means of a name, such as 'R1' for register one, or it may be 'A' for the accumulator. 


Anyway, Id go out and get a text book if the lecturer is useless, maybe even try to get an ex-student of the course to give you a hand.

---

### Post by supirman on 2007-03-12
[http://ocw.mit.edu/NR/rdonlyres/Aeronautics-and-Astronautics/16-01Fall-2005-Spring-2006/828F67C6-85C6-42C6-AEF2-8CF28E541558/0/2.pdf](http://ocw.mit.edu/NR/rdonlyres/Aeronautics-and-Astronautics/16-01Fall-2005-Spring-2006/828F67C6-85C6-42C6-AEF2-8CF28E541558/0/2.pdf)

[http://www.augustana.ab.ca/~mohrj/courses/2004.fall/csc110/assignments/simpsim_summary.html](http://www.augustana.ab.ca/~mohrj/courses/2004.fall/csc110/assignments/simpsim_summary.html)

google is your friend.

---

### Post by nite owl on 2007-03-12
Thankyou Supirman and Slimdog360 I owe you both one..I hope I can return the favour one day

---

### Post by Hendrixski on 2007-03-12
I remember absolutely nothing of my assembly programming classes from college.  I mean, it probably helped me become a better programmer, but...  I'm sure there's a better way to get that value.

There are a few different architectures out there, each with a different assembly language that goes with it.  I did mine on Solaris Unix machines, and my room-mate had taken an assembly language class the semester before on a different architecture, and couldn't help me one bit.

Just hang in there, once you're done the pain goes away and you'll never look at assembly again.  Ever.

---

### Post by supirman on 2007-03-12
> **Hendrixski said:**
> ... Just hang in there, once you're done the pain goes away and you'll never look at assembly again.  Ever.

I work as an embedded systems engineer and I get to play with assembly every time we have a new hardware platform that needs a bootloader.  I enjoy assembly though, so perhaps I'm a bit odd.

---

