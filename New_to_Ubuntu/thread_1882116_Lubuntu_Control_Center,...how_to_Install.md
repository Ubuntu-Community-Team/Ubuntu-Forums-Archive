---
title: "Lubuntu Control Center,...how to Install?"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Carlzam on 2011-11-16
I installed Lubuntu 11.10 in my old ThinkPad Plll - 700Mhz - 512 Mb. - 40Gb Hd.

It run wonderful, I got new life for this old machine, everything work from the box, I am surprised that even the wireless not a problem and it has a decent speed too.

**The problem is:** I want to install **Lubuntu Control Center**; I downloaded the program and saved it in the downloads Folder, then I try to install it with Synaptic , it recognized but the install button is shaded, then I figure that maybe I can installed from Terminal, I tried, but I probably didn't do it right, so nothing happened,... can somebody help me with this one please......... I basically don't know the commands.....and the how to... 

Thanks in advance
Carl

---

### Post by wolfen69 on 2011-11-16
From what I gather, it is only compatible with older versions of lubuntu.

---

### Post by robro on 2011-11-16
The command to install from the terminal is:
sudo dpkg -i packagename.deb
It will ask for your password but nothing will show, just type it as usual and see if it works :)

---

### Post by Carlzam on 2011-11-16
```
Thanks for your response; I tried the command in two ways, but didn't work, even that the package was just there in the desktop, here is what I did:

carlzam@carlzam-laptop:~$ sudo dpkg -i lubuntu-control-center.deb
[sudo] password for carlzam: 
dpkg: error processing lubuntu-control-center.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lubuntu-control-center.deb
carlzam@carlzam-laptop:~$ sudo dpgk -i lubuntu-control-center.deb
sudo: dpgk: command not found
carlzam@carlzam-laptop:~$ sudo apt-get install  lubuntu-control-center.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lubuntu-control-center.deb
E: Couldn't find any package by regex 'lubuntu-control-center.deb'
carlzam@carlzam-laptop:~$ 


```> **robro said:**
> The command to install from the terminal is:
sudo dpkg -i packagename.deb
It will ask for your password but nothing will show, just type it as usual and see if it works :)

---

### Post by SteveDee on 2011-11-17
...as wolfen69 says, there may be a compatibility problem, but one last chance:-
 - Use file manager to navigate to the deb file you downloaded in the Downloads folder.
 - Right-click on the file and select GDebi Package Installer and install (make sure Synaptic is not also open at the same time).

---

### Post by beew on 2011-11-17
Install it from ppa

[https://launchpad.net/~lubuntu-desktop/+archive/ppa]("https://launchpad.net/%7Elubuntu-desktop/+archive/ppa")

Opps, sorry, it seems that the LCC in the ppa only goes up to 11.04.

---

### Post by beew on 2011-11-17
> **Carlzam said:**
> Thanks for your response; I tried the command in two ways, but didn't work, even that** the package was just there in the desktop**, here is what I did:
```

carlzam@carlzam-laptop:~$ sudo dpkg -i lubuntu-control-center.deb
[sudo] password for carlzam: 
dpkg: error processing lubuntu-control-center.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lubuntu-control-center.deb


```

You were in the wrong directory when you ran the dpkg command. You have to either cd (= change directory) into the directory where the .deb is (Desktop in this case) or enter its full path (Desktop/lubuntu-control-center.deb) when running the dpkg command.  (You are in the /home/carlzam/ directory by default when you start the terminal, so instead of /home/carlzam/Desktop or ~/Desktop just Desktop would do)

Since you saved the .deb file on the desktop, you have to do

```
cd Desktop
sudo dpkg -i lubuntu-control-center.deb
```Notice the capital D

But you can also install .deb  files by right clicking if you have installed gdebi
```

sudo apt-get install gdebi
```

---

### Post by Carlzam on 2011-11-17
```
I tried first with the GDebi installer but the install button is shaded, then I tried with Terminal and this is what I got:
carlzam@carlzam-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
carlzam@carlzam-laptop:~$ cd Desktop
carlzam@carlzam-laptop:~/Desktop$ sudo dpkg -i lubuntu-control-center.deb
[sudo] password for carlzam: 
Selecting previously deselected package lubuntu-control-center.
(Reading database ... 107807 files and directories currently installed.)
Unpacking lubuntu-control-center (from lubuntu-control-center.deb) ...
dpkg: dependency problems prevent configuration of lubuntu-control-center:
 lubuntu-control-center depends on python (<< 2.7); however:
  Version of python on system is 2.7.2-7ubuntu2.
dpkg: error processing lubuntu-control-center (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 lubuntu-control-center
carlzam@carlzam-laptop:~/Desktop$ 


```> **beew said:**
> You were in the wrong directory when you ran the dpkg command. You have to either cd (= change directory) into the directory where the .deb is (Desktop in this case) or enter its full path (Desktop/lubuntu-control-center.deb) when running the dpkg command.  (You are in the /home/carlzam/ directory by default when you start the terminal, so instead of /home/carlzam/Desktop or ~/Desktop just Desktop would do)

Since you saved the .deb file on the desktop, you have to do

```
cd Desktop
sudo dpkg -i lubuntu-control-center.deb
```Notice the capital D

But you can also install .deb  files by right clicking if you have installed gdebi
```

sudo apt-get install gdebi
```

---

### Post by Carlzam on 2011-11-17
I checked this option and it say 11.10, I tried to run it from Terminal with the commands shown following the instructions there but then got too complicated for me, there is another way to  do do it  there but it is out of my league.
  > **beew said:**
> Install it from ppa

[https://launchpad.net/~lubuntu-desktop/+archive/ppa]("https://launchpad.net/%7Elubuntu-desktop/+archive/ppa")

Opps, sorry, it seems that the LCC in the ppa only goes up to 11.04.

---

### Post by wolfen69 on 2011-11-17
It is not available for your version of ubuntu. It may be soon, but not right now.

---

### Post by beew on 2011-11-17
It seems that it is not available for your release (11.10) if you couldn't install with gdebi (and the ppa doesn't offer a version for 11.10)  It is probably not ready and will be available in the ppa eventually, so wait a bit keep an eye on the ppa (use the filter in the web site, set it to Oneiric and then see what packages are displayed, right now the lubuntu-control-center is not there)

---

