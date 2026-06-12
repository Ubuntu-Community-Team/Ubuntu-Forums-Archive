---
title: "dual monitor help"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by benjaminjames on 2008-07-13
wow im sure this question has been asked like a million times but i have searched and searched and i cannot find any threads that help me so here goes :)
i have a 19 inch lcd monitor as my main display and i want to set up my 42 inch plasma as a second display so that i can surf and stuff on my main monitor whilst watching a film in full screen on my second monitor. in windows this is called dual view and is a simple as clicking on 2 buttons in the nvidia control panel. when i installed the nvidia control panel for ubuntu i was completely lost it is amazingly different. i also want to be able to drag things from one monitor to the other. i know i sound real demanding and i apologize i just really need to get this set up so that i can delete my vista partition and go all ubuntu, can anyone help remember i am a noob with a minimal knowledge of linux so go easy on me :) hehe thanks all. btw im using an amd 5200+ 2 gig ram and  a 7300le nvidia graphics card i have the restricted drivers installed and working fine

---

### Post by overdrank on 2008-07-13
> **benjaminjames said:**
> wow im sure this question has been asked like a million times but i have searched and searched and i cannot find any threads that help me so here goes :)
i have a 19 inch lcd monitor as my main display and i want to set up my 42 inch plasma as a second display so that i can surf and stuff on my main monitor whilst watching a film in full screen on my second monitor. in windows this is called dual view and is a simple as clicking on 2 buttons in the nvidia control panel. when i installed the nvidia control panel for ubuntu i was completely lost it is amazingly different. i also want to be able to drag things from one monitor to the other. i know i sound real demanding and i apologize i just really need to get this set up so that i can delete my vista partition and go all ubuntu, can anyone help remember i am a noob with a minimal knowledge of linux so go easy on me :) hehe thanks all. btw im using an amd 5200+ 2 gig ram and  a 7300le nvidia graphics card i have the restricted drivers installed and working fine

Hi and you can use nvidia settings and the command is 
 ```
gksu nvidia-settings
```
Then Xserver display config, and configure your additional monitor with twinview.

---

### Post by benjaminjames on 2008-07-13
hi thanks for the reply but when i go into nvidia settings and set up my second screen in twin view if i try to maximize a window in one monitor it stretches it over both so i end up with half of the movie on one screen and half on the other, how do i set it up so that it maximizes on one screen only leaving the other screen free for surfing etc??

---

### Post by benjaminjames on 2008-07-14
bump

---

### Post by morganGDFP on 2008-07-20
I got it sorted (well, sort of anyway)..
I put both my screens (a 42" Plasma and my LCD monitor) to position "absolute" and placed the plasma at position +0+0 and the LCD at +1360+0.
Now I can maximize the movie on the plasma screen and keep the other for whatever else I want to do.

Just try that and see if it works..If you're using VLC media player it has a default setting for maximizing that you will have to change as well..

I have on problem left however..

When I download stuff, get mesages or put things on my desktop they sometimes get placed on the part of my desktop that belongs to my plasma..This is a pain in the a*** since it is not always turned on..

How can I make ubuntu understand that I ONLY want to use my 42" plasma to watch movies on?

---

