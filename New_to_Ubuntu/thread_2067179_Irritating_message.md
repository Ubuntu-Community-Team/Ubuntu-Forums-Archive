---
title: "Irritating message"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by Barney-R on 2012-10-06
Hello everybody,

I've been here a few times, but still consider myself a beginner, so I hope it's ok to post this here.

I'm using Ubuntu 10.10 Maverick, which is no longer supported, but Update Manager keeps giving me a message (red triangle) saying the update information is out of date.

When I try to check (merely to appease it in the hope of clearing that "warning"), it returns a couple of "404" page not found messages, so then I get a message saying the update failed, and the warning triangle is still there.

It's not a serious annoyance, but I'd like to find  a way of getting rid of it, perhaps by stopping Update Manager monitoring the system.

Does anyone know a way of doing this that won't affect anything else?

If I need to enter a terminal command, please try to keep it simple, or to explain each command. I've still got a lot to learn.

Btw, I'll be off-line for the next couple of days, but will check back next week.

---

### Post by cway00 on 2012-10-06
> **Barney-R said:**
> Hello everybody,

I've been here a few times, but still consider myself a beginner, so I hope it's ok to post this here.

I'm using Ubuntu 10.10 Maverick, which is no longer supported, but Update Manager keeps giving me a message (red triangle) saying the update information is out of date.

When I try to check (merely to appease it in the hope of clearing that "warning"), it returns a couple of "404" page not found messages, so then I get a message saying the update failed, and the warning triangle is still there.

It's not a serious annoyance, but I'd like to find  a way of getting rid of it, perhaps by stopping Update Manager monitoring the system.

Does anyone know a way of doing this that won't affect anything else?

If I need to enter a terminal command, please try to keep it simple, or to explain each command. I've still got a lot to learn.

Btw, I'll be off-line for the next couple of days, but will check back next week.

**This will only stop the update notifier **

In your terminal, type the following command:
```
gconftool [COLOR=#660033]-s[/COLOR] [COLOR=#660033]--type[/COLOR] bool [COLOR=#000000]**/**[/COLOR]apps[COLOR=#000000]**/**[/COLOR]update-notifier[COLOR=#000000]**/**[/COLOR]auto_launch [COLOR=#c20cb9]**false**[/COLOR]
```To recover 
```
gconftool [COLOR=#660033]-s[/COLOR] [COLOR=#660033]--type[/COLOR] bool [COLOR=#000000]**/**[/COLOR]apps[COLOR=#000000]**/**[/COLOR]update-notifier[COLOR=#000000]**/**[/COLOR]auto_launch [COLOR=#c20cb9]**true**[/COLOR]
```Hope it helps

---

### Post by Barney-R on 2012-10-06
That was quick! Thank you cway00.[U]

[/U]

---

### Post by Cheesemill on 2012-10-06
If I were you I would seriously consider upgrading to a later version.

As 10.10 has reached end-of life you no longer receive any support or security updates, meaning that your system is wide open to attacks that use exploits that have been discovered in the last 6 months.

---

