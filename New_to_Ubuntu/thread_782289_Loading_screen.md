---
title: "Loading screen"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Mezillious on 2008-05-04
Hey guys, first I'd like to say that the amount of information and assistance available on these forums is enormous! Well done for supporting such a great OS and being so friendly and knowledgable to newcomers like myself.

My problem is that I have upgraded from 6.06 to 8.04 and it looks great, everything seems to run fine so far. The only problem I have is that i've lost the load up screen, not the bootsplash screen with the progress bar, the splash screen that comes up after you log in which shows what Ubuntu is loading. I just don't like that gap where it sits there with a blank screen for a while loading stuff, I'd like my load up screen back! Can anyone help me?

Thanks
Craig

---

### Post by Tatty on 2008-05-04
I dont seem to have that either... I hadnt noticed till just now.  I dont think I had that in gutsy either...

---

### Post by iAtari on 2008-05-04
You mean the splash that appears when the startup sound is activated, and little icons appear on the bottom left of the splash screen?

I'm running 8.04 and mine doesn't show this splash screen either. It used to in 7.04... :|

---

### Post by VraiChevalier on 2008-05-04
Perhaps what you are looking for is in the Grub configuration file. I think it may be the "quiet" splash setting. I'm not in my Ubuntu at this moment so I cannot check on this.

---

### Post by VraiChevalier on 2008-05-04
Mezillious,  I'm not sure if this is what you mean but here is a link to Hermans site which describes editing the "menu.lst" file. Here you can see how to edit the file so you can see what is loading.
[http://users.bigpond.net.au/hermanzone/p15.htm#defoptions](http://users.bigpond.net.au/hermanzone/p15.htm#defoptions)

> defoptions
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

This means every time a new kernel is added to the list, the new kernel's default entry ( the one we normally use for booting) in menu.lst will be accompanied automagically by the option '=quiet splash'.
quiet means we won't see a lot of white typing scrolling up a black monitor background to explain every step of the process of booting up the system, (unless something special is there we might want to see, like a file system check).
splash means we will see a nice picture in our monitor  while our computer is booting. Some people customize these splash screens too. It's a different sort of splash screen than the one behind the grub menu.

Hope this helps.

---

### Post by Tatty on 2008-05-04
I think Mezillious is talking about the post-gdm splash which shows it loading sounds, icons etc... I dont recall seeing it since feisty.

---

### Post by VraiChevalier on 2008-05-04
> **Tatty said:**
> I think Mezillious is talking about the post-gdm splash which shows it loading sounds, icons etc... I dont recall seeing it since feisty.

Oops!:oops:
I'm going to have to fire up one of my old machines with 6.06 still on it to see what this looks like. I never even realized it was gone!

---

