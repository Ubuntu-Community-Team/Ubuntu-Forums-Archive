---
title: "How to compile Amarok 1.4.10 with Wikipedia support"
date: 2009-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ArgiBurgi on 2009-09-11
I really dislike amaroK 2.x.....it's ugly and with less functionality. So I tried compiling amarok 1.4.10 from source, that's what you got to do in order to compile it WITH Wikipedia support (wich stopped functionning due to  a code update in the Wikipedia website):

Download the needed files from [http://rapidshare.com/files/278454219/amarok_1.4.10.orig.tar.gz.html](http://rapidshare.com/files/278454219/amarok_1.4.10.orig.tar.gz.html)
(You can also find them yourself but i have everything ready for you).

Extract them

First you need to install the ammarok common and the xine engine:
install amarok-common_1.4.10-0ubuntu3.1_all.deb 
install libgpod3-nogtk_0.6.0-5ubuntu2_amd64.deb
install amarok-engine-xine_1.4.10-0ubuntu3.1_amd64.deb

Install them according to your system architecture,those files and th are included  in the Amarok1.4.10.tar.gz (also I included the *i386 files).

Then we need to install the dependencies, those were calculated for an ubuntu 8.10 installation wich is the last version that amarok 1.4.10 were available via synaptic.
 
Open a terminal and insert:

```
sudo apt-get install cdbs comerr-dev diffstat fdupes gawk gettext-kde kdelibs4-dev kdesdk-scripts libaa1-dev libacl1-dev libart-2.0-dev libasound2-dev libaspell-dev libattr1-dev libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-qt3-dev libbz2-dev libcaca-dev libcucul-dev libcups2-dev libcupsys2-dev libcurl4-gnutls-dev libdbus-qt-1-dev libdirectfb-dev libdirectfb-extra libesd0-dev libfftw3-dev libflac-dev libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libidn11-dev libifp-dev libilmbase-dev libjasper-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev libldap2-dev liblua50-dev liblualib50-dev libmad0-dev libmng-dev libmpcdec-dev libmtp-dev libmusicbrainz4-dev libmysqlclient15-dev libncurses5-dev libnjb-dev libofa0-dev libogg-dev libopenexr-dev libpcre3-dev libpq-dev libqt3-compat-headers libqt3-headers libqt3-mt-dev libsasl2-dev libsdl1.2-dev libslang2-dev libsqlite3-dev libssl-dev libsysfs-dev libtag1-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 libtunepimp-dev libusb-dev libvisual-0.4-dev libvorbis-dev libxine-dev libxml2-dev libxmu-dev libxmu-headers libxslt1-dev lua50 mesa-common-dev qt3-dev-tools quilt ruby1.8-dev

```Next step is to downgrade libmtp-dev and libmtp8 in order to compile successfully (don't worry thei will be updated llater from the update manager and amarok will not stop functioning).

```
sudo apt-get autoremove libmtp-dev libmtp8
```Now install libmtp7_0.2.6.1-2ubuntu1_amd64.deb (or *i386)
and
install libmtp-dev_0.2.6.1-2ubuntu1_amd64.deb (or *i386)
from the folder.

Next and last dependency is to install Ruby, execute in a terminal:

```
sudo apt-get install ruby-full
```Ok. Now that we are done installing the needed files to compile we gonna add Wikipedia support to amarok.In the folder ther is a file called: contextbrowser.cpp witch i fixed it according to launchpad [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/comments/9](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/316140/comments/9)
First extract amarok_1.4.10.orig.tar.gz   copy contextbrowser.cpp and paste it in ~/amarok-1.4.10/amarok/src replacing the old one.

Now the compilation, open a terminal and navigate to ~/Amarok 1.4.10 Source/amarok-1.4.10
execute:
```
./configure --prefix=`kde-config --prefix` --without-arts
``````
make
``````
sudo make install
```At last it is installed but we need to add mp3 support so execute:
```
sudo apt-get install libxine1-ffmpeg
```Last step is to keep the amarok xine engine in the current version go to 
System -> Administration -> Synaptic Package Manage and search amarok
left click on amarok-engine-xine go to the package menu and click lock package, also do the same for amarok-common in order to keep the icons in tact, and you are done.

---

### Post by r_avital on 2009-11-04
Hi, and thank you, very useful.  However, the link you gave for downloading the files returns an error from that web site, saying that the download limit has been reached (10 downloads).

Any ideas on where I can find them all in one place?  Sorry, a bit new to this.

Thanks

---

### Post by randolf_ambrose on 2010-01-01
hi guys...

i tried to install Amarok 1.4 in my ubuntu 9.04...

i tried with all possible repos and in the end when i try to install, it says
> The following packages have unmet dependencies:
amarok14: Depends: amarok14-engine-xine (= 2:1.4.10-0ubuntu3~ppa4) but it is not going to be installed
so i tried "amarok-engine-xine_1.4.10-0ubuntu3.1_amd64.deb" but deb installer gave the error as 'Error: Cannot install 'libxine1'' and didnt install that package...
so i couldnt find a way to install xine and other stuff on my jaunty yet...

so i tried using tarball... but configuration didnt finish and gave this error
> checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
Please, someone help me with Amarok 1.4 on my 9.04...
am i forgetting something???

---

### Post by r_avital on 2010-01-01
Randolph,

Are you trying to compile Amarok 1.4 with Wikipedia, or just get Amarok 1.4 running in Ubuntu Jaunty 9.04?

If the latter, follow this link:[http://diabolicalorsmart.com/tech/installing-amarok-14-in-ubuntu-jaunty/](http://diabolicalorsmart.com/tech/installing-amarok-14-in-ubuntu-jaunty/)

What it describes, is how to get the repositories for Amarok 1.4 Jaunty comes with 2.0 and many people don't like it).  Once these repositories are added, you can follow the instructions on the link to install it,  or find Amarok 1.4 in Synaptic and install it from there.

I definitely recommend removing all traces of Amarok 2.0 before you start, if you're installed it earlier.  You can do that from Synaptic.

Hope this helps

---

