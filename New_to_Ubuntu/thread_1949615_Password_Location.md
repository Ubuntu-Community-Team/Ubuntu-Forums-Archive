---
title: "Password Location"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by johnfarrow on 2012-03-30
I have Ubuntu 9.10 on a dual boot with Windows 7.  I haven't used it in a while and I need to change to network settings.  It ask for my password and I don't remember it.

Can I reset it while I am running 9.10?

---

### Post by haqking on 2012-03-30
> **johnfarrow said:**
> I have Ubuntu 9.10 on a dual boot with Windows 7.  I haven't used it in a while and I need to change to network settings.  It ask for my password and I don't remember it.

Can I reset it while I am running 9.10?

if its your sudo password then it is the one you login with, same password.

however if you have troubles see here

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by winh8r on 2012-03-30
Start your Ubuntu in recovery mode by holding down the shift key at boot time.

Select (recovery mode) from the menu and hit enter

Navigate down the options menu to "drop to root shell prompt"

select and hit enter

at the prompt enter 

```
passwd johnfarrow
```

or whatever your username is on that machine

you will be prompted to enter a new unix password and confirm it , complete the rest of the details if required and it will update the password for user johnfarrow.

at the prompt enter 
```

shutdown -r now
```

the machine will reboot and you should be able to login with your new password.

hope this helps.


and in the time it took me to write this haqking had answered and you have probably done it already!!!!:p:p

---

