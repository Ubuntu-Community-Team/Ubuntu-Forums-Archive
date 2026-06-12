---
title: "Resetting Network History at Midnight"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-08-19
Hi all

Is there a way that I can, either manually, or by cron, reset my network history at midnight each day. I can see my network history on system monitor, but if I disconnect from the network and then reconnect, system monitors history doesnt change.

Obviously I am needing more than just disconnecting and reconnecting. I mean I could shutdown the computer, or perhaps logout then login, but thats a pain.

Any thoughts?
Glenn.

---

### Post by lukeiamyourfather on 2013-08-19
Maybe use a different network monitor that has more intelligent history, like Cacti or something else that relies on RRDtool.

---

### Post by Cheesemill on 2013-08-19
It ***can*** be done by unloading and reloading the kernel module for your network card but this will take down your network connection.

Why are you trying to do this? If you just want to keep daily network usage stats then it would be far better to use something like vnstat.

---

### Post by lukeiamyourfather on 2013-08-19
> **Cheesemill said:**
> 
Why are you trying to do this? If you just want to keep daily network usage stats then it would be far better to use something like vnstat.

Nice, that looks less cumbersome than Cacti for just one machine.

---

### Post by deadflowr on 2013-08-19
> **Cheesemill said:**
> It ***can*** be done by unloading and reloading the kernel module for your network card but this will take down your network connection.

Why are you trying to do this? If you just want to keep daily network usage stats then it would be far better to use something like vnstat.
 +1 to using vnstat to do this.
it has a reset option.
personally, I'd make a small conky script just for vnstat/maybe other network activity and then learn how to make a script to have vnstat reset itself every midnight.

---

### Post by Cheesemill on 2013-08-19
> **deadflowr said:**
> +1 to using vnstat to do this.
it has a reset option.
personally, I'd make a small conky script just for vnstat/maybe other network activity and then learn how to make a script to have vnstat reset itself every midnight.

The reason I mentioned vnstat was that it keeps daily totals, negating the need for any sort of resetting at all.

---

