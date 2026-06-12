---
title: "Can't use Mono to run a windows application anymore"
date: 2019-03-05
forum: New to Ubuntu
---

### Post by tackskull on 2019-03-05
Hi there,

antill yesterday I was able to run  an windows program called iso2god via Mono runtime. But after my pc encountered a bug (I am using kubuntu18.10), that was avoiding me to update the distro (issue now solved), mono runtime doesn't read the .exe file anymore. Why? Can you guys help me?

edit: I found a program that does the same thing for linux. Is called xipper but is a .deb file and I cannot install it on ubuntu (is a .deb package, I tried also to install it via software center by right clicking the file and clicking on software install, but once I install it just nothing happen and the "install" button reappear.)

---

### Post by Holger_Gehrke on 2019-03-05
The only xipper I can find for Ubuntu is a [discontinued project from 2012 by Red Squirrel]("http://redsquirrel87.altervista.org/doku.php/xipper") (and I can't find the .deb-download on that site, so if it's the same program you probably found the download somewhere else). This is just a GUI for extract-xiso (discontinued 2006, available from sourceforge.net) and needs Gambas libraries in rather specific versions. I think your chances of getting this to run are very slim. To get a better idea why the installation fails you can try to run 'sudo apt  install "put-the-path-and-name-of-the-deb-file-here"' (substitute the obvious and **do** put a path, even if the file is in the current working directory; apt will try to get the package from the repositories (which don't have it ...) unless an explicit path is given) in a terminal. This will try to install the dependencies of the package and the package itself and tell you what fails.

Holger

---

### Post by tackskull on 2019-03-06
Thanks for your reply Holger.

I get this on terminal:

tackskull@tackskull-Aspire-5552G:~$ sudo apt install /desktop/Xipper_2.0-1_i386.deb
[sudo] password for tackskull: 
Reading package lists... Done
E: Unsupported file /desktop/Xipper_2.0-1_i386.deb given on commandline

Maybe I can make Mono working again somehow? Is strange before was working well runni iso2god and now not working anymore

---

### Post by Impavidus on 2019-03-06
I doubt that's the correct path to the file. I guess it's```
sudo apt install ~/Desktop/Xipper_2.0-1_i386.deb
```
But it may be better to get mono working. When you try running the .exe with mono, do you get an error message? Most error messages on Linux are useful.

---

### Post by tackskull on 2019-03-06
This is what I get

```
tackskull@tackskull-Aspire-5552G:~$ sudo apt install ~/Desktop/Xipper_2.0-1_i386.deb
[sudo] password for tackskull: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xipper:i386' instead of '/home/tackskull/Desktop/Xipper_2.0-1_i386.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xipper:i386 : Depends: gambas3-gb-form:i386 (>= 3.1.1) but it is not installable
               Depends: gambas3-gb-gtk:i386 (>= 3.1.1) but it is not installable
               Depends: gambas3-gb-image:i386 (>= 3.1.1) but it is not installable
               Depends: gambas3-runtime:i386 (>= 3.1.1) but it is not installable
E: Unable to correct problems, you have held broken packages.

```


When I right click iso2god I click on "run with mono", at first Mono looks like to do some stuff but immediately crush without giving any error message

---

### Post by Impavidus on 2019-03-06
Have you tried running it from the command line? I think it's```
mono filename.exe
```If the file is not in the current directory, provide the path as appropriate.

---

### Post by tackskull on 2019-03-06
I solved the problem. I don't know what was the problem but I found this terminal code on the internet:  sudo apt-get install mono-complete 

After a long install now mono work grate. Thanks you guys for the support :)

---

