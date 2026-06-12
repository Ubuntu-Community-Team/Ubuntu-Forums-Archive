---
title: "Enabling empathy accounts through filesystem"
date: 2010-10-25
forum: Programming Talk
---

### Post by jabalsad on 2010-10-25
Hi all,

I'm trying to figure out if there is an easy way to disable/enable empathy accounts through the file system (like editing a file or something).

I've learnt that Empathy uses the mission-control library to keep track of its accounts, and it seems to use the location under $HOME/.mission-control to write some of the account data to disk. However this seems to be more like an output than anything else since editing it doesn't actually make any changes.

The next step would be to dig into the mission-control libraries but I'm hoping I can avoid that. Do you guys have any suggestions?

Much appreciated.

---

### Post by jabalsad on 2010-10-25
I think I figured out what I was doing wrong...

Whenever I edited the accounts data under ~/.mission-control, I only killed Empathy to see whether I made any changes. Turns out there was another process called mission-control-5 that was still running. When I also killed that then the changes would be visible next time I start Empathy.

---

