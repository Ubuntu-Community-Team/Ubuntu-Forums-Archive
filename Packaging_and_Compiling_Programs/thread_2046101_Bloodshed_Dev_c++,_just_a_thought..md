---
title: "Bloodshed Dev c++, just a thought."
date: 2012-08-22
forum: Packaging and Compiling Programs
---

### Post by Crash525 on 2012-08-22
Has anyone used this IDE before? I finally figured out why I was having such a hard time trying to write any program. For some reason dev-cpp does not like for loops and the command cin.get(). I was using bloodshed dev-cpp because it can be used from a jump drive. I get bored at work and I cannot install programs on work computers so I used bloosheds IDE and run it off of my jump drive. Well it was all fine and dandy until I started using for loops. The compiler would skip over the loops for some reason. I have MS visual studio 2008 and I can run the same program fine with out any issues or the compiler skipping some the for loops. Has anyone had any issues like this before with dev-cpp or any other compilers or IDEs? Does any one else know of a portable compiler that I could use from a jump drive?

---

### Post by SevenMachines on 2012-08-23
The chances that the compiler is faulty is usually tiny compared to the probability that your code is not doing what you expect it is. when one compiler skips something and another doesn't I'd tend to look at things being optimised out for whatever reason. In short, the best advice I could give is to post some code this is happening to to [the programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39") along with the exact compile commands used so that others can see whats going on

---

### Post by MadCow108 on 2012-08-25
> **SevenMachines said:**
> The chances that the compiler is faulty is usually tiny compared to the probability that your code is not doing what you expect it is.

this is generally very true, but not for bloodshed dev c++.
It uses some ancient mingw compiler version (< 3.4) which might very well have issues. Its last release was sometime around 2005.

please just use something newer and let that thing die.

---

### Post by Darren Sparrow on 2012-08-25
Truthfully don't use Bloodshed Dev C++. It's really outdated, and Code:Blocks is much much better. I cut my coding teeth on Dev C ++ back in the day, and although there is an attempt to carry on the project on Sourceforge, I feel its really had its day.

---

