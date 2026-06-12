---
title: "HOW To: Ardour with VST support (Hardy)."
date: 2008-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by sanus|art on 2008-05-20
[[COLOR=Red]**!**[/COLOR]] - This tutorial is for x86 32bit only.
This post is meant to create "step-by-step" HOW TO on compiling ardour 2+ with VST effects support. It was pretty much time-waister to follow all the dependencies, so nothing new here except the needed packages really - consider it as an plain time-saver.

**[COLOR=Red][!] For Jaunty[/COLOR]** (or ardour 2.8+):

Execute:
```
sudo apt-get built-dep ardour
```and continue from step [5]

**[COLOR=Red][!] For Hardy[/COLOR]**:

[**!**] - Ardour was released under GNU GENERAL PUBLIC LICENSE Version 2, vst sdk 2.3 are NOT - So here is a note from ardour developers regarding VST support:
[I]
You may not distribute binaries of Ardour with VST support. Doing so
is a violation of the license agreement for the Steinberg VST SDK. If
you are found to be distributing such binaries, you risk both
prosecution by Steinberg and public humiliation by me.

This is not my choice, and as soon as Steinberg change their
licensing, which they have indicated they will do, this policy (and
file) will be removed.
[/I]

**[1]** - Download the latest ardour-<VERSION>.tar.bz2 source from [[here]("http://ardour.org/source_downloads")] to yor desktop and extract it.

```

tar -xjvf ~/Desktop/ardour*.tar.bz2 -C ~/Desktop

```**[2]** - Download 'vst_sdk2_3.zip' (must be version _2.3_) from [www.steinberg.net]("http://www.steinberg.de/532+M52087573ab0.html")  or [here]("http://ygrabit.steinberg.de/%7Eygrabit/public_html/vstsdk/Download/VST%20Plug-Ins%20SDK%202.3/") (use the search function if the link is leading nowhere as Steinbergs are changing the location of this archive all the time) to your desktop and copy it 'as is' (without extracting) into 'ardour*/libs/fst/<HERE>':
```

cp ~/Desktop/vst_sdk2_3.zip ~/Desktop/ardour*/libs/fst/

```**[3]** - Install dependencies:
```

sudo apt-get install build-essential scons libtool pkg-config gettext libjack-dev libasound2-dev qjackctl libxml2-dev libsamplerate-dev libraptor-dev liblrdf-dev libgnomecanvas2-dev libboost-dev liblo-dev libglib-dev libgtkmm-dev libsndfile-dev wine wine-dev automake libfftw3-3 libfftw3-dev -y

```[**[COLOR=Red]![/COLOR]**] NOTE - If your ardour is 2.5 - You also need this as dependencies (thanks to [angelsguitar]("http://ubuntuforums.org/showpost.php?p=5441999&postcount=27") for pointing this out): 
```

sudo apt-get install aubio-tools libaubio-dev libaubio-doc libaubio2 pd-aubio python-aubio

```**[4]** - Get into ardour's source directory:
```

cd ~/Desktop/ardour*

```**[5]** - Configurations/makefile:
add 'VST=1'             - to enable VST support.
add 'FREESOUND=1'       - to enable the use of Freesound database lookup.
add 'LV2=1'             - to enable support of LV2 if slv2 is available. [Here]("http://ubuntuforums.org/showpost.php?p=5574524&postcount=31") is a bit about installation of all 'slv' related (tanks to motin)
add 'OLDFONTS=1'        - to compile with fonts as of ardour v.1 (fonts in v.2 sometimes get bigger than is has to be). 

I desided to compile mine with VST and FREESOUND.
```

scons VST=1 FREESOUND=1

```It takes about 5-10 minutes - make yourself a cup of coffee. If you have slow machine, it could get to 20 minutes very easy.

**[5.1]** - Build:
```

sudo scons install

```It takes about 5-10 minutes too - drink that cup of coffee while it's still hot.

**[6]** - The default VST folders locations are '/usr/local/lib/vst' and '/usr/lib/vst' (not exist - have to be created). You might want to create system link to one of those directories from your home '~/VST':
Create directory at '/usr/lib/vst':
```

sudo mkdir /usr/lib/vst

```Create directory at '~/vst':
```
mkdir ~/vst
```Create system link to '/usr/lib/vst' so you could add VST without being root.
```

sudo ln -s ~/vst /usr/lib/vst

```(You can set the path for VST plug-ins in '~/.bashrc' but I choose to not mess with variables.)
Now you can put your VST in '~/vst'.

**[7]** - To launch ardour use <ALT+F2> and type:
```

ardourvst

```or
create desktop icon/Launcher on your desktop:
```

gedit ~/Desktop/ArdourVST

```and add the lines bellow:
```

[Desktop Entry]
Encoding=UTF-8
Name=ArdourVST
Type=Application
Exec=ardourvst
Comment[en_US]=ardour
Comment=ardour
Icon=/usr/local/share/ardour2/icons/ardour_icon_48px.png

```That is it, I hope I did not forget/messed up anything. This is my first tutorial
:guitar:

---

### Post by dilandog on 2008-06-13
This file (vst_sdk2_3.zip) is impossible to find! ](*,)

---

### Post by sanus|art on 2008-06-14
> **dilandog said:**
> This file (vst_sdk2_3.zip) is impossible to find! ](*,)

Try [here]("http://www.steinberg.de/532+M52087573ab0.html"). Accept the license ...

---

### Post by dilandog on 2008-06-14
No, this link is dead end. Steinberg seems to regularly change the URL required to get the SDK, search on Steinberg site is dead end too. I tryed [ftp://steinberg.net](ftp://steinberg.net) -no luck.

---

### Post by sanus|art on 2008-06-14
> **dilandog said:**
> No, this link is dead end. Steinberg seems to regularly change the URL required to get the SDK, search on Steinberg site is dead end too. I tryed [ftp://steinberg.net](ftp://steinberg.net) -no luck.
I was able to download SDK for 3 times during our little chat here from the page in link of previous post, are you sure you can't? You need to accept the licence + fill your name and email and then they redirecting you to some random page with working link to VST SDK. Maybe you get blocked our something?

---

### Post by roaldz on 2008-06-14
What if I already have ardour installed? Can I have two copies of ardour at the same time? Or do I have to uninstall the repo version? I heard the VST support in ardour is a bit buggy.

---

### Post by sanus|art on 2008-06-14
> **roaldz said:**
> What if I already have ardour installed? Can I have two copies of ardour at the same time? Or do I have to uninstall the repo version? I heard the VST support in ardour is a bit buggy.
I think the version from the repositories will be overwritten. The VST in ardour a bit buggy - true, but from my experience - any wondows application is a bit buggy while handling VST, that is why we are trained so much with the "Ctrl+S".

---

### Post by cino on 2008-06-15
> **roaldz said:**
> What if I already have ardour installed? Can I have two copies of ardour at the same time? Or do I have to uninstall the repo version? I heard the VST support in ardour is a bit buggy.

From one beginner to another, I do not know but I have ardour already installed and am trying the above instructions now...

---

### Post by cino on 2008-06-15
@Sanus

hey, I am trying your instructions, but I am not very experienced...

step 5 has no code for me and I was wondering if you could explain to me what to do, in a little more detail. 

I now have ardour-2.4.1 on my desktop but am not sure how to do "these things" to the make file.

pls help.

cino

---

### Post by cino on 2008-06-15
omg -- never mind... **reads more carefully

---

### Post by cino on 2008-06-16
if anyone is out there,

scons: Reading SConscript files ...
Are you building Ardour for personal use (rather than distribution to others)? [no]: yes
OK, VST support will be enabled
IOError: [Errno 13] Permission denied: 'config.log':
  File "/home/james/Desktop/ardour-2.4.1/SConstruct", line 479:
    'CheckPKGVersion' : CheckPKGVersion })
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 552:
    return apply(SCons.SConf.SConf, args, kw)
  File "/usr/lib/scons/SCons/SConf.py", line 835:
    return apply(SConfBase, args, kw)
  File "/usr/lib/scons/SCons/SConf.py", line 419:
    self._startup()
  File "/usr/lib/scons/SCons/SConf.py", line 655:
    fp = open(str(self.logfile), log_mode)

Furthermore, 
ardour said it compiled but when I try to run it, I am told:

Error. Details: Failed to execute child process "ardourvst" (No such file or directory)

---

### Post by sanus|art on 2008-06-16
> **cino said:**
> if anyone is out there,

scons: Reading SConscript files ...
Are you building Ardour for personal use (rather than distribution to others)? [no]: yes
OK, VST support will be enabled
IOError: [Errno 13] Permission denied: 'config.log':
  File "/home/james/Desktop/ardour-2.4.1/SConstruct", line 479:
    'CheckPKGVersion' : CheckPKGVersion })
  File "/usr/lib/scons/SCons/Script/SConscript.py", line 552:
    return apply(SCons.SConf.SConf, args, kw)
  File "/usr/lib/scons/SCons/SConf.py", line 835:
    return apply(SConfBase, args, kw)
  File "/usr/lib/scons/SCons/SConf.py", line 419:
    self._startup()
  File "/usr/lib/scons/SCons/SConf.py", line 655:
    fp = open(str(self.logfile), log_mode)

Furthermore, 
ardour said it compiled but when I try to run it, I am told:

Error. Details: Failed to execute child process "ardourvst" (No such file or directory)

It seems like your 'SConstruct' is messed
or 
You executed "scons install" without "sudo"
or
The dependencies are not installed completely.

Is it any of those?

---

### Post by LitusMayol on 2008-07-01
Hi!

I'm having some problems with the processes:

```
Are you building Ardour for personal use (rather than distribution to others)? [no]: yes
OK, VST support will be enabled
Checking for pkg-config version >= 0.8.0... yes
Checking for gthread-2.0... no
gthread-2.0 >= 2.10.1 not found.
You do not have the necessary dependencies required to build ardour
Please consult http://ardour.org/building for more information
litus@UbuntuStuio:~/Escriptori/ardour-2.4.1$ 
```

I haven't found how to install or download this "*gthread*". Can anyone help me?

Thanks in advance!

---

### Post by sanus|art on 2008-07-01
Did you installed the dependencies as of the first post?
gthread is a part of libglib as far as I know - so you need the dev package:
```
sudo aptitude install libglib1.2-dev
```

---

### Post by LitusMayol on 2008-07-02
Done! 

I've used *apt-get* and I could install nothing, but using *aptitude* everything is installed except the "*build-essential*" package.

It gives me this error:
```
Media Change: Please insert the disc labeled 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)' in the drive '/cdrom/' and press [Enter].

```

I'm not usind any CD, so I don't understand. Moreover, if I tray to continue without this package this error is given:
```
litus@UbuntuStuio:~$ scons VST=1 FREESOUND=1
scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 825, in _main
litus@UbuntuStuio:~$ 

```

Thanks again!

---

### Post by sanus|art on 2008-07-02
The *build-essential* package is not installed by default - you need to insert the "Hardy" CD to install it.

So did you managed to compile or not? As I see you started the post with the "Done!" thing, but I see you also have *scons* error?
The error is because you're supposed to execute "scons VST=1 FREESOUND=1" in the ardour's source directory.

---

### Post by LitusMayol on 2008-07-02
OK!
Here I go again! 

I didn't know that about the *build-essential*, thanks man. I've installed it allright. 

But the "*scons*" order stills giving me an error:
```
litus@UbuntuStuio:~$ cd /home/litus/Escriptori/ardour-2.4.1/
litus@UbuntuStuio:~/Escriptori/ardour-2.4.1$ scons VST=1 FREESOUND=1scons: Reading SConscript files ...
Enabling VST support. Note that distributing a VST-enabled ardour
is a violation of several different licences.
Build with VST=false if you intend to distribute ardour to others.
Checking for pkg-config version >= 0.8.0... yes
Checking for gthread-2.0... yes
Checking for lrdf... no
lrdf >= 0.4.0 not found.
You do not have the necessary dependencies required to build ardour
Please consult http://ardour.org/building for more information
litus@UbuntuStuio:~/Escriptori/ardour-2.4.1$ 

```

Any idea?

Thanks again!!


PS: the "*done*" in the oder post was a way to say "I've done what you told me" ;)

---

### Post by sanus|art on 2008-07-03
Hi, You're probably out of certain dependencies run the
```
 sudo aptitude install build-essential scons libtool pkg-config gettext libjack-dev libasound2-dev qjackctl libxml2-dev libsamplerate-dev libraptor-dev liblrdf-dev libgnomecanvas2-dev libboost-dev liblo-dev libglib-dev libgtkmm-dev libsndfile-dev wine wine-dev automake libfftw3-3 libfftw3-dev -y
```liblrdf-dev is what you missing in this case.

---

### Post by LitusMayol on 2008-07-03
Thanks again! 

Ok. I've installed them. But I've another problem (sorry if I'm bothering...). I'm not able to find the package "*vst_sdk_2.3.zip*". Just impossible. I've been surfing *steinberg* web and *google*-ing out there and the only thing I've find out is "*dvstsdk_2.4.2.1.zip*".

I've tried to go on with it but the terminal don't recognize it because it's looking for the "*vst_sdk_2.3.zip*". There's any way to use the package I've got? Or maybe better, do you now where I can find the "*vst_sdk_2.3.zip*"? 


Thanks dude! You're having a lot of patience thanks!


(PS: good web *[http://www.sanusart.com/fx.php](http://www.sanusart.com/fx.php)*)

---

### Post by sanus|art on 2008-07-03
Hi, 

Patience?
We came here to help and to get helped - so patience is not for this kind of place.

I've found the sdk page [here]("http://www.steinberg.net/en/company/3rd_party_developer/steinberg_developer_information/steinberg_licensing_aggreement.html") right now.

Please do stop "thanking" me after every post.
Thanks
:guitar:

---

### Post by LitusMayol on 2008-07-03
Hi again!

I've a problem with [this]("http://www.steinberg.net/en/company/3rd_party_developer/steinberg_developer_information/steinberg_licensing_aggreement.html") web you have given me. I click on "*I AGREE (download version 2.3)*" and it moves to [this]("http://www.steinberg.net/en/company/3rd_party_developer/steinberg_developer_information/steinberg_licensing_aggreement/download_licensing_agreement.html") page where nothing happens...

:S  Do you know why?


ok, I won't thank you any more! ;)

---

### Post by sanus|art on 2008-07-03
> **LitusMayol said:**
> Hi again!

I've a problem with [this]("http://www.steinberg.net/en/company/3rd_party_developer/steinberg_developer_information/steinberg_licensing_aggreement.html") web you have given me. I click on "*I AGREE (download version 2.3)*" and it moves to [this]("http://www.steinberg.net/en/company/3rd_party_developer/steinberg_developer_information/steinberg_licensing_aggreement/download_licensing_agreement.html") page where nothing happens...

:S  Do you know why?


ok, I won't thank you any more! ;)
:)

I get this page too, strange - I they might be changing the location of the files and did not uploaded them yet.

---

### Post by LitusMayol on 2008-07-03
> **sanus|art said:**
> :)
I get this page too, strange - I they might be changing the location of the files and did not uploaded them yet.

Oh... 

So... There is no way to get it? I can't continue without it. Do you have it and can pass it on? Or do you know how to?

Thanks man! 

(sorry I did it again! xD)

---

### Post by sanus|art on 2008-07-05
Hi, I'm really sorry - but I could not find it ether. I hope they'll put it back as It is the only way to VST support in Linux.

---

### Post by LitusMayol on 2008-07-07
Hi again!

I've done it!!!

I've got the *vstsdk2.3.zip* asking in the **ubuntuStudio**mail list.

More over a friend have founded this web that may help some others. [Here]("http://ygrabit.steinberg.de/~ygrabit/public_html/vstsdk/Download/VST%20Plug-Ins%20SDK%202.3/") you can download it.

Thanks for everything.

---

### Post by sanus|art on 2008-07-08
Great, I'll update the link in how to.
:)

---

### Post by angelsguitar on 2008-07-23
Hi.

Just wanted to comment that, while compiling ardour 2.5 on UbuntuStudio 8.04-1, it gave an error about a missing dependency: aubio.  So had to install the packages aubio-tools, libaubio-dev, libaubio-doc, libaubio2, pd-aubio, and python-aubio.  See the following info on aubio and its packages:

[http://packages.ubuntu.com/source/hardy/aubio]("http://packages.ubuntu.com/source/hardy/aubio")

After that, it compiled without errors..now let's see if I can install without errors...

Anyway, just wanted to let you know this, in case it's useful to someone.

---

### Post by angelsguitar on 2008-07-23
Well, it compiled and installed without problems.

---

### Post by sanus|art on 2008-07-23
Thanks for the tip - I've updated the first post.

---

### Post by zirbs on 2008-08-05
Hey - I just wanted to say thanks for making this guide as it helped me out greatly.  Went off without a hitch!

---

### Post by motin on 2008-08-12
Thanks man!

Here are some additions:

**LV2 Support**
In order to be able to use LV2=1 you need the following:
Add SLV repository as per instructions on [http://wiki.drobilla.net/Debian](http://wiki.drobilla.net/Debian) and then install:
```
sudo apt-get install slv2 slv2-9-dev slv2-dev lv2core
```

**Uninstallation possibility**
Build+Install with uninstallation support (instead of just "sudo scons install"):
```
sudo apt-get install checkinstall
sudo checkinstall scons install
```
When prompted to approve the package details, be sure to change the version from "2.5" to "1:2.5.0" (or Ubuntu will think replace it with the Repo-version upon next upgrade...)

---

### Post by BlackCat13 on 2008-08-20
Excellent tutorial... worked like a charm...
Cheers

---

### Post by sanus|art on 2008-08-20
Tanks motin, added to the first post.

---

### Post by noctrex on 2008-10-03
First of all thanks for the nice tutorial, followed all the steps, but when compiling, with the options mentioned (scons VST=1 FREESOUND=1) after about 2-3 minutes of some miles of scrolling the compiling aborted :(

libs/ardour/vst_plugin.cc: In member function ‘virtual std::string ARDOUR::VSTPlugin::unique_id() const’:
libs/ardour/vst_plugin.cc:415: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
libs/ardour/vst_plugin.cc:415: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long int’
libs/ardour/vst_plugin.cc: In member function ‘virtual ARDOUR::PluginPtr ARDOUR::VSTPluginInfo::load(ARDOUR::Session&)’:
libs/ardour/vst_plugin.cc:485: error: cast from ‘FSTHandle*’ to ‘int’ loses precision
scons: *** [libs/ardour/vst_plugin.os] Error 1
scons: building terminated because of errors.


has anyone experienced an error like this?
any advice is appreciated...

FYI, I got version ardour-2.5. (and of course vstsdk2.3.zip)

---

### Post by sanus|art on 2008-10-04
Hi noctrex,

I just did a complete follow-up on the tutorial on a "fresh" laptop with ardour2.5 sources and all went well. 
Your error sad that there are no numbers where they are supposed to be in the source files of ardour, I don't know C/C++ so nothing to add about this error.

I'll advise you to start over with the tutorial to see what happens.

---

### Post by noctrex on 2008-10-06
OK, my bad...
apparently I was trying to compile ArdourVST on my 64bit Kubuntu Hardy system.
All nice and well, except that the VST SDK is for 32bit systems only :(

from Ardour site: ([http://ardour.org/building_vst_support]("http://ardour.org/building_vst_support"))

> This section applies only to people building Ardour 2.0 (not 0.99.X) and only for Linux/x86 platforms. At this time, you cannot run VST plugins in Ardour on OS X or Linux x86_64 platforms.

So, no nope for us 64bit users...

---

### Post by sanus|art on 2008-10-06
I guess I should state this 32bit only thing in the tutorial. Thanks.

---

### Post by deadly_sinn on 2008-11-03
ok so i am running on 64bit..8.10 gonna install 8.4 instead since it is not so buggy..i have no internet connection at home due to some issues with 8.10...so if i were to run 8.10 32bit and since i would already have ardour and dependencies installed, if i repackaged would i still need to be able to access the repositories to dl the dependencies?

---

### Post by sanus|art on 2008-11-03
> **deadly_sinn said:**
> ok so i am running on 64bit..8.10 gonna install 8.4 instead since it is not so buggy..i have no internet connection at home due to some issues with 8.10...so if i were to run 8.10 32bit and since i would already have ardour and dependencies installed, if i repackaged would i still need to be able to access the repositories to dl the dependencies?

As far as I know packages are NOT get removed from the repositories with version upgrade of ubuntu. They might be updated to newer versions though. I yet did not tried to install ardour on 8.10 32bit, but it should work.

---

### Post by brandjamie on 2008-12-05
Used this how to before on hardy and it worked perfectly. Trying it now with Ibex. 

      "LV2 Support
      In order to be able to use LV2=1 you need the following:
      Add SLV repository as per instructions on [http://wiki.drobilla.net](http://wiki.drobilla.net)  /Debian and then install:"

At present that link isn't working. Eventually found the debian repository here: [URL="http://download.drobilla.net/debian"]

installing slv2 from this repository doesn't seem to work though. i mean, synaptic says slv2 slv2-9 and the relevant dev files are installed (version 0.6.0) but when i run scons LV2=1  it gives me the error message

LV2 support is not enabled (SLV2 not found or older than version 0.6.0). 

any ideas anyone?

---

### Post by sanus|art on 2008-12-05
Try to add repository of [http://archive.ematech.fr/](http://archive.ematech.fr/) to /etc/apt/sourses.list
```

deb http://archive.ematech.fr intrepid all
deb-src http://archive.ematech.fr intrepid all

```And GPG key:
```

wget -q http://archive.ematech.fr/ematech.gpg -O- | sudo apt-key add -

```and install:
```

sudo aptitude install libslv2-utils libslv2-9 libslv2-dev libslv2-doc libslv2-9-dbg 
lv2core 
```

---

### Post by oleksus on 2009-02-05
Well, I'm trying to install a new version of Ardour with scons, and here's what it says in the end.

```
In file included from libs/vamp-plugins/plugins.cpp:44:
libs/vamp-plugins/Onset.h:56: error: ISO C++ forbids declaration of ‘fvec_t’ with no type
libs/vamp-plugins/Onset.h:56: error: expected ‘;’ before ‘*’ token
libs/vamp-plugins/Onset.h:57: error: ISO C++ forbids declaration of ‘cvec_t’ with no type
libs/vamp-plugins/Onset.h:57: error: expected ‘;’ before ‘*’ token
libs/vamp-plugins/Onset.h:58: error: ISO C++ forbids declaration of ‘fvec_t’ with no type
libs/vamp-plugins/Onset.h:58: error: expected ‘;’ before ‘*’ token
libs/vamp-plugins/Onset.h:59: error: ISO C++ forbids declaration of ‘aubio_pvoc_t’ with no type
libs/vamp-plugins/Onset.h:59: error: expected ‘;’ before ‘*’ token
libs/vamp-plugins/Onset.h:60: error: ISO C++ forbids declaration of ‘aubio_pickpeak_t’ with no type
libs/vamp-plugins/Onset.h:60: error: expected ‘;’ before ‘*’ token
libs/vamp-plugins/Onset.h:61: error: ISO C++ forbids declaration of ‘aubio_onsetdetection_t’ with no type
libs/vamp-plugins/Onset.h:61: error: expected ‘;’ before ‘*’ token
libs/vamp-plugins/Onset.h:62: error: ‘aubio_onsetdetection_type’ does not name a type
scons: *** [libs/vamp-plugins/plugins.os] Error 1
scons: building terminated because of errors.

```

What are the vamp-plugins and how do I fix them good?

---

### Post by sanus|art on 2009-02-05
I am not sure, as I've never seen this before - but "[vamp-plugins]("http://vamp-plugins.org")" are parts of some audio analyses systems.  

You might be short of this packages: 
[http://packages.debian.org/unstable/sound/vamp-plugin-sdk](http://packages.debian.org/unstable/sound/vamp-plugin-sdk)

---

### Post by oleksus on 2009-02-05
Well, I installed those packages, but when I try to install ardour again it says
```
WARNING: some VAMP plugins will not be built because this machine has no AUBIO support

```
and then the same errors I posted before.

What is this AUBIO support, anyway? I have previous version of ardour working on my machine.

EDIT: Well, guess what, I downloaded and installed that AUBIO, but STILL the ardour installation stops at the same thing!

---

### Post by mkloch on 2009-03-05
> **oleksus said:**
> Well, I installed those packages, but when I try to install ardour again it says
```
WARNING: some VAMP plugins will not be built because this machine has no AUBIO support

```
and then the same errors I posted before.

What is this AUBIO support, anyway? I have previous version of ardour working on my machine.

EDIT: Well, guess what, I downloaded and installed that AUBIO, but STILL the ardour installation stops at the same thing!

Hi! I am getting the same message, did you manage to find a way to fix it? I was trying to install AUBIO via synaptic, from source and even older versions, nothing worked so far :(

---

### Post by sanus|art on 2009-03-05
Ok I just have compiled it strait as in the first post - had no troubles at all (Ubuntu Intrepid - 8.10).
Try to run 'sudo apt-get build-dep ardour' before the 'scons VST=1'.

---

### Post by Ozzman on 2009-11-16
hopefully this will help someone in the future..

1. its build-dep not built-dep

2. if you decide not to go through with it and want to remove the 400+mb of files this command helped me

```
sudo aptitude markauto $(apt-cache showsrc ardour | grep Build-Depends | perl -p -e 's/(?:[\[(].+?[\])]|Build-Depends:|,|\|)//g')
```

thanks

---

### Post by jack.herbert on 2010-03-23
@oleksus
I had the same problem, installed the "aubio" business from step 3 in the original post and TADA! compile went passed the vamp-plugin stuff.
Hooray for now!

edit: just read your second post. Did you install all the aubio stuff?

---

