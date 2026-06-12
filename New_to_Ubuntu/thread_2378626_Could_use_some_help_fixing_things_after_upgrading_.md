---
title: "Could use some help fixing things after upgrading ubuntu from 14.04 to 16.04, please."
date: 2017-11-25
forum: New to Ubuntu
---

### Post by greyfaux01 on 2017-11-25
*feel free to skip to tldr*
I've been a linux user since hardy, pretty much exclusively, and ive always managed to fix my own problems (with the communities  help of course, thanks so much guys for your unending generosity). Now back when i had 12.04, i upgraded to 14.04, and i had to do a bunch of stuff to get my system back to normal, for example depency issues, getting my compiz cube working again (i know, i cant let it go on my htpc), broken programs/packages, set up dual boot, fixed grub, edited grub, restored from a redobackup image (and fixed grub again), etc etc. Just recently a regular 'partial upgrade' had what appeared to be 'broke' my root partition, gparted said it was an unsupported filesystem, couldn't login, only in the boot recovery screen. I tried the great tool disc-repair, and that didnt magically fix it like it has in the past. I even asked for help from the dev of boot-repair, and he instructed to just reinstall root. Now why that would have been the sane, and quicker option, i didnt want to 'give up', not to mention i having to reinstall all my programs, who knows what settings would be broke, etc, so i pushed on, and eventually started to think i had a bad superblock. I found some random blog (seemed legit), followed the instructions, and low and behold, im using that system now to type this.

I also hate reinstalling because i would rather fix the problem, in the past i would spend weeks researching, fixing/rebreaking stuff, just to get my system fixed 'how i wanted it', opposed to admitting defeat, and reinstalling.
 Even after all this xp, I still consider myself kind of a linux noob. If theres a gui tool, i try to use it instead, because i feel like i 'understand it' more, even though i know i dont, because i understand so little in the terminal i guess. Not to mention, im always trying to find friends that would be a good candidate to try linux, and i always ask 'what if a linux noob had this problem, how would they fix it?'. So i spend hours researching different ways to fix grub, even though its fairly straight forward, i opted to use boot-repair, so then i can point out that its now different than using a windows repair tool. So using redobackup to reflash my HDD, and boot-repair to get it to boot, was a 'win' in my book (yes i know dd does the same thing).

Anyway, sorry for the long intro, but now i dont have as much time as i used to, i barely have any free time at all. I upgraded just yesterday to 16.04, did an in place upgrade from 14.04, and some packages are broken (and probably depency issues, at first i got my old nemisis 'cant update, tex-common error' but i think that went away by itself). So im here in teh forums wondering if someone could help my specific use-case out, because i just dont have time to search for every individual problem thats 'broken', read about 10 different ways to fix it, and then start trying. If i knew more about the internals of linux, i would be able to know which solution is best, but i always try to opt for the solutions that change as little as possible, the least 'powerful' solutions. I definately am not looking for overkill, but if thats whats needed, so be it.

*tldr*
My only specific problems now after upgrading from 14.04 to 16.04 are, my megasync seems broken, its not running in system monitor, and im running inside xfce and theres no icon for it. Another thing on the no icon issue, pre-upgrade, i still didnt have a mega icon, plus a few more, what i did to get it to work, was kill the process 'indicator-application-service', and then like magic, all my icons appeared. Because of the number of 'indicators' that i think are out there, it confuses me as to what is actually happening, and i have no idea what 'indicator-application-service' is, but killing it got my mega icon to be there. Maybe ive just never had anyone explain in a way thats easy to understand, i dont have time to read every man page on every indicator service, and even if i did, they dont say how they connect with every other indicator in every other Desktop Environment. Anyway, now when i go (into system monitor gui) to kill it, not only is mega not in system-monitor, neither is indicatorAppService. Im running ubuntu, and i prefer to be inside xfce on this particular desktop. If i have to change i will. I also use synapse, and when i type in 'mega' nothing appears, and its not in my 'start' menu either, it used to be under the internet catagory.

Also, relating to the xfce panel still, there were a few other icons, cant rember what they were, but their not there, but what i DO know, is i have the little 'resource indicator' boxes, and their all glitchy/grey/flashing black/white. These resource monitors were another thing that popped up when i killled the now non existent 'indicator-application-service'. So those boxes are there now, their just all glitched up.

Im also missing Kodi. I noticed in my 'updates' area, the repos, that it looks like i got some new kodi repos (maybe they were there the whole time), but theres 2 sets, one that is no checked, and some others, 'teamxbmc' that are checked, the checked ones say 'xenial' next to it. I went to the URL of the non-checked repos, and the website only provided packages up to ubuntu 15.x, so i guess the ones that are not checked are not avaiable for 16.04, and im assuming i was indeed using them prior to upgrading. Whats strange though, is the entire kodi program is gone, or broken. And if im using the xenial repos, i wonder why kodi didnt upgade by itself. Hoping no deeper issue here.

Now my first instinct was to just purge/reinstall these 2 missing packages (mega, kodi), but i didnt want to start breaking things worse, especially with repos, before getting professional help. I would rather not reinstall even these pacakges, but then again maybe thats what im supposed to do, since i had old packages that are not supported. Im just confused why kodi/mega did not get upgraded automagically with the rest of the system. Because of my confusion, im hesitant to start changing stuff without knowing why.

Any help is greatly appreciated. I actually have to sign off now, and only have a little bit of time each day to check, sometimes no time, but this is a problem i definately need to fix, its my daily driver desktop here, so if i dont respond for a day or 3, i will be back. In fact if i can manage some freetime, like a few hours, it would be great if i could chat/irc with someone, then we can just troubleshoot/fix fairly quickly in 1 shot. If thats asking too much i apologize. Thanks again for everyones ongoing help here.

---

### Post by DuckHook on 2017-11-25
Welcome to the forums, greyfaux01.

A friendly word of advice: you will have a better chance of attracting help if you break your post down to multiple posts: one thread per problem, and then post them in the appropriate subforum. Forum experts tend to specialize in their own area of expertise. Keep the problem description to the point while remaining complete, and with supporting data output wrapped in [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Good luck and Happy Ubuntuing!

---

### Post by greyfaux01 on 2017-11-25
Hey thanks for the advice, i'll do that.

I have a few questions thought if you dont mind. So im assuming the broken packages will be in a 'packages' section? or is there a particular section for that? Or what area would be best for that? broken packages after upgrade? also, if its intertwined with depency issues, would this be a seperate area, or is there a 'package/dependency' area?

As far as the xfce panel problem, i think i seen the xfce/xubuntu area, so i'll post that there.

And i am indeed having some tex-common, tex-live problems, where would you say i should post this? Nothing seems to be outright broken (that i can tell), but when i installed xscreensaver lastnight i get the error, but when i do apt-get update, i get no error. So im not sure where this type of error would go.

Thanks so much for your help.

And also for the record, i was hesitant so post in any 'specialized' area since the faq said 'when in doubt post in noobs', so honestly, because im not super proficient at using the terminal, but i can follow instructions, i still dont know exactly where to post. I see there are the 'general flavor' areas, but also the 'specialized' areas. The number of subforums is honestly overwhelming, so any guidance with my particular issues would be much appreciated.

Edit: or should i just post all these problems under 'general help?' Looking at all the sections, it seems all my problems could go in possibly 2 sections, for example, my package/depency kodi i think is broken, but im assuming 'general help' would still be better opposed to 'multimedia software'. With my xfce panel, im not sure if i should post under DE's, or general, since its not a problem getting the DE up and running, its just a minor tweak, that imo can happen across all DE's (after upgrade, minor gui compononts and other 'indicators' break).

With tex-common, i still have no idea, so im thinking to just default to 'general' there too..?.. If any of my assumptions are wrong here please let me know.. im going to try to wait for your response before posting these under general. I guess my only real question, is my kodi/mega problem considered the same problem, since indeed their broken packages, both happening after upgrade? I would hate to 'waste' a new thread on every tiny issue if they can be fixed by 1 person with just some basic, general knowledge, which i feel like my problems are noobish enough, they can be. Im tempted to just post all my 'minor' problems in 1 thread under general, since i believe all are very basic problems that almost any of the pros here can fix.

Again im making assumptions so please tell me if im off base, or if it is ok to post everything under general, since its all pretty basic stuff.. Thanks again for your help..

---

### Post by wildmanne39 on 2017-11-25
You can keep it simple, you are new just post them in the new to ubuntu section.

Thanks

---

### Post by #&amp;thj^% on 2017-11-25
Your making it hard on yourself>>>It's all good.:D
Lets see if we can get the ball rolling with the below code;
To get the list of partially installed packages (with architecture information) preceded by their states, with one line, run

```
dpkg-query -W -f='${db:Status-Abbrev} ${binary:Package}\n' | grep -E ^.[^nci]
```
Paste back the code  from the Terminal please>>>In Code Tags, to help myself or others read it better.

See "man dpkg-query" for information about the states etc. (for later reding)

---

### Post by greyfaux01 on 2017-11-25
Hey thanks a lot guys. Yea my bad for making stuff complicated. It’s s what i do:) On my way to work but I will do it later tonight.  Now I didn’t run autoremove yet so there will be tons of crap that I don’t need, but I didn’t want to run it in case i needed th old kodi/mega packages. I also saved the error output from when I installed (successfully) xscreensaver. So unless you tell me not to I’ll post that too (tex-common errors). And yes I read the faq about ```
 xxx 
``` before my first post;) ... I’ve been annoyed enough over the years when other ppl do it. That said when I’m typing a wall of text I guess I’m no better;). 

If I don’t get back tonight it’s cuz I worked too late,  but I will get back at some point. Thanks again everyone.

ok 1fallen, heres the output of the dpkg-query of yours.

While at work i did read the man page you suggested, im not gonna lie and say i understood it all, but i get (some of) the gist, i think. i get its querying the package database, and will give errors and info, and the query can be amended to ones liking.. it appears the output is showing tex-common is half configured, by the capital F, and from what i understand, the capital U's are still an error because their capitalized, but it means their unpacked.. not sure why thats an error, unless it means their unpacked, but not installed.. at any rate, i have no idea what im talking about, heres that output..

```

jonny2@jonny2-OptiPlex-745:~$ dpkg-query -W -f='${db:Status-Abbrev} ${binary:Package}\n' | grep -E ^.[^nci]iU  prosper
iF  tex-common
iU  texlive-extra-utils
iU  texlive-font-utils
iU  texlive-generic-recommended
iU  texlive-latex-base
iU  texlive-latex-base-doc
iU  texlive-latex-recommended
iU  texlive-latex-recommended-doc
iU  texlive-luatex
iU  texlive-pictures
iU  texlive-pictures-doc
iU  texlive-pstricks
iU  texlive-pstricks-doc
jonny2@jonny2-OptiPlex-745:~$ 

```



i thought the output from installing xscreensaver (bunch of errors) would help, but now i see now after your very precise command showing the same tex-common errors, my output errors from installing xscreensaver may not be helpful at all.. that said im going to include it anyway, in case there are some clues to other stuff.. i did notice it gave me some 'suggested' and 'recommends', like perl5, although im not sure thats relevant atm. and again sorry for the huge list of packages no longer needed, i didnt want to run autoremove until i know it wont cause more work.. and just for the hell of it i ctrl-f'd the below output and looked for 'mega' and 'kodi' to check for errors, of course nothing there.. im sure im getting ahead of myself, really just trying to help in ways that wont break stuff..

```



jonny2@jonny2-OptiPlex-745:~$ sudo apt-get install xscreensaver
[sudo] password for jonny2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  aptitude-common checkbox-ng comerr-dev g++-4.8 gcc-4.9-base gcj-4.8-jre-lib
  gstreamer1.0-clutter heirloom-mailx icedtea-netx-common java-common
  java-wrappers krb5-multidev libamd2.3.1 libapache-pom-java libapt-inst1.5
  libarchive-extract-perl libart2.0-cil libatk-wrapper-java
  libatk-wrapper-java-jni libavahi-client-dev libavahi-common-dev
  libavdevice53 libavfilter3 libavresample1 libbaloocore4 libbaloofiles4
  libbaloowidgets4 libbalooxapian4 libbasicusageenvironment0 libbcmail-java
  libbcpkix-java libbcprov-java libbind9-90 libbit-vector-perl
  libboost-date-time1.54.0 libboost-filesystem1.54.0 libboost-iostreams1.54.0
  libboost-python1.54.0 libboost-regex1.54.0 libboost-serialization1.54.0
  libboost-thread1.54.0 libc-ares2 libcamd2.3.1 libcamel-1.2-45
  libcarp-clan-perl libccolamd2.8.0 libcdr-0.0-0 libcec-platform1v5
  libcholmod2.1.2 libcmis-0.4-4 libcolamd2.8.0 libcolorhug1
  libcommons-codec-java libcommons-httpclient-java libcommons-logging-java
  libcommons-parent-java libdate-calc-perl libdate-calc-xs-perl libdns100
  libdom4j-java libdvbpsi8 libebackend-1.2-7 libebook-1.2-14
  libebook-contacts-1.2-0 libechonest2.1 libedata-book-1.2-20
  libedataserver-1.2-18 libegl1-mesa-drivers libelfg0 libept1.4.12 libexif-dev
  libexiv2-12 libfreenect0.2 libfstrcmp0 libgcj14 libgcrypt11-dev
  libgcrypt20-dev libgegl-0.2-0 libgif4 libglade2.0-cil libglamor0 libglew1.10
  libglewmx1.10 libgmp-dev libgmpxx4ldbl libgnome-bluetooth11
  libgnome-desktop-2-17 libgnome-desktop-3-7 libgnome2.24-cil libgnuinet-java
  libgnumail-java libgnutls-dev libgnutlsxx27 libgnutlsxx28 libgpac2
  libgpg-error-dev libgphoto2-dev libgphoto2-port10 libgps20
  libgraphicsmagick3 libgroupsock1 libgsoap4 libgssrpc4 libgtkhotkey1 libicu52
  libidn11-dev libieee1284-3-dev libilmbase6 libimobiledevice4 libisc95
  libisccc90 libisccfg90 libisl10 libitext-java libjaxen-java libjdom1-java
  libjgoodies-common-java libjgoodies-looks-java libkadm5clnt-mit9
  libkadm5srv-mit9 libkdb5-8 libkfilemetadata4 libkimap4 libkldap4 libkrb5-dev
  liblinear1 liblivemedia23 libllvm3.4 liblockdev1 liblog-message-perl
  liblog-message-simple-perl liblog4j1.2-java liblwres90 libmagickcore5
  libmagickcore5-extra libmagickwand5 libmbim-glib0 libmikmod2
  libmodule-pluggable-perl libmodule-runtime-perl
  libmono-compilerservices-symbolwriter4.0-cil libmono-system-runtime4.0-cil
  libmono-web4.0-cil libmrm4 libmspub-0.0-0 libmusicbrainz5-0
  libnepomukcleaner4 libnfs1 libobrender29 libopenexr6 libopenvg1-mesa
  liborcus-0.6-0 libp11-kit-dev libparams-classify-perl libpcre32-3
  libpcrecpp0 libplatform1 libpocketsphinx1 libpod-latex-perl libpodofo0.9.0
  libpoppler44 libprocps3 libprotobuf-c0 libprotobuf8 libprotoc8
  libqextserialport1 libqmi-glib0 libqmmp0 libqmmpui0 libqmobipocket1
  libqpdf13 libqt5qml-graphicaleffects libqt5sensors5
  libqt5webkit5-qmlwebkitplugin libqtlocation1 libquazip0 libraw9
  librhythmbox-core8 libsctp1 libsexy2 libshairplay0 libshp1 libsphinxbase1
  libstdc++-4.8-dev libsvga1 libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libtar0 libtasn1-6-dev libtasn1-doc libterm-ui-perl
  libtext-soundex-perl libthumbnailer0 libtinyxml2-0.0.0 libtinyxml2.6.2
  libts-0.0-0 libuil4 libumfpack5.6.2 libunique-1.0-0 libunityvoice1
  libusageenvironment1 libusbmuxd2 libv4l-dev libv4l2rds0
  libva-intel-vaapi-driver libvisio-0.0-0 libwlocate0 libwxbase2.8-0
  libwxgtk-media2.8-0 libwxgtk2.8-0 libxen-4.4 libxerces2-java libxfce4util6
  libxine1 libxine1-misc-plugins libxine1-plugins libxine1-x
  libxml-commons-external-java libxml-commons-resolver1.1-java libxom-java
  libxpp2-java libxpp3-java libxtables10 libzip2 linux-generic
  linux-headers-generic linux-image-generic lksctp-tools lxsession-logout
  lxshortcut nettle-dev python-bluez python-commandnotfound python-support
  python-wxgtk2.8 python3-checkbox qml-module-qtquick-localstorage
  qml-module-ubuntu-ui-extras-browser qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-window-plugin ruby-vte ruby-vte3 shared-desktop-ontologies
  sphinx-voxforge-hmm-en sphinx-voxforge-lm-en syslinux-themes-debian
  syslinux-themes-debian-wheezy texlive-luatex thermald tsconf
  ttf-dejavu-extra unity-scope-audacious unity-scope-clementine
  unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque
  unity-scope-musique unity-voice-service watershed xchat-common xfce4-mixer
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  xfishtank xdaliclock fortune qcam | streamer
Recommended packages:
  perl5
The following NEW packages will be installed:
  xscreensaver
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
14 not fully installed or removed.
Need to get 544 kB of archives.
After this operation, 2,280 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 xscreensaver i386 5.34-2ubuntu1 [544 kB]
Fetched 544 kB in 1min 11s (7,607 B/s) 
Selecting previously unselected package xscreensaver.
(Reading database ... 465087 files and directories currently installed.)
Preparing to unpack .../xscreensaver_5.34-2ubuntu1_i386.deb ...
Unpacking xscreensaver (5.34-2ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up tex-common (6.04) ...
Ignoring /etc/texmf/texmf.d/05TeXMF.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/15Plain.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/45TeXinputs.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/55Fonts.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/65BibTeX.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/75DviPS.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/80DVIPDFMx.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/85Misc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/90TeXDoc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/95NonPath.cnf during generation of texmf.cnf, please remove manually!




Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: Please see /usr/share/doc/tex-common/NEWS.Debian.gz
Warning: found file: /etc/texmf/updmap.d/00updmap.cfg
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-base.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-base.cfg


Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.xjTLuy7s
Please include this file if you report a bug.


Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory


dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.


dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-pictures depends on texlive-latex-recommended (>= 2015); however:
  Package texlive-latex-recommended is not No apport report written because the error message indicates its a followup error from a previous failure.
                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           configured yet.


dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-pictures (>= 2015); however:
  Package texlive-pictures is not configured yet.
 texlive-pstricks depends on texlive-generic-recommended (>= 2015); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent conNo apport report written because MaxReports is reached already
                   figuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.


dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.
 texlive-extra-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-luatex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
Setting up xscreensaver (5.34-2ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Errors were encountered while processing:
 tex-common
 texlive-latex-base
 texlive-latex-recommended
 texlive-pictures
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 texlive-luatex
 texlive-pictures-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)


jonny2@jonny2-OptiPlex-745:~$ sudo apt-get update
Hit:1 http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial InRelease        
Hit:2 http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial InRelease       
Hit:3 http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial InRelease       
Hit:4 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease    
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:6 http://archive.canonical.com/ubuntu xenial InRelease          
Hit:7 http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial InRelease
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:9 http://archive.canonical.com xenial InRelease                            
Hit:10 http://ppa.launchpad.net/pipelight/stable/ubuntu xenial InRelease       
Hit:11 http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial InRelease
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB] 
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]  
Ign:14 http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise InRelease  
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 DEP-11 Metadata [307 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [223 kB]
Hit:17 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 DEP-11 Metadata [7,080 B]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 DEP-11 Metadata [188 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [265 kB]
Hit:21 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease          
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386 DEP-11 Metadata [3,328 B]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe i386 DEP-11 Metadata [4,588 B]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-security/main i386 DEP-11 Metadata [60.2 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.6 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu xenial-security/universe i386 DEP-11 Metadata [51.4 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [79.6 kB]
Hit:28 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial InRelease
Hit:29 http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise Release    
Fetched 1,558 kB in 8s (174 kB/s)                                              
Reading package lists... Done
W: http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu/dists/precise/Release.gpg: Signature by key A3F281188DF32E7665592D8188DB8FC6C190F85D uses weak digest algorithm (SHA1)
jonny2@jonny2-OptiPlex-745:~$ 



```

thanks!

at any rate if you dont hear from me tonight im trying to get some sleep.. thanks again. i'll have to force myself not to keep checking the forum all night, or worse, looking at other threads around the forum.. got to stop going to sleep at 7am.. its not working out, and i got a busy day tmo..

---

### Post by #&amp;thj^% on 2017-11-26
Now I'm getting the Gist of why some of your problems are happening.
Allow me to offer some Friendly Advice here, when upgrading OS versions:
This should always be the first thing to do**>>Backing Up Existing Data!<<**
2. Disable/Remove "All" PPA's added before your "Version" upgrade.
3. Remove any 3rd party Drivers>>(Video, Audio, etc etc)
4. Make sure the system is fully updated and dist-upgraded. (This is done after disabling all PPA's and removing 3rd party divers and such)
I like to use update-manager-core to manage the release upgrade. This package is installed by default in most Ubuntu installations, but to verify whether or not it is installed on the system by using "apt-cache":
```
apt-cache policy update-manager-core
```

If it is not installed, install it now with:
```
sudo apt-get install update-manager-core
```

Now you can begin your Upgrade process with:
```
sudo do-release-upgrade
```

**Now we can get on trying to help solving your problems.**
This PPA "ppa:rye/ubuntuone-extras"is dead it has not had any activity since (2013-11-25) 
 Ubuntu One on the file storage service has been dead for a few years, so it would better to remove it completly. 
And Yes we should run the autoremove command now.
```
sudo apt autoremove
```
Post back any errors please.
We will do this step by step so be patient. :D
BTW I will be in and out today ftr.

---

### Post by greyfaux01 on 2017-11-26
Ok not home so I can't do it now, but 2 things, 1. when I upgraded originally to 16.04 with do-release-upgrade, I didn't have enough free space in root, after removing stuff in synaptic (carefully,  only stuff it would let me without errors), and after removing all old kernels except for current and 1 prior, I finally had 6.5gb and it let me upgrade. But now with all the unneeded packages, I only have about 1.5gb free again, so I think the do-release-upgrade will fail again until I do autoremove first, so unless there's a other way, I think I need to autoremove before anything else. 

2. As you see I have tons of old dependencies, so I'm not sure exactly which ones I need to remove. I've used 14.04 for years (and 12.04 before that) and have no idea what specifically I need to disable.  If I can just uncheck all 3rd party dependencies or something I think I know how to do that. If that's an option 

Thanks

---

### Post by #&amp;thj^% on 2017-11-27
Do this for me:
```
sudo apt autoremove
```
And before accepting any changes, post back what is shown in the terminal.
Small steps at first.;) >>>We need to see the health of the package manager.

---

### Post by mastablasta on 2017-11-28
> **greyfaux01 said:**
> 
Now my first instinct was to just purge/reinstall these 2 missing packages (mega, kodi), but i didnt want to start breaking things worse, especially with repos, before getting professional help. I would rather not reinstall even these pacakges, but then again maybe thats what im supposed to do, since i had old packages that are not supported. Im just confused why kodi/mega did not get upgraded automagically with the rest of the system. Because of my confusion, im hesitant to start changing stuff without knowing why.
.

you very likely used PPAs for those apps. 

PPAs now get disabled on upgrade as they caused even more problems before (e.g GPU drivers PPA could cause boot failure/blank screen on when kernel was upgraded, but not the driver - a scary situation for some people). solution is to leave them disabled and add new ones, then upgrade the software via normal method. if that still fails then safest way is to remove the old software packages, remove the old PPA and then reinstall using new PPA.

---

### Post by greyfaux01 on 2017-11-28
Ok sorry, bunch of crap going on, plus car broke down, just now able to get back..
Well i realize now 1fallen that a lot of what you were saying was actually just general advice, when i read it fast at work i thought you wanted me to actually do the do-release-upgrade again, but now i see (i think) it was just all general advice, except for the update-manager-core. So either way, i went ahead and installed update-manager-core for future reference

```

jonny2@jonny2-OptiPlex-745:~$ apt-cache policy update-manager-coreupdate-manager-core:
  Installed: 1:16.04.10
  Candidate: 1:16.04.10
  Version table:
 *** 1:16.04.10 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:16.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
jonny2@jonny2-OptiPlex-745:~$ 
 
```


and the recon autoremove (ive always used 'apt-get' autoremove in the past, i think i remember reading something about 16.04 using only 'apt' now, idk).

```


jonny2@jonny2-OptiPlex-745:~$ sudo apt autoremove
[sudo] password for jonny2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  aptitude-common checkbox-ng comerr-dev g++-4.8 gcc-4.9-base gcj-4.8-jre-lib gstreamer1.0-clutter heirloom-mailx
  icedtea-netx-common java-common java-wrappers krb5-multidev libamd2.3.1 libapache-pom-java libapt-inst1.5
  libarchive-extract-perl libart2.0-cil libatk-wrapper-java libatk-wrapper-java-jni libavahi-client-dev
  libavahi-common-dev libavdevice53 libavfilter3 libavresample1 libbaloocore4 libbaloofiles4 libbaloowidgets4
  libbalooxapian4 libbasicusageenvironment0 libbcmail-java libbcpkix-java libbcprov-java libbind9-90
  libbit-vector-perl libboost-date-time1.54.0 libboost-filesystem1.54.0 libboost-iostreams1.54.0
  libboost-python1.54.0 libboost-regex1.54.0 libboost-serialization1.54.0 libboost-thread1.54.0 libc-ares2
  libcamd2.3.1 libcamel-1.2-45 libcarp-clan-perl libccolamd2.8.0 libcdr-0.0-0 libcec-platform1v5 libcholmod2.1.2
  libcmis-0.4-4 libcolamd2.8.0 libcolorhug1 libcommons-codec-java libcommons-httpclient-java libcommons-logging-java
  libcommons-parent-java libdate-calc-perl libdate-calc-xs-perl libdns100 libdom4j-java libdvbpsi8 libebackend-1.2-7
  libebook-1.2-14 libebook-contacts-1.2-0 libechonest2.1 libedata-book-1.2-20 libedataserver-1.2-18
  libegl1-mesa-drivers libelfg0 libept1.4.12 libexif-dev libexiv2-12 libfreenect0.2 libfstrcmp0 libgcj14
  libgcrypt11-dev libgcrypt20-dev libgegl-0.2-0 libgif4 libglade2.0-cil libglamor0 libglew1.10 libglewmx1.10
  libgmp-dev libgmpxx4ldbl libgnome-bluetooth11 libgnome-desktop-2-17 libgnome-desktop-3-7 libgnome2.24-cil
  libgnuinet-java libgnumail-java libgnutls-dev libgnutlsxx27 libgnutlsxx28 libgpac2 libgpg-error-dev libgphoto2-dev
  libgphoto2-port10 libgps20 libgraphicsmagick3 libgroupsock1 libgsoap4 libgssrpc4 libgtkhotkey1 libicu52
  libidn11-dev libieee1284-3-dev libilmbase6 libimobiledevice4 libisc95 libisccc90 libisccfg90 libisl10 libitext-java
  libjaxen-java libjdom1-java libjgoodies-common-java libjgoodies-looks-java libkadm5clnt-mit9 libkadm5srv-mit9
  libkdb5-8 libkfilemetadata4 libkimap4 libkldap4 libkrb5-dev liblinear1 liblivemedia23 libllvm3.4 liblockdev1
  liblog-message-perl liblog-message-simple-perl liblog4j1.2-java liblwres90 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmbim-glib0 libmikmod2 libmodule-pluggable-perl libmodule-runtime-perl
  libmono-compilerservices-symbolwriter4.0-cil libmono-system-runtime4.0-cil libmono-web4.0-cil libmrm4
  libmspub-0.0-0 libmusicbrainz5-0 libnepomukcleaner4 libnfs1 libobrender29 libopenexr6 libopenvg1-mesa
  liborcus-0.6-0 libp11-kit-dev libparams-classify-perl libpcre32-3 libpcrecpp0 libplatform1 libpocketsphinx1
  libpod-latex-perl libpodofo0.9.0 libpoppler44 libprocps3 libprotobuf-c0 libprotobuf8 libprotoc8 libqextserialport1
  libqmi-glib0 libqmmp0 libqmmpui0 libqmobipocket1 libqpdf13 libqt5qml-graphicaleffects libqt5sensors5
  libqt5webkit5-qmlwebkitplugin libqtlocation1 libquazip0 libraw9 librhythmbox-core8 libsctp1 libsexy2 libshairplay0
  libshp1 libsphinxbase1 libstdc++-4.8-dev libsvga1 libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libtar0
  libtasn1-6-dev libtasn1-doc libterm-ui-perl libtext-soundex-perl libthumbnailer0 libtinyxml2-0.0.0 libtinyxml2.6.2
  libts-0.0-0 libuil4 libumfpack5.6.2 libunique-1.0-0 libunityvoice1 libusageenvironment1 libusbmuxd2 libv4l-dev
  libv4l2rds0 libva-intel-vaapi-driver libvisio-0.0-0 libwlocate0 libwxbase2.8-0 libwxgtk-media2.8-0 libwxgtk2.8-0
  libxen-4.4 libxerces2-java libxfce4util6 libxine1 libxine1-misc-plugins libxine1-plugins libxine1-x
  libxml-commons-external-java libxml-commons-resolver1.1-java libxom-java libxpp2-java libxpp3-java libxtables10
  libzip2 linux-generic linux-headers-generic linux-image-generic lksctp-tools lxsession-logout lxshortcut nettle-dev
  python-bluez python-commandnotfound python-support python-wxgtk2.8 python3-checkbox qml-module-qtquick-localstorage
  qml-module-ubuntu-ui-extras-browser qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin
  qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-window-plugin ruby-vte ruby-vte3 shared-desktop-ontologies sphinx-voxforge-hmm-en
  sphinx-voxforge-lm-en syslinux-themes-debian syslinux-themes-debian-wheezy texlive-luatex thermald tsconf
  ttf-dejavu-extra unity-scope-audacious unity-scope-clementine unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-musique unity-voice-service watershed xchat-common xfce4-mixer
0 upgraded, 0 newly installed, 267 to remove and 2 not upgraded.
14 not fully installed or removed.
After this operation, 357 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
jonny2@jonny2-OptiPlex-745:~$ 




```


and yea mastablasta, those definitely are 3rd party PPA's. Ok makes sense though that it disables PPA's to make the upgrade smoother.. then im supposed to upgrade via package manager (or whatevers normal for me) after adding the new PPAs. You know, now that you say that, i realize i know that already, i think read that during the upgrade process, this time and in the past.. And yea ive encountered times where i wasn't able to boot, the one reason i love linux so much, is because even though not being able to boot/login/have a gui sucks, i know that at least it CAN be fixed. Opposed to when windows gets a BSOD, and you just cant really do anything. Ive broken grub before, and kept my cool and was able to fix it.. I remember the first time i ran 'sudo startx' lol.. that sucked.. also i somehow messed up my xauthority file (you know what im talking about, im not sure its 1 file or not) to where i had to create a guest account, and then fix the file, which then allowed me to login to my main account. I love how linux is meant to be broken basically, and then fixed again.. The saddest thing when it comes to windows, is when you end up on the official microsoft forums.. man. talk about dead end.. all the 'employees' do is act condescending to people, putting them down because they didnt include 'enough info about the problem', like all kinds of irrelevant hardware crap, that has nothing to do with say their networking/windows upgrade problem, and then, because i get sometimes it *is* relevant, the people give all the requested info, no one ever comes back to help.. sad really..

---

### Post by #&amp;thj^% on 2017-11-28
Hmm? There is a couple of things that concern me a bit.
Just to be safe lets use PPA-purge and recheck the autoremove just a bit later on.
Can you show me all your Repo Sources.
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```
Paste back please.
You can install things currently right?
Install this tool if you can to help clean things up from added PPA's
```
sudo apt install ppa-purge
``` 
When I see your source list I will give you some more task's to run. :)
Please be patient I have been very busy and will reply when I get a chance for the next couple of days. Thanks

---

### Post by greyfaux01 on 2017-11-29
Well yea, i did install xscreensaver and afterward the program is indeed on here now, even with all the errors. I just ran 'apt install ppa-purge' and it seems i already have that installed (i have y-ppa-manager with the gui installed, so if ppa-purge is not a default package, it may have came with y-ppa-manager).. at any rate, heres the output from when i installed ppa-purge, there were errors, and strangly it acted like it was going to install 0kb, but seemed to finish this ghost install with no problems, other than all the texcommon stuff.. (after 'installing' i went ahead and tried to run the program at the end there).. i wasn't going to actually do anything, i just wanted to see if it was indeed installed.

```

jonny2@jonny2-OptiPlex-745:~$ sudo apt install ppa-purge
[sudo] password for jonny2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ppa-purge is already the newest version (0.2.8+bzr63).
The following packages were automatically installed and are no longer required:
  aptitude-common checkbox-ng comerr-dev g++-4.8 gcc-4.9-base gcj-4.8-jre-lib
  gstreamer1.0-clutter heirloom-mailx icedtea-netx-common java-common java-wrappers
  krb5-multidev libamd2.3.1 libapache-pom-java libapt-inst1.5 libarchive-extract-perl
  libart2.0-cil libatk-wrapper-java libatk-wrapper-java-jni libavahi-client-dev
  libavahi-common-dev libavdevice53 libavfilter3 libavresample1 libbaloocore4
  libbaloofiles4 libbaloowidgets4 libbalooxapian4 libbasicusageenvironment0
  libbcmail-java libbcpkix-java libbcprov-java libbind9-90 libbit-vector-perl
  libboost-date-time1.54.0 libboost-filesystem1.54.0 libboost-iostreams1.54.0
  libboost-python1.54.0 libboost-regex1.54.0 libboost-serialization1.54.0
  libboost-thread1.54.0 libc-ares2 libcamd2.3.1 libcamel-1.2-45 libcarp-clan-perl
  libccolamd2.8.0 libcdr-0.0-0 libcec-platform1v5 libcholmod2.1.2 libcmis-0.4-4
  libcolamd2.8.0 libcolorhug1 libcommons-codec-java libcommons-httpclient-java
  libcommons-logging-java libcommons-parent-java libdate-calc-perl libdate-calc-xs-perl
  libdns100 libdom4j-java libdvbpsi8 libebackend-1.2-7 libebook-1.2-14
  libebook-contacts-1.2-0 libechonest2.1 libedata-book-1.2-20 libedataserver-1.2-18
  libegl1-mesa-drivers libelfg0 libept1.4.12 libexif-dev libexiv2-12 libfreenect0.2
  libfstrcmp0 libgcj14 libgcrypt11-dev libgcrypt20-dev libgegl-0.2-0 libgif4
  libglade2.0-cil libglamor0 libglew1.10 libglewmx1.10 libgmp-dev libgmpxx4ldbl
  libgnome-bluetooth11 libgnome-desktop-2-17 libgnome-desktop-3-7 libgnome2.24-cil
  libgnuinet-java libgnumail-java libgnutls-dev libgnutlsxx27 libgnutlsxx28 libgpac2
  libgpg-error-dev libgphoto2-dev libgphoto2-port10 libgps20 libgraphicsmagick3
  libgroupsock1 libgsoap4 libgssrpc4 libgtkhotkey1 libicu52 libidn11-dev
  libieee1284-3-dev libilmbase6 libimobiledevice4 libisc95 libisccc90 libisccfg90
  libisl10 libitext-java libjaxen-java libjdom1-java libjgoodies-common-java
  libjgoodies-looks-java libkadm5clnt-mit9 libkadm5srv-mit9 libkdb5-8 libkfilemetadata4
  libkimap4 libkldap4 libkrb5-dev liblinear1 liblivemedia23 libllvm3.4 liblockdev1
  liblog-message-perl liblog-message-simple-perl liblog4j1.2-java liblwres90
  libmagickcore5 libmagickcore5-extra libmagickwand5 libmbim-glib0 libmikmod2
  libmodule-pluggable-perl libmodule-runtime-perl
  libmono-compilerservices-symbolwriter4.0-cil libmono-system-runtime4.0-cil
  libmono-web4.0-cil libmrm4 libmspub-0.0-0 libmusicbrainz5-0 libnepomukcleaner4 libnfs1
  libobrender29 libopenexr6 libopenvg1-mesa liborcus-0.6-0 libp11-kit-dev
  libparams-classify-perl libpcre32-3 libpcrecpp0 libplatform1 libpocketsphinx1
  libpod-latex-perl libpodofo0.9.0 libpoppler44 libprocps3 libprotobuf-c0 libprotobuf8
  libprotoc8 libqextserialport1 libqmi-glib0 libqmmp0 libqmmpui0 libqmobipocket1
  libqpdf13 libqt5qml-graphicaleffects libqt5sensors5 libqt5webkit5-qmlwebkitplugin
  libqtlocation1 libquazip0 libraw9 librhythmbox-core8 libsctp1 libsexy2 libshairplay0
  libshp1 libsphinxbase1 libstdc++-4.8-dev libsvga1 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libtar0 libtasn1-6-dev libtasn1-doc
  libterm-ui-perl libtext-soundex-perl libthumbnailer0 libtinyxml2-0.0.0 libtinyxml2.6.2
  libts-0.0-0 libuil4 libumfpack5.6.2 libunique-1.0-0 libunityvoice1
  libusageenvironment1 libusbmuxd2 libv4l-dev libv4l2rds0 libva-intel-vaapi-driver
  libvisio-0.0-0 libwlocate0 libwxbase2.8-0 libwxgtk-media2.8-0 libwxgtk2.8-0 libxen-4.4
  libxerces2-java libxfce4util6 libxine1 libxine1-misc-plugins libxine1-plugins
  libxine1-x libxml-commons-external-java libxml-commons-resolver1.1-java libxom-java
  libxpp2-java libxpp3-java libxtables10 libzip2 linux-generic linux-headers-generic
  linux-image-generic lksctp-tools lxsession-logout lxshortcut nettle-dev python-bluez
  python-commandnotfound python-support python-wxgtk2.8 python3-checkbox
  qml-module-qtquick-localstorage qml-module-ubuntu-ui-extras-browser
  qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin
  qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets qtdeclarative5-window-plugin
  ruby-vte ruby-vte3 shared-desktop-ontologies sphinx-voxforge-hmm-en
  sphinx-voxforge-lm-en syslinux-themes-debian syslinux-themes-debian-wheezy
  texlive-luatex thermald tsconf ttf-dejavu-extra unity-scope-audacious
  unity-scope-clementine unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-musique unity-voice-service watershed xchat-common
  xfce4-mixer
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
14 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
\Setting up tex-common (6.04) ...
Ignoring /etc/texmf/texmf.d/05TeXMF.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/15Plain.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/45TeXinputs.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/55Fonts.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/65BibTeX.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/75DviPS.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/80DVIPDFMx.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/85Misc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/90TeXDoc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/95NonPath.cnf during generation of texmf.cnf, please remove manually!




Warning: Old configuration style found in /etc/texmf/updmap.d
Warning: For now these files have been included, 
Warning: but expect inconsistencies.
Warning: These packages should be rebuild with tex-common.
Warning: Please see /usr/share/doc/tex-common/NEWS.Debian.gz
Warning: found file: /etc/texmf/updmap.d/00updmap.cfg
Warning: found file: /etc/texmf/updmap.d/10lmodern.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-base.cfg
Warning: found file: /etc/texmf/updmap.d/10texlive-latex-base.cfg


Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.S2qoPGnl
Please include this file if you report a bug.


Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory


dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.


dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
 texlive-pictures depends on texlive-latex-recommended (>= 2015); however:
  Package texlive-latex-recommended is not No apport report written because the error message indicates its a followup error from a previous failure.
                                                           No apport report written because the error message indicates its a followup error from a previous failure.
                                                                           No apport report written because MaxReports is reached already
                                               configured yet.


dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-pictures (>= 2015); however:
  Package texlive-pictures is not configured yet.
 texlive-pstricks depends on texlive-generic-recommended (>= 2015); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.


dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2015); however:
  Package texlive-latex-base is not configured yet.
 texlive-extra-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.
No apport report written because MaxReports is reached already


dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-luatex (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 6); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on tex-common (>= 6); however:
No apport report written because MaxReports is reached already
                                                                Package tex-common is not configured yet.


dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tex-common
 texlive-latex-base
 texlive-latex-recommended
 texlive-pictures
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-latex-base-doc
 texlive-latex-recommended-doc
 texlive-luatex
 texlive-pictures-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonny2@jonny2-OptiPlex-745:~$ ppa-purge
Warning:  Required ppa-name argument was not specified
Usage: sudo ppa-purge [options] <ppa:ppaowner>[/ppaname]


ppa-purge will reset all packages from a PPA to the standard
versions released for your distribution.


Options:
	-p [ppaname]		PPA name to be disabled (default: ppa)
	-o [ppaowner]		PPA owner
	-s [host]		Repository server (default: ppa.launchpad.net)
	-d [distribution]	Override the default distribution choice.
	-y 			Pass -y --force-yes to apt-get or -y to aptitude
	-i			Reverse preference of apt-get upon aptitude.
	-h			Display this help text


Example usage commands:
	sudo ppa-purge -o xorg-edgers
	will remove https://launchpad.net/~xorg-edgers/+archive/ppa


	sudo ppa-purge -o sarvatt -p xorg-testing
	will remove https://launchpad.net/~sarvatt/+archive/xorg-testing


	sudo ppa-purge [ppa:]ubuntu-x-swat/x-updates
	will remove https://launchpad.net/~ubuntu-x-swat/+archive/x-updates


Notice: If ppa-purge fails for some reason and you wish to try again,
(For example: you left synaptic open while attempting to run it) simply
uncomment the PPA from your sources, run apt-get update and try again.


jonny2@jonny2-OptiPlex-745:~$ 



```


And heres all my repos. fyi about the old chrome repo, im running 32bit, and I know google doesnt support chrome/linux/32bit anymore, but i didnt want to remove the repo and break dependencies (even though it probably wouldn't have, i didnt know for sure).. but i did want to keep chrome around for random stuff.. mainly it was for netflix when i used to use netflix, but thats long gone.. I havent used it in years probably.. sorry for the several years worth of old junk, im sure theres more..



```

jonny2@jonny2-OptiPlex-745:~$ grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-security main restricted multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-security universe
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list:
/etc/apt/sources.list:# deb http://packages.mate-desktop.org/repo/ubuntu trusty main # disabled on upgrade to trusty
/etc/apt/sources.list:# deb-src http://packages.mate-desktop.org/repo/ubuntu trusty main # disabled on upgrade to trusty
/etc/apt/sources.list:deb http://archive.canonical.com/ xenial partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ trusty partner
/etc/apt/sources.list:# deb http://ppa.launchpad.net/aap/kodi/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list:# deb-src http://ppa.launchpad.net/aap/kodi/ubuntu trusty main
/etc/apt/sources.list:# deb http://archive.getdeb.net/ubuntu trusty-getdeb apps # disabled on upgrade to xenial
/etc/apt/sources.list:# deb-src http://archive.getdeb.net/ubuntu trusty-getdeb apps
/etc/apt/sources.list:# deb https://deb.opera.com/opera-stable/ stable non-free # disabled on upgrade to xenial
/etc/apt/sources.list:# deb-src https://deb.opera.com/opera-stable/ stable non-free
/etc/apt/sources.list.d/banshee-team-ppa-precise.list:# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu xenial main #Banshee Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/banshee-team-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu xenial main #Banshee Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/banshee-team-ppa-precise.list.save:# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu xenial main #Banshee Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/bimsebasse-cinnamonextras-precise.list.save:# deb-src http://ppa.launchpad.net/bimsebasse/cinnamonextras/ubuntu precise main
/etc/apt/sources.list.d/deluge-team-ppa-precise.list:# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu xenial main #Deluge Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/deluge-team-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu xenial main #Deluge Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/deluge-team-ppa-precise.list.save:# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu xenial main #Deluge Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/dockbar-main-ppa-trusty.list:deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial main
/etc/apt/sources.list.d/dockbar-main-ppa-trusty.list:deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial main
/etc/apt/sources.list.d/dockbar-main-ppa-trusty.list.distUpgrade:deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial main
/etc/apt/sources.list.d/dockbar-main-ppa-trusty.list.distUpgrade:deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial main
/etc/apt/sources.list.d/dockbar-main-ppa-trusty.list.save:deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial main
/etc/apt/sources.list.d/dockbar-main-ppa-trusty.list.save:deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu xenial main
/etc/apt/sources.list.d/docky-core-ppa-precise.list:# deb http://ppa.launchpad.net/docky-core/ppa/ubuntu xenial main #Docky Development PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/docky-core-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/docky-core/ppa/ubuntu xenial main #Docky Development PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/docky-core-ppa-precise.list.save:# deb http://ppa.launchpad.net/docky-core/ppa/ubuntu xenial main #Docky Development PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.distUpgrade:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu xenial main
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list:# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu xenial main #GNOME 3 PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.distUpgrade:# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu xenial main #GNOME 3 PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.save:# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu xenial main #GNOME 3 PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.save:# deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/hannes-janetzek-enlightenment-svn-precise.list.save:# deb-src http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu precise main
/etc/apt/sources.list.d/hydr0g3n-qbittorrent-stable-precise.list.distUpgrade:# deb http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu precise main
/etc/apt/sources.list.d/hydr0g3n-qbittorrent-stable-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu precise main
/etc/apt/sources.list.d/jitsi.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/jitsi.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/jitsi.list.distUpgrade:deb http://download.jitsi.org/deb unstable/
/etc/apt/sources.list.d/jitsi.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/jitsi.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/jitsi.list.save:deb http://download.jitsi.org/deb unstable/
/etc/apt/sources.list.d/jitsi-stable.list.distUpgrade:deb https://download.jitsi.org stable/
/etc/apt/sources.list.d/jitsi-stable.list.save:deb https://download.jitsi.org stable/
/etc/apt/sources.list.d/kokoto-java-omgubuntu-stuff-precise.list.distUpgrade:deb http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu precise main
/etc/apt/sources.list.d/kokoto-java-omgubuntu-stuff-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu precise main
/etc/apt/sources.list.d/megasync.list.distUpgrade:deb https://mega.nz/linux/MEGAsync/xUbuntu_14.04/ ./
/etc/apt/sources.list.d/megasync.list.save:deb https://mega.nz/linux/MEGAsync/xUbuntu_14.04/ ./
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list:deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list:deb-src http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list.distUpgrade:deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list.distUpgrade:deb-src http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list.save:deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list.save:deb-src http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main #WebUpd8 disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list.distUpgrade:# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main #WebUpd8 disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/nilarimogard-webupd8-precise.list.save:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main #WebUpd8 disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list:deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.distUpgrade:# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.save:# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/opera.list.distUpgrade:deb http://deb.opera.com/opera/ stable non-free #Opera Official Source
/etc/apt/sources.list.d/opera-stable.list:# This file makes sure that Opera Browser is kept up-to-date
/etc/apt/sources.list.d/opera-stable.list:# as part of regular system upgrades
/etc/apt/sources.list.d/opera-stable.list:
/etc/apt/sources.list.d/opera-stable.list.distUpgrade:# This file makes sure that Opera Browser is kept up-to-date
/etc/apt/sources.list.d/opera-stable.list.distUpgrade:# as part of regular system upgrades
/etc/apt/sources.list.d/opera-stable.list.distUpgrade:
/etc/apt/sources.list.d/opera-stable.list.save:# This file makes sure that Opera Browser is kept up-to-date
/etc/apt/sources.list.d/opera-stable.list.save:# as part of regular system upgrades
/etc/apt/sources.list.d/opera-stable.list.save:
/etc/apt/sources.list.d/peterlevi-ppa-precise.list:deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial main
/etc/apt/sources.list.d/peterlevi-ppa-precise.list:deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial main
/etc/apt/sources.list.d/peterlevi-ppa-precise.list.distUpgrade:deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial main
/etc/apt/sources.list.d/peterlevi-ppa-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial main
/etc/apt/sources.list.d/peterlevi-ppa-precise.list.save:deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial main
/etc/apt/sources.list.d/peterlevi-ppa-precise.list.save:deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu xenial main
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list:# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu xenial main #Pidgin Developers PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu xenial main #Pidgin Developers PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/pidgin-developers-ppa-precise.list.save:# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu xenial main #Pidgin Developers PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/pipelight-stable-precise.list:deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
/etc/apt/sources.list.d/pipelight-stable-precise.list:deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
/etc/apt/sources.list.d/pipelight-stable-precise.list.distUpgrade:deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
/etc/apt/sources.list.d/pipelight-stable-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
/etc/apt/sources.list.d/pipelight-stable-precise.list.save:deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
/etc/apt/sources.list.d/pipelight-stable-precise.list.save:deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
/etc/apt/sources.list.d/qbittorrent-team-qbittorrent-stable-precise.list:deb http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
/etc/apt/sources.list.d/qbittorrent-team-qbittorrent-stable-precise.list:deb-src http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
/etc/apt/sources.list.d/qbittorrent-team-qbittorrent-stable-precise.list.distUpgrade:deb http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
/etc/apt/sources.list.d/qbittorrent-team-qbittorrent-stable-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
/etc/apt/sources.list.d/qbittorrent-team-qbittorrent-stable-precise.list.save:deb http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
/etc/apt/sources.list.d/qbittorrent-team-qbittorrent-stable-precise.list.save:deb-src http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu xenial main
/etc/apt/sources.list.d/rvm-smplayer-precise.list:# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu xenial main #SMPlayer disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/rvm-smplayer-precise.list.distUpgrade:# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu xenial main #SMPlayer disabled on upgrade to xenial disabled on upgrade to xenial
/etc/apt/sources.list.d/rvm-smplayer-precise.list.save:# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu xenial main #SMPlayer disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list:deb http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list:deb-src http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.distUpgrade:deb http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.save:deb http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.save:deb-src http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/satyajit-happy-themes-precise.list:# deb http://ppa.launchpad.net/satyajit-happy/themes/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/satyajit-happy-themes-precise.list:# deb-src http://ppa.launchpad.net/satyajit-happy/themes/ubuntu trusty main
/etc/apt/sources.list.d/satyajit-happy-themes-precise.list.distUpgrade:# deb http://ppa.launchpad.net/satyajit-happy/themes/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/satyajit-happy-themes-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/satyajit-happy/themes/ubuntu trusty main
/etc/apt/sources.list.d/satyajit-happy-themes-precise.list.save:# deb http://ppa.launchpad.net/satyajit-happy/themes/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/satyajit-happy-themes-precise.list.save:# deb-src http://ppa.launchpad.net/satyajit-happy/themes/ubuntu trusty main
/etc/apt/sources.list.d/shnatsel-zram-precise.list.distUpgrade:deb http://ppa.launchpad.net/shnatsel/zram/ubuntu precise main
/etc/apt/sources.list.d/shnatsel-zram-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/shnatsel/zram/ubuntu precise main
/etc/apt/sources.list.d/skype.list:# deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/skype.list.distUpgrade:# deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/skype.list.save:# deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list:deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list:deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.distUpgrade:deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.save:deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.save:deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/swiftfox.list.save:# deb http://getswiftfox.com/builds/debian unstable non-free #Swiftfox
/etc/apt/sources.list.d/synapse-core-ppa-trusty.list:# deb http://ppa.launchpad.net/synapse-core/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/synapse-core-ppa-trusty.list:# deb-src http://ppa.launchpad.net/synapse-core/ppa/ubuntu xenial main
/etc/apt/sources.list.d/synapse-core-ppa-trusty.list.distUpgrade:# deb http://ppa.launchpad.net/synapse-core/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/synapse-core-ppa-trusty.list.distUpgrade:# deb-src http://ppa.launchpad.net/synapse-core/ppa/ubuntu trusty main
/etc/apt/sources.list.d/synapse-core-ppa-trusty.list.save:# deb http://ppa.launchpad.net/synapse-core/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/synapse-core-ppa-trusty.list.save:# deb-src http://ppa.launchpad.net/synapse-core/ppa/ubuntu xenial main
/etc/apt/sources.list.d/syncthing.list:# deb http://apt.syncthing.net/ syncthing release # disabled on upgrade to xenial
/etc/apt/sources.list.d/syncthing.list.distUpgrade:# deb http://apt.syncthing.net/ syncthing release # disabled on upgrade to xenial
/etc/apt/sources.list.d/syncthing.list.save:# deb http://apt.syncthing.net/ syncthing release # disabled on upgrade to xenial
/etc/apt/sources.list.d/team-xbmc-ppa-precise.list:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/team-xbmc-ppa-precise.list:deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/team-xbmc-ppa-precise.list.distUpgrade:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/team-xbmc-ppa-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/team-xbmc-ppa-precise.list.save:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/team-xbmc-ppa-precise.list.save:deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial main
/etc/apt/sources.list.d/tiheum-equinox-precise.list:# deb http://ppa.launchpad.net/tiheum/equinox/ubuntu xenial main #Include the Faenza icon set disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/tiheum-equinox-precise.list.distUpgrade:# deb http://ppa.launchpad.net/tiheum/equinox/ubuntu xenial main #Include the Faenza icon set disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/tiheum-equinox-precise.list.save:# deb http://ppa.launchpad.net/tiheum/equinox/ubuntu xenial main #Include the Faenza icon set disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list:# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main #Ubuntu Wine Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main #Ubuntu Wine Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save:# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main #Ubuntu Wine Team PPA disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list:# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu xenial main #X Updates disabled on upgrade to xenial
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.distUpgrade:# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu xenial main #X Updates disabled on upgrade to xenial
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save:# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu xenial main #X Updates disabled on upgrade to xenial
/etc/apt/sources.list.d/virtualbox-offical-source.list:# deb http://download.virtualbox.org/virtualbox/debian xenial contrib #VirtualBox Offical Source disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/virtualbox-offical-source.list.distUpgrade:# deb http://download.virtualbox.org/virtualbox/debian xenial contrib #VirtualBox Offical Source disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/virtualbox-offical-source.list.save:# deb http://download.virtualbox.org/virtualbox/debian xenial contrib #VirtualBox Offical Source disabled on upgrade to trusty disabled on upgrade to xenial
/etc/apt/sources.list.d/vivaldi.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/vivaldi.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/vivaldi.list:#deb http://repo.vivaldi.com/stable/deb/ stable main
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:# deb http://repo.vivaldi.com/stable/deb/ stable main # disabled on upgrade to xenial
/etc/apt/sources.list.d/vivaldi.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/vivaldi.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/vivaldi.list.save:# deb http://repo.vivaldi.com/stable/deb/ stable main
/etc/apt/sources.list.d/vovansrnd-coolreader-precise.list:# deb http://ppa.launchpad.net/vovansrnd/coolreader/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/vovansrnd-coolreader-precise.list:# deb-src http://ppa.launchpad.net/vovansrnd/coolreader/ubuntu xenial main
/etc/apt/sources.list.d/vovansrnd-coolreader-precise.list.distUpgrade:# deb http://ppa.launchpad.net/vovansrnd/coolreader/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/vovansrnd-coolreader-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/vovansrnd/coolreader/ubuntu trusty main
/etc/apt/sources.list.d/vovansrnd-coolreader-precise.list.save:# deb http://ppa.launchpad.net/vovansrnd/coolreader/ubuntu xenial main # disabled on upgrade to xenial
/etc/apt/sources.list.d/vovansrnd-coolreader-precise.list.save:# deb-src http://ppa.launchpad.net/vovansrnd/coolreader/ubuntu xenial main
/etc/apt/sources.list.d/weather-indicator-team-ppa-precise.list.distUpgrade:deb http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu precise main #Weather Indicator PPA
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list:deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list.distUpgrade:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list.save:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-precise.list.save:deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
jonny2@jonny2-OptiPlex-745:~$ 



```


Thanks again for all your help.. Hopefully when the weekend comes i'll have a few hours of free time before work.. i'll try to check the forum tomorrow during the day though.. I really appreciate your help.

---

### Post by greyfaux01 on 2017-12-12
If anyone else is less busy and able to help, im totally cool with that, and would appreciate it very much.

General rundown is i have a few packages broken after updating from ubuntu 14.04 to 16.04 (kodi, megasync), and some problems with my xfce panel (DE of choice). Previously i would kill the 'application indicator service' and it would magically fix the xfce panel problems, but after upgrading, that service is no longer there to kill.

Updates and package installs still seem to work, but with tons of (tex-common) errors. I also have tons of old repos that i need to get rid of, but have been waiting to do things in the correct order. Im generally at the level of noob even though i been using linux for years. Ive always managed to fix things myself, but i feel like its been by the skin of my teeth, which means i dont really remember how i fixed it a month later.

Thanks for any help, from 1fallen or anyone.

---

### Post by VMC on 2017-12-12
How is your system partitioned. Do you have several partitions. fdisk will us: ```
sudo fdisk -l
```

Also, have you considered to just install 16.04 fresh, and add your saved ppa's later. Or is that completely out of the question?
I use to release-upgrade years ago but found the trouble not worth it. By the way, is this the command you first used:
```
sudo do-release-upgrade
```

Its too late to start over, unless you made backups, but here's one step by step solution, as 1fallen alluded to:
[https://www.howtoforge.com/tutorial/ubuntu-lts-update-dist-upgrade/](https://www.howtoforge.com/tutorial/ubuntu-lts-update-dist-upgrade/)

---

### Post by greyfaux01 on 2017-12-12
I’ll answer your questions for sure when I get home, but just generally, on this desktop the partitioning is basic root, home, swap. Again I'll run the command hopefully tonight though. 
 i have the steps written down that I did to upgrade, and yes I'm fairly certain it was do-release-uograde. I will certainly check my notes on that to be sure. 

Now I did actually do a redo backup of my hdd, but honestly I would rather avoid doing a fresh install. From what I understand I will have to install all my programs again, I realize there are possible shortcuts (like a text file from synaptic packages or something, idk), but also I got everything basically exactly like I want it, and would rather avoid the hassle of getting the UI set back up, programs, etc. I've made so many changes over the years I have no idea what I'll have to from scratch, not to mention what won't work anymore. 

I realize this can be an argument for a fresh install, but when I've upgraded in the past, I FEEL like I was able to get things back in perfect working order with just basic, minimal fixing, like the average couple broken packages etc. Where as a fresh install I feel like will take weeks/months of extra time to get everything back how I had it. I have less spare time now then I've had in the past, so I just think fixing a couple problems might take less time overall and still have my system like I want it. 

I could be wrong, but I'm so close already, everything else is working, xfce is still there, my repos, programs, tweaks, etc, the thought of going fresh seems daunting. I could certainly be wrong, but I certainly don't WANT to do a fresh install. I realize I'm asking a favor by doing it the hard way so I want to be clear that I appreciate the help. If my system will be too much a time vampire then I'll try to be open minded. But it still boots, updates, installs, my email accounts are all setup in tbird, and other  little things that takes up lots of time after a fresh install, that I usually forget I have to redo.

---

### Post by greyfaux01 on 2017-12-13
```
 jonny2@jonny2-OptiPlex-745:~$ sudo fdisk -l[sudo] password for jonny2: 
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00076746


Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  39069695  39067648  18.6G 83 Linux
/dev/sda2       39071742 487497727 448425986 213.8G  5 Extended
/dev/sda5       39071744  42975231   3903488   1.9G 82 Linux swap / Solaris
/dev/sda6       42977280 487497727 444520448   212G 83 Linux




jonny2@jonny2-OptiPlex-745:~$ 

```


and yes, i did sudo do-release-upgrade to upgrade to 16.04

---

### Post by greyfaux01 on 2017-12-14
Ok, got megasync reinstalled, and working.. also got my printer working, which was the original reason i upgraded to 16.04 in the first place (was gonna start a seperate thread for the printer when i got the OS back to prime).. All i did to get the printer working, was upgrade to 16.04.. of course orignally i had to install the HPIP (or whatever its called).. but when i was on 14.04, i went through the motions of setting up my printer, and it i think it said 'no printer found', either that or it acted like it set it up and didnt print anything..

Post upgrade, i went through the 'setup printer' motions again, and while im using an HP deskjet 3637, it listed it as a '3630 series', but that was the default selection, so i went with it. on the last step, it offered to print test page, so i hit the option, and low and behold the test page printed.

To get megasync working again, all i did was download the new 16.04 .deb from mega.nz, and use gdebi to install it.. i was thinking i needed to get rid of the old megasync first, but the need to use megasync and a printer drove me to just try and install it 'on top of' the old one.. it worked flawlessly..

If the mods want to close this thread then feel free.. 

The whole upgrade was a lot smoother than i even thought it was.. i guess 14.04 doesnt have the drivers to support my printer, but 16.04 did.. again i didnt do anything special to get the printer finally working or megasync, just reinstall megasycn, and install the HPIP and go through 'setup' for the printer..

All i got to do is get kodi working again, but i'll just try to install it 'on top of' the old one, then worry about clearing out those old packages down the road.. the last thing i need to fix, me xfce panel, i'll make a new thread in the xfce area.. i guess nothing really got broken during the upgrade.. but oh yea, those tex-common errors i just remembered about.. i'll make a new thread specifically for that.. regardless, thanks for inspiring me to fix this stuff myself..

---

