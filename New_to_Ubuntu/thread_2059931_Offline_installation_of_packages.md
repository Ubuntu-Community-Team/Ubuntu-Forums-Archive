---
title: "Offline installation of packages"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by bijupp on 2012-09-19
Hai everyone

I have little experience with ubuntu and linux  I have a computer which does not have a internet connection I wish to install ubuntu in it.  

but in ubuntu if I want to install packages every time this requires internet.  

or use commands like "sudo apt get install ...."  

My question is there is any way I can download the required files from another computer and by using Pendrive or cd copy the same to the computer which does not have internet connection and install it.

Please help me...

---

### Post by rybnik on 2012-09-19
Yes, download the tarball (.tar.gz) then unzip then untar it.

---

### Post by rybnik on 2012-09-19
Then

./ configure
make
make install

---

### Post by rybnik on 2012-09-19
apt-get command requires internet

---

### Post by mips on 2012-09-19
> **rybnik said:**
> Yes, download the tarball (.tar.gz) then unzip then untar it.

This does not resolve dependencies issue.

---

### Post by mips on 2012-09-19
You can use the following to do this,

[http://keryxproject.org/](http://keryxproject.org/)
[http://ubuntuofflineinstall.com/](http://ubuntuofflineinstall.com/)

Once you have the packages you can copy them to /var/cache/apt/archives with sudo and set the permissions to -rw-r--r-- (owner:root access:read&write, group:root access:read only, others:read only)

Then you can install them the normal way.



Tags: offline package installation download no internet

---

### Post by Wim Sturkenboom on 2012-09-19
This might do the trick: [http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx](http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx)

No experience with it.

---

### Post by elliotn on 2012-09-19
check this thread [http://ubuntuforums.org/showthread.php?t=1901446]("http://ubuntuforums.org/showthread.php?t=1901446") 

then go to synaptic and mark all packages u want then go to file - save as download package script, save the script smin a thumb drive then go to the PC with internet (if a windows machine- download flashget or free download manager and open the script with a text editor copy all the contents and go to your download manager and file add downloads from clipboard).
set the download location yo your thumb drive.

take the thumb drive to your offline Ubuntu open synaptic then go to file and add downloded packages.....then apply...

walla solved no dependency headaches

---

### Post by bijupp on 2012-09-19
Thank you [rybnik]("http://ubuntuforums.org/member.php?u=1134219")

once i tried to install vlc through tar.gz but it doesn't works well... later i have used wine to install vlc.. the restricted extras doesn't show much problem...


I have tried sudo apt-get install .... command to run  and found out that there are many options for the command the help screen i get as follows...  

```
  apt 0.8.16~exp12ubuntu6 for i386 compiled on Mar 15 2012 18:53:59
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers. 
```In the above list I found some commands and option  may came helpful... as follows



   source - Download source archives
   download - Download the binary package into the current directory

options
  -d  Download only - do NOT install or unpack archives



I wish to know more about the above 


taking yu:lolflag::popcorn:

---

### Post by foberle on 2012-09-19
Hi. I'm VERY new at Ubuntu, but also needed to put Ubuntu on several machines and found a way that worked for me. What I did to "clone" an installation of 12.04 with a large and customized group of applications was the following:

1. Install all of the apps that you want to clone onto the other machines. Get rid of apps you don't want to have placed on the other machine(s)*.
2. Go to the Ubuntu Software Center and search for "remastersys-gui"
3. Download this. It should install both remastersys itself (a command line app) as well as remastersys-gui, which is a gui front-end.
4. Run remastersys by selecting the Dash and typing remas...
5. The gui is fairly self-explanatory. Choose "Clear out the working folder" (probably not necessary on the first pass) to begin. 
6. Choose "Customize system and remastersys settings" and then click "User Settings." Pick yourself as the User.
7. Click Main to return to the main menu.
8. Choose "Distribution" and let it go do its thing.
9. The end result (after it works for quite a while) will be an ISO file named /home/remastersys/remastersys/custom-dist.iso.
At this point, you can close remastersys, but if any errors occurred, you're on your own.

You'll need a blank DVD-R or (for testing) a blank DVD-RW for the next step.

Now go find the iso file above in the Nautilus file manager, right-click on it, and choose "Open with Brasero Disk Burner."

Since Brasero recognizes that this is an iso file, it will offer to burn it directly to the blank disk (you can't just copy an iso file and have it work in the way I'm describing).

This also will take some time, but when you are finished, you'll have a customized Ubuntu distribution DVD (you can use a CD, but there probably won't be enough room if you have a collection of applications). Stick it in another machine and boot from it. It will let you run Ubuntu from the DVD so you can test to see if all the apps work ok on the new machine (you'll have to select them by using the Dash). Assuming that all goes well, you can simply choose the install option and then let the user of that machine have at customizing wallpaper and such things.

If this works out for you, you can also take advantage of all the other options you see on the remastersys menu - custom splash screens for the DVD and so forth.

I found this to be far less tedious than doing all of the manual work, and waiting for downloads of stuff I had already downloaded onto the first machine.

Good Luck.

* I just removed unwanted apps using the Ubuntu Software Center, but if you want to keep them and just not put them on the "distro" DVD, you can use the "exclude" capability that you'll find in remastersys.

---

### Post by rybnik on 2012-09-19
[quote=mips]

[quote=rybnik]Yes, download the tarball (.tar.gz) then unzip then untar it.[/quote]

This does not resolve dependencies issue.[/quote]

Sorry, but what does "dependencies" mean?

---

### Post by newb85 on 2012-09-19
> **rybnik said:**
> Sorry, but what does "dependencies" mean?

Often, when you install something, it isn't self-contained.  It needs other packages to work.  Those packages are referred to as dependencies.  The advantage of this modularity is that often many packages users install have common dependencies, so a lot of redundancy is eliminated.  The downside is that if you don't use package management software, you have to manually make sure you have all dependencies installed.

If you install using the Software Center, Synaptic, or apt-get, dependencies should be handled automatically.

---

### Post by rybnik on 2012-09-20
> **newb85 said:**
> Often, when you install something, it isn't self-contained.  It needs other packages to work.  Those packages are referred to as dependencies.  The advantage of this modularity is that often many packages users install have common dependencies, so a lot of redundancy is eliminated.  The downside is that if you don't use package management software, you have to manually make sure you have all dependencies installed.

If you install using the Software Center, Synaptic, or apt-get, dependencies should be handled automatically.

Thanks, I understand this in theory, but could you name an example, please?

---

### Post by newb85 on 2012-09-20
Certainly.

I just pulled up the Software Center and grabbed a random app that I saw on the first screen: Stellarium.  (It's a cool app, by the way, but I'll abstain from puns.)

To see it's dependencies, I ran

```
aaron@aaron-Satellite-P755:~$ sudo apt-get install stellarium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbabl-0.0-0 libgegl-0.0-0
Use 'apt-get autoremove' to remove them.
[B]The following extra packages will be installed:
  stellarium-data[/B]
The following NEW packages will be installed:
  stellarium stellarium-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.6 MB of archives.
After this operation, 48.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

As you can see, stellarium requires the package stellarium-data to run.  I can't say for certain, but stellarium-data probably contains all the info about the stars, planets, and constellations, and stellarium probably is just the user interface.  If someone wanted, they could write a different astronomy program and use stellarium-data, which would save them the trouble of collecting, collating, and formatting the info.

You may also notice (above) the two packages that were previously installed and no longer needed.  These were dependencies of a program that I must have installed and then removed.  There's little harm in keeping them around, but it's not a bad idea to do a little housekeeping once in a while.  Once again, the package manager comes in handy.

```
aaron@aaron-Satellite-P755:~$ sudo apt-get autoremove
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libbabl-0.0-0 libgegl-0.0-0
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1,837 kB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by rybnik on 2012-09-20
> **newb85 said:**
> Certainly.

I just pulled up the Software Center and grabbed a random app that I saw on the first screen: Stellarium.  (It's a cool app, by the way, but I'll abstain from puns.)

To see it's dependencies, I ran

```
aaron@aaron-Satellite-P755:~$ sudo apt-get install stellarium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbabl-0.0-0 libgegl-0.0-0
Use 'apt-get autoremove' to remove them.
[B]The following extra packages will be installed:
  stellarium-data[/B]
The following NEW packages will be installed:
  stellarium stellarium-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.6 MB of archives.
After this operation, 48.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```As you can see, stellarium requires the package stellarium-data to run.  I can't say for certain, but stellarium-data probably contains all the info about the stars, planets, and constellations, and stellarium probably is just the user interface.  If someone wanted, they could write a different astronomy program and use stellarium-data, which would save them the trouble of collecting, collating, and formatting the info.

You may also notice (above) the two packages that were previously installed and no longer needed.  These were dependencies of a program that I must have installed and then removed.  There's little harm in keeping them around, but it's not a bad idea to do a little housekeeping once in a while.  Once again, the package manager comes in handy.

```
aaron@aaron-Satellite-P755:~$ sudo apt-get autoremove
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libbabl-0.0-0 libgegl-0.0-0
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1,837 kB disk space will be freed.
Do you want to continue [Y/n]?
```

Thank you for  your detailed reply!  That was very helpful.

I apologize for deviating from the original topic of this thread.

---

### Post by mips on 2012-09-21
> **rybnik said:**
> Thanks, I understand this in theory, but could you name an example, please?

Example:
Open "Synaptic Package Manager" and look for the music player called "audacious", right click on the audacious package and select "Properties", next select the "Dependencies" tab and it will show you a whole list of packages.

Without that list of packages installed audacious will not work. So if you download audacious manually you also have to download all those packages (if not already installed) and install everything in order for audacious to work.

---

### Post by tienlbhoc on 2012-09-21
if you have not any internet, you can't use synaptic or copy  /var/cache/apt/archives 

download all deb (with dependencde) with my web [http://ubuntuofflineinstall.com/](http://ubuntuofflineinstall.com/)

and run:

sudo dpkg -i **--force-depends** *.deb

---

### Post by newb85 on 2012-09-21
> **tienlbhoc said:**
> if you have not any internet, you can't use synaptic or copy  /var/cache/apt/archives 

download all deb (with dependencde) with my web [http://ubuntuofflineinstall.com/](http://ubuntuofflineinstall.com/)

and run:

sudo dpkg -i **--force-depends** *.deb

Wow, that sounds like it could really come in handy in a bind.  Thanks!

---

### Post by bijupp on 2012-09-24
a big thanks for everyone who participated in the discussion


I hav enjoyed that...   But even though I am not clear how to generate a list of files to download from "sudo apt-get .... " command but I assume that the remaining part of the command will be the same one as earlier said....."

---

### Post by bijupp on 2012-09-26
> **foberle said:**
> Hi. I'm VERY new at Ubuntu, but also needed to put Ubuntu on several machines and found a way that worked for me. What I did to "clone" an installation of 12.04 with a large and customized group of applications was the following:

1. Install all of the apps that you want to clone onto the other machines. Get rid of apps you don't want to have placed on the other machine(s)*.
2. Go to the Ubuntu Software Center and search for "remastersys-gui"
3. Download this. It should install both remastersys itself (a command line app) as well as remastersys-gui, which is a gui front-end.
4. Run remastersys by selecting the Dash and typing remas...
5. The gui is fairly self-explanatory. Choose "Clear out the working folder" (probably not necessary on the first pass) to begin. 
6. Choose "Customize system and remastersys settings" and then click "User Settings." Pick yourself as the User.
7. Click Main to return to the main menu.
8. Choose "Distribution" and let it go do its thing.
9. The end result (after it works for quite a while) will be an ISO file named /home/remastersys/remastersys/custom-dist.iso.
At this point, you can close remastersys, but if any errors occurred, you're on your own.

You'll need a blank DVD-R or (for testing) a blank DVD-RW for the next step.

Now go find the iso file above in the Nautilus file manager, right-click on it, and choose "Open with Brasero Disk Burner."

Since Brasero recognizes that this is an iso file, it will offer to burn it directly to the blank disk (you can't just copy an iso file and have it work in the way I'm describing).

This also will take some time, but when you are finished, you'll have a customized Ubuntu distribution DVD (you can use a CD, but there probably won't be enough room if you have a collection of applications). Stick it in another machine and boot from it. It will let you run Ubuntu from the DVD so you can test to see if all the apps work ok on the new machine (you'll have to select them by using the Dash). Assuming that all goes well, you can simply choose the install option and then let the user of that machine have at customizing wallpaper and such things.

If this works out for you, you can also take advantage of all the other options you see on the remastersys menu - custom splash screens for the DVD and so forth.

I found this to be far less tedious than doing all of the manual work, and waiting for downloads of stuff I had already downloaded onto the first machine.

Good Luck.

* I just removed unwanted apps using the Ubuntu Software Center, but if you want to keep them and just not put them on the "distro" DVD, you can use the "exclude" capability that you'll find in remastersys.


As earlier said Iam just a user of ubuntu doesnot have much experience in installing softwares 

I have tried to install from Ubuntu Software Center and search for "remastersys-gui" but not found anything on searching the web some offline installer found but it was unsuccessful please route me from the base ie. command code for installing  all dependencies 

please help me......

---

### Post by HiImTye on 2012-09-26
use Synaptic as mentioned earlier. you will need to install it, if you don't already have it.

once in Synaptic, search for the program you want, right click it, and mark it for installation. next, go to File > Generate package download script. choose '/home/<your username>' for the folder and then type in 'downloadlist' to name the file. next, run the following in a terminal (ctrl+alt+t):
```
sudo chown $USER $HOME/downloadlist; sed -i 's|#!/bin/sh||g;s|wget -c ||g' downloadlist
```the result will just be a list of URIs that you can plug into a browser and download

note: you will likely need to download synaptic and resolve any dependencies manually.

---

### Post by Lars Noodén on 2012-09-26
Synaptic actually creates a script that can be run which will download all the packages for you into the current directory.  So there is no need to plug them into a browser, the script can get them for you automatically.  So in short, run the script that Synaptic has created for you and it will get your packages.

---

### Post by HiImTye on 2012-09-26
> **Lars Noodén said:**
> Synaptic actually creates a script that can be run which will download all the packages for you into the current directory.  So there is no need to plug them into a browser, the script can get them for you automatically.  So in short, run the script that Synaptic has created for you and it will get your packages.
this is true if the computer you use to download them with has an sh shell

---

### Post by Polydorus on 2012-09-26
I have a similar situation, installed 64 bit Ubuntu 12.04 last week on a computer with no internet connection.  Since I only have Windows dialup, which made downloading Ubuntu impractical, I purchased the distribution.  I also bought a 13 dvd Repository Set  (I still have not been able to copy it to my computer)  which I believe contains some of the files you have been discussing Would this be a possible solution to the OP's problem or am I barking up the wrong tree?

---

