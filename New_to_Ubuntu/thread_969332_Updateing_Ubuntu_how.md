---
title: "Updateing Ubuntu how?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-11-03
I would like to update to see if it will fix a problem i'm having with ubuntu the problem is that the problem make me unable to start-up ubuntu. So is there some way to update ubuntu without doing it inside ubuntu, I have read that it's possible with alternative cd but how?

---

### Post by superprash2003 on 2008-11-03
why not just do a fresh install, it doesnt seem to work anyways..

---

### Post by bwhite82 on 2008-11-03
If you have an alternative CD, add it to your repos from the command line - No desktop needed:

> sudo apt-cd add (make sure CD is in drive)

then

> sudo apt-get update

If you have network connectivity, then you can update via network:

> sudo apt-get dist-upgrade

---

### Post by Paqman on 2008-11-03
> **SpinningAround said:**
> So is there some way to update ubuntu without doing it inside ubuntu, I have read that it's possible with alternative cd but how?

You can use the CD as a repo, which would allow you to upgrade to the package versions on that CD, but you need to be running to do so.

When you say you are unable to start up, what do you mean precisely? Do you get any error messages? Can you boot into recovery mode?

---

### Post by SpinningAround on 2008-11-03
> **Paqman said:**
> 
When you say you are unable to start up, what do you mean precisely? Do you get any error messages? Can you boot into recovery mode?It freezes during boot I'm simply to able to get a terminal with normal boot or recovery mode

---

