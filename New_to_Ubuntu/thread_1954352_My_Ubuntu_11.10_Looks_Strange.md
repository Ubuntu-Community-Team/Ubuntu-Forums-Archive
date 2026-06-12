---
title: "My Ubuntu 11.10 Looks Strange"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by kizzyaggots on 2012-04-07
HI, this might be a stupid question but i have to ask. I had problems with putting through updates, so i entered a suggested terminal command suggested in the forums. I turn my pc off and i log in and it says i am using 11.10, I never upgraded to a new version of Ubuntu but my screen looks totally different and it's completely different to 11.10 . Does anybody know what's gone wrong?

               Cheers Kizzy.

---

### Post by Bucky Ball on 2012-04-07
What was the command?

---

### Post by kizzyaggots on 2012-04-07
I have no idea mate but as i remember it was sudo-get updates ... something.

---

### Post by kizzyaggots on 2012-04-07
It looks like half debian and half Ubuntu if that helps at all?

---

### Post by Bucky Ball on 2012-04-07
```
sudo apt-get update
```... or:

```
sudo apt-get upgrade
```... ring a bell? Neither command would upgrade the release. If you had no idea what the command was about to do perhaps you should have stuck to the update manager GUI or asked here ... ;)

I'm presuming it has updated the kernel but hard to tell. It is also not clear what release you were using before it upgraded to 11.10. 10.04?

---

### Post by kizzyaggots on 2012-04-08
Hi Bucky, I stuck with the update manager using Ubuntu 11.10  i could not update through the update manager so i asked for help here in the forums, i was directed to the terminal where i tried several commands until one went through; it wasn't updates or upgrade it was a command in the forums that i cannot find in previous threads. When i restart the debian screen comes up and then my username is entered afterwards and what i get isn't 11.10 it seems to have half upgraded or something.

                    Cheers Kizzy.

---

### Post by Bucky Ball on 2012-04-08
Open a terminal. Hit the up arrow on the keyboard and that should show you previously used commands. The command should appear there eventually. Post it back here. ;)

If you used:

```
sudo apt-get dist-upgrade
```

... then you could have upgraded the release, yes.

---

### Post by ZeroCool96 on 2012-04-08
I know when I put 10.10 on my VMware Server I went to do upgrades and the 11.10 dist upgrade popped up and I didn't realize it and I clicked upgrade. Maybe that's what happened?

---

### Post by Bucky Ball on 2012-04-08
> **ZeroCool96 said:**
> I know when I put 10.10 on my VMware Server I went to do upgrades and the 11.10 dist upgrade popped up and I didn't realize it and I clicked upgrade. Maybe that's what happened?

Or something like it, particularly if it is reporting 11.10 as your OS ...

Unfortunately you can't go back without a re-install of 10.10.

---

### Post by kizzyaggots on 2012-04-08
Seems as though it did update, tried to copy and paste with all options and couldn't from the terminal, so I looks as tho i'm stuck with the latest version of Ubuntu 12 i guess; live and learn as they say. Thanks for the help Bucky.

                 Cheers Kizzy.

---

### Post by Bucky Ball on 2012-04-08
No probs. Is it showing as 12.04 LTS? Then you have upgraded to the next long-term support release. If that is the case probably a good thing in some ways, but it is in beta, testing, and not yet released. Expect some issues, big or small, and update daily.

If the issue is solved please mark it that way from 'Thread Tools' at top right. ;)

---

