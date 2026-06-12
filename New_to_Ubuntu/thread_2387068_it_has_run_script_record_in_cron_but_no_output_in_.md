---
title: "it has run script record in cron but no output in folder"
date: 2018-03-14
forum: New to Ubuntu
---

### Post by zerop2 on 2018-03-14
configured crontab every 15 minutes

it has run script record in /var/log/cron but no output result in folder 

however it can run standalone having output
/root/checklog.sh

---

### Post by TheFu on 2018-03-14
By default, cron jobs email output.  You need to setup an MTA to send email or otherwise configure cron to do something else.  I setup postfix as a "satellite system" and forward all email to my main email server on the network.

---

### Post by zerop2 on 2018-03-14
No, not email script, 
i run my checklog.sh which is to mkdir directory and clear directory files and filter keywords of syslog and saved into /root/Error
standalone it can run, but after scheduled with cron, there is no files in the folder /root/Error

---

### Post by steeldriver on 2018-03-14
We can't possibly know the issue unless you show us (1) your cron entry and (2) the relevant portions of your script

---

### Post by TheFu on 2018-03-14
> **zerop2 said:**
> No, not email script, 
i run my checklog.sh which is to mkdir directory and clear directory files and filter keywords of syslog and saved into /root/Error
standalone it can run, but after scheduled with cron, there is no files in the folder /root/Error

Cron doesn't have much environment.  Environment variables aren't set that are commonly set for a normal login.  This is the most common issue with cron scripts that don't work. Plus, being able to see the emailed cron output often will show the issue - especially if the script is run in verbose mode (#!/bin/bash -x)

Seeing the script would help as steeldriver suggests.

---

