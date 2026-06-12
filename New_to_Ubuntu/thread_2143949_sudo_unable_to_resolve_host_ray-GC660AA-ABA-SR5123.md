---
title: "sudo: unable to resolve host ray-GC660AA-ABA-SR5123WM"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-05-10
i googled and tried all morning to correct the above error message but have failed.
here is output for etc/hostname

ray-GC660AA-ABA-SR5123WM
here is output for etc/hosts

127.0.0.1	localhost
127.0.0.1	ray-GC660AA-ABA-SR5123WM


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

best way to correct tks

---

### Post by TheFu on 2013-05-10
What does `hostname` return?  Also, 127/8 networks are internal use only. No other machine will be able to ssh into it.  The remote host needs to nkow the name/IP cross-reference. This is accomplished either via a DNS server (perhaps the router?) or by editing every /etc/hosts file for every PC on the network.

---

### Post by rburkartjo on 2013-05-10
sudo gedit /etc/hostname
sudo: unable to resolve host ray-GC660AA-ABA-SR5123WM

---

### Post by TheFu on 2013-05-10
> **rburkartjo said:**
> sudo gedit /etc/hostname
sudo: unable to resolve host ray-GC660AA-ABA-SR5123WM

So, the issue is only with sudo?
What does `**hostname**` return ... the command, not the file? 

If this is an issue with sudo, I'd restore from the last known working backup of the /etc/sudoers file, if that is possible. All should be fine then.
If that isn't possible, boot off a liveCD, mount the partition with /etc inside and fix the sudoers file manually.  **man sudoers** will explain the format.

---

### Post by rburkartjo on 2013-05-12
going to bump this once and then live with it. just bugs me that i cant find a fix that works.

---

### Post by CatKiller on 2013-05-12
You could try responding to TheFu.

---

### Post by rburkartjo on 2013-05-12
cat that wont help. have tried everything i have found online including what  thefu suggested. couldnt get that to work. i am not the only one having this problem lots of posts on google about. tks for your suggestion maybe problem will be resolved when i upgrade to 13.10 in october.

---

### Post by CatKiller on 2013-05-12
The only time I've seen this error is when there's a problem with the hostname. You've shown that /etc/hosts and /etc/hostname give the same name for your computer, but you haven't said what your computer thinks it's called by the output of the hostname command, nor have you said if you've restarted at any point.

---

### Post by TheFu on 2013-05-12
> **rburkartjo said:**
> cat that wont help. have tried everything i have found online including what  thefu suggested. couldnt get that to work. i am not the only one having this problem lots of posts on google about. tks for your suggestion maybe problem will be resolved when i upgrade to 13.10 in october.

You've provided an overwhelming amount of data, just not the requested data. We can't help if you don't run the command AND show the output. Oh well.  

What about running **hostname** didn't work? If that is failing, you have much bigger issues.

Also, I've never setup my real hostname on a 127/8 network. Seems counter productive since other machines can't communicate and THAT is the purpose of having a network. Whatever. You could ahve very specific reasons to do that - I don't know.

We really did want to help.

---

