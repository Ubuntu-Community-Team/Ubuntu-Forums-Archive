---
title: "vmware install - firefox prob"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by HypNemes on 2008-05-14
[actually posted this in network section by mistake - so reposed here]

Hello all.

I'm new to linux and am checking it out via using vmware on my winxp system.

I'm using xubuntu latest v installed via vmware.

I'm having trouble with firefox 3 - which "for some unknown reason" is the defualt browser instead of a more stable current ver..

Anyways whats happenign is, everytime i click "bookmark" for a webpage, firefox just crashes.

It also crashes if i click the "organise bookmarks" link under bookmarks button.

Any ideas?

If answer is simply install ff 2... for a more curremt stable ver.. how do i go about uninstalling ff3?

Thanks in advance..

---

### Post by Xiong Chiamiov on 2008-05-15
The general guide to installing things in ubuntu is [here]("http://monkeyblog.org/ubuntu/installing/").  Some things will be slightly different, since you're using xfce, but the core will all be the same.  Specifically, you'll want to do this in the terminal:
```

sudo aptitude remove firefox-3.0
sudo aptitude install firefox-2

```
And yes, it's probably a firefox3 problem.

You can also try out Wubi, which installs *buntu like a program in Windows, but runs it separately, rather than inside of Windows like VMware.

---

