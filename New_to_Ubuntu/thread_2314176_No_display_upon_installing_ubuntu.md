---
title: "No display upon installing ubuntu"
date: 2016-02-18
forum: New to Ubuntu
---

### Post by SynapticVibe on 2016-02-18
Completely new to Linux. 

I'm trying to install Ubuntu 15.10 on my desktop PC which is running an old Nivida Geforce 9600GT and my display is cutting out. It appears the signal is lost right before I reach Ubuntu install screen as my particular monitor indicates that there is no signal being received by the video card. Tried it on Mint and same problem occurred. I believe it's driver/video card related. Any ideas how to solve this problem?


I'm able to get to the text menu using Alt Control and F1 after this occurs. 

Thanks.

---

### Post by Bucky Ball on 2016-02-19
Welcome. Try this. When you boot from the install media, you will see a purple screen with a little icon down the bottom. Hit a key (any key from memory, but try F6 also if none work). That should take you to the options screen. 

In there, you'll see 'Try Ubuntu' 'Install Ubuntu', etc. Hit the F6 key. A pop-up should appear. Choose 'nomodeset' then proceed with the boot and 'Try Ubuntu'. 

Get anywhere? The nomodeset method can also be used if you have already installed and are having this issue, just a different way of going about it. Have you installed already and now you get a black screen or you are trying to install and only getting that far?

(PS: We don't officially support Mint here so please stick with your Ubuntu discoveries as we dig deeper, but good to know that the same happens in Mint. If the solution above works with Ubuntu, though, it should work with Mint also. :))

---

### Post by gordintoronto on 2016-02-19
A 9600GT should work perfectly with Ubuntu 15.10. What are the specs of the computer? Memory is the most important one, but it might be something else.

Have you tried Xubuntu? It might work better with a computer of that age.

---

### Post by SynapticVibe on 2016-02-19
Hey thanks for replying. 

I got it to work from choosing to boot with nomodeset. I installed the 9600GT drivers once inside. Works great.

---

### Post by Geoffrey_Arndt on 2016-02-19
Great . . way to follow up!   pls mark thread as solved so others can benefit (see thread tools at top of thread).    Thanx.

---

### Post by Bucky Ball on 2016-02-20
> **Geoffrey_Arndt said:**
> pls mark thread as solved so others can benefit (see thread tools at top of thread).    Thanx.

And also see the first link in my signature. Always share your fix with the community if you find one please and let helpers (and potential helpers) know you no longer need support by marking the thread as solved. 

Good luck.

---

