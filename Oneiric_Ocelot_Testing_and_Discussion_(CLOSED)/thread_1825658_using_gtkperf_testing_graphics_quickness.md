---
title: "using gtkperf testing graphics quickness"
date: 2011-08-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fjgaude on 2011-08-15
Testing overall time, 100 reps, in seconds, using gtkperf, the speed of oneiric on two different boxes and with three different shells and versions...

Main box, 4.0MZ, with Intel built-in grahics: Unity 3D: 9; Unity 2D: 5
Under natty, same main box: Unity 3D: 12; gnome: 7; gnome with effects: 11; under VMware Player 2D: 5

Now using Dell mini 10n, 1.33Mz, poulsbo; oneiric, Unity 2D: 314; lucid, gnome classic: 71
---

Interesting, eh? Unity has good speed against gnome w/effects.

---

### Post by tekstr1der on 2011-08-17
Since I've yet to run GS on native hardware, it's all about compiz performance for me.

On Lucid, with OR without compiz 8.4 effect enabled, I'd get between 7 and 8 seconds on gtkperf.

On Natty I see a massive performance hit running compiz 9.4. Under Unity 3d gktperf is taking 14-15s. Running a metacity fallback session (compiz disabled), I get around 8s again.

So for me,

no compiz:  8s
compiz 8.4: 8s
compiz 9.4: 15s

---

### Post by fjgaude on 2011-08-17
All this seems about right and good! When we are talking about Unity 3D we are not pushing the video machine like some heavy games do.

We can think that once compiz gets cut down to a custom version just for Unity we would have about the best of all worlds.

---

