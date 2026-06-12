---
title: "Speakers won't work (HT Omega Claro soundcard issue)"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Elronius on 2013-03-04
Hey all,  I'm a new user of Ubuntu, trying out Linux from Windows in hopes of switching. However, right now I'm not able to get the sound working and it's cramping my ability to use Ubuntu for general purpose stuff. I'm using an HT Omega Claro sound card. Have tried installing ALSA from the Ubuntu Software Center, but that alone didn't fix it. Right now I'm looking at following the instructions on this page: [www.alsa-project.org/main/index.php/Matrix:Module-oxygen](www.alsa-project.org/main/index.php/Matrix:Module-oxygen) to install the relevant driver (I think). However, I can't seem to input the instructions word for word, and I don't really understand what I'm doing anyway. I'm not at all afraid of the terminal (or even messing anything up, bring it, this hard drive is freshly formatted! :p), but I do want to understand what I'm doing so I can learn in the process. Oh, and above all I'd like to get my sound card up and running so I can hear the audio from kittens riding on Roombas (just not as enjoyable muted).  In all seriousness, I guess my question here is: am I on the right track as I described above, and what am I missing in terms of updating the drivers if so? I seem to be having trouble with interfacing with GIT repositories and using the "cp" command, but that's not too surprising considering I'm not familiar with what the commands are doing.

---

### Post by ManamiVixen on 2013-03-04
what version of ubuntu you have?

---

### Post by ManamiVixen on 2013-03-04
Is it 12.04, 12.10, or older?

---

### Post by Elronius on 2013-03-04
Oops, sorry - that would be good to mention :p Using 12.04.2 LTS  Edit: Also Unity, if it matters.

---

### Post by ManamiVixen on 2013-03-04
You have to upgrade your kernel to a newer version. The oxygen chipset driver for your card was added in Kernel 3.7. To upgrade your kernel, youll have to get down and dirty.

Open Terminal "ctrl+alt+t" and type without the quotes "sudo apt-get install wget"
Now in your home folder, create a folder called Kernel-3.7.10. Then back in Terminal type "cd /home/yourusername/Kernel-3.7.10 then type in all four of only one of the groups below.

For 32bit Ubuntu:
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710-generic_3.7.10-030710.201302271235_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710-generic_3.7.10-030710.201302271235_i386.deb) 
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710_3.7.10-030710.201302271235_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710_3.7.10-030710.201302271235_all.deb) 
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-3.7.10-030710-generic_3.7.10-030710.201302271235_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-3.7.10-030710-generic_3.7.10-030710.201302271235_i386.deb) 
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-extra-3.7.10-030710-generic_3.7.10-030710.201302271235_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-extra-3.7.10-030710-generic_3.7.10-030710.201302271235_i386.deb)

For 64bit Ubuntu:
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710-generic_3.7.10-030710.201302271235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710-generic_3.7.10-030710.201302271235_amd64.deb) 
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710_3.7.10-030710.201302271235_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-headers-3.7.10-030710_3.7.10-030710.201302271235_all.deb) 
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-3.7.10-030710-generic_3.7.10-030710.201302271235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-3.7.10-030710-generic_3.7.10-030710.201302271235_amd64.deb) 
wget  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-extra-3.7.10-030710-generic_3.7.10-030710.201302271235_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.10-raring/linux-image-extra-3.7.10-030710-generic_3.7.10-030710.201302271235_amd64.deb)

After it finishes downloading, run in the same terminal right after download " sudo dpkg -i *.deb "

Once that is done, reboot and everything should be fixed.

---

### Post by ManamiVixen on 2013-03-04
Well ****... the forum keeps shortening the links! so you can't copypaste them >:O

So in the terminal just type wget then copy link location and paste the link in the terminal. Then press enter.

---

### Post by Elronius on 2013-03-04
Hm, I have an AMD64 processor and was pretty sure I installed 64-bit Ubuntu, but it says I have an x86 processor for some reason... Anyway, went ahead and got the following errors:
ERROR (dkms apport): kernel package linux-headers-3.7.10-030710-generic is not supported
ERROR (dkms apport): kernel package linux-headers-3.7.10-030710-generic is not supported
Error! Bad return status for module build on kernel: 3.7.10-030710-generic (i686)
Consult /var/lib/dkms/nvidia-current-updates/304.64/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.7.10-030710-generic (i686)
Consult /var/lib/dkms/nvidia-173-updates/173.14.36/build/make.log for more information.
ERROR (dkms apport): kernel package linux-headers-3.7.10-030710-generic is not supported
Error! Bad return status for module build on kernel: 3.7.10-030710-generic (i686)
Consult /var/lib/dkms/nvidia-173-updates/173.14.36/build/make.log for more information.
ERROR (dkms apport): kernel package linux-headers-3.7.10-030710-generic is not supported
Error! Bad return status for module build on kernel: 3.7.10-030710-generic (i686)
ERROR (dkms apport): kernel package linux-headers-3.7.10-030710-generic is not supported
Error! Bad return status for module build on kernel: 3.7.10-030710-generic (i686)
Consult /var/lib/dkms/nvidia-173-updates/173.14.36/build/make.log for more information.
ERROR (dkms apport): kernel package linux-headers-3.7.10-030710-generic is not supported
Error! Bad return status for module build on kernel: 3.7.10-030710-generic (i686)
Consult /var/lib/dkms/nvidia-current-updates/304.64/build/make.log for more information.

That was in addition to a lot of other messages though. I'm going to try a reboot and see where that gets me.

---

### Post by Elronius on 2013-03-04
Woo-hoo, sound works now! The video resolution got a little screwy, but that's less essential (can see, just not at the resolution I prefer) and I can experiment on my own to see if I can figure that part out. Thanks! I guess what I was doing was installing 4 different parts of the kernel with those .deb files? Edit: also, where did you go to figure out what version kernel the driver started working for?

---

