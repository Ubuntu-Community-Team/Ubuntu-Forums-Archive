---
title: "The year 2038 bug"
date: 2006-10-04
forum: Programming Talk
---

### Post by Rhubarb on 2006-10-04
It seems the (linux) world will enter a time tunnel in the year 2038 and spit us back to 1901.

[http://www.2038bug.com/index.html](http://www.2038bug.com/index.html)

I'm by no means a programmer (a teeny bit of vb, that's all), but I stumbled accross the 2038bug.com site.
It says that on Tuesday January 19th 2038 at 03:14:07 the UTC clock will 'clock' over to a negative value, making the resultant date end up on Friday December 13th, 1901 at 08:45:52

So on my half self-borked Dapper install (32bit, I'm unable to test 64bit) I decided to test it out.  Sure enough it worked, bought me back to 1901.
Decided I didn't like 1901 much so I set it back to the present.
Then I noticed my fans on my laptop spinning faster than usual.  There's a few unhappy threads consuming heaps of juice, namely evolution.
Evolution had decided that it wanted more than 500Megs of RAM and rising.

So, while 2038 is a fair way off, the main jist of the 2038bug.com site is for programmers to take this into account especially when programming for lifts / microwaves / DVD players / *nix powered nuclear bomb timers / anything that runs on long term chips for domestic use or whatever.

---

### Post by Engnome on 2006-10-04
Hopefully every critical system have by that time switched over to 64bit, problem solved.

More read at:
[http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)

Gotta love AOL, first ones to ever have a problem with this even before 2038 :D

> 
In May, 2006, reports surfaced of an early Y2038 problem in the AOLServer software. The software would specify that a database request should "never" timeout by specifying a timeout date one billion seconds in the future. One billion seconds after 21:27:28 on 12 May, 2006 is beyond the 2038 cutoff date, so after this date, the timeout calculation overflowed and calculated a timeout date that was actually in the past, causing the software to crash.

---

### Post by Rhubarb on 2006-10-04
Yep, I hope so too.  Maybe by then there'll be another platform change up to 128bit? ...

**In the mean time I suggest to anyone out there NOT to try this little trick out on their Linux box.**

As I just restarted after having heaps of memory leaks after trying this bug, now it seems my system log file is either borked or it's too big (maybe it tried to record events from the past in the future, then figured it didn't like time travel that much and gave up).

Still very much noobish ere, so I'm gonna re-install dapper - so close to Edgy's release date - arrrrgghhhh.
It's always good to know that I back up my system, phew.

---

### Post by 3rdalbum on 2006-10-05
I'm going to try it out on a Live CD, see what happens, and put the results into my blog.

To misquote something I read on the "Computer stupidities" website:

"I'm sure if Linux Toveralds can create Ubuntu all by himself, he can fix the Millennium Bug in time".

---

### Post by uk_sphinx on 2006-10-05
dosnt the bug work if you got 64 bit?
i want to try!!!!

[edit] dammn, guess time traveling was never meant to be for me. i had visions of terminator running through my head.

sarah conner??   come with me if you want to live!

---

### Post by Rhubarb on 2006-10-05
uk_sphinx, if you want to try 64bit for the 2038 problem, then I suggest you do what 3rdalbum is trying - boot off a live (64bit) DVD and see what happens.
**Just make sure you change the date back to the present BEFORE you boot into your local installation of Ubuntu.**
Let me know what happens, I'd be very interested to know.
3rdalbum, thanks for the ie crash script, that's kinda cool - I might use it on my personal website.  :-D

---

