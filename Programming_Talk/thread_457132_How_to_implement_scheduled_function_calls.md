---
title: "How to implement scheduled function calls"
date: 2007-05-28
forum: Programming Talk
---

### Post by Laterix on 2007-05-28
I need to implement such a system that invokes method calls at the specific date and time. For example, let's say that I want to execute method **foo()** at **2007-11-03, 11:32:10**. How should I implement this kind of system. Should I use cron somehow or a thread that sleeps (possibly a very long time) and then executes.

I use Python, but I think that this is not programming language related question as much as it is algorithmic.

At the moment, the best idea I have is to create a new thread, set when function should be calld, calculate time difference from current time and sleep that time difference in thread.

---

### Post by seamless on 2007-05-28
Could you give a little more information about what it is you exactly want to do with the funciton call? Blindly guessing not knowing what you are doing I would say Cron would be the route to take. If you are doing something like a mail checking application or something similar then Cron would not be a good way to go.

---

### Post by Frosty Cold Drink on 2007-05-28
> **Laterix said:**
> I use Python, but I think that this is not programming language related question as much as it is algorithmic.

At the moment, the best idea I have is to create a new thread, set when function should be calld, calculate time difference from current time and sleep that time difference in thread.

Disclaimer: I don't do any real time programming.

There isn't a 100% guarentee this will happen on time. Depending on how specific you need to get, and how important it is that the code is run at he proper time, you may want to wake up more often and check how things are going.

As an example, cron wakes up once a minute, as that is the resolution it provides.

Perhaps you can sleep for a fe whors to get you into the ballpark, but when you are approaching go time you should consider waking up every few minutes, then every second when you are very close.

Of course, all of this depends on how important it is to actualy run at the schedule time. If its critlcal, and you need an RTS, then the anwsers are completely different.

---

### Post by Laterix on 2007-05-28
Thanks for the answers. I'm planning to do DVB-recorder. So it needs to be pretty accurate. I thought about that "checking" strategy that would get more intense when getting closer to recording time. But I can't see, why that would be better than calculating the time to sleep. So I'm thinking something like this:

```

class DVBRecorder(threading.Thread):
   run(self):
      time.sleep(calculate time from current time)
      self.startRecording()

```

---

### Post by Frosty Cold Drink on 2007-05-28
> **Laterix said:**
> Thanks for the answers. I'm planning to do DVB-recorder. So it needs to be pretty accurate. I thought about that "checking" strategy that would get more intense when getting closer to recording time. But I can't see, why that would be better than calculating the time to sleep. So I'm thinking something like this:

```

class DVBRecorder(threading.Thread):
   run(self):
      time.sleep(calculate time from current time)
      self.startRecording()

```

As far as I know (note my previous disclaimer) a "more important" process may get more processor time, and your thread may not be woken up on time. I don't know the rules by which the kernel scheduler operates, but I'd bet threads constantly in queue would have a better chance of getting woken up on time than something dormant.

Of course if you don't anticpate resources being scarce it wouldn't really matter.

---

