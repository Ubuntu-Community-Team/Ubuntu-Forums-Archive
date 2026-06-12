---
title: "Fresh 13.04 install alongside windows 7 graphics issues"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by edwardmlyte on 2013-07-04
I tried xubuntu via wubi on my entirely win7 machine (and upgraded via 12.10 to 13.04) and liked what I saw. So I uninstalled the wubi version, and then proceeded to install xubuntu via live usb. It did all the partitioning fine. I selected "Download updates" and "install 3rd party software" as both my wifi and gfx need those proprietry drivers. After finishing installation successfully it restarted and showed the spinning circle logo. Then I get a full screen flash of green and then crazy coloured pixels, as shown in [http://i.imgur.com/7UKU5XL.jpg](http://i.imgur.com/7UKU5XL.jpg)

How can I remedy this? I've tried booting in xubuntu recovery mode. And then went to fix broken packages and pressed enter and nothing seemed to happen.

My laptop is an old dell studio 1555, and judging from the website it's got a ATI Mobility Radeon HD 4570 in it.

Thanks very much in advance.

---

### Post by Mark Phelps on 2013-07-04
You need to try a couple of different boot parms to see if either of them work to get you a display: nomodeset and xcforcevesa.

Because of that model card, you are stuck using the default Radeon drivers.  Do not download or attempt to install drivers from AMD -- that will only trash your display and make the situation worse.

When you're booting, keep pressing a Shift key until you get a GRUB menu.  Then press "e" to get into edit mode.  In the line beginning with "linux", you will see boot parms like "nosplash" and "quiet".  Replace "quiet" with "nomodeset" and press Enter to continue to boot.  IF that doesn't fix it, repeat the process but replace "quiet" with "xforcevesa".

You may have to use both parms to get a working desktop.

When you have the combination that works, you will need to edit the "grub" file under /etc/default/ to make the same boot parm changes.

---

### Post by edwardmlyte on 2013-07-05
Hey thanks for the reply. I didn't find it until just now. This morning I read how easy it is to reinstall the latest ubuntu releases, so I gave that a whirl. This time without auto-updating and auto-installation of third party software. All booting normally now.

However should I ever run into that issue again I'll definitely try your recommendation.

---

