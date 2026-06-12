---
title: "[C++]Clearing the console - Cross Platform"
date: 2007-08-13
forum: Programming Talk
---

### Post by anothrguitarist on 2007-08-13
I am making a simple text tic tac toe game, and I was wondering how to clear the console window. Also, I want this game to work on windows as well, so is there any cross-platform method for clearing the console window and setting the cursor back to 0,0?

Regards,
- John

---

### Post by anothrguitarist on 2007-08-15
Well I found a non cross platform method of doing this:

system("clear")

And if I want to create a windows version of this program, I can just edit a few lines.

---

### Post by slavik on 2007-08-15
read about ncurses. :)

---

### Post by Wybiral on 2007-08-15
> **slavik said:**
> read about ncurses. :)

NCurses is really good, but I'm not entirely sure if there is a windows port of it. I could be wrong, but at first glance it looks like there is none.

---

### Post by slavik on 2007-08-15
probably not, but it beats printing stuff over and over again ...

---

### Post by Wybiral on 2007-08-15
> **slavik said:**
> probably not, but it beats printing stuff over and over again ...

I'll second that. If you plan to write some sort of UI in the terminal, you'll be much better off using a library like ncurses then to use all the work-arounds required to make simple printed output look right.

---

### Post by LaRoza on 2007-08-15
> **anothrguitarist said:**
> Well I found a non cross platform method of doing this:

system("clear")

And if I want to create a windows version of this program, I can just edit a few lines.

You can use:

```

#ifndef WINDOWS
system("clear");
#else
system("cls");
#endif

```

When you compile it for Windows, just just define Windows:
```

#define WINDOWS

```

---

### Post by anothrguitarist on 2007-08-15
Thanks all :)

---

### Post by slavik on 2007-08-15
there is actually a #define that the compiler does ... check the gcc headers (__WIN32 I think)

this way, you don't even have to do any extra work. :)

---

### Post by anothrguitarist on 2007-08-15
Got it. So, instead of ifndef windows, use __WIN32... Although it is a console program, do I need to check for __WIN64 too?

Thank you this makes things much better.

Edit: Err.. I'll check the headers to see what I find.

---

### Post by anothrguitarist on 2007-08-16
Works like a charm on both windows and ubuntu.

Cheers,
- John

---

