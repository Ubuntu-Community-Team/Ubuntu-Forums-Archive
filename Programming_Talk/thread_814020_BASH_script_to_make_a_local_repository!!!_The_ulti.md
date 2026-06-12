---
title: "BASH script to make a local repository!!! The ultimate .deb script"
date: 2008-05-31
forum: Programming Talk
---

### Post by hammer v2 on 2008-05-31
Hey guys, 
I'm completely newto programing. I'm totally crap at it, but I'm ploughing away at a BASH script cause I believe that I have a really good idea.

I'm making a script that downloads a deb plus all it's dependancies and packages it up into an executable archive with a metapackage. The user simply clicks on the "setup" file and the program installs....without the internet.

anyway I've pieced together a small script that does just about everything I need. But I'm having trouble creating a local apt repository.

Can someone help out here? This script currently works (I'm more amazed than you) but I just can't get the metapackage to install the dependancies. My repository is incorrect. HELP!!!

Here's my crusty script

l#/bin/bash
# MAKE AN INSTALL SCRIPT SCRIPT

gksu -k /bin/echo "login der"

sudo mkdir /tmp/setupfiles

sudo rm -f /var/cache/apt/archives/*.deb

#sudo yes | sudo apt-get update

sdebname=$(zenity --text "Please enter a one-word name for your superdeb." --entry)

zenity --info \
--text="Please choose the packages to include in your setup file. When you have finished downloading your packages, please exit Synaptic to continue."

sudo synaptic
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

##Control file is made! Yay! Now just have to make it into a .deb file
cd /tmp/setupfiles/
sudo dpkg-deb -b --nocheck $sdebname

#in theory I should now have a metapackage! <CONFIRMED>

#Now to make a repository

 cd /var/cache/apt/archives 
sudo cp *.deb /tmp/setupfiles
sudo -i
cd /tmp/setupfiles/


	sudo ls -1 *.deb > override

	# create a package file
	dpkg-scanpackages ./ override | gzip > Packages.gz
	
mkdir /tmp/setupfiles/packages
sudo cp *.deb /tmp/setupfiles/packages

---

### Post by abhiroopb on 2008-05-31
Have you looked into: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by hammer v2 on 2008-05-31
Yup! sure have! apt-on cd is a great program.. but too complicated for my target audience here. I want 1 file that the user double clicks to install a program.

---

### Post by madjr on 2008-06-01
hi hammer v2,

i just read your post in my thread and this is very interesting (subscribed).

count me in with the research and testing :)

oh and you may want to look at **nonetdebs**

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

it's similar but he uses terminal instead of zenity (zenity frontend is easier for new users)

if we all work at this we can have a great solution very soon!

aptoncd is already great for sharing "**ubuntu updates**"

now sharing .debs like .exes in windows will be just as easy :)

and even better with the integration with our package-manager (something windows lacks)

Ubuntu will be the ultimate OS for anyone (with or without internet). Many millions of people will benefit.

---

