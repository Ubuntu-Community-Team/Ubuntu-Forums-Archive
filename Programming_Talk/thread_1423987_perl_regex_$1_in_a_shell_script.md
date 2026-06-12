---
title: "perl regex $1 in a shell script"
date: 2010-03-07
forum: Programming Talk
---

### Post by king vash on 2010-03-07
I am writing a rename script to deal with some bad naming of my TV shows.

I pass the name of the TV show and the folder into a shell script
I cd to that folder and run a couple rename commands (adding show name...)

My issue 

```

rename "s!^([0-9]{3}) - !$show - $1 - !" *.avi

```
if I use double quotes for my rename regex I can use variables from the shell level ie. $show but then the $1 will be the first parameter passed to the shell script not the episode number (the three numbers in matched at the beginning of the line).

so I used \1 instead of $1, but then I get this nasty message.

"\1 better written as $1 at (eval 1) line 1."

If I use single quotes I can use $1 for the matched episode number but not $show.
```

rename 's!^([0-9]{3}) - !$show - $1 - !' *.avi

```

any ideas?

do I just deal with the error message cluttering up my screen?

---

### Post by diesch on 2010-03-07
```
rename "s!^([0-9]{3}) - !$show - \$1 - !" *.avi
```

---

### Post by king vash on 2010-03-09
solved the problem, thanks!

---

