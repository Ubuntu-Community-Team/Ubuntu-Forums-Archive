---
title: "Update to 4.2.0-30 caused error in my /etc/fstab file ..."
date: 2016-02-28
forum: New to Ubuntu
---

### Post by cwmoser on 2016-02-28
Got a popup about a security update for Ubuntu Mate and applied the update.
Restarted, and got this error:

[B][COLOR="#B22222"]failed to create mount unit file /run/systemd/generator/tmp.mount
[/COLOR][/B]
The update was to bring my kernel from 4.2.0-27 to 4.2.0-30

A little investigation and I found a duplicate entry in /etc/fstab.
I commented out the duplicate like this:

[B][FONT=Fixedsys]tmpfs /tmp     tmpfs defaults,noatime,mode=177 0 0 
tmpfs /var/log tmpfs defaults,noatime,mode=1777 0 0 
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0 
### tmpfs /tmp     tmpfs nodev,nosuid,size=7G 0 0 [/FONT][/B]

Questions:  Why?  And should I have commented out the other entry?

---

### Post by DuckHook on 2016-03-01
My entry is a hybrid of yours and looks like this:```
tmpfs    /tmp    tmpfs    defaults,noatime,nosuid,nodev,mode=1777    0    0
```...some users include *noexec* as well for added security, but this breaks some apps that run from /tmp. Frankly, I'm not sure your problem is in *fstab*, but you can start your detective work by changing the /tmp entry to mine. BTW, I haven't tried this on 15.10 and *systemd*, so I may not even be on the right trail. Problem may be due to a *systemd* setting that I am not familiar with.

---

### Post by DuckHook on 2016-03-01
After further research, according to [this]("https://bugs.freedesktop.org/show_bug.cgi?id=73710") bugzilla thread, the problem is that systemd does not support multiple mount objects to the same mount point. So you can only assign one of /tmp or /var/log or /var/tmp directed to tmpfs and no more than one. Are you running 15.10? If so, I don't know why you were even permitted to do this prior to kernel 4.2.0-30. Perhaps the kernel only started enforcing this limitation in the latest version. Since I don't redirect anything but /tmp to tmpfs, I don't know.

You may wish to sidestep the issue by leaving /var/log and var/tmp in their natural state. Clearly, you're okay with keeping no logs, but if it were me, I would feel rather naked doing so. I also don't believe that it is recommended. As well, /var/tmp is used for persistent files&#8213;that is, files that, while somewhat temporary, may be useful for the next session.

If you must have these directories in tmpfs, then you might be able to work around the limitation using soft links. The referenced thread offers workarounds that I don't understand.

More and more, I anticipate moving to systemd with mounting dread.

---

