---
title: "newbie VPN problems"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by PhantomOG on 2008-08-16
Ok, I'm having problems with VPN so this might go in the networking section, however, I have a feeling my problems are from my utter lack of linux understanding and not *real* issues.


I *think* I got the Cisco VPN client installed correctly.  I had to patch two things but I finally got the install script to run.  I've done the vpnclient_init start.

How do I now connect?  According to my work instructions, I just run:

vpnclient connect aus

where I have an aus.pcf file located at /cisco/vpnclient/

But it doesn't work.  Am I have a path issue?  Where can I call vpnclient from?  Do I need "sudo" in front"  sudo bash?  This is all greek to me, so please feel free to assume I'm a complete idiot and don't be afraid to suggest the simplest ideas.  Thanks!  :lolflag:

---

### Post by tamoneya on 2008-08-16
what is the error or are no errors given.  Also have you seen vpnc.  It is typically easier to use.

[http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/)

---

### Post by PhantomOG on 2008-08-16
I assume I have to use the Cisco one since it is the only one supported by my work.

brian@laptop:~$ vpnclient connect aus
bash: /usr/local/bin/vpnclient: No such file or directory

So I'm thinking path issue?  So I do this:

brian@laptop:~$ cd /opt/cisco-vpnclient/
brian@laptop:/opt/cisco-vpnclient$ ls
bin  include  lib  license.txt
brian@laptop:/opt/cisco-vpnclient$ cd bin/
brian@laptop:/opt/cisco-vpnclient/bin$ ls
cisco_cert_mgr  cvpnd  ipseclog  vpnclient
brian@laptop:/opt/cisco-vpnclient/bin$ vpnclient connect aus
bash: /usr/local/bin/vpnclient: No such file or directory

Still no joy.

---

### Post by PhantomOG on 2008-08-16
I see vpnclient is located in /opt/cisco-vpnclient/bin directory, but even calling it from there doesn't seem to work.  This is probably something really silly right?

---

### Post by PhantomOG on 2008-08-16
I've just verified that the correct pcf file is located in:
/etc/CiscoSystemsVPNClient

So I just need help on actually getting the vpnclient command started.  I keep getting:
bash: /usr/local/bin/vpnclient: No such file or directory

---

### Post by cariboo on 2008-08-16
> brian@laptop:/opt/cisco-vpnclient/bin$ vpnclient connect aus

Just add a ./ before the vpnclient connect aus eg:

```
brian@laptop:/opt/cisco-vpnclient/bin$ ./vpnclient connect aus
```

That should make you command work.

or use the full path when issueing a command from your home directory

```
 /opt/cisco-vpnclient/bin/vpnclient connect aus
```

Jim

---

### Post by PhantomOG on 2008-08-16
Thanks, I tried both:

brian@laptop:/opt/cisco-vpnclient/bin$ ./vpnclient connect aus
bash: ./vpnclient: No such file or directory
brian@laptop:/opt/cisco-vpnclient/bin$ /opt/cisco-vpnclient/bin/vpnclient connect aus
bash: /opt/cisco-vpnclient/bin/vpnclient: No such file or directory


I see the vpnclient file there so I have no idea what's wrong?

---

### Post by PhantomOG on 2008-08-16
Maybe my install didn't go so well?  As you can tell, I really have no idea what I'm doing so its very possible I screwed up the install process.

---

### Post by PhantomOG on 2008-08-16
So if its not a path issue, is there any way to verify my install is correct?

---

### Post by PhantomOG on 2008-08-16
bump for the weekend crowd.  I think this is probably a really easy problem to solve.  As I said above, I think I have properly installed the cisco vpn client, I just am having trouble actually calling it.
Thanks.

---

### Post by tamoneya on 2008-08-16
it may not have executable permissions.  Run this code to confirm:```
ls -l /opt/cisco-vpnclient/bin/
```

Also please do not bump a post for 24 hours.

---

### Post by PhantomOG on 2008-08-16
brian@laptop:~$ ls -l /opt/cisco-vpnclient/bin/
total 4240
---x--x--x 1 root bin 1241184 2008-08-15 21:43 cisco_cert_mgr
-rwsr-xr-x 1 root bin 2181944 2008-08-15 21:43 cvpnd
---x--x--x 1 root bin  226700 2008-08-15 21:43 ipseclog
---x--x--x 1 root bin  666260 2008-08-15 21:43 vpnclient

So I should be ok, right?

---

### Post by tamoneya on 2008-08-16
that looks correct to me.  Mine is very similar:```
tamoneya@tamoneyat61:~$ ls -l /opt/cisco-vpnclient/bin/
total 4240
---x--x--x 1 root bin 1241184 2008-06-19 09:27 cisco_cert_mgr
---s--x--x 1 root bin 2181944 2008-06-19 09:27 cvpnd
---x--x--x 1 root bin  226700 2008-06-19 09:27 ipseclog
---x--x--x 1 root bin  666260 2008-06-19 09:27 vpnclient
```

---

### Post by Skipster on 2008-11-12
> **tamoneya said:**
> that looks correct to me.  Mine is very similar:```
tamoneya@tamoneyat61:~$ ls -l /opt/cisco-vpnclient/bin/
total 4240
---x--x--x 1 root bin 1241184 2008-06-19 09:27 cisco_cert_mgr
---s--x--x 1 root bin 2181944 2008-06-19 09:27 cvpnd
---x--x--x 1 root bin  226700 2008-06-19 09:27 ipseclog
---x--x--x 1 root bin  666260 2008-06-19 09:27 vpnclient
```

was there any resolution to this? I seem to have the same problem...  everyone is there they just done want to work?.. :(

---

### Post by nstuart on 2008-11-14
I had the same problem with 8.10 64bit. Solution was to install lib32gcc1.

Seems to have taken care of it.

---

