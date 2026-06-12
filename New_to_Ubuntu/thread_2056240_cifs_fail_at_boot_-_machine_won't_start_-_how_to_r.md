---
title: "cifs fail at boot - machine won't start - how to resolve"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by dvrs on 2012-09-11
Hi,

After getting some great advice via this forum ([http://ubuntuforums.org/showthread.php?t=2053165](http://ubuntuforums.org/showthread.php?t=2053165)) how to cifs mount shares at boot time I've now realised this may not always be such a wise move as one of the shares is a windows laptop that is often turned off..

My questions are:

1. I'm getting errors like this one:
```
mountall: Disconnected from Plymouth
[    28.180335] CIFS VFS: cifs_mount failed w/ return code = -113
Unable to find suitable address.
mountall: mount /home/mats/MATSLUND-HP [1105] terminated with status 2
```

..which obviously must be because the share is not available. Problem is that unless the share is available the (L)Ubuntu machine won't start up. How can I get around this at boot time and make my linux box spark up regardless? 

2. Is there an 'automount' way of mounting shares, i.e. so that they are mounted only if they are available?

(3. I've also been having some other spurious errors which may be related to the fact that my disk is full but I suspect this has no bearing on the questions posed above).

Grateful as always for any assistance,
Mats

UPDATE: The machine appears to have booted but is now stuck at a black screen (which appears before the graphical login screens is presented) with the following error message:
```
mountall: Disconnected from Plymouth
```
I can ssh on to the machine - I am moving data off it to free space to see if that has any effect.

Any ideas of actions to take to repair the damn thing?

---

### Post by dvrs on 2012-09-11
Update 2:

Ok problem (temporarily) solved. Via ssh access I removed the fstab entry for network boot of my windows share, then ran an apt-get clean to remove the cache which was sizeable (500MB). The machine started up and is now behaving. Will likely look to run the cifs mount via a command in the /etc/rc.local file (this seems to be a foolproof solution recommended by others).

Marking as solved.

---

### Post by whlteXbread on 2013-06-12
> **dvrs said:**
> 

My questions are:

1. I'm getting errors like this one:
```
mountall: Disconnected from Plymouth
[    28.180335] CIFS VFS: cifs_mount failed w/ return code = -113
Unable to find suitable address.
mountall: mount /home/mats/MATSLUND-HP [1105] terminated with status 2
```



I'm running into a similar problem.

I'm mounting a network drive in fstab that's used to backup information on the machine. For some reason, CIFS can't resolve the IP address of the network machine. Pinging the network machine correctly resolves the IP address, so DNS information is at the very least available to my system.

Due to the network configuration, I have no control over the networked machine or the networking environment. 

In fstab, the network machine is specified like so:

```
//networkmachine/share
```

Is there any way to specify the network address instead of using the machine name?

Thanks for any help.

---

### Post by bab1 on 2013-06-12
> **whlteXbread said:**
> I'm running into a similar problem.

I'm mounting a network drive in fstab that's used to backup information on the machine. For some reason, CIFS can't resolve the IP address of the network machine. Pinging the network machine correctly resolves the IP address, so DNS information is at the very least available to my system.

Due to the network configuration, I have no control over the networked machine or the networking environment. 

In fstab, the network machine is specified like so:

```
//networkmachine/share
```

Is there any way to specify the network address instead of using the machine name?

Thanks for any help.

Does the IP address change?  If so then mounting via fstab by IP address is not possible.

---

### Post by whlteXbread on 2013-06-12
I didn't solve my problem, but I answered my original question. One can specify an IP like so:

```
sudo mount -t cifs //servername/share -o "ip=0.0.0.0" /mnt/mntpoint
```

---

### Post by bab1 on 2013-06-12
> **whlteXbread said:**
> I didn't solve my problem, but I answered my original question. One can specify an IP like so:

```
sudo mount -t cifs //servername/share -o "ip=0.0.0.0" /mnt/mntpoint
```

That's interesting (if you are referring to my post).  Your method should be the same as```

sudo mount -t cifs //ip_address/share /mnt/mntpoint
```...where ip_address is the actual address of the server with the share.  Did you literally mean 0.0.0.0?

---

### Post by whlteXbread on 2013-06-12
I should clarify—my problem can't be solved by a CIFS mount. Turns out CIFS (and lots of Windows domain-type stuff) is blocked by a firewall between the two machines.

No, I didn't literally mean 0.0.0.0.

As for ```
sudo mount -t cifs //ip_address/share /mnt/mntpoint
```
I found an AskUbuntu post (am having trouble finding it again) that said that will sometimes fail because some servers need the netbios name.

Thanks for your responses!

---

### Post by bab1 on 2013-06-12
> **whlteXbread said:**
> I should clarify&#8212;my problem can't be solved by a CIFS mount. Turns out CIFS (and lots of Windows domain-type stuff) is blocked by a firewall between the two machines.

So does this mean you can't use SMB/CIFS at all.  There is no other way to mount a Windows share other than that.  As soon as you use ```
mount -t cifs
```...you are using CIFS (whether you are using the netbios name or not).  in fact anytime you use //COMPUTER_NAME/share or //IP_address/share you are using CIFS.

> 

No, I didn't literally mean 0.0.0.0.

As for ```
sudo mount -t cifs //ip_address/share /mnt/mntpoint
```
I found an AskUbuntu post (am having trouble finding it again) that said that will sometimes fail because some servers need the netbios name.  

Thanks for your responses!

At all times **Samba and Windows CIFS servers **use NETBIOS to resolve COMPUTER NAMES to IP addresses.  Samba for sure can resolve *hostnames* to *NETBIOS* names to *IP addresses*.  The Samba server uses ***nmbd*** for that.

---

### Post by devantemack on 2013-09-23
what do u do if u cant type in a command in a terminal when you press ctrl+alt+f2 or f1? becuz i can type in it but it doesnt ask for a command.

---

