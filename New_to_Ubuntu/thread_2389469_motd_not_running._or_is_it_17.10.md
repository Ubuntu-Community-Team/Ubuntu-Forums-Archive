---
title: "motd not running. or is it? 17.10"
date: 2018-04-17
forum: New to Ubuntu
---

### Post by nmparmar on 2018-04-17
New to this world, and trying to customise motd setup on ubuntu 17.10.

Mostly understand how it works, but all I see on logon is the 'Last login: <date> from <IP>'
I have checked the following as per [https://askubuntu.com/questions/538732/no-motd-on-ubuntu-14-04](https://askubuntu.com/questions/538732/no-motd-on-ubuntu-14-04) and all appear ok:
 - file /etc/pam.d/login contains the following:
  session    optional   pam_motd.so motd=/run/motd.dynamic
  session    optional   pam_motd.so noupdate
 - file /etc/ssh/sshd_config contains the following: 
  UsePAM yes
  PrintMotd no

however running [FONT=Consolas][COLOR=#111111]sudo run-parts /etc/update-motd.d/ doesn't display the expected message. [/COLOR][/FONT]

I have followed this article: [https://ownyourbits.com/2017/04/05/customize-your-motd-login-message-in-debian-and-ubuntu/](https://ownyourbits.com/2017/04/05/customize-your-motd-login-message-in-debian-and-ubuntu/) still no message. 
I then backed out those changes and removed and reinstalled update-motd which stopped me getting the last logon details. Reinstalling them I can see the timestamp again.  
I then followed this article: [https://wiki.ubuntu.com/UpdateMotd](https://wiki.ubuntu.com/UpdateMotd) and noticed the following:
  - /etc/update-motd.d directory existed but no scripts / files therein. I created a sample script as per that article and added it to the directory as '10-stats'. Contents below:
```
 #!/bin/sh
  echo
  date
  echo
  who
  echo
  uptime

```
  - /etc/cron.d/update-motd doesn't exist at all. 
  - Still trying to run ```
sudo run-parts /etc/update-motd.d/
```returns nothing and login only displays the last login date/source. I can execute 10-stats fine and get the expected output.

I've now confused myself silly and need some help. Any pointers anybody?

Thanks

---

### Post by nmparmar on 2018-04-17
Minor update: 
Not sure what has changed, but now upon running 'sudo run-parts /etc/update-motd.d/ I am getting the below error messages:

run-parts: failed to exec /etc/update-motd.d//10-stats: Exec format error
run-parts: /etc/update-motd.d//10-stats exited with return code 1

I can still run the 10-stats file directly without issue.

I am running Ubuntu in a virtual machine under vmware esx 6.5.

---

### Post by nmparmar on 2018-04-19
*tumbleweed*

Oh well, ended up resolving with a fresh install. Consider this closed.

---

