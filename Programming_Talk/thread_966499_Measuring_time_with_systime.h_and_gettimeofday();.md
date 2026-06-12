---
title: "Measuring time with sys/time.h and gettimeofday();"
date: 2008-11-01
forum: Programming Talk
---

### Post by Calmatory on 2008-11-01
So, I am a bit lost, confused and frustrated thus I am not sure do I even know what I am asking/writing about but here it goes:

As you should already know, gettimeofday puts seconds + microseconds since 1st of jan 1970 to the timeval struct. 

Now, I have the seconds + microseconds since that date, but how on earth can I use them to measure time differences between two sets of seconds + microseconds?

The seconds value is huge(billion or so), and I am a bit concerned about dealing with it. 16-bit unsigned int should have boundaries of 65536 or so, so what is the way to deal with the value?

Storing two that huge values and getting the delta seconds, then delta microseconds and doing some calculation does not seem the best way. What I'd think as better way would be to trim the seconds value down and deal with the smaller values instead. How do I accomplish this? How do I convert from e.g. 40 seconds and 493294 microseconds to milliseconds?

Yes, I could multiply the seconds with 1000 to get the milliseconds and then divide the microseconds with 1000 to get milliseconds and try to measure the delta from that, but 1000 billion... :drool:

I tried googling, with no help. I thought this would be better place to ask rather than use IRC.

---

### Post by whoelse on 2008-11-01
Hi, I am a rewriting a program at the moment where the problem is solved that way:

> static struct timeval start_time;

void init_time() {
        gettimeofday(&start_time, NULL);
}

int64 get_time() {
        struct timeval t;
        gettimeofday(&t, NULL);
        return (int64) (t.tv_sec - start_time.tv_sec) * 1000000
                + (t.tv_usec - start_time.tv_usec);
}

Then I execute init_time() in the beginning and thats all.
Afterwards you can just calculate get_time_value_1 - get_time_value_2.

---

### Post by Calmatory on 2008-11-01
That returns microseconds, right? I'd only need precision of milliseconds, though that approach seems to be the best for that also. Where does the int64 come from? And how does the "static" infront of struct change a thing? :)

Just a bit inexperienced with C++. :)

---

### Post by whoelse on 2008-11-01
Sorry, just copied that stuff from my file.

Yes its microseconds. In the beginning you will always have microseconds, I can't think of any function to measure millisecs.

int64 is just long long: 

> typedef long long int64;

[Static variables explaination]("http://en.wikipedia.org/wiki/Static_variable#Static_Variables_as_Class_Variables")

---

### Post by Calmatory on 2008-11-01
Well, microseconds are fine also, I am just way more familiar with milliseconds. Just need to divide the microseconds with 1000. :)

EDIT: Got it working, just what I needed. Thanks! :)

---

