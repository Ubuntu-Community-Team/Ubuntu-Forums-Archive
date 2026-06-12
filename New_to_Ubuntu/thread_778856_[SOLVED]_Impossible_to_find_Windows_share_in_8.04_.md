---
title: "[SOLVED] Impossible to find Windows share in 8.04 but not in 7.10"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by MockY on 2008-05-02
When I ran 7.10, I had no issues sharing folders in one of my Windows servers. I could connect to it just fine. However, once I installed 8.04, this ability was removed. I can browse the network and the server is found, but once logged on (double clicking on the server), no share's are listed, nor the drives. What is missing in my default 8.04 install?

---

### Post by andrewbrown22 on 2008-05-02
Samba is broken in 8.04.
Open Computer and type in smb://[IP address]/sharename
and it'll work for now.
Should be fixed soon, hopefully.

---

### Post by brigux on 2008-05-02
Hi Had this problem too... Just rebooting the linux fixed it, no kidding.
alternative solution: open \\windowsShar\C$, just to force the RE-authentication process. stupid, yes, but working.

---

### Post by brigux on 2008-05-02
> **brigux said:**
> \\windowsShar\C$

smb://[IP address]/sharename 
...indeed :-)

---

### Post by MockY on 2008-05-02
Very bizarre that a later version of Ubuntu breaks something that already works, and is then released with this issue. Well thanks for the information, now I know that it is not on my end.

> Open Computer and type in smb://[IP address]/sharename

This worked like a charm. Thanks

---

### Post by wmf on 2008-05-02
I am having the same problem... using the smb://[IP Address]/[Sharename] comes back with an authentication error. It just says that I don't have permissions to view the contents... Sigh, I would be happy to provide the authentication, but can't figure out where. In the past, first time connection to a share would kick open the Keyring, ask for username/password and from then on always connect.

---

### Post by bhold on 2008-05-02
I was able to work around this problem by installing smbfs, then mounting the share. After installing smbfs do "man smbmount" on the command line in a terminal window, it will show you the required syntax.

---

### Post by Jerry N on 2008-05-02
I solved the problem by returning to Gutsy and LinuxMint 4.0.  Hopefully the upcoming LinuxMint 5 release will properly fix the problem. 

Jerry

---

### Post by MockY on 2008-05-03
Though work around worked, Hardy Heron is a hot mess and nothing seem to work like it should. So I am doing the same, but Feisty for me.

---

### Post by wmf on 2008-05-06
I found a pretty good workaround to get a Windows AD Share mounted up.
See this thread[http://ubuntuforums.org/showthread.php?t=783552&highlight=samba]("http://ubuntuforums.org/showthread.php?t=783552&highlight=samba")

Not pretty, but gets the share fully visible from your home folder.

---

### Post by linuxmonkey on 2008-05-25
Has this been fixed yet?

---

### Post by MockY on 2008-05-30
Yeah, I wonder that too.
Been running Linux Mint ever since the release of Hardy and I want our favorite distro back on my computer. I am downloading the latest iso as we speak and hope that this issue is resolved by now.

EDIT:
Booted the latest ISO and the problem persists.
It extremely odd that this issue is still around. Since it worked before, it really can't be that hard to fix it. But what do I know. All I can do is wait.

---

### Post by MockY on 2008-11-03
In the release candidate of Ibex, this issue was finally resolved. But once the final release was out, the issue was back. What the hell is that all about? I am very confused why this is still an issue. Downright pathetic.

---

