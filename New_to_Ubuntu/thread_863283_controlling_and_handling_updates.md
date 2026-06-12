---
title: "controlling and handling updates"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-18
Now that I have my Ubuntu 8.04.01 system running (wifi working etc). I would like to keep my system stable. How should I configure Synaptic (repositories etc) to ensure my system receives only stable code?

I do not have a test system, which I probably should. So I was thinking that I need to be careful on how I update my current and only Ubuntu system.

Do most people have a test system that they load updates on first? Or do most people just apply the updates to their main install.

---

### Post by drs305 on 2008-07-18
In Synaptic > Settings > Repositories > Updates:
Tick "Important security updates (hardy-security)" 

You would also be safe to tick "Recommended updates (hardy-updates)" but may not meet the strict standards you mentioned.

---

### Post by Oldsoldier2003 on 2008-07-18
> **pgte3 said:**
> Now that I have my Ubuntu 8.04.01 system running (wifi working etc). I would like to keep my system stable. How should I configure Synaptic (repositories etc) to ensure my system receives only stable code?

I do not have a test system, which I probably should. So I was thinking that I need to be careful on how I update my current and only Ubuntu system.

Do most people have a test system that they load updates on first? Or do most people just apply the updates to their main install.

Since you are using the LTS i wouldn't worry too much unless you are always in search of the latest greatest updates. Just avoid backports and proposed repos for Hardy and you should remain pretty stable.

---

### Post by pgte3 on 2008-07-18
Thanks for the replies, I do not want to give the impression that I am freak about being stable, but on the other hand I do not want to be flooding my install with to many updates and break something that is working.

---

### Post by avtolle on 2008-07-18
As you did not indicate how you got your wifi working, be aware that if you had to manually install the drivers, you *might* have an issue on kernel updates "breaking" your wifi. The same applies to any graphics drivers manually installed.

---

### Post by pgte3 on 2008-07-18
This is an excellent point. I did get my wifi working via a "manual" install by down loading a current madwifi driver. In the case of something like this, what steps should I take to prevent my wifi from breaking? There may be nothing I can do, except reinstall it again if it breaks.

---

### Post by drs305 on 2008-07-18
> **pgte3 said:**
> This is an excellent point. I did get my wifi working via a "manual" install by down loading a current madwifi driver. In the case of something like this, what steps should I take to prevent my wifi from breaking? There may be nothing I can do, except reinstall it again if it breaks.

StartUp-Manager is an app that controls the boot menu. In it is an option to keep the current kernel as the default, even if a newer kernel is downloaded and installed. You can do the same thing by editing grub's menu.list, but this method is probably easier.

Install StartUp-Manager:
```
sudo aptitude install startupmanager
```

To 'freeze' it at the current kernel: System, Administration, StartUp-Manager.  You can set the default operating system to a specific kernel or 'Last Used' which would freeze it. 

If and when you wanted to use a newer kernel, you would go into StartUp-Manager and select the newer kernel.

Caution: when installing a new kernel, often the installation asks if you want to use your current menu or install the newer one. In this case, you would want to keep use the old one and not update it.

---

### Post by XanII on 2008-07-18
I have problem related to this: i cannot tick the 'important security updates' checkbox. 

i removed it at some place to test what else the system offers and now i cant get it back. it wont allow me to tick it.

---

### Post by XanII on 2008-07-18
Nevermind. found this: [http://ubuntuforums.org/showthread.php?t=852947&highlight=important+security+updates](http://ubuntuforums.org/showthread.php?t=852947&highlight=important+security+updates)

Too quick to reply. :P

---

### Post by pgte3 on 2008-07-18
drs305 thanks for the tips. By delaying or controlling the use of a new kernel might be helpful, although I will have to use a changed kernel at some point and will still be confronted with a reinstall of my wifi driver.

---

### Post by drs305 on 2008-07-18
> **pgte3 said:**
> drs305 thanks for the tips. By delaying or controlling the use of a new kernel might be helpful, although I will have to use a changed kernel at some point and will still be confronted with a reinstall of my wifi driver.

The biggest advantage will be that you can deal with the problem on your schedule (when you have time to fix it) rather than when you really need your computer to work RIGHT NOW! 

It also gives you a chance to see what happens to others before trying it yourself...  ;-)

---

### Post by avtolle on 2008-07-18
What drs305 said. I'll add that while waiting to deal with it, you might find that the new kernel has "solved" the problem with the wifi driver, which would be a good thing, no?

---

### Post by barney385 on 2008-07-18
> **drs305 said:**
> StartUp-Manager is an app that controls the boot menu. In it is an option to keep the current kernel as the default, even if a newer kernel is downloaded and installed. You can do the same thing by editing grub's menu.list, but this method is probably easier.

Install StartUp-Manager:
```
sudo aptitude install startupmanager
```To 'freeze' it at the current kernel: System, Administration, StartUp-Manager.  You can set the default operating system to a specific kernel or 'Last Used' which would freeze it. 

If and when you wanted to use a newer kernel, you would go into StartUp-Manager and select the newer kernel.

Caution: when installing a new kernel, often the installation asks if you want to use your current menu or install the newer one. In this case, you would want to keep use the old one and not update it.

Is it possible to use startup manager to edit the old kernels from the boot menu.

Sounds like a cool app...

Thanks

---

### Post by drs305 on 2008-07-18
> **barney385 said:**
> Is it possible to use startup manager to edit the old kernels from the boot menu.

Sounds like a cool app...

Here's some info on using StartUp-Manager I wrote a month or so ago. I'm a big fan of this simple gui app for editing grub's menu.lst:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by barney385 on 2008-07-18
> **drs305 said:**
> Here's some info on using StartUp-Manager I wrote a month or so ago. I'm a big fan of this simple gui app for editing grub's menu.lst:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

Thanks!! You're the man/woman!!


:guitar:

---

### Post by pgte3 on 2008-07-18
Good points. Advance notice is a good thing.

---

