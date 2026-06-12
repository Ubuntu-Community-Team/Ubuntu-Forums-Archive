---
title: "Raw beginner"
date: 2023-05-23
forum: New to Ubuntu
---

### Post by mcnaugg2 on 2023-05-23
I am completely new to Ubuntu and don't know where to go next.  Are there any docs that I can download to read offline to grasp the basics of the OS. Having being brought up on windows it is very difficult for me to transfer over.  I have loaded Ubuntu 22 onto my second PC (desktop) and it appears to run OK.  I now want to load some external programs ( a zip program and a model railway control program) but I don't know where to go or start.
My connection to the outside world is via WiFi as they are only just staring to install fibre in my neck of the woods.  We are also subject to daily power cuts(called Load Shedding) which is also problematic.  Any help would be appreciated.

Gareth.

---

### Post by mIk3_08 on 2023-05-23
press ctrl + alt + t in your Linux Ubuntu Desktop then type yelp then press enter. Help window will open. Regards and cheers

---

### Post by Impavidus on 2023-05-23
Windows programs don't run on Linux &#8211; at least, not out of the box. Some programs run on some sort of script interpreter, which may be available on both Windows and Linux, some programs are designed to run on both systems, but need a separate executable for both, and some programs are designed for just one of the two operating systems (usually Windows). Most Windows applications are distributed as a Windows executable, which doesn't work on Linux. There is software called [Wine]("https://help.ubuntu.com/community/Wine"), which is a compatibility layer to run Windows executables on Linux, but it doesn't always work. I've never used Wine myself.

If possible, try to find Linux alternatives for your favourite software. There are plenty of archiving and compression tools for Linux, handling many formats, but maybe not some proprietary formats. Those commonly used on Linux are already installed. A model railway control program may be harder to deal with.

Wifi is to connect your computer to your home router/modem (commonly both functions are combined in one device), fibre is to connect your home router/modem to the outside world. I don't see the issue.

Sudden power failures can seriously mess up your computer, like when they hit while installing updates to vital components of your operating system. An uninterruptible power supply may be nice. Laptops have a battery built-in and are immune to such issues.

---

### Post by nowindows2 on 2023-05-23
I'm not really in a position to offer advice because I'm also a raw beginner, but it might be easier for folks to answer  one or two specific questions i.e., how to load an external program.  Good luck with your journey - for me, it's a bit more difficult than I thought it would be, especially figuring out what does what ( and what it's called) so I can search for answers.  

Hang in there, and good luck!

---

### Post by coley9225 on 2023-05-23
Welcome to linux! Yes, coming from another operating system can be daunting, but if you want to learn it, YOU CAN DO IT!! I began my linux journey about 4 years ago, and yes it was tough. I'm glad I make the leap. Linux isn't for everyone, that's up to the individual. I ran across an excellent learning resource, that I still refer back to often. 

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  is an excellent book to get you started. Download the free pdf and start learning. This book starts at the beggining, and teaches you the basics of a multitude of stuff. I recommend starting at page 1 and proceed through the book, in order, at your own pace. If you need to find more info, google is a great help, as is these forums.

These forums, and others like it, are a tremendous help, not only for us newbies, but experience folks as well.

Again, welcome to linux, my your journey be a pleasant one. Good luck.

---

### Post by zebra2 on 2023-05-23
I use the same open source software on both my Windows 11 and my Ubuntu Installs.  Much of the linux app store won't run on Windows but many of the apps that you need for day to day living work in both.  Most of the Internet browsers, LibreOffice Suite, Claws Email, Moneydance (a premium app), desktop scanner apps. etc can all be used on both ports.  Just get any thing working.  It actually took me a couple of years to convert to Linux 100% but I still have a Windows system that I need  a couple of times a year.

---

### Post by donald187 on 2023-05-24
I found askubuntu.com to be very helpful starting out.  You can do a search on Google such as "<search item> site:askubuntu.com" or be lazy like me and type "<search item> ubuntu" and look for the askubuntu entries.

---

### Post by VMC on 2023-05-24
> **mcnaugg2 said:**
> I am completely new to Ubuntu and don't know where to go next.  Are there any docs that I can download to read offline to grasp the basics of the OS. Having being brought up on windows it is very difficult for me to transfer over.  I have loaded Ubuntu 22 onto my second PC (desktop) and it appears to run OK.  I now want to load some external programs ( a zip program and a model railway control program) but I don't know where to go or start.
My connection to the outside world is via WiFi as they are only just staring to install fibre in my neck of the woods.  We are also subject to daily power cuts(called Load Shedding) which is also problematic.  Any help would be appreciated.

Gareth.

Regarding, model railway control program, will this work:
  [https://traintastic.org/en-us](https://traintastic.org/en-us)

---

### Post by ian-weisser on 2023-05-24
> **mcnaugg2 said:**
> Having being brought up on windows it is very difficult for me to transfer over.

Almost everybody here migrated from Windows, and most remain proficient at both. Your experience is very, very common among us.

---

### Post by TheFu on 2023-05-24
> **coley9225 said:**
> [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  is an excellent book to get you started. Download the free pdf and start learning. This book starts at the beggining, and teaches you the basics of a multitude of stuff. I recommend starting at page 1 and proceed through the book, in order, at your own pace.

Do this.  Don't get caught up with the GUI.  The GUI on Linux is NOT the OS. It is just another program.  There are 20+ different GUIs that we can pick to run ... or even change between at login time, if we like.

Anyway, I used the TLCL book when I taught Linux at the local University to beginners.  With Linux, the order that you learn things matters. Just like a baby can't sprint just after birth, your linux skills need to build over time.  Crawl, stand, wobble, walk-falling, walk, jog, sprint.... trying to learn sprint-level skills when you can't stand yet is a waste of time.  Learn the crawl first.  Follow the book, reading and working the exercises for a chapter each week.  In 12 weeks, you'll be ready to stand and google will be safer.  Right now, google is a danger for you and your system, if you are really new to Unix.

And whatever you do, spend the time to learn Unix permissions for files and directories.  If you don't, you'll spend hours, days, weeks, months, of frustration. It takes 45 minutes to learn the 90% of permissions that you'll need to know.  Spend the time when they are introduced by the book.  Practice until the permissions "click" in your brain and you can predict what will work and won't work - test yourself - prove that you know the subject.  If it takes longer to learn, then it takes longer. Spend the time now.

---

### Post by Quarkrad on 2023-05-28
Some way down your ubntu/linux timeline, once you are reasonably comfortable, you will come across something called Virtual Machine software.  With these you can install other operating systems, like Window 10 or 11, and run then within your ubuntu system.  Many people do this and the performance is amazing - for general use I cannot tell the difference between running win 10 inside ubuntu or as an os on its own.  You can also do a thing called dual booting where you have both windows and ubuntu installed on the same machine.  As said, these are a little way down your time line.  The key thing is, as *ian-weisser* said, most of us here have come from windows and you can have both systems running, so effectively you can have your 'cake and eat it' if you need to have both. (E.g. if there is an absolute necessity to have iTunes because of other devices you may want to have Windows, a lot of people, including myself, just run windows 10 as a virtual machine within ubuntu :P).

---

### Post by ActionParsnip on 2023-05-28
> **VMC said:**
> Regarding, model railway control program, will this work:
  [https://traintastic.org/en-us](https://traintastic.org/en-us)

Yes. There are Ubuntu debs
[https://traintastic.org/en-us/download/ubuntu-22.04](https://traintastic.org/en-us/download/ubuntu-22.04)

---

### Post by mcnaugg2 on 2023-06-09
Thank you for the replies to my posting. I have taken note of the various suggestions and have downloaded the two pdf files(The Linux Command Line and Adventures with the Linux Command Line) and started to read through them.  I have also noted the suggested model train software (Traintastic)and attempted to install it but it failed.  The command I used was "sudo dpka -i traintastic-data_0.2.0~ubuntu all".  It came back to say the the file was not found.  I had copied the traintastic software into the download directory, is that the correct place to download to or install from?
The two programs I need to install are "arduino-ide_2.1.0_Linux_64.Applmage and Rocrail-debian11-i64.zip"  From the comments received zip files can be a problem but the Rocrail program is listed in the Rocrail Linux download directory.  Any additional help would be appreciated.

---

### Post by yancek on 2023-06-09
If you download software to your Downloads directory, you need to  change to that directory to run the command in a terminal.  The command you posted has a typo (maybe?) as it should be dpkg not dpka.  Note that case sensitivity applies and usually there are no spaces in commands.

---

### Post by Holger_Gehrke on 2023-06-09
A small tip: use command line completion. Just type the first few letters and then hit the tabulator key. So for that 'dpkg' command, you'd type 'dpkg -i traint' and hit the tabulator. readline (the library the shell uses for input) will look for a file that begins with the letters you typed and fill it in for you as far as it can; if there are multiple files whose names start the same way, it will fill it in to the point were the names differ; hitting tab twice more at that point will show you the alternatives.

traintastic is made up of three package files: the data (which is what we know you have), a server, and a GUI. I think you need to download and install all three to get something useful. I'd download all three and then switch to the directory with the files (probably 'cd ~/Downloads') and then run 'sudo apt install ./traintastic*'. The advantage is that this should install all three pieces and also download and install any other packages the program might need (libraries, programs it will call as helpers, whatever). Using 'dpkg' can also work but if there are any dependencies dpkg doesn't know how to resolve them while apt does.

The "arduino-ide_2.1.0_Linux_64.Applmage" is quite simply to use. Change it's permissions to allow execution (either with the file manager or with 'chmod u+x arduino-ide_2.1.0_Linux_64.Applmage') and run it. An AppImage is the closest thing on Linux to a 'portable app' on Windows. It contains everything needed to use the program (that's why these things are usually rather big ...).

For the zip file there's an explanation / tutorial in the [rocrail wiki]("https://wiki.rocrail.net/doku.php?id=linux-en").

Holger

---

### Post by TheFu on 2023-06-10
**+100000 for learning command line tab completion.**

You'll never mistype a command or enter a file that doesn't exist.  The completion setup validates that stuff.  It is easy to learn, but hard to explain in writing.  Look for some youtube videos on just **completion**.

Holger_Gehrke explanation is excellent, but since I'd already typed all this in before seeing it ... you get both. ;)

Linux has many different ways that programs can be installed.

[LIST]
[*]**dpkg** probably shouldn't be used by anyone new to Linux.  Use **apt** instead to install packages from the repos or from a PPA. If you download a .deb (debian package) directly, use **apt** to install it and any dependencies.  
[*]AppImage files don't use APT.  They are self-contained programs that don't get installed.  Just download an AppImage, probably to ~/bin/someprogram.AppImage, set the permissions to be executable, and run it.
[*]Snap packages and Flatpaks are also mostly self-contained programs, but snap packages are installed using the Ubuntu Software center or from the command line "snap install".  I don't know much about Flatpaks.  Both snap packages and flatpaks come with a constraint system that's meant to be safer by placing the program into a virtual restricted environment before running the program.  Most of the time, these constraints don't get in the way, but sometimes they do.  Snap constraints cannot be turned off, so if there's a constraint preventing something from working, you are screwed. Flatpaks allow local control to override the default constrains if necessary. That's a good thing. Not all our systems or storage setups are the same.  Main thing is that snaps and flatpaks are not APT packages.  
[*]Download source code, compile it, then install it to the /usr/local/ area on the computer. This is a completely different, non-package, way to get software.
[/LIST]

Packages in the repos or a PPA that you've integrated into your system will be maintained with normal weekly patching processes.

Snap Packages will update themselves without action on your part. By default, updates are check 4x every day, so a bad update could break a program that worked fine before lunch, but in the afternoon, it doesn't.

I think there's a way to have flatpaks updated on demand, but that wasn't initially part of the flatpak system.

AppImages don't update without manually doing it yourself.  I think there are AppImage tools now that perform much of the things that a proper package manager does - installs, updates, removals.  I still manually check and download new versions of the few programs I use that are AppImages.  I check about once a month, which is a bit of a hassle.  Would really like it if they'd just use APT which I have setup to patch all my systems once a week.

Source code installs always require manually checking for updates, recompiling those updates and doing a fresh install.  Each source program team has their own method for building and installing their software. There is usually a README file and an INSTALL file which explains their process.  Some methods like autoconf are more popular, but programmers are all different and different languages tend to use language specific tools for their builds.  Considering there are over 500 different languages and each has 5-50 common, different ways to handle compiling and installing software from that language, you can see why we have to say installing is specific to each project team.  In Unix, nobody should distribute software as a ZIP file.  They should be using tar.gz or tar.Z or tar.bz files, which retain directory structures and permissions, unlike ZIP.

BTW, if you need the most compatible ZIP program, peazip is it.  There are many different ZIP formats and not all of them have support for the current ZIP file capabilities.  PeaZip does.  Unfortunately, PeaZip isn't in the repos, so be prepared to learn how they package it and learn their install.  Add it do the list of programs you need to manually check for updates monthly.

---

