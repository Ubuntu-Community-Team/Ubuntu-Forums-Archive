---
title: "HOWTO: Silkroad Online in Ubuntu 6.06"
date: 2007-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Ben Sprinkle on 2007-02-26
HOWTO: Silkroad Online in Ubuntu 6.06

Right, let's start off. By the end of this HOWTO, you will be able to fully run your Silkroad Online.

**Step 1: Import the Wine trusted APT keys.**
Open a terminal and type (or copy and paste) this.
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

**Step 2: Add the repository to your system's list of APT sources.**
Open a terminal and type (or copy and paste) this.
For Ubuntu 6.10:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

```

For Ubuntu 6.06:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list -O /etc/apt/sources.list.d/winehq.list

```

**Step 3: Install Wine.**
Now you can do this 2 ways, 1 being you open Synaptic and searching Wine there. Or 2, you open a terminal and type this.
```

sudo apt-get update
sudo apt-get install wine

```
Boom, Wine is now installed.

**Step 4: Download and install Silkroad Online.**
If you try to get to [http://www.silkroadonline.net](http://www.silkroadonline.net) it will not let you. The easiest way is to install the User Agent Switcher addon for Firefox.
Go here: [http://addons.mozilla.org/firefox/59/](http://addons.mozilla.org/firefox/59/)

After it is installed, restart Firefox. Then click Tools > Agent Switcher > Internet Explorer (WindowsXP)[Or something along the lines of that]
Then go here: [http://www.silkroadonline.net](http://www.silkroadonline.net) and click download. You may have to download the manual patch if the normal patching does not work correctly.

**Step 5: Install Silkroad Online**
Now before we do this step let me tell you this. I preinstalled Silkroad on my Windows XP machine and ran it from a FAT32 drive I had. I have not installed on Ubuntu so I am in the dark on that one.
Before we install, open a terminal and type this.
```

sudo winecfg

```
Enable pixel shading and select default operating system to Windows XP. If when you run Silkroad it crashes, put the OS to Windows 98. I believe I have mine on 98.
After the installer is downloaded, right click the .exe and click run with (or open with). Find the spot is for a command and type this in that spot.
```

sudo wine

```
It should install in $USER/.wine somewhere.

**Step 6: Running Silkroad Online**
Type this in a terminal.
```

sudo wine /path/to/silkroad.exe

```
Of course you replace the path with the correct one to your silkroad.exe.
When I ran it, it didn't show the title screen correctly, but I guess there will be problems.

---

I have gotten as far as logging in because I have a very slow computer and it lags me too much. Also remember I preinstalled on Windows XP.
Please post your feedback as it is appreciated. =)

Credits:
Me for writing this HOWTO.
WineHQ for the commands and information.
Mozilla.org for the link to User Agent Switcher

---

I do support this thread. Also noted I used a 32bit 6.06 Ubuntu on this.

---

### Post by k420 on 2007-02-28
Hey so i have installed the game just fine but i am getting the server updating error. I looked on there forum and the said turn off your firewall and they give directions but it is for windows any idea what to do?

---

### Post by Ben Sprinkle on 2007-03-01
Try running it in root, or just apply the manual patch. You can download the patch from their site, to run in root:
```

sudo wine /path/to/silkroad.exe

```
Try preinstalling in Windows like I did. =)

---

### Post by powersnork on 2007-03-21
Hey all!
Can I use Wine to play SO in Ubuntu "6.10" ?

---

### Post by MST3Kakalina on 2007-04-06
Running a patched SO in wine even as su still gets me that same error about connecting to the server.  I'm on Kubuntu Dapper.  Anyone have any suggestions?

---

### Post by Vicfred on 2007-04-07
ncie guide I luv this game

---

### Post by xhuan on 2007-04-10
ermmm

i haf a problem here...
mi internet its ok  but always said that the server its underground...
any1 know about this?

thx

---

### Post by Toxicity999 on 2007-04-10
Uhm right, don't run wine as root, unless you enjoy windows tack on bugs festering in your / (It can be possible)

[http://appdb.winehq.net](http://appdb.winehq.net) is a better place to ask questions since there will be more experience there =]

and yes this is Version independent (Ubuntu itself anyway, wine, generally use the latest version) Anything that can support wine, can run what wine supports.

---

### Post by xhuan on 2007-04-10
thx...  the problem its between wine and the internet conection for silkroad.exe

---

### Post by Verbious on 2007-04-15
I had some problems with my windows install, so I decided to come back to Ubuntu.  I used it for about a year for school work and was very happy with it, except for games.  I don't game as much as I used to, but my kids turned me on to SRO.  

I just ripped Ubuntu 6.06 and installed Wine per the instructions above.  I was able to get the log in screen, but it was extremely slow and choppy.  I am going to try to install DirectX in Wine and update my video drivers to the latest and greatest Nvidia.

I will let you know what happens.

Thanks for the guide!  You :guitar:

---

### Post by Verbious on 2007-04-15
After installing the latest nvidia drivers, the game starts with the same speed as it does in Windows.  Servers are crowded as all hell, so i cant log in to test game play.

My son got in with one of his characters and said that it is running ok.  I will check it out myself in about 20 minutes.  Getting ready for a party.   

SRO works with Ubuntu 6.06 and Wine.

I was not able to install directx in wine, so I will have to research how to do it.  The installer failed.

---

### Post by pingpongboss on 2007-04-17
you guys might be interested in this thread which is posted under [www.silkroadforums.com](www.silkroadforums.com)

[http://www.silkroadforums.com/viewtopic.php?t=36267](http://www.silkroadforums.com/viewtopic.php?t=36267)

there's something about adding the joymax IP address into wine somewhere

---

### Post by kazuya on 2007-06-26
Thanks for this Guide. I shall Be experimenting with Crossover office as well to see if I get luckier.

---

### Post by Arjent on 2007-08-05
I didn't get it to work, but here is how they say to alter your host settings. I tried it in wine, but had no luck

[http://news.mmosite.com/content/2006-09-19/20060919000732714.shtml](http://news.mmosite.com/content/2006-09-19/20060919000732714.shtml)

---

