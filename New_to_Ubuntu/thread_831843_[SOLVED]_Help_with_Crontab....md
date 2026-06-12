---
title: "[SOLVED] Help with Crontab..."
date: 2008-06-17
forum: New to Ubuntu
---

### Post by billygriffiths on 2008-06-17
I am completely new to the Ubuntu/Linux environment and would like some help with Crontab. 

I've set up a crontab file with "sudo crontab -e", but the command does not seem to execute. 

Command looks as follows: 

0,05 * * * * sudo /usr/local/sphinx/bin/indexer --rotate  index_main

It should run every 5 minutes. Is there anything i need to do to make this happed? I am running a standard Ubuntu Server installation. Also, how do I monitor crontab activity? Is there a logfile somewhere I can see if it actually executes, and if any errors occur? 

Thanks!

---

### Post by justleen on 2008-06-17
every 5 minutes would be
*/5 * * * *

dit: you can skip the "sudo" part, since youre working in the root crontab file (sudo crontab -e -> edit the roots crontab)

---

### Post by fatality_uk on 2008-06-17
This is a nice little how to (not mine I might add)
Details the crontab scheduler very well

---

### Post by billygriffiths on 2008-06-17
Should there have been a URL Fatality?

---

### Post by fatality_uk on 2008-06-17
Sheeesh, you want me to do everything for you :lol:
Sorry, yeah here it is ;)

[http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/](http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/)

---

### Post by ibuclaw on 2008-06-17
I personally always use the system crontabs. I can always expect predictable behaviour from using it.

```
sudo gedit /etc/crontab
```

And put your line in at the bottom.

[EDIT]
Also, after a quick browse through the man page, run this command if you prefer to use your own crontab file:
```
sudo touch /etc/cron.deny
```
To explain the reason of the above command, the **cron.deny** file, when being used, contains the list of users who are not allow to use the cronjobs on the system. thus, creating the file WITHOUT putting your name in it should grant you permissions to execute cronjobs.
By default, both the files "cron.deny" and "cron.allow" are not put in place in the /etc folder. This may cause some abstract behaviours such as cronjobs not executing as expected for non-super users.

[EDIT2]
Works just fine for me. Are you sure that the file location is correct?
```
* * * * *  /bin/echo "Hello World"
```
Wait a minute, then type in "**mail**" in your terminal and you'll have a message from the Cron Daemon.

Regards
Iain

---

### Post by billygriffiths on 2008-06-17
Thanks fatality, will have a look at that file. Changed my interval as told by justleen and all seems to work perfectly now. Tinivole, does it matter which contab file you make use of? Do some perform more reliable than others?

---

### Post by billygriffiths on 2008-06-17
Very nice how to...appreciate all your help! The Ubuntu tunnel gets less dark every day.

---

### Post by fatality_uk on 2008-06-17
Your welcome. Many people are surprised just how powerful Linux is after scratching the surface.

Please mark the thread as solved if you are happy with the responses and feel free to thanks the guys above using the button on the right. (I just posted a link :))

---

### Post by aravinda_sh on 2008-07-28
The example 
* * * * *  /bin/echo "Hello World"

Did not work in my machine.
I added this code into crontab and then did "sudo /etc/init.d/sysklogd restart"

After a minute I checked mail by typing mail command and it said "No mails to root".

Please help me in getting my crontab working.

Thanks,
Aravinda

---

