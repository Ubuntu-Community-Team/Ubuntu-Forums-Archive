---
title: "CPU Usage in percent"
date: 2015-10-05
forum: Programming Talk
---

### Post by Jran_Haugli on 2015-10-05
Hi!

I have been running around on the internet trying to find the ultimate command to get CPU Usage in percent. I found alot of results that works in some how, but how accurate are they?
Im looking for a command which shows active CPU usage, not a average result.

Have anyone found the ultimate command?

This is my current commands:

UPTIME: > cat /proc/stat | grep btime | awk '{ print $2 }'
CPU > grep 'cpu ' /proc/stat | awk '{usage=($2+$4)*100/($2+$4+$5)} END {print usage}'
RAM: > free | awk 'FNR == 3 {print $3/($3+$4)*100}'
HDD: > df /home | awk '{ print $5 }' | tail -n 1

(Im also looking for RAM and HDD)

Regards,
Haugli92

---

### Post by SeijiSensei on 2015-10-05
Run the "top" command.  It updates the statistics once per second.

Remember that CPU usage can vary dramatically from moment to moment depending on what the computer is doing.  Instantaneous CPU figures are pretty uninformative.

---

