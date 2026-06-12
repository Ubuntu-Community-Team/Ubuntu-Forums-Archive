---
title: "C question: how do I have a function operate for 10 seconds"
date: 2005-05-30
forum: Programming Talk
---

### Post by epb613 on 2005-05-30
I wanna write a function to count how many times I press spacebar in 10 seconds. Is there a timer function or something that I can use? (I'm a C newbie).

I'm guessing it would go along the lines of:

int spaces = 0;
start timer
while (timer < 10) {
check to see if last key pressed was spacebar and if so spaces++ 
}
printf("%d", spaces);

Sorry for mixing pseudocode and real code.

Thanks in advance.

---

### Post by epb613 on 2005-05-30
Hmmm, I actually came up with this based on [http://www.cplusplus.com/ref/ctime/](http://www.cplusplus.com/ref/ctime/):

```

#include <stdio.h>
#include <time.h>

int main ()
{
  long seconds = time(NULL), timeUp = seconds + 10;
  printf("\n");
  while(seconds < timeUp)
  {
    /* SPACEBAR COUNTER GOES HERE */
    seconds = time(NULL);
  }
  
  return 0;
}

```

The code is pretty simple. The only problem with it is that it doesnt really measure 10 seconds as I lose however far I am into the first second when I start the program. Is there a better way to do this?

Thanks in advance.

---

### Post by jerome bettis on 2005-05-30
```
#include <stdio.h>
#include <time.h>

int main()  {
	const int RUNTIME = 10;
	time_t start, current;
	int spaces = 0;    
	start = time(NULL);
	do {
		current = time(NULL);
		if (lastKeyPressed == ' ') // you get to figure that out
		   spaces++;
	} while (difftime(current, start) < RUNTIME);
	return 0;
}
```

---

### Post by epb613 on 2005-05-30
Oooh that's really cool. My way worked fine but your version is alot cleaner and skips unneccessary steps (using the difftime function). Thanks alot!

---

### Post by jerome bettis on 2005-05-31
lol you're welcome .. it's almost the same thing

not sure how you're gonna do the input part though. i hate I/O in C ... but love it in C++.

---

### Post by epb613 on 2005-05-31
:) So lets say I broke down and used c++....

[To build a c++ program, I just type 'g++ program.c' instead of 'cc program.c' - right?]

---

### Post by epb613 on 2005-05-31
Haha I found it! After hours of searching... [http://cboard.cprogramming.com/showthread.php?t=27714](http://cboard.cprogramming.com/showthread.php?t=27714)

> 
```
#include <stdio.h>
#include <termios.h>
#include <unistd.h>

int mygetch( ) {
  struct termios oldt,
                 newt;
  int            ch;
  tcgetattr( STDIN_FILENO, &oldt );
  newt = oldt;
  newt.c_lflag &= ~( ICANON | ECHO );
  tcsetattr( STDIN_FILENO, TCSANOW, &newt );
  ch = getchar();
  tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
  return ch;
}

```


Using this, my code is:

```

while(seconds < timeUp)
  {
    c = mygetch();
    printf("%c", c);
    if (c == ' ') spaces++;
    seconds = time(NULL);
  }

```

I havent incorperated your code in yet. Thanks for all the help by the way!

---

### Post by LordHunter317 on 2005-05-31
No, writing C++ isn't as simple as changing your compiler from 'cc' to 'g++'.  If that's your current line of thinking, don't even try to write any C++ until you read a complete book on the subject.  *Thinking in C++* is OK and available online for free.

You don't need that nasty termios using function.  You can do what you want using standard C I/O functions.

The fact you didn't realize that tells me you need to go read a good C tutorial as well.  K&R's *The C Programming Language* is the basic tome and an easy enough read.

---

### Post by epb613 on 2005-05-31
I don't think it's neccessary to be a C++ expert before having some fun with it. Could you just tell me the code I need?

---

### Post by jerome bettis on 2005-05-31
actually I/O streams in C++ (and C) are pretty complicated.  i wouldn't expect everyone to sit here and spoon feed you code all day so you can continue getting drunk and get an A on your assignment.

:-P

[www.cplusplus.com](www.cplusplus.com)  read up

---

