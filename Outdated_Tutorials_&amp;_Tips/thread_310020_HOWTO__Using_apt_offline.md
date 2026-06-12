---
title: "HOWTO : Using apt offline"
date: 2006-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Skippy le Grand Gourou on 2006-11-30
Hi,

Tired for waiting my internet connection, and as many people ask for how to do it, I wrote a little script to allow the use of apt-get offline. The main advantage in comparison to the real apt-offline tool (which I didn't try :-# ) is that it doesn't need to have apt on the connected computer (ie you can download packages from a rpm-based distribution, for instance).

Here it is, just copy this code in your favorite text editor, save it as **apt-off** on your usb flash/hard drive (or any other kind of mobile disk) and make it executable by typing **chmod +x apt-off** in a terminal.

```
#!/bin/bash
#
# Copyright 2006, Goulven Guillard.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

BOLD="\\033[1;39m"
NORMAL="\\033[0;39m"
GREEN="\\033[32m"
RED="\\033[31m"
PINK="\\033[35m"
BLUE="\\033[34m"


##################
## Display help	##
##################
if [[ $1 == -h || $1 == --help ]]; then
	echo -e "\\033[2J\\033[0;0f$BOLD$BLUE""NAME"$NORMAL
	echo -e "\tapt-off\n"
	echo -e $BOLD$BLUE"SYNOPSIS"$NORMAL
	echo -e $GREEN"\tapt-off [option] [packages/dist-upgrade]\n"$NORMAL
	echo -e $BOLD$BLUE"DESCRIPTION"$NORMAL
	echo -e "\t$GREEN""apt-off$NORMAL is a script designed to allow the use of the apt tool on a"
	echo -e "\tcomputer without any network connection. It proceeds in three steps,"
	echo -e "\twhich must be done in the directory containing the apt-off file :"
	echo -e "\t1- packages selection (option -g)"
	echo -e "\t2- packages download (option -d); this step has to be done on a Linux"
	echo -e "\tsystem computer (it$BOLD does not need$NORMAL apt, but uses$GREEN wget$NORMAL ; if you only"
	echo -e "\thave access to a Windows system, you should uncomment one of the two"
	echo -e "\tdedicated lines at the end of the apt-off file and download all the"
	echo -e "\tpackages listed in the $GREEN""offline.packages_url$NORMAL or in the"
	echo -e "\t$GREEN""offline.packages_list$NORMAL files by hand...) with an internet connection"
	echo -e "\t3- packages installation (option -x)\n"
	echo -e $BOLD$BLUE"WARNING"$NORMAL
	echo -e $BOLD$RED"\tCAUTION :$NORMAL the installation of packages and the use of the dist-upgrade"
	echo -e "\toption can pose some risks. You are strongly encouraged to"
	echo -e "\tsimulate these operations with apt-get before to use apt-off."
	echo -e "\tThe author cannot be considered as responseable for any problem.\n"
fi
	

##########################
## Display options	##
##########################
if [[ $1 == -h || $1 == --help || $1 == -o || $1 == --options ]]; then
	echo -e $BOLD$BLUE"OPTIONS"$NORMAL
	echo -e $GREEN"\t-c$NORMAL ou$GREEN --configure$NORMAL"
	echo -e "\tDownload apt configuration files.\n"
	echo -e $GREEN"\t-d$NORMAL ou$GREEN --download$NORMAL"
	echo -e "\tDownload packages. This option has to be used on a Linux system"
	echo -e "\twith an internet connection.$BOLD$RED Don't forget the offline.packages"
	echo -e "\tfile !!!$NORMAL\n"
	echo -e $GREEN"\t-g$NORMAL or$GREEN --generate$BLUE [package1 package2 ...]$NORMAL or$BLUE [dist-upgrade]$NORMAL"
	echo -e "\tGenerate packages list, stored in the $BLUE offline.packages$NORMAL file.\n"
	echo -e $GREEN"\t-h$NORMAL or$GREEN --help"$NORMAL
	echo -e "\tPrint this help.\n"
	echo -e $GREEN"\t-o$NORMAL or$GREEN --options$NORMAL"
	echo -e "\tDisplay options.\n"
	echo -e $GREEN"\t-x$NORMAL or$GREEN --extract$BLUE [package1 package2 ...]$NORMAL or$BLUE [dist-upgrade]$NORMAL"
	echo -e "\tExtract and install packages.\n"
	
	if [[ $1 == -h || $1 == --help ]]; then	
		echo -e $BOLD$BLUE"COPYRIGHT"$NORMAL
		echo -e "\tCopyright 2006, Goulven Guillard."
		echo -e "\tThis program is copyleft : copy, modification and diffusion are"
		echo -e "\tauthorized and encouraged if they are free."
		echo -e "\tPlease report bugs at$BLUE lecotegougdelaforce [at] free.fr$NORMAL.\n"
	fi
	

##########################################
## Download of apt configuration files	##
##########################################
elif [[ $1 == -c || $1 == --configure ]]; then
	if [[ -e config_files/config_apt ]]; then
		cd config_files
		sh -x ./config_apt
		cd ..
	else
		echo -e "You didn't execute$GREEN apt-off -p$NORMAL yet, or you have deleted the$VERT config_files$NORMAL directory and the$VERT config_apt$NORMAL file there was in it... Please restart all the procedure."
	fi


##########################
## Packages selection	##	
##########################
elif [[ $1 == -g || $1 == --generate ]]; then
	if [[ `ls /var/lib/apt/lists/ | grep binary-i386_Packages | wc -l` == 0 ]]; then
		if [[ ! -e config_files ]]; then
			mkdir config_files
			awk '($1=="deb"||$1=="deb-src")&&!match($2,"cdrom"){split($2,A,"/");for(i=4;i<=NF;++i) print "wget -O "A[3]"_"A[4]"_dists_"$3"_"$i"_binary-i386_Packages.gz "$2"dists/"$3"/"$i"/binary-i386/Packages.gz"}' < /etc/apt/sources.list > config_files/config_apt
			echo -e "WARNING : Your computer isn't correctly configured in order to use the apt tool."
			echo -e "This program will configure it for you. You now have to execute the$VERT apt-off -c$NORMAL"
			echo -e "command on a computer with an internet connexion. The configuration will end"
			echo -e "automatically next time you will use apt-off."
			exit
		elif [[ `ls config_files | grep gz | wc -l` > 0 ]]; then
			sudo cp config_files/*.gz /var/lib/apt/lists/
			sudo gunzip /var/lib/apt/lists/*.gz
		else
			echo -e "Vous devez d'abord exécuter$VERT apt-off -c$NORMAL sur un ordinateur avec internet !"
			exit
		fi
	fi

	if [[ -e offline.packages ]]; then
		echo "WARNING : The offline.packages file already exists, do you want to overwrite it (if not, the packages will be added to the existing list) ? (y/n)"
		read OVERWRITE
	fi

	if [[ $OVERWRITE == y ]]; then
		echo "cd ./deb" > offline.packages
	else
		echo "cd ./deb" >> offline.packages
	fi
	if [[ "$#" < 2 ]]; then
		echo "WARNING : You have to indicate which packages you want to install,"
		echo "or \"dist-upgrade\" !!!"
		exit
	elif [[ $2 == dist-upgrade ]]; then
		sudo apt-get -qq --print-uris dist-upgrade > .offline_tmp
	else
		for ((i=2; i<="$#"; i++ ))
		do 
			sudo apt-get -qq --print-uris install ${!i} >> .offline_tmp
		done
	fi
       	awk '{print "wget -O " $2 " " $1}' < .offline_tmp >> offline.packages
	echo "cd .." >> offline.packages

#### Lines to uncomment for Windows :
#	awk '{print $1}' < .offline_tmp >> offline.packages_url
#	awk '{print $2}' < .offline_tmp >> offline.packages_list

        rm -f .offline_tmp	


##########################
## Packages download	##
##########################
elif [[ $1 == -d || $1 == --download ]]; then
	if [[ ! -e deb ]]; then
		mkdir deb
	fi
	sh -x ./offline.packages


##########################
## Packages extraction	##
##########################
elif [[ $1 == -x || $1 == --extract ]]; then
	if [[ ! -e deb/partial ]]; then
		PARTIAL_CREATED=true
		mkdir deb/partial
	else
		PARTIAL_CREATED=false
	fi
	if [[ "$#" < 2 ]]; then
		echo "WARNING : You have to indicate which packages you want to install, or \"dist-upgrade\" !"
		exit
	elif [[ $2 == dist-upgrade ]]; then
		sudo apt-get -o dir::cache::archives=$PWD/deb/ dist-upgrade
	else
		for ((i=2; i<="$#"; i++ ))
		do 
			sudo apt-get -o dir::cache::archives=$PWD/deb/ install ${!i}
		done
	fi
	if [[ PARTIAL_CREATED ]]; then
		rm -rf deb/partial
	fi


##########################
## Display usage rules	##
##########################
else
	./apt-off -o


fi
## End of apt-off.


```

All the instructions are explained by **apt-off -h**. Enjoy ! ;) 

PS : Please report any problems (such as English corrections... :-? ).

Edit : I forgot to say that I inspired myself [from this page](http://www.batmat.net/apt-offline/ch3.html).

Please note that the French version (see [here](http://forum.ubuntu-fr.org/viewtopic.php?pid=611901#p611901)) can be much more up-to-date (update of this (english) version has been done today, 12/22/06).

---

### Post by Azathoth_ on 2006-12-02
Very, very god script my friend.
Is it possible to make and simple .exe or .bat for using it with windows i use on my university?

I think no, because it is no simple. We can use livecd and this script

Thank you very much

---

### Post by Azathoth_ on 2006-12-02
> **Azathoth_ said:**
> Very, very god script my friend.
Is it possible to make and simple .exe or .bat for using it with windows i use on my university?

I think no, because it is no simple. We can use livecd and this script

Thank you very much

I have read the help (./apt-off -h)
I don't need any hep thanks

---

### Post by Azathoth_ on 2006-12-02
If you like, i can translate it into spanish
Another question... is  it possible to add the dependences with this script?? I would be very good
Thanks

---

### Post by Skippy le Grand Gourou on 2006-12-04
I guess it should be possible to do some script for Windows, a short ask to google told me that wget also exists for Windows. If anybody wants to, please modify the script in consequence and post it ! :D (otherwise, I'll try to think about it when I finally have internet...)

Idem for any translation, in this case I guess it would be better to open a new thread on the relative language Ubuntu forum to post the translated script. Go ahead, it is copyleft ! ;)

At last, if you are asking about dependences that are needed to install a soft, here they are : apt-get knows that they are needed, so apt-off downloads them all.

---

### Post by Azathoth_ on 2006-12-04
I know, but t's for simply the things... when i have time i'll translate it.
Thanks for all and i think it's a very very good script

---

### Post by scrooch on 2006-12-06
Somebody aware of a windows version yet?

---

### Post by Skippy le Grand Gourou on 2006-12-22
Hi, script updated : a few bugs (well, nothing very important...) corrected, some warnings addd, and automatic apt configuration.

However, I still don't have tried to make the script executable under Windows, sorry.
Edit : After a quick look, it seems that wget for Windows should be installed on the online computer, which is not obvious if you are using a public computer... Nevertheless, I'll try to think about it one of these days. ;)

---

### Post by apparle on 2008-02-11
Could someone here please explain the script.
I have it running but unable to use it. Please explain in detail as I am a noob

---

### Post by sopin on 2009-01-29
Hi! I recommend using the cygwin utility ([www.cygwin.com](www.cygwin.com)) to add some linux commands to Windows. I am using it successfully to make backups with rsync and substituting dumb .BAT scripts with more flexible and powerful scripts. Only you have to use EditPlus or Notepad++ or similar editor to create scripts and to change the file format to Unix (or install nano or mc inside cygwin) 

Of course, wget works great on cygwin! Simply select it when cygwin asks for packages...

The procedure for using apt-off is below:

0. On the unconnected machine, mkdir some directory to store the script **apt-off**. Always run it here.

1. use **apt-off -g package(s)** to generate the file *offline.packages* on the unconnected ubuntu machine.

2. copy the file to the Internet enabled machine having *wget* (Linux or Windows with cygwin)

3. use **apt-off -d** to download the packages to the subdirectory  *deb* in the current directory (it worked nice under cygwin!)

4. copy the full directory *deb* to the unconnected machine

5. use **apt-off -x package(s)** to install them

6. Voilà! Packages ready to use!

Note that **apt-off -h** explain all this, leaving out the copy steps. Remember: If it doesn't work, read the manual!

Happy updating!

---

### Post by janmartin on 2009-03-29
Hi!

A fantastic script.

Please can someone post a working **config_apt** for Ubuntu Jaunty Jackalope 9.04 BETA for MID?

I am om Asus Eeepc 901 with Ralink rt2860 WIFI chipset, testing Ubuntu Jaunty Jackalope 9.04 BETA for MID: 
[http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-mid-lpia.img](http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-mid-lpia.img)

Because the driver is missing I need to install it driver manually: rt2860-source_1.8.0.0-3_all.deb

However there are lots of dependencies, so this script would be very handy. Sadly all the paths in my config_apt are outdated and wrong. So I cannot download the Packages.gz files needed.

Thanks,
Jan

---

### Post by GuruX on 2009-04-13
I have a computer running Intrepid and one runnng Jaunty beta right now. The Jaunty machine is offline (stupid I know), and kind of half broken. The Intrepid machine is online.

So these machines have different repositories. And the Jaunty package list updates daily. So I need the Intrepid machine to download the package lists (after reading sources.list from Jantu machine) aswell. Is this feature included in apt-off? If not it's be really nice to implement.

And then to download the debs, I guess there is no problem since apt-off uses wget.

---

### Post by apparle on 2009-04-19
> **GuruX said:**
> I have a computer running Intrepid and one runnng Jaunty beta right now. The Jaunty machine is offline (stupid I know), and kind of half broken. The Intrepid machine is online.

So these machines have different repositories. And the Jaunty package list updates daily. So I need the Intrepid machine to download the package lists (after reading sources.list from Jantu machine) aswell. Is this feature included in apt-off? If not it's be really nice to implement.

And then to download the debs, I guess there is no problem since apt-off uses wget.
Try this
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
Create a offline repository of jaunty on jaunty box and then use apt-offline to generate package list.
If you want to upgrade the package list just check the Release file if there has been any upgrade. If it is there then download the upgraded files. Put the new files in your offline repo and then reload the list in pacakge manager and then use apt-offline

---

### Post by mac9416 on 2009-04-28
I believe it's worthwhile to mention [http://keryxproject.org/]("http://keryxproject.org/").
It should make matters for ya'll a lot simpler :-).

---

