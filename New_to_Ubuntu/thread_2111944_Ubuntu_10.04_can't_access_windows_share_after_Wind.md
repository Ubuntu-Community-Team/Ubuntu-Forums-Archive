---
title: "Ubuntu 10.04 can't access windows share after Windows 8 upgrade"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by EEE901 on 2013-02-03
Hello,

I've been using Ubuntu Netbook Edition for a couple of years now. I upgraded my main PC from Vista to Windows 8. I want to reach a Windows share which went well in Vista. Now it keeps prompting my for a username/password. On a Win7 laptop the share is reachable without credentials.

The netbook (ubuntu 10.04) shows up when I browse the network on the Win8 PC and vice versa.

The NMDB & SMDB services are running. When I run: sudo service samba start, I get: unrecognized service.

Any ideas? Which credentials should I use? I tried the username/password of the regular account of the main PC and also of the Ubuntu Laptop. I even created a identical named account on the Win8 Pc.

I use the netbook mainly for streaming some video from the main PC, so I really like to have the share!

Thanks in advance.

---

### Post by EEE901 on 2013-02-04
Hello,

I've been using Ubuntu Netbook Edition for a couple of years now. I  upgraded my main PC from Vista to Windows 8. I want to reach a Windows  share which went well in Vista. Now it keeps prompting my for a  username/password. On a Win7 laptop the share is reachable without  credentials.

The netbook (ubuntu 10.04) shows up when I browse the network on the Win8 PC and vice versa.

The NMDB & SMDB services are running. When I run: sudo service samba start, I get: unrecognized service.

Any ideas? Which credentials should I use? I tried the username/password  of the regular account of the main PC and also of the Ubuntu Laptop. I  even created a identical named account on the Win8 Pc.

I use the netbook mainly for streaming some video from the main PC, so I really like to have the share!

Thanks in advance.

---

### Post by oldfred on 2013-02-04
Threads merged. Please do not post the same question in two sub-forums.

---

### Post by EEE901 on 2013-02-05
> **oldfred said:**
> Threads merged. Please do not post the same question in two sub-forums.

You're right! I wasn't sure which sub-forum to post.

Any suggestions about my problem people?

---

### Post by EEE901 on 2013-02-06
I fixed the problem by installing Lubuntu 12.04 on the netbook. When I mount a networklocation it asks for credentials. When I "cancel" the underlying folder does appear, which it didn't under Ubuntu Remix 10.04. I can also fill in the username/password combination I use on the Win8 machine. It remembers the setting also for other shares.

Thanks for all the answers! The thread can be marked as solved and closed.

---

