---
title: "Installing a given ktorrent version"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by belier on 2008-10-18
Hi.

i need to install ktorrent 3.1.0. Via synaptics and Add/Remove programs I only get another version.
I've downloaded it in gz2 file. 
What do I have to do now?

(Totally noob here)

Thanks in advance

---

### Post by burnetbj on 2008-10-18
Hi there 

I am also very amateur in linux, but i think what you are trying to do is. Browse to the location you downloaded the app to on your hard drive in terminal in Gnome and Konsole in KDE the type in the name of the download with a ./ in front of it this will trigger it to execute

---

### Post by belier on 2008-10-18
Thx for the answer.

That didn't work... :(

---

### Post by burnetbj on 2008-10-18
Hey 

Im back had to go out for a bit. Did you actually have both the period and forward slash ?

./  and then file name ?

If you have internet just got to Adobe and they have a tutorial on how to install software from them. This is the same concept for all software programmed for linux and bundeled in a zip format 

If anything hope this helps move the thread up so someone with experience can help you :)

---

### Post by sethvath on 2008-10-18
[http://ubuntuforums.org/showthread.php?t=42902](http://ubuntuforums.org/showthread.php?t=42902)

---

### Post by belier on 2008-10-19
> **sethvath said:**
> [http://ubuntuforums.org/showthread.php?t=42902](http://ubuntuforums.org/showthread.php?t=42902)

Thx a lot for the answer. I've used the advanced search but it makes "or's" instead of "and's" and it gives me tons of results. I'm unable to refine the search.

---

### Post by sethvath on 2008-10-19
Do you still need help with installing the tar.gz? If so follow these instruction

Install checkinstall:
sudo apt-get install checkinstall

Download the source package:
wget [http://ktorrent.pwsp.net/downloads/ktorrent-1.0.tar.gz](http://ktorrent.pwsp.net/downloads/ktorrent-1.0.tar.gz) [COLOR="RoyalBlue"]you have already downloaded the latest file so ignore this step[/COLOR]

Extract the archive:
tar -xvzf ktorrent-1.0.tar.gz [COLOR="RoyalBlue"]in terminal, type cd /location/of/targz/ ie "cd ~/Desktop/ktorrent.tar.gz" before you extract the file with the tar command[/COLOR]

Navigate to the extracted folder:
cd ktorrent-1.0

Configure the package, using this command:
./configure

Or this (for faster compilation):
./configure --enable-final

Note: if you does not compile a KDE based package before, you will get an error message complaining about missing KDE/QT headers or libraries files. To fix this problem, install the following packages:
sudo apt-get install libqt3-mt-dev kdelibs4-dev

Compile the package:
make

Install the package:
sudo checkinstall -D make install

You will find the program in the following place:
Kmenu > Internet > Bittorent Client (KTorrent)

---

### Post by belier on 2008-10-19
Did everything on last post but it doesn't appear on the Internet menu...

By now I'm using Azureus.

Thx for helping

---

### Post by spinny on 2008-10-26
This is the reason why people do not switch to linux.... Installing a SIMPLE program like this should NEVER be this complicated. Why can i not just download the file and install it!!! (is that so hard??)

Why is the file in add and remove files so OLD!!!

I am using that file and the memory leaks are driving me crazy, but the instructions above might as well be in finnish. (not slamming you just pointing out that most people that are new to ubuntu would not have the first clue as to how to follow your directions. (ie i get lost at the ./configure part) says no directory.

Is there no simple install file for this program, or does one have to be a ubuntu guru to use this.

sorry for my rant, but this is just crazy. (and you guys make fun of windows.)

---

### Post by SunnyRabbiera on 2008-10-26
> **spinny said:**
> This is the reason why people do not switch to linux.... Installing a SIMPLE program like this should NEVER be this complicated. Why can i not just download the file and install it!!! (is that so hard??)

Why is the file in add and remove files so OLD!!!

I am using that file and the memory leaks are driving me crazy, but the instructions above might as well be in finnish. (not slamming you just pointing out that most people that are new to ubuntu would not have the first clue as to how to follow your directions. (ie i get lost at the ./configure part) says no directory.

Is there no simple install file for this program, or does one have to be a ubuntu guru to use this.

sorry for my rant, but this is just crazy. (and you guys make fun of windows.)

well please note that if you are using Hardy it only keeps to the last known stable package as sometimes the latest version has too many errors.
Also keep in mind that add/remove is NOT the main installer in ubuntu, its only a simplistic tool.
If a update is availible and it is known to be worthy of update then Ubuntu will update to it.
What version of ubuntu are you using here anyway?
Hardy has just updated to kde 3.5.10 for kde3 users and KDE 4.2 for KDE4 users.
If this is a kde4 issue expect it as KDE4 is still experimental

---

### Post by spinny on 2008-10-26
Ok where is the main file spot??? 

i am running heron... how do i find out what kde version???

Can you translate the instuctions above?? what is the ./configure???

i need help to get the new program as the old version is dragging may computer down.

I just do not get why there is just not a exe file like windows has... is that so hard???

thanks

---

### Post by SunnyRabbiera on 2008-10-26
> **spinny said:**
> Ok where is the main file spot??? 

i am running heron... how do i find out what kde version???

Can you translate the instuctions above?? what is the ./configure???

i need help to get the new program as the old version is dragging may computer down.

I just do not get why there is just not a exe file like windows has... is that so hars???

thanks

Typically Linux doesnt use executables, because it has its own set of installers.
Just because windows installs things its way doesnt mean its a standard on all operating systems.
But lest go down the line, to find out your KDE version does it look anything like this:
[http://en.wikipedia.org/wiki/Image:KDE_4.png](http://en.wikipedia.org/wiki/Image:KDE_4.png)

---

### Post by spinny on 2008-10-26
no mine is brown (elephant skin) it does not look anything like that picture.

but.... 

when i goto ktorrent and select help>about kde it says version 4.0.5

hope that helps

ohh and i know it is not standard (exe) but it is standard in windows and uncomplicated, and that is my point.

why would there not just be a file to download and run to install and remove old versions, etc... making ubuntu easy is the key to general acceptance.

---

### Post by SunnyRabbiera on 2008-10-26
> **spinny said:**
> no mone is brown (elephant skin) it does not look anything like that picture.

but.... 

when i goto ktorrent and select help>about kde it says version 4.0.5

hope that helps

ohh and i know it is not standard (exe) but it is standard in windows and uncomplicated, and that is my point.

why would there not just be a file to download and run to install and remove old versions, etc... making ubuntu esy is the key to general acceptance.

Well Ubuntu does have that, it just does it in a different way.
But if you are using KDE 4.0.5 I vcan see why you are having issues.
No worries, for you you can add this repository to your sources list:
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/)
If you need instructions I can provide them on how to get the latest version of KDE4.
It will overwrite your old applications as well so any issues you have now may be fixed with the update.

---

### Post by spinny on 2008-10-26
clicked on the link and get a not found error, please check the link is current...

and yes i would like the help upgrading... or should i wait for the new release in a week?

thanks again

tried the link again.. it worked.. but what do i do once i get there?

---

### Post by SunnyRabbiera on 2008-10-26
> **spinny said:**
> clicked on the link and get a not found error, please check the link is current...

and yes i would like the help upgrading... or should i wait for the new release in a week?

thanks again

dont worry about the link, dont worry about the upgrade to ibex.
Firstly i will ask are you using Ubuntu or Kubuntu?
Or ubuntu with KDE installed?

---

### Post by spinny on 2008-10-26
i am running ubuntu... how do i know if i have kde installed?

---

### Post by milesinnz on 2008-10-26
I have been using Ktorrent for a long time, then a few weeks ago I started getting performance problems – memory seems to be getting used up. Then I found what had happened.

I upgraded to Hardy by a fresh installation and reinstalled Ktorrent from the option in “Applications - add/remove”.

Looking at the Ktorrent applications from System – Administration – Synaptic Package Manager, and doing a “search” for Ktorrent I find there are two Ktorrent packages shown.

I installed the first Ktorrent listed (not the Ktorrent-Kde4 – which was shown correctly as installed already) and of course there are now two versions of Ktorrent under “applications – internet”. Using the second one runs Ktorrent 2.2.5 which I can now see is the one I have been using with no problems for ages! On a 32bit 1.8 ghz 512Mb desktop.

So there seems to be a problem with Ktorrent-Kde4 – which I guess must be the later version.

---

### Post by SunnyRabbiera on 2008-10-26
> **spinny said:**
> i am running ubuntu... how do i know if i have kde installed?

so you are running regular Ubuntu with some KDE applications then?
I am just trying to determine your situation here thus all the questions.
Now this might seem like an odd question  but what does your current main desktop look like?
does it have a panel on top and another on the bottom and you have the bird wallpaper?
if so you are using gnome and that gives me a basis on telling you what you need to do, to see if it is really gnome go up to system, then to administration and system monitor and go to the first tab in that.
if there is a menu like this in the first place then I know you are using gnome and the standard ubuntu desktop and i can teach you how to get what you want working here.

---

### Post by spinny on 2008-10-26
it says 

8.04 hardy
gnome 2.22.3

i had the bird desktop but changed it to elephant skin

i also enabled extra effects

---

### Post by SunnyRabbiera on 2008-10-26
> **spinny said:**
> it says 

8.04 hardy
gnome 2.22.3

i had the bird desktop but changed it to elephant skin

i also enabled extra effects

Alright, there is what i need to know.
In a terminal I would put in gksudo gedit /etc/apt/sources.list
and add this line to it:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/) hardy main

after you add it you exit your terminal and then in synaptic located under system> administration> synaptic package manager hit the "refresh" button
This will reload your repositories and then search for ktorrent, you should have the latest version listed as an update.
It should be easy enough to update the latest version.

---

### Post by spinny on 2008-10-27
ok my version of ktorrent is 3.0.1

in the place you told me it has 2 files

1 is ktorrent with a ubuntu symbol it says version 2.2.5 torrent client for kde

2 is ktorrent-kde4 has listed under installed version 1:3.01-0ubuntu1 

what do i do from here?

thanks

---

### Post by milesinnz on 2008-10-27
right click the line with the 2.2.5 version - (the box to the left should be empty), then select "mark for installation" then where the green tick says "apply" click, and all should be good

---

### Post by SunnyRabbiera on 2008-10-27
> **milesinnz said:**
> right click the line with the 2.2.5 version - (the box to the left should be empty), then select "mark for installation" then where the green tick says "apply" click, and all should be good

right, it should be a easy transition.
If you need the KDE4 version dont be afraid to download it :D

---

### Post by belier on 2008-10-27
Hi. The thread is resurrected. I ended up using the 2.5.0.4 version of azureus cause it was on the list. I would have used ktorrent for not having to use a java application but i was unable to install the version that I needed. 
I have installed version 3.5 of KDE. Is it worth to go to version 4? I've read about not being as stable as 3.5. Is it true?

---

### Post by spinny on 2008-10-27
should i wait till my torrents are done.. (i have a SLOW connection) or will they be transfered to the new version?

thanks for all your help.

peace

---

### Post by milesinnz on 2008-10-27
You can swap your old torrents to 2.2.5 can't remember the exact details but firstly you will need to know where the data from the Ktorrent is being stored with your existing version – remember the option in the file browser (Nautilus) to display “hidden files” under “view” - note the hidden files are prefixed with a “.”

I think when you start 2.2.5 it will complain that it can't find the data file for your individual torrents. If you “right click” each individual torrent, there are a number of options, one of them being “set download location”. Set this to where your current Ktorrent is storing them.

---

