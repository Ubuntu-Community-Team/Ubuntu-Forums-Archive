---
title: "Script to help check interface and reboot if not up"
date: 2009-12-07
forum: Programming Talk
---

### Post by zappadragon on 2009-12-07
So I am running an IPCop firewall and it works great other than dropping the connection from time to time. I have read that Smoothwall offered a reboot if connection not up within 5 minutes setting. Unfortunitly IPCop does not have this feature and I am trying to write a script to ping every so often (say a interface or website even) and if its not up then send a shutdown -r now command. Is there a simple way or script to do this? Any help would be great.

Thanks

---

### Post by zappadragon on 2009-12-07
maybe something like this:

ping -i 300 [www.google.com](www.google.com) (pings google once every 5 minutes)

But if a ping fails:

shutdown -r now (this would reboot the firewall)

I am just not sure how to do it.

I also was thinking of changing the interval to like 120 and if the ping fails 3 times send the reboot. 

Is anyone good at writing something like this?

Thanks

---

### Post by zappadragon on 2009-12-09
Anyone?

---

### Post by mo.reina on 2009-12-09
```
#!/bin/bash

counter=0
while true; do
	result=$(ping -c 1 www.google.com)
	packet=$(echo $result | grep -o "[0-9] received" | awk '{print $1}')
	[ $packet == 0 ] && counter=$[$counter+1]
	sleep 300
	[ $counter == 3 ] && `shutdown -r now`
done

```

will ping once every 300 seconds... if you want to change the interval change the value after **sleep**.
will shutdown after 3 timeouts

---

