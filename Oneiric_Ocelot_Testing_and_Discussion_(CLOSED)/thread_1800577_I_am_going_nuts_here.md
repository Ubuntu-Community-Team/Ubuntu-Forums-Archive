---
title: "I am going nuts here:"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2011-07-09
This is a clean installation on Ubuntu-Oneiric Alpha 2
there are no extra packages or applications installed and every time I tried to upgrade it fails.
no,not even sudo aptitude safe upgrades works and it's got me nuts.
love to test upcoming releases to help in finding problems but this one's got me.
Here are some screen shots:HELP!

---

### Post by Harry33 on 2011-07-09
Do not use Update Manager. It is not a good media at all for development phase.

Use Synaptic and you will also have a clue what is the problem in your setup.

---

### Post by VinDSL on 2011-07-09
> **Harry33 said:**
> Do not use Update Manager.
aka Update Mangler (my all-time favorite *ranch hand* saying)  :D

I don't use it, even on stable releases...

---

### Post by kuvanito on 2011-07-09
yeap,i tried again through terminal and got most of the updates,some were ignored but eventually they will all come down,thanks guys!!!!
I also had a crash on the update manager so now all my updates will go via terminal,i reported that bug to the team and some others.HAPPY TESTING!
so far so good.I LOVE UBUNTU! even steve jobs loves it,hehehehe iCloud what a joke! Ubuntu One has been here for 2 years now.

---

### Post by seeker5528 on 2011-07-09
> **kuvanito said:**
> This is a clean installation on Ubuntu-Oneiric Alpha 2
there are no extra packages or applications installed and every time I tried to upgrade it fails.

There seems to be a transition to a newer indicator library, which requires everything that uses it to be updated, until that gets sorted there will be complaints about conflicts and or removals of things you should keep, this morning it looked like there was progress on this, not sure if it was forward or backward. :P

I'm guessing if these things don't get sorted today, they probably will be in the next day or two.

Later, Seeker

---

