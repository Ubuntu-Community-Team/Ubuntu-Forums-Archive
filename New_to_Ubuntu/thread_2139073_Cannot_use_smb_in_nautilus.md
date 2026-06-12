---
title: "Cannot use smb:// in nautilus"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by sysrpl on 2013-04-26
I have ubuntu 12.04 on another computer and by default I believe I could type "smb://192.168.1.150" (or whatever windows server address) and see shared folders. Now when I do that in 13.04 (64bit) nothing happens. If I select "Files | Connect to a Server ..." in the menu and fill out the dialog with the same information, again nothing happens. What gives? What can I try to fix this problem?

---

### Post by papibe on 2013-04-26
Hi sysrpl.

Could you post the result of these commands?
```
smbtree

apt-cache policy samba-common
```
Regards.

---

### Post by sysrpl on 2013-04-26
smbtree
WORKGROUP
	\\TERRAPC 
And then it kind of hangs. There are a few other pcs on my network which I usually connect to.

apt-cache policy samba-common
samba-common:
  Installed: 2:3.6.9-1ubuntu1
  Candidate: 2:3.6.9-1ubuntu1
  Version table:
 *** 2:3.6.9-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status

t seems to want to start working randomly. I think it's (smb or nautilus) buggy because I received a password/login prompt about 30 minutes after I gave up on it. I tried again and it work, but I received a timeout error after a while. On this same pc with a swapped out hard disk and 12.04 I have non of these problems, though that install was 32bit and this one is 64bit.

---

### Post by papibe on 2013-04-26
Do you have the same user and password as in 12.04? (thinking authentication problem here)

Regards.

---

### Post by sysrpl on 2013-04-26
Yes, I made the account the same name/password. Also, i'd like to add nautilus freezes quite a bit while navigating shared folders. And when I say a bit, I mean crashes.

---

