---
title: "Installed Nvidia driver. Lost sound. djl;afkjsd;lkfa"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Roasted on 2008-10-16
I installed a nvidia tip on the hardy guide. 

sudo apt-get install linux-restricted-modules-server


Then I rebooted as instructed and everything was just messed up hardcore. So I reverted back and installed the Nvidia driver via Envy-GTK. Now, my video is fine. Compiz still doesn't work, but I have a normal looking screen.

But now, Ubuntu doesn't detect my sound card, yet XP plays it just fine. My sound card was working before, but now it does not.

I tried to install the latest alsa driver, but it gave me an error when I ran make (and yes I tried it with sudo too).

I did a search on here and it said I need linux headers. I went to install it and it said there is no installation candidate for linux headers.

djfkalsjd;lasdkfas

Now what?

edit - Oh I have a 9600GT Nvidia card. Restricted drivers aren't available for it, that I've seen.

---

### Post by Roasted on 2008-10-16
Fixed.

I'm running 64 bit Ubuntu Hardy. I was trying to install alsa 1.0.17 on here and it was erroring out. I ended up installing 1.0.18rc3 and it worked fine. I thought I'd get 1.0.17 because it was the latest one under "current version." I figured 1.0.18rc3, being under development version, that it was like... beta or something.

But, it works now. Woo!


Now if somebody could help me figure out why my custom settings on compiz won't stick, that'd be great... 9600GT Nvidia... Envy-GTK latest driver... :):):):):)

EDIT - by the way, how do you guys know certain things are required to run alsa drivers? Like linux-headers? Is there a main page somewhere that shows dependencies of everything??

---

