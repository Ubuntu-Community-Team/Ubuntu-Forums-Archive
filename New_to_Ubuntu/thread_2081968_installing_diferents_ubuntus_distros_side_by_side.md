---
title: "installing diferents ubuntus distros side by side"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by papilonaa on 2012-11-08
helo i did install various ubuntus distros automatichly side to side, ils fine but i would like to change the line text and the grafic boot display, how shall i do?
and how many distros can i install side to site?
thanks

---

### Post by newb85 on 2012-11-08
I would suggest grub-customizer.  It's not in the repos, so you'll have to add the PPA.
[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

I'm not aware of a limit to the number of distros you can install side-by-side, aside from the practical limit of your HDD space.  I currently have four distros installed, in addition to Win7.

---

### Post by grahammechanical on 2012-11-08
Here are some things to read:


[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

[http://ubuntuforums.org/showthread.php?t=1534689]("http://ubuntuforums.org/showthread.php?t=1534689")

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")


Regards.

---

### Post by oldfred on 2012-11-08
Above are good, and some more links:

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by Calinou on 2012-11-08
You can install several desktop environments/window managers on one installation, then choosz them at login.

---

### Post by Raphicerus on 2012-11-08
> **Calinou said:**
> You can install several desktop  environments/window managers on one installation, then choosz them at  login.

After using a standard 12.04, after several months I finally noticed  the login choice button (!), and tried the various user interfaces.

Having  installed various programs like k3b, I'd like to try the interface  (kubuntu?) that they hail from. Is that something that can just be added  to the options already offered in the 12.04 logon, without putting the  stability of the existing installation at risk?

Hope this is still on-topic enough, but it seems relevant to the OP.

---

### Post by newb85 on 2012-11-08
Everything you need for the Kubuntu interface is available in the repos.  kubuntu-desktop is what you're looking for.  In addition to the Desktop Environment, it also recommends the apps that are installed in Kubuntu by default.

```
sudo apt-get install kubuntu-desktop
```

Or, if you want the DE without the extra default apps,
```
sudo apt-get install --no-install-recommends kubuntu-desktop
```

---

### Post by Raphicerus on 2012-11-08
> **newb85 said:**
> Everything you need for the Kubuntu interface is available in the repos.  kubuntu-desktop is what you're looking for.  In addition to the Desktop Environment, it also recommends the apps that are installed in Kubuntu by default.

```
sudo apt-get install kubuntu-desktop
```Or, if you want the DE without the extra default apps,
```
sudo apt-get install --no-install-recommends kubuntu-desktop
```

Just tried the first option, and totally scared the living cr*p out of myself rebooting.
Time to run away and hide in the proverbial aardvark burrow. :)

Opted for reboot into the standard interface; I'll try kubuntu tomorrow.

Thanks.

---

