---
title: "/etc/rc.local"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by jimafternoon on 2013-04-09
Hello, 

I installed Ubuntu on a Lenovo Ideapad u400. It was running hot, which I found out was due to switchable graphics. I found a fix online, where you insert this in  /etc/rc.local, so that it runs every time you start up, instead of having to put this in the terminal each time:

```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

It worked fine. 

But yesterday, I replaced my HDD with an SSD, and I was using this guide to help tweak a few things in order for SSD:

[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Now, this tutorial suggested I put some other stuff in  /etc/rc.local, such as:

```
#
# Modification for SSD
for dir in apparmor apt cups dist-upgrade fsck gdm installer samba unattended-upgrades ;
do
           if [ ! -e /var/log/$dir ] ; then
                   mkdir /var/log/$dir
           fi
done
```

and this:

```
fstrim -v /
fstrim -v /home

```

So I've got all of that in there, and it looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
fstrim -v /
fstrim -v /home
fstrim -v /boot/efi
#
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
#
# Modification for SSD
for dir in apparmor apt cups dist-upgrade fsck gdm installer samba unattended-upgrades ;
do
           if [ ! -e /var/log/$dir ] ; then
                   mkdir /var/log/$dir
           fi
done
exit 0


```

The problem is, the graphics aren't being shut off when I log in now.  So I'm not sure if the whole thing is screwed up or what. 

I'd appreciate any help, thanks guys!

---

### Post by jimafternoon on 2013-04-09
Well, I just realized I prob shouldn't have put the ```
fstrim -v /boot/efi
``` in there, I took it out and restarted, and the fans definitely turned off. 

Sorry.

---

### Post by Pjotr123 on 2013-04-10
> **jimafternoon said:**
> Well, I just realized I prob shouldn't have put the ```
fstrim -v /boot/efi
``` in there, I took it out and restarted, and the fans definitely turned off. 


Thanks for reporting this issue. I'm the guy who maintains the Easylinuxtipsproject website, and I've added a warning to my SSD instruction, not to apply trim to a separate /boot/efi partition. :)

---

