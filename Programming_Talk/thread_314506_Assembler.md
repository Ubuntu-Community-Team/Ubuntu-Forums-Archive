---
title: "Assembler"
date: 2006-12-07
forum: Programming Talk
---

### Post by rado_london on 2006-12-07
Hello People
I have to handle in my coursework tomorow but I am stuck on one of the questions. It is about assembler. Then program that we use is ASMTutor. I will atach it if it helps you to help me. It runs fine in WINE. Ok now here is the task:

```
Create a program that will do the following (all values are in hex)
a. Start the counter at 6
b. Reduce by 1.
c. Each time we reduce compare with 2.
d. If the counter is greater than or equal to 2, jump to a section of code which will add 2 to the AX register then return to steb "b."
e. If the counter is less than 2 go to another section of code which moves the value of the AX register to memory location
f. Move this value back into the AX register and multiply by 2
g. Move the result to a memory location
h. At the end of the whole procedure you should have the result in the memory location you specified.
```

As this looks a bit complicated the teacher gave us a sheet with easier to understand instructions. I have attached a picture of it.

Hope you can help me ASAP as this is due to tomorow.

Thanks in advance

---

### Post by mips on 2006-12-07
Is this 8088 assembly.

Does not look very complex but the last time i wrote anything in asm was over 10yrs ago so i'm gonna bow out. someone will be able to help you.

edit: oops i just saw it was tutor software so it is probably not 8088 but uses it's own registers and stuff. dont have wine either.

---

### Post by yabbadabbadont on 2006-12-07
Hey!  Shouldn't you be doing your *own* homework?!?   :D

---

### Post by Brunellus on 2006-12-07
> **yabbadabbadont said:**
> Hey!  Shouldn't you be doing your *own* homework?!?   :D
he's bazaaring it.

---

### Post by rado_london on 2006-12-07
> **yabbadabbadont said:**
> Hey!  Shouldn't you be doing your *own* homework?!?   :D

I should but my teacher is dickhead and he didn't explain any of it in class so I don't have any idea what to do:)

Help me please!

---

### Post by Brunellus on 2006-12-07
thread has been moved to more appropriate venue.  I'll let other participants to sort out the ethics of doing OP's homework for him.

---

### Post by rado_london on 2006-12-07
> **Brunellus said:**
> thread has been moved to more appropriate venue.  I'll let other participants to sort out the ethics of doing OP's homework for him.

Thanks for moving it away.

Now a bit about the ethics. I know it is generally unacceptable to this but in this case the teacher didn't explain a single thing. I asked him in person and he said:
"This is BTEC course. Find the answer yourself."

In my opinion this type of work must be explained. Dont you think the same?

---

### Post by yabbadabbadont on 2006-12-07
> **rado_london said:**
> Thanks for moving it away.

Now a bit about the ethics. I know it is generally unacceptable to this but in this case the teacher didn't explain a single thing. I asked him in person and he said:
"This is BTEC course. Find the answer yourself."

In my opinion this type of work must be explained. Dont you think the same?

I would assume that you are not learning assembler as your first programming language...  in which case, solve the problem in a language you know, then see if you can translate.  Not the best way to do it, but it is a good place to start.  Also, doesn't your course have a required textbook?  If so, *read it*.  If not, look for x86 assembler tutorials on the web.  There may even be tutorials on the web for the emulation software that you are using.  Finally, in the real world, bosses and clients rarely fully explain the requirements of a task.  You will have to learn sooner or later how to "Find the answer yourself."  ;)

---

### Post by rado_london on 2006-12-07
> **yabbadabbadont said:**
> I would assume that you are not learning assembler as your first programming language...  in which case, solve the problem in a language you know, then see if you can translate.  Not the best way to do it, but it is a good place to start.  Also, doesn't your course have a required textbook?  If so, *read it*.  If not, look for x86 assembler tutorials on the web.  There may even be tutorials on the web for the emulation software that you are using.  Finally, in the real world, bosses and clients rarely fully explain the requirements of a task.  You will have to learn sooner or later how to "Find the answer yourself."  ;)

OK thanks.
I found few things on the web. One thing I dont get is:
How to do if something is bigger from something then go to a place and if its not to go to other.

---

### Post by yabbadabbadont on 2006-12-07
> **rado_london said:**
> OK thanks.
I found few things on the web. One thing I dont get is:
How to do if something is bigger from something then go to a place and if its not to go to other.

How would you do that in any other programming language?

---

### Post by mips on 2006-12-07
> **rado_london said:**
> Thanks for moving it away.

Now a bit about the ethics. I know it is generally unacceptable to this but in this case the teacher didn't explain a single thing. I asked him in person and he said:
"This is BTEC course. Find the answer yourself."

In my opinion this type of work must be explained. Dont you think the same?

I dunno, I kind of agree with your lecturer, at that level you should be able to find the answer for yourself. What year are you in seeing it is a 4yr degree ?

Do you want to be spoon fed ?

---

### Post by mips on 2006-12-07
If you want a good reference book, although old, look at "IBM PC assembly language and programming" by Peter Abel, published by Prentice Hall.

It's not one of those thick monstrosities, is concise and to the point and would answer your question in a jiffy.

---

### Post by mips on 2006-12-07
I just found GNUSim8085 in the repos which looks pretty good, [http://gnusim8085.sourceforge.net/index.php/Main_Page](http://gnusim8085.sourceforge.net/index.php/Main_Page)

Gonna give it a bash.

Shite it uses diffrent registers in your example ??? Can't they just stick the defaults.

---

### Post by mips on 2006-12-07
> **rado_london said:**
> OK thanks.
I found few things on the web. One thing I dont get is:
How to do if something is bigger from something then go to a place and if its not to go to other.

CMP    R1,02    (Compare R1 to 02)
JAE    106        (Jump if above/equal)
JB      109        (Jump if below)

---

### Post by rado_london on 2006-12-07
> **mips said:**
> CMP    R1,02    (Compare R1 to 02)
JAE    106        (Jump if above/equal)
JB      109        (Jump if below)

Love you man. The moment u come to london give me a call and I will buy you a drink:)

EDIT: Done it on paper will type it on the computer and will post back.

---

### Post by rado_london on 2006-12-07
A bit of a problem. These two JAE and JB arent recognised by ASMTutor. Anyway I still owe you drink and I will do some more research of the equvelents of these instructions.

---

### Post by mips on 2006-12-07
Here is the entire code, you might have to define some addresses/values and ensure the correct sytax is used, hex etc.
[FONT=Arial][SIZE=2]
```

mov     R1,06    (Move the value 06 into R1)
sub      R1,01    (Subtract 01 from R1)
cmp     R1,02
jae       106     (Jump if above/equal)
jb         109     (Jump if below)

add      R3,02    (Add 02 to R3)
jmp      101

mov      115,R3    (Move contents of R3 to address 115)
mov      R3,115    (Move contents of address 115 to R3)
shl         R3,1    (Shift left 1, equvalent to multiply by 2 operation which is longer)
mov      116,R3    (Move contents of R3 to address 116)
```[/SIZE][/FONT]

---

### Post by mips on 2006-12-07
> **rado_london said:**
> A bit of a problem. These two JAE and JB arent recognised by ASMTutor. Anyway I still owe you drink and I will do some more research of the equvelents of these instructions.

Sorry, can't help there. Maybe introduce your lecturer to GNUSim which looks better than asmtutor.

Your R1, R2 etc will be your AX, CX registers etc. I assume.

---

### Post by rado_london on 2006-12-07
> **rado_london said:**
> A bit of a problem. These two JAE and JB arent recognised by ASMTutor. Anyway I still owe you drink and I will do some more research of the equvelents of these instructions.

You made me think people thank you very much!
The JAE=i is equvelent to BLE
adn JB is equivelent to BLT.

Thanks for the help

---

### Post by mips on 2006-12-07
> **rado_london said:**
> Love you man. The moment u come to london give me a call and I will buy you a drink:)


Lol, that might be sooner than later. Got a wedding in June I think which I have to attend.

---

### Post by rado_london on 2006-12-07
> **mips said:**
> Lol, that might be sooner than later. Got a wedding in June I think which I have to attend.

PM me when you are coming though. By June I will be 18 and wont have ptrouble getting into the pubs:)

---

