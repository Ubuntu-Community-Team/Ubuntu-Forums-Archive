---
title: "[How-To] Install Amarok with MTP-Device Support"
date: 2006-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by ButteBlues on 2006-12-10
**[size=4]The scripts are broken at the moment. Use manual instructions please.**[/size]


As of recent builds of Amarok by the devs, and the release of a recent libmtp, it is now possible to install Amarok with support for your MTP device.

**Note: This article was written mainly for Feisty users. However, it is possible to install this without Feisty. You will need to locate the corresponding updated libs which can be found in [http://archive.ubuntu.com/pool](http://archive.ubuntu.com/pool).**

**Method 1: Installation Script**

Download one of the tarballs at the bottom of this post. Untar them, read the README, and go.

If you are using Edgy, use 1.2.2. If you are using Feisty, either tarball should work.


**Method 2: Install yourself**

These steps are a copy/paste of the same steps used in the install script.

1. Upgrade the system

```
sudo apt-get update
sudo apt-get dist-upgrade
```

2. Make the install directory.

```
cd ~
mkdir amarok-with-mtp_dir
cd amarok-with-mtp_dir
```

3. Obtain the files.

```
[color=red]If on Feisty:[/color]
wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.4-0.3ubuntu2_i386.deb"
wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.4-0.3ubuntu2_i386.deb"[/color]

[color=blue]If on Edgy:[/color]
sudo apt-get source amarok

[color=green]Do either way:[/color]
wget "http://downloads.sourceforge.net/libmtp/libmtp-0.1.0.tar.gz?modtime=1165440680&big_mirror=0"
```

4. Install libmtp.

```
tar -zxvf libmtp-0.1.0.tar.gz
cd libmtp-0.1.0/
./configure --prefix=/usr
sudo make
sudo checkinstall
sudo cp libmtp.rules /etc/udev/rules.d/
cd ../
```

5. Install Amarok

```
[color=red]If on Feisty:[/color]

sudo dpkg -i amarok_1.4.4-0.3ubuntu2_i386.deb
sudo dpkg -i amarok-xine_1.4.4-0.3ubuntu2_i386.deb

[color=blue]If on Edgy:[/color]
sudo chmod 700 amarok*
cd amarok-1.4*
sudo apt-get build-dep amarok
./configure --with-njb --with-mtp --prefix=`kde-config --prefix`
make
sudo make install
sudo apt-get install amarok-xine

```

6. Choose one of the below options:

6A. Restart the computer.

6B. Run the following command, and restart Amarok:

```
sudo /etc/init.d/udev restart
```

7. You're done. Just plug your MTP device in with Amarok open and it should auto-detect.



Changelog:
11.12.2006 - Added 1.2.2 bug fix.
11.12.2006 - Added 1.2.1 bug fix.
11.12.2006 - First beta for Edgy support, 1.2.0.
11.12.2006 - fixed minor typo.

---

### Post by splitsch on 2006-12-11
Hi!
It seems that there is an error in the manual installation instructions!
Indeed, for the second package we donwloadn, the instruction should be
```
wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.4-0.3ubuntu2_i386.deb"
```
and Not ```
wget "http://archive.ubuntu.co/ubuntu/pool/main/a/amarok/amarok-xine_1.4.4-0.3ubuntu2_i386.deb"
```
(notice the "M" missing in ubuntu.coM)

Anyway, it's a great script :)
Thanks !

Splitsch

---

### Post by splitsch on 2006-12-11
Hello !
I get a dependencies error.
libmtp install itself fine, then, whenever I try to install either amarok or amarok-xine, I have depedencies error, about  kdelibs4c2a, libc6, libfontconfig1, libgcc1, libmtp2, libqt3-mt.
Here is the error message (in french)

```
dpkg : des problèmes de dépendances empêchent la configuration de amarok :
 amarok dépend de kdelibs4c2a (>= 4:3.5.5-1) ; cependant :
  La version de kdelibs4c2a sur le système est 4:3.5.5-0ubuntu3.
 amarok dépend de libc6 (>= 2.5-0ubuntu1) ; cependant :
  La version de libc6 sur le système est 2.4-1ubuntu12.
 amarok dépend de libfontconfig1 (>= 2.4.0) ; cependant :
  La version de libfontconfig1 sur le système est 2.3.2-7ubuntu2.
 amarok dépend de libgcc1 (>= 1:4.1.1-20ubuntu1) ; cependant :
  La version de libgcc1 sur le système est 1:4.1.1-13ubuntu5.
 amarok dépend de libmtp2 (>= 0.0.18) ; cependant :
  Le paquet libmtp2 n'est pas installé.
 amarok dépend de libqt3-mt (>= 3:3.3.7) ; cependant :
  La version de libqt3-mt sur le système est 3:3.3.6-3ubuntu3.
 amarok dépend de libstdc++6 (>= 4.1.1-20ubuntu1) ; cependant :
  La version de libstdc++6 sur le système est 4.1.1-13ubuntu5.
dpkg : erreur de traitement de amarok (--install) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 amarok

```

I'm running ubuntu edgy eft, fully updated...Maybe my sources.list isn't good enough...?
Or the mirror need time to update...
Do you have any solution, please ?

Thanks a lot :)

---

### Post by ButteBlues on 2006-12-11
I'm running feisty, so some of those packages reflect that.

I'll add that as a note.


If needed, additional packages can be found in the archive.ubuntu.com pool for those libraries. They shouldn't break anything, but if they do, reverting is easy enough.

---

### Post by splitsch on 2006-12-11
Hello!
Okay, I give up :p
Indeed, all the depedencies aren't there :s
Anyway, if you have any idea how to get it work on edgy, I'll be the one happy :d

Thanks

---

### Post by ButteBlues on 2006-12-11
I'll add edgy support shortly. :)

---

### Post by ButteBlues on 2006-12-11
First test of Edgy support has been added.

I need edgy users to check both the Manual and scripted installation (choose amarok-with-mtp_1.2.0.tar.gz if trying the script under edgy).

Please report any errors here.

---

### Post by jrjazzman on 2006-12-11
Anybody know why the Amarok in the official repos would lack mtp and other features?  I continue to be frustrated with the repository method of installing software.  Seems like a good idea, but it just doesn't seem to work in lots of cases.

Edit:

I got the following error message when running the 1.1.0 script on edgy:

./amarok-with-mtp: line 55: unexpected EOF while looking for matching `''
./amarok-with-mtp: line 62: syntax error: unexpected end of file

Edit 2:

appears that the script tries to mkdir a directory with the same name as the script file.

---

### Post by ButteBlues on 2006-12-11
> **jrjazzman said:**
> Anybody know why the Amarok in the official repos would lack mtp and other features?  I continue to be frustrated with the repository method of installing software.  Seems like a good idea, but it just doesn't seem to work in lots of cases.

Edit:

I got the following error message when running the 1.1.0 script on edgy:

./amarok-with-mtp: line 55: unexpected EOF while looking for matching `''
./amarok-with-mtp: line 62: syntax error: unexpected end of file

Edit 2:

appears that the script tries to mkdir a directory with the same name as the script file.
1. It needs a compatible Libmtp version.

2. The amarok in Feisty repos is built with mtp support. Just not the Edgy one. ;)


===

For edgy, please try 1.2.0. It accounts for Edgy not being compatible with certain libs.

I'll be looking through for those bugs.

---

### Post by ButteBlues on 2006-12-11
Script and instructions updated to reflect errors noted from jrjazzman.

---

### Post by jrjazzman on 2006-12-11
When I execute this:

./configure --with-njb --with-mtp --prefix=`kde-config --prefix`

I get this:

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

Know how I can fix this?

---

### Post by ButteBlues on 2006-12-11
Ah! I found one step in the script but not in the list of things! :)

Run ```
sudo apt-get build-dep amarok
``` before the ./configure.

---

### Post by jrjazzman on 2006-12-11
Are these make errors normal?

make[2]: Entering directory `/home/jross/dls/amarok/amarok/amarok-1.4.3/amarok'
make[2]: *** No rule to make target `all'.  Stop.
make[2]: Leaving directory `/home/jross/dls/amarok/amarok/amarok-1.4.3/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jross/dls/amarok/amarok/amarok-1.4.3'
make: *** [all] Error 2

---

### Post by ButteBlues on 2006-12-11
It seems as if they had issues doing the make. Try running "sudo make install" and then completing as normal.

---

### Post by jrjazzman on 2006-12-11
> **a simple façade said:**
> It seems as if they had issues doing the make. Try running "sudo make install" and then completing as normal.

The result is:

make[1]: Entering directory `/home/jross/dls/amarok/amarok/amarok-1.4.3/amarok'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/jross/dls/amarok/amarok/amarok-1.4.3/amarok'
make: *** [install-recursive] Error 1

---

### Post by ButteBlues on 2006-12-11
huh.

```
make clean
./configure --with-njb --with-mtp --prefix=`kde-config --prefix`
sudo make
sudo make install
```

---

### Post by jrjazzman on 2006-12-11
I had to run configure as root.  For some reason all the dirs were owned by root.  Suppose I could have done a chown an all.  Thanks for the help.  Unfortunately, my creative zen micro still won't detect.  In "media devices", should MTP be in the drop down list?  I don't see it.

edit: Just noticed that that help > about amarok shows a oct 15 build date.  I think apt-get installed the repo's amarok over the custom built version when I ran apt-get install amarok-xine.

---

### Post by ButteBlues on 2006-12-11
> **jrjazzman said:**
> I had to run configure as root.  For some reason all the dirs were owned by root.  Suppose I could have done a chown an all.  Thanks for the help.  Unfortunately, my creative zen micro still won't detect.  In "media devices", should MTP be in the drop down list?  I don't see it.

edit: Just noticed that that help > about amarok shows a oct 15 build date.  I think apt-get installed the repo's amarok over the custom built version when I ran apt-get install amarok-xine.
That shouldn't be the case. Amarok-xine should just be the XINE engine.

Go to Tools > Configure > Media Devices and see if MTP Device is one of the listed options.

---

### Post by jrjazzman on 2006-12-11
> **a simple façade said:**
> That shouldn't be the case. Amarok-xine should just be the XINE engine.

Go to Tools > Configure > Media Devices and see if MTP Device is one of the listed options.

amarok-xine depends on amarok according to synaptic.  I uninstalled both then reinstalled from the source, skipping the install of amarok-xine.  Then in amarok, under Settings > Configure Amarok >  Media Devices, sda4 is listed, but it's set to "do not handle" and MTP is not in the list of available choices.

sda4 is an unmounted partition I forgot about, not sure why amarok thinks it's a music device.

---

### Post by ButteBlues on 2006-12-11
> **jrjazzman said:**
> amarok-xine depends on amarok according to synaptic.  I uninstalled both then reinstalled from the source, skipping the install of amarok-xine.  Then in amarok, under Settings > Configure Amarok >  Media Devices, sda4 is listed, but it's set to "do not handle" and MTP is not in the list of available choices.

sda4 is an unmounted partition I forgot about, not sure why amarok thinks it's a music device.
That is odd. Perhaps only 1.4.4 has proper support for MTP.

---

### Post by jrjazzman on 2006-12-11
ok.. making progress.  I reinstalled libmtp, then reinstalled amarok (twice).  Now amarok shows the option for mtp.  however, it still doesn't detect the device.  

when i plug in the device, amarok spits this to stdout

```
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:     DeviceManager: getDevice called with name argument = camera
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00069s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.00086s
amarok:   [DeviceManager::mediumAdded] Obtained medium name is camera, id is: /org/freedesktop/Hal/devices/usb_device_41e_4130_0105255182038FD6_if0
amarok: BEGIN: void MediaDeviceManager::slotMediumAdded(const Medium*, QString)
amarok: END__: void MediaDeviceManager::slotMediumAdded(const Medium*, QString) - Took 4.5e-05s
amarok: BEGIN: void MountPointManager::mediumAdded(const Medium*)
amarok: END__: void MountPointManager::mediumAdded(const Medium*) - Took 4.1e-05s
amarok: END__: void DeviceManager::mediumAdded(QString) - Took 0.0012s

```

also, mtp-detect finds the device with no problem.

edit:

ok, so I manually added the device and it works!  cool!

---

### Post by ButteBlues on 2006-12-11
Awesome! :)

---

### Post by splitsch on 2006-12-12
Hello!
Everything work up to "make" in the amarok building process.
Here is the error:
```

make  all-recursive
make[1]: entrant dans le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4 »
Making all in amarok
make[2]: entrant dans le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4/amarok »
make[2]: *** Pas de règle pour fabriquer la cible « all ». Arrêt.
make[2]: quittant le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4/amarok »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4 »
make: *** [all] Erreur 2

```
Do you have any idea where it comes from.
It throu me the same whenever I try make clean.
With or without any "sudo" in front of it !

Thanks

---

### Post by ButteBlues on 2006-12-12
Are you using Edgy or Feisty? If you are using Feisty, you do not need to build Amarok - just libmtp. The Amarok in the Feisty repos is built with mtp enabled already.

---

### Post by jrjazzman on 2006-12-12
> **splitsch said:**
> Hello!
Everything work up to "make" in the amarok building process.
Here is the error:
```

make  all-recursive
make[1]: entrant dans le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4 »
Making all in amarok
make[2]: entrant dans le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4/amarok »
make[2]: *** Pas de règle pour fabriquer la cible « all ». Arrêt.
make[2]: quittant le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4/amarok »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/yannick/amarok-with-mtp_dir/amarok-1.4.4 »
make: *** [all] Erreur 2

```
Do you have any idea where it comes from.
It throu me the same whenever I try make clean.
With or without any "sudo" in front of it !

Thanks

I don't really know what the error message says, but it looks like similar to a problem I had.  I solved it by running the make commands AND the configure command with sudo.  The reason for this is that directories were created as owned by root, and configure was unable to copy into them.  Some kind of chmod would have fixed it also, but sudo was easier.

---

### Post by saixx on 2006-12-18
> **jrjazzman said:**
> ok.. making progress.  I reinstalled libmtp, then reinstalled amarok (twice).  Now amarok shows the option for mtp.  however, it still doesn't detect the device.  

when i plug in the device, amarok spits this to stdout

```
amarok: BEGIN: Medium* DeviceManager::getDevice(QString)
amarok:     DeviceManager: getDevice called with name argument = camera
amarok: BEGIN: QStringList DeviceManager::getDeviceStringList()
amarok: END__: QStringList DeviceManager::getDeviceStringList() - Took 0.00069s
amarok: END__: Medium* DeviceManager::getDevice(QString) - Took 0.00086s
amarok:   [DeviceManager::mediumAdded] Obtained medium name is camera, id is: /org/freedesktop/Hal/devices/usb_device_41e_4130_0105255182038FD6_if0
amarok: BEGIN: void MediaDeviceManager::slotMediumAdded(const Medium*, QString)
amarok: END__: void MediaDeviceManager::slotMediumAdded(const Medium*, QString) - Took 4.5e-05s
amarok: BEGIN: void MountPointManager::mediumAdded(const Medium*)
amarok: END__: void MountPointManager::mediumAdded(const Medium*) - Took 4.1e-05s
amarok: END__: void DeviceManager::mediumAdded(QString) - Took 0.0012s

```

also, mtp-detect finds the device with no problem.

edit:

ok, so I manually added the device and it works!  cool!

i have the same problem, mtp-detect finds it but amarok doesnt. could you explain how you added it manually? do you need to mount it or something?

---

### Post by jrjazzman on 2006-12-18
> **saixx said:**
> i have the same problem, mtp-detect finds it but amarok doesnt. could you explain how you added it manually? do you need to mount it or something?

I didn't mount anything.  I went to settings > configure amarok > media devices.  Clicked Add Device, plugin = MTP, Name = zen.   That's all.

I think the name could have been anything.  It probably assumes you'll only have one mtp device hooked up at a time.

---

### Post by saixx on 2006-12-18
> **jrjazzman said:**
> I didn't mount anything.  I went to settings > configure amarok > media devices.  Clicked Add Device, plugin = MTP, Name = zen.   That's all.

I think the name could have been anything.  It probably assumes you'll only have one mtp device hooked up at a time.

heh, my amarok doesnt show a "plugin = MTP". any ideas?

edit: never mind, i got gnomad2 working :)

---

### Post by czheng on 2006-12-20
On Edgy, tried to use your script and got the following error just after answering NO to whether I'm using Feisty:

./amarok-with-mtp: line 29: syntax error near unexpected token `do'
./amarok-with-mtp: line 29: `do wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.4-0.3ubuntu2_i386.deb" && wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.4-0.3ubuntu2_i386.deb"'

---

### Post by ButteBlues on 2006-12-20
> **czheng said:**
> On Edgy, tried to use your script and got the following error just after answering NO to whether I'm using Feisty:

./amarok-with-mtp: line 29: syntax error near unexpected token `do'
./amarok-with-mtp: line 29: `do wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.4-0.3ubuntu2_i386.deb" && wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.4-0.3ubuntu2_i386.deb"'
Looks like a bug. Start the manual instructions in first post at step 3. :)

---

### Post by mkw87 on 2006-12-22
mtp-detect finds my Creative Vision M fine, but the MTP plugin option does not show up in Amarok.  I have the latest version (1.4.4).  Any ideas?

---

### Post by freshanointing on 2006-12-23
Finally I have managed to install **Amarok** with **MTP Support**.  Make sure you have all the deps installed.  Open a terminal window and copy paste (step by step) each line. Here it is:


[B]
Installing MTP from SVN:[/B]
*(Gathered from many sources here and there)*

[FONT="Arial Narrow"]_Start Copy_[/FONT]
[FONT="Courier New"][INDENT]cvs -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp login
cvs -z3 -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp co -P libmtp


cd libmtp
./autogen.sh
./configure --prefix=/usr
make
sudo make install
sudo cp libmtp.rules /etc/udev/rules.d/
sudo bash hotplug.sh[/INDENT][/FONT]
[FONT="Arial Narrow"]_End Copy_[/FONT]

[I](Answere No when asking "Do you also want to install the old hotplug support (y/n)?
")[/I]

[FONT="Arial Narrow"]_Start Copy_[/FONT]
[FONT="Courier New"][INDENT]
make clean[/INDENT][/FONT]
[FONT="Arial Narrow"]_End Copy_[/FONT]


**Installing Amarok from SVN:**
*([http://amarok.kde.org/wiki/Installation_HowTo#Building_SVN_Amarok]("http://amarok.kde.org/wiki/Installation_HowTo#Building_SVN_Amarok"))*

[FONT="Arial Narrow"]_Start Copy_[/FONT]
[FONT="Courier New"][INDENT]svn co -N svn://anonsvn.kde.org/home/kde/trunk/extragear/multimedia
cd multimedia
svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kde-common/admin
svn up amarok

make -f Makefile.cvs
./configure --with-libmtp --enable-debug=full --prefix=`kde-config --prefix`
make
sudo make install 
make clean[/INDENT][/FONT]
[FONT="Arial Narrow"]_End Copy_[/FONT]

I encountered some errors my self at the end of my make install but i did not have any problems later on. Hope this helps !:-D

---

### Post by ButteBlues on 2006-12-23
> **mkw87 said:**
> mtp-detect finds my Creative Vision M fine, but the MTP plugin option does not show up in Amarok.  I have the latest version (1.4.4).  Any ideas?
The 1.4.4 version offered up on kubuntu.org for Edgy users wasn't built with MTP support, so you'll need to build Amarok.

---

### Post by maebe on 2006-12-23
I am having touble when I get to step #4 with amarok with MTP support.

here is what happens.

 cd libmtp-0.1.0.tar.gz
bash: cd: libmtp-0.1.0.tar.gz: Not a directory
mark@mark-desktop:~$

---

### Post by ButteBlues on 2006-12-23
libmtp-0.1.0.tar.gz is not a directory.


libmtp-0.1.0/ *is*.


So,

```
cd libmtp-0.1.0/
```


Accordingly fixed in the first post. A rewrite of this script is coming by Christmas Day.

---

### Post by maebe on 2006-12-23
I tried it using the script since last time, this is where I am at. I am new to Ubuntu only about 4 days so I might be in over head.

 ./amarok-with-mtp
Welcome to my script. This bash script uses a few simple commands to build a recent version of libmtp, and then install a recent version of the Amarok media player so that you may use Amarok with your MTP device, such as a Creative Zen.



Before we can proceed, please enter your password at the prompt. By doing so, you admit that I have no liability if something were to go wrong.
Updating your system.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_US
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Setting up directories.
mkdir: cannot create directory `amarok-with-mtp_dir': File exists
Now downloading the required files.
Retreiving amarok debian packages.
Are you using Feisty Fawn Testing Release? Y/N
N
./amarok-with-mtp: line 29: syntax error near unexpected token `do'
./amarok-with-mtp: line 29: `do wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.4-0.3ubuntu2_i386.deb" && wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.4-0.3ubuntu2_i386.deb"'
mark@mark-desktop:~/Desktop$

---

### Post by ButteBlues on 2006-12-23
maebe - The scripts are bugged out at the moment. Use the manual instructions starting at "3. Obtain the files."

---

### Post by Dr_Deadmeat on 2006-12-24
I still doesent get it to work here. I am using Feisty on this computer, and when I try to start Amarok I get this message

> KLibLoader could not load the plugin:
libamarok_mtp-mediadevice

Error message:
libmtp.so.2: cannot open shared object file: No such file or directory

When I try a mtp-detect I get the following message:
```
andreas@baerbar:~/.amarok-with-mtp_dir/libmtp-0.1.0$ mtp-detect 
Found non-autodetected device "SanDisk Sansa m240" on USB bus...
usb_claim_interface(): Device or resource busy
Connection error.
No devices.
andreas@baerbar:~/.amarok-with-mtp_dir/libmtp-0.1.0$ 
```

Is the message I get in my terminal right? And do anyone know what the problem with Amarok is?

---

### Post by ButteBlues on 2006-12-24
The terminal message seems a little odd.


Since you're on feisty, libmtp 0.1.0 is in the repos now.

```
sudo apt-get install libmtp2 libmtp-dev
sudo aptitude reinstall amarok
```

---

### Post by Dr_Deadmeat on 2006-12-25
When I connected my Creative Zen micro, mtp did detect it, (even though it is broken) and I got a lot of output with info about the device. But now Amarok has stopped working on my computer. when I start Amarok, it just wont start (and when I start it in a terminal/konsole, I get no output). I've tried to reinstall Amarok many times without luck... I would preffer things to work on that computer... I am almost thinking about moving back to dapper were everything I wanted worked (I am not sure if that will help my MP3-player much since I got that after updating to Feisty) =P

Anyhow... Do anyone know what could make this happen? Any help is appreciated.

EDIT: I've tried to just install it from the repos, but things stil doesent work (looks like I can see a bit longer too I can format my c:\ drive with windows xp and replace it with dos and windows 3.11)

---

### Post by ButteBlues on 2006-12-26
Feisty's Amarok appears to be experiencing some severely odd bugs at the moment.

You can search on these forums for the how-to on installing gnomad2 - which should work. :)

---

### Post by ErikTheRed on 2006-12-26
Great how-to! I can use my Zune with Amarok now.

---

### Post by cainlevy on 2006-12-27
Installing with Edgy, and so far have had to take these extra steps:

* Had to `sudo apt-get install build-essential` because of configure complaining that gcc couldn't compile executables.
* Had to `sudo apt-get install libusb-dev` because of configure for libmtp complaining about missing the usb libraries
* `sudo checkinstall` does nothing ... I ran `sudo make install` instead.

Also, [http://archive.ubuntu.com/pool](http://archive.ubuntu.com/pool) returns a 404.

I think I've finished the tutorial, but Amarok still isn't detecting my iRiver Clix. I'm going to just restart my computer...

---

### Post by ErikTheRed on 2006-12-27
I'm not sure if this problem is zune related or not but i can connect my zune and browse its contents via amarok with mtp support but when I try to transfer files to it amarok freezes.

I'm using edgy and I followed your how-to to the T.

---

### Post by ButteBlues on 2006-12-27
It could be that the Zune introduced new protocols that aren't implemented in libmtp yet.

Try installing gnomad2 via the howto on this forum (you shouldn't need to compile libmtp again; just gnomad2) and see if that works betterforyou.

---

### Post by ErikTheRed on 2006-12-27
> **a simple façade said:**
> It could be that the Zune introduced new protocols that aren't implemented in libmtp yet.

Try installing gnomad2 via the howto on this forum (you shouldn't need to compile libmtp again; just gnomad2) and see if that works betterforyou.

Ok I'll try that when I get done with work today. From what I've heard elsewhere the Zune may have introduced new protocols like you said. I'll give gnomad2 a try though.

---

### Post by djsamsel on 2006-12-28
when i try to configure libmtp i get the following error. any suggestions?

configure: error: I can't find the libusb libraries on your system. You
        may need to set the LDFLAGS environment variable to include the
        search path where you have libusb installed before running
        configure (e.g. setenv LDFLAGS=-L/usr/local/lib)

---

### Post by ButteBlues on 2006-12-28
> **djsamsel said:**
> when i try to configure libmtp i get the following error. any suggestions?

configure: error: I can't find the libusb libraries on your system. You
        may need to set the LDFLAGS environment variable to include the
        search path where you have libusb installed before running
        configure (e.g. setenv LDFLAGS=-L/usr/local/lib)
Try:

```
sudo apt-get install libusb libusb-dev
```

---

### Post by djsamsel on 2006-12-28
thanks, that got me to the command 

sudo apt-get build-dep amarok

to which i received 
E: Build-dependencies for amarok could not be satisfied.

---

### Post by ButteBlues on 2006-12-28
> **djsamsel said:**
> thanks, that got me to the command 

sudo apt-get build-dep amarok

to which i received 
E: Build-dependencies for amarok could not be satisfied.
Odd. Sounds like there's conflicting packages or something...

You have universe and multiverse repositories enabled?

---

### Post by djsamsel on 2006-12-28
i think so. here's my sources.list

> 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END

# Beryl
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy

# Nvidia Latest Drivers
# deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/
deb [http://albertomilone.com/drivers/unstable/edgy/32bit](http://albertomilone.com/drivers/unstable/edgy/32bit) binary/

#Beryl SVN
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

#Amarok
deb [http://imbrandon.com/packages](http://imbrandon.com/packages) edgy amarok

deb-src [http://imbrandon.com/packages](http://imbrandon.com/packages) edgy amarok

## LG3D repsoitories
# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib
# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib

# deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy unstable


---

### Post by ButteBlues on 2006-12-28
The repos should be good. It could just be a bad sync. 

Go to the Amarok site (amarok.kde.org) and look at their dependencies and install them with apt-get.

---

### Post by bsalt on 2006-12-31
here's the correct link:

[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

---

### Post by ErikTheRed on 2007-01-01
For those who are curious, the Zune currently **does not work**. You can connect up to it and see the music on it currently, but writing doesn't work yet.

---

### Post by webellusion on 2007-01-07
The manual guide in the first post worked without any problems on Kubuntu Edgy with my Creative Zen V Player. However when I restarted computer post installation, loaded Amarok, and plugged in the MP3 player, it didn't detect it first. 

All I had to do (only first time) was to go to "Tools" > "Amarok Settings" > "Media Devices" > "Add Device" choose "MTP Media Device" from the drop down list, entered name as Creative Zen V (or whatever you want), and clicked OK.

From now on all I have to do each time to transfer music, is click Media Devices on the left and I can all of my music, I can drag music from the right (on my computer) to the left (on MP3 player) and click "Transfer" at the top

My experience may seem quite basic for advanced users, but I am sure it will help a newbie save hours (which I wasted figuring this out!)

Many thanks to  a simple façade for this amazing guide.

---

### Post by dada1958 on 2007-01-07
I struggled with this one this entire weekend; time for a clean install and a (for this moment) good bye to Beryl. It's an achievement but still too early in its development stage  to be reliable on a computer that has to be more or less stable. I seldom used Exposé on my Mac so what's the point?
But my Zen V is recognized by Amarok now, what a wonderful piece of software is that! I thank the OP for sharing his efforts ...

---

### Post by Stonecougar on 2007-01-16
Okay, so, in trying to make Amarok play nice with my Zen Micro, I followed the list of directions given at the start of the thread. Everything went pretty smoothly, with a few snags that were quickly remedied by actually paying attention. :P One problem... it's all installed, but I can't find Amarok! It's not in my Applications menu, and when I run the 'sudo amarok' command, it says it's an invalid command. I'm still a bit of a Linux n00b, so I'm not sure what to do here.  I went looking for the application itself, but all I could find was the folder it was built in, in my /home directory. Didn't see anything inside there that held much promise. I am thoroughly confused. Help?

---

### Post by ButteBlues on 2007-01-16
> **Stonecougar said:**
> Okay, so, in trying to make Amarok play nice with my Zen Micro, I followed the list of directions given at the start of the thread. Everything went pretty smoothly, with a few snags that were quickly remedied by actually paying attention. :P One problem... it's all installed, but I can't find Amarok! It's not in my Applications menu, and when I run the 'sudo amarok' command, it says it's an invalid command. I'm still a bit of a Linux n00b, so I'm not sure what to do here.  I went looking for the application itself, but all I could find was the folder it was built in, in my /home directory. Didn't see anything inside there that held much promise. I am thoroughly confused. Help?
Don't run amarok as root.

In any case, log out, log back in. Try again.

---

### Post by Stonecougar on 2007-01-16
Thanks for the quick reply!

I got it figured out, I left out a command in there, the one where it actually installs Amarok... like I said, paying attention. :P I have a new problem, though. It's still not recognizing my Zen. I plug it in, and the little bugger doesn't even light up to charge, like it usually does. I tried following webellusion's suggestion for configuring Amarok, but... MTP devices aren't listed. I think I may have hosed something up back there, but I'm not sure what. Any ideas?

---

### Post by ButteBlues on 2007-01-16
> **Stonecougar said:**
> Thanks for the quick reply!

I got it figured out, I left out a command in there, the one where it actually installs Amarok... like I said, paying attention. :P I have a new problem, though. It's still not recognizing my Zen. I plug it in, and the little bugger doesn't even light up to charge, like it usually does. I tried following webellusion's suggestion for configuring Amarok, but... MTP devices aren't listed. I think I may have hosed something up back there, but I'm not sure what. Any ideas?
Did you forget to install libmtp while you were at it? =P

---

### Post by Stonecougar on 2007-01-16
Well, I installed the libmtp again, just to be safe, but... still no dice. The brief popup error message when I hit "Autodetect devices" said no new devices were found, and  something about DBUS and HAL daemons. MTP device is still not in the dropdown list.

Edit: I ran the "dcop kded mediamanager fullList" command suggested by the error message, and it came up with the following: 

/org/freedesktop/Hal/devices/volume_label_GnomeBaker_data_disk
hdc
GnomeBaker data disk

true
/dev/hdc
/media/cdrom0
iso9660
true

media/dvd_mounted

---
/org/freedesktop/Hal/devices/volume_label_FARCRY_1
hdd
FARCRY_1

true
/dev/hdd
/media/cdrom1
iso9660
true

media/cdwriter_mounted

---
/org/freedesktop/Hal/devices/volume_uuid_6b5d803d_ad9c_4c11_a81d_384b50f25b1b
hda1
161G Media

true
/dev/hda1
/
ext3
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/volume_uuid_24A83F8FA83F5E8C
hdb1
41G Media

true
/dev/hdb1
/media/Winblows
ntfs
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/platform_floppy_0_storage
fd0
Floppy Drive

true
/dev/fd0


false

media/floppy_unmounted

---
/org/freedesktop/Hal/devices/usb_device_41e_4130_0105255100039316_if0
camera
USB Interface

false



false
camera://Creative Zen Micro@[usb:003,006]/
media/gphoto2camera

---

Dunno if that'll be any help in diagnosing the problem...

---

### Post by ButteBlues on 2007-01-16
> **Stonecougar said:**
> Well, I installed the libmtp again, just to be safe, but... still no dice. The brief popup error message when I hit "Autodetect devices" said no new devices were found, and  something about DBUS and HAL daemons. MTP device is still not in the dropdown list.

Edit: I ran the "dcop kded mediamanager fullList" command suggested by the error message, and it came up with the following: 

/org/freedesktop/Hal/devices/volume_label_GnomeBaker_data_disk
hdc
GnomeBaker data disk

true
/dev/hdc
/media/cdrom0
iso9660
true

media/dvd_mounted

---
/org/freedesktop/Hal/devices/volume_label_FARCRY_1
hdd
FARCRY_1

true
/dev/hdd
/media/cdrom1
iso9660
true

media/cdwriter_mounted

---
/org/freedesktop/Hal/devices/volume_uuid_6b5d803d_ad9c_4c11_a81d_384b50f25b1b
hda1
161G Media

true
/dev/hda1
/
ext3
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/volume_uuid_24A83F8FA83F5E8C
hdb1
41G Media

true
/dev/hdb1
/media/Winblows
ntfs
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/platform_floppy_0_storage
fd0
Floppy Drive

true
/dev/fd0


false

media/floppy_unmounted

---
/org/freedesktop/Hal/devices/usb_device_41e_4130_0105255100039316_if0
camera
USB Interface

false



false
camera://Creative Zen Micro@[usb:003,006]/
media/gphoto2camera

---

Dunno if that'll be any help in diagnosing the problem...
It seems that version of Amarok dislikes that version of mtp.

---

### Post by Stonecougar on 2007-01-16
HA! Got it to work. Realized I was running 1.4.3 Amarok, so I went through and reinstalled everything, just like jrjazzman did. Little bit of fiddling later and BING! She lights right up. Thanks so much for the help, Butte. And thanks for being patient with a n00b who doesn't know how to read. >.>

---

### Post by joshlfisher on 2007-01-18
I have installed Amarok and libmtp, connected my samsung yp-t7jZ. Amarok did not recognize it, but I added it manually (MTP option did exist). It was able to connect fine, and I was able to drag items to the sync area. BUT when I clicked transfer, Amarok Froze.

---

### Post by ButteBlues on 2007-01-18
> **joshlfisher said:**
> I have installed Amarok and libmtp, connected my samsung yp-t7jZ. Amarok did not recognize it, but I added it manually (MTP option did exist). It was able to connect fine, and I was able to drag items to the sync area. BUT when I clicked transfer, Amarok Froze.
Send a bug to Amarok devs.

---

### Post by joshlfisher on 2007-01-18
Done! Bug #140270

---

### Post by bsalt on 2007-01-19
Currently, I am only using gnomad2 with the mtp support, but I will most definitely switch to Amarok when Feisty is released - Amarok 1.4.4 will come with mtp straight out of the box. :)

---

### Post by jkgruet on 2007-01-19
Thanks for all the help, all.  I finally got it all to work.  Some comments on ButteBlues' "Install yourself" directions.

[LIST=1]
[*]I have a single-user machine, and did the installation in the */usr/local/src/* directory.  That worked fine.  

[*]I found that I had to already have amarok installed using *sudo apt-get install amarok* before proceeding to step 5.  If I didn't, *sudo apt-get install amarok-xine* would *also* install amarok (from the repository, and without MTP support), messing up what had just been done.

[*]In addition, do *not* use *sudo checkinstall* instead of *sudo make* in step 5.  I did that without thinking (the first time); if one does that, then when one tries to install amarok-xine, it also installs ("updates") the non-MTP amarok from the repository.  

[*]". . . it should autodect?"  Surely that is a typo.  Or, perhaps my machine or it's operator just did something wrong.  In any event, the autodetect did not work when I tried it.  I verified that my device was being detected by my machine using the *lsusb* command, and then just went through a manual installation.  As near as I could see, the Zen V was never actually mounted anywhere (leastwise, it didn't appear to be), but it started to work as soon as I used Settings -> Configure Amarok -> Media Devices -> Add Device.   I selected the "MTP Media Device" from the dropdown, gave it a name, and clicked "OK".  It finally worked.
[/LIST]

Next tasks:
[LIST=1]
[*]*Figure out how to upload* from the Zen V to the computer.  Apparently that is not something that Amarok can do.  My understanding is that gnomad2 can do it, so that's next on my list.
[*]*Get sound working.*  Kubuntu supposedly has great sound support.  I've found it to be intermittent (works sometimes, then sometimes it doesn't) using either a Sound Blaster 16 , *or* the onboard AC97 (nVidia) device.
[*]*Get multimedia working.* Following the various howtos didn't work:  that's when sound became intermittent, and then stopped altogether.  
[/LIST]

But these are additional topics; this one has ended successfully.  Thanks again for all the help.

---

### Post by ButteBlues on 2007-01-19
I'm going to be abandoning this as I no longer use Amarok. Whoever wishes to maintain it can drop me a PM.

---

### Post by AronVanAmmers on 2007-01-20
Hi,

I've been trying to get this working with my Samsung YH 925GS player. I'm running Kubuntu Edgy. 

I'm running into a problem with libmtp. I'll post this on the libmtp forum as well, but since this might be a Ubuntu-specific problem I'm posting it here too.

The YH 925GS is not included in the supported devices of libmtp, but I figured it should probably work as well as the YH 925. The device number is different though, so without modification, libmtp will not detect it. To make it work, I looked up the device number using "lsusb -v" and added a line for my device in src/libusb-glue.c:

```
87:  { "Samsung YH-925GS", 0x04e8, 0x5024, DEVICE_FLAG_NONE },
```

And a line to libmtp.rules:
```
41: SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="5024", SYMLINK+="libmtp-%k", MODE="666"
```

Then I compiled libmtp as explained in the guide. Compiling and installing went fine. I copied libmtp.rules to /etc/udev/rules.d/45-libmtp.rules. When I connect the device, a couple of symlinks are created in /dev:

```
$ ls /dev/libmtp*
/dev/libmtp-sdb  /dev/libmtp-sdb1  /dev/libmtp-sg1  /dev/libmtp-usbdev3.15
```

So the udev rules seem to work. However, here's the problem:

```
$ mtp-detect
Found non-autodetected device "Samsung YH-925GS" on USB bus...
usb_claim_interface(): Device or resource busy
Connection error.
No devices.
```

mtp-detect correctly finds the device, so adding the line in libusb-glue.c did its work. However, it can't connect to it.

I'm at a loss trying to solve this. mtp-detect tells me the device wasn't autodetected. I don't entirely understand what's going on there. I think udev should somehow trigger libmtp to take action when the device is mounted. However, the included rules file only creates some symlinks in /dev. I tried reloading and restarting udev, and I rebooted the machine.

Could somebody help me how to proceed?

---

### Post by le_vainqueur on 2007-01-30
I am running Edgy, and have the following problems.

When running sudo checkinstall one of the responses is
> Installing Debian package... FAILED!

When Running the command
> cd amarok-1.4*
I get the error
> brandon@brandon-desktop:~/amarok-with-mtp_dir$ cd amarok-1.4*
bash: cd: amarok-1.4.3: Permission denied

---

### Post by bsalt on 2007-01-30
I've got gnomad 2.8.10 installed, and it is using libmtp 0.1.3 - is there anyway newer versions of this protocol can be used for Amarok... having to remove one thing to get another to work doesn't sound too appealing right now...

but thanks for the how-to! I had it running with libmtp 0.1.0 (beautifully, I might add) - but as libmtp 0.1.3 improves, I feel that amarok should be able to benefit from it as well...

---

### Post by bsalt on 2007-01-31
I recommend you update this how-to for Edgy users. I have tried installing amarok using "apt-get source amarok", but there is an update in the repos after install. I'd recommend downloading amarok 1.4.4 from source at amarok.kde.org.


Ok, nevermind, I found that when I was typing "sudo checkinstall", I wasn't naming the package something other than amarok... once I renamed it to amarok-built or something different, it stopped bothering me. :)

---

### Post by Minyaliel on 2007-01-31
I followed the instructions, but to no avail - my Zen Creative V still won't show up. :(

---

### Post by bsalt on 2007-01-31
> **Minyaliel said:**
> I followed the instructions, but to no avail - my Zen Creative V still won't show up. :(

Let's try this.

Connect your Zen Vision to your computer and in a terminal type

```
lsusb
```

in a terminal.


Does it show a line for your player at all? Something similar to this, but different numbers:

```
Bus 005 Device 010: ID 041e:4128 Creative Technology, Ltd
```

---

### Post by Colonel Forbin on 2007-02-02
Help... when I try to run ./configure on edgy or feisty I get:

./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

What does this mean? What do I do?

Thanks,
Forbin

---

### Post by ButteBlues on 2007-02-02
> **Colonel Forbin said:**
> Help... when I try to run ./configure on edgy or feisty I get:

./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

What does this mean? What do I do?

Thanks,
Forbin
Just a note. I've tested it and the libmtp and amarok in the feisty repository IS a working combination. =)

Using it now actually.

---

### Post by bsalt on 2007-02-03
> **le_vainqueur said:**
> I am running Edgy, and have the following problems.

When running sudo checkinstall one of the responses is


When Running the command

I get the error

I'm sorry I did not respond to your post! For whatever folder it is in, make sure you have read/write permission for it. So type something similar to this command:

```
sudo chown -R $USER:$USER ~/amarok-with-mtp_dir
```

After that, you should be fine. However, when you run "sudo checkinstall" rename the package to something like "amarok-built" before you hit enter a third time. Otherwise, Ubuntu will try to "update" your amarok install to the previous version... which sucks.


Hope that helps!

---

### Post by bsalt on 2007-02-03
> **Colonel Forbin said:**
> Help... when I try to run ./configure on edgy or feisty I get:

./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

What does this mean? What do I do?

Thanks,
Forbin


Before you had gone through with all of this, did you make sure to type in the terminal

```
sudo apt-get build-dep amarok
```

If it still gives you errors, try this how-to I whipped up earlier today (actually yesterday now):

[http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html](http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html)

---

### Post by kingborel on 2007-02-03
> **le_vainqueur said:**
> 
I get the error:

brandon@brandon-desktop:~/amarok-with-mtp_dir$ cd amarok-1.4*
bash: cd: amarok-1.4.3: Permission denied



I worked around this by chomd-ing it to 777, NOT 700 as the How-To says :)

---

### Post by Jarn on 2007-02-05
When updating Amarok, do you have to do the stuff to install libmtp again? Or can you just get the source and install?

---

### Post by ButteBlues on 2007-02-05
> **Jarn said:**
> When updating Amarok, do you have to do the stuff to install libmtp again? Or can you just get the source and install?
You should only need to update Amarok. =)

---

### Post by Jarn on 2007-02-05
Thanks. :D

---

### Post by Jarn on 2007-02-05
Argh! Amarok used to work with my MTP device. I just upgraded to the newest version (1.4.5), following these instructions again, and now it doesn't work! It doesn't even show MTP functionality in Media Devices like it used to! When I configured, though, it said that it was configuring it with MTP support!

---

### Post by Jarn on 2007-02-05
Okay, it looks like the newest amarok (1.4.5) needs a newer version of libmtp than is linked to in the first post. I got it working now. The newest needs >=1.1. I downloaded and installed 1.3.

---

### Post by bsalt on 2007-02-05
I wonder if it will work with the libmtp in the repos...

---

### Post by ButteBlues on 2007-02-05
> **bsalt said:**
> I wonder if it will work with the libmtp in the repos...
1.4.4 did IIRC, but I just fresh installed this morning so I can't tell you.

---

### Post by bsalt on 2007-02-06
Hey guys, I wrote a how-to a few days ago that sort of simplifies this how-to for really basic end-users. Let me know if it works for ya. (And with later versions of Amarok)

[http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html](http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html)

---

### Post by Chumsley on 2007-02-07
I just wanted to let you know, your method worked great.  I spent the past day and a half trying to get my Zen to work with Amarok (or anything at all on Ubuntu), and this is the only method that works.  Thanks so much.

---

### Post by oxyrosis on 2007-02-08
i've torn out most of my hair with this problem

my Zen Xtra is reading as a camera whenever i plug it in, i have tried all of the methods listed with no success.

Also, Amarok isnt giving me the MTP functionality, and i've installed it several times.

- when i type "lsusb" i do see my player listed as a creative device

also, the general consensus around here is that because my player is installed with "playforsure" drivers from back in my windows days, it isnt being read properly. is there any truth to this?

---

### Post by bsalt on 2007-02-08
> **oxyrosis said:**
> i've torn out most of my hair with this problem

my Zen Xtra is reading as a camera whenever i plug it in, i have tried all of the methods listed with no success.

Also, Amarok isnt giving me the MTP functionality, and i've installed it several times.

- when i type "lsusb" i do see my player listed as a creative device

also, the general consensus around here is that because my player is installed with "playforsure" drivers from back in my windows days, it isnt being read properly. is there any truth to this?

oxyrosis, your device will be read properly, now that libmtp is present for Linux. I posted a how-to blog for installing Amarok and MTP (with the aid of this thread). The link is in my profile. See if that helps.

---

### Post by oxyrosis on 2007-02-08
well, i got to the installing of Amarok step when i got this wonderful error when i inupt "make"

collect2: ld returned 1 exit status
make[5]: *** [libamarok_mtp-mediadevice.la] Error 1
make[5]: Leaving directory `/home/oxyrosis/Desktop/Amarok/amarok-1.4.5/amarok/src/mediadevice/mtp'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/oxyrosis/Desktop/Amarok/amarok-1.4.5/amarok/src/mediadevice'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/oxyrosis/Desktop/Amarok/amarok-1.4.5/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/oxyrosis/Desktop/Amarok/amarok-1.4.5/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/oxyrosis/Desktop/Amarok/amarok-1.4.5'
make: *** [all] Error 2

any ideas? or do you need to see the whole output?

---

### Post by Brokenrgv on 2007-02-08
I dont get why they just cant install MTP support straight up in Amarok, everything else is "switched on" e.g ipod support, why make it hard for MTP users its driving me nut.

---

### Post by bsalt on 2007-02-08
probably because MTP support is still so new. a year ago, i was trying to find a way to connect using gnomad2 - which is still awesome. MTP is probably still thought of as "experimental" because of it's newness. i'm sure it'll be ported just like ipod support has been. it'll just take time.

---

### Post by Brokenrgv on 2007-02-08
and my device will be broken and old by the time they turn it on by default i can see.

---

### Post by bsalt on 2007-02-08
i'm using a creative zen xtra - a very old school player... but i hear ya... you buy a "new" device, and as soon as you tear the box open, it's already the older model. 

it's funny how much worse tech stuff depreciates than cars.

---

### Post by Brokenrgv on 2007-02-08
ive had this Zen Vision M for i think a year, when ever it first came out and ive been at logaheads with linux and apps gnomad2,Amarok  the entire time and its getting to me, im not an apple fan by any stretch but it got to the point where i bought a shuffle just so with new releases of amarok at least i know ill be able to listen to something while i work out how to get my $500 player to work, it shouldnt be like that, just venting thats all.

---

### Post by bsalt on 2007-02-08
ok, so you've got your vision working?

---

### Post by Brokenrgv on 2007-02-08
I wish, ive got a version of Amarok working with mtp support in the past by simply changing sources to feisty and install amarok that way, not this time around though even 1.4.5 from edgy repo's is now locking up on me, this is so frustrating, this is one of the reasons windows users get to laugh at us :( 

[http://img525.imageshack.us/img525/664/amarokerror1xu6.png](http://img525.imageshack.us/img525/664/amarokerror1xu6.png)

this is where it locks up, now id be happy just to have a working version of amarok

anyone know where to get older debs of amarok btw?

---

### Post by ButteBlues on 2007-02-08
1.4.5 in Feisty isn't currently built with mtp support.

---

### Post by Jarn on 2007-02-08
It appears the newest Amarok in the repos, 1.4.5, is packaged with MTP functionality. :D

---

### Post by Brokenrgv on 2007-02-09
we talking feisty or edgy repo's ??

---

### Post by lamalex on 2007-02-09
> **ButteBlues said:**
> 1. It needs a compatible Libmtp version.

2. The amarok in Feisty repos is built with mtp support. Just not the Edgy one. ;)


===

For edgy, please try 1.2.0. It accounts for Edgy not being compatible with certain libs.

I'll be looking through for those bugs.

mine doesnt have it... I'm running herd 3, and I installed it from the repo.

---

### Post by ButteBlues on 2007-02-09
> **Iamalex said:**
> mine doesnt have it... I'm running herd 3, and I installed it from the repo.
It doesn't now, but it DID. You must understand the amarok in the repos updates often.

---

### Post by Jarn on 2007-02-10
Mine had MTP support when I installed it yesterday. Edgy.

---

### Post by rachii on 2007-02-10
i'm on a newly installed feisty.  i have libmtp and amarok 1.4.5 installed.  if i type mtp-detect it reads the device just fine it is listed in libmtp.rules and matches the ID's of lsusb..,  however inside of amarok MTP is not an option when configuring a new media device

any ideas?

thank you


nevermind, i rebuilt amarok with the command:

./configure --with-libnjb --with-libmtp --with-libgpod --prefix=`kde-config --prefix`

and now it recognizes mtp

---

### Post by anaspeople on 2007-02-11
HOw exactly did you do it? :confused:

---

### Post by ButteBlues on 2007-02-11
> **anaspeople said:**
> HOw exactly did you do it? :confused:
Build libmtp 0.1.3 as directed here: [http://www.ubuntuforums.org/showthread.php?t=199250](http://www.ubuntuforums.org/showthread.php?t=199250).

Then, open up the terminal.

Run the following (ignore the $: in front of any given line when copying/pasting):
```
$: sudo apt-get update
$: sudo apt-get upgrade
$: sudo apt-get build-dep amarok
$: wget -C http://kde.mirrors.tds.net/pub/kde/stable/amarok/1.4.5/src/amarok-1.4.5.tar.bz2
$: tar -jxf amarok-1.4.5.tar.bz2
$: cd amarok-1.4.5/
$: ./configure --with-libnjb --with-libmtp --with-libgpod --prefix=`kde-config --prefix`
$: sudo make
$: sudo make install
```

Once all that's done, assuming none of it exited with errors, Amarok should work with MTP.

---

### Post by anaspeople on 2007-02-13
Thanks for answering, anyways I get these problems:
First I'm using Gnome so when I  do this
> **ButteBlues said:**
> 
$: sudo apt-get build-dep amarok

I get 58MBs of dependency packages which decompressed mean 172MB. I don't think I need many of them, but wonder which one I really need.

Sencondly I managed to download using wget -c but when I do
> **ButteBlues said:**
> 
$: ./configure --with-libnjb --with-libmtp --with-libgpod --prefix=`kde-config --prefix`

I get 
```
checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

```
And consecuntly when I try to do make I get:
```
make: *** No targets specified and no makefile found.  Stop.
```
Any suggestions?

---

### Post by ButteBlues on 2007-02-13
You need to apt-get build-dep amarok and install all the files needed to build amarok.

---

### Post by L2wis on 2007-02-14
Hey all, i followed the guide and everything seems to be installed all okay. BUT

When i connect my micro zen with Amarok running nothing happens. I tried clicking Media Devices then connect but nothing happens.

---

### Post by superxero044 on 2007-02-15
ok I tried this a few times with no luck.

What I did have luck with was - 

1) uninstalling all versions of libmtp (including libmtp2) 
2) uninstalling amarok
3.  installing the latest libmtp - version 0.1.3 using check install
4) running the command to get all of amarok's dependencinies 
5( installing amarok from source using checkinstall

THEN I had to restart my computer - then when I opened amarok I had to tell it to look for a mtp device - it didn't automatically detect the zen still.

Then when i told it to connect to the mtp device it worked.

Good luck. I will try to post a more detailed set of instructions soon because the main set are severly out dated - but being a newb myself i don't really know the proper terminology / rules to writing a guide.

---

### Post by bsalt on 2007-02-15
Yeah... for some reason, it does not autodetect MTP devices. What we can look foward to, however, is Amarok 2.0. It will be released this summer, most likely, and will support Windows, Mac, AND Linux. We can most likely expect new and good things.

Jon

---

### Post by Jarn on 2007-02-15
It autodetects my MTP device, once I added an entry for it in the Devices menu...

---

### Post by disembodied on 2007-02-16
> **ButteBlues said:**
> Build libmtp 0.1.3 as directed here: [http://www.ubuntuforums.org/showthread.php?t=199250](http://www.ubuntuforums.org/showthread.php?t=199250).

Then, open up the terminal.

Run the following (ignore the $: in front of any given line when copying/pasting):
```
$: sudo apt-get update
$: sudo apt-get upgrade
$: sudo apt-get build-dep amarok
$: wget -C http://kde.mirrors.tds.net/pub/kde/stable/amarok/1.4.5/src/amarok-1.4.5.tar.bz2
$: tar -jxf amarok-1.4.5.tar.bz2
$: cd amarok-1.4.5/
$: ./configure --with-libnjb --with-libmtp --with-libgpod --prefix=`kde-config --prefix`
$: sudo make
$: sudo make install
```

Once all that's done, assuming none of it exited with errors, Amarok should work with MTP.
I followed this exactly... first I installed lib-mtp, ran the mtp-detect command and it recognize my creative zen vision m just fine... then i ran through the above console commands, and it all went fine, but still no MTP in amarok.

One problem may be that I didn't have a -C command for wget... i ran -c (which is just continue a partially downloaded) but what was the -C command and why do I not have it? Could that have caused the problem somehow?

Any other help would be greatly appreciated.

Thanks

---

### Post by ButteBlues on 2007-02-16
> **disembodied said:**
> I followed this exactly... first I installed lib-mtp, ran the mtp-detect command and it recognize my creative zen vision m just fine... then i ran through the above console commands, and it all went fine, but still no MTP in amarok.

One problem may be that I didn't have a -C command for wget... i ran -c (which is just continue a partially downloaded) but what was the -C command and why do I not have it? Could that have caused the problem somehow?

Any other help would be greatly appreciated.

Thanks
I typo'd that -c.


In Amarok, in the Configuration screen, add an MTP device in Amarok, then connect the device to your computer, open the Devices screen, and click Connect in Amarok.

---

### Post by disembodied on 2007-02-16
> **ButteBlues said:**
> I typo'd that -c.


In Amarok, in the Configuration screen, add an MTP device in Amarok, then connect the device to your computer, open the Devices screen, and click Connect in Amarok.

I still don't get the option for an MTP device in amarok configuration... its like it didn't configure/compile with libmtp, even though i did it exactly as it was written out.

Thanks

---

### Post by ButteBlues on 2007-02-16
> **disembodied said:**
> I still don't get the option for an MTP device in amarok configuration... its like it didn't configure/compile with libmtp, even though i did it exactly as it was written out.

Thanks
I can't really explain that sort of behavior by amarok. If compiled like that, MTP _should_ be a listed choice.

---

Also, I'll be completely renovating this soon and moving it to my site.

If someone could create an Edgy deb that's built with mtp support, I'd also host that.

---

### Post by forcesofhabit on 2007-02-17
I am not sure if this has been noticed/discussed earlier, but after using Amarok to get my mp3s from my Microphoto, they sound like garbage. All low-end from the files is gone.
Anyone else have the same problem?

---

### Post by anaspeople on 2007-02-17
I followed post #108  exactly but I still don't get MTP support for amarok :( 
 I did ask it to configure it with mtp support but then it says >  = The following extra functionality will NOT be included:
 =   - NMM-engine
 =   - Helix-engine
 =   - yauap-engine
 =   - MySql Support
 =   - Postgresql Support
 =   - MP4/AAC Tag Write Support
 =   - MTP Device Support
 =   - Rio Karma Support
 =
 = The following extra functionality will be included:
 =   + xine-engine
 =   + libvisual Support
 =   + Konqueror Sidebar
 =   + MusicBrainz Support
 =   + iPod Support
 =   + iRiver iFP Support
 =   + Creative Nomad Jukebox Support
 =   + DAAP Music Sharing Support

Any idea??

---

### Post by LeslieL on 2007-02-22
I've been trying to get both Amarok and Gnomad2 (using [another excellent howto]("http://ubuntuforums.org/showthread.php?p=1153431#poststop")) to work with my Creative Microphoto. I can get one or the other. Amarok seems to need <=libmtp-0.1.0, and Gnomad uses the latest version of libmtp. Has anyone got them both working together? I'm on Edgy just now; should I upgrade to Feisty?

---

### Post by AdotB on 2007-02-27
> **ButteBlues said:**
> Also, I'll be completely renovating this soon and moving it to my site.

If someone could create an Edgy deb that's built with mtp support, I'd also host that.

I managed to make a .deb on Edgy and was able to transfer an album to my iriver clix. the package is 28.3 MB.

Note: After trying to reconnect it a second time, i get a closing session error and amarok crashes when i try to connect. I don't know what is causing this.

---

### Post by anchois on 2007-02-27
Hello all,

I'm using Dapper so that I manage to make some .deb with
amarok 1.4.5 and libmtp 0.1.3 (last known)

Here how:

First remove, old packages:

```
sudo apt-get remove amarok amarok-xine libmtp2 libmtp-dev
```

Then get source packages (example for France mirrors)

```
wget ftp://ftp.lip6.fr/pub/X11/kde/stable/amarok/1.4.5/src/amarok-1.4.5.tar.bz2
wget http://kent.dl.sourceforge.net/sourceforge/libmtp/libmtp-0.1.3.tar.gz

```

Uncompress both of the files,
go to the libmtp dir and do:

```
./configure --prefix=/usr
sudo make
sudo checkinstall
sudo cp libmtp.rules /etc/udev/rules.d/

```

Get the build dependencies for amarok:

```
sudo apt-get build-dep amarok
sudo apt-get install ruby1.8-dev

```

Then go to the amarok directory, compil amarok and build packages:

```
./configure --with-njb --with-mtp --prefix=`kde-config --prefix`
sudo make
sudo checkinstall

```

It should be straight forward and you now have libmtp and amarok installed on 
your system.

I post a link to the two .deb that I had (watch out, there aren't configured with dependencies, make sure
you have all the needed packages before installing it):

[http://anchois.free.fr/dapper/amarok_1.4.5-1_i386.deb]("http://anchois.free.fr/dapper/amarok_1.4.5-1_i386.deb")
[http://anchois.free.fr/dapper/libmtp_0.1.3-1_i386.deb]("http://anchois.free.fr/dapper/libmtp_0.1.3-1_i386.deb")

[B]The only thing is that on my Dapper it's only working as root (not as a user). I didn't manage to correct
the problem with the  mtp-detect -> Operation not permitted as normal user.[/B]

btw: I have a Creative Vision M, I didn't have time to test deeply but connection is working and it's showing all my mp3
(which is more than I had before ;)

I have done some tests:
stability -> rock solid: 5Gb of deleted mp3 and 7Gb transfered to the player with 3 or 4 Connexion/Deconnexion between
usuability -> it's nice to have all the album covers / transfer from the player to the PC is not working

---

### Post by TheSoko on 2007-03-11
If mtp-detect gives you this:

```

Found non-autodetected device "Creative Zen V" on USB bus...
usb_claim_interface(): Operation not permitted
Connection error.
No devices.
```

Then try this thread: [http://amarok.kde.org/forum/index.php?topic=13539.msg17145](http://amarok.kde.org/forum/index.php?topic=13539.msg17145)

Working successfully for me, though I did still have to manually add it in Amarok...

---

### Post by mattyp1 on 2007-03-11
I followed the directions several times and was not able to get MTP support to apply to amarok. After a little more hunting I found a great summary of this entire thread at "http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html" . It appears that the key difference is you MUST use an alias when you checkinstall amarok and MTP support. I think that because I didn't do this when I ran sudo apt-get install amarok-xine a standard install from the ubuntu repo overwrote my manual compile.

The author of this post references this thread as the primary source for his writeup.
Thank you for all the help! - MP

---

### Post by able421 on 2007-03-12
Well, I'm pretty sure I've tried every suggestion in this forum and the others it has linked to, but it comes down to this. I'm running Kubuntu Edgy, with all the latest packages. I have successfully compiled and/or installed the supporting packages.  Mtp-detect and other mtp example commands work fine with my Creative Zen Vision:M. But when I try to make amarok-1.4.5, I get this (much compilation finished at this point):

/bin/bash ../../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall
-W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION    -o amarokapp -L/usr/share/qt3/lib -L/usr/lib    -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib -R /usr/lib main.o ../../amarok/src/amarokcore/libamarokcore.la libamarok.la ../../amarok/src/analyzers/libanalyzers.la ../../amarok/src/plugin/libplugin.la ../../amarok/src/statusbar/libstatusbar.la ../../amarok/src/metadata/libmetadata.la -l kutils -lkio -lkdeui -lkdecore -lkhtml -lknewstuff -L/usr/lib -ltag -lGL  ../../amarok/src/sqlite/libsqlite.la  -ltunepimp

/usr/bin/ld: BFD 2.17 Debian GNU/Linux assertion fail ../../binutils-2.17/bfd/elflink.c:6261
/usr/bin/ld: .libs/amarokapp: hidden symbol `__fini_array_end' in .libs/amarokapp is referenced by DSO
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status
make[4]: *** [amarokapp] Error 1

My version of binutils is 2.17-1ubuntu1. I'm running the latest kernel. I don't have the most experience developing for Linux, so I would appreciate any suggestions.

/Once this works, I'll never need to boot XP again.

---

### Post by AronVanAmmers on 2007-03-23
Hi,

I've been able to succesfully build Amarok 1.4.5 with MTP support. I'm using Ubuntu Edgy.

I'm using libmtp from CVS, like this:

```

cvs -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp login
cvs -z3 -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp co -P libmtp
./autogen.sh
./configure --prefix=/usr
make
sudo checkinstall

```

Then get and compile Amarok like this:

```

wget ftp://ftp.lip6.fr/pub/X11/kde/stable/amarok/1.4.5/src/amarok-1.4.5.tar.bz2
tar xjf amarok-1.4.5.tar.bz2
cd amarok-1.4.5
make
sudo checkinstall
```

The package actually failed to install at first, because it would overwrite a file from the existing amarok-xine package. So I had to force it:

```

sudo dpkg --force overwrite -i amarok-1.4.5.deb
```

And Bob's your uncle. Since yesterday libmtp supports my Samsung YH 925GS which I can now fully use with Amarok as well as with gnomad2. Wahey!

---

### Post by cborga1985 on 2007-04-04
Edgy AMD64 Debs
[http://www.filespacer.com/users/cborga/amarok/](http://www.filespacer.com/users/cborga/amarok/)

---

### Post by cborga1985 on 2007-04-07
I just pulled fiesty sources from the repo and hacked the control a little to build my packages. Now, the Phillips GoGear HDD6330/17 is supported by the lastest libmtp. You have to build it from source though.

---

### Post by Someone09 on 2007-04-11
Hi

Sorry I'm quite sure it's one of my usual stupid mistake but i block there 

lois@lois-desktop:~/amarok-with-mtp_dir$ sudo apt-get source amarok
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture de l'information d'état... Fait
E: Impossible de verrouiller /var/lib/apt/lists/e17.sos-sts.com_dists_edgy_e17_source_Sources - open (2 Aucun fichier ou répertoire de ce type)

What should I do ??

---

### Post by cborga1985 on 2007-04-11
> **Someone09 said:**
> Hi

Sorry I'm quite it's one of my usual stupid mistake but i block there 

lois@lois-desktop:~/amarok-with-mtp_dir$ sudo apt-get source amarokLecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture de l'information d'état... Fait
E: Impossible de verrouiller /var/lib/apt/lists/e17.sos-sts.com_dists_edgy_e17_source_Sources - open (2 Aucun fichier ou répertoire de ce type)

What should I do ??
sudo apt-get install build-essential checkinstall
sudo apt-get build-dep amarok

---

### Post by Someone09 on 2007-04-11
Thanks for the quick reply but I tryed what you said and I still have the same problem

---

### Post by cortana on 2007-04-15
Hi,

The above guide is great, thanks. If you're still having problems I suggest taking a look at an excellent post on the mysticriver site: [http://www.misticriver.net/showthread.php?t=50579](http://www.misticriver.net/showthread.php?t=50579)

---

### Post by cyberdemon on 2007-05-19
I have a kubuntu 64bit edition installed on my system and the above did not work for me. it did however give me an outline on what to do.

for others wanting support for mtp devices on an amd64 system these are the steps I went through to get it.


1.
sudo apt-get update
sudo apt-get dist-upgrade

2.
cd ~
mkdir amarok-with-mtp_dir
cd amarok-with-mtp_dir



3.
wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.5-0ubuntu7_amd64.deb"
wget "http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.5-0ubuntu7_amd64.deb"
wget "http://superb-east.dl.sourceforge.net/sourceforge/libmtp/libmtp-0.1.5.tar.gz"

4.
tar -zxvf libmtp-0.1.5.tar.gz
cd libmtp-0.1.5/
./configure --prefix=/usr
sudo make
sudo checkinstall
sudo cp libmtp.rules /etc/udev/rules.d/
cd ../

5.
sudo dpkg -i amarok_1.4.5-0ubuntu7_amd64.deb
sudo dpkg -i amarok-xine_1.4.5-0ubuntu7_amd64.deb

---

### Post by robertsaron on 2007-05-21
will amarok work with M$ ZUNE? Or is it just better to dual boot windows for this device?

---

### Post by Jarn on 2007-05-24
I'm trying to install libmtp, but when I try to install the deb I created through checkinstall it errors with:

dpkg: error processing libmtp_0.1.5-1_i386.deb (--install):
 trying to overwrite `/usr/bin/gcc', which is also in package gcc

---

### Post by johnzbesko on 2007-06-02
OK, following the instructions/comments/other links, I am able to get amarok to recognize a Creative Zen and list all the songs within. However, when I attempt to play a song by double-clicking on it, I get an error message "Error Loading Media Could not open file"

This error does not occur if I am using an iPod, i.e. the song plays. I also notice that the song file on the Zen seems to be recognized as a "stream", as opposed to an mp3 file, which is is.

I have not tried reading or writing to the device as I don't want to mess my daughter's music collection up.

---

### Post by llzero1337 on 2007-08-07
the wget are 404

---

### Post by Graduate on 2007-08-22
> **Jarn said:**
> I'm trying to install libmtp, but when I try to install the deb I created through checkinstall it errors with:

dpkg: error processing libmtp_0.1.5-1_i386.deb (--install):
 trying to overwrite `/usr/bin/gcc', which is also in package gcc
Fixed this problem running
sudo aptitude purge gcc

but i think i broke my system now. Don't know if i can fix it.

> **llzero1337 said:**
> the wget are 404

I went to the website where the files are and just edited the wget with the latest amarok files.

---

### Post by AdotB on 2007-08-25
> **Jarn said:**
> I'm trying to install libmtp, but when I try to install the deb I created through checkinstall it errors with:

dpkg: error processing libmtp_0.1.5-1_i386.deb (--install):
 trying to overwrite `/usr/bin/gcc', which is also in package gcc

I have encountered this problem using checkinstall a lot lately. The way i fix it involves a little manual package editing:
```
dpkg -x <deb file> <folder to extract to>
dpkg -e <deb file> <folder to extract to/DEBIAN/>
```

Then i delete all the files that conflict with other packages (I don't know why these are included. If anyone knows how to prevent this, please let us know.) and repackage it with the following:
```
sudo chown -R 0:0 <folder to extract to>
sudo chmod -R 775 <folder to extract to>
dpkg -b <folder to extract to> <new deb file> 
```

---

### Post by link48010 on 2008-07-17
I've got it working. I installed both libmtp and Amarok (and all Dependant packs as well) with synaptic. Plugging in my Zune didn't work automatically, so I went to Settings>Configure Amarok>Media Devices>Add Device>Added it with the MTP handle and my name. When I plugged it and Hit connect it worked like a champ. Note, that only music can be seen, Pictures, Podcasts, etc. cannot be seen via Amarok. Also right clicking files and selecting "Copy to Collection" always seems to fail. I have the Zune 30 w/2.5 firmware. Note*Copying files from the Zune takes a long time, but I can still play music on my Zune device while I'm pulling music off which is nice (Just don't try to play the music you are syncing, if they happen to use the same file at the same time it will lock Amarok and the Zune up too requiring a Back+Down restart on the Zune).

Edit: I'm using Amarok 1.4.5 with Feisty. Sorry but I'm a n00b at anything linux.

---

### Post by raiderleaf on 2009-04-29
Does anyone know if this works right for Ubuntu 8.04 LTS ?

---

### Post by Wartender on 2009-05-13
oi just a couple fo questions. will this work for zune? i got linked to this thread from another as a solution for using zune on linux. and btw in synaptic there's a libmtp 0.3.0 , i'm guessing that will work? and i just have to install amarok?

---

