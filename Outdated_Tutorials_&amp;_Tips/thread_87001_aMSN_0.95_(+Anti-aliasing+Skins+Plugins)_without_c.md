---
title: "aMSN 0.95 (+Anti-aliasing+Skins+Plugins) without compiling"
date: 2005-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by NeTo on 2005-11-07
[SIZE="3"]**NOTE: This guide is for Breezy only! For Dapper, follow [thread=216689]this guide[/thread] instead.**[/SIZE]

I have created debian packages for aMSN 0.95 (final), Tcl/Tk 8.5a3, based on the packages for previous versions. This will let you install the most recent aMSN (as of the date of this thread) in breezy in a breeze.

[LIST]
[*]Tk is built with support for anti-aliased fonts, meaning that aMSN will look very nice.

[*]Furthermore, I have made two extra packages with tons of plugins and skins. The skins package has a even a skin matching the Ubuntu Human theme :KS
[/LIST]
I will first cover the aMSN installation, and then some customization tips.

I have only built i386 packages. For other architectures, you'll need (yup) to compile from sources. Hopefully, as everything is already debianized, that ain't that hard either (read the ''Building from Sources" below). If you build for other architectures, be sure to post the links here when possible, to add them to this post.

A last note: Some of these packages are hosted on my home PC, which is only online for a few hours a day with a slow net connection. So, if you're unable to download them, try again after a few hours.

**Contents**
1. Install Tcl/Tk, aMSN
2. Customization Tips[INDENT]2.1 Sound
2.2 Anti-aliased Fonts
2.3 Extra Skins and Plugins[/INDENT]3. Video/Audio Conference Support (Optional)  
4. Other packages[INDENT]4.1 Dev. files: tcl8.5-dev, tk8.5-dev
4.2 aMSN CVS snapshots (+Chameleon plugin)[/INDENT]
5. Building from Sources

You will get a fully functional aMSN installation just by following the steps at 1. Now, to the guide itself:

**1. Install Tcl/Tk, aMSN**

Although there is no need for compiling, you must still download and install the packages. So, open a terminal window an type:```
sudo apt-get install imlib11 sox libpng12-0 docker tcltls
```This will download all the required dependencies, mostly for aMSN.

After the packages are installed, type the following:
```
wget http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb
wget http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb
wget http://www.doeweling.com/files/ubuntu/amsn/amsn_0.95-1~neto1_i386.deb
```

After downloading, you'll end up with 3 .deb files. To install them run:```
sudo dpkg -i tcl8.5_8.5.0-1~neto3_i386.deb tk8.5_8.5.0-1~neto3_i386.deb amsn_0.95-1~neto1_i386.deb
```Finally (and just in case), you need to create some symlinks:```
cd /usr/lib
sudo ln -sf libtk8.5.so.0 libtk8.5.so
sudo ln -sf libtcl8.5.so.0 libtcl8.5.so
```And that's it! Now you are ready to use aMSN. Enjoy!


**2. Customization Tips**

*2.1 Sound*
[LIST]
[*]To enable sound in Ubuntu, run the following in a terminal:```
sudo apt-get install esound-clients
```Now, run aMSN and go to *Tools->Preferences*, select the *Others* tab, and head to the *Sound Server* option.

Make sure that *Use a different program* is selected, and type in the textbox below it: *esdplay $sound*

[*]To enable sound in Kubuntu, type the following instead: *artsplay $sound*
[/LIST]


*2.2 Anti-aliased Fonts*
If you followed the installation steps above, anti-aliased fonts work out of the box. Just go to *Fonts->Preferences->Appearance*, click on *Change Fonts*, and select a nice font/font size.


*2.3 Extra Skins and Plugins*
Several skins and plugins are already packaged for Ubuntu, and are just a few miles away (considering where I'm located ;)). Just open a terminal window and type:```
wget http://www.doeweling.com/files/ubuntu/amsn/amsn-plugins_0.95-1~neto1_i386.deb
wget http://www.doeweling.com/files/ubuntu/amsn/amsn-skins_0.95-1~neto1_i386.deb
```And to install them:```
sudo dpkg -i amsn-plugins_0.95-1~neto1_i386.deb amsn-skins_0.95-1~neto1_i386.deb
```Restart amsn and check *Tools->Skins* and *Tools->Plugins* to see what's included. 

Some notes on the plugins: 
[LIST]
[*]For *changeit* the required program [talk-filters](http://www.hyperrealm.com/main.php?s=talkfilters) is already included and installed in */usr/bin/amsn-plugins/changeit/*. You can check the contents of that folder to see what other filters are available besides *pirate* (the default).
[*]*gename* requieres fortune installed if I'm not mistaken, so remember to install *fortune-mod* if you want to use this plugin.
[*]*Say it* requieres [Festival](http://www.cstr.ed.ac.uk/projects/festival/) installed. I haven't tried it yet, but you should only need to run```
sudo apt-get install festival
``` if you want to use this plugin.
[/LIST]


**3. Video/Audio Conference Support (Optional)**

This aMSN version has built-in webcam support, so if your webcam works in programs like GnomeMeeting, you are ready to use it in aMSN. 

But MSN has also a Video/Audio Conference feature, which is not enabled in aMSN by default,as it will be implement using the libraries from the [Farsight Project](http://farsight.sourceforge.net/) in the future. 

Anyway, you can still enable Video/Audio Conference in aMSN (at your own risk) using the linphone-im libraries I compiled. To do so, you will need to uninstall Linphone if you have it installed, as these libraries replace the Linphone libs:```
sudo apt-get remove linphone liblinphone1 libortp0
```Then, you need to install some packages:```
sudo apt-get install libosip0
```The following step is to download linphone-im:```
wget http://netosoft.no-ip.org/Ubuntu/breezy/amsn/linphone-im_0.12.1-1~neto2_i386.deb
```and install it:```
sudo dpkg -i linphone-im_0.12.1-1~neto2_i386.deb
```The next time you start aMSN, Video/Audio Conference support will be enabled by default, and you need to take no further steps. To use it, as explained in the [aMSN wiki](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installing+Plugins+and+Skins#linphone):> Now you should be able to receive Audio conversations or Video conference invitations (NOT WEBCAM in MSN6, it's different). 
You can also issue invitations by: CTRL+S : 
MSNAV::inviteAV email@em... A <-- Audio conversation 
MSNAV::inviteAV email@em... AV <-- Video Conference (with audio)
I now the plugin loads and starts conferences correctly, but I haven't tested it yet. If it is broken beyond repair, or if you want to install the actual linphone, you can safely remove this package by issuing the command:```
sudo apt-get remove linphone-im
```aMSN will start as usual the next time you run it.


**4. Other packages**

*4.1 Dev. files: tcl8.5-dev, tk8.5-dev*

In case you need other packages, like tcl8.5-dev or tk8.5-dev, you can download them from *[http://netosoft.no-ip.org/Ubuntu/breezy/tcl-tk/](http://netosoft.no-ip.org/Ubuntu/breezy/tcl-tk/)*

For example, for tcl8.5-dev, you can type the following commands:```
wget http://netosoft.no-ip.org/Ubuntu/breezy/tcl-tk/tcl8.5-dev_8.5.0-1~neto3_i386.deb
sudo dpkg -i tcl8.5-dev_8.5.0-1~neto3_i386.deb
```

*4.2 aMSN CVS snapshots (+Chameleon plugin)*

Now and then, I will build packages from the aMSN CVS tree (it won't happen frequently though). You can get the packages with:```
wget http://netosoft.no-ip.org/Ubuntu/breezy/amsn/amsn_0.95+cvs20060408-1~neto1_i386.deb
wget http://netosoft.no-ip.org/Ubuntu/breezy/amsn/amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb
```And to install them:```
sudo apt-get install amsn_0.95+cvs20060408-1~neto1_i386.deb amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb
```
One new interesting feature is the [Chameleon plugin](http://amsn.sourceforge.net/forums/viewtopic.php?t=618), which changes the default Tcl/Tk controls with better looking ones.


**5. Building from Sources**

What a lengthy guide! Finally I reach the last part. If for some reason you need to re-compile any of this packages, you can download the sources from *[http://netosoft.no-ip.org/Ubuntu/breezy-sources/](http://netosoft.no-ip.org/Ubuntu/breezy-sources/)*.

The sources are in the *tcl-tk* and *amsn* subfolders, and have the debian naming scheme.

To compile a source file:
[LIST]
[*]Download the three files that make up the source. They have the *package.diff.gz*, *package.orig.tar.gz* and *package.dsc* naming scheme. For example, for tcl8.5 you can run:```
wget http://netosoft.no-ip.org/Ubuntu/breezy-sources/tcl-tk/tcl8.5_8.5.0-1~neto3.diff.gz
wget http://netosoft.no-ip.org/Ubuntu/breezy-sources/Sources/tcl-tk/tcl8.5_8.5.0.orig.tar.gz
wget http://netosoft.no-ip.org/Ubuntu/breezy-sources/Sources/tcl-tk/tcl8.5_8.5.0-1~neto3.dsc 
```[*]Extract the package. For the example above the command would be:```
dpkg-source -x tcl8.5_8.5.0-1~neto3.dsc
```[*]Install the build dependencies for your package. For example:```
cd *tcl8.5-8.5.0*
sudo apt-get build-dep amsn tcl8.4 tk8.4 linphone
sudo apt-get install libxft-dev
```You can remove any of the package names in the second line depending on what you're compiling. Notice I typed tcl8.4 and tk8.4, as those are the packages apt-get knows about, and share the same dependencies of tcl8.5 and tk8.5 (except for libxft-dev).
[*]Now, you can compile the package with: ```
dpkg-buildpackage -nc -uc -rsudo
```
[/LIST]

Finally, I can't end up this guide without showing how it looks like :D :

---

### Post by NeTo on 2005-11-07
PS: The one in that webcam shot is me, of course. I have had a though week, hence the hair loss.

---

### Post by Beire on 2005-11-07
```
/usr/bin/wish: error while loading shared libraries: libtk8.5.so: cannot open shared object file: No such file or directory

```

Seems to be something wrong with the symlinks

*EDIT: i uploaded the files to my personal webspace.

```

wget http://users.telenet.be/beires/tcl8.5_8.5.0-1neto~1_i386.deb
wget http://users.telenet.be/beires/tk8.5_8.5.0-1~neto1_i386.deb
wget http://users.telenet.be/beires/amsn_0.95-1neto~1_i386.deb

```

---

### Post by kashms on 2005-11-07
Is that supposed to be version 0.95 cvs and not 0.75?

aMSN must have gone through some nifty changes since it now supports video and audio chats with MSN messenger! But how stable is it since it is cvs?

---

### Post by neuschnee on 2005-11-07
[http://savefile.com](http://savefile.com) seems to work well enough for hosting files. I don't know if it's the best or anything, but it's what I found after a quick search when I needed to host a file to the public. No problems so far.

---

### Post by blakken on 2005-11-07
here is the error I got:
slayer@ubuntu:~/debian package$ sudo ln -sf  /usr/bin/tclsh8.5 /usr/bin/tclsh
slayer@ubuntu:~/debian package$ sudo ln -sf  /usr/bin/wish8.5 /usr/bin/wish
slayer@ubuntu:~/debian package$ amsn
/usr/bin/wish: error while loading shared libraries: libtk8.5.so: cannot open shared object file: No such file or directory
slayer@ubuntu:~/debian package$ amsn
/usr/bin/wish: error while loading shared libraries: libtk8.5.so: cannot open shared object file: No such file or directory
:confused:

---

### Post by jordz on 2005-11-07
I got the same problem :(

jordz@S260:~$ amsn
/usr/bin/wish: error while loading shared libraries: libtk8.5.so: cannot open shared object file: No such file or directory

---

### Post by kashms on 2005-11-07
I got the same error, and I fixed it by some symlinking:

```

cd /usr/lib
sudo ln -s libtk8.5.so.0 libtk8.5.so
sudo ln -s libtcl8.5.so.0 libtcl8.5.so

```

---

### Post by jordz on 2005-11-07
thx that worked for me :)

---

### Post by jamesshuang on 2005-11-07
I'm having problems with tcl/tk it seems, this is the error I'm getting:
```
/usr/bin/amsn: line 3: 13581 Segmentation fault      /usr/bin/wish amsn

```

Any ideas why it's doing this?

EDIT* - nevermind, seems that if I open /usr/bin/amsn, and change /usr/bin/wish to /usr/bin/wish8.5, this goes away.

---

### Post by NeTo on 2005-11-07
[QUOTE=kashms]Is that supposed to be version 0.95 cvs and not 0.75?

aMSN must have gone through some nifty changes since it now supports video and audio chats with MSN messenger! But how stable is it since it is cvs?[/QUOTE]

Sorry, it was 0.95; that's what happens when you write a guide at 4am :p. I have now edited the post with the correct version number :-\" I haven't tested it a lot, since I just compiled it this weekend, but looks very stable considering what has been added. But anyway, it's not only amsn which is CVS, both tcl8.5 and tk8.5 aren't yet stable releases, so even from a positive point of view, you should expect *something* to be broken.

Btw, I think I figured out what caused this symlinking problem. I am recompiling and will upload the .debs as soon as they finish. They won't need any symlinks anymore, as they will be automatically created.

---

### Post by NeTo on 2005-11-07
Done! I have updated the first post with links to the new packages. I forgot to rise the priority of *update-alternatives* in the postinst scripts for both tcl and tk, so Ubuntu kept 8.4 as the prefered version.

As that's now fixed, the symlinks problems should be gone. Furthermore, the packages should handle automatically the symlinks at install. I have updated the howto reflecting this.

Please, update with the new versions if you installed the previous ones. Sorry for any inconvenients.

---

### Post by cowlip on 2005-11-13
Hi, I think I had to make the symlinks still.  Anyways, thanks so much, I complained about the lack of new amsns before ;)

---

### Post by sal on 2005-11-13
[QUOTE=NeTo]I have created debian packages for aMSN 0.95 CVS, Tcl/Tk 8.5a3 and the Linphone plugin (plus the modified linphone), based on the packages for previous versions. This will let you install the most recent aMSN (as of the date of this thread) in breezy in a breeze.

Tk is built with support for anti-aliased fonts, meaning that aMSN will look very nice. Furthermore, the aMSN package has several plugins and extra skins, including one matching the Ubuntu Human theme :KS.

I will first cover the aMSN installation, and then some customization tips.

I have only built i386 packages. For other architectures, you'll need (yup) to compile from sources. Hopefully, as everything is already debianized, that ain't that hard either (read the ''Building from Sources" below). If you build for other architectures, be sure to post the links here when possible, to add them to this post.

**Contents**
1. Install Tcl/Tk, aMSN
2. Customization Tips
    2.1 Sound
    2.2 Anti-aliased Fonts
    2.3 Skins and plugins
3. Video/Audio Conference Support (Optional)  
4. Other packages
5. Building from Sources

You will get a fully functional aMSN installation just by following the steps at 1. Now, to the guide itself:

**1. Install Tcl/Tk, aMSN**

Although there is no need for compiling, you must still download and install the packages. So, open a terminal window an type:```
sudo apt-get install imlib1 sox libpng10-0 docker tcltls
```This will download all the required dependencies, mostly for aMSN.

After the packages are installed, type the following:
```
wget http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/tcl-tk/tcl8.5_8.5.0-1~neto2_i386.deb
wget http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/tcl-tk/tk8.5_8.5.0-1~neto2_i386.deb
wget http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/amsn/amsn_0.95-1~neto1_i386.deb
```Sadly, this packages are hosted on my home PC, which is only online for a few hours a day with a slow net connection. So, if you're unable to download them, try again after a few hours (Is there any charitable soul willing to host these?).

After downloading, you'll end up with 3 .deb files. To install them run:```
sudo dpkg -i tcl8.5_8.5.0-1~neto2_i386.deb tk8.5_8.5.0-1~neto2_i386.deb amsn_0.95-1~neto1_i386.deb
```And that's it! Now you are ready to use aMSN. Enjoy!


**2. Customization Tips**

*2.1 Sound*
To enable sound in Ubuntu, run the following in a terminal:```
sudo apt-get install esound-clients
```Now, run aMSN and go to *Tools->Preferences*, select the *Others* tab, and head to the *Sound Server* option.

Make sure that *Use a different program* is selected, and type in the textbox below it: *esdplay $sound*

To enable sound in Kubuntu, type the following instead: *artsplay $sound*


*2.2 Anti-aliased Fonts*
If you followed the installation steps above, anti-aliased fonts work out of the box. Just go to *Fonts->Preferences->Appearance*, click on *Change Fonts*, and select a nice font/font size.


*2.3 Skins and plugins*
The aMSN package includes several skins and plugins not present in the previous debian version. Check *Tools->Skins* and *Tools->Plugins* to see what's included. 

Some notes on the plugins: For *changeit* the required program [talk-filters](http://www.hyperrealm.com/main.php?s=talkfilters) is already included and installed in */usr/lib/amsn/plugins/changeit/*. You can check the contents of that folder to see what other filters are available besides *pirate* (the default).

*gename* requieres fortune installed if I'm not mistaken, so remember to install *fortune-mod* if you want to use this plugin.


**3. Video/Audio Conference Support (Optional)**

This aMSN version has built-in webcam support, so if your webcam works in programs like GnomeMeeting, you are ready to use it in aMSN. 

But MSN has also a Video/Audio Conference feature, which is not enabled in aMSN by default,as it will be implement using the libraries from the [Farsight Project](http://farsight.sourceforge.net/). 

Anyway, you can still enable Video/Audio Conference in aMSN (at your own risk) using the linphone-im libraries I compiled. To do so, you will need to uninstall Linphone if you have it installed, as this libraries replace the Linphone libs:```
sudo apt-get remove linphone liblinphone1
```Then, you need to install some packages:```
sudo apt-get install libosip0
```The following step is to download linphone-im:```
wget http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/amsn/linphone-im_0.12.1~neto1_i386.deb
```and install it:```
sudo dpkg -i linphone-im_0.12.1~neto1_i386.deb
```The next time you start aMSN, Video/Audio Conference support will be enabled by default, and you need to take no further steps. To use it, as explained in the [aMSN wiki](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installing+Plugins+and+Skins#linphone):
I now the plugin loads and starts conferences correctly, but I haven't tested it yet. If it is broken beyond repair, or if you want to install the actual linphone, you can safely remove it by issuing the command:```
sudo apt-get remove linphone-im
```aMSN will start as usual the next time you run it.


**4. Other packages**
In case you need other packages, like tcl8.5-dev or tk8.5-dev, you can download them from *[http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/tcl-tk/](http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/tcl-tk/)*

For example, for tcl8.5-dev, you can type the following commands:```
wget http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/tcl-tk/tcl8.5-dev_8.5.0-1~neto2_i386.deb
sudo dpkg -i tcl8.5-dev_8.5.0-1~neto2_i386.deb
```


**5. Building from Sources**

What a lengthy guide! Finally I reach the last part. If for some reason you need to re-compile any of this packages, you can download the sources from *[http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/Sources/](http://neto.no-ip.com:8080/Ubuntu%20-%20Breezy/Sources/)*.

The sources are in the *tcl-tk* and *amsn* subfolders, and have the *name-debian.tar.gz* naming scheme. To compile a source file, download it, extract it to a folder of your choice and run:```
cd *folder*
sudo apt-get build-dep amsn tcl8.4 tk8.4 linphone
sudo apt-get install libxft-dev
dpkgbuildpackage -nc -uc -rsudo
```You can remove any of the package names in the second line depending on what you're compiling. Notice I typed tcl8.4 and tk8.4, as those are the packages apt-get knows about, and share the same dependencies of tcl8.5 and tk8.5 (expect for libxft-dev).

Finally, I can't end up this guide without showing how it looks like :D :[/QUOTE]

after i install sudo apt-get install libosip0 and then try and install sudo dpkg -i linphone-im_0.12.1~neto1_i386.deb it comes back with the following error:

Unpacking linphone-im (from linphone-im_0.12.1~neto1_i386.deb) ...
dpkg: error processing linphone-im_0.12.1~neto1_i386.deb (--install):
 trying to overwrite `/usr/lib/libortp.so.0', which is also in package libortp0
Errors were encountered while processing:
 linphone-im_0.12.1~neto1_i386.deb

i want to get the voice chat with msn. what could be causing this?
thanks.

also, if you want i could host the packages for you on my webspace. no big deal. let me know.

---

### Post by ykpaiha on 2005-11-13
worrk great here!!
Just a little advice could you please  add the corerction for the "links" to the main page .
(easier, this is just to help newbies)
Thanks

---

### Post by arnieboy on 2005-11-13
Excellent work! Arnie salutes your effort.
u need to put the following lines in ur first post to make it complete:
```
cd /usr/lib
sudo ln -s libtk8.5.so.0 libtk8.5.so
sudo ln -s libtcl8.5.so.0 libtcl8.5.so
```

---

### Post by NeTo on 2005-11-13
[QUOTE=sal]after i install sudo apt-get install libosip0 and then try and install sudo dpkg -i linphone-im_0.12.1~neto1_i386.deb it comes back with the following error:

Unpacking linphone-im (from linphone-im_0.12.1~neto1_i386.deb) ...
dpkg: error processing linphone-im_0.12.1~neto1_i386.deb (--install):
 trying to overwrite `/usr/lib/libortp.so.0', which is also in package libortp0
[/QUOTE]

The problem isn't caused because of the libosip0 install, but because you have libortp0 installed beforehand. You should run synaptic, and see if you can uninstall libortp0. If some program you use needs libortp0, I wouldn't recommend trading it for linphone.

Feel free to host the packages if you want. They need to be in a place with more bandwith and that is more time online than my pc :KS . Oh! Please note that I uploaded a new version of linphone-im, that checks for libortp0.

[QUOTE=ykpaiha]worrk great here!!
Just a little advice could you please  add the corerction for the "links" to the main page .
(easier, this is just to help newbies)
Thanks[/QUOTE]
[QUOTE=arnieboy]Excellent work! Arnie salutes your effort.
u need to put the following lines in ur first post to make it complete:
[/QUOTE]
Thank you both for the suggestion. I have edited the first post to include this step. Ideally, the links should be created; why that isn't happening is out of my reach. I hope someone which more knowledge about debian packages can take a look in the source files, and check what's going wrong.

---

### Post by sal on 2005-11-14
[QUOTE=NeTo]The problem isn't caused because of the libosip0 install, but because you have libortp0 installed beforehand. You should run synaptic, and see if you can uninstall libortp0. If some program you use needs libortp0, I wouldn't recommend trading it for linphone.

Feel free to host the packages if you want. They need to be in a place with more bandwith and that is more time online than my pc :KS . Oh! Please note that I uploaded a new version of linphone-im, that checks for libortp0.



Thank you both for the suggestion. I have edited the first post to include this step. Ideally, the links should be created; why that isn't happening is out of my reach. I hope someone which more knowledge about debian packages can take a look in the source files, and check what's going wrong.[/QUOTE]

thanks for the info.
im dling the new linphone now.

ill sort the packages tomorrow and upload them and then come back here and pm you the info so you could update the howto.

---

### Post by sal on 2005-11-15
[QUOTE=NeTo]The problem isn't caused because of the libosip0 install, but because you have libortp0 installed beforehand. You should run synaptic, and see if you can uninstall libortp0. If some program you use needs libortp0, I wouldn't recommend trading it for linphone.

Feel free to host the packages if you want. They need to be in a place with more bandwith and that is more time online than my pc :KS . Oh! Please note that I uploaded a new version of linphone-im, that checks for libortp0.



Thank you both for the suggestion. I have edited the first post to include this step. Ideally, the links should be created; why that isn't happening is out of my reach. I hope someone which more knowledge about debian packages can take a look in the source files, and check what's going wrong.[/QUOTE]


the package is up in tar.gz format. here is the info:
address: 
[http://mysite.verizon.net/vze1ui63/amsn/aMSN-CVS-VV.tar.gz](http://mysite.verizon.net/vze1ui63/amsn/aMSN-CVS-VV.tar.gz)

like this ===>mysite.verizon.net/vze1ui63/amsn/aMSN-CVS-VV.tar.gz
archive contains:
amsn_0.95-1~neto1_i386.deb
linphone-im_0.12.1~neto2_i386.deb
tcl8.5_8.5.0-1~neto2_i386.deb
tk8.5_8.5.0-1~neto2_i386.deb

if you update this files let me know so as i can update the archive.

---

### Post by Locutus on 2005-11-15
I get the following error when trying to follow the guide:

dpkg -i tcl8.5_8.5.0-1~neto2_i386.deb tk8.5_8.5.0-1~neto2_i386.deb amsn_0.95-1~neto1_i386.deb
Selecting previously deselected package tcl8.5.
(Reading database ... 90994 files and directories currently installed.)
Unpacking tcl8.5 (from tcl8.5_8.5.0-1~neto2_i386.deb) ...
Selecting previously deselected package tk8.5.
Unpacking tk8.5 (from tk8.5_8.5.0-1~neto2_i386.deb) ...
Selecting previously deselected package amsn.
Unpacking amsn (from amsn_0.95-1~neto1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing amsn_0.95-1~neto1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/amsn/utils/TkCximage/demos/movie2.gif')
Setting up tcl8.5 (8.5.0-1~neto2) ...

Setting up tk8.5 (8.5.0-1~neto2) ...

Errors were encountered while processing:
 amsn_0.95-1~neto1_i386.deb
root@box:

Any ideas?

Thanks for any help.

---

### Post by NeTo on 2005-11-15
[QUOTE=sal]the package is up in tar.gz format
...
if you update this files let me know so as i can update the archive.[/QUOTE]

Thank you! I have added the link to the first post. I'll let you know whenever a package gets updated.

[QUOTE=Locutus]I get the following error when trying to follow the guide:
...
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing amsn_0.95-1~neto1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/amsn/utils/TkCximage/demos/movie2.gif')[/quote]

This is most likely due to a broken .deb . Run the following command:```
cksum amsn_0.95-1~neto1_i386.deb
```If you get something different to:```
4026924276 9969096 amsn_0.95-1~neto1_i386.deb
```then you need to redownload the file. If the numbers (checksum and byte size) are the same, let me know, so I can take a look at the hosted file.

---

### Post by bored2k on 2005-11-15
Music plugin is not working with XMMS (not even with totem).

---

### Post by Patrick on 2005-11-17
[QUOTE=jamesshuang]I'm having problems with tcl/tk it seems, this is the error I'm getting:
```
/usr/bin/amsn: line 3: 13581 Segmentation fault      /usr/bin/wish amsn

```

Any ideas why it's doing this?

EDIT* - nevermind, seems that if I open /usr/bin/amsn, and change /usr/bin/wish to /usr/bin/wish8.5, this goes away.[/QUOTE]

I get he same error, but dont understand how i fix it with your solution??

What do i do

---

### Post by NeTo on 2005-11-17
[QUOTE=bored2k]Music plugin is not working with XMMS (not even with totem).[/QUOTE]

I have just tested the plugin and have the same problem. I'm not sure of what's causing it, as the totem version shipped with Ubuntu has the feature the plugins requires, and the *infototem* plugin that the script uses works if you execute it from the command-line.

I don't have xmms installed, but from the plugin readme, the [/i]xmms-infopipe[/i] package is required.

[QUOTE=Patrick]I get he same error, but dont understand how i fix it with your solution??

What do i do[/QUOTE]

You need to run```
sudo gedit /usr/bin/amsn
``` and replace any appearance of */usr/bin/wish* with */usr/bin/wish8.5*

If that works for you, let me know, as that isn't supposed to happen with the package.

---

### Post by LichiMan on 2005-11-18
Hi,
Yesterday, I installed amsn and it worked great. But today, after reboot the computer I get this error when I try to load amsn:

```
Application initialization failed: this isn't a Tk applicationinvalid color name "#efebe5 "
Error in startup script: can't invoke "wm" command:  application has been destroyed
    while executing
"wm state . withdraw"
    (file "amsn" line 46)

```

Why I get this error?
Thank you.

**EDIT: IT'IS WORKING AGAIN. After do an apt-get upgrade, all works again :) Thanks**

---

### Post by NeTo on 2005-11-18
Not sure. You didn't try to execute amsn as root right? Try reinstalling amsn.

The error looks very cryptic, could you please check if a file in /usr/share/amsn or ~/.amsn has that string?

---

### Post by LichiMan on 2005-11-18
Thank you NeTo,
I fixed doing a apt-get upgrade.

But now I've problems with tabs. When I open a chat window and then open another, the amsn freezes. Anyone have this problem? I need to set at preferences to get one window per user :(

---

### Post by chele on 2005-11-19
Thanks for putting this package together. I installed it all succesfully, with the object of getting voice chat going over msn. 

I have installed your linphone-im package, but cannot seem to make a solid voice chat connection. I can receive/send & accept Voice Conversations, but without any audio actually going through.  

It just sits there without speaking a word! (How rude :-)

Eventually it times out and msn cuts the Voice Conversation. What did I miss?

---

### Post by chele on 2005-11-19
I found the following note on the aMSN forum: [http://sourceforge.net/forum/message.php?msg_id=3411688](http://sourceforge.net/forum/message.php?msg_id=3411688)

"...linphome-im is deprecated and not supported anymore..."

Which is too bad, I guess we have to be patient and wait for gaim2, no?

Webcam support. Does this support using a firewire-connected camcorder or just usb devices using v4l? Gnomemeeting can see my firewire attached camcorder.

---

### Post by lindt on 2005-11-19
[QUOTE=bored2k]Music plugin is not working with XMMS (not even with totem).[/QUOTE]

not even with amarok

---

### Post by JD11 on 2005-11-19
[QUOTE=jamesshuang]I'm having problems with tcl/tk it seems, this is the error I'm getting:
```
/usr/bin/amsn: line 3: 13581 Segmentation fault      /usr/bin/wish amsn

```

Any ideas why it's doing this?

EDIT* - nevermind, seems that if I open /usr/bin/amsn, and change /usr/bin/wish to /usr/bin/wish8.5, this goes away.[/QUOTE]

I have a similar message but cant edit the file because i dont have the permissions, anyone know a way round this?  (Sorry im a bit of a linux noob)

---

### Post by NeTo on 2005-11-19
[QUOTE=chele]I have installed your linphone-im package, but cannot seem to make a solid voice chat connection. I can receive/send & accept Voice Conversations, but without any audio actually going through. [/QUOTE]

Sorry for not being able to help you here. Maybe the plugin can't capture sound because of esd?

[QUOTE=chele]Webcam support. Does this support using a firewire-connected camcorder or just usb devices using v4l? Gnomemeeting can see my firewire attached camcorder.[/QUOTE]

The capture utility in amsn seems to have libraries to handle two types of webcams: v4l and v4l2.

To see if amsn can detect your webcam, you can run the following test utility:```
cd /usr/share/amsn/utils/linux/capture/
wish8.5 test.tcl
```

---

### Post by NeTo on 2005-11-19
You need to run the following:```
sudo gedit /usr/bin/amsn
```. As superuser, you have the required permissions to edit the file.

---

### Post by anarchist_hippy on 2005-12-12
:~$ sudo dpkg -i tcl8.5_8.5.0-1~neto2_i386.deb
(Reading database ... 99546 files and directories currently installed.)
Preparing to replace tcl8.5 8.5.0-1~neto2 (using tcl8.5_8.5.0-1~neto2_i386.deb) ...
Unpacking replacement tcl8.5 ...
dpkg: dependency problems prevent configuration of tcl8.5:
 tcl8.5 depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing tcl8.5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tcl8.5


I got this... ?! What's the solve?! Anyone knows?...

---

### Post by NeTo on 2005-12-12
Are you trying to install this package in hoary? All of the packages were compiled for breezy, which has libc6 2.3.5.

You should uninstall the broken package:```
sudo apt-get remove tcl8.5
```And then compile tcl8.5 and tk8.5 from sources as mentioned in the first post of this thread.

---

### Post by anarchist_hippy on 2005-12-12
:) Mine is not Breezy..  I don't know how to install.. I think that's the reason... :(

---

### Post by NeTo on 2005-12-26
To install just follow the instructions under "5. Building from sources" in the first post. That way you can install amsn and tcl/tk if you don't have Breezy.

Btw, since amsn 0.95 is out I will attempt to update the debs and the sources sometime this week.

---

### Post by Ibbelz on 2005-12-27
Wow, just installed this beta. Before this I was using GAIM. But aMSN is way better! It even supports webcam, and it also looks better then GAIM.

Thanks TS, great post! :)

---

### Post by Unicast on 2005-12-27
Thanks NeTo - a great (and better) alternative to gaim. You're a :KS !

---

### Post by Vinze on 2006-01-17
Thanks a lot! Before I installed aMSN 0.95 with [EasyUbuntu]("http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23"), but that wasn't really perfect. The music plugin just works with me.

When I had aMSN 0.94 installed, it just showed it when a contact opened a display window. Since I had the EasyUbuntu CVS one, it didn't work anymore, and with this one, it still doesn't :(  Anyone know why? Thanks.

NeTo, you rock!

---

### Post by NeTo on 2006-01-31
Thank you all for comments. It's nice to see the package works as expected :KS 

I have built a new set of packages for the final amsn 0.95. I have now separated amsn, the plugins and the skins in three different packages. I would like to test them first though before making them public. If there is someone interested in installing a "beta package" of amsn, please PM me.

[QUOTE=Vinze]When I had aMSN 0.94 installed, it just showed it when a contact opened a display window. Since I had the EasyUbuntu CVS one, it didn't work anymore, and with this one, it still doesn't :(  Anyone know why? Thanks.
[/QUOTE]

I don't think I understand your problem. You mean you can't keep amsn hidden in the tray until someone writes to you?

---

### Post by Vinze on 2006-01-31
No, never mind, it seems to work now. I'll test the beta package if you wish.

---

### Post by NeTo on 2006-02-01
At last! I have updated the first post with new packages for amsn, tcl, tk and linphone.

I have created two new packages with skins and plugins. So, the aMSN packages are:[LIST][*]*amsn* which has the current amsn version, just as in Dapper Drake.[*]*amsn-plugins* which has several plugins (mostly taken from the amsn page). [*]*amsn-skins* with skins taken from the amsn homepage and CVS.[/LIST]
Thanks a lot to Vinze for testing this packages.
Enjoy!

---

### Post by ember on 2006-02-01
Great work - I will put them onto my webspace as soon as I have downloaded and tested them. That should help to spread your work.

---

### Post by NeTo on 2006-02-01
Thank you. I will have the pc online only a few hours today, as I have been upgrading it. Hopefully tomorrow the links should "feel" more stable.

---

### Post by ember on 2006-02-01
O.k. Here we go - files are available:

[Tcl 8.5]("http://www.doeweling.com/files/ubuntu/amsn/tcl8.5_8.5.0-1~neto3_i386.deb")
[Tk 8.5]("http://www.doeweling.com/files/ubuntu/amsn/tk8.5_8.5.0-1~neto3_i386.deb")
[aMsn 0.95]("http://www.doeweling.com/files/ubuntu/amsn/amsn_0.95-1~neto1_i386.deb")
[Plugins]("http://www.doeweling.com/files/ubuntu/amsn/amsn-plugins_0.95-1~neto1_i386.deb")
[Skins]("http://www.doeweling.com/files/ubuntu/amsn/amsn-skins_0.95-1~neto1_i386.deb")

I have 10 GByte / month transfer limits, so I can leave them there as long as I do not get too near that limit. Connection is pretty good, so have fun and download ;)

---

### Post by sal on 2006-02-02
[QUOTE=NeTo]Thank you. I will have the pc online only a few hours today, as I have been upgrading it. Hopefully tomorrow the links should "feel" more stable.[/QUOTE]

since ember is hosting the files now, there will be no need for me to. if the need strikes again, i will then again host the files.

---

### Post by hunteramor on 2006-02-10
anybody know where i can find these packages for amd64 architecture?  i'd REALLY appreciate it.

---

### Post by Vinze on 2006-02-10
[QUOTE="NeTo"]I have only built i386 packages. For other architectures, you'll need (yup) to compile from sources. Hopefully, as everything is already debianized, that ain't that hard either (read the ''Building from Sources" below). If you build for other architectures, be sure to post the links here when possible, to add them to this post.[/QUOTE]

So if you'd want the latest version, you'd have to compile from source. I think you can best install the dependencies NeTo mentioned and then compile it, then it'll probably work, and if you use the "checkinstall" program than it's just as other .debs.

---

### Post by hunteramor on 2006-02-10
the problem i have when i try to compile it is that it tells me tcl is version 8.4 (it needs 8.5) when i've JUST INSTALLED 8.5

i'll paste the exact message when i get a chance to breathe here.

---

### Post by hunteramor on 2006-02-10
ok, here's what i get from trying to ./configure amsn.  everything goes fine, but at the end it reads:

> 
compile time options summary
============================

    X11          : yes
    Using Libng  : yes
    Tcl          : 8.4
    TK           : 8.5
    DEBUG        : no

if i try to make, everything goes well for a time, but then at the end...

> In file included from utils/linux/traydock/libtray.c:7:
/usr/local/include/tk.h:72:3: error: #error Tk 8.5 must be compiled with tcl.h from Tcl 8.5
make: *** [utils/linux/traydock/libtray.o] Error 1

i've installed tcl and tk 8.5 from the nightlies, which should be as updated as it comes.  what gives?

---

### Post by NeTo on 2006-02-10
You could try to compile with:```
./configure --with-tk=/usr/lib/tk8.5/ --with-tcl=/usr/lib/tcl8.5/ --enable-xft2
```

Anyway, if that fails, you could try the compile intructions in the first post, as the packages should build without further problems.

---

### Post by CyberAngel on 2006-02-10
Has anyone managed to run amsn compiled with tcl/tk 8.5 and connect through http proxy?

Please take a look in this problem: 
[http://www.ubuntuforums.org/showthread.php?p=719332#post719332]("http://www.ubuntuforums.org/showthread.php?p=719332#post719332")

Also if I try to connect directly (I can`t connect directly actually. Just for test) amsn always asks for tls that I already have installed... (The first time I installed amsn 0.95 from the installer they have on their site it asked me for tls and it was installed succesfully. After that it was working but was too ugly. I couldn`t even read what the others was writing to me when I was chating)

Note: I am using Kubuntu Breezy AMD64..

Thanks in advance :)

---

### Post by hunteramor on 2006-02-10
Thanks for the help, NeTo.  When I try it that way, I get the following:

> checking tcl build dir... using tcl library in /usr/lib/tcl8.5/
./configure: line 3012: /usr/lib/tcl8.5//tclConfig.sh: No such file or directory

---

### Post by NeTo on 2006-02-11
[QUOTE=hunteramor]Thanks for the help, NeTo.  When I try it that way, I get the following...[/QUOTE]You need to modify *--with-tcl=/usr/lib/tcl8.5/* to reflect the path where you have tcl8.5 installed, assuming it compiled and got installed correctly.

[QUOTE=CyberAngel]Also if I try to connect directly (I can`t connect directly actually. Just for test) amsn always asks for tls that I already have installed... (The first time I installed amsn 0.95 from the installer they have on their site it asked me for tls and it was installed succesfully. After that it was working but was too ugly. I couldn`t even read what the others was writing to me when I was chating)[/quote]You could try with a clean install of amsn, making sure that the configuration files got removed. It may be that something related to the tls configuration changed in amsn before the final version release.

---

### Post by hunteramor on 2006-02-11
got 0.95  installed right for x64, finally, but the fonts look crappy... oh well, can't have everything.  as much time as i'm willing to spend on it for now

---

### Post by Mr.X on 2006-02-15
I can host the file off my main website, but your computer is off atm.

---

### Post by NeTo on 2006-02-16
[QUOTE=Mr.X]I can host the file off my main website, but your computer is off atm.[/QUOTE]

Sorry for that. ember has mirrored the packages, but I forgot to update the links. If you wish to mirror the files anyway, you can check the now updated links in the first post :KS

---

### Post by ashrack on 2006-02-23
I have succesfully built DEB packages of TCL/TK 8.5 with AA enabled.
Also I have compiled latest aMSN from CVS so that I am now able to switch tabs with keyboard shortcuts.
If anyone wants them...

---

### Post by NeTo on 2006-02-26
[QUOTE=ashrack]I have succesfully built DEB packages of TCL/TK 8.5 with AA enabled.
Also I have compiled latest aMSN from CVS so that I am now able to switch tabs with keyboard shortcuts.
If anyone wants them...[/QUOTE]

Great!. Did you use the source tcl/tk packages on this thread? If you did, then I could add your amsn cvs package to the first post if you wish.

---

### Post by ashrack on 2006-02-26
NETO
no I haven't. Since your DL links for the source of TCL,TK never worked 4 me. So I built them of of the official TCL/TK site.

---

### Post by NeTo on 2006-03-21
[QUOTE=ashrack]NETO
no I haven't. Since your DL links for the source of TCL,TK never worked 4 me. So I built them of of the official TCL/TK site.[/QUOTE]

Sorry to hear that, it seems that no-ip.com doesn't redirect addresses that look like *membername.no-ip.com* anymore for non-premium members. I didn't realized the issue until now, so the links for the sources were down all of this time.

I have now registered a different address, so I have updated the (now hopefully) working links in the first post. Sorry for any inconvenience.

Every link in the first post should be working atm.

---

### Post by manicka on 2006-03-25
* I can confirm that these packages also work in Dapper
    * when running amsn in an Xgl server you will find that you get an error message like 

```
Application initialization failed: this isn't a Tk applicationunknown color name "Black" 
```


This is due to an Xgl server error. It can be fixed by running the command

```
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/rgb.txt
```


Great work NeTo :D

---

### Post by mundano on 2006-03-25
Works great on dapper... :mrgreen: :mrgreen: 

The only bad thing, is Adept-updater who is allways trying to update amsn to the ofcial package... :-|

---

### Post by NeTo on 2006-03-26
[QUOTE=mundano]Works great on dapper... :mrgreen: :mrgreen: 

The only bad thing, is Adept-updater who is allways trying to update amsn to the ofcial package... :-|[/QUOTE]

It's great to see that is working with dapper :KS. I will check out the version number of the official dapper package tomorrow, hopefully a minor version change will fix that issue. 

Btw, I compiled a cvs snapshot (with the new [chameleon](http://amsn.sourceforge.net/forums/viewtopic.php?t=618) plugin) and it looks great :D. Packages coming tomorrow ;)

---

### Post by manicka on 2006-03-26
[QUOTE=mundano]Works great on dapper... :mrgreen: :mrgreen: 

The only bad thing, is Adept-updater who is allways trying to update amsn to the ofcial package... :-|[/QUOTE]

Just lock the package to that version and that problem will go away

---

### Post by NeTo on 2006-03-27
New packages are out! In the first post I have added links for packages built from a recent CVS snapshot (including a new *plugins* package).

There are also links for a Dapper package. It only differs in version number: it's basically the same one for Breezy but with a +1. That and the fact that I compiled it with Dapper :p

---

### Post by Vinze on 2006-03-28
Emm. There are no TCL and TK 8.5 packages for Dapper, though it is dependent on it...

**Edit:** The Breezy packages installed on Dapper, however, when I now ran aMSN I got the following error: > wish: error while loading shared libraries: libtk8.5.so: cannot open shared object file: No such file or directory


---

### Post by NeTo on 2006-03-28
[QUOTE=Vinze]Emm. There are no TCL and TK 8.5 packages for Dapper, though it is dependent on it...

**Edit:** The Breezy packages installed on Dapper, however, when I now ran aMSN I got the following error:[/QUOTE]

Yeah, the breezy packages for tcl/tk 8.5 work with dapper too. I recompiled amsn just to increase the version number of the package.

To fix the shared libraries error, you need to create some simlinks (as explained in the how-to):```
cd /usr/lib
sudo ln -sf libtk8.5.so.0 libtk8.5.so
sudo ln -sf libtcl8.5.so.0 libtcl8.5.so
```

---

### Post by Vinze on 2006-03-28
OK, then it works, do you know if there also is a way to install that Chameleon plugin, because it looks very nice. When I manually install it it just says the installation failed... Maybe it conflicts with Desktop Integration?

---

### Post by NeTo on 2006-03-28
[QUOTE=Vinze]OK, then it works, do you know if there also is a way to install that Chameleon plugin, because it looks very nice. When I manually install it it just says the installation failed... Maybe it conflicts with Desktop Integration?[/QUOTE]

I have already included the chameleon plugin in the *amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb*. Read the *4.2 aMSN CVS snapshots* section of the guide. You need to install both packages, *aMSN cvs* and the *plugins*, as chameleon will work only on aMSN CVS (newer than March 14)

Sorry for the messed up instructions, but since the guide is oriented to breezy users, I couldn't figure out how to add some type of detailed dapper howto on top of it.

---

### Post by Papou on 2006-03-31
Seems you've done a great job Neto,

My dauter is fan of audio-video conf using msn under windows XP :mrgreen: 
I'm trying to keep her under Ubuntu :D and I've installed aMsn from the official web page ( [http://amsn.sourceforge.net/index.php](http://amsn.sourceforge.net/index.php) ). But audio-video is missing and my poor computer is often turned back to windows :( 

I'm under Breezy, kernel 2.6.12-10-386. 
Would you recommand me to Re-install aMsn using your files ?
Any recommendation to do that ?
Do you know members using succesfully audio-video conf with firends under XP ( My dauter's friends are not lucky enough to have got Ubuntu ) ? 

All the best.

---

### Post by Vinze on 2006-03-31
[QUOTE=NeTo]I have already included the chameleon plugin in the *amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb*. Read the *4.2 aMSN CVS snapshots* section of the guide. You need to install both packages, *aMSN cvs* and the *plugins*, as chameleon will work only on aMSN CVS (newer than March 14)

Sorry for the messed up instructions, but since the guide is oriented to breezy users, I couldn't figure out how to add some type of detailed dapper howto on top of it.[/QUOTE]

Maybe something in a quote, or a sepearate thread? Anyway, if I remember right I tried the plugins, but the package depended on aMSN which it sais wasn't installed. Ah well, I'll try again at home in a few days.

@ papou: video worked for me :D

---

### Post by Papou on 2006-03-31
@ Vinze :  
Thanks for the advise ;) . Video is also OK for me. What is missing on my instalation is the Video/Audio Conference Support :-# . Did you succesfully install it to allow audio conference with friends under windows msn ?

---

### Post by Vinze on 2006-03-31
[QUOTE=Papou]@ Vinze :  
Thanks for the advise ;) . Video is also OK for me. What is missing on my instalation is the Video/Audio Conference Support :-# . Did you succesfully install it to allow audio conference with friends under windows msn ?[/QUOTE]

You mean just MSN on Windows? The time I used Windows is over, but when I used Windows I did not use MSN. I have seen audio successfully on MSN on Windows though.

---

### Post by Papou on 2006-03-31
@ Vinze
My question was : do you succesfully use aMsn under Ubuntu to make audio-video conference with friends using MSN under windows ?
It's what I try to get to keep my daughter away from windows !

---

### Post by NeTo on 2006-04-01
Hi. Sadly, I haven't hear any successful reports on the status of the linphone plugin that I have packaged. I haven't tested it, so it is included only as is, with the hope that it will work for someone else.

I personally wouldn't recommend you to reinstall amsn, as the chances that the linphone plugin will work or not are most likely half and a half.

If you really need videoconference though, you could take a look at [Mercury](http://mercury.to). Unfortunately, you also need follow additional setup instructions to get [videoconferencing in Mercury](http://mercury.to/index.php?page=Wiki&wikipage=Video_Conference).

---

### Post by Vinze on 2006-04-01
[QUOTE=Papou]@ Vinze
My question was : do you succesfully use aMsn under Ubuntu to make audio-video conference with friends using MSN under windows ?
It's what I try to get to keep my daughter away from windows ![/QUOTE]

Oh, like that, well, I was able to view webcams of people running MSN on Windows, but I don't know about sound, as I haven't tested that.

---

### Post by Papou on 2006-04-01
@ Neto :
Thank you so much for your detailed information. Yes, it's probably better to wait the completion of the FarSight project for videoconferencing with aMsn.

For the timebeing, I installed Mercury with videoconferencing. Hopefully it will avoid windows sessions to my poor computer. 

@ Vinze :
That's OK.

All the Best.

---

### Post by NeTo on 2006-04-08
I have compiled a package from today's aMSN CVS snapshot. If you are using aMSN CVS, I recommend you to update to this one, as a [connection issue](http://amsn.sourceforge.net/forums/viewtopic.php?t=742) has been fixed.

On a sidenote I have just tested the Desktop Integration plugin in both amsn packages (0.95 and CVS) and noticed it isn't working. The file dialog appears, but the files aren't actually being sent. Has anyone else noticed this?

---

### Post by eKoeS on 2006-04-18
Very good job NeTo, I'm using your packages and aMSN works fine.
There's only a problem: when I open a new chat window, the last one begins to shake (LoL, is not a nudge :P), so I must kill amsn from terminal.
Do you know why chat windows behave in this strange way?

Thank you, 
eKoeS

---

### Post by NeTo on 2006-04-19
That's strange, I haven't noticed anything similar. You could try disabling/enabling tabbed browsing. An extreme measure could be to wipe out the ~/.aMSN folder. I doubt  that is cause though.

---

### Post by gardara on 2006-04-19
I get these errors: 

when I enter
```
sudo apt-get install libosip0
```
I get
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libosip0
```


When I enter 
```
 wget http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/linphone-im_0.12.1-1~neto2_i386.deb
```

I get

```
--23:52:10--  http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/linphone-im_0.12.1-1~neto2_i386.deb
           => `linphone-im_0.12.1-1~neto2_i386.deb'
Resolving netosoft.no-ip.org... 204.16.252.98
Connecting to netosoft.no-ip.org|204.16.252.98|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://201.220.118.178:8080/Ubuntu%20-%20Breezy/amsn/linphone-im_0.12.1-1~neto2_i386.deb [following]
--23:52:11--  http://201.220.118.178:8080/Ubuntu%20-%20Breezy/amsn/linphone-im_0.12.1-1~neto2_i386.deb
           => `linphone-im_0.12.1-1~neto2_i386.deb'
Connecting to 201.220.118.178:8080... failed: Connection refused.
```


:???:

---

### Post by eKoeS on 2006-04-20
[QUOTE=NeTo]That's strange, I haven't noticed anything similar. You could try disabling/enabling tabbed browsing. An extreme measure could be to wipe out the ~/.aMSN folder. I doubt  that is cause though.[/QUOTE]
You're right, I solved that problem simply disabling tabbed browsing. Thank you for support. :)

---

### Post by NeTo on 2006-04-20
[QUOTE=gardara]I get these errors: 

when I enter```
sudo apt-get install libosip0
```I get
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libosip0
```[/quote]Uhm, it seems that in Dapper liposip0 has been deprecated. You could try installing libosip2-3 package (but I'm not sure that would work), or downloading the libosip0 package from the breezy repositories.

[quote=gardara]When I enter```
 wget http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/linphone-im_0.12.1-1~neto2_i386.deb
```I get```
--23:52:10--  http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/linphone-im_0.12.1-1~neto2_i386.deb
           => `linphone-im_0.12.1-1~neto2_i386.deb'
Resolving netosoft.no-ip.org... 204.16.252.98
Connecting to netosoft.no-ip.org|204.16.252.98|:80... connected.
HTTP request sent, awaiting response... 302 Found
```:???:[/QUOTE]There have been power outages where I live for these two days because of strong winds. So the server where I host the files (my home pc) has been offline most of the day. Weather should hopefully get better by the end of the weekend, along with the stability of my internet connection :wink:

---

### Post by nowadays who knows on 2006-04-20
ok I have followed your scripts from the front of the post except for vid/audio conferencing. Everything loaded right but tha darned thing wont log in. it just seems to hang. I am using port 80 to connect behind firewall. When not using 80 I get a actual message but with using 80 it just hangs any advice?:-k

---

### Post by nowadays who knows on 2006-04-20
Ok tried runing in terminal and foud this error but still don't know how to fix it.

---

### Post by nowadays who knows on 2006-04-20
gerror failed to handle background error.
    Original error: bad variable name "options(-proxy_writing)": upvar won't create a scalar variable that looks like an array element
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"
Malformed attributes:  HTML PUBLIC "-//IETF//DTD HTML 2.0//EN" found in:
 HTML PUBLIC "-//IETF//DTD HTML 2.0//EN"
Current stack: :!DOCTYPE

---

### Post by NeTo on 2006-04-20
[QUOTE=nowadays who knows]gerror failed to handle background error.
    Original error: bad variable name "options(-proxy_writing)": upvar won't create a scalar variable that looks like an array element
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"
Malformed attributes:  HTML PUBLIC "-//IETF//DTD HTML 2.0//EN" found in:
 HTML PUBLIC "-//IETF//DTD HTML 2.0//EN"
Current stack: :!DOCTYPE[/QUOTE]

That isn't related to your problem, actually, I noticed I get that too when running from a terminal. I wonder what that error means...

Anyway, you can try enabling port 1863 in your firewall and setup aMsn to use a direct connection to the internet. Also, you could post your question in the aMsn forums, as they have a Troubleshooting section.

---

### Post by bored2k on 2006-04-24
This is one hell of a contribution. Thanks mate.

---

### Post by bored2k on 2006-04-24
Has anyone gotten the Music plugin working with _any_ player? how?

---

### Post by Mr Aragorn on 2006-04-24
When i type the first command
sudo apt-get install imlibll sox libpng12-0 docker tcltls

I get this, im a total noob to ubuntu so i dont know what t do. What should i do?

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imlibll

---

### Post by NeTo on 2006-04-24
[QUOTE=Mr Aragorn]When i type the first command
sudo apt-get install imlibll sox libpng12-0 docker tcltls

I get this, im a total noob to ubuntu so i dont know what t do. What should i do?

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imlibll[/QUOTE]
Make sure you typed *imlib**11*** instead of *imlib**ll***. The package should be in the universe repository of Ubuntu.

---

### Post by Mr Aragorn on 2006-04-25
sudo apt-get install imlib11 sox libpng12-0 docker tcltls
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imlib11

Ok I changed it but it still says the same error. Can anyone help me](*,) ](*,)

---

### Post by XP1 on 2006-04-29
[QUOTE=Mr Aragorn]sudo apt-get install imlib11 sox libpng12-0 docker tcltls
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imlib11

Ok I changed it but it still says the same error. Can anyone help me](*,) ](*,)[/QUOTE]

Here friend, I had trouble too...

[http://psychocats.net/linux/sources.php](http://psychocats.net/linux/sources.php)

---

### Post by migraineboy on 2006-05-01
Well I've just installed here in 2 computer, mine and my wife's. Im mine, everything ok, but in hers when I click on the Amsn link under aplications tab, it starts to load and suddenly crashes and never really starts to work, it never loads. Any ideas(int)
It seems some kind of conflict...
P.S: sorry for my bad english, I'm brazilian.

---

### Post by NeTo on 2006-05-01
Have you tried running amsn from a terminal window? That could give you a hint on what is going wrong.

You could try creating the symlinks to libtk8.5.so.0 and libtcl8.5.so.0 as indicated in the first post.

---

### Post by migraineboy on 2006-05-02
[QUOTE=NeTo]Have you tried running amsn from a terminal window? That could give you a hint on what is going wrong.

You could try creating the symlinks to libtk8.5.so.0 and libtcl8.5.so.0 as indicated in the first post.[/QUOTE]

Thank you, that solved the problem.

---

### Post by Patok on 2006-05-07
Prlbem: I run amsn, start a conversation, then suddenly the windows starts shaking and amsn freezes, whats happening?

---

### Post by NeTo on 2006-05-07
[QUOTE=Patok]Prlbem: I run amsn, start a conversation, then suddenly the windows starts shaking and amsn freezes, whats happening?[/QUOTE]

Maybe the issue is similar to something described in this same thread. You could try disabling tabbed browsing.

---

### Post by e4m on 2006-05-10
hi ,
this version tc/tk 8.5a3 will cause much of problem with amsn interface (like dialog .. send file for example). AMSN developers team say me to switch at 8.5 CVS version becouse the bug was corrected. Or degradate to 8.4 (without AA )..

bye

---

### Post by NeTo on 2006-05-13
[QUOTE=e4m]hi ,
this version tc/tk 8.5a3 will cause much of problem with amsn interface (like dialog .. send file for example). AMSN developers team say me to switch at 8.5 CVS version becouse the bug was corrected. Or degradate to 8.4 (without AA )..

bye[/QUOTE]

For dialogs, a way around could be the desktop integration plugin.

Anyway, my university has been besieged (if that's the correct term) by a group of students, so I have some spare time to take a look at Tk/Tcl. If I can get a package out of it I will post it here.

---

### Post by panurge77 on 2006-05-16
Any hope to find amd64 debs?

---

### Post by Daiver on 2006-05-17
Thanks for this guide.  It worked perfectly.

---

### Post by l.capriotti on 2006-05-17
I followed the guide and installed the latest CVS packages with no problems.
When I try to login (using HTTP method as I'm behing a restrictive firewall) I have the following error in the console:

[FONT="Courier New"][SIZE="2"]bad variable name "options(-proxy_writing)": upvar won't create a scalar variable that looks like an array element
    while executing
"upvar 1 ::ProxyHTTP::Snit_inst2::options(-proxy_writing) options(-proxy_writing)"
    ("uplevel" body line 1)
    invoked from within
"uplevel 1 [list upvar 1 ${selfns}::$varname $varname]"
    (procedure "::snit::RT.variable" line 5)
    invoked from within
"variable options(-proxy_writing)"
    (procedure "::ProxyHTTP::Snit_methodHTTPRead" line 8)
    invoked from within
"$self HTTPRead $sb"
    (procedure "::ProxyHTTP::Snit_methodConnectReply" line 5)
    invoked from within
"::Proxy::ProxyHTTP1 ConnectReply ns sock7"[/SIZE][/FONT]

and amsn is not able to connect to MSN.

Any clue/hints?

Thanks in advance

Luigi

---

### Post by panurge77 on 2006-05-18
Tryng to build from your sources in Drapper amd64 leads me to this error

checking if 64bit support is requested... yes
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)... ./configure: line 15271: syntax error near unexpected token `)'
./configure: line 15271: `      OSF*)'
make: *** [build-stamp] Error 2


Any idea how to fix that?

---

### Post by b0rsten on 2006-05-19
> wget [http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/amsn_0.95+cvs20060408-1~neto1_i386.deb](http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/amsn_0.95+cvs20060408-1~neto1_i386.deb)
wget [http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb](http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/amsn/amsn-plugins_0.95+cvs20060325-1~neto1_i386.deb)
those are working fine for me (dapper)

---

### Post by pjot on 2006-05-22
First of all a BIG 5/5 stars to you!! :KS :KS :KS :KS :KS 

Secondly you have to pin the package if you don't want apt-get/synaptic to ruin it when you upgrade.

```
sudo gedit /etc/apt/preferences
```

Add these lines to the file (if you haven't pinned any packages before it should be empty):

```
Package: amsn
Pin: version 0.95-1~neto1
Pin-Priority: 1001
```

I've only tried this on Dapper but it should work on everything (this feature as existed in debians apt-get for as long as I can remember). ;)

---

### Post by Daiver on 2006-05-23
My kernel was updated in the last Adept update and now aMSN stopped working.  I installed it using this guide.  Do I have to reinstall for each kernel update?

---

### Post by pjot on 2006-05-23
Daiver: Do as I wrote in the post above and it shouldn't ruin your aMSN install.

---

### Post by Daiver on 2006-05-23
Pjot, thanks for the reply and sorry for being so distracted.

I went into /etc/apt and the file "preferences" does not exist, so I can't edit with nano unless I create a new file.  Is this OK?

---

### Post by pjot on 2006-05-24
If it doesn't exist that's because you havn't pinned anything before so just create it and att those lines to it and you should be fine :)

---

### Post by Muahdib51 on 2006-05-24
first thanks, Neto for those information,

but for me the package linphone-im_0.12.1-1~neto2_i386.deb don't work can you give me an url for downloading sources of linphone-im like this i will try to compile it myself for my Ubuntu,
thanks
(excuse my english, i'm french guy :-k )

---

### Post by NeTo on 2006-05-24
[QUOTE=Muahdib51]first thanks, Neto for those information,

but for me the package linphone-im_0.12.1-1~neto2_i386.deb don't work can you give me an url for downloading sources of linphone-im like this i will try to compile it myself for my Ubuntu,
thanks
(excuse my english, i'm french guy :-k )[/QUOTE]

The linphone-im sources are located at:```
http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/Sources/amsn/linphone-im_0.12.1.orig.tar.gz
http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/Sources/amsn/linphone-im_0.12.1-1~neto2.dsc
http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/Sources/amsn/linphone-im_0.12.1-1~neto2.diff.gz
```

I haven't taken a look at the linphone sources in a while, I hope you're able to compile it successfully.

[quote=panurge77]Tryng to build from your sources in Drapper amd64 leads me to this error

checking if 64bit support is requested... yes
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)... ./configure: line 15271: syntax error near unexpected token `)'
./configure: line 15271: ` OSF*)'
make: *** [build-stamp] Error 2


Any idea how to fix that?[/quote]
I am not sure what could be causing the amsn configure script to fail that way, as I don't have any amd64 computers nearby to test with. Have you tried with the cvs packages I posted?

---

### Post by Daiver on 2006-05-26
[QUOTE=pjot]If it doesn't exist that's because you havn't pinned anything before so just create it and att those lines to it and you should be fine :)[/QUOTE]

[QUOTE=anodizer]I'm using Synaptic, not Adept, but there must be an option to hold back the specified -by you- packages. Upgrading the kernel is always a good idea, however.[/QUOTE]

Thanks!

---

### Post by sotua on 2006-05-31
Hi!

I tried this and it worked perfectly with Breezy.

However, I did the same for Dapper, and now the antialiasing of the fonts is very much "off" - I'm seeing weird colored pixels instead of properly antialiased text. It happens only within amsn and not other apps so I doubt it is because of general antialiasing/hinting/etc settings.

Any  ideas?

Thanks in advance

---

### Post by NeTo on 2006-06-07
[QUOTE=sotua]Hi!

I tried this and it worked perfectly with Breezy.

However, I did the same for Dapper, and now the antialiasing of the fonts is very much "off" - I'm seeing weird colored pixels instead of properly antialiased text. It happens only within amsn and not other apps so I doubt it is because of general antialiasing/hinting/etc settings.

Any  ideas?

Thanks in advance[/QUOTE]

I will into Dapper issues as soon as I get Dapper installed. I will most likely repackage Tcl/Tk, amsn and a CVS snapshot, which should hopefully solve incompatibility issues.

---

### Post by panurge77 on 2006-06-07
I switched to x86, so I gave up building that amd64 deb. But I learned to complie everything while I was at amd64 and amsn wiki has a suggestion that maybe you missed (at least it was not on the howto I found here on the forums for compiling it all). That is, tcl/tk shoud be compiled without the --enable-threads option. That way you don't need the ld assum kernel thing and amsn won't have any trouble with 2.6 kernel. It's on amsn wiki > known issues. And if you do build new debs using the svn version (amsn quited cvs), and if you find some error about make not finding a rules.mk file, please tell me the workaround. I want to know what I missed. I can compile .95 without any problem but got stuck on this error while trying to compile the svn. Anyway, good luck.;)

---

### Post by kpolice on 2006-06-07
I build the svn version 2 weeks ago but I can't find the .deb file :( . But I followed the guide in [http://www.ubuntu-es.org/node/13729](http://www.ubuntu-es.org/node/13729) , it's in spanish and for CVS but the compilation process is the same.

---

### Post by panurge77 on 2006-06-07
I've never built a deb before. My rpevious atempt was compiling from source to a make install but I'll try that guide, thanks. Spanish wont be a big problem since I speak portuguese.

---

### Post by Cryptopsy on 2006-06-28
I have had nothing but problems with these instructions.
My aMSN wont even open up.  I followed the instructions in the first post to a T.  

When it goes to install the three debs, it says "Resolving wget... failed: Name or service not known."


So ya. how do I fix my aMSN.  Im faily new at linux.

---

### Post by Vinze on 2006-06-30
[QUOTE=Cryptopsy]I have had nothing but problems with these instructions.
My aMSN wont even open up.  I followed the instructions in the first post to a T.  

When it goes to install the three debs, it says "Resolving wget... failed: Name or service not known."


So ya. how do I fix my aMSN.  Im faily new at linux.[/QUOTE]
Well, if you followed the guide and at least installed TK and stuff, you might want to try and download the latest cvs version, you can just download a tar.gz . I did it, it worked and it already has some very cool new features (and it supports the "Personal Message" ;)

---

### Post by Rackerz on 2006-07-10
After using this howto I try to run amsn and I get this error.

> darren@darren:~$ amsn
Segmentation fault

---

### Post by arnieboy on 2006-07-10
> **Rackerz said:**
> After using this howto I try to run amsn and I get this error.
 if u are running dapper, this happened because dapper upgraded amsn to its own version which depends on tcl/tk 8.4 and the version of tcl/tk which this howto installs (for smoother feel and looks is 8.5). To undo the damage done by the automatic repository upgrade in dapper, install the version of amsn packaged by neto and lock it to prevent further upgrades.

---

### Post by rogeriovinhal on 2006-07-20
I am getting a connection refused error when I try to download the files to build myself the amd64 package...

EDIT:
Now I got it.
I have built amd64 packages with the latest 8.5a4 versions and installed here, it seems to be ok, but I haven't tested in a clean system, I am not certain if it will work anywhere. I also built the 0.97b version of amsn to use with it.
So if anyone is interested, talk to me that I may host it somewhere.

---

### Post by obavjestenja on 2006-07-22
how to remove this package(debian packages for aMSN 0.95 (final), Tcl/Tk 8.5a3) plaese !!!
amsn not working](*,)

---

### Post by Zigon on 2006-07-26
Wow thanks first program installed on linux! thanks a bunch

---

### Post by TomParker on 2006-07-30
Like this makes sense... not.

this is my 8th install of ubuntu in a matter of 4 days. My amsn is now screw on a clean install I get this when i try to start amsn

tom@tom-desktop:~$ amsn
wish: error while loading shared libraries: libtk8.5.so: cannot open shared object file: No such file or directory

im getting errors all over the place

dpkg: dependency problems prevent configuration of amsn:
 amsn depends on imlib11; however:
  Package imlib11 is not installed.
 amsn depends on sox; however:
  Package sox is not installed.
 amsn depends on docker; however:
  Package docker is not installed.
 amsn depends on tcltls; however:
  Package tcltls is not installed.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn

tom@tom-desktop:~$ sudo apt-get install imlib11 sox libpng12-0 docker tcltls
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imlib11

stupid synaptic thing wont find imlib11 and now stays theres a broken thing in there any help?

Edit - F**k it im going back to windows too much pissing about to do something so simple, bye.

---

### Post by zerwas on 2006-07-30
> **TomParker said:**
> 
E: Couldn't find package imlib11
stupid synaptic thing
imlib11 is part of the universe repositories. Open Synaptic and add universe.
this will not help you because you won't read this message anymore. Instead, you installed Windows, what - i think - is better for your claims.
> **TomParker said:**
> 
Edit - F**k it im going back to windows too much pissing about to do something so simple, bye.
I don't think that **anybody** in these forums should have speak like this...
Why don't you try aMSN 0.97b..a few clicks and you have it:[aMSN 0.97b package]("http://www.ubuntuforums.org/showthread.php?t=216689")

Greetings,
zerwas

---

### Post by shame on 2006-07-30
I'm having trouble with webcam on this version of amsn.
I have 2 webcams but when I go to settings I get "Error opening device" on both of them.
I've tried connecting just one in case of conflict but still get the same error.
Everything else is working ok and I have set up port forwarding for the webcam ports but still no good.
I've also tried the tcltest thing and it brings up an empty window.
Both webcams worked perfectly fine with the previous version of amsn without tcl/tk 8.5.
Here is the terminal output when the webcams fail - ```

dlsym[./utils/linux/capture/libng/plugins/drv0-v4l2.so]: ./utils/linux/capture/libng/plugins/drv0-v4l2.so: undefined symbol: _ng_plugin_init
dlsym[./utils/linux/capture/libng/plugins/drv1-v4l.so]: ./utils/linux/capture/libng/plugins/drv1-v4l.so: undefined symbol: _ng_plugin_init
WARNING: no plugins found [/home/neto/Sources/tcl-tk/amsn/amsn-0.95]
bgerror failed to handle background error.
    Original error: expected integer but got ""
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"
bgerror failed to handle background error.
    Original error: expected integer but got ""
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"
bgerror failed to handle background error.
    Original error: expected integer but got ""
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"
bgerror failed to handle background error.
    Original error: expected integer but got ""
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"
```
I don't understand what it all means but I have noticed this particular line - ```
WARNING: no plugins found [/home/neto/Sources/tcl-tk/amsn/amsn-0.95]
bgerror failed to handle background error.
```
/home/neto isn't my home directory so it obviously wouldn't find any plugins there.

<EDIT>
I should also mention there are no problems with the webcams themselves as they are still working with other apps such as camorama, xawtv , gyach enhanced and kopete

---

### Post by vivia on 2006-09-13
@shame :

This error (Unable to convert date-time string) has been fixed in latest aMSN version.

I don't know what's wrong in Neto's package, I was going to suggest that you compile the SVN version yourself but it seems that he hasn't include the dev packages, which you will need. I uploaded them on [http://www.autom.teithe.gr/~vivia/index82](http://www.autom.teithe.gr/~vivia/index82) (Unzip and install all packages).

I suggest you:

1) remove packages for tcl8.5, tk8.5 and amsn
2) install the build-essential package. IIRC you will also need libpng, libjpeg, x11-dev - I am not sure about the exact names
3) install the tcl/tk 8.5 packages from the link I am sending you
4) wget [http://amsn.sourceforge.net/amsn_dev.tar.gz](http://amsn.sourceforge.net/amsn_dev.tar.gz)
5) tar xvfz amsn_dev.tar.gz
   cd amsn
   ./configure
6) If ./configure doesn't complain, you are ready to:
   make
   make install

Hope it works :)

---

### Post by Vinze on 2006-09-13
But you can also download the development package of aMSN 0.96 at the [official site](http://amsn.sourceforge.net/linux-downloads.php). I recommend that.

---

### Post by vivia on 2006-09-13
That is compiled against tcl/tk 8.4 . If you don't mind not having antialiasing support, I recommend that too :)

---

### Post by Poka64 on 2006-09-14
Can't compile with your debs vivia :(

checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev

I have installed all the packages in your zipped folder :/

---

### Post by vivia on 2006-09-15
Try to look at the `tclsh` and `wish` executables and see if they are linked against tclsh8.4/wish8.4 or tclsh8.5/wish8.5 , change the symlinks if necessary.

---

### Post by Poka64 on 2006-09-15
> **vivia said:**
> Try to look at the `tclsh` and `wish` executables and see if they are linked against tclsh8.4/wish8.4 or tclsh8.5/wish8.5 , change the symlinks if necessary.

I can't find those files, can you point me in the right direction where to find them?

Edit: found them, but how do I setup the symlinks?

Edit2: solved it, used the firsts post -dev packages

---

### Post by vivia on 2006-09-17
rm /usr/bin/tclsh
rm /usr/bin/wish
ln -s /usr/bin/tclsh8.5 /usr/bin/tclsh
ln -s /usr/bin/wish8.5 /usr/bin/wish

should do the trick :)

---

### Post by Poka64 on 2006-09-17
Got it to work vivia, with the -dev packages in this howtos first post :)

---

### Post by lemerou on 2006-09-22
> **vivia said:**
> @shame :

This error (Unable to convert date-time string) has been fixed in latest aMSN version.

I don't know what's wrong in Neto's package, I was going to suggest that you compile the SVN version yourself but it seems that he hasn't include the dev packages, which you will need. I uploaded them on [http://www.autom.teithe.gr/~vivia/index82](http://www.autom.teithe.gr/~vivia/index82) (Unzip and install all packages).

I suggest you:

1) remove packages for tcl8.5, tk8.5 and amsn
2) install the build-essential package. IIRC you will also need libpng, libjpeg, x11-dev - I am not sure about the exact names
3) install the tcl/tk 8.5 packages from the link I am sending you
4) wget [http://amsn.sourceforge.net/amsn_dev.tar.gz](http://amsn.sourceforge.net/amsn_dev.tar.gz)
5) tar xvfz amsn_dev.tar.gz
   cd amsn
   ./configure
6) If ./configure doesn't complain, you are ready to:
   make
   make install

Hope it works :)

before the ./configure:

```

sudo update-alternatives --config wish
sudo update-alternatives --config tclsh

```

and after make install:

"Download tcl8.5a4 source and copy entire dir from tcl8.5a4/library/msgcat/ to /usr/lib/tcl8.5 and then, will work"

[http://prdownloads.sourceforge.net/tcl/tcl8.5a4-src.tar.gz](http://prdownloads.sourceforge.net/tcl/tcl8.5a4-src.tar.gz)

---

### Post by NeTo on 2006-09-28
Sorry all for disapearing for so long. I have been very busy the last couple of months working a project at Uni. Basically I am designing a GUI por a surveillance camera, in order to take panoramics of national parks. I used the project as an "excuse" to learn python (I'm working with wxpython/wxglade wight now). Hopefully I will upload a panoramic sometime soon to show you the city where I live :KS

Back on topic, I want to clarify that I will leave this HOWTO for **Breezy** only.

For Dapper, manzuk has already a great guide [thread=216689]here[/thread]. I will try to support his effort by updating some of the packages here (new versions of the tcl, tk and tcltls packages are in the works :mrgreen:).

---

### Post by sbubba on 2008-02-09
> **NeTo said:**
> 
You should uninstall the broken package:```
sudo apt-get remove tcl8.5
```
yeeah i've a problem with amsn 0.97b and I've solved in this way
thanks =)

---

