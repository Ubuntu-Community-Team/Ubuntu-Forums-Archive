---
title: "How TO:  Custom repo (local or remote)"
date: 2005-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by cdk on 2005-06-19
Hya m8s!
i searched around the forum looking for some info on how to create my own repo and i came up with nothing so i decided to research it and come up with a really easy way to do it and here is what i have found.

**HOWTO:  Custom repo (local or remote)**

REQ: In order to use this how to you will need several things
dpkg-dev
local/remote dir for repo
some .deb files to test
spare time!

** I will be assuming you are going to use a local repo but if you want to use one for your network then all you need to do is create the repo dir in /var/www and follow the same steps

Step One
Most systems come with the following files but just ot be safe run these
```

sudo apt-get install apt-utils
sudo apt-get install dpkg-dev

```
If you havent created your repo directory do it now (i made mine in /var/www because i use apache)
```

mkdir /home/your repo dir/

```

Step Two
Now we are going to fill our repo with some .debs (if you are making this repo then you should have some you want to install)

Step Three
We are going to create a script that will make the .debs apt-get'able
```

cd /bin/
sudo nano autorepo

```
Enter the following lines into autorepo
```

#!/bin/bash
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
sudo dpkg-scansources . /dev/null | gzip -9c > Sources.gz

```
Save the file.  Now we have to make it executable
```

sudo chmod +x autorepo

```

Step Four
We are going to create our repo packages.gz and sources.gz
```

cd /home/your repo name/
autorepo

```
you should get some output and be able to see 2 new files in the dir.  If you placed the .debs in the repo and they are good packages you shouldnt see any errors if you do get some errors its okay just continue on to the next step to verify if the script works.  You can also run this script manually too.

Step Five
Time to update your sources.list
```

sudo nano /etc/apt/sources.list

```
add the following to the bottom of the list
```

##My Repo
deb file:///path/to/repository/ reponame/

example:
deb file:///home/ repo/

and for remote:
deb http://host name or ip/ repo/

```
Its important to remeber that you need to add your repo dir with a space and then "/" otherwise apt will not beable to read the files correctly.

Lets test it out now fire up synaptic and do a repo update now search for the names of the .debs you have in your repo with any luck they will be there.

If you have any further questions PM me or reply here! I hope this helps somebody!

cheers,
   CDK

---

### Post by spacemonkey on 2005-06-19
Is there anyway to automatically add to the repo all the .deb's you've got installed on your system?  To create a sortof quick system restore?

---

### Post by cdk on 2005-06-20
sounds interesting.  im not sure how to go about it though. if you could some how output the list of packages installed on your system and then mirrior them to your repo it might work. any one else have some ideas?

---

### Post by angrykeyboarder on 2005-06-20
" Wrote 251 entries to output Packages file.
Prototype mismatch: sub main::getopt: none vs (@) at /usr/bin/dpkg-scansources line 116."

---

### Post by cdk on 2005-06-20
i have seen that error many times.  Im no expert at this but i did exactly what i wrote above on a minimal ubuntu server and everything works.  i just added some new packages to my repo to day and installed it on my workstation with no problems.  Maybe someone here will know how to fix that error.  In my experience i could still install from my repo even when i got that error.

cheers,

---

### Post by angrykeyboarder on 2005-06-20
[QUOTE=cdk]i have seen that error many times. Im no expert at this but i did exactly what i wrote above on a minimal ubuntu server and everything works. i just added some new packages to my repo to day and installed it on my workstation with no problems. Maybe someone here will know how to fix that error. In my experience i could still install from my repo even when i got that error.

cheers,[/QUOTE]

I was seemingly able to install from my repo as well. But I'd still like to know what the error was about.

Does anyone have any ideas?

---

### Post by AndyAWS on 2005-08-11
It appears that the error is caused by the scansources line in the script. I commented that line and the error went away.

My guess would be that if you don't have any sources for it to scan it kicks out the prototype mismatch.

---

### Post by aveline on 2005-08-11
[QUOTE=AndyAWS]It appears that the error is caused by the scansources line in the script. I commented that line and the error went away.

My guess would be that if you don't have any sources for it to scan it kicks out the prototype mismatch.[/QUOTE]
 dumb Q: why would you want to do this?

aveline

---

### Post by AndyAWS on 2005-08-11
If you had source files in your local repo you would want to scan for them so that you could use apt-get to build and install them...probably nothing that the average user would need to do.

---

### Post by ArthurHeng on 2005-09-30
This guide simply rocks! Thanks a lot man!

---

### Post by Velox Letum on 2005-09-30
Wonderful guide! Worked perfectly for me and helped me achieve a few things I was wondering how to do. Thanks! =)

---

### Post by caprajack on 2005-10-05
Ok

---

### Post by Brando569 on 2005-10-07
i was actually wondering about this a few days ago, awesome guide! really helpful. time to make my download directory my repo directory :)

edit:

just tried this and sadly mine doesnt work, it wouldnt matter if the directory is hidden would it? i got a few errors when i ran autorepo:

** Packages in archive but missing from override file: **
  kubuntu-pkgmenu libdvdcss2 mtaskbar-0.7 superkaramba

 Wrote 4 entries to output Packages file.
Prototype mismatch: sub main::getopt: none vs (@) at /usr/bin/dpkg-scansources line 116.

mtaskbar doesnt even exist in the directory i dunno how that got in there but the other three are there and are deb packages, the rest are tar.gz or bz2 files. synaptic didnt give me any errors that it couldnt find/access the directory any idea whats up?

---

### Post by ryan76 on 2005-10-20
I'm having a problem with setting it up:

The repository is in

/home/repo

I put this in sources.list:

deb file:///home/ repo/ 

Synaptic finds the .deb file but when I hit Apply, I get this error message:

W: Failed to fetch file:///home/./libdvdcss2_1.2.9-1ubuntu1_amd64.deb
  File not found

What should I be putting in sources.list to make it work???

---

### Post by phanboy_iv on 2005-10-31
[QUOTE=ryan76]I'm having a problem with setting it up:

The repository is in

/home/repo

I put this in sources.list:

deb file:///home/ repo/ 

Synaptic finds the .deb file but when I hit Apply, I get this error message:

W: Failed to fetch file:///home/./libdvdcss2_1.2.9-1ubuntu1_amd64.deb
  File not found

What should I be putting in sources.list to make it work???[/QUOTE]

Yeah, I had the exact same problem. Can someone please help?

---

### Post by stimpson on 2005-11-10
i've had the same problem as ryan76, a quick workaround:
```

#!/bin/bash
sudo dpkg-scanpackages repo /dev/null | gzip -9c > repo/Packages.gz
sudo dpkg-scansources repo /dev/null | gzip -9c > repo/Sources.gz

```
and execute 'autorepo' from /home instead of /home/repo

doesn't seem to be a nice solution though :razz:

---

### Post by lreyes6 on 2005-11-14
Great guide... just great... 

but... 

jejeje there's allways a but 

i'm kind of new for linux... what should i do if i want to make this on a dvd? so i dont duplicate space on my home computer? (with the deb file and intalling the file) 

like a mobil repository!

thanks!

---

### Post by peanut butter on 2005-11-19
Hello, anyone know how i could download package deb files from the web using apt?

---

### Post by kkass on 2005-11-30
This is an excellent howto.  The checkinstall tip makes it even better.  I have my own remote repository working, but when I run 'apt-get install <some package>' I get the following warning:
```

WARNING: The following packages cannot be authenticated!

```
How do I add information to authenticate them?

---

### Post by artAlexion on 2005-12-05
I got the following message in response to autorepo

```
 ** Packages in archive but missing from override file: **
  amarok amarok-arts amarok-gstreamer amarok-xine nerolinux tellico

 Wrote 6 entries to output Packages file.
Prototype mismatch: sub main::getopt: none vs (@) at /usr/bin/dpkg-scansources line 116.
```

synaptic seems to choke on the Packages file created

```
apt-get update 
``` returns

```
Ign file: deb/ Release.gpg
Ign file: deb/ Release
Ign file: deb/ Package
```

but seems to want to use the packages contained there.

Any ideas?

---

### Post by sabitha on 2005-12-21
client@client-01:~$ sudo apt-get update
Err [http://10.0.0.1](http://10.0.0.1) local_repository/ Release.gpg
  Could not connect to 10.0.0.1:80 (10.0.0.1). - connect (111 Connection refused)
Ign [http://10.0.0.1](http://10.0.0.1) local_repository/ Release
Ign [http://10.0.0.1](http://10.0.0.1) local_repository/ Packages
Err [http://10.0.0.1](http://10.0.0.1) local_repository/ Packages
  Could not connect to 10.0.0.1:80 (10.0.0.1). - connect (111 Connection refused)

---

### Post by magomago on 2006-06-03
just wondering if still works for dapper!

---

### Post by Toky on 2006-06-11
I'm about to find out... will let you know...

---

### Post by oneyoudontknow on 2006-06-16
Step One
Most systems come with the following files but just ot be safe run these
```

sudo apt-get install apt-utils
sudo apt-get install dpkg-dev

```
If you havent created your repo directory do it now (i made mine in /var/www because i use apache)
```

mkdir /home/your repo dir/

```


I am not able to folow your command line as I do not get access to create any directory. 
EDIT: Not the one mentioned in the command line mentioned above
I am sorry for this question as I am using (X)Ubuntu for the first time.

---

### Post by lreyes6 on 2006-06-16
[quote=artAlexion]I got the following message in response to autorepo

```
 ** Packages in archive but missing from override file: **
  amarok amarok-arts amarok-gstreamer amarok-xine nerolinux tellico

 Wrote 6 entries to output Packages file.
Prototype mismatch: sub main::getopt: none vs (@) at /usr/bin/dpkg-scansources line 116.
``` 
synaptic seems to choke on the Packages file created

```
apt-get update 
``` returns

```
Ign file: deb/ Release.gpg
Ign file: deb/ Release
Ign file: deb/ Package
``` 
but seems to want to use the packages contained there.

Any ideas?[/quote]

I'm having the same problem but the repository works fine... i guess is because a lack of gpg keys...

---

### Post by killernurd on 2006-06-28
apt-get (and thus Synaptic) are looking for the GPG key you used to sign the package, so they can authenticate the packages against the key. If you don't provide a key, they'll complain that the packages can't be authenticated. If you didn't sign the packages to begin with, apt-get will *still* complain about it, but the simple method is to just use gpg to sign your packages and then put the gpg key in Releases.gpg

At least, it's worked that way so far... I'm still in the process of creating a complex repo of my own, and that's what I've done to get apt-get to stop complaining.

---

### Post by penguinfan on 2006-07-13
Excellent howto, BUT (and this is a big BUT)

I have quite a few duplicate debs (older and newer versions). Thus when i do a 'autorepo' , i get the following error.

[INDENT][B] ! Package linux-386 (filename ./linux-386_2.6.15.24_i386.deb) is repeat but newer version;
   used that one and ignored data from ./linux-386_2.6.15.23_i386.deb !
[/B][/INDENT]

Is there a way to remove old debs and just keep the latest??

Thanx a lot

---

### Post by jamadagni on 2006-09-14
> **penguinfan said:**
> Is there a way to remove old debs and just keep the latest??
I had to do manual delete. I don't think there's any other way.

---

### Post by louis_nichols on 2006-09-20
for the record... I just used the howto and made a local repo under /home/myself/repo.

I used the autorepo script in the original post and initially ran into the error ```
File not found
Failed to fetch file:///home/myself/./cli-common_0.4.3ubuntu1_all.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I solved it easily by modifying the entry in sources.list to:

deb file:///home/myself/repo/ ./

maybe someone will need this.

I now run dapper, with part of edgy in it (I'm building some packages from the edgy src debs, which is actually the reason I setup a local repo)

---

### Post by ihavenoname on 2006-11-12
Excellent I'll be trying this soon.

---

### Post by brkamikaze on 2006-11-20
Is it possible to modify the alternate CD repository to include a few langpacks so I need to use only 1 CD and forget networking to install Ubuntu?

---

### Post by h.mehdi on 2006-12-31
Hi,

I have an error like this:
some packages can't be fetched!

```
mehdi@edgy:~$ sudo apt-get install ntfs-3g bind9 clamav clamtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav-base clamav-freshclam fuse-utils libbit-vector-perl libcarp-clan-perl
  libclamav1 libdate-calc-perl libfile-find-rule-perl libfuse2 libgmp3c2
  libntfs-3g0 libnumber-compare-perl libtext-glob-perl
Suggested packages:
  bind9-doc lha clamav-docs cabextract
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  bind9 clamav clamav-base clamav-freshclam clamtk fuse-utils
  libbit-vector-perl libcarp-clan-perl libclamav1 libdate-calc-perl
  libfile-find-rule-perl libfuse2 libgmp3c2 libntfs-3g0 libnumber-compare-perl
  libtext-glob-perl ntfs-3g
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 7869kB of archives.
After unpacking 11.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  bind9 libgmp3c2 libclamav1 clamav-base clamav-freshclam clamav
  libtext-glob-perl libnumber-compare-perl libfile-find-rule-perl
  libcarp-clan-perl libbit-vector-perl libdate-calc-perl clamtk fuse-utils
  libfuse2 libntfs-3g0 ntfs-3g
Install these packages without verification [y/N]? y
Err http://192.168.23.1 ./ bind9 1:9.3.2-2ubuntu3
  404 Not Found
Err http://192.168.23.1 ./ libgmp3c2 2:4.2.1+dfsg-3
  404 Not Found
Get:1 http://192.168.23.1 ./ libclamav1 0.88.4-1ubuntu2 [271kB]
Get:2 http://192.168.23.1 ./ clamav-base 0.88.4-1ubuntu2 [175kB]
Get:3 http://192.168.23.1 ./ clamav-freshclam 0.88.4-1ubuntu2 [5911kB]
Get:4 http://192.168.23.1 ./ clamav 0.88.4-1ubuntu2 [67.4kB]
Get:5 http://192.168.23.1 ./ libtext-glob-perl 0.06-3 [7938B]
Get:6 http://192.168.23.1 ./ libnumber-compare-perl 0.01-3 [6068B]
Get:7 http://192.168.23.1 ./ libfile-find-rule-perl 0.30-1 [29.9kB]
Get:8 http://192.168.23.1 ./ libcarp-clan-perl 5.3-4 [10.5kB]
Get:9 http://192.168.23.1 ./ libbit-vector-perl 6.4-4 [145kB]
Get:10 http://192.168.23.1 ./ libdate-calc-perl 5.4-4 [249kB]
Get:11 http://192.168.23.1 ./ clamtk 2.24-0ubuntu1 [37.0kB]
Get:12 http://192.168.23.1 ./ fuse-utils 2.5.3-2.1ubuntu4 [56.6kB]
Get:13 http://192.168.23.1 ./ libfuse2 2.5.3-2.1ubuntu4 [50.9kB]
Get:14 http://192.168.23.1 ./ libntfs-3g0 20060920-0ubuntu2 [88.8kB]
Get:15 http://192.168.23.1 ./ ntfs-3g 20060920-0ubuntu2 [31.3kB]
Fetched 7137kB in 1s (4762kB/s)
Failed to fetch http://192.168.23.1/archives/./bind9_1%3a9.3.2-2ubuntu3_i386.deb  404 Not Found
Failed to fetch http://192.168.23.1/archives/./libgmp3c2_2%3a4.2.1+dfsg-3_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mehdi@edgy:~$ 
```

---

### Post by kkass on 2007-01-02
Check your web server and verify that 'http://192.168.23.1/archives/./bind9_1%3a9.3.2-2ubuntu3_i386.deb' is the correct location for your file.

---

### Post by h.mehdi on 2007-01-03
> **kkass said:**
> Check your web server and verify that 'http://192.168.23.1/archives/./bind9_1%3a9.3.2-2ubuntu3_i386.deb' is the correct location for your file.
Yep! I can download these packages with my browser without any problem, just don't know why apt can't fetch them :(

---

### Post by ihavenoname on 2007-01-21
> **spacemonkey said:**
> Is there anyway to automatically add to the repo all the .deb's you've got installed on your system?  To create a sortof quick system restore?
Well. assuming you didn't delete anything from /var/cache/apt/archives or run apt-get clean/autoclean you could pull all the debs in /var/cache/apt/archive into a folder and follow the steps above. Check the wiki for a way to make your own custom repo cd.

---

### Post by rai4shu2 on 2007-05-01
I think it should be pointed out that unless you authenticate a custom CD/DVD of your own making, apt will still prefer the repos to your discs. There is a way around this, of course:

```
sudo apt-get --allow-unauthenticated install package
```

Or if you prefer Synaptic, you can use the following:

```
gksudo "synaptic -o APT::Get::AllowUnauthenticated=true"
```

---

### Post by rraj.be on 2008-05-22
When i executes the steps i got the below

```
root@raj-dworkstation:~# mkdir /home/rajrepo/    
mkdir: cannot create directory `/home/rajrepo/': File exists
root@raj-dworkstation:~# cd /bin/
root@raj-dworkstation:/bin# sudo nano autorepo
root@raj-dworkstation:/bin# sudo chmod +x autorepo
root@raj-dworkstation:/bin# cd /home/rajrepo/
root@raj-dworkstation:/home/rajrepo# autorepo
 Wrote 0 entries to output Packages file.
root@raj-dworkstation:/home/rajrepo# 

```

please some one tell me why there was no package added tio my repositry

---

### Post by rholt on 2008-05-22
> **cdk said:**
> ...if you could some how output the list of packages installed on your system and then mirror them to your repo it might work. any one else have some ideas?

"Quoted from [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

Posted by Vivek on Tuesday August 22, 06 @6:48 pm

Hardware and Software failures are part of Life. That is why you need to have a backup. I have already written about backing files and MySQL databases. You need not to backup all installed binaries (mostly software) with following tips. It will not just save your time but both Debian and RHEL distro can update them instantly.

In order to reinstall or restore your installed software you need to have a list of all installed software.
Task: Backup list of installed software

Debian Linux
If you are using Debian Linux use dpkg command to list installed software:
$ dpkg --get-selections

Store list of installed software to a file called /backup/installed-software.log
$ dpkg --get-selections > /backup/installed-software.log

RPM based distributions (RHEL, Fedora Core, Cent OS, Suse Linux etc) 
...


Debian Linux
Debian Linux makes your life easy. All you have to do is type following two commands:
# dpkg --set-selections < /backup/installed-software.log
Now your list is imported use dselect or other tools to install the package.
# dselect

Select 'i' for install the software.

RPM based distro
As far as I know RPM based distro does not offer ...."

---

### Post by mc4man on 2009-07-12
With some slight adjustments to post 1 worked perfectly in hardy to set up a local repo. Makes using and maintaining a custom, multimedia upgraded hardy and sharing the builds with some friends much, much easier.

Method in case anyone wants likewise

Install dpkg-dev first

```
sudo apt-get install dpkg-dev
```


Decided to keep simple with local repo in $HOME named repo

```
mkdir repo
```

```
cd /bin
```

```
gksudo gedit autorepo
```

entered this script instead (from post 16
```
#!/bin/bash
sudo dpkg-scanpackages repo /dev/null | gzip -9c > repo/Packages.gz
sudo dpkg-scansources repo /dev/null | gzip -9c > repo/Sources.gz
```

save and close gedit
from bin prompt
```
sudo chmod +x autorepo
```

```
gksudo gedit /etc/apt/sources.list
```

add at bottom

```
##My Repo
deb file:///home/[COLOR="Blue"]doug[/COLOR] repo/
```

save and close

Then add package(s) to repo folder in home dir. and run from a normal prompt, (home dir.


```
 autorepo
```

Then to update 
```
sudo apt-get update

```
If adding packages to repo then just repeat 
```
autorepo && sudo apt-get update
```

works perfectly Ex.

> 
doug@doug-laptop:~$ autorepo && sudo apt-get update
 ** Packages in archive but missing from override file: ** [COLOR="Blue"]<- don't get, but no ill effect[/COLOR]
  audacity audacity-data audacity-dbg boo command-not-found command-
  not-found-data debhelper dvdwizard ffmpeg ffprobe gnome-panel gpac
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-doc
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-
  multiverse-dbg intltool lame libasound2 libasound2-dev libasound2-
  plugins libass-dev libass1 libavcodec-dev libavcodec52 libavdevice-
  dev libavdevice52 libavfilter-dev libavfilter0 libavformat-dev
  libavformat52 libavutil-dev libavutil50 libboo2.0-cil libcaca-dev
  libcaca0 libcucul-dev libcucul0 libdc1394-13 libdc1394-22 libdca-dev
  libdca0 libdirac-dev libdirac0 libdvbpsi5 libdvbpsi5-dev libdvdcss2
  libdvdnav-dev libdvdnav4 libdvdread-dev libdvdread4 libfaac-dev
  libfaac0 libfaad0 libgpac-dev libgpac0.4.5 libgsm1 libid3tag0
  libmad0 libmad0-dev libmcs-dev libmcs1 libmodplug-dev libmodplug0c2
  libmp3lame-dev libmp3lame0 libmpeg2-4 libmtp-dev libmtp8
  libopencore-amrnb-dev libopencore-amrnb0 libopencore-amrnb0-dbg
  libopencore-amrwb-dev libopencore-amrwb0 libopencore-amrwb0-dbg
  libopenjpeg-dev libopenjpeg2 libpostproc-dev libpostproc51
  libsamplerate0 libsamplerate0-dev libschroedinger-1.0-0
  libschroedinger-dev libshout3 libshout3-dev libsidplay1 libsndfile1
  libsndfile1-dev libsoundtouch1-dev libsoundtouch1c2 libspeex-dev
  libspeex1 libsqlite3-0 libswscale-dev libswscale0 libtag1-dev
  libtag1c2a libtaglib2.0-cil libtool libv4l-0 libv4l-dev libva-dev
  libva1 libva1-dbg libvlc2 libvlccore2 libx264-59 libx264-67 libx264-
  68 libx264-dev libxcb-keysyms0 libxcb-keysyms0-dev libxine-dev
  libxine1 libxine1-bin libxine1-console libxine1-dbg libxine1-doc
  libxine1-ffmpeg libxine1-gnome libxine1-misc-plugins libxine1-
  plugins libxine1-x libxvidcore4 libxvmc1 mencoder mplayer mplayer-
  doc nvidia-180-libvdpau nvidia-180-libvdpau-dev ogmtools quilt
  rubyripper samplerate-programs soundstretch sqlite3 transcode
  transcode-doc transcode-utils vdpau-video vdpau-video-dbg vlc vlc-
  data vlc-nox vorbis-tools w32codecs yasm

 Wrote 151 entries to output Packages file.

Ign file: repo/ Release.gpg
Ign file: repo/ Translation-en_US                                            
Ign file: repo/ Release                                                      
Ign file: repo/ Packages                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Reading package lists... Done


---

### Post by dinxter on 2009-09-30
there is fun to be had with reprepro if you want to mirror a repository (or partial) , have your own deb packages you want to throw in, etc

---

### Post by VMC on 2011-03-02
> **mc4man said:**
> With some slight adjustments to post 1 worked perfectly in hardy to set up a local repo. Makes using and maintaining a custom, multimedia upgraded hardy and sharing the builds with some friends much, much easier.

Method in case anyone wants likewise

Install dpkg-dev first

```
sudo apt-get install dpkg-dev
```
Decided to keep simple with local repo in $HOME named repo

```
mkdir repo
``````
cd /bin
``````
gksudo gedit autorepo
```entered this script instead (from post 16
```
#!/bin/bash
sudo dpkg-scanpackages repo /dev/null | gzip -9c > repo/Packages.gz
sudo dpkg-scansources repo /dev/null | gzip -9c > repo/Sources.gz
```save and close gedit
from bin prompt
```
sudo chmod +x autorepo
``````
gksudo gedit /etc/apt/sources.list
```add at bottom

```
##My Repo
deb file:///home/[COLOR=Blue]doug[/COLOR] repo/
```save and close

Then add package(s) to repo folder in home dir. and run from a normal prompt, (home dir.


```
 autorepo
```Then to update 
```
sudo apt-get update

```If adding packages to repo then just repeat 
```
autorepo && sudo apt-get update
```works perfectly Ex.


I noticed you got the same result as I did, but mine never install my repo's:

```
$ sudo apt-get update
Ign file: repo/ InRelease
Ign file: repo/ Release.gpg                                                  
Ign file: repo/ Release                                                      
Ign file: repo/ Translation-en_US                                                                                                  
Ign file: repo/ Translation-en  
```

Everything gets updated but my repo file is always ignored?!

This error has come up before without a solid fix.

---

### Post by mc4man on 2011-03-03
> Everything gets updated but my repo file is always ignored?!
That's quite normal, shouldn't matter at all.

While I don't have quite the need anymore for a local repo (heyday was hardy where I had around 170 packages to get hardy current multimedia wise) still do use a bit, just set up as above on natty.

If the packages you have in there are available in synaptic then you should be good.

Small notes - 
checkinstall packages are generally not useful in this type of repo

If you don't set up authentication for the repo then software center and update manager will not install from, though the packages will show up.
I don't bother, find it much easier to rebuild aptdaemon to allow installing from unauthenicated sources then set it up.

See screen - shows a custom abcde package i made, visible in SC, and if I desired could be installed from because I redid aptdaemon.

All you need to be concerned is whether the packages show up when running 'autorepo'

There is another howto around for a more extensive set up of a local repo, I find this way fine for my uses.

Natty note - 

The new aptdaemon in natty runs a lintian ck. on .debs and will refuse to install on any errors and some previous warning's. This can  be as simple as .debs that install to /usr/local or /opt, quite the bs.

This does not affect synaptic or dpkg

EX. of what's in repo here on maverick (haven't used in a while
> doug@doug-alienware:~/repo$ ls
abcde-nero_2.4.2-2_all.deb                               
cdda2wav_3.00-0ubuntu1_i386.deb                          
cdrecord_3.00-0ubuntu1_i386.deb                                        ffmpeg_0.6-2ubuntu8_i386.deb                             
ffmpeg-dbg_0.6-2ubuntu8_i386.deb                         
ffmpeg-doc_0.6-2ubuntu8_all.deb                                  
gir1.0-nautilus-2.0_2.32.0-0ubuntu6+nmu2_i386.deb        
libavcodec-dev_0.6-2ubuntu8_i386.deb                     
libavcodec-extra-52_0.6-2ubuntu8_i386.deb                
libavcore-dev_0.6-2ubuntu8_i386.deb                      
libavcore-extra-0_0.6-2ubuntu8_i386.deb                  
libavdevice-dev_0.6-2ubuntu8_i386.deb                    
libavdevice-extra-52_0.6-2ubuntu8_i386.deb              
libavfilter-dev_0.6-2ubuntu8_i386.deb                    
libavfilter-extra-1_0.6-2ubuntu8_i386.deb                
libavformat-dev_0.6-2ubuntu8_i386.deb                   
libavformat-extra-52_0.6-2ubuntu8_i386.deb               
libavutil-dev_0.6-2ubuntu8_i386.deb                      
libavutil-extra-50_0.6-2ubuntu8_i386.deb                 
libdvdcss2_1.2.10-0.3medibuntu1_i386.deb                 
libdvdcss-dev_1.2.10-0.3medibuntu1_i386.deb              
libfaac0_1.28-0.3_i386.deb                               
libfaac-dev_1.28-0.3_i386.deb                           
libmediainfo0_0.7.30-1~ppa1~lucid1_i386.deb              
libmpcdec3_1.2.2-2.1ubuntu1_i386.deb                     
libnautilus-extension1_2.32.0-0ubuntu6+nmu2_i386.deb     
libnautilus-extension-dev_2.32.0-0ubuntu6+nmu2_i386.deb  
libpostproc-dev_0.6-2ubuntu8_i386.deb
libpostproc-extra-51_0.6-2ubuntu8_i386.deb
libswscale-dev_0.6-2ubuntu8_i386.deb
libswscale-extra-0_0.6-2ubuntu8_i386.deb
libtotem-plparser12_2.28.1-1_i386.deb
libx264-104_0.104.1698+gitc41b8f0-1_i386.deb
libx264-dev_0.104.1698+gitc41b8f0-1_i386.deb
libxine1_1.1.19-2ubuntu2_i386.deb
libxine1-bin_1.1.19-2ubuntu2_i386.deb
libxine1-console_1.1.19-2ubuntu2_i386.deb
libxine1-ffmpeg_1.1.19-2ubuntu2_i386.deb
libxine1-misc-plugins_1.1.19-2ubuntu2_i386.deb
libxine1-x_1.1.19-2ubuntu2_i386.deb
libxine-dev_1.1.19-2ubuntu2_i386.deb
libzen0_0.4.12-1~ppa1~lucid1_i386.deb
mediainfo_0.7.30-1~ppa1~lucid1_i386.deb
mediainfo-gui_0.7.30-1~ppa1~lucid1_i386.deb
mkisofs_3.00-0ubuntu1_i386.deb
nautilus_2.32.0-0ubuntu6+nmu2_i386.deb
nautilus-data_2.32.0-0ubuntu6+nmu2_all.deb
nautilus-dbg_2.32.0-0ubuntu6+nmu2_i386.deb
nvidia-current_260.19.29-0ubuntu1_i386.deb
nvidia-settings_260.19.21-0ubuntu3_i386.deb
Packages.gz
pana_1.4.16-2_i386.deb
pana-common_1.4.16-2_all.deb
pana-engine-xine_1.4.16-2_i386.deb
pana-engine-yauap_1.4.16-2_i386.deb
Sources.gz
w32codecs_20100303-0.0medibuntu1+nmu1_i386.deb


---

### Post by VMC on 2011-03-03
@mc4man, Thanks for the reply.

Here's what I'm trying to do. Instead of downloading nvidia-currrent on each daily-live ISO after installation. I wanted to use the custom repo and have just those few files and then update right after I install the natt ISO.

Here's what's inside ~/home/vmc/repo:

[COLOR="Red"][B]dkms_2.1.1.2-5ubuntu1_all.deb
nvidia-current_270.29-0ubuntu3_amd64.deb
nvidia-settings_270.29-0ubuntu1_amd64.deb
Packages.gz
screen-resolution-extra_0.14build1_all.deb
Sources.gz[/B][/COLOR]

I tried even modifying the **sources.list** to just include my file, like so:

```
##My Repo
deb file:///home/vmc repo/
```

sudo apt-get update or even sudo apt-get install *deb all failed to install the nvidia-comman files.

I'm missing some key ingredient here. 

[I made a backup of the orginal sources.list file]

---

### Post by mc4man on 2011-03-03
> all failed to install the nvidia-comman files.

I actually find a local repo quite useful for re-installs in addition to providing packages not available in ubuntu repos and or ppa's.

In this case there would be no reason for nvidia-common to be installed - none of the packages you've listed have it as a depend
It's a depend of ubuntu-desktop, and a recommend of jockey-common so it should already be installed
(and relatively unneeded anyway

 - keep in mind that in many cases if package 12345.deb is in both a local repo (as done here) and in an enabled ubuntu repo that the ubuntu repo package will be considered a 'higher' version

In this particular case I may just either use gdebi on the saved nvidia-current or stick them all in a folder and do a dpkg -i *.deb

---

### Post by VMC on 2011-03-03
> **mc4man said:**
> I actually find a local repo quite useful for re-installs in addition to providing packages not available in ubuntu repos and or ppa's.

In this case there would be no reason for nvidia-common to be installed - none of the packages you've listed have it as a depend
It's a depend of ubuntu-desktop, and a recommend of jockey-common so it should already be installed
(and relatively unneeded anyway

 - keep in mind that in many cases if package 12345.deb is in both a local repo (as done here) and in an enabled ubuntu repo that the ubuntu repo package will be considered a 'higher' version

In this particular case I may just either use gdebi on the saved nvidia-current or stick them all in a folder and do a dpkg -i *.deb

I think with natty I have to install gdebi in order for that to work. Regarding the nvidia-current. Its almost 50megs and I'm trying to avoid downloading it each and every time I re-install a new ISO. that's the whole reason to learn this process.

I don't think I tried the *dpkg -i* route yet. I'll try that and let you know. Thanks!

---

### Post by mc4man on 2011-03-03
> I don't think I tried the dpkg -i route yet. I'll try that ..
When gdebi is used on a single .deb (or Software center when it works), then any additional dep package will be installed as needed as long as they're available 

When you use dpkg -i then any dep packages must either be already installed or in the group you're running dpkg on 
Otherwise you'll get 'broken package(s)', usually not a big deal, synaptic will fix (though in this case better to have things go right the first time

---

### Post by VMC on 2011-03-03
Thanks for your help. It worked! I now remember using *dpkg -i *in the distant past, on OpenOffice, but for some reason got confused and tried installing debi installer, and using that instead, and forgot trying with dpkg. Got sidetracked and tried alternative method of using local repo.

```
$ sudo dpkg -i *deb
[sudo] password for vmc: 
Selecting previously deselected package dkms.
(Reading database ... 121328 files and directories currently installed.)
Unpacking dkms (from dkms_2.1.1.2-5ubuntu1_all.deb) ...
Selecting previously deselected package nvidia-current.
Unpacking nvidia-current (from nvidia-current_270.29-0ubuntu3_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from nvidia-settings_270.29-0ubuntu1_amd64.deb) ...
Selecting previously deselected package screen-resolution-extra.
Unpacking screen-resolution-extra (from screen-resolution-extra_0.14build1_all.deb) ...
Setting up dkms (2.1.1.2-5ubuntu1) ...
Setting up screen-resolution-extra (0.14build1) ...
Processing triggers for man-db ...
Setting up nvidia-current (270.29-0ubuntu3) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-270.29 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-5-generic
Building for architecture x86_64
Building initial module for 2.6.38-5-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-5-generic/updates/dkms/

depmod......

DKMS: install Completed.
Processing triggers for python-central ...
Setting up nvidia-settings (270.29-0ubuntu1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-5-generic
Processing triggers for python-support ...
v
```

---

