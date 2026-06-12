---
title: "Beginner Project"
date: 2009-12-06
forum: Programming Talk
---

### Post by furialis on 2009-12-06
I'm trying to teach myself programming and I need a first project. The examples from the books I have are more about teaching concepts than implementing them. For me to really "get it" I think I need something tangible. 

I have an idea for a program that searches for lottery results for a given number of days prior to today, figures out what numbers were drawn and gives me the frequency the numbers were drawn in this format
```

1 (0)
2 (1)
3 (0)
4 (5)
5 (25)
and so on..

```

I plan on using Python. Is this project too ambitious? My guess is that it would work using the "Search for winning numbers" link onthis website. [http://www.flalottery.com/inet/games-fantasy5Main.do](http://www.flalottery.com/inet/games-fantasy5Main.do) I'm guessing that the numbers are in some table that I could read from. Is that right?

Suggestions?

---

### Post by mo.reina on 2009-12-06
[http://ubuntuforums.org/showthread.php?t=783387&highlight=laroza]("http://ubuntuforums.org/showthread.php?t=783387&highlight=laroza")

---

### Post by phrostbyte on 2009-12-07
No that is not hard. I would first program this with mock data (eg. import random). That way you generate random numbers from like 1-52 from instance and record the results. I think that would be 10-20 lines of code at most.

Getting data from a website and it's difficulty STRONGLY depends on the website. :) If they don't have a web services interface it's quite difficult.

---

### Post by OgreProgrammer on 2009-12-07
If you like visible tangible results, why not plot out the mandelbrot fractal?

Once you have that, you can learn a little gtk and use gtk widgets to change the parameters.

Pygame will let you plot the pixels and also save images to disk. It could be great fun.

---

