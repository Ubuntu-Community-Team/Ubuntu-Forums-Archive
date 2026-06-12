---
title: "Eclipse CDT crashed with Boost libraries"
date: 2007-10-23
forum: Programming Talk
---

### Post by perigee on 2007-10-23
I've installed Boost C++ libraries along with CDT-eclipse. Each time, I tried to make a dot, the system is just frozen. I thought that Eclipse tried to find member function for the object, but failed. Could I just disable the auto-complete functionality?


Thank you in advance.

---

### Post by prisoner849 on 2009-04-15
Hey, I know it's a little late but for anybody with this problem (which should be anybody using CDT, I've used it on both Ubuntu 8.10 and XP 64/32 with and without sun java 6), but you can turn off auto complete.

For linux and windows versions, you can find it in these options:
Window->Preferences->C/C++->Editor->Content Assistant
Then de-check all the 'Auto activation' check boxes.

Like I said, I've gone through a few tutorials about forcing Eclipse to use the proper java 6 engine, but it's still way too slow and sometimes just gives up the ghost. I use to use intellisense a lot in Visual Studios, but really, it's better if you don't.

Get into the habit of writing code that's easy to remember and short to type. Don't get into the habit that some workplaces suggest and write massive function names for the sake of a description. Co-workers should not be so lazy and go and read the header file first before using your functions in the first place.

Just thought I'd get that off my chest.

---

### Post by leeoz on 2009-06-23
same problem here.

but... anyone knows a fix so i can use the autocomplete function because it is really handy?

leeoz

---

