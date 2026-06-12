---
title: "Dell GX 260 with Nvidia FX5200"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by oldsmobile2 on 2014-04-23
Hi, First I would like to say that i am a complete noob in programming and i have no unerstanding of languages but a friend recommended me Ubuntu and i installed ubuntu 14.04 in place of win 7 on my GX 260 with Nvidia FX5200  the installation went fine except some glitches like the screen kept twitching and the speed was slow but other than that it went fine.Due to the fact that it was extremely slow while i used it due to to some reason i don't know maybe it was running on software mode (just a hunch) i had to remove it and had to revert back to win7 so my question is.Is there any ubuntu version which is fast,reliable and with some easy instructions because i fiddled for 2 hours in 14.04 just to see if the graphic cards drivers were installed or not and even then i failed to do so and there was no device manager and on every site i kept seeing these sudo codes and i did'nt know what they were.I liked the UI of Ubuntu 14.04 so anything similar to that would be just great and i also use my PC for games so support for graphic card drivers should be there.

---

### Post by kc1di on 2014-04-23
We would really need a little more information in order to give you the best advise.  Linux is not like windows and you'll have to be willing to learn some new stuff, but once learned it's not bad and you'll have a great system.  

To start with give us the make & model of your computer (IE. is it an hp , compaq, dell etc. ) How much ram does it have 
you gave the video card already.(which by the way is quite old) There are drivers for it though and it's not hard to install them.  but any other information would be helpful. is it a laptop or desktop system?

---

### Post by suprleg on 2014-04-23
I'm sure you'll have little trouble getting ubuntu 14.04 to work well on that machine. I just did an install on my '06 Dell 9150 with zero problems. This is a fresh install not upgrade or dual boot?

---

### Post by deadflowr on 2014-04-23
I think your graphics card might be a little on the old/weak side for normal Ubuntu.
I'm guessing you're running the open source nouveau drivers.
Perhaps seeing if there are better drivers for it might help improve performance.

(You can see what drivers are available by pressing the super key(windows key on the keyboard) and typing
"software and updates"
Then go to the tab marked Additional Drivers.
It should listed drivers aside from the open source Xorg drivers.)

More, possibly here
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

My own opine is that if you can find a more modern graphics card, the performance should greatly improve.

Two cents in the wishing well from me, at least.

---

### Post by oldsmobile2 on 2014-04-23
thank you for the prompt reply...don't really get that alot in other forums.
Yeah it's a pretty ancient machine 
It is an old Desktop Dell GX260 with 768 MB ram,
2.4 GHZ Processor  
128 mb graphic card with 2.0 pixel shader
i just want an OS to keep the PC going because win xp has no support now and i don't like win7 that much.I willing to give linux a try and to learn new things.
so what would you recommend??
I also did a Fresh Install but i think my desktop is just not cut out to run 14.04.  K._Besig.

---

### Post by oldsmobile2 on 2014-04-23
Thank you.
 I did go to the additional Drivers tab but there was nothing there and it kept on saying that the drivers were up to date.I think you are right that even if the drivers were there the hardware is'nt that powerful plus my PC can't even run win 8 beacuse of some XD feature so thinking that an OS that came this week could run smoothly was bit of a dream.

---

### Post by deadflowr on 2014-04-23
Your processor should be, somewhat, fine.
If you could increase the ram, that would help improve it some.
And Ubuntu's desktop, Unity, I believe, works best with at least a 256MB graphics card.

---

### Post by PondPuppy on 2014-04-23
A common remedy for computers with little RAM is to try Lubuntu (or Xubuntu). These are based on Ubuntu but their windowing managers put fewer demands on the system. As someone just transitioning from Windows, you might find them less confusing "out of the box" than the Unity desktop.

If you can download Lubuntu and/or Xubuntu and burn the file to a DVD, you can try them without having to do a full install. (Running from a DVD is, of course, clunkier than running from an installed OS.)

---

### Post by oldsmobile2 on 2014-04-23
hmmm The thing is I might upgrade my PC probably dual core with a good Graphic card at the end of my semester i.e after 3 months,
 but i need something until then,it could be anything except Microsoft's OSs and which is similar to ubuntu's UI.

---

### Post by oldsmobile2 on 2014-04-23
Could you please tell me that according to you which of these Lubuntu versions will run faster and still be somewhat beautifull and latest given that priority is to speed.
on my PC.

---

### Post by SeijiSensei on 2014-04-23
Another vote for lubuntu on your hardware.  Here's the disk image if you want to give it a try:

[http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-desktop-i386.iso)

That one's small enough that you can burn it to a CD.

---

### Post by oldsmobile2 on 2014-04-23
forgive me for asking but will it be fast ?
Because the standard one took almost 3,4 minutes just to boot up.

---

### Post by deadflowr on 2014-04-23
Lubuntu should run faster than standard Ubuntu.
And as it sits now, I would agree that Lubuntu is probably the best version for you to run on the machine as it is right now.

But I don't know if the boot time will improve.

My earlier advice is strictly what you would probably need to do to get Ubuntu, normal?, running effectively.
If increases in ram and graphic card quality are not possible or are too troublesome, then by all means, try Lubuntu.

---

### Post by Vladlenin5000 on 2014-04-23
Any Dell Optiplex GX260 is quite old now and the nVIDIA card - not from Dell -, a more recent addition and improvement, helps but not much. This machines were shipped either with a couple of 2003-2004 integrated Intel Graphics and/or slightly better 32MB ATI Radeon.

So... Lubuntu definitely (and proprietary nVIDIA drivers).

---

### Post by kc1di on 2014-04-23
I would say Lubuntu also , if you want it to look nice (Not that Lubuntu doesn't you might want to take a look at LXLE [here]("http://www.lxle.net/download")) Good luck.

---

### Post by mörgæs on 2014-04-23
I have been running a 270 for some time. After Lubuntu is running and updated I recommend playing with swappiness, as described in the link in my signature.

---

### Post by oldsmobile2 on 2014-04-24
Thank you all for your help i will try Lubuntu 14.04 as soon as i get get my hands on it (started downloading).
Furthermore can any body help me to a post where i can learn how to use basic linux just enough to use this Lubuntu.

---

### Post by mörgæs on 2014-04-24
[https://ubuntu-manual.org/](https://ubuntu-manual.org/)

---

### Post by kc1di on 2014-04-25
there is also a good introduction to linux on You Tube here :  [https://www.youtube.com/watch?v=_gCwCOhMcog](https://www.youtube.com/watch?v=_gCwCOhMcog)

---

### Post by oldsmobile2 on 2014-04-25
thank you for providing me with the tutorials these ought to cover all the basics intended for running ubuntu I guess now i'll just close this as solved because I certainly got what i needed 
again I thank you all for your help.

---

