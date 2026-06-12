---
title: "How to do this in Python?"
date: 2011-04-13
forum: Programming Talk
---

### Post by kevin11951 on 2011-04-13
How do I make Python listen for external input while running?  I don't mean "raw_input()", I mean where the program will be running happily, and then if I press "q" while its running, it quits...  Or something along those lines...

---

### Post by ssam on 2011-04-13
simplest method is to catch the KeyboardInterrupt exception that is generated when the user presses ctrl+C

```

try:
  code_that_takes_long_time()
except KeyboardInterrupt:
  print "stopped"
  clean_up()

```

otherwise you may need to look at a terminal handling library like curses.

---

### Post by kevin11951 on 2011-04-13
> **ssam said:**
> simplest method is to catch the KeyboardInterrupt exception that is generated when the user presses ctrl+C

```

try:
  code_that_takes_long_time()
except KeyboardInterrupt:
  print "stopped"
  clean_up()

```

otherwise you may need to look at a terminal handling library like curses.

So there is no way to do two things at once in Python?

---

### Post by ssam on 2011-04-13
you can use threads.

---

