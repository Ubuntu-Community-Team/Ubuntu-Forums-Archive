---
title: "avahi says not recomended,or compatible? re: port forwarding"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by Un_Known on 2014-07-17
i managed to successfully set my sky hub wifi router to port forward for a TCP connection (nicotine+ in this instance)
however, i now get a notification at top left of my desktop saying something along the lines of me seeming to have a .domian present, and this is not recomened, nor compatible with avahi network discovery.
any advice? why wouldnt i be able to set a simple port forwarding?
or has something else happened there?

i noticed that i did get search results with nicotine before i set router to port forward for nicotine, now i get nothing!

---

### Post by Un_Known on 2014-07-17
oh,and thanx by the way!

---

### Post by steeldriver on 2014-07-17
Port forwarding itself shouldn't have caused that - did you also try to set up some kind of dynamic hostname updater (like dyndns) as well?

---

### Post by Un_Known on 2014-07-17
> **steeldriver said:**
> Port forwarding itself shouldn't have caused that - did you also try to set up some kind of dynamic hostname updater (like dyndns) as well?

thanks steeldriver!
to be honest, i dont even know what that is!
i guess the answer is no!

---

### Post by Un_Known on 2014-07-17
incidently,i am getting a very limited connection now,with my app that needs port forwarding, but not very good though.

---

### Post by steeldriver on 2014-07-17
can you describe what actual changes you made on the router?

---

### Post by Un_Known on 2014-07-17
changes?

adding a service:
type of service: nicotine (tho actually thats just the name i called it,its actually a TCP (something):80
ports:               2234to 2240[TABLE="class: nospace, width: 650"]
[TR="class: header"]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]


router firewall:

yes,
type of service        (TCP set to the particular tcp i opened for nicotine)
action                   (always allow)
send to LAN server (IP inserted)
WAN users             (any)   < i didnt understand that one
start                      (left blank) <i didnt know what to put there
finish                      (left blank)<i didnt know what to put there
log                          (didnt bother setting it to keep log)

---

