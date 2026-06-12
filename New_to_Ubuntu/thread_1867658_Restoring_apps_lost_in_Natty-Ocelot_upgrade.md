---
title: "Restoring apps lost in Natty-Ocelot upgrade"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-10-23
Since I'm travelling with a limited capacity 3G internet access,  I took care to save all my Natty folders (home, etc, lib, proc, sys  var, usr) on a seperate drive before I ran an Ocelot live CD to upgrade my Natty.

Having now upgraded, I find that I've lost the following which were previously installed in my Natty:

Skype,  GIMP,   Adobe Flash Player.

I also had SeaMonkey installed in my Natty and that seems to have survived  the upgrade intact,  except that it's lost its logo and shows as a "?" 

To avoid wasting valuable Mbytes on my 3G internet, I'm wondering if it would be possible to rescue the necessary files for these missing apps from my Natty backup, and transfer them to my Ocelot files.

For example in my Natty home folder I see I have both .Skype and .adobe folders.   By copying these across to my Ocelot,  could I expect to be able to reinstall Skype and Adobe Flash there without incurring a heavy download?

---

### Post by haqking on 2011-10-25
> **Sleepy-zz-John said:**
> Since I'm travelling with a limited capacity 3G internet access,  I took care to save all my Natty folders (home, etc, lib, proc, sys  var, usr) on a seperate drive before I ran an Ocelot live CD to upgrade my Natty.

Having now upgraded, I find that I've lost the following which were previously installed in my Natty:

Skype,  GIMP,   Adobe Flash Player.

I also had SeaMonkey installed in my Natty and that seems to have survived  the upgrade intact,  except that it's lost its logo and shows as a "?" 

To avoid wasting valuable Mbytes on my 3G internet, I'm wondering if it would be possible to rescue the necessary files for these missing apps from my Natty backup, and transfer them to my Ocelot files.

For example in my Natty home folder I see I have both .Skype and .adobe folders.   By copying these across to my Ocelot,  could I expect to be able to reinstall Skype and Adobe Flash there without incurring a heavy download?

Upgrades are not the best way to do things IMO, especially as alot of people are having issues with upgrading from 11.04 to 11.0 mainly due to Gnome 2 to Gnome 3.

I would be inclined to reinstall the apps to circumvent possible headaches.

I believe skype is now in a official 11.10 repo, though i may be wrong, but i remember reading it

---

### Post by Sleepy-zz-John on 2011-10-25
> **haqking said:**
> Upgrades are not the best way to do things IMO, especially as alot of people are having issues with upgrading from 11.04 to 11.0 mainly due to Gnome 2 to Gnome 3.

I would be inclined to reinstall the apps to circumvent possible headaches.

I believe skype is now in a official 11.10 repo, though i may be wrong, but i remember reading it
Thanks for the comments.   My main motivation for upgrading instead of installing new was because I hoped it would save considerabl e Mbytes on my limited temporary 3G access.  I reckoned new downloads of Seamonkey and Skype and GIMP and Adobe flash, plus all new Ocelot updates would add up to a prohibitive total. This motivation didn't turn out to be as valid as I'd hoped,  though.  

Although I've now managed to muddle through by downloading some of my missing apps via a public free wifi,  I do still wonder how practical it would be to copy files across from an old Natty backup into Ocelot without running into multiple headaches?

---

### Post by decoherence on 2011-10-25
The thing is, the programs from Natty are expecting the libraries from Natty. If you were to try and run a Natty binary on Ocelot, you would likely get an error about not being able to find libwhatever.4.so because Ocelot is using libwhatever.5.so (just to be clear, i'm made this library up.)

One thing you could try but definitely shouldn't is symlinking the new libraries to their old names. Provided nothing significant has changed in how the library works, the program may function. However, it's a lot of effort, it could screw up future upgrades and Strange Things can happen. In other words, in an emergency where you are totally cut off from the world it might be something to try but it would be far better to muddle through with the public wifi.

ADD: I supposed you could also try copying the needed libraries from your Natty backup. But again, I'm pretty sure that sort of thing is outside the usage scenario Canonical tests for. It might work but it also might make life hell.

---

