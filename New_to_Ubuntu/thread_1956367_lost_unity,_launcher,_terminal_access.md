---
title: "lost unity, launcher, terminal access"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by cray5656 on 2012-04-10
SOLVED

Hi
I installed Ubuntu 11.10 onto my mothers laptop showing her how much better than Windows it is and I went into compiz and set up the rotating cubes, then decided it wasnt needed.

As a result now I cant access Unity, terminal etc.

How do I get them back?

Thanks

---

### Post by PhantomTurtle on 2012-04-10
When you enabled the cube effect, did you disable anything else.(like the ubuntu unity plugin) You can try and install another desktop environment until you figure it out. Press CTRL+ALT+F2. this will give you a virtual console. install kde from it.
```
sudo apt-get install kubuntu-desktop
```
or xfce
```
sudo apt-get install xubuntu-desktop
```
when it is done type in 
```
sudo shutdown now
```
and then start it up again and select kubuntu from the login screen

---

### Post by daslinkard on 2012-04-10
I'm assuming you used the following sudo command:

> sudo apt-get install compizconfig-settings-manager

To Uninstall this you can use the following sudo command:

> sudo apt-get remove compizconfig-settings-manager

Then you can utilize the following command to bring back Unity

> unity --reset

This should bring back your Unity, Terminal, etc. back to the way it was prior to the compiz install.  i was messing around with Compiz late last week and this happened to me as well.  The above solution brought everything back to the way it was prior.

---

### Post by grahammechanical on 2012-04-10
What did you do? Did you uncheck the Unity plugin?

Can you log in to Ubuntu 2D? That uses a different window compositing manager. If you can get back to a desktop you can run CCSM again and make sure that the Ubuntu Unity Plugin is enabled.

Oh, by the way, in 12.04 the option to uncheck the Unity Plugin is removed.

Regards.

---

### Post by cray5656 on 2012-04-10
Hi Thanks

I think in uninstalled the unity plug in.

now to make matters sligtly worse I cant remember my password, well i am sure what it is but it is saying incorrect. I have checked cap locks etc.

I do have docky showing but only have Chrome and the rubbishbin icons

sorry to be a pain.

---

### Post by cray5656 on 2012-04-10
basically all i see is the desktop with no icons Docky down the bottom.

and in the upper left side File Edit View Go Bookmark Help

---

### Post by PhantomTurtle on 2012-04-10
> **cray5656 said:**
> basically all i see is the desktop with no icons Docky down the bottom.

and in the upper left side File Edit View Go Bookmark Help

I had a similar problem like that. I think you might have done something with the unity plugin that caused it to do this. I'm not sure how you can fix it, but you can install a different desktop environment until someone else helps you fix it.

---

### Post by daslinkard on 2012-04-10
First call up the Terminal

> CTRL+ALT+TNext please type the following command

> sudo apt-get remove compizconfig-settings-managerAfter that is finished uninstalling please type the following command in the Terminal:

> unity --resetThis should reset the unity and uninstall the compiz so you can retry your install of the compiz or you can stick with Unity.

---

### Post by PhantomTurtle on 2012-04-10
Sorry I forgot to add this, you can reset your compiz settings in the terminal. Open it up and type in, 
```
gconftool-2 --recursive-unset /apps/compiz
```
You do not need to remove CCSM as the post above me mentions(you could try it as well if you want to), but I would be careful with it the next time you play around with it.

---

### Post by cray5656 on 2012-04-10
Brilliant!!!!

Thanks people s much!!!! Respect!

---

### Post by PhantomTurtle on 2012-04-10
You should post the solution and mark the thread solved.

---

### Post by daslinkard on 2012-04-10
I agree with Phantom...I'm curious if this was able to get this solved for you.

---

### Post by daslinkard on 2012-04-10
Also I came across this [link]("http://ubuntuforums.org/www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html") and it made me think of you.  The linked page deals specifically with how to reset Unity, Launcher Icons, or Compiz in Ubuntu.

---

### Post by cray5656 on 2012-04-10
This is what fixed my problem
irst call up the Terminal

 	Quote:
 	 	 		 			 				CTRL+ALT+T 			 		 	 	 
Next please type the following command

 	Quote:
 	 	 		 			 				sudo apt-get remove compizconfig-settings-manager 			 		 	 	 
After that is finished uninstalling please type the following command in the Terminal:

 	Quote:
 	 	 		 			 				unity --reset 			 		 	 	 
This should reset the unity and uninstall the compiz so you can retry your install of the compiz or you can stick with Unity.

---

### Post by daslinkard on 2012-04-10
Awesome....glad it helped you!  I just had to deal with this last Friday night and my heart was in my throat...until I found the sudo commands.  Anytime you need anything with Ubuntu...we're here for you!

---

### Post by cray5656 on 2012-04-10
Thanks again everyone for such smart and fast support!

I have put Ubunti on my 2 sons laptops, mother inlaw, her sister and my mother. The all love Ubuntu. I tell everyone how great Ubuntu is :-)

I have it running on my MacBook Pro.

I love Ubuntu enough to get an Ubuntu baseball cap and heaps of stickers :-)

---

### Post by daslinkard on 2012-04-10
LOL....that's awesome...you sound a lot like me as I continuously try to convert people to Ubuntu.  I only have the 1 sticker though....BUT I have started a blogging website [here]("http://livinglinux.wordpress.com/").  Good luck with Linux!

---

