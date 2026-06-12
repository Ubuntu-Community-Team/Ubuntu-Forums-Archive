---
title: "Idle on channel 2."
date: 2013-02-08
forum: New to Ubuntu
---

### Post by Illusionistik on 2013-02-08
Just wiped my HD and wanted to just install ubuntu. Had a live cd so I originally had the error with "idling channels"  when I tried to boot from cd. I researched that at boot screen press F6 and select nomodeset.

Awesome, it worked. I connect to my Internet mouse/headset working perfect I'm happy that its actually working. It starts doing an upgrade and after that is finished asks to restart. I hit yes, and as it was restarting it asked me to take out the download cd and close tray and when it finally restarted, boom again the same error of idling channels. Now that have it downloaded(at least I think so) and "updated" I actually don't get that same menu screen when I had the livecd in to allow me to select nomodeset. 

So I put the cd back in and selected nomodeset again and this time just clicked try ubuntu without install (because I didn't want to reinstall it because I technically did that already and apparently updated it). I do some more research and I found how you can permenantly set the nomodeset action so that I don't have to constantly do it 

I followed the steps so I actually wrote nomodeset after "quiet splash" while on the "trial" Ubuntu.(hopefully you guys understand what I did here)

So I saved it and restarted it without CD thinking that I have that option set so I can go to me newly installed and updated ubuntu. But no. I think it did t work because I did it on the trial and they are on different "partitions?" I'm not sure

So that's basically all of it. I just need to bypass the (novaeu) idling channel error after I downloaded ubuntu and how to fix it permenantly so I can just boot straight to my desktop without any problems.

---

### Post by arpanaut on 2013-02-08
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

After you set this temporarily at the grub menu, and get into your install try to get the proper video drive installed. If that fails then you will need to set the nomodset option permanently, which is covered in the link above.

---

### Post by Illusionistik on 2013-02-08
Thanks, I'm going to bed right now but will try this in the morning and respond with the results.

---

### Post by Illusionistik on 2013-02-08
Great more problems, I managed to get to the grub menu and see ubuntu kernel but nothing happens when I press E to edit it so that I can temporarily set nomodeset. Is there any way around this so I can login to permenantly set it or another way to temp set it? I'm completely stuck right now.

---

### Post by Illusionistik on 2013-02-08
Update: So playing around I found out I had to press ' and not e to edit the kernel to temporarily set nomodeset. I hit Ctrl-X and it booted with new settings. Took me to my desktop and I followed the steps to permenantly set that option saved it and restarted it to test if it'll boot with no problems. And boom same error I'm gonna try it again to see if maybe I didn't save it correctly?

Update2: I tried this again And saved it but it still did not work. I even tried putting another cmd after nomodeset "acp_osi=Linux" it was along those lines. Still the same error. Right now I'm on the desktop but I continuously have to temporarily set nomodeset to login. I have a nvidia and that's what I think is the main problem so I think just getting updates for it will solve it? Basically I'm asking what can I do to make my vidia card cooperate instead of me having to set it to bypass it cuz it isn't working.

---

### Post by Illusionistik on 2013-02-08
Alright Im gonna close the thread but I will explain what i did.

After temp setting nomodeset in grub to access my desktop I tried to then permenantly set it so that i didnt have to keep on doing it on start up. I tried adn tried and it didn't work. No idea why but w/e.

I then just tried to solve the problem that was being caused with the idling channels or w/e instead of trying to bypass it with the nomodeset command.

I found out if you go to system settings then software sources and then go to additional drivers, you can change your video card driver to i believe a proprietary one and your set to go. thanks for your help.

---

