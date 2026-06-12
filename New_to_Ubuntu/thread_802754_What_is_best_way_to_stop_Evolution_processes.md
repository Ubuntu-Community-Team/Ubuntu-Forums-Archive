---
title: "What is best way to stop Evolution processes?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by SlappyPappy on 2008-05-21
I see three items running for Evolution but I don't even use it. I tried to remove evolution but it told me it couldn't because something else depended on it.

What is the best way to keep Evolution processes from running? Thanks.

---

### Post by neurostu on 2008-05-21
Do these processes start upon boot?

Have you tried using sudo kill?

try:
```

ps -A | grep evolution

```
this will list all processes with evolution in the name. It will have a 4 or 5 digit number associated with each one. To kill the processes type:
```

sudo kill -9 ####

```
You can replace #### with one pid (process id) or list the pid of every process you want to kill.

I think this answers your question...

---

### Post by SlappyPappy on 2008-05-21
They do start at boot. How can I make it so that they don't start at boot?

Thanks for the help man.

---

### Post by neurostu on 2008-05-21
what processes are they exactly?

---

### Post by aktiwers on 2008-05-21
In System => Preferences => Sessions

There is a program called Evolution-alarm or something..  you could disable that.

Is that the process you are talking about?

---

### Post by SlappyPappy on 2008-05-22
evolution-alarm-notify
evolution-data-server-1.0.2
evolution-exchange-storage

I mean, what do I need these things running for? Don't use evolution.

---

### Post by stchman on 2008-05-22
> **SlappyPappy said:**
> I see three items running for Evolution but I don't even use it. I tried to remove evolution but it told me it couldn't because something else depended on it.

What is the best way to keep Evolution processes from running? Thanks.

Remove Evolution.

```
sudo apt-get autoremove evolution
```

---

