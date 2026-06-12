---
title: "very strange c++ problem (gcc bug?)"
date: 2007-02-23
forum: Programming Talk
---

### Post by dbd on 2007-02-23
Hey, I have an very strange bug with my C++ program.  I've managed to reproduce it in a simplified version of whats happening so here is that code:
```
int main()
{
	double num=0;
	while(num<12) {
		num += 0.2;
		cout << "num=" << num << ", (num*10)%10=" << (((int)(num*10))%10) << endl;
	}
	return 0;
}
```
For some values of num this works as expected, however for other values the (((int)(num*10))%10) gives the result as if num were 0.1 less than it should be! Here is the output the program gives:
> num=0.2, (num*10)%10=2
num=0.4, (num*10)%10=4
num=0.6, (num*10)%10=6
num=0.8, (num*10)%10=8
num=1, (num*10)%10=0
num=1.2, (num*10)%10=1
num=1.4, (num*10)%10=3
num=1.6, (num*10)%10=5
num=1.8, (num*10)%10=7
num=2, (num*10)%10=9
num=2.2, (num*10)%10=1
num=2.4, (num*10)%10=3
num=2.6, (num*10)%10=6
num=2.8, (num*10)%10=8
num=3, (num*10)%10=0
num=3.2, (num*10)%10=2
num=3.4, (num*10)%10=4
num=3.6, (num*10)%10=6
num=3.8, (num*10)%10=8
num=4, (num*10)%10=0
num=4.2, (num*10)%10=2
num=4.4, (num*10)%10=4
num=4.6, (num*10)%10=6
num=4.8, (num*10)%10=8
num=5, (num*10)%10=0
num=5.2, (num*10)%10=2
num=5.4, (num*10)%10=4
num=5.6, (num*10)%10=6
num=5.8, (num*10)%10=8
num=6, (num*10)%10=0
num=6.2, (num*10)%10=2
num=6.4, (num*10)%10=4
num=6.6, (num*10)%10=6
num=6.8, (num*10)%10=8
num=7, (num*10)%10=0
num=7.2, (num*10)%10=2
num=7.4, (num*10)%10=4
num=7.6, (num*10)%10=6
num=7.8, (num*10)%10=8
num=8, (num*10)%10=0
num=8.2, (num*10)%10=2
num=8.4, (num*10)%10=4
num=8.6, (num*10)%10=6
num=8.8, (num*10)%10=8
num=9, (num*10)%10=0
num=9.2, (num*10)%10=1
num=9.4, (num*10)%10=3
num=9.6, (num*10)%10=5
num=9.8, (num*10)%10=7
num=10, (num*10)%10=9
num=10.2, (num*10)%10=1
num=10.4, (num*10)%10=3
num=10.6, (num*10)%10=5
num=10.8, (num*10)%10=7
num=11, (num*10)%10=9
num=11.2, (num*10)%10=1
num=11.4, (num*10)%10=3
num=11.6, (num*10)%10=5
num=11.8, (num*10)%10=7
num=12, (num*10)%10=9
num=12.2, (num*10)%10=1

Anyone got a clue what is going on? I'm totally stumped!
(BTW, I'm running Edgy Eft and compiling with gcc-4.1)

---

### Post by GeneralZod on 2007-02-23
Floating point arithmetic is inherently inaccurate.  It's quite likely that e.g. 12.2 * 10 is being calculated as

121.999999999999

in which case 

(int)(num * 10) will be 121.  Either add .5 before converting to an int (so that the number is rounded to the nearest int) or, (even better, in your particular case), use ints instead (e.g. use 122 instead of 12.2 internally, and give the "correct" answer when you are printing the results out).

---

### Post by dbd on 2007-02-23
thanks, gonna use ints instead, problem solved :)

---

