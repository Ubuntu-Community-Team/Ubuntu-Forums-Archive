---
title: "Nvidia drivers are a joke"
date: 2017-03-11
forum: Recurring Discussions
---

### Post by paralis on 2017-03-11
and it's been a joke for years. No news here I guess.

I use Ubuntu 16.10 (i7 4790k, Z97-UD5H, GTX770, 32 Gb, SSD EVO) and so far I was using Nouveau as driver. Since I don't play games on Linux, it's good enough.

I have encountered problems with nvidia drivers for years (and I DO mean years) and that's why I thought 'No need for nvidia drivers, Nouveau is fine'.

Today, I thought, well let's give it a shot. After all, we're in 2017 right? Both the Linux and Nvidia have come a long way so things should be better.
So here I am, decided to install some nvidia drivers. I know there are several ways : from nvidia, ppa and the official way.
I thought let's try the official way. Should be tested and all. So I went to the system settings and check the 'use Nvidia binary driver 367.57 (proprietary, tested)' option and, confident (my second error, the first one being 'we're in 2017, things are better now'), reboot the system.

Strangely it takes some time to reboot but well it's the first reboot after the installation, so it may be normal.
Finally I get on the desktop. Things seems okay. Because I'm curious to see if the boot process will get back to normal, I reboot again. I see right away that it takes forever to shutdown. Then it takes also forever to get to the grub (on a SSD, I find that rather disturbing). Finally, the desktop pops up and it works fine. Then, in a 'crazy' move, I decide to check the consoles (because I remember the nvidia drivers have always messed up the tty). CTRL+ALT F1 and... nothing. Black screen. I try tty2, 3, 4 and so on. Nothing. I try to get back to the desktop CTRL+ALT F7 and... nothing... for like 30 seconds.

So, here I am: a functional desktop (if I'm not in a hurry to get there) and no tty consoles (because who need them with the multiple terminal solutions today...). And we're in 2017.
I'm sure there are some solutions. I dealt with that countless times. But I find just incredible such problems still exist on Linux and especially on the desktop (sadly not the only problem there, like the distro upgrade from within the desktop, I have never seen it working properly, not once in years). I try to talk about Linux to people tired of Windows but when I see that kind of problem, there is no way Linux gains new users. I know I probably can fix it but what about the pure users?

I don't know if it's a kernel thing or the 'evil' proprietary drivers from Nvidia but it sucks and it's quite sad. Real, real, REAL sad. Not for me, not for all the geeks, techies, hackers here and there but for the rest of the world. And that's a LOT of people.

Eric

---

### Post by Perfect Storm on 2017-03-11
Moved to The Cafe for now.

EDIT: Moved to recurring.

---

### Post by uNoubu8a on 2017-03-13
I miss having a nvidia card and being able to use the proprietary driver that always installed easily on Ubuntu (well the last few years) and just worked.  IMO best to make a thread in the right support area, don't rant, give information and see if it can be figured out :KS

---

### Post by paralis on 2017-03-15
I spent years figuring out things on Linux. Learned a lot obviously from the community, my readings and experiments (and mistakes).

I was just naive enough to think that sort of thing 'just worked' today so the average user could concentrate on something else. It does not or more precisely, on some hardware/system, sometimes it works and on some other, it does not. No big deal. Been that way for years, have no doubt now it won't be fixed tomorrow either.

Anyway, have a nice day

---

### Post by SeijiSensei on 2017-03-15
```
sudo apt-get install nvidia-current
```

always works for me.

---

### Post by QIII on 2017-03-15
The open source developers back-engineer into a black box.  It's a wonder and a testament to their skill that they get anything to work at all.

The proprietary driver is the responsibility of NVIDIA.  Nobody in the Linux world can change that.

Belly-aching here will do little to affect either.

If you would like support from other common users such as yourself, for such are we all here, then start a polite request for help.

---

### Post by jnguyen-m on 2017-03-15
Always works for me too on several computers.

---

### Post by ulysses77 on 2017-11-02
I've had some work wonderfully, and others work awfully. Most notably in laptops. It seems any GPU in a laptop is going to, or has a significally higher chance of having issues on Ubuntu. On a desktop though, I have a hard time thinking of any issue I've ever had at all. The problem being, support comes too little and too late. Companies will always cater to whatever gets them the most money, and that's Windows and Mac OS X.

Simply, there's just not enough reason for them, or any of them, to care. 1% market share, less people to report issues, if they do, they're a small minority that they're not making any money off of (relative to the other systems), and they aren't taken seriously. They have less staff that knows what Linux is or how to code for it, and it's not profitable to hire people who do. The Linux community is just viewed as a small handful of nerds who insists on using some weird complicated OS that doesn't have any software, can't play any games, and there's just not anybody worthwhile using it. So it gets dusted into the rubbish bin and updates aren't seen unless someone like Valve or something requests support because they're making a propriety Linux-based device that they can make money off of (Steam Machine or Google Android).

The free drivers are great and we owe a lot of respect to the people who made them because often times they do work better than that supplied by the company. It's different to reverse engineer or do... anything, with that kind of hardware. With basic port-related hardware, it's often Linux that is used to test it, however, with GPUs, Windows is because they are primarily marketing to Windows users, whereas port things are just seeing if and how the port will work and how well they potentially could make it work. That and to see if they can somehow use that for servers and to make better servers. The only money around Linux lies in servers... so you can count on those sorts of hardware working really well with Linux all of the time. 

Now, a lot of this is coming from a business perspective, I have a lot of knowledge in that field as that's pretty much what I do... but the corperate viewpoint on Linux is very, very poor unless there's something that they can exploit out of it. Linux is often used as a base for new projects as it makes it a lot easier to turn a profit. Companies like Apple will steal the best chunks of code for themselves and use for their operating systems and make big bucks off of it (and Apple will hand back junk and say that they're 'contributing to the community'). I mean, that's generally a side effect of the downside of Linux as a whole (sans Android). 

However, there is no doubt fundamentally Linux is the best operating system. In reality things just don't translate out that way, thoughts and concepts have a harder time coming to completion. That doesn't mean Linux doesn't have it's up sides from this as well... but it's just a double edged sword.

---

### Post by QIII on 2017-11-02
Apple's OSes are descendents of BSD (not Linux), although precious little may remain, especially in userland.  Even the kernel has been heavily rewritten.

Their OSes are not Linux, but they are generally Posix compliant.  That means they are cousins of Linux.  Apple isn't stealing the best stuff from Linux.  They have their own path.

By the way, bashing other OSes and their purveyors is not allowed here, so tone it down.

With regard to drivers (to get back on track) both OEMs do a lot of work to support Linux and for the most part they work very well.  The perception that they don't based on the complaints about them is an illusion.  People do not come to support venues when things go right.  So there is no measure of the ratio of dissatisfied to satisfied users.

---

### Post by ulysses77 on 2017-11-02
The original iPhone up until the iPhone 3GS (as far I as know) did use Debian files, .debs. They are distant cousins, you know the kind that see each other at the family reunions and don't know each other all that well but still say hi to each other? I believe I've referred to them as cousins, maybe on this post, maybe on another post, maybe somewhere else. 

I don't bash them, but I am honest! Brutally honest perhaps, I'm even critical of my own operating system. I won't turn a blind eye to something just because I happen to like it. If you're too blindly dogmatic or tolerant to something, nothing gets better. Acknowledge the bad and do something about it. There is evidence to support my claims, but I'd have to dig around and no point in wasting time on an internet argument that I'm not going to win. The opponent has the high ground. Smile buddy, you're an admin.

---

### Post by Scott Deagan on 2018-08-02
It's now 2018, and I agree with the OP - Nvidia drivers on Linux are pretty bad. I'm not talking about the number of pixels an Nvidia card can push to the screen per second. I'm talking more about just every day desktop usage. With Nvidia proprietary drivers, animations stutter, scrolling in browsers isn't "pixel-perfect" smooth. It's as though the Nvidia drivers are glitchy - either that, or my GTX 1070 is glitchy.

I have an z97 motherboard with an Intel i7-4790, which has the HD 4600 iGPU. Most of the time, I'm using the iGPU instead of the dGPU (the GTX 1070) because the iGPU feels so much more responsive and smooth.

Here's a simple test:


[LIST=1]
[*]Open Firefox.
[*]Go to Google and click on the "Images" link.
[*]Do an image search for something (e.g. "Linux").
[*]Click down on the middle mouse button to enable auto-scroll.
[*]Move the mouse cursor about 1cm below the circle that appears.
[*]Let go of the mouse and observe as the page scrolls downwards.
[/LIST]

When using the Nvidia GPU, it "stutters" (janks) every now and then. I call these "micro-stutters". It really ruins the user experience.

When using the Intel GPU, repeating the same test results in super smooth scrolling.

If I'm doing anything CUDA related ("deep learning" etc) or if I need to record at 60 frames per second, I'll switch to the Nvidia drivers (using: sudo prime-select nvidia and then rebooting). For every day use though, I'll always use the Intel integrated GPU because it makes for a much better experience.

---

### Post by VMC on 2018-08-02
My older PC now can't use nvidia. It stopped right after the end of last year December 2017. So is nouveau or nothing. I had to adjust. I know what programs to watch out for, which ones I can change settings so my PC won't freeze.
It all started after kernel 15. I have an older legacy nvidia chip. Its just that technology moves on. I'm very glad that nouveau works as good as it does.

So I tend to agree that bellyaching isn't going to help. Find a solution, a work around.

---

