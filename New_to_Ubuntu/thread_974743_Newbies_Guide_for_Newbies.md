---
title: "Newbies Guide for Newbies"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by AmbiguousOutlier on 2008-11-07
Hello, I'm a newbie and now I've been using Ubuntu for about 6 weeks, I've finally got it to the point where I'm happy with it. However I could have got there a lot quicker if I didn't have to use google and these forums so much. So I thought I'd create a “Newbies guide for Newbies”. Basically what I have learnt so far explained in newbie words. Intended for those who've only installed Ubuntu 10 minutes ago and still using Windows to get on the net or those who haven't even got that far.

I thought I'd begin with a bit of background, what I learnt before I installed Linux to decide whether it was right for me. First off Linux is based around a philosophy of sharing knowledge and this is the way the world of computing worked pre 1980's, before the corporate world we know today started to take form. Ubuntu is a project that aims to promote and continue this philosophy for many years to come. Although we may think of Linux as being a free operating system because people in the own time help in making software and putting these distributions together, which largely is the case. In actual fact this guy Mark Shuttleworth who is the man behind Ubuntu has actually invested $10 million dollars and has a team of fully paid developers to ensure the project continues. 

Ubuntu is based upon a Linux distro called Debian which came about 1993, The leading developers behind these distros as such have similar goals and therefore when you reading pages about Ubuntu you may frequently see references to Debian. Ubuntu though tries to bring Linux to the masses, and aims to overcome to misconceptions that Linux is for geeks and developers. In my own opinion there is a learning curve but once you've been playing with it for a few days you will feel perfectly at home. 

What actually is Linux? Well in the mid 70's a Finnish man named Linus Torvalds whilst at university in Helsinki wanted to access the universities powerful (at the time) Unix servers, from home during the cold winter months. He decided upon Minix over DOS as this was based on Unix and would run on his home computer. Anyway Linus eventually developed Linux from Minix, which is merely some programs that allows your computers hardware to communicate with each other, so Linux is actually the kernel program, which on it's own would allow your PC to boot up and provide a blank screen. Software is then run on top of this, this software originally comes from the GNU organisation. So many people refer to what is commonly known as Linux as GNU/Linux. 

Richard Stallman who studied in at MIT in during the 70's at the very popular Artificial Intelligence Lab. When ideas and programs were shared freely however this changed in the 80's where people decided software should be proprietary (Microsoft was at the forefront of this movement), where code wasn't shared and secrets and contracts were created. Stallman left MIT and started the GNU project in 1984. 

With the history lesson over, I guess it's time to install Ubuntu. I'm assuming that as you're interested in GNU/Linux then you've probably already typed “Download Ubuntu” into google, then downloaded the relevant version (64 for AMD or i386 or Intel) burnt two copies to disk given one to a mate and put the other in your CD drive. Then rebooted your computer and followed the very simple on screen instructions. Just in case you haven't I'd recommend you keep your installation of Windows and create a second partition, Ubuntu should only take as much space as it needs. And follows the default installation steps. 

Please keep in mind I am a newbie and although I have installed Ubuntu five times and Kubuntu once they all worked seamlessly and a lot quicker then Vista did. So if you do have any initial installation issues I probably wont be able to answer them.

Once logged into Ubuntu for the first time I'd suggest you have a look around, you wont be able to break anything as you will be required to enter a password before you can make any fundamental changes to the system. Things will be very different to Windows users, almost upside down. To users with experience on a Mac then you should see some similarities after all both OS X and Ubuntu and developed from Unix. 

First things first I had issues with my Wireless networking and also my graphics card. So I suggest you install this application as your first task. We'll take the long way round to begin with. You can use the Terminal window, which is located in the Applications Menu then the Accessories submenu. More on this later, as I got very lost to begin with even though I thought I was quite good in dos.

Click System > Adminstration > Synaptic Package Manager. 

Most apps within the Admin submenu of the System menu will require you to input your password as these programs will make changes to the system, which potentially could damage your computer. Within the Synaptic Package Manager click the search button and type

```

gnome-device-manager

```

Click the first entry and select “Mark for installation” Occasionally when installing apps this way you'll be asked to accept that this app requires other apps to be installed. Then click “Apply” on the toolbar. If you're not online with your wifi then Ubuntu will work out of the box with the wired LAN connection.

After installation Device Manager can now be found within the Applications menu and System Tools submenu. This device manager is different from that what you'd be used to in Windows and provides not as much information but on a lot more components of you machine. Also unlike Windows will list hardware even if it is not yet configured to work. 

Out of the box Ubuntu did not get online wirelessly for bothof my laptops, it may have done for you, if so ignore the next bit. Ndiswrapper is an application you can install which uses your windows drivers. However I attempted this once and it didn't work, although if I had of persisted I'm sure I would have succeeded. I used madwifi which worked almost immediately, the guide I followed was;

```

http://ubuntuforums.org/showthread.php?t=816780&highlight=madwifi

```

In the terminal I did need to run before I followed the thread above;

```

sudo aptitude update

sudo aptitude install

```

You probably wont, but just in case. (And I'm still not sure exactly what they do, don't worry they wont hurt your computer). If your wifi still does not work then use the device manager you installed earlier to find the make and type of the card you have type this into Google with Ubuntu at the end. 

Next thing I did was some power saving configuration, essential in the green world we live in. Different computers have different power saving capabilities, whatever yours are they will be located in the System menu then the Preferences submenu. Select an app called power management. Change these settings to suit your own needs.

Next if I'm not using my hard disk then I like it spin down this saves on power consumption considerably over time, especially as a lot of my computer use is for internet and email. Which doesn't really require the hard drives to be available. If you want to do the same open up the terminal window and type (by the way you can just highlight and middle mouse click (the scroll wheel) or click the left and right mouse buttons simultaneously with focus on the Terminal window);

```

gksu gedit /etc/hdparm.conf

```

This will open up a file in gedit (Ubuntu's advanced text editor) click find on the toolbar and search for “spindown_time”. I have mine set to;

```

spindown_time = 24

```

Which is two minutes, for each 1 is equal to 5 seconds. Although above 240 it starts incrementing in 30 minutes, however don't worry about that. Just set it to 24. In the long run you'll save energy and your hard disk wont get as hot especially useful on a laptop. Save the file, then a reboot will be necessary.

The next important thing is graphics, my integrated Intel graphics card worked no problem out of the box however my Radeon ATI card did not. To get this working I selected Hardware Drivers from the System Menu and the Administration submenu. Remember Admin stuff requires a password. When you click the enable box next to your graphics card, then another box pops up asking you to install new software. Click apply. 

Close out of all of these boxes and then restart your computer. If this produces anything unexpected then you can disable via the same method and use Device Manager again to find the type of Graphics card you have and again Google using Ubuntu at the end of the search string. 

Although Ubuntu is secure. I am paranoid. So I installed a firewall, Firestarter is the one I chose. In the Synaptic Package Manager in the Administration menu, search for firestarter and Install. Once completed go back into the System menu and Administration submenu then Firestarter. You'll be provided with a Wizard where most of the default settings will be sufficient for the average user. 

On the first screen detected devices, eth0 refers to your LAN connection and wlan0 refers to your wifi connection choose whichever is appropriate. Assuming you have broadband put a check in the “IP address is  assigned via DHCP”. Then click forward a couple of times and Save.

Like any other firewalls you can set specific rules for inbound connections like Azureus or any other Bit torrent client for example.

If you've installed firestarter then you are probably as paranoid as me and will want an anti virus program. These are useful, as many Linux users still want to transfer files between Windows computers and it is prudent to check for Windows viruses. Now because Linux does not have security holes that are currently been exploited by any viruses, where as I believe a couple thousand are found every week on Windows. We'll be installing CalmAV which only detects and does not disinfect viruses. But at least you'll know not to transfer that file to a Windows machine. Please keep in mind although 90% of the world use windows, if Ubuntu grows in popularity (which is the goals of Ubuntu) virus programmers will soon turn there attention to Linux. (More people switch to Linux and OS X then switching to Windows).

Open up the Synaptic Package Manager, and search for calmtk (this is gui for CalmAV). Mark it for installation, in the same as we've done before and install. You'll need to be open to calmtk and update the database. To do this open up the Terminal and copy the following;

```

gsku calmtk

```

You'll need to enter your password as your running with Administration rights. Click help and Update signatures. It may be reported as already up to date on first use as during the installation it will automatically update the database. However it is advisable to update before each manual scan. You can also update the database by purely entering;

```

sudo freshcalm

```

Click Applications > System Tools > Virus Scanner to start CalmAV. For the first time select Options then Scan hidden files. Then Click File > Recursive Scan, navigate to your /home directory. CalmAV is not designed to scan your entire disk but more so for documents and files. Quarantine any files that show up as a virus in the programs window. Then Google the name of the virus and decide what to do from there.

Now we have the system working and fully protected, we want to start having a bit of fun. Click System > Preferences > Appearance, Choose a theme and customise to your hearts content. For the background, I found that typing your resolution into Google Images provides a good selection of backgrounds for instance; “1440x900”. You can also change system fonts here. On the Visual Effects tab select the Extra radio button. Hopefully if you've installed you graphics card correctly and it's powerful enough, then you be able to select this option, you'll have some cool effects as a result, the popular one being wobbly windows.

[http://www.saunalahti.fi/frog1/wavs/systemsounds.htm](http://www.saunalahti.fi/frog1/wavs/systemsounds.htm)

The above website provides a good selection of system sounds that can be downloaded to your /home directory and changed in System > Preferences > Sound.

Now back to visual effects, I just wanted to get sounds out of the way as the next step will occupy you for the next couple of hours.

Open up the Synaptic Package Manager, and search for copizconfig-settings-manager. Mark and install. Now go to System > Preferences > Advanced Desktop Effects. Alternatively Start up the Terminal and type;

```

ccsm

```

There is an amazing number of effects that can altered, some of which you may have seen on youtube and even lured you into the world of Linux. The ones I like are;

Enhanced Zoom Desktop – As the name suggests enables you to zoom into your desktop
Desktop Cube / Rotate Cube – The very popular cube that spins round and round (Please ensure within the General Options at the very top, Horizontal Virtual Size set to 4 on the Desktop Size tab) Lots and lots of settings with these so spend an hour playing around until you get it just right.
3D Windows – Very cool but sadly my graphics cards just aren't good enough. Produces a very small amount of lag, enough to be an annoyance.
Animations – These are also very good, controls how you windows look when opening and closing. I like the beam up and fire ones.

If you liked your widgets on Vista then you may be interested in the screenlets, I personnally found them as boring as they were on Vista. Go back to the Synaptic Package Manager and search for screenlets. Once installed you can find them under the preferences menu. Play with them if you wish. 

If you not happy with how your mouse and keyboard are operating then you can change these settings in the preferences menu. Just so you know a wireless Logitech mouse and keyboard connected straight away even though the box didn't mention it's compatibility with Linux. 

If you've used OS X and you like the dock at the bottom then you may want to install AWN Avant Window Manager. Within Synaptic Package Manager search for Awn-manager-Trunk. Once installed goto System > Preferences > Awn Manager, In the general options tab ensure “Automatically start AWN on login” check box is enabled. Then Change whichever preferences you like. Once setup you can drag and drop icons from any of the menus onto the dock. These will be placed in the launcher option, where you can also customise the dock. If you can't see the dock then type into the terminal;

```

awn
[/awn]

This was a bit fiddlerly to get working exactly how I wanted it but persistence pays off. Now you probably still have the “taskbar” at the bottom of the screen, I've already removed mine and can't figure out how to get it back but I'm sure I simply right clicked and removed. But a word of warning it may take a little Googling if you want to get it back. 

Hopefully by now you'll have ubuntu working and looking the way you want it. There are some additional features out of the box that may be of interest to you. Openoffice.org is pre installed and is almost identical to Windows Office. However Base which is MS Access equivalent is not installed by default. You also have image editors simailar to Adobe Photoshop called gimp although having not used used photoshop I can not tell you how good it is. Virtually any program you have on Windows can be found in a similar form for Ubuntu. Just type what you're after into Google with Ubuntu after it. We do have an email tool with a fairly decent calendar called Evolution. Now I did try and get my hotmail account to work with evolution but I just couldn't do it. You may have better luck with this;

http://ubuntuforums.org/showthread.php?t=200408&highlight=hotmail+evolution

I ended up setting up a gmail account using this guide;

http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/

And also my google calendar synced quite easily. To do this goto your Google Calendar settings and copy the “ical” option from the www onwards.

Then goto evolution and select Calendar button from the bottom left, File > New > Calendar, change type to “on the web”. In the URL box past the address from google settings after the webcal://. Type  in your username without the @gmail.com / @googlemail.com.

I have a Wii and although this is pointless you can set it up in half an hour with no additional expenditure providing you have a Wii. It is cool to show to your friends.

http://ubuntuforums.org/showthread.php?t=836231&highlight=wiimote

One of the biggest learning curves I experienced with Ubuntu is the file structure. With Linux we no longer have letters for drives. Everything in Linux effectively is treated like a file and will appear within the the Filesystem, when ever a piece of hardware is attached, a web cam, usb drive then a file will be created. Go to Places > Computer. Then click on the Filesystem icon. This will show you all the files and directories on your system. You wont be able to edit most of this data as you will need administrative permissions called root or super user in Linux. Anything you save or download will more then likely be save in your /home directory. Also of interest is your /media directory which contains any external hard drives or CD/DVD drives attached your computer. 

You may have also noticed I'm using forward slash rather then back slash as Windows does. Linux is also case sensitive so when creating a file you can have files with exactly the same name but differing capitals ie File or FILE or file keep this in mind if transferring files to and from Windows.   Windows will invariable break if you try and copy files of the same name. You can also use special characters like \:*”<>?| in your Linux file names which will not work in Windows. Another cool thing you can do is right click a file, select properties then on the Emblems tab you can add icons to each of your files to display easy to see prompts on the type of files you have.

Lastly I'd like to share what I have learnt about the Terminal Window. Like DOS the BASH Shell is Linux version but so much more powerful. Pretty much anything you do in a GUI can be done in BASH. Ubuntu's shell is based on the Unix Bourne shell, BASH means Bourne Again SHell. The Shell is very useful as we can make certain operations with one line of code rather then a whole string a mouse clicks and keyboard inputs. For instance every app we've installed so far can be installed using just a couple lines of Shell commands, which are all largely generic. 

If there is a command you're not sure of then you can use the --help command after the initial command;

[code]
ifconfig --help

```

If you are proficient in DOS then you can create aliases for instance in DOS to copy a file you would use the command COPY in shell you use cp. 

```

alias copy='cp'

```

You can change this if you wish but it probably isn't a good idea. As you should try and learn BASH. This will provide you with a list of commands and their DOS equivalent.

[http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html)

Previously we have used the sudo and gksu commands. As standard we do not have root permissions, so to enable us to run a program with root powers we need to use one of the above commands. Sudo is used most of the time, gksu is used for GUI apps, like opening the Anti Virus GUI or a file in gedit.

I think that's enough for now, I may do follow up guide in another 6 weeks of using Linux. I hope this has been useful to at least one person. And I hope I haven't got anything wrong, please let me know if I have.

Thanks for reading.
Rhys.

---

### Post by pikabuntu on 2008-11-07
> **RhysGM said:**
> 
What actually is Linux? Well in the mid 70's a Finnish man named Linus Torvalds whilst at university in Helsinki wanted to access the universities powerful (at the time) Unix servers, from home during the cold winter months. He decided upon Minix over DOS as this was based on Unix and would run on his home computer. 
It was in the early 90's :P

This guide would have been cool when I first started with ubuntu :)

---

### Post by AmbiguousOutlier on 2008-11-07
No sorry, Linus first conceived the idea of Linux in the 70's but what we know as Linux today with the GNU projects was later fully developed in 1993 as debian.

---

### Post by B34ST1Y on 2008-11-07
sticky?

---

### Post by chrisod on 2008-11-07
Linus was born in 1969. He did not conceive the idea of Linux prior to his 10th birthday.Linus started work on what would become Linux in 1991. The history is all on Wikipedia for anybody interested in it.

---

### Post by ugm6hr on 2008-11-08
> **B34ST1Y said:**
> sticky?

Added to the Start here sticky: [http://ubuntuforums.org/showthread.php?p=6127715#post6127715](http://ubuntuforums.org/showthread.php?p=6127715#post6127715)

Since this is not a help request, thread closed.

---

