---
title: "RealPlayer install"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-11
I have been trying to install real player using the following instructions:
   1. Get the RPM for RealPlayer 11 Gold here. NOT Helix Player 11.
   2. Using Synaptic Package Manager, install "alien" (or "sudo apt-get install alien" from the command line)
   3. From a terminal, navigate to the location of the RPM file you just downloaded ("cd path/to/file")
   4. In the terminal, type "alien HelixPlayer-11.0.0.4052-20080318.i586.rpm --scripts"
   5. Exit the terminal. Open Places --> Home Folder, navigate to the location of the RPM and the new DEB file. Double-Click on the DEB file to install (Note: You may get a script error. It is safe to ignore the error)
   6. The executable is /opt/helix/HelixPlayer/hxplayer
   7. You may manually add it to your Applications Menu.

Where I get stuck is on Number 3.  I have no idea where the RPM file is.  

Help

---

### Post by th3james on 2008-05-11
Have you downloaded the RPM from their site? the default download location in firefox is your desktop, so it would be ~/Desktop/RPMFILENAME.rpm

---

### Post by saskatchewan on 2008-05-11
This is the message that I get:
shawn@shawn-laptop:~$ cd Desktop/RealPlayer11GOLD.rpm
bash: cd: Desktop/RealPlayer11GOLD.rpm: Not a directory
shawn@shawn-laptop:~$ cd /Desktop/RealPlayer11GOLD.rpm: Not a directory
bash: cd: /Desktop/RealPlayer11GOLD.rpm:: No such file or directory
shawn@shawn-laptop:~$ 

WHat do I do?

---

### Post by Mze on 2008-05-11
Download deb file from this [thread]("http://ubuntuforums.org/showthread.php?t=758024")

---

### Post by th3james on 2008-05-11
The reason it wasnt working is because the command 'cd' tries to change directory, to the location you give it, but u we're giving it the file itself, so u needed to do the command '~/Desktop/' to get into the directory, sorry if i was unclear
But, as the guy above suggested, the deb file is the easiest thing to do

---

