---
title: "[SOLVED] cannot upgrade Ubuntu"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-06-06
i am trying to upgrade my Ubuntu 7.04 to 7.10 with the update manager.
When i click update, it says 
"Release notice cannot be downloaded"
"Please check your internet connection"

what is wrong?
tq

---

### Post by Joeb454 on 2008-06-06
Do you get the same error if you run the following 2 commands from a terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```

It looks like you might...but I just want to check :) Is your internet connection working correctly?

---

### Post by fmpfmpf on 2008-06-06
1st one fails
2nd one works

i can surf internet and update my 7.04
but i cannot upgrade to 7.10

it is very weird :(

---

### Post by sayakb on 2008-06-06
If the second one works, then you should already be upgrading to Gutsy ;)

---

### Post by CREEPING DEATH on 2008-06-06
Can you download the Alternate CD?  If so, download it and use it to upgrade.

CD

---

### Post by fmpfmpf on 2008-06-06
> **LinuxIsInnovation said:**
> If the second one works, then you should already be upgrading to Gutsy ;)

oh, it is supposed to upgrade to gutsy??
when i say it works, i meant no error was shown.
Anyway, this is the output:-
p/s - the output isnt 100% exact. This is because my laptop is running on german OS. i have to translate them into english before posting here.

root@laptop:~# sudo apt-get dist-upgrade
Packet lists are beign read... Completed
Dependency tree being built
Reading state information... Completed
Calculating Upgrade...Completed
0 upadted 0 newly installed, 0 deleted und 0 not updated.

what is wrong?

tq

---

### Post by Joeb454 on 2008-06-06
You can download the Gutsy CD images from here, if you want to download it :)

[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

Edit: This will sound stupid - but you're sure you're running 7.04 and not 8.04 :)

---

### Post by sayakb on 2008-06-06
You get that when you don't have any distribution upgrade. **Enable **all repositories and update sources (except for Unsupported updates) and try again.

> **Joeb454 said:**
> Edit: This will sound stupid - but you're sure you're running 7.04 and not 8.04 :)

LOL.. I was thinking of that too.. :D

---

### Post by fmpfmpf on 2008-06-06
i have the alternate 7.10 CD.
tried using it and got this error:-

Failed to determine which actualizations are available.

An unsolvable problem arose with the calculation of the actualization.
Please provide an error report for the package” update manager “and add the files in the listing /var/log/dist-upgrade/.

p/s - just a reminder, this msg was also translated to english.

tq

> Edit: This will sound stupid - but you're sure you're running 7.04 and not 8.04 
yes, i am using 7.04. hehehehe

---

### Post by fmpfmpf on 2008-06-06
> **LinuxIsInnovation said:**
> You get that when you don't have any distribution upgrade.

now it says server is busy.
i think something is still wrong :(

---

### Post by Joeb454 on 2008-06-06
What speed did you burn the 7.10 cd at? And are you sure it's the alternate install CD?

---

### Post by fmpfmpf on 2008-06-06
28x
yes, it is

---

### Post by Joeb454 on 2008-06-06
It could be a burn error. Try reburning at between 1-4x :) See if the error still persists

---

### Post by fmpfmpf on 2008-06-06
it is now 7.10
i have no idea what id id,, but my whole system is now screwed up.
arrrgggghhhh...

---

### Post by sayakb on 2008-06-06
You may check the disk's integrity by verifying MD5Sum or just re-burn the disk at slow speed.

---

### Post by Joeb454 on 2008-06-06
If your system is screwed up - you could run a live CD and back up your data, then reinstall

---

### Post by fmpfmpf on 2008-06-06
i have reinstalled everything
now using 7.10
thnx

---

### Post by Joeb454 on 2008-06-06
No problem :)

You can mark your thread as solved from "Thread Tools" at the top of this page :)

---

