---
title: "can't install oo or libreoffice on xubuntu 11.10"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by al.adab on 2011-11-02
hello 

this is what I'm trying to do: 

        [I]sudo add-apt-repository ppa:openoffice-pkgs/ppa


        sudo apt-get update 


        sudo apt-get install openoffice.org[/I]

and this is what I get: 

[I]W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu)[I]/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
imageraw@T42:~$ sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 openoffice.org : Depends: libreoffice but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/I][/I]

can you please help? thanks

---

### Post by al.adab on 2011-11-02
something similar is happening if I try to install libreoffice...specifically the line 

*E: Unable to correct problems, you have held broken packages.*

appears in the error message.

---

### Post by westie457 on 2011-11-02
Hi, if you are still using Lucid, Open Office was installed by default and is available in Synaptic. The use of PPA's should not be necessary.

With the error message for Libre Office there should be a suggestion of a command to run to fix things.


==================================================================

Silly me! Reread the thread title. I think Open Office has been deprecated for 11.10 and is no longer available, This is certainly true for my test install of - under development - Precise Pangolin.

---

### Post by al.adab on 2011-11-02
installed from Synaptic. Error has disappeared on a sudo apt-get update. 
thank you

---

