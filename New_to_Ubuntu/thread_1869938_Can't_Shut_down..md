---
title: "Can't Shut down."
date: 2011-10-26
forum: New to Ubuntu
---

### Post by Keshav2050 on 2011-10-26
Today I have upgraded my ubuntu 11.04 to 11.10. I can't shut down the system its just getting logged out.
I have typed the command 'sudo apt-get update' and I got

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

what can I do?

---

### Post by ArgusVision on 2011-10-26
There have been a lot of apt-get problems with 11.10. I'll try to research and get back to you if someone doesn't beat me to it.

As far as shutting down goes, the commmand line way is:

```
sudo shutdown -h now
```

You can check **man shutdown** for more options

---

### Post by Keshav2050 on 2011-10-27
Now the PC's shutting down directly by clicking shut down. Thanks anyway, but what are those errors?

---

### Post by Atryxx on 2011-10-27
does aptitude work for you?
ro do you get the same error??

---

### Post by Silent Warrior on 2011-10-27
Keshav2050: I'm pretty much 100% certain you get those messages because two different applications are trying to update your APT cache. (Update Manager at the same time as Muon, PackageKit or Synaptic?) To get rid of those messages, simply close whatever updater or other is trying to refresh the cache and try updating again with the updater you left running. If that doesn't work, do this when the errors show up (and ONLY then!):
sudo rm /var/lib/apt/lists/lock

This removes some kind of 'lock' on the APT cache file, which I think is put in place as part of normal APT operations.

If you have the option of delaying an update check in whatever program, consider changing the delay. 15 seconds in either direction should be enough.

---

### Post by Keshav2050 on 2011-10-27
Thanks, there were no errors this time. So no problem. Everything went on smoothly without any errors.

---

