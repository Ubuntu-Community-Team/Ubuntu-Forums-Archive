---
title: "xubuntu 13.10 has a black screen after boot"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by vitor.rca on 2013-12-13
I installed xubuntu 13.10 on an 2003 HP-Compaq Desktop / AMD Athlon-64 / 1Gb RAM / 80Gb HD,  installed all the updates, restarted the computer and it worked great. But, I turned it off and on again, a black screen appears and nothing happens!

I am able to Ctrl+Alt+F1

Any help, please.

---

### Post by eldrich_rebello2 on 2013-12-13
can you start in 'safe mode' or with all options off after the GRUB prompt?

---

### Post by Topsiho on 2013-12-13
Try boot the computer with the nomodeset option.
That works for this boot only.

See: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Topsiho

---

### Post by mörgæs on 2013-12-13
Nomodeset is a classical solution to Nvidia problems, so maybe we should first ask original poster about which graphics hard he has...

Does it run well in a live boot?

---

### Post by squakie on 2013-12-13
And....if the OP can indeed to get to a terminal as indicated: 

 lspci | grep VGA  <press enter>

if probably the easiest way to get that information. ;)

---

### Post by r_nguba on 2013-12-14
Close and re-open laptop to get lights back the do below changes, if cant get back ligh by closing and re-opening, then i advice u use a touch light to get to configuracions, brightness and lock to increase brightness then do bellow.
Edit grub, via comand in terminal [COLOR=#ff0000]sudo gedit /etc/default/grub[/COLOR]   will ask for password, enter pass and press enter,  change below line: 

GRUB_CMDLINE_LINUX=""  to   GRUB_CMDLINE_LINUX="acpi_backlight=vendor" 

and save the file, then update grub [COLOR=#ff0000]sudo apt-get update grub[/COLOR]

Enjoy Ubuntu 13.10 during xmas. -)

---

