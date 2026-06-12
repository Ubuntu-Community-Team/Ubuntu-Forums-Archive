---
title: "[SOLVED] OpenSSL - Keys reset - known_hosts"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by BassKozz on 2008-05-24
I recently did an update using the "Update Manager" that updated OpenSSH + OpenSSL on both of my machines (1 xubuntu 1 ubuntu), I use SSH to connect to these machines all the time... Well now when I try to connect I get the following error:
> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
82:3e:28:fd:13:eg:62:47:1b:**:**:**:**:**:**:**.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:2
RSA host key for 192.168.**.*** has changed and you have requested strict checking.
Host key verification failed.
So can I just delete the ***known_hosts*** file and it will reset and use the new keys? or is that not a safe move?

---

### Post by Heinzelotto on 2008-05-24
if it's just 2 machines, remove the ~/.ssh directory, it'll ask you next time you connect to those machines if you trust them and if you answer yes it'll add the correct keys.

---

### Post by Monicker on 2008-05-24
Its line 2 which is the problem.  You can open it with a text editor and just remove that line specifically.

---

### Post by Heinzelotto on 2008-05-24
> **Monicker said:**
> Its line 2 which is the problem.  You can open it with a text editor and just remove that line specifically.

are you sure? I think what's meant is the second key in that file.

---

### Post by Monicker on 2008-05-24
I'm positive.  Its one key per line.

---

### Post by BassKozz on 2008-05-24
What's the down side to just removing all the keys from ***known_hosts***?
Won't that just issue new keys for all hosts I connect to via SSH? Is this a security concern?

---

### Post by Monicker on 2008-05-24
You will be prompted to verify that you want to accept the keys for any other servers in your known_hosts file again the next time you connect to them.  Ideally you should already know the ssh fingerprint for any keys you accept, so that you can be sure they are legitimate, and not the result of a man in the middle attack.

---

### Post by BassKozz on 2008-05-24
Removed line 2 and were good 2 go, Thanks guys :)

---

### Post by Chokkan on 2008-05-27
I had the exact same problem including scary message and deleting the offending key solved my problem.

---

### Post by ericdegen on 2008-05-29
Thanks Heinzelotto, worked like a charm!

---

### Post by irvingswiftj86 on 2010-02-26
Thanks...this really helped me out....I just had to delete the ~/.ssh folder .:D

---

