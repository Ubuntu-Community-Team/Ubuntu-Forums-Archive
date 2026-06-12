---
title: "How to install Adobe Air in Ubuntu 8.04 [64-bit]"
date: 2008-10-07
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxed on 2008-10-07
[color=red]**UPDATED:**[/color] *20/02/10*
This guide has been updated for Ubuntu 9.10 (karmic).  Please note that this guide is only for 64-bit users.  If you are running a 32-bit operating system then you won't need quite a few of the steps listed here.


The Adobe website currently offers a Linux version of their Air runtime.  Unfortunately the current version is only available to install on 32-bit platforms.  The Air runtime actually runs quite well on 64-bit platforms but getting it installed requires a few extra steps.  This guide will attempt to walk you through the process of installing the Air runtime in a 64-bit environment.  As a time saver you may want to simply copy the text below from the code boxes and paste it directly into your terminal window.


The first step is to download the Air runtime [_from here._](http://get.adobe.com/air/)  You will also need to download the ia32-air-libs archive attached to this post.  Make sure to download these files to your desktop as the steps below assume that the files can be found in your desktop folder.


[list=1]
[*]Once you have those files downloaded you need to install the ia32-libs package if it is not already installed.
```

sudo apt-get install ia32-libs

```
[*]The ia32-air-libs.tar.gz file contains a few 32-bit libraries that are missing from the ia32-libs package but are necessary for either installing air, installing air apps, or running air apps.  The missing libraries may not present any immediate problems and you can probably get through the installation without them, however you will eventually discover errors with certain air apps if these libraries are missing.  If you decide to continue without installing these libraries then you may be presented with the following error during installation.
```

(setup:6859): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so: wrong ELF class: ELFCLASS64

```
Type the following to extract the libraries to your lib32 folder.
```

sudo tar --overwrite -xf ~/Desktop/ia32-air-libs.tar.gz -C /usr/lib32

```
[*]You're now ready to install Air so make the bin file executable.
```

chmod +x ~/Desktop/AdobeAIR*.bin

```
[*]And now start the installation.
```

~/Desktop/AdobeAIR*.bin

```
[*]Click "I agree" and then enter your system password when prompted.
[*]After the installation you'll need to move one of the adobe libraries to your lib32 folder.  If you don't move this library then the following error will be displayed anytime you try to install an air app.
```

/usr/bin/"Adobe AIR Application Installer"

Error loading the runtime (libadobecertstore.so: cannot open shared object file: No such file or directory)

```
Move the library with the following command.
```

sudo mv /usr/lib/libadobecertstore.so /usr/lib32

```
[*]For whatever reason Adobe chose to use an extremely long and inconvenient filename for their app installer shortcut (/usr/bin/Adobe AIR Application Installer).  If you plan on installing any apps from the command line I'd recommend creating a new and much easier to remember shortcut.
```

sudo ln -s "/opt/Adobe AIR/Versions/1.0/Adobe AIR Application Installer" /usr/sbin/airinstall

```
[*]To install an air app from the command line type the following.
```

airinstall /full/path/to/app.air

```
[/list]

---

### Post by yawl on 2009-03-10
Thank you! 

There is one step missing:

sudo ln -s /usr/lib32/libsmime3.so.1d /usr/lib32/libsmime3.so

---

### Post by rmcooke on 2009-03-18
I have followed the steps above on Intrepid 64 Bit and the installation of the Adobe AIR installer appears successful.

However, I get the following messages when launching the Installer:

```

richard@ubuntu:~$ "Adobe AIR Application Installer"
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

```


The installer application appears regardless and I try to install TweetDeck which installs and runs after a fashion.

All buttons in TweetDeck are then unresponsive and the application does nothing.

Has anyone solved this problem?

Thanks,



Richard

---

### Post by mouseclone on 2009-03-22
When trying install Air apps on Ubuntu 8.04 64bit clean install I get 
```
Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so: wrong ELF class: ELFCLASS64
Segmentation fault
```

I'm not sure where I need to go from here to get the Air installer working so that Air apps will work. I'm tired of fighting it for tonight.

---

### Post by linuxed on 2009-03-22
The instructions above were originally written for the beta version of Adobe Air for Linux.  They have since been rewritten for v1.5.1.  You may want to try the v1.5.1 installer from the link below.

[http://get.adobe.com/air/](http://get.adobe.com/air/)

Make sure to remove old versions of adobe air before installing v1.5.  You should be able to click on "Adobe AIR Uninstaller" from your Applications > Utilities menu.

---

### Post by mouseclone on 2009-03-22
Still no good for me.  I did what you said about removing the version I had installed.  Removed the folder and did a reinstall.  When I go to run an install app for Air I get a box and pops up and drops rather quickly.  I'm sure if I run from CLI that I will get the same thing as before.

---

### Post by linuxed on 2009-03-22
Just ran a few tests and apparently even v1.5.1 requires a few extra 32-bit libraries to be installed.  I just updated one of the steps in the instructions above.  Try following steps 3 - 16 again and see if that helps.  Then check if the required libraries are installed.
```

ldd /opt/"Adobe AIR"/Versions/1.0/airappinstaller
ldd /opt/"Adobe AIR"/Versions/1.0/Resources/"Adobe AIR Updater"
ldd /opt/"Adobe AIR"/Versions/1.0/Resources/airappinstaller
ldd /opt/"Adobe AIR"/Versions/1.0/Resources/appentry

```
If it's still not working then there has to be another 32-bit library you're missing.  Try running and installing the .air apps from the command line which should give you an error message stating which library is causing the problem.

---

### Post by linuxed on 2009-03-22
@rmcooke
[Try downloading this package](http://mirrors.kernel.org/ubuntu/pool/main/g/gvfs/gvfs_1.0.2-0ubuntu1_i386.deb) and extracting all the .so files to your /usr/lib32 folder and see if that makes any difference.

@mouseclone
Make sure you have the ia32-libs package installed.

**Edit:** One other thought, it occurred to me that some users may be trying to install Air on an earlier version of Ubuntu.  In those cases there may be some libraries missing from the ia32-libs package you install (i.e. libsmime3.so).  To ensure that all required 32-bit libraries are installed make sure that you do not install an ia32-libs package older than 2.2 (intrepid) or preferably 2.7 (jaunty).  You may want to download it manually from one of the links below instead of using apt-get.

[http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu18_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu18_amd64.deb)

[http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu4_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu4_amd64.deb)

---

### Post by binbash on 2009-03-22
> **linuxed said:**
> Just ran a few tests and apparently even v1.5.1 requires a few extra 32-bit libraries to be installed.  I just updated one of the steps in the instructions above.  Try following steps 3 - 16 again and see if that helps.  Then check if the required libraries are installed.
```

ldd /opt/"Adobe AIR"/Versions/1.0/airappinstaller
ldd /opt/"Adobe AIR"/Versions/1.0/Resources/"Adobe AIR Updater"
ldd /opt/"Adobe AIR"/Versions/1.0/Resources/airappinstaller
ldd /opt/"Adobe AIR"/Versions/1.0/Resources/appentry

```
If it's still not working then there has to be another 32-bit library you're missing.  Try running and installing the .air apps from the command line which should give you an error message stating which library is causing the problem.

Thanks for the update

---

### Post by linuxed on 2009-03-26
**Update**
The guide has now been completely rewritten for Ubuntu 8.10.  To this point I haven't experienced a single error or missing library file after following the steps posted above.  I've also created an ia32-air-libs package to help simplify the installation.  It contains all of the necessary 32-bit library files to run AIR that are not found in the ia32-libs package.  You can find the new package attached to the first post in this thread.

**Important**
If you are trying to install AIR on a version of Ubuntu earlier than 8.10 then you'll need to manually install the ia32-libs package.  The package you install MUST be >= 2.2ubuntu18.

**Moderators**
If a moderator happens to notice this post please update the title of this thread to display 8.10 instead of 8.04.  Thanks in advance.

---

### Post by accabrown on 2009-03-27
step 11 seems out of date in your instructions, at least with 8.10. The /opt/Adobe\Air/ directory exists, but there is nothing underneath it.

---

### Post by accabrown on 2009-03-27
Tweetdeck: I can get this to install, but when I try to run it from a command line I get a truly mysteirous error message: > sudo /opt/TweetDeck/bin/TweetDeck
Unkown desktop manager((null)), only Gnome and KDE are supported
But I *am* running Gnome.

---

### Post by linuxed on 2009-03-27
@accabrown
Step 11 in the updated guide refers to creating a symlink for installing air apps from the command line.  Assuming you installed AIR to the default location then you should have a "/opt/Adobe AIR" directory.  Make sure that you include the quotes when creating the symlink.  Otherwise the space between Adobe and AIR will cause an error to occur.

"/opt/Adobe AIR/Versions/1.0/airappinstaller"

Also, make sure that you're installing Air v1.5.1.  The guide was originally written for the beta version of Air but has since been rewritten for use with v1.5.1.

[http://get.adobe.com/air/](http://get.adobe.com/air/)

---

### Post by poozle on 2009-03-29
For anyone having troubles running Tweetdeck in 64-bit there is an extra set of libs needed.  If you have getlibs then you can use:

```

sudo getlibs -l libgnome-keyring.so
sudo getlibs -l libgnome-keyring.so.0
sudo getlibs -l libgnome-keyring.so.0.1.1
```

Which will then get it running.

I found this out here with a very quick google [http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

---

### Post by linuxed on 2009-03-29
> **poozle said:**
> For anyone having troubles running Tweetdeck in 64-bit there is an extra set of libs needed.  If you have getlibs then you can use:

```

sudo getlibs -l libgnome-keyring.so
sudo getlibs -l libgnome-keyring.so.0
sudo getlibs -l libgnome-keyring.so.0.1.1
```

Which will then get it running.

Have you tried this in Ubuntu 8.10?  Adding the libgnome-keyring libraries to the /usr/lib32 folder still doesn't help.  TweetDeck still opens with a line of icons across the top of the window and an empty area below them.  When you run /opt/TweetDeck/bin/TweetDeck as a normal user then no error message is displayed.  But when you run it with sudo then the following message is displayed.

sudo /opt/TweetDeck/bin/TweetDeck
Unknown desktop manager, only Gnome and KDE are supported

All of the required 32-bit libraries seem to be installed.  At this point I'm not sure what else to try. :?:

---

### Post by linuxed on 2009-04-03
Just now figured out what the problem was.  As it turns out if you're running KDE4 then TweetDeck seems to have a problem determining which desktop manager you're using.  In my case I was running Kubuntu 8.10 64-bit with KDE 4.1.  Each time I would open TweetDeck it would simply display a blank window with a row of buttons across the very top.  To be able to run TweetDeck successfully in KDE4 you'll have to install the kwalletmanager which will also upgrade you to KDE4.2.  Make sure to enable the intrepid backports in your sources.list file.  Anytime you want to run TweetDeck, first open KWalletManager from your Applications > Settings menu, then click on your TweetDeck icon or type /opt/TweetDeck/bin/TweetDeck.  As far as I can tell the libgnome-keyring libraries are not necessary in KDE4.
[list=]
[*]Enable intrepid backports.
```

sudo gedit /etc/apt/sources.list

```
[*]Delete the # from the lines below.
```

deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

```
[*]Click save and close gedit.
[*]Type the following:
```

sudo apt-get update
sudo apt-get install kwalletmanager

```
[*]Click on Applications > Settings > KwalletManager
[*]Type the following:
```

/opt/TweetDeck/bin/TweetDeck

```
[*]Enter a password when prompted.  If you don't enter the password quickly enough TweetDeck may go ahead an open which will cause the same blank window to appear.  If that happens go ahead and finish entering your password and then close and reopen TweetDeck.
[/list]

---

### Post by mark.rogers on 2009-04-08
I'm trying to install the 1.5.1 version of AIR, and unfortunately after following these docs, along with Adobes ([http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084)) all I get is the following:

[f4nt@f4nt-laptop:~/Downloads][]$  ./AdobeAIRInstaller.bin
[f4nt@f4nt-laptop:~/Downloads][]$

So I tried with sudo...

[f4nt@f4nt-laptop:~/Downloads][]$  sudo ./AdobeAIRInstaller.bin
[f4nt@f4nt-laptop:~/Downloads][]$

Nothing launches, can't find any stragglig PIDs lying around.. Nothing. I *did* just remove an older version of AIR prior to this. Any ideas?

EDIT:

Environment:
Ubuntu Intrepid 64BIT
Gnome

---

### Post by mark.rogers on 2009-04-08
Also is attached is the strace of the installer. Any thoughts?

---

### Post by linuxed on 2009-04-08
Try purging the two packages below.
```

sudo apt-get purge adobe-certs adobeair1.0

```
Remove the "/opt/Adobe AIR" and "/var/opt/Adobe AIR" directories and their contents if they're still on your system.
```

sudo rm -R "/var/opt/Adobe AIR"
sudo rm -R "/opt/Adobe AIR"

```
Make sure the Adobe AIR installer is executable.
```

cd /path/to/directory/containing/AIR/Installer
chmod +x ./Adobe*.bin

```
Make sure you have the ia32-libs package installed and that it's version 2.2ubuntu18 or higher.  And make sure that you install the ia32-air-libs package attached to the first post in this thread.  Try running the installer again.
```

./Adobe*.bin

```
You don't need to run it as root.  It will automatically prompt you for your password before installing AIR.

---

### Post by josel777 on 2009-04-16
Thank you! Worked like a charm.

---

### Post by linuxed on 2009-04-18
As long as you have Adobe AIR installed you shouldn't have any problems installing twhirl.  If you're running Ubuntu 32-bit then you can simply [_install the .bin file available from Adobe_](http://get.adobe.com/air/) without any additional steps.  If you're running Ubuntu 64-bit then follow the steps listed in the first post in this thread to install AIR.  Once installed simply [_download the twhirl .air file_](http://d.seesmic.com/twhirl/twhirl-0.9.2.air) and then click on the file to begin the installation.  I'm currently running Kubuntu 8.10 64-bit with KDE 4.2.2 and twhirl installed flawlessly.

---

### Post by revchris on 2009-04-25
I get this error when trying to install the ia32-air-libs.deb:

dpkg: error processing ia32-air-libs.deb (--install):
 trying to overwrite `/usr/lib32/libavahi-client.so.3.2.4', which is also in package ia32-libs
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ia32-air-libs.deb

---

### Post by linuxed on 2009-04-25
If you're running jaunty (9.04) or if you've installed version 2.7ubuntu6 of the ia32-libs package then you might not need the ia32-air-libs package.  This guide was specifically written for 8.10 and currently the latest version of ia32-libs available for 8.10 is 2.2ubuntu18 which doesn't contain a number of libraries required by AIR.  If you already have the libraries installed that the ia32-air-libs package provides then just skip that step.

---

### Post by batjew_beyond on 2009-04-25
Trying to install twirhl as well.
I have air installed after a few hitches here and there (Mostly old packages).
Now I'm getting this error when I run it from the Adobe Air Application Installer:
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiohal-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiohal-volume-monitor.so
Segmentation fault

---

### Post by revchris on 2009-04-25
> **linuxed said:**
> If you're running jaunty (9.04) or if you've installed version 2.7ubuntu6 of the ia32-libs package then you might not need the ia32-air-libs package.  This guide was specifically written for 8.10 and currently the latest version of ia32-libs available for 8.10 is 2.2ubuntu18 which doesn't contain a number of libraries required by AIR.  If you already have the libraries installed that the ia32-air-libs package provides then just skip that step.

Yes I'm on Jaunty.  When I try to install Adobe Air from the terminal, this error comes up: 
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

But when I click on the installer icon nothing happens. 

Edit:
I tried to run it from the terminal using the path from the shortcut, "/usr/bin/Adobe AIR Application Installer", but I get the following error:
Error loading the runtime (libadobecertstore.so: cannot open shared object file: No such file or directory)

---

### Post by revchris on 2009-04-25
Had to add this one step:
sudo cp /usr/lib/libadobecertstore.so /usr/lib32 

Got it from [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084&sliceId=1)

---

### Post by mark.rogers on 2009-04-28
I have Adobe Air working in Jaunty, however TweetDeck, Seesmic, and Twhirl all give me errors similar to items such as:

```
4/28/2009 13:40:08.923 [INFO] twhirl ----- initialized --------------------
4/28/2009 13:40:09.688 [INFO] twhirl AccountsManager - configuration file loaded
4/28/2009 13:40:12.567 [INFO] twhirl AccountsManager - configuration saved
4/28/2009 13:40:16.726 [ERROR] TwitterLib TwitterRequest - IO error: [IOErrorEvent type="ioError" bubbles=false cancelable=false eventPhase=2 text="Error #2032" errorID=2032]
4/28/2009 13:40:16.728 [ERROR] twhirl TwitterAccount - verifying credentials failed (TwitterEvent (type=error, status=-1, response=ErrorResponse (status=-1, message=Error #2032)))
4/28/2009 13:40:16.894 [ERROR] twhirl TwhirlAccount - storing password for f4nt failed, error: EncryptedLocalStore database access error
4/28/2009 13:40:18.221 [ERROR] TwitterLib TwitterRequest - IO error: [IOErrorEvent type="ioError" bubbles=false cancelable=false eventPhase=2 text="Error #2032" errorID=2032]
4/28/2009 13:40:18.222 [ERROR] TwitterLib TwitterService - request error: TwitterEvent (type=error, status=-1, response=ErrorResponse (status=-1, message=Error #2032))
4/28/2009 13:40:18.223 [ERROR] TwitterLib TwitterRequest - IO error: [IOErrorEvent type="ioError" bubbles=false cancelable=false eventPhase=2 text="Error #2032" errorID=2032]
4/28/2009 13:40:18.223 [ERROR] TwitterLib TwitterService - request error: TwitterEvent (type=error, status=-1, response=ErrorResponse (status=-1, message=Error #2032))
4/28/2009 13:40:19.244 [ERROR] TwitterLib TwitterRequest - IO error: [IOErrorEvent type="ioError" bubbles=false cancelable=false eventPhase=2 text="Error #2032" errorID=2032]
4/28/2009 13:40:19.244 [ERROR] TwitterLib TwitterService - request error: TwitterEvent (type=error, status=-1, response=ErrorResponse (status=-1, message=Error #2032))
4/28/2009 13:40:20.250 [ERROR] TwitterLib TwitterRequest - IO error: [IOErrorEvent type="ioError" bubbles=false cancelable=false eventPhase=2 text="Error #2032" errorID=2032]
4/28/2009 13:40:20.250 [ERROR] TwitterLib TwitterService - request error: TwitterEvent (type=error, status=-1, response=ErrorResponse (status=-1, message=Error #2032))

```

Any thoughts? This all works fine in Intrepid using the instructions provided here.

---

### Post by mark.rogers on 2009-04-28
fixed with:

apt-get install lib32nss-mdns

---

### Post by unimatrix on 2009-05-31
Now, see, this is why M$ still has the majority of users.
I'm not going to do 7 ******* step to install some shitty app. **** you Adobe.

---

### Post by genesis2seven on 2009-06-18
You don't have all these steps on 32 bit. The issues have a lot less to do with Linux/Ubuntu vs. Microsoft than the Adobe Developers and they way they've chosen to deploy their platform. Doesn't have to be as hard as they've made it.

---

### Post by bthodla on 2009-06-29
I am having problems installing Adobe Air apps on 32-bit Jaunty. The Adobe Air installation itself goes through but installing any app just freezes and needs to be terminated.

Can someone please point me to the steps?

Thanks.

---

### Post by v1nsai on 2009-08-11
I'm also having some AIR related issues, this seemed like a good place to post.  I'm using the Pandora app and every time I push a button, it opens a browser with the Pandora site.  Annoying as hell.

I wasn't able to install the ia32-air-libs.deb, it simply told me the install failed (I'm assuming its because that was directed toward users of 8.04) but I don't know what else to try, any suggestions?

---

### Post by afrodeity on 2009-08-18
> **linuxed said:**
> @rmcooke
[Try downloading this package](http://mirrors.kernel.org/ubuntu/pool/main/g/gvfs/gvfs_1.0.2-0ubuntu1_i386.deb) and extracting all the .so files to your /usr/lib32 folder and see if that makes any difference.

@mouseclone
Make sure you have the ia32-libs package installed.

**Edit:** One other thought, it occurred to me that some users may be trying to install Air on an earlier version of Ubuntu.  In those cases there may be some libraries missing from the ia32-libs package you install (i.e. libsmime3.so).  To ensure that all required 32-bit libraries are installed make sure that you do not install an ia32-libs package older than 2.2 (intrepid) or preferably 2.7 (jaunty).  You may want to download it manually from one of the links below instead of using apt-get.

[http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu18_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.2ubuntu18_amd64.deb)

[http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu4_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu4_amd64.deb)

I get this error when trying to install ia32-libs_2.2ubuntu18_amd64.deb
```
 Error. A later version is already installed 
```

The link for the ia32-libs_2.7ubuntu4_amd64.deb is broken. 

Which one does Ubuntu 8.04 need?

---

### Post by linuxed on 2009-08-18
This guide was updated for Ubuntu 8.10.  If you're using intrepid (8.10) or jaunty (9.04) you can simply install the package with apt-get install ia32-libs.  If you're using an older version of Ubuntu then you'll need to manually download and install the package.  Here's a list of mirrors for the ia32-libs package.

[http://packages.ubuntu.com/intrepid-updates/amd64/ia32-libs/download](http://packages.ubuntu.com/intrepid-updates/amd64/ia32-libs/download)

Once the ia32-libs package is installed you'll need to install the ia32-air-libs package attached to the first post in this thread.  If for some reason you can't get it to install then you can manually extract the libraries from the package into your /usr/lib32 folder.
[list]
[*]sudo file-roller /path/to/ia32-air-libs.deb
[*]Double click the data.tar.gz file
[*]Double click on . > usr > lib32
[*]Select everything in the file roller window and extract to /usr/lib32
[*]Go back to . > usr > sbin
[*]Extract airinstall to /usr/sbin
[/list]

---

### Post by SinCityBlues on 2009-08-27
Worked for Me! Thanks

---

### Post by bushda on 2009-09-11
I've followed all the steps listed here, and have performed each task. I'm still having no luck. I also followed the instructions on Adobe's web site. Nothing. 

I did a complete uninstall, and manually nuked all remaining references like /var/opt/Adobe\ AIR. I then did a fresh install, which was successful followed by an attempt at installing Tweet Deck and it fails. Here's the log from the terminal:

dbush@hunter:/share/air$ ./AdobeAIRInstaller.bin 
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
dbush@hunter:/share/air$ ls /opt/
Adobe  Adobe AIR  boxee  google
dbush@hunter:/share/air$ /opt/Adobe\ AIR/Versions/1.0/airappinstaller 
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(airappinstaller:10730): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/dbush/.recently-used.xbel', but the parser failed: Error reading file '/home/dbush/.recently-used.xbel': Is a directory.
Segmentation fault
dbush@hunter:/share/air$ 

The segfault is the same behavior I was getting before. 

I thought that perhaps I had a library permissions issue, so I scanned through /usr/lib32 and everything is world readable like it should be. 

This is happening on Ubuntu 9.04 64 bit. 

Tweet Deck and other Air apps work fine on my 32 bit system, and I'd really like to get them working on my 64 bit systems. I'd appreciate any tips that anyone might have.

---

### Post by LaughingBubba on 2009-09-23
Ok as of today (Wed 23-Sep 2009) the following worked for me:

I'm on Kubuntu 9.04 and I:

- de-installed previous adobe air attempts based on this post and others like [http://jamesfridley.com/2009/04/install-tweetdeck/]() via Kpackagekit (there's only about 5-7 entries if you type Adobe in the search bar)

- Re downloaded the installer (1.5.2) from the Adobe site [http://get.adobe.com/air/thankyou/?installer=Adobe_AIR_1.5.2_for_Linux](http://get.adobe.com/air/thankyou/?installer=Adobe_AIR_1.5.2_for_Linux)

- ran sudo chmod +x ./AdobeAIRInstaller.bin command over the location to where I downloaded it to ...

- ran the installer sudo ./AdobeAIRInstaller.bin

- Then downloaded Tweetdeck from the Tweetdeck site AND this time instead of it saying it need to install Adobe Air it it launched the AA installer window and pulled down Tweetdeck

- Hope this helps

Cheerio!

---

### Post by nualaor on 2009-10-15
I found a solution for ubuntu 9.04 64-bit,
[http://www.bauer-power.net/2009/05/getting-adobe-air-to-work-in-ubuntu-904.html](http://www.bauer-power.net/2009/05/getting-adobe-air-to-work-in-ubuntu-904.html)

plus another command.
```
$ sudo cp /usr/lib/libadobecertstore.so /usr/lib32
```

Done !

---

### Post by anotherone33 on 2009-11-20
ubuntu 9.10, x64:
I found and followed this guides:
[http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04](http://kb2.adobe.com/cps/408/kb408084.html#Installing_AIR_1.5_on_64-bit_Ubuntu_7.10__8.04_and_9.04)
[http://kb2.adobe.com/cps/408/kb408084.html#Required_32-bit_Packages_Libraries](http://kb2.adobe.com/cps/408/kb408084.html#Required_32-bit_Packages_Libraries)
install ok. at now running.

I ignore the error message after   ./AdobeAIRInstaller.bin 
```

Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: classe ELF errata: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: classe ELF errata: ELFCLASS64

```
and I go on.

Adobe\ AIR\ Application\ Installer 
is the tool for installing .air application, it is working only again some error messages ...
```

Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: classe ELF errata: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: classe ELF errata: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: classe ELF errata: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: classe ELF errata: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: classe ELF errata: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

```

bye.

---

### Post by Penguineer on 2010-01-17
I am running 9.10 64 bit.  I started with the installation instructions on the Adobe website for installing AIR (1.5.3).  Everything seemed to work.  A couple of the symbolic links setting commands returned "file exists" but no errors.

At the end, I had the AIR installer and uninstaller launchers on I had right click context menus on .air applications.  However, When I try to launch the application nothing happens.  Nothing at all.  No errors, no dialog box, not even a flash on the screen.  I have tried many of the steps here (and elsewhere) but can't seem to change anything.  When I attempt to run the command line (airinstall) I get "command not found." It is very hard to troubleshoot a bunch of nothing!  I would like to uninstall everything and start over, but with all of the manual file extractions and all, I am not sure how to get it all cleanly out.
Help?

---

### Post by roachkazy on 2010-03-15
I am having the same problem. I would love any help.

---

### Post by randolf_ambrose on 2010-05-12
excellent tutorial...

worked well except last step > airinstall

but now airinstaller works...

now i've tweetdeck installed and working...

thanks!!!

good work!!!

---

### Post by El1iP3S01D on 2010-05-25
linuxed, thank you very much! Your how to worked, i was able to install adobeari 1.51 and Tweetdeck...Thanks again..by the way you forget one more step; That is "sudo ldconfig" and voila...By the way, i've installed on Debian xfce4 lenny 64 bit...uhhh, how do i capture a picture of my screen to illustrate that ur how to worked?

---

### Post by El1iP3S01D on 2010-05-25
Folks, i finally installed Adobe Air 1.53, Tweetdeck and Tube...Here's the problem i did it as root not as user...So my question to all of you, How do i give myself access to Adobe Air and everything related to it?

---

### Post by sardamil on 2010-06-12
This line gave me an error message:

sudo mv /usr/lib/libadobecertstore.so /usr/lib32

mv: cannot stat `/usr/lib/libadobecertstore.so': No such file or directory

After looking around I found the file at:

/opt/Adobe AIR/Versions/1.0/Resources/libadobecertstore.so

Perhaps you should change this?

I got it working now. :)

---

### Post by axy_ugur on 2010-06-12
I installed thanks

---

### Post by mitcoes on 2010-09-10
As easy in 10.4 as install the bin.

chmod +x ~/Desktop/AdobeAIR*.bin
And now start the installation.
Code:
~/Desktop/AdobeAIR*.bin
Click "I agree" and then enter your system password when prompted.

---

### Post by volaer on 2010-10-21
I have here the instructions if you are going to install it in Ubuntu 10.04 64bit:
[http://brandbuildit.com/how-to-install-adobe-air-in-ubuntu-with-64bit-os/](http://brandbuildit.com/how-to-install-adobe-air-in-ubuntu-with-64bit-os/)

---

### Post by pjeide on 2010-12-20
These instructions worked great.  Was able to get Air 2.5.1 installed on Ubuntu 9.10 64bit without a hitch.  Running Pandora One desktop app!

Thanks!

---

