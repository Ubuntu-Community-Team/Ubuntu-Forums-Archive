---
title: "using shell script to EOF (control + d)?"
date: 2006-06-04
forum: Programming Talk
---

### Post by pasdar1 on 2006-06-04
Hello,

I am trying to write a shell script that will write a bunch of "at commands" to schedule some tasks (there are changing times, so I am using "at" instead of "cron jobs").  For example, if in my shell script I write:

at 12:04
mplayer something.mp3

and if I execute this, the computer will say:

at>

becuase it wants me to continue entering more commands, or to press "control d" to end it.  But I want the shell script to also include a "control d" so that I can list multiple

at XXX
program job1

at XXY
program job2

I hope I was clear, so how can I tell the shell script to press "control d" so that the computer knows to stop asking for more commands to execute at the specified time?

Thanks in advance!

---

### Post by Arndt on 2006-06-05
[QUOTE=pasdar1]Hello,

I am trying to write a shell script that will write a bunch of "at commands" to schedule some tasks (there are changing times, so I am using "at" instead of "cron jobs").  For example, if in my shell script I write:

at 12:04
mplayer something.mp3

and if I execute this, the computer will say:

at>

becuase it wants me to continue entering more commands, or to press "control d" to end it.  But I want the shell script to also include a "control d" so that I can list multiple

at XXX
program job1

at XXY
program job2

I hope I was clear, so how can I tell the shell script to press "control d" so that the computer knows to stop asking for more commands to execute at the specified time?

Thanks in advance![/QUOTE]

It mystifies me a little why 'at' continues to ask for input although the script is finished, but no matter - I have a solution: use the << construction in the shell (a so-called "Here Document").

```
at XXX <<EOF
program job1
EOF

at XXY <<EOF
program job2
EOF
```

To learn more about <<, see the man page for 'bash'.

---

