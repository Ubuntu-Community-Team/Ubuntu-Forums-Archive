---
title: "Confused"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by blakebb on 2008-10-31
I'm a newbie, but I got a little excited and downloaded the beta release..stupid I know now.  

Now that 8.10 has been release I want to update it, but I can't get software sources under applications to work.  I click but it doesn't do anything. 

I've tried to upgrade in the terminal, but to no avail. 

Can somebody help?!?

Lonely and Confused....

---

### Post by oldos2er on 2008-10-31
Can you show the terminal output?

---

### Post by OrangeCrate on 2008-10-31
This should help...

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Gamma746 on 2008-10-31
Go to Software Sources, open the Updates tab, and make sure that you're set to show all distribution upgrades, not just LTS releases.

---

### Post by cariboo on 2008-11-01
The repositories still seem to be suffering from all the updates being done. Try another server. I had to change servers just to install my graphics adapter drivers, From the Canadian server it was stuck at 1.5Mb download for about an hour, so I changed to the fastest server and it still took ten minutes to download the driver and dependencies.

Jim

---

### Post by kostkon on 2008-11-01
what output do you get if you do
```
sudo apt-get update && sudo apt-get upgrade
```
as fas as the *Software Sources* not working, try running it from the terminal and see what error message(s) you get
```
gksudo software-properties-gtk
```

---

### Post by blakebb on 2008-11-01
Yeah..that's the problem ...software sources just doesn't open.

---

