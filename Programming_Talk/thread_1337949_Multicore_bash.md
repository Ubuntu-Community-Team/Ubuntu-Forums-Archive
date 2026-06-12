---
title: "Multicore bash?"
date: 2009-11-25
forum: Programming Talk
---

### Post by shaggy999 on 2009-11-25
I have a simple bash script that I execute on every subdirectory of a given directory. This script churns for awhile on each directory and maxes out one of my four cores. This is how I run it:

find . -type d -exec scriptname '{}' \;

This is really inefficient because the script is cpu-bound and not io-bound. It would be really awesome to be able to run four copies of this script at once on each of my cores. Theoretically this should bring the total elapsed compute time to 1/4 of what it is now. Right now it takes about 8 hours to churn through all the data.

Does anybody know of any simple programs that would assist me with this or suggestions on how to write a bash script that is multi-core aware?

I've got a general idea for a script that would go something like this:

```

DIRS=`find . type d`

MAX_THREADS=4
THREADS=0
SLEEP_TIME=10

while ('$DIRS Contains data')
{
    if (THREADS < MAX_THREADS)
    {
          Spawn thread with line from DIRS
          THREADS++
    }
    else
    {
          sleep SLEEP_TIME
    }
}

```

Obviously, this is all pseudocode. The biggest hurdle I'm trying to get past is figuring out how to spawn new processes and figure out how to get notified when a process finishes so I can decrement the thread count. Perhaps this is too much to ask of bash and I should move to python or something.

---

### Post by stylishpants on 2009-11-25
One little puzzle piece that might be useful is xargs.

Read the man page and look at the "-P" option, which lets you specify a maximum number of processes to spawn.

---

### Post by shaggy999 on 2009-11-25
oh, wow! I had no idea xargs supported multi-process! I'm gonna go try that.

---

### Post by shaggy999 on 2009-11-26
Wow, that was so incredibly simple!! I'm very happy, I just had to pipe find's results to xargs instead of executing from within find. :)

For others, here's the way the commandline changed:

Original:
```

find "$1" -type d -exec ./scriptname '{}' \;

```

New:
```

find "$1" -type d -print0 | xargs -0 -n 1 -P 4 ./scriptname

```

The -print0 in the find command and -0 option in xargs help to deal with filenames that have spaces and other special characters in them. The -n 1 refers to how many arguments to pass per process, and -P 4 is how many processes to execute concurrently.

Oh, and for a small set of directories the time difference was 1min20secs vs 19secs :)

---

### Post by mo.reina on 2009-11-26
you mean that by running 4 processes the 4 cores of your cpu are utilized?  no other special coding is needed?

---

### Post by shaggy999 on 2009-11-27
> **mo.reina said:**
> you mean that by running 4 processes the 4 cores of your cpu are utilized?  no other special coding is needed?

Yes. The kernel is smart enough to schedule each of the processes on separate cores. It had all 4 cores pegged @ 100%. It has brought my total processing time down to 25% of what it originally was. I am so incredibly happy with the performance that I'm taking second looks at other scripts I run routinely to see if I can do the same for them.

I was initially concerned that I would have to manually set the cpu affinity, but that is not the case. :)

---

