---
title: "Hardy locks up on shutdown"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Unstuck on 2008-05-31
Most of the time when I try to shutdown using the quit icons, the system locks up--I can still move mouse, but can't select windows or highlight anything on the menu bar--and I have to complete the shutdown by hitting Ctrl+Alt+Backspace and choosing to shutdown from the login screen.

I searched the forums and none of the other problems people have posted seem quite like mine...please forgive me if I'm wrong and point me to the correct thread.

---

### Post by dracayr on 2008-05-31
what about 
```
sudo init 0
```
or
```
sudo shutdown now
```

dracayr

---

### Post by Unstuck on 2008-05-31
```
sudo init 0
```...fastest shutdown i've ever been witness to.

---

### Post by Daveth on 2008-06-01
I'm occassionally getting the same problem, though if you wait it does resolve. It is almost like there is a memory block somewhere which it has to work through to take the command. 

The terminal shutdown code is useful, but does not address the base problem.

---

### Post by Unstuck on 2008-06-01
I agree, I would like to resolve the issue permanently rather than work around it.

---

### Post by dracayr on 2008-06-09
If sudo init 0 works, you can set that to the shutdown command in System>Administration>login screen>change commands... I have a similar problem, but it never occurs with sudo init 0, only with shutdown. I think on a System where only one user is logged on simultanously (no network System), there should be no problems with init 0

---

### Post by Unstuck on 2008-07-31
Has anyone figured out a solution to this?

---

### Post by chrone on 2009-02-11
i'm having the same problem here in my office, most intel desktop board paired with ati radeon onboard could not shutdown after pressing the shutdown button in power menu. it's just wait there to be manually shut off through the power button in chassis.

shame on ubuntu who still having problems with this minor job. :confused:

---

