---
title: "[SOLVED] Clean Install"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by lucasl on 2008-11-02
My sound recently stopped working, and I really can't wait for an upgrade to fix it. Instead its probably easier to do a clean install (sound works on the Live CD). I have a separate home partition, so it shouldn't be too difficult.
I basically have 2 questions:
1. Should I change permissions on my home folder before installation or after?
2. Is there a way I can get a list of packages that I have installed manually which aren't included? I was thinking doing a diff between the live cd and my installation but I can't exactly remember how to do this.
Also, is there anything else I should do (other then backup my data)?

Thanks!

---

### Post by lucasl on 2008-11-02
```
dpkg --get-selections > pkgs.txt
```
Was what I was looking for. I did this on my install and the live cd, then opened both in Meld. I went through and made a list of things I'd need to install. Surprisingly, the list came to only ~15 packages (not including dev libraries which I'll install as needed).

As for permissions, I'm sure it won't make a HUGE difference, so I'll just mark this as solved.

---

