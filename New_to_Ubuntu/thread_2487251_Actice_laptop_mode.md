---
title: "Actice laptop mode"
date: 2023-05-28
forum: New to Ubuntu
---

### Post by hejmattias on 2023-05-28
Hello!

I am new to Ubuntu, migrated from Windows. I have figured out some basics with the help of this forum, among other sources. However, I am running Ubuntu on my laptop, and it has been running hot constantly and is draining battery at an alarming rate. I have tried for hours to activate laptop mode but I just cannot seem to do it. I have installed laptop mode tools, but I cannot save any of the options. It just says "Could't apply all options" even if I don't cross any of the options available. What can I do?

Kind regards
Mattias

---

### Post by Impavidus on 2023-05-29
There's a tool called "Additional drivers". Check it; maybe some proprietary graphics driver is available that may help. That's one of the more common causes for this problem.

Find out what process takes all that CPU time. And can you tell a bit more about your hardware?

---

### Post by hejmattias on 2023-05-29
Thank you for your help! I installed a proprietary driver now and I will see if that helps some.

It seems I don't have a lot of processes. Gnome shell takes the most and it's just a few percent cpu. So I really don't understand what would take up so much power.

I use a i7-9750H CPU @ 2.60GHz
GTX 1660 ti mobile
1 tb ssd
32 gb ram

---

### Post by grahammechanical on 2023-05-29
I have a laptop with an Intel i7-1051OU CPU running at 1,8GHz. Which is a lot slower that the 2.60GHz that your CPU is running at. I am using Ubuntu 20.04 which does not have a means to change the power settings in System Settings. So, I guess that the power setting is set in the UEFI settings utility.

I also have Ubuntu 22.04 installed and the Setting Settings>Power tab has options to change the power settings.

Performance = High Performance & Power usage
Balanced = Standard Performance & Power usage
Power Saver = Reduced Performance & Power usage.

My machine is set to Balanced. I have not tried to change it. If I try to change it and am not allowed to, it could mean that the setting in UEFI is overriding the setting in System Settings.

Regards

---

### Post by ActionParsnip on 2023-05-30
Does the system have a make and model?

---

### Post by hejmattias on 2023-05-30
> **grahammechanical said:**
> I have a laptop with an Intel i7-1051OU CPU running at 1,8GHz. Which is a lot slower that the 2.60GHz that your CPU is running at. I am using Ubuntu 20.04 which does not have a means to change the power settings in System Settings. So, I guess that the power setting is set in the UEFI settings utility.

I also have Ubuntu 22.04 installed and the Setting Settings>Power tab has options to change the power settings.

Performance = High Performance & Power usage
Balanced = Standard Performance & Power usage
Power Saver = Reduced Performance & Power usage.

My machine is set to Balanced. I have not tried to change it. If I try to change it and am not allowed to, it could mean that the setting in UEFI is overriding the setting in System Settings.

Regards

Thank you for a good reply! And is everything working fine with your lower clock speed? 

It might be the case what you are suggesting actually. I also have a physical button on my keyboard which switches from power saving mode, to normal mode to performance mode. I guess that when I changed the power options in the UEFI settings, it may have overrided the aforementioned power settings. However, if I keep the power settings in UEFI to normal, does it matter what power settings I have on my physical button?

Kind regards

---

### Post by hejmattias on 2023-05-30
> **ActionParsnip said:**
> Does the system have a make and model?

Unfortunately, it does not. It is a custom build from a local company. Can that also cause problems?

Kind regards

---

### Post by MAFoElffen on 2023-05-31
FYI to all, what those settings panels connect to on the backend, listing and setting from the command line looks like this...

Since different machines have differing options, to list what is available on that machine, do this
```

mafoelffen@Mikes-B460M:~$ powerprofilesctl list
* performance:
    Driver:     intel_pstate
    Degraded:   no

  balanced:
    Driver:     intel_pstate

  power-saver:
    Driver:     intel_pstate

```
which will list all available power profile options, and indicate which is selected with an asterisk ( * ).

Then this will show you which power profile is selected, and what driver it uses on that machine to set that.
```

mafoelffen@Mikes-B460M:~$ powerprofilesctl get
performance

```
Replace 'get' with 'set' and the profile name, and it will set the power profile to that profile.

Note that there is no man page for this utility.

---

### Post by ActionParsnip on 2023-06-01
> **hejmattias said:**
> Unfortunately, it does not. It is a custom build from a local company. Can that also cause problems?

Kind regards

No that's fine. Just helps narrow searches down

---

### Post by hejmattias on 2023-06-02
> **MAFoElffen said:**
> FYI to all, what those settings panels connect to on the backend, listing and setting from the command line looks like this...

Since different machines have differing options, to list what is available on that machine, do this
```

mafoelffen@Mikes-B460M:~$ powerprofilesctl list
* performance:
    Driver:     intel_pstate
    Degraded:   no

  balanced:
    Driver:     intel_pstate

  power-saver:
    Driver:     intel_pstate

```
which will list all available power profile options, and indicate which is selected with an asterisk ( * ).

Then this will show you which power profile is selected, and what driver it uses on that machine to set that.
```

mafoelffen@Mikes-B460M:~$ powerprofilesctl get
performance

```
Replace 'get' with 'set' and the profile name, and it will set the power profile to that profile.

Note that there is no man page for this utility.

Thank you for your kind explanation! I tried this and I am at balanced but still the battery runs out totally in about 1-2 hours now, while in Windows it lasts for at least 4 hours. I wil ltry to set it to power saving mode.

Kind regards

---

