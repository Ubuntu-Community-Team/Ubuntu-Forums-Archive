---
title: "Cron job"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by Old-un on 2011-12-19
I have installed rkhunter and would like to set it to run once a week. For this i have been told that i need to set up a cron job? Could someone help me out here please

---

### Post by MartijnNL on 2011-12-19
You could add a simple script to /etc/cron.weekly which calls rkhunter.

Like:

```

#!/bin/sh

rkhunter <any options you need>

```

You will need root privileges to place the file in this directory. If you're familiar with vim or another text-mode editor you could use something like:

```
sudo vim /etc/cron.weekly/rkhunter
```

Or create it in your home directory and copy it.

```
sudo cp rkhunter /etc/cron.weekly
```

---

### Post by Lars Noodén on 2011-12-19
> **MartijnNL said:**
> You will need root privileges to place the file in this directory. If your familiar with vim or another text-mode editor you could use something like:


While I also highly recommend vi and vim, since this is a beginner topic, maybe [nano](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nano.1.html) would be more appropriate.  The [font=Courier New]-w[/font] option is needed to prevent it from inadvertently wrapping the lines.

```

sudo nano -w  /etc/cron.weekly/rkhunter
sudo chmod +x /etc/cron.weekly/rkhunter

```

---

### Post by MartijnNL on 2011-12-19
That's why I said: "or another text-mode editor". But it would perhaps have been better to suggest nano as the first option instead of vim. But using Gedit and copying it using sudo would work fine too in that case.

And I forgot to mention the chmod bit. Thanks for adding that.

---

### Post by Old-un on 2011-12-22
Still getting my head around Cron jobs lol. So i've come up with the following:

crontab -e
MAILTO=validemailaddress.com
* 10 * * 0 /usr/local/bin/rkhunter

Which i hope will run rkhunter at 10am every Sunday, i hope! 

Could some knowledgable forum member at a look please

---

### Post by MartijnNL on 2011-12-22
It should, if it isn't a graphical (GUI) program. If it is it should be:

```
* 10 * * 0 export DISPLAY=:0 && /usr/local/bin/rkhunter
```

By the way: the way it is now, you are running it as you own user. Does you user have read and execute permissions to the file? Otherwise it won't work. Either the file should be owned by you and have those permissions, or you should be in the file's group (and the group should have these permissions) or the world should have these permissions. If you post the output of

```
ls -l /usr/local/bin/rkhunter 
```

we might be able to help you with that.

I assume you entered a real e-mail address?

---

### Post by Old-un on 2011-12-22
I was going to open the nano text editor from the command line and then type:

crontab -e
MAILTO=myemailaddress.com
* 10 * * 0 /usr/local/bin/rkhunter

I was going to use a valid email addresss.

Here is the output of ls -l command:
old-un@ubuntu:~$ ls -l /usr/local/bin/rkhunter
-rwxr-x--- 1 root root 496564 2011-12-10 15:50 /usr/local/bin/rkhunter
old-un@ubuntu:~$

---

### Post by Paqman on 2011-12-22
Is this for a server or a desktop?

Traditional cron is really designed more for servers or other machines that are always on. If it's a desktop you're better off using anacron. It has two advantages:
[LIST=1]
[*]Tasks will still run if the machine happens to be off at the time. They'll run next time it starts up.
[*]It's much easier to use.
[/LIST]
To set an anacron task just drop an executable script with your commands into the appropriate folder (e.g: /etc/cron.weekly).

---

### Post by MartijnNL on 2011-12-22
As it is now only root can execute the script. So either you'll have to set the cron for the root user. (Edit /etc/crontab) Or you'll have  to change ownership of permissions for the file. Or (which may indeed be the easiest way) add a script calling it to /etc/cron.weekly.

The latter solution is described in [your earlier thread]("http://ubuntuforums.org/showthread.php?p=11549035#post11549035"). It would have been better if had continued there instead of starting a new thread. Perhaps a moderator can merge the two threads?

---

### Post by Old-un on 2011-12-22
Shall have a look at anacron. Thanks for the help both

---

