---
title: "Installen RTL8188CUS Network adapter"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by jeffrey123 on 2012-09-16
Aloha!

I want to install the RTL8188 CUS network adapter in Xubuntu 12.04 LTS.
Spend hours google-ing to find a simple solution for it, but nada:(

So here's what happend...

-Freshly installed Xubuntu.
-Plugged in my network adapter.
-Connects to the internet for 5 seconds and disconnects.

I found out that Xubuntu is using a different driver, 8192su? or cu....
So i want to delete the not-working driver and install the correct one. (already found the drivers from realtek)

Can anyone guide me step-by-step how to do this?


(apology's for my horrible english)

---

### Post by jeffrey123 on 2012-09-16
Solved!

For people with the same problem, i will explain what i did:)

-First i plugged out my usb network stick.

-Open the windows where de driver was. (in my case in a 2gig usb stick).
Note: not opening in terminal, but the normal way..doubleclick the folder.

-rightclick anywhere in the window and click "open terminal here".

- In the terminal type :  sudo bash install.sh
(and press enter..duhh)

Now the driver should be installing, may take about 30 seconds.

Removing the old driver->

- open terminal (new terminal or old, dousnt matter)

-type  :    sudo leafpad /etc/modprobe.d/blacklist.conf

- now a new window will open. Here you will see blacklisted drivers.

-scroll all the way down, type :  blacklist rtl8192cu

- Click the cross in the upper-right to close the text-editing windows.
Press YES to save.

- Reboot your pc, plug your network usb stick in...and done!



The whole problem was, Xubuntu is not using Getid, but Leafpad.
Hope someone can type this story in a normal easy way.

And no need for comment, i already feel stupid:(

---

