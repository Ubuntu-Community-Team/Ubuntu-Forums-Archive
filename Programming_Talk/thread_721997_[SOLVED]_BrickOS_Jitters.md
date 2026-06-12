---
title: "[SOLVED] BrickOS Jitters"
date: 2008-03-11
forum: Programming Talk
---

### Post by HIGHLIFE on 2008-03-11
Hey guys I was playing around with BrickOS and had a problem with this code:

```
#include <config.h>
#include <dmotor.h>
#include <dsensor.h>



int main() 
{

while (1)
	{

		motor_a_dir(fwd);
		motor_c_dir(fwd);

		motor_a_speed(255);
		motor_c_speed(255);

		if (TOUCH_1 == 1)
			{
			 	motor_a_dir(rev);
				motor_a_speed(0);	
			}
		else 
			{
				motor_a_dir(fwd);
				motor_a_speed(255);
			}
	}

return 0;
}
```

When I press the touch sensor the motor just jitters in the reverse direction rather than driving backwards at full speed.  What am I doing wrong here?

---

### Post by Zugzwang on 2008-03-12
Should be obvious. If you press the button then the code
```

{
   motor_a_dir(rev);
   motor_a_speed(0);	
}
``` is executed. Afterwards the end of the control loop is reached (the "while(1) {...}"), so the controller begins executing it from the beginning of the loop again, which starts with:
```

motor_a_dir(fwd);
motor_c_dir(fwd);

motor_a_speed(255);
motor_c_speed(255);

```
Afterwards the condition is checked again and ```

{
   motor_a_dir(rev);
   motor_a_speed(0);	
}
``` is again executed (and so on). This surely causes jitter since the direction of the motor is switched extremly often. You probably want: [PHP]#include <config.h>
#include <dmotor.h>
#include <dsensor.h>

int main() 
{
   motor_a_dir(fwd);
   motor_c_dir(fwd);

   motor_a_speed(255);
   motor_c_speed(255);
   while (1)
	{

		if (TOUCH_1 == 1)
			{
			 	motor_a_dir(rev);
				motor_a_speed(0);	
			}
		else 
			{
				motor_a_dir(fwd);
				motor_a_speed(255);
			}
	}

return 0;
}[/PHP]

---

### Post by HIGHLIFE on 2008-03-12
#-o Haha thanks.

---

