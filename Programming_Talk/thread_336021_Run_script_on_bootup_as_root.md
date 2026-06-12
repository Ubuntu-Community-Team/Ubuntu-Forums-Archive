---
title: "Run script on bootup as root"
date: 2007-01-11
forum: Programming Talk
---

### Post by RudolfMDLT on 2007-01-11
Hi there,

I need to write a script that will restart a server install every 24 hours. Is there a program already installed/ that i can install on a server that will allow me to schedule a restart every 24 hours or will my script have to count down 24 hours?

Secondly - If my script has to count down itself, where do I tell Ubuntu server to load it at startup?

Thirdly - The script needs to reboot the computer, so it has to be executed with root privileges? how can I execute a script with root privileges without having some one enter the password? Can I have the script enter the root password for me?


Thanks,

Rudolf

---

### Post by LotsOfPhil on 2007-01-11
This is hopefully not the best solution but you can make a file with your password in it and have sudo use that.

sudo -S /execute/script < /file/with/password

Not something I would do.

---

### Post by RudolfMDLT on 2007-01-15
O! read it from a file! Thanks a lot!

---

### Post by Grey on 2007-01-15
I was hesitating to reply to this, as I really don't know the answer.  But that solution is just terrible, as LotsOfPhil has already said.

The correct way of doing this would be to install the script to /etc/init.d.  I'm not really sure how this works, or what the procedure is.  But that's the place that boot-time scripts are placed.  I think they need to be registered somewhere as well.  But again, I'm not sure.  Which is why I didn't answer.

My suggestion would be to check out the folding@home script on these forums, since it installs the F@H binary manually (via a script), and sets it to run on boot.  It would be a good starting point.

---

### Post by RudolfMDLT on 2007-01-15
I know it's not the most delecate or secure solution - But I'm really a noob and the machine I'm going to be running this on in an isolated ubuntu server. But I'll try the init.d advice. Thank you very much!

---

### Post by andrem on 2007-01-16
I would put the script on /etc/init.d then do a 
```
sudo chmod +x /etc/init.d/script_name.sh
```
and finally
```
sudo update-rc.d script_name.sh defaults
```
```
man update-rc.d
``` may also help

---

### Post by yota on 2007-01-16
To schedule a script to be run every 24 hours you can just put it under /etc/cron.daily (make sure that it's executable and has no extension).
The cron scheduler will take care of executing it trough the anacron command; there are also the self-explaining 'cron.hourly' and 'cron.monthly'

For advanced usage have a look at

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Hope this helps!

p.s. by default the script will be run as root as you require

---

### Post by andrem on 2007-01-16
Yes, I'd also use cron. I set the script with update-rc.d because I though your script handled the triggering. Anyway, it seems stupid to do it that way, i'd stick to Cron.

---

### Post by LotsOfPhil on 2007-01-16
When/if you use Cron, type:

sudo crontab -e

And it will run as root.

---

