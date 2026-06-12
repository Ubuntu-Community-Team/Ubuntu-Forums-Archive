---
title: "Packages"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by ALPER on 2008-05-09
Dear my friends,
I didn't install any packages(deb). When i clicked the deb file, my computer made some processes but there isn't install any file.

---

### Post by kellemes on 2008-05-09
> **ALPER said:**
> Dear my friends,
I didn't install any packages(deb). When i clicked the deb file, my computer made some processes but there isn't install any file.

What package are you trying to install?

---

### Post by ALPER on 2008-05-14
I want to install deb files. When i click .deb files,it ask the root password.but now, it dosen't.

---

### Post by MaindotC on 2008-05-14
When is the last time you were prompted for a root password?  If you did something earlier that required the root password, like accessing an item from the Administration menu, it will not prompt you for the root password again until you've met the timeout period.  Do you see the program installed?  Does the dpkg program say that the program was installed?

---

### Post by ALPER on 2008-05-14
When i clicked again, &#305; understand that the deb file doesn't install. So &#305; couldn't install any packages. Also program doesn't ask me root password. i think there is a problem.

---

### Post by SunnyRabbiera on 2008-05-14
what were you trying to install?

---

### Post by ALPER on 2008-05-14
i want &#305;nstall the "mplayer"

---

### Post by SunnyRabbiera on 2008-05-14
alright, did you try synaptic package manager or add/remove
did you make sure they worked?

---

### Post by ALPER on 2008-05-14
i can't run the synapsis.

---

### Post by SunnyRabbiera on 2008-05-14
are you getting errors?
try running sudo apt-get in a terminal and see if it has any errors.

---

### Post by dorkdork777 on 2008-05-14
To clarify the above post, don't type "sudo apt-get" into the terminal; it won't do anything. Type this instead:```
sudo apt-get install mplayer
```That is what the above poster meant.

---

### Post by SunnyRabbiera on 2008-05-14
> **dorkdork777 said:**
> To clarify the above post, don't type "sudo apt-get" into the terminal; it won't do anything. Type this instead:```
sudo apt-get install mplayer
```That is what the above poster meant.

actually I was trying to see if apt itself was having errors, certainly the install function wont work if apt is having issues.

---

### Post by Paqman on 2008-05-14
Have you got Synaptic, Add/Remove or Update Manager open? If so, close them and try again.

---

### Post by alexandremrj on 2008-05-14
If you think you don't have anything open you can install the program mplayer in two ways:

- Open synaptic (System - Administration - Synaptic) and search for mplayer, press the square next to it and select install.

or

- place the command: sudo apt-get install mplayer

If there is an error, synaptic won't open because it will say that there is another process opened and apt-get will give an error in the command line.

If you are running hardy there is a new button, a grey arrow that appears in the notification area when a package manager is running.

---

### Post by ALPER on 2008-05-16
Thank you for your all helps. I enjoy with time ubuntu.

---

