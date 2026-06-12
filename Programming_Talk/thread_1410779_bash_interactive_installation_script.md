---
title: "bash interactive installation script"
date: 2010-02-19
forum: Programming Talk
---

### Post by Softsmid on 2010-02-19
Hi, for an exercise I need to write a script that will ask the user about each package in a (local) repository and install it or not according to the user's input.

I am fairly new to scripting, so I did not get very far. Here is what I came up with. I really appreciate your help.


```
#!/bin/bash 
#Checks if you are root or not 
if test "`id -u`" -ne 0
	then 
	echo "You need to run this script as root!" 
	exit 
fi
#here needs to start a loop that lists all the packages like dpkg -l does one for one and
#asks for user input. I got as far as the code below. But the script does not stop yet to ask
#after every file, any suggestions?
for pkg in `dpkg -l`
do
	echo Found package: $pkg
done
		echo "Do you wish to install $pkg ?"
		select yn in "Yes" "No"
		do
		    case $yn in
		        Yes ) apt-get -d install $apl; break;;
		        No ) exit;;
		    esac
		done
	# continue...

```

---

