---
title: "Kernel panic in Ubuntu 12.10"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by AndrewS on 2013-01-06
Hello

I just installed 12.10 on my PC, no problems with the installation and it seemed fine.  For a while...  At intervals, I get a "kernel panic" and the system reboots after 30 seconds, after which is is fine until next time.  There doesn't seem to be any pattern to this, and I can't identify anything that triggers it.

I did a google search and found some suggestions that it might be a memory problem, so I ran the Memtest86 utility that is accessed from the grub menu.  Once it got to test #7, it started giving lots of red error messages.  So I thought that's it, I have some bad memory.  However, I ran other versions of Memtest86 (from various Ubuntu alternate install discs, openSuse liveCDs, even the standalone version, no memory errors detected.

I've attached a photo of the error message (not very good, taken with phone, but legible I think).

Any thoughts?

TIA

Andrew

---

### Post by Bashing-om on 2013-01-06
AndrewS; Hi !

I do not claim to be the sharpest tack in the box; But, if this were me I would start by examining my log files (get familiar with how they look):
Then I would blow the dust out of my box(do not forget to hold your fan blades from spinning):
then I would reseat my ram chips.

See what haps and look at the log files once more for any difference.


[INDENT][INDENT]my 2 pounds worth <== BDQ

[/INDENT][/INDENT]

---

### Post by AndrewS on 2013-01-07
Thanks, I'll give that a try, although I've never delved into log files before...

Andrew

---

### Post by Bashing-om on 2013-01-07
AndrewS;

Reading log files, pretty straight forward. The logs just relate what is going on. If there is a serious problem you will recognize it. Google is your friend; DuckDuckGo is pretty likeable too.

Most of the logs are located in /var/log/. The utility "log file viewer" is the easiest method to view the logs or the tool "less":
```
less /var/log/syslog
```see the manual page for full disclosure:
```
man less
```[INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by tgalati4 on 2013-01-07
Keep a terminal open with:

```
 tail -f /var/log/syslog
```

That will keep a running log that may show what is going on just before the panic.

Keep that window visible while you run other tasks so you can catch the crash.

Clean out the machine and reseat the cables and cards.  Also check the voltages in your power supply, either with a voltmeter or through the BIOS.

---

