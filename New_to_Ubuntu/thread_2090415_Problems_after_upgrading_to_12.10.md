---
title: "Problems after upgrading to 12.10"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by HenrikMundt on 2012-12-02
I made an update from 12,04 to 12,10 the other day from the net.  But the result gave me a surpice!. After the end of updating I ended whith  "restart" and so I did.
After that i have no contact whit the program.
When i start I get so fare into the system that I can print in my securitycode and after a while i get a scren whit the curser and nothing else. I am even not able to end the program. The only way out is the mainswich.
What vent wrong - and how can I get back into the system??
Y s
Henrik Mundt/Sweden

---

### Post by 2F4U on 2012-12-02
Can you provide more information about your hardware? Did you have proprietary graphics card drivers enable before the upgrade? This is often a reason for a failed upgrade. Am I right in assuming that there were no errors during upgrade?

---

### Post by HenrikMundt on 2012-12-02
About hardw:
ASUS K8W-X-SE
2 G ram
AMD Semperon 2800
Harddisk 240 G
A stand DVD RW

Priory drivers - I am not shure: That matter is ½ a year old and i have forgotten most of what went on that day. If so it might be drivers for the soundkart wich is a part of the motherboard.

During the upgrade - I got no alarm. most of it happend while I was doing something else. It's so borring just sittig and waiting.
But what surprices me mostly is that there is no icons at all - even the clock is gone!

R//H

---

### Post by squakie on 2012-12-02
Try adding the following 1 at a time to the boot line and see if it/they help:

nomodeset

acpi=off

noapic

---

### Post by Mark Phelps on 2012-12-02
You sure about the model of your motherboard? Could only find info on a K8V motherboard, and that does not have onboard video.

---

### Post by HenrikMundt on 2012-12-02
I am very surden that I have a ASUS K8W-X-SE:).
[http://www.asus.com/Motherboards/AMD_Socket_754/K8VX_SE/](http://www.asus.com/Motherboards/AMD_Socket_754/K8VX_SE/)
is the link and it works here.

The other anserw to add. YES but how do I get in - I have no reaktionon  from the screen where I stand after the inlogg?

Sinc // Henrik

---

### Post by Wim Sturkenboom on 2012-12-02
> **HenrikMundt said:**
> I am very surden that I have a ASUS K8**[COLOR="Red"]W[/COLOR]**-X-SE:).
[noparse]http://www.asus.com/Motherboards/AMD_Socket_754/K8[/noparse]**[COLOR="Red"]V[/COLOR]**[noparse]X_SE/[/noparse]
is the link and it works here.

That's what Mark is referring to (W vs V) ;)

To prevent you from forcing power down, you can press <ctrl><alt><F1>. You will end up with a console where you can login; note that you will not see anything happening while typing your password, just type it and press <enter>). Next type _sudo shutdown -h now_ to shutdown.

Any feedback on squakie's suggestions (post #4)?

---

### Post by HenrikMundt on 2012-12-02
NO -just because that I did not now how to find the konsol - I will try it to morrow.
R//H

---

### Post by HenrikMundt on 2012-12-03
First of all - it seams that 12:10 in somewhere in the box:)
After (alt+control+F1) and login I ended whit ubuntu 12.10 at the top.
Thats a start.

next was: nomodeset at the prompt - result: command not found.

secondly: apci=off - the only respond was that the curser went on to the next line.
third: noapic - command not found.

finally i tried to get out the nice way by printing "shutdown -h"
Well it did not shutdown!
But i got: shutdown: time
and - try "shutdown --help" which i did but i came not further i o w it was the switch that was the solution.
That was the morning exercise.

Hawe a nice day//H

---

### Post by Wim Sturkenboom on 2012-12-03
You forgot the 'now' in the shutdown command ;)

The suggestions that squakie made are supposed to be made in the grub menu. If you normally don't get the grub menu when your PC starts, press (and keep pressed) the <shift> key while your system starts (power on; actually immediately after the POST) till you get the grub menu.
Press 'e' when the menu shows which will give you a screen with a couple of lines. Find the one with _quiet splash_ and change it to e.g. _quiet splash nomodeset_. Next press <ctrl>x to boot.

To make the grub menu show at each boot without pressing <shift>, edit /etc/default/grub (you need root permissions) and modify the hidden timeout as shown below (in bold red)

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
**[COLOR="Red"]GRUB_HIDDEN_TIMEOUT=[/COLOR]**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Save the file and run
```

sudo update-grub

```
to activate the changes and after a reboot you will always have the menu.

---

### Post by squakie on 2012-12-05
You don't put the boot options at the command line.  You must put these in the boot line that is being used when you boot linux.  I believe if you keep pressing F6 while the hardware is initializing (not ubuntu loading) you should get a menu from where you can edit the boot line.  Add those options by the quiet nosplash options in that line, then tell it to boot.  If that works, then we can walk you through making the changes permanent.

---

