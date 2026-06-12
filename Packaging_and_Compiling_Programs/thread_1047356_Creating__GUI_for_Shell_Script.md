---
title: "Creating  GUI for Shell Script"
date: 2009-01-22
forum: Packaging and Compiling Programs
---

### Post by strobon on 2009-01-22
please help me...

i`m trying to create an automatic installer for ubuntu application and
its library, in this example case i use "mplayer". To install it (for those who`s tottally offline),
they need to manually download the application itself plus the library.
But i`ve already create a shell script to automatically install the package 
(sudo dpkg -i libartsc0_1.5.9-0ubuntu2_i386.deb libaudio2_1.9.1-1_i386.deb.........).
The problem is i have already many application to install and it takes a lot of time to install
them one by one.So i decide want to create a single interface to make other offline user easy to 
install package they want to by just select the application they want to install and hit install 
button (in the background, the program execute the shell script that install the application and
its library automatically).For example if they select to install "mplayer" the
shell script executed and all the package inside the folder "mplayer" were installed,
and the application install by itself in the background.I know its easy for online user, they just
only need to run "sudo apt-get install mplayer" (CMIIW), and the required library downloaded by itself.
But to them who is tottally offline, thats a big problem.

I`ve anyone got some idea about this,i wanna thanks a lot...

---

### Post by sisco311 on 2009-01-22
you can copy debs in /var/cache/apt/archives/ and install them with: ```
apt-get install package-name
```
or add/remove or synaptic.

Also Synaptic has a 'Generate package download script' menu item.
Just select the apps you want to install, generate the script
and use it to download the apps on an on-line linux system.
Copy the debs in /var/cache/apt/archives/ and use apt to install the packages.

---

### Post by ajgreeny on 2009-01-22
Look into aptoncd, a package which will make a kind-of on-CD repository which can then be transfered to another off-line computer.

---

### Post by strobon on 2009-01-25
thx for the help...it makes easier for me to get rid of those library dependency problem.
now comes the problem...
i need to create an interface for this to automatically execute my shell script (that install deb package)

---

