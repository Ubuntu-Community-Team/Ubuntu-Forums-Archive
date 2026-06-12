---
title: "new video card"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by benner on 2008-05-24
I am about to swap out my video card. The computer is randomly freezing up and I am swapping out hardware piece by piece to see what might be causing it.  I just want to see what I'm in for before I do. I doubt it will be the same card as I have (borrowing from someone) so it will need to be reconfigured. Do I need to sudo dpkg-reconfigure xserver-xorg? Will it find it on its own when I reboot?

If it isn't the video card that's the problem, I will also try to switch the network interface from the integrated one on the mobo to a pci card. Same question. will ubutnu find it or do i need to run a command?

thanks in advance

---

### Post by ardvark71 on 2008-05-24
> **benner said:**
> I am about to swap out my video card. The computer is randomly freezing up and I am swapping out hardware piece by piece to see what might be causing it.  I just want to see what I'm in for before I do. I doubt it will be the same card as I have (borrowing from someone) so it will need to be reconfigured. Do I need to sudo dpkg-reconfigure xserver-xorg? Will it find it on its own when I reboot?

If it isn't the video card that's the problem, I will also try to switch the network interface from the integrated one on the mobo to a pci card. Same question. will ubutnu find it or do i need to run a command?

thanks in advance

Hi...

What is the system exactly and how old is it? How long has this been happening and is it the result of something specific or did start happening out of nowhere?

Just as a preliminary guess, if it's not software related, I'm thinking your motherboard, PSU or memory are possible culprits. checking those out might be easier than messing with xorg settings after you swap the card, especially if it won't go into a graphical menu for you. ;)

Best Regards...

---

### Post by benner on 2008-05-24
thanks. actually, i have been trying to solve this problem for over a year. it happened on feisty and gutsy, even with fresh installs and it happened with xp and xp-64bit. it happened on more than one hard drive. i sent the machine away to a repair shop that tested every component and said they couldn't find anything. the freezes are completely random. they may happen once and not again for 2 weeks. then they happen 3 times in ten minutes. they happen when using the internet and not, when doing intensive video editing and when typing word documents. i ran a pile of tests with various boot cd's and every test came out aok except one test on one program that failed the cpu test. every time i ran it, it failed. but another cpu test with another program was fine. memory tests came out fine after 3 passes. so now all i can think of is to start removing parts and switching them. i know i need to replace something but i don't want to waste money.

video card will be first. but how about ubuntu recognizing it? i no longer have xp to test with. i am full-time linux now.

---

### Post by PmDematagoda on 2008-05-24
From what I've seen, your issue maybe due to two things mainly:-
1) A bad CPU.
2) Bad memory.

I know that you got some good results both from memory and CPU tests, but have you tried swapping the CPU and the memory modules(the CPU in particular since you got a bad result with one application).

---

### Post by benner on 2008-05-24
i have 3 ram sticks so i can try running without 2 and switch them around to see.

in terms of the cpu, is anyone likely to loan me a cpu to try out to see if that is the problem? i just assumed that i would have to bite the bullet and buy a new one to find out if that was the case.

---

### Post by ardvark71 on 2008-05-24
> **benner said:**
> thanks. actually, i have been trying to solve this problem for over a year. it happened on feisty and gutsy, even with fresh installs and it happened with xp and xp-64bit. it happened on more than one hard drive. i sent the machine away to a repair shop that tested every component and said they couldn't find anything. the freezes are completely random. they may happen once and not again for 2 weeks. then they happen 3 times in ten minutes. they happen when using the internet and not, when doing intensive video editing and when typing word documents. i ran a pile of tests with various boot cd's and every test came out aok except one test on one program that failed the cpu test. every time i ran it, it failed. but another cpu test with another program was fine. memory tests came out fine after 3 passes. so now all i can think of is to start removing parts and switching them. i know i need to replace something but i don't want to waste money.

video card will be first. but how about ubuntu recognizing it? i no longer have xp to test with. i am full-time linux now.

Hi...

How about the power supply? If that turns out ok, then I'm inclined to to suggest buying another system rather than continuing to cycle parts through it. It could be something that the different parts couldn't fix anyway. :-( Just my opinion, though.

If you want to swap out video cards, try to get something with a Nvidia chipset as they are (at least one of) the easiest to deal with as far as drivers.

Best Regards...

---

### Post by benner on 2008-05-27
i changed the power supply a few months back. that wasn't it.

so, i just borrowed a new video card to test out. i had an ati x550 and this one is an ati 'colorful' x1550. now compiz won't work. i assume i have to do something to configure it. what do i do?

---

### Post by PmDematagoda on 2008-05-27
You would have to install the ATi driver(perhaps from Hardware Drivers) and then configure the X-Server to use the ATi driver(if it already doesn't).

---

### Post by benner on 2008-05-27
i ran dpkg-reconfigure xserver-xorg but it only gave me options to change keyboard settings. nothing about the graphics card.

is there a different command to use?

---

### Post by PmDematagoda on 2008-05-27
What was your last card?

---

### Post by benner on 2008-05-27
ati x550. the new one is an ati x1550

---

