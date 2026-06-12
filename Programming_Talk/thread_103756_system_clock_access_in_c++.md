---
title: "system clock access in c++"
date: 2005-12-14
forum: Programming Talk
---

### Post by oldmanstan on 2005-12-14
how would i go about accessing the system clock in c++? right now i'm using the clock() and CLOCKS_PER_SEC constant to time how long an operation takes, but it seems that when i run it "nice" the time gets weird. so instead i want to read the system clock at the beginning then at then end and subtract the two for a total time.

any other method that would work would be fine too.

---

### Post by darth_vector on 2005-12-14
you can get the current time by #include'ing <time.h> and doing as follows:

time_t current_time=time(NULL);
...
time_t next_time=time(NULL);
//to calculate difference:
double difference=difftime(current_time,next_time);

---

### Post by toojays on 2005-12-15
I agree with darth_vector's suggestion, but would add that in ISO C++ you should #include <ctime> instead of <time.h>.

---

### Post by thumper on 2005-12-15
I'd take a look at boost::date_time and boost::timer.  Much nicer than dealing with time_t.

---

