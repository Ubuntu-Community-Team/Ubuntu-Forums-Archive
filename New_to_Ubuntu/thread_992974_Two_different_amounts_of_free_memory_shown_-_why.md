---
title: "Two different amounts of free memory shown - why?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by kajman on 2008-11-25
When I check the amount of memory using top or free command (both give the same result) I see this:

             total       used       free     shared    buffers     cached
Mem:       2074536    2001924      72612          0      72132    1355416

But when I look at the system monitor values, I see that only ~25% of my memory is used up (560mb).

Where does this huge differences come from and which of the values is correct? Why is this happening?

I use Ubuntu 8.04 now, but i remember it was the same on Ubuntu 8.10.

---

### Post by Paqman on 2008-11-25
Forget the top line of that output, take a look at the second line. What does it say?

---

### Post by kajman on 2008-11-25
total       used       free     shared    buffers     cached
Mem:       2074536    1977836      96700          0      39924    1337496
-/+ buffers/cache:     600416    1474120
Swap:      2618552      40108    2578444

this is the whole output of free command. So is the second line the REAL amount of my used/free memory? Can anyone explain to me what do those lines are all about?

---

### Post by JohnFH on 2008-11-25
The confusing answer is that they are both correct.  One value (the system monitor value) only reports memory as used by applications, whereas the 'free' command also gives details of memory used for disk cache.  The memory used as disk cache is still available to the system if it needs it, so essentially it is still considered 'free'.

Does that make sense to you?

---

### Post by JohnFH on 2008-11-25
> **kajman said:**
> total       used       free     shared    buffers     cached
Mem:       2074536    1977836      96700          0      39924    1337496
-/+ buffers/cache:     600416    1474120
Swap:      2618552      40108    2578444

this is the whole output of free command. So is the second line the REAL amount of my used/free memory? Can anyone explain to me what do those lines are all about?

The second line is the one to pay attention to (+/- buffers/cache).  It reports the memory available to the system, ignoring the memory used as cache and buffers.  In your system, 600Mb are used with nearly 1.5Gb free.  Most of that free memory is still being made use of, but is available if needed.

---

### Post by unutbu on 2008-11-25
JohnFH, what does the '-/+' mean?
Using kajman's example, is the output of free saying that

1977836KB of RAM is being used for applications + buffer cache, and
600416KB of RAM is being used for applications only?

Thus, is 1377420KB (=1977836-600416) of RAM being used for buffer cache? 

And am I correct in believing that memory used for applications must be kept in either RAM or swap, but  memory used for buffer cache (such as recently accessed files) is good for performance but can be discarded at any time?

Finally, in the first line of free, I see a column for buffers and a column for cached. What's the difference? 

The web page
[http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)
makes it sound like there is only one thing called buffer cache...

---

### Post by kajman on 2008-11-25
Thanks JohnFH, that clears a little bit :) Got to think it through, it sounds rather confusing.

---

### Post by JohnFH on 2008-11-25
> **unutbu said:**
> JohnFH, what does the '-/+' mean?
Using kajman's example, is the output of free saying that

1977836KB of RAM is being used for applications + buffer cache, and
600416KB of RAM is being used for applications only?

Thus, is 1377420KB (=1977836-600416) of RAM being used for buffer cache? 

And am I correct in believing that memory used for applications must be kept in either RAM or swap, but  memory used for buffer cache (such as recently accessed files) is good for performance but can be discarded at any time?

Finally, in the first line of free, I see a column for buffers and a column for cached. What's the difference? 

The web page
[http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)
makes it sound like there is only one thing called buffer cache...

You've got it all exactly correct!  

Some explanations ... the +/- just means that line is reporting the used and free memory after taking the 'buffer cache' memory into account (ie. ignoring it!).  So the two values in that line are used memory and free memory.

Strictly speaking a buffer is something that has yet to be "written" to disk. A cache is something that has been "read" from the disk and stored for later use.  Sometimes the terms are used interchangably.

---

