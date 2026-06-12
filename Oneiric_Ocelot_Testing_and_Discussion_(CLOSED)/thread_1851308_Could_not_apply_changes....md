---
title: "Could not apply changes...?"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by soylentcola on 2011-09-28
So I upgraded to Oneric a few days ago and am now trying to update my software and all that jazz through Ubuntu Tweak...I've got about 292 updates sitting here to be installed but once I hit Install Updates, it processes and then tells me: "Could not apply changes! Fix broken packages first!" But I don't know what packages it wants me to fix...or really how to fix them.

Anyone wanna give a guy a hand?

---

### Post by soylentcola on 2011-09-28
Looks like I may have solved this myself...checking to see if I forgot a step in updating...

---

### Post by RomeReactor on 2011-09-28
Hi. Just as a comment on this, if you have Synaptic installed there's a filter (either in **Status** or **Custom Filters**, lower left) to select the broken packages. Otherwise, from the terminal:
```
sudo apt-get install -f
```

---

### Post by soylentcola on 2011-09-28
Will try that after this step finishes...I think I forgot to ran apt-get upgrade in my half-sleep blunder so I'm running through that to see if it'll help with the problem.

---

