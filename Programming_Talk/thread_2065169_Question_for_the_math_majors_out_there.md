---
title: "Question for the math majors out there"
date: 2012-10-01
forum: Programming Talk
---

### Post by ofnuts on 2012-10-01
I need to measure the duration of some activity in our application. I have logs with start and end times, unfortunately only to the second while the activity is likely much shorter.

Of the 70000 pairs of times collected, only 200 have start and end times that do no fall in the same second (but that fall in successive seconds).

Can I infer that the activity takes an average of 1/350 (200/70000) of a second?

---

### Post by Vaphell on 2012-10-01
not a math major but i'd say that's reasonable assuming constant time and uniform distribution.

---

### Post by trent.josephsen on 2012-10-01
I didn't spend much time on this, but one concern that comes to mind is whether the operations are consecutive, and if so, whether you're concerned about accidentally measuring the overhead of tearing down after one activity and starting up for another. I'm imagining a situation where when each activity N begins, say, about 50ms after activity N - 1 finishes up. If each activity takes around 30ms by itself, you'd measure the entire thing as 80ms, which may or may not be a problem.

If each operation can happen at any time during a second, independent of the others, then I think your inference is sound, but I don't have a proof on hand...

---

### Post by PaulM1985 on 2012-10-01
It seems reasonable.

Are you able to programmatically force your application to carry out the same task many times over and record that duration?

```

long startTime = getTime();
for (int i = 0; i < 100000; i++)
{
   testfunction();
}
long endTime = getTime();

```

Paul

---

### Post by StephenF on 2012-10-01
Some computers will have the CPU throttle down when idle then go faster when under load. This is a power management feature which might explain why you get more efficiency in subsequent seconds.

```

long startTime = getTime();
for (int i = 0; i < 20000; i++)
{
   testfunction();
   testfunction();
   testfunction();
   testfunction();
   testfunction();
}
long endTime = getTime();

```
This revised code only does the loop increment and test on every fifth run of testfunction. The idea is to reduce the time contribution of the loop.

---

