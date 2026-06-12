---
title: "Update manager notify"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by phil66 on 2012-09-19
Dell xps 600 plentiun d dual core 3.0 mhz
Nvidia ge 7900 gs
Ubuntu lucid 10.04

The update manager no longer send an icon to the task bar when there are updates available.

I can open the update manager by using the menu
The updates are listed in the manager and also in synaptic and they can be downloaded and installed from these sources.

This has only started a few updates ago

Any help !!!

---

### Post by daslinkard on 2012-09-20
Does it work correctly if you switch virtual desktops or does it act the same?

---

### Post by phil66 on 2012-09-20
Made change to configuration editor>apps>update-notifier

Unchecked auto_launch

I now get a different icon which is the old one..works I am now getting notices

I tried changing virtual desktop with no success

I was also able to find a bug even though it was mostly amd folks having to same problem

Thanks for the reply

---

### Post by kostkon on 2012-09-20
> **phil66 said:**
> Dell xps 600 plentiun d dual core 3.0 mhz
Nvidia ge 7900 gs
Ubuntu lucid 10.04

The update manager no longer send an icon to the task bar when there are updates available.

I can open the update manager by using the menu
The updates are listed in the manager and also in synaptic and they can be downloaded and installed from these sources.

This has only started a few updates ago

Any help !!!
I think your problem lies in the fact that Update Manager will only pop-up every 7 days, the only exception being when there are security updates available. In this case it will pop-up right away.

But when you open the update manager yourself and you check and install the updates you actually disrupt this 7-day cycle; thus, it will wait for another 7 days before poping-up again.

But in any case, you could check if update-notifier actually loads when you log in your desktop. After you login, just give in a terminal:
```
ps -A | grep update-notifier
```
It should output something along the lines of
```
2229 ?        00:00:02 update-notifier
```

Hope that helps.

---

### Post by phil66 on 2012-09-21
Thanks for the reply

I had checked the code you suggested prior to posting

The code showed the notifier to be uploaded and running in background.

The configuration of the notifier says every day or daily
That seems to be different than the seven days cycle you are talking about.

I remember having updates two days in a row and being notified

I will have to wait seven days to see if it now notify's with the changes I have made.

---

### Post by phil66 on 2012-09-26
The changes made to configuration>apps>update-notifier>auto-launch

Is now notifying both security and recommended updates on a daily basis

The icon in the taskbar has changed but still very recognizable 

Problem now solved

---

### Post by daslinkard on 2012-09-26
> **phil66 said:**
> The changes made to configuration>apps>update-notifier>auto-launch

Is now notifying both security and recommended updates on a daily basis

The icon in the taskbar has changed but still very recognizable 

Problem now solved

Awesome! Please mark this thread as solved!

---

