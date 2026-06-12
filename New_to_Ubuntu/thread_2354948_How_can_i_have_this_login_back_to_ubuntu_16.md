---
title: "How can i have this login back to ubuntu 16?"
date: 2017-03-07
forum: New to Ubuntu
---

### Post by danielhk1 on 2017-03-07
HI,

I noticed that for ubuntu 14, i can have the following information when login in ssh:


Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 3.13.0-110-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Mar  7 18:06:48 HKT 2017

  System load:    0.08              Processes:           341
  Usage of /home: 0.2% of 20.39GB   Users logged in:     0
  Memory usage:   1%                IP address for eth0: x.x.x.x
  Swap usage:     0%

  => There are 2 zombie processes.

  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)

But for my ubuntu 16 server, it is not like this.
How can i make it like this?

Thanks.
Daniel

---

### Post by QIII on 2017-03-07
Hello!

Install landscape-common on the server:

```
sudo apt install landscape-common
```

Log out of your ssh session and log back in.  You should get a bunch of system info.  You may need to reboot your server.

For instance, I get:

```
Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-65-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Tue Mar  7 19:42:42 PST 2017

  System load:    0.05              Processes:           201
  Usage of /home: 0.1% of 73.21GB   Users logged in:     0
  Memory usage:   12%               IP address for eno1: 192.168.1.23
  Swap usage:     0%

  Graph this data and manage this system at:
    https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

```

when I ssh in to my server.

---

### Post by papibe on 2017-03-07
Hi danielhk1.

Try setting the PrintMotd option in your ssh server:
```
sudo vi /etc/ssh/sshd_config
```
Add a line like this:
```
PrintMotd yes
```
Then restart ssh:
```
sudo systemctl restart ssh.service
```
Logout an log in again.

Hope it helps. Let us know how it went.
Regards.

---

### Post by danielhk1 on 2017-03-07
Hi papibe,

Thanks for the suggestion, yes, the PrintMotd seems is the key of this problem as the server already have landscape installed.

Problem solved.

Daniel

---

### Post by scarabaeus2 on 2018-02-19
Actually, PrintMotd in sshd_config is not the solution. Motd is handled by PAM.

I found that there is a file name mismatch in Ubuntu 16. To solve it, check the filename of your dynamic motd script in /run:

```
# ls /run/*motd*
/run/motd.dynamic.new
```

Then check that the filename in the pam config file matches:

```
sudo vi /etc/pam.d/sshd
```

Look for this section:

```
# Print the message of the day upon successful login.
# This includes a dynamically generated part from /run/motd.dynamic
# and a static (admin-editable) part from /etc/motd.
session    optional     pam_motd.so  motd=/run/motd.dynamic
session    optional     pam_motd.so noupdate
```

Adjust the motd parameter to match the filename in /run. On my system, after a marathon upgrade (karmic to lucid to precise to trusty to xenial) it ended up as above, and I had to change it to:

```
session    optional     pam_motd.so  motd=/run/motd.dynamic.new
```

---

