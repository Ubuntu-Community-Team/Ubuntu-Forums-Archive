---
title: "X windows question"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by timandjulz on 2008-05-30
I have a high powered machine I want to share.  I want my wife and kids to have cheap computers that act like terminals connecting to my desktop.  (quad core, 64bit Ubuntu 8.04, 8gb memory)

I do not want to use VNC.

What is wrong with this plan?  Things I can think of:
1. Will sound play on the remote machines?
2. They will not be able to use USB devices (cameras, etc.) since the USB device won't connect to my machine.
3. GUI performance may suffer.
4. Will some apps not like this configuration?  (seems like all X apps should automatically work)
5. How will I boot directly into an X connection to the main desktop?

Any hints or suggestions would be appreciated.

Thanks,
Tim

---

### Post by wolfen69 on 2008-05-30
do your wife and kids do simple things? if so, it seems like alot of work for very little payoff. plus, if they have cheap computers, connecting to fast machine wont make the experience better. a chain is only as strong as the weakest link.

---

### Post by timandjulz on 2008-05-31
Yeah.  Partly, this is a learning experience.  I would like to understand this beast better.

But also, I want to have only one computer running all the time.  Right now I have 5 running at once.  I am hoping to eventually run diskless workstations connecting.

Benefits would be less power consumption.  The worksation computers would boot and connect in... hoping... less than 30 seconds.  Also easier to administrate.  And easier to screw everyone up at once.  :-)

Mainly though, I want to learn more about X.  Any feedback on my previous list?

---

### Post by timandjulz on 2008-06-01
So far it looks like X is not good for running a desktop remotely.

First, sound is not supported.

Second, performance via standard Ubuntu packages stinks (Terminal Server Client and XNest) even when connected via gigabit switch.

---

