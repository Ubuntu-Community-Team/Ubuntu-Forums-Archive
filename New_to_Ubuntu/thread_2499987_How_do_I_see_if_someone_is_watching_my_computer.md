---
title: "How do I see if someone is watching my computer?"
date: 2024-08-17
forum: New to Ubuntu
---

### Post by ralle12 on 2024-08-17
Hello, 
I'm rater new to Ubuntu and see some services on with SSH for example and some weird things according to me in wireshark. How can I see if only I'm logged in and no one is mirroring my screen or taking information like log-in credentials and stuff? 

Can I do any command that do so only I can make connections to websites and so so? And use the computer like I use to but be sure it's not mirrored or someone taking information of my computer?

Would love all the help I can get!

Regards Rasmus

---

### Post by #&amp;thj^% on 2024-08-17
> **ralle12 said:**
> Hello, 
I. How can I see if only I'm logged in and no one is mirroring my screen or taking information like log-in credentials and stuff? 

Can I do any command that do so only I can make connections to websites and so so? And use the computer like I use to but be sure it's not mirrored or someone taking information of my computer?

Would love all the help I can get!

Regards Rasmus
To see logins:
```
last
```
to look at network activity:
```
sudo tcpdump -i ethX icmp and icmp[icmptype]=icmp-echo
```
Replace ethX with your device. Use "ip a" to see.

TCDump has flags as well:
```
-n avoid a (potentially slow) reverse DNS query
&#8722;i interface
icmp[icmptype]=icmp-echo    To print all ICMP packets that are echo requests/replies

```

---

### Post by currentshaft on 2024-08-18
,

---

### Post by Rubi1200 on 2024-08-18
Perhaps if you post some of these "weird" results someone would be able to offer a better analysis.

---

### Post by ralle12 on 2024-08-20
Thank you this helped me alot ty! rather new to Ubuntu as told so these commands can be hard to form yourself in the beginning!, ty!

---

### Post by ralle12 on 2024-08-20
True, I have not done that, ifm it's no default config. But I think its rather not, right?

---

### Post by ralle12 on 2024-08-20
very true, i will check later at home imf i have a dump from wireshark or so. Otherwise I will listen again and see if i "see" these what I think mysterious things are.

---

