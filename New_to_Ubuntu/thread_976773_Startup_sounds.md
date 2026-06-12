---
title: "Startup sounds?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by bartre on 2008-11-09
hi, i'm trying to change the sound it plays when i login.
i go to system -> preferences -> sound and i pick the clip i want, but it won't test or play when i login.
is there a specific codec or format i need to use? i'm using a .wav file.

---

### Post by dlm4849 on 2008-11-09
Go to administration > login window then to the acessibilty tab. there you can change the login sounds.

---

### Post by dlm4849 on 2008-11-09
double post, sorry

---

### Post by bartre on 2008-11-09
alright, so i did that, but i got the same thing, it knows what i want, but when i test it or login, i get nothing.
any ideas?

---

### Post by dlm4849 on 2008-11-09
i dont know if this is even a issue, but is it possible the files too big or something? try converting it to an .ogg or a .mp3.

---

### Post by empty_tank on 2008-11-10
I had problems with no login sounds with upgraded intrepid amd64. I found a bug report at: [https://bugs.launchpad.net/ubuntu/+s...ra/+bug/273507](https://bugs.launchpad.net/ubuntu/+s...ra/+bug/273507)


Bug #273507: No sound effects play when "play sound effects when buttons are clicked" is enabled

The workaround is to install latest libcanberra 0.10.

"Check this page: "https://launchpad.net/~gkulyk/+archive" with the latest libcanberra 0.10 (the one used in intrepid is the outdated 0.6).
Include the line: "deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main" in synaptic and reload.
Immediately the new 0.10 will show up as an upgrade, marked all upgrades, and reboot!"

The workaround fixed the problem

---

### Post by Sef on 2008-11-10
Moved to absolute beginners.

---

### Post by bartre on 2008-11-10
> **empty_tank said:**
> I had problems with no login sounds with upgraded intrepid amd64. I found a bug report at: [https://bugs.launchpad.net/ubuntu/+s...ra/+bug/273507](https://bugs.launchpad.net/ubuntu/+s...ra/+bug/273507)


Bug #273507: No sound effects play when "play sound effects when buttons are clicked" is enabled

The workaround is to install latest libcanberra 0.10.

"Check this page: "https://launchpad.net/~gkulyk/+archive" with the latest libcanberra 0.10 (the one used in intrepid is the outdated 0.6).
Include the line: "deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main" in synaptic and reload.
Immediately the new 0.10 will show up as an upgrade, marked all upgrades, and reboot!"

The workaround fixed the problem

i'm sorry i didn't understand any of that, still a n00b with ubuntu.
could i have you dumb it down a bit?

---

### Post by dlm4849 on 2008-11-10
go to synaptic package manager and then click on settings, repositories, the third party software. click add source, then add the line "deb...intrepid main" from the post before yours. That will add that repository and allow update manager to see that there is a new version of the software you are looking for.

---

### Post by asgard_command on 2008-11-10
I have the same problem changing startup sounds. Setting up this ppa and installing the above package didn't help my system.

---

