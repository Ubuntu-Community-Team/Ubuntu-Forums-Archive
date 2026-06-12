---
title: "Amd64 Dapper Howto, Install/DVDS/nvidia/Quake4/firefox32/etc"
date: 2006-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Floydius on 2006-06-15
**You can download this at my website [here]("http://www.floydius.com/linux/dapper64review.odt")**


**[SIZE="4"]Ubuntu 6.06 LTS (Long Term Service) Dapper Drake amd64 Install:[/SIZE]**

	My first experience with Linux was Mandrake (now Mandriva).   It was great, but lately it's been very disorganized and the releases have been a bit buggy, so I've been shopping around.  Everyone seems to love Ubuntu, and I wanted to give it a spin.  This is intended as a tutorial for those who may need some help installing.  These steps may not work for everyone, and I retrieved this information from various sources, I have tried to place links to all the ones I could remember.

**Installation**

	Install was easy, probably the most simple install of any Linux distro ever.  Download the &#8220;desktop&#8221; CD ([http://www.ubuntu.com)](http://www.ubuntu.com)).  The way Ubuntu does this is actually pretty creative.  Instead of dealing with the old text-based installs (at little scary for non-geeks), the developers use a live CD to get you started.  Pop it in the drive, hit enter at the menu for &#8220;Install or Run Live CD&#8221;, and you're on your way.  It boots up to Gnome (version 2.14.1) and there is a nice shiny &#8220;Install&#8221; icon waiting for you.

	The install routine is nearly foolproof, the only part that may cause confusion to those who've never installed their own OS before is partitioning.  I have two Hitachi 250GB SATA hard drives, one for Linux, and the other one (shamefully) for XP.  Don't partition over anything you want to keep!  In my case, my Linux hard drive was sda (probably hda if you use IDE hard drives), so that is what I formatted.  Just make sure to check out the existing partitions if you don't know what you're doing.  If you have a windows hard drive, the existing partitions will say either ntfs or fat32... if you want to keep your data, either back it up first, or don't format those partitions, because afterwards it WILL be gone.  In any case, I used the first 247 GB or so for my root partition ( / ) and the remainder for swap.  Some people recommend other arrangements, and of course you can always get Ubuntu to choose for you instead of doing it manually.  I left my windows drive (sdb) alone, and Ubuntu configured it automatically to mount.  You can even tell it where to mount, and I chose /mnt/xp because that's what is familiar for me, but leaving it in /media is fine too.

	After that, I let the install routine do it's thing, after a few minutes (not sure how long it took since I went to eat lunch and take a shower, but probably 15 minutes or so) it prompted me to reboot, remove the CD, and voila, it is installed!

**Setup**

	Hardware detection for Ubuntu is excellent.  It got all my hardware (including sound, wireless keyboard/mouse, my windows hard drive, video card, network, everything.)  The first thing I noticed (since my network card was so kindly working without any configuration needed) was that there were some updates available.  I clicked on that message, did the auto-update routine, and now my computer is up-to-date.  Next, I fired up Open Office and started typing this document.

	If you are going to be installing a lot of programs, libraries, or whatever, you should get your repositories set up.  Go to System --> Administration --> Synaptic Package Manager.  From there, Settings --> Repositories.  You will get a list of Repositories, or locations from which Ubuntu software packages can be downloaded.  Some will say &#8220;Officially Supported&#8221; while others will read &#8220;Community Maintained&#8221;  You should check in the Universal Repositories at least for certain software packages.  

**Video**

	The first thing I wanted to do was get my video drivers set up.  Ubuntu configured my screen resolution at 1024 x 768, and I needed it to be 1280 x 1024.  In the screen resolution section, it would not let me go any higher.  (Note: This is quite strange, but I reinstalled Ubuntu with this exact same CD, because I had screwed up X11 doing something and couldn't figure out where my permissions needed to be changed.  Using all the same config options, it detected my monitor resolution correctly the second time... so weird).  I fixed this by typing in console after #

sudo dpkg-reconfigure xserver-xorg

Follow the instructions and use defaults if you don't know what you're doing; when it comes to the resolutions, just choose the ones you want.  This is also a good method for adding resolutions for later and setting up your general xorg options.

Installing the nvidia drivers was as easy as pie.  System --> Administration --> Synaptic Package Manager.  Choose nvidia-glx, install it.  Edit your xorg.conf (/etc/X11/xorg.conf) in the device section to say &#8220;nvidia&#8221;, instead of &#8220;nv&#8221;, and you're up and running. (You might have to reboot or log out, then log back in).

To test, I use glxgears.  They stopped outputting the fps by default because people were using it as a benchmark. I'm not sure why they care, but anyway, here is how you can check.  in console:

glxgears -iacknowledgethatthistoolisnotabenchmark

or

glxgears -printfps

and mine:

72452 frames in 5.0 seconds = 14490.223 FPS
75419 frames in 5.0 seconds = 15083.717 FPS
74907 frames in 5.0 seconds = 14981.352 FPS
75422 frames in 5.0 seconds = 15084.291 FPS
75507 frames in 5.0 seconds = 15101.395 FPS

anything up in the 5000+ range generally means its working.  yours might not be that high depending on your hardware/ram/cpu, etc.  I have a 7800GT and 2GB of corsair so that explains how it is that high.

**Quake 4**

Of course, nothing tests video like a good game, so i whipped out my copy of Quake 4, which can run natively on linux.  (as can Doom 3, UT2004, and many others.)  Unfortunately, not all games do, but you can always try Cedega (aka WineX). I'm not sure if that runs in amd64 or not, you might have to use a chroot solution for that.

How easy was it to get Quake 4 up and running?  Very.  Here's how (see the official page [here]("http://zerowing.idsoftware.com/linux/quake4/")):

1.Download linux installer file here:  [ftp://ftp.idsoftware.com/idstuff/quake4/](ftp://ftp.idsoftware.com/idstuff/quake4/)
2.make the installer executable. (right click on file, and in permissions, check executable under &#8220;user&#8221;), or 
```
$chmod 755 quake4-linux-1.2.1.x86.run
```  as explained [here]("http://www.lucentplum.com/?p=16") 
3.Double click on the file and run it.  Follow the Installation routine.  I chose to put mine in /home/yourusernamehere/games/quake4 and I put my symbolic links in /home/yourusername since i have permissions there.
4.Copy all the pak files from the q4base directory on the DVD (or CDs) to the q4base directory in your install (dont overwrite anything, if the installer has a file of the same name placed there, just leave it).
5.Frag! (With High Quality, 1280x1024, 16xAA my avg FPS on a timedemo was 77fps.)

Some issues I had were: 

A) at first, only the SMP binary worked for me.  This website, [http://www.lucentplum.com/?p=16](http://www.lucentplum.com/?p=16) helped me fix that.  During one install, I had an issue where the sound worked, but no voices.  [EDIT]: The no voices problem came from me forgetting to copy the ZPAK files from the DVD, apparently they contain the voices.[/EDIT] Your milage may vary, but the first install I did with the above instrustions went very well.

B) If you have your keyboard set to international, you may not be able to use the console (Ctrl + Alt +  ~). You may have to set it to regular in order to use that.

**Watching DVDs**

If you pop in a DVD with just about any stock linux distro, it will generally not read immediately.  (this is true of a fresh Windows install as well, but few people realize it because there is generally DVD software installed with their system if they bought it from a vendor instead of building from scratch).

So what do you do?  There are detailed instructions here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats).
That link will give you tons of information, I suggest reading it, even if you don't use another flavor of linux than Ubuntu.  Please note that this may or may not be legal in your country of residence.  Nonetheless, these are the quick steps from the aforementioned guide.

1.Install the libdvdread & libdvdnav (or just install the vlc package, it provides both) via Synaptic.
2.(**If you are running amd64 version**) install debhelper, build-essential, and fakeroot packages via Synaptic.
3.run this in console: $sudo /usr/share/doc/libdvdread3/examples/install-css.sh (make sure Synaptic is closed if you still have it open before you run this, otherwise it will not complete.)

If you're going to use totem, you'll have to install the totem-xine package to use the xine backend.  Totem-gstreamer currently does not support DVD decryption (as of version 0.10). that may change later, but for right now that's the case.  Also, for some reason, VLC does not want to play a dvd in menus mode.  It crashes every time with a segmentation fault, at least in amd64.

**Java**

The instructions I used can be found here:  [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava)

this is just a summary of those instructions:

For the main Java environment, use sun-java5-bin and j2re (blackdown) packages.

run #sudo update-alternatives --config java to choose the java environment default.

**There seems to be a bug with openoffice, as it does not want to use new java installations, this is not limited to Ubuntu, as seen on some other forums, including FC5.**

**Firefox**

And now, for 32bit firefox, First though, why would you want a 32bit firefox?  There are some things that are not yet available in native 64bit versions.  Some things will work with 64bit firefox, for instance, VLC with the mozilla-plugin-vlc package works fine in 64bit firefox.  However, playing any videos which require w32 codecs (wmv, etc) do not.  Mplayer and the mplayer plugin work fine too, but have the same restriction.  There is no flash (yet) for 64bits, and also no java web plugin.  So, as you can see, your browsing experience may be somewhat limited, but you can install a 32bit firefox to fix some of these issues.

**[SIZE="3"]these instructions are ripped directly from [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) (with spelling fixed):[/SIZE]**

**1 - Install suport for 32 bit applications :** 
sudo apt-get install ia32-libs ia32-libs-gtk linux32 
**2 - Download firefox 32 bit version from [www.getfirefox.com](www.getfirefox.com) **
 [http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US) 
(Another kind of installation is in FirefoxNewVersion which however differs in some details (installs into /opt; replaces regular /usr/bin/firefox with a new command), but I never tested :S ) 
**3 - Untar the downloaded file like you always do in Ubuntu, and go inside the directory : **
cd ~/Desktop/firefox 
(or go where the uncompressed file is) 
**4 - Create a folder for the 32 bit firefox installation, and copy firefox there :** 
mkdir /usr/local/firefox32 
cp -r -p ./* /usr/local/firefox32/ 
**5 - Create the execution files for 32 bit firefox : **
sudo nano /etc/pango32/pangorc & 
Next add this text to the file : 
[Pango] 
ModuleFiles=/etc/pango32/pango.modules 
[PangoX] 
AliasFiles=/etc/pango/pangox.aliases 
Then create another file : 
sudo nano /usr/local/bin/firefox32 & 
Next add this text to the file : 
#!/bin/sh 
export GTK_PATH=/usr/lib32/gtk-2.0 
export PANGO_RC_FILE=/etc/pango32/pangorc 
linux32 /usr/local/firefox32/firefox $@ 
**6 - Make it executable : **
sudo chmod +x /usr/local/bin/firefox32 
**7 - Check if your new 32 bit firefox is working :** 
firefox32 & 
(it says warnings but doesn't matter) 
**11 - To install Java player to run applets, go to  [http://www.java.com](http://www.java.com), and download the linux self-exstracting file for 32 bit linux computers (I was surprised to see than this file works in amd64 bits Breezy installation) : **
 [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) 
**12 - To install java : **
sudo bash 
chmod 777 ./jre-1_5_0_06-linux-i586.bin 
(this file name will depend on the java version you download) 
./jre-1_5_0_06-linux-i586.bin 
(it will ask you some questions) 
mkdir /usr/local/java32 
cp -r -p ./jre1.5.0_06/* /usr/local/java32 
cd /usr/local/firefox32/plugins/ 
ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./ 
**13 - Restart firefox32 and check if java is working : **
firefox32 & 
**14 - Visit :  [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) **
**15 - Add an icon at the top panel to start this 'cool' browser :** 
Click with the right button at the top panel 
Choose : Add to panel 
Choose : Custom application launcher, and press 'Add' button 
Name : firefox32 
Generic name : Firefox 1.5 32 bits 
Comment : Firefox with 'Flash' and 'Java' 
Command : firefox32 
Type : Application 
Icon : /usr/share/pixmaps/mozilla-firefox.png 
**16 - Enjoy the net !**

**For the non linux savvy, nano is just a text editor.  you can get the same results using gedit if you dont have nano installed.  Also, I'm not sure what steps 8 &#8211; 10 were, but they're absent on the website.  Following the instructions as listed above worked fine for me.**

*Plugins for 32bit firefox:*

Java:  the instructions above explain how to get java going.
Flash: once you get the 32bit firefox working as above, you can use the regular firefox plugin installer to install flash.  (i always go to [www.nvidia.com](www.nvidia.com) and click on the green puzzle piece.)
Video:  Video is a bit more difficult.  As mentioned before, some things work fine in 64bit firefox.  To get video going in 32bit firefox, from what I understand, you would need to set up mplayer or some video player with the plugin in a 32bit chroot environment.  I have not attempted this, but look around [www.ubuntuforums.org](www.ubuntuforums.org) for some discussion of this.  Anyone who wants to add to this section is more than welcome.

Hopefully this will help some people do some basic things with their linux installation.  Feel free to let me know if you want to add anything.  You can also download the openoffice version of this here:
[http://www.floydius.com/linux/dapper64review.odt](http://www.floydius.com/linux/dapper64review.odt)

God bless!

---

### Post by acad on 2006-06-23
What's the best approach for installing 32 bit applications on a **AMD64 Ubuntu 6.06 Dapper** installation?  I see an older chroot How-to for Unbuntu Hoary [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32+bit](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32+bit) , but I'm not sure if parts of it are outdated.  I've seen how you installed firefox 32bit in this How-to and it looks pretty interesting.

I'm new to Ubuntu & 64 bit Linux; does AMD64 Ubuntu 6.06 Dapper come with SMP enabled or do I have to install an alternate kernel or rebuild the kernel?

Thanks;

Acad

---

### Post by jinacio on 2006-06-23
I keep forgetting about firefox 64/32 windows, so...

At the top of "/usr/local/bin/firefox32", i added:

```

#!/bin/sh
FF64_RUNNING=`ps aux | grep /usr/lib/firefox/firefox-bin | grep -v grep -c`
if [ "${FF64_RUNNING}" -gt "0" ]; then
        zenity --error --text="Firefox 64 Bits is already running.\n\nPlease close all it's windows before running Firefox32"
        exit 1
fi;

```

Now i **always** remember to close my windows 8-)

Cheers

---

### Post by Zybernaut on 2006-07-03
[quote=acad]What's the best approach for installing 32 bit applications on a **AMD64 Ubuntu 6.06 Dapper** installation?  I see an older chroot How-to for Unbuntu Hoary [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32+bit]("http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32+bit") , but I'm not sure if parts of it are outdated.  I've seen how you installed firefox 32bit in this How-to and it looks pretty interesting.
[/quote] 

I followed that How-to, replacing the Hoary referances with "dapper", and chroot seems to be working. At least as far as installing and running Adobe Reader 7.0.
[SIZE=2][COLOR=Red]
I'm still trying to figure out how to let 32 bit apps, particularly  Adobe Reader 7.0, access the 64 bit /usr/bin/lp or some other way to print.  [B]
Anyone have any suggestions? :confused:[/B][/COLOR][/SIZE]

TTFN
   Tom

---

### Post by Floydius on 2006-07-08
sorry, i dont know a whole lot about the chroot thing beyond the firefox install above; it can get so complicated (too complicated to be worth it, for me) -- I think I may just try to install the 32bit version on this computer.

Before I go that route though, i want to run some benchmarks (like quake 4, etc) to see how the 2 systems compare speedwise.  i have a feeling compiling will show the biggest difference; anyone know some good tests I should run before a reinstall?

---

