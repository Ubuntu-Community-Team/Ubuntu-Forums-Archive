---
title: "[SOLVED] .tar.gz files?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by dmurat on 2008-09-03
hi
i have been using ubuntu for 1-2 hours now so am a noob. anyway, i downloaded flash player to launch flash videos and games etc on the net. however, the file i downloaded is named as install_flash_player_9_linux.tar.gz

however, i have no idea how the .tar.gz file should be treated...what can i do now to get the flash player?

thanks

---

### Post by perlluver on 2008-09-03
Open up System>Administration>Synaptic Package Manager, and install flashplugin-nonfree.

And if you want MP3 support, and Java, just open up Applications>Accessories>Terminal, and type in ```
sudo apt-get install ubuntu-restricted-extras
``` or you can do it through synaptic by searching for ubuntu-restricted-extras.

---

### Post by bubba_169 on 2008-09-03
If I remember right flash uses its own install script. So, what you need to do is extract the tar.gz by right clicking on it and selecting extract. Navigate to the new folder where the files extracted to and there should be a file called something like install_flash_player.sh. Double click this and from the dialog that appears choose run in terminal.

That should do the trick!

---

### Post by tuxxy on 2008-09-03
> **dmurat said:**
> hi
i have been using ubuntu for 1-2 hours now so am a noob. anyway, i downloaded flash player to launch flash videos and games etc on the net. however, the file i downloaded is named as install_flash_player_9_linux.tar.gz

however, i have no idea how the .tar.gz file should be treated...what can i do now to get the flash player?

thanks

Hi,

To install Flash in Ubuntu you do not need to download from the web, Flash is included in the ubuntu-restrcited-extras package, this is in the repos.

Open a terminal and type

```
sudo apt-get install ubuntu-restrcited-extras
```

To install the Flash plugin for your broswer type this

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Sinkingships7 on 2008-09-03
.tar.gz is just a compression format, similar to .zip or .rar. There's nothing particularly special about it, other than the fact that it's used mostly on Linux. That should answer your initial question, and the posts above will get you flash.

Welcome to the community. :)

---

### Post by whitethorn on 2008-09-03
Hi and welcome, probably the biggest difference between Windows and Ubuntu is that most of the programs you want are found in System -> Administration -> Synaptic package manager.  You don't really have to search the internet for packages and install them like under windows.  Go into synaptic do a search for what you want and then let it install the program.  You'll find almost everything you need in there.  If you some specific software you then you might have to install it urself on your system.  That's usually when you you have .tar.gz file. You first need to unpack it, I usually just right click on it and choose extract.  Then you should probably read the README file in the folder.  It should give you the instructions on how to install it.  Before you can do that you first need the 

```
sudo apt-get install build-essential
```

just copy that into a terminal windows (apt-get is a program that does the same as Synaptic package manager just from the terminal, if you know the name of the program you can get it installed from the terminal saves a bit of time).  Then just follow the instructions in the README.  Usually it's better to search Synaptic for the program you want and let Synaptic install it for you.

---

### Post by dmurat on 2008-09-03
thank you all you helped a lot...all essentials being already installed in the system is great! :D
one more question, is there any alternative application for Itunes for accessing my ipod and an alternative application for Microsoft Visual Studio, for compiling and executing C++ codes?

---

### Post by Sinkingships7 on 2008-09-03
> **dmurat said:**
> thank you all you helped a lot...all essentials being already installed in the system is great! :D
one more question, is there any alternative application for Itunes for accessing my ipod and an alternative application for Microsoft Visual Studio, for compiling and executing C++ codes?

Amarok is a highly regarded iTunes replacement, but I much prefer [Songbird]("http://getsongbird.com/").

For compiling and executing C++ code, you'll want to be using G++. First,
```
sudo aptitude install build-essential
```
Then you'll want an IDE. I suggest Geany, which you can get with this code:
```
sudo aptitude install geany
```
If you want a more 'full-featured' (I call it bloated :p) IDE, you can try Eclipse, Anjuta, or NetBeans, but Geany should be just fine for your needs.

An important thing to remember is that Linux is not Windows, and as such, does not inherit any of Windows non-standard libraries, like conio.h. In any case, it's always best to write standardized code. So if you were ever in the habit of using Microsoft's libraries, please seek alternatives.

If you wish to program and compile for Windows using Windows headers, then you may do so by installing [Dev-C++]("http://www.bloodshed.net/dev/devcpp.html") via WINE. On the download page, be sure to choose the first selection, with MinGW/GCC.

---

### Post by dmurat on 2008-09-04
thanks but i guess there is a problem with my terminal
whatever code i type and press enter, it says

```
dmurat@mrt:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for dmurat: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

and when i try to run dpkg --configure -a it tells me that it is required super user rights to do run that?

a similar error message comes up when i try to open synaptic package..

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


how do i fix this any idea?

---

### Post by t0p on 2008-09-04
You need to type

```
sudo dpkg --configure -a
```

I don't know why that message doesn't say to use sudo.  Lots of people have this problem when they first encounter this message.

---

### Post by jemate18 on 2008-09-04
> **dmurat said:**
> hi
i have been using ubuntu for 1-2 hours now so am a noob. anyway, i downloaded flash player to launch flash videos and games etc on the net. however, the file i downloaded is named as install_flash_player_9_linux.tar.gz

however, i have no idea how the .tar.gz file should be treated...what can i do now to get the flash player?

thanks

Check my post here ... There is an instruction on how to install flash player 9. It works for me
> [http://ubuntuforums.org/showthread.php?t=905806](http://ubuntuforums.org/showthread.php?t=905806)
It really works

---

### Post by dmurat on 2008-09-04
ok thanks..now i can access the terminal and package thing but one more problem :\

while i was installing ubuntu-restricted-extras and flashplugin-nonfree i had to shut down my computer so these applications are half-installed. when i try to install again (sudo apt-get install ....) it gives an error like 
"try to use apt-get -f install to correct the errors below: 
sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1)  but won't be installed
E: Unmatched dependencies"

so, i tried to uninstall the half-installed packages and reinstall but it doesnt let me uninstall too :\

what can i do now? 

*i am translating all the error messages from my own language to english so i hope they make sense =)

---

### Post by Bucky Ball on 2008-09-04
Copy/paste in terminal a line at a time, not all at once:

```
cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz")
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```If that doesn't work, replace second line with:

**wget -c [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz)**

and third line with:

[B]tar -xvzf flashplayer10_install_linux_081108.tar.gz

[/B]:)

---

### Post by dmurat on 2008-09-04
> **dmurat said:**
> ok thanks..now i can access the terminal and package thing but one more problem :\

while i was installing ubuntu-restricted-extras and flashplugin-nonfree i had to shut down my computer so these applications are half-installed. when i try to install again (sudo apt-get install ....) it gives an error like 
"try to use apt-get -f install to correct the errors below: 
sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1)  but won't be installed
E: Unmatched dependencies"

so, i tried to uninstall the half-installed packages and reinstall but it doesnt let me uninstall too :\

what can i do now? 

*i am translating all the error messages from my own language to english so i hope they make sense =)

the thing is i still have the problem mentioned in the quote. so i cant install flash before fixing this thing

---

### Post by Bucky Ball on 2008-09-04
Have you done a clean install of 8.04 recently from Dapper 6.06? Or perhaps an upgrade from within Dapper? Or are you in fact using Dapper, not Hardy, the latest stable release? Please let us know which version of Ubuntu you are running as I can't seem to find that detail anywhere.

---

### Post by dmurat on 2008-09-04
i dont know what is dapper?

---

### Post by Bucky Ball on 2008-09-04
Do you know what version of Ubuntu you are using? The latest is Hardy Heron 8.04. Dapper Drake 6.06 is an old version. :)

```
sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1)  but won't be installed
```Notice the (=6.06 ?

Or is that 6**-**6 ?

---

### Post by dmurat on 2008-09-04
:D  yea, i use the latest version 8 0 4 not dapper =))

---

### Post by Bucky Ball on 2008-09-04
Well, just install ubuntu-restricted-extras again and in terminal type:
[B]
sudo apt-get remove flashplugin-nonfree[/B]

then run the instructions for flash 10 I posted earlier. :)

---

### Post by dmurat on 2008-09-04
the problem is, i cant install ubuntu-restricted-extras again since i quit at the middle of installation process. i want to remove but cant do that also...i face the errors written above ^^

***edit: i dont know how but i achieved to continue the installation from where i left :D but now there is a license agreement and an ok button at the end but i cant click it. its not a button, its in text written "ok" what do i do?
***edit2: thanks all! i finally managed to install ubuntu-restricted-extras AND flashplugin-nonfree thanks again for the help

SOLVED! :D

---

### Post by Bucky Ball on 2008-09-04
Great news! You can mark the thread as solved by going to 'Thread Tools' at the top of the page and clicking 'Mark thread as solved'. Good luck and welcome. :)

---

### Post by dmurat on 2008-09-04
just did it ^^ thanks! :D

---

