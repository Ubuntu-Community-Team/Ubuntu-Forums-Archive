---
title: "Flash doesn't load video in Firefox"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by alcla on 2012-09-23
Adobe Flash Plugin 10 version 11 doesn't load video in Firefox.

Flash videos or games on sites like Facebook or YouTube may appear, black, white or grey and never play.

I upgraded to Ubuntu 10.04 - The Lucid Lynx - released in April 2010.

Is there a fix for this.

---

### Post by daslinkard on 2012-09-23
Try this first:

```
sudo apt-get remove flashplugin-nonfree
```
```
 sudo apt-get install flashplugin-nonfree 
```

Let me know if this works for you....

---

### Post by alcla on 2012-09-23
> **daslinkard said:**
> Try this first:

```
sudo apt-get remove flashplugin-nonfree
``````
 sudo apt-get install flashplugin-nonfree 
```Let me know if this works for you....

I tried the 2 commands, and there seems to be no difference on Utube. Here is the terminal code:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-opengl libavutil1d gtali gimp-help-en glchess libgcj-bc gnobots2
  xulrunner-1.9 libregexp-java python-gtkglext1 lightsoff liblog4j1.2-java
  libaccess-bridge-java-jni libpostproc1d libaccess-bridge-java seed gnibbles
  gimp-help-common libbcel-java swell-foop gnotski gij liblzo2-2 iagno glines
  cabextract gir1.0-gconf-2.0 gnotravex gnect gir1.0-clutter-gtk-0.10 libdb4.6
  libpt-1.10.10-plugins-v4l python-smartpm openoffice.org-help-en-gb
  libgtkglext1 libmx4j-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alfred@alfred-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Broken packages

---

### Post by mansonfan78 on 2012-09-23
Firefox has an add-on called flash-aid that might help you.  It'll remove any conflicting files and reinstall flash automatically.

---

### Post by daslinkard on 2012-09-24
> **mansonfan78 said:**
> Firefox has an add-on called flash-aid that might help you.  It'll remove any conflicting files and reinstall flash automatically.
Did mansonfan's suggestion help you?

---

### Post by Puzzleman on 2012-09-24
I'm a newbie but experienced a similar problem after installing 12.04.

I went to the ubuntu  software center through the provided link on the menu bar and typed in "flash" in the search engine. Amongst the programs which appeared was Adobe Flash Plugin which I loaded. Problem over.

I hope it is that simple for you.

Puz.

---

### Post by alcla on 2012-09-24
> **daslinkard said:**
> Try this first:

```
sudo apt-get remove flashplugin-nonfree
``````
 sudo apt-get install flashplugin-nonfree 
```Let me know if this works for you....

This did n ot work.

---

### Post by daslinkard on 2012-09-24
**Step 1: Disabling bcm43xx**
Ok, so first thing we need to do is make it so that the pre-installed  driver, bcm43xx, doesn't attach to the hardware on bootup.  The way we  do this is by blacklisting it.  In a terminal window type:
 	```
sudo gedit /etc/modprobe.d/blacklist
```
	 
in the window that pops up, find a new line and type: blacklist bcm43xx

After this, reboot and make sure that when you go to System >  Administration > Networking there isnt a listing for your wireless  connection

**Step 2: Get ndiswrapper**

Make sure you have the universe repositories enabled. (google it if you  dont know how) and go to a terminal and type the following:
 	```
sudo apt-get install ndiswrapper-utils
```
	 
this might prompt you for your password and ask you to continue and such, its very easy, just go through it.

**Step 3: Use ndiswrapper to configure the drivers**

Get the drivers you need, i suggest [these ones]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip"),  and make sure u have the .inf and .sys files of the driver.  If you use  the ones i suggested they will be bcmwl5.sys and bcmwl5.inf

Once you have the driver, put them on the desktop and then go to a terminal and type:

 	```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```
 	 
this will install the driver

then, in the same terminal window, type:

 	```
sudo ndiswrapper -m
```
 	 
now restart and you will be able to connect to wireless networks.   If you have a wep encryption on your wireless network, go on to step 4  below.  

**Step 4: Installing Network Manager**

Network manager will allow you to connect to those wep encrpypted networks.

Simply go to a terminal window and type:

 	```
sudo apt-get install network-manager-gnome
```
 	 
Let that install by typing your password and whatnot, then restart  and you will be good to go, just click on it up in the corner and  select your wireless network.

**Still not working?**
If you still cannot connect to a wireless network try running the following commands in terminal
 	```
modprobe ndiswrapper
```
	 
and
 	```
echo ndiswrapper >> /etc/modules
```

---

### Post by Cavaticus on 2012-09-24
Adobe dropped flash support for Linux, unless Mozilla makes some sort of deal with Adobe and releases a plugin (like Google did with Linux Chrome), you will see less support for flash as websites begin to rely on newer versions of flash.

[http://news.softpedia.com/news/Adobe-Drops-Flash-for-Linux-Except-in-Google-Chrome-254483.shtml](http://news.softpedia.com/news/Adobe-Drops-Flash-for-Linux-Except-in-Google-Chrome-254483.shtml)

I ::shudders:: installed Chrome on my laptop running 12.04 in case something doesn't load right as I am scouring the web for the latest lolcats. 

Note:
Chromium doesn't have the flash support last I checked. Just the official Chrome release. :(

As a side gripe:
Unless Firefox starts supporting webkit prefixes other website feature may become inaccessible too.
::kicks dirt at Google and Apple for undermining W3C standards for an open web:: :mad:

---

### Post by alcla on 2012-09-25
> **mansonfan78 said:**
> Firefox has an add-on called flash-aid that might help you.  It'll remove any conflicting files and reinstall flash automatically.

                                  [SIZE=4]From the menu, I selected the Flash Aid Wizard, and the following occurred:[/SIZE]
 

 [SIZE=4]First window:[/SIZE]
 [SIZE=4]Flash-Aid has detected that your browser architecture is 32bit and selected the best plugin for you. By default, Flash-Aid selects the latest development version from Adobe Labs, which usually works better than the stable release. However, such version may not be as secure as the stable version from the repositories.[/SIZE]
 

 [SIZE=4]Second window:[/SIZE]
 [SIZE=4]Flash-Aid has detected the plugins you have installed and selected them to be removed. This is essential to make sure the new plugin gets loaded by Firefox.[/SIZE]
 

 [SIZE=4]Third window:[/SIZE]
 [SIZE=4]Flash-Aid has automatically selected the available tweaks for your system. Deselecting a tweak will remove it, if already appllied.[/SIZE]
 

 [SIZE=4]Forth window:[/SIZE]
 [SIZE=4]Flash-Aid generated a shell script with the commands necessary to perform the plugin maintenance. The script can be executed automatically by Flash-Aid or can be exported to your Desktop, for manual execution. When executing the script, either via Flash-Aid or manually, your password will be requested, since some actions require administrative privileges.[/SIZE]
 

 [SIZE=4]Then I clicked finish, and got a terminal with the following error message:[/SIZE]
 [SIZE=4]There was an error creating the child process for this termina[/SIZE]
 

 [SIZE=4]From the Flash Aid menu, I selected preferences, and got the following:[/SIZE]
 [SIZE=4]/usr/bin/X11/gnome-terminal[/SIZE]
 [SIZE=4]The Terminal path is required for running the extension. The default should be fine for most systems, but if you get any child process errors while trying to execute the script, then select a different emulator like gnome-terminal or konsole, located in the /usr/bin directory.[/SIZE]
 

 [SIZE=4]Was I suppose to change the terminal path? If so, what changes should be made?[/SIZE]

---

### Post by mansonfan78 on 2012-09-25
I think I might have had a problem with gnome terminal once with flash-aid.  Since I also have xfce installed I switched it to /usr/bin/xfce4-terminal and it's worked fine since.  If you don't have another terminal emulator you should be able to install one easily enough from synaptic without it pulling in to many dependencies.  Sakura doesn't have any dependencies, but I've never used it, so no guarantees.

---

### Post by HiImTye on 2012-09-26
> flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
```
sudo apt-get install flashplugin-installer
```

---

