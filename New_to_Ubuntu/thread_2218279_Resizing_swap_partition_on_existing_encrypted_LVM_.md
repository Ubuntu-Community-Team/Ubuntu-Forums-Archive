---
title: "Resizing swap partition on existing encrypted LVM install"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by shandu9 on 2014-04-20
I'm very new to Linux, so I think this fits in the beginners section! :)

What I did was the following:
- Installed Lubuntu 14.04 from the "Try Lubuntu" environment.
- Enabled encryption and LVM.
- I got an error about an unsecure swap drive during installation, for which I had to run the command "swapoff --all" (which solved it).

Everything seems to be working. However, I did not manually modify partitions (perhaps naively). The result is that my swap partition is smaller than my RAM size, which disables hibernation. And I want hibernation, as I'm running this on a laptop.

I've tried to figure out how to resize the root and swap partitions via the Live CD, but I've come up completely blank. There seems to be a wealth of information, but somehow this all seems to be either incompatible with LVM or with encryption. Can someone help me with this?

In more detail, what I want is to remove 2 GB from root and add 2 GB to swap_1, and use this as swap drive.

Thanks!

Edit:
I've been playing around with it some more, and I eventually found some more general problem associated with the encryption, apart from my own desire to modify the swap size. During startup I noticed a briefly-displayed message saying "The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present", and swapon -s and free -m both suggested there wasn't any swap either. After playing with this for what seems like forever, there now is a swap partition (/dev/mapper/lubuntu--vg-swap_1), but swapon ---all still returns an error: "/dev/mapper/crytpswap1: stat failed: No such file or directory". I'm even more lost now, I think, and wondering if the swap partition is still encrypted this way. Hibernation also still doesn't work properly (it comes back with an error when the system resumes after I manually typed sudo pm-hibernate).

I'm considering trying to reinstall to see if this fixes anything at the moment, especially since I've read some articles that suggest that hibernation and encryption just don't go well together. I'll be trying this tomorrow, but if anyone has any suggestions on the matter they would be highly appreciated :)

---

### Post by shandu9 on 2014-04-30
To update my previous post with the current situation:

I've reinstalled and left everything regarding the swap 'as is' without fiddling with it this time. Again, I've chose both for full encryption and encryption of the home directory of the first user. I've made no more attempts to resize the swap partition, and have decided to learn to live without hibernation (as I've read it can be very troublesome in general combined with encryption, which I consider the more important of the two).

I'm now getting the message "The disk drive for /dev/mapper/lubuntu--vg-swap_1 is not ready yet or not present" during startup, which also seems to cause a startup delay. Running swapon -s or free -m both suggest that there is no swap partition.

Can anyone tell me how to fix this?

---

### Post by fkkroundabout on 2014-05-01
i suppose you could always just use suspend instead, but yes that's would require constant power. then again many devices often use the most power for just the display

yes i don't think it's possible yet to resize encrypted paritions, from what i've read. there may be a complex work around but i've yet to see it
i suppose hibernation may not be the best supported and therefore most popular feature

you could also say: what is it that makes you want to hibernate the computer to begin with ? just faster startup ? since encryption is important for you, i think booting from scratch is more secure than booting from swap

---

### Post by LastDino on 2014-05-01
Hmm just a though but have you tried creating a ''swap file''? 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by shandu9 on 2014-05-01
> **fkkroundabout said:**
> i suppose you could always just use suspend instead, but yes that's would require constant power. then again many devices often use the most power for just the display

yes i don't think it's possible yet to resize encrypted paritions, from what i've read. there may be a complex work around but i've yet to see it
i suppose hibernation may not be the best supported and therefore most popular feature

you could also say: what is it that makes you want to hibernate the computer to begin with ? just faster startup ? since encryption is important for you, i think booting from scratch is more secure than booting from swap

Well, the reason to hibernate in general is mostly that I tend to have a lot of programs open that I don't all want to start up again for short interruptions in my work. And the battery of my laptop is basically non-existent by now, so suspension is not really an option. Anyway, I've resigned myself to working without hibernation already. On the bright side: since my laptop is quite old and crappy, it doesn't run too many programs at once anyway, which helps me adjust my workflow ;)

> **Goten0007 said:**
> Hmm just a though but have you tried creating a ''swap file''? 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Thanks for the suggestion. I looked into that, and I suppose it's an option with hibernation off the table. However, I already have an unused swap partition, so I'd prefer to utilize that first if at all possible :)

---

### Post by whitesmith on 2014-05-01
A few of my thoughts: You **do** realize hibernation (saving machine state to an HDD) is inherently slower than suspension (saving to RAM), do you not? Also, it is much easier from an engineering perspective to implement suspension, so it seems the favored route in Linux, presuming adequate memory is available. My deskside PC has 32 GB of RAM so I just suspend it instead of hibernating (which, incidentally, was a feature that never worked reliably on my computer). The only power used is whatever minimal amount is required to keep the CPU and RAM functional -- about 25 watts in a machine that normally consumes 175 while running. I would caution against LVM because if one drive fails, the entire chain is useless without a 100.0% up-to-date backup. Encrypting the way most distros do it is another snake ready to strike. Why not a vanilla installation followed by whole-disk encryption on a USB stick for sensitive stuff? This approach is less prone to failing and dragging everything down with it. Hope my experience has helped in some way. Cheers.

---

### Post by shandu9 on 2014-05-03
> **whitesmith said:**
> A few of my thoughts: You **do** realize hibernation (saving machine state to an HDD) is inherently slower than suspension (saving to RAM), do you not? Also, it is much easier from an engineering perspective to implement suspension, so it seems the favored route in Linux, presuming adequate memory is available. My deskside PC has 32 GB of RAM so I just suspend it instead of hibernating (which, incidentally, was a feature that never worked reliably on my computer). The only power used is whatever minimal amount is required to keep the CPU and RAM functional -- about 25 watts in a machine that normally consumes 175 while running. I would caution against LVM because if one drive fails, the entire chain is useless without a 100.0% up-to-date backup. Encrypting the way most distros do it is another snake ready to strike. Why not a vanilla installation followed by whole-disk encryption on a USB stick for sensitive stuff? This approach is less prone to failing and dragging everything down with it. Hope my experience has helped in some way. Cheers.

Thanks for your perspective and the extra information.

Once again, hibernation isn't really the issue here anymore, as I've decided I can live without it if the (L)ubuntu implementations aren't working properly. I know hibernation is slower, and I know that suspension doesn't take a lot of power. Still, as mentioned, my laptop basically has **no **battery anymore, so suspension just isn't an option at all. Besides the point, but I also never suspend my desktop computer for the simple reason that a little bit of power is still a waste if I'm not using it for a longer time. So I prefer to either turn the computer off, or hibernate it if I decide I'm too lazy to open/close programs (my desktop is on Windows, where hibernation does work properly, though maybe not as securely).

I'm not aware of any inherent issues of LVM on a system like mine, which has only a single physical hard drive. Am I missing something there?

Regarding encryption I fully agree: a hard drive failure, even a partial one, would probably destroy all data. But then that's not so much the point (for me), and neither is encryption of a few critical files on an encryption USB drive (which can fail too, by the way) or in something like a TrueCrypt container. The latter option does work, and this is what I used to do on Windows. However, I prefer the convenience of leaving myself logged on at a multitude of websites, which I consider to be the greatest security risk there is nowadays. Encryption of personal files is more of a 'bonus' for me: I wouldn't like it if people saw my latest vacation photos, but it also wouldn't be a really big deal ;)

Anyway, I imagine that a solid protection can be achieved in a different way too. For example, encrypting just the home directory may already be enough, and I can also log myself out of everything on my laptop (of course). But this whole-disk encryption seems like a logical solution to me, so if it's available why not use it?

Those are my thoughts on the topic, but any input to show me that I'm missing something is appreciated. I'm a huge newbie on Linux, so I might be missing a ton of things, especially when it comes to specific limitations and options for Linux :)

Does anyone have any ideas regarding the unused swap partition?

---

