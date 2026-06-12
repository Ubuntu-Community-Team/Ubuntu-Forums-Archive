---
title: "Display Blackouts"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Lupicek on 2013-04-16
Hello all,

I am a brand-new Ubuntu user: over the weekend I inherited a Toshiba Satellite from a family member, quickly grew tired of the installed Vista, and installed Ubuntu 12.10. I love using the OS, but there are a couple of issues with my display that have me scratching my head. The issues are described below; for technical issues, I am running a Toshiba Satellite A305-S6916, the specs for which can be found here ([http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=431542](http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=431542)). The graphics card is an ATI Mobility Radeon HD 3650.

Issue 1: Startup blackout
When starting the machine, the startup process initially works ok: I see the Toshiba logo, followed by the Ubuntu purple screen. Once the purple screen shows for a second or two, the screen goes black - not off, but it shows just black. I had to test this in a dark room to be sure. I cannot get the computer to function after this point, so I hard-reboot by holding the power button for 5 seconds. Upon the second startup, in place of the blank purple screen I receive a list of boot options, including regular Ubuntu, safe mode, etc, against a purple screen. After I press enter for the first option (Ubuntu 12.10), the startup proceeds normally and I can enter my passwords for decrypt, login, etc. This happens every time the computer is turned off, and it never requires more than one reboot.

Issue 2: Wakeup blackout
This issue occurs only after suspending the hard drive by closing the lid or otherwise; it does not occur when the display only goes to sleep. When waking the computer from suspension, the screen appears to try to turn on but fails. The screen displays black as before, but it flashes once per second - like a camera flash, bright white then immediately fading back to black. I have tried entering my password while the screen is flashing, but that does not stop the issue. The only solution I have seen is a hard reboot, which then leads back to Issue 1. 

I have no idea what could be causing these issues, but I would appreciate any help or suggestions!

---

### Post by gordintoronto on 2013-04-16
For issue one, you might try this: after pressing the power button, lean on the shift key. No guarantees.

---

### Post by Lupicek on 2013-04-17
> **gordintoronto said:**
> For issue one, you might try this: after pressing the power button, lean on the shift key. No guarantees.

Leaning on the shift key after pressing the power button brings me immediately to the GNU GRUB menu (the "boot options" menu described before), which initially got me very excited. After selecting Ubuntu, though, I get the same screen blackout. Hard rebooting is the only option from that point, and after the second boot the startup process continues as described previously.

---

### Post by schuks on 2013-04-17
I too am new to linux. I was having the same problem, I have an HP laptop, on the keyboard there is a brightness button located on F3 and F2 has a dimmer light, when I hit the F3 brightness button the screen then showed. Don't know why I had to do this, but that is what worked for me. Now as far as installing ubuntu that I still have not figured out.

---

### Post by Lupicek on 2013-04-19
Problems Solved!

For Issue 1, I had to use both solutions posed here. When I power up, I lean on the shift key until the GNU GRUB menu pops up. I then select the first choice, and press one of the brightness buttons (F6 and F7 in my case) for the next screen to pop up. Strange but true. Still takes less time than the old Vista startup.

For Issue 2, the problem seems to have resolved itself. I downloaded the Mediabuntu suite to watch DVDs, and the screen stopped its wakeup freakout. Perhaps a video driver needed to be updated, and it was covered when performing *sudo apt-get update*? I am not sure, but it seems to have worked. Sorry I can't offer a more concrete solution for people who are having the same problem, but this has worked for me.

Thanks all for your help!

---

