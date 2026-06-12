---
title: "noob c++ compilation error"
date: 2010-03-20
forum: Programming Talk
---

### Post by WillFerrellLuva on 2010-03-20
to make a long story shorter, I have been out of programming for a while and decided to start up again.  This is also my 1st time programming in Linux.  I am using gedit and terminal to compile my programs with g++.

I'm trying to do something a little bit more complicated but when i try to do the following:

```

double answer = 0;

	for(int i=1; i<=x; i++)
	{
		answer += (16/i) * (4/8i); //error on this line
		...
	}

```

I get an error from the compiler:
cannot convert &#8216;double __complex__&#8217; to &#8216;double&#8217; in assignment

Not sure whats going on here.  Any help will be greatly appreciated.

---

### Post by SledgeHammer_999 on 2010-03-20
What is **8i** in **(4/8i)** supposed to mean?

---

### Post by WillFerrellLuva on 2010-03-20
4 divided by (8 times i)

---

### Post by Slim Moe on 2010-03-20
```
answer += (16 / i) * (4 / (8 * i)); // no errors in this line

```

---

### Post by WillFerrellLuva on 2010-03-20
tyvm for your time, that was indeed my problem.  Time to brush up on my syntax :-)


/sheepishly goes back to his corner

---

