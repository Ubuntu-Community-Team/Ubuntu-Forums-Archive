---
title: "random pieces of number"
date: 2010-08-10
forum: Programming Talk
---

### Post by learnbash on 2010-08-10
Hello folks,

i have number for example 10 and i want to divide into 4 random pieces  that may be (6+2+1+1). How can i do this via script i have random number  234951 and i want to divide into 31 pieces. 		   		  		  		  		  		  		 			 			 				[IMG]http://fedora.unix.com/images/misc/progress.gif[/IMG] 

[]("http://www.unix.com/editpost.php?do=editpost&p=302443835")

---

### Post by Bachstelze on 2010-08-10
Sounds like homework, but it is very vague. What exactly does "random" mean here?

---

### Post by learnbash on 2010-08-10
> **Bachstelze said:**
> Sounds like homework, but it is very vague. What exactly does "random" mean here?

Dear sir, as earlier i say 10 we can divide it [6+2+1+1] or [5+2+1+2] or any combination so it could be any random number that makes 10 after breaking into 4 pieces. Same need to do for this number 234951.

---

### Post by dwhitney67 on 2010-08-10
learnbash - Why do you need this script?

Learning how to develop software is one thing; asking for a solution to a specific problem seems to imply that you are asking for someone on this forum to do your school work... and that is against the forum policies.

---

### Post by learnbash on 2010-08-10
> **dwhitney67 said:**
> learnbash - Why do you need this script?

Learning how to develop software is one thing; asking for a solution to a specific problem seems to imply that you are asking for someone on this forum to do your school work... and that is against the forum policies.

dear i am asking for idea, can you help.

---

### Post by dwhitney67 on 2010-08-10
> **learnbash said:**
> dear i am asking for idea, can you help.

No, other than to suggest that you attempt to solve the problem on your own.  If during the course of your endeavor you encounter any problems, then please ask again for help.  But you better be prepared to show your work.

---

### Post by Bachstelze on 2010-08-10
> **learnbash said:**
> dear sir, as earlier i say 10 we can divide it [6+2+1+1] or [5+2+1+2] or any combination so it could be any random number that makes 10 after breaking into 4 pieces. Same need to do for this number 234951.

1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+234921

---

### Post by learnbash on 2010-08-10
> **Bachstelze said:**
> 1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+234921


Hahaha, its not shell script, may be you suggest some logic so i can proceed.

---

### Post by Bachstelze on 2010-08-10
> **learnbash said:**
> Hahaha, its not shell script, may be you suggest some logic so i can proceed.

Find the maximum value for the first number, choose one value between 1 and that maximum value, repeat for all other numbers.

---

### Post by learnbash on 2010-08-10
> **Bachstelze said:**
> Find the maximum value for the first number, choose one value between 1 and that maximum value, repeat for all other numbers.

bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
234951/31
7579

Dear sir it give 7579, so i need to fill 7579 in all remaining 30 field, is it possible i can get random values other than this 7579 30 times to accomplish 234951

---

### Post by Bachstelze on 2010-08-10
I don't think you can generate random numbers directly in Bash. You can use Python:

```
python -c "import random; print random.randint(1, n)"
```

will give you a random number between 1 and n (inclusive).

---

### Post by DanielWaterworth on 2010-08-10
It really depends on what you mean by random. Different algorithms will give different distributions and without knowing what you are using it for it is difficult to say of an approach "This will give the best results".

Although the algorithm outlined by varies people above would be the simplest to implement, that of recursively choosing an integer between 1 and the remaining space left. It is a skewed distribution, ie, the first numbers are bigger in general.

Another approach is to generate a number between 1 and the size. This is the amount of numbers you will generate. Set all of the numbers to one, then randomly increment them until the sum is equal to size. This will generate a distribution that is not skewed.

---

