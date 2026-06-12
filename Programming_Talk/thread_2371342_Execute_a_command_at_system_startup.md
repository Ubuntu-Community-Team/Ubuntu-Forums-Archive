---
title: "Execute a command at system startup"
date: 2017-09-13
forum: Programming Talk
---

### Post by maxcarter99 on 2017-09-13
Hello everyone !

First of all, I know there are many threads on many websites regarding my issue, but despite all of my efforts, I can't get it work... !

Basically, what I want to do is make a *.sh* file running when my system boots.

What I've done so far :

[LIST]
[*]I created a new text editor file, typed in ```
sudo shutdown -r 00:00
``` so my computer reboots each day at midnight, and saved this file with the extension *.sh *on my desktop
[*]I moved the file to the */etc/init.d* directory using *sudo mv* command on terminal
[*]I did set up executable permission on script with terminal, typing ```
chmod +x /etc/init.d/script.sh
```
[*]I used the following command to get my file executed at my system startup : ```
update-rc.d script.sh defaults 100
```
[/LIST]

Have I done something wrong, or does it miss any step so I can get it work ?

Hope that anyone could help me on that ! Thank you very much.

Max

---

### Post by deadflowr on 2017-09-13
Remove the sudo from the command.
It's not needed in /etc/init.d and most likely is causing the issue since sudo usually needs user interaction.
You would also most likely need to set the full path to shutdown,  /sbin/shutdown should be it.

---

### Post by SeijiSensei on 2017-09-13
A much better way to handle scheduled jobs like this is through cron.

```

sudo echo '00 00 * * * /sbin/shutdown -r now' >> /var/spool/cron/root

```

That will run the command "/sbin/shutdown -r now" every night at midnight.

See:  [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

