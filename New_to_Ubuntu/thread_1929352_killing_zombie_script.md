---
title: "killing zombie script"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by duceduc on 2012-02-21
On my old server (Ubuntu 10.4), I had 1 or 2 zombie process that will crept up from time to time. I have been searching for a way to kill it permanently and never found a real solution. So I just left it like that since it was only 1.

Now, I have upgraded my pc and my server to ubuntu 11.10, I noticed there are over 9000 zombie process that will show up. Since I do not know how to go about solving it, I found a script to kill zombie process by running a cronjob. This script has a 'kill-9' which I also read it is bad to use. 

> #!/usr/bin/env python

##Killing zombie process ##

	for each in `ps auxww | grep Z | grep -v PID | awk ‘{print $3}’`; 
		do for every in `ps auxw | grep $each | grep cron | awk ‘{print $2}’`; 
			do kill -9 $every; done; 
				done

Is this ok to use? How often should I check it?

---

