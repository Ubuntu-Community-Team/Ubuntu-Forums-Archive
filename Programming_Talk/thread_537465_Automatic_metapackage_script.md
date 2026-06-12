---
title: "Automatic metapackage script"
date: 2007-08-28
forum: Programming Talk
---

### Post by hammer v2 on 2007-08-28
Hey Guys, I'm working on a program to create install shield installation files for ubuntu. I'm almost finished but I need a hand with a bash script. If someone could help me out here, I'd be very grateful!

I need a bash script that creates a metapackage dependant on all the packages located in /var/apt/cache


This can't be that hard, I'd do it but I'm so new to this, only been scripting for 2 weeks. Any help here would be wonderful!!

Hope you're having a good day.
H.

---

### Post by nanotube on 2007-08-29
> **hammer v2 said:**
> Hey Guys, I'm working on a program to create install shield installation files for ubuntu. I'm almost finished but I need a hand with a bash script. If someone could help me out here, I'd be very grateful!

I need a bash script that creates a metapackage dependant on all the packages located in /var/apt/cache


This can't be that hard, I'd do it but I'm so new to this, only been scripting for 2 weeks. Any help here would be wonderful!!

Hope you're having a good day.
H.

well, i don't know exactly what you are doing there, but the first step would clearly be to get a list of all the packages. so...
```
ls -1 /var/cache/apt/archives |awk -F_ '{print $1}'
```
will give you a list of the package names (stripped of all extraneous info like versions, etc).

once you have that, you can do whatever you want with it with regard to putting them in as dependencies for your metapackage, etc.

---

### Post by hammer v2 on 2007-08-29
-------------------
#!/bin/bash
# MAKE AN INSTALL SCRIPT SCRIPT
# Hamish's convert's deb files to self extracting gz files. 
# bundles the desired deb and all it's dependancies together.

gksudo -k /bin/echo "login der"

sudo mkdir /tmp/setupfiles

sudo rm -f /var/cache/apt/archives/*.deb

sudo 
yes | sudo apt-get update

zenity --info \
          --text="Please choose the packages to include in your setup file"

sudo synaptic

#### HELP!! Up to this point, it's all going swimingly But I now need some way to create a metapagkage that is dependant on all the files now in /var/cache/apt/archives

sudo mv -f /var/cache/apt/archives/*.deb /tmp/setupfiles/Packages

#### HELP!! Now I need to create a local apt repository 

#Copy sources.list with only /tmp/setup as local repository
# /tmp/setup is where finished installer will uncompress the 
# repository to.

sudo cp ~/installerconverter/sources.list /tmp/setupfiles/sources.list

#copy the setup script

sudo cp ~/installerconverter/install.setup /tmp/setupfiles/install.setup

#Use makeself.sh to bundle everything together
Makeself.sh..blah blah :)
--------------------------------

This is kinda what I'm trying to do here. The idea is that when you run the script synaptic appears where you download the programs + dependancies.

Then the script makes a metapackage of everything that synaptic just downloaded, before moving it all to a tmp directory and creating an APT repository

Then a clean sources.list file is added as well as the install script and the whole lot is bundled together using makeself.

The idea is if this script is run on a clean install (live cd?) f ubuntu feisty then it should create a file that can be installed on any  ubuntu feisty install. The file can be transferred via memory stick or bundled on a CD and given to your firends who may not have internet.


Here's the a copy of a finished INSTALL script - this one is tested and works great

#!/bin/bash
# Hamish's setup script

gksudo -k /bin/echo "login der"

sudo mkdir /tmp/setup

sudo cp -r *.* /tmp/setup

sudo cp -r ./packages -d /tmp/setup/

# cd /tmp/setup

# sudo dpkg-scanpackages ./dev/null | sudo gzip -9c > /tmp/setup/Packages.gz

sudo mv -f /etc/apt/sources.list /etc/apt/sources.list.bak

sudo mv -f /etc/apt/sources.list.d /etc/apt/sources.list.d.bak

sudo cp sources.list -t /etc/apt/

# sudo yes | sudo apt-cdrom add /dev/cdrom 

sudo apt-get update

yes | sudo apt-get install aptoncd-metapackage

sudo mv -f /etc/apt/sources.list.bak /etc/apt/sources.list

sudo mv -f /etc/apt/sources.list.d.bak /etc/apt/sources.list.d

zenity --info \
          --text="Setup Completed. You can now run the program from the applications menu"

exit 1
fi

I could really do with some feedback here guys. Is my idea any good? I'm new to scripting so feel free to chime in here with pointers.


I've got a version of scribus here that I manually made using the above process if anyone wants to try it on their system.
Send me an email robertsonhamish at gmail dot com and I'll swing you a copy (17meg!)
H.

---

