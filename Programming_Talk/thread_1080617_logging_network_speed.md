---
title: "logging network speed"
date: 2009-02-25
forum: Programming Talk
---

### Post by t0p on 2009-02-25
I often use a 3G cellphone to connect my computer to the internet.  Connection speed is extremely variable, and I would like to collect the data as to what the speed is at different times of the day.  I've installed the utility **iptotal**, which can get this data for me.  I figured I could put in a cron job to run iptotal on the interface in question at regular intervals.

The time at which iptotal runs is also data that interests me.  I don't know how best to collect this data in a useful way.  I could just run **date** at the same time and collect the times in a text file. But I thought maybe it would be more useful to store all the data (time and connection speed) in a database.  Thing is, I don't know how to do this.  I have **isql**, **iusql**, **sqlite** and **sqlite3** installed at the moment.  Would I need something else?

I need some pointers as to the methods needed to do this.  I have basic bash scripting knowledge.

---

