---
title: "brickOS - int main() return 0;"
date: 2007-12-23
forum: Programming Talk
---

### Post by Suraine on 2007-12-23
im new in brickOS
so, i try on testing the motor controlling stuff.
the following is my program:

#include <unistd.h>
#include <conio.h>
#include <time.h>
#include <dmotor.h>

int main(int argc, char **argv)
{
	motor_a_speed(MIN_SPEED);
	motor_a_dir(fwd);
	sleep(5);
	off();
	return 0;
}

when i compile it with brickOS version 5.0.3.32 makefile
however the error comes out:

In function "int main(int, char **)
"0" cannot be used as a function.

why is that so?
anyone can help?

thanks:)

---

### Post by moma on 2007-12-24
Hello,

The BrickOS's source code ( "util/dll-src/lx.c" )  shows that **off** is defined as 
[COLOR="DimGray"]unsigned short off =(ptr[0]<<8 ) | ptr[1];[/COLOR]

**off**  is also defined in the "include/dmotor.h" file as an enum value (enum MotorDirection).

It seems to me that your function off() beceomes a function call (where the function name is number 0)
0();

You have to replace the off() function with something else.

Open the "include/dmotor.h" file and study what are the possible motor direction values.

$ [COLOR="SeaGreen"]cat include/dmotor.h[/COLOR]```

...
//! The motor directions
typedef enum {
  off = 0,			//!< freewheel
  fwd = 1,			//!< forward
  rev = 2,			//!< reverse
  brake = 3			//!< hold current position
} MotorDirection;
...
```
So you may call 
motor_a_dir(off);
----

Open the [source package...]("http://sourceforge.net/project/showfiles.php?group_id=58151&package_id=53978&release_id=297797"), unpack it to your $HOME and study the examples in the Demo directory.
----
Drive safely!

Merry Christmas

---

