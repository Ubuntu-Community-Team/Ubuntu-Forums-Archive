---
title: "C program compiler gives wrong results"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by sreeharitk on 2012-04-08
Hey all!!
Humble salute to all great  souls of a great community!
Hope somebody will help me in solving the below issues
Problem 
I recently started learning C. I run programs in terminal. but The following program gives me a wrong result.
#include<stdio.h>
main ()
{
char in;
puts ("enter a character");
in=getchar();
fflush (stdin);
if (in!='y'|| in!='Y')
puts ("You did not enter Y!!");
else
puts ("There you entered Y sweetiee!!!");
}

In this program, when I enter Y or y, it gives me the result  "You did not enter Y!!".
Where am I going wrong??

---

### Post by roelforg on 2012-04-08
> **sreeharitk said:**
> Hey all!!
Humble salute to all great  souls of a great community!
Hope somebody will help me in solving the below issues
Problem 
I recently started learning C. I run programs in terminal. but The following program gives me a wrong result.
#include<stdio.h>
main ()
{
char in;
puts ("enter a character");
in=getchar();
fflush (stdin);
if (in!='y'|| in!='Y')
puts ("You did not enter Y!!");
else
puts ("There you entered Y sweetiee!!!");
}

In this program, when I enter Y or y, it gives me the result  "You did not enter Y!!".
Where am I going wrong??

replace the if with this:
```

if ((in!='y')||(in!='Y'))

```

---

### Post by dfreer on 2012-04-08
Your logic is wrong. When using || (logical OR), if either of your conditions equals true, the whole expression is equal to true. Consider the following:
```

in = y

(in != y) = False
(in != Y) = True
(false || true) = True

```
```

in = Y 

(in != y) = True
(in != Y) = False
(true || false) = True

```

One of the correct ways for this to work would be to use the following logic:
```
if ((in == 'y') || ( in == 'Y')) # This is a bit more readable and easier to follow than your expression.
puts ("You have entered the letter 'Y'");
else
puts ("You did not enter the letter 'Y'");

```

OR

```
if ((in != 'y') && (in != 'Y'))
puts ("You did not enter Y!!");
else
puts ("There you entered Y sweetiee!!!");
```

---

### Post by sreeharitk on 2012-04-08
Oh!!!!
Thanks for a very quick reply [roelforg]("http://ubuntuforums.org/member.php?u=1517674").
But even that does not work!!
is there any chance that I am shot of some installed files needed for the smooth run of C?!!
I installed Build essentials

---

### Post by roelforg on 2012-04-08
> **sreeharitk said:**
> Oh!!!!
Thanks for a very quick reply [roelforg]("http://ubuntuforums.org/member.php?u=1517674").
But even that does not work!!
is there any chance that I am shot of some installed files needed for the smooth run of C?!!
I installed Build essentials

should work, gimme a min

edit: stupid me! i missed the logic error. the || in the if should be &&
The reason is that your way of doing things is a bit the reverse of what most do.
You do:
if you didnt press y print "bad"
else print "good"
whereas most will do:
if you pressed y print "good"
else print "bad"

---

### Post by sreeharitk on 2012-04-08
[Hi Dfreer]("http://ubuntuforums.org/member.php?u=66193")
Thanks a lot for that reply
so I did re-write in this way 
#include<stdio.h>
main ()
{
char in;
puts ("enter a character");
in=getchar();
fflush (stdin);
if ((in=='y')||(in=='Y'))
puts ("You entered Ysweetie!!");
else
puts ("There you did not enter Y!!!");
}
Now it works perfect.
Thanks a lot for the help!!

---

### Post by roelforg on 2012-04-08
> **sreeharitk said:**
> [Hi Dfreer]("http://ubuntuforums.org/member.php?u=66193")
Thanks a lot for that reply
so I did re-write in this way 
#include<stdio.h>
main ()
{
char in;
puts ("enter a character");
in=getchar();
fflush (stdin);
if ((in=='y')||(in=='Y'))
puts ("You entered Ysweetie!!");
else
puts ("There you did not enter Y!!!");
}
Now it works perfect.
Thanks a lot for the help!!

happy to see you're happy!
Ironically i am programming whilst posting.

---

### Post by sreeharitk on 2012-04-08
Hey roelforg
That too works great!!!!
Thanks for that!!

---

### Post by roelforg on 2012-04-08
> **sreeharitk said:**
> Hey roelforg
That too works great!!!!
Thanks for that!!

Just remember:
you have to discover your own style, but the one rule of if that i think is important:
when you're comparing things, make sure the thing you want to test (werether in equals y or Y, in your case) inside the if so else can handle the edge cases (not a problem here, but could be when you write complex ones)

---

