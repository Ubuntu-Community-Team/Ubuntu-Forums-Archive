---
title: "Having some difficulty installing wine"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by bill31 on 2014-03-17
I have a chromebook (acer c7) with 2gb of RAM and Ubuntu is partioned with 9gb. My ubuntu version is 13.10. I am MUCH more accustumed to windows OS's so this issue may just be a lack of understanding of how ubuntu works. I have looked online for a sollution (generally on forums) but havent come across one that works or that I fully understand how to exicute. Some of the time there will be terms I dont know or steps that a common user of ubuntu would understand how to reach but for newbie like me does not have a clue. I would ask in said topics what a term means or how to complete a task I do not know of, but many of said topics are old and would be impolite to respond such an outdated topic on a forum. 

I try to install it through the software center by typing in "wine" in the search box and clicking on the first option avaible "mircosoft windows compatiblity layer (media package)". I then follow up clicking "install". I then encounter the following error "package dependencies cannot be resolved". These steps are the most common ones I find when searching online for "how to install wine" and most dont seem to differ too much. I have also tried installing it through using the terminal but I also encounter problems.

---

### Post by oldos2er on 2014-03-17
Moved to Absolute Beginners.

Can you open a terminal with Ctrl-Alt-t, run the following command and copy & paste all its output here? Should help in diagnosing your problem. ```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by bill31 on 2014-03-17
For the command above I get the following:

apt 0.9.9.1~ubuntu1 for amd64 compiled on Sep 11 2013 17:45:21
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
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
user@chrubuntu:~$

---

### Post by Yellow Pasque on 2014-03-18
You probably want to install wine:i386 package

---

### Post by jaspreet on 2014-03-18
Looks like you are typing/pasting the command incorrectly. Try to fire these commands one at a time:

First:
> sudo apt-get update

then:
> sudo apt-get install wine

---

### Post by bill31 on 2014-03-18
After running the command "sudo apt-get update here is what I encountered:

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg [933 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release [49.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [80.3 kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [68.0 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [1348 B]      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main amd64 Packages [223 kB]     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe amd64 Packages [158 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1552 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en            
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources [38.0 kB]         
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources [14 B]      
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources [8428 B]      
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources [692 B]     
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main amd64 Packages [104 kB]   
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe amd64 Packages [35.4 kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse amd64 Packages [1160 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en           
Fetched 821 kB in 11s (71.0 kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

After running the "sudo apt-get install wine" I get the following:

user@chrubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



I also notice a software updater pop up as well and I will proceed to update.

---

### Post by bill31 on 2014-03-18
I have successfuly completed the update.

---

### Post by Yellow Pasque on 2014-03-18
Okay, but did you run?
```
sudo apt-get install wine1.4:i386
```

---

### Post by bill31 on 2014-03-18
I did not. I will proceed to do so.

---

### Post by bill31 on 2014-03-18
Here is what I encountered when I used "sudo apt-get install wine1.4:i386":

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine1.4
E: Couldn't find any package by regex 'wine1.4'

---

### Post by bill31 on 2014-03-18
Looking for a sollution for above problem online seems confusing

---

### Post by DGINSD on 2014-03-18
Open the software sources application and on one of the first two tabs click to enable cannoical partner repositories, and close the application. In a terminal run the command 'sudo apt-get update' 'sudo apt-get install synaptic' (a more complete package manager application), then launch synaptic search wine and install.

---

### Post by bill31 on 2014-03-18
what is "software sources application"?

---

### Post by DGINSD on 2014-03-18
> **bill31 said:**
> what is "software sources application"?
 
Hit your ubuntu logo in the launcher to pull up the dash,  in the search box enter 'software sources', it should be the first application in the results (the name may have changed I'm flying blind here)

---

### Post by bill31 on 2014-03-18
I do believe I have successfully installed synaptic, but how do I launch it?

---

### Post by bill31 on 2014-03-18
I just tried "sudo apt launch synaptic" as a guess for launching the spplication and got the following:

apt: invalid flag: launch
Usage: apt <apt and javac options> <source files>
where apt options include:
  -classpath <path>          Specify where to find user class files and annotation processor factories
  -cp <path>                 Specify where to find user class files and annotation processor factories
  -d <path>                  Specify where to place processor and javac generated class files
  -s <path>                  Specify where to place processor generated source files
  -source <release>          Provide source compatibility with specified release
  -version                   Version information
  -help                      Print a synopsis of standard options; use javac -help for more options
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system
  -A[key[=value]]            Options to pass to annotation processors
  -nocompile                 Do not compile source files to class files
  -print                     Print out textual representation of specified types
  -factorypath <path>        Specify where to find annotation processor factories
  -factory <class>           Name of AnnotationProcessorFactory to use; bypasses default discovery process
See javac -help for information on javac options.


warning: The apt tool and its associated API are planned to be
removed in the next major JDK release.  These features have been
superseded by javac and the standardized annotation processing API,
javax.annotation.processing and javax.lang.model.  Users are
recommended to migrate to the annotation processing features of
javac; see the javac man page for more information.
user@chrubuntu:~$

---

### Post by DGINSD on 2014-03-18
Search for it in the dash, or in a terminal 'synaptic'

---

### Post by bill31 on 2014-03-18
I have synaptic open

---

### Post by DGINSD on 2014-03-18
I just re-read your original post and responses. You have broken held packages, I believe this is usually caused by an interupted package install. I'd need to research a bit to be sure but I believe the command to resolve is in a terminal
dpkg configure -a

Then after that completes try and install wine again
sudo apt-get install wine

---

### Post by bill31 on 2014-03-18
Using the command "dpkg configure -a" I encountered the following: 

user@chrubuntu:~$ dpkg configure-a
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
user@chrubuntu:~$

---

### Post by Vladlenin5000 on 2014-03-18
```
sudo dpkg --configure -a
```
Exactly like this, including spaces. And no, Synaptic alone won't solve your issue but can give a lot of additional information.

---

### Post by DGINSD on 2014-03-18
I'll have to wait till I'm in front of my machine to be sure of the correct command to clear broken packages. In the mean time you can try searching on-line for 'ubuntu fix broken packags'. The synaptic program I had you install has an option for this, but I've always had to resort to dpkg to actually fix the problem.

---

### Post by bill31 on 2014-03-18
I did the command given by _[[COLOR=#000000]Vladlenin5000[/COLOR]]("http://ubuntuforums.org/member.php?u=1468732")_ but I am not sure if anything happened. After putting in the text it asked me for my password and after pressing enter it didnt show any more text. Is that what should have happened?

---

### Post by DGINSD on 2014-03-18
Did you enter your password and then press enter? That would be the correct action. When the command has completed you should be left with another command prompt.

BTW thank you Vladlinin500

---

### Post by bill31 on 2014-03-18
I did indeed enter my password and was met with another command prompt. I am guessing the next action is to attempt a reinstall for wine.

---

### Post by DGINSD on 2014-03-18
Correct
sudo apt-get install wine

---

### Post by bill31 on 2014-03-18
I closed all windows except the command prompt and used the command "sudo apt-get install wine" and was met with:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
user@chrubuntu:~$ 


should I once again uninstall the packages and retry?

---

### Post by DGINSD on 2014-03-18
Were you able to open the 'software sources' program and enable the cannoicle partner repositories? I believe wine or is part of that repository and needs to be activated to install.

---

### Post by bill31 on 2014-03-18
How do I enable the cannoicle partner repositories?

---

### Post by DGINSD on 2014-03-18
Ok the program is actually called Software & Updates, search for it in the dash and launch it. The second tab you should see Canonical Partners check it if it is not checked.

[IMG]http://s19.postimg.org/hjrtrravn/software_and_updates1.png[/IMG]

---

### Post by bill31 on 2014-03-18
I have the "software & updates" program open and I am on the "other software" tab just as the picture you suppied. I do not however see any option for "canonical partners".

[ATTACH=CONFIG]251270[/ATTACH]


I did learn how to do screenshots :)

---

### Post by widi2 on 2014-03-18
If I may interject with a completely different solution which is supported by WINE, unlike the USC version:

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

Copy and paste into browser, follow instructions.

---

### Post by bill31 on 2014-03-18
I am able to follow all but the "installing wine" step from the link provided by widi2. After I click on the link for wine 1.6 (I have a prefrence for sticking with stable versions of programs) it pops up with "launch application" of which minecraft.jar is the only option. I have no clue what to do when said window appears.

---

### Post by DGINSD on 2014-03-18
What does the first tab of Software & Updated look like?

The option widi2 offered should work, it just seems odd that your not able to install without adding another repository.

---

### Post by bill31 on 2014-03-18
Here is what the first tab looks like from software & updates look like:


[ATTACH=CONFIG]251273[/ATTACH]

---

### Post by SuperFreak on 2014-03-18
WINE will allow you to run some Windows programs but only after you install them. To do this you would download the exe file of the program you want and install as you would a Windows program. Beware that this may open your computer to all the dangers a Windows computer is exposed to. You should go to the WINE web site and see which programs are usable and which version. The site has a system for classifying programs which work (ie Gold) and which don't (Junk) [http://appdb.winehq.org/]("http://appdb.winehq.org/") use the appDB to check out the available windows programs

EDIT: forgive me for interjecting but it sounded to me as though WINE is now installed, but perhaps I am mistaken

---

### Post by DGINSD on 2014-03-18
That install wine 1.6 link should open Ubuntu software center, to install wine

---

### Post by bill31 on 2014-03-18
Would it be possible to dirrect it from "launch application" to ubuntu software center? It does offer an option to choose an application.

---

### Post by DGINSD on 2014-03-18
No it should launch it automatically. regaurdless now that you have activated the wine repo. you should be able to install wine.

```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by bill31 on 2014-03-18
Following the command above I got:

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg [933 B]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg [933 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release [49.6 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release [49.6 kB]         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources [14 B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources [68.0 kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources [1348 B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources [80.3 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B] 
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe amd64 Packages [158 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [1552 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main amd64 Packages [223 kB]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en            
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources [14 B]      
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources [8428 B]      
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources [692 B]     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources [38.0 kB]         
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted amd64 Packages [14 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe amd64 Packages [35.5 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse amd64 Packages [1160 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main amd64 Packages [104 kB]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en           
Fetched 821 kB in 11s (72.9 kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.




I suspect I need to get rid of my previous packages and reinstall, I shall proceed to do so.

---

### Post by bill31 on 2014-03-18
I oddly still am encountering the same exact response.

---

### Post by DGINSD on 2014-03-18
Try this just to be sure

```
sudo apt-get remove --purge wine
```

then

```
sudo apt-get install wine
```

I don't think the result will be any different, but it's worth a shot.  The dpkg command from before should of fixed the held broken packages problem but it didn't.

---

### Post by bill31 on 2014-03-18
Here is what I encountered with those commands:

user@chrubuntu:~$ sudo apt-get remove --purge wine
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wine' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@chrubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by DGINSD on 2014-03-18
On the Software & updates application, on the second tab, click the add button and in the pop up window enter

```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
```

Then click the add button.

In a terminal window and again

```
sudo apt-get update
```

and

```
sudo apt-get install wine
```

---

### Post by DGINSD on 2014-03-18
Actally give this a whirl

```
[COLOR=#000000]sudo apt-get clean && sudo apt-get update[/COLOR]
```

then

```
sudo apt-get install wine
```

---

### Post by bill31 on 2014-03-18
Darn it! I realy thought that was going to work for a moment. Well, here is what I got from the terminal (the text for the software and updates seems to have worked. I now have canonical partners):

user@chrubuntu:~$ sudo apt-get update
[sudo] password for user: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                         
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease   
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release.gpg             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security Release                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
user@chrubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by DGINSD on 2014-03-18
Did you try the last one I just posted 'apt-get clean'

---

### Post by bill31 on 2014-03-18
I did and I seem to get the same "held broken package" response from it at the end.

---

### Post by DGINSD on 2014-03-19
Can you post the output of this command

```
 sudo lshw | grep -A 8 -B 2 cpu
```

It will give me info on your cpu, you did say this was a Chrome book which I believe runs on an ARM platform. I'm curious if wine will run on ARM architecture. The held packages output your getting is still odd both the dpkg --configure -a command and apt-get clean commands should of both cleared that up.

---

### Post by bill31 on 2014-03-19
user@chrubuntu:~$ sudo lshw | grep -A 8 -B 2 cpu
[sudo] password for user: 
sudo: lshw: command not found

---

### Post by DGINSD on 2014-03-19
Sorry

```
sudo apt-get install lshw
```

then run it again

---

### Post by bill31 on 2014-03-19
user@chrubuntu:~$ sudo lshw | grep -A 8 -B 2 cpu
          size: 1MiB      
          capabilities: pci pcmcia upgrade bootselect acpi
     *-cpu:0 DISABLED
          description: CPU [empty]
          product: Pentium Pro
          vendor: GenuineIntel
          physical id: 3
          version: Intel(R) Celeron(R) CPU 1007U @ 1.50GHz
          configuration: cores=16
     *-memory
          description: System memory
          physical id: 1
          size: 1873MiB
     *-cpu:1
          product: Intel(R) Celeron(R) CPU 1007U @ 1.50GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          size: 1500MHz
          capacity: 1500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
user@chrubuntu:~$

---

### Post by DGINSD on 2014-03-19
No problem there, Pentium Pro GenuineIntel.


Launch the Synaptic program and click on the 'Status' button and see if there's a listing for any broken packages. If there is take a screen shot and post it or list them here.

---

### Post by bill31 on 2014-03-19
Sorry for my absence. I have hundreds of packages listed so I scrolled down to the ones with wine in there name.

[ATTACH=CONFIG]251289[/ATTACH]

---

### Post by bill31 on 2014-03-19
Still not finding any help online but I am still looking

---

### Post by DGINSD on 2014-03-19
Just to clarify you have hundreds of packages listed under status broken?

---

### Post by bill31 on 2014-03-19
No, just hundreds of packages in total. But how would I know if one was broken?

---

### Post by DGINSD on 2014-03-19
[IMG]http://s19.postimg.org/xdjr4xgpf/synaptic_origin.png[/IMG]
 
This is the synaptic package manager program, the buttons labeled; Sections, Status, Origin, Etc..., click on the button labeled Status, and in the sub window directly above these buttons you will see; All, Installed, Installed (local or obsolete), Etc..., just like in the above picture except in your case there should be and entry for broken, it may be; Not Installed (broken) or something like that. Click on that entry that and see what packages are shown in the sub window to the left, Wine should definitely be among them.

Out of curiosity when you did your system install was it a straight forward install, or did you use a special method or instructions?

---

### Post by bill31 on 2014-03-19
Yes wine is in the "not installed" directory.


[ATTACH=CONFIG]251303[/ATTACH]

---

### Post by bill31 on 2014-03-19
By system install do you mean when I installed ubuntu or when I first attempted to install wine?

---

### Post by DGINSD on 2014-03-20
What's listed in the left pane of synaptic after you click the Status button.

By Install I meant install Ubuntu.

---

### Post by bill31 on 2014-03-20
Since I had a chromebook I had to install ubuntu via chrubuntu.

As for what is listed in the left pane, "all" "installed" "installed (manual)" and "not installed" in that order.

---

### Post by DGINSD on 2014-03-20
I'm really out of any real helpful ideas, the only thing I can think is that it's related to it being a non-standard Ubuntu install (chrubuntu), or possibly being related to the small drive space confines. That being said the errors your getting are fairly common ones that are usually remedied with

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a[/FONT][/COLOR]
```

or

```
sudo apt-get clean
```

But neither of these fixed your issue. It seems very odd that 'sudo apt-get install wine' tells you you have broken held packages but Synapic package manager doesn't even have a listing for broken packages, seems like a situation that shouldn't even be possible as. Unless someone else can chime in here with another possible solution the only other thing I could suggest is try formatting your problem as a question and posting it at [http://askubuntu.com/](http://askubuntu.com/),  it's not a great place for troubleshooting but perhaps if you explain the issue and the two commands we've tried to correct the problem, someone may have another solution.  If there is a specific forum for [COLOR=#000000]chrubuntu someone there my have some more information for you, I didn't find much in my search. [/COLOR]

It's also possible that during your installation of Ubuntu something went wrong, in which case we may be chasing our tails and the issue would not be able to be corrected without re-installing. Personally I don't like the idea that that a problem can't be corrected, but I have had to re-install my own system when a solution couldn't be found, always with good results.

---

### Post by bill31 on 2014-03-20
Thanks for trying to help. I do hope someone with can come up with another solution. I will also look for a chrubuntu forum and see if anyone can solve the issue there.

---

### Post by DGINSD on 2014-03-20
I think I found your solution, unfortunately looks like you will need to abandon your current chrubuntu install and re-install ubuntu using crouton. Here's the conversation I found this answer in you will have to read through a few posts.
[https://plus.google.com/app/basic/stream/z12uixjrmvjew5joy04cgt24nwj2trcjtn40k?cbp=3sqyy7zfrr5x&partnerid=gpmobile:android&sview=58&cid=5&soc-app=115&soc-platform=1&spath=/app/basic/communities/108883927831773328803&sparm=source%3Dapppromo%26gpsrc%3Dgpmobile:android%26partnerid%3Dgpmobile:android](https://plus.google.com/app/basic/stream/z12uixjrmvjew5joy04cgt24nwj2trcjtn40k?cbp=3sqyy7zfrr5x&partnerid=gpmobile:android&sview=58&cid=5&soc-app=115&soc-platform=1&spath=/app/basic/communities/108883927831773328803&sparm=source%3Dapppromo%26gpsrc%3Dgpmobile:android%26partnerid%3Dgpmobile:android)

---

### Post by DGINSD on 2014-03-20
If you planning on reinstalling anyway, at one point in that thread they talk about trying to install the package that allows 32bit programs to run in a 64bit system as a possible solution. The name of that package is ia32-libs, which is depreciated so you would need to manually download it and install, so you would search on-line for ia32-libs.deb, after download right click the package and select open with ubuntu software center and install it. For the record I don't see that as a valid solution but if your going to re-install with crouton little to no harm in trying.

---

### Post by bill31 on 2014-03-20
I would install crouton but it is likely that my chromebook could not handle the amount of ram it uses. I have trouble running as little as 5 tabs at times already and if I understand correctly how crouton works it would eat up even more ram than chrubuntu.

---

### Post by DGINSD on 2014-03-21
Run this

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw | grep -A 12 -B 2 "[/FONT][/COLOR]*-memory"
```

lets see how much ram you have, another option could be to run Ubuntu via crouton with a different desktop environment such as XFCE which is supposed to be lighter  than Ubuntu default Unity, not sure if LXDE is available in crouton but it would be even lighter still.

---

### Post by bill31 on 2014-03-21
version: Intel(R) Celeron(R) CPU 1007U @ 1.50GHz
          configuration: cores=16
     *-memory
          description: System memory
          physical id: 1
          size: 1873MiB
     *-cpu:1
          product: Intel(R) Celeron(R) CPU 1007U @ 1.50GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          size: 1500MHz
          capacity: 1500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq

---

### Post by widi2 on 2014-04-15
I posted earlier on this thread, and it looks like my solution was inconclusive: after adding the official wine repo, use the wine1.6 package not the wine package.

Sorry!

---

