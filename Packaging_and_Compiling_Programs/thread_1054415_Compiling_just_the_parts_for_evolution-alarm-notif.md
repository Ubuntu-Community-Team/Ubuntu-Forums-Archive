---
title: "Compiling just the parts for evolution-alarm-notify"
date: 2009-01-29
forum: Packaging and Compiling Programs
---

### Post by Rockiger on 2009-01-29
Hello,
there is a tendency to ged rid of evolution and replace it with thunderbird in this post: [http://ubuntuforums.org/showthread.php?p=6633123#post6633123](http://ubuntuforums.org/showthread.php?p=6633123#post6633123)

One problem is that if you uninstall evolution, there is no way to get notified anymore. 

Is it possible to just compile the parts that a neede for evolution-alarm-notify that you don't have to keep the rest of evolution?

I played around with the source code, but I couldn't find a way to just compile parts.

---

### Post by bruce89 on 2009-01-30
Since this part of Evolution depends on Evolution's appointment schedule thingy (technical name), even if you could isolate the alarm bit, it would need the Evolution backend to tell it what to do.

---

### Post by Rockiger on 2009-01-30
To bad.
Is there a programm how has the same function and watching the evolution-data-server?
If not, is it hard to write such a daemon? Maybe I could write this. After I finished my ongoing projects :)

Thanks for the help.

---

