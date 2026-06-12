---
title: "NVIDIA Driver selection issues"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by sun7 on 2014-03-07
Hi All,

I'm running a AMD64, 2.03 ghz processor, with 1gig ram and an NVIDIA GeForce 6600 GPU. Xubuntu 13.10 is running just fine on this system, even though it is an older one. I have done much research concerning the best stable NVIDIA driver for this OS and this GPU, but it has been to no avail. Is anyone able to assist me in selecting the optimum stable driver for my current GPU and setup?

Sun7

---

### Post by phidia on 2014-03-07
With "optimum stable" as your goal it would seem like the driver provided by package manager/the installer would be the right one.
You may have other requirements you didn't express? [Here's the official Ubuntu guide on Nvidia drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

---

### Post by sun7 on 2014-03-08
Hi Phidia,

I ran a software update and thereafter could not boot up my system due to the 173 x-org driver booting to black screen. I proceded to nomodeset and removed the 173 driver provided, and was thereafter able to boot, running on the Nouveau driver. With the Nouveau driver, I am, for example, able to run Star Wars Kotor 2 through wine, but it is a bit jittery. Under additional drivers, I am provided with a Nvidia 304 proprietery driver. I am now running this driver and Star Wars won't even boot up due to an insufficient GPU driver error. Shouldn't this proprietary driver be better than the Nouveau driver? But on the other hand, Plants vs Zombie 1 wouldn't run on the Nouveau but runs perfectly on the new 304 proprietary. This is strange, because Star Wars is much more resource intensive than PvZ. See my dilemma? 

Sun7

---

### Post by phidia on 2014-03-08
Hey, It's an interesting question and there are people looking at perfecting gaming on linux/ubuntu. Take a look [this thread]("http://askubuntu.com/questions/334319/best-nvidia-additional-driver-option") at ask ubuntu. From that it would seem that the very latest drivers might be worth trying. While the gaming info at [this link]("https://help.ubuntu.com/community/Games") might be to basic maybe it will lead you to something you can use. Good luck and welcome to the forums.

---

### Post by sun7 on 2014-03-10
Thanks very much. Will look into the thread and link and see whereto from there. I have posted another thread today and am hoping to find a solution to quite an intricate dilemma. It's in the beginners section. 

Sun7

---

