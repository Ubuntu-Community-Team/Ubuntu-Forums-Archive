---
title: "ATI upgrade corrupt?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by bonedragon on 2008-08-07
hi 
i have been using Ubuntu for 3months now and have run into a brick wall.
a week ago i updated my software. The normal Ubuntu stuff.
when all of a sudden Ubuntu wouldn't boot after that. i got the terminal started and updated the system again but again no dice.

 so finally after pressing some random buttons namely Ctrl+Alt+F9 (or F10) not sure which really, I managed to get Ubuntu started in low graphics mode i.e no visual effects.

i tried starting the effects up again and again it wouldn't boot.
i think it is because of a corrupt ATI driver that upgraded the week before.
any idea how to get my system back to normal? with visual effects  
i miss AWN:(
p.s. i have a ATI radeon 1250 mobo integrated chip.

---

### Post by markbuntu on 2008-08-07
The -19 and-20 kernel updates have some issues with the ati driver and certain cards, they do not load thefglrx kernel modules into the kernel, yours may be one of them. Try reinstalling the driver.

---

### Post by kk0sse54 on 2008-08-07
I had that problem so I booted into a different kernel and everything seemed to work fine since. You can try and like markbuntu said and reinstall the drivers or if that doesn't work use a different or older version of your kernel until you get another kernel update that might fix the problem.

---

### Post by prabhakaran1989 on 2008-08-07
Did u get the White screen after getting in to windows??

---

### Post by bonedragon on 2008-08-08
hi i will try reinstalling the drivers.
and yes prabhakaran1989 i did get the white screen where i could not see anything but i could open it.

---

### Post by prabhakaran1989 on 2008-08-08
ya i too got that same problem when i installed the OPEN SUSE 11..i tried upon 3 times installing the os again d again ...but i could'nt able to solve that..

according to some post in the opensuse  they say it is a bug due to drivers..
But in UBUNTU 8.04 my driver ib been updated///when i started configuring the visual effects it automatically ask that wether to uptdate ATI driver so at that time u too update ..don't download from ATI site kk...

for my sake try d see if u dont have any other option..i shall give u the links which i found in suse forums...

[http://forums.opensuse.org/pre-release-beta/391339-11-new-ati-drivers.html#post1847878](http://forums.opensuse.org/pre-release-beta/391339-11-new-ati-drivers.html#post1847878)
[http://forums.opensuse.org/applications/386613-desktop-effects-crashed-kde-4-a.html#post1847895](http://forums.opensuse.org/applications/386613-desktop-effects-crashed-kde-4-a.html#post1847895)

k ...if u had no other option in either these try as i said ..u will get no problem......

---

### Post by bonedragon on 2008-08-08
hi 
i have tried reinsalling the drivers no dice still have the same problem.
prabhakaran1989 did you fix the problem. i triesd what the inks said but to no avail.
damn ATI...
ok any other ideas im open to anythng:)

---

### Post by prabhakaran1989 on 2008-08-08
actually i fixed the problem by this way... see clearly

u try to install the fresh Ubuntu 8.04 then try to make automatic detection of the ATI driver then allow ubuntu to download automatically the things which it needed....then no problem will be there!!


wats ur ATI model?? i will search fo it!

---

### Post by prabhakaran1989 on 2008-08-08
stay on to this thread i will search for that d help u to solve..there should be some way!!

---

### Post by prabhakaran1989 on 2008-08-09
have u solved the problem?

---

### Post by bonedragon on 2008-08-09
hi 
sorry i cant reply very fast a bit busy these days.
any way no i  dident but i am goig to reinstall ubuntu now because i kind of made it worse... i hope the fresh install will help.
thanks for all you help by the way prabhakaran1989 and everybody elsen to. should i leave this thread as unsolved?? let me know

---

