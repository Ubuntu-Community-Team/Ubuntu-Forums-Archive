---
title: "Ubuntu Feels Sluggish. What Can I do about that?"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by asunny on 2012-08-03
Hi there,

Just installed Ubuntu 12.04, replacing my Windows XP. My other computer is running Windows 7. Both computers have similar specs, this one has an Nvidia graphics card and 4 GB of DDR2 Ram, 320GB hd, and a duo-core cpu.

Everything on Ubuntu feels a bit sluggish. I click on firefox for example, and I'm not sure if anything is happening. A few seconds later it opens. Same for other applications, like the update manager.

On Windows I am able to disable services I don't need using services.msc, and prevent applications from starting up automatically, like adobe updater and itunes updater. What programs do you use on Ubuntu to do the same thing?

Many thanks,
A.S.

---

### Post by Paqman on 2012-08-03
Have you installed the drivers for your graphics card? Is this a laptop with "Optimus" graphics?

---

### Post by asunny on 2012-08-03
It is a nvidia quadro, so no, not the type you mentioned. I used the restricted drivers application to use the 'recommended' driver, and it tells me that it is active.

I am thinking I must need to do one or more of the following:

1) Reduce the 'pretiness' of unity. Disable some effects, or switch to a low-resource version of it. Unity 2d?
2) Turn off some services to reduce its overhead... for example, automatic updates, because I can manually check for updates.
3) Turn off some auto-started applications.

Maybe there are other options as well.

---

### Post by vasa1 on 2012-08-03
> **asunny said:**
> It is a nvidia quadro, so no, not the type you mentioned. I used the restricted drivers application to use the 'recommended' driver, and it tells me that it is active.

I am thinking I must need to do one or more of the following:

1) Reduce the 'pretiness' of unity. Disable some effects, or switch to a low-resource version of it. Unity 2d?
2) Turn off some services to reduce its overhead... for example, automatic updates, because I can manually check for updates.
3) Turn off some auto-started applications.

Maybe there are other options as well.
So try Unity 2D.
Automatic updates may slow things down while they're actually happening but not otherwise.

---

### Post by asunny on 2012-08-03
I was looking into how to do that and I read that when you switch to unity2 using metacity replace, you lose the hud. Which was the main reason I wanted to use unity. 

I've installed ccsm and turned off some animations, and things have slightly improved. There is no longer a delay switching between open windows. And menus are opening a little quicker and following my mouse a little better as well. 

I'm currently downloading xubuntu 12.04 right now to see if it works a little better on my system.

Thanks for the replies.

---

### Post by Paqman on 2012-08-03
Check in System Monitor. Is your CPU being maxed out? Is your RAM being use heavily? Are you using any swap? If none of the above it's going to be graphics, and disabling services and the like won't make any difference.

---

### Post by asunny on 2012-08-03
Thanks PAQMAN,

I'd already installed xubuntu 12.04 before I read your reply and things are much better. So it is probably graphics like you said, my video card not playing nice with compiz most likely. 

The only thing that remains sluggish is the ubuntuforums website, clicking quick links continues to respond slowly, but that's probably more to do with how much traffic there is here. :)

Thanks both for replies!

AS

EDIT: Wesbite isn't slow either. Xubuntu was just downloading a ton of updates.

---

