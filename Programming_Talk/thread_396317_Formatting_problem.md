---
title: "Formatting problem"
date: 2007-03-29
forum: Programming Talk
---

### Post by LittleLebowski on 2007-03-29
I'm trying to copy and paste sscript written by a colleague on a Windows box and run it on a Solaris box.  I'm copying from a GEdit/Kedit opened .txt file and no matter what I do, it runs incorrectly.  I tried running dos2unix on the file.  Any ideas?  I'm running Feisty but this problem existed on Dapper as well.

---

### Post by Mirrorball on 2007-03-29
On Kate, you can go to Tools -> End of line and select Windows/DOS. You can also run a script to substitute "\n" for "\r\n" in this file.

---

### Post by LittleLebowski on 2007-03-29
Thanks for quick reply!  Unfortunately that didn't work.  Getting frustrated here.

---

### Post by WW on 2007-03-29
"It runs incorrectly" is a bit vague.  Give some more details.

---

### Post by LittleLebowski on 2007-03-29
It gives the proper results as in a grep for "FW" returns only "FW" results when ran from a Windows box or another Unix box aside from my Ubuntu box.  When run form my Ubuntu box it returns "FM and "FD."

How it should look:
[root@phantom: /tmp]# echo -n `mminfo -m -t '3/23/07' | grep FW | awk '{print $1}'` > wt
[root@phantom: /tmp]# for r in `cat wt`; do echo $r; done  | xargs -i@ mminfo -a @ | egrep "3/23|3/24|3/25|3/26" | awk '{print $1}' | sort | uniq
mminfo: no matches found for the query
mminfo: no matches found for the query
mminfo: no matches found for the query
mminfo: no matches found for the query
FW4092
FW4095
FW4096
FW4098
FW4099
FW4100
FW4102
FW4104
FW4106
FW4107
FW4108
FW4650

------------------------------------------------------------------------------------------------------------------------------------

  What it looks like from my box.

[root@phantom: /tmp]# echo -n `mminfo -m -t '3/24/07' | grep FW | awk '{print $1}'` > wt
[root@phantom: /tmp]# mminfo -a `cat wt` | egrep "3/24|3/25|3/26|3/27" | awk '{print $1}' | sort | uniq

FD4008
FD4009
FD4010
FM4123
FM4124
FM4125
FW4099
FW4100
FW4102
FW4104
FW4106
FW4107
FW4108
FW4109

---

### Post by Mr. C. on 2007-03-29
Oh my, that's convoluted.

You're going to have to provide us with a few lines of output from the mminfo command.

I have no idea what its output is.  Once you show that, we'll help with the rest.

MrC

---

