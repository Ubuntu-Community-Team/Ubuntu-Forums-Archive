---
title: "I still have a hard time with permissions in linux maybe I haven't come across the ri"
date: 2022-02-07
forum: New to Ubuntu
---

### Post by bazagee on 2022-02-07
I still have a hard time with permissions in linux maybe I haven't come across the right tutorial yet. In this use case I'm starting VMware Workstation as root (at my logon) so it can have access a couple of mounted partitions from a RAID array. 

```
 sudo su
 vmware &
```

I'll get this error:
root@<computername>:/home/<username># I/O warning : failed to load external entity "/etc/vmware/hostd/proxy.xml"  the hostd directory is not written.
Failed to create secure directory (/root/.config/pulse): Permission denied

So root can't create a directory in my limited profile?

---

### Post by schragge on 2022-02-07
Rather than **sudo su**, run
```
sudo su -
```
or, even better,
```
sudo -i
```
That way the environment for root would be loaded, and your current directory would be changed from **/home/<username>** to **/root**.

---

### Post by MAFoElffen on 2022-02-13
Actually... You "should" approach it from a different perspective. Do not run a VM as root. 

The perspective you should approach it is to fix your mount to give read/write/execute permissions to a VM User group, which you then, in turn, become a member of. That would be the "best practice" solution for that. The next step down from that, from a different perspective, would be to just give your userid the read/write/execute access to that mount.

---

