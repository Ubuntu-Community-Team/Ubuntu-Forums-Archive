---
title: "PowerShell scripting question - Measure-command"
date: 2010-03-08
forum: Programming Talk
---

### Post by derelict888 on 2010-03-08
I'm trying to use powershell to open a "large" spreadsheet (500KiB) from that is being shared from a colocated Domain controller. I'm trying to use ```
measure-command
``` within ps to measure the time it takes to open the file in excel but the only time its measuring is the time it takes to pass the command to excel. So I'm seeing times of 6ms but the actual file takes around 30s to full download and load in excel.

I'm doing this in powershell because I want to run this every 5min for a day or 2, and graph the results. See if there are any significant changes in load times - I have a small office in the UK that have been complaining about the share being "slow". So I need to get something quantifiable.

Just so I dont get the suggestion, downloading the file and then opening it locally is not the same as opening it from a share directly; the total time spent is way different (and not useful since my users won't be using this method). I'm doing it this way so I can get a real world number. Thanks for any help,

---

### Post by derelict888 on 2010-03-09
I'm closing this out I don't think I'll get any responses, this is the wrong place for PS expert talk  : )

---

