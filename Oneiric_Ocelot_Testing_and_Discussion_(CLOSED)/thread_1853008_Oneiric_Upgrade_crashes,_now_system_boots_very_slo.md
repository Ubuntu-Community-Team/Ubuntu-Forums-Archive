---
title: "Oneiric Upgrade crashes, now system boots very slowly"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nishant.singh28 on 2011-10-01
I had upgraded to Oneiric from Natty 64 bit by running update-manager -d. The upgrade worked fine till it threw up an error related to initramfs-tools. I realized my /boot partition had run out of space, but I rebooted nevertheless. To my surprise, the update had been almost successful. So I uninstalled old kernels to clear up some space in the boot drive. I then fixed everything up and the system is working now.
The only issue that remains is the boot time. The boot is very slow. I booted without the "quiet splash" option in the kernel parameters, and the system waited a long time at "Running init-scripts bottom" before proceeding. I am not sure that is the only issue, but it seems to be the main issue. The login is also a bit on the slower side, but not much, so I'm not really bothered about that right now.
I don't know what else needs attaching here. I will be very happy to provide the requisite info.

Update: I installed bootchart and generated logs for both the installed kernels. I can't make much out of it, but here are the links:
[2.6.38-11]("http://i.imgur.com/81sHF.png")
[3.0.0-12]("http://i.imgur.com/LvaMj.png")

---

### Post by sonnet on 2011-10-04
I have the same problem

---

### Post by nishant.singh28 on 2011-10-05
Well after a long and painful illness, my Ubuntu install committed suicide today morning. Update manager uninstalled unity and with my not so extensive knowledge of recovering systems, couldn't rescue it. So I did a clean install. So now the issue of slow boot is solved, but the Shutdowns remain excruciatingly slow. Also, the system often fails to log out of the session. Suspend works perfectly, but that's no consolation. I know it's a beta, but I've not seen such issues in Karmic, Lucid, Maverick or Natty betas. Anyone out there with some solution?

---

### Post by philinux on 2011-10-05
Moved to ubuntu +1

---

