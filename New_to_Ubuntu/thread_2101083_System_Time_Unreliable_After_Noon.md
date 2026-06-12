---
title: "System Time Unreliable After Noon"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by ton8ty on 2013-01-03
Ubuntu 12.04 LTS recently installed on an older Toshiba laptop has time issues.  Gnome displays the correct time until noon and then the clock displays incorrect times.  Next morning, the time is correct.  Where do I start?

---

### Post by Frogs Hair on 2013-01-03
Hello and Welcome 

Are by chance using 24 hour format instead of 12. With 24 hour format 1:00 pm through 12.00 am becomes 13:00 hours through 0:00 hours.

Example: 2:15 pm becomes 14:15

Time settings should offer both 12 and 24 hour format.

---

### Post by ton8ty on 2013-01-03
System settings are set for 12 hour tme and to set the time automatically from the internet.  Prior to noon the time is correct and after noon it displays a valid time, but it is way off.  It's 7:04 PM now and the Linux clock says 1:00 PM.

---

### Post by steeldriver on 2013-01-03
Does the command-line 'date' command show the same problem?

```
$ date
```That will narrow it down a bit i.e. whether it is a processing / display issue in the gnome desktop, or an actual underlying problem with the system clock

---

### Post by ton8ty on 2013-01-03
Looks to be a problem with the system clock.  date command returns the same incorrect time as is displayed.

---

### Post by Wim Sturkenboom on 2013-01-04
What if you don't update the time from the internet? Your clock will / should slowly shift in that case. Or does it show the same symptoms? If it solves the issue, you can try to use a different time server; I'm not sure what to modify and therefore  leave the research to you ;) (read up on ntp configuration)

I assume you tried a couple of things, but what I would check
After reboot, enter the BIOS and check the time?
Does it come right in Ubuntu after reboot?
Does the time still change after 12pm, but at a slower rate?

And that's about how far I can help.

---

### Post by siddharth007 on 2013-01-04
Don't know if it is an internal clock problem,but you can always use '**'ntpdate" **package to synchronize the time.You can install it using this command
[B]apt-get install ntpdate

[/B]Better use it as a cronjob.Put this in the crontab file

[B]@reboot /usr/sbin/ntpdate -d NTP server ip/domain name

[/B]There are lots of ntp servers available for time sync.Check out this link 
[http://tf.nist.gov/tf-cgi/servers.cgi](http://tf.nist.gov/tf-cgi/servers.cgi)

Additionally,you can also check if your system was synchronized at reboot by redirecting the output of the above job to a file.To do this ,have the following entry in your crontab file

**@reboot /usr/sbin/ntpdate -d NTP server ip/domain name >> filename **
 
Cheers!!!

---

### Post by Fahim Abdun-Nur on 2013-01-04
For those inclined to use a GUI to set the NTP server: [https://help.ubuntu.com/community/UbuntuTime#Time_Synchronization_using_NTP](https://help.ubuntu.com/community/UbuntuTime#Time_Synchronization_using_NTP)

---

### Post by rburkartjo on 2013-01-04
ton you might want to try this
[http://www.howtogeek.com/howto/ubuntu/sync-your-system-clock-with-internet-time-servers-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/sync-your-system-clock-with-internet-time-servers-in-ubuntu/)

---

### Post by grahammechanical on 2013-01-04
> System settings are set for 12 hour tme and to set the time automatically from the internet.

How often does the OS check the internet for the correct time? Once and soon after booting?

Your machine could be loosing time because the battery powering the CMOS chip is loosing its charge and needs replacing. The OS resets the CMOS time but from then on the machine steadily looses time and this is shown in the OS.

Regards.

---

### Post by ton8ty on 2013-01-04
That's what I was afraid of.  Laptop is almost 10 years old and I don't even want to think of replacing the battery.

---

