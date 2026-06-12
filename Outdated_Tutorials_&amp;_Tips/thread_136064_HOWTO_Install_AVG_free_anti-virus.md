---
title: "HOWTO: Install AVG free anti-virus"
date: 2006-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2006-02-25
**[size=5]AVG Linux Free Edition - Do not exist anymore[/size]**


**Tested in Feisty x86**
**For Ubuntu 64-bit: [http://ubuntuforums.org/showthread.php?p=3840641](http://ubuntuforums.org/showthread.php?p=3840641)**



**This guide have been totally rewritten due to the support of an avg.deb package.**


If you're looking for Anti-virus to protect Windows OS, network, servers etc. via your Linux system, you might use this instead: [HOWTO: Install F-Prot anti-virus](http://ubuntuforums.org/showthread.php?t=88357)

This one is for paranoid single home users ;) 


**NOTE:** It can only scan, no more no less!


============================================================


Q: **Is viruses, trojans and malware a threat to a linux system as in Windows?**

A: No, there's a very few viruses to linux and the way a Linux/unix is build up makes it difficult to do any serious damage to the system, in fact I've never heard from people who got their Linux/unix system infected.

Q: **So why install a anti-virus application/program?**

A: For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running network, server or dual booting with win OS this tool can be very handy to scan and delete viruses.

Q: **I'm a home user only running Linux do I need it?**

A: No, a firewall is way better as protection in that case.



============================================================

**_Before Installation_**

Make sure that your sourcelist is set up correctly. If you are in doubt make a search on the forum.



**_Installation_**

Download The Free AVG Advisor from [here (.deb)](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl) to your **Desktop**.

```

cd ~/Desktop
sudo dpkg -i avg75fld-r45-a0973.i386.deb
```



**_Launcher**_

Making a launcher to start AVG

```
sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktop
```

add:
```
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
```
save and exit.

You can now start AVG by going to Applications tab ---> System Tools.



======================================================

If people want to discuss security about virus' and firewall if it needed or not, also a good place to see peoples opinion on this matter: [http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616)

---

### Post by knalle on 2006-02-25
great stuff! thanks a lot!

---

### Post by Klaidas on 2006-02-25
Rebooting to ubuntu, gotta try this! ;)

---

### Post by bierpullen on 2006-02-25
Worked like a charm. Thanks :D 




------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu](http://www.antarctica-rbak.nl/ubuntu)

---

### Post by Matchless on 2006-02-25
[QUOTE=Artificial Intelligence]
This one is for paranoid single home users ;) 

Q: **Is viruses, trojans and malware a threat to a linux system as in Windows?**

A: No, there's a very few viruses to linux and the way a Linux/unix is build up makes it difficult to do any serious damage to the system, in fact I've never heard from people who got their Linux/unix system infected.

Q: **So why install a anti-virus application/program?**

A: For an ordinary Linux Home user with only one OS system their's no need for Anti-virus, but people who's running network, server or dual booting with win OS this tool can be very handy to scan and delete viruses.

Q: **I'm a home user only running Linux do I need it?**

A: No, a firewall is way better as protection in that case.

F[/QUOTE]

Hi,
    Just my 2 cents worth. I see many linux users refering to "not really needing virus protection", but that is not really true. Linux may be fairly virus resistant, but we are continually exchanging files on the internet, on a LAN with other PC's and via email and other systems with users who are mostly using Windows. We will be passing on infected files to our friends and families who are using Windows if we do not scan our files for virus infections. ClamAV has been around for quite a while, but is one of the slowest programs to use that I have seen. Thanks to Artificial Intelligence we now have AVG and Fprot to use as well. My suggestion is that every Linux user should have a proper updated anti-virus program installed at all times and that Dapper should also come with one as a standard. We are in the real world here and must make sure that no-one is under any misconception here!
:twisted:

---

### Post by Perfect Storm on 2006-02-26
I know, that's why I wrote the howtos, but in the other hand I don't think we should paint the devil on the wall before it's actual is needed. 

For discussion about security, virus, firewall etc. there's a good thread here: [http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616)

---

### Post by gammagoat on 2006-02-26
GEEZ I dont know what I've done wrong , but at step 6 I get this

License type is FREE.
bigvern@ubuntu1:~/Desktop$ avggui &
[1] 9386
bigvern@ubuntu1:~/Desktop$ No module named pygtk
Traceback (most recent call last):
  File "main.py", line 24, in ?
    sys.exit(1)
NameError: name 'sys' is not defined

Think you all could tell me what I am doing wrong?:cry:

---

### Post by Perfect Storm on 2006-02-26
```
sudo apt-get install python2.4-gtk2
```

See if this helps.

---

### Post by gammagoat on 2006-02-26
ok did that and now.

No module named glade
Traceback (most recent call last):
  File "main.py", line 24, in ?
    sys.exit(1)
NameError: name 'sys' is not defined

---

### Post by yasenov on 2006-02-26
this question may be stupid but..
is it better than clamav?

---

### Post by Matchless on 2006-02-26
[QUOTE=gammagoat]ok did that and now.

No module named glade
Traceback (most recent call last):
  File "main.py", line 24, in ?
    sys.exit(1)
NameError: name 'sys' is not defined[/QUOTE]


Try installing python2.4-glade2, this and pythongtk as shown earlier is required to make avggui work

---

### Post by dcstar on 2006-02-26
[QUOTE=yasenov]this question may be stupid but..
is it better than clamav?[/QUOTE]
Clamav won't repair infected files (only delete them), looking at the documentation for AVG it has a command line run option to actually repair files.

And looking at the AVG Linux FAQ, these are the system requirements:

[I]Necessary libraries:

    * pygtk2.0 >= 2.0.0
    * pygtk2.0-libglade >= 2.0.0
    * python >= 2.2.2
    * libstdc++-libc6.2-2.so.3
    * libc.so.6
    * libexpat.so.0[/I]

---

### Post by r4ik on 2006-02-26
Thank you A.I worked (in Breezy) without any probs.
In Dapper avggui & has to be ran as root but i suspect that is old news.
Cant get a launcher in Dapper (big problem :) ) so i run it from the Terminal until i get it fixed.

---

### Post by Matchless on 2006-02-26
[QUOTE=yasenov]this question may be stupid but..
is it better than clamav?[/QUOTE]

This question comes up in the windows environment quite a bit. I suggest installing the Clamav, Windows version, as well as the free AVG and i.e. the free Avast one if you have a Windows PC. Otherwise do it on Ubuntu. Find a test virus by Googling and see which one detects these best. I look for a simple and user friendly interface, ease of updating the virus signatures, can it find the latest virii and whether it scans incoming and outgoing mail. Thereafter any other functions are a bonus. Clamav is very slow! AVG is an commercial program and free, so it normally detects all latest virii. I actually use the free Avast on my Windows PC which has the fasted signature update I have seen to date, about 20 seconds on a dial up, others can take up to an hour or more on a slow dialup. As we are mostly putting preventative measures in place for windows shared files containing virii, the rule of thumb may be to use what works well on Windows at the moment!!! This I am going to regret saying!
[-(

---

### Post by lotusleaf on 2006-02-26
*Edit: removed the text of this post to unclutter thread*

---

### Post by Perfect Storm on 2006-02-26
Updated: added the two packages.

---

### Post by Perfect Storm on 2006-02-26
[QUOTE=lotusleaf]FWIW: There's a tar.gz file for AVG for Linux if you don't want to bother downloading an .rpm file and using alien:

[http://www.grisoft.com/doc/71/lng/us/tpl/tpl01](http://www.grisoft.com/doc/71/lng/us/tpl/tpl01)
Look for "AVG 7.1 for Linux Workstation" near the bottom at the above linked page in the "AVG 7.1 for Linux" section.

Current version of it as of this posting: 7.1-23 [avglinux-7.1-23_avi0716.i386.tar.gz](http://www.grisoft.cz/softw/70/filedir/inst/lnx_lws_stf__7_1-23.dir/avglinux-7.1-23_avi0716.i386.tar.gz)[/QUOTE]

That's a trial version (30 days) not the free version.

---

### Post by lotusleaf on 2006-02-26
[QUOTE=Artificial Intelligence]That's a trial version (30 days) not the free version.[/QUOTE]

Thanks for the info, I haven't tried it yet. I'm going to send them an e-mail suggesting they make a .deb available for Ubuntu. :) Thanks for the howto with screenshots and all. :)

---

### Post by Perfect Storm on 2006-02-26
You're welcome ^^

Good idea about sending them a request for a .deb package. Going to do it myself too. Also if everybody else does it I think they'll do it.

---

### Post by maulattu on 2006-02-26
Nice howto ;)

---

### Post by gammagoat on 2006-02-26
Thanks Artificial Intelligence and Matchless. avg is working now.

---

### Post by spartan777 on 2006-02-26
thank you artificial intelligence so much, i'm running an ubuntu network server surrounded by windows comps. this helps much. somebody should get the easy ubuntu guys to add this, that would be brilliant.

---

### Post by Cousindaddy on 2006-02-27
The install went perfectly. 

So that I wouldn't forget the command needed to update AVG, I did the following:

ran **smeg** (or *Applications* > *System Tools* > *Applications Menu Editor*)

In the same folder that I had AVG (in my case, *Internet*) , I created a *New Entry*. entitled **AVG UPdate**.

In the **Command** line I entered: *sudo /opt/grisoft/avg7/bin/avgupdate -o*
In the **Icon** area I entered: */opt/grisoft/avggui/prog/pixmaps/avgupdateico.png*

_Make sure that you tick the *Run in Terminal* box!_

I then dragged this entry just underneath the AVG icon.  
This makes it much easier for me to remember to update.

Appologies if this post is redundant to any other.

---

### Post by Perfect Storm on 2006-02-27
No apologies needed :)
I was thinking to add it as it will make things easier.

---

### Post by arnieboy on 2006-02-27
The following is the easiest way to create a menu item for AVG antivirus and also to allow antivirus signature updates happening from the AVG GUI

```
sudo gedit /usr/share/applications/avg.desktop
```
paste the following lines in the empty file that opens:
> [Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;

save and exit.

AVG Antivirus will appear in Applications --> System Tools

Awesome howto by the way. **Good job AI.**

---

### Post by Perfect Storm on 2006-02-28
Thanks arnieboy :)


Updated the howto
- added diffrent ways to run avg a) as root b) as normal user.
- changed the way to add launchers in the application tab.
- fixed spell errors and typos.
- Added an extra screenshot showing the application tab with avg launchers.
- Added a link for discussion about anti-virus and firewall: "Is it needed or not".

---

### Post by TransitMan on 2006-03-01
AI, thanks for the How To.
Works like a charm.

---

### Post by Urmas on 2006-03-01
Thank You, AI! Works like a... moose! :mrgreen:  10/10.

To make this HOWTO perfect... **UN**installing guide could be useful.

---

### Post by SFN on 2006-03-01
Works perfectly here as well.

Thanks!

Can we no longer vote on posts?

---

### Post by Perfect Storm on 2006-03-01
> To make this HOWTO perfect... UNinstalling guide could be useful.

Comming soon when I get my lazy butt up from the chair ;)

> Can we no longer vote on posts?

Must be a forum glitch, you might want to report/post it here: [http://ubuntuforums.org/forumdisplay.php?f=48](http://ubuntuforums.org/forumdisplay.php?f=48)

---

### Post by FoxLogic on 2006-03-01
THANK YOU! YOU ARE NOW GOD!

I got about half way in getting mine to work.   You finished the work for me, your fast man...


Now all we need is an easy right click a file and scan option.  Then things would really rock.

---

### Post by darknightuk on 2006-03-11
nice how to...but install seems to go fine when i load avg a window pops up with a yellow triangle and exclamation mark if i click ok and try to update it gives the message below, any ideas?
Update process failed..
Reason: Unexpectedly terminated or not running.

---

### Post by NatvAmer on 2006-03-11
When the link for the AVG antivirus didn't work I went to the AVG website and apparently Grisoft is charging for the Linux Email Server 7.1. Too late I guess.

---

### Post by arnieboy on 2006-03-11
[QUOTE=NatvAmer]When the link for the AVG antivirus didn't work I went to the AVG website and apparently Grisoft is charging for the Linux Email Server 7.1. Too late I guess.[/QUOTE]
The link does work.
This is what u need to do.
right click on the link and choose "save target as"
and save the rpm file
u can also do the following from terminal:
```
wget http://free.grisoft.com/softw/70free/setup/avglinux-7.1-23_free_mdk_avi0676.i386.rpm
```

---

### Post by Perfect Storm on 2006-03-11
[QUOTE=darknightuk]nice how to...but install seems to go fine when i load avg a window pops up with a yellow triangle and exclamation mark if i click ok and try to update it gives the message below, any ideas?
Update process failed..
Reason: Unexpectedly terminated or not running.[/QUOTE]

Did you ran it with gksudo first?

---

### Post by darknightuk on 2006-03-12
[QUOTE=Artificial Intelligence]Did you ran it with gksudo first?[/QUOTE]yep tried with both in both sudo and root

---

### Post by Perfect Storm on 2006-03-12
Hmmm...I see you use Dapper Drake. This howto was written with breezy in mind. r4ik tried this on Dapper Drake without success. So you might wait until it's tested on Dapper or try to crunch the errors by yourself.

---

### Post by NoNo_231 on 2006-03-12
Thanks! that is really good! It is really fast (much more faster than clamtk) and does't have a daemon searching e-mail attachments. So I left the clamav daemon to run scanning e-mail attachments. From my experience from windows if these 2 run together there is big problem (the e-mail scanners). If it is sometime to have an AVG e-mail scanner in a distro probably it has to stop the clamav.

---

### Post by geakhawk on 2006-03-14
I'm not sure why but when i get to the registration part i get ```
eric@pokeylinux:~/Desktop$ sudo /opt/grisoft/avggui/bin/avggui_update_licinfo.shsudo: /opt/grisoft/avggui/bin/avggui_update_licinfo.sh: command not found

```
anyone know what happened?

---

### Post by Perfect Storm on 2006-03-14
Are you sure that the previous steps are done without any errors?

---

### Post by geakhawk on 2006-03-14
yes all previous steps go through without errors but when i issue > sudo /opt/grisoft/avggui/bin/avggui_update_licinfo.sh i get > sudo: /opt/grisoft/avggui/bin/avggui_update_licinfo.sh: command not found i browsed to this directory and there is no avggui directory

---

### Post by Perfect Storm on 2006-03-14
hmm...sounds to me the installation went wrong somehow.

---

### Post by geakhawk on 2006-03-14
there's an avg7 directory but no avggui directory, hidden or otherwise:confused:

---

### Post by Perfect Storm on 2006-03-14
Try uninstall avg. Then go through every step again inclusive downloading and making the .deb file, ther could be a glitch somewhere.

and you are on a x86 i386?

---

### Post by geakhawk on 2006-03-14
redownloading it seems to have done the trick! up and running! Thanks a lot AI!

---

### Post by Perfect Storm on 2006-03-14
My pleasure ^^

---

### Post by Christopher on 2006-03-16
I downloaded AVG Free & i type this command in console sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2 & i get this error: E: Couldn't find package libstdc++2.10-glibc2.2 . Did I do something wrong? Thank you in advance.

---

### Post by Perfect Storm on 2006-03-16
You need to enable universe in your sourcelist first.

---

### Post by Christopher on 2006-03-16
[QUOTE=Artificial Intelligence]You need to enable universe in your sourcelist first.[/QUOTE]

Sorry im new to linux, how do i go about doing this. Thank you in advance.

---

### Post by Perfect Storm on 2006-03-17
```
sudo gedit /etc/apt/sources.list
```

Then uncomment the lines that start with one #, you just remove the #.
like:
#deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

so it says:
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe


save and exit.
You may also check: [http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories) for more information.


```
sudo apt-get update
```

---

### Post by Christopher on 2006-03-17
[QUOTE=Artificial Intelligence]```
sudo gedit /etc/apt/sources.list
```

Then uncomment the lines that start with one #, you just remove the #.
like:
#deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

so it says:
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe


save and exit.
You may also check: [http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories) for more information.


```
sudo apt-get update
```[/QUOTE]


Awsome TY I got it installed. But when I go to update it its telling me Update process failed Reason: Sorry, you do not have permission to execute avg update. Thank you in advance.

---

### Post by Perfect Storm on 2006-03-17
Did you made the update launcher which are explained in thte howto?

> If you're using the b) you need also an update launcher:

```

sudo gedit /usr/share/applications/avgupdate.desktop

```

add:
[quote]
[Desktop Entry]
Name=AVG Updater
Comment=Antivirus
Exec=sudo /opt/grisoft/avg7/bin/avgupdate -o
Icon=/opt/grisoft/avggui/prog/pixmaps/avgupdateico.png
Terminal=true
Type=Application
Categories=Application;System;


save and exit.
[/quote]

---

### Post by Christopher on 2006-03-17
[QUOTE=Artificial Intelligence]Did you made the update launcher which are explained in thte howto?[/QUOTE]

Yea my fault, the update icon was under Applications/System Tools/Avg Updater  I just added it to my panel. I was trying to do it from the AVG program itself. I also got like 120 errors while scanning for viruses, something about files it couldnt open: Cannot open; Not checked! Permission denied, is this ok?

---

### Post by valnar on 2006-03-17
Excellent guide.  And though this has no reflection on you, I still am miffed that average users such as myself require such a guide to get a program installed on Linux.  And something as "simple" as antivirus.

Sigh....  I don't believe Linux as a desktop will ever go mainstream if your average utility program requires instructions such as this.  :???: 

But once again, thanks for the HowTo!

-Robert

---

### Post by Perfect Storm on 2006-03-17
Aye, it should be easier. The problem is that AVG didn't released a package for the debian way. If the did the howto would have been something like:

```

cd Desktop
sudo dpkg -i avg7.deb

```

Edit: typos

---

### Post by Christopher on 2006-03-17
I got like 120 errors while scanning for viruses, something about files it couldnt open: Cannot open; Not checked! Permission denied, is this ok or normal? :confused:

---

### Post by mitjab on 2006-03-18
very nice howto

---

### Post by arnieboy on 2006-03-18
[QUOTE=Christopher]I got like 120 errors while scanning for viruses, something about files it couldnt open: Cannot open; Not checked! Permission denied, is this ok or normal? :confused:[/QUOTE]
run the antivirus with sudo.

---

### Post by Matchless on 2006-03-18
[QUOTE=arnieboy]run the antivirus with sudo.[/QUOTE]


And your update button in AVG will also work!

---

### Post by Christopher on 2006-03-18
[QUOTE=arnieboy]run the antivirus with sudo.[/QUOTE]

Sorry Im new to linux, whats the command? Thank you in advance.

---

### Post by Perfect Storm on 2006-03-18
7. Now we need an avg launcher in the application tab, there's two ways **a)** if you want to launch avg as root (the update button works then in AVG) or **b)** as normal user.

**a)**
```
sudo gedit /usr/share/applications/avg.desktop
```
add:
>  [Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
save and exit.

---

### Post by atoponce on 2006-03-18
[Archived]("http://doc.gwos.org/index.php/Install_AVG_Anti_Virus").

---

### Post by arthur on 2006-03-19
An absolutely brilliant thread! Many thanks to AI
However, please forgive my ignorance, but I decided to install the a) option (to run AVG as root):

How can I make it run through its icon under
Apps >> System Tools >> AVG Antivirus
??? :-k 

*BTW, the same happens with Firestarter; I installed it through Automatix, and since no icon is shown anywhere in the menus, included a customized launcher (/usr/sbin/firestarter). Quite obviously, when I clic on it, it won't let it open ...*

---

### Post by Perfect Storm on 2006-03-19
It happens sometimes, I suspect a bug somewhere. Just 

```
smeg
```
and make your own launcher

Name: AVG Antivirus
Comment: Antivirus
Command: gksudo avggui &
Icon: /opt/grisoft/avggui/prog/pixmaps/avgico_big.png

---

### Post by arthur on 2006-03-19
You are very kind ... and incredibly quick :) .

BTW, are both Firestarter and AVG _automatically_ running in the background just after they are installed, or do we need to start them every time we log in?

---

### Post by Perfect Storm on 2006-03-20
No, just scan once in awhile with with AVG. Virus' aren't a problem in linux like in Windows.

For firestarter to run everytime:

```
sudo gedit /etc/sudoers
```

add in the buttom:

**<your username> ALL= NOPASSWD: /usr/sbin/firestarter**

(without the < and >)

```
gnome-session-properties
```
Or System tab ---> Preferences ---> Sessions

Go to **Startup Programs** tab click **add**

Startup Command: **sudo firestarter --start-hidden**
Order: **50**

Click ok and close. That should do it.

---

### Post by LordMerlin on 2006-03-21
Can this be done on a server, with out Gnome / KDE installed? I don't quite want to use clamawin, due to the speed issues, and AVG seems to be a good, well maintained AV. How would I be able to install, and run it on a samba file servers, say from CRON, or something?

---

### Post by WoodyMahan on 2006-03-21
This is Awesome.  I didn't know what I was doing for the most part, but I just kept following the instructions and AVG is working perfectly on my system now.  Excellent Doc.  Thanks

---

### Post by Perfect Storm on 2006-03-21
[QUOTE=LordMerlin]Can this be done on a server, with out Gnome / KDE installed? I don't quite want to use clamawin, due to the speed issues, and AVG seems to be a good, well maintained AV. How would I be able to install, and run it on a samba file servers, say from CRON, or something?[/QUOTE]

You can run AV via commanline, but don't ask me about samba as I have never used it. Perhaps someone with that knowledge can answer the question?

---

### Post by int on 2006-03-21
I download avglinux-7.1-24_free_mdk_avi0720.i386.rpm 
and install like HOW TO in first post, but in avgscan -register say Aborted...
And everything steps install fine...

```
int@int:~/Desktop$ **rpm -qip --scripts avglinux-7.1 -24_free_mdk_avi0720.i386.rpm**
Name        : avglinux                     Relocat ions: (not relocatable)
Version     : 7.1                               Ve ndor: (none)
Release     : 24_free_mdk_avi0720           Build Date: Thu 09 Mar 2006 02:42:01 PM WET
Install Date: (not installed)               Build Host: qak.grisoft.cz
Group       : Application/Anti-Virus        Source  RPM: avglinux-7.1-24_free_mdk_avi0720.src.rpm
Size        : 25088652                         Lic ense: (c) 2006 GRISOFT, s.r.o.
Signature   : (none)
URL         : http://www.grisoft.cz/linux
Summary     : AVG 7.1 Anti-Virus Workstation for L inux
Description :
This package contains the binary release of AVG 7. 0 Anti-Virus for x86 Linux and
graphical user interface.
preinstall scriptlet (using /bin/sh):
RET=`grep ^avg /etc/group | cut -f1 -d:`
if [ -z  $RET ];
then
        groupadd avg 2> /dev/null
fi

RET=`grep ^avg /etc/passwd | cut -f1 -d:`
if [ -z $RET ];
then
        useradd -s /sbin/nologin -g avg avg 2>/dev /null
fi
postinstall scriptlet (using /bin/sh):
/sbin/chkconfig --add avgd
touch /opt/grisoft/avg7/data/set_vers.cfg
/usr/bin/avgscan -register 70FREE-TX-IB-P1-C01-S13 9FC-327-9FPB
echo "Please launch the '/opt/grisoft/avggui/bin/a vggui_update_licinfo.sh'"
echo "script as root for updating license informat ion."
echo
echo "AVG 7.1 Anti-Virus Free for Linux successful ly installed."
if [ -x /usr/bin/update-menus ]; then /usr/bin/upd ate-menus || true ; fi
preuninstall scriptlet (using /bin/sh):
if [ $1 = 0 ] ; then
    /sbin/chkconfig --del avgd
    /sbin/service avgd stop >/dev/null 2>&1
fi
cp /opt/grisoft/avg7/data/set_vers.cfg /opt/grisof t/avg7/data/upd_vers.cfg
rm -f /opt/grisoft/avggui/prog/*.pyc
exit 0
postuninstall scriptlet (using /bin/sh):
if [ -x /usr/bin/update-menus ]; then /usr/bin/upd ate-menus || true ; fi
int@int:~/Desktop$ **sudo alien avglinux-7.1-24_free_mdk_avi0720.i386.rpm**
Password:
Warning: Skipping conversion of scripts in package avglinux: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
avglinux_7.1-25_i386.deb generated
int@int:~/Desktop$ **sudo dpkg -i avglinux_7.1-25_i386.deb**
Selecting previously deselected package avglinux.
(Reading database ... 86771 files and directories currently installed.)
Unpacking avglinux (from avglinux_7.1-25_i386.deb) ...
Setting up avglinux (7.1-25) ...
int@int:~/Desktop$ **sudo /opt/grisoft/avggui/bin/avggui_update_licinfo.sh**
Please enter two additional registration information.
What is your name: Marco
What is the name of your company: NA
int@int:~/Desktop$ sudo avgscan -register
AVG7 Anti-Virus command line scanner
Copyright (c) 2006 GRISOFT, s.r.o.
Program version 7.1.24, engine 718
Virus Database: Version 268.2.0/275  2006-03-06
Aborted
```

Execute sudo avggui  and put my code in license because the textbox is empty, say **License number 70FREE-TX-IB-P1-C01-S13 9FC-327-9FPB is not correct.**

Using Dapper..

---

### Post by Perfect Storm on 2006-03-21
This howto havn't be tested on Dapper yet, other have reported it won't work on Dapper. It could be something with dapper...

Try with a new install, new download and new .rpm convert. So you get a new License number. Ther could be something wrong with the number you got.

When uninstall you might check and remove if there are left overs of AVG (opt/grisoft and /home/<username>/.avg7) to be on the safer side.

---

### Post by n0fx on 2006-03-23
Does anyone how to fix this error:

avgscan: symbol lookup error: avgscan: undefined symbol: __dynamic_cast_2

When I try to register the serial number that I got from the script, I get that error message in the terminal.  I tried to reinstall the program, since when I installed it the first time, after running the program, it gives me a dialog box with an exclamation point without any text.

Also, I'm running this on Breezy and not drapper.

---

### Post by Perfect Storm on 2006-03-26
Did you clean grisoft in /opt before reinstalling (redownload and re-alien) and removing .avg from your home?

Also did any output/warnings occure which might seems suspicious while doing the howto steps?

are you running a non-i386 structure? Like pcc or am64.

---

### Post by ubunturules on 2006-03-26
How do I uninstall AVG?

---

### Post by Perfect Storm on 2006-03-27
sudo dpkg -r avglinux

---

### Post by mstlyevil on 2006-03-27
[QUOTE=Artificial Intelligence]This howto havn't be tested on Dapper yet, other have reported it won't work on Dapper. It could be something with dapper...

Try with a new install, new download and new .rpm convert. So you get a new License number. Ther could be something wrong with the number you got.

When uninstall you might check and remove if there are left overs of AVG (opt/grisoft and /home/<username>/.avg7) to be on the safer side.[/QUOTE]

I tried installing it several ways with Dapper and it does not work. Just thought I would verify that for you.

---

### Post by Perfect Storm on 2006-03-27
Thanks. I tried myself without any luck. I suspect that there's a permission problem in /opt/grisoft

---

### Post by arnieboy on 2006-03-27
[QUOTE=Artificial Intelligence]Thanks. I tried myself without any luck. I suspect that there's a permission problem in /opt/grisoft[/QUOTE]
yes its failing to ask for the code while registering.

---

### Post by ubunturules on 2006-03-27
Is there a way to fix this?

---

### Post by Hoffmann on 2006-03-27
> **Artificial Intelligence]If you're looking for Anti-virus to protect Windows OS, network, servers etc. via your Linux system, you might use this instead: [HOWTO: Install F-Prot anti-virus](http://ubuntuforums.org/showthread.php?t=88357)

This one is for paranoid single home users  said:**
> here[/URL] and save it to your Desktop. (Right click on link and choose Download Link)

2. Now we need some extra libs to get it to work, open the terminal:
```

sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2
```

3. Even though AVG is free (as in beer) it still need you to get a registration number. It can be done like this
```
cd Desktop
rpm -qip --scripts avglinux-7.1-23_free_mdk_avi0676.i386.rpm

```
Find where it says **70FREE-TX-IB-P1-C01-S139FC-327-9FPB** the numbers are diffrent from each time you install avg.
[IMG]http://www.imageviper.com/displayimage.php?id=27905&name=avg1.jpg[/IMG]

4. Installing AVG:
```
sudo alien avglinux-7.1-23_free_mdk_avi0676.i386.rpm
sudo dpkg -i avglinux_7.1-24_i386.deb
```
5. Now to the registration of AVG:
```

sudo /opt/grisoft/avggui/bin/avggui_update_licinfo.sh
sudo avgscan -register

```
6. AVG needs to make a folder and save some files at your home folder:
```
avggui &
```
Close AVG again.

7. Now we need an avg launcher in the application tab, there's two ways **a)** if you want to launch avg as root (the update button works then in AVG) or **b)** as normal user.

**a)**
```
sudo gedit /usr/share/applications/avg.desktop
```
add:

save and exit.

**b)**
```
sudo gedit /usr/share/applications/avg.desktop
```
add:

save and exit.

If you're using the **b)** you need also an update launcher:
```
sudo gedit /usr/share/applications/avgupdate.desktop
```
add:

save and exit.

If people want to discuss security about virus' and firewall if it needed or not, also a good place to see peoples opinion on this matter: [http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616)

Hi Artificial Intelligence,

Such a nice how-to!
I followed all of the instructions and AVG antivirus is working fine. However, I am confuse about the update process. I mean, when I click on the update launcher, right after booting to the system, it asks my password on the terminal. If I try to do that again, the terminal just flashes. On the other hand, if I press the button on the main AVG window, it tells me that the update is alredy running. 
Could you, please, let me know how this process works? Am I missing anything?
Thanks!
Hoffmann

---

### Post by n0fx on 2006-03-30
[QUOTE=Artificial Intelligence]Did you clean grisoft in /opt before reinstalling (redownload and re-alien) and removing .avg from your home?

Also did any output/warnings occure which might seems suspicious while doing the howto steps?

are you running a non-i386 structure? Like pcc or am64.[/QUOTE]

No, I didn't clean the /opt/grisoft or .avg7 directories before reinstalling the program.  I'll give that a try before installing the program.

There weren't any specific warnings that I can recall when I install it.  I'm going to try reinstalling it with those directories removed first and if I get any errors, I'll post it in this thread.

I'm running the standard i386 architecture for the processor. (non 64)

**EDIT:**  I cleaned all the directories specified and I still get that error.  This is what I did and it didn't output any errors until I got to the part where I register it:

n0fx@maximus:~/Desktop$ rpm -qip --scripts avglinux-7.1-24_free_mdk_avi0720.i386.rpm
Name        : avglinux                     Relocations: (not relocateable)
Version     : 7.1                               Vendor: (none)
Release     : 24_free_mdk_avi0720           Build Date: Thu 09 Mar 2006 06:42:01 AM PSTInstall date: (not installed)               Build Host: qak.grisoft.cz
Group       : Application/Anti-Virus        Source RPM: avglinux-7.1-24_free_mdk_avi0720.src.rpm
Size        : 25088652                         License: (c) 2006 GRISOFT, s.r.o.
URL         : [http://www.grisoft.cz/linux](http://www.grisoft.cz/linux)
Summary     : AVG 7.1 Anti-Virus Workstation for Linux
Description :
This package contains the binary release of AVG 7.0 Anti-Virus for x86 Linux and
graphical user interface.
preinstall scriptlet (through /bin/sh):
RET=`grep ^avg /etc/group | cut -f1 -d:`
if [ -z  $RET ];
then
        groupadd avg 2> /dev/null
fi

RET=`grep ^avg /etc/passwd | cut -f1 -d:`
if [ -z $RET ];
then
        useradd -s /sbin/nologin -g avg avg 2>/dev/null
fi
postinstall scriptlet (through /bin/sh):
/sbin/chkconfig --add avgd
touch /opt/grisoft/avg7/data/set_vers.cfg
/usr/bin/avgscan -register 70FREE-TX-IB-P1-C01-S139FC-327-9FPB
echo "Please launch the '/opt/grisoft/avggui/bin/avggui_update_licinfo.sh'"
echo "script as root for updating license information."
echo
echo "AVG 7.1 Anti-Virus Free for Linux successfully installed."
if [ -x /usr/bin/update-menus ]; then /usr/bin/update-menus || true ; fi
preuninstall scriptlet (through /bin/sh):
if [ $1 = 0 ] ; then
    /sbin/chkconfig --del avgd
    /sbin/service avgd stop >/dev/null 2>&1
fi
cp /opt/grisoft/avg7/data/set_vers.cfg /opt/grisoft/avg7/data/upd_vers.cfg
rm -f /opt/grisoft/avggui/prog/*.pyc
exit 0
postuninstall scriptlet (through /bin/sh):
if [ -x /usr/bin/update-menus ]; then /usr/bin/update-menus || true ; fi

n0fx@maximus:~/Desktop$ sudo alien avglinux-7.1-24_free_mdk_avi0720.i386.rpm
avglinux_7.1-25_i386.deb generated

n0fx@maximus:~/Desktop$ sudo dpkg -i avglinux_7.1-25_i386.deb
Selecting previously deselected package avglinux.
(Reading database ... 105460 files and directories currently installed.)
Unpacking avglinux (from avglinux_7.1-25_i386.deb) ...
Setting up avglinux (7.1-25) ...

n0fx@maximus:~/Desktop$ sudo /opt/grisoft/avggui/bin/avggui_update_licinfo.sh
Please enter two additional registration information.
What is your name: User
What is the name of your company: Company

n0fx@maximus:~/Desktop$ sudo avgscan -register
AVG7 Anti-Virus command line scanner
Copyright (c) 2006 GRISOFT, s.r.o.
Program version 7.1.24, engine 718
Virus Database: Version 268.2.0/275  2006-03-06
Enter license number: 70FREE-TX-IB-P1-C01-S139FC-327-9FPB
License type is FREE.
avgscan: symbol lookup error: avgscan: undefined symbol: __dynamic_cast_2

I also checked to make sure all the packages required to do this was up to date:

n0fx@maximus:~/Desktop$ sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2
Reading package lists... Done
Building dependency tree... Done
alien is already the newest version.
libstdc++2.10-glibc2.2 is already the newest version.
python2.4-glade2 is already the newest version.
python2.4-gtk2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

I don't know exactly what's causing this problem and I couldn't find any else on the forums who had this exact problem either.

---

### Post by master5o1 on 2006-03-31
How do i make i link to AVG Free program from my TOP panel?
is it just: 

> avggui &

---

### Post by Perfect Storm on 2006-04-01
or
```
gksudo avggui &
```

if you want to start AVG with adminstration previledge (so you can use the update button in AVG)

---

### Post by ubunturules on 2006-04-01
When is there going to be a HOWTO for AVG for Dapper?

---

### Post by Perfect Storm on 2006-04-02
[QUOTE=ubunturules]When is there going to be a HOWTO for AVG for Dapper?[/QUOTE]

When a Howto for Dapper forum is made and also when I/or someone else solve the Permission problem that happens on Dapper.

---

### Post by gullyhole on 2006-04-02
E: Couldn't find package libstdc++2.10-glibc2.2


when i put in the first line of code it returns that error.

---

### Post by darknightuk on 2006-04-02
[QUOTE=gullyhole]E: Couldn't find package libstdc++2.10-glibc2.2


when i put in the first line of code it returns that error.[/QUOTE]install the missing dependency it using apt-get  or synaptic!

---

### Post by gullyhole on 2006-04-02
I am a total noob. How do i do that. I tried entering sudo apt-get and then teh file name. I really dont know how to get that file.

---

### Post by gullyhole on 2006-04-02
Ok so i doubt this changes anything but i went in and searched the packages and could not find ++2.10, is it possible to go in and use a different ++ thing. I am able to see 5 and 6. Could i substitute or do I need to find ++2.10. If i need to find it. Where would i find it.

---

### Post by gullyhole on 2006-04-02
Ok so i got it to work. I kind of overlooked one of the replys that pretained to what i needed. So i got it to install. However now It wont allow me to run an update. It says something about I am not authorized to update. Is it because it is a free avg thing.

---

### Post by Perfect Storm on 2006-04-02
Yo uneed to make the launcher with 'sudo avggui &'. Check step 7 in the howto again.

---

### Post by gullyhole on 2006-04-02
OH hahaha. It never did anything before. Not sure what it was. I probably did something stupid. Thank you.

---

### Post by darkwarrior0404 on 2006-04-03
Excellent : ) directions easy to use worked first time! Think I'm starting to get the hang of this haha. Thanks for the How To :mrgreen:

---

### Post by suspend on 2006-04-03
Any suggestions why this is happening?


ubuntu@ubuntu:~$ sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libstdc++2.10-glibc2.2

then I get...

ubuntu@ubuntu:~/Desktop$ rpm -qip --scripts avglinux-7.1-23_free_mdk_avi0676.i386.rpm
bash: rpm: command not found

---

### Post by Perfect Storm on 2006-04-03
You need to enable universe in your sourcelist first.

---

### Post by gold4tune on 2006-04-04
thx for all

---

### Post by Healey on 2006-04-04
Hi
Thanks for the How to on installing AVG - It works a treat

In fact it works so well that it has found a virus

Virus found Akuku

There does not seem to be a way to remove a "found" virus !!!

What should I do now ??

Regards

Healey

---

### Post by OMRebel on 2006-04-04
I can't get the Update to run.  I am assuming it's looking for the root password.  How can I set this to just go with sudo instead?

---

### Post by Perfect Storm on 2006-04-04
Just type in the password you use for your account.

---

### Post by Perfect Storm on 2006-04-04
[QUOTE=Healey]Hi
Thanks for the How to on installing AVG - It works a treat

In fact it works so well that it has found a virus

Virus found Akuku

There does not seem to be a way to remove a "found" virus !!!

What should I do now ??

Regards

Healey[/QUOTE]

You might try with another anti-virus to double-check. I looked it up and it's rated as low threat windows virus. It won't affect your linux system if you caught it.

---

### Post by Healey on 2006-04-04
Hi
Thanks for your reply

Yes I checked it also and found it was a low risk however I would like to remove it so that I do not pass it on to somebody with windows.

Is there no way to remove it ???

Surely if there is no way to remove a virus then what is the point in scanning for them !!!

Seems strange

Regards

Healey

---

### Post by Perfect Storm on 2006-04-04
[http://free.grisoft.cz/softw/70free/doc/avg_afl_uma_en_71_3.pdf](http://free.grisoft.cz/softw/70free/doc/avg_afl_uma_en_71_3.pdf)

It's only for testing/finding. That's why it says test instead of scan ;). Either you delete the infected file or use F-prot for removing and dis-infection or use AVG commandline.
```
avgscan -clean <paths>
```
I don't know if the full version have a clean option in gui.

> Command-line scanner:

avgscan [options] <path or file to scan>

-scan           Scan test /path,path/
-heur           Heuristic Analysis /path,path/
-exclude        Exclude path or files from scan
-@              Command file /file name/
-ext            test these extensions /for example EXT=*/
-noext          do not test these extensions /for example NOEXT=JPG/
-smart          Smart scan
-arc            test archives
-rt             test run-time compressions
-pup			detection of potentially unwanted programs
-clean          clean automatically
-arcw           report archives
-rtw            report run-time compressions
-macrow         report macros
-pwdw           Report password-protected files
-changew        Report changes
-ignlocked      Ignore locked files
-report         Report to file /file name/
-repappend      Append to the report file
-repok          report uninfected files as OK
-stoplevel      Pause on detection /1-n/
-h              Display help on this topic
--help          Display help on this topic


> examples:
1) next command scans whole directory /home and checks all files, including
   archives and run-time compressed files

   $ avgscan -ext=* -rt -arc /home

2) same as example above, but with heuristic analysis

   $ avgscan -ext=* -rt -arc -heur /home

3) same as example above, but saves scanning results to the 'results.log' file

   $ avgscan -ext=* -rt -arc -report results.log -heur /home


---

### Post by Healey on 2006-04-04
Hi
Many thanks for your reply

This is what i did - I assume it did not work:

avgscan -clean /usr/lib/wine/wintab32.dll.so
AVG7 Anti-Virus command line scanner
Copyright (c) 2006 GRISOFT, s.r.o.
Program version 7.1.24, engine 718
Virus Database: Version 267.0.0/301  2006-04-04
License type is FREE.
/usr/lib/wine/wintab32.dll.so  Virus found Akuku $(@FileError) /usr/lib/wine/wintab32.dll.so
Tested: 1 files, 0 sectors
Infections: 1
Errors: 0


What should I do now ??

Thanks

Healey

---

### Post by Perfect Storm on 2006-04-04
In theory it should clean it, but you might do it with sudo if it's in /usr/lib/wine. Try run it again. With sudo permission.

Question how did it come there in the first place? Did you run wine with sudo?

---

### Post by OMRebel on 2006-04-04
Healey - I just got the exact same thing.  Using -clean didn't do any good for me, so I just deleted the file using:

sudo rm /usr/lib/wine/wintab32.dll.so

I'm gonna uninstall Wine and reinstall it.  Gonna find out where it's coming from.

---

### Post by Healey on 2006-04-04
Hi
Thanks for your reply OMRebel

I wanted to delete this file, but as i am new at Linux I was not sure if this would stop wine working or even worse perhaps !!

Is it ok to do this ??

Thanks

Healey

---

### Post by Perfect Storm on 2006-04-04
As I said before I'll recommend you try to scan it with another anti-virus application. It could be a hoax.

---

### Post by OMRebel on 2006-04-04
I completely removed Wine through Synaptic, reinstalled it, and it is still finding Akuku in that same file.  Either this is a false positive, or the repo has an infected file.

The deb it was using when reinstalling was showing as /wine_0.9.11~winehq1-1_i386.deb

The file it is reporting it on is consistent: /usr/lib/wine/wintab32.dll.so

---

### Post by OMRebel on 2006-04-04
AI - I copied the file to a floppy and scanned it on my XP machine with Trend OfficeScan, and it didn't report any error.  

So, is it just a foul up in AVG's definition files?

---

### Post by Healey on 2006-04-04
Hi
I have tried clamscan (old version because I dont know how to upgrade it) It did NOT find any virus

I have tried again with sudo permission - same result !

I dont think I tried wine with sudo - Not sure why I should have done that but its possible because I am new to all this - still learning !!


Its strange eh!

Healey

---

### Post by Perfect Storm on 2006-04-04
[QUOTE=OMRebel]AI - I copied the file to a floppy and scanned it on my XP machine with Trend OfficeScan, and it didn't report any error.  

So, is it just a foul up in AVG's definition files?[/QUOTE]


Must be, I can't see any other reason it should do so.

---

### Post by OMRebel on 2006-04-04
Hang in there Healey.  I'm still new to Linux and learning as well, so I'm in the same boat as you are.  It appears that it's just misreporting that file as being infected, so I'm not really gonna worry about it.

---

### Post by Healey on 2006-04-04
Hi
OMRebel - Thanks for your comment

I am enjoying learning so I wont give up yet !!

I think you must be correct - I wonder if anyone else has noticed this ??

That was good thinking to check that file the way you described - well done, wish I had thought of that !!!

OK I wont worry about it either

Thanks again

Healey

---

### Post by darkwarrior0404 on 2006-04-05
Wow I got the same thing, but as for the way it looks its in Wine... its on linux and windows stuff still gets viruses:-D  lol

---

### Post by jefrey on 2006-04-14
This worked perfectly.  Thanks!

---

### Post by Red Knuckles on 2006-04-16
Does selecting 'Update' in the gui update f-prot or only the gui. If not how to update f-prot?:)

---

### Post by Perfect Storm on 2006-04-17
It's updating both the gui and the difinition and engine of AVG.

---

### Post by LordMerlin on 2006-04-19
I'm not sure if it's just me, but I don't see any options to either clean the infected files, or removing the virus / infected file. How do I do that? I'd like to run AVG unattended, but can't get it to clean the files

Any suggestions?

---

### Post by Perfect Storm on 2006-04-19
[http://ubuntuforums.org/showpost.php?p=891034&postcount=102](http://ubuntuforums.org/showpost.php?p=891034&postcount=102)

---

### Post by asusrules on 2006-04-22
sorry if this problem has already been addressed but
when i try to launch avg, it says i need registration code, where do i add the registration code?? i have the code it self already, just dont know where to put it in order to make avg to work

---

### Post by Perfect Storm on 2006-04-23
Does it work without it?

---

### Post by asusrules on 2006-04-23
[QUOTE=Artificial Intelligence]Does it work without it?[/QUOTE]

no, it does not

---

### Post by Matchless on 2006-04-23
Hi,
    Has anyone managed to get this working on Dapper Fl6 yet? My install works well right up to sudo avgscan -register and then shows "Aborted" This did not happen in Breezy.

---

### Post by Perfect Storm on 2006-04-23
[QUOTE=Matchless]Hi,
    Has anyone managed to get this working on Dapper Fl6 yet? My install works well right up to sudo avgscan -register and then shows "Aborted" This did not happen in Breezy.[/QUOTE]

Nope.
Best would do if you write a letter to AVG and ask them to release a .deb package. If we all do I'm sure they can't ignore it.

---

### Post by Perfect Storm on 2006-04-23
[QUOTE=asusrules]no, it does not[/QUOTE]

Try reread the howto, it says where to put it.

---

### Post by pecos.wil on 2006-04-23
My only question is, does it run in the background & scan in comming eMail and downloaded files like it does for windows?

---

### Post by Perfect Storm on 2006-04-24
Nope. But you can make/build a script to do so.

---

### Post by demonhunter on 2006-05-10
hello fellows...

I was trying to install it following the steps of this HOWTO but I got an error.

Do you guys know if it works using Dapper 6.06 beta 2 for amd64. I get the error when I try to run Alien and it tells me:

There are no support for 64 bit architecture.

so... do you guys know how can I go through this problem? or do I have to wait for a 64 bits version??

thanks...

---

### Post by Perfect Storm on 2006-05-11
No 64-bit version, and this howto doesn't work on dapper.

---

### Post by demonhunter on 2006-05-11
ok... thanks man...

---

### Post by TTN on 2006-05-13
I have read all of this thread and I have not seen my error. 

It pertains to the registration # .

I went to the AVG site and they said the current version of FREE AVG did not require a number.

My error

At the point where I am to find the registration # from a script, I get a no file found message.

I searched the rpm package and could not find a script

---

### Post by TTN on 2006-05-13
[QUOTE=TTN]I have read all of this thread and I have not seen my error. 

It pertains to the registration # .

I went to the AVG site and they said the current version of FREE AVG did not require a number.

My error

At the point where I am to find the registration # from a script, I get a no file found message.

I searched the rpm package and could not find a script[/QUOTE]


I just opened a term session again and changed to Desktop.
The path looks the same but this time it found the package and gave me the script. 

Many thanks for your How to

---

### Post by apresvoop on 2006-05-14
This was an excellent walk-through.  AVG is installed and works fine. Thank you.

---

### Post by 3novice378 on 2006-05-14
:confused:  I AM VERY SORRY TO ASK THIS QUESTION AGAIN BUT I AM A NEWBIE.  I enjoy learning a new system but I still can't get the "typing part" quite right. 

5. Now to the registration of AVG:
 
Code:
sudo /opt/grisoft/avggui/bin/avggui_update_licinfo.sh
sudo avgscan -register
[COLOR="#9932cc"]I did this but I don't get the chance to put in my reg #.  (I already read through this post over seven times and did the uninstall thing but I am still having problems[/COLOR]
 
6. AVG needs to make a folder and save some files at your home folder:
 Code:
avggui &
 Close AVG again.
 
](*,)[COLOR="DarkOrchid"]Now these steps have me completely stumped.  Every time I do this I get this message: sudo: gedit: command not found
[/COLOR]
7. Now we need an avg launcher in the application tab, there's two ways a) if you want to launch avg as root (the update button works then in AVG) or b) as normal user.
 
 a)
 
Code:
sudo gedit /usr/share/applications/avg.desktop
 add:

[COLOR="#9932cc"]Where do you type this????[/COLOR]
 Quote:
 [Desktop Entry]
 Name=AVG Antivirus
 Comment=Antivirus
 Exec=gksudo avggui &
 Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
 Terminal=false
 Type=Application
 Categories=Application;System; 
 save and exit.

 b)
Code:
sudo gedit /usr/share/applications/avg.desktop
 add:
 
Quote:
 [Desktop Entry]
 Name=AVG Antivirus
 Comment=Antivirus
 Exec=avggui &
 Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
 Terminal=false
 Type=Application
 Categories=Application;System; 
 save and exit.
 
 If you're using the b) you need also an update launcher:
 
Code:
sudo gedit /usr/share/applications/avgupdate.desktop
 add:
 
Quote:
 [Desktop Entry]
 Name=AVG Updater
 Comment=Antivirus
 Exec=sudo /opt/grisoft/avg7/bin/avgupdate -o
 Icon=/opt/grisoft/avggui/prog/pixmaps/avgupdateico.png
 Terminal=true
 Type=Application
 Categories=Application;System; 
 save and exit
[COLOR="DeepSkyBlue"]Thank you in advance to the one that answers this and gives help to one sho is truly a novice but wants to learn.  I really enjoy this OS and the more I learn how to type in the commands the better it gets.[/COLOR][COLOR="Green"][/COLOR]

---

### Post by Perfect Storm on 2006-06-01
Updated and fixed the howto so it also works in Ubuntu Dapper 6.06
Still works in Ubuntu Breezy 5.10
Fixed the download link.
Changed the howto to Dapper 6.06

---

### Post by Perfect Storm on 2006-06-01
3novice378, which version of ubuntu are you using and which desktop?

---

### Post by RavenOfOdin on 2006-06-08
(EDIT: Never mind, just put the code after -register and installation worked flawlessly.

There were a few stopped jobs in sudo, but I figure it was trying to do three of the same jobs at once so it shouldn't be a problem.

Thanks a lot!)

---

### Post by RavenOfOdin on 2006-06-11
As for the Dazuko kernel module, if anyone has trouble installing it after the ./configure and make steps, type these:

```

make install
make test

```

The kernel module needs commoncap to operate correctly, so load that and Dazuko in via /etc/modules with the text editor of your choice.

---

### Post by Matchless on 2006-06-11
Hi AI,
       This Howto does not work exactly in Kubuntu dapper 6.06, but requires some permission changes for the /opt/grisoft folders to allow upates to be done from the button. I have not been able to run avggui as root in dapper, although this used to work in breezy. I have not managed to figure it out exactly and maybe someone else has proven this, if so please post.

---

### Post by Christopher on 2006-06-12
I followed "The How To", i typed in "sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2 libgtk2-dev"  I get this:


Reading package lists... Done
Building dependency tree... Done
python2.4-glade2 is already the newest version.
python2.4-gtk2 is already the newest version.
E: Couldn't find package libgtk2-dev

I uncommented these 2 lines in my sources.list:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

Is there any thing else to uncomment in my sources.list to get that last file to update or install?

---

### Post by Perfect Storm on 2006-06-12
try first with:
```
sudo apt-get update
```

---

### Post by RavenOfOdin on 2006-06-12
[QUOTE=Matchless]Hi AI,
       This Howto does not work exactly in Kubuntu dapper 6.06, but requires some permission changes for the /opt/grisoft folders to allow upates to be done from the button. I have not been able to run avggui as root in dapper, although this used to work in breezy. I have not managed to figure it out exactly and maybe someone else has proven this, if so please post.[/QUOTE]

It shouldn't require permission changes.

I have them both running just fine with my menu editor reflecting the commands "kdesu avggui" and "kdesu avgupdater."

---

### Post by Matchless on 2006-06-16
Thanks. AVG also works in Kubuntu and creates its own menu item when installing. If this menu item is just edited by adding kdesu in front of the avggui then AVG can be run and the update button should work and no seperate update button will be required. Maybe AI will update the howto to include kubuntu?

---

### Post by chakkid on 2006-06-16
thanks a lot, man;)

---

### Post by six on 2006-06-20
Many thanks for this how-to. I was directed to this post by a kind member. I followed your instructions and everything worked great. (I never did manage to install AVG on FC5 or SUSE).

---

### Post by Somenoob on 2006-06-20
A Question for those who have scanned their hard drives with AVG

--> Did it detect any infected files?

---

### Post by Perfect Storm on 2006-06-20
Nope, but I'm only running gnu/linux. But some have discovered false alarms with wine some months ago. But it was a fault with AVG.
If you are only running Linux/ubuntu there's no need for AVG.

---

### Post by Drifter on 2006-06-22
I can't get it to work for me.  I get broken pagages, and commond not found etc.

---

### Post by dtruesdale on 2006-07-04
AI on the reg code you just say find this, then nothing else. Not what to do with it or whether we change it, add to it or re-use it. There is no such facts in there. I can see the confusion. Can you help on this? 

Update: Ok Folks take that number and add it to the end of the  sudo avgscan -register , it should then register that was the missing explanation.

---

### Post by shane2peru on 2006-07-24
When I tried the first step I got these errors: ```
sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages

```
I simply left that package off, the libgtk2.0-dev and ran through the rest of the steps.  It seems that it is working fine, I'm running the update now!  I'm using Dapper KDE.  I don't know if that has anything to do with it or not, and I don't really understand all the errors, and broken packages things.  

Shane

---

### Post by Perfect Storm on 2006-07-24
Is your sourcelist set up correctly? If not you might check [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by shane2peru on 2006-07-24
I believe that is where I set it up before.  I haven't touched it since then, other than to add a few here and there, but no major changes to my sources.list.  

BTW - great how to, thanks!

Shane

---

### Post by Perfect Storm on 2006-07-24
May I see your sourcelist?

---

### Post by shane2peru on 2006-07-24
ok, here it is:

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# Sound package
deb http://neogate.homelinux.org/debian/ dapper sound

 # Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free

```
Thanks for the help.

Shane

---

### Post by LordMau on 2006-07-26
Hi been trying to enable the on-access scanning of avg by trying to make the dazuko module. I followed step 3 from [this thread]("http://ubuntuforums.org/showthread.php?p=274555&highlight=debian%2Frules#post274555"), but always get this error:

```
/usr/share/modass/packages/generic.sh: line 70: debian/rules: No such file or directory
```

Any suggestions?

---

### Post by Uncle Spellbinder on 2006-07-26
@ Artificial Intelligence

Thanks so much for the Howto. Got it installed, Update icon and Workstation icon in my panel. Extremely easy-to-follow Howto. Thanks again!

---

### Post by Perfect Storm on 2006-07-27
> **Uncle Spellbinder said:**
> @ Artificial Intelligence

Thanks so much for the Howto. Got it installed, Update icon and Workstation icon in my panel. Extremely easy-to-follow Howto. Thanks again!

Thanks.


[quote=LordMau]
Hi been trying to enable the on-access scanning of avg by trying to make the dazuko module. I followed step 3 from this thread, but always get this error:

Code:

/usr/share/modass/packages/generic.sh: line 70: debian/rules: No such file or directory


Any suggestions?[/quote]
That howto doesn't work for AVG. Sorry.


[quote=shane2peru]snip
/snip[/quote]

Your sourcelist looks okay. But if you updated some of your libs from an unofficial source, it can course dependency problems.

---

### Post by LordMau on 2006-07-27
> **Artificial Intelligence said:**
> 
That howto doesn't work for AVG. Sorry.


Could you post the proper way to make the dazuko module for AVG please? Thanks.

---

### Post by Browser_ice on 2006-07-27
I followed your instructions and got AVG to run on my Ubuntu 6.06

I also use it on my Win-XP

I am only disapointed that their Linux version doesn't run in background nor checks email. It is just a plan scan you start manualy or via a custom made script (crontab also probably).

---

### Post by dabbner on 2006-07-29
I followed your instructions, but I am getting a wierd error after I run AVG from my applications menu.  It runs ok, but as if it was not launched as root.  I can run it with the same command string "gksudo avggui &" from the command line and it runs with root priv's.  Any suggestions?

---

### Post by Perfect Storm on 2006-07-29
Depends which one of the suggestion you followed in the howto. There's one which make you run AVG as root and one as non-root.
It makes a launcher in Accessories by default which you can delete. The one you make is in System Tools.

---

### Post by jrjr on 2006-08-03
.

---

### Post by Perfect Storm on 2006-08-03
Try with a second anti-virus program to confirm if it is a virus. Usually it's a program error in the anti-virus application.

---

### Post by jrjr on 2006-08-03
.

---

### Post by jrjr on 2006-08-03
.

---

### Post by Perfect Storm on 2006-08-03
Try F-prot I wrote a howto on it.

---

### Post by jrjr on 2006-08-03
.

---

### Post by Perfect Storm on 2006-08-03
```
sudo dpkg -r avg71flm_r28-1_i386.deb
```

or make a search in synaptic, search for avg.

---

### Post by cardude on 2006-08-04
When i type 

sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2 libgtk2.0-dev

I get this error

 Couldn't find package alien

---

### Post by Perfect Storm on 2006-08-04
Which version of Ubuntu do you use?
Which arch of Ubuntu are you running? (i386, ppc, a64)
How's your sourcelist looks like?
```
sudo nano /etc/apt/sources.list
```

---

### Post by cardude on 2006-08-04
Latest version (Dapper) i386 and sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Copied from [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

---

### Post by jrjr on 2006-08-04
.

---

### Post by Perfect Storm on 2006-08-05
> **cardude said:**
> Latest version (Dapper) i386 and sources.list:

/snip

Copied from [http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

Hmm...looks okay so far. Any error while updating the list?
```
sudo apt-get update
```

Can you find alien in synaptic package manager?
Also you may try look at this sourcelist (remember to backup your old): [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Perfect Storm on 2006-08-05
> **jrjr said:**
> Wow! 
I did not install with Synaptic but yet there is a package in it called avg71flm that says its installed. So even though I installed with cli I can remove it with Synaptic eh?   Cool!

Edit:
So why werent we directed to install with Synaptic since its so easy? I assume its the same as F Prot in that the method you describe yields a result with features not available in the Synaptic install. Right?


Edit
One more question. Why aren't all of my files being scanned? In terminal I even tried su to root and run AVG. It still only scans 6300 files or so and says it does not have access to 2 items just like before. If I try to scan as me I get tons of errors due to restricted access.

Its not saying there is a virus anymore. I never got to see the results of that test either. It was just displayed in the gui on start of the program.

The howto converts the .rpm file to .deb which is why it shows up .

The Free AVG is quiet tame if you ask me. I havn't tried the pay version to linux but I guess it have all the things people are asking for.
Use Clam AV or F-prot if you want some serious scanning.

> So why werent we directed to install with Synaptic since its so easy? I assume its the same as F Prot in that the method you describe yields a result with features not available in the Synaptic install. Right?

The methode shown installs the latest (with gui).

---

### Post by cardude on 2006-08-05
Quote:
Hmm...looks okay so far. Any error while updating the list?

Can you find alien in synaptic package manager?
Also you may try look at this sourcelist (remember to backup your old): [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

No alien in synaptic. And i have already changed my sources.list using source-o-matic.

When i try to update it i always get: connection timed out.

---

### Post by cyme on 2006-08-05
working damn good thaks m8 ;)

---

### Post by jrjr on 2006-08-05
.

---

### Post by Perfect Storm on 2006-08-06
> **cardude said:**
> Quote:
Hmm...looks okay so far. Any error while updating the list?

Can you find alien in synaptic package manager?
Also you may try look at this sourcelist (remember to backup your old): [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

No alien in synaptic. And i have already changed my sources.list using source-o-matic.

When i try to update it i always get: connection timed out.

Then there's properly something wrong with your internet connection. My suggestion is open new thread for that.



> Is it scanning your whole drive though? It seems to just scan my home dir and throws errors for the rest of the drive(s) even though I run sudo

I can't say. But there's some stuff it aren't allowed to scan due to some permission priviledge.
You might want to check this, it's a bit power hungry: [http://ubuntuforums.org/showthread.php?t=230022](http://ubuntuforums.org/showthread.php?t=230022)

---

### Post by jrjr on 2006-08-06
.

---

### Post by Perfect Storm on 2006-08-06
Aye.

---

### Post by jurij20 on 2006-08-10
Thanks alot! It works perfectly :D

---

### Post by enjoyin on 2006-08-10
Thanks for the how to. That went fine but when I opened the application and clicked on test I got a screen window full of "cannot open;not checked!Permission denied. How do I fix it?

---

### Post by floibler on 2006-08-22
[QUOTE=Matchless;770718]Hi,
    Just my 2 cents worth. I see many linux users refering to "not really needing virus protection", but that is not really true. 


Finally some sense!  Why is is it that every discussion on antivirus on these forums ends up with someone commenting that it is not necessary on linux.  Many of us dual boot, or have work computers running windows.  Some of us even carry our email around on USB flash drives (thunderbird portable) - antivirus IS necessary - however it is also extremely unfriendly in linux - as a newbie i've managed to get ClamAV installed, but now want email scanning - I use AVG on windows, but it looks like a lot of work to get it on ubuntu.  Can someone please put together a simple HOW-TO that installs a AV program that does eveything that new-commers from windows would expect - otherwise they wont come!

Sorry for the rant - I love Ubuntu and I want everyone to use it like I do - I just wory they wont spend the hours that I have getting things to work.

---

### Post by jrjr on 2006-08-22
.

---

### Post by oss_monkey on 2006-08-23
Hey, AI, thanks for a great HowTo! I've been a fan of AVG for so long and to have it on my Linux box just makes me feel all fuzzy inside. :)

Anyway, I ran into an error when I tried to update.

> Update process failed..
Reason: Can not create file '/opt/grisoft/avg7/var/run/avgupdate.pid'.

Any idea what's wrong? The only thing I haven't done is to reboot. Also, I used the A) option (run as root) with avg.desktop.

TIA.

---

### Post by Perfect Storm on 2006-08-23
Make sure it's the right launcher youp picked. The AVG made one itself which are located in accessories, don't use that one, but go to System Tools.

---

### Post by quad3d@work on 2006-08-23
Works great mate, thanks a ton.

---

### Post by jrjr on 2006-08-23
.

---

### Post by Perfect Storm on 2006-08-23
Works fine here.
Do you get this, when clicking test:

---

### Post by jrjr on 2006-08-23
.

---

### Post by oss_monkey on 2006-08-24
> **Artificial Intelligence said:**
> Make sure it's the right launcher youp picked. The AVG made one itself which are located in accessories, don't use that one, but go to System Tools.

That did it. Thanks, AI! =D>

---

### Post by peabody on 2006-08-25
Just a question, this app seems to correctly identify virii, but it only seems to identify them, it doesn't really do anything to them.  No quarenteen or cleaning.  That's fine I suppose, since this is just to identify files that might hurt Windows users.  I could see it being a problem though if say, you're running a samba file server, and all of a sudden you find yourself with 100's of infected files across several different folders.  Could be a nasty manual cleanup job.

Is there a way to get this software to actually do things to infected files?

---

### Post by Perfect Storm on 2006-08-25
Only if you buy a license it'll do that. I'll recommend that you try the F-prot howto, then you can do what you asked. (and it's free as in beer and the gui is under GPL).

---

### Post by matchstich on 2006-08-25
ok, i did one and two, but when i typed in 3 for the license, i got you can not use--gernerate or---single with ---install.

whats that? thanks

---

### Post by Perfect Storm on 2006-08-25
Make you spelling it correctly.

---

### Post by Sharka on 2006-08-28
Dear Artificial Intelligence,

I get this message whenever I click on the update key:

Update process failed..
Reason: Can not create file '/opt/grisoft/avg7/var/run/avgupdate.pid'.

I am a newbie and have read your previous response to the same question but couldn't understand where I could access the correct file path.

I was able to do a test scan but am unable to scan. 

Thanks

---

### Post by Perfect Storm on 2006-08-29
[http://ubuntuforums.org/showpost.php?p=1413176&postcount=186](http://ubuntuforums.org/showpost.php?p=1413176&postcount=186)

---

### Post by jng on 2006-09-08
Definitely a good guide. Even I, as a completely new one to Linux, can install AVG after your guidelines. Thanks (mange tak).

---

### Post by Rafinator on 2006-09-24
Sorry for reviving this, but I get this error.

```
rafinator@ubuntu:~$ sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2 libgtk2.0-dev
Password:
Reading package lists... Done
Building dependency tree... Done
python2.4-glade2 is already the newest version.
python2.4-gtk2 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
                 Depends: libglib2.0-dev (>= 2.8.5) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages
rafinator@ubuntu:~$ cd Desktop
rafinator@ubuntu:~/Desktop$ rpm -qip --scripts avg71flm-r28-a0757.i386.rpm
bash: rpm: command not found

```

---

### Post by Perfect Storm on 2006-09-24
Are you using XGL & Compiz source in your repo?

---

### Post by Perfect Storm on 2006-10-18
Now tested on edgy with Beryl enable and latest 9xxx nvidia driver.
Rewritten a bit.

Knock yourself out, guys.

---

### Post by eilu on 2006-10-21
Took me ~4 hours to download everything on my dial-up, but it's worth it. Works like a charm on Dapper. Thanks!

Btw, whenever I run AVG, I get a "warning: licenese is FREE" notification. Is it supposed to do that? Not really an issue, just wondering.

Another thing, is there a way to incorporate a "test with AVG" option to the context menu?

---

### Post by Perfect Storm on 2006-10-21
It's normal that it pop-up with a free window.

Try F-prot it have a EICAR test virus, or search google for it.

---

### Post by eilu on 2006-11-03
How do you *uninstall* AVG? I need to reinstall.

---

### Post by Perfect Storm on 2006-11-04
```
sudo aptitude remove avg71flm
```

or search for avg in synaptic.

---

### Post by SteveGreenhouse on 2006-11-04
I wouldn't trouble myself too much with AVG free if I were you.  According to their website, the free edition ceases to exist in mid January, 2007.

---

### Post by Perfect Storm on 2006-11-12
It says:
> GRISOFT is announcing a new version of the AVG Anti-Virus Free Edition. This new 7.5 version with improved performance and full compatibility with the latest Windows Vista version is available. Users that are using AVG Free 7.1 will be provided with a specific dialog, within the next few weeks, with the opportunity to choose the right option fulfilling their needs. AVG Free 7.1 version will be discontinued on 15th of Jan 2007.


This doesn't mean that free version of AVG is going away. It means that the 7.1 series will stop. New versions will reappear.

---

### Post by Perfect Storm on 2006-11-12
Howto updated.
A face lift were made. Should be easier now.

---

### Post by srafx on 2006-11-14
Thanks for the great howto, but one questions...I'm hoping I didnt miss it in a post already:

Does this run in the background automatically?  I see that there is a scheduler, but do I have to run at startup, or can I have it run in the tray?

---

### Post by Perfect Storm on 2006-11-15
No, it doesn't. Anyway there's no reason it should (waste of resources). The only things that runs in the startup is avgd (avg deamon) which you can disable by bum (boot-up manager).

---

### Post by srafx on 2006-11-15
> **Artificial Intelligence said:**
> No, it doesn't. Anyway there's no reason it should (waste of resources). The only things that runs in the startup is avgd (avg deamon) which you can disable by bum (boot-up manager).

Sounds good to me.  I'm just use to the windows AVG and that always is running in some way shape or form.  

What is the point of the schedule feature though?  It wont run on schedule if it isnt open, so I could just manually start the test when I open it.

---

### Post by tchoklat on 2006-11-21
Hi,

I have downloaded the AVG 7.5 deb file from Grisoft (avg75lms-r39-a0859.i386.deb) and installed it with the debi package manager. It has installed to /opt/grisoft with two directories under that, AVG7 and lib

I cannot find how to run it. YOur HOw to does not owrk and the required libraries - 
 - **libc.so.6**
- [B]libstdc++-libc6.2-2.so.3

I also cannot find.  Can you assist please?

Tony
[/B]

---

### Post by fcc56 on 2006-11-29
> **tchoklat said:**
> Hi,

I have downloaded the AVG 7.5 deb file from Grisoft (avg75lms-r39-a0859.i386.deb) and installed it with the debi package manager.


FWIW, this is the commerical email server package, with anti-spam and AV functions. The price is 1039 USD.

---

### Post by tekoholix on 2006-11-29
In your post, you state that the rebuilt avg.desktop file should be created with the following line:


Exec=gksudo avggui &

On my systems (2), this created an AVG Gui that could not update or scan, due to lack of file permissions, started from your shortcut.

Changing it to "Exec=gksu avggui &" causes it to ask for password, and actually run as root, as it is stated that it should...

---

### Post by Perfect Storm on 2006-11-30
a) Have you change some fundemental things in Ubuntu regarding permission and/or root account?
b) It can be a breezy thing. This howto is well tested on Dapper and Edgy. Though it says Breezy, it's from feedback from people.

---

### Post by bodhi.zazen on 2006-12-02
Nice How-to 



This thread has been added to the UDSF wiki.

[Install AVG](http://doc.gwos.org/index.php/Install_AVG)

---

### Post by yaohui on 2006-12-29
Works like a charm!
Many thanks!

---

### Post by matchstich on 2006-12-30
i did everything on here. have the update button on system tools but the gui for avg isnt there.
thanks
running 6.06 LTS

---

### Post by Perfect Storm on 2006-12-31
Try with **killall gnome-panel** first.

---

### Post by jthomp86 on 2007-01-10
sweet. worked like a charm.

---

### Post by mahiyar on 2007-01-21
I think I'am to balme for this. By mistake I had installed the 7.5 deb file which I later uninstalled using Synaptic (complete removal) now when I have installed the correct AVG free version, it says license type trial for server No of days to expire 30. Can anybody help.

---

### Post by mahiyar on 2007-01-21
BTW reinstallation does not help. It seems that somehow the old code is "acquired" in the script and disallows the new "free" code

---

### Post by Perfect Storm on 2007-01-21
Try check /opt and /.avg7

---

### Post by mahiyar on 2007-01-22
Thanks a lot AI, No wonder they call u an expert. I was suprised to find out that even after uninstalling through synaptic all the files and directories were intact, maybe that understanding is a windows hangover?

---

### Post by Mikeyboy1 on 2007-01-27
Many thanks for the clear and detailed instructions!

Everything worked - BUT - when I try to start AVG from the menu the mouse cursor bounces as usual - program loading - then nothing. :(  Any suggestions on what I've done wrong?

PS - I'm using _Kubuntu_ - Dapper - I know this is the wrong forum but couldn't find an AVG howto on Kubuntu forums. PLEASE help.

---

### Post by mikewhatever on 2007-01-31
Is there any reason I should not be able to update?

---

### Post by mahiyar on 2007-02-01
mike when avg is installed using AI's method the line "gksudo avggui" in avg.desktop is very important, have you put this line correctly, else try running gksudo avggui from terminal and see.

---

### Post by mikewhatever on 2007-02-01
Thanks Mahiyar. It worked.

---

### Post by gorg on 2007-02-03
i have 6.06 and it worked for me, thanks

---

### Post by ethoslight on 2007-02-23
Thanks much for this nice howto!

---

### Post by Nemix77 on 2007-02-24
Thx very much for this how to.  :) 

Um, just one question does AVG run in the background like Firestarter  without the GUI being launched?  Oh, and I'm not talking about the scheduled scans or updates but I mean On-Demand Virus protection like if I insert a disc that contains a Virus.  Sorry if it's already been answered.  

This is my first post on the Ubuntu forum and on any linux forum for that matter, but gotta say you guys sure have alot of how to's for newbie's to Ubuntu.  Got myself set up to Ubuntu very easily and quickly.  

Thnx to all!

---

### Post by Perfect Storm on 2007-02-24
No, it doesn't run in the background. Primarly Free AVG can detect virus', and that's it. Virus in Linux is a "millenium event". The Anti-virus applications on linux are used for E-mail servers, network to protect windows users.

---

### Post by Nemix77 on 2007-02-24
Guess I'll fit under that category, as I'm dual booting Windows XP  and will be trying to tripple boot Vista soon if it's possible.  Still it's better than nothing.  Thx.  :)

---

### Post by PortKreede on 2007-02-27
Thanks so much for the How-To.  Super easy for a *nix n0ob like me to follow.
:KS :KS :KS :KS :KS

---

### Post by sagasha on 2007-03-02
Hi,
I was using SUSE 10.2 and of course the rpm file worked. I bought a liense and also received the updated file avg75lms-r39-a0859.i386.rpm. This installed fine.

Question is when using your directions for Ubuntu, the free avg71fls-r30-a0791.i386.rpm installed fine but when trying to add the update, I get the error:

(Reading database ... 116216 files and directories currently installed.)
Unpacking avg75lms (from avg75lms_r39-1_i386.deb) ...
dpkg: error processing avg75lms_r39-1_i386.deb (--install):
 trying to overwrite `/opt/grisoft/avg7/bin/avgscan', which is also in package avg71flm
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 avg75lms_r39-1_i386.deb

Any ideas? The file avg75lms_r39-1_i386.deb is only an update and cannot be installed alone.

Thanks

---

### Post by Prometheus.172214 on 2007-03-02
Woah ! You The Man .......... Awesome Stuff. 

(Hmmm, paranoid home users reminds me of a guy whose call I took, way back when I was a newbie agent in Tech Supportl. McAfee kept giving him notifications about the internet status and registry changes in Windows and did all the usual notification stuff that it does and the result was this guy went into paranoia believing that someone was breaking into his system.)

---

### Post by sagasha on 2007-03-03
Please ignore my post. I see as of March 1, they are offering 7.5 in a .deb file (avg75lms-r43-a0967.i386.deb) in the paid version.

---

### Post by grunge09 on 2007-03-03
I have the AMD64 verison of Ubuntu 6.06 that I did an online upgrade to 6.10.  

I installed Alien, I could not download the AVG RPM, said file not found.   So I went to GRIsoft's site and found  avg71flm-r30-a0791.i386.rpm

from there I was able to get the registration code.  But after that things go wrong.

here's a copy of the log.  

mkdir: cannot create directory `avg71flm-r30': File exists
mkdir: cannot create directory `avg71flm-r30/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/avg71flm
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpam (soname 0, path libpam.so.0, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: avg71flm-r30: No such file or directory

Is this program for 32 bit OS and not for the 64 BIT OS?

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Perfect Storm on 2007-03-03
It's only 32bit program. I havn't got any successful feedback from 64bit users.

---

### Post by grunge09 on 2007-03-03
I was hoping you were not gonna say that.  

Could you update your howto" stating this is for 32 bit Ubuntu only.

---

### Post by Perfect Storm on 2007-03-03
Considered done.

---

### Post by sagasha on 2007-03-26
AVG now has a free verision for Ubuntu/Kubuntu, it's at:
[http://free.grisoft.com/softw/70free/setup/avg75fld-r45-a0973.i386.deb]("http://free.grisoft.com/softw/70free/setup/avg75fld-r45-a0973.i386.deb")

---

### Post by Perfect Storm on 2007-03-26
Sounds great! Then I have to rewrite the howto when I get time. :KS

---

### Post by sagasha on 2007-03-26
Ya, I think so. You have to be root to run (at least to update and apply license, if you buy it.) Sudo doesn't work, so what I did was to tell it to run as a different user (root) and added a root password through -> system settings ->User management, and it works great.

---

### Post by Perfect Storm on 2007-04-21
Howto updated

---

### Post by tjl30 on 2007-04-22
You said at the beginning that you almost never get virus' but I got one 2 days ago through wine. Ubuntu and Ubuntu Server are my only OS's.

---

### Post by Perfect Storm on 2007-04-22
It's properly false setection, it happen alot. All the time I have used Linux I never got a virus.
It aren't the first time that AVG makes a false detection on a Linux system, it's not uncommon.

---

### Post by sagasha on 2007-04-24
This works with Free version. As of 04/24/2007 avg75fld-r45-a0973.i386.deb on page [http://free.grisoft.com/doc/5390/lng/us/tpl/v5]("http://free.grisoft.com/doc/5390/lng/us/tpl/v5")

Click "System Settings"
Click "User Management"
Click "Administrator Mode"
Click "Show system accounts"
Highlight "root"
Click "Modify"
ClicK "Password & Security"
Add Password (I used sudo password)
Click "OK"
install avg.deb package.
Right click on icon. (It will be under Utilities)
Select "run as different user"
user "root"

That should do it.

---

### Post by carney1979 on 2007-04-28
VERY nice!

Here's a little script to check individual files or whole directories.

Note that the script needs to be placed in your ~/.gnome2/nautilus-scripts folder and it needs to be executable. 

```
#!/bin/bash
avgscan -scan -heur -smart -macrow -report /home/david/virusscanresults -repok $@
```

You will need to change "david" to your username. :) 

Just right-click on the file or folder and select Scripts >> Whatever-you-named-your-script

It works recursively on folders.

Enjoy!

David

---

### Post by benfindlay on 2007-04-28
Installed AVG on 7.04 and got the following error:

> Can't get license information,
avgscan output:

License initialization failed with the license number %"2@WEO%\X/H\.]?-I22,Z;-:AF,2;4,:GOJ%.
AVG7 Anti-Virus command line scanner
Copyright (c) 2006 GRISOFT, s.r.o.
Program version 7.5.45, engine 442
Virus Database: Version 269.6.1/776  2007-04-25

I know that in this guide before, it used to talk about registration for the free version, is this my problem? If so, anyone know what I need to type in?

Thanks in advance!

---

### Post by sagasha on 2007-04-29
Did you try this? It works on my box with 7.04

[I]This works with Free version. As of 04/24/2007 avg75fld-r45-a0973.i386.deb on page [http://free.grisoft.com/doc/5390/lng/us/tpl/v5](http://free.grisoft.com/doc/5390/lng/us/tpl/v5)

Click "System Settings"
Click "User Management"
Click "Administrator Mode"
Click "Show system accounts"
Highlight "root"
Click "Modify"
ClicK "Password & Security"
Add Password (I used sudo password)
Click "OK"
install avg.deb package.
Right click on icon. (It will be under Utilities)
Select "run as different user"
user "root"

That should do it.[/I]

---

### Post by benfindlay on 2007-04-30
> **sagasha said:**
> Did you try this? It works on my box with 7.04

[I]This works with Free version. As of 04/24/2007 avg75fld-r45-a0973.i386.deb on page [http://free.grisoft.com/doc/5390/lng/us/tpl/v5](http://free.grisoft.com/doc/5390/lng/us/tpl/v5)

Click "System Settings"
Click "User Management"
Click "Administrator Mode"
Click "Show system accounts"
Highlight "root"
Click "Modify"
ClicK "Password & Security"
Add Password (I used sudo password)
Click "OK"
install avg.deb package.
Right click on icon. (It will be under Utilities)
Select "run as different user"
user "root"

That should do it.[/I]

Itake it you use kubuntu? On ubuntu myself, so its slightly different code I think. Anyway, tried it and it still gives me the same error. Any ideas?

---

### Post by benfindlay on 2007-04-30
fixed it with ```
sudo avgscan -register
``` and then used 70FREE-TX-IB-P1-C01-S139FC-327-9FPB as the registration code (its the old code for free version!

Not sure if someone else posted this solution earlier, just thought I would post it in case anyone has the same problems as me!

---

### Post by Perfect Storm on 2007-04-30
Strange it doesn't ask me for that on a fresh install (done that on 2 PCs), that's why I removed the registration part from the howto.

---

### Post by benfindlay on 2007-04-30
maybe I did something wrong in setting it up.

Anyway, it works at least! It could well be that there was a problem with the install, i.e. something didnt go quite right on my system that I missed. I would have thought that they would have automated free version install by now anyway!

Cheers

---

### Post by mwiebelhaus on 2007-04-30
how do u make it able to update mine says you cannot update because you do not have something permissong something

---

### Post by motang on 2007-05-01
Excellent thanks for the info. :)

---

### Post by duderduderini on 2007-05-23
Hi
Nice guide to installing 
 i did as recommended yet when i try to launch i get the following message
"Failed to execute child process "/usr/share/applications/avg.desktop" (Permission denied)"
What gives
I have tried to find answer to no avail..
Thanks Nick
Really trying to become an ex windows addict

---

### Post by davidjd on 2007-05-24
Worked GREAT!!  Thank You!

---

### Post by nickpaton on 2007-05-28
Please note that grisoft have now updated their downloaded file and the first line of the HOWTO should now read:

```
sudo dpkg -i avg75fld-r47-a1022.i386.deb
```

The rest of this excellent HOWTO still works as expected.

Many thanks for it.

EDIT:  There is a problem with the updated file, which for me stops AVG from actually launching.
When clicking on the App >Sys Tools > AVG a password prompt comes up and I complete, but then AVG simply does not load.

Credit to Techno-mole who has supplied [this]("http://free.grisoft.com/softw/70free/setup/avg75fld-r45-a0973.i386.deb") link to the older file in the HOWTO.

This works fine.

Also he suggests (from an earlier page in this huge post) that the following should be run to make sure that all dependencies are loaded (mine wasn't on a box which had been updated to Feisty from Edgy):

```
sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2
```

Again thanks to Techno-mole for this and could you possibly look into using the updated file, AI

---

### Post by nickpaton on 2007-05-28
Update to the above

I decided to update AVG from the .deb (r45-a0973) in the HOWTO to the latest one (r47-a1022).

Removed the launcher, and attempted to remove the old .deb via Synaptic using complete removal option.
Did not uninstall but produced the following error message:

> E: avg75fld: subprocess pre-removal script returned error exit status 100

So in summary this older version is marked as being still installed and I cannot find a way to uninstall it

Decided to try simply installing the new .deb but using the HOWTO to see if the new version checks for old versions and uninstalls before installing the new one and got the following error message:

```
~/Desktop$ sudo dpkg -i avg75fld-r47-a1022.i386.deb
(Reading database ... 126983 files and directories currently installed.)
Preparing to replace avg75fld 7.5.45_a0973 (using avg75fld-r47-a1022.i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: warning - old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg75fld-r47-a1022.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 100
Errors were encountered while processing:
 avg75fld-r47-a1022.i386.deb
```

Then tried to reinstall the old version again and got a similar error message to the above:

```
~/Desktop$ sudo dpkg -i avg75fld-r45-a0973.i386.deb
Password:
Selecting previously deselected package avg75fld.
(Reading database ... 126983 files and directories currently installed.)
Preparing to replace avg75fld 7.5.45_a0973 (using avg75fld-r45-a0973.i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: warning - old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg75fld-r45-a0973.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 100
Errors were encountered while processing:
 avg75fld-r45-a0973.i386.deb
```

The reason for this has to be that this older version is still installed and operating, but I cannot see a way of turning it off to uninstall it.

Thought I'd mention this since I guess it could become a problem in the near future with people like me who decide to uninstall the old version and try to install the new one.

---

### Post by EEVOL on 2007-05-28
Well I have having the same problem, I installed the updated .deb file using this tut but it simply would not load.

So, I downloaded the old file from the original tut and it installed just fine.  The problem is, everytime I try to update, it'll download everything but I get the following error:

> Online update failed.
Reason: Error occurred while processing the update files.

I've installed avgfree on my ubuntu laptop in the past, but now that I'm installing this on my desktop, it's been giving me some major headaches!!

EDIT 1: Ok I checked my laptop and tried to update avg, but it gives me the same error.  I've been able to update my laptop install in the past.  What gives!!??  Anyone else have the same problem?

---

### Post by EEVOL on 2007-05-28
> **nickpaton said:**
> Update to the above

I decided to update AVG from the .deb (r45-a0973) in the HOWTO to the latest one (r47-a1022).

Removed the launcher, and attempted to remove the old .deb via Synaptic using complete removal option.
Did not uninstall but produced the following error message:



So in summary this older version is marked as being still installed and I cannot find a way to uninstall it

Decided to try simply installing the new .deb but using the HOWTO to see if the new version checks for old versions and uninstalls before installing the new one and got the following error message:

```
~/Desktop$ sudo dpkg -i avg75fld-r47-a1022.i386.deb
(Reading database ... 126983 files and directories currently installed.)
Preparing to replace avg75fld 7.5.45_a0973 (using avg75fld-r47-a1022.i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: warning - old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg75fld-r47-a1022.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 100
Errors were encountered while processing:
 avg75fld-r47-a1022.i386.deb
```

Then tried to reinstall the old version again and got a similar error message to the above:

```
~/Desktop$ sudo dpkg -i avg75fld-r45-a0973.i386.deb
Password:
Selecting previously deselected package avg75fld.
(Reading database ... 126983 files and directories currently installed.)
Preparing to replace avg75fld 7.5.45_a0973 (using avg75fld-r45-a0973.i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: warning - old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg75fld-r45-a0973.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 100
Errors were encountered while processing:
 avg75fld-r45-a0973.i386.deb
```

The reason for this has to be that this older version is still installed and operating, but I cannot see a way of turning it off to uninstall it.

Thought I'd mention this since I guess it could become a problem in the near future with people like me who decide to uninstall the old version and try to install the new one.


I removed mine by doing the following:

> sudo apt-get --purge remove avggui

---

### Post by nickpaton on 2007-05-28
The purge command didn't work for me - I manually deleted all the AVG files from /opt/grisoft dir and it's messed up something somewhere and I'm in a kinda loop where it's looking for a file which doesn't exist any more.

Fortunately with having a second box I'll copy the AVG files back into that directory and see if I can delete via Synaptic or purge.

Thanks for the help though

---

### Post by swejuggalo on 2007-05-28
From "AVG free forum", avg:s own forum. Works to solve the problem on 7.04 too. Just updated from r45 to r47...

[http://forum.grisoft.cz/freeforum/read.php?10,96855,backpage=,sv=](http://forum.grisoft.cz/freeforum/read.php?10,96855,backpage=,sv=)


"2) 3) 
To reinstall or uninstall avg, running avg daemons must be stopped. 
This should be done automatically, but there is an issue with 
Ubuntu 6.10 which is using dash instead of bash as a default 
/bin/sh shell and as a consequence the initscripts which are used to 
stop the daemons during the process of package removing 
don't work correctly. This should be fixed in next .deb package. 
As a workaround, you can either stop the daemons manually (A), 
or modify the initscript files to work correctly ( B ). 

(A) 
To stop the daemons, you can kill the daemons and remove their 
lockfile by running commands 

$ sudo killall avgscan 
$ sudo rm /var/lock/avgd 

Then the reinstall or uninstall by dpkg should work. 

( B ) 
To modify the initscripts to work correctly, change the first line 
of the file /opt/grisoft/avg7/etc/init.d/avgd.all 

from: 

#!/bin/sh 

to: 

#!/bin/bash"

---

### Post by nickpaton on 2007-05-28
Thanks for that - I'll need to try another day though - late here LOL!

Could you quickly explain how to apply the the bash commands - presumably its just a case of moving to that directory and applying the commands - thanks loads

---

### Post by swejuggalo on 2007-05-29
I used "sudo gedit /opt/grisoft/avg7/etc/init.d/avgd.all" in the termial. At the top of the avgd.all file, replace #!/bin/sh with #!/bin/bash and save. The most simple way since the uninstall and reinstall then can make the commands for you

---

### Post by DougieFresh4U on 2007-06-02
I have tried many ways to get rid of avg. opt file is empty.. this is all terminal out put:
[B]dougie@DougiesToyBox:~$ sudo apt-get --purge remove avggui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting avg75fld instead of avggui
The following packages will be REMOVED:
  avg75fld*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160550 files and directories currently installed.)
Removing avg75fld ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg75fld (--purge):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 avg75fld
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~$ sudo killall avgscan 
dougie@DougiesToyBox:~$ sudo rm /var/lock/avgd 
dougie@DougiesToyBox:~$ sudo apt-get --purge remove avggui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting avg75fld instead of avggui
The following packages will be REMOVED:
  avg75fld*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160550 files and directories currently installed.)
Removing avg75fld ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg75fld (--purge):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 avg75fld
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~$ sudo gedit /opt/grisoft/avg7/etc/init.d/avgd.all
dougie@DougiesToyBox:~$ 
[/B]

---

### Post by EEVOL on 2007-06-02
Did you replace #!/bin/sh with #!/bin/bash?  After doing the edit on avgd.all?

Once you do that, run the following;

```
sudo apt-get --purge remove avggui
```

It should be able to remove the files.


I'm still having a problem trying to update AVG on Feisty Fawn.  Is anyone else having this error when updating?

```
Online update failed.
Reason: Error occurred while processing the update files. 
```

AVG is running as root, so it's not a problem with the permission.  It downloads the files, but before it can apply the updates it gives me that error.
Anyway to fix it?

---

### Post by DougieFresh4U on 2007-06-02
I can't find avg any where on my machine (Feisty). It's  listed ONLY under: **Applications>Accessories>AVG for Linux Workstation**.
That is the only place I see it . Is there some code or some thing to see where it is?
Thanks

---

### Post by swejuggalo on 2007-06-03
The file avgd.all should be in /opt. Try " find /opt -name avgd.all " or maybe even " find /* -name avgd.all ". Edit this file as I have written before

---

### Post by Thehound on 2007-06-13
Thanks for the input on this. To almost say this is worthless can't be further from the truth. As was said, you might be swapping Windoze files and want to scan them before exposing Bill to them, but there is another great purpose of this. If you have Windoze on another partition, this could kill rootkits that blind every AV known to Bill as Windows antivirus apps rely on what the OS sees. Scanning from Linux would give a true picture, Also, if you run a server, there is a such thing as php viruses. They may not hurt your machine due to permissions, but they can wreak havoc for anyone that connects to an infected server with scripting enabled, There really is a point to these antivirus apps and I like AVG due to speed and familiarity, as well as stability.

---

### Post by techno-mole on 2007-06-18
ok, ive been usnig avg for a while now on my fiesty install, but for the last 3 days when its run a scheduled test it says its found a virus, so where does it put them ? like under windows it will create a file called virus vault, so where does it create this file in linux ? ive looked and im stuffed if i can find it.
ive also run tests manually and it doesnt find anything so im scratching my head a little as to whats going on, it does seem related to me starting the scheduled tests, im lazy so setting it up to scan itself is a bonus, had it set like this under windows, but if anyone has had similar or knows where i can find the virus vault file then id be grateful for the help.
cheers

---

### Post by Yarias on 2007-06-27
Thanks for the guide.  Worked like a charm.

Nice to be able to scan from linux on my dual boot box.

---

### Post by Midahed on 2007-07-04
Has anyone had any success getting AVG to work on Ubuntu 7,04 Feisty **64-bit**?  I know the AVG product isn't packaged for the 64-bit environment, but I wondered if anyone had managed to get it working manually using the --force-architecture option in dpkg?  Or are there reasons why that approach would never work?

I'd try it myself, but I'm still too new to Linux and I know that if it doesn't work I'll spend the next week or so trying to get round the problems. :(

I know there's really no risk to my system if I don't have a virus scanner, but I regularly transfer data to and from Windows machines, so for that reason I'd like to be able to use AVG.

Thanks,

Mike

---

### Post by GlennW on 2007-07-09
**_Launcher**_

Making a launcher to start AVG

```
sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktop
```

add:
```
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
```
save and exit.



So I've got the AVG file sitting on the desktop. I followed the commands above but after editing the file, there's no place that says Save or Save As so when I exit, as instructed, I loose everything that I've just done and needless to say, AVG isn't in Application>System Tools.

I need to install this as I'm running a dual boot setup with XP and of course FF 7.04.

---

### Post by Perfect Storm on 2007-07-10
If you read the buttom of the terminal when using nano you'll see how to save and exit.

<ctrl> + <o> = Save
<ctrl> + <x> = exit

---

### Post by anewguy on 2007-07-18
Thank you for an easy to follow how-to that works great!  I have used AVG on Windows for years, so I was really happy to be directed to your how-to.

thanks for the great work!:)

---

### Post by mtnwinds on 2007-07-18
Artificial Intelligence..Thanks for the instructions on how to install AVG.  All I had to do was substitute the current file name and my choice of 'gedit' and it installed perfectly.:o

---

### Post by CJJones on 2007-08-21
Worked like a charm on fiesty fawn 7.04!

Actually installed faster than on my xp laptop.

---

### Post by AnasGul on 2007-09-23
I have installed it, thanks.
It got installed in Applications->Accessories.
But when i click on "update" I get this error message, please help.
"Update process failed.
Reason: Sorry, you do not have permission to execute avgupdate".

---

### Post by Perfect Storm on 2007-09-23
You can delete that one. The "real one" is under system tool.

---

### Post by Hhkmac on 2007-09-27
A couple of years on since first post and this thread is still very helpful.. Much appreciated.. quick and clean install for a linux noob!

---

### Post by twinszg on 2007-10-04
thanks for that

---

### Post by popos123 on 2007-10-12
Hi guys, I am totaly new to ubuntu (and linux). question of Artificial Inteligence: where do you write the 2 codes for the AVG Launcher and what form and place do you save them in????

I love this OS and would appreciate some help. Thanks

---

### Post by popos123 on 2007-10-12
Hi guys, I am totaly new to ubuntu (and linux). question of Artificial Inteligence: where do you write the 2 codes for the AVG Launcher and what form and place do you save them in????

I love this OS and would appreciate some help. Thanks:)

---

### Post by Perfect Storm on 2007-10-12
You mean the sudo nano thing?
[ctrl]+[o] = Save
[ctrl]+[x] = exit

---

### Post by popos123 on 2007-10-12
No I mean these codes below. Are they writen in the Terminal Window? Also, do you write the first line and then hit enter to write the second one? Finally, in the Terminal window there was no "save" choice at the bottom

Sorry, but I am very new and I get lost. Thanks for the reply though

"Code:
sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktopadd:

Code:
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;

---

### Post by Perfect Storm on 2007-10-12
You write them in the terminal (Applications tab ---> Accessories ---> terminal.
You enter each command and press [Enter]

---

### Post by ThanadoS on 2007-10-13
hi there! 
first of all, thanks for the guide, and all the guides on this forums.
AVG works perfectly after this installation, but when I try to update it tells me, that I do not have the permission to update - what could be wrong there? I'm the only user of this computer, and entered my password for the installation of the program...

regards
    ThanadoS

---

### Post by Perfect Storm on 2007-10-13
You're using the wrong launcher. Check the launcher under Applications ---> System (and delete the oter one).

---

### Post by popos123 on 2007-10-13
I really appreciate your help AI and sorry for the bother. 

I followed your direction for Launching the program. I used the Terminal Window and the first two commands worked fine. I then cut and pasted the last command to create the shortcut in the Applications>System but the terminal window did not have any save choice. I tried all variations of [ctr]+[o] etc.by typing exactly that, by pressing the corresponding keys only (control plus +) etc. but nothing happened. Again no Save. Any suggestions??? I did however managed to get the program to scan by typing "avgscan /folder" 

Again thanks:)

---

### Post by Perfect Storm on 2007-10-13
Try instead with;

```
gksudo gedit /usr/share/applications/avg.desktop
```

instead, you can save it with point'n'click.

---

### Post by popos123 on 2007-10-14
Thanks for your patience AI. I'll get it right sooner or later. A question:

I also have Win Vista on my computer. If I catch a virus through ubuntu can my antivirus on Vista detect it or only antiviruses that run on Linux  can?? thanks :)

---

### Post by samuraiCat on 2007-10-14
AI, this was a totally painless process. Please consider writing all Gutsy documentation. Salud!

---

### Post by samuraiCat on 2007-10-14
> **popos123 said:**
> Thanks for your patience AI. I'll get it right sooner or later. A question:

I also have Win Vista on my computer. If I catch a virus through ubuntu can my antivirus on Vista detect it or only antiviruses that run on Linux  can?? thanks :)

I believe the answer is, "No." Windows acts like Linux does not exist in a dual boot. That said, you really can't "catch" a virus in Linux in a way that could harm your machine. The password/sudo thing would prevent it from getting anywhere inside your files.

---

### Post by popos123 on 2007-10-14
Thanks SamuraiCat but maybe I was not clear. On my computer I have installed both OS - Windows Vista Ultimate and Ubuntu. I choose which to run through a boot manager when I turn my computer on. So, If I am running Ubuntu and catch a virus (as difficult as it might be), when I reboot and run Vista can I detect the virus with the Windows based Antivirus program? Sorry for been simplistic but I just started on Linux and know nothing, but I would like to learn. Thanks

---

### Post by Perfect Storm on 2007-10-14
No, sorry. Only the other way around (as far as I know)

---

### Post by popos123 on 2007-10-14
thanks guy you have been great!!!!!!!!!!!!!!!

---

### Post by drewster77 on 2007-10-16
Thanks, always used AVG in my Windows days  (which are long gone)

---

### Post by switchover on 2007-10-24
> **Artificial Intelligence said:**
> You can delete that one. The "real one" is under system tool.

doesn't seem to be a system tool menu on the applications menu. Am having the same problem: do not have permission to update AVG anitvirus. The only shortcut availble is under the accessories menu on the applications menu.

---

### Post by mikewhatever on 2007-10-24
Have you followed the how-to on the fist page of this thread?

---

### Post by switchover on 2007-10-24
yep but it came up with errors will try again.

---

### Post by mikewhatever on 2007-10-24
In case you get errors again, try to copy them or take a screenshot, and post here.

---

### Post by Nick Payne on 2007-10-30
The AVG i386 deb can be installed on amd64 by using the --force-architecture option:

sudo dpkg -i --force-architecture avg75fld-r49-a1130.i386.deb

This worked for me on Gutsy amd64, and the installed avggui runs ok. However, when scanning a path containing the eicar test virus, it doesn't report any infection, so appears pretty useless.

---

### Post by chiefbearclaw on 2007-10-31
This solved my update problem. *Note - Once you update this way and reboot, try to update via the program GUI itself again. I noticed that after I ran the update procedure below and rebooted, the regular program update GUI (clicking the button) now works as well.

```
sudo gedit /usr/share/applications/avg.desktop
```

(File:/usr/share/applications/avg.desktop)

Copy and Paste the following lines, save and exit.

```
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
```

Now, for an AVG Anti-Virus update launcher work-around.

```
sudo gedit /usr/share/applications/avgupdate.desktop
```

(File:/usr/share/applications/avgupdate.desktop)

Copy and Paste the following lines, save and exit.

```
[Desktop Entry]
Name=AVG Updater
Comment=Antivirus
Exec=sudo /opt/grisoft/avg7/bin/avgupdate -o
Icon=/opt/grisoft/avggui/prog/pixmaps/avgupdateico.png
Terminal=true
Type=Application
Categories=Application;System;
```

It will now update but only via the shortcut you've now made.
____
I am using LinuxMint 4.0 beta1 and installed the avg75fld-r49-a1130.i386.deb via saving it to my desktop, right clicking, and opening with GDebi Package Installer. Then did the above. Works fine. Hope I helped someone. Don't forget to reboot after installing any Anti-Virus as this can also lead to permission issues. Happy Halloween!

---

### Post by Scimu on 2007-10-31
Worked fantasticly on Gutsy. Thanks a lot for this

---

### Post by johnz8 on 2007-11-04
That tip worked great. It cleaned up my ugly AVG install and made everything work great. Thanks so much!!!!

---

### Post by simplypatrick on 2007-11-10
**chiefbearclaw**


Thank you!
Worked great on Gutsy!

---

### Post by helmut888 on 2007-11-10
Thanks, nice to see that I'm on the right track with this stuff. I do have a couple of comments and a question though. Firstly, why don't you use the /etc/sudoers file to allow no password challenge on loading the avggui with "gksu avggui" or "sudo avggui"? This would allow the update button to work. Also, since the daemon based scanner requires dazuko (and I can't get it working), do you recommend to run it at startup?
Thanks in advanced.
Phil

---

### Post by Perfect Storm on 2007-11-10
> why don't you use the /etc/sudoers file to allow no password challenge on loading the avggui with "gksu avggui" or "sudo avggui"?

Security wise, that is not recommenable.

> Also, since the daemon based scanner requires dazuko (and I can't get it working), do you recommend to run it at startup?

It's a waste of resources to have it run as a home user. If you have your linux PC only for example LAN security for windows boxes.

---

### Post by k1234 on 2007-11-10
good info

---

### Post by Tachions on 2007-11-14
every time i try to install avg it says a broken pipe is preventing it, or something like that, I even tried to install manually through the terminal, same thing about "broken pipe"? 

anyone with the same issue, and fixes???? 

please let me know thanks!

---

### Post by mahiyar on 2007-11-15
A clear cut case of bad plumbing in your computer ? :) :) Maybe a previously wrongly or partly installed package of avg is preventing an install, try to run this  from CLI >>apt-get remove --purge avg***, where avg *** is the name of the avg package and then try to reinstall.

---

### Post by firedancer on 2007-11-15
just suffered hackattack , dualbooting and using ubuntu at the moment (cause it's not my pc)

so if i install it ,i can the scan the windows partition ,sounds cool, but will it cause any trouble having symantec on it, i understand that it will be installed on the ubu side and not the ms side ,so it shouldn't then

---

### Post by Beagleburt on 2007-11-15
Wow! 32 x pages & counting....Have finally exhausted myself searching for relevant posts, so I shall post my queries here - (please forgive me if I have repeated someone else) - as I have NOT got the AVG installation disk (for my Kubuntu 6.06 LTS dual booting with XP on a Dell 3000 with 512MB RAM & 40GB HDD  - Linux partition) & there are NO explanations on HOW/WHERE to install neccessary prerequisite modules/libraries on the AVG Documentation pdf...GRRRR! :mad:

So, could some kind person please tell me Where from I can download & How/Where do I install:
pygtk2-libglade version 2.0.0 or higher  &
libstdc++-libc6.2-2so.3   :confused:

Alot of people say "Why bother with 'safe-as' Linux?"; but I prefer to follow the advice of those who say that we should be responsible, & not pass virii onto other (Windows) users; also as more & more people begin to use Linux, then some virus-writers looking for a challenge & the kudos that goes with it in underground circles...will INEVITABLY start concocting nefarious code for the various flavours of Linux OS...& I think that Ubuntu would be the largest usergroup?

Although - at the moment - with 32 pages of forum help on what should be such a simple task, I think that it will be a while before the threat gets real!

'bye, 'bye for now - TKU in anticipation - B.

---

### Post by DiJoNK on 2007-11-22
i got an error message when i installed AVG through Terminal...

aldi@Aldi-Ubuntu:~$ sudo dpkg --install avg75fld-r49-a1130.i386.deb
Selecting previously deselected package avg75fld.
(Reading database ... 98930 files and directories currently installed.)
Unpacking avg75fld (from avg75fld-r49-a1130.i386.deb) ...
Setting up avg75fld (7.5.49_a1130) ...
Installing 'avgd' service initscripts...
Registering 'avgd' service to runlevels...
 Adding system startup for /etc/init.d/avgd ...
   /etc/rc0.d/K20avgd -> ../init.d/avgd
   /etc/rc1.d/K20avgd -> ../init.d/avgd
   /etc/rc6.d/K20avgd -> ../init.d/avgd
   /etc/rc2.d/S20avgd -> ../init.d/avgd
   /etc/rc3.d/S20avgd -> ../init.d/avgd
   /etc/rc4.d/S20avgd -> ../init.d/avgd
   /etc/rc5.d/S20avgd -> ../init.d/avgd

(update-desktop-database:8852): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing avg75fld (--install):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 avg75fld

Then i typed avgscan (PATH that to be scanned), and it was working...seems that my avg has already installed even though there were an error message when i installed through terminal..but there is more problem. when i click from Applications-Accesories-AVG for Linux Workstation..it didn't open the AVG's GUI...

do u have any idea with this ? what should i do ?

---

### Post by DiJoNK on 2007-11-22
uppss sorry...i think i got a good luck today. my avg is running normally and the AVG GUI is running too...
so there is no more problem...^^

---

### Post by Perfect Storm on 2007-11-25
It seems the free AVG for Linux is no more - So I'm going to move this thread to outdated guides.

---

### Post by mahiyar on 2007-11-25
If you are saying it must be true, but can you please clarify, even today they are offering free download for linux.

---

### Post by Perfect Storm on 2007-11-25
Just checked there page for a half hour - not a shadow of the free AVG, but if you have the link - I might have missed it.

---

### Post by mahiyar on 2007-11-26
Is this link correct [http://free.grisoft.com/doc/5390/us/frt/0](http://free.grisoft.com/doc/5390/us/frt/0)

---

### Post by Perfect Storm on 2007-11-26
Ah, yes. Thanks! I'm moving thread back.
Funny, how I could missed it. But sometimes you stare to long on the problem to see the obvious. :popcorn:

---

### Post by mahiyar on 2007-11-26
So thiis thread still has a chance of breaking the world record or something of being the longest thread. LOL

---

### Post by Perfect Storm on 2007-11-26
Still on the track :)....but we have much longer threads around ubuntuforums ;)

---

### Post by Dumpy Dumpster on 2007-11-27
Sorry fellas, I have worked through all this 'techno-speak' as best I can and AVG STILL does not function without Terminal inputs.  I am afraid that this is why Ubuntu and it sister Os's will never oust Microsoft. Once installed, programmes just work straight off with Windows - sad but true.  So either AVG could not care less about the download files they publish or else the Ubuntu OS is sadly lacking.  What a shame, but then one only has to look up the VOLUMES of  Ubuntu help pages available to see the scale of the problem.

---

### Post by Perfect Storm on 2007-11-27
First, if you want help...that's a very bad way to express it. Secondly Windows applications doesn't just works out of the box (try search  via google and you'll see). Thirdly if you want to rant this isn't the place.
</end>

---

### Post by cccc on 2007-12-02
hi 

could someone post pls its **/etc/init.d/avgd** and **/opt/grisoft/avg7/data/set_vers.cfg** from AVG 7.5 under gutsy ?
these files are missing and cannot remove, install or reinstall AVG 7.5

---

### Post by swejuggalo on 2007-12-03
tried installing with sudo dpkg -i -force-all filename.deb ? You have tried the latest version of avg?

---

### Post by cccc on 2007-12-03
> **swejuggalo said:**
> tried installing with sudo dpkg -i -force-all filename.deb ? You have tried the latest version of avg?

I tried the latest version of AVG, but still doesn't work.

---

### Post by czarandom on 2008-01-05
install succeeded without a hitch except updates seem to fail silently, Program settings window and test function throw the following errs (respectively)

[INDENT]```
Traceback (most recent call last):
  File "/opt/grisoft/avggui/prog/mainview.py", line 194, in __service_item_settigs_cb
    config_window = configview.CAvgGuiMainSetProperties()
  File "/opt/grisoft/avggui/prog/configview.py", line 137, in __init__
    self.__fsh_default = fsh.CView([home_dir], False, False)
  File "/opt/grisoft/avggui/prog/fsh.py", line 744, in __init__
    self.model = CStore(pathnames, selected, expand, w_message)
  File "/opt/grisoft/avggui/prog/fsh.py", line 349, in __init__
    self.add_pathname(pathname, selected, expand, w_message)
  File "/opt/grisoft/avggui/prog/fsh.py", line 587, in add_pathname
    self.expand(iter)
  File "/opt/grisoft/avggui/prog/fsh.py", line 419, in expand
    entries = self.dir_entries.get_entries(pathname) 
  File "/opt/grisoft/avggui/prog/fsh.py", line 145, in get_entries
    self.__logger.warn(detail)
  File "/opt/grisoft/avggui/prog/logger.py", line 125, in warn
    self.__log(WARN, format, args)
  File "/opt/grisoft/avggui/prog/logger.py", line 85, in __log
    msg = format.encode(sysinfo.CLocaleInfo().get_value('console_encoding'))
AttributeError: 'exceptions.OSError' object has no attribute 'encode'

```[/INDENT]


[INDENT]```
Traceback (most recent call last):
  File "/opt/grisoft/avggui/prog/mainview.py", line 175, in __test_item_run_cb
    select_window = select.CSelect()
  File "/opt/grisoft/avggui/prog/select.py", line 23, in __init__
    self.__select_view = fsh.CView([os.path.expanduser("~")], False, True)
  File "/opt/grisoft/avggui/prog/fsh.py", line 744, in __init__
    self.model = CStore(pathnames, selected, expand, w_message)
  File "/opt/grisoft/avggui/prog/fsh.py", line 349, in __init__
    self.add_pathname(pathname, selected, expand, w_message)
  File "/opt/grisoft/avggui/prog/fsh.py", line 568, in add_pathname
    self.expand(self.get_iter_root())
  File "/opt/grisoft/avggui/prog/fsh.py", line 419, in expand
    entries = self.dir_entries.get_entries(pathname) 
  File "/opt/grisoft/avggui/prog/fsh.py", line 145, in get_entries
    self.__logger.warn(detail)
  File "/opt/grisoft/avggui/prog/logger.py", line 125, in warn
    self.__log(WARN, format, args)
  File "/opt/grisoft/avggui/prog/logger.py", line 85, in __log
    msg = format.encode(sysinfo.CLocaleInfo().get_value('console_encoding'))
AttributeError: 'exceptions.OSError' object has no attribute 'encode'

```[/INDENT]

I'm wondering if all that broken py has something to do with my using the live session disk.  Did ubuntu eat the py perhaps?

My goal is to make a nice little bulletproof recovery kit that I can use on my friends' ill boxes.  Any thoughts as to the cause?  All I can figure without pouring over *all* the code is that it's throwing an exception while trying to set the char encoding of the text in the ! box.  

Thanks in advance.

---

### Post by narayansmate on 2008-01-19
Followed the instructions and worked beautifully. Thanks a bunch. Much much better and easier to install than CLAMAV. gave up on that...

---

### Post by dlizar on 2008-04-26
HELP....i installed avg for linux on ubuntu 8.04 and it loads ok but when ever i try to update virus definitions it tell me i dont have authorization...how can i fix this problem????Update process failed.
Reason: Sorry, you do not have permission to execute avgupdate

---

### Post by shaunat on 2008-04-26
Hi Everyone I'm new at this I have just started using ubuntu 7.10 two weeks ago and have installed ubuntu 8.04 and have  the same problem as dlizar above, AVG says it installed fine but the same problem as above with trying to update ?????

Cheers

shaunat

---

### Post by Perfect Storm on 2008-04-26
```
gksudo avggui &
```
in the terminal. Are you sure you went and used the right launcher in applications tab ---> System tools. It regenerate one itself which wont let you update.

---

### Post by shaunat on 2008-04-27
Thanks heaps Artificial Intelligence, I have done that in the terminal and it is now updateing, it's all new to me but I love ubuntu and do as much reading as I can to learn about it thatks again for the fix.

Regards

Shaun.

---

### Post by Norm24 on 2008-04-27
This will also work,and you won't have to keep opening Terminal and entering the code:


Click on "System-->Preferences-->Main Menu" To launch the menu editor.

Find the AVG entry in Accessories. Right click its entry and select Properties.

In the "Command" box add gksudo to the beginning (ie. make it look like this "gksudo avggui")

Click on close for the AVG option then the same for the menu.

You will be now prompted for your password when necessary as AVG will only run with your password being supplied

---

### Post by shaunat on 2008-04-27
Thanks heaps Norm24, that works great, I'm leaning new stuff everyday with ubuntu.

Cheers

Shaun

---

### Post by oscarmeyer51 on 2008-05-01
OK, Since AVG is no longer available for Ubuntu or Linux in general, how do I get if off of my system? I have tried manually removing and using the Synaptic Update Manager and get the same results each time. A wonderful cryptic note stating that I have a removal error of 150.

Here is the gist of the error message:

Removing avg75fld ...
 * Stopping avgdkill: 246: Illegal number: -
local: 246: 6081: bad variable name
( not running)
 *                                                                       [fail]
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing avg75fld (--remove):
 subprocess pre-removal script returned error exit status 150
Errors were encountered while processing:
 avg75fld
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

I will post this at the AVG Grisoft site as well to see if they can post a reply.

Thanks....

---

### Post by rakavka on 2008-05-03
Hi to all
I'm new to linux..
Does antivirus run all the time (real protection like on windows ) or only scan option ?
Thnaks

---

### Post by Perfect Storm on 2008-05-03
Only scan option as it isn't really needed, it's more to scan e-mails you're passing to your windows friends to make sure they don't get virus.

---

### Post by rakavka on 2008-05-03
AI
And can it hurt somehow windows as a second OS?
Thanks

---

### Post by Perfect Storm on 2008-05-03
> **rakavka said:**
> AI
And can it hurt somehow windows as a second OS?
Thanks

Please rephrase, I don't understand what you mean, thanks :KS

---

### Post by rakavka on 2008-05-05
:))
I have a dual boot, Windows and Ubuntu. If I download virus in Ubuntu, can it harm Windows files or make some damage when I start windows?

thanks

---

### Post by Perfect Storm on 2008-05-05
I honestly don't think so. But I don't know, as it's years since I had Windows, maybe ask in our security forum about it.

---

### Post by phoenix_abhi on 2008-05-08
Hello A I Thanks man. In linux it is not necessary, but I like the tutorial, It worked without any hickup

---

### Post by sonhadorpr on 2008-05-09
Hello all:
I'm getting this error msg.
What I'm trying to do is run the Virus Scan from linux unto the Windows drive, and manuelly deleting the corrupted files.  Hoping that'll work!
But I'm having a problem installing AVG
Thank you!


sudo dpkg -i avg75fld-r51-a1243.i386.deb
(Reading database ... 103653 files and directories currently installed.)
Unpacking avg75fld (from avg75fld-r51-a1243.i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing avg75fld-r51-a1243.i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./opt/grisoft/avg7/etc/antispam/sc12.bin.full.2007.03.30.09.04.53')
Errors were encountered while processing:
 avg75fld-r51-a1243.i386.deb

--

 Registered Linux User #457355

ROM

---

### Post by phoenix_abhi on 2008-05-09
> **Artificial Intelligence said:**
> ```
gksudo avggui &
```
in the terminal. Are you sure you went and used the right launcher in applications tab ---> System tools. It regenerate one itself which wont let you update.

That launcher not exist in systems tools. I have to use the command every time for updating database. Any other alternate ?

---

### Post by Perfect Storm on 2008-05-09
You can just add it yourself. You have command to add in alacarte.

---

### Post by philcleaver on 2008-08-13
> **phoenix_abhi said:**
> That launcher not exist in systems tools. I have to use the command every time for updating database. Any other alternate ?


Hi.
As a BRAND new user went through the same frustration .
Searched forums  tried various sudo hints etc  (using Hardy Heron) 

BUT FOUND AN EASY FIX   
AND it just works 

1 click on system 
2 go to synaptic manager
3 reload
4 enter in search field   AVG 


you will see a number of hardy  complient avg downloads 

select those
hit apply and run 

then come back and look for amavisd new 
get that 
 and then python -libavg

load them up 
 and REBOOT  !

worked like a treat   upgrades and runs  sweet as a nut 
Hope that helps

---

### Post by lisati on 2008-08-13
> **phoenix_abhi said:**
> That launcher not exist in systems tools. I have to use the command every time for updating database. Any other alternate ?

You don't need to use (gk)sudo to do the updates - just add your normal user name to the avg user group, log off, and on again.

---

### Post by lisati on 2008-08-13
IMPORTANT: to do the updates without the need for (gk)sudo, read the AVG documentation! Add yourself to the avg user group. It works!

---

### Post by seanksg on 2008-11-23
> **Artificial Intelligence said:**
> 
**_Launcher**_

Making a launcher to start AVG

```
sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktop
```

add:
```
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
```
save and exit.

You can now start AVG by going to Applications tab ---> System Tools.


I got to this point.  How do you save from the GNU Nano program?

---

### Post by Perfect Storm on 2008-11-23
save = [ctrl]+[o]
exit [ctrl]+[x]

---

### Post by seanksg on 2008-11-23
> **lisati said:**
> IMPORTANT: to do the updates without the need for (gk)sudo, read the AVG documentation! Add yourself to the avg user group. It works!

How do you do this?

---

### Post by ||Z0di4C|| on 2008-11-25
hey this is just what i am looking for but i have one problem first i would download it then in the package installer screen i would hit install files at first it would say close other programs but i had nothing running then for some reason out of the blue it started installing but in the status area it said ERROR: failure to satisfy all dependencies (broken cache) 
so what do i do ? please help

---

### Post by superthin on 2009-03-15
I encountered error like **sonhadorpr**'s one.

```

(Reading database ... 201189 files and directories currently installed.)
Unpacking avg75fld (from avg75fld-r51-a1243.i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing avg75fld-r51-a1243.i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./opt/grisoft/avg7/etc/antispam/sc5.bin.full.2007.01.28.16.09.00')
Errors were encountered while processing:
 avg75fld-r51-a1243.i386.deb

```

I use Ubuntu 8.04. Please tell me, what should I do. Thanks a lot!

---

### Post by esalnoj on 2009-04-05
Say AI, would you please update the f-prot tutorial to include xfprot as a .deb and f-prot as a .tar.gz?

I tried compiling the f-prot i686 tar, but the .config file can't be located in the new folder.

Many thanks

Esalnoj

---

### Post by Perfect Storm on 2009-04-05
I have moved to 64-bit, that's why this guide havn't been updated. It's quite diffrent.

---

### Post by cccc on 2009-07-09
hi

I've installed on my jaunty the newest avg package **avg85flx-r287-a2632.i386.deb** from the avg webpage:

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

but avggui won't start:
```

# dpkg -l | grep avg
ii  avg85flx                               8.5.287                                              AVG Anti-Virus for Linux

# sudo avggui
sudo: avggui: command not found

```

What's wrong and howto solve this problem?

---

### Post by cccc on 2009-07-10
The newest AVG deb package **avg85flx-r287-a2632.i386.deb** seems to be Jaunty incompatible...

---

### Post by mohit_iitp on 2009-07-13
i had downlaoded the .deb package and then used Gdebi Package installer but i do not get any launcher/link to avg antivirus ,how can i get it

---

### Post by Magna on 2009-07-18
I have done everything asked. I have added the words to the text file and saved. But when I go to the Applications => System Tools => AVG Antivirus it asks for my password then does nothing. No matter how much I click on it.

This is probably a stupid question but what should I do? I use 8.04 Ubuntu if that helps anyone ...

Thanks if anyone is willing to help ...

---

### Post by kitebari on 2009-07-23
Same here. Downloaded it and clicked on it, it said installed. Tried again and it said it was installed but I can't get it to appear on the menu, just shows a strange screen, kind of terminal one. Any ideas?

> **mohit_iitp said:**
> i had downlaoded the .deb package and then used Gdebi Package installer but i do not get any launcher/link to avg antivirus ,how can i get it

---

### Post by lisati on 2009-08-03
As far as I know the latest Linux-friendly version of AVG is command line only....

edit: a common complaint I saw for version 7.5 of AVG free when it was still current was easily solved by reading the AVG documentation and the solution was a lot more elegant than some of those suggested in these forums: don't be scared to read the instructions that comes with software you are installing!

---

### Post by lisati on 2009-08-03
OK here's what I did for version 8.5 of AVG free:
[LIST=1]
[*]Download the .deb file from [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)
[*]Open the downloaded file
[*]click on "install package" and enter password
[*]Go to terminal
[*]Use ```
man avgscan
``` to get help on scanning
[*]Use ```
man avgupdate
``` for help on doing updates
[/LIST]

I have to go soon (an get-together with some friends I'd forgotten about) so it might be a few hours before I'm able to get back and share ideas.

edit: it seems that you might need to learn some command-line stuff, e.g. avgscan for the scans, and avgupdate for the updates.

---

### Post by lisati on 2009-08-04
These notes assume you have downloaded and installed AVG free v8.5 from [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

It would appear that AVG free v8.5 is command-line based. Some of the features are noted here, and more information can be gleaned from the relevant "man" pages.

**Starting AVG**
The main AVG daemon/task is controlled with the *avgctl* command. To get it started, use: ```
sudo avgctl --start
```

**Updating AVG**
You need a working internet connection. Use: ```
sudo avgupdate
```

**Scanning**
For a simple scan of your home folder, use: ```
sudo avgscan ~
```


Hope this helps somebody.

---

### Post by Soren37 on 2009-08-10
I'm a new Ubuntu user who's trying to get AVG 8.5.  I'm running Ubuntu 8.10.  I've followed the guide on the first page and tried the codes above.  However, the most I have is a small picture that's *supposed* to open AVG.  Could someone please help me?

---

### Post by thinksuccessgal on 2009-08-11
Thanks for the Tip. I have trouble with looking for antivirus software that I can rely on and that is freely available. This indeed is very useful! :)

---

### Post by dmflad on 2009-09-06
I am running Ubuntu 9.04 32bit. Had downloaded AVG Free Linux and followed their instructions. Ended up with bad unusable install that would not uninstall.

Took multiple runs of "find" and "rm" and a few reboots to get all traces of AVG 8.5 linux free off my LT.

Tried install again using lisati's info (#365, #366 of this thread) and now have working install of AVG 8.5 Free for Linux. Also did a " sudo avgctl --stat-all " command after install and startup.

True, its all command line and no menu item for it but that is okay. I was able to update virus files and run scans.

I run the WinOS version on work PC and am moving files across Win, Red Hat and Ubuntu platforms and various user accts daily. I run an anti-virus on my LT so I can be proactive about not spreading viruses in the places I routinely go.

Thank you lisati!

---

### Post by Colin_L on 2009-09-12
> **dcstar said:**
> Clamav won't repair infected files (only delete them), looking at the documentation for AVG it has a command line run option to actually repair files.

And looking at the AVG Linux FAQ, these are the system requirements:

[I]Necessary libraries:

    * pygtk2.0 >= 2.0.0
    * pygtk2.0-libglade >= 2.0.0
    * python >= 2.2.2
    * libstdc++-libc6.2-2.so.3
    * libc.so.6
    * libexpat.so.0[/I]

I have done the install but when I click on the item in System Tools it seems to load but then I dont see anything.  do I need to D/L these libraries before the gui will work?

---

### Post by M!SF!TS on 2009-09-13
Two Issues:

#1. whats the command to update AVG via command line
is it this?  :::  $ avgscan update  :::   I did this and it went good... the out put was this...
################################################
nick@linux-box:~$ avgscan update
AVG command line Anti-Virus scanner
Copyright (c) 2009 AVG Technologies CZ

nick@linux-box:~$ 
################################################

Yes... i know it looks good right ? so good, i am confused... there was no out put saying update complete or virus definition files updated, or NOTHING!!! LOL!!!

if that out put was good, someone please confirm... please... its literally driving me crazy.

okay thanks... now here is my second Issue...



#2. I have no GUI. (personally i prefer to use the command line, it is faster, lags my system less, saves resources, and has less chance of giving me the all annoying 'freeze' and turns a dark shade of grey...) I would like to have a GUI, for i dont know... just to have one ? they look pretty ?

But mostly i want a GUI for it because of Issue #1. I WANT TO KNOW IF IT UPDATED!!!

I ran this...

> **arnieboy said:**
> The following is the easiest way to create a menu item for AVG antivirus and also to allow antivirus signature updates happening from the AVG GUI

```
sudo gedit /usr/share/applications/avg.desktop
```
paste the following lines in the empty file that opens:


save and exit.

AVG Antivirus will appear in Applications --> System Tools

Awesome howto by the way. **Good job AI.**


I have the AVG in my Apps-->Sys-tools  But... when i click it, i get nothing. no response or nothing, sooooo i did this

~$ ps -U nick

and their was nothing under my processes that said ANYTHING related to AVG, soooo


How do i activate my GUI...

This is how i installed AVG, its the brand new one AVG 8.5 it is a .deb package and if you want it your self you can get it here...

wget [http://www.avg.com/filedir/inst/avg85flx-r287-a2632.i386.deb](http://www.avg.com/filedir/inst/avg85flx-r287-a2632.i386.deb)


Please help.... thank you

---

### Post by wekebu on 2009-09-15
#lisati, greetings my Kiwi friend.  Thank you for your instructions in #365+366.  I'm scanning for the first time since having Ubuntu!   

I forward emails to my Windows friends & family and it's good to have an anti-virus scanner for them.

How would I scan one folder, as oppose to the entire /home folder?

---

### Post by M!SF!TS on 2009-10-03
> **wekebu said:**
> #lisati, greetings my Kiwi friend.  Thank you for your instructions in #365+366.  I'm scanning for the first time since having Ubuntu!   

I forward emails to my Windows friends & family and it's good to have an anti-virus scanner for them.

How would I scan one folder, as oppose to the entire /home folder?


just type the directory... example

$ avgscan /home/nick/whateverforlderitisyouwanttoscan/

---

### Post by wekebu on 2009-10-03
Duh, of course, thanks! :oops:  silly me!

---

### Post by prabath_fun on 2009-10-19
Hi,
   I used the first page how to in Ubuntu 9.04 with avg85flx-r287-a2632.i386.deb pages, which I got as latest package from the link. I got launcher under Applications ->System tools. But, nothing It launches.

Please help me....

Prabath

---

### Post by Perfect Storm on 2009-10-19
avg 8.5 is command-line application and don't have gui.

---

### Post by prabath_fun on 2009-10-20
I got GUI which is under development and works fine through the forum in AVG website

[http://forums.avg.com/in-en/avg-free-forum?sec=thread&act=show&id=12565](http://forums.avg.com/in-en/avg-free-forum?sec=thread&act=show&id=12565)

It is really good.

Prabath

---

### Post by wild_ecstasy1985 on 2009-10-20
I double-clicked on the .deb file and installed it using the package manager. (It installed all by itself, did not ask me to accept license agreement - so I am wondering if it really installed) However, I am not able to create the launcher as the avggui.desktop file does not exist :( 

The output of the installation is as follows: 

```

sagar@sagar-laptop:~/Desktop$ dpkg -i avg85flx-r287-a2632.i386.deb 
dpkg: requested operation requires superuser privilege
sagar@sagar-laptop:~/Desktop$ sudo dpkg -i avg85flx-r287-a2632.i386.deb 
(Reading database ... 200721 files and directories currently installed.)
Preparing to replace avg85flx 8.5.287 (using avg85flx-r287-a2632.i386.deb) ...
 * Stopping avgd (not running)                                           [ ok ]
Unpacking replacement avg85flx ...
Uninstalling 'avgd' service initscripts...
Unregistering 'avgd' service ...
 Removing any system startup links for /etc/init.d/avgd ...
   /etc/rc0.d/K20avgd
   /etc/rc1.d/K20avgd
   /etc/rc2.d/S20avgd
   /etc/rc3.d/S20avgd
   /etc/rc4.d/S20avgd
   /etc/rc5.d/S20avgd
   /etc/rc6.d/K20avgd
Setting up avg85flx (8.5.287) ...
Installing 'avgd' service initscripts...
Registering 'avgd' service to runlevels...
 Adding system startup for /etc/init.d/avgd ...
   /etc/rc0.d/K20avgd -> ../init.d/avgd
   /etc/rc1.d/K20avgd -> ../init.d/avgd
   /etc/rc6.d/K20avgd -> ../init.d/avgd
   /etc/rc2.d/S20avgd -> ../init.d/avgd
   /etc/rc3.d/S20avgd -> ../init.d/avgd
   /etc/rc4.d/S20avgd -> ../init.d/avgd
   /etc/rc5.d/S20avgd -> ../init.d/avgd
Registering with license: 8FREE-VHRDW-PAP8C-E64FA-9ZMGD-6D6L2-EEHG
AVG command line controller
Copyright (c) 2009 AVG Technologies CZ

License was successfully changed.

Processing triggers for man-db ...


```

---

### Post by prabath_fun on 2009-10-21
I downloaded the GUI seperatly from link in [http://forums.avg.com/in-en/avg-free...=show&id=12565](http://forums.avg.com/in-en/avg-free...=show&id=12565) link and used. 
Works fine..
Prabath

---

### Post by phamtuanamd on 2009-11-27
> **M!SF!TS said:**
> just type the directory... example
$ avgscan /home/nick/whateverforlderitisyouwanttoscan/
Do it can automatically delete the infected files viruts?

---

### Post by newbieEXE on 2009-12-04
Does this work for avg version 8.5?
the step where we're suppose to remove tht file from usr/share/applications/avggui.desktop can't work, The file isnt there =(

---

### Post by ugo1 on 2009-12-08
> **phamtuanamd said:**
> Do it can automatically delete the infected files viruts?

Good question I can setup a scheduled job which scan a folder and move / delete infected files?

Regards

Ugo

---

### Post by mettehe on 2010-02-08
I have a dualboot (Ubuntu 9.04 - Vista). Microsoft Essentials is installed on Vista. Is it necessary to install an antivirus on Ubuntu too? If yes, why?

---

### Post by sriny1512 on 2010-02-28
Thank you :guitar:

---

### Post by maddg3241 on 2010-03-05
is it a 90 day trial or is is forever

---

### Post by JackRock on 2010-03-05
> **maddg3241 said:**
> is it a 90 day trial or is is forever

Depends on which version of AVG you get.  Check out avg.com for details on that.

---

### Post by Nisal on 2010-03-17
avg package s not available any more :(

---

### Post by xzimppledink on 2010-06-30
I just want to comment on the virus's in Linux. I loaded Ubuntu 10.04 and within a couple of days evolution started malfunctioning. I ran a virus scan with the native AV and got 3 virus's listed. I am a political activist and perhaps have been targeted, my switch from XP to Linux was for that very reason. My XP files should have been about 5 gigs but constantly read over 55 Gigs.  Huge untraceable files do not appear in Linux as they did with windows. In that respect the switch to Linux has been successful, however Linux based Virus's do exist I can assure you.

---

### Post by bodhi.zazen on 2010-07-01
> **xzimppledink said:**
> I just want to comment on the virus's in Linux. I loaded Ubuntu 10.04 and within a couple of days evolution started malfunctioning. I ran a virus scan with the native AV and got 3 virus's listed. I am a political activist and perhaps have been targeted, my switch from XP to Linux was for that very reason. My XP files should have been about 5 gigs but constantly read over 55 Gigs.  Huge untraceable files do not appear in Linux as they did with windows. In that respect the switch to Linux has been successful, however Linux based Virus's do exist I can assure you.

Finding a virus on your hard drive is not the same thing as being infected.

What files did you find ?

There are indeed Linux viruses, but your system has been patched against then known viruses ...

There are reports of Windows viruses running in wine , but the do little "harm" so long as you are not running wine as root.

Also be aware there are more false positives then true positives, so just because something was detected does not mean it was a virus, you need to investigate further ....

---

### Post by doublewitt on 2010-07-09
> **Nisal said:**
> avg package s not available any more :(

**It's still available...**
[COLOR="Blue"]look here [/COLOR]
[http://free.avg.com/ca-en/download.prd-afl]("http://free.avg.com/ca-en/download.prd-afl")

---

### Post by AmirK47 on 2010-07-12
does this not work with 64 bit isadora?

---

### Post by KasRoth on 2010-07-14
Hello! Sorry to bother you, but I cannot get the window picture that you linked to show up for me at all. I'm a brand new user and need the antivirus to get onto my school's wireless. I'm learning, but fairly green to say the least. I followed the commands but could not get the rm to run and there were a few other minor errors. It did prompt me to have a user passcode, and entered it in, but i have no way to tell if it's running.

---

### Post by Perfect Storm on 2010-07-14
The old version of AVG had gui, but it's now commandline now instead.

---

### Post by farmerjohn73 on 2010-08-09
Hi,

I am using Lenovo G400 series with 80 GB HDD, 1GB Ram, Intel dual core.

I successfully installed avg8.5 and I successfully update the database and I can also scan root for viruses.

But I didn't find the avg processes in resource monitor.  When I tried to start avg by typing "sudo avgctl --start" it says another avg is already running.

When I try to configure the scheduler by typing "sudo avgsched" it says command not found.

How do I make it start at boot up, update automatically and scan computer automatically ?

pls help.

---

### Post by Perfect Storm on 2010-08-09
If you're not running a mail server and do not switch files with your windows partitions, it's rather pointless what you're asking for, and waste of resources. Linux is not Windows. Why would you scan your computer on every bootup?

---

### Post by farmerjohn73 on 2010-08-11
Dear AI,

I do swap files from my windows desktop.

bye the way,  I fixed the problem of scanning / and updating avg.

But I am unable to run scheduler.  It says command not found.

any body pls help.

---

### Post by JCyberinux on 2010-09-01
sorry to ask here in this thread, now i install it but it seems not work...

so my question is, how to uninstall or remove AVG? thanks!

---

### Post by farmerjohn73 on 2010-09-09
Jcyberinux,

try this command:


sudo /opt/avg/avg8/bin/uninstall.sh

as to my question of running avgsched no body has replied to me as yet.  no body is seeing this thread???

---

### Post by Perfect Storm on 2010-09-09
More like nobody is using anti-virus applications - so it's rarely checked.

---

### Post by Noampod on 2010-12-03
Hi, I have installed avg85 using the information contained in this thread. When I use the code:

sudo avgctl --start

I get this error from the CLI:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
AVG command line controller
Copyright (c) 2010 AVG Technologies CZ

Starting avgd
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
Operation successful.

Is there anything I can do to correct the error?

---

### Post by nomko on 2010-12-03
AVG only has command line operated server edtions for Linux systems [http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf).
 
I really don't think a virusscanner is needed for Linux as a primairy tool. But on the other hand, knowing there's a growth in smartphone's, PDA's and other gadgets which runs on Linux and are very vulnerable for attacks through bluetooth or mms or email, it might be taken in consideration that those virusses or trojans may work on desktop versions of Linux.
 
But if u want to have a good virusscanner, consider Clamav (in combination with Calmtk). Why? Main reason: with Clamtk it is also possible to scan Windows formatted drives!

---

### Post by Noampod on 2010-12-03
Thanks for your reply nomko. Even with that error I am able to run AVG, I was just wondering why and how to solve it. I will take a look at the anti virus scanner you recommended. Is there a how to in the ubuntu forums for those?

---

### Post by haqking on 2011-07-15
> **aneelamishra said:**
> hello sir/mam sorry to ask such question is ubuntu safe for surfing internet, does it need any antivirus if so which is the best antivirus for ubuntu plz reply thank you.


**[Free Antivirus]("http://www.freeantivirus.co.in/")**


Try reading the thread you have posted to ;-)

---

### Post by Elfy on 2011-07-15
Closed - more necro spam.

---

