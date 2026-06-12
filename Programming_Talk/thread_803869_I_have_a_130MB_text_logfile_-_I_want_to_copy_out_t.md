---
title: "I have a 130MB text logfile - I want to copy out the last 1k lines or so - how?"
date: 2008-05-22
forum: Programming Talk
---

### Post by spaceballl on 2008-05-22
Hi all,

I'm slowly getting more and more familiar with the linux command line. Maybe you can help me with this. I've done a lot of searching on google and couldn't quite get what i was looking for. Here's the situation. I'm SSHing into a remote machine and there's a log file. It is 2522924 lines long, so editing it in VI can be sluggish. I want to copy out about 1k lines of the log - how do I do it? This is on a remote machine and my connection is too slow to download the file so I need to use only the command line.

So, this is what I was thinking. I made a duplicate log_file and then opened it w/ VI. I found the line where I wanted to start copying. I was going to use the command xxxxxxdd to just get rid of the first gajillion lines, but it is SO slow - like, it takes forever and still doesn't finish deleting all the lines - the window seems to hang so I need to open a new one.

I've looked at the "cat" command and it doesn't seem like I can cat to a new file, starting at a certain line - help! Thanks!

---

### Post by WW on 2008-05-22
You can use the **tail** command:
```

$ tail -n 1000 logfile > /tmp/last1000lines

```

---

### Post by spaceballl on 2008-05-22
Aaaah thank you - I'm trying it now. Man this thing is slow, but i'm hoping it doesn't hang.

---

### Post by CptPicard on 2008-05-22
Check out the commands "head" and "tail".

---

### Post by geirha on 2008-05-22
And as a side note, you might want to consider [log rotation](https://help.ubuntu.com/community/LinuxLogFiles#head-a5a09beac9bb4bbf12cf5e7a4f854dc5ae1f16e8) ;)

---

### Post by drubin on 2008-05-22
tail on a 130mb logfile should be fine,

I often for work tail logfiles that are over a gig!

---

### Post by deuce868 on 2008-05-22
yea, our log files are >2gb per day per server and I head/tail them all the time. Might run for a sec, but it'll be ok.

---

### Post by spaceballl on 2008-05-23
Thanks, guys - tailing worked like a champ. Normally our log files are smaller, but we're trying to fix a bug so we had debugging messages turned up all the way - thx!!

---

