---
title: "Python threading question"
date: 2012-01-04
forum: Programming Talk
---

### Post by xaegis on 2012-01-04
Hello.
I am using Python 2.7.2 to write a game. I would like to know the best way have multiple working (terminal) windows in my program each showing different information.

I cant figure out how to use stdout, and make it explicit. I would like to know if I should use a thread or multi/child process.

Spawning a new process will not lock the main thread is this thinking correct?

Thank you in advance.

---

### Post by StephenF on 2012-01-05
If all you need to do is display status info...

```

logfile = open("/path/to/terminfo_1", "w")
print >> logfile "text to display"

```

To view it in real time open a regular terminal and type...
```

tail -f /path/to/terminfo_1

```

---

### Post by xaegis on 2012-01-05
> **StephenF said:**
> If all you need to do is display status info...

```

logfile = open("/path/to/terminfo_1", "w")
print >> logfile "text to display"

```

To view it in real time open a regular terminal and type...
```

tail -f /path/to/terminfo_1

```

Thank you for responding. I was hoping to get an IO/Buffer command but if this is the industry standard then I'll use the text file method. Isn't it rather heavy on the disk reading to have a loop calling that txt file so many times?

---

### Post by slavik on 2012-01-05
python does not have true concurrent threads ...

---

### Post by xaegis on 2012-01-05
So the recommendation is to use a looped thread to a serialized text file?
ok, thanks everyone.

---

### Post by StephenF on 2012-01-06
> **xaegis said:**
> Isn't it rather heavy on the disk reading to have a loop calling that txt file so many times?
That's not how it works -- the file in question is cached in RAM and tail is almost certainly putting the file into blocking mode meaning it won't even be given any CPU time until there is something to read.

---

