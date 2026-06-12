---
title: "Trying to install MATLAB for Ubuntu... help?"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by Ephemeralmemory on 2012-02-01
I downloaded Matlab for Linux though the university I work for, (I have the license and installation key through the University) and I have the iso archive downloaded. I unzipped the iso and tried to run the installer through the command line, but I think I used the wrong command.

In the iso archive, there was a "installer" autorun file but I don't know how to access it through the command line. Is there a easy way to do this? 

Here is my terminal output:

brian@brian-System-Product-Name:~$ cd Downloads/
brian@brian-System-Product-Name:~/Downloads$ sudo sh install
Preparing installation files ...
Installing ...
eval: 1: /tmp/mathworks_20054/java/jre/glnxa64/jre/bin/java: Permission denied
Finished

Thanks for all your help!!

---

### Post by BeRoot ReBoot on 2012-02-01
See here: [http://www.mathworks.com/support/solutions/en/data/1-9VXDYZ/](http://www.mathworks.com/support/solutions/en/data/1-9VXDYZ/)

---

### Post by Ephemeralmemory on 2012-02-03
Thanks for helping, but I still have a permissions problem.

Every time I try to install, I get the same Permission denied error. Just out of curiosity, do you know why I would get a permissions error?

This is my new terminal output:

brian@brian-System-Product-Name:~$ cd Downloads/
brian@brian-System-Product-Name:~/Downloads$ ls
activate.ini  etc      installer_input.txt   java         R2010b_UNIX.iso
archives      help     InstallForMacOSX.app  license.dat  readme.txt
bin           install  install_guide.pdf     license.txt  version.txt
brian@brian-System-Product-Name:~/Downloads$ ./install.sh -t
bash: ./install.sh: No such file or directory
brian@brian-System-Product-Name:~/Downloads$ sudo sh ./install -t
[sudo] password for brian: 
Preparing installation files ...
Installing ...
eval: 1: /tmp/mathworks_2116/java/jre/glnxa64/jre/bin/java: Permission denied
Finished
brian@brian-System-Product-Name:~/Downloads$ sudo sh install -t
Preparing installation files ...
Installing ...
eval: 1: /tmp/mathworks_2147/java/jre/glnxa64/jre/bin/java: Permission denied
Finished
brian@brian-System-Product-Name:~/Downloads$

---

### Post by Ephemeralmemory on 2012-02-03
Scratch that, I know my problem. I can only use a silent installer for 2010b, apparently, I'll get the 2010a version through my uni.

Thanks for helping me!

---

