---
title: "How to create a Distro Installer"
date: 2009-03-06
forum: Programming Talk
---

### Post by sujoy on 2009-03-06
How does one write an installer for a new distro?
I am working on a LFS project for sometime now. While I have found the required scripts for turning it into a live CD, I am as yet clueless how to write an installer for it.

I am not trying to compete with the debian installer or anaconda for that matter, just a trivial, no frills system that gets the job done. Something like zenwalk, slackware, arch's installer type perhaps?

Any materials, links and pointers on the above is gratefully accepted. 
Thank you.

---

### Post by the_unforgiven on 2009-03-06
Since it's a 'from scratch' distro, there is no installer spec pre-defined as such - it's what you define it to be :p.

Also, installers for linux should be pretty straighforward - even a simple shell script should do. Because, the only thing you need to take care of is putting the right files in right places and handling configuration updates - both of which are defined by your LFS FS hierarchy.

---

### Post by gjoellee on 2009-03-06
> **sujoy said:**
> How does one write an installer for a new distro?
I am working on a LFS project for sometime now. While I have found the required scripts for turning it into a live CD, I am as yet clueless how to write an installer for it.

I am not trying to compete with the debian installer or anaconda for that matter, just a trivial, no frills system that gets the job done. Something like zenwalk, slackware, arch's installer type perhaps?

Any materials, links and pointers on the above is gratefully accepted. 
Thank you.

I don't know so much about this, but you CAN install a distro using a simple bash script! Here are something that might help you:

-You must use the "mount" command to mount the created partitions

-Make sure to know where the root partition (also kalled "/") is mounted, because it is on that partition all software should be installed

-To install software to the root partition, just use the "cd" command to go do the mount moint, ie: /mnt/root/ and then you can use "wget" do download the source packages you need, and install them. If you install dpkg, you can download DEB packages after it is installed, and install the DEB packages instead of source.

-To add a user use the "adduser" command. To give the users it's correct information you should study that command.

-If some files have to be configured before you reboot into the installed system, make sure those files get's configured

-Use the "umount" command to unmount the partitions you installed Linux in, and use "reboot" to reboot the computer, and the installation is finished!

---

### Post by sujoy on 2009-03-06
hey, thanks for the input guys.
but the main problem is, when i'll be distributing the distro, say on a CD, the guy installing it will need to boot from it.

how do i make a bootable disc that will boot the PC and run some shell scripts or any other programs that i write?
like the ubuntu installer, you can use the ubuntu CD on a brand new PC, it boots from the CD and then goes on running the installer. pretty much all the distros has a bootable disc that runs the installer. so i need to make my shell scripts or whatever run from a booted-from-my-CD environment, since i cannot assume the user will have any other OS installed

---

### Post by the_unforgiven on 2009-03-07
You might want to check out this:
[http://www.linux.com/feature/146863](http://www.linux.com/feature/146863)

---

### Post by sujoy on 2009-03-07
hmm, yea i did came across this one earlier. it specifically asks for a ubuntu ISO and since i am doing it from scratch ... well i guess its source code might contain some important information.

---

### Post by jimi_hendrix on 2009-03-07
i think you absolutely stole my idea and i now hate you

:)

good luck!

---

### Post by albandy on 2009-03-07
If you want to base it on ubuntu you can use uck (ubuntu customization kit) allowing you to add packages and modify all you want throught synaptic and a console

---

### Post by .Maleficus. on 2009-03-07
If you haven't seen [this]("http://www.linuxfromscratch.org/hints/downloads/files/boot-cd_easy.txt") already, check it out.  It tells how to create an "easy boot CD" from an existing LFS install.  As for creating an installer for it, I can't help much with that.  My only suggestion would be a Bash script using Ncurses or similar to handle the "GUI" of it.

---

### Post by gjoellee on 2009-03-07
This can be helpful: [http://www.linux-live.org/](http://www.linux-live.org/)

---

### Post by Gordon Bennett on 2009-03-07
[URL="http://custom.nimblex.net/"]
NimbleX[/URL] is also worth checking out.

---

### Post by sujoy on 2009-03-15
well after some consideration, i am now going be content with the live cd scripts @ linux-live :)

guess i should get the distro doing the stuffs, i want it to do now, and once the live cd is satisfactory, i'll think about an installer ...

thanks for all the help guys

---

