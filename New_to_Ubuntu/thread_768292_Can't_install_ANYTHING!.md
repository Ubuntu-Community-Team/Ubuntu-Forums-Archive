---
title: "Can't install ANYTHING!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by kulotzy on 2008-04-26
Something happened during upgrading to Hardy Heron... it wasnt able to install gcc 3.3 and 3.4... now i cant install anything... please help, thanks.

> ~$ aptitude search gcc 
p   colorgcc                        - Colorizer for GCC warning/error messages  
i   gcc                             - The GNU C compiler                        
i A gcc-2.95                        - The GNU C compiler                        
i   gcc-2.95-doc                    - Documentation for the GNU compilers (gcc, 
i   gcc-3.3                         - The GNU C compiler                        
i A gcc-3.3-base                    - The GNU Compiler Collection (base package)
C   gcc-3.3-doc                     - Documentation for the GNU compilers (gcc, 
i A gcc-3.4                         - The GNU C compiler                        
i A gcc-3.4-base                    - The GNU Compiler Collection (base package)
C   gcc-3.4-doc                     - Documentation for the GNU compilers (gcc, 
i   gcc-4.1                         - The GNU C compiler                        
i   gcc-4.1-base                    - The GNU Compiler Collection (base package)
idA gcc-4.1-doc                     - Documentation for the GNU compilers (gcc, 
i   gcc-4.1-locales                 - The GNU C compiler (native language suppor
idA gcc-4.1-multilib                - The GNU C compiler (multilib files)       
i   gcc-4.1-source                  - Source of the GNU Compiler Collection     
i   gcc-4.2                         - The GNU C compiler                        
i   gcc-4.2-base                    - The GNU Compiler Collection (base package)
i   gcc-4.2-doc                     - Documentation for the GNU compilers (gcc, 
i   gcc-4.2-locales                 - The GNU C compiler (native language suppor
i   gcc-4.2-multilib                - The GNU C compiler (multilib files)       
i   gcc-4.2-source                  - Source of the GNU Compiler Collection     
i   gcc-avr                         - The GNU C compiler (cross compiler for avr
i   gcc-doc                         - Documentation for the GNU C compilers (gcc
v   gcc-docs                        -                                           
i   gcc-h8300-hms                   - The GNU C compiler (cross compiler for h83
i   gcc-m68hc1x                     - GNU C compiler for the Motorola 68HC11/12 
i   gcc-multilib                    - The GNU C compiler (multilib files)       
p   gcc-snapshot                    - A SNAPSHOT of the GNU Compiler Collection 
i   gcc272                          - The GNU C compiler.                       
i   gccxml                          - XML output extension to GCC               
i A lib64gcc1                       - GCC support library (64bit)               
p   lib64gcc1-dbg                   - GCC support library (debug symbols)       
i   libgcc1                         - GCC support library                       
p   libgcc1-dbg                     - GCC support library (debug symbols)       
p   pocketpc-gcc                    - The GNU C compiler for Pocket PC          
p   ppu-gcc                         - PPU C compiler                            
p   spu-gcc                         - SPU cross-compiler (preprocessor and C com
apostol@Family:~$ sudo apt-get install gcc
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  gcc-4.1-doc libpopt-dev g++-4.1 refblas3 lapack3 libstdc++6-4.1-dev
  libcrypto++6 gcc-4.1-multilib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gcc-3.3-doc (1:3.3.6-15ubuntu4) ...
sh: cannot open /usr/share/info/gcc-3.3.info.gz: No such file
install-info(/usr/share/info/gcc-3.3.info.gz): 
dpkg: error processing gcc-3.3-doc (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gcc-3.4-doc (3.4.6-6ubuntu3) ...
sh: cannot open /usr/share/info/gcc-3.4.info.gz: No such file
install-info(/usr/share/info/gcc-3.4.info.gz): 
dpkg: error processing gcc-3.4-doc (--configure):
 subprocess post-installation script returned error exit status 2
[B]Errors were encountered while processing:
 gcc-3.3-doc
 gcc-3.4-doc[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)

I get that bolded error EVERYTIME i install and now uninstall anything which causes it to fail. It caused my upgrade to Hardy Heron to error even though it seems that i am upgraded.

---

### Post by kulotzy on 2008-04-26
Well now i cant even uninstall them either... whats wrong with this.....

---

### Post by SunnyRabbiera on 2008-04-26
well you know you dont have to compile from source right?
you can use the repositories (though they will be pretty shaky for a little while now)

---

### Post by kulotzy on 2008-04-26
> **SunnyRabbiera said:**
> well you know you dont have to compile from source right?
you can use the repositories (though they will be pretty shaky for a little while now)

Sorry... Lol.. i didnt understand anything you said. Im new to Linux and all... all i practically know how to do is sudo apt-get install/remove


[B]Errors were encountered while processing:
gcc-3.3-doc
gcc-3.4-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

I get that bolded error EVERYTIME i install and now uninstall anything which causes it to fail. It caused my upgrade to Hardy Heron to error even though it seems that i am upgraded.

---

### Post by artir on 2008-04-26
try sudo dpkg --configure -a

---

### Post by oskar2000 on 2008-04-26
Try sudo apt-get autoremove like apt suggests.
Then do a sudo apt-get update&& sudo apt-get upgrade

---

### Post by kulotzy on 2008-04-26
> **artir said:**
> try sudo dpkg --configure -a


Hey thanks for replying, however, well here's the output:

> ~$ sudo dpkg --configure -a
Setting up gcc-3.3-doc (1:3.3.6-15ubuntu4) ...
sh: cannot open /usr/share/info/gcc-3.3.info.gz: No such file
install-info(/usr/share/info/gcc-3.3.info.gz): 
dpkg: error processing gcc-3.3-doc (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gcc-3.4-doc (3.4.6-6ubuntu3) ...
sh: cannot open /usr/share/info/gcc-3.4.info.gz: No such file
install-info(/usr/share/info/gcc-3.4.info.gz): 
dpkg: error processing gcc-3.4-doc (--configure):
 subprocess post-installation script returned error exit status 2
[B]Errors were encountered while processing:
 gcc-3.3-doc
 gcc-3.4-doc[/B]

---

### Post by kulotzy on 2008-04-26
> **oskar2000 said:**
> Try sudo apt-get autoremove like apt suggests.
Then do a sudo apt-get update&& sudo apt-get upgrade

> apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libg2c0-dev libg2c0
The following packages will be REMOVED:
  libg2c0 libg2c0-dev
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 1143kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145442 files and directories currently installed.)
Removing libg2c0-dev ...
Removing libg2c0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up gcc-3.3-doc (1:3.3.6-15ubuntu4) ...
sh: cannot open /usr/share/info/gcc-3.3.info.gz: No such file
install-info(/usr/share/info/gcc-3.3.info.gz): 
dpkg: error processing gcc-3.3-doc (--configure):
 subprocess post-installation script returned error exit status 2
Setting up gcc-3.4-doc (3.4.6-6ubuntu3) ...
sh: cannot open /usr/share/info/gcc-3.4.info.gz: No such file
install-info(/usr/share/info/gcc-3.4.info.gz): 
dpkg: error processing gcc-3.4-doc (--configure):
 subprocess post-installation script returned error exit status 2
[B]Errors were encountered while processing:
 gcc-3.3-doc
 gcc-3.4-doc[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks but i got the same error... cant i use the 7.10 CD to reinstall this or something...?

---

### Post by SunnyRabbiera on 2008-04-26
alright well you still really dont need to compile source unless its needed, take a look at this guide:
[look here]("http://monkeyblog.org/ubuntu/installing/")
its pretty universal and good for all versions :D

---

### Post by kulotzy on 2008-04-26
> **SunnyRabbiera said:**
> alright well you still really dont need to compile source unless its needed, take a look at this guide:
[look here]("http://monkeyblog.org/ubuntu/installing/")
its pretty universal and good for all versions :D

Thanks, but because im missing those two files...things, it seems i cant install or uninstall anything at all from the terminal, from the update manager, or synaptic package manager.

---

### Post by marquee moon on 2008-04-26
are you upgrading or doing a clean install? 
Last night I tried installing a 7.10 command line system and when I.. 

   *sudo aptitude update *

...I had a very similar error message to yours. I think something's happened to the repositories. I was accessing canonical UK. I may well be wrong here, but I've never had this error message before. 

I tried twice & the same thing happened twice. I decided to format that partition and start again. I tried installing Gparted on my other partition (running 7.04), and found that "Add/Remove and "Synaptic Package Manager" didnt work. I'm not sure what's happend, but the fact that I've had *exactly* the same as you suggests that its something external.

I gave up triying to get things working and just downloaded the 8.04 alternate install ISO. That worked first time absolutely perfectly (I directed the installation to the previously partly installed command line partition, which it then formated & re-installed on top of)

So if all else fails, backup your "home" files, format that partition & do a clean install from 8.04. Gparted (partition manager) is on the live CD.

---

### Post by kulotzy on 2008-04-26
> **marquee moon said:**
> are you upgrading or doing a clean install? 
Last night I tried installing a 7.10 command line system and when I.. 

   *sudo aptitude update *

...I had a very similar error message to yours. I think something's happened to the repositories. I was accessing canonical UK. I may well be wrong here, but I've never had this error message before. 

I tried twice & the same thing happened twice. 

I downloaded the 8.04 ISO and that worked first time absolutely perfectly. 

So if all else fails, backup your "home" files, format that partition & do a clean install from 8.04.

Thanks for the suggestion. 

Im not trying to upgrade or anything, its just that everytime i try to install something ie WINE, i get those errors and it fails. When i upgraded, i got those errors which cause my upgrade to Heron fail BUT i checked "About Ubuntu" and it said that i AM upgraded to Heron.

What is "home"? All my files that i saved (ie. openoffice documents, pictures) are in it? Just clarifying, im really not sure what it is.

That though... it seems like everytime i encounter a problem, i have to do a clean install... ive already done it about 5 times...... so yeah, im pretty reluctant to do it because its been so repettive...i guess im just going to go ahead and download 8.04 for now (is still have 7.10) until hopefully someone can provide a different solution.

---

### Post by marquee moon on 2008-04-26
if its like my problem, it gets 95% or so through the update, then fails on the last few. 
I'd suggest (but no expert by any means...)that this means that when you've tried to upgrade to 8.04, most (or at lease some) of the files will have been successfully installed, but others wont. 

The package managers arent reading the repositories correctly. So whatever you try to install, whether its a a little add-on or whether its the whole hardy-heron upgrade wont work properly. 

Unless someone comes along to tell you (us) how to reconfigure your package managers, I'd recommend going with the clean install. 

Its personal prefference, but a clean install of 8.04 is likely to run faster, smoother and with less funky glitches than an upgrade from 7.10 (at least, this is what I found with 7.04>7.10)

You "home" is the directory where your personal files are saved in, like 'documents', 'pictures', 'music' etc... The file structure is automatically created during the install. Just drop these personal files onto a memory stick, then re-install. You'll be sorted in an hour or so, rather than spending a day or two trying to sort it out.

---

### Post by marquee moon on 2008-04-26
> **kulotzy said:**
> That though... it seems like everytime i encounter a problem, i have to do a clean install... ive already done it about 5 times...... so yeah, im pretty reluctant to do it because its been so repettive...i guess im just going to go ahead and download 8.04 for now (is still have 7.10) until hopefully someone can provide a different solution.

I know what you mean, but re-installing becomes so common place that its no-longer a problem or a pain. If I get into dificulty, I know that I can be back to a perfect, pristine system within an hour or two.

In my view, that's how I learn. I try odd things out, I fiddle and muck about. Sometimes it works & I've learned something good, other times I just give up & re-install. Hopefully as I understand more, the re-installs will become less frequent. Untill then, its a valuable tool.

---

### Post by kulotzy on 2008-04-26
> **marquee moon said:**
> if its like my problem, it gets 95% or so through the update, then fails on the last few. 
I'd suggest (but no expert by any means...)that this means that when you've tried to upgrade to 8.04, most (or at lease some) of the files will have been successfully installed, but others wont. 

The package managers arent reading the repositories correctly. So whatever you try to install, whether its a a little add-on or whether its the whole hardy-heron upgrade wont work properly. 

Unless someone comes along to tell you (us) how to reconfigure your package managers, I'd recommend going with the clean install. 

**Its personal prefference, but a clean install of 8.04 is likely to run faster, smoother and with less funky glitches than an upgrade from 7.10 (at least, this is what I found with 7.04>7.10)**

You "home" is the directory where your personal files are saved in, like 'documents', 'pictures', 'music' etc... The file structure is automatically created during the install. Just drop these personal files onto a memory stick, then re-install. You'll be sorted in an hour or so, rather than spending a day or two trying to sort it out.

Thanks, im leaning towards that. IF i dont find an immediate solution (ive become impatient because i had reinstalled and had to do clean installs several times already) i might just have to.

---

### Post by kulotzy on 2008-04-26
> **marquee moon said:**
> I know what you mean, but re-installing becomes so common place that its no-longer a problem or a pain. If I get into dificulty, I know that I can be back to a perfect, pristine system within an hour or two.

In my view, that's how I learn. I try odd things out, I fiddle and muck about. Sometimes it works & I've learned something good, other times I just give up & re-install. Hopefully as I understand more, the re-installs will become less frequent. Untill then, its a valuable tool.

After the first couple of clean installs, i was smart enough to get an external hard drive and just back up everything, i dont save anything on my hard drive, i save it in my external. Even if i did save something, i would later transfer it just in case something like this happens again (im sure it wont be the last).

My windows crashed which prompted me to completely switch to Linux... before i DID crash, i was lucky enough to move all my videos, pictures, documents to the external drive (it crashed just moments soon after). Since then, ive been backing everything up.

---

### Post by brigadoon on 2008-04-27
I have a GeForce 420 Go on my Toshba Satellite 1415-S173. I upgraded to the new version of Ubuntu today ( Sunday April 27, 2008 ). I was hit by the gcc-3.3-doc and gcc-3.4-doc bug as well. This is defined as a bug by the Ubuntu team. I usually wait a month or two before installing a new Ubuntu version because of bugs like this. The bug and work around may be found at the following link...

[https://bugs.launchpad.net/ubuntu/+source/gcc-3.4/+bug/205348](https://bugs.launchpad.net/ubuntu/+source/gcc-3.4/+bug/205348)

A note to new linux users. The work around is simple enough. Just make sure you type "sudo" at the front of each command line. The fix is for the 3.4 files. To work around the 3.3 file change the 3.4 to 3.3 in the command lines.

It seems to work for me. Back up first though!!! [-o<

---

### Post by mlanza on 2008-05-02
I am having the same problem and I did do a complete REINSTALL after formatting the harddrive.  I am reluctant to do this again, because I could take the same steps that created the issue in the first place.  It makes more sense to learn how to correct the issue.  The reinstall process takes 4-5 hours for me since I'm reconfiguring lots of things for a Ruby development environment.

Has anyone corrected this issue?

EDIT: nevermind, I followed the above link and corrected the issue.

---

### Post by bunny rabbit on 2008-05-03
Thanks brigadoon.

This error was the first one that worried me since I got started with Ubuntu, and yet it was really easy to fix it with those command lines. Good that you pointed out to edit the command lines for the 3.3 files.

---

