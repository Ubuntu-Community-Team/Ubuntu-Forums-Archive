---
title: "replacement for the tools I used on windows..."
date: 2012-08-16
forum: New to Ubuntu
---

### Post by vikkrraant on 2012-08-16
Hello,
I recently moved from windows to ubuntu. On windows I had some of my favorite tools... which I may miss here.
Can you suggest a best Ubuntu replacement for these tools... I see some of them have there mac version.. but I want to check if there is a ubuntu specific package available (before trying a way to run whatever  i have through wine) 

**ccleaner- [http://www.piriform.com/CCLEANER](http://www.piriform.com/CCLEANER)**
Cleans ur system... cleans well.. temp files, trash, cookies, and other temp stuff.

**zoomit - [http://technet.microsoft.com/en-us/sysinternals/bb897434.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897434.aspx)**
supertool for taking screenshot... and simply much more

[B]winmerge
itunes
google earth[/B]


Also looking for some OS provided replacment...
1[B].> Windows OS Taske MAanger (ctrl+shift+esc)
2.> Windows Event Log 
3.> Windows Services (run menu --> services.msc)[/B]

Also it will be helpful if I u can suggest some more tools which are ur favourite.

---

### Post by ubudog on 2012-08-16
Hi, welcome to the forums and to Ubuntu!

**ccleaner** - Not really needed on Ubuntu, but there is [Ubuntu Tweak]("http://ubuntu-tweak.com/") that has a janitor function that cleans up unused packages, etc.

**zoomit** - There's lots of alternatives to this, including the default screenshot program in Ubuntu.  Search for "screenshot" in the Ubuntu Software Center.

**winmerge** - [Meld]("http://meldmerge.org/") seems like a good alternative for this, and it's in the repositories.
```
sudo apt-get install meld
```

**iTunes** - This is very difficult to get running Ubuntu, but there are lots of music managers that could be possible alternatives.  See [this]("http://www.psychocats.net/ubuntu/itunes/").

**Google Earth** - Google offers a Linux version of Google Earth [here]("http://www.google.com/earth/download/ge/agree.html").  If you're running 64-bit Ubuntu, select the 64-bit .deb file, and for 32-bit, the 32-bit .deb file.  Once it's downloaded, double click on it to install.

**Task Manager** - Check out the System Monitor, which comes by default with Ubuntu.  Search for it in the Dash (Ubuntu button in the top left corner of the screen).

**Event Log** - Search for "Log File Viewer" in the Dash.

**Services** - This is normally managed with the command-line, and is hardly needed for day-to-day use.

Hope that helps, if you have any questions feel free to reply!
- ubudog

---

### Post by unevenflow on 2012-08-16
Hey,

ccleaner-->**bleachbit **
zoomit-->**Shutter**
winmerge-->**Meld**
itunes-->**Rhythmbox** or itunes win version installed through **wine**
google earth--> follow this guide: 
[http://ubuntuguide.net/install-google-earth-and-fix-ugly-fonts-in-ubuntu-11-04-natty](http://ubuntuguide.net/install-google-earth-and-fix-ugly-fonts-in-ubuntu-11-04-natty)
Windows OS Task Manager-->**system monitor** is already installed 
Windows Event Log--> search here **/var/log** 
Windows Services-->**system settings** is already installed, **gconf-editor** **dconf-tools** for more advanced stuff you should do some reading about linux
everything is available from software center

---

### Post by oldfred on 2012-08-16
Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

If you have some applications that you cannot live without you may need to dual boot. I converted to Ubuntu 6 years ago and said for years I would stop using XP, but it was only this year with my new SSD and some configurations settings that I needed for SSD that made me finally stop using XP.

There is no equivalent for itunes & Apple does not offer a Linux version. I am able to copy my photos from the iphone to my Ubuntu but that is about it.

Ubuntu has a screenshot as a tool but it does not do more. 

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

You install software differently in Ubuntu also:
Installing software
[http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre](http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)


Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

Best Free Software for Linux
[http://www.techsupportalert.com/content/best-free-software-linux.htm](http://www.techsupportalert.com/content/best-free-software-linux.htm)

A few Windows applications run or partially run in wine. But do not rely on that without reviewing to see how well it works. I run Picasa's Windows version in wine without any issues. 
The Linux versions of Firefox & Thunderbird use the same profile as Windows and you can share the profiles.

---

### Post by Darkhaund on 2012-08-16
I just had a HORRIBLE personal experiene with UBUNTU TWEAK&#346; janitor

I cleaned everything and after i dida reboot i lost all my desktop unity environment....

Unless you get detailed info on how to use that tool dont

---

### Post by vikkrraant on 2012-08-16
oldfred,
Thanks for inputs and links... I will go through them.
I understand that somehow I am still in windows mode... and sooner I comeout of this is better. I will start reading more.
unevenflow,ubudog,
Thanks for inputs.. 

In general... I have an understanding that using terminal I can do most of the stuff (related with system mgmt) faster and in more efficient way. But it has its own learning curve. I think I should start using terminal more and make myself less dependent on GUI. 
Do you agree on this approach

---

### Post by vikkrraant on 2012-08-16
sure I will keep this in mind... thanks for input

---

### Post by ubudog on 2012-08-16
> **vikkrraant said:**
> 
In general... I have an understanding that using terminal I can do most of the stuff (related with system mgmt) faster and in more efficient way. But it has its own learning curve. I think I should start using terminal more and make myself less dependent on GUI. 
Do you agree on this approach

A good place to start is [here]("https://help.ubuntu.com/community/UsingTheTerminal/").  Should get you through all the basics of navigating, running commands as root, etc.

---

### Post by oldfred on 2012-08-16
Good link from ubudog.

I am accused of giving too much info, so some more links with too much:
A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

I still copy & paste most terminal commands. I did find some sets of commands that I run that I can just copy into a bash file and then run the bash file. That was how I got started on using bash files.

---

