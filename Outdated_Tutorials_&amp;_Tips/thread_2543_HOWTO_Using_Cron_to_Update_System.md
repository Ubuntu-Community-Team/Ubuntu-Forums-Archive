---
title: "HOWTO: Using Cron to Update System"
date: 2004-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by cacofonix on 2004-10-29
Here is a quick and hopefully informative way to use cron to update your system.

Cron is a scheduling program used often in many *nix distro to run automated tasks if your like me and are coming from windows it would equate to task scheduler in windows.

cron's format is
minute:  hour:  day of the month:  day of the week: command:
[i]

30 22 * * 0 apt-get update &&  apt-get -y dist-upgrade -t warty-security
[/i]
The above example would tell cron to run a check for security updates every sunday at 10:30 pm   

*suggested by jdong*
[i]
30 22 * * 0 apt-get update 
[/i]
This job would tell cron to update but you would be required to upgrade manually

To make a cron job yourself type in an open console type: 
1) crontab -e 
2) press the i key to insert commands
3) input your commands using the above guide
4) press esc and then press :wq! to exit and save changes

hopefully if all goes well you should now have setup cron to run a specific task at its appointed time 

if your not comfortable inputing the commands yourself there is a site that goes into more detail and has a tool to set up your commands for you.

[http://www.clockwatchers.com/cron_tool.html](http://www.clockwatchers.com/cron_tool.html) 

I hope this helps

Cacofonix

* updated to include sugestions by jdong

---

### Post by jayclark on 2004-10-29
Although I won't use it because I perfer to do it myself. I even did it myself when running windows. This is a very good guide.

---

### Post by jdong on 2004-10-30
I don't think it's correct. **apt-get dist-upgrade** will just sit at a Y/n prompt indefinitely. Every night you run it, you'll get a new one...... You need apt-get **-y** dist-upgrade -t warty-security.


If you don't like for updates to apply without you knowing, you can always just set a cron job for **apt-get update** so you'll always have up to date sources.

---

### Post by rapha on 2006-01-11
Although apt-get does have the '-y' option, many other commands do not. In that case, you can simply say: ```
yes 'y' | your -command -here
``` and it will answer all questions with 'y'.

---

### Post by jsandys on 2006-10-10
How can I extend this to dial up, say every Saturday night at midnight, do the update, then hangup?

I found the answer at this thread:
[http://ubuntuforums.org/showthread.php?t=207422](http://ubuntuforums.org/showthread.php?t=207422)

This thread has an elaborate script:
[http://ubuntuforums.org/showthread.php?t=197300](http://ubuntuforums.org/showthread.php?t=197300)

---

