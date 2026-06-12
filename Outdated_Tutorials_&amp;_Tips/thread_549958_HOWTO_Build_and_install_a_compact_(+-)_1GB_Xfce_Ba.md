---
title: "HOWTO Build and install a compact (+/-) 1GB Xfce Based Ubuntu Desktop"
date: 2007-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Warren Watts on 2007-09-13
**Purpose**
This document will guide you though the process of installing a basic (+/-) 1GB Ubuntu desktop utilizing the Xfce desktop environment.  

[B]WARNING: THIS HOWTO REQUIRES A FAIR AMOUNT OF ENTERING COMMANDS INTO THE COMMAND LINE.  
UNTIL THE PROCESS IS NEARLY COMPLETE, THERE IS NO GUI. [/B] 

However, that warning aside, you might be surprised how easy it really is to build a working Xfce desktop from a base install using only the command line.  

I will try and outline each step of the process, so that someone with only a basic understanding of the command line can use this HOWTO and install the basic system without too much difficulty.

**Why use the Xfce desktop enviroment and not Gnome?**
Gnome uses considerably more RAM and requires a lot more system resources than Xfce.  

**So why not just install Xubuntu, which uses the Xfce desktop enviroment?**  Why would I want to go through all these manual steps at the command line when I can just pop in an Xubuntu CD and have it all install for me?
Xubuntu installs a large number of packages, applications, and tools that take up extra disk space and use more system resources.  The compact install described in this document only installs the BARE MINIMUM needed to get a useable Xfce desktop up and running.

**Why would I want a compact basic install?**
Such an install is ideal for older Pentium II and III systems with 256MB or less of RAM. Older systems don't generally perform well with a standard Ubuntu installation.

**What you need: Fiesty (7.04) Server Edition ISO**
Download Ubuntu Server Edition and burn the ISO to a disk. Make sure you dowload the **Server Edition**

I chose the Server Edition for this HOWTO because it doesn't install ANY GUI at all, and I wanted to be selective about what GUI components DO get installed.  This keeps the install size compact.

**Install the base system**
Once you have burned the CD, insert the CD and boot from the CD-ROM.
Choose the regular install. Start the installation with the default install.
When you get to the point near the end of the install where it says "S**elect and Install Software**" and you are given the option of installing the DNS Server and/or LAMP Servers, **DON'T select either option**.  All we want is the simple base installation without any extras.

Let the install of the base system complete, install the GRUB bootloader if needed, and reboot the system when prompted.
**REMEMBER TO REMOVE THE CD BEFORE YOU REBOOT!**
The system should reboot, load the base system, and prompt you to log in.  
Use the username and password you created during the base install process.

**Update and Upgrade the base system**
The packages on the CD probably aren't up to date, so we want to make sure we are using the latest releases of all the packages the base system installed.  
We are going to use apt-get's update and upgrade options to update the system.
At the command line, type in:
```
sudo apt-get update
```
This will update the list of currently available packages.

Once that completes, type in:
```
sudo apt-get upgrade
```
This will upgrade any packages installed by the base installer to the latest releases.
Answer Yes to any questions that apt-get may ask about installing packages.

Now we need to install the power management package. The ACPI package provides these functions.
ACPI support is needed if you want to use some special functions on your notebook (e.g. sleep, sleep when lid is closed, special keys...).
Type in:
```
sudo apt-get install acpid
```

The ACPI package will install (again, answer yes to any questions apt-get may ask you about installing packages)

**Installing Xorg, Xfce, and a few basic applications**
We are now ready to install the GUI!  

You will probably want to re-insert your CD at this point.
If you forget, don't worry; apt-get will prompt you to put it in if it needs files that are on the CD.

I have broken the install commands down into three steps; installation of XWindows, installation of the Xfce desktop, and installation of the basic applications that will installed on the system.

The first step is to install Xorg, the Xwindows platform that most Linux GUI's use as a foundation.
To install Xorg, type in the following command:
```
sudo apt-get install xserver-xorg xorg ttf-bitstream-vera x-ttcidfont-conf
```
There are quite a few packages to install, so it will take a few minutes.
(Again, answer yes to any questions apt-get may ask you about installing the packages)
A box will pop up at some point asking you to define the basic resolutions your graphics card is capable of; you can use the defaults for now.

Now we are going to install the Xfce desktop environment.  Type in:
```
sudo apt-get install xfce4 xfce4-appfinder xfce4-artwork xfce4-goodies
```
There are quite a few packages to install, so it will take a few minutes.

Now we are going to install the GDM (the GDM provides the GUI login screen), Ubuntu GDM themes and artwork, and a few basic applications like a terminal, text editor, and the Synaptic Package manager.
Install these by typing in:
```
sudo apt-get install gdm feisty-gdm-themes ubuntu-artwork synaptic gnome-terminal gedit
```
Not quite as many packages to install this time, but it may still take a minute or two.
(again, answer yes to any questions apt-get may ask you about installing the packages)

Now we need to re-configure the xorg.conf file, which is the file that tells the GUI what kind of keyboard, mouse, graphics card and monitor are installed in the system.
To reconfigure the xorg.conf file, type in:
```
sudo dpkg-reconfigure xserver-xorg
```
A series of dialogs will pop up asking you to define the specifics of your hardware.

Now that we have installed all the necessary packages, all that is left to do is make sure they are up to date.
Enter the apt-get upgrade command again to bring all the newly installed packages up to date:
```
sudo apt-get upgrade
```

Now that all of the packages are all up to date, we are ready to reboot into your brand new GUI!

**Reboot into your GUI**
Remove the CD if you put it back in during the install process.  If you don't remeber to take it out, the system will biit from the install CD when you reboot!
Use the shutdown command to shutdown and restart the system.  Type in:
```
sudo shutdown -r now
```
The system will reboot, and you will be presented with the GUI login.
Enter the username and password you created during the base install.

The Xfce desktop will load, and you will be staring at your brand new desktop!  Woo Hoo!

**OK, so now what?  All I see is a few icons and a funny little gray box with a star thingy on it up the corner!?!?**
Now comes the fun part! 
You get to build your desktop just the way you want it, installing only the applications you need.

If you are already familar with Xfce, this shouldn't pose too much of a problem.  Just put the panel where you want it and start adding applications and applets to it.
If you are new to Xfce and are used to Gnome, the last sentence probably didn't make much sense to you.  
Don't fret; I have step-by-step instructions on how to do it.

There are 21 screen shots that go with this portion of the HOWTO, They are attached to this thread as an archived file.  I had to archive them as lossy JPEGS to keep the archive under the forum limit, I apologize..)
The Screen shots are referenced in the text below in **BOLD CAPS**.

**Populating and positioning your Xfce panels**
I am now going to outline the basics of populating and positioning your panels.  
A panel is basically just an area on the edge of your screen where you can place icons.  The icons can be used to open a tool, display system information, provide a menu, or launch an application.

Our basic installation didn't provide any pre-populated panels; we need to populate and place them ourseves.

Here is what you see after a basic install:  Not very pretty, eh?
(Look at the first atachment to this thread)

Ok, let's get to work.
The gray box with the star thingy on it up the left hand corner is our default panel.  
Right click on the panel and choose **Customize Panel**.
**SCREENSHOT 1**

This opens the **Panel Mananger** Dialog.
Choose **Fixed Position**, then click on the gray bar in the center of the bottom of the box.  
This will move our panel to the center at the bottom of the screen.
Click Close.
**SCREENSHOT 2**

Now we are going to add our first icon to the panel.
Right click the panel and choose **Properties**.
**SCREENSHOT 3**

This will open the **Program Launcher** Dialog.
Right click on the desktop (outside of the open Dialog) and choose **Accessories --> Appfinder**
**SCREENSHOT 4**

This will open the** Xfce4 Appfinde**r Dialog.
Position the two open windows so they don't overlap each other.
**SCREENSHOT 5**

Under **Categories**, click on **ALL** and scroll down to the Terminal.
Drag the terminal icon from the **Appfinder** into the gray box with the Name and Description fields in the **Program Launcher** Dialog. The box frame will darken when you are inside the box.  
**SCREENSHOT 6**

Let go of the icon inside the box, and the fields will be populated with the name of the program and the command needed to launch it.
**SCREENSHOT 7**

Click Close in the** Program Launche**r Dialog.
Your panel will now have the Terminal launcher in it!
Now we are going to add another icon to the panel.
Right click on the panel again and choose **Add New Item**.
**SCREENSHOT 8**

The **Add Items to the Panel** Dialog will open.
Don't choose any of the items listed, instead, just click **Add (+)**.
**SCREENSHOT 9**

A new **Program Launcher** Dialog will open.
From the **Xfce4 Appfinder** Dialog, drag the Text Exitor icon into the **gray box on the [B]Program Launcher** Dialog.
SCREENSHOT 10[/B]

Just like before, the **Program Launcher** Dialog will now be populated with the information for launching the Text Exitor.
**SCREENSHOT 11**

Close the **Program Launcher** Dialog.
Now the panel has two launchable programs; the Terminal and the Text Editor.
Now lets add a panel to the TOP of the screen.
Right click on the panel and choose **Customize Panel**.
**SCREENSHOT 12**

The **Panel Mananger** Dialog will open.
Click the **(+)** until "**Panel 2**" apears to the left of the (+).
Scale the size of the panel down to a smaller size (I used 27 pixels in the screen shot), choose a fixed postion at the top center, and set the panel to the full width of the screen.
**SCREENSHOT 13**

The new panel appears at the top of the screen.
Right click the panel and choose **Add Item**.
**SCREENSHOT 14**

The **Add Items to the Panel **Dialog will open.
Choose the clock from the list.
**SCREENSHOT 15**

Click close and a dialog will pop up allowing you to set up your clock to your liking.  Close the clock dialog, and your clock now appears on the top panel!
Right click the top panel again and choose **Add Item**.
**SCREENSHOT 16**

Click on the **Task List** in the **Add Items to the Panel** Dialog and click Close.
**SCREENSHOT 17**

A task list will now appear in the top panel.
Open the Terminal and the Text Exitor, and you will see them displayed in the task list.
**SCREENSHOT 18**

Now that you have a basic understanding of how Xfce panels work, you can move the icons on the panels around to suit your taste, and add any additional applets and launchers you might want.

Now lets add some more applications to the installation.
[B]
Customizing you compact Xfce system[/B]
Adding additional applications is as easy as right clicking on the desktop and choosing **System --> Synaptic Package Manager**, then searching for and installing the applications you want.  
Installed applications will usually be added automatically to the right click desktop menu.
If an installed application doesn't automatically get added to the menu, you can use the Appfinder to search for it.

I installed file-roller (for decompressing archives), Gaim (an instant messenger), Firefox, gFTP (an FTP client), Gnomebaker (a CD/DVD burner), Gimp, VLC (a multimedia player) and Xfce Mixer to the sample install I built for this HOWTO.
**SCREENSHOTS 19 & 20**
[B]
Total size on disk with all the applications listed above: 1.1GB[/B]

If you are interested in building an install like the one in this HOWTO, I hope I have provided enough information to allow you to do so with a minimum of effort.  If you have questions, you can always PM (Private Message) me on the Ubuntu Forum, or feel free to send me an email (You can email using the Forum User Control Panel).

Have fun and good luck!

EDIT: Feel free to comment on what I have written here.  If you see anything that could be simplified, post a reply and I will consider editing this HOWTO.

---

### Post by meborc on 2007-09-15
hmm, looks good.... but i would use mousepad instead of gedit and xfce4-terminal instead of gnome-terminal... better to run xfce apps in xfce... or?

---

### Post by RedSquirrel on 2007-09-15
Nice howto.

A few comments:

For the base system, you can also use the Alternate Install CD ("Install a command-line system") or the [net installer]("https://help.ubuntu.com/community/Installation/MinimalCD"). One advantage of the latter is that you don't have to do the "upgrade" step since you're grabbing all the latest packages.

> **Warren Watts said:**
> The compact install described in this document only installs the BARE MINIMUM needed to get a useable Xfce desktop up and running.

I would consider putting the artwork packages under a separate heading since they are not strictly necessary.

I agree with the above comment about gnome-terminal and gedit. In my opinion, you're better off with xfce4-terminal and mousepad (leafpad is also quite nice). There are of course lots of other terminals: xterm, uxterm (well, it's just a wrapper), urxvt, etc. and for text editors: vim, gvim (package: vim-gtk), scite, etc. xfce4-terminal is a heck of a nice terminal and dead simple to configure.

It's always a good idea to check out the dependencies of things you're going to install. I see you use gnomebaker, so you would have the GNOME libraries installed with that application. For you to install gedit and gnome-terminal would not be an extra penalty. However, not everyone would want those GNOME libraries installed. ;)

I don't think the second 'sudo apt-get upgrade' step is necessary. When you do 'sudo apt-get update', it updates the package list so apt knows what the latest packages are.


EDIT: added a link for the net installer and reworded the second last paragraph to make it a bit clearer (I hope :grin:)

---

### Post by mocoloco on 2007-09-16
Couple of things.  Like RedSquirrel said I know you could use the Alternate CD.  Wouldn't that be better, since doesn't the server edition install a bunch of server-ish stuff that a regular desktop doesn't need?  or am I wrong and the alternate text-only install is the same as the server install?

This may be a separate ball of wax, but what about the opposite, stripping down an existing Xubuntu install, basically a list of packages to be removed.

Also wouldn't this be mostly a disk space thing and not a system performance thing?

---

### Post by Haama on 2007-09-28
Nice howto. It was easy even for a beginner like me to follow.
I'm now going to try to make my own installation without all unwanted apps.
I just have one question. I want to install Gnome instead of Xfce. What packages should I install?

---

### Post by Warren Watts on 2007-10-04
> **Haama said:**
> Nice howto. It was easy even for a beginner like me to follow.
I'm now going to try to make my own installation without all unwanted apps.
I just have one question. I want to install Gnome instead of Xfce. What packages should I install?

Glad you found it helpful!  
As far as doing the same thing with Gnome, I don't really know.  I developed the Xfce HOW-TO mainly by experimenting.  Basically, I used the Synaptic Package Manager to search for Xfce packages and them installed them one at a time to see what happened and what I was still missing.
Using the same approach for a Gnome install might prove more difficult because Gnome has a ***LOT*** more support packages than Xfce.

---

### Post by RedSquirrel on 2007-10-04
> **mocoloco said:**
> Couple of things.  Like RedSquirrel said I know you could use the Alternate CD.  Wouldn't that be better, since doesn't the server edition install a bunch of server-ish stuff that a regular desktop doesn't need?  or am I wrong and the alternate text-only install is the same as the server install?

If you use the Server Edition CD, I think you'll end up with the server kernel. One can install the generic kernel afterwards by installing one of **linux-generic** or **linux-image-generic**. The former also pulls in the restricted modules. I don't need those so I just install linux-image-generic if I want the generic kernel on a server installation. I think for most people the alternate CD or the net installer might be better because they'll get the generic kernel by default.


> **mocoloco said:**
>  This may be a separate ball of wax, but what about the opposite, stripping down an existing Xubuntu install, basically a list of packages to be removed.

Sure, you could do that. I personally find it easier to start from a minimal system and add the things I want.

> **mocoloco said:**
> Also wouldn't this be mostly a disk space thing and not a system performance thing?

Generally speaking, yes, but again, when you've only installed the base system, you can be sure you're not running too much extra stuff. With the "stripping down" method, you have to do a fair bit of hunting around.

---

### Post by RedSquirrel on 2007-10-04
> **Haama said:**
> I'm now going to try to make my own installation without all unwanted apps.
I just have one question. I want to install Gnome instead of Xfce. What packages should I install?

I would have a look at the package **gnome-core**. Here is its description:

> [COLOR=DimGray]These are the core components of the GNOME Desktop environment, a graphical
interface to use on your Debian system. It includes a basic set of
programs, including a file manager, image viewer, text editor, sound
recorder and other useful tools.[/COLOR]

---

### Post by Scott-271 on 2007-11-12
I want to try this.

I just installed Xubuntu, but would love the stripped down version; I have the alternate *Xubuntu* cd, would that work for this, or would I still need to get the *Ubuntu* alternate cd?

Also, if/when I get this finished, is there a way for me to copy what I did, and be able to install it on another computer?

Thanks in advance,
Scott

---

### Post by Scott-271 on 2007-11-15
Ok, I'm just finishing up tweaking my new install.

I went with the *Ubuntu* alternate cd, with cli. I did try using my Xubuntu cd I had laying around, but it didn't go too well. The Ubuntu one worked like a charm. I followed the directions above, although substituting/using mostly xfce apps.

I prefer this much better than my fresh install of Xubuntu 7.10, it doesn't seem as bloated. Now, I just need to get use to doing things the Ubuntu way. :o

---

### Post by mocoloco on 2007-11-17
> **Scott-271 said:**
> 
...I have the alternate *Xubuntu* cd, would that work for this, or would I still need to get the *Ubuntu* alternate cd?

I see you already got it installed Scott, just FYI to posterity: installing a command-line only system ends up identical whether you use the Ubuntu, Xubuntu, or Kubuntu alternate CDs.

---

### Post by Scott-271 on 2007-11-17
I figured as much, but when I tried to use my Xubuntu disc, I had problem with the command-line. The text install went fine with that disc, just not the cli; now I have both Ubuntu and Xubuntu discs. :)

I'm going to give it another shot on an old laptop I just got from eBay, see how that goes. Now that I've done it and gotten pretty famaliar with the apps/programs, I'll try for a even leaner version.

---

