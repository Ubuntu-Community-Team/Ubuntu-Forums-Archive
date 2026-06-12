---
title: "[SOLVED] Many Problems After Upgrade-Gnome, No Log Out-Need Assistance"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by randy78 on 2008-04-24
Well,

I decided to upgrade to Hardy after using Gutsy since release and things have been hectic, to say the least.

While installing the upgrade, I got 2 errors:
John
Timidity

Things seemed fine though, and I was instructed to reboot, rebooted and immediately noticed that the GRUB menu did not reflect a kernel update.

I could NOT even get to the log-in screen (progress circle would just spin and spin) so I would ctrl+alt+backspace, where I got an error about ALSA and Timidity (error 32)

I rebooted into Ubuntu (old kernel), waited and waited for the login page (5-6 minute wait!), booted into a Failsafe terminal, where I did sudo apt-get remove john and sudo apt-get remove timidity. After this, I did'sudo apt-get update' and 'sudo apt-get dist-upgrade' again, and the upgrade finished, the new kernel compiled and I rebooted.

GRUB reflected that the new kernel had been installed, so I booted into Ubuntu (new kernel), had to wait a very long time again for the login page to load, and tried to login as usual, but was greeted with errors about "Jockey"(?) "Bonobo Activation Server" and how nautilus and gnome could not be used.

I did some searching on my own, rebooted into failsafe gnome and created a new user (heard that my Gnome settings may have been corrupted).

I tried to logout by pressing the logout button on my taskbar, only to find that it did not work and none of the other buttons would work either.
I tried clicking the menu button, and got nothing.

So I ctrl+alt+backspaced and got back to the login screen, rebooted from there, booted into Ubuntu (new kernel), waited an eternity for the login window to come up, and logged in as my new user.

Success...

I then logged out again, logged into a failsafe gnome session as my old user, transferred my critical files and settings to a shared partition, logged back in as my new user (logged out of old user first), and copied the files I needed from the shared partition.

Things seem OK, and I'm able to work and get stuff done but several things are not working at all, such as the logout button...

To log out I am having to ctrl+alt+backspace and restart or power down from the login menu...

If I click the logout button, it seems that all of the other buttons on the taskbar just freeze and do not respond to ANY amount of left or right clicking.

It seems that not all of my Compiz settings are being imported, as I no longer have the ability to scroll wheel click and drag the desktop cube around.

When I scroll down on the desktop using the scroll wheel, however, the cube does spin.

When I opened Firefox (recently installed Slickness theme), I noticed that I could not input any text into the main Google search bar, and can only search using the search field next to the URL bar in Firefox.

Gutsy was completely outstanding and I installed it on dozens of boxes for friends, to help them shake the draft from the Windoze, and I know that in time, Hardy will be just as awesome, if not better by leaps and bounds.

I just need some help getting my logout button to work again and decreasing the time it takes for the login screen to load.

I'm going to try and uninstall the Slickness theme to see if that remedies the google search box mystery in Firefox 3 and will report back with my findings.

Thanks in advance and Take Care
:guitar:

BTW:
Gutsy and Feisty ran FLAWLESSLY on my box... Here are the Specs:
HP Pavillion A1104x
Intel P4 3.06ghz
2GB Ram
Intel Integrated graphics 
Integrated soundcard

---

### Post by randy78 on 2008-04-24
Okay, it seems that the problem with the Google search box is that my font is bright white... rookie mistake...

---

### Post by randy78 on 2008-04-24
Just an update... I was able to login as my old user after uninstalling Mono from my home directory in Failsafe Gnome...

I read that it was causing the errors that I was receiving and decided to give it a try...

It worked...

I am still quite frustrated at how long it takes to bring up the LogOut/Switch User dialog after clicking the logout button and by how long it takes to bring up the login screen.

Compiz cube is back but my animation effects are gone...

Will try a few things to see if I can get them going ;)

Take Care :D

---

