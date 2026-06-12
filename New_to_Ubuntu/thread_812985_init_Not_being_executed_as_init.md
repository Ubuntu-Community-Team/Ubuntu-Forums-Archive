---
title: "init: Not being executed as init"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-30
Hi guys...

First install of Ubuntu server... 

When i try to run 

```
init 6
```

I get the following error message

```
init: Not being executed as init
```

Any ideas? would like to reboot the server remotley!

Thanks!

---

### Post by Oldsoldier2003 on 2008-05-30
> **markbusu said:**
> Hi guys...

First install of Ubuntu server... 

When i try to run 

```
init 6
```

I get the following error message

```
init: Not being executed as init
```

Any ideas? would like to reboot the server remotley!

Thanks!
any of these commands should work
```
sudo telinit 6 
sudo reboot now
sudo shutdown -r
```

---

### Post by markbusu on 2008-05-30
Thanks for your reply... however the results are as follows:

```
root@ubt00:~# sudo shutdown -r
sudo: shutdown: command not found

root@ubt00:~# sudo telinit 6
sudo: telinit: command not found

root@ubt00:~# sudo reboot now
sudo: reboot: command not found
```

This is the Server Edition... could this be the cause?

---

### Post by Oldsoldier2003 on 2008-05-30
> **markbusu said:**
> Thanks for your reply... however the results are as follows:

```
root@ubt00:~# sudo shutdown -r
sudo: shutdown: command not found

root@ubt00:~# sudo telinit 6
sudo: telinit: command not found

root@ubt00:~# sudo reboot now
sudo: reboot: command not found
```

This is the Server Edition... could this be the cause?

if you are logged in as root omit the sudo

---

### Post by markbusu on 2008-05-30
Yup.... reboot worked... however im quite amaized about init... do you know what might be the cause?

Thanks!

---

### Post by markbusu on 2008-05-30
Actually failed :(

The system is going down for reboot NOW!
shutdown: timeout opening/writing control channel /dev/initctl
init: timeout opening/writing control channel /dev/initctl

---

### Post by markbusu on 2008-05-30
reboot -f worked...

---

### Post by markbusu on 2008-05-30
PS. once rebooted... Init is working fine...

thanks!

---

