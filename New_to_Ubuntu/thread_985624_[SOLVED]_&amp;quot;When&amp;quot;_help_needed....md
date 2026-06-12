---
title: "[SOLVED] &amp;quot;When&amp;quot; help needed..."
date: 2008-11-17
forum: New to Ubuntu
---

### Post by I wanted to leave on 2008-11-17
I've installed "when' as a terminal calendar which I plan to use in conjunction with conky to display the calendar on the desktop, and hopefully also display appointments etc. 

The format for adding entries is apparently 

```
w=2008 November 19, 7.30PM Job Interview
```

However, when I try to run 'when' via a terminal, I get the following output:

```
bra10n@bra10n-desktop:~$ when
Prototype mismatch: sub Terminal::__LONG_MAX__ () vs none at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
Constant subroutine __LONG_MAX__ redefined at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
****** nested parentheses or other syntax error: w= 2008 november 19th wednesday
******  w= 2008 november 19th wednesday, 3.30PM - Job Interview
```

Here is the code from line 291 above
```
unless (defined &__LONG_MAX__) { sub __LONG_MAX__ { 2147483647 } }
```

It seems the above problem prevents the command 'when e' which apparently appends appointments to the calendar. When I run 'when c' which displays the calendar, I see no appointments, just the current date highlighted.

What am I doing wrong?

---

### Post by I wanted to leave on 2008-11-18
:confused: Bump!

Has anybody any suggestions regarding this?

---

### Post by hyper_ch on 2008-11-18
it is not appreciated if you bump your threads within 24h after your last reply.

---

### Post by Exic on 2009-01-24
Why is this solved? I see no solution...

First... "w=" is the syntax to set a weekly appointment.

e.g. "w=fri, go somewhere"


After updating to intrepid I got the same message:

```
Prototype mismatch: sub Terminal::__LONG_MAX__ () vs none at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
Constant subroutine __LONG_MAX__ redefined at /usr/lib/perl/5.10/_h2ph_pre.ph line 291.
```

Which is annoying because I have when in my .bashrc so the message appears every time I start a terminal. Doesn't seem to affect the programs functionality though.

Found a solution: [https://bugs.launchpad.net/ubuntu/+source/perl/+bug/303765](https://bugs.launchpad.net/ubuntu/+source/perl/+bug/303765)
The patch is: Just remove line 291 of the named /usr/lib/perl/5.10/_h2ph_pre.ph... (and 290 if you like ;) ).

Best regards

---

