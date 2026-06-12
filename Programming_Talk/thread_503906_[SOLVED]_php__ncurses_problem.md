---
title: "[SOLVED] php / ncurses problem"
date: 2007-07-18
forum: Programming Talk
---

### Post by xavier_r on 2007-07-18
OK... so i have this code... in PHP using Ncurses...

```

while(1)
{
    ...
    display_time()
    ...
    ncurses_getch($lower_main_window) //wait for pressing key
    ...
    ...
    ...
}
```

In this Ncurse app, I want to display changing time continously(real time)... whether or not the user presses a key...
But in my code... The program has to wait for a key... and so time change is not shown untul the users presses a key...


I have tried various stuff... but none gave results...
Also apparently there are only two "get character" functions in PHP/Ncurses getch and wgetch, both of which wait for a key... So options are exhausted...
How to solve this?

---

### Post by crashie on 2007-07-18
Try the ncurses_timeout function. First set a timeout, then call ncurses_getch but check if it returned ERR. If it did it timed out and no key was pressed. You can do this in a loop and wait until it returns a key instead of ERR. Just remeber to remove the timeout (set it to -1) when you're done:

[PHP]
while(1)
{
    ...
    ncurses_timeout($lower_main_window, 1000); // 1000 ms = one second
    do {
      display_time()
      $key = ncurses_getch($lower_main_window); //wait for pressing key
   } while ($key == ERR);
   ncurses_timeout($lower_main_window, -1); // Disable timeout
    ...
    ...
    ...
}
[/PHP]

When i installed PHP i choosed to remove ncurses support so unfortunately i can't test this code but i think it should work.

---

### Post by xavier_r on 2007-07-18
You example didnt work
But timeout() is a good suggestion... thanks...
I'll check that out...

---

### Post by xavier_r on 2007-07-20
hey i solved the problem using timeout() :) thanks a lot

---

