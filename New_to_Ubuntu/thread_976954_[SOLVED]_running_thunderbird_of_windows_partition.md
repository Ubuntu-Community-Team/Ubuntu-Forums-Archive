---
title: "[SOLVED] running thunderbird of windows partition"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by myddewji13 on 2008-11-09
Hi,

I recently installed ubuntu on my moms laptop. Have gotten everything up and running...there is only one problem.Currently she is dual booting with windows xp and she runs thunderbird (on win xp) for her email. I have managed to get thunderbird working using wine but It starts off with no profiles (no emails, address etcc...). Basically it is like a new instal of thunderbird. Anyway to get it to use the same settings that it uses when used under windows xp (with her emails, inbox etc.. )?

Also as a side note...anyway to run thunderbird natively in linux and get it to use the xp profile?

---

### Post by LowSky on 2008-11-09
yeah, this should help

[http://ubuntuforums.org/showthread.php?t=606820](http://ubuntuforums.org/showthread.php?t=606820)

---

### Post by myddewji13 on 2008-11-09
ok..that deals with migration...anyway to share them? As in...use the same profile in linux and windows...so that when using linux she can download emails etc...then go to windows...and have the emails and everything there...

---

### Post by louieb on 2008-11-09
Thunderbird (Linux version) is in the repositories.  And you can share the profile with windows. [http://ubuntuforums.org/showthread.php?t=203524](http://ubuntuforums.org/showthread.php?t=203524)

Check the How To section theres some other threads that explain how also.

---

### Post by 73ckn797 on 2008-11-09
> **myddewji13 said:**
> ok..that deals with migration...anyway to share them? As in...use the same profile in linux and windows...so that when using linux she can download emails etc...then go to windows...and have the emails and everything there...

You will have to just setup Thunderbird to leave message on the server. Then from Windows or Ubuntu just "get Mail". Both installations will have to have the leave message on server switched on. That is how I am able to have the same messages between the laptop and desktop systems. If one message is sent from one machine it will not show up in the other as being sent. To do that you will have to follow my procedure: [http://ubuntuforums.org/showthread.p...72#post5764972]("http://ubuntuforums.org/showthread.php?p=5764972#post5764972") 
everytime you boot from one OS to the other. In that case you would only need to copy and paste the Mail directory each time. Rather a hassle actually.

As mentioned above you can install T'Bird directly into Ubuntu. Go to: System/Administration/Synaptic Package Manager. There you will find T'Bird and mark it for installation and away you go!!

---

### Post by myddewji13 on 2008-11-10
THNKS :D ...loieb u rock!!1

---

