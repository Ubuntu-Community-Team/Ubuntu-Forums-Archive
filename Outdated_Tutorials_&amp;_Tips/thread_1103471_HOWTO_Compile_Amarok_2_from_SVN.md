---
title: "HOWTO: Compile Amarok 2 from SVN"
date: 2009-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by hyper_ch on 2009-03-22
[SIZE="6"]HOWTO: Compile Amarok 2 from SVN[/SIZE]


[SIZE="5"]Introduction[/SIZE]

Amarok is a pretty nifty and advance music player for the KDE desktop. However the current version in the *buntu 8.10 repos is hopelessly outdated and (IMHO) totally bugged. There's also the Amarok Neon Project, which aims at providing daily SVN builds for *buntu however lately they have not been updated. So, if you want to be up-to-date with latest Amarok development you either wait until the Neon Project provides binaries again or you compile it on your own. If you want to compile it on your own, you require KDE 4.2. There are also PPA repos for that, use my generator [http://repogen.simplylinux.ch](http://repogen.simplylinux.ch) to get the according info.

The following howto will feature a few more things than are necessary. I like especially to add the medibuntu repos so that together with kubuntu-restricted-extras I have codecs for just about everyting. The package I install from medibuntu in this howto is the w32codecs (or w64codecs if you are on a 64bit OS).

I tested this howto on a vanilla Kubuntu 8.10 install. Depending on how you modified your system over time you will need to adjust a few things.

Thanks goes to markey and mamarok in the #amarok channel in irc.freenode.org. Also the groundwork for this howto are the following two pages:
[http://amarok.kde.org/blog/archives/833-Installing-Amarok-2-from-SVN-in-your-home-directory.html](http://amarok.kde.org/blog/archives/833-Installing-Amarok-2-from-SVN-in-your-home-directory.html)
[http://amarok.kde.org/wiki/Development/MySQL_Embedded](http://amarok.kde.org/wiki/Development/MySQL_Embedded)


[SIZE="5"]Step 1: Remove current amarok installation[/SIZE]


**JAUNTY USERS: Have a look at this post here: [http://ubuntuforums.org/showpost.php?p=7052425&postcount=12](http://ubuntuforums.org/showpost.php?p=7052425&postcount=12)**


```

sudo apt-get purge amarok amarok-common amarok-engine-xine

```

Instead of "purge" you can also use "remove". The difference is that purge will delete config and user data files (e.g. your statistics and stuff) - you may want to make a backup first.


[SIZE="5"]Step 2: Update your sources.list[/SIZE]

You can use my repo generator: [http://repogen.simplylinux.ch](http://repogen.simplylinux.ch) . It's important that you select the "main, restricted, universe, multiverse" branches, the "security, updates, proposed, backport" updates and the "KDE 4.2 PPA, Medibuntu" 3rd party repos. Medibuntu isn't required but it's recommended (although some people don't like it /me glances at HymnToLife).

That should generate a list like this:

```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse 
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse 
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted universe multiverse 
deb http://ch.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu intrepid partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### KDE 4.2 PPA Repos - http://www.kubuntu.org/news/kde-4.2
## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main

#### Medibuntu - http://www.medibuntu.org/
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
deb http://packages.medibuntu.org/ intrepid free non-free

```

Replace your /etc/apt/sources.list with this list above (or your own) or add the missing parts to it.

Finally you just need to import that gpg keys to get rid of the error message that would appear otherwise:

```

gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```


[SIZE="5"]Step 3: Upgrade[/SIZE]

After you added the KDE 4.2 repos you need to upgrade your system:

```

sudo apt-get dist-upgrade

```

And then remove the obsolete dependencies (not necessary but recommended):

```

sudo apt-get autoremove

```


[SIZE="5"]Step 4: Reboot[/SIZE]

Reboot your system:

```

sudo reboot

```


[SIZE="5"]Step 5: Installe required packages[/SIZE]

Now install the required packages. If you're on 64-bit then use the w64codecs package instead of the w32codecs one.:

```

sudo apt-get install kubuntu-restricted-extras w32codecs build-essential kde-devel subversion libmysqlclient15-dev libncurses5-dev libtag1-dev libstrigiqtdbusclient-dev

```


[SIZE="5"]Step 6: Extend your .bashrc and myenv.sh[/SIZE]

You need to extend your .bashrc and myenv.sh files with a few things. Just run those commands:

```

echo '' >> ${HOME}/.bashrc
echo 'export PATH=$HOME/kde/bin:$PATH' >> ${HOME}/.bashrc
mkdir -p ${HOME}/.kde/env
touch ${HOME}/.kde/env/myenv.sh
echo '' >> ${HOME}/.kde/env/myenv.sh
echo 'export KDEDIR=$HOME/kde' >> ${HOME}/.kde/env/myenv.sh
echo 'export KDEDIRS=$KDEDIR' >> ${HOME}/.kde/env/myenv.sh

```

**Non-KDE users need to run this code instead:**
```

echo '' >> ${HOME}/.bashrc
echo 'export PATH=$HOME/kde/bin:$PATH' >> ${HOME}/.bashrc
echo 'export KDEDIR=$HOME/kde' >> ${HOME}/.bashrc
echo 'export KDEDIRS=$KDEDIR' >> ${HOME}/.bashrc

```


And verify whether those were really added:

```

cat ${HOME}/.bashrc
cat ${HOME}/.kde/env/myenv.sh

```

*Non-KDE users just run the first command.*

[SIZE="5"]Step 7: Reload your .bashrc[/SIZE]

Reload your .bashrc:

```

source ${HOME}/.bashrc

```


[SIZE="5"]Step 8: Created required folders[/SIZE]

Create the required folders:

```

mkdir -p ${HOME}/kde/src
mkdir -p ${HOME}/kde/build/amarok

```


[SIZE="5"]Step 9: Download amarok and taglib-extras by svn[/SIZE]

Download Amarok and libtag-extras by issuing these commands:

```

cd ${HOME}/kde/src
svn co svn://anonsvn.kde.org/home/kde/trunk/extragear/multimedia/amarok amarok
svn co svn://anonsvn.kde.org/home/kde/trunk/kdesupport/taglib-extras/ taglib-extras

```

At the time I did this I checked out revision 942886.


[SIZE="5"]Step 10: Download MySQL[/SIZE]

MySQL is now integrated in Amarok 2 directly, this means we require the source for it. You can download MySQL here [http://dev.mysql.com/downloads/mysql/5.1.html#source](http://dev.mysql.com/downloads/mysql/5.1.html#source) (select the tar.gz version). The current version is 5.1.32 and for the next commands to be correct you need to change the version number accordingly if you use a newer one. If you opt to manually download MySQL then download it to: ${HOME}/kde/src

Or you can just follow those commands below to get the MySQL source into the proper place:

```

cd ${HOME}/kde/src
wget http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.32.tar.gz/from/http://mirror.switch.ch/ftp/mirror/mysql/

```


[SIZE="5"]Step 11: Extract and compile MySQL[/SIZE]

As said before, if you use a different version, you need to alter the version number in the following steps:


```

tar xzvf mysql-5.1.32.tar.gz
cd mysql-5.1.32
cp -R ${HOME}/kde/src/amarok/supplementary_scripts/mysqle/* .

```

In case you got a multicore cpu or more cpus then you can change the number of cores to be used to compile. If you have a dual core then set the option below to "-j3". If you have a quadcore set it to "-j5". In rare cases there are problems by using multicore; if that's the case then just set it to "-j1":

```

export MAKEOPTS=-j2

```

Now you can compile MySQL:

```

./build-mysqle.sh --prefix=${HOME}/usr

```


[SIZE="5"]Step 12: compile taglib-extras[/SIZE]

This has lately been moved out of the amarok svn and needs to be compiled on its own. Run the following steps:

```

cd ${HOME}/kde/src/taglib-extras/
mkdir build
cd build
export LD_LIBRARY_PATH=${HOME}/kde/build/taglib-extras/taglib-extras
cmake -DCMAKE_INSTALL_PREFIX=${HOME}/kde ..
make
make install

```


[SIZE="5"]Step 13: Compile QtScriptGenerator[/SIZE]

This is another part that was recently moved out of the amarok svn and there are still a few issues with it. Just run the code below or download newer versions at [http://code.google.com/p/qtscriptgenerator/downloads/list](http://code.google.com/p/qtscriptgenerator/downloads/list) :

```

cd ${HOME}/kde/src
wget http://qtscriptgenerator.googlecode.com/files/qtscriptgenerator-src-0.1.0.tar.gz
tar xfvz qtscriptgenerator-src-0.1.0.tar.gz
cd qtscriptgenerator-src-0.1.0

```

The current version 0.1.0 has a few issues with *buntu. Because of that you need to patch it by running the following from the qtscriptgenerator-0.1.0 directory:

```

nano include_everything.patch

```

And add this code to it:

```

--- b/generator/qtscript_masterinclude.h	2009-03-21 20:37:30.719523909 -0400
+++ a/generator/qtscript_masterinclude.h	2009-03-21 21:00:25.108149339 -0400
@@ -31,17 +31,41 @@
 
 #include <QtUiTools/QtUiTools>
 
-#ifndef QT_NO_XMLPATTERNS
-#  include <QtXmlPatterns/QtXmlPatterns>
-#endif
-
-#ifndef QT_NO_WEBKIT
-#  include <QtWebKit/QtWebKit>
-#endif
-
-#ifndef QT_NO_PHONON
-#  include <phonon/phonon>
-#endif
+#include <QtXmlPatterns/QtXmlPatterns>                                                              
+
+#include <QtWebKit/QtWebKit>                                                                        
+                                                                                                    
+#include "phonon/abstractaudiooutput.h"                                                             
+#include "phonon/abstractmediastream.h"                                                             
+#include "phonon/abstractvideooutput.h"                                                             
+#include "phonon/addoninterface.h"                                                                  
+#include "phonon/audiooutput.h"                                                                     
+#include "phonon/audiooutputinterface.h"                                                            
+#include "phonon/backendcapabilities.h"                                                             
+#include "phonon/backendinterface.h"
+#include "phonon/effect.h"
+#include "phonon/effectinterface.h"
+#include "phonon/effectparameter.h"
+#include "phonon/effectwidget.h"
+#include "phonon/mediacontroller.h"
+#include "phonon/medianode.h"
+#include "phonon/mediaobject.h"
+#include "phonon/mediaobjectinterface.h"
+#include "phonon/mediasource.h"
+#include "phonon/objectdescription.h"
+#include "phonon/objectdescriptionmodel.h"
+#include "phonon/path.h"
+#include "phonon/phonondefs.h"
+#include "phonon/phononnamespace.h"
+#include "phonon/platformplugin.h"
+#include "phonon/seekslider.h"
+#include "phonon/streaminterface.h"
+#include "phonon/videoplayer.h"
+#include "phonon/videowidget.h"
+#include "phonon/videowidgetinterface.h"
+#include "phonon/volumefadereffect.h"
+#include "phonon/volumefaderinterface.h"
+#include "phonon/volumeslider.h"
 
 #include "../qtbindings/qtscript_core/qtscriptconcurrent.h"

```

Now run the following command to patch the source:
 
```

patch -p1 < include_everything.patch

```
 
Once you've done that, you can compile qtscriptgenerator and the plugings by running the following:
 
```

export INCLUDE=/usr/include/qt4
cd generator
qmake
make
./generator
cd ../qtbindings
qmake
make

```

Once you're done you'll need to copy the plugins to /usr/lib/qt4/plugins/script:
 
```

cd ../plugins/script
sudo cp -R * /usr/lib/qt4/plugins/script/

```


[SIZE="5"]Step 14: Compile Amarok 2[/SIZE]

Finally we've reached the point where we can compile Amarok 2:
 
```

cd ${HOME}/kde/src/amarok
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=${HOME}/kde -DCMAKE_BUILD_TYPE=debugfull ${HOME}/kde/src/amarok
make
make install

```
 
After the cmake you will get a few warnings but compiling and installation should go without errors.


[SIZE="5"]Step 15: Update KDE config[/SIZE]

Now you need to update the KDE config:
 
```

kbuildsycoca4 --noincremental

```


[SIZE="5"]Step 16: Run Amarok 2[/SIZE]

Finally you can run Amarok 2 by issuing the following command in the terminal. I have yet to find a way to start it from the menu.:
 
```

amarok

```

---

### Post by linleno on 2009-04-03
This howto also works on Kubuntu Jaunty.
Thanks hyper_ch for this great howto!

---

### Post by hyper_ch on 2009-04-03
of course, on jaunty you need to have the jaunty repos (and not intrepid ones as in the howto) however they can easily be created by my tool :)

---

### Post by binbash on 2009-04-03
Excellent howto, thanks

---

### Post by linleno on 2009-04-03
BTW If someone also need to use ipod support, you may also need to have libgpod 0.7.0 installed. You could easily install the apt package "libgpod-common", "libgpod4-dev" and "libgpod4" in Jaunty. Not sure for other distro or previous k/ubuntu release.

sudo apt-get install libgpod-common libgpod4-dev libgpod4

---

### Post by clintonthegeek on 2009-04-10
> Amarok could not find any collection plugins. it is possible that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` && su -c "make install"
$ kbuildsycoca4 --noincremental
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.
This is what happens when I finally try to run "amarok" from the command line. It appears in a pop-up window after the Amarok splash screen pops up. This is on brand new Jaunty amd64 installation.

I've tried a few different things, but can't figure it out. Any ideas?

edit: Here's the debug output:

```
clinton@clinton-desktop:~/kde/src$ amarok --debug
amarok(4805) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
amarok:  ************************************************************************************************************
amarok:  ** DEBUGGING OUTPUT IS NOW ENABLED. PLEASE NOTE THAT YOU WILL ONLY SEE THE FULL OUTPUT ON THE NEXT START. **
amarok:  ************************************************************************************************************
amarok: END__: static void App::handleCliArgs() - Took 0.0004s
amarok: END__: virtual int App::newInstance() - Took 0.00055s
clinton@clinton-desktop:~/kde/src$ amarok: [PluginManager] Plugin trader constraint:  "[X-KDE-Amarok-framework-version] == 40 and [X-KDE-Amarok-plugintype] == 'collection' and [X-KDE-Amarok-rank] > 0"
amarok: [CollectionManager] Second attempt: Received [ "0" ] collection plugin offers
```

---

### Post by hyper_ch on 2009-04-10
I run it with those instructions on kubuntu jaunty 64bit. Are you using Ubuntu or Kubuntu?

---

### Post by clintonthegeek on 2009-04-10
I'm running Kubuntu, from the newest Beta install iso.

---

### Post by koolcracker on 2009-04-11
I am running Ubuntu 9.04 from the latest update and I got this same error. I followed everything to a tee. 

There were issues when I was setting up where it said that the ${HOME}/.kde/env/myenv.sh file did not exist, and after not finding anything useful in any searches I simply created a blank file myself.

Does anyone have any suggestions for me? Much appreciated.

---

### Post by kuja on 2009-04-11
I'm running 8.10 with KDE 4.2svn & Qt 4.5 (both installed in /usr/local), and trying to follow along with this but I've run into a slight problem :\

How can I tell cmake to look for qtscript-qt in /usr/local/plugins/script/? (It's having trouble finding it) Or should I take a different approach to this?

---

### Post by hyper_ch on 2009-04-11
> **clintonthegeek said:**
> I'm running Kubuntu, from the newest Beta install iso.
You still get that after reboot?

> **koolcracker said:**
> There were issues when I was setting up where it said that the ${HOME}/.kde/env/myenv.sh file did not exist, and after not finding anything useful in any searches I simply created a blank file myself.
The echo >> file command will create that variable with the according content.

> **kuja said:**
> How can I tell cmake to look for qtscript-qt in /usr/local/plugins/script/? (It's having trouble finding it) Or should I take a different approach to this?
If it doesn't work out of the box you could try to add it to the myenv.sh. I guess you need to enhance or alter this: KDEDIRS=$KDEDIR

---

### Post by hyper_ch on 2009-04-11
Update for Jaunty:

There are three differences on Jaunty (Beta):

Step 1: The amarok-engine-xine package is not installed by default on Jaunty so it cannot be purged.

Step 13: include_everything patch is not required

Step 16: Before running "amarok" in the terminal reboot the system.

I have attached the install log of a vanilla Kubuntu Jaunty 9.04 install on VmWare Workstation 6.5. It contains all steps done. The expanded log file is 2.5 MB and contains 30'000 lines.

---

### Post by koolcracker on 2009-04-11
graeme@graeme-laptop:~$ echo '' >> ${HOME}/.kde/env/myenv.sh
bash: /home/graeme/.kde/env/myenv.sh: No such file or directory

Is what happens when I echo that. I am going to try and follow the steps again with my manually created myenv.sh file and your new Jaunty instructions. Thanks for the reply.

---

### Post by hyper_ch on 2009-04-11
no clue why you get that response but you shouldn't get it.

---

### Post by koolcracker on 2009-04-11
I still came up empty handed. It says it can't find any collection plugins, would that be somehow related to that file that wouldn't create with the echo? Even though I ended up creating on manually?

---

### Post by hyper_ch on 2009-04-11
when did it come up with collection plugins?

---

### Post by kuja on 2009-04-11
> **hyper_ch said:**
> If it doesn't work out of the box you could try to add it to the myenv.sh. I guess you need to enhance or alter this: KDEDIRS=$KDEDIR

Still no joy here. Also, I'm not sure if I need the patch or not, so I've tried with and without. Attached are my scrollbacks for when I compiled qtscript (afterwards I copied them into /usr/local/plugins/script ... where I'd assume would be the proper place to look for them with my Qt installed in /usr/local), and another scrollback for when I tried to do cmake for amarok. (note, mymake="time taskset -c 1-3 make -j 4")

Also attaching CMakeCache.txt ... hopefully you'll be able to find something interesting.

---

### Post by hyper_ch on 2009-04-11
kuja:

no clue, if you want to use alternate paths you'll have to figure out yourself. I know tht my howto works as I've used it on my 8.10 64bit install and my current 9.06 64bit install and on 8.10 32bit and 9.04 32bit install on vmware.

---

### Post by koolcracker on 2009-04-11
I am getting the same error that was posted in #6. It comes up when I try to start Amarok. The installation seemed to go smoothly, but it won't run on the start up. I've tried redoing the prcoess three times now with the same results.

---

### Post by hyper_ch on 2009-04-11
as I said before, as you don't use the paths provided in the howto you need to figure out on your own what to change where.

---

### Post by koolcracker on 2009-04-11
I did use them though, I copied and pasted the majority of that tutorial.

---

### Post by hyper_ch on 2009-04-11
> **koolcracker said:**
> I copied and pasted the **majority** of that tutorial.
and that's the issue

---

### Post by koolcracker on 2009-04-11
I repeated it three times. I would love to hear where I went wrong then. I'm not incompetent.

---

### Post by hyper_ch on 2009-04-11
sorry, I confused your replies with those of Kuja. Please ignore my last few comments.

I have no clue why you don't get that environement .sh script set with the command issued. I tend to think you'll need to solve that problem first.

---

### Post by hyper_ch on 2009-04-11
actaully it seems, that echo '' >> /path/to/some/file.txt won't create the path. Then I wonder why do I have the env folder on a vanilla install with the according updates and you don't.

---

### Post by hyper_ch on 2009-04-11
I just did a vanilla install (again) and the ${HOME}/.kde/env folder exists. So it must be related to your setup then. If you don't have those folders then create them.

---

### Post by koolcracker on 2009-04-11
Ya, I did just create them, but my myenv.sh is completely blank except for the two lines i was supposed to add. Is there anythign else integral thats supposed to be in there? I don't really trust the Ubutunu update, but I didn't really feel like doing a fresh install for the Beta. When the RC comes out I'll do a clean install and see if that changes anything maybe.

---

### Post by hyper_ch on 2009-04-12
as you didn't have the folder I don't know what else you are missing... I assume there's more stuff. Do you use Ubuntu or Kubuntu?

---

### Post by bardophile on 2009-04-12
I'm running Ubuntu Intrepid 8.10. When I get to Step 5, I get the following error messages:

[I]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde-devel: Depends: kde-core (>= 5:48ubuntu1) but it is not going to be installed
             Depends: kdesdk (>= 4:4.1.1) but it is not going to be installed
             Depends: kdelibs5-dev (>= 4:4.1.1) but it is not going to be installed
             Depends: kdebase-dev (>= 4:4.1.1) but it is not going to be installed
             Depends: libkonq5-dev (>= 4:4.1.1) but it is not going to be installed
             Depends: kdebase-workspace-dev (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
[/I]

Any ideas on what I should do next?

---

### Post by hyper_ch on 2009-04-12
what's the output of

```

cat /etc/apt/sources.list

```

---

### Post by bardophile on 2009-04-12
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

###### Ubuntu Update Repos
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Amarok 2 - Project Neon - [http://amarok.kde.org/wiki/User:Apachelogger/Project_Neon](http://amarok.kde.org/wiki/User:Apachelogger/Project_Neon)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 0F7992B0 && gpg --export --armor 0F7992B0  | sudo apt-key add -
deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) intrepid main

#### Gnome-Do - [http://do.davebsd.com/](http://do.davebsd.com/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 77558DD0 && gpg --export --armor 77558DD0  | sudo apt-key add -
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main

#### KDE 4.2 PPA Repos - [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)
## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main

#### Medibuntu - [http://www.medibuntu.org/](http://www.medibuntu.org/)
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

#### Mozilla Daily Build Team - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: gpg --keyserver subkeys.pgp.net --recv-key 247510BE && gpg --armor --export  247510BE | sudo apt-key add -
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) intrepid main

#### OpenOffice.org 3.0 - [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF  | sudo apt-key add -
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

#### Skype - [http://www.skype.com](http://www.skype.com)
## Run this command: gpg --keyserver pgp.mit.edu --recv-keys 0xd66b746e && gpg --export --armor 0xd66b746e  | sudo apt-key add -
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

#### Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 0624A220 && gpg --export --armor 0624A220  | sudo apt-key add -
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main

#### Wine - [http://www.winehq.org/](http://www.winehq.org/)
## Run this command: wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main



deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

---

### Post by bardophile on 2009-04-12
Do I need to remove that last line?

---

### Post by hyper_ch on 2009-04-12
try to remove it but it should have no influence...

---

### Post by hyper_ch on 2009-04-12
actually add also proposed and backport repos.

---

### Post by bardophile on 2009-04-12
Just did that. Now in the process of installing 95.0MB of updates. Will get back to you after that is over. Thanks for your help up to now.

---

### Post by hyper_ch on 2009-04-12
then I need to update my howto :(

strange that the according kde packages are not provided by the ppa also.

---

### Post by koolcracker on 2009-04-12
I am running Ubutnu Jaunty. I'll post back after I do a clean install in a couple of days. I'm wondering if maybe something was missing.

---

### Post by hyper_ch on 2009-04-12
before reinstall you could try to instll kubuntu-desktop instead... just don't use KDM and after installation log out and back in but with kde session so that default folders and stuff are created.

Btw, I had a little talk with apachelogger today. Seems like there might be soon again nightly amarok versions provided by the Neon project.

---

### Post by bardophile on 2009-04-12
I'm sorry. I think I wasn't very clear. Following your advice, I went back and added the proposed and backport repos. After that, update manager told me that I had 95.0 MB of updates to install. Now that I have done that, and rebooted, I think I am successfully running step 5. It involves another large download, so will take some time for me. Back with an update later.

(edited to add this comment below)

Incidentally, this is only tangentially related, but the repo generator does not offer Pakistan as a country. I have no idea how hard that is to change, but it would be helpful.

---

### Post by hyper_ch on 2009-04-12
yeah, the downloads take a little while (and then compiling also). When I tested this on the virtual machines it took a bit less than 4h to go through all the steps (having 5mbit download).

The compilation of mysqle and qtscriptgenerator will also take a long time.

Are there official ubuntu repos in Pakistan? If so, just add "Pakistan" and the 2-letter country abbreviation to the generator :)

---

### Post by bardophile on 2009-04-12
hmm... now I get this. I'm sorry for the newbie questions, but I'm totally new to Linux.

aisha@minstrel:~/kde/src/mysql-5.1.33$ ./build-mysqle.sh --prefix=${HOME}/usr
bash: ./build-mysqle.sh: No such file or directory

---

### Post by hyper_ch on 2009-04-12
in the step before you needed to copy the build-mysqle.sh script over into the mysql folder.

---

### Post by bardophile on 2009-04-12
I THINK I'm in the mysql folder...am I not reading the bash prompt correctly?

---

### Post by bardophile on 2009-04-12
doesn't the line of code below accomplish that?

cp -R ${HOME}/kde/src/amarok/supplementary_scripts/mysqle/*

Update:ok, figured out how to do that... :)

---

### Post by bardophile on 2009-04-12
When I try to patch the qtscriptgenerator, I am told:

aisha@minstrel:~/kde/src/qtscriptgenerator-src-0.1.0$ patch -p1 < include_everything.patch
patching file generator/qtscript_masterinclude.h
patch: **** malformed patch at line 53:

---

### Post by hyper_ch on 2009-04-12
remove the qtscript folder, extract the sources again and try to patch again.

I just did it on my two virtual machines (I've forgotten to remove the qtscript tgzs so they were saved as .1 each). I have attached again the script log. I don't encounter any problems.

---

### Post by bardophile on 2009-04-13
Thanks for your patient assistance:

I managed to get the patch done on the third attempt. Must have been a problem with the way I was cutting and pasting code into the nano file.

However, having come to the end of your how-to, I now run into the same error message that others are reporting about amarok being unable to find collection plugins.

"Amarok could not find any collection plugins. It is possible that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` && su -c "make install"
$ kbuildsycoca4 --noincremental
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net."

I tried to follow their suggestions, but when I try to "make uninstall", I get:

"make: *** No rule to make target `uninstall'.  Stop."

My searching online leads me to think that I may need to simply remove the amarok src folder and then start over... is that correct?

---

### Post by hyper_ch on 2009-04-13
hmmmm, no clue why you get that... :(

you're using Ubuntu or Kubuntu?

---

### Post by bardophile on 2009-04-13
I'm wondering... in the line of code where we're compiling amarok, your version and the suggested version are slightly different...i.e.:

yours: [COLOR="Red"]cmake -DCMAKE_INSTALL_PREFIX=${HOME}/kde[/COLOR] -DCMAKE_BUILD_TYPE=debugfull ${HOME}/kde/src/amarok

error message suggestion:[COLOR="Red"]cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`[/COLOR] && su -c "make install"

What do you think would happen if we replaced your code in red with their code in red? I'm in the process of redownloading amarok. Am thinking of trying this alternative when I get to that step. Am I going to break something by doing that?

---

### Post by bardophile on 2009-04-13
Tried reading up some more. The "HACKING" folder in the amarok sources says to use the line of code as you've written it. Am recompiling Amarok as we speak...didn't try the alternative after all. Will report back when I'm done.

P.S. My understanding was that there was some little "thanks" icon that I could click on for my appreciation of your help to be officially recorded. I don't see that anywhere....?

---

### Post by hyper_ch on 2009-04-13
my version is correct for my howto as it will make a local install into the compiling user's home. That's the same way (some) of the amarok developpers test it.

---

### Post by bardophile on 2009-04-13
I just realised that you had asked me a question: I am using Ubuntu 8.10

When I try to update the KDE Config this time, I get:

aisha@minstrel:~$ kbuildsycoca4 --noincremental
kbuildsycoca4 running...
kbuildsycoca4(6182) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/audio/x-sbc.xml" 
kbuildsycoca4(6182) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-pem-key.xml" 
kbuildsycoca4(6182) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-ssh-key.xml" 
kbuildsycoca4(6182) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-hcidump.xml" 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/flocks.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/flux.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/helios.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/fieldlines.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/matrixview.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/solarwinds.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/sundancer2.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hufo_smoke.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/lattice.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/biof.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/cyclone.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hufo_tunnel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/euphoria.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/busyspheres.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hyperspace.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/spirographx.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/colorfire.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/plasma.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/skyrocket.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/kde/k3b.desktop" is not compliant with XDG standard (missing trailing semicolon). 
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 2: " "Invalid escape sequence "\ "." 
"KConfigIni: In file /usr/share/applications/wine-browsedrive.desktop, line 8: " "Invalid escape sequence "\ "." 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/screensavers/plasma.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/avidemux-gtk.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/avidemux-gtk.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/exfalso.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/quodlibet.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/winff.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/speedcrunch.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/openoffice.org-startcenter.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(6182) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/openoffice.org-startcenter.desktop" is not compliant with XDG standard (missing trailing semicolon). 
aisha@minstrel:~$

---

### Post by bardophile on 2009-04-13
Tried running amarok in debug mode. The result is gobbledygook to me. Is it meaningful to you? I really appreciate your continued help.


aisha@minstrel:~/kde/src/amarok$ amarok --debug
amarok(6647) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
amarok:  ************************************************************************************************************ 
amarok:  ** DEBUGGING OUTPUT IS NOW ENABLED. PLEASE NOTE THAT YOU WILL ONLY SEE THE FULL OUTPUT ON THE NEXT START. ** 
amarok:  ************************************************************************************************************ 
amarok: END__: static void App::handleCliArgs() - Took 0.00042s 
amarok: END__: virtual int App::newInstance() - Took 0.00055s 
aisha@minstrel:~/kde/src/amarok$ kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
<unknown program name>(6028)/ KStartupInfo::createNewStartupId: creating:  "minstrel;1239611818;320812;6028_TIME0" : "unnamed app"
kbuildsycoca4 running...
amarok: [PluginManager] Plugin trader constraint:  "[X-KDE-Amarok-framework-version] == 40 and [X-KDE-Amarok-plugintype] == 'collection' and [X-KDE-Amarok-rank] > 0" 
amarok: [CollectionManager] Second attempt: Received [ "0" ] collection plugin offers

---

### Post by hyper_ch on 2009-04-13
noting extra ordinary there... run amarok now from the command line... if you get an error about collection plugins not found, reboot and run amarok again from the cli.

---

### Post by bardophile on 2009-04-13
Tried rebooting and running again from CLI. I get the same error window from Amarok, and this output in the terminal:

aisha@minstrel:~$ amarok
amarok(6004) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
aisha@minstrel:~$ kbuildsycoca4 running...
amarok(6004) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch /usr/bin/knotify4

---

### Post by hyper_ch on 2009-04-13
start it with amarok --debug and run first the kbuildsycoca command again.

---

### Post by hyper_ch on 2009-04-13
I finally figured out what the problem is.

Markey, one of the devs, told me that I should put a few paths into the myenv.sh file. That works really nice on KDE. However if you don't run KDE then that file won't get parsed. So non-KDE users have to run:

```

echo 'export KDEDIR=$HOME/kde' >> ${HOME}/.bashrc
echo 'export KDEDIRS=$KDEDIR' >> ${HOME}/.bashrc

```

Then reload the bashrc:

```

source ${HOME}/.bashrc

```

and then it should work.

I had originally everything in the .bashrc :)

---

### Post by bardophile on 2009-04-13
Ok, after having added these lines and then updating the KDE config again, I have finally been able to start Amarok. Hurray! Now to get acquainted with it. :)

Many many thanks for your patient help.

---

### Post by hyper_ch on 2009-04-13
well, the last part was because of a change I did and didn't consider the effect to non-KDE users ;)

---

### Post by hyper_ch on 2009-04-13
btw, if you need iPod or mass storage support you'll have to compile it with a few more libs ;)

---

### Post by SoulSmasher on 2009-04-25
i get this errors when i try to run ./generator
```
c-0.1.0$ cd generator
arda@arda-laptop:~/qtscriptgenerator-src-0.1.0/generator$ qmake
arda@arda-laptop:~/qtscriptgenerator-src-0.1.0/generator$ make
make -f Makefile.Release
make[1]: Entering directory `/home/arda/qtscriptgenerator-src-0.1.0/generator'
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/ast.o parser/ast.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/lexer.o parser/lexer.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/list.o parser/list.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/parser.o parser/parser.cpp
parser/parser.cpp:782:2: warning: #warning "implement me"
parser/parser.cpp:2329:2: warning: #warning "implement me"
parser/parser.cpp:2353:2: warning: #warning "implemente me (AST)"
parser/parser.cpp:2529:2: warning: #warning "implement me"
parser/parser.cpp:2537:2: warning: #warning "implement me"
parser/parser.cpp:3180:2: warning: #warning "mark the ast as constant"
parser/parser.cpp:3281:2: warning: #warning "Parser::skipFunctionBody() -- implement me"
parser/parser.cpp:3310:2: warning: #warning "implement me"
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/smallobject.o parser/smallobject.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/control.o parser/control.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/visitor.o parser/visitor.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/default_visitor.o parser/default_visitor.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/dumptree.o parser/dumptree.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/tokens.o parser/tokens.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/binder.o parser/binder.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/codemodel.o parser/codemodel.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/type_compiler.o parser/type_compiler.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/name_compiler.o parser/name_compiler.cpp
parser/name_compiler.cpp:66:2: warning: #warning "NameCompiler::visitUnqualifiedName() -- implement me"
parser/name_compiler.cpp:79:2: warning: #warning "don't use an hardcoded string as cast' name"
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/declarator_compiler.o parser/declarator_compiler.cpp
parser/declarator_compiler.cpp:116:2: warning: #warning "ptr to mem -- not implemented"
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/class_compiler.o parser/class_compiler.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/codemodel_finder.o parser/codemodel_finder.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/compiler_utils.o parser/compiler_utils.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/preprocessor.o parser/rpp/preprocessor.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/generator.o generator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/main.o main.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/reporthandler.o reporthandler.cpp
reporthandler.cpp: In static member function ‘static void ReportHandler::warning(const QString&)’:
reporthandler.cpp:42: warning: format not a string literal and no format arguments
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/typeparser.o typeparser.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/typesystem.o typesystem.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/asttoxml.o asttoxml.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/fileout.o fileout.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/generatorset.o generatorset.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/metajava.o metajava.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/customtypes.o customtypes.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/abstractmetabuilder.o abstractmetabuilder.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/abstractmetalang.o abstractmetalang.cpp
abstractmetalang.cpp: In member function ‘AbstractMetaFunctionList AbstractMetaClass::queryFunctions(uint) const’:
abstractmetalang.cpp:1391: warning: suggest parentheses around && within ||
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/prigenerator.o prigenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/generatorsetqtscript.o generatorsetqtscript.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/metaqtscriptbuilder.o metaqtscriptbuilder.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/metaqtscript.o metaqtscript.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/classgenerator.o classgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/shellgenerator.o shellgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/shellimplgenerator.o shellimplgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/shellheadergenerator.o shellheadergenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/setupgenerator.o setupgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/docgenerator.o docgenerator.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. generator.h -o release/moc_generator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_generator.o release/moc_generator.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. fileout.h -o release/moc_fileout.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_fileout.o release/moc_fileout.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. generatorset.h -o release/moc_generatorset.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_generatorset.o release/moc_generatorset.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. prigenerator.h -o release/moc_prigenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_prigenerator.o release/moc_prigenerator.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. generatorsetqtscript.h -o release/moc_generatorsetqtscript.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_generatorsetqtscript.o release/moc_generatorsetqtscript.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. classgenerator.h -o release/moc_classgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_classgenerator.o release/moc_classgenerator.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. shellgenerator.h -o release/moc_shellgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_shellgenerator.o release/moc_shellgenerator.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. shellimplgenerator.h -o release/moc_shellimplgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_shellimplgenerator.o release/moc_shellimplgenerator.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. shellheadergenerator.h -o release/moc_shellheadergenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_shellheadergenerator.o release/moc_shellheadergenerator.cpp
/usr/bin/moc-qt4 -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. setupgenerator.h -o release/moc_setupgenerator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/moc_setupgenerator.o release/moc_setupgenerator.cpp
/usr/bin/rcc -name generator generator.qrc -o release/qrc_generator.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DRXX_ALLOCATOR_INIT_0 -DQT_NO_DEBUG -DQT_XML_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I. -I/home/arda/qtscriptgenerator-src-0.1.0/generator/../common -Iparser -Iparser/rpp -Iparser/rpp -Irelease -I. -o release/qrc_generator.o release/qrc_generator.cpp
g++ -Wl,-O1 -o generator release/ast.o release/lexer.o release/list.o release/parser.o release/smallobject.o release/control.o release/visitor.o release/default_visitor.o release/dumptree.o release/tokens.o release/binder.o release/codemodel.o release/type_compiler.o release/name_compiler.o release/declarator_compiler.o release/class_compiler.o release/codemodel_finder.o release/compiler_utils.o release/preprocessor.o release/generator.o release/main.o release/reporthandler.o release/typeparser.o release/typesystem.o release/asttoxml.o release/fileout.o release/generatorset.o release/metajava.o release/customtypes.o release/abstractmetabuilder.o release/abstractmetalang.o release/prigenerator.o release/generatorsetqtscript.o release/metaqtscriptbuilder.o release/metaqtscript.o release/classgenerator.o release/shellgenerator.o release/shellimplgenerator.o release/shellheadergenerator.o release/setupgenerator.o release/docgenerator.o release/moc_generator.o release/moc_fileout.o release/moc_generatorset.o release/moc_prigenerator.o release/moc_generatorsetqtscript.o release/moc_classgenerator.o release/moc_shellgenerator.o release/moc_shellimplgenerator.o release/moc_shellheadergenerator.o release/moc_setupgenerator.o release/qrc_generator.o    -L/usr/lib -lQtXml -lQtCore -lpthread
make[1]: Leaving directory `/home/arda/qtscriptgenerator-src-0.1.0/generator'
arda@arda-laptop:~/qtscriptgenerator-src-0.1.0/generator$ ./generate
bash: ./generate: No such file or directory
arda@arda-laptop:~/qtscriptgenerator-src-0.1.0/generator$ ./generator
Please wait while source files are being generated...
QTDIR environment variable not set. This may cause problems with finding the necessary include files.
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:312
^C
arda@arda-laptop:~/qtscriptgenerator-src-0.1.0/generator$ 

```
do you have any idea what is the issue ?
trying on a fresh install of jaunty

---

### Post by metalcoat on 2009-04-27
What additional steps are required to build in ipod support?

---

### Post by SoulSmasher on 2009-04-30
*bump* any ideas about my question about qtscriptgenerator?

---

### Post by fperwth on 2009-07-06
I had the problem that compiling QtScriptGenerator failed with missing header files. (I'm using 9.04 with KDE 4.3 RC 1)
I just read about a solution in [http://amarok.kde.org/forum/index.php/topic,16753.0.html](http://amarok.kde.org/forum/index.php/topic,16753.0.html)

Using **qmake-qt4** instead of **qmake** solved the problem for me, too. I think that should be edited in the Howto, at least for 9.04.

---

### Post by Bloemetjesgordijn on 2009-08-11
Hi


Thx for the how to...but I get stuck at step 9

desktop:~/kde/src$ svn co svn://anonsvn.kde.org/home/kde/trunk/extragear/multimedia/amarok amarok
svn: URL 'svn://anonsvn.kde.org/home/kde/trunk/extragear/multimedia/amarok' doesn't exist


What a I doing wrong....thx in advance

cheerz

---

### Post by fperwth on 2009-08-11
The Amarok project switched to Git lately, now you have to use

git clone git://gitorious.org/amarok/amarok.git

to obtain the source code.

---

### Post by Bloemetjesgordijn on 2009-08-11
> **fperwth said:**
> The Amarok project switched to Git lately, now you have to use

git clone git://gitorious.org/amarok/amarok.git

to obtain the source code.



thx

Now I am stuck at step 13 lucky number :)


after ./generator

I get these messages....
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:315
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:315
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:315
** WARNING unknown directive '#warning' at /usr/include/qt4/QtCore/qglobal.h:315
WARNING(MetaJavaBuilder) :: enum 'QGradient::InterpolationMode' does not have a type entry or is not an enum
Classes in typesystem: 566
Generated:
  - classes...: 535 (0)
  - header....: 360 (0)
  - impl......: 360 (0)
  - modules...: 11 (8)
  - pri.......: 11 (0)

Done, 1 warnings (873 known issues)
marc@marc-desktop:~/kde/src/qtscriptgenerator-src-0.1.0/generator$

Beats me... but I dont think thats good is it?

I tried with and without the patch .....same warning/issue

I also tried qmake-qt4 instead of qmake but that didnt do the trick

cheerz

---

### Post by Bloemetjesgordijn on 2009-08-11
Well I decided to leave the warning as is was...

Now I get another error (this time @ compiling Amarok)

-----------------------------------------------------------------------------
-- The following REQUIRED packages could NOT be located on your system.
-- You must install these packages before continuing.
-----------------------------------------------------------------------------
   * qtscript-qt  <http://code.google.com/p/qtscriptgenerator/>
     QtScript Qt Bindings


it looks like qtscriptgenerator cannot be found, does anybody know were I should put it???

Cheerz

---

### Post by fperwth on 2009-08-11
I had the same problem. I think I solved it by installing some extra packages, but I don't know exactly anymore wich ones.

Maybe You could try
sudo apt-get install libqt4-script libqt4-scripttools

---

### Post by Sidb on 2009-08-11
Thanks for all the posts came in handy I was almost ripping my hair out :P

---

### Post by Bloemetjesgordijn on 2009-08-12
> **Sidb said:**
> Thanks for all the posts came in handy I was almost ripping my hair out :P

Your welcome :popcorn:

But do you have it working now?

---

