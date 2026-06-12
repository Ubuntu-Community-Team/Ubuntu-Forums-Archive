---
title: "Loop Forever Problem"
date: 2010-03-10
forum: Programming Talk
---

### Post by safarin on 2010-03-10
Hi, I'm doing PWM(Pulse Width Modulation) for each condition..
My idea is this program will refresh for every X seconds and enter inside the specific condition and do loop forever until the X seconds is finish.
and restart to take new data to execute new condition.

My problem now, I don't know how to quit from loop forever..
What is the interrupt or flag condition to jump from the loop forever to main line in X second..


```
	else if ((c[0] == 1)&&(c[1] == 0))
	{
		for(;;)
		{
		*PBDR = 0x40;
		usleep(20);
		*PBDR = 0x00;
		usleep(90000);
		}
	} //1101 1111 = 0xDF
		//==2
	else if ((c[0] == 1)&&(c[1] == 1))
	{
		for(;;)
		{
		*PBDR = 0x60;
		usleep(20);
		*PBDR = 0x00;
		usleep(90000);
		}

	}
```

Hope anybody can help..

---

### Post by MindSz on 2010-03-10
Maybe you can do a 'break' when your X seconds have elapsed?

---

### Post by safarin on 2010-03-10
how to?? what flag should I refer If I want to break for X second??

---

### Post by Some Penguin on 2010-03-10
I don't see why you're using loops at all.  usleep() and sleep() already wait.

---

### Post by safarin on 2010-03-10
Ok.. I using loop to give signal to Digital Input Ouput Port and make this DIO react as PWM (Pulse Width Modulation).. So I need to give the TRUE and FALSE value forever (the sleep and usleep function I use is to give the value TRUE and FALSE continuously). And at the same time.. I need some mechanism (function or something in C) to control this PWM which this mechanism is outside the for(loop forever).. Because for my system I have many PWM condition.. If I cannot jump outside this for in X time.. This mean I will stack in there (for (loop forever)) and cannot make another decision...
Until now.. I still don't get the ideas to solve this problem.. 
Any suggestion??

---

### Post by Some Penguin on 2010-03-11
So you want something to be going on a regular basis until there's some kind of input that tells it to stop doing that and instead doing something else?

You might want to look into threads.  e.g.
[http://www.yolinux.com/TUTORIALS/LinuxTutori]("http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html")[alPosixThreads.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html")
[http://www.ibm.com/developerworks/linux/library/l-posix1.html](http://www.ibm.com/developerworks/linux/library/l-posix1.html)

There have been whole books written on concurrent programming, but these sorts of tutorials should get you started.

---

