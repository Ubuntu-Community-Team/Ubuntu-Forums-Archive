---
title: "Can fgetc() be used without suspending program flow?"
date: 2008-10-03
forum: Programming Talk
---

### Post by yoda2031 on 2008-10-03
I have a program in which there is a loop in which there is a fgetc() and the loop pauses at fgetc() until the Enter key is pressed.  Is there any function in C to basically just ask the system for the last byte of /dev/stdin (or whatever standard in is on your box)?  so you could have a program like this:

```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
  int i = 0;
  char you = "";
  while (i<3)
  {
    you = getchar();
    if (you==" ")
    {
      i++;
      printf("%s %d",you,i);
    }
  }
  return EXIT_SUCCESS;
}

```

So every time the user hits the space bar (rather than the enter key), their space is displayed followed by the loop number (which means they can only do it 3 times before the program exits successfully).  It's not very useful as it stands but I could spend a few minutes polishing that up or spend the same amount of time trying to get the program I actually want to function working... :P

So... how do I do it?

---

### Post by supirman on 2008-10-03
Yes, you can.  By default, the n_tty line discipline works in canonical mode.  In this mode, the terminal driver doesn't present the buffer to userspace until the newline is seen.  

To accomplish what you want, you need to set the terminal into raw mode.  To do this, you must manipulate the termios structure.  It sounds hard, but really it's not.

```
#include <stdio.h>
#include <termios.h>


int main(void)
{

  int ch;

  struct termios terminal_settings;

  // Get the current terminal settings
  if (tcgetattr(0, &terminal_settings) < 0)
    perror("tcgetattr()");


  // disable canonical mode processing in the line discipline driver
  terminal_settings.c_lflag &= ~ICANON;

  // apply our new settings
  if (tcsetattr(0, TCSANOW, &terminal_settings) < 0)
    perror("tcsetattr ICANON");


  // Now, getchar won't wait until enter is pressed.
  ch = getchar();

  printf("%d\n", ch);


  return 0;
}

```

---

### Post by yoda2031 on 2008-10-03
Thanks a lot! That makes a lot of sense, but I'm not sure you did it quite right... for a start, what's this variable "old"?  My compiler asks the same question :P

I think you mean it to say:
```

/* --snip-- */
  /* apply our new settings */
  if (tcsetattr(0, TCSANOW, &terminal_settings) < 0)
    perror("tcsetattr ICANON");
/* --snip-- */

```
of course, that snippet won't compile on its own - but when I amended your snippet with that, it compiles and runs.  It even does what I expect it to!

Now to just integrate that into my application, and thank Supirman in a comment... ;)

---

### Post by supirman on 2008-10-03
Sorry about that.  I had the variable named "old" originally, and then changed it - but apparently not all instances! 

Typically, you'll store the old termios settings and leave them unchanged.  You'll copy the old ones to a new struct termios and modify your new copy.  Then you can be nice and restore the original settings upon exiting your application, hence the name old.  


I'll update the previous one to be correct - thanks for catching it...

---

### Post by yoda2031 on 2008-10-03
something a bit like this?
```

  struct termios old_terminal_settings;
  struct termios new_terminal_settings;
  /* Get the current terminal settings */
  if (tcgetattr(0, &old_terminal_settings) < 0)
    perror("tcgetattr()");
  new_terminal_settings=old_terminal_settings;
  /* disable canonical mode processing in the line discipline driver */
  new_terminal_settings.c_lflag &= ~ICANON;

  /* apply our new settings */
  if (tcsetattr(0, TCSANOW, &new_terminal_settings) < 0)
    perror("tcsetattr ICANON");

```

I've also changed my mind about whether this is doing what I want... is it still suspending program flow until a key is pressed, just not caring what the key is now?

I kind of need it to say "if no key is pressed just move on" but I'm getting myself in a logic battle here with my compiler... in basic terms, I just want synchronous input and output - a clock and a command line running in parallel.  So far I can get the clock to count down on its own but it won't let the user input anything, OR I can get the user to input things but the clock only counts down when the user has finished putting data in...

---

### Post by supirman on 2008-10-03
Sorry, I didn't realize that you also wanted it to read data only if available, else continue on normally.

The good news is that it's doable, the bad news is that it's more complicated.  

Since you want this to be non-blocking, we'll have to move to a more advanced approach.  We'll use the select() call with a timeout period of zero so that it will check if a key is pressed, but it won't wait for a key to be a pressed.  The net effect is that your application should work as expected finally.

To do this, we'll implement a function which will tell you when data is available on stdin.  Then, you only call getchar when data is known to be avialable.

```
#include <stdio.h>
#include <termios.h>
#include <sys/select.h>
#include <unistd.h>
#include <string.h>

int is_key_pressed(void)
{
     struct timeval tv;
     fd_set fds;
     tv.tv_sec = 0;
     tv.tv_usec = 0;

     FD_ZERO(&fds);
     FD_SET(STDIN_FILENO, &fds); 

     select(STDIN_FILENO+1, &fds, NULL, NULL, &tv);
     return FD_ISSET(STDIN_FILENO, &fds);
}

int main(void)
{

  int ch;

  struct termios old_terminal_settings, new_terminal_settings;


  // Get the current terminal settings
  if (tcgetattr(0, &old_terminal_settings) < 0)
    perror("tcgetattr()");


  memcpy(&new_terminal_settings, &old_terminal_settings, sizeof(struct termios));

  // disable canonical mode processing in the line discipline driver
  new_terminal_settings.c_lflag &= ~ICANON;

  // apply our new settings
  if (tcsetattr(0, TCSANOW, &new_terminal_settings) < 0)
    perror("tcsetattr ICANON");


  while(1)
  {
    sleep(1);

    // Check if a key is pressed.  If it is, call getchar to fetch it.
    if(is_key_pressed())
    {
      ch = getchar();

      printf("%d\n", ch);

      if(ch == 'x') break;
    }
    else
    {
      printf("nothing pressed\n");
    }
  }

  // restore the terminal settings to their prvious state
  if (tcsetattr(0, TCSANOW, &old_terminal_settings) < 0)
    perror("tcsetattr ICANON");


  return 0;
}

```

See "man select" for mor information on what it's doing.  Note, that in this example, only one key per second is seen since I'm only doing one getchar per loop and then sleeping for 1 second.  Depending on what exactly you plan on doing in your main program, there are different ways to tackle this problem.

---

### Post by lisati on 2008-10-03
The kbdhit() function (spelling?) comes to mind from the minimal programming I've done in Turbo C in MS-DOS to check if a key has been pressed without pausing. Is that the kind of thing you're after?

---

### Post by supirman on 2008-10-03
> **lisati said:**
> The kbdhit() function (spelling?) comes to mind from the minimal programming I've done in Turbo C in MS-DOS to check if a key has been pressed without pausing. Is that the kind of thing you're after?


As far as I know, that doesn't exist natively on linux, but that functionality is essently what the above is_key_pressed() routine does...

---

### Post by yoda2031 on 2008-10-03
Thanks again, supirman.  You are such a guru! It'll take some tweaking of the flow until I can get the wider application behaving as expected, but I think [read:hope] that's pretty much all I'll need to be going on for now.  :)

---

### Post by supirman on 2008-10-03
Glad to help.  If you get stuck again, there are plenty of people on the boards to help...

---

### Post by nikraj87 on 2011-08-02
HI 
 
I saw this post when i was looking for coding a timeout on standard input.
The is_key_pressed function works perfectly fine I wanted to know if there is any way without using such functions I can have standard input with timeout.. "wait for input for specified time only" . Is there any of versions of getch ,getc,getchar, or scanf or anything that comes out of default libraries which timesout ?
 
And one more question -when we grab standard input through any of above mentioned should we get echo of what we give as input through keyboard by default ??

---

### Post by Wim Sturkenboom on 2011-08-03
Specify a time in *tv.tv_sec* in post #6

Next add a check
```

if(select(....) == 0)
{
    //timeout occured
}
else
{
    //something happened on the file descriptors
}

```

And read *man select*

---

