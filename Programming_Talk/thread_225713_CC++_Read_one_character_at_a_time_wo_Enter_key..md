---
title: "C/C++: Read one character at a time w/o Enter key."
date: 2006-07-30
forum: Programming Talk
---

### Post by dimis on 2006-07-30
Hello,
I have a simple problem actually (C/C++), but unfortunatelly seem not to be able to find the solution pretty easily. Here is the case:
I want to read the characters from standard input as soon as they are available, i.e. no Carriage Return is required to be pressed.

I re-read about various functions but I simply can't make it work the way I want. My latest attempt, which also failed was something like the following
(let's say that as soon as I read character 'a' I want to stop reading characters):
```
c = 'b';
do {
   c = getchar ();
   fflush( stdin );
} while (c != 'a');
```

Thank you in advance,
- dimis -

---

### Post by dabear on 2006-07-30
Well, I guess you'd have to turn off line buffering.
Take a look at: [http://www.flipcode.org/cgi-bin/fcarticles.cgi?show=64166](http://www.flipcode.org/cgi-bin/fcarticles.cgi?show=64166)

Here's how to do it in python, btw:
```

try:
    from msvcrt import getch
except ImportError:
   #we're not on Windows, so we try the Unix-like approach
    def getch( ):
        import sys, tty, termios
        fd = sys.stdin.fileno()
        old_settings = termios.tcgetattr(fd)
        try:
            tty.setraw(fd)
            ch = sys.stdin.read(1)
        finally:
            termios.tcsetattr(fd, termios.TCSADRAIN, old_settings)
        return ch

```

---

### Post by subiet on 2006-07-30
> **dabear said:**
> 

[snip]

   #we're not on Windows, so we try the Unix-like approach

[snip]



ridiculous, c++ is a platform/layer independent language, and therefore such references and assumptions should be avoided at all costs.

secondly, the author should ideally post his question in the comp.std.c++ usenet group.

the guidelines clearly state that "Feel free to discuss any programming trends, ideas, problems, etc relating to Ubuntu Linux" and i do not think that c++ (standard) should have anything to do with platform dependence.

---

### Post by Stone123 on 2006-07-30
I would go with some lib for event handling and using its function. 

maby this can help:

[http://msdn2.microsoft.com/en-us/library/ee2k0a7d.aspx](http://msdn2.microsoft.com/en-us/library/ee2k0a7d.aspx)

---

### Post by misterE0 on 2006-07-31
you can use getch().  I think it's in conio.h

---

### Post by subiet on 2006-08-01
> **misterE0 said:**
> you can use getch().  I think it's in conio.h

that way he can use getche too (get character echo), but then conio.h isn't standard c++. it (conio.h) is platform and architechture dependent.

---

### Post by wmcbrine on 2006-08-02
I'd suggest **curses** as the standard Unix way to do this. It provides getch() and other nice things, takes care of all that low-level termio stuff for you, and lets your program work on all kinds of terminals (xterm, console, serial, etc.).

subiet, there *is no* standard C or C++ way to do this, and the question will not be welcomed in comp.std.c++.

P.S. I should say, it wouldn't be welcomed in comp.lang.c -- I've seen people stomped hard and quick for posting about curses there. I'm only assuming that comp.std.c++ would be the same.

---

### Post by subiet on 2006-08-02
> **wmcbrine said:**
> 

subiet, there *is no* standard C or C++ way to do this, and the question will not be welcomed in comp.std.c++.




if what you are saying is true (that there is no standard compliant way to do this), which seems to be very possible, as C++ doesn't recognoize any standard input or output device, like keyboard/monitor etc, then you can first confirm it in the comp.std.c++, they might come up with a suggestion, where you control the input buffer, and after that you can suggest something for the inclusion in standard too, if it is technically possible, given the constraints of maintaing a platform and architechture independent c++.

---

### Post by dimis on 2006-08-03
Thank you all for your input guys. I never thought there was no standar platform-independent way of making this thing. Anyway, for the time being I do not implement the feature, as I am testing on Ubuntu64 and eventually I want this program to work under Windows.

However, I followed dabear's links and tried to copy-paste some code I found there so that I can play a bit on my linux system. Unfortunately, not even a single variant of Unix-like editions did compile. Any suggestions? If you have 5 minutes (and you've used getch() in the past) can you please upload a small program that exhibits the feature?

Thanks again,
- dimis -

---

### Post by VirtuAlex on 2006-08-03
> **dimis said:**
> If you have 5 minutes (and you've used getch() in the past) can you please upload a small program that exhibits the feature?

Modified example from [http://c-faq.com/osdep/cbreak.html]("http://c-faq.com/osdep/cbreak.html")
test.c
```
#include <stdio.h>
#include <curses.h>

int main(int argc, char *argv[])
{
	char c;
	initscr();
	cbreak();
	do
	{
		c = getch();
	} while (c != 'a');
	endwin();
	return 0;
}
```
compile and run
```
gcc -lcurses -o test test.c
./test
```

---

### Post by dimis on 2006-08-03
Thanks for the input VirtuAlex. However, I still have problems. Obviously, not everything (regarding libraries) is installed under Ubuntu64. I tried to use Synaptic to install some packages containing the word "curses" like:
lib32ncurses5-dev
libncurses5-dev
but seems that universe repositories are temporarilly down (or I temporarilly have problems with my internet connection).

Anyway, I tried to find the file on the internet.
First thing that showed up was from [opensolaris]("http://cvs.opensolaris.org/source/xref/on/usr/src/ucbhead/curses.h"). I got the file and I installed (copied :p) it under my /usr/include directory.
Now, on compile time, I get the following errors:
```
test.c: In function ‘main’:
test.c:8: error: invalid use of incomplete typedef ‘SGTTY’
test.c:8: error: ‘CBREAK’ undeclared (first use in this function)
test.c:8: error: (Each undeclared identifier is reported only once
test.c:8: error: for each function it appears in.)
```

Now this last one is off-topic but I never really cared up to now where those headers were supposed to be stored. If I search for stdio.h in my entire filesystem I get:
```
./usr/include/bits/stdio.h
./usr/include/stdio.h
```
Is this normal? Moreover, is it normal that 'diff'-ing those files, I get results ... :confused:

---

### Post by VirtuAlex on 2006-08-03
That I do not know. I have bits/stdio.h too and have no idea what these bits are. By the way, before this afternoon I had no idea what ncurses are either. I would suggest you wait for repos to be available or switch the mirrior, instead of dumping headers from different system into your include and wandering what these errors mean.

---

### Post by misterE0 on 2006-08-03
so i did some googling around and found this to work:

```

#include <stdio.h>
#include <unistd.h>
#include <termios.h>

int main()
{
	char x = ' ';
	
	printf("Press any key to continue...\n");
	x = getch();

	printf("The key you entered is: %c \n", x);
	
	return 0;
}

int getch(void)
{
    int ch;
    struct termios oldt;
    struct termios newt;
    tcgetattr(STDIN_FILENO, &oldt); /*store old settings */
    newt = oldt; /* copy old settings to new settings */
    newt.c_lflag &= ~(ICANON | ECHO); /* make one change to old settings in new settings */
    tcsetattr(STDIN_FILENO, TCSANOW, &newt); /*apply the new settings immediatly */
    ch = getchar(); /* standard getchar call */
    tcsetattr(STDIN_FILENO, TCSANOW, &oldt); /*reapply the old settings */
    return ch; /*return received char */
}


```

it was on linuxquestions.org.  Just copy the function getch and make sure to include the unistd and termios headers.

---

### Post by dimis on 2006-08-04
Indeed! The above is the first working piece of code in my machine! :)
Thank you very much misterE0.

---

### Post by napsy on 2006-08-04
You can implement the ncurses getch() with select(). There's an example in the select(3) manual page.

---

### Post by wmcbrine on 2006-08-04
> **dimis said:**
> I tried to use Synaptic to install some packages containing the word "curses" like:
lib32ncurses5-dev
libncurses5-devYou're on the right track there...

> *but seems that universe repositories are temporarilly down (or I temporarilly have problems with my internet connection).*Well, it's not in universe anyway, it's in main.

> [i]Anyway, I tried to find the file on the internet. First thing that showed up was from [opensolaris]("http://cvs.opensolaris.org/source/xref/on/usr/src/ucbhead/curses.h"). 
[/i]Oh dear. No, that won't work with ncurses, nor with Ubuntu. It's a whole different implementation of curses. Just try the repositories again. If that doesn't work, than IMHO you have bigger problems than curses to worry about. But you can get the source of ncurses at [http://invisible-island.net/ncurses/](http://invisible-island.net/ncurses/) .

And yes, you could use termios instead of curses. But I invite you to consider two things:

1. Compared to curses code, termios code is complex and hard to understand.

2. You will probably not be able to port your termios code to Windows, as you mentioned you wanted to do. But curses code can be ported, by linking against PDCurses instead of ncurses.

---

### Post by dimis on 2006-08-04
> **wmcbrine said:**
> Well, it's not in universe anyway, it's in main.
Are you sure? Because, repositories worked this time and libncurses5-dev was indeed in main, but lib32 was in universe.

As for the solaris-attempt, it was just a wild try ... and I reported that it didn't work. :) Thanks, for the link on curses. I'll check it out as soon as I come back from holiday. :D As for porting in win, I don't think there will be much trouble. I will just "hide" the linux/win implementations inside one of my functions, which is going to do all the work. Anyway, fact is that I had too much work these last days and haven't managed to read a single line regarding curses, termio and conio ...

Anyway,
I want to thank you all once again for your input. :)
Regards,
dimis

---

