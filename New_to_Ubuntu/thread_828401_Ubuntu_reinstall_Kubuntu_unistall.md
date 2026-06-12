---
title: "Ubuntu reinstall Kubuntu unistall"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by simonlugi on 2008-06-13
I tried to install KDE on top of my Ubuntu using synaptic Kubuntu-desktop.
For some unknown reason I could not get the KDE desktop to appear. Tried suggestions given on other threads. Eventually decided to uninstall Kubuntu, this has resulted in ubuntu and a number of apps not working properly. 
I would like to reinstall ubuntu. Can some advise as to how best to do this. I have a Vista on another partition. Partitioning always worries me having had some bad experience. Please simple instructions would be greatly appreciated.
Thanks Simon

---

### Post by gr4nf on 2008-06-13
You should back up the following:
/home
/etc
/root (if there's stuff in it)
/pmi (if you have one)
and then boot to live cd. Use GPartEd to delete the ubuntu partition, and then select the option "use largest continuouse free space" in the installer.

---

### Post by simonlugi on 2008-06-13
Thanks, What do I do with the backed up files. 
Simon

---

### Post by simonlugi on 2008-06-13
Please not I was unable to backup ssl folder. Is this a problem
simon

---

### Post by Lostincyberspace on 2008-06-13
Just make a file titled ubuntu.sh in you home folder with this inside
```
#!/bin/bash
sudo apt-get remove gdm && apt-get remove kubuntu-desktop && apt-get install gdm
```

Then switch to a terminal( ctrl+alt+f2) and login and type ./ubuntu.sh .
And every shoukl work fine after that it resets gdm as the main loader and ubuntu is most likely still on there you just need it to beset to use first.

---

### Post by kansasnoob on 2008-06-13
Do you have anything saved in Ubuntu that you really, really don't want to lose? Files, photos, movies, etc?

---

### Post by SunnyRabbiera on 2008-06-13
have you tried reinstalling the ubuntu desktop package?
You can also retry installing the parts you need

---

### Post by gr4nf on 2008-06-13
With the backed up files? Replace the ones in your new ubuntu install with them.

---

### Post by kansasnoob on 2008-06-13
> **SunnyRabbiera said:**
> have you tried reinstalling the ubuntu desktop package?
You can also retry installing the parts you need

That makes more sense than what I was thinking, which was just delete the Ubuntu partition and start over.

You're right!

I was wrong to jump to conclusions.

---

### Post by kansasnoob on 2008-06-13
If you absolutely want to reinstall I'd be glad to help with that, but it's up to you!

When I was first learning Ubuntu I hosed things several times and found that just starting over was both easier and also educational each time.

You really should be able to fix it if you want to spend the time. It's up to you.

---

### Post by simonlugi on 2008-06-13
I have looked in synaptic and the package labeled ubuntu desktop has a green box. Do I need to uninstall it first and the reinstall?
simon

---

### Post by SunnyRabbiera on 2008-06-13
> **simonlugi said:**
> I have looked in synaptic and the package labeled ubuntu desktop has a green box. Do I need to uninstall it first and the reinstall?
simon

actually you can mark it for reinstallation.
but remove the kubuntu desktop files too, there might be a conflict of some kind.

---

### Post by simonlugi on 2008-06-13
Thanks for the advice unfortunately uninstalling kubuntu and reinstalling ubuntu has changed nothing. 
Note I still get the kubuntu "welcome page" (not sure if this is the right name) when the os is booting up.

I tried inserting the ubuntu.sh file into the home folder. Denies permission. Said I do not have authority to make changes.

Any other suggestions would be greatly appreciated.
Thanks
simon

---

### Post by simonlugi on 2008-06-14
Thanks to everyone advice.
I finally got ubuntu up and running again. The option of using the ubuntu live CD and GParted did not allow me to delete the partitions, however I deleted them via Vista and then reinstalled ubuntu.
Now going thru the process of reinstalling apps such as Skype which are a hassle.
Anyway the end result is still good.
Thanks again

---

