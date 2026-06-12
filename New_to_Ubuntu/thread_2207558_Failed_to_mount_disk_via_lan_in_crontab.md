---
title: "Failed to mount disk via lan in crontab"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by huangchenmin on 2014-02-24
Dear all, I ran crontab -e in terminal and modified crontab like following shows:

10 16 * * * mount -t cifs //192.168.0.33/workroom/ /usr/local/mnttest -o username=myusername,password=mycode
[ATTACH=CONFIG]250635[/ATTACH]

I am sure that above works while executed in terminal. I checked /var/log/syslog. It told me that contab did run on schedule.
[ATTACH=CONFIG]250634[/ATTACH]
Please help me figure out why that command did not done in crontab.
I thank you in advance.
sincerely yours
tom

---

### Post by huangchenmin on 2014-02-24
> **huangchenmin said:**
> Dear all, I ran crontab -e in terminal and modified crontab like following shows:

10 16 * * * mount -t cifs //192.168.0.33/workroom/ /usr/local/mnttest -o username=myusername,password=mycode
[ATTACH=CONFIG]250635[/ATTACH]

I am sure that above works while executed in terminal. I checked /var/log/syslog. It told me that contab did run on schedule.
[ATTACH=CONFIG]250634[/ATTACH]
Please help me figure out why that command did not done in crontab.
I thank you in advance.
sincerely yours
tom
I modified crontab and make it output processing message to /tmp/auto.log. Followings are content. Please help!

sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: no tty present and no askpass program specified
Sorry, try again.
sudo: 3 incorrect password attempts

---

### Post by steeldriver on 2014-02-25
Does your cifs password contain special characters (% sign in particular)? regardless, try moving the mount command to a script file and calling *that* from cron

---

### Post by Morbius1 on 2014-02-25
I should in no way be confused with someone with any kind of expertise in cron jobs but you are not in fact running this command as you originally posted:
> mount -t cifs //192.168.0.33/workroom/ /usr/local/mnttest -o username=myusername,password=mycode
You are in fact running this command in cron:
> [COLOR=#0000cd]**sudo**[/COLOR] mount -t cifs //192.168.0.33/workroom/ /usr/local/mnttest -o username=myusername,password=mycode
Sudo requires a username and password and there is no way to give it one. The "username=myusername,password=mycode" is for passing credentials to the samba server not for sudo.

---

### Post by steeldriver on 2014-02-25
Ah well spotted Morbius1 - that's most likely the issue

---

### Post by huangchenmin on 2014-02-25
> **Morbius1 said:**
> I should in no way be confused with someone with any kind of expertise in cron jobs but you are not in fact running this command as you originally posted:

You are in fact running this command in cron:

Sudo requires a username and password and there is no way to give it one. The "username=myusername,password=mycode" is for passing credentials to the samba server not for sudo.
Thanks for replying.
My understanding from your reply is that I should remove "username=myusername,password=mycode" from crontab.
Is that right ?
Thank you again.
tom

---

### Post by Morbius1 on 2014-02-25
Nope.

If the samba server requires a username and password to gain access your mount command must include them.

This issue here is the use of sudo. When cron reads that line it will look for sudo's username and password but it can't spawn a terminal to ask you for it.

If this cron job is being done by root then don't include sudo because it is sudo. Is this your own personal cron job or is it root's?

---

### Post by huangchenmin on 2014-02-26
> **Morbius1 said:**
> Nope.

If the samba server requires a username and password to gain access your mount command must include them.

This issue here is the use of sudo. When cron reads that line it will look for sudo's username and password but it can't spawn a terminal to ask you for it.

If this cron job is being done by root then don't include sudo because it is sudo. Is this your own personal cron job or is it root's?

Thank you again.
The crontab is belong to me not root.
 tom

---

### Post by huangchenmin on 2014-02-26
> **Morbius1 said:**
> Nope.

If the samba server requires a username and password to gain access your mount command must include them.
......
If this cron job is being done by root then don't include sudo because it is sudo. Is this your own personal cron job or is it root's?

after seeking on web, I modified /etc/sudoers in terminal with following command "sudo visudo -f /etc/sudoers". 
adding "myusername ALL =NOPASSWD: ALL" then save without reboot.
Now wake on lan was executed successfully even "NO MTA installed.......' kept displaying.

Thank you again
Sincerely yours
tom

---

