---
title: "VMWare Player sending mixed messages"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by BeBoBli on 2008-06-13
```

The configuration of VMware Player 2.0.4 build-93057 for Linux for this running
kernel completed successfully.

You can now run VMware Player by invoking the following command: 
"/usr/bin/vmplayer".

Enjoy,

--the VMware team

bebobli@Apmuc:/usr/bin$ vmplayer
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

bebobli@Apmuc:/usr/bin$ 

```
This would make it the third time I've had to reconfigure the program. I've answered mostly defaults except for maybe routing the network to my wireless rather than ethernet. What should I try doing?

---

### Post by BeBoBli on 2008-06-13
Update:

I went through the configuration again and just disabled networking for virtual machines altogether. I can change it later I'm assuming. I'd rather do it after I can get to a GUI anyways. VMWare Player does not seem to appreciate my wireless hardware. That is still a problem.

Until I can solve that very problem I will be leaving this thread unsolved.

Edit: I am trying different virtualization software. VMWare server definitely has more options that would help me, and I am now going to try out VirtualBox. The problem is not solved because in Server it still does not work with my wireless device. Oh well.

---

