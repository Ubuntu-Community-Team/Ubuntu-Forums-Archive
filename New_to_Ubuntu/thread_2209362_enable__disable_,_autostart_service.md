---
title: "enable | disable , autostart service"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by shiyas on 2014-03-05
Dear all,

 How I can able to enable/disable a service from auto startup in Ubuntu systems.

In Redhat flavours:

Chckconfig smb on (enable smb on)

Chckconfig smb off (disable smb off)

Please help me.

---

### Post by Lars Noodén on 2014-03-05
Ubuntu uses Upstart, for the time being.  There are several ways but perhaps the simplest is to just add an [override file](http://upstart.ubuntu.com/cookbook/#disabling-a-job-from-automatically-starting).

```

sudo sh -c 'echo "manual" >> /etc/init/ssh.override'

```

That leaves the init file intact and it can still be started manually.  Remove the .override file to restore the automatic startup.

Sometime in the future, Ubuntu will move to systemd and all that will change.  But for now it works.

Edit: that stops ssh in the example above.  To stop some other service, use that service's corresponding file name.

---

### Post by raja.genupula on 2014-03-05
install bum there you can manage.

sudo apt-get install bum

---

### Post by ibjsb4 on 2014-03-05
Hi Raja

Does 'bum' work?  Last time I tried it, it was broke.

---

### Post by raja.genupula on 2014-03-05
My [URL="http://ubuntuforums.org/member.php?u=1729120"][COLOR=#000000]Friend ibjsb4

Hope you are doing good.

I just checked bum  now to re verify . its working fine
[/COLOR][/URL]

---

