---
title: "Auto restart Script"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by GoldenWing81 on 2013-05-29
Greetings,  

     First things first... I am rather new to writing bash scripts, and have been learning quite alot from friends of mine who have been assisting me in learning.  I currently have a little follow script running to monitor a log file.  It works very well and grabs the information I need, however I have one issue with it.  I would like it to automaticly clear the output terminal window at the end of each day, say midnight.  I have found some references to adding lines to try to have the script rerun itself but im concerned about an infinite loop.  

TLDR:  I have the following code that works well, & I want to get it to automaticly clear the terminal window screen every night at midnight. 

```
#!/bin/bash

logfile="/home/goldenwing/server.log"

clear
tail -F 2>/dev/null "$logFile" | perl -ne 's/(^.+) \[.+\] \[.+\]/\1/g; print if m/\</ or m/\>/ or m/Loading Player/ or m/Unloading Player/;'
```


Any help / assistance would be great, and thanks for the taking the time to read this.

-=GoldenWing=-

---

