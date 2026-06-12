---
title: "amd catalyste instalation error need help"
date: 2014-09-03
forum: New to Ubuntu
---

### Post by jimbob3 on 2014-09-03
hi i have a serious issue when trying to install catalyst manually i keep getting this error

Error! Bad return status for module build on kernel: 3.13.0-35-generic (x86_64)
Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up fglrx-amdcccle (2:13.251-0ubuntu1) ...
Setting up fglrx-dev (2:13.251-0ubuntu1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
darkcoin@darkcoin-GA-990FXA-UD3:~/Downloads$ 

i am a noob to unbuntu and dont know exactly how to go about resolving this issue, i have looked about for a solution but  with no success i have read that it might have somthing to do with xorg and how amd wont develope drivers that support the xorg platform can anyone help thanks.

---

### Post by coffeecat on 2014-09-03
Not a Forum Feedback and Help thread.

*Thread moved to **New to Ubuntu**.*

It looks as though you are trying to install a driver downloaded from the AMD site. Do you have a reason for making it more difficult for yourself rather than using the repository driver from Additional Drivers as suggested by three people in your earlier thread?

[http://ubuntuforums.org/showthread.php?t=2241560](http://ubuntuforums.org/showthread.php?t=2241560)

---

### Post by QIII on 2014-09-03
Why do you keep trying what is not working when I and others have given you alternate methods?

AMD/ATI drivers for Linux most certainly DO support xorg.  Three of my Linux machines run ATI cards with the proprietary driver.

I suggest you stop using random methods from the web and go back to your old thread where you were getting help.

---

### Post by jimbob3 on 2014-09-03
yes i am trying to mine crypto, doing repository drives i get a low dif which causes rejection of coins tried looking for solution for a week with no success so i am attempting to load drivers manually following guide in highoncoins.com that guides you through from installing configuring ubuntu, catalyst and cgminer. would appreciate any help from anyone my rig details Gigabyte motherboard GA-990FXA UD3, CORSAIR DUAL DDR3 RAM 1600, AMD ATHLON II CPU GRAPHIC CARDS 2 SAPHIRE HD7950 3GB BOOST 1 HD6450 HDD SANDISK 32GB SOLID STATE DRIVE POWER SUPPLY CORSAIR CX 750 M

---

### Post by QIII on 2014-09-03
If you insist on using someone else's tutorial, it might be best to see if they have a help forum.

I have installed the driver any number of times both by using the .sh file raw and by building a .deb file.  Both of those are also covered in the wiki in my signature, I believe.

I genuinely doubt that there is such a huge difference in the driver available in the repo, which was released in April 2014 and the current release or beta driver that it should make that much difference.

Unfortunately it would be impossible for us to assess the state of your machine at this point since you have bounced back and forth trying a number of different things.

Again:  you should go back to your original thread and address your concerns there so that you don't have several people, including me, trying to help in more than one place.

Thread closed.

---

