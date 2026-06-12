---
title: "[SOLVED] Update manager not playing nice!"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by ocean223 on 2008-05-31
When I run update manager it says it can only do a partial update. 

/home/ocean223/Desktop/Screenshot.png


I've seen this before and it was never a problem. When I click on partial upgrade, I get this:
/home/ocean223/Desktop/Screenshot-1.png

This is a problem I think.

What gives?:(

**Uh OH!!!!!  I screwed up the screen shot How do I start over???**

---

### Post by Hospadar on 2008-05-31
You should attatch your screenshots, cause I don't actually have access to your machine =P

Sounds like you might have a broken package, we, shall see.

Also it might be helpful if you went into a terminal, and typed "sudo apt-get upgrade" (this attempts to upgrade all your packages to the latest version, which is the same as when synaptic does an update) and post the output here.

---

### Post by fickenbaisage on 2008-05-31
> **ocean223 said:**
> When I run update manager it says it can only do a partial update. 

/home/ocean223/Desktop/Screenshot.png


I've seen this before and it was never a problem. When I click on partial upgrade, I get this:
/home/ocean223/Desktop/Screenshot-1.png

This is a problem I think.

What gives?:(

**Uh OH!!!!!  I screwed up the screen shot How do I start over???**

By updating and taking a screenshot again?

---

### Post by sayakb on 2008-05-31
Close the update manager window.
Goto System->Administration->Software sources.
Click on Updates Tab, and **uncheck** the last two update sources (ie. **uncheck** the Proposed and unsupported updates). Close the Window and Reload the package list when it asks to. Then try again with the update manager.

---

### Post by ayenack on 2008-05-31
EDIT: To late.

Before doing sudo apt-get upgrade it's might be an idea to update first. Like this.

**sudo apt-get update**

Then the upgrade as Hospadar said.

Also might be worth doing it in this order and with the additional line. Pressing return after each line.

[B]sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade[/B]

---

### Post by ocean223 on 2008-05-31
Thanks, here are the screen shots. I think.

---

### Post by sayakb on 2008-05-31
Uncheck the two update sources as indicated above. This should fix your problem.

---

### Post by ocean223 on 2008-05-31
> Close the update manager window.
Goto System->Administration->Software sources.
Click on Updates Tab, and uncheck the last two update sources (ie. uncheck the Proposed and unsupported updates). Close the Window and Reload the package list when it asks to. Then try again with the update manager.

That did it! And the terminal stuff did'nt hurt either.


Thanks to all!:guitar:

---

### Post by ayenack on 2008-05-31
Glad you got it fixed.

To be honest I didn't read your first post correctly and my suggestion was not appropriate to the problem.

But you got it fixed with the help of LinuxIsInnovation suggestion so that's cool.

ayenack.

---

