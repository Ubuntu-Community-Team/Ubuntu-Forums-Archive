---
title: "BASH script HELP!!!"
date: 2008-09-03
forum: Programming Talk
---

### Post by hammer v2 on 2008-09-03
Hey guys,
firstly...I am NOT a programmer! I had a cool idea for making software easier to install and the only way I could pieve something together was using BASH. Anyway...I've almost finished it, except I'm having trouble inserting a variable into a text file...it seems as if my variable dissapears from memory halfway down the script. anyone got any ideas?
(Excuse the crappy programming...:P)

Here's the script;
l#/bin/bash
# MAKE AN INSTALL SCRIPT SCRIPT
# Hamish's convert's deb files to self extracting gz files.
# bundles the desired deb and all it's dependancies together.

gksu -k /bin/echo "login der"

sudo mkdir /tmp/setupfiles

#sudo rm -f /var/cache/apt/archives/*.deb

#sudo yes | sudo apt-get update

sdebname=$(zenity --text "Please enter a one-word name for your superdeb." --entry)

#zenity --info \
--text="Please choose the packages to include in your setup file. When you have finished downloading your packages, please exit Synaptic to continue."

#sudo synaptic
#Synaptic has now finished
#Make a directory for the metapackage

sudo mkdir -p /tmp/setupfiles/$sdebname/DEBIAN
# Now we need to clear the control file if there is a pre-existing control file
sudo rm -f /tmp/setupfiles/$sdebname/DEBIAN/control
cd /tmp/setupfiles/$sdebname/DEBIAN
#Make a new (and empty) control file
sudo touch control
sudo chmod 666 control
#start filling in the fields

#Insert package name into control file
sudo echo "Package: "$sdebname >> control
#insert version no... in this case it's always 1.0
sudo echo "Version: 1.0" >> control
#insert section
sudo echo "Section: unknown" >> control
#insert Priority
sudo echo "Priority: optional" >> control
#insert Maintainer
sudo echo "Maintainer: Superdeb! <superdeb@superdeb.org>" >> control
#insert Architechture
sudo echo "Architecture: i386" >> control
#insert list of dependancies
cd /var/cache/apt/archives/
## Rob's perl listing script. (Thanks Rob!!)
DEPLIST=$(perl -e 'print join(", ", map { s/.deb$//; $_ }
split("\n", `ls *.deb`)), "\n";')
cd /tmp/setupfiles/$sdebname/DEBIAN
sudo echo "Depends: "$DEPLIST >> control
#Metapackage Description
sudo echo "Description: This is the metapackage used to install "$sdebname  >> control
#Control file doesn't work yet - NEED to remove _ndjdkkf_i386 after each filename...HELP!!'
## I got help! Thanks Nicholas!! :)
sudo cp ~/caca.pl /tmp/setupfiles/$sdebname/DEBIAN
sudo perl caca.pl
##Control file is made! Yay! Now just have to make it into a .deb file
cd /tmp/setupfiles/
sudo dpkg-deb -b --nocheck $sdebname

#in theory I should now have a metapackage! <CONFIRMED>

#Now to make a repository
sudo mkdir install
sudo cp /var/cache/apt/archives/*.deb /tmp/setupfiles/install
sudo cp $sdebname.deb /tmp/setupfiles/install
cd /tmp/setupfiles/install
sudo -su
sudo dpkg-scanpackages . /dev/null | sudo gzip -9c > Packages.gz
#repository created! <CONFIRMED>

#TEST REPO - <CONFIRMED>
#create install script - USE MAKESELF
sudo touch setupscript.sh
echo "#! /bin/bash" >> setupscript.sh
echo "gksudo -k" >> setupscript.sh
echo "sudo mkdir /tmp/setupfiles" >> setupscript.sh
echo "sudo cp -r *.* /tmp/setup/setupfiles" >> setupscript.sh
echo "sudo cp -r ./install -d /tmp/setupfiles/" >> setupscript.sh
echo "sudo mv -f /etc/apt/sources.list /etc/apt/sources.list.bak" >> setupscript.sh
echo "sudo mv -f /etc/apt/sources.list.d /etc/apt/sources.list.d.bak" >> setupscript.sh
echo "sudo cp sources.list -t /etc/apt/" >> setupscript.sh
echo "sudo yes | sudo apt-get update" >> setupscript.sh
echo "yes | sudo apt-get install $sdebname" >> setupscript.sh
echo "sudo mv -f /etc/apt/sources.list.bak /etc/apt/sources.list" >> setupscript.sh
echo "sudo mv -f /etc/apt/sources.list.d.bak /etc/apt/sources.list.d" >> setupscript.sh
echo "zenity --info /" >> setupscript.sh
echo '--text="Setup Completed. You can now run the program from the applications menu"' >> setupscript.sh
echo "exit 1" >> setupscript.sh
echo "fi" >> setupscript.sh

#install script created!
cp ~/sources.list /tmp/setupfiles/install
#Bundle everything into one executable file with makeself.
cp ~/makeself-2.1.4/*.* /tmp/setupfiles
cd /tmp/setupfiles
./makeself.sh --bzip2 /tmp/setupfiles/install TEMPFILE "This package was created with superdeb. Started by Hamish Robertson" ./setupscript.sh
sudo mv -f TEMPFILE $sdebname-UB0710.sdeb
sudo chmod a+x $sdebname-UB0710.sdeb
sudo cp $sdebname-UB0710.sdeb ~/Desktop/

---

### Post by hyper_ch on 2008-09-03
(1) you should use [noparse]```

```[/noparse] brackets around when you put some output or code

(2) you should also disable smileys as they interfere

---

### Post by ajgreeny on 2008-09-03
Are you sure the first line is correct?
```
l#/bin/bash
```Shouldn't that be 
```
#!/bin/bash
```

---

