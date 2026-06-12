---
title: "HOWTO: Install the most common software we might need for an absolute N00b"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by boom2k1 on 2008-04-26
Preface:

I was writing this for my girlfriend so she can install the most often used **software** in Ubuntu in my attempt to help her experience Linux!

This is not really a guide to help you fix any hardware related issues, since I am no expert.
To my surprise, I only have very minor issues with any of my hardware. [ie. some keys are not mapped, some axillary mouse buttons don't function]


Overall, I am so impressed by Ubuntu 8.04 since becoming an Ubuntu user 2 years ago. Installing software in Ubuntu is so darn easy nowadays. [I rarely HAVE TO use the console.]
 - This guide is far from perfect.

*This thread might disappear quickly because I really don't plan to update/ edit it often... but as a starting point for Ubuntu newbies, I hope it might help! Here are a few pointers I made while installing 8.04 from the scratch.

==========================================================
Ubuntu installation process 

[before you do these, you may wish to explore Ubuntu a little bit first.. navigate around without screwing stuff]

    * [optional] System -> Preferences -> Appearance -> Fonts  [change the size of Application, Document]
          o or right click empty space on desktop -> Change Desktop background -> Fonts
    * System->Admin->Software Source: under Ubuntu Software Download from: Main server
                +  [this is needed because last time when I install, there are a lot of software sources which aren't available]
          o Enable Multiverse... check every sorce there
          o Third-Party software tab.. select both -close, reload.
    * System and Administration -> Update Manager -> Check
    * To install Adobe Flash Player for firefox (3 beta5!)
          o Go to [www.youtube.com](www.youtube.com)
            try watch a video, additional plugins required prompt.. -> Install Missing plugins -> ADOBE Flash Player (Installer)
            Enable additional components popup appears:
            Press Yes to enable multiverse
                + [Alternative: enable Multiverse (way... Software Source first page)]
                  Downloading package.
                   -wait
                + Problem... too busy server?         The CA servers failed... high capacity?
                      # if Plugin Finder service hanged.. keep pressing the X button of the window to force quit.. that's why I needed to change Software source to the Main server
                + flash should work now.
                      # Also good for checking if the sound/internet works....


    * You may also wish to use the proprietary driver for your graphics card (so you get 3D acceleration) --in my opinion, it is probably only needed for 3D games & advanced desktop effects [which are really cool.. but then it slows the system a bit AND can cause some trouble which I can't solve yet.. ie. wake up after suspending desktop]... but anyway, it is a good idea to enable restricted driver first
          o from System->Administration-->Hardware driver -> Enable restricted driver of your graphics card
          o *new video cards may be more tricky and require downloading files from the web.


Other installation:

    * Overview: Most of the stuff is available from Add/Remove
    * The programs which I need to find from webpages so far are:
          o  Skype (easy), Acrobat Reader (easy), Realplayer (tricky)





Part 1
From Add/Remove. Applications --> Add/Remove

*The easiest way to add software is to use Add/Remove

-To install some of the packages, may need to enable Multiverse, etc.... just press enable when prompted
    In Add/Remove
        May wish to have Software to check: (from Show All available applications)  (and sort by popularity)

Select software (recommendation):
From

    * Accessories:
          o RAR
          o 7-zip: community maintained software [Enable]
    * Internet:
          o Sun 6 Java: when check, Enable installation of unsupported and restricted software prompt will appear.. press enable
          o Mozilla Thunderbird (although you may argue Evolution works very well already)
          o Gmail Notify or CheckGmail [pick one... I am testing CheckGmail now]
          o Emesene (3 stars?) [windows live messenger alternative.. I find it superior to aMSN because of its simple look, but aMSN has more features].. although the preinstalled Pidgin serves the basic purpose of MSN anyway.. I use it because it has offline message support + it just feels better.
          o For Google centric user:
                + Google Mail (GMail) Prism for Google Mail (2 stars), Google Calendar for Prism, etc....  [allow you to run those web services as applications]
    * Sound & Video
          o VLC Media Player...  (very well known)
          o We also need media codec to listen to songs, etc.. since Ubuntu by default doesn't come with media support for proprietary formats
                + GStreamer extra plugins
                + GStreamer ffmpeg video plugin
                + GStreamer plugins for mms, wavpack, quicktime, musepack,
                + GStreamer plugins for aac, xvid, mpeg2, faad,
                      # having all these we will probably not run into that much trouble later
          o there are a lot other cool things you might want.
                + ie. Soundconverter (for me)
                + gtk-recordMyDesktop (for me)
    * System Tools
          o video card driver... NVIDIA or ATI... well.. I would choose to use the System->Administration->Hardware driver ->Enable Restricted driver way
          o Virus Scanner [perhaps we don't need it]

Perhaps later:

    * Install SCIM, SCIM-bridge from Add/Remove or Synaptics if you want to type in foreign language... [haven't done it on mine yet]
    * Graphics:
          o PDF Editor (later) [if you need]
    * Firestarter  [if you think you need. I didn't need]
    * Wine Windows Emulator (later?) [to run Windows software...] (Probably no need for now)
    * Other:
    * Advanced Desktop Effects Setting (ccsm) - (later?)
    * first, from System->Administration-->Hardware driver -> Enable restricted driver 
    * mine is a ATI x1250 (ATI Based video card, so xorg-driver-fglrx is selected by default)...[fancy desktop effect related stuff]


Other ways to install programs

    * Use Synaptic... System->Administration?? (or preference) -> Synaptics Package Manager? (something like this)... or if root access were granted there.... we would obtain root access by first opening the Terminal (console-based (dos-like command line program)  [Accessories->Terminal] and type         sudo synaptic
    * Command-based approach in Terminal... sudo apt-get install YOUR_SOFTWARE NAME... "double-tab" your keyboard for a list of name.. learn how to use the double tab feature to give hint to what to type next....  ie. type... sudo apt-get install ban   AND THEN "double tab"... automatical filling of "shee" or a list of ban*... words would be associated
          o sudo apt-get install is very convenient actually...
    * Get deb packages  from [www.getdeb.net/](www.getdeb.net/) ---> then double click on the downloaded packages
          o in my complicated deb packages like Openoffice.... you may need to install the deb in Terminal ... I forgot how too.
    * Others.... Automatix?? Envy, etc..... (i don't think I need it anymore.. Ubuntu seems to have come a very long way),

[only realplayer seems to require me to do that annoying chmod multistep console based installation stuff]
[Good news: i haven't done any tar xvf .... , sudo make, sudo install command line thing yet!]
--------------


Part 2
Install (download from web):

-Quick note: .deb packages are very easy to install in Ubuntu; it is the .exe analog from Windows... but more restrictive in that .deb only do installation [safer too]
)


From firefox:
    Save file : by default, files are automatically save to desktop
    To change it: Firefox edit-> preference -> DOwnloads: Always ask me where to save files

Things you might want to install:
Skype, Acrobat Reader, Realplayer (tricky) [may wish to hold off until you need it]

    * Download Skype: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)
          o Choose Ubuntu 7.04+
          o after download, double click the package, then install package (it will install other dependency automatically for you)


    * Download Acrobat reader [http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html) [do not download the .rpm version.. it is for other linux distribution.... not the same as deb]
          o choose Different language or oeprating system?
                + -installer: Linux -x86 (.deb)
                  Press continue -> Download...
          o installation then proceed the same way as Skype
    * Download RealPlayer
          o I download from   http:/www.tuxwerx.com/realplayer_11.0.0.4028-20080226_i386.deb
                + /opt/real/RealPlayer
                  click on realplay... guild you through
                + after installation, you will still not see anything from Application .... you will have to manually add the launcher yourself
                      # ask how..
                            * otherwise, everytime you run it, you have to go to /opt/real/RealPlayer and click realplay... and then Run it
                            * to be edited:
          o or... [http://www.real.com/linux](http://www.real.com/linux)        [notice it is a tricky Realplayer11GOLD.bin] file
                + harder: Applications -> Terminal
                   "
                  - Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer11GOLD.bin" command from a terminal window.

                  - Run the .bin file by typing "./RealPlayer11GOLD.bin". Follow the prompts provided to finish installing the player.

                  - When you launch the player for the first time, a set-up assistant will take you through configuring your player.

                  - Enjoy your RealPlayer11 for Linux!"

My new favorite software:

    * Gnome-do [very good software launcher]  ([http://www.youtube.com/watch?v=aWVfsSZAuTs](http://www.youtube.com/watch?v=aWVfsSZAuTs))
          o to install, go to the Terminal (Application -> Terminal) and type
                + sudo apt-get install gnome-do
                      # sudo means "run as root (administrator)" so you can have all the administrator assess to ie. install software



Other preferences:

    * Clock setting. add weather
    * workspace Switcher Preference (below beside the trash)... 4 workspaces
    * add a system monitor to the panel below


Other guide:

    * Setup Pidgin:
          o ie. Protocol = MSN ... Screen name: [email]YOURNAME@hotmail.com[/email]
          o Better MSN client? (emesene)



Other reference:

    * [http://www.getdeb.net](http://www.getdeb.net) [newest .deb software which are not yet available in the main add/remove or Synaptics software channel]
    * [http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
    * [http://ubuntuforums.org/](http://ubuntuforums.org/)  [EXTREMELY USEFUL]




[http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron](http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron)





Minor tweak:

    * From sessions  (System->Administration or Preference?) --> Sessions
          o in the list of startup programs, add gnome-do (command: gnome-do   ???)

    * To make Skype font bigger (or other qt-based software fonts bigger)
          o sudo apt-get install qt4-qtconfig
                + then from the Terminal, type: qtconfig-qt4... then change font there
                      # [http://ubuntuforums.org/showthread.php?t=678123&highlight=skype+font](http://ubuntuforums.org/showthread.php?t=678123&highlight=skype+font)
    * System -> Administration -> Language Support
          o Enable Support for Complex Character... select language too..





My other annoyance:

    * Microphone sound doesn't work for me...
          o go Volume COntrol
          o Edit -> Preferences -> Capture/ Capture1   enable sound by unmuting it and brining up the volume of it
    * The other drives (partitions) don't mount properly)
          o changed fstab... in command: sudo gedit /etc/fstab 
                + ***** DO NOT MODIFY IT UNLESS YOU KNOW WHAT TO DO ***** (read up first)
    *


Thanks!

===============

---

### Post by dorkdork777 on 2008-04-26
Might be worth noting that you can use Synaptic or apt-get to get a package called ubuntu-restricted-extras, which will get you Java, Flash, a load of codecs, MS fonts, ability to extract RAR archives, and basic non-encrypted DVD playing functionality. Just an easy way to get all those functions, by selecting only one package.

---

### Post by Bethra 0_0 on 2008-07-18
Thank you!

---

### Post by SunnyRabbiera on 2008-07-18
also use this a reference:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by bodhi.zazen on 2008-07-18
It is also wise ot start with a version on Linux that already has much of this pre-installed.

Linux Mint has been very popular, but it has sun off and is now a distro in it's own right.

I suggest kiwi Linux. It is much closer to a default installation of Ubuntu but it has many of these things pre-installed as well as default applications more familiar to windows users (Thunderbird for example).

[http://kiwilinux.org/en/](http://kiwilinux.org/en/)

> Kiwi is a modified  [** Ubuntu**]("http://ubuntu.com/") live CD for the i386 architecture. It includes Romanian and Hungarian localization, multimedia codecs, encrypted DVD support, Flash plugin for Firefox, PPPoE GUI for accessing local internet services (Clicknet and RDS).

 The latest release, Kiwi 8.04 is based on Ubuntu 8.04. Differences from Ubuntu include replacing Evolution with Thunderbird, Rhythmbox with Audacious and dropping Ekiga. Support for languages other than English, Romanian and Hungarian, German and French is not included on the CD.


  Kiwi uses the same software repositories as Ubuntu with one additional source added for the handful of artwork related or slightly modified packages. Hence it is easy to switch to and from Ubuntu and all the security and bugfix updates from Ubuntu are getting into Kiwi automatically.

---

### Post by alexcckll on 2008-07-20
The other option as well as applying the Restricted Media packs is to add the Medibuntu repositories and yank them down.

---

