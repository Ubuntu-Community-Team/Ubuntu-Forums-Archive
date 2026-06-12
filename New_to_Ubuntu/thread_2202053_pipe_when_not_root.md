---
title: "pipe when not root"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by agarrett5 on 2014-01-27
Hi,

I am trying to pipe the output of zmbkpose --restoreAllAccounts.  I would usually use either 2> or | but it seems I can only do this as root user.  As I can only run zmbkpose --restoreAllAccounts as user: zimbra I can't pipe the out put.  any suggestions of how I can pipe?  I am using Ubuntu 12.04 LTS on Zimbra 8.0.6 :)

Andy

---

### Post by Iowan on 2014-01-27
The "tee" command is occasionally used with sudo... I'll need to look up a better example than:  <command> | sudo tee <command>

---

### Post by agarrett5 on 2014-01-27
unfortunately I cant use sudo in Zimbra as a zimbra user :(  I don't know if there's a setting somewhere I can change in a config file or something that may allow me to use sudo

---

### Post by steeldriver on 2014-01-27
There shouldn't be any problem in piping output as a non-privileged user **unless the place you are trying to pipe to** requires elevated privileges - for example you should be able to pipe to a file in your own home directory, but not somewhere like / or /etc

---

### Post by agarrett5 on 2014-01-27
That's the issue, chowned the output file to zimbra and it worked :)

---

