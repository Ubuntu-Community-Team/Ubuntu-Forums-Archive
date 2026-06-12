---
title: "no internet after latest update"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by deschar on 2008-09-21
Hello, I hope someone can help.

I installed hardy heron on a Toshiba Satellite about six months ago, and very slowly and tortuously (for me, as I have never taken a computer science class in my life much less written a line of code) have been getting various parts of the system to work (movie player, microphone, wireless internet, etc.) I'd succeeded mostly - still no sound in firefox - and then about three weeks ago I accepted and installed a number of updates which knocked out not only the wireless internet connection but the ethernet connection as well. 

I have not been able to find a fix for this. It's disheartening - getting one part of the system to work seems to kill another - and now I know to beware updates. 

Does anyone know how I may remedy this? I probably missed the fix for this somewhere on the net, but I gave up and threw in the towel.

(I have re-installed the Madwifi Atheros driver but that has not helped the wireless side of the problem)

---

### Post by nhasian on 2008-09-21
hello,

did you install a new kernel?  when your pc first powers on, in the menu system you can try booting an older kernel to see if that resolves your problem.  let me know if that fixes it!

as for the sound in your browser, your using firefox right?  and the flashnon-free plugin?

---

### Post by deschar on 2008-09-21
Hello nhasian, thank you for responding.

My grub boot menu indicates that I have 2.6.24-19-generic intalled, as well as two other versions of it, if I am reading the menu correctly.

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+

I had downloaded hardy from the ubuntu website and burned it onto a CD and from there installed it on my laptop. I then installed several fixes for different parts of the system, as I indicated in my original post, and then I accepted and installed several updates to hardy. In all that, might I actually have an older kernel installed on my laptop that the grub menu doesn't show? And if so, how would I gain access to it and activate it? Or by 'older kernel' do you mean gutsy gibbon? Do you recommend that I install that? I have heard that it is a much less buggy system than hardy.

And if I installed an earlier kernel would I then not also have to reinstall all those fixes for the different parts of the system that did not work with my hardware, or would I have to look for other fixes to match the older kernel?

Or is there a specific kernel that you recommend I install as being more internet-friendly than 2.6.24-19-generic?

Please bear in mind that I am not conversant in ANY computer language, hence my post in the Absolute Beginners section of the forum, and that if you have any instructions for me, please include command lines that I may cut-and-paste into the terminal if I need to.

As for my sound problem in firefox, I am using the Shockwave Flash 10.0 b218 plug-in, which I did not pay for. Is there a version of the plug-in that will enable sound in firefox but that I must pay for? And where would I find it?

Many thanks again.

---

### Post by billgoldberg on 2008-09-21
If you updated the kernel, as another user mentioned, just use the older one. As you know, you can select it on boot.

For the sound issue.

Most likely it's a Pulse Audio thing, so try switching to Alsa and see if it works.

See link:
[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)

---

### Post by deschar on 2008-09-22
Hello billgoldberg, thanks for responding. 

I don't think I can get to an older kernel just by rebooting. All my choices seem to be ubuntu 8.04.1, kernel 2.6.24-19. I didn't see anything that said kernel 2.6.24-18 or 2.6.24-17. And as I said in my two previous posts, I am very new at this, and I have no programming skills whatsoever, so if there is an older kernel available on my laptop that I cannot see on my grub menu I would very much appreciate it if you could give me detailed instructions as to how I may gain access to it. 

When you said 'just use the older one' did you mean reinstall hardy but do not accept any updates after that? Because at this point that is what I think I will do.

Thank you for the link re: pulse audio. Unfortunately I still have no sound for flash in firefox. 

Many thanks again for responding.

---

