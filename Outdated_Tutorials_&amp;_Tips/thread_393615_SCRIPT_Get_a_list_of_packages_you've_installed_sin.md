---
title: "SCRIPT: Get a list of packages you've installed since the initial installation"
date: 2007-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by bruenig on 2007-03-25
With feisty coming up, those who prefer to fresh install may want to know all the packages you have installed yourself outside of the base installation to allow you to pick up very quickly where you left off. 

I have created this script, that works in ubuntu, xubuntu, and kubuntu that allows you to do that. It not only allows you to pair down the installed packages to the one's you added yourself, but also allows you the choice to omit libraries (seeing as those are generally dependencies) as well as the choice to omit the long list of kernel and module versions that have likely been installed and allows you to output the package list to a file.

The script works by amassing a long list of packages using timestamps as well as using the core meta packages and then removing those packages from the list of installed packages.

To use this script, make sure you are in the home directory and do the following: (make sure word wrap is turned off by the way)
```
gedit user_installed_packages # or use kate for kde and mousepad for xfce
```
Then copy and paste the script:
```
#!/bin/bash

#Ask for version to set DESKTOP
while [ "$answer" != "ubuntu" -a "$answer" != "kubuntu" -a "$answer" != "xubuntu" ]; do 
	echo "Was your install cd ubuntu, kubuntu, or xubuntu (type out exactly)?"
        read answer
done

#Get the installed packages
INSTALLED_PACKAGES=$(dpkg --get-selections | grep -v deinstall | awk '{print $1}')

#Get date of minimal and use that to find untouched packages
INSTALL_DATE=$(ls -l /var/lib/dpkg/info | grep ubuntu-minimal.list | awk '{print $6}')
BASE_PKG=$(ls -l /var/lib/dpkg/info | grep $INSTALL_DATE | awk '{print $8}' | sed 's/.list//g')

#Get the dependencies of the meta packages used during install
STANDARD=$(apt-cache show ubuntu-standard | grep -E ^Depends | sed 's/^Depends: //' | \
sed 's/, /\n/g' | sed 's/ | /\n/g')
MINIMAL=$(apt-cache show ubuntu-minimal | grep -E ^Depends | sed 's/^Depends: //' | \
sed 's/, /\n/g' | sed 's/ | /\n/g')
DESKTOP=$(apt-cache show $answer"-desktop" | grep -E ^Depends | sed 's/^Depends: //' | \
sed 's/, /\n/g' | sed 's/ | /\n/g')

#Set up the grep strings (what a stupid way to do this)
GREP_STRING=$(for x in $(echo $BASE_PKG) $(echo $STANDARD) $(echo $MINIMAL) \
$(echo $DESKTOP) ; do echo "$x|" ; done)
CLEAN_GREP=$(echo $GREP_STRING | sed 's/\ //g' | sed "s/|$/\'/" | sed "s/^/\'/")

# Find the new packages and setup nolib
NEW_PACKAGES=$(echo "$INSTALLED_PACKAGES" | grep -Evw $CLEAN_GREP)
NOLIB=$(echo "$NEW_PACKAGES" | grep -Ev ^lib)

# Ask for libraries or no libraries, kernel or no kernel, and output file or not
while [ "$choice" != "y" -a "$choice" != "n" ]; do 
	echo "Include libraries in the results (y/n)?"
        read choice
done

if [ "$choice" = "y" ] ; then
	OUTPUT=$(echo "$NEW_PACKAGES")
else
	OUTPUT=$(echo "$NOLIB")
fi

while [ "$response" != "y" -a "$response" != "n" ]; do 
	echo "Include every version of the kernels and modules that you have installed (y/n)?"
        read response
done

if [ "$response" = "n" ] ; then
	OUTPUT=$(echo "$OUTPUT" | grep -Ev '^linux-headers-2|^linux-image-2|^linux-restricted-modules-2')
fi

while [ "$input" != "y" -a "$input" != "n" ]; do 
	echo "Do you want to output the package list to a text file (y/n)?"
        read input
done

if [ "$input" = "n" ] ; then
	echo "$OUTPUT"
else
	echo -e "What should the name of the file be?\n(Make sure you can write \
to it and make sure the path exists)"
	read file
	if [ "${file%%/*}" = "~" ] ; then
		file="/home/$USER$(echo $file | sed 's/~//')"
	fi
echo "$OUTPUT" > $file
fi
exit
```
Save and exit, then 
```
chmod +x user_installed_packages
```
To run it then
```
./user_installed_packages
```

Just follow the prompts and you should get what you want.

Note: this is not 100% perfect, a few packages can slip by that were part of the base installation, but generally that is maybe 3-4.

---

### Post by klytu on 2007-03-31
A friend of mine mentioned this post to me. Great idea and great script! I am surprised it didn't get more attention.

Incidentally, when I ran this it seems the installed package list that generated included some packages that I had installed and then later removed.  Was that intended?

---

### Post by bogolisk on 2007-03-31
how about:

```

dpkg --get-selections
dpkg --get-selections | grep -E '\<install$'
dpkg --get-selections | grep -E '\<install$' | cut -f 1

```

---

### Post by bruenig on 2007-03-31
> **klytu said:**
> A friend of mine mentioned this post to me. Great idea and great script! I am surprised it didn't get more attention.

Incidentally, when I ran this it seems the installed package list that generated included some packages that I had installed and then later removed.  Was that intended?

Hmmm, that does appear to happen. I never even considered that. I just assumed that those things would be gone. Such a thing can be fixed though. I have changed the script above.

---

### Post by kvonb on 2007-04-01
Nice one, I really needed something like this because I setup a mail server and forgot all the packages I installed.  Saved me a heap of time, thanks :).

---

### Post by klytu on 2007-04-01
> **bruenig said:**
> Hmmm, that does appear to happen. I never even considered that. I just assumed that those things would be gone. Such a thing can be fixed though. I have changed the script above.

Nice job! It was also educational for me to read through your scripts. Thanks!

---

### Post by tabinin on 2007-04-06
This script is awsome!  Thank you.  I like that it asks you if you want the libraries included.  I figured that dependancies will install the ones I need along the way.

---

### Post by Bill Statler on 2007-04-22
Thanks, this is exactly what I was looking for.  It'll be a *big* help with a fresh install.

[This wiki page]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion") has a section on "Clean install with /home on separate partition".  Maybe your script should be part of this.

---

### Post by martinw89 on 2007-04-22
Very nice script, thank you for putting your time into this.  Thanks :)

---

### Post by timmie on 2007-04-30
Hi,
your script is very nice.

It would be good to have a version that doesn't need user feedback and then could be put to *cron.daily*

---

### Post by bruenig on 2007-05-01
> **timmie said:**
> Hi,
your script is very nice.

It would be good to have a version that doesn't need user feedback and then could be put to *cron.daily*

That shouldn't be hard, I don't know what you want though. Simply follow the logic of the script figure out what your choices are and then where it says If [ answer = yes ] or whatever, if your answer is yes, just keep that part of the script.

---

### Post by dimeotane on 2008-09-13
thanks for writing this.... I was wanting something like this , instead of reinstalling all my packages with a fesh install, I wanted to eliminate most of the garbage and just wanted a printout of the user added packages to look over.  However I found that this script didn't output quite a few packages that I'd installed.  I couldn't rely on this script's output for my reinstall.  I still am looking over my system application menu trying to figure out what I 've got installed.   Maybe a second write of this script is needed?

---

