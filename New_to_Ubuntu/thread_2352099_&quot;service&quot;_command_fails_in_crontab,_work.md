---
title: "&quot;service&quot; command fails in crontab, works in interactive shell"
date: 2017-02-09
forum: New to Ubuntu
---

### Post by rayholme on 2017-02-09
I am new to Ubuntu, but not new to Unix (many years). I have created a script to update something automagically.
The script must run as root. It runs fine with sudo every time in an interactive shell (using ssh into the target box to do it).
However it fails every time when run by root's crontab.

The error message basically states that it fails to bring tomcat down. (need to update a DB)

The command to do this is (this is how it appears in the script):
   service S95tomcat stop

I then check to make sure before proceeding and issue the warning message to a file.
Can anyone tell me why this works ALWAYS when run in an interactive shell but fails ALWAYS if run out of crontab??

Thanks for any enlightenment.

---

### Post by steeldriver on 2017-02-09
Possibly because the upstart `service` command lives in /usr/sbin, which is not in cron's default PATH

Always either use full paths for executables in crontabs - or specify a suitable PATH at the top

```

PATH=/usr/sbin:/sbin:$PATH

```

[Note that `stop` is also probably a distinct executable `/sbin/stop`]

---

### Post by rayholme on 2017-02-09
Nice try, but I have been doing Unix a long time.

The script lives where it belongs and is not in /usr/bin or /usr/sbin.
stop is an option to the script as documented with service
and yes I always qualify command name not in root's path.

 ls -l /etc/init.d/S95tomcat /usr/sbin/S*
ls: cannot access '/usr/sbin/S*': No such file or directory
lrwxrwxrwx 1 root root 20 Nov 10  2015 /etc/init.d/S95tomcat -> /local/bin/S95tomcat

I will make sure next time I try in a shell to use "su -" instead of "su", but I really think that is not the problem.
I will be able to try again after another backup has been performed (later today or tomorrow).

But yes, that could be the only difference that I can think of between crontab and my normal sudo session.
Will post if that is it, but hope someone has a better answer.

---

### Post by SeijiSensei on 2017-02-09
On my 14.04 system the service command is in /usr/bin.  On 16.04 it is in /usr/sbin. 

However if you're running 16.04 or later, you should be using the systemd commands like systemctl.  To start a service on a systemd machine, use
```
/bin/systemctl start service_name
```

---

### Post by ajgreeny on 2017-02-09
Steeldriver was not talking about the folder of the script itself but the folder where the executable **service** sits, ie /usr/sbin/service.

so try that command in your script **/usr/sbin/service S95tomcat stop** and you may see that cron will now find the executable and run it.

EDIT:
I see SeijiSensei has also added to this thread and I think he is correct; note that he has also given the full pathway of the executable **systemctl** which is always a very good idea in commands used in a crontab, whether for you as user or for root cron.

---

### Post by rayholme on 2017-02-09
I think you are dead right. I put explicit calls to service in the script AND I am logging the PATH for my own edification.

Apologies for my non-belief. In other versions of Unix and Linux, /sbin and /usr/sbin seem to be in the PATH for root and I never had a crontab failure like that.

Thanks for your tip. Thanks SteelDriver. Thanks to SeijiSensei too. That is the right way in Fedora and I will update my methods.

Thanks also to algreeny.

 :=] RaySensei (Aikido)

---

### Post by ajgreeny on 2017-02-09
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

