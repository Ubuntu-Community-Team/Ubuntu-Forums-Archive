---
title: "Annoying bug that is only present in win32 builds"
date: 2011-10-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2011-10-05
I wrote a 4-player Tron clone yesterday using C and SDL. There is about 400 lines of code.
There is a bug, that causes players to die semi-randomly by hitting non-existent walls.
This bug makes the game completely unplayable, because it happens very often :(

But the real problem is, that this bug is only present when I compile my game in windows XP using VS08.
In other words, the Linux executable does not have the bug. :-k
I'm using gcc 4.4.5 in 64-bit Linux Mint, and compiling the Windows .exe in a virtualbox (32bit).
Gcc doesn't give any warnings with -Wall -Wextra -ansi, and valgrind doesn't report anything suspicious.
And there are no OS-specific #ifdefs, so this code should be 100% portable.

Also, I have noticed that if player #1 turns left, he always dies. But if he turns first right and later turns left, he doesn't.
The other players seem to die randomly without any consistent or obvious patterns.

I have absolutely no clue what might cause this. :confused: Can you help? 
What kind of mistakes or typos should I be looking for?

---

### Post by DarkAmbient on 2011-10-05
Do you know how to debug your project? Try to run the project in debug-mode with a breakpoint at the player die-event. Perhaps then it's easier to sort out what causes it.

---

### Post by nvteighen on 2011-10-05
Chances are that you're relying on some undefined behavior that works on GNU/Linux GCC for some random reason, but not on VS...

---

### Post by crazyfuturamanoob on 2011-10-05
I save each grid cell as an integer. Players die when they move into a tile with a nonzero value.
But evil nonzero integers just popped out of nowhere and killed the innocent players.

Now I finally fixed this bug. Here is the bad code:
```

typedef enum {
    D_RIGHT=0,
    D_DOWN=1,
    D_LEFT=2,
    D_UP=3
} Direction;
#define ROTATE_CW(dir) (((dir)+1)%4)
#define ROTATE_CCW(dir) (((dir)-1)%4)

```
gcc thinks 0%4 is 0, while VS apparently blows up and corrupts everything. Yup, I was relying on undefined behaviour.
I have spent about 1 hour coding the game itself and like 10 hours on searching this bug. Now I feel myself stupid, but also a winner.
Like always after fixing a bug. :)

---

### Post by Bachstelze on 2011-10-05
> **crazyfuturamanoob said:**
> 
gcc thinks 0%4 is 0, while VS apparently blows up and corrupts everything. Yup, I was relying on undefined behaviour.

0%4 should definitely be 0. That's not undefined behavior, that's a bug in your compiler.

*EDIT:* (-1)%4, however, is -1, not 3.

---

### Post by trent.josephsen on 2011-10-05
> **Bachstelze said:**
> 0%4 should definitely be 0. That's not undefined behavior, that's a bug in your compiler.

*EDIT:* (-1)%4, however, is -1, not 3.

I was under the impression that -a%b and -a/b can be defined either way, provided that b*(-a/b) + (-a%b) == -a.  Or am I thinking about a%-b?

---

### Post by Bachstelze on 2011-10-06
> **trent.josephsen said:**
> I was under the impression that -a%b and -a/b can be defined either way, provided that b*(-a/b) + (-a%b) == -a.  Or am I thinking about a%-b?

Yes, I should have said "may be -1", which is probably not what is expected.

---

### Post by crazyfuturamanoob on 2011-10-06
I have always assumed that a modulus can't return negative values, so I though -1%4 equals 3.
Here is the new code anyway: (forgot to add to my previous post)
```

#define ROTATE_CW(dir) ( (dir) == 3 ? 0 : ((dir)+1) )
#define ROTATE_CCW(dir) ( (dir) == 0 ? 3 : ((dir)-1) )

```

---

### Post by Bachstelze on 2011-10-06
I would have just done

```
#define ROTATE_CCW(dir) (((dir)+3)%4)
```

There should be no need to change ROTATE_CW.

---

