---
title: "[SOLVED] getting nvidia drivers to work"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by garfunk3l on 2008-10-13
Hi,

I used to be quite good using WinXP but I am absolutely drowning in jargon trying to figure out the first thing about ubuntu hardy heron (apart from using open office and mozilla!!!!)
I am trying to get the system set up properly but for some reason I can't enable any desktop effects, use 3D in chess and goodness knows what else.
When I check hardware it says that nvidia_new is enabled but not in use.
In WinXP I would probably just download drivers and install them... what do I do in ubuntu? Every search I do refers me to something else that refers me to something else and I end up going in circles - people offer 'sure' fixes to the same problem for other people and it doesn't work for me, and I'm thinking I might just flag ubuntu and go back to WinXP. What's more is every time I 'try' something out I get the feeling I'm going to mess up the system because I don't know what I'm doing.

My computer is HP DV2111TX, Intel Core 2 Duo T550 1.66GHz, Nvidia GeForce Go 7200.
The install of Ubuntu should be completely clean - I have literally only opened 6 or so programs and I don't think any of my failed fixes have changed anything.
How might I be able to fix the 'not in use' problem just so I know everything is set up properly? - maybe one day I might want to play a game??
Any help will be very much appreciated because ubuntu looks like its awesome but not if all I can do is use the net.

---

### Post by Ryadt on 2008-10-13
Try to update your box first```
sudo apt-get update && sudo apt-get upgrade
```

Then retry to enable the driver.

---

### Post by garfunk3l on 2008-10-13
Hi, thanks. When I turned on my computer today it did a lot of updating and then the drivers worked. You were right, it just needed updating.

Cheers,

Dave

---

