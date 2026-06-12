---
title: "HOWTO: Build beryl from source, gnome"
date: 2006-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by killkoy on 2006-10-21
This guide was created as there are currently no beryl repositories for amd64 dapper that I am aware of. It involves compiling beryl from source.
All the ATI sections of this guide are untested by me and from the following two guides
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=fglrx](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=fglrx)
[http://forum.beryl-project.org/viewtopic.php?id=389](http://forum.beryl-project.org/viewtopic.php?id=389)
If you own an x series radeon  and have problems with lockups, read this post:
[http://ubuntuforums.org/showthread.php?t=150854](http://ubuntuforums.org/showthread.php?t=150854)
This guide has been tested by me using a nvidia graphics card and the amd64 version of dapper.

**1) Add repos**

Open your sources list```
sudo gedit /etc/apt/sources.list
```
and add the following lines to it ```
deb http://www.beerorkid.com/compiz dapper main main-amd64
deb-src http://www.beerorkid.com/compiz dapper main main-amd64
```
If your sources list already contains these repos you dont need to add them again

**2) install graphics drivers**

**For nvidia**
run ```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install nvidia-glx
```

**For Ati**
follow [this]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=fglrx") guide to instal fglx
run ```
glxinfo
```
if it shows direct rendering: yes , then you are good to go.

**3) edit xorg.conf**

first back it up
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
**Nvidia only**; xorg configuration is included in fglx guide above
Then edit it
```
sudo gedit /etc/X11/xorg.conf
```
look for    Section "Module"   if this section contains  Load "dri"  or  Load "glcore"  comment them out like this ```
#	Load	"dri"
#	Load	"glcore"
```
Then ensure that this section contains ```
 	Load	"glx"
```
Scroll down to Section "Device" and ensure that the driver is nvidia and there is the renderaccel option so that this section will look a bit like this
```
Section "Device"
	Identifier	"NVIDIA Corporation NV41.0"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option "RenderAccel" "true"
EndSection
```
don't change the identifier or the BusID. The one above is only an example.

**end nvidia only**

**4) Now install xgl**
```
sudo aptitude install xserver-xgl libgl1-mesa libglitz-glx1
```
There are two ways to run xgl (**only do one**)

**Method 1, run as part of regular session**
edit gdm.conf-custom
```
sudo gedit /etc/gdm/gdm.conf-custom
```
At the bottom (in the servers bit) add this
**For nvidia**
```
[servers]
0=Xgl 

[server-Xgl]
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```
**For ATI**
```
 [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```
**ATI only**
Modify /etc/gdm/gdm.conf 
```
sudo gedit /etc/gdm/gdm.conf
```
And change
```
#0=Standard
1=Standard
```
Go to line 198 and change GdmXserverTimeout=10 to  (this one is very important!!!)
```
GdmXserverTimeout=50
```
**End ati only**

**Method 2, run as a separate session** (from [http://www.ubuntuforums.org/showthread.php?t=260452](http://www.ubuntuforums.org/showthread.php?t=260452) , untested by me)

create a script to start xgl
```
sudo gedit /usr/bin/startxgl.sh
```
and paste this in then save and exit
**For nvidia**
```
#!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session
```
**For ATI**
```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session
```
**For Both**
make the script executable
```
sudo chmod +x /usr/bin/startxgl.sh
```
 Then add the script to sessions
```
sudo gedit /usr/share/xsessions/xgl.desktop
```
paste this in then save and exit
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

**5) Installing beryl from source** not recommended for people that have repositories for beryl. Beryl is still in development and could cause kittens to die, nukes to go off and your computer to crash, you've been warned :p (as far as i know there are no repositories for amd64 dapper, if anybody knows of one please tell me).

First remove compiz
```
sudo aptitude remove compiz-core compiz-gnome cgwd csm
```

Run the following one line at a time so that you can identify any errors. 
Pay particular attention when you type ./autogen.sh --prefix=/usr as you may be informed of unmet dependencies. If you get informed of one install it (sudo aptitude install package) then go back to the last make clean line and carry on.
Please post the unmet dependency up here so that I can add it to this guide.

The following should be done in order.
Either build release 0.1.2 or the trunk release not both
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo apt-get update
sudo apt-get build-dep compiz
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev subversion libneon25-dev libapr0-dev libsvn0-dev
sudo update-alternatives --config automake
svn co svn://svn.beryl-project.org/beryl/tags/release-0.1.4/

ln -s ~/release-0.1.4/distro-specific-build-files/bdock/debian ~/release-0.1.4/bdock/
ln -s ~/release-0.1.4/distro-specific-build-files/beryl-core/debian ~/release-0.1.4/beryl-core/
ln -s ~/release-0.1.4/distro-specific-build-files/beryl-plugins/debian ~/release-0.1.4/beryl-plugins/
ln -s ~/release-0.1.4/distro-specific-build-files/beryl-dbus/debian ~/release-0.1.4/beryl-dbus/
ln -s ~/release-0.1.4/distro-specific-build-files/beryl-manager/debian ~/release-0.1.4/beryl-manager/
ln -s ~/release-0.1.4/distro-specific-build-files/beryl-settings/debian ~/release-0.1.4/beryl-settings/
ln -s ~/release-0.1.4/distro-specific-build-files/emerald/debian ~/release-0.1.4/emerald/
ln -s ~/release-0.1.4/distro-specific-build-files/emerald-themes/debian ~/release-0.1.4/emerald-themes/
ln -s ~/release-0.1.4/distro-specific-build-files/heliodor/debian ~/release-0.1.4/heliodor/

cd ~/release-0.1.4/beryl-core
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb

cd beryl-plugins
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-plugins-data*.deb beryl-plugins*.deb

cd emerald
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald*.deb

cd emerald-themes
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald-themes*.deb

cd beryl-settings
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-settings*.deb

cd beryl-manager
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-manager*.deb *.deb
```
Beryl should now be installed :D

[COLOR="Silver"]**To build Trunk release (latest version from repository), not remotely stable. If you use this method please bug report [http://bugs.beryl-project.org](http://bugs.beryl-project.org).**Includes extra packages not needed for general running of beryl.
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo apt-get update
sudo apt-get build-dep compiz
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev subversion libneon25-dev libapr0-dev libsvn0-dev
sudo update-alternatives --config automake
svn co svn://svn.beryl-project.org/beryl/trunk/

ln -s ~/trunk/distro-specific-build-files/bdock/debian ~/trunk/bdock/
ln -s ~/trunk/distro-specific-build-files/beryl-core/debian ~/trunk/beryl-core/
ln -s ~/trunk/distro-specific-build-files/beryl-plugins/debian ~/trunk/beryl-plugins/
ln -s ~/trunk/distro-specific-build-files/beryl-dbus/debian ~/trunk/beryl-dbus/
ln -s ~/trunk/distro-specific-build-files/beryl-manager/debian ~/trunk/beryl-manager/
ln -s ~/trunk/distro-specific-build-files/beryl-settings/debian ~/trunk/beryl-settings/
ln -s ~/trunk/distro-specific-build-files/emerald/debian ~/trunk/emerald/
ln -s ~/trunk/distro-specific-build-files/emerald-themes/debian ~/trunk/emerald-themes/
ln -s ~/trunk/distro-specific-build-files/heliodor/debian ~/trunk/heliodor/

cd trunk/beryl-core
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb libberylsettings*.deb

cd beryl-plugins
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-plugins-data*.deb beryl-plugins*.deb

cd emerald
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald*.deb libemeraldengine*.deb

cd emerald-themes
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald-themes*.deb

cd beryl-settings
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-settings*.deb

cd beryl-manager
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-manager*.deb beryl*.deb

cd beryl-dbus
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-dbus*.deb

cd bdock
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i bdock*.deb

cd heliodor
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i heliodor*.deb
```[/COLOR]

**6)Add beryl to startup programs**
System > Preferences > Sessions > Startup Programs
Add beryl-manager

**7) restart x **

**Important, If x fails to start do step 8**

press <ctrl><alt><back>
login and enjoy beryl :D

**8. only do if x fails to start**
go to terminal
<ctrl><alt><f1>
login
type ```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo reboot
```


Edit 1, changed svn to [http://svn.beryl-project.org/tags/release-0.1.1/](http://svn.beryl-project.org/tags/release-0.1.1/)
Edit 2
changed svn to svn://svn.beryl-project.org/beryl/tags/release-0.1.2/
Added links to debian build files. Added method to build trunk.

---

### Post by thoffland on 2006-10-21
An excellent how to!! Thanks for helping me get Beryl up and running on my 64 bit system!!

---

### Post by s_spiff on 2006-10-22
when I run :
```
cd release-0.1.1/beryl-core
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
```

I get this error :
```
make[1]: Entering directory `/home/alokshenoy/Misc./release-0.1.1/beryl-core'
make[2]: Entering directory `/home/alokshenoy/Misc./release-0.1.1/beryl-core'
cd . && autoheader
make[2]: Leaving directory `/home/alokshenoy/Misc./release-0.1.1/beryl-core'
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=[config.h] \
             /bin/sh ./config.status
config.status: creating [config.h]
config.status: error: cannot find input file: [config.h].in
make[1]: *** [stamp-h] Error 1
make[1]: Leaving directory `/home/alokshenoy/Misc./release-0.1.1/beryl-core'
make: *** [build-stamp] Error 2

```
whats is going wrong?

---

### Post by killkoy on 2006-10-22
run the following bits one line at a time and paste the entire output separatly for each command here.
```
cd release-0.1.1/beryl-core

make clean

./autogen.sh --prefix=/usr
```

---

### Post by myk.ism on 2006-10-24
thanks for the guide, i finally got it working ;]

i added beryl-manager to startup programs but i have to reload the beryl window manager after i log in to get it to work; any ideas why? there is an entry for "gnome-window-decorator" in startup programs, should it be removed?

---

### Post by h0ser81 on 2006-10-24
I followed the how to verbatim and Beryl runs and works great but I have two problems. 1. I can't switch themes at all and 2. I have no window decorations at all. I can swithc back and forth between Beryl and Metacity with no problems but as soon as I go to Beryl my window decorations vanish. Any help or ideas as to what's causing this? I have and ATI card and using fglrx.

---

### Post by killkoy on 2006-10-24
[quote=myk.ism]there is an entry for "gnome-window-decorator" in startup programs, should it be removed?[/quote]
Yes it should be fine to remove gnome-window-decorator.
[quote=h0ser81]I followed the how to verbatim and Beryl runs and works great but I have two problems. 1. I can't switch themes at all and 2. I have no window decorations at all. I can swithc back and forth between Beryl and Metacity with no problems but as soon as I go to Beryl my window decorations vanish. Any help or ideas as to what's causing this? I have and ATI card and using fglrx.[/quote]
I think you need to check that emerald is installed (search for it in synaptic)

---

### Post by kesman on 2006-10-24
Same problem here, no window decorations, emerald and emerald-themes -packages installed from synaptic. I have to run beryl-manager from terminal to get it running, and it prints out:
```

user@host:~$ beryl-manager
user@host:~$ XGL Present
beryl-xgl: Plugin 'settings' already active
beryl-xgl: No GLXFBConfig for depth 32
beryl-xgl: No GLXFBConfig for depth 32
beryl-xgl: No GLXFBConfig for depth 32
Initiating splash
beryl-xgl: No GLXFBConfig for depth 32
beryl-xgl: No GLXFBConfig for depth 32
beryl-xgl: No GLXFBConfig for depth 32

```

---

### Post by h0ser81 on 2006-10-24
I get the same error when running it from a terminal too. Also get this when trying to run emerald from a terminal. emerald: Screen 0 on display ":1.0" already has a decoration manager; try using the --replace option to replace the current decoration manager. When I run it with the --replace option I still have no window decorations.

---

### Post by killkoy on 2006-10-24
You could try using an older or newer version of beryl.
To use 0.1.0 change the svn line and the one after to the following
```
svn co http://svn.beryl-project.org/tags/release-0.1.0/

cd release-0.1.0/beryl-core
```
To use trunk version (being developed) change the svn line and the one after to the following```
svn co http://svn.beryl-project.org/trunk/


cd trunk/beryl-core
```

---

### Post by kesman on 2006-10-25
I don't think that solves anything, I had this exact same problem with compiz too, with same error messages and all...
I found something related to this on another forum, 
[URL="http://www.rage3d.com/board/showthread.php?p=1334361825"]http://www.rage3d.com/board/showthread.php?p=1334361825
[/URL]
was the url. It's about some patch to beryl, but I'm not sure if it's gonna work with this version of beryl, or even with 64-bit beryl at all :P

---

### Post by kesman on 2006-10-26
Oh man, seems like there is no answer to this, I've searched trough many forums, and the best solution so far is to change to 32-bit distro, since it seems to be too complicated to get this thing working under 64-bit.. Damn :P

---

### Post by Rooy on 2006-11-23
Hi, I can't checkout the beryl svn:

~/beryl-svn$ svn co [http://svn.beryl-project.org/trunk/](http://svn.beryl-project.org/trunk/)
svn: PROPFIND request failed on '/trunk'
svn: PROPFIND of '/trunk': 405 Method Not Allowed (http://svn.beryl-project.org)rooy@vikb:~/beryl-svn$ svn co [http://svn.beryl-project.org/tags/release-0.1.1/](http://svn.beryl-project.org/tags/release-0.1.1/)
svn: PROPFIND request failed on '/tags/release-0.1.1'
svn: PROPFIND of '/tags/release-0.1.1': 405 Method Not Allowed ([http://svn.beryl-project.org](http://svn.beryl-project.org))

How can I get the source code?

Edit: the link is svn://svn.beryl-project.org/trunk/ [http://wiki.beryl-project.org/index.php/Compile/Sources](http://wiki.beryl-project.org/index.php/Compile/Sources)

---

### Post by vloveya08 on 2006-11-26
I'm trying to do this but for some reason it says it can't do whatever the command "svn" does.
> 
valerie@valerie2:~$ svn co [http://svn.beryl-project.org/trunk/](http://svn.beryl-project.org/trunk/)
bash: svn: command not found

what can I do?  I haven't changed anything major on my Edgy, and its an AMD Turion 64 processor (dunno if that helps) but it seems weird to me that its not recognizing a command.  I'm kinda new, but not completely so if you could make it as basic as possible (i follow directions well :D )

HELP!

Thanks.

---

### Post by killkoy on 2006-11-28
```
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev subversion libneon25-dev libapr0-dev libsvn0-dev
```
part of guide

specifically you need the
```
sudo aptitude install subversion
```

---

### Post by vloveya08 on 2006-11-28
thank you so much...except now that that's working I have another issue..

I come up with this error when I try to extract the beryl core:
> 
valerie@valerie2:~/release-0.1.2$ fakeroot dpkg-buildpackage
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is

I don't know what to do...

thank you for all your help.

---

### Post by killkoy on 2006-11-30
run these commands
```
ln -s ~/release-0.1.2/distro-specific-build-files/bdock/debian ~/release-0.1.2/bdock/
ln -s ~/release-0.1.2/distro-specific-build-files/beryl-core/debian ~/release-0.1.2/beryl-core/
ln -s ~/release-0.1.2/distro-specific-build-files/beryl-plugins/debian ~/release-0.1.2/beryl-plugins/
ln -s ~/release-0.1.2/distro-specific-build-files/beryl-dbus/debian ~/release-0.1.2/beryl-dbus/
ln -s ~/release-0.1.2/distro-specific-build-files/beryl-manager/debian ~/release-0.1.2/beryl-manager/
ln -s ~/release-0.1.2/distro-specific-build-files/beryl-settings/debian ~/release-0.1.2/beryl-settings/
ln -s ~/release-0.1.2/distro-specific-build-files/emerald/debian ~/release-0.1.2/emerald/
ln -s ~/release-0.1.2/distro-specific-build-files/emerald-themes/debian ~/release-0.1.2/emerald-themes/
ln -s ~/release-0.1.2/distro-specific-build-files/heliodor/debian ~/release-0.1.2/heliodor/
```
Then repeat step 5

---

### Post by vloveya08 on 2006-11-30
Thank you so much for your help...

I figured out a mildly easier way...

After running the svn command, I saw a folder with the release number on it (0.1.2)  I opened the file and saw a file named "makefile."  I executed it and it installed the entire program for me.  Then I restarted and it froze on me.  I forgot to start the XGl so I ran terminal and got that working and now it works wonderfully.

Thank you so much for your help.

---

### Post by killkoy on 2006-12-01
That way will work fine, however it doesn't build .deb packages so in may be harder to remove and wont be included in the ubuntu package management system (apt)

---

### Post by espulsione on 2006-12-17
Thanks for your guide. I'd really like to get beryl up and running on amd64, but I got stuck at the first ./autogen.sh statement. At some point the script starts "checking for BERYL" and stops with an error that "xcomposite >= 0.3" and that the actual version of xcomposite is 0.2.2.2. Is there a way to resolve this?

Cheers, Peter

---

### Post by killkoy on 2006-12-17
run the step after the ./autogen.sh statement as well and post the output of that

---

### Post by espulsione on 2006-12-20
Sorry I took so long: I run Kubuntu and I did a setup of Ubuntu to check if my problem with compiling Beryl were related to that. I got the same error messages. The first from autogen.sh:

```
checking for BERYL... configure: error: Package requirements (libpng            xcomposite >= 0.3                xfixes                  xdamage                xrandr                   ice                     sm                  xinerama   libstartup-notification-1.0 >= 0.7) were not met:

Requested 'xcomposite >= 0.3' but version of Xcomposite is 0.2.2.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BERYL_CFLAGS
and BERYL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Then when I try to do the next step:

```
peter@desktop:~/release-0.1.2/beryl-core$ fakeroot dpkg-buildpackage
dpkg-buildpackage: source package is beryl-core
dpkg-buildpackage: source version is 0.1.2-0ubuntu1
dpkg-buildpackage: source changed by Manuel Evano <reggaemanu@beryl-project.org>
dpkg-buildpackage: host architecture amd64
dpkg-checkbuilddeps: Unmet build dependencies: x11proto-gl-dev (>= 1.4.7)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
```

Of course I checked for the dependencies:

```
peter@desktop:~/release-0.1.2/beryl-core$ sudo apt-get install x11proto-gl-dev
Reading package lists... Done
Building dependency tree... Done
x11proto-gl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I ckecked the version of x11proto-gl-dev and it is 1.4.3.

Do I have to use an older version of Beryl or is there some other explanation?

---

### Post by killkoy on 2006-12-22
ok, if you run dapper add this repository to your sources list
```
deb http://ubuntu.beryl-project.org dapper main
```
If you run edgy
```
deb http://ubuntu.beryl-project.org edgy main all
```
Then use the following command for both
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

---

### Post by cborga1985 on 2007-01-26
You need the compiz repository already added to your sources but here is an updated guide. This guide does use a workaround because beryl-settings depends on beryl-settings-bindings. I tried to get beryl-settings-bindings to compile with the debian control but it won't because there is not a updated python-support deb. In the control it needs 0.5.3 and Dapper only has 0.1.1 and a new from Edgy would not compile because it depended on debhelper 5.0.27 I think. Anyway, this will work fine if you follow the first part about drivers and stuff first.
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo apt-get update
sudo apt-get build-dep compiz
sudo aptitude install fakeroot libtool automake1.9 librsvg2-dev x11proto-gl-dev subversion libneon25-dev libapr0-dev libsvn0-dev
sudo update-alternatives --config automake
svn co svn://svn.beryl-project.org/beryl/branches/beryl-0.1.99.2/

ln -s ~/beryl-0.1.99.2/distro-specific-build-files/bdock/debian ~/beryl-0.1.99.2/bdock/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/beryl-core/debian ~/beryl-0.1.99.2/beryl-core/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/beryl-plugins/debian ~/beryl-0.1.99.2/beryl-plugins/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/beryl-dbus/debian ~/beryl-0.1.99.2/beryl-dbus/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/beryl-manager/debian ~/beryl-0.1.99.2/beryl-manager/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/beryl-settings/debian ~/beryl-0.1.99.2/beryl-settings/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/emerald/debian ~/beryl-0.1.99.2/emerald/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/emerald-themes/debian ~/beryl-0.1.99.2/emerald-themes/
ln -s ~/beryl-0.1.99.2/distro-specific-build-files/heliodor/debian ~/beryl-0.1.99.2/heliodor/

cd ~/beryl-0.1.99.2/beryl-core
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-core*.deb beryl-dev*.deb

cd beryl-plugins
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-plugins-data*.deb beryl-plugins*.deb libberyldecoration*.deb

cd emerald
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald*.deb

cd emerald-themes
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i emerald-themes*.deb

cd beryl-settings-bindings
make clean
./autogen.sh --prefix=/usr
make
sudo checkinstall
change the name to beryl-settings-bindings
change the version to 0.1.99.2

cd beryl-settings
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-settings*.deb

cd beryl-manager
make clean
./autogen.sh --prefix=/usr
fakeroot dpkg-buildpackage
cd ..
sudo dpkg -i beryl-manager*.deb *.deb

```

---

### Post by pelle@xburk on 2007-02-13
Hey guys, I am running Kubuntu Dapper 6.06 on an amd64 pocessor and with an nVIDIA graphics card.  When I use this guide I get a few errors that wont let me install it.

ERROR 1

> pelle@xburk:~$ sudo update-alternatives --config automake
Password:

There is only 1 program which provides automake
(/usr/bin/automake-1.9). Nothing to configure.
pelle@xburk:~$


ERROR 2

> pelle@xburk:~$ cd ~/release-0.1.4/beryl-core
pelle@xburk:~/release-0.1.4/beryl-core$ make clean
make: *** No rule to make target `clean'.  Stop.
pelle@xburk:~/release-0.1.4/beryl-core$


ERROR 3

> pelle@xburk:~/release-0.1.4/beryl-core$ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

./autogen.sh: line 11: intltoolize: command not found
pelle@xburk:~/release-0.1.4/beryl-core$    

Is anybody else having the same problems?  Can somebody help me?

---

### Post by killkoy on 2007-02-19
The first two are expected and nothing to worry about
for the last one have you installed libtool ?

---

### Post by thepacsays on 2007-02-23
i've been trying to get beryl to work but i have a problem. i have an integrated graphics driver from intel on my hp vectra.  how do i use beryl then...i unfortunately don't have nvidia or ati.  if anyone can help me i'd appreciate it.

---

### Post by cborga1985 on 2007-03-21
> **pelle@xburk said:**
> Hey guys, I am running Kubuntu Dapper 6.06 on an amd64 pocessor and with an nVIDIA graphics card.  When I use this guide I get a few errors that wont let me install it.

ERROR 1



ERROR 2



ERROR 3



Is anybody else having the same problems?  Can somebody help me?

you could just use my repository

---

