---
title: "evolution notify"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-07
when evolution notifies about news emails is it supposed to run the same time? 
or am i able to be informed without having evolution open all the time (and also without having to install anything extra)..

i think once i was notified by surprise  while it was closed(at least i have the impression)

---

### Post by Joeb454 on 2008-05-07
I think it has to be running, Though it can obviously be minimised (to the bottom panel or to the tray). Or kept on a separate workspace :)

---

### Post by lunaluna on 2008-05-07
> **Joeb454 said:**
> (to the bottom panel or to the tray)

"tray" how ?

---

### Post by Joeb454 on 2008-05-07
Search synaptic for alltray or open up a terminal and do ```
sudo aptitude install alltray
```

Run it from Applications > Accessories and then click the app you want to minimize to the tray :)

Note: By tray - I mean the top panel on the right :)

---

### Post by lunaluna on 2008-05-07
> **Joeb454 said:**
> Search synaptic for alltray or open up a terminal and do ```
sudo aptitude install alltray
```

Run it from Applications > Accessories and then click the app you want to minimize to the tray :)

Note: By tray - I mean the top panel on the right :)

if you go to the sessions preferences you'll see that ubuntu by default has 
"Evolution Alarm Notifier" 
command: /usr/lib/evolution/2.22/evolution-alarm-notify   :popcorn:

so why i have to open everytime evolution?

---

### Post by ilcavero on 2008-05-12
I wonder the exact same thing, what's the point of this 1.7Mb process? just to popup if you happen to have evolution already opened?

---

### Post by lunaluna on 2008-05-12
can someone more advanced reply to us (a developer maybe lol )
maybe it does work alone....

---

### Post by lunaluna on 2008-05-13
bump

---

### Post by logx on 2008-05-14
Hello,

The alltray app is working fine for me!

No need to have evolution "open" as another window anymore to be able to receive the email notifications.

Great!

Thnx

---

### Post by lunaluna on 2008-05-14
> **logx said:**
> Hello,

The alltray app is working fine for me!

No need to have evolution "open" as another window anymore to be able to receive the email notifications.

Great!

Thnx

the point is evolution have a native notification feature...
why it doesn't work

---

### Post by Joeb454 on 2008-05-14
Is it not showing the notifications then?

---

### Post by lunaluna on 2008-05-14
> **Joeb454 said:**
> Is it not showing the notifications then?

no it does not...

---

### Post by sysex on 2008-05-15
well what I did was went: system > preferences > sessions
at the 'start up programs' tab I removed the tick just cause I wanted the mail client to only use the internet line when I open it.

the funny thing is that even after that, Evolution Mail knows about the new mails when I run it.

any ideas ? :D

---

### Post by stchman on 2008-05-15
> **lunaluna said:**
> when evolution notifies about news emails is it supposed to run the same time? 
or am i able to be informed without having evolution open all the time (and also without having to install anything extra)..

i think once i was notified by surprise  while it was closed(at least i have the impression)

Yes, Evolution needs to be running for it's notification feature to work.

If you want to be notified of incoming mail without Evolution being launched use the package mail-notification.  You can install it in your sessions profile so it will launch at startup.

---

### Post by lunaluna on 2008-05-15
> **stchman said:**
> Yes, Evolution needs to be running for it's notification feature to work.

If you want to be notified of incoming mail without Evolution being launched use the package mail-notification.  You can install it in your sessions profile so it will launch at startup.

tried mail notification didn't work...use gnubif instead(nice)

but what is the point for evolution to have such an notification feature if it cant notify by default...?

---

