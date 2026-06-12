---
title: "KDM login and ubuntu problem"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by arieleoar on 2014-08-06
Hi there again :S  The situation: i've ubuntu 14.10 LTS installed and kubuntu-desktop with it. I use Kde more than ubuntu, so weeks ago i changed the default lightdm login screen with the KDM login screen.  The problem: Kde desktop session opens normally, but when i want to login with the ubuntu-desktop (unity) it freezes in the load, neither shows the desktop. to access to it i've to open the tty console and open ```
sudo lightdm
``` then with CTRL+ALT+F7 open the ubuntu-desktop in the lightdm login screen and then runs in the "CTRL+ALT+F7" screen. Meanwhile the "CTRL+ALT+F8" screen stills frozen in the load.  Any solutions? i don't like lightdm...

---

### Post by grahammechanical on 2014-08-07
Are you sure that you did not remove ubuntu-desktop at the same time that you made the switch over to KDM. How did you switch from LightDM to KDM?

 As I understand things we have 7 TeleTYpewriter consoles (TTY) and Linux loads on TTY1 and Ubuntu runs on TTY7.

We can switch to TTY1 from the desktop with Ctrl+Alt+F1 and then switch back to the desktop with Ctrl+Alt+F7 (TTY7), The other five consoles (TTY) are accessed through Ctrl+Alt+F2 to F6.

So, I do not understand what you are saying about Ctrl+Alt+8. Ubuntu with whatever login manager that we have installed should be loading on TTY7.

Regards.

---

### Post by coldcritter64 on 2014-08-07
OP, with KDM set as your default you should be able to select either a kde desktop or an ubuntu (unity) desktop from the kdm login screen. You don't need to use lightdm at all under normal circumstances with your setup.

**Question: **Are you trying to get multiple desktop sessions running, kde and unity (ubuntu), _*on separate ttys at the same time*_ using ctrl+ alt + f? to switch between them ?

If so, after launching kdm and logging into your kde desktop (on TTY7), try using ctrl + alt + f2 (don't use f1, that is for the default session already launched on TTY7)  then try the command,
```
sudo service lightdm start
```
I think Ubuntu's login screen may be hanging on TTY8 because of the command used. I'm not sure how well this will work with kdm and lightdm and launching multiple sessions. I've had similar multi-headed sessions on up to 7 TTYs at once using GDM launched from TTY1 and the startx command launching sessions from TTYs 2 to 6 on a Debian install in the past. I'd be interested to hear how you go in this case IF this is what you are attempting. Though really you should try to stick to a single session from the KDM login if you don't like lightdm, less potential problems. There should be an option in a drop down menu on the KDM login screen for an Ubuntu (Unity) session to be selected, no need to use lightdm to launch unity (ubuntu), KDM should be able to do so.

---

### Post by arieleoar on 2014-08-07
[QUOTE=grahammechanical]Are you sure that you did not remove ubuntu-desktop at the same time  that you made the switch over to KDM. How did you switch from LightDM to  KDM?[/QUOTE]

I'm sure, because using muon package manager (from kde, shows all the packages installed in the system, including non kde packages) shows that the entire package "ubuntu-desktop" is installed, if there's a problem with it, will be show as broken.
i've set as default using
```
sudo dpkg-reconfigure kdm
```
and then appears a screen where you select which manager you want as predefined

[QUOTE=grahammechanical]So, I do not understand what you are saying about Ctrl+Alt+8. Ubuntu  with whatever login manager that we have installed should be loading on  TTY7.
[/QUOTE]

sorry that was a typo, i mean CTRL+ALT+F1 and CTRL+ALT+F7, what i don't know and can't explain (because i'm newbie) is why KDM login manager is shown in the "CTRL+ALT+F8" before boot and the lightdm is shown in CTRL+ALT+F7 when it's running from TTY1

[QUOTE=coldcritter64]OP, with KDM set as your default you should be able to select either a  kde desktop or an ubuntu (unity) desktop from the kdm login screen. You  don't need to use lightdm at all under normal circumstances with your  setup.[/QUOTE]

That's the problem, is not normal :p, I'm able to select unity desktop from the kdm, but then it stops loading and the screen stays with the background image of KDM.

I have to call lightdm to access to unity from TTY session, I not attempted to open multiple desktop in the same pc, i opened unity from lightdm to find something helpfull about this problem, at the moment i can say that unity session opens well in lightdm and it wont in KDM

Question: kdm makes a log in every attempt to login? where i find it?

Sorry about the grammar and the typos, and thanks to answer!

---

### Post by coldcritter64 on 2014-08-07
>  I not attempted to open multiple desktop in the same pcGood, I advise you not to. This narrows down what is happening to a fault launching unity from the kdm manager.

Sorry I can't help further, more experienced/knowledgeable helpers will likely be needed to sort out the technicalities of setting up KDM with launching unity. Good luck.

---

### Post by danrgmc-yahoo2 on 2015-01-05
I had the same problem with a fresh ubuntu 14.10 installation; I simply entered: 'sudo dpkg-reconfigure lightdm'; when given choice between KDM, (which I had selected after doownloading and installing 'kde-full' and LIGHTDM, I selected LIGHTDM-rebooted and am now able to boot to either unity or kde at desktop login without problems.

---

### Post by arieleoar on 2015-08-03
Thanks danrgmc-yahoo2; sorry for not responding, that solved that problem, and runs everything without problem. but now i've made the mistake to install a fresh kubuntu 15.04 with plasmashell memory leaks without reading the bugs report of the upgrade. but that is other problem, i will mark this as solved. 
thanks everyone!

---

