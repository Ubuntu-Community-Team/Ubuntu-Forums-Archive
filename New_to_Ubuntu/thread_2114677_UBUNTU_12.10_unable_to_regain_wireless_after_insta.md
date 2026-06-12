---
title: "UBUNTU 12.10 unable to regain wireless after installing updates."
date: 2013-02-10
forum: New to Ubuntu
---

### Post by fds57 on 2013-02-10
Hello,
      Yes I'm totally new.
I installed 12.10 64Bit on an DELL N5010 laptop and everything was working very nicely...untill I did a software update.
     And then rebooted But no longer could connect to wireless network.
    I deleted,and reinstalled twice more, Each time I could go on wireless
as often as I wished, reboot as often too, as long as I did not run the Updater. I have tried everything I could find on the Internet,nothing helps.
   
Sure hope someone has a solution.;)

---

### Post by HugoHughes on 2013-02-10
I've learned one thing today, when in doubt, just ask.

I fully installed Ubuntu 12.10 with Windows 7 (dual-boot) today and I too experienced this same problem. But it's an easy fix, at least it was for me.

Just follow this: [http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html]("http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html")

You can fix wifi problems using two methods:

- Either connect to the internet via wired connection and run this command:

sudo apt-get update && sudo apt-get upgrade

Then reboot your system.


- Or use the following commands:

sudo apt-get install linux linux-headers-generic kernel-package

sudo apt-get install --reinstall bcmwl* firmware-b43-lpphy-installer b43-fwcutter

Finally, reboot your system.


If that didn't help, try these commands:

sudo apt-get remove bcmwl-kernel-source

sudo apt-get install firmware-b43-installer b43-fwcutter

sudo reboot

---

### Post by fds57 on 2013-02-10
> **HugoHughes said:**
> I've learned one thing today, when in doubt, just ask.

I fully installed Ubuntu 12.10 with Windows 7 (dual-boot) today and I too experienced this same problem. But it's an easy fix, at least it was for me.

Just follow this: [http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html]("http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html")

You can fix wifi problems using two methods:

- Either connect to the internet via wired connection and run this command:

sudo apt-get update && sudo apt-get upgrade

Then reboot your system.


- Or use the following commands:

sudo apt-get install linux linux-headers-generic kernel-package

sudo apt-get install --reinstall bcmwl* firmware-b43-lpphy-installer b43-fwcutter

Finally, reboot your system.


If that didn't help, try these commands:

sudo apt-get remove bcmwl-kernel-source

sudo apt-get install firmware-b43-installer b43-fwcutter

sudo reboot




Sure was hopefull but none of the above worked for me. 
            thanks for trying ,still looking

---

### Post by Bryan55 on 2013-02-10
I once had the same problem after an update. It was solved by doing a cold reboot. That's totally removing all power for a minute or 2 before booting

---

### Post by fds57 on 2013-02-14
> **HugoHughes said:**
> I've learned one thing today, when in doubt, just ask.

I fully installed Ubuntu 12.10 with Windows 7 (dual-boot) today and I too experienced this same problem. But it's an easy fix, at least it was for me.

Just follow this: [http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html]("http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html")

You can fix wifi problems using two methods:

- Either connect to the internet via wired connection and run this command:

sudo apt-get update && sudo apt-get upgrade

Then reboot your system.


- Or use the following commands:

sudo apt-get install linux linux-headers-generic kernel-package

sudo apt-get install --reinstall bcmwl* firmware-b43-lpphy-installer b43-fwcutter

Finally, reboot your system.


If that didn't help, try these commands:

sudo apt-get remove bcmwl-kernel-source

sudo apt-get install firmware-b43-installer b43-fwcutter

sudo reboot

problem solved! thanks for the fromyou guys.
the first time I tried the commands one at a time and it failed.
the second time I tried them together separated by &&, and it worked.

---

