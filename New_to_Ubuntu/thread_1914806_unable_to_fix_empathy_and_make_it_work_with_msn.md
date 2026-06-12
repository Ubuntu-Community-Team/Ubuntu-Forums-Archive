---
title: "unable to fix empathy and make it work with msn"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by carega on 2012-01-25
hello there... i've tried it many times and it's just not working for me.

I've installed ubuntu 10.10 a few hours ago and I've been having a problem with empathy where it keeps trying to log in but never actually gets to do it. I found a solution on the internet where i should do this: 

**gksudo gedit usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py**

[LIST]
[*]Search for a line which contains
[/LIST]
**CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")**

[LIST]
[*]Replace that line to
[/LIST]
**CONTACTS = ("contacts.msn.com", "MBI")**

[LIST]
[*]Save the file and restart Empathy. MSN should work now.
[/LIST]
(source: [http://techepisode.com/fix-msn-bug-empathy-ubuntu-10-10/](http://techepisode.com/fix-msn-bug-empathy-ubuntu-10-10/) )

Anyway, the problem is that when I go and try to modify the file... it's blank! and when i close it the system asks me if i want to keep the changes i've made... but i haven't touched a thing!

Can anyone help me please? i'm kinda desperate here... i don't know what to do...

EDIT: I fixed the issue already.

---

