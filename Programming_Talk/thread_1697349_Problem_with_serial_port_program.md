---
title: "Problem with serial port program"
date: 2011-02-28
forum: Programming Talk
---

### Post by alegomaster on 2011-02-28
Hi, right now I am new to Ubuntu so I can't solve this issue by myself.

I wrote a program in C that would communicate data between two computers, and have an issue with the program. Whenever I sent text from one computer to the other, the recieving computer would send it back to the transmitting computer even though I didn't specify it. Here's the code that is involved with receiving.

```

//First part
file=fopen("/dev/ttyS0","r");
// Some Error checking code

while (1==1)
	{
		while(fgets(test, sizeof(test), file)!=NULL);
		{
		fputs(test, stdout);
		}
        }


```

---

### Post by johnl on 2011-02-28
You probably need to:

1. retrieve the current tty settings with tcgetattr
2. mask out the appropriate ECHO flags
3. update the tty settings with tcsetattr

check the man pages (**man tcsetattr**) to get started.

Hope this helps.

---

### Post by alegomaster on 2011-03-01
> **johnl said:**
> You probably need to:

1. retrieve the current tty settings with tcgetattr
2. mask out the appropriate ECHO flags
3. update the tty settings with tcsetattr

check the man pages (**man tcsetattr**) to get started.

Hope this helps.



Right now I have issues with figuring out which flag does the ECHO. Can anybody help.

---

