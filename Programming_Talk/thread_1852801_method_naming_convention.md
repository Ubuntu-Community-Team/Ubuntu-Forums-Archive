---
title: "method naming convention"
date: 2011-09-30
forum: Programming Talk
---

### Post by jmartrican on 2011-09-30
hello,

Background:
I'm working on a turret based video game.  A turret can have different types of projectiles but only one can be armed/selected at a time

Question:
Lets say the turret is selecting a projectile (e.g. changing from Fire to Laser).  In this scenario it has to deselect Fire and select Laser.  There are two projectile functions that the turret needs to call for this (one for deselecting and the other for selecting).  My question is should the functions be called projectileSelected (and projectileDeselected) or selectProjectile (and deselectProjectile).  Basically is the function named for the object calling it (e.g. select this) or for the implementation (e.g. this has been selected)?

Does the keyword "handler" in the method name help out in this situation?  I imagine there are some standards for this.

This has ramifications throughout my project as this type of scenario keeps popping up so its a pretty big deal in making the code readable and editable in the future.

thanks
jose

---

### Post by karlson on 2011-10-01
> **jmartrican said:**
> 
Question:
Lets say the turret is selecting a projectile (e.g. changing from Fire to Laser).  In this scenario it has to deselect Fire and select Laser.  There are two projectile functions that the turret needs to call for this (one for deselecting and the other for selecting).  My question is should the functions be called projectileSelected (and projectileDeselected) or selectProjectile (and deselectProjectile).  Basically is the function named for the object calling it (e.g. select this) or for the implementation (e.g. this has been selected)?

I would call the public version switchWeapon(weapon).  Which removes the Fire weapon from the slot and adds weapon.

> 
Does the keyword "handler" in the method name help out in this situation?  I imagine there are some standards for this.

Not sure it makes a difference as long as the method name describes what it does.

---

### Post by jmartrican on 2011-10-01
thanks karlson,

On the turret I actually have that.  So the turret is told switchProjectile(projectile), just like you mentioned.  In that method I have to tell the old weapon that it is no longer selected, and need to tell the new weapon that it is selected.

I could extend that switchProjectile terminology over to the projectiles, but how would I then convey deselect and select?

---

### Post by Tony Flury on 2011-10-01
> **jmartrican said:**
> thanks karlson,

On the turret I actually have that.  So the turret is told switchProjectile(projectile), just like you mentioned.  In that method I have to tell the old weapon that it is no longer selected, and need to tell the new weapon that it is selected.

I could extend that switchProjectile terminology over to the projectiles, but how would I then convey deselect and select?

You don't need to, do you ? Is there ever a case where the turret can have no weapon ? If a turret always has one type of projectile, then a deselect will ALWAYS have a select, so it makes no sense to separate the two.

Don't make the code more complicated than you need to.

---

### Post by ofnuts on 2011-10-01
> **jmartrican said:**
> thanks karlson,

On the turret I actually have that.  So the turret is told switchProjectile(projectile), just like you mentioned.  In that method I have to tell the old weapon that it is no longer selected, and need to tell the new weapon that it is selected.Not sure this is usueful, unless you are telling "Fire" to all your weapons, and expect only  the select one to fire. IMHO a weapon should only be able to do one thing: fire when it's told (and maybe reload...). Weapon selection is the turret's business, unless the weapon is shared between turrets.

---

### Post by nvteighen on 2011-10-01
I don't get this... is this about design or is this about naming? If it's about naming, any name that's decently informative and unambiguous about what the method does is good.

If it's about design, I'd go for this approach:

0. Strip the turret class to be just a container for weapons.
1. Have a switch method.
2. Have a fire method.
3. Optionally have a switch+fire method, which would call switch and then fire...

A good advice is always try to do small steps when abstracting, so you avoid having "premature optimization/abstraction" issues. If executable size is critical, you can then remove methods that have been proven to not be ever used.

I know, this is a very Lispish development approach :P

---

### Post by karlson on 2011-10-01
> **nvteighen said:**
> I don't get this... is this about design or is this about naming? If it's about naming, any name that's decently informative and unambiguous about what the method does is good.

If it's about design, I'd go for this approach:

0. Strip the turret class to be just a container for weapons.
1. Have a switch method.
2. Have a fire method.
3. Optionally have a switch+fire method, which would call switch and then fire...

A good advice is always try to do small steps when abstracting, so you avoid having "premature optimization/abstraction" issues. If executable size is critical, you can then remove methods that have been proven to not be ever used.

I know, this is a very Lispish development approach :P

I personally think that there is no way to separate one from the other.  If you have bad design you can't follow what is going on even if the names are descriptive.

---

### Post by snip3r8 on 2011-10-01
Method names usually start with a verb

---

### Post by jmartrican on 2011-10-01
Thanks for the feedback.  The original question was about naming but I am enjoying the design feedback.  I will address design here.

The Turret is a container of Weapons (which i call Projectiles).  Originally it just told the selected projectile to Shoot (Fire is one of the Projectiles).

I eventually had to implement the concepts of fuel-up and charge-up on some of the Projectiles, this was part of the game requirements.  The way these concepts work is that the Projectile must first charge-up completely before it can shoot its special-ability.  Fuel-up is similar, you need fuel to use the Fire Projectile (its a flame thrower).  Fuel and charge accrue by not using the Projectile but having it selected.  Charge and fuel must not accrue if its Projectile was not selected.  Only one Projectile can be selected at a time.  When the player hits the right or left mouse button the selected Projectile will shoot.  They can then switch Projectiles via hot-keys or scroll button.

So to not have a Projectile accrue charge or fuel if it is not selected, I had to implement this "select or not-selected" concept into the Projectiles.  Laser will start charging up if it is selected and will stop charging if it is not selected.  Fire will fuel up if is selected and will stop when it is no longer selected.

---

### Post by jmartrican on 2011-10-01
nvteighen,

So in this scenario last night i named the two methods being discussed selectProjectileHandler and deselectProjectileHandler.  So what I am leaning towards is using the word "handler" in methods where I am telling the object "hey this is what is happening, do whatever you have to do to prepare or handle it".  I am then forcing forcing objects to implement these handler methods even if they do not have to do anything.  For example some Projectiles do not care if they are selected or not, as they do not have any charge or fuel.  But at least the implementer would have paid thought to it and made the conscious choice to not do anything, which is better than making said method optional and having the developer forget to handle said situation.

One problem I am having also, and this affects both naming and design, is that when a shot is finished there are various objects that may need to know about this event.  A shot could be finished by the projectile finishing on its own (aka the shot goes off the screen), a shot could finish by having the projectile hit an enemy, it could also end by the player letting go of the mouse button (this only affects Projectiles with continuous shooting capabilities, like the Fire's flamethrower), it could also end by the player quitting the round, and finally the Board the player is on could end the shot if the player lost all its lives or the enemies died.  Depending on who ends the shot different objects need to be notified.  Things were not that complicated at first but as the implementation of the game has moved further along this is where we find ourselves.  

Naming in this situation matters because you have some objects that are in the middle and are being told to end a shot or are deciding to end a shot and the naming convention of these methods all look the same (e.g. endShotHandler).  When I look at the code it is not obvious if said method is being told to end the shot or is the own object itself ending the shot.  

So I want to do two things here: 
1) come up with a naming convention for the scenario where I am being told to deal with a shot ending versus the method where I decide to end a shot.

2) Look into using an EndShotObserver, where the objects that need to know that a shot ended subscribe to it, and an object that desiced to end a shot will communicate out to it.

I imagine that regardless of what I do for item 2 (aka refactoring the design) I still need a tight naming schema here.

Any advice?

thanks
jose

---

### Post by nvteighen on 2011-10-02
> **jmartrican said:**
> nvteighen,

So in this scenario last night i named the two methods being discussed selectProjectileHandler and deselectProjectileHandler.  So what I am leaning towards is using the word "handler" in methods where I am telling the object "hey this is what is happening, do whatever you have to do to prepare or handle it".  I am then forcing forcing objects to implement these handler methods even if they do not have to do anything.  For example some Projectiles do not care if they are selected or not, as they do not have any charge or fuel.  But at least the implementer would have paid thought to it and made the conscious choice to not do anything, which is better than making said method optional and having the developer forget to handle said situation.

One problem I am having also, and this affects both naming and design, is that when a shot is finished there are various objects that may need to know about this event.  A shot could be finished by the projectile finishing on its own (aka the shot goes off the screen), a shot could finish by having the projectile hit an enemy, it could also end by the player letting go of the mouse button (this only affects Projectiles with continuous shooting capabilities, like the Fire's flamethrower), it could also end by the player quitting the round, and finally the Board the player is on could end the shot if the player lost all its lives or the enemies died.  Depending on who ends the shot different objects need to be notified.  Things were not that complicated at first but as the implementation of the game has moved further along this is where we find ourselves.  

Naming in this situation matters because you have some objects that are in the middle and are being told to end a shot or are deciding to end a shot and the naming convention of these methods all look the same (e.g. endShotHandler).  When I look at the code it is not obvious if said method is being told to end the shot or is the own object itself ending the shot.  

So I want to do two things here: 
1) come up with a naming convention for the scenario where I am being told to deal with a shot ending versus the method where I decide to end a shot.

2) Look into using an EndShotObserver, where the objects that need to know that a shot ended subscribe to it, and an object that desiced to end a shot will communicate out to it.

I imagine that regardless of what I do for item 2 (aka refactoring the design) I still need a tight naming schema here.

Any advice?

thanks
jose

Ok...

Without further details and not having read the source code, I can't really judge the design. It sounds a bit overcomplicated, but I'm not able to tell you why, because you seem to be using a "general sentinel" that watches over conditions that might interrupt a shot and interrupts them when needed.

If I had to do this, I'd have done something like this: have shots derived from a single class Shot (I'm sure you've done this), have something contain all shots on screen, have the main loop check conditions that might require destroying Shot objects and destroy them, using the objects' destructors for that, I guess.

Now, I don't fully get the naming issue you have. For me, method called endShotHandler would imply something that ends a Shot... even if it just calls the Shot destructor.

---

