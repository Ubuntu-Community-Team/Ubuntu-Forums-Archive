---
title: "Installed a package with synaptic but can not find it now"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by george97 on 2014-12-13
Hi I am having a problem trying to install ParaView version 4.1.0 on my Ubuntu 14.04 LTS. I usually use Synaptic Package Manager, however when i search for paraview they only have a different version. I need version 4.1.0 because i am trying to connect to a supercomputer with paraview that has that version. So I found paraviewopenfoam on Synaptic and it is version 4.1.0. However, after it installed successfully i can not open the application by either typing paraview from the command line or it is not listed as an installed program when i search for it in  the dash. I did find the folder in my opt folder however. But i am doing this run around because i can not figure out how to install the binaries directly. After i unpack the tar ball i get four different folders and ./configure doesn't work from that location and i can not find a README file or INSTALL file. Can somebody please help me to learn how to install binaries when i need to or just to fix this Synaptic problem ?? 

Thank you very much,
George Lees Jr.

---

### Post by buzzingrobot on 2014-12-13
The version of Paraview in the 14.04 repos is 4.0.1. 4.1.0 is available for 14.10 and the pre-release 15.04. The packages in the 14.10/15.04 repos would not ordinarily appear in Synaptic on 14.04. I.e., you should not have been able to install 4.1.0 with Synaptic on a standard 14.04 system. The 4.1.0 packages would have been visible in Synaptic only if you added the 14.10 or 15.04 repos (which is not recommended).

A package needs to create a'.desktop' file in /usr/share/applications before its icon will appear in the Dash. A .deb package intended for Ubuntu contains scripts that, among other things, handle that task. If you have extracted the binaries from a .deb package (that's unclear since you say you installed paraview with Synaptic, but then later menton a tar archive) then that file would not have been created. 

Since you can execute the program from the command line, it's likely it is installed correctly, except for the missing .desktop file.

The "./configure" command is used as the initial step in compiling source code extracted from a tar archive. The tar archives contained inside .deb packages intended for installation don't contain source code.

---

### Post by george97 on 2014-12-13
No i can not run it from the command line. I can open it only by double clicking an object file in its bin subfolder. Soo are you saying to upgrade Ubunut to 14.10 or Synaptic ? What would be the easiest way to correctly install because i tried to link paraview with BW supercomputer and it didn't work so before i contact their support network i want to atleast make sure that it doesn't work once i have it installed directly. Thank you btw

---

### Post by george97 on 2014-12-13
Ok i got you i am going to upgrade to 14.10 right now thank you

---

### Post by buzzingrobot on 2014-12-13
Paraview 4.1.0 on 14.10 appears to require a number of dependencies that are not available for 14.04 ([http://packages.ubuntu.com/utopic/paraview](http://packages.ubuntu.com/utopic/paraview)).  So, getting 4.1.0 on Ubuntu requires running 14.10.  Upgrading Synaptic wouldn't affect anything because it's just a tool that accesses whatever repositories a specific release uses. That's the reason you don't see 4.1.0 listed in Synaptic on 14.04:  It isn't in the 14.04 repos.

The correct way to install an Ubuntu package from the repositories is to use Synaptic or apt or the Software Center or one of the other similar programs.  They all access the same packges on the same repos.

---

### Post by george97 on 2014-12-13
Ok i am trying to upgrade from Ubuntu 14.04 to 14.10. When i look in "About This Computer" it says i have 14.04 LTS. So when i type update-manager from the prompt i get a message saying all software is up to date. Then when i go into Software and Updates and go to the tab "updates" and i am not able to click on anything. If i click a checkbox it automatically unchecks itself and i also can not change the "Notify me of a new Ubuntu version" from For long term support versions to any new versions. Then every time i go to exit i get a message saying "The information about available software is out of date" . Does anyone know how i can go ahead with this upgrade ???

---

### Post by buzzingrobot on 2014-12-14
Open a terminal, run "sudo apt-get update", and post the output here.

---

