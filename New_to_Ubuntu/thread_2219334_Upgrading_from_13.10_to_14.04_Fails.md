---
title: "Upgrading from 13.10 to 14.04 Fails"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by playing_with_matches on 2014-04-23
Hello,

I originally was running 13.04, and upgraded to 13.10 today so I can update to the LTS version of 14.04.  Unfortunately when I go to upgrade, I get the error message:

"Could Not calculate the upgrade: An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu "

I looked in synaptic repository, and I have all of the "other" software sources disabled. I removed the keys I do have MATE and Cinnamon installed not sure if that matters, (I use MATE as my sole desktop environment).  Please help!  I'm pretty clueless as to what to do to fix this, and I want to get to 14.04

---

### Post by Frogs Hair on 2014-04-23
Just a thought ,14.04 has Mate available in the repository and there may be a conflict if you had installed Mate from a PPA or unofficial source.

---

### Post by playing_with_matches on 2014-04-23
You nailed it!  It actually wasn't MATE causing the issue, but Cinnamon.  I removed cinnamon, and now it gets passed the screen it was stopping on.  Fingers crossed the rest goes smoothly.  Thank you!

---

### Post by playing_with_matches on 2014-04-23
I automatically upgraded 13.10 to 14.04, and in the middle of the upgrade, my computer just froze and went black screen.  I let it sit for a while, and it didn't resume, so I had to do a hard reboot.  After rebooting, when I try to launch Ubuntu, I get prompted with a white message box saying "Your computer is running in low graphics mode, what do you want to do?" and just prompts me. 


Please help, my PC is unusable currently.

---

### Post by mörgæs on 2014-04-23
Threads merged.

---

### Post by cwmoser on 2014-04-23
> **playing_with_matches said:**
> I automatically upgraded 13.10 to 14.04, and in the middle of the upgrade, my computer just froze and went black screen.  I let it sit for a while, and it didn't resume, so I had to do a hard reboot.  After rebooting, when I try to launch Ubuntu, I get prompted with a white message box saying "Your computer is running in low graphics mode, what do you want to do?" and just prompts me. 


Please help, my PC is unusable currently.

Is your Video Card an nVidia???
When I installed 14.04, Ubuntu froze up after logging in.
Would only work in low graphics mode.

Fix was to:
sudo apt-get remove nvidia*
sudo apt-get install nvidia-current

I did this in Recovery running Fail Safe Graphics.

Carl

---

### Post by playing_with_matches on 2014-04-24
Hey I was able to fix it. I have a Radeon.  I'm not exactly what I did to solve it, I wound up booting up the ubuntu safe mode, then clicked fix broken packages at the prompt, and rebooted, and it seemed to resolve the issue.

---

### Post by mörgæs on 2014-04-24
Good, please mark the thread 'solved'.

---

