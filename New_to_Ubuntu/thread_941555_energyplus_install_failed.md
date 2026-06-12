---
title: "energyplus install failed"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by anantyk on 2008-10-08
dear Friends

I have been struggling with trying to install a energy simulation software called EnergyPlus, Repeatedly getting the errors I have pasted below.

Somebody from energy plus support sent a solution which I have pasted at the bottom but I am not in a position to make sense of it. Please help

kjit@energytrac:~$ cd EnergyPlusV220/install
kjit@energytrac:~/EnergyPlusV220/install$ dir
energyplusenv.csh0 install.sh instfils.lis
energyplusenv.sh0 instdirs.lis uninstall.sh
kjit@energytrac:~/EnergyPlusV220/install$ chmod +x install.sh
kjit@energytrac:~/EnergyPlusV220/install$ ./install.sh
#############################################
#### Find Operating System version etc...
#############################################
#### Find ENERGYPLUS_DIR :
./.setup.sh: 36: pushd: not found
./.setup.sh: 38: popd: not found
#### EnergyPlus directory is /home/kjit/EnergyPlusV220/install
#### Check writability of /home/kjit/.cshrc , .profile , .bash_profile
#############################################
######## Check for install , uninstall
#############################################
#### Install EnergyPlus at directory /home/kjit/EnergyPlusV220/install
#### Write energyplusenv.csh , energyplusenv.sh
#### Modify .cshrc , .profile , .bash_profile
#############################################
# To update your environment variables, you #
# need to log in your system again. #
#############################################
cp: cannot create regular file `install/profile.beforeEnergyPlus': No such file or directory
./.setup.sh: 201: cannot create install/instfils.lis: Directory nonexistent
#############################################
#### Install done.
#############################################
kjit@energytrac:~/EnergyPlusV220/install$


Message from EnergyPlus support team:

I just isntalled EnergyPlus v2.2.0 for linux on Kubuntu (Ubuntu) 8.04 Hardy
Heron. The installation script, .setup.sh, by virtue of its first line:

#! /bin/sh

is executed via /bin/sh. On Ubuntu systems, /bin/sh is a symlink to dash, a
shell that doesn't implement the pushd and popd commands, among other things.
Correspondingly, on Ubuntu, the ENERGYPLUS_DIR environment variable is set
to "<somepath>/EnergyPlusV220/install" instead of the
correct "<somepath>/EnergyPlusV220".

One possible solution might be to change install.sh to purposefully exec via
bash if bash is available, something like:

BASH=$(which bash)
if [ -x "$BASH" ]; then
exec "$BASH" .setup.sh install
else
exec .setup.sh install
fi
echo "Failed to exec the setup program" >&2
exit 1

---

### Post by handydan918 on 2008-10-08
> I just isntalled EnergyPlus v2.2.0 for linux on Kubuntu (Ubuntu) 8.04 Hardy
Heron. The installation script, .setup.sh, by virtue of its first line:

#! /bin/sh

is executed via /bin/sh. On Ubuntu systems, /bin/sh is a symlink to dash, a
shell that doesn't implement the pushd and popd commands, among other things.
Correspondingly, on Ubuntu, the ENERGYPLUS_DIR environment variable is set
to "<somepath>/EnergyPlusV220/install" instead of the
correct "<somepath>/EnergyPlusV220".

One possible solution might be to change install.sh to purposefully exec via
bash if bash is available, something like:

BASH=$(which bash)
if [ -x "$BASH" ]; then
exec "$BASH" .setup.sh install
else
exec .setup.sh install
fi
echo "Failed to exec the setup program" >&2
exit 1

The script above seems to try to locate bash, set it as the default shell for the purposes of the install script, and then run the install script, but fail if no bash. 

seems like you have a couple of options here. 
I'm not in front of an Ubu box at the moment, but if you do ```
which bash
```it will tell you the location of the bash shell. If it is not installed, you could install it via ```
sudo apt-get install bash
```
Then you could either change the opening line on the script from ```
#!/bin/sh
```
to 
```
#!/bin/bash
```
Good luck!

---

### Post by anantyk on 2008-10-10
dear friend

I tried changing the first line in "istall.sh" file from

"#! bin/sh" to "#! bin/bash"

but got the same error again, terminal window output appended below;

kjit@energytrac:~/EnergyPlusV220/install$ chmod +x install.sh
kjit@energytrac:~/EnergyPlusV220/install$ ./install.sh
#############################################
#### Find Operating System version etc...
#############################################
#### Find ENERGYPLUS_DIR :
/home/kjit/EnergyPlusV220/install/.setup.sh: 36: pushd: not found
/home/kjit/EnergyPlusV220/install/.setup.sh: 38: popd: not found
#### EnergyPlus directory is /home/kjit/EnergyPlusV220/install
#### Check writability of /home/kjit/.cshrc , .profile , .bash_profile
#############################################
######## Check for install , uninstall
#############################################
#### Install EnergyPlus at directory /home/kjit/EnergyPlusV220/install
#### Write energyplusenv.csh , energyplusenv.sh
#### Modify .cshrc , .profile , .bash_profile
#############################################
# To update your environment variables, you #
# need to log in your system again.         #
#############################################
cp: cannot create regular file `install/profile.beforeEnergyPlus': No such file or directory
/home/kjit/EnergyPlusV220/install/.setup.sh: 201: cannot create install/instfils.lis: Directory nonexistent
#############################################
#### Install done. 
#############################################
kjit@energytrac:~/EnergyPlusV220/install$ 


do I need to make other changes in the "install.sh" file??

---

### Post by handydan918 on 2008-10-11
```
which bash
```

?

---

