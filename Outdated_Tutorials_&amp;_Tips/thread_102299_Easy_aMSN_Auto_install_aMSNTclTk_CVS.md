---
title: "Easy aMSN: Auto install aMSN/Tcl/Tk CVS"
date: 2005-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2005-12-11
Hello


I was tired of re-installing aMSN, tcl and tk from CVS everytime i format or I want to update them, so i have made an automated script that will do all the needed tasks to get a working version of aMSN CVS with Tcl/Tk CVS.

so this script will do the following:

1- if ~/easyamsn folder does not exist
It will check for packages cvs, tcl8.4-dev tk8.4-dev, esound-clients and buil-essential and it will install the missing ones, then it will check for ~/.cvspass if it does not exist it will create one, if it does exist it will check for amsn,tcl and tk logins insert the missing ones into the file,

next it will create a folder located at ~/easyamsn where it will put all required folders/files, meaning all CVS files will be downloaded to that folder compiled there too, it will download msn, amsn-extras (contains all CVS plugins and skins) tcl and tk, compile and install tcl and tk with /usr/local/ prefix compile msn and copy it to ~/msn (if ~/msn exists it will be moved to ~/easyamsn/backup) and it will copy the amsn-extras/plugins and amsn-extras/skins to ~/.amsn folder (again if they already exist they will get moved to ~/easyamsn/backup)

it will check if the file ~/amsn exists if not it will create it, insert the code that will launch amsn and chmod it with +x flag

it will check if the ~/.local/share/applications/amsn.desktop exists if not it will be also created to have aMSN menu item under Applications -> Internet

2- if ~/easyamsn folder does exist
it will just update the updated CVS files of tcl/tck and aMSN, compile them and install them, very usefull to get updated...

Easy aMSN is Licensed under GPL you can find a copy of GPL License inside the compressed file...

Now how to get this script working and how to use it
open Terminal ( Applications -> Accessories -> Terminal )
```

cd /tmp
wget http://wael.nasreddine.com/files/ubuntu/easyamsn.tar.gz
tar xzvf easyamsn.tar.gz
cd easyamsn
sudo ./install

```

now Easy aMSN has been installed on your system under /usr/local/easyamsn, to launch it just go to Applications -> System Tools -> Easy aMSN



it has been tested only on Breezy Badger, i tested it with an already installed/customized system and on Livecd

Hope it helps.

Sources for some things used in this script:
[HOWTO: Install & run latest CVS amsn](http://www.ubuntuforums.org/showthread.php?t=75276)
[HOW-TO: De-uglify aMSN.](http://www.ubuntuforums.org/showthread.php?t=84765)

---

### Post by Gandalf on 2005-12-12
Script has been updated to check (and install if not found) for esound-clients

---

### Post by ykpaiha on 2005-12-12
fine but sorry it didn't backup any plug-in and skin
and didn't download others than standards one....

---

### Post by Gandalf on 2005-12-12
[QUOTE=ykpaiha]fine but sorry it didn't backup any plug-in and skin
and didn't download others than standards one....[/QUOTE]
it will download what is [here](http://cvs.sourceforge.net/viewcvs.py/amsn/amsn-extras/)

---

### Post by Sebby on 2005-12-16
Wow, great idea. I plan on formatting soon, so I'll give it a try then. :)

---

### Post by Gandalf on 2005-12-16
[QUOTE=Sebby]Wow, great idea. I plan on formatting soon, so I'll give it a try then. :)[/QUOTE]
don't forget to report bugs and/or problems if any :D

---

### Post by Septicaemia on 2005-12-16
Well, it failed overall, but it downloaded Tcl and Tk alright, and compiled them just fine. aMSN did not run afterwards, and it had numerous errors during the make process, in fact I don't think it even made at all.

You should also include instructions on how to appropriately remove what the script does if it fails.:cool:

---

### Post by Gandalf on 2005-12-16
it will produce errors only if the CVS closed the connection which can be because u have made may connections to CVS today, i've tried it about (ummm let's see 50 times :roll: ) on different machines (i made it because i wanted it mainly) and nothing went wrong :roll:

---

### Post by ersplus on 2005-12-21
Great job, thanks !

---

### Post by Juippisi on 2005-12-21
When it comes to aMSN, Gandalf is always on view ;-).

No but, great job - again. And thanks - again ;-).

---

### Post by henriquemaia on 2005-12-21
Great job!

Worked flawlessly. Thanks a lot, Gandalf.

---

### Post by Gandalf on 2005-12-21
you're welcome :)

---

### Post by purdy hate machine on 2005-12-21
How can I remove amsn from my pc if I have installed it using this method? Thanks.

---

### Post by Gandalf on 2005-12-21
you delete the folders ~/.amsn and ~/amsn-received

if you want to remove tcl/tk too then go to the source folder
cd ~/easyamsn/tcl
sudo make uninstall
cd ~/easyamsn/tk
sudo make uninstall

that should do it

---

### Post by rhipwell on 2005-12-22
Prior to giving this script a try I was using Amsn 0.94 and it worked, but was ultra ugly. I figured if I am going to beautify amsn, I may as well use the cvs. 

So I ran the script and now when I launch amsn I get a window wanting to download the tcltls package. I have tcltls installed on my breezy system so I back out of that window and provide the path ( /usr/lib ) in the preferances window of amsn with no resolve. 

I have also tried the installation method offered by amsn with no resolve. 

Any ideas?

---

### Post by trash on 2005-12-28
sweet script Gandalf!
It work perfectly on my mac running Dapper but on my x86 running Breezy starting up Amsn complains about wish and a directory not exsisting, though the script itself ran without complaint... any ideas?

---

### Post by Gandalf on 2005-12-28
dont you have a wish8.5 in /usr/local/bin folder?
```

ls /usr/local/bin |grep wish

```

---

### Post by trash on 2005-12-28
hmm no i don't but whereis tells me i do have usr/bin/wish8.4... have i missed an upgrade somewhere?

---

### Post by Clement on 2005-12-29
Thank you Gandal it works well :D
nice job and very useful :)

no problem with installation

---

### Post by Gandalf on 2005-12-29
[QUOTE=trash]hmm no i don't but whereis tells me i do have usr/bin/wish8.4... have i missed an upgrade somewhere?[/QUOTE]
re-run the script again something have happened i think..

@Clement, youre welcome :D

---

### Post by trash on 2005-12-29
i've run it a good 5 times now, deleting files and directories, starting from scratch but nothing helps and now i can't get further than downloading tcl files or configuring tcl when i'm asked for a password and then the script just exits. I guess there is a conflict somewhere... thanks anyway.

---

### Post by Sebby on 2006-01-01
Hi Gandalf

A couple of questions...

What happens now that aMSN 0.95 final has been released?

Also, I just tried to use your script, but the easyamsn.tar.gz file cannot be found. :(

---

### Post by Gandalf on 2006-01-01
i just saw the release of amsn final, great !

am sorry about the script i'm replacing debian with ubuntu on my server so all my sites are currently down!! they will be up by tomorrow!

---

### Post by Sebby on 2006-01-01
Great stuff, Gandalf. :smile: 

[QUOTE=Gandalf]i just saw the release of amsn final, great ![/QUOTE]
So what will happen about this? Will your Easy aMSN script use this latest version?

---

### Post by Gandalf on 2006-01-01
Yes for sure, i will change it, for the moment it download CVS version, but later i will change it to install stable 0.95 version!

---

### Post by Sebby on 2006-01-01
[QUOTE=Gandalf]Yes for sure, i will change it, for the moment it download CVS version, but later i will change it to install stable 0.95 version![/QUOTE]
Okay great, I will wait for the updated script. :D

---

### Post by Bavo on 2006-01-02
Nice script, but it didn't work out of the box for me.

It installed cvs via apt-get and something else (i guess gcc) but it also needs **make** and **g++**

after installing those packages it went perfectly.

Edit: you should also install libxft-dev if you don't want it to look ugly

---

### Post by rado_london on 2006-01-02
Hey guys I installed everything, even libxft-dev, but I still have ugly fonts.

Can someone help me?

---

### Post by patrick295767 on 2006-01-06
[QUOTE=Gandalf]Hello


I was tired of re-installing aMSN, tcl and tk from CVS everytime i format or I want to update them, so i have made an automated script that will do all the needed tasks to get a working version of aMSN CVS with Tcl/Tk CVS.

so this script will do the following:

1- if ~/easyamsn folder does not exist
It will check for packages cvs, tcl8.4-dev tk8.4-dev, esound-clients and buil-essential and it will install the missing ones, then it will check for ~/.cvspass if it does not exist it will create one, if it does exist it will check for amsn,tcl and tk logins insert the missing ones into the file,

next it will create a folder located at ~/easyamsn where it will put all required folders/files, meaning all CVS files will be downloaded to that folder compiled there too, it will download msn, amsn-extras (contains all CVS plugins and skins) tcl and tk, compile and install tcl and tk with /usr/local/ prefix compile msn and copy it to ~/msn (if ~/msn exists it will be moved to ~/easyamsn/backup) and it will copy the amsn-extras/plugins and amsn-extras/skins to ~/.amsn folder (again if they already exist they will get moved to ~/easyamsn/backup)

it will check if the file ~/amsn exists if not it will create it, insert the code that will launch amsn and chmod it with +x flag

it will check if the ~/.local/share/applications/amsn.desktop exists if not it will be also created to have aMSN menu item under Applications -> Internet

2- if ~/easyamsn folder does exist
it will just update the updated CVS files of tcl/tck and aMSN, compile them and install them, very usefull to get updated...

Easy aMSN is Licensed under GPL you can find a copy of GPL License inside the compressed file...

Now how to get this script working and how to use it
open Terminal ( Applications -> Accessories -> Terminal )
```

cd /tmp
wget http://wael.nasreddine.com/files/ubuntu/easyamsn.tar.gz
tar xzvf easyamsn.tar.gz
cd easyamsn
sudo ./install

```

now Easy aMSN has been installed on your system under /usr/local/easyamsn, to launch it just go to Applications -> System Tools -> Easy aMSN



it has been tested only on Breezy Badger, i tested it with an already installed/customized system and on Livecd

Hope it helps.

Sources for some things used in this script:
[HOWTO: Install & run latest CVS amsn](http://www.ubuntuforums.org/showthread.php?t=75276)
[HOW-TO: De-uglify aMSN.](http://www.ubuntuforums.org/showthread.php?t=84765)[/QUOTE] 
  
I followed the step of this amazing and great script, 
I do from xterm 
./amsn 
from the created stuffs 
and I get :
segmentation fault.
  
Someone would know how to make it run amsn 0.95 ?
  
Thnak you very much !!
  
Pat'

---

### Post by trash on 2006-01-14
for those who are having troubles getting Easyamsn to complete the install here's what has worked for me on Breezy and Dapper, both x86 and ppc...
restart your machine after each time you run the script and it fails, dunno why but it helps! at best I needed to run the script/reboot twice at worst it took 5 attempts before the script finished.
hope it helps.

---

### Post by jonny_boy27 on 2006-01-15
[QUOTE=rado_london]Hey guys I installed everything, even libxft-dev, but I still have ugly fonts.[/QUOTE]
same here :S

---

### Post by darkwings on 2006-01-20
uhm, hello, just wanted to say that the script seemed to work, i had no problems during install of it, but when i go to home/amsn/ an click the icon or right click and  tell it to run in a terminal, nothing happens, i have tried most of the previous suggestions with no results :( , i admit i wasnt paying full attention and did initially install it thru KDE, but quickly redid it under GNOME, still no use...didnt mean to piss anyone off if i posted in the wrong spot. new to this thread stuff :???: 
b.t.w. Gandalf...i like how you explain stuff...its clear and to the point..plus your lil icon guy is cool later.
DW

(edit)...i also just realized that im still on Hoary, yet the script says it'll do this for Breezy...would this make a difference as well?

---

### Post by benjy on 2006-01-26
HI there, I've used the script and unfortunately had a couple of problems the first few times but after a couple of attempts it looks like all is well.

Or not quite. When I click the link in the applications menu to run aMSN I get a small dialog box saying:

"You can't load TkCximage, this is now needed to run aMSN. Please compile aMSN first, instructions on how to compile are located in the file INSTALL."

Sadly, the text of this looks brilliant...

If i do attempt to compile aMSN manually with the following command:

"sudo make -f ./easyamsn/msn/Makefile"

I get:

"CXX     /home/benjy/easyamsn/msn/utils/TkCximage/src/TkCximage.cpp.o
make: g++: Command not found
make: *** [/home/benjy/easyamsn/msn/utils/TkCximage/src/TkCximage.cpp.o] Error 127
"

Interestingly if I run the amsn in /easyamsn/amsn i get exactly the same dialog box just with naff looking text. I don't know how helpful that is... just thought i'd throw it in there.

Hope you can help.

Addendum: My attempts to uninstall where met with:

"make: *** No rule to make target `uninstall'.  Stop."

I don't really know what to make of that... i don't tend to compile a lot... and this is a new install of breezy so I haven't amassed a lot of those "needed" little things...

FIXED:

Ulrika (ka ka ka...) I went back to the original guide for installing amsn from CVS and installed the dependencies listed at the top, restarted then started easyamsn again - and it compiled! It couldn't get the plugins or skins from cvs though... but I'm not too fussed about that.

Cheers

Benjy

---

### Post by babygigi on 2006-01-26
Hum... i've done this before and its worked... wahts wrong this time?

> cd /tmp
wget [http://wael.nasreddine.com/files/ubuntu/easyamsn.tar.gz](http://wael.nasreddine.com/files/ubuntu/easyamsn.tar.gz)
tar xzvf easyamsn.tar.gz
cd easyamsn
sudo ./install

*[EDIT]hum... i guess the site was just down...nm

---

### Post by babygigi on 2006-01-30
I've tried a few times installing and re-installing yet it wont' open! i just dn't know y? anybdoy know y? and how to solve it?

---

### Post by Gandalf on 2006-01-30
Guys, This was meant to be used to get amsn CVS version, aMSN 0.95 was out officially a while so no need to use this!
though if u wanna use it for tcl/tk then tell me, i'll update it in order to be CVS for Tcl/Tk and use sources of the new MSN to compile with tcl/tk!

---

### Post by zer on 2006-02-11
Yes, sure i want that :D
I got amsn 0.96cvs working but now i have dapper i forgot how that worked ^^'

Thanks for your great work!

---

### Post by Marvelous on 2006-03-25
the download link seems to be dead.. any alternatives ?
thanks

---

### Post by Anti-Establishment on 2006-04-10
How do I completely remove easy amsn so that when I go to Applications - System Tools it won't be there?

---

### Post by OrganicPanda on 2006-04-13
I've got it all working using the easyaMSN script (thank you very much by the way, you are a legend) and i'm using the ubuntu human skin and wondering why the font's look so terrible, I heard something about AA font's but I don't know quite how to achive that ... any help?

---

### Post by NoWhereMan on 2006-04-13
[QUOTE=OrganicPanda]I've got it all working using the easyaMSN script (thank you very much by the way, you are a legend) and i'm using the ubuntu human skin and wondering why the font's look so terrible, I heard something about AA font's but I don't know quite how to achive that ... any help?[/QUOTE]

see [http://ubuntuforums.org/showthread.php?t=84765&highlight=de-uglify](http://ubuntuforums.org/showthread.php?t=84765&highlight=de-uglify)

---

### Post by DuckMan on 2006-04-16
the script installed all in my personal dir (a little troublesome for a n00b like me), but worked.

But when i open the new amsn, and i try to log in, shows me an "TK error" and the login process never end.. i see the antialiased fonts, and the new cool skin but it doesnt work..

if someone can help me..

bye!

(sorry for my english)

---

### Post by NoWhereMan on 2006-04-16
try to redownload the package (if you used the http tunnel option it is a known bug, now should be fixed)

---

### Post by DuckMan on 2006-04-16
i downloaded with firefox, and i follow the instructions, but stills giving the "TK error" :( what happens?

---

### Post by Maelgwyn on 2006-04-20
I'm using Dapper, so I shouldn't really expect anything other than this, but I got the following message after TCLS had downloaded/installed at aMSN's request:

```

can't find package msnSOAP
    while executing
"package require msnSOAP"
    (file "msnp13.tcl" line 1)
    invoked from within
"source msnp13.tcl"
    ("v" arm line 8)
    invoked from within
"switch [ns cget -stat] {
		a {
			#Send three first commands at same time, to it faster
			if { [::config::getKey protocol] == 11 } {
				::MSN::Write..."
    (procedure "cmsn_auth" line 7)
    invoked from within
"cmsn_auth $item"
    ("VER" arm line 2)
    invoked from within
"switch [lindex $item 0] {
			MSG {
				cmsn_ns_msg $item $message
				return 0
			}
		    	IPG {
			    ::MSNMobile::MessageReceived "$message"
			   ..."
    (procedure "cmsn_ns_handler" line 17)
    invoked from within
"cmsn_ns_handler $command $message"
    ("default" arm line 2)
    invoked from within
"switch [lindex $command 0] {
				ILN {
					if {$::msnp13} {
						$self handleILN $command
					} else {
						cmsn_ns_handler $command $message
				..."
    (procedure "::NS::Snit_methodhandleCommand" line 27)
    invoked from within
"$options(-name) handleCommand $command"
    (procedure "::Connection::Snit_methodreceivedData" line 38)
    invoked from within
"ns receivedData"

```

---

### Post by WishMaster on 2006-05-02
msnSOAP is being used for 'Games' or so...

Open up a terminal:
```
cd /home/<user-name>/.amsn/plugin
ls
rm -Rf games
```

The "ls" command gives a list of all files in the directory.
"rm -Rf" removes a file.

Use "ls" to see the correct name of "games", and then use "rm" to remove it.
Restart aMSN & it works :)

---

### Post by aysiu on 2006-05-02
I know this script gets the CVS, but if Breezy users just want a quick and dirty installation of version 0.95, here's a script for you: ```
gedit getamsn.sh
``` in Gnome or ```
kwrite getamsn.sh
``` in KDE. Then paste in this code: ```
#!/bin/bash
cd
wget -c http://superb-west.dl.sourceforge.net/sourceforge/amsn/amsn_0.95-3.ubuntu.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0-2_i386.deb
sudo dpkg -i tcltls_1.5.0-2_i386.deb
sudo dpkg -i amsn_0.95-3.ubuntu.deb
sudo mv amsn_0.95-3.ubuntu.deb /var/cache/apt/archives/amsn_0.95-3.ubuntu.deb
sudo mv tcltls_1.5.0-2_i386.deb /var/cache/apt/archives/tcltls_1.5.0-2_i386.deb
``` Save and exit. ```
chmod +x getamsn.sh
./getamsn.sh
```

---

### Post by richbarna on 2006-05-04
aysiu rocks !!!
This person is a newbie God !!
Where is the terminal ? info :-10 points
Instructions ? Just cut and paste :-10 points
How cool is that?
Thanks aysiu,

---

### Post by aysiu on 2006-05-04
Can I take it from your response that... it worked?

---

### Post by wblancqu on 2006-05-05
Changed the script because aMSN works with SVN now. Also changed the CVS access lines. They didn't work anymore. This version of Easy aMSN also downloads Tile and Tile-themes for use with the Chameleon-plugin in aMSN.

Nevertheless, great work Gandalf

---

### Post by u.b.u.n.t.u on 2006-06-11
Hi,

How long is the process meant to take?

```
make: *** No rule to make target `/home/name/easyamsn/tcl/unix/Makefile'.  Stop.
/usr/local/easyamsn/easyamsn: line 108: 19656 Terminated              zenity --p rogress --pulsate --title "Easy aMSN" --text "Getting Tcl CVS Files"
/usr/local/easyamsn/easyamsn: line 108: 19811 Terminated              zenity --p rogress --pulsate --title "Easy aMSN" --text "Configuring Tcl"
make: /home/name/easyamsn/tcl/unix/Makefile: No such file or directory
make: *** No rule to make target `/home/name/easyamsn/tcl/unix/Makefile'.  Stop.
```

I followed the instruction at this webage:
[http://wael.nasreddine.com/Articles/Articles/Easy_aMSN.html](http://wael.nasreddine.com/Articles/Articles/Easy_aMSN.html)

There is a little window endlessly "Getting Tk CVS Files".

The problem I tried to fix was not being able to send files.

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-11
How do I uninstall this "Easy aMSN"? It didn't install properly and I want to delete it.

Thanks.

---

### Post by NoWhereMan on 2006-06-11
[QUOTE=u.b.u.n.t.u]How do I uninstall this "Easy aMSN"? It didn't install properly and I want to delete it.

Thanks.[/QUOTE]

probably just

```
rm -Rf ~/easyamsn
```

to remove recursively all the content of the directory
or, open your home in nautilus and delete easyamsn directory

---

### Post by u.b.u.n.t.u on 2006-06-11
/easyman is empty, no hidden files either.

Yet it downloaded a whole lot. I want to remove everything it did, thanks.

edit

that program has a link in Applications > System Tools and also resides in  usr/bin.

Is there an uninstall to completely get rid of it?

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-11
[QUOTE=NoWhereMan]probably just

```
rm -Rf ~/easyamsn
```

to remove recursively all the content of the directory
or, open your home in nautilus and delete easyamsn directory[/QUOTE]

NoWhereMan, your instructions are incomplete and therefore wrong. I want to completely unistall "easyamsn" as it doesn't work, and not just remove one directory, which your instructions would yield.

Thanks.

---

### Post by NoWhereMan on 2006-06-12
I'm sorry not to be able to help you. It's strange; I had a look at where the script save the files and they aren't where they're supposed to be, so I suppose they've been already deleted by easy amsn itself (it's only a supposition as i NEVER used it). 
by the way the installer puts files in:

/usr/local/easyamsn/*

/usr/share/applications/easyamsn.desktop

/usr/bin/easyamsn

looks like the process stopped right before downloading anything from cvs. whatever it's been downloaded should be packages you can find right in synaptic 

they're cvs, gcc, tcl8.4-dev, tk8.4-dev, esound-clients

This should make it
```
sudo apt-get remove cvs gcc tcl8.4-dev tk8.4-dev esound-clients
```

I've NEVER used easyamsn. I downloaded the script, opened it, read it and tried to figure out what have been done.

HTH

bye

---

### Post by panurge77 on 2006-06-15
Amsn is not using cvs anymore. They moved to svn

---

### Post by Gandalf on 2006-06-15
[QUOTE=panurge77]Amsn is not using cvs anymore. They moved to svn[/QUOTE]
And that is wayyyy better, I'll update the script later on, thx for the info...

---

### Post by pek on 2006-07-23
did you manage to do the update?

---

### Post by voodoonirvana on 2006-09-10
This is great, thanks!

---

### Post by voodoonirvana on 2006-09-10
When I go to usr/local/easyamsn I click on the icon but nothing happens...am I missing something? Im new to this stuff.

---

### Post by vivia on 2006-09-11
aMSN is now using svn (subversion) instead of cvs. The script above needs to be modified accordingly.

---

### Post by vivia on 2006-09-11
If you have tried to run easyamsn but failed, this means you have all required packages installed. You might want to :

```
wget http://amsn.sourceforge.net/amsn_dev.tar.gz
tar xvfz amsn_dev.tar.gz
cd amsn
./configure
make
sudo make install
```

That should work.

---

