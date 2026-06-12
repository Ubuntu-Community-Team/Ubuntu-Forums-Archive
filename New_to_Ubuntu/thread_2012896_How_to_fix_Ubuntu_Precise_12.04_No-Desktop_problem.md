---
title: "How to fix Ubuntu Precise 12.04 No-Desktop problem after fresh install"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by qigong888 on 2012-06-30
Hi Guys,

I just wanted to post this how to after endless hours of research, trial and error and tribulations.

How to fix the blank desktop issue after freshly installing Ubuntu Precise 12.04 into a PC with various NVIDIA graphics cards and Compiz.

I've done the following install from the Ubuntu Precise DVD install selecting first the TRY UBUNTU option first.  Once it was loaded, I then set up my wireless connection parameters and then selected the INSTALL UBUNTU icon.

This way, once you've installed Ubuntu Precise, your settings are kept and wireless will be immediately available to you seeing you have no way to set it up after installed because you'll need internet connectivity.  I've tried this on two different Laptops which are HP Pavilion D9000.

By the way, even if you select the "Download updates whilst installing" feature on the installation doesn't seem to do anything at this stage.

This method works (and was tested twice) as of 30 June 2012

------------------------------------------------------------------------

1. After installing fresh Ubuntu Precise 12.04 you log in, only to find either a totally black screen or default background image with just mouse pointer and no menu bar at all.

2. Now press CTRL and ALT together with the F1 key which will bring you to console screen which requests username and password.

3. Type in your username, then it will then ask you for your password you used when you installed Ubuntu Precise 12.04

4. Once you are logged in, type the following:
# sudo apt-get install aptitude gnome-panel gnome-shell
(Note: Obviously do not type in the "#" and because I hate Unity, I've opted to install the gnome panel and gnome shell packages for Gnome desktop rather than unity)

5. You will then be asked to type your password again and then it will start downloading the packages.

6. After the packages have installed, then type:
# sudo aptitude full-upgrade
(Note: Obviously do not type in the "#")

7. This process takes a while as it will upgrade all of the required packages to the latest version.

8. Once that's finished, type in:
# sudo reboot
(Note: Obviously do not type in the "#" but also, if you are asked for password, you obviously type it in and hit enter)

9. Wait until the PC reboots and once you've got the login screen up, type in your username and password and voila!  You've got a working desktop.

(Note: If you are like me and hate Unity interface, then don't forget to select Gnome-Classic(no effects) on the little wheel/cog next to the password box on the login screen)

Enjoy !!!

P.S.  Hope this helps at least 1 person.

(Reason for edit: Spelling Mistakes :D)

---

### Post by UforumMeforum on 2012-10-12
> **qigong888 said:**
> Hi Guys,

I just wanted to post this how to after endless hours of research, trial and error and tribulations.

How to fix the blank desktop issue after freshly installing Ubuntu Precise 12.04 into a PC with various NVIDIA graphics cards and Compiz.
...
P.S.  Hope this helps at least 1 person.

(Reason for edit: Spelling Mistakes :D)

YES! Thank you. :P I used Unity for a  LONG 5 minutes, and already despised it. Then I rebooted and it stopped working. Ha! It knew I didn't like it already. Coming from the 10.10 Gnome GUI, for the past 3 years, this really helped me.
:guitar: qigong888, you rock. (I'll pretend it's a bass guitar)

---

### Post by evelynb on 2012-11-23
wow thank you after several months of not having a functional ubuntu desktop your instructions resolved my issue.  so nice to see my desktop again!

Evelyn Rosa

---

