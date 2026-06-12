---
title: "Cannot connect to wifi"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by tlplw717 on 2011-12-21
All,
I know there are a lot of threads about this and I already went through the search function. I just installed Ubuntu on my dell with the Windows Installer (have Windows 7).

At first my internet was fine. Now however, it does not connect. I can see the networks and can select mine, however, it doesn't tell me it is connected and doesn't work. It continues to pop up a window telling me to type in my password which I have done (both internet pw and account pw)

Any suggestions? I'll post any command lines

---

### Post by anewguy on 2011-12-21
First, left-click on the network manager icon on the top bar and select "Edit Connections".  Click on the wireless tab, select your network and delete the connection definition.  Sometimes if the password has been attempted more than once it seems to remember the bad attempt in the connection definition.  Deleting it solves that.

Second, try connecting to your network again.  Remember this is the network (router) password and be sure the type matches as well.  Sometimes it is best to click the box so the password shows as you type it - then you can see if you've made an error.

Now, if that doesn't work, and you are sure you have the correct password, then I would have to ask if you are trying to connect to a router you have or to someone elses.

Dave ;)

---

### Post by TBABill on 2011-12-21
You could also have a driver issue with the machine. If you change network settings to make it an "open" network (no encryption) will it connect? If not, you likely have a hardware/driver issue. Could you post the output of two commands if you're still having trouble? They are: ```
lspci
``` and ```
lsmod
``` That'll show us the devices in the machine and the active drivers.

---

### Post by tlplw717 on 2011-12-21
Thanks a lot you guys. I turned my computer on today and Linux connects to Wifi...if it fails again, I will try to implement these suggestions.

---

