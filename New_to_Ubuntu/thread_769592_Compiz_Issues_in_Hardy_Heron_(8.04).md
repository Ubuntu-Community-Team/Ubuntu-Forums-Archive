---
title: "Compiz Issues in Hardy Heron (8.04)"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Paqmann on 2008-04-26
I have been running Gutsy for the past few months on a Dell Inspiron 6000 

-1.6GHz Centrino Processor 
-1.2Gb RAM 
-30Gb HD
-ATI Mobility Radeon X300 video

Using Gutsy I had Compiz enabled, running beautifully, using the opensource video drivers and xgl (if memory serves). Upon upgrading to Hardy, I found that Compiz was disabled. I tried enabling it (System->Preferences->Appearance->Visual Effects and click either 'normal' or 'extra'), but received a message stating that the graphics could not be enabled. I tried using the ATI Restricted Drivers, but that just gives me a white screen when I try to enable Compiz.

I looked around online and found that maybe I needed to reinstall xserver-xgl. I did that, and (using the restricted drivers) got Compiz working, but very, very sluggishly. So slowly, in fact, that I couldn't use it. The helpful response I found for this problem was to remove xgl, taking me back to my original, helpless state. 

So that leaves me in this position: I need XGL for Compiz to work at all, but I need to delete XGL in order for Compiz to work properly.

You can see the pickle I am in. 

If anybody has any ideas (or needs more information; I tried to keep from getting too verbose here) I would be very grateful.

-Johannes

PS I know similar threads to this one are all over the forums already, but I've been through so many of them and just been run in circles that I figured this was the next step in finally getting somewhere.

---

### Post by mjantz on 2008-04-26
You aren't the only one with these problems. I am having the exact same issues almost verbatim as you described it with an ATI X1400 card.

---

### Post by LaRoza on 2008-04-26
Would this help? [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by mjantz on 2008-04-26
I tried the SKIP_CHECKS fix suggested in that thread, but I am still getting a white screen when I try to run compiz --replace. I am currently using the restricted drivers for my ATI X1400 card, but I have removed xgl for the reason described in Paqmann's post.

---

### Post by Paqmann on 2008-04-28
I'm hoping to find a fix rather than just a workaround. Something about my obsessive-compulsive nature, I guess. I'll take broken-awaiting-a-fix over working-with-a-workaround-which-I'll-eventually-have-to-remove-if-it-ever-gets-fixed.

---

### Post by Paqmann on 2008-04-28
Bump.

---

### Post by Paqmann on 2008-04-28
Got sick of searching and tried the workaround; it did the same thing as enabling Compiz normally--went to a white screen. So the workaround is a no go. 

It also might be worth mentioning that when I look at the restricted divers manager, the ATI Accelerated Graphics Driver is labeled as 'enabled' bot 'not in use'.

---

### Post by ocean223 on 2008-04-28
Same thing happened to me and it drove me nutso.  You need to get the Ubuntu restricted extras package first. I think I got it in Synaptic.  THEN go to system>administration>hardware drivers and enable the restricted driver. 

Hope this helps.:)

---

### Post by rmksd on 2008-04-29
I have the exact same problem with my radeon 9550 (my topic just died and was never replied to :( )
I have tried just about every guide around to fix this, but nothing seems to do the trick
I was really hoping to get compiz in Hardy :(

...and I just tried the restricted extra package with no difference.

---

### Post by joshrobinson on 2008-04-29
if the drivers "not in use" uncheck it, check it again, and restart

as for the white screen, i got that once, i changed back to the vesa driver, the reinstalled the fglrx driver, and it eventually worked fine

---

### Post by Paqmann on 2008-04-30
Update:

I tried a fix found in another thread in which I had to install a new driver offered on ATI's website. Rather than working, it tanked all my video settings to the point that, on the rare occasion that I could get into the GUI, all the video was smushed onto the top half of the screen and was interlaced and staggered or something so that it was impossible to see anything. 

I decided to cut my losses and do a fresh install of 8.04.

The new install looks great, runs fast, and automatically set up my ATI restricted driver properly. It also managed to get all of my video settings right from the get-go, something which Gutsy failed to do, making the overall installation quite a bit easier.

I still can't get Compiz to work, but now instead of giving me the white screen it just informs me that 'Desktop Effects Could Not Be Enabled'. Also, the ATI Restricted driver (now labeled as ATI Fire GL) is still shown as enabled but not in use. I tried your uncheck, check, and reboot trick and, not surprisingly, saw no improvement. 

I'm about to try the Ubuntu Restricted Extras package. I'll let you know if I get any results that way.

EDIT: I can't seem to find anything in Synaptic related to Restricted Extras. What is this and where did you find it?

---

### Post by mjantz on 2008-04-30
I assume what ocean223 was talking about was a package titled ubuntu-restricted-extras. I installed it, but I am still getting the white screen.

---

### Post by Paqmann on 2008-04-30
Got it. Had to do an apt-get update in order to be able to find the package. We'll see how things go.

Update: Success! At first I thought it didn't work, but then I looked at the restricted drivers and realized that, when I installed ubuntu-restricted-extras, it had disabled the restricted ATI driver. When I enabled it and rebooted, everything worked. 

So much has changed with my computer since this thread started that I don't know if this fix will work for people who upgraded to Hardy instead of a fresh install. I hope it does. 

To recap: In order to get Compiz working with a fresh install of Hardy Heron (8.04) on a Dell Inspiron 6000 with an ATI Mobility Radeon X300, you have to install the package ubuntu-restricted-extras and ensure that your ATI accelerated graphics driver is enabled.

Thanks, everyone, for your help.

---

