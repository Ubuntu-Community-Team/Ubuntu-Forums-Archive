---
title: "Convert Perl script to C code"
date: 2009-03-04
forum: Programming Talk
---

### Post by rvbhute on 2009-03-04
I have a Perl script that I run every second - used by Conky

```
#!/usr/bin/perl

use strict;

$_ = `sudo iwconfig eth1`;

if (/ Link Quality=([0-9]\/[0-9]) /) 
{
	print $1;
}
```

Obviously it would be more efficient in C code. My C is very very rusty. Can someone point out the resources to do it in C? 

1. Capture output of external program
2. Capture required part through Regular Expressions

---

### Post by sujoy on 2009-03-04
C for a script like this would be overkill IMO
perl, bash, awk etc, were made for this

---

### Post by imdano on 2009-03-04
You don't think you'd be getting that much of an efficiency boost either.  The most expensive part of that script is the call to iwconfig, which is expensive in every language.

---

### Post by rvbhute on 2009-03-04
I was worried whether it would be OK to call a Perl script every second? Well, actually, right now, there are three quick scripts - returning ESSID, Rate and Link Quality each. I may write a few more later on. I thought maybe running it as a compiled program would be faster, but you are right regarding the call to an external program - the time it would take for that would render any gains made by a compiled C program as insignificant. I hadn't thought of that.

Regards.

---

### Post by imdano on 2009-03-04
The real question is whether you think it's ok to call iwconfig every second.  Or 3 times every second, if I read that last post correctly.  You may want to try updating ESSID, rate, and link quality using the output from just one iwconfig call, and maybe make the time between calls a few seconds longer.

If you really wanted it to be fast you could write the whole thing in C, but instead of parsing iwconfig output, use the ioctl calls iwconfig uses internally to get the essid, rate, and link quality directly.  Probably (definitely?) overkill, but it might be a nice learning experience.

---

### Post by nvteighen on 2009-03-04
I agree with the previous posts: you are using Perl for what is meant for.

Also, nothing implies C will do stuff more efficiently... yes, it will be faster because it's executed (almost) directly by the system... but real boost ups come from algorithmic improvements.

What I'd consider is whether that 'sudo' should be hardcoded into the program or not. I wouldn't do what you did, actually and enforce explicit 'sudo' by the user somehow.

---

### Post by rvbhute on 2009-03-05
*points to self and shakes head* I am using proprietary wireless drivers (Broadcom STA) - have to, since disabling them disables the wireless. 

As a result of this (this is my best guess), conky's built-in variables (wireless_*) do not return any values. Neither does 'cat /proc/net/wireless' or 'iwconfig eth1'. The only command that gives usable values is 'sudo iwconfig eth1'. So I added an exception for 'iwconfig' in sudoers and whipped up the Perl script above.

---

