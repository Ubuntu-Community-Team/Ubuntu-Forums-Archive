---
title: "Grub in Xu 12.04 still lists old deleted kernels"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by ineuw on 2012-06-16
After a recent kernel update to .25, everything was working fine. Using Synaptic, I uninstalled versions .23 and 24. then updated grub several times, but on reboot it still lists the old kernels. Also checked Synaptic, and all elements are completely uninstalled. If I click on their grub entries, it tells me that the kernels don't exist.

Posted the grub.cfg to pastebin here: [http://pastebin.com/jmmDbVG2](http://pastebin.com/jmmDbVG2) The file is public and named xu 12_04 grub.cfg Perhaps someone can look at it and see what I did wrong? Thanks.

---

### Post by sudodus on 2012-06-16
How did you update grub? If you have dual or triple boot, only one of the linux installations is controlling grub, so you must run
```
sudo update-grub
``` from there.

---

### Post by drs305 on 2012-06-16
The boot info script from Boot Repair or from the following link would give us a better idea, but there are multiple repetitions in the grub.cfg file.

Do you have copies of the 10_linux scripts in /etc/grub.d ? If you have copies and they are executable they will run and place the information they find into grub.cfg. If you do, either remove the executable bit from the extras or move them out of the /etc/grub.d folder.

Boot Repair and "Boot Info Script" links in my signature line.

---

### Post by ineuw on 2012-06-16
> **drs305 said:**
> The boot info script from Boot Repair or from the following link would give us a better idea, but there are multiple repetitions in the grub.cfg file.

Do you have copies of the 10_linux scripts in /etc/grub.d ? If you have copies and they are executable they will run and place the information they find into grub.cfg. If you do, either remove the executable bit from the extras or move them out of the /etc/grub.d folder.

Thanks for the replies.
sudodus: I used sudo update-grub several times.

drs305: yes,  have several files and they are:

00_header
05_debian_theme
0_linux
20_memtest86+
20_linux_xen
30_os-prober
40_custom
41_custom
README

Please give one sample of the command line needed to remove the executable bits and move the unnecessary files out of the folder. Thanks

---

### Post by drs305 on 2012-06-16
> **ineuw said:**
> Thanks for the replies.
sudodus: I used sudo update-grub several times.

drs305: yes,  have several files and they are:

00_header
05_debian_theme
0_linux
20_memtest86+
20_linux_xen
30_os-prober
40_custom
41_custom
README

Please give one sample of the command line needed to remove the executable bits and move the unnecessary files out of the folder. Thanks

Those are all the normal files that should not produce the results you are getting.

I think the next step would be to purge and reinstall grub. From your running installation:
```

sudo apt-get update # Make sure your Internet connection is working. If it isn't, don't run the rest of the commands.
sudo apt-get purge grub-common # This will purge all the grub packages
# You will be warned you are removing the bootloader. TAB to OK.
sudo apt-get install grub-pc
sudo update-grub # Run again just to make sure. Watch the terminal for any unusual messages.
```
If asked, install the package maintainer's version.
Use the SPACEBAR to select the *drive* (sda, sdb, etc). Do not select a partition. TAB to OK.
Grub should update after it is reinstalled. You can inspect /boot/grub/grub.cfg or reboot to see if the menu is now correct.

If it isn't, run the Boot Info Script and post the contents of RESULTS.txt (see BIS link in my signature line).

---

### Post by ineuw on 2012-06-16
dr305: Please accept my gratitude. Did as instructed and the grub is as it should be. In biblical terms, your solution will not win you my sister's hand (I don't have one), but it is certainly worth a flock of sheep. Thanks again.

---

### Post by drs305 on 2012-06-17
> **ineuw said:**
> dr305: Please accept my gratitude. Did as instructed and the grub is as it should be. In biblical terms, your solution will not win you my sister's hand (I don't have one), but it is certainly worth a flock of sheep. Thanks again.


Sheep!  :guitar:

Glad it's working. If you would mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post it will allow the helpers concentrate on unresolved issues. Thanks.

Happy Ubuntu-ing !

---

