---
title: "snmp doesn't start on boot"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by menkurau on 2008-06-04
I am running Ubuntu 8 and for some reason snmpd doesn't start on boot.  I can start it manually just fine and the config is working.  I see the symlink in rc2.d.  Any help is appreciated.

---

### Post by menkurau on 2008-06-25
bump

---

### Post by dwhitney67 on 2008-06-25
I just installed the SNMP-daemon (using apt-get) and it is started up after installation.

I've checked to see if it will be launched during start-up by examining **System->Administration->Services**.  It appears that it will.  Now for the test... rebooting....

Ok, it works for me.  :-)

This is what I did:
```
$ sudo apt-get install snmpd
$ sudo reboot
```
Then after the reboot:
```

$ ps -ef | grep snmpd
```

I would recommend that you de-install the SNMP-daemon, then reinstall it again.  Maybe that will help.

---

