---
title: "cannot acess the Internet (wired/wireless connection problem)"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by alexDgreat on 2012-10-31
I just installed Ubuntu 10.04.4 LTS on my VirtualBox 4.2.4.
After rebooting and logging in, I was prompted to update important software. I clicked on update but the response I got is "Connection failed....unable to fetch........(5-could not locate address of host).

Pls wat do I do?

---

### Post by adrien214 on 2012-10-31
So let me get this straight: you have a windows machine running a Ubuntu in a virtual machine? Ok?

can you give us the result of the following command typed in a terminal (launch by hitting Ctrl+Alt+T):

```
ifconfig
```

Also, try to ping your windows host and make sure the windows firewall allows the access to the net for the virtual machine.

edit: ping your.win.dows.ip
edit2: if you are inside ubuntu inside ubuntu try ifconfig as well

---

### Post by alexDgreat on 2012-10-31
@ adrien214

I removed the ubuntu from my virtual machine and reinstalled it. After logging the update manager window had been opened.... I clicked on install update...then the downloading started....
thanks a lot for the reply

---

### Post by alexDgreat on 2012-11-03
I installed Ubuntu 10.04 LTS desktop on a virtualbox having windows vista as my host OS. I did the installation today. I clicked on systems, clicked on administrators, then clicked on  update manager manually. i clicked on check for update in the update manager dialogue box. the response was

could not download repository.


pls wat do i do?

---

### Post by newb85 on 2012-11-03
Is the same as the second install mentioned in your other thread?
[http://ubuntuforums.org/showthread.php?t=2078577]("http://ubuntuforums.org/showthread.php?t=2078577")
What has changed?

---

### Post by lisati on 2012-11-03
Threads merged

---

