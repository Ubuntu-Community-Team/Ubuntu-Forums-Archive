---
title: "HOWTO : install beryl from AWESOME SVN repository"
date: 2007-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by AlexenderReez on 2007-03-24
Firstly,this is my first howto and i hope this guide can helpful....:) 

it is true beryl is still beta version and it is quite dangerous ...but bear in mind . . . there is no such thing as guarantee while using linux(even ubuntu itself)=[COLOR="Blue"]my Principe[/COLOR] and that is what is the purpose of existing forum ,to discuss problem..
 ***[COLOR="Blue"][COLOR="Red"]no risk no fun[/COLOR][/COLOR]***:guitar: 


firstly you need to enable your 3d support (whether xgl ,aixgl or Nvidia support). ..look at beryl wiki how to enable it.....


firstly remove all your previous beryl and configuration by enable hidden view in home folder ,then delete .beryl~ folder and .emerald~ folder...**OR **by using terminal...

> sudo mv ~/.beryl ~/.beryl-backup
sudo mv ~/.bdm ~/.bdm-backup
sudo mv ~/.emerald ~/.emerald-backup
sudo rm -R /usr/local/lib/beryl
sudo rm /usr/local/lib/libseom*
sudo rm /usr/local/bin/beryl*
sudo rm /usr/local/bin/heliodor*
sudo rm /usr/local/bin/seom*
sudo rm /usr/local/bin/screenletsd*
sudo rm -R /usr/lib/beryl
sudo rm /usr/lib/libberylsettings*
sudo rm -R /usr/lib/emerald
sudo rm /usr/bin/beryl*
sudo rm /usr/bin/emerald*
sudo rm -R /usr/share/beryl
sudo rm -R /usr/share/emerald

then edit source list sources.list ,add this awesome repository--->(FOR ADDING REPOSITORY PLEASE REFER TO [http://shame.tuxfamily.org/repo/?page_id=29](http://shame.tuxfamily.org/repo/?page_id=29) AND [http://shame.tuxfamily.org/repo/?page_id=30](http://shame.tuxfamily.org/repo/?page_id=30) ) 

FOR RELATIVE STABLE SVN VERSION(having all latest stable plugins )
> deb [http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/](http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/relatively-stable/) ./



FOR UNSTABLE SVN VERSION (having **daily** update plugins ) 

> deb [http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/unstable-daily/](http://download.tuxfamily.org/myberyl/shame/debian-sid/beryl-svn/unstable-daily/) ./

then add key

> wget [http://download.tuxfamily.org/myberyl/shame/A42A6CF5.gpg](http://download.tuxfamily.org/myberyl/shame/A42A6CF5.gpg) -O- | apt-key add -

or by manual - - -open tex editor copy and paste all key below..save....and using software sources --> authentication -->import key file --->choose saved previous key

> -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQGiBEWW9UARBACMtiONcrI2Qt3oWu7QgUzo9ES07rRvmrmpVoGgNvmkK6bxqDxY
kQ/xIGmY/9q81vBvmGDL1Dl04PDROKTKpeedHX0NeJTGDXjo0rcsbPiV4MeRIky/
2LAcQRo8t9zTfkhVHWDkkSxC4UV8ibbyM1d3g0m7FAnyQgPwtOOBsBKkXwCgn+kn
ckSEuO3VA8Tr+wTqpPTv+x0D/3LmK1Wclv4vlS9+ntyqHAiO5sFP1nPgxihLQ78B
pB/eQbei/6ldZIH8aCQhYlKUZZ/G71misx6fe9OfXQ52puORAn1wyQfRp34GTObI
4ffl2rR6Ux+Tuo7DqYsTNdaPAO73ck9FY/0VOD9RpkvVxph1wYlR7LfZI+QeoYgW
x1HXA/0SnHTUQlLDJpTp6HPp7pAKX5d3nL2R6w+wvowgnZW9GGew9rT8bKhkQEa1
n0ixcbjbEED6eS6ip7AbhxcS4AzLoV/ZtRcaZG1r8z82itewPeatmphCcG3DFA7j
UqsmiuFBspY0DDWYXUH+KEEdz06PkqSt/+cCJBKvcJPpRt5Y87Qmc2hhbWUgKGJl
cnlsIHJlcG9zaXRvcnkpIDxzaGFtZUBzaWR1eD6IYAQTEQIAIAUCRZb1QAIbAwYL
CQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEHPmsPqkKmz1zcUAmwUS0qLcC1FXMFXp
ICMulpzAtrs+AJ0fVSHox9RWhJ0QCR7xNxaIP1Ovh7kCDQRFlvVIEAgAqG6f+PXq
swQI8KgoEsyU9N6QmtD75dOJhCAb1bK3jbwRZHqS9eWAqbQB3/7HNVfH+SifzGb9
Lsd7KT8FS8uk8olKKvtpu/RUsiVXE7tJ8/u8VB3KIZYacan1xBa6PlQC2pXv4xJr
CQC2Z8el0Tu/g8l7o1G9dsavoHoVE55dxwIp+Mb2hxXqW/29qAn9zEuTXzwDCjYG
rPPaN3w8T7/GLIh70w0f5WCTz4ob1Aa3o/76S4fUrPP2M7vJgW5cSGS6FJHs6qR2
pBY5NSqgOnE7YP0SG7t1AWwRdr+q8oXktq0NFwGnU+Kl4UVX+x3mWXtrPMkCzYXu
w54HtRVy9dj0AwADBQgAo0CU3hgttCmvCCMNz/pIjBTS3pqnWIhP15oFVEBTQRBQ
kvr7/sIGDN8Xkbl3zYXIOItW1p8Es0X3jJ1p/6zGP2hyvb39oULzUSAzlTvi4hxL
xoLs7CdytiWmhQ5DWMX4w9+uJIlQ2UaYkw2L9KyJjRdmo4fKrOUmbQ+FZ5bZYZ9C
Mfa3/s1NvhMYSXWoEXs7SO/n8VhI1UDRGqB9gGsV/uqYDV4dtjMCrWTDfZ2TrgIC
nS/t5NWUy2mE2GBDRBdztrYmt7Rx1QrmoEu078agRWF3nQu6jhB5QqwQCJXiGCBj
4l75D/9XpehO1auyzR7fT0m8fMBjf01XT98ifkIeV4hJBBgRAgAJBQJFlvVIAhsM
AAoJEHPmsPqkKmz1lmAAn19AdGOiK+oqtOvy1UMmR+MZnGXeAJ4tQ46Occ+Vl7n6
hr05MWkxwSg0Zw==
=PIoM
-----END PGP PUBLIC KEY BLOCK-----


**_package list_**[COLOR="Blue"](TAKEN FROM SHAME (MAINTAINER REPOSITORY) BLOG)
[/COLOR]

Beryl-svn base packages:
The main packages required for the beryl experience, including beryl itself, plugins and a window decorator

beryl
beryl-core
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-settings
beryl-settings-bindings
libberylsettings0
libberylsettings0-gconf
libberyldecoration0
emerald
libemeraldengine0

Beryl-svn extra and development packages:
Extra packages providing more functionality and eyecandy and development headers

beryl-settings-simple - Much more simplified alternative to beryl-settings
beryl-plugins-unsupported - Extra plugins considered too new or unstable for beryl-plugins at this point
beryl-plugins-unsupported-data - Plugin data
beryl-plugins-vidcap - Enables video capture of a desktop session
emerald-themes - Extra themes for emerald
aquamarine - Alternative window decorator for kde which uses kwin themes
bdock - WindowMaker style dock app
beryl-dev - Development headers for beryl
libberylsettings-dev - Development headers for beryl-settings
libemeraldengine-dev - Development headers for emerald window decorator
aquamarine-dev - Development headers for aquamarine

shame extra packages:
Extra packages including unofficial plugins and beryl related or complimentary packages

beryl-shame - metapackage and upgrade/removal script for the beryl-shame repos
beryl-plugins-shame - Unofficial plugins not yet part of beryl-plugins or beryl-plugins-extra
- firefly
- screensaver
- stars
- wallpaper
- widget
seom - video capture library (needed for vidcap/capture plugin)
kicker-compiz - beryl/compiz aware pager applet for kde
taskbar-compiz - beryl/compiz aware taskbar applet for kde

**[COLOR="Red"]TOO IMPORTANT NOTE FOR FEISTY USER ...[/COLOR]** **[COLOR="Blue"]~EDIT~[/COLOR]**
 noted that feisty using python2.5 which is always the latest python but in SVN repository choose to use python2.4.4...so you need to to use SPECIFIC beryl-settings-bindings by  used FIRST POST ATTACHMENT!...(BERYL-SETTINGS-BINDINGS-UBUNTU JUST FOR EXPERIMENT(SECOND ATTACHMENT BUT NEXT UPDATE I GUESS SHAME WILL CHANGE IT,SO PLEASE IGNORE SECOND ATTACHMENT IN SECOND POST)
double click that(install) before any future step and don't upgrade beryl-settings-bindings
**Installation | Upgrade | Removal**

You can install the base beryl packages with this command:
> sudo apt-get install beryl

Or the base packages plus unofficial plugins (beryl-plugins-unsupported and beryl-plugins-shame)
> sudo apt-get install beryl-plugins-shame


Or you can use this command to install everything in the repo:
> sudo apt-get install beryl-shame
[B]
beryl-shame other commands[/B]

If beryl-shame is installed it can be used to perform a few basic functions, these commands should be run in a konsole/terminal as root user:
> sudo beryl-shame remove

This will completely remove all packages from the repos, useful if you no longer want to use beryl or want to use packages from a different repo.
The reported problems with it failing because of unknown packages is fixed and it should work for everyone now.
> sudo beryl-shame upgrade

This will check for and install any available upgrades, useful if you want to upgrade beryl packages without doing a full dist-upgrade.
Previously, this command simply checked for updates to beryl-shame then completely removed and reinstalled all packages regardless of whether or not the other packages had upgrades available.
Now it checks for updates for each individual package and only upgrades those for which upgrades are available.
> sudo beryl-shame hold

This will hold/pin all installed beryl-shame packages to stop them being upgraded with dist-upgrade, useful if problems are reported (especially with unstable-daily) and you want to keep a working version but still dist-upgrade other, non-beryl related packages.
> sudo beryl-shame unhold

This will unhold all previously held/pinned beryl-shame packages and make them available for upgrade again, for example if reported problems have now been fixed.
> sudo beryl-shame version

This will simply display the currently installed version of beryl-shame, useful if you wish to report problems and want to know the revision you are using...


[B][U]
A Little Tips & Tricks[/U][/B]

~only enable frequently used plugin to get better performance...

~as far as i'm using beryl,(even in official repo) there is dead bugs for mini-viewpoint plugin under extra...and i don't sure whether it is already fixed or not...if not  fixed yet then if you enable it..it will disturb your cube/rotate cube , wall and Desktop plane plugins performances (crash your system when you use it and you need to set up all over again..if you just unchecked that specific plugin it won't fixed that problem...

~MAKE SURE TO BACKUP YOUR BERYLSETTING EACH TIME AFTER SUCCESS  UPGRADE
(to newbie , you can do this by show hidden files in home folder and open .beryl~ files,copy all in that(or just berylsetting)  then save in other folder than home folder)

~to get the setting...open beryl-settings(simple) and put it in the best quality...then configure it using beryl-setting...like change cubecaps wallpaper,skykindom....disable  ungrab windows wave...change animation duration..

~ for the best setting vidcap plugin. . .install mencoder
> sudo apt-get install mencoder

then create a folder in home folder,let say 'berylvidcap'

> mkdir berylvidcap

open beryl-settings-->under extra---> capture-->
output-- >
> file:///home/[COLOR="Red"]YOURUSERNAME[/COLOR]/[COLOR="Red"]berylvidcap[/COLOR]/beryl-capture.seom

--> post processing -->

> seom-filter /home/[COLOR="Red"]YOURUSERNAME[/COLOR]/[COLOR="Red"]berylvidcap[/COLOR]/beryl-capture.seom | mencoder - -ovc xvid -xvidencopts bitrate=1200 -o /home/[COLOR="Red"]YOURUSERNAME[/COLOR]/[COLOR="Red"]berylvidcap[/COLOR]/capture-`date +%d-%m-%y_%H%M`.avi

~change~
[COLOR="Red"]YOURUSERNAME[/COLOR] = username to login
berylvidcap= name of folder that you have create

ALL CREDITS
all credits goes to great maintainer --> SHAME ( [http://shame.tuxfamily.org/repo/](http://shame.tuxfamily.org/repo/) )
BECAUSE WITHOUT ALL HIS HARD WORKS ,THIS AWESOME REPOSITORY WON'T EXIST..

Any request , please directly contact Shame([http://shame.tuxfamily.org/repo/](http://shame.tuxfamily.org/repo/)) via support sections..

[B][COLOR="Blue"]PLEASE REFER TO MAINTAINER BLOG FOR FUTURE INFORMATION...
[/COLOR][/B]
I can't guarantee anything but as far as i'm using . . .i always have **latest** **beryl plugins ** even if just using relatively-stable section. . .

THANKS SHAME :guitar:

---

### Post by AlexenderReez on 2007-03-24
[COLOR="Red"][SIZE="4"]don't install this second post attachment or if you have already installed...please remove it first before install beryl....[/SIZE][/COLOR]

after install first attachment (in first post)

then

> sudo apt-get install beryl

> sudo apt-get install beryl-shame

---

### Post by Hangly on 2007-03-24
clancy@ubuntu:~$ sudo apt-get install beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-plugins but it is not installable
         Depends: beryl-settings but it is not going to be installed



clancy@ubuntu:~$ sudo apt-get install beryl-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl-settings: Depends: beryl-plugins (>= 0.1) but it is not installable
E: Broken packages

---

### Post by AlexenderReez on 2007-03-24
i'm using Feisty  AND I thought that only feisty user can't use beryl-settings-bindings from that repository. .. .

[SIZE="5"]
so[/SIZE]

[COLOR="Blue"][FONT="Arial Black"][SIZE="4"]after you have remove all previous installed beryl then download my attachment...which is the first attachment ......=beryl-settings-bindings 0.2.0 (old beryl setting..)[/SIZE][/FONT][/COLOR]
[COLOR="DarkRed"][SIZE="4"]
install it....(double click)[/SIZE][/COLOR]


then 

try  [SIZE="4"][COLOR="SeaGreen"] (mine success with using feisty and unstable daily)[/COLOR][/SIZE]

> sudo apt-get install beryl

> sudo apt-get install beryl-shame

---

### Post by AlexenderReez on 2007-03-24
[[IMG]http://img255.imageshack.us/img255/6508/51196403ir4.th.jpg[/IMG]](http://img255.imageshack.us/my.php?image=51196403ir4.jpg)

[[IMG]http://img154.imageshack.us/img154/926/extraja5.th.jpg[/IMG]](http://img154.imageshack.us/my.php?image=extraja5.jpg)


[[IMG]http://img157.imageshack.us/img157/661/fgqx1.th.jpg[/IMG]](http://img157.imageshack.us/my.php?image=fgqx1.jpg)


[[IMG]http://img133.imageshack.us/img133/8493/screenshotsu3.th.jpg[/IMG]](http://img133.imageshack.us/my.php?image=screenshotsu3.jpg)

[[IMG]http://img260.imageshack.us/img260/2033/wmdg6.th.jpg[/IMG]](http://img260.imageshack.us/my.php?image=wmdg6.jpg)


[[IMG]http://img256.imageshack.us/img256/8476/regfdaz1.th.jpg[/IMG]](http://img256.imageshack.us/my.php?image=regfdaz1.jpg)

---

### Post by Treviño on 2007-03-25
Why duplicate?
**[Mine]("http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/")** is working since long time and supports (works with) feisty too...

---

### Post by shame on 2007-03-25
Hi, I'm shame,  maintainer of the repos mentioned in the guide.
Of course evryone is free to do whatever they want but here is my official word on the subject: [http://shame.tuxfamily.org/repo/?page_id=45&xdforum_action=viewthread&xf_id=3&xt_id=27&pstart=0&search_words=#100](http://shame.tuxfamily.org/repo/?page_id=45&xdforum_action=viewthread&xf_id=3&xt_id=27&pstart=0&search_words=#100)

---

### Post by AlexenderReez on 2007-03-26
it is just alternative repo..and it doesn't claim any better or not but just  to mention as alternative or variable..i'm sorry...
if it make Trevino angry . . .i'm really sorry....:(

---

### Post by Treviño on 2007-03-28
I'm not angry... absolutely!
Just I thought that this was a new repo, considering that maybe beryl is "closing" I just warned that there's another repo yet :P

Of course open source means also "more resources", so no problems for me :)

---

### Post by ppan76 on 2007-03-30
This might be a stupid question. I am using kubuntu and when I add the source in source.list and then run apt.get upgrade it cannot find Packages file.

For  adept Manager the source has to be like this

deb [http://download.tuxfamily.org/mybery...tively-stable/](http://download.tuxfamily.org/mybery...tively-stable/) /

not "./"

---

### Post by AlexenderReez on 2007-04-01
please refer to the link besides the address...it is because  it is not full address of link:)

---

### Post by loadfoo on 2007-05-02
This :
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)
Thank's

---

### Post by AlexenderReez on 2007-05-06
> **loadfoo said:**
> This :
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)
Thank's


Actually this howTo you can get it in [http://doc.gwos.org/index.php/HowToInstallBeryl](http://doc.gwos.org/index.php/HowToInstallBeryl)


P/S : actually i just realized it...huhu:popcorn:

---

### Post by adarkenigma on 2007-06-09
i can't install shame's plugin. 
doin -f install doesnt fix it .. wat am i doin wrong? 

```
Selecting previously deselected package taskbar-compiz.
Unpacking taskbar-compiz (from .../taskbar-compiz_3.5-1-shame-0_i386.deb) ...
Selecting previously deselected package beryl-shame.
Unpacking beryl-shame (from .../beryl-shame_0.2.1-1-shame-0_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/beryl-plugins-shame_0.2.1-1-shame-0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
root@ubuntu:~# sudo apt-get install beryl-plugins-shame
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  beryl-plugins-shame
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
72 not fully installed or removed.
Need to get 0B/9900kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 116415 files and directories currently installed.)
Unpacking beryl-plugins-shame (from .../beryl-plugins-shame_0.2.1-1-shame-0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/beryl-plugins-shame_0.2.1-1-shame-0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/beryl/libwidget.so', which is also in package beryl-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/beryl-plugins-shame_0.2.1-1-shame-0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

also you said 
"Double click Install before any other step and don't upgrade beryl-settings-bindings"

i am not that advanced in linux  how do stop the tray icon from sayin i need update

thanks

---

### Post by adarkenigma on 2007-06-10
anyone?

---

### Post by adarkenigma on 2007-06-10
okay i was able to install beryl but i cant open beryl settings manager .. like emerald theme manager loads .. i can change skin and stuff but i cant open beryl manager... not even simple manager.. can someone help me?

---

### Post by adarkenigma on 2007-06-11
many thanks :)

---

### Post by AlexenderReez on 2007-10-06
this guide quite out to date....especially...Shame concentrate to compiz fusion...but nerveless...it is applicable...

---

