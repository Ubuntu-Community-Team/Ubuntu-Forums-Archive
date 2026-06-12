---
title: "c# double -&gt;  ToString()"
date: 2008-08-15
forum: Programming Talk
---

### Post by muteXe on 2008-08-15
hiya,
I got this line:
string part2 = newLaunchTime.ToString();

where newLaunchTime is a double. i want part2 variable to be "30.0" if newLaunchTime = 30.0, but it's coming out as "30".  I really need to decimel place there.
Any ideas?

Cheers,
mute

---

### Post by realitybites on 2008-08-15
a wild method could be this:
check if there is a dot in part2, if not, add ".0" to it

---

### Post by muteXe on 2008-08-15
yeah i thought of that.  just wondered if there was a more elegant way.  Thanks for the reply though :)
I'll probably end up doing that tbh.

---

### Post by DavidBell on 2008-08-15
Googling "C# tostring format" gets me

```
 part2 = newLaunchTime.ToString("F1");
```

works on MS platform, not sure about mono

DB

---

### Post by muteXe on 2008-08-15
omg that worked!  thank you.
I've lost my googling skills :o

---

### Post by jimi_hendrix on 2008-08-15
i always use

double d = Convert.ToString(put int/float/double/whatever here);

---

