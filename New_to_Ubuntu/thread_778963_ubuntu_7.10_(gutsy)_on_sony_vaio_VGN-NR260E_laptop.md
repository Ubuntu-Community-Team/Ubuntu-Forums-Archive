---
title: "ubuntu 7.10 (gutsy) on sony vaio VGN-NR260E laptop : brightness and boot issues"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by bhi24 on 2008-05-02
dear all,

I installed Ubuntu 7.10  (gutsy gibbon) on my Sony Vaio VGN-NR260E laptop (This came prepackaged with Windows Vista).
1) got wireless to work using steps prescribed in
[http://ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ubuntuforums.org/showpost.php?p=3868406&postcount=48)
2) installed wicd (and uninstalled network manager) using steps described in
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
2) got advanced desktop effects to work after installing gnome-compiz-manager and installing Xgl (and other necessary related packages as identified by Synaptic)
3) got touchpad to be disabled temporarily by typing using steps described here
[http://ubuntu-tutorials.com/2007/05/06/temporarily-disable-touchpad-while-typing/](http://ubuntu-tutorials.com/2007/05/06/temporarily-disable-touchpad-while-typing/)

there are two problems now:
1) Screen Brightness can not be controlled using power manager and/or brightness applet.
i can not control screen brightness using the steps described in
[https://help.ubuntu.com/community/SonyVaioBrightness?highlight=%28brightness%29](https://help.ubuntu.com/community/SonyVaioBrightness?highlight=%28brightness%29)
changing spicctrl by using the -b tag does not alter the brightness
since spicctrl does not work, i used the manual workaround, but there is not /proc/acpi/sony folder.
using xbacklight does not work either, as it comes up with a message saying something like 'no outputs have backlight property'

2) boot is extremely slow.
i saw that the verbose mode would always be stuck around the 'enabling common unix printing services' message, and so disabled that from the sessions menu in gnome. but the gnome desktop is still extremely slow to load. (nearly 5min after logging into the splash screen)
i have installed bootchart and attached are two outputs. interestingly the output in the bootchart shows that the time taken to boot is fairly quick (~45s), but by the time the desktop actually loads,and the buttons start working - it's about 5 min. 

needless to say, i would be immensely grateful for any help/suggestion!

---

