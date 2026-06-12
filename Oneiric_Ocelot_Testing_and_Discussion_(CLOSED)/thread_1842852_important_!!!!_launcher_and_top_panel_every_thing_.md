---
title: "important !!!! launcher and top panel every thing is disappear :("
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gladiator-prog4me on 2011-09-12
launcher and top panel every thing is disappear :(

---

### Post by nothingspecial on 2011-09-12
Hi, did you update today, because I noticed it wanted to remove unity?

Try getting a wired connection if you don't have one, then pressing Ctrl-Alt-F1

Login then

```
sudo apt-get update && sudo apt-get dist-upgrade
```

because they seem to have fixed it now.

---

### Post by Gladiator-prog4me on 2011-09-12
> **nothingspecial said:**
> Hi, did you update today, because I noticed it wanted to remove unity?

Try getting a wired connection if you don't have one, then pressing Ctrl-Alt-F1

Login then

```
sudo apt-get update && sudo apt-get dist-upgrade
```

because they seem to have fixed it now.

i do the dist update and restart my computer then i faces this problem :( 

now i will try a sudo apt-get update && sudo apt-get dist-upgrade  and tell you

---

### Post by Gladiator-prog4me on 2011-09-12
i do this : sudo apt-get update && sudo apt-get dist-upgrade

but still face a problem :(

---

### Post by cecilpierce on 2011-09-12
Same thing happen to me and I opened synaptic in unity 2d and install unity and a bunch of compiz stuff, now it working again.

---

### Post by effenberg0x0 on 2011-09-12
In a last case scenario, you could try to reinstall the default important packages that might relate to what you are reporting. That would be something like 

[I](If you can't launch a terminal because you have no launcher/panel,  press ctrl+alt+F1(or F2, F3, etc) - Whatever gets you to a console /  login prompt)

[/I]```


sudo apt-get update
sudo apt-get install --reinstall compiz compiz-core compiz-gnome unity [I]unity-2d unity-2d-launcher  unity-2d-places unity-2d-spread  unity-common unity-greeter  unity-lens-applications
[/I]

```[I]

*_[SIZE=4][COLOR=DarkRed]**READ**[/COLOR][/SIZE]_*[/I] what apt is telling you in the console. If it says that it will remove a lot of stuff before installing these packages (like removing ubuntu-desktop, etc), then *[I]_[SIZE=4][COLOR=DarkRed]**STOP**[/COLOR][/SIZE]_*[/I] what you're doing by selecting [I][I][U][SIZE=4][COLOR=DarkRed][B]NO.

[/B][/COLOR][/SIZE][/U][/I][/I][I]Then restart the PC or just the DM, whatever you choose
sudo service lightdm restart
or 
sudo reboot now

Enter a Gnome/Ubuntu2d/Ubuntu session, etc and only then you try a normal update:
[/I]*sudo apt-get update && sudo apt-get upgrade*
[I]
Should work.

Regards
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)




[/I]

---

### Post by Gladiator-prog4me on 2011-09-12
> **cecilpierce said:**
> Same thing happen to me and I opened synaptic in unity 2d and install unity and a bunch of compiz stuff, now it working again.

please can you tell me how to that step by step ? because i still have a problem

---

### Post by Gladiator-prog4me on 2011-09-12
> **effenberg0x0 said:**
> In a last case scenario, you could try to reinstall the default important packages that might relate to what you are reporting. That would be something like 

[I](If you can't launch a terminal because you have no launcher/panel,  press ctrl+alt+F1(or F2, F3, etc) - Whatever gets you to a console /  login prompt)

[/I]```


sudo apt-get update
sudo apt-get install --reinstall compiz compiz-core compiz-gnome unity [I]unity-2d unity-2d-launcher  unity-2d-places unity-2d-spread  unity-common unity-greeter  unity-lens-applications
[/I]

```[I]

*_[SIZE=4][COLOR=DarkRed]**READ**[/COLOR][/SIZE]_*[/I] what apt is telling you in the console. If it says that it will remove a lot of stuff before installing these packages (like removing ubuntu-desktop, etc), then *[I]_[SIZE=4][COLOR=DarkRed]**STOP**[/COLOR][/SIZE]_*[/I] what you're doing by selecting [I][I][U][SIZE=4][COLOR=DarkRed][B]NO.

[/B][/COLOR][/SIZE][/U][/I][/I][I]Then restart the PC or just the DM, whatever you choose
sudo service lightdm restart
or 
sudo reboot now

Enter a Gnome/Ubuntu2d/Ubuntu session, etc and only then you try a normal update:
[/I]*sudo apt-get update && sudo apt-get upgrade*
[I]
Should work.

Regards
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)




[/I]

Thank you :) i will try it now

---

### Post by Gladiator-prog4me on 2011-09-12
> **effenberg0x0 said:**
> In a last case scenario, you could try to reinstall the default important packages that might relate to what you are reporting. That would be something like 

[I](If you can't launch a terminal because you have no launcher/panel,  press ctrl+alt+F1(or F2, F3, etc) - Whatever gets you to a console /  login prompt)

[/I]```


sudo apt-get update
sudo apt-get install --reinstall compiz compiz-core compiz-gnome unity [I]unity-2d unity-2d-launcher  unity-2d-places unity-2d-spread  unity-common unity-greeter  unity-lens-applications
[/I]

```[I]

*_[SIZE=4][COLOR=DarkRed]**READ**[/COLOR][/SIZE]_*[/I] what apt is telling you in the console. If it says that it will remove a lot of stuff before installing these packages (like removing ubuntu-desktop, etc), then *[I]_[SIZE=4][COLOR=DarkRed]**STOP**[/COLOR][/SIZE]_*[/I] what you're doing by selecting [I][I][U][SIZE=4][COLOR=DarkRed][B]NO.

[/B][/COLOR][/SIZE][/U][/I][/I][I]Then restart the PC or just the DM, whatever you choose
sudo service lightdm restart
or 
sudo reboot now

Enter a Gnome/Ubuntu2d/Ubuntu session, etc and only then you try a normal update:
[/I]*sudo apt-get update && sudo apt-get upgrade*
[I]
Should work.

Regards
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)




[/I]



thank you :) this is helped me and problem is fixed :)

---

### Post by effenberg0x0 on 2011-09-12
Hey,

Congratz man. Please, mark the thread as solved when possible. Stay way from partial upgrades.

Regards,

---

