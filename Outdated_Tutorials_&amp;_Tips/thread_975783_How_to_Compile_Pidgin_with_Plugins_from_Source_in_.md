---
title: "How to Compile Pidgin with Plugins from Source in Intrepid Ibex"
date: 2008-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by kevdog on 2008-11-08
_**[SIZE="4"]Compiling Pidgin From Source on Intrepid Ibex[/SIZE]**_

**[SIZE="2"]Successful Platform Builds[/SIZE]**
32-bit - KevDog
64-bit - Fir3chi3f

**[SIZE="2"]Pidgin Plugins Later Described in this Guide[/SIZE]**
Purple Plugin Pack
OTR - Off-the-Record Messaging
Talkfilters
Bot Sentry
Pidgin Encryption
Pidgin Guifications
Gfire
Pidgin Status History Logging Plugin
Pidgin Rhythmbox Plugin
Pidgin Facebook
Twitter - Microblog-Purple

**[SIZE="3"]Install Necessary Dependencies[/SIZE]**

**Please note that installation of the pidgin dependency libraries will require 124 Mb of disk space.

```

sudo aptitude install build-essential graphviz checkinstall
sudo apt-get build-dep pidgin

```

(Wait for all libraries and dependencies to install)

**[SIZE="3"]Grab Pidgin Sources -- Currently using Pidgin 2.5.5 version[/SIZE]**

```

mkdir -p ~/src
cd ~/src
wget http://downloads.sourceforge.net/pidgin/pidgin-2.5.5.tar.bz2

```

**[SIZE="3"]Unpack and Compile, and Install Pidgin[/SIZE]**

```

tar -jxvf pidgin-2.5.5.tar.bz2
cd pidgin-2.5.5
./configure --enable-cyrus-sasl --with-system-ssl-certs=/etc/ssl/certs --enable-nss=yes  **(**See note below)**
make

```

Additional options can be used with the ./configure statement.  These switches are **Optional**, however the recommended switches were given above. (See ./configure --help for full option list):

--enable-cap : Contact Availability Plugin.  Requires SQLlite as an additional dependency.  Package no currently maintained
--enable-gevolution : Compile with the Evolution Plugin.  Again package maintainence has waned.
--enable-mono : Option Broken for >= 2.5.3 Releases (Actually de-activated by developers).  Do not use for releases >= 2.5.3.  Package has been abandoned
--enable-cryus-sasl : Option to enable Cyrus SASL support. Cyrus SASL is the recommended authentication library for the XMPP protocol plugin.

**[SIZE="3"]Installing Pidgin[/SIZE]**

```

#1 - Recommended Way -- Not using the Apt System -- This will make it easier to upgrade packages later
sudo make install

#2 - Using Apt System via the checkinstall program 
sudo checkinstall -D --fstrans=no --install=yes --pkgname=pidgin --pkgversion=2.5.5

#If upgrading from a previous install, or deinstallation, or going from deb to compiled version, the following command may also be helpful:
sudo ldconfig

```


_**[SIZE="4"]Plugins[/SIZE]**_

**Talkfilter**
The GNU Talk Filters are filter programs that convert ordinary English text into text that mimics a stereotyped or otherwise humorous dialect. These filters have been in the public domain for many years, but now for the first time they are provided as a single integrated package. The filters include austro, b1ff, brooklyn, chef, cockney, drawl, dubya, fudd, funetak, jethro, jive, kraut, pansy, pirate, postmodern, redneck, valspeak, and warez. Each program reads from standard input and writes to standard output. The package also provides the filters as a C library, so they can be easily used by other programs.
Homepage: [http://www.hyperrealm.com/main.php?s=talkfilters](http://www.hyperrealm.com/main.php?s=talkfilters)

```

cd ~/src
wget http://www.hyperrealm.com/talkfilters/talkfilters-2.3.8.tar.gz
tar zxfv talkfilters-2.3.8.tar.gz
cd talkfilters-2.3.8
./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname talkfilters --pkgversion 2.38

```

**Purple Plugin Pack**
51 Various Plugins to Add to the Functionality of Pidgin
Homepage: [http://plugins.guifications.org/trac/wiki/PluginPack](http://plugins.guifications.org/trac/wiki/PluginPack)

At the time of writing of this guide the latest version was:
purple-plugin_pack-2.5.1.tar.bz2

```

sudo aptitude install libaspell-dev
cd ~/src
wget http://plugins.guifications.org/trac/downloads/22 -O purple-plugin_pack-2.5.1.tar.bz2
tar -jxvf purple-plugin_pack-2.5.1.tar.bz2
cd purple-plugin_pack-2.5.1

To enable all the plugins (which some are deactivated in default install, do the following):
for i in *; do if [ -d $i ]; then cd $i; echo "Touching .build in: $i"; touch .build; cd ..; fi; done

./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname purple-plugin_pack --pkgversion 2.5.1
sudo ln -s /usr/local/lib/purple-2 /usr/lib/purple-2

```

**OTR - Off-the-Record Messaging**
Off-the-Record (OTR) Messaging allows you to have private conversations over instant messaging by providing: Encryption, Authentication, Deniability and Perfect forward secrecy.
Homepage: [http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/)

```

cd ~/src
wget http://www.cypherpunks.ca/otr/libotr-3.2.0.tar.gz http://www.cypherpunks.ca/otr/pidgin-otr-3.2.0.tar.gz
tar zxvf libotr-3.2.0.tar.gz && tar zxvf pidgin-otr-3.2.0.tar.gz
cd libotr-3.2.0
./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname libotr --pkgversion 3.2.0

cd ~/src/pidgin-otr-3.2.0
./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname pidgin-otr --pkgversion 3.2.0

```

**Character Counting Plugin**
.deb file available only for i386 architecture
Homepage: [http://dossy.org/2008/02/debian-package-of-character-counting-plugin-for-pidgin/](http://dossy.org/2008/02/debian-package-of-character-counting-plugin-for-pidgin/)

NOTE -- Following for i386 architecture only:
```

cd ~/src
wget http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin_2.3.1-1_i386.deb
sudo dpkg -i pidgin-convcharcount-plugin_2.3.1-1_i386.deb
sudo ln -s /usr/lib/pidgin/convcharcount.la /usr/local/lib/pidgin/convcharcount.la
sudo ln -s /usr/lib/pidgin/convcharcount.so /usr/local/lib/pidgin/convcharcount.so

```

For all other platforms-
The pidgin source code can be patched in order to gain functionality.  This would mean that pidgin would need to be reinstalled.
The patch file can be found here: [http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin-patch.txt](http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin-patch.txt)

In order to apply the patch, the following method could be used (Example listed below):
```

cd /src/pidgin-2.5.4
wget http://static.panoptic.com/pidgin/pidgin-convcharcount-plugin-patch.txt
patch -p1 < pidgin-convcharcount-plugin-patch.txt

Then recompile pidgin (as according to the instructions above):
./configure --enable-cyrus-sasl --with-system-ssl-certs=/etc/ssl/certs --enable-nss=yes

make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname=pidgin --pkgversion 2.5.4

```


**Pidgin-Encryption**
Pidgin-Encryption transparently encrypts your instant messages with RSA encryption. Easy-to-use, but very secure.
This is a competing product to the OTR (Off-the-Record Messaging Plugin)
Homepage: [http://pidgin-encrypt.sourceforge.net/](http://pidgin-encrypt.sourceforge.net/)

```

cd ~/src
wget http://downloads.sourceforge.net/pidgin-encrypt/pidgin-encryption-3.0.tar.gz
tar -zxvf pidgin-encryption-3.0.tar.gz
cd pidgin-encryption-3.0
./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname pidgin-encryption --pkgversion 3.0

```


**Pidgin Guifications**
Guifications is a Pidgin plugin that displays "toaster" popups in a user-defined corner of the screen, similar to features that have been added to the official MSN Messenger (now called Windows Live Messenger), Yahoo! Messenger and AOL Instant Messenger clients. It's highly configurable, easy to use, and has theme support. It really is the end-all, be-all toaster pop-up plugin for Pidgin!
Homepage: [http://plugins.guifications.org/trac/wiki/Guifications](http://plugins.guifications.org/trac/wiki/Guifications)

```

cd ~/src
wget http://downloads.guifications.org/plugins/Guifications2/pidgin-guifications-2.16.tar.bz2
tar -jxvf pidgin_guifications-2.16.tar.bz2
cd pidgin_guifications-2.16
./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname=pidgin_guifications --pkgversion=2.16

```

Now that the Guificatons plugin is installed -- It needs to be loaded with a theme in order to Work
Themes are available here: [http://sourceforge.net/tracker2/?func=browse&group_id=92888&atid=676821](http://sourceforge.net/tracker2/?func=browse&group_id=92888&atid=676821)

For our purposes we will install and load the Ubuntu_Human theme

```

cd ~/src
wget "http://sourceforge.net/tracker2/download.php?group_id=92888&atid=676821&file_id=263816&aid=1880191" -O Ubuntu_Human.tar.gz
tar -zxvf Ubuntu_Human.tar.gz
mkdir -p ~/.purple/guifications/themes
cp -rf Ubuntu_Human ~/.purple/guifications/themes

```

Of course once the theme is installed, the plugin must be activated once inside Pidgin by going to:
Tools->Plugins->Guifications (Select This Option)->Configure Plugin->Themes
Select Ubuntu Human as the Theme


**Bot Sentry**
Bot Sentry is a Pidgin plugin that attempts to stop SPAM IM.  This problems has been documented: [http://ubuntuforums.org/showthread.php?t=994677](http://ubuntuforums.org/showthread.php?t=994677).  Bot Sentry Homepage: [http://sourceforge.net/projects/pidgin-bs/](http://sourceforge.net/projects/pidgin-bs/)

```

sudo aptitude install subversion subversion-tools
cd ~/src
svn co https://pidgin-bs.svn.sourceforge.net/svnroot/pidgin-bs/bot-sentry/trunk pidgin-bot-sentry
cd pidgin-bot-sentry
./autogen.sh
./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname=Bot-Sentry --pkgversion=svn-`svn info|grep Revision |cut -f2 -d' '`

```

After Installation, Plugin must be Activated from within Pidgin (Tools->Plugins (Select Bot Sentry))


**Gfire**
Gfire is an open source plugin for the Pidgin IM client which allows you to connect the Xfire network. Gfire Homepage: [http://gfire.site40.net/?page_id=20](http://gfire.site40.net/?page_id=20)

```

cd ~/src
wget http://downloads.sourceforge.net/gfire/gfire-0.7.1.tar.gz
tar zxvf gfire-0.7.1.tar.gz
cd gfire-0.7.1

./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname=Gfire --pkgversion=0.7.1

```

Gfire adds the capabilities of becoming a client within the Gfire network.  To use the plugin, Select Account->Manage Accounts.  Select Add.  Then choose Xfire from the Protocol Dropbox List


**Pidgin Status History Logging Plugin**
Pidgin Status History is a Plugin to add the ability to log users statuses.  This functionality is not included in the default logging process. Homepage: [http://bla.thera.be/archives/20](http://bla.thera.be/archives/20)

```

cd ~/src
wget http://thera.be/my_public/my_projects/pidgin-logstatus-0.6.tar.bz2
tar jxvf pidgin-logstatus-0.6.tar.bz2
cd pidgin-logstatus-0.6v

make
sudo make install

```

With the install process the plugin (logstatus.so) will be copied to the:
~/home/.purple/plugins directory

To enable the plugin:
Tools->Plugins: Put a checkmark next to Buddy Status history 0.6v, and click Close


**Pidgin Rhythmbox Plugin**
The Pidgin-Rhythmbox plugin will automatically update your Pidgin user info and status message with the currently playing music in Rhythmbox. If the artist and title are known, it will also attempt to create a link to the song's lyrics by using Google's "I'm Feeling Lucky" feature.  Homepage: [http://jon.oberheide.org/projects/pidgin-rhythmbox/](http://jon.oberheide.org/projects/pidgin-rhythmbox/)

Grab svn sources, compile, and install:
```

cd ~/src
svn co http://pidgin-rhythmbox.googlecode.com/svn/trunk/ pidgin-rhythmbox
./autogen.sh
./configure
make

**Choose one of the Following Options (First Option Recommended):**
sudo make install
sudo checkinstall -D --fstrans=no --install=yes --pkgname=Pidgin-Rhythmbox --pkgversion=svn-`svn info|grep Revision |cut -f2 -d' '`

```

In order to Use Plugin:
#1 - Activate Plugin for Use
     Tools->Plugins: Put a checkmark next to Pidgin-Rhythmbox 2.0, and click Close
#2 - Configure Status (Will configure Away Status in this Example):
Select the Status Box at the Bottom of the Main Pidgin Window (The one that states available next to the Icon)
New Status
Within popup window select 
     Status: Away
     Message: %rb

%rb will substitute the name of the Artist and Track currently playing in Rhythmbox when your Away status is shown. (Of course this demands that rhythmbox actually be running).

For more Information: [http://ubuntuforums.org/showthread.php?t=622264](http://ubuntuforums.org/showthread.php?t=622264)

**Pidgin Facebook**
Facebook is due in the future to switch to the Jabber protocol at a yet undetermined date.  Until this happens this allows pidgin to interact with the Facebook IM protocol: [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

Although there is a .deb file available here: [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/), we will compile from svn source code to grab the latest and greatest capabilities.  This process however is somewhat convoluted.

Grab svn sources:
```

cd ~/src
svn checkout http://pidgin-facebookchat.googlecode.com/svn/trunk/ pidgin-facebookchat
cd pidgin-facebookchat

```

Modify Makefile

The Makefile included with the svn sources is applicable to a number of different platforms and architectures.  In order to use the makefile appropriately you must know something about your system architecture.  The general form how to enable the makefile is:

make libfacebook.so -- to build the plugin for 32-bit Linux
make libfacebook64.so -- to build the plugin for 64-bit Linux

Additional modifications however must be done to the Makefile to make this process actually work.  This requires manually editing a few lines in the Makefile.  Open your editor of choice to edit the makefile (gedit, vim, etc).

The top of the Makefile appears as the following:
```

#Customisable stuff here
LINUX32_COMPILER = i686-pc-linux-gnu-gcc
LINUX64_COMPILER = x86_64-pc-linux-gnu-gcc
WIN32_COMPILER = /usr/bin/i586-mingw32-gcc
#LINUX_ARM_COMPILER = arm-pc-linux-gnu-gcc
LINUX_ARM_COMPILER = arm-none-linux-gnueabi-gcc
LINUX_PPC_COMPILER = powerpc-unknown-linux-gnu-gcc
FREEBSD60_COMPILER = i686-pc-freebsd6.0-gcc

```

In order to compile for a 32-bit architecture I changed the first line to:
```

LINUX32_COMPILER = gcc

```

The default install section of the Makefile:
```

install:
        cp libfacebook.so /usr/lib/purple-2/
        cp libfacebook64.so /usr/lib64/purple-2/
        cp libfacebookarm.so /usr/lib/pidgin/
        cp libfacebookppc.so /usr/lib/purple-2/
        cp facebook16.png /usr/share/pixmaps/pidgin/protocols/16/facebook.png
        cp facebook22.png /usr/share/pixmaps/pidgin/protocols/22/facebook.png
        cp facebook48.png /usr/share/pixmaps/pidgin/protocols/48/facebook.png

```

Because I only wanted to install the 32-bit compilation I changed the install section to the following:
```

install:
        cp libfacebook.so /usr/lib/purple-2/
#       cp libfacebook64.so /usr/lib64/purple-2/
#       cp libfacebookarm.so /usr/lib/pidgin/
#       cp libfacebookppc.so /usr/lib/purple-2/
        cp facebook16.png /usr/share/pixmaps/pidgin/protocols/16/facebook.png
        cp facebook22.png /usr/share/pixmaps/pidgin/protocols/22/facebook.png
        cp facebook48.png /usr/share/pixmaps/pidgin/protocols/48/facebook.png

```

To actually compile and install the module: (using the 32-bit architecture as an example:

```

make libfacebook.so
sudo make install

```

To use the plugin, Select Account->Manage Accounts.  Select Add.  Then choose Facebook from the Protocol Dropbox List


**Twitter Plugin for Pidgin** 
Allows to send and receive Twitter Messages Using Pidgin
Homepage: [http://code.google.com/p/microblog-purple/](http://code.google.com/p/microblog-purple/)

Install Necessary Dependencies
```

sudo aptitude install libpurple-dev

```

Grab SVN sources
```

mkdir -p ~/src/microblog-purple
cd ~/src
svn co http://microblog-purple.googlecode.com/svn/trunk/ microblog-purple
cd microblog-purple

```

Modification of global.mak file to ensure plugins are installed within the /usr/local directory tree rather than the /usr tree
```

sed -i -e '/^PREFIX/s/usr/usr\/local/'

```

Compile and Install
```

make
sudo make install

```

Enabling Plugin

Two Use The Plugin, 2 Steps Are Required:
#1 - Within Pidgin, Add your Twitter Account 
(Accounts->Manage Accounts, Select Add.  Choose Protocol: TwitterIM.  Fill In Username/Password Properties)
#2 - Enable Twitter Plugin
(Tools->Plugins. Check the Twitgin Plugin).  Please see [http://code.google.com/p/microblog-purple/](http://code.google.com/p/microblog-purple/) for more details.

__________________________________________
Edits:[I]
Thanks to **andrew.46** for clarifying the checkinstall procedure as documented here: **[http://ubuntuforums.org/showpost.php?p=6222080&postcount=229](http://ubuntuforums.org/showpost.php?p=6222080&postcount=229)**
__________________________________________
Thanks to **borisattva** for providing much of the information for the Pidgin Rhythbox Plugin: [http://ubuntuforums.org/showthread.php?t=622264](http://ubuntuforums.org/showthread.php?t=622264)
__________________________________________
Thanks to **darkrain42** who provided clarification regarding the appropriate ./configure switches.  Noted also that the linux-header package is also not needed.
__________________________________________
Thanks to **irc://irc.freenode.net/#pidgin** for providing clarification on multiple issues
__________________________________________
Thanks to **Artificial Intelligence** from whom I borrowed much information for this guide: [http://sudan.ubuntuforums.com/showthread.php?t=658244](http://sudan.ubuntuforums.com/showthread.php?t=658244)[/I]

---

### Post by andrew.46 on 2008-11-21
Hi,

You may be able to get around the checkinstall problem by running:

```
sudo checkinstall --fstrans=no --install=yes 
```

Andrew

---

### Post by kevdog on 2008-11-21
Thanks a ton -- added to the guide!!!

---

### Post by bigbrovar on 2008-12-21
would this also work on hardy ? thanks  for the guide

---

### Post by kevdog on 2008-12-22
This should work for any version of Ubuntu past Feisty.  pre-Feisty they used a gaim-dep package rather than a pidgin-dep package.

---

### Post by IainPurdie on 2008-12-22
Think I may be missing something. I can't install the Debian packages due to lack of dependencies (though I seem to have the programs installed that it claims I don't...) so I had a look at your instructions.

I get to the "./configure..." line which seems to work, when I type:

"make"

I'm told there is no makefile. If I skip onto the next section and try either of the longer "checkinstall" or "make install" instructions, I get the same failure message:

"make: *** No rule to make target `install'. Stop."

Any ideas? I'm not one for usually going this route, but always interested in learning as I never know when I'll need it some other time!

---

### Post by kevdog on 2008-12-23
You must be doing something wrong -- Running config generates the make files.  Are you in the incorrect directory?  Something seems strange.

---

### Post by IainPurdie on 2008-12-23
I thought the same - I did many years ago (and I mean *many*) use to do this fairly frequently. I've ditched the folder now, but I did have three "make" files if I recall correctly. But for some reason "make" didn't seem to want to pick them up :(

I'm wondering if my system is anti-Pidgin as I can't get the thing to install from the deb files either! Might have to go back to the buggy old version from the repository :(

---

### Post by kevdog on 2008-12-23
Download and try to compile some other program for example (gnupg).  If you can't compile that program, its a problem with your setup and not pidgin.  I've never heard of this problem before.  Possibly your PATH statements are messed up?

---

### Post by IainPurdie on 2008-12-23
I'll have a try at that just to be sure. Best to iron out any kinks there in case it causes me problems in future.

In the meantime I found another three MSN-a-like programs which I much prefer to Pidgin anyway... So that's one solution :)

---

### Post by trash on 2009-01-02
Hardy xfce, at the 'sudo apt-get build-dep pidgin' it asks to install/download 23mb of 100+files that will use 124mb of space.
Space is an issue for me and maybe for others too so thought i would mention it before they start.

---

### Post by kevdog on 2009-01-03
I suppose your right, however I guess I don't consider 123Mb a lot of space.  If you are going to compile anything I would suggest a least some spare disk space since developmental libraries will always need to be downloaded.

---

### Post by telepathetic on 2009-01-03
Should I remove or purge pidgin before attempting this?  or does it matter?

---

### Post by kevdog on 2009-01-03
This guide installs pidgin within the 
/usr/local/ tree.  The normal installation using synaptic, or apt, or using the ubuntu repositories is within the /usr tree.  By default, a user's PATH statement looks within /usr/local/bin prior to /usr/bin, so its possible to have 2 installations of the program which do not conflict with each other.  

If you wanted to change this behavior to have the compiled version installed within the /usr tree, you would add the --prefix switch to the configure statement (something like):

./configure --prefix=/usr ......

Despite what is written in the guide, I usually install outside the apt system using sudo make install since its a lot easier to upgrade when a new version comes out.  

If after installing pidgin, you would like to know which version of pidgin you are using (the version within /usr or within /usr/local) you would type at the command line:

which pidgin

Hopefully that clears up some things.

---

### Post by brandon88tube on 2009-01-11
> **kevdog said:**
> 
```

tar -jxvf pidgin-2.5.3.tar.bz2
cd pidgin-2.5.3
./configure --enable-mono --enable-cap

[B]****Note something with mono seems to be broken with the 2.5.3 release.  
****A workaround is the following 
****./configure --enable-cap[/B]

make

```


What is mono and cap? I don't remember using these before.

---

### Post by kevdog on 2009-01-11
Just a few things to know.

From within the source directory, if you run:
./configure --help

It will give you the various configuration options that are available.  If you are adding --enable options, you are additionally adding features that are not contained in the base install of by default.

--enable-cap=compile with Contact Availability Prediction plugin

--enable-mono=compile with Mono runtime support (experimental)  I'm guessing this feature probably isn't needed by most, and in my experience its broken when trying to compile 2.5.3 from source. 

You may want to add additional non-default options such as:
--enable-dot - enable graphs in doxygen via dot

--enable-cyrus-sasl - enable Cryrus SASL support for jabberd

--enable-gevolution - compile with Evolution plugin

Please note that when choosing additional options, that additional dependencies may need to be installed prior to running the configure script.  For example, if choosing --enable-dot, both doxygen and graphviz should be installed.  

I'll try to clarify more if you have any additional questions.

---

### Post by brandon88tube on 2009-01-11
Thanks, another quick question. What are the downsides to installing it the make install way instead of the apt way?

---

### Post by kevdog on 2009-01-11
In my opinion there are no downsides to installing using the make install way.  However here is what someone else would say:
1. Using the apt system to install software, the apt system will warn you if there are conflicts with your currently installed version if one of the dependent libraries are updated (such as in the future).

What I've found however is although I have been warned, what the system wants to do is suggest an upgrade to the pidgin version currently in the repository, however the version contained in the repository is often an earlier version than what you have installed.

Also if you upgrade pidgin for example (say from 2.5.2 to 2.5.3 and you used checkinstall to install 2.5.2), it will suggest uninstalling all of your plugins you compiled first, and also want to install 2.5.2 from repository.  It really knows nothing about the upgrade you want to install and that 2.5.3 is actually a newer version than that contained in repository.

Although there are theoretical arguments for using checkinstall, I personally (unlike the guide would suggest), recommend simply using make install.  I have experienced no conflicts are breakages of packages when using this system when upgrading dependencies.  Also the plugins compiled against a later version always work for me with the newer version without uninstalling, recompiling, and then reinstalling.

Do what you think is best, however I recommend the make install way (although this would not be the official party line -- the guide was written in compliance with the party line principles, however since this isn't the main tutorial page, I feel I can comment at will).

---

### Post by Yink on 2009-01-11
RE: no make file in purple-plugin_pack

I had this same problem I typed in the command line

sudo apt-get install pidgin-dev

and then run the configure and make

---

### Post by kevdog on 2009-01-11
Yink

What part of the installation are you having problems with?  The actual install of pidgin or the purple-plugin-pack?

---

### Post by adamlau on 2009-01-12
Here are my minimal, working options for 2.5.3 under Xubuntu:

```
--disable-consoleui --disable-avahi --disable-nls --disable-doxygen --disable-gestures --disable-screensaver --disable-startup-notification --disable-gtkspell --disable-meanwhile --disable-gnutls --enable-nss --disable-perl --disable-tcl --disable-dependency-tracking --disable-schemas-install --disable-nm --with-dynamic-prpls=irc,jabber,msn,oscar,yahoo CFLAGS="-march=native -O2 -fomit-frame-pointer -pipe" CXXFLAGS="${CFLAGS}"
```

Breaks when going with:

```
--disable-shared --enable-static --with-static-prpls=irc,jabber,msn,oscar,yahoo
```

Anyone get 2.5.3 going with a strictly static build?

---

### Post by kevdog on 2009-01-12
Regarding the static build -- I didn't install the compilation, but was able to compile using your exact same flags without a problem:

./configure --enable-shared=no --enable-static --with-static-prpls=irc,jabber,msn,oscar,yahoo && make

Did you get an error in the compilation process?

---

### Post by darkrain42 on 2009-01-19
kevdog,

It would be good to recommend the following options by default. They are taken from Ubuntu's package and help Ubuntu interoperate with the OS better:

```

--enable-cyrus-sasl
--with-system-ssl-certs=/etc/ssl/certs
--enable-nss=yes

```

[LIST]
[*] Cyrus SASL is the recommended authentication library for the XMPP protocol plugin and is not just used to connect to servers using jabberd.
[*] Letting Pidgin use the system's store of trusted CA roots alleviates problems with some networks when they change certificates to ones not in the limited set Pidgin provides.
[*] The NSS plugin is the one that Ubuntu's package uses (and forcing at least one to be enabled will ensure that Pidgin builds with SSL support, needed for MSN, Google Talk, and possibly others)
[/LIST]

Also, I'm not quite sure why you recommend installing the linux-headers; those should /not/ be necessary for building pidgin or any of the plugins listed (unless I'm missing something).

If you have any questions, I can be found in irc://irc.freenode.net/#pidgin

---

### Post by sunny_nwho on 2009-01-19
cool thanks mate!

---

### Post by brandon88tube on 2009-01-30
Is there a way to just update pidgin without having to always compile from source? This tends to get annoying.

---

### Post by kevdog on 2009-01-31
> **brandon88tube said:**
> Is there a way to just update pidgin without having to always compile from source? This tends to get annoying.

What other method do you propose?  Usually upgrading any compiled software version, is either a new compile, or downloading and installing a new package someone else compiled, ie a .deb package.  Its possible to make a script that would automate the download/compilation process.  I haven't got any requests for that method.

---

### Post by brandon88tube on 2009-01-31
I guess, but it would be nice if it could update through your update manager/synaptic or something similar.

---

### Post by kevdog on 2009-01-31
The whole point of this thread is for those that want to compile from source.  If you want to update through synaptic, then use the pidgin version (which is usually quite old) in the Ubuntu repositories.  There is a price of inconvenience to be paid for cutting-edge releases.

---

### Post by brandon88tube on 2009-01-31
> **darkrain42 said:**
> kevdog,

It would be good to recommend the following options by default. They are taken from Ubuntu's package and help Ubuntu interoperate with the OS better:

```

--enable-cyrus-sasl
--with-system-ssl-certs=/etc/ssl/certs
--enable-nss=yes

```

[LIST]
[*] Cyrus SASL is the recommended authentication library for the XMPP protocol plugin and is not just used to connect to servers using jabberd.
[*] Letting Pidgin use the system's store of trusted CA roots alleviates problems with some networks when they change certificates to ones not in the limited set Pidgin provides.
[*] The NSS plugin is the one that Ubuntu's package uses (and forcing at least one to be enabled will ensure that Pidgin builds with SSL support, needed for MSN, Google Talk, and possibly others)
[/LIST]

Also, I'm not quite sure why you recommend installing the linux-headers; those should /not/ be necessary for building pidgin or any of the plugins listed (unless I'm missing something).

If you have any questions, I can be found in irc://irc.freenode.net/#pidgin

I'm curious, would it be better to use the Debugging info provided with the pidgin that came installed with ubuntu for all of your future installs? Example of pidgin 2.5.2```
Debugging Information
  Arguments to ./configure:   '--build=x86_64-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/pidgin' '--disable-maintainer-mode' '--disable-dependency-tracking' '--enable-gevolution' '--enable-cap' '--with-system-ssl-certs=/etc/ssl/certs' '--enable-perl' '--with-zephyr=/usr' '--enable-dbus' '--enable-gnutls=no' '--enable-nss=yes' '--enable-cyrus-sasl' 'build_alias=x86_64-linux-gnu' 'CC=cc' 'CFLAGS=-fstack-protector' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXX=g++' 'CXXFLAGS=-g -O2 -g -Wall -O2' 'FFLAGS=-g -O2'

```

Also, my main question here is even if you do not use those configuration options would you suggest having  Zephyr library (libzephyr): External or Internal?

---

### Post by kevdog on 2009-01-31
I'm going to be honest with you -- I dont know anything about libzephyr.

Are far as the configure flags, many of them I obtained from talking to the developers on the #pidgin IRC.  I usually prefer /usr/local as the default tree, since its then possible to keep two versions of pidgin installed on the system (the .deb install within /usr and the compiled version within /usr/local).  Ive never ran into any problems needing to alter the compiler or linker flags.

---

### Post by brandon88tube on 2009-01-31
Sorry for all the questions, but I wanted to know how I would uninstall the version I compiled if I used sudo make install? I would think sudo make uninstall, but I'm not sure on the exact code.

---

### Post by kevdog on 2009-01-31
Exactly sudo make uninstall.  That is the ticket. What I'm finding for my mileage however, is that I usually install over the top with the next version, and then I do a clean wipe of the system when a new version of ubuntu comes out, and start the process all over again.  It doesn't really take all that long to compile.  Once you do it once, you will be amazed how easy it actually is (may take anywhere from 20-30 min, maybe less depending on your computer).

---

### Post by brandon88tube on 2009-01-31
Yeah, thanks I decided just to make install over the old one.

---

### Post by khm on 2009-02-04
I don't understand how to integrate talkfilters with pidgin.  I've got talkfilters compiled and installed properly (I can use it from a command line), but I don't see any interface between talkfilters and pidgin.

Am I missing something?

---

### Post by kevdog on 2009-02-04
You need the purple plugin pack -- specifically the talkfilter plugin to access.  Here is a link: [http://plugins.guifications.org/trac/wiki/talkfilters](http://plugins.guifications.org/trac/wiki/talkfilters)

---

### Post by seriesoftubes on 2009-02-06
> alex@alex-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.

I get this message when I type 'make'. What do I do?

---

### Post by kevdog on 2009-02-07
Are you sure you are in the same directory where you performed the ./configure statement?

If following the guide exactly as written (which you don't really have to), it would be:

cd ~/src/pidgin-2.5.4
/.configure ....... (parameter listed here --- see guide)
make
sudo make install

---

### Post by khm on 2009-02-09
> **kevdog said:**
> You need the purple plugin pack -- specifically the talkfilter plugin to access.  Here is a link: [http://plugins.guifications.org/trac/wiki/talkfilters](http://plugins.guifications.org/trac/wiki/talkfilters)

Yeah, I did that... everything seemed to work just fine... but I don't see anywhere in the UI for pidgin that mentions talk filters. The plugins that are listed are as follows:
Album
Autoaccept
AutoProfile
Autoreply
bash.org
Buddy List Options
Buddy Notes
Buddy State Notification
Buddy Ticker
Chat User List Logging
Coin Flip
Colorize
Conversation Badger
Conversation Colors
DBus example
DeWYSIWEGification Plugin
Dice
DiffTopic
Enhanced History
/exec
ExtPlacement
Find IP
Google
gRIM
Group IM
Highlight
History
I'dle Mak'er
Iconify on away
Ignore
Infopane Options
IRC Helper
IRC More
Irssi Feature
Join/Part Hiding
Last Seen
List Handler
Log Reader
Magic 8 Ball
Markerline
Message Notification
Message Splitter
Message Timestamp Formats
Mouse Gestures
Music Messaging
Mystatusbox
Nautilus Integration
New Line
Nicksaid
Offline Message Emulation
Old Logger
Pidgin GTK+ Theme Control
Plonkers
Psychic Mode
Release Notification
Schedule
Send Button
Separate and tab
Show Offline
SIM-fix
SSL Info
Text Replacement
Timelog
Timestamp
XChat Chats
XMPP Console

Here is my output for the make install is:
```
***@***-desktop:~/src/purple-plugin_pack-2.5.1$ sudo make install
make  install-recursive
make[1]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1'
Making install in common
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/common'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/common'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/common'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/common'
Making install in doc
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/doc'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/doc'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/doc'
Making install in po
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/po'
linguas="en_AU es_ES fr vi "; \
	for lang in $linguas; do \
	  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
	  /home/***/src/purple-plugin_pack-2.5.1/install-sh -d $dir; \
	  if test -r $lang.gmo; then \
	    /usr/bin/install -c -m 644 $lang.gmo $dir/plugin_pack.mo; \
	    echo "installing $lang.gmo as $dir/plugin_pack.mo"; \
	  else \
	    /usr/bin/install -c -m 644 ./$lang.gmo $dir/plugin_pack.mo; \
	    echo "installing ./$lang.gmo as" \
		 "$dir/plugin_pack.mo"; \
	  fi; \
	  if test -r $lang.gmo.m; then \
	    /usr/bin/install -c -m 644 $lang.gmo.m $dir/plugin_pack.mo.m; \
	    echo "installing $lang.gmo.m as $dir/plugin_pack.mo.m"; \
	  else \
	    if test -r ./$lang.gmo.m ; then \
	      /usr/bin/install -c -m 644 ./$lang.gmo.m \
		$dir/plugin_pack.mo.m; \
	      echo "installing ./$lang.gmo.m as" \
		   "$dir/plugin_pack.mo.m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
installing en_AU.gmo as /usr/local/share/locale/en_AU/LC_MESSAGES/plugin_pack.mo
installing es_ES.gmo as /usr/local/share/locale/es_ES/LC_MESSAGES/plugin_pack.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/plugin_pack.mo
installing vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/plugin_pack.mo
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/po'
Making install in album
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/album'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/album'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'album.la' '/usr/local/lib/pidgin/album.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/album'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/album'
Making install in autoprofile
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/autoprofile'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/autoprofile'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'autoprofile.la' '/usr/local/lib/purple-2/autoprofile.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/autoprofile'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/autoprofile'
Making install in autoreply
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/autoreply'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/autoreply'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'autoreply.la' '/usr/local/lib/purple-2/autoreply.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/autoreply'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/autoreply'
Making install in bash
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/bash'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/bash'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'bash.la' '/usr/local/lib/purple-2/bash.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/bash'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/bash'
Making install in blistops
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/blistops'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/blistops'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'blistops.la' '/usr/local/lib/pidgin/blistops.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/blistops'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/blistops'
Making install in colorize
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/colorize'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/colorize'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'colorize.la' '/usr/local/lib/purple-2/colorize.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/colorize'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/colorize'
Making install in convbadger
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/convbadger'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/convbadger'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'convbadger.la' '/usr/local/lib/pidgin/convbadger.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/convbadger'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/convbadger'
Making install in dewysiwygification
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/dewysiwygification'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/dewysiwygification'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'dewysiwygification.la' '/usr/local/lib/purple-2/dewysiwygification.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/dewysiwygification'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/dewysiwygification'
Making install in dice
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/dice'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/dice'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'dice.la' '/usr/local/lib/purple-2/dice.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/dice'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/dice'
Making install in difftopic
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/difftopic'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/difftopic'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'difftopic.la' '/usr/local/lib/pidgin/difftopic.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/difftopic'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/difftopic'
Making install in eight_ball
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/eight_ball'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/eight_ball'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'eight_ball.la' '/usr/local/lib/purple-2/eight_ball.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/eight_ball'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/eight_ball'
Making install in enhancedhist
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/enhancedhist'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/enhancedhist'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'enhancedhist.la' '/usr/local/lib/pidgin/enhancedhist.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/enhancedhist'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/enhancedhist'
Making install in findip
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/findip'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/findip'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'findip.la' '/usr/local/lib/purple-2/findip.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/findip'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/findip'
Making install in flip
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/flip'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/flip'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'flip.la' '/usr/local/lib/purple-2/flip.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/flip'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/flip'
Making install in gRIM
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/gRIM'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/gRIM'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'gRIM.la' '/usr/local/lib/pidgin/gRIM.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/gRIM'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/gRIM'
Making install in google
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/google'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/google'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'google.la' '/usr/local/lib/purple-2/google.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/google'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/google'
Making install in groupmsg
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/groupmsg'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/groupmsg'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'groupmsg.la' '/usr/local/lib/purple-2/groupmsg.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/groupmsg'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/groupmsg'
Making install in highlight
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/highlight'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/highlight'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'highlight.la' '/usr/local/lib/purple-2/highlight.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/highlight'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/highlight'
Making install in ignore
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/ignore'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/ignore'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'ignore.la' '/usr/local/lib/purple-2/ignore.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/ignore'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/ignore'
Making install in infopane
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/infopane'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/infopane'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'infopane.la' '/usr/local/lib/pidgin/infopane.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/infopane'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/infopane'
Making install in irc-more
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/irc-more'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/irc-more'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'irc-more.la' '/usr/local/lib/purple-2/irc-more.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/irc-more'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/irc-more'
Making install in irchelper
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/irchelper'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/irchelper'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'irchelper.la' '/usr/local/lib/purple-2/irchelper.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/irchelper'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/irchelper'
Making install in irssi
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/irssi'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/irssi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'irssi.la' '/usr/local/lib/pidgin/irssi.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/irssi'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/irssi'
Making install in lastseen
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/lastseen'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/lastseen'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'lastseen.la' '/usr/local/lib/pidgin/lastseen.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/lastseen'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/lastseen'
Making install in listhandler
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/listhandler'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/listhandler'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'listhandler.la' '/usr/local/lib/purple-2/listhandler.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/listhandler'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/listhandler'
Making install in listlog
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/listlog'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/listlog'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'listlog.la' '/usr/local/lib/pidgin/listlog.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/listlog'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/listlog'
Making install in mystatusbox
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/mystatusbox'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/mystatusbox'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'mystatusbox.la' '/usr/local/lib/pidgin/mystatusbox.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/mystatusbox'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/mystatusbox'
Making install in napster
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/napster'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/napster'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'napster.la' '/usr/local/lib/purple-2/napster.la'
test -z "/usr/local/share/pixmaps/pidgin/protocols/16" || mkdir -p -- "/usr/local/share/pixmaps/pidgin/protocols/16"
 /usr/bin/install -c -m 644 '16/napster.png' '/usr/local/share/pixmaps/pidgin/protocols/16/napster.png'
test -z "/usr/local/share/pixmaps/pidgin/protocols/22" || mkdir -p -- "/usr/local/share/pixmaps/pidgin/protocols/22"
 /usr/bin/install -c -m 644 '22/napster.png' '/usr/local/share/pixmaps/pidgin/protocols/22/napster.png'
test -z "/usr/local/share/pixmaps/pidgin/protocols/48" || mkdir -p -- "/usr/local/share/pixmaps/pidgin/protocols/48"
 /usr/bin/install -c -m 644 '48/napster.png' '/usr/local/share/pixmaps/pidgin/protocols/48/napster.png'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/napster'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/napster'
Making install in nicksaid
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/nicksaid'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/nicksaid'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'nicksaid.la' '/usr/local/lib/pidgin/nicksaid.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/nicksaid'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/nicksaid'
Making install in oldlogger
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/oldlogger'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/oldlogger'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'oldlogger.la' '/usr/local/lib/purple-2/oldlogger.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/oldlogger'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/oldlogger'
Making install in plonkers
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/plonkers'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/plonkers'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'plonkers.la' '/usr/local/lib/pidgin/plonkers.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/plonkers'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/plonkers'
Making install in schedule
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/schedule'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/schedule'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'pidgin-schedule.la' '/usr/local/lib/pidgin/pidgin-schedule.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/schedule'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/schedule'
Making install in sepandtab
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/sepandtab'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/sepandtab'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'sepandtab.la' '/usr/local/lib/pidgin/sepandtab.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/sepandtab'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/sepandtab'
Making install in showoffline
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/showoffline'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/showoffline'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'showoffline.la' '/usr/local/lib/purple-2/showoffline.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/showoffline'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/showoffline'
Making install in simfix
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/simfix'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/simfix'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'simfix.la' '/usr/local/lib/purple-2/simfix.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/simfix'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/simfix'
Making install in slashexec
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/slashexec'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/slashexec'
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'slashexec.la' '/usr/local/lib/purple-2/slashexec.la'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/slashexec'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/slashexec'
Making install in snpp
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/snpp'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/snpp'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'libsnpp.la' '/usr/local/lib/purple-2/libsnpp.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/snpp'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/snpp'
Making install in splitter
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/splitter'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/splitter'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'splitter.la' '/usr/local/lib/purple-2/splitter.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/splitter'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/splitter'
Making install in sslinfo
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/sslinfo'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/sslinfo'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/purple-2" || mkdir -p -- "/usr/local/lib/purple-2"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'sslinfo.la' '/usr/local/lib/purple-2/sslinfo.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/sslinfo'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/sslinfo'
Making install in timelog
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/timelog'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/timelog'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'timelog.la' '/usr/local/lib/pidgin/timelog.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/timelog'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/timelog'
Making install in xchat-chats
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/xchat-chats'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1/xchat-chats'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pidgin" || mkdir -p -- "/usr/local/lib/pidgin"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c  'xchat-chats.la' '/usr/local/lib/pidgin/xchat-chats.la'
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/xchat-chats'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1/xchat-chats'
make[2]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1'
make[3]: Entering directory `/home/***/src/purple-plugin_pack-2.5.1'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1'
make[2]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1'
make[1]: Leaving directory `/home/***/src/purple-plugin_pack-2.5.1'

```

---

### Post by kevdog on 2009-02-09
Try the following:

cd /home/***/src/purple-plugin_pack-2.5.1/talkfilters
make
sudo make install

sudo updatedb
locate talkfilters | grep /usr/local/lib

---

### Post by khm on 2009-02-10
> **kevdog said:**
> Try the following:

cd /home/***/src/purple-plugin_pack-2.5.1/talkfilters
make
sudo make install

sudo updatedb
locate talkfilters | grep /usr/local/lib

```
***@***-desktop:~/src/purple-plugin_pack-2.5.1$ sudo updatedb
***@***-desktop:~/src/purple-plugin_pack-2.5.1$ locate talkfilters | grep /usr/local/lib
/usr/local/lib/libtalkfilters.a
/usr/local/lib/libtalkfilters.la
/usr/local/lib/libtalkfilters.so
/usr/local/lib/libtalkfilters.so.1
/usr/local/lib/libtalkfilters.so.1.0.4
/usr/local/lib/pkgconfig/talkfilters.pc

```

Still nothing... :(

Like I said before, the talkfilters work on their own (from command line)... I just don't see any interface between them and pidgin.

---

### Post by kevdog on 2009-02-10
I'm not sure if you installed them like I told you.  You should have

/usr/local/lib/pidgin/talkfilters.la
/usr/local/lib/pidgin/talkfilters.so

Something tells me they were not compiled and installed with the rest of the plugins.

---

### Post by xX-Felipao-Xx on 2009-02-11
I like pidgin's style, but I'm waiting it to get a Plus! like plugin.
Any news about it, or its dead? 
The fact is that most of my contacts have those strange coloured nicks that look ugly without the plugin :S

---

### Post by kevdog on 2009-02-12
Can you inform me about the plugin you are referring to specifically and I'll investigate it?

---

### Post by Fir3chi3f on 2009-02-12
Anyone get this to compile on 64bit? 

I keep getting this:

```
checking for X11... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
configure: error:
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.



```

---

### Post by kevdog on 2009-02-12
> **Fir3chi3f said:**
> Anyone get this to compile on 64bit? 

I keep getting this:

```
checking for X11... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
configure: error:
XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.



```


Try this:
sudo aptitude install libxss-dev

---

### Post by Fir3chi3f on 2009-02-13
Thanks kevdog

After that was fixed got this:
```
checking for STARTUP_NOTIFICATION... no
no
configure: error:
Startup notification development headers not found.
Use --disable-startup-notification if you do not need it.

```

Fixed with libstartup-notification0-dev

Then got this:
```
checking for MEANWHILE... no
configure: error:
Meanwhile development headers not found.
Use --disable-meanwhile if you do not need meanwhile (Sametime) support.

```

edit: fixed with libmeanwhile-dev

Now stuck on: 
```
checking for MEANWHILE... yes
checking for AVAHI... no
checking avahi-client/client.h usability... no
checking avahi-client/client.h presence... no
checking for avahi-client/client.h... no
checking avahi-glib/glib-malloc.h usability... no
checking avahi-glib/glib-malloc.h presence... no
checking for avahi-glib/glib-malloc.h... no
checking for avahi_client_new in -lavahi-client... no
configure: error:
avahi development headers not found.
Use --disable-avahi if you do not need avahi (Bonjour) support.

```

fixed with libavahi-client-dev and libavahi-compat-libdnssd-dev

---

### Post by kevdog on 2009-02-13
Just a few questions and I can add info to the original post

I know you are installing on 64 bit Ubuntu

Did you do the following:
sudo apt-get build-dep pidgin

If you did, are you telling me you had to install additional libraries as listed above to compile on the 64 bit platform?

---

### Post by antony_css on 2009-02-20
After installation using checkinstall... The update daemon instantly turns on to notify a "new" version of pidgin is available, which is "1:2.4.1-ubuntu2.2". I think this is something about the version number.

I suggest to run this command instead:
> 
sudo checkinstall -D --fstrans=no --install=yes --pkgname=pidgin --pkgversion=**1:**2.5.4**~checkinstall**

Also, Bot Sentry cannot autogen itself. Here is the error encountered:
> $ ./autogen.sh
configure.ac:47: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:48: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
configure.ac:49: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1

I wonder what are they...

---

### Post by kevdog on 2009-02-20
I would recommend installing outside the apt system with a simple sudo make install rather than a checkinstall.  checkinstall although it has theoretical advantages, is really a pain to work with on a practical basis.  If you are persistent however in using the apt system, I believe you can put updates on hold like sudo aptitude hold pidgin.

As far as the bot sentry ./autogen.sh problem -- let me take a look at it.  I have bot sentry installed, however have not looked at the package in quite a while and don't know if a recent upgrade broke something.

---

### Post by rtom on 2009-02-21
I read about an oppurtunity to compile pidgin from source with video and voice support, so I wanted to try. This is how I proceed:

```
sudo apt-get install build-essential dh-make
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad libgstreamer-plugins-base0.10-dev
```

Installed packages from [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) (added to the sources)

```
sudo apt-get install libgstfarsight0.10-0 libgstfarsight0.10-dev gstreamer0.10-plugins-farsight 
```

in order to fetch the last revision of pidgin:

```
apt-get install monotone monotone-viz
```

then:

```
DATABASE=/home/user/monotone_databases/pidgin.mtn
WORKINGDIR=/home/user/code/pidgin-mtn
cd $(dirname $DATABASE)
wget http://developer.pidgin.im/static/pidgin.mtn.bz2
bzip2 -d pidgin.mtn.bz2
mtn -d $DATABASE pull --set-default mtn.pidgin.im "im.pidgin.*"
```

I got an error message so:

```
mtn -d $DATABASE db migrate
```

then again:

```
mtn -d $DATABASE pull --set-default mtn.pidgin.im "im.pidgin.*"
mtn -d $DATABASE co -b im.pidgin.pidgin.vv $WORKINGDIR
```

During configure with autogen I got messages about several missing dependencies, to install them:

```
sudo apt-get install autogen libtool intltool libgtk2.0-dev  libgtkspell-dev libstartup-notification0-dev libmeanwhile-dev libavahi-glib-dev libdbus-1-dev libperl-dev libssl-dev libgnutls-dev tcl8.5-dev libdbus-1-dev tk8.5-dev libxss-dev
```

What I couldn't frind:  d-bus and tk development headers so I disabled:

```
sudo sh ./autogen.sh --disable-dbus --disable-tk
```


Warning during configuring:
```
Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).
```


Error when "sudo make":
```
gtkmain.c:314: error: implicit declaration of function &#8216;pidgin_medias_init&#8217;
make[3]: *** [gtkmain.o] Error 1
make[3]: Leaving directory `/home/tom/code/pidgin-mtn/pidgin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tom/code/pidgin-mtn/pidgin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/code/pidgin-mtn'
make: *** [all] Error 2 
```

Any suggestion to avoid this?

---

### Post by kevdog on 2009-02-21
The voice and video support are experimental.  I would ask questions specifically on #pidgin IRC.  If however you find an answer I would be very interested in your solution.  I am not involved in pidgin development. Do you have a link to another page that provides tenative instructions?  I would be happy to try myself.

---

### Post by rtom on 2009-02-21
I used the following descriptions:
[GSoC2008]("http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo")
[Monotone for Pidgin]("http://developer.pidgin.im/wiki/UsingPidginMonotone")
[Install Pidgin from Source]("http://developer.pidgin.im/wiki/Installing%20Pidgin#Compiling")

If you gou through my earlier post, you can save a lot of time by installing the dev packages I listed there.

Any feedback would be appreciated.

---

### Post by kevdog on 2009-02-21
Voice and video seems to refer to developmental source code.  If you could tell me where to obtain this source code I would be greatful.

---

### Post by kevdog on 2009-02-21
How do I add that debian repository?

---

### Post by kevdog on 2009-02-22
Ok this Ive successfully compiled the source.  Here is how I did it: (Thanks for the instructions by the way -- very helpful. I using 8.10 on my system)

Did the following commands:
> 
```
sudo apt-get install build-essential dh-make
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad libgstreamer-plugins-base0.10-dev
```

I actually temporarily added the jaunty universe repository to my /etc/apt/sources.list and removed intrepid's.  I did a 
sudo aptitude update

Then ran the following commands:
> 
```
sudo apt-get install libgstfarsight0.10-0 libgstfarsight0.10-dev gstreamer0.10-plugins-farsight 
```

I then removed the jaunty repository, and added back in Intrepid's, and re-ran the update command.


The following instructions also worked, however I didn't install monotome-viz

> ```
apt-get install monotone monotone-viz
```

then:

```
DATABASE=/home/user/monotone_databases/pidgin.mtn
WORKINGDIR=/home/user/code/pidgin-mtn
cd $(dirname $DATABASE)
wget http://developer.pidgin.im/static/pidgin.mtn.bz2
bzip2 -d pidgin.mtn.bz2
mtn -d $DATABASE pull --set-default mtn.pidgin.im "im.pidgin.*"
```

I got an error message so:

```
mtn -d $DATABASE db migrate
```

then again:

```
mtn -d $DATABASE pull --set-default mtn.pidgin.im "im.pidgin.*"
mtn -d $DATABASE co -b im.pidgin.pidgin.vv $WORKINGDIR
```


During the configure process I did not get any errors about missing any dependencies.  Possibly this is because I had compiled pidgin before and had the library install.  I would suggest the following:

sudo apt-get build dep pidgin

> ```
sudo apt-get install autogen libtool intltool libgtk2.0-dev  libgtkspell-dev libstartup-notification0-dev libmeanwhile-dev libavahi-glib-dev libdbus-1-dev libperl-dev libssl-dev libgnutls-dev tcl8.5-dev libdbus-1-dev tk8.5-dev libxss-dev
```


I didn't need to do the following -- Again I think because I had the correct libraries installed.  A quick perusal of the config.log located in the top pidgin directory should tell you why you needed to do this:
> 
```
sudo sh ./autogen.sh --disable-dbus --disable-tk
```


I also got the following warnings listed below! I have no idea how to rectify, however they were just warnings!!

> Warning during configuring:
```
Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).
```


I didn't get the following when using the make command:
> 
Error when "sudo make":
```
gtkmain.c:314: error: implicit declaration of function ‘pidgin_medias_init’
make[3]: *** [gtkmain.o] Error 1
make[3]: Leaving directory `/home/tom/code/pidgin-mtn/pidgin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tom/code/pidgin-mtn/pidgin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/code/pidgin-mtn'
make: *** [all] Error 2 
```

---

### Post by rtom on 2009-02-22
> sudo apt-get build dep pidgin

Thanx for your feedback, using this I could also run the configure script without disable d-bus and tk support. However, at the end I receive 
```
Build with voice and video.... no
``` which should be yes...:-(

Update: I downloaded farsight2 and compiled it from source, so now I have the configure script with voice and video ... yes!

Update2: make and make install was successful, but when I try to run pidgin I got an error message:
"pidgin: symbol lookup error: pidgin: undefined symbol: purple_media_manager_get"

Update3: I upgraded all gstreamer- packages from the jaunty repo (thanx for the hint kevdog!) and recompiled. SUCCEED! Now I have Pidgin working with webcam (using Linux4Video2), need to test audio.

---

### Post by Jackelope King on 2009-02-23
I followed your instructions for compiling the Pidgin Facebook chat from source (in addition to trying it from repositories and via the .deb file) to no avail. When I go to "Manage Accounts" the dropbox simply does not have Facebook Chat as an option for creating an account. I had this working a few weeks ago for the space of a few hours before Pidgin crashed and Facebook Chat refused to work again. I've since reinstalled facebook chat numerous times (including by your method above) to no avail.

---

### Post by kevdog on 2009-02-24
rtom

Will your pidgin vv install with with gchat?

---

### Post by rtom on 2009-02-26
I gave up trying pidgin vv from source, I compiled it twice and both times the system collapsed after a while, and I couldn't recover (in recovery mode I uninstalled pidgin but the gdm not started at all).
So I reinstalled Ubuntu 8.10 and stay on Pidgin delivered with the distro :-(

---

### Post by kevdog on 2009-02-26
Im not sure what you mean collapsed, but I'm sorry to hear about your ordeal.  My vv version is running ok, but I can't test with gchat

---

### Post by rtom on 2009-02-27
> **kevdog said:**
> Im not sure what you mean collapsed, but I'm sorry to hear about your ordeal.  My vv version is running ok, but I can't test with gchat

You're lucky :p Does video and/or voice work?

On my PC booting process was busy before logging in, I switched off after 5 mins. That was the first boot after installing pidgin vv. Then I reinstalled and formatted the /home partition as well, recompiled pidgin vv, and then when normal booting I had only the blinking cursor. In recovery mode I uninstalled pidgin, but no improvement. I reinstalled the OS without formatting the /home partition and now also GRUB failed... :-k Next time I will boot a liveCD and try to check the system logs.

---

### Post by kevdog on 2009-02-27
I havent been able to test voice or video yet, however from your description, it would be hard to pin all those problems on just a pidgin vv installation.

---

### Post by rtom on 2009-03-02
> **kevdog said:**
> it would be hard to pin all those problems on just a pidgin vv installation.

You're right, it seems I'm facing problems with the HDD, in some cases it's not booting at all, after a fresh install...:mad:

---

### Post by kevdog on 2009-03-02
Lets talk again once you get the situation with your hardware solved :)

---

### Post by Fir3chi3f on 2009-03-04
> **kevdog said:**
> Just a few questions and I can add info to the original post

I know you are installing on 64 bit Ubuntu

Did you do the following:
sudo apt-get build-dep pidgin

If you did, are you telling me you had to install additional libraries as listed above to compile on the 64 bit platform?

Sorry, haven't had time to play with the laptop in a while. 
I believe that I already had build-dep pidgin install, I'll retest to make sure. 

Just to be safe, can anyone else confirm this on 64?

---

### Post by Fir3chi3f on 2009-03-04
UNCONFIRMED

I removed the additional packages mentioned earlier and reinstalled build-dep pidgin

Then make installed the latest version of Pidgin 2.5.5
Unless someone else confirms it, 64 works great and does NOT need additional packages. 

Works great so far, thanks for the tut by the way.

---

### Post by kevdog on 2009-03-04
Thanks for input -- I'll add that the instructions are also for 64 bit builds

---

### Post by =CrAzYG33K= on 2009-03-06
Any specific info for Pidgin 2.5.5 ??
I'm not getting the new one to work now :(

EDIT: Never mind .. Got 2.5.5 working in Intrepid :D

---

### Post by stesind on 2009-03-06
Hi,

yesterday I compiled 2.5.5 and I have to say it worths. This version is not that buggy as the official Ubuntu Intrepid one. 

Today I compiled and tested the current mtn version 2.6dev with video support. Result: gtalk audio calls work. Webcam works also, but a video call was not possible to establish. The windows appear but there is no transmitted video, just audio. 

Video for Yahoo was not supported. Maybe this is because I only took the faresight libaries from medibuntu. And with the latest it works.

Hope this will come in version 2.6 soon and thanks for the great work to the pidgin team! 

Bye from Berlin

---

### Post by kevdog on 2009-03-06
Just a few followup points

Im glad you tested gtalk -- since I never tested it.  From my conversations with the developers, only audio right now is supported and not video.  That means there was no error with your compilation or settings.

From my knowledge video at a minimum is not supported until the 3.0 release, and since right now we are only at 2.5.5, its going to be awhile.

As far as the yahoo video, the actual video implementation is controlled by the farsight library package: [http://farsight.freedesktop.org/wiki/](http://farsight.freedesktop.org/wiki/)
In order to allow for yahoo video, the base package must be compiled with the YahooWebCam Plugin.  Due to library dependency issues, I could not compile libfarsight/YahooWebCam Plugin with the base libraries contained within the intrepid universe repositories.  Dependency issues may be solved with the jaunty libraries or by using another distro such as Arch that is a rolling release.  I'd be curious if you are using Jaunty, if you could compile farsight with the YahooPlugin.  By compiling from source, this would basically eliminate the part of the developmental instructions:

sudo apt-get install libgstfarsight0.10-0 libgstfarsight0.10-dev

---

### Post by ninja senses on 2009-04-08
can someone send me the .so of the Pidgin Status History Logging Plugin??


i havent been able to make it compile

---

### Post by Good Zombie on 2009-04-11
I followed your guide and install pidgin and it was GOOD. but now I have to uninstall pidgin. I do not know how to uninstall it, it is not showing up in Synaptic, is that supposed to happen?

---

### Post by kevdog on 2009-04-11
If it was GOOD why do you want to uninstall it?

Ok, how do you install it, with checkinstall or sudo make install?

---

### Post by Good Zombie on 2009-04-11
I need to uninstall it because I am using other chat programs. I used "sudo make install".

---

### Post by kevdog on 2009-04-12
Ok, for the main program to uninstall, you need to go into the directory where the sources are located (or where you basically typed sudo make install), and type:

sudo make uninstall

If you installed any additional plugins, you must do the same for each source tree you compiled.

---

### Post by Good Zombie on 2009-04-13
Thank you.

---

### Post by Gourgi on 2009-05-12
i want to install switchspell plugin but configure option doesn't seem to work :(
i tried the 'touch' method in the first post and i also tried both 
```
./configure --prefix=/usr --with-plugins=switchspell
```
and 
```
./configure --prefix=/usr --with-plugins=all
```
but none of them work :(
in the report at the end of configure (=all) i get this:
> Purple plugins to be built.......:
  Autoreply, bash.org, Colorize, DeWYSIWYGification, Dice, Magic 8 Ball
  Find IP, Coin Flip, Google, Group IM, Highlight, Ignore, IRC Helper
  List Handler, Napster, Old Logger, Show Offline, SIM-fix, /exec, SNPP
  Message Splitter, SSL Info

where is switchspell ???

i also asked at #guifications but noone seems to care about user problems there ...

---

### Post by kevdog on 2009-05-15
Do you have the source for switchspell?  Have you tried to manually enter the switchspell directory and run the configure statement from this directory?

---

### Post by Gourgi on 2009-05-15
> **kevdog said:**
> Do you have the source for switchspell?  Have you tried to manually enter the switchspell directory and run the configure statement from this directory?
the source is in the plugin-pack.
```

$ ls -la switchspell/
-rw-r--r--  1 gourgi gourgi   655 2008-12-10 05:30 Makefile.am
-rw-r--r--  1 gourgi gourgi 19616 2008-12-26 07:46 Makefile.in
-rw-r--r--  1 gourgi gourgi   446 2007-12-03 01:47 Makefile.mingw
-rw-r--r--  1 gourgi gourgi   333 2008-12-10 05:43 plugins.cfg
-rw-r--r--  1 gourgi gourgi 10843 2009-05-15 21:56 switchspell.c

```

this are the files in the switchspell directory 
i can't run configure or make there.
i wonder if the others that followed this guide have this plugin installed?

---

### Post by kevdog on 2009-05-15
Gourgi

Give me about a day.  I just moved, so my ubuntu box is temporarily in a box somewhere.  I'm fairly certain I have this plugin compiled but I would have to check.  What version of the plugin pack are you using?

---

### Post by Gourgi on 2009-05-15
> **kevdog said:**
> Gourgi

Give me about a day.  I just moved, so my ubuntu box is temporarily in a box somewhere.  I'm fairly certain I have this plugin compiled but I would have to check.  What version of the plugin pack are you using?

this is the version [http://plugins.guifications.org/trac/downloads/22](http://plugins.guifications.org/trac/downloads/22)
it is the same as in the first post.

---

### Post by Gourgi on 2009-05-27
@kevdog:
any news about the plugin ?

---

### Post by kevdog on 2009-05-27
sorry not yet, things have been quite hectic at work.  Playtime has been limited.

---

### Post by Gourgi on 2009-05-28
i've found this PPA and now i'm able to use the switchspell plugin
[https://launchpad.net/~andrikos/+archive/ppa](https://launchpad.net/~andrikos/+archive/ppa)

---

### Post by kevdog on 2009-05-29
If you write exactly how you installed the switchspell plugin from the PPA, I'll add it to the original guide

Thanks.

---

### Post by Gourgi on 2009-05-29
i added this ppa to my sources.lst
```
deb http://ppa.launchpad.net/andrikos/ppa/ubuntu jaunty main
```
and i then installed the ***purple-plugin-pack*** package
the switchspell plugin is in that package

your pidgin package will be updated too..
also to use the switchspell you need to install aspell for your language
```
sudo apt-get install aspell-el
``` gives me greek spelling

---

### Post by autigers on 2009-07-06
I have followed the directions and the comments back and forth but am still having trouble getting the Farsight2 multicast plugin to work with Pidgin.  My problem is that the Plugin does not show up in Pidgin's list of plugins even though everything seemed to build correctly.

 I have compiled Pidgin 2.6.0vv from source as well as the Farsight2 package and gst-plugin-farsight. The following three files were built successfully into /usr/local/lib/farsight2-0.0: libmulticast-transmitter.a, -.la, -.so. I have tried moving these to /usr/local/lib/pidgin as a farshot with no success.

I installed the libpurple plugins and those do show up so I am trying to figure out what I am missing to get the multicast transmitter working. Any help would be very much appreciated.

---

### Post by kevdog on 2009-07-06
Please give me more details about this plugin since Im unfamilar with it and have never heard about it until now!

---

### Post by autigers on 2009-07-07
> **kevdog said:**
> Please give me more details about this plugin since Im unfamilar with it and have never heard about it until now!

Thanks for the quick reply, Kev.

Farsight2 is a video communications framework that supposedly can plugin to Pidgin.  I am not interested in the A/V comm however, I am trying to use the multicast UDP transmitter plugin they have bundled with it.  "Farsight2 has rawudp, iceudp, and multicast transmitter plugins" for Pidgin (2nd link below). 

The following site has a description of the entire Farsight project and just a snippet about the Multicast transmitter:
[http://farsight.freedesktop.org/wiki/](http://farsight.freedesktop.org/wiki/)

I have compiled Pidgin and when I configured it, I did get the "Build with Voice and Video... Yes" described here:
[http://developer.pidgin.im/wiki/vv](http://developer.pidgin.im/wiki/vv)

However, I do not have any of the Farsight2 plugins showing up in the list in Pidgin. Is there a way to link Plugins to Pidgin or should they just have to be compiled and placed in the /usr/local/lib/pidgin or ../farsight directory.

If there is another simpler implementation of a multicast UDP transmitter plugin anyone knows of, I'd love to know about it.

---

### Post by kevdog on 2009-07-07
I guess you are farther than me on this one.  I compiled the Pidgin vv experimental version successfully, however was never able to get either Farsight 1 or 2 compiled and installed sucessfully.  In fact I failed on the Yahoo, and MSN options.  I would try the IRC Pidgin channel.  The developers hang out there and if you mention something about vv they are more than likely to chime in and answer your questions.  I received a lot of help there when I had questions.

---

### Post by autigers on 2009-07-07
I will definitely go try the IRC channel.  Thanks for your help.  I'll post the solution back here if I get it figured out.

---

