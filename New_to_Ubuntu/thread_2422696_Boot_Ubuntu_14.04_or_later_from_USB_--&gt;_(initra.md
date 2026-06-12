---
title: "Boot Ubuntu 14.04 or later from USB --&gt; (initramfs)"
date: 2019-07-11
forum: New to Ubuntu
---

### Post by omodayo1523 on 2019-07-11
Hey Everyone,

This is my first post and my first time trying something like this so I apologize in advance for my clumsiness. I am trying to boot Ubuntu 14.04 or later from a USB to a Dell Edge 5000 that arrived preprogrammed with Ubuntu Core. The instructions I have been following here: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#1](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#1), are straightforward enough until I get to the point where I have to actually boot the Ubuntu_Desktop OS from the USB to the Server. 
Problem Points:


[LIST=1]
[*]The Server never boots automatically from the USB. I am prompted with a request for login credentials and then I am placed in a "snap" environment.
[*]The Commands I've found to manually boot ubuntu_desktop from the USB via GRUB run fine, but instead of being presented with the familiar Ubuntu GNOME GUI, once the boot process is finished, I find myself with a command prompt awaiting input named: (initramfs)
[/LIST]

Any advice on how to proceed would be much appreciated. Thank you for your time!

Best,
Dayo

PS. I am sure I've left out some important information. Let me know what is missing and I'll add it to the thread.

---

### Post by omodayo1523 on 2019-07-11
_**SOLUTION**_: I rebooted the Dell Edge 5000 to its '**Factory Settings*' and held down **ESC**, **F2**, **F8**, **F10** and the **Fn** button during the boot menu (*Dell Image display page*) and the option to boot directly from USB displayed for the first time. Setup from that point was almost completely automated and very easy. :)

---

