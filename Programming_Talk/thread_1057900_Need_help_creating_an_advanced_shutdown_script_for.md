---
title: "Need help creating an advanced shutdown script for powersaving?"
date: 2009-02-02
forum: Programming Talk
---

### Post by BassKozz on 2009-02-02
My NAS box (see sig) is a power-hungry beast, and while I know I could build a VIA or ATOM based system to do simple NAS tasks and replace the power-hungry p4, that would cost money, and I am trying to pinch-a-penny in these economic times...

So I usually leave the NAS box on 24/7 but I am starting to feel bad about that, and my electricity bill is making me feel it :p
But I need to leave the NAS on at night because it is my media server for my TV's (XBMC)...
So I created 2 crontab lines:
```
# Weekdays
30 02 * * 1-5 /sbin/shutdown -h now
# Weekends
30 04 * * 6-7 /sbin/shutdown -h now

```
This is great, I just turn the NAS on in the morning when I need it... but this isn't the optimal setting because I usually go to sleep well before 2:30am on weeknights and before 4:30am on weekends, however there are a few nights that I stay up past my bedtime :p  So I wanted to account for that in crontab.  But on average I would have to say I usually go to sleep about 2-3hrs before these times.

So I gots-ta-thinkin and I figured that there must be a better way to handle this with a script, and after a quick question to the forums about finding out [who is using samba]("http://ubuntuforums.org/showthread.php?t=1057630") JillSwift replied with:```
net status shares parseable
``` Which seems perfect for what I need...
Now I have little-to-no skills in scripting, but if someone wouldn't mind helping me out in the name of '[going green]("http://www.gogreeninitiative.org/")' it would be greatly appreciated.

The goal is to create a shutdown script that first checks to see if anyone is using any of the samba shares using 'net status shares parseable', if not shutdown, if so wait 5 minutes and check again.
Here is my rough draft:
```
loop
    if 'net status shares parseable' = null
        shutdown -h now
        Exit Loop
    else
        Pause 5minutes

```

Alternatively, if using samba share activity as a guide isn't a sound option, another option would be to check and see if a specific set of computers is on or off using ping (I have all of my computers on my LAN setup with STATIC IP's so I could just ping their ip's to see if they are active).
For example```

loop
    if 'ping 192.168.1.112' AND 'ping 192.168.1.114' = Destination Host Unreachable
        shutdown -h now
        Exit Loop
    else
        Pause 5minutes  

```

This way with the script I can set it to run in crontab at an earlier time (say 1am on weeknights and 2am on weekends) to shutdown my NAS.
Does anything like this exist already?
Is there a better way to handle this, if so I am all ears?
If not, Can someone lend a hand with this or point me in the direction to get some assistance?

Thanks in advance for any/all help,
-BassKozz

---

### Post by BassKozz on 2009-02-03
Solved: [http://www.linuxquestions.org/questions/linux-general-1/need-help-creating-an-advanced-shutdown-script-for-power-saving-701727/](http://www.linuxquestions.org/questions/linux-general-1/need-help-creating-an-advanced-shutdown-script-for-power-saving-701727/)
See Also: [http://basskozz.wordpress.com/2009/02/03/advanced-shutdown-script-powersaving/](http://basskozz.wordpress.com/2009/02/03/advanced-shutdown-script-powersaving/)

---

### Post by bapoumba on 2009-02-03
Just saw the report, do you still want it moved to General Help ?

---

### Post by BassKozz on 2009-02-03
> **bapoumba said:**
> Just saw the report, do you still want it moved to General Help ?

Nah, that's alright, Thanks anyways bapoumba ;)

---

### Post by bapoumba on 2009-02-03
Welcome !
Glad to see you got it to work :)

---

