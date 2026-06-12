---
title: "Unity gutted bone dry from last update"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-09
I just did an update earlier and it gutted Unity complety and won't give it back!!
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libnux-1.0-0 (< 1.6.2) but 1.8.0-0ubuntu1 is to be installed
         Depends: libunity-core-4.0-4 (>= 4.12.0) but it is not going to be installed
         Depends: libunity-core-4.0-4 (< 4.14.0) but it is not going to be installed
 unity-2d : Depends: unity-2d-panel but it is not going to be installed
 unity-2d-launcher : Depends: libunity-2d-private0 (= 4.4.0-0ubuntu1) but it is not going to be installed
 unity-2d-places : Depends: libunity-2d-private0 (= 4.4.0-0ubuntu1) but it is not going to be installed
 unity-2d-spread : Depends: libunity-2d-private0 (= 4.4.0-0ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@dale:~#

---

### Post by flipper T on 2011-09-09
was it a partial upgrade ?

---

### Post by ventrical on 2011-09-09
> **flipper T said:**
> was it a partial upgrade ?


Absolutely not! I am running a fresh install from beta .. but I just read in another forum where they are saying - just wait - and it will fix in the repositiories eventually.

 I am in GNOME now. I  would rather have Unity.

thanks

---

### Post by flipper T on 2011-09-09
No problem !

:)

---

### Post by sgage on 2011-09-09
> **flipper T said:**
> was it a partial upgrade ?

Of course it was. Doesn't anyone read the sticky about partial upgrades?

Just use Synaptic. If you click on "mark all upgrades", it instantly pops up a list of what is going to be installed, what is going to be ugpraded, what is going to be unchanged, and at the top of the list, WHAT IS GOING TO BE REMOVED.

Many folks got bitten by this today. I could have told you this was going to happen. In fact, last time I did post a warning message about this very situation, but was told it was inappropriate. So to hell with it.

---

### Post by lobo_tuerto on 2011-09-09
Same thing happened here, and GNOME session would start but _broken_, no applications menu, just a window fullscreen without borders.

Had to Ctrl+Alt+F1 and then install unity by hand, it worked.

---

### Post by ventrical on 2011-09-09
> **sgage said:**
> Of course it was. Doesn't anyone read the sticky about partial upgrades?

Just use Synaptic. If you click on "mark all upgrades", it instantly pops up a list of what is going to be installed, what is going to be ugpraded, what is going to be unchanged, and at the top of the list, WHAT IS GOING TO BE REMOVED.

Many folks got bitten by this today. I could have told you this was going to happen. In fact, last time I did post a warning message about this very situation, but was told it was inappropriate. So to hell with it.

Hey ..

  I never did a partial upgrade. I loaded it from synaptic.

---

### Post by lobo_tuerto on 2011-09-09
Hey, maybe you did, but just didn't know?

Read this: [http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

---

### Post by flipper T on 2011-09-09
Hey, maybe he didn't, and does know it

---

### Post by castrojo on 2011-09-09
The new Unity from this week (and a bunch of stuff it uses) is being uploaded, give it a few hours and it should resolve itself.

---

### Post by sgage on 2011-09-09
> **ventrical said:**
> Hey ..

  I never did a partial upgrade. I loaded it from synaptic.

It was indeed a partial upgrade - synaptic just doesn't happen to call it that. It simply tells you what it's about to do, and then you make your decision. When it says "to be removed - unity*", you might decide to wait :KS

Sometimes I don't think I really need the things in the "to be removed" list, and let 'er rip. Sometimes I really wish I didn't, but when I'm fiddling around in the dev cycle, I am well backed-up and fully prepared to reinstall :)

---

### Post by Quackers on 2011-09-09
Tha packages that did the damage were the libnux ones. In synaptic it told me that unity, ubuntu-desktop and a load of unity 2D stuff was going to be removed. I updated everything except those 2 libnux packages and all is well.

---

### Post by sgage on 2011-09-09
> **Quackers said:**
> Tha packages that did the damage were the libnux ones. In synaptic it told me that unity, ubuntu-desktop and a load of unity 2D stuff was going to be removed. I updated everything except those 2 libnux packages and all is well.

Yes, if you have a feel for what is causing the "to be removed", you can finesse the upgrade with some precision using Synaptic. 

When "mark all upgrades" results in nasty removals, I cancel out of it, then go to the Upgradable filter, and select just the upgrades I think are safe. Then mark them for upgrade, and Synaptic tells you of any problems. Often with a couple of iterations you can figure out what's going on.

I still maintain frequent backups :lolflag:

---

### Post by lobo_tuerto on 2011-09-09
Yeah, frequent backups are key! Just did that after Unity got removed and I reinstalled it, hehe.

---

### Post by ventrical on 2011-09-09
> **Quackers said:**
> Tha packages that did the damage were the libnux ones. In synaptic it told me that unity, ubuntu-desktop and a load of unity 2D stuff was going to be removed. I updated everything except those 2 libnux packages and all is well.

  And it now foobarred GNOME Shell and boots like Windows XP !!

:)

---

### Post by ventrical on 2011-09-09
> **sgage said:**
> It was indeed a partial upgrade - synaptic just doesn't happen to call it that. It simply tells you what it's about to do, and then you make your decision. When it says "to be removed - unity*", you might decide to wait :KS

Sometimes I don't think I really need the things in the "to be removed" list, and let 'er rip. Sometimes I really wish I didn't, but when I'm fiddling around in the dev cycle, I am well backed-up and fully prepared to reinstall :)


 Alright .. so rub some salt in the wound eh ! :) 
ahraehaeha

---

### Post by jbicha on 2011-09-09
No, GNOME Shell being broken is for different reasons.

---

### Post by ventrical on 2011-09-09
> **jbicha said:**
> No, GNOME Shell being broken is for different reasons.

I just went to uninstall GNOME-SHELL and it re-installed Unity 3D!!

 So I got Unity 3D back and I'm a happy camper :)

  I think there is a conflict between Unity and GNOME Shell.

---

### Post by tadcan on 2011-09-09
Ahh so thats whats been going on. I just grabbed a new daily build and reinstalled on the virtual machine

---

### Post by ventrical on 2011-09-09
> **tadcan said:**
> Ahh so thats whats been going on. I just grabbed a new daily build and reinstalled on the virtual machine

Synaptic automatically installed Unity 3D when I uninstalled GNOME shell.

Really weird ..as if they had a depends.

---

### Post by sgage on 2011-09-09
> **ventrical said:**
> Synaptic automatically installed Unity 3D when I uninstalled GNOME shell.

Really weird ..as if they had a depends.

Now that's weird! Perhaps good old Synaptic didn't want to leave you with no desktop, so it thoughtfully installed Unity. :KS

---

### Post by ventrical on 2011-09-09
> **sgage said:**
> Now that's weird! Perhaps good old Synaptic didn't want to leave you with no desktop, so it thoughtfully installed Unity. :KS

   yeah .. :) .. um.. angels on the internet .. for sure ! :)

---

### Post by ratcheer on 2011-09-09
Unity (3D) is still working for me, but gnome-shell is not. I haven't tried Unity 2D yet.

Tim

---

### Post by ratcheer on 2011-09-09
> **ratcheer said:**
> Unity (3D) is still working for me, but gnome-shell is not. I haven't tried Unity 2D yet.

Tim

Suggestion by jbicha in another thread fixed gnome-shell, for me.

[http://ubuntuforums.org/showthread.php?t=1841441](http://ubuntuforums.org/showthread.php?t=1841441)

Tim

---

### Post by Benjamin_Lebsanft on 2011-09-09
> **ratcheer said:**
> Suggestion by jbicha in another thread fixed gnome-shell, for me.

[http://ubuntuforums.org/showthread.php?t=1841441](http://ubuntuforums.org/showthread.php?t=1841441)

Tim
Not for me sadly

---

### Post by VinDSL on 2011-09-09
> **castrojo said:**
> The new Unity from this week (and a bunch of stuff it uses) is being uploaded, give it a few hours and it should resolve itself.
In the meantime, I'm taking the opportunity to test the E17 DE in Oneiric.  It's quite nice, actually!

Every cloud has a silver lining, yes?

---

### Post by VinDSL on 2011-09-09
> **sgage said:**
> I still **maintain frequent backups** :lolflag:
Words of wisdom!

And, this is the reason I run a separate /home partition.

If worse comes to worst, I can do a fresh install, and be back on speed in 30 minutes.  ;)

---

### Post by ratcheer on 2011-09-09
> **VinDSL said:**
> In the meantime, I'm taking the opportunity to test the E17 DE in Oneiric.  It's quite nice, actually!

Every cloud has a silver lining, yes?

Is that Enlightenment?

Tim

---

### Post by Quackers on 2011-09-09
> **ratcheer said:**
> Is that Enlightenment?

Tim

Yes. I use E17 on BodhiLinux - it's quite nice and it's light on resources.

---

### Post by ventrical on 2011-09-09
> **VinDSL said:**
> In the meantime, I'm taking the opportunity to test the E17 DE in Oneiric.  It's quite nice, actually!

Every cloud has a silver lining, yes?

Vin,

Where to we get E17? Is it in the software center ?

Will check :)

---

### Post by ventrical on 2011-09-09
Ok.. gave it a whirl!

WOW MAN !!!

:)

Lots of potential there .. but my eyesight  is not what it used to be ... besides .. i am just begining to warm up to Unity.

---

