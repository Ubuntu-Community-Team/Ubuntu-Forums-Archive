---
title: "HOWTO: Compile Updated Orinoco Wireless Drivers/Airsnort/Kismet/Ethereal"
date: 2005-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by wernst on 2005-03-10
Here are some steps to get Airsnort working on Ubuntu. (Other programs listed at end.)

- Back up your system. I like using Norton Ghost 2003. It is much easier thrashing around the system trying things when you know you can go back to a working setup. Think of it as a system-wide Undo.

- Find out what kernel you are running. You can open a terminal window and type "uname -r", or you can look at the GRUB bootloader screen. Write down what it says. In my case it is "2.6.1-4-686".

- Download the latest CVS version of the Orinico driver. I found it at:
[http://savannah.nongnu.org/cgi-bin/viewcvs/*checkout*/orinoco/orinoco/index.html?rev=1.22&cvsroot=Web](http://savannah.nongnu.org/cgi-bin/viewcvs/*checkout*/orinoco/orinoco/index.html?rev=1.22&cvsroot=Web)

after going to:
[http://savannah.nongnu.org/cvs/?group=orinoco](http://savannah.nongnu.org/cvs/?group=orinoco)

The result will be a tarbar. The file I got was: orinoco-0.15rc2.tar.gz

- OK, we need to uncompress it and work with it. If you're a GUI person, double-click the download, which opens it in File Roller, which is Gnome's archive manager. (Think Winzip.) Click the Extract button, make a new folder in your Home directory by clicking "Create Folder" and naming it something like "orinoco_cvs_driver", then click "Extract". Close File Roller. If you're not a GUI person, then you almost certainly know how to deal with a tarball on the command line.

- This makes a folder in your Home folder called "orinoco_cvs_driver" and inside this is a folder called "orinoco-0.15rc2" (at least for me. Version numbers can change.)  Inside "orinoco-0.15rc2" are all the files we need to compile and work with.

- Since we need to compile things, you need a few tools and files in order to compile. Open Synaptic Package Manager (Computer menu > System Configuration > Synaptic Package Manager) and use the Search function to find "linux-headers-(version #)" and highlight those items. In my case it was "linux-headers-2.6.8.1-4-686" and  "linux-headers-2.6.8.1-4". Then click "Apply" and then "Apply" again to get them. Use the same procedure to get "build-essential" (which also gets a lot of depandant things).

- A lot of people will tell you that you should move this folder of stuff to a "proper" working directory, like /usr/src or usr/local/src, and if you want to, go ahead. I don't bother with this. You also need to do a lot of things as root, which in Ubuntu is different. I just open up a Root Terminal window (Applications menu > System Tools > Root Terminal) but you can run "sudo" all the time in a regular terminal window if you like. These instructions assume you'll use the Root Terminal.

- Go to the folder with all the orinoco files. There's a "README.orinoco" file in there. I'd read it for any last minute instructions.

- Open your Root Terminal window and move to the orinoco folder with all the files. In my case, that is: /home/wernst/orinoco_cvs_driver/orinoco-0.15rc2.

- Type "make" (no quotes). After a moment, you should get a prompt again, and without errors.

- Type "make install" (no quotes). If you aren't doing this in a root terminal, then the command is "sudo make install" (no quotes) and enter your password. This installs the driver to the correct location. 

- (Note - if and when you upgrade your kernel or Ubuntu in general, if the new features of these Orinoco drivers stop working, it is because the update overwrote these files you just built. If that's the case, download the new Linux headers that correspond to whatever new kernel you have, and then do a "make" and "make install" with these files again, and you should be good to go.)

- Restart the computer. Make sure wireless access still works. If it does: good! You didn't break anything.

- You're probably doing all this to get the monitor modes working for Airsnort and other similar tools. To manually start monitor mode, first "disable" the wireless interface (eth1, in my case) in the Gnome networking panel (Computer menu > System Configuration > Networking).  Theres also a command line, um, command you can do as root, but I forget what that is. (I *think* its "ifconfig eth1 status down" but don't hold me to that.)

- Open a Root Terminal window. Type the command: "iwconfig eth1 mode monitor" (no quotes). You should see no error message. If you re-enable the wireless card in the Networking panel and try to ping other things, it shouldn't be able to. That's because you're in Monitor mode! Congratulations!

- Restart the system to get your normal wireless connection working again. To use an older version of Airsnort (0.23d), just select it from Synaptics. Then open a Root Terminal window. Start monitor mode (iwconfig eth1 mode monitor). Start Airsnort by typing "airsnort" (no quotes). Click "Refresh" once. Set Network Device to whatever your wireless card is (eth1 for me). Set Driver Type to "Host AP/Orinoco". Then click "Start" to start. Your capturing! Restart computer to reset interface (ejecting and inserting PCMCIA card should do it too).

- If you're looking for the latest Airsnort, download the latest package from [http://airsnort.shmoo.com/](http://airsnort.shmoo.com/). As of now, the latest version is 0.27e, so the download file is: airsnort-0.2.7e.tar.gz. As before, double-click it to open it in File Roller. Uncompress it someplace safe; I made an "airsnort" folder in my Home folder and uncompressed it there, which made a folder called "airsnort-0.2.7e" within "airnsort".  There's a README file you should check for any last minute instructions, along with an INSTALL file.

-Building airsnort requires some more things, but they are installable via Synaptic. I THINK all you need to install is "libgtk2.0-dev" but I also installed "libgtk1.2-dev" to be safe. You also need "libpcap0.8-dev."

- Open a Root Terminal window and move into the airsnort directory with all the files. For me, that's: /home/wernst/airsnort/airsnort-0.2.7e. Start with typing "./configure" (no quotes). This makes sure you've got the right building blocks to build. If there are no errors...

- Then do a "make" and "make install" (no quotes). With any luck, this puts an airsnort executable in /usr/loca/bin, which happens to be in the PATH.

- To run it, open a Root Terminal window and type "airsnort" (no quotes). The latest version of Airsnort AUTOMATICALLY ENABLES MONITOR MODE. You don't even need to disable the wireless interface (like eth1) first. Just make sure "eth1" and "Host AP/Orinoco" are selected in Airsnort and click "Start." To stop, click "Stop." You won't be able to go online while scanning, but the connection will be restored to normal when you stop scanning.

- Interested in the latest versions Ethereal and Kismet? You're in luck! They use the updated CVS-based Orinoco drivers too. I am not going to go through the steps, but if you paid attention to how to make Airsnort, then you'll do fine. The basic deal is to download the source tarball, uncompress it, read any README or INSTALL files that came with the package. Use Synaptics to download any required dependancies. You'll be told to "./configure", "make", and "make install". You may (will) get errors during your ./configures and makes, BUT stay calm and read them. If, for example, the error message says "yaff not found" then use Synaptics to search for "yaff" and install it, and then try the ./configure or make again. Doing nothing more than this, Ethereal and Kismet will compile, install, and work.

- Don't mind using older versions of Kismet and Ethereal? Just use Synaptics to get them.

Want to know how to actually *use* these programs? I'm the wrong person to ask.

- Warren Ernst

---

### Post by wernst on 2005-03-16
I thought *for sure* someone would have commented by now. Oh well, at least there's no grousing over how I screwed something up. ;-)

-Warr

---

### Post by jax on 2005-03-16
ok, well i finally managed to 'make' and 'make install' thanks to this guide, but I still can't seem to enable monitor mode. It's as if the drivers haven't been updated.

Am I missing something here ?  ](*,) 

jax

---

### Post by wernst on 2005-03-20
You need to be root to enable monitor mode, either with "sudo" or by opening up a root terminal window.

-Warr

---

### Post by jax on 2005-03-20
Yea, I know. But that isn't the problem.

---

### Post by emmbec on 2005-03-21
I downloaded the drivers and uncompressed them correctly. I am in root terminal. I downloaded wverything you sayed. Then I tryed the "make" command but I receive an error that says:

Makefile:35: *** The kernel source is not configured.  Stop.

what do i do now?????

---

### Post by mbridak on 2005-03-23
Well, I have the Orinoco sources, and installed the kernel headers for the correct kernel version I'm running. I can compile the drivers with the make command. I can even install them with the make install command. I can even reboot and the wireless still works thank god. But the monitor mode is still not working.... after ifdown eth1 and then issuing the command to enable monitor mode i get:

root@linuxssn:~ # iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not supported.

And iwpriv does not show the option available to use....

root@linuxssn:~ # iwpriv eth1
eth1      Available private ioctl :
          force_reset      (8BE0) : set   0       & get   0
          card_reset       (8BE1) : set   0       & get   0
          set_port3        (8BE2) : set   1 int   & get   0
          get_port3        (8BE3) : set   0       & get   1 int
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get   1 int
          set_ibssport     (8BE6) : set   1 int   & get   0
          get_ibssport     (8BE7) : set   0       & get   1 int
          get_rid          (8BE9) : set   0       & get 1024 byte

Perplexed.... Befuddled... Bewildered...

I guess I will have to rtfm... E-gads.

---

### Post by charon79m on 2005-06-06
Anyone else having issues with this?

I've got my sources:

root@hostname:/home/username/orinoco/orinoco-0.15rc2 # apt-get install linux-headers-2.6.10-5-686
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@hostname:/home/username/orinoco/orinoco-0.15rc2 # apt-get install linux-headers-2.6.10-5
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

"make" results in this output:

make -C /usr/src/linux-headers-2.6.10-5-686 M=/home/username/orinoco/orinoco-0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /home/username/orinoco/orinoco-0.15rc2/orinoco_pci.o
In file included from /home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:117:
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_cor_reset':
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:158: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:164: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:171: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:174: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_suspend':
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/home/username/orinoco/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
make: *** [modules] Error 2

Anyone have any suggestions?

Charon79m

---

### Post by jshein on 2005-06-10
See my post here. It works ( at least for me ) every time

[http://ubuntuforums.org/showthread.php?t=23596](http://ubuntuforums.org/showthread.php?t=23596)

---

### Post by renesr on 2005-11-07
Hi.

You have been a great help to set up Aisnort until:

#cvs -z3 -d:ext:anoncvs@savannah.gnu.org:/cvsroot/orinoco co orinoco

Please let me know how to get/install the above.

Thanks,
Rene.

---

### Post by jshein on 2005-11-07
You will need to have the CVS program installed in order to complete this step.

> #apt-get install cvs

---

### Post by ardoaamch on 2005-11-29
[QUOTE=charon79m]Anyone else having issues with this?

I've got my sources:

root@hostname:/home/username/orinoco/orinoco-0.15rc2 # apt-get install linux-headers-2.6.10-5-686
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@hostname:/home/username/orinoco/orinoco-0.15rc2 # apt-get install linux-headers-2.6.10-5
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

"make" results in this output:

make -C /usr/src/linux-headers-2.6.10-5-686 M=/home/username/orinoco/orinoco-0.15rc2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /home/username/orinoco/orinoco-0.15rc2/orinoco_pci.o
In file included from /home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:117:
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_present':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:400: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_set_irqmask':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:406: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_read_words':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:447: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_write_words':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:467: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/hermes.h: In function `hermes_clear_words':
/home/username/orinoco/orinoco-0.15rc2/hermes.h:483: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_cor_reset':
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:158: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:164: warning: passing arg 2 of `writew' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:171: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:174: warning: passing arg 1 of `readw' makes pointer from integer without a cast
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_suspend':
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:330: error: too many arguments to function `pci_save_state'
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c: In function `orinoco_pci_resume':
/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.c:347: error: too many arguments to function `pci_restore_state'
make[2]: *** [/home/username/orinoco/orinoco-0.15rc2/orinoco_pci.o] Error 1
make[1]: *** [_module_/home/username/orinoco/orinoco-0.15rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
make: *** [modules] Error 2

Anyone have any suggestions?

Charon79m[/QUOTE]

I'm getting this exact same error.

---

