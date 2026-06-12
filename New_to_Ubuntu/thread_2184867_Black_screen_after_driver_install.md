---
title: "Black screen after driver install"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by davesr300 on 2013-10-30
Installed ATI driver 13.1 on a Linux Mint 14 OS and since Mint is based on Ubuntu I was hoping someone here could help. After finishing the install the screen said to reboot to finish install. After reboot I have no video, only a black screen. After a while I get a message on the screen the says "*Failed to start X-server. It is likely that it is not set up correctly*." Then it asks a question* "Would you like to view the X-server to diagnose the problem."*
I have no idea how to proceed. Do you need the X-server view to help me? Thanks

---

### Post by Mark Phelps on 2013-10-31
The more important question is whether or not your AMD video hardware is compatible with the X-server in Mint 14.

If you have one of the newer Radeons (5x-series or newer) then it should be compatible.

If you have one of the older Radeons (HD 2x/3x/4x-series or xnnnn series), the AMD driver is NOT compatible with the X-server in Mint 14 and won't work. In that case, you would need to remove the AMD drivers and replace them with the default Radeon drivers.

---

### Post by davesr300 on 2013-10-31
Card is HD 7970

---

