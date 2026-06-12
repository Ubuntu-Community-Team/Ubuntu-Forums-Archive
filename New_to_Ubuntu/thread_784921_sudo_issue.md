---
title: "sudo issue"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by asmodaeus on 2008-05-06
Since I installed the new version, sudo commands aren't working at all, and the App Manager is not working either, along with the package manager. This is only happening on my laptop however, it seems to be workable on my desktop, which also has the new version. 

This is what I get when I try to update the package manager in the terminal

michael@michael-laptop:~$ sudo apt-get update
sudo: unable to resolve host michael-laptop

what should I do?

---

### Post by HotShotDJ on 2008-05-06
> **asmodaeus said:**
> michael@michael-laptop:~$ sudo apt-get update
sudo: unable to resolve host michael-laptop

what should I do?You'll need to reboot into recovery mode (press "esc" key at the grub prompt when your booting up and select the first recovery mode entry you see)

When you get to the scary text prompts :)  type: ```
nano -w /etc/hosts
```
The contents should look something like this:
```
127.0.0.1       localhost
127.0.1.1       michael-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
The first and second line are the important ones.  After editing the file (if it needs editing), press ctrl+x and answer yes to save.  Then reboot normally.

---

### Post by asmodaeus on 2008-05-06
Thanks, I'll have to do this on my laptop when I get home and can look at this thread on my desktop. I'll report the results.

---

