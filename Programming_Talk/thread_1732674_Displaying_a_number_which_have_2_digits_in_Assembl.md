---
title: "Displaying a number which have 2 digits in Assembly"
date: 2011-04-18
forum: Programming Talk
---

### Post by quartaela on 2011-04-18
hi there i am working on a project with assembly programming and i am facing with a problem about displaying a number which have 2 digits. the main problem is if i have one digit number i can display but if i have 2 digit number the program displays the first digit. here is an example code which is in a subroutine. i used ASRA, LSRA and RORA but i can't fixed this problem.

```
DISPA:
	JSR CLEARD
	
	LDAA 20H
	JSR PATCON
	LDAB #40H
	JSR DISPAT
	
	LDAA 20H
	CMPA #0FH
	BLT DISPALEVEL1
	ASRA
	LDAB #80H
	JSR DISPAT
	
DISPALEVEL1:
```

and the second problem is BLT code isn't working correctly. assume that in 20H there is a number bigger than 0FH, so it must be a 2 digit number. and if it is less than 0FH it must branch to DISPALEVEL1 but it executes the code above BLT if i replace BGT when the number is bigger than 0FH. 

so how can i fix this problem_?. and thanks for your help anyway. : )

---

### Post by layers on 2011-04-19
Which processor is this for? I think one cannot say "Assembly", like one can say "C", because it's not generally universal. i.e. I am familiar with NIOS II assembly, and some of your commands I have never seen before.
But I think the "flavor" of assembly might help us understand what the code does.

---

### Post by quartaela on 2011-04-24
upps i forgot this thread. anyway i solved the problem : ). Layers we are using motorola 6800 emulator for programming assembly language. and sorry for late answer :)

---

### Post by layers on 2011-04-24
> **quartaela said:**
> upps i forgot this thread. anyway i solved the problem : ). Layers we are using motorola 6800 emulator for programming assembly language. and sorry for late answer :)
No problem. I suspected it, but wanted to be sure.
Can this thread be marked as solved?

---

### Post by quartaela on 2011-04-24
yes i solved the problem : )

---

### Post by cgroza on 2011-04-24
Wait, are'nt you going to tell us how? Someone in the same situation like you may find it useful.

---

