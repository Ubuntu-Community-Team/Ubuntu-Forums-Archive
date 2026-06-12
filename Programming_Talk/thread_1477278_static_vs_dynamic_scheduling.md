---
title: "static vs dynamic scheduling"
date: 2010-05-08
forum: Programming Talk
---

### Post by cybo on 2010-05-08
in my OS class we were covering scheduling (just skimmed over the topic) but professor really never really explained the difference between static and dynamic scheduling? all i know is that static means that nothing changes, and dynamic means that something changes. i'd appreciate the if anyone could explain what those "nothing" and "something" mean.

thanks

---

### Post by Zugzwang on 2010-05-08
Indeed, the question you are asking is not answered in the "scheduling (computing)" wikipedia article. So I'll try that here, as the question doesn't seem to be precisely homework:

A static schedule is some kind of list containing the order of the processes and the durations in which they are scheduled. For example, a simple communicating device could have the following static schedule in pseudo-code:
```

repeat forever:
   execute task 1 for 10 ms
   execute task 2 for 20 ms
   execute task 1 for 5 ms
   execute task 3 for 15 ms

```

This is a static schedule. It's just like the bus schedule: Task three is executed for 15 ms every 50 ms. The schedule never changes, even if task 1 has nothing to do and task 2 is missing its deadlines.

On the other hand, when performing dynamic scheduling, whenever the scheduler decides which task to execute next (and for how long), it looks at a list of tasks requesting the processor at that point in time and then decides which to use next. Examples are the "earliest-deadline first" scheduler. Here, the schedule changes if some task has nothing to do and does not request resources.

There are a couple of books on embedded systems where you can read more about that.

---

