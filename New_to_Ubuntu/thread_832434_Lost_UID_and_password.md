---
title: "Lost UID and password"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Dawgwalker on 2008-06-17
I've done a fourth or fifth install of HH because of networking issues.  Was dualbooting with W2K on a Linksys WRT54G fast e wired network.

Could never see network and think it was because W2K did not release ip so HH could use.   

Install of HH removed the W2K partition and my plan to force w2k ip release went down.   I now only have HH, but cannot signin.

HH does not recognize my username/password combo, one of the reasons for the new install.  Have used same u/p

I can get to "grub".  Can I get to "root" from "grub" and issue a command to id the username and reset the password?

If can do can I please have straightforward directions that I can take from this Vista machine into the other room where sits HH.

ubuntu 8.04

---

### Post by wormser on 2008-06-17
It sounds like you need to get the user name and reset the password.  Boot into recovery mode.  The first command will show you the users names.

```
ls /home
```

Now we reset the password.

```
passwd username
```

```
reboot
```

---

### Post by cariboo on 2008-06-17
Once you got your password problem fixed why not tell us about your network problem, In a Applications-->Accessories-->Terminal type:

```
lspci
```

just highlight the output and paste it in your next post.

Jim

---

### Post by aysiu on 2008-06-17
This should help:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Dawgwalker on 2008-06-17
Thanks for responses.

Determined user name and password.  Problem for future reference came from naming computer and account the same.  Made my uid "uiduid".

Now for network.  I don't know how to paste from HH on another machine to this Vista machine with internet access.

ifconfig shows
rx 596 no errors
tx 596 no errors

ifconfig eth0 shows
rx o
tx o

My router shows no DHCP for HH.

What are the commands for ip release and renew in HH?

I cannot ping another ip.  I have DHPC manually configured and typed my router ip in for nameserver.  No ip show for nameserver when I use HH Network to experiment with that ip.  I suspect DNS but cannot verify my nic is correctly configured.

lspci returns ADMtec MC100 etc. nic; it is actually Linksys branded but maybe.

Thanks for your assistance.  Getting to the internet will greatly simplify solving other issues.

---

