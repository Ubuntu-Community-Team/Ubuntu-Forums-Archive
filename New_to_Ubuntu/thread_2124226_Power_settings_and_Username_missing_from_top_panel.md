---
title: "Power settings and Username missing from top panel in gnome/unity..."
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Jakob Bielski on 2013-03-10
Just to clarify, i am a complete noob to linux. Ehhh. yeah this has been asked to death but so far none of the proposed solutions have worked for me.. A little background.. my computer was constantly freezing whilst i was using it, forcing me to do a hard restart, ended up messing up ubuntu, couldn't login without tty1, bla bla bla.. i fixed it all so that's all good, it was mainly a GUI and packages problem... Anyway.. i'm glad that my computers back, but when it came back there was a s*** load of problems with unity/gnome, invisible icons in the launcher panel, dash home was being screwy.. yadayada yada, so far i managed to fix that, except for one thing, the top panel in unity is missing stuff... in particular, it's missing the power settings and user settings... i've tried many of the proposed solutions, resetting gnome or unity, reinstalling them, configuring unity.. but to no avail.. here i'll throw you a screenie.
[IMG]http://i48.tinypic.com/29zsl53.png[/IMG]

Hey.. guess what that's a capture of? As you can see the power settings n such is missing from the top panel... and you can also see that i am a bit of a doom nerd...

P.S. Just to clarify im running 64-bit precise pangolin.....

---

### Post by ViliX64 on 2013-03-10
Try to reinstall the classic packages, that comes with ubuntu installation. You might have uninstalled those packages..

---

### Post by Jakob Bielski on 2013-03-10
Might have.. i'll get back to this in the morning though cos im gonna hit the hay... but to clarify,,, i do not recall uninstalling any packages.. just updating and repairing.. i did remove and purge packages relating to a certain app but this was after the problem begun...

---

### Post by ViliX64 on 2013-03-10
Ok, it looks like you are using Ubuntu - Unity enviroment.. so try to search for Unity in Ubuntu Software Center. Maybe it will help, because I have lost calendar (up there) and later I have found out that is was uninstalled..

---

### Post by Frogs Hair on 2013-03-10
Install this application. [https://apps.ubuntu.com/cat/applications/dconf-tools/](https://apps.ubuntu.com/cat/applications/dconf-tools/)

Open the dconf tools and select apps > indicator session and be sure show real name in panel is checked and see that the log-out/power buttons are not suppressed. To install or  re-install the applet/s if needed . ```
sudo apt-get install --reinstall indicator-session 
```
```
sudo apt-get install --reinstall indicator-power
``` Log-out/ in  or restart.

---

### Post by Jakob Bielski on 2013-03-13
Hey yo thanks both of you for helping me solve this..  sorry for the late reply.. ViliX64, you were right, i had some packages uninstalled, including the indicator for power and session, and thnx Frogs hair, dconf tool really helped, that way i was certain that the indicators were uninstalled, and thanks for giving me the commands for it.. I had been getting on alright with using commands in the terminal for my computer, but my main concern was that other people would use my computer, not know what to do, and hard boot/reboot/power off it. messing it up.. How do i reward both of you dudes? You gave me the perfect solution.. my desktop is back to norms again...

---

