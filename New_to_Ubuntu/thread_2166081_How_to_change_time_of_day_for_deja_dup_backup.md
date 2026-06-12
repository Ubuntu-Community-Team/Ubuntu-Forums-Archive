---
title: "How to change time of day for deja dup backup?"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by Wadcutter on 2013-08-07
Does anyone know how to control the time of day for daily backups? Deja dup doesn't seem to offer that option, only the choice of daily, weekly, monthly etc backups. I looked thru the Duplicity manual but couldn't find (may have missed) a command to change the time. Right now it backs up daily upon startup, but I would prefer it back up some time in the evening after a day's work. If I can't change the time, I can always do a manual backup at day's end and change the automated ones to weekly so I won't be filling my drive with 2 backups per day. But if anyone knows how to change the time, I would appreciate it. I'm running Ubuntu 12.04. Thanks

---

### Post by Jonathan Precise on 2013-08-07
Hello [COLOR=#000000]Wadcutter!

First, disable automatic backups in Deja dup

Then enter the following command:

```
crontab -e
```

Choose the option that says something like:

[/COLOR]```
[COLOR=#000000]2) nano[/COLOR]
```[COLOR=#000000]

or

[/COLOR]```
[COLOR=#000000]2) /bin/nano[/COLOR]
```

add the following line at the bottom:

```
00 20 * * * deja-dup --backup
```

That should backup your files every day at 08:00 PM.

Then press CTRL+O, and CTRL+X to save and exit.

If you need to backup at any other time, reply to me.

---

### Post by Wadcutter on 2013-08-08
Thank you, Jonathan Precise. 08:00 PM is good. I'll give it a try.

Doesn't seem to work for me. Tried it with different times (like 15  15 * * * deja-dup --backup - for 3:15 pm) so that I could test it right away instead of waiting until 20:00 hrs to see if it would work ( as I had done for two previous days). No dice. Nothing.
I've posted in the beginner section for a reason--I don't know much. But it seemed like if I created a file as it claimed, I should be able to find it. It showed something each time like /tmp/crontab.Atkxq]/crontab but I've never been able to find any files like that in the tmp folder.

---

