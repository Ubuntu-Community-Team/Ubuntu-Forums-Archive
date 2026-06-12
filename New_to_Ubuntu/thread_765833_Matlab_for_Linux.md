---
title: "Matlab for Linux"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by runnerdi7 on 2008-04-24
I know mathworks makes a matlab for linux, but are there any linux programs that do roughly the same thing for free?

---

### Post by runnerdi7 on 2008-04-24
bump,

anyone? please, i have a midterm tomorrow, and project due in a week, this is my only complaint with ubuntu so far.

---

### Post by SOULRiDER on 2008-04-24
Im not sure about this, but have you tried Scilab? I think its rather similar to Matlab, at least with what it can do.

---

### Post by wt8008 on 2008-04-24
I have seen Scilab which does something similar to MATLAB, but the code isn't compatible with it.

There is also GNU Octave which is mostly compataibe with MATLAB [http://en.wikipedia.org/wiki/GNU_Octave](http://en.wikipedia.org/wiki/GNU_Octave)

I don't use MATLAB enough to give you tell you which one to use, but if you need to turn in code that runs in MATLAB, use GNU Octave, but watch out some modifications maybe needed before it can be ran.

---

### Post by runnerdi7 on 2008-04-24
thanks wt8008, the ubuntu forums are the best. thats exactly what i was looking for.

---

### Post by ad_267 on 2008-04-24
Yeah octave is what you want. I'm currently working on an assignment that has to work in Matlab using Octave. One problem I had is that I installed the octave2.9-forge package to get additional functions I needed but these were not automatically recognised by Octave. I had to insert this to get the dmlread function to work for example:

```
addpath('/usr/share/octave/site/api-v22/m/octave2.9-forge/io/');
pkg load all;
```

I'll be upgrading to hardy soon and using octave 3.0 so hopefully this will be fixed in that.

---

### Post by tyblu on 2008-04-24
Octave is fantastic. I've used Matlab in several courses now (Elec. Engin.), and have found Octave compatible with almost all computational commands. Aside from some minor differences in plotting commands, Octave has actually proven to be more stable than Matlab in 'puter-unfriendly calculations (ie: 10min+ calcs) and it has less memory overhead. I haven't tried the GUI's for Octave yet, but there are a few.

---

