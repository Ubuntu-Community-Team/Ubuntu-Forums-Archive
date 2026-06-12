---
title: "HOW-TO: Install GrabIt and associate it with NZB files (WINE)"
date: 2007-02-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Corvo78 on 2007-02-14
First of all I'd like to point out that I haven't tried out any native (Linux) newsreaders yet.
As far as I could tell, from reading the forums, none of them came close to GrabIt's ease of use.
So, this how-to focusses on installing GrabIt using WINE ([www.winehq.com](http://www.winehq.com/)).

I can imagine that 'purists' would like to try and prevent Win32 apps from being installed...
...therefor I've compiled this list of native applications they can try first:[list]
[*]PAN
[*]KLibido
[*]HellaNZB[/list]*(If anyone knows another application, I'll add it to the list.)*
In the future, I'm surely going to give HellaNZB a whirl.


I recently 'converted' to Ubuntu Linux and I'm certain more people, like me, would consider not having
a similar binary news leecher a showstopper from switching over to Linux entirely (completely ditching Windows).

I also want to give something back to the great Ubuntu community.
I based this how-to on my installation of GrabIt on my 32-bit Ubuntu Edgy (6.10) desktop installation.

Without further delay, my How-To: :)
_________________________



[SIZE="3"]*** Step 1 - Installing WINE**[/SIZE] *(a.k.a. the Microsoft Windows Compatibility Layer)*
In order to install WINE I simply followed Wine-HQ's instructions, found here: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
In short, it boils down to this (for Ubuntu Edgy):
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```


[SIZE="3"]*** Step 2 - Configuring WINE**[/SIZE] *(optional)*
In order to install/run GrabIt this step isn't necessary, since the default settings work nicely!
Now that WINE was installed I would like to be able to configure it. So, I navigated my gnome-menu and selected 'System > Preferences > Menu Layout'.
This will start the 'Alacarte' programm which will allow you to Add/Remove items to your gnome-menu.
I added a menu-item to 'System > Preferences' and named it 'Wine configuration', selected some generic icon and set it to run the following command
```
winecfg
```In my case the newly added item didn't show up until I rebooted (Old Windows habits, die hard...).
Start Wine configuration and change things you deem approriate. In my case I changed to default Sound Driver from OSS to ALSA and changed some directory links
(I made 'My Music' link to a different folder on my Linux partition).


[SIZE="3"]*** Step 3 - Downloading GrabIt**[/SIZE]
I wanted all WINE related things to be stored in one place, so I made a new folder in my home for this.
I named the new folder 'vinyard', allthough anything will do.
Within this folder I created two more subfolders, namely 'installers' and 'launchers'.
Using my favorite browser I surfed to [www.shemes.com](http://www.shemes.com/index.php?p=download) and downloaded the latest version of GrabIt (in my case this was version 1.6.2 ßeta).
I moved the download to my '~/vinyard/installers/' folder.


[SIZE="3"]*** Step 4 - Installing GrabIt**[/SIZE]
In nautilus right click on GrabIt's installer (in my case the 'GrabIt162b.exe' file) and choose the 'Open With' tab.
In this tab choose to add a new program and simply use the following command
```
wine
```Close the dialog and double-click on the installer. You should be able to run it (using Wine).
_Important:_
The installation will play nice until the installer wants to launch a browser window. Since this is impossible, an error will show-up and exit the installer.
Fact is, the installation was succesfull except the installer didn't create a 'start-menu shortcut'. This however, proved to be a good thing.


[SIZE="3"]*** Step 5 - Creating a 'Wine/GrabIt' shell file**[/SIZE] *(a.k.a. launcher)*
In order to be able to launch GrabIt when double-clicking a NZB file a shell (batch) file needs to be created.
Using my favorite editor (in my case that is 'gedit') I created a file named 'GrabIt.sh' in my '~/vinyard/launchers/' folder.
The contents of the file should be
```
wine "C:\Program Files\GrabIt\GrabIt.exe" $1
```Using nautilus, right-click on the file and make sure to mark a checkbox to make 'GrabIt.sh' executable.


[SIZE="3"]*** Step 6 - Creating the missing menu shortcut for GrabIt**[/SIZE]
As you might have seen, after installing GrabIt there's now a Wine menu available in the gnome-menu under 'Applications'.
Now we're going to correct the installer's error by creating a custom 'start-menu shortcut' to our newly made 'GrabIt.sh' file.
I navigated my gnome-menu and selected 'System > Preferences > Menu Layout'.
This will start the 'Alacarte' programm which will allow you to Add/Remove items to your gnome-menu.
I added a menu-item to 'Wine > Programs > GrabIt' and apptly named it 'GrabIt', selected an icon and set it to run the following command
```
~/vinyard/launchers/GrabIt.sh
```In my case the newly added item didn't show up until I rebooted (Old Windows habits, die hard...).


_________________________


**WE'RE DONE!!** :KS 

Everything is now setup! It's probably a good idea to run 'GrabIt' now and set it up with your nntp-server settings.
When downloading a NZB file in your browser (in my case that is 'Firefox') select it to automatically use the 'GrabIt' application
(it should be listed since it is in our gnome-menu). GrabIt should run and ask details on how-to import the downloaded NZB file!

I hope this How-To is of use to some people. My biggest problem setting it up was to have Firefox be able to launch GrabIt.
That's when I thought up to use a shell file as a 'wrapper'... and to my amazement, that worked :D


*(If anything is wrong with my how-to or could be improved, I'm glad to hear it and change the how-to accordingly.)*

---

### Post by frodon on 2007-02-14
Nice guide but as you said not inescapable because native linux apps do the same job, i just don't agree with the "none of them came close to GrabIt's ease of use" because it is really a matter of feeling. For example i find Klibido with par2 far more easy to use than grabbit but it's just me ;)

---

### Post by Corvo78 on 2007-02-15
Thanks.
I'm sure that in time, I will try all alternatives. It's just that by reading the forums I got the impression that all "ex-Windows" users were kinda missing GrabIt.
I guess I simply got used to GrabIt's interface too much ;)

Being able to run GrabIt in Linux, is one less reason for potential Ubuntu users to stick to Windows.

---

### Post by Chevalric on 2007-02-15
Hi Corvo ;)

I'm currently using Klibido for my downloading entertainment under Ubuntu. I have some issues with it, that would convince me to follow this howto:
[LIST=1]
[*] Klibido is unable to open NZB files directly. I need to save them first from Firefox, and then open them through the Klibido menu.
[*] Klibido only supports 4 threads, but I have a newsserver that allows me to use 8 threads.
[*] My system slows down when Klibido is decoding a file that I've downloaded.
[*] Oh, and of course because it's officially a KDE app, and I'm using Gnome, so it looks weird :P).
[/LIST]

Finally, I'd like to say, good howto. I hadn't looked at Wine yet, but it seems easier than I expected.

---

### Post by Corvo78 on 2007-02-15
I was expecting Wine to be difficult too, but it isn't. There's a good userguide for it, here: _[WINE User-guide](http://www.winehq.com/site/docs/wineusr-guide/index)_

I actually didn't realize it yet, Klibido is a KDE app (The "K" should have been a dead give away, I know...).
Since I use Ubuntu, and thus use Gnome, installing a KDE app would cause a lot of KDE libraries to be installed (right?). Which is not preferable, I'd think.

---

### Post by frodon on 2007-02-15
Another great wine ubuntu guide which cover almost all the questions and common tweaks can be found here :
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by ykpaiha on 2007-02-15
just to add:
klibido looks fine but too much memory and system eater!
pan works fine as well but need to be a bit improved . to my point of view.
[http://pan.rebelbase.com/](http://pan.rebelbase.com/)
:popcorn:

---

### Post by frodon on 2007-02-15
I guess i never got problems with klibido because i have 2Go of RAM :), don't know for low ressource computers.

---

### Post by Chevalric on 2007-02-15
Well, Pan is ok, but I don't like the way the UI works.
And Klibido works fine with 1 GB as well, but it slows down the system on decoding files.

---

### Post by pt123 on 2007-03-04
I got a problem after its downloaded the files it is putting this around the file name
[b]
[11334]-[#altbin@EFNet]-[FULL]-[Some.Movie.XviD-ESPiSE]-[028132] - espise-xvid-cd1.r18 yEnc (3636) (by Yenc-PP-GB).txt[/b]

---

### Post by Corvo78 on 2007-03-05
Strange.... I haven't had this problem (in Linux).
This basically means that GrabIt hasn't decoded the files... and I can understand that you don't want to do this manually (it is possible, btw).
I assume you were using the latest version of GrabIt?

Hmm.... Perhaps there's a newer version of yEnc encoding?
Although I do know for sure that I've had decoding problems like this on Windows too, from time to time (it is related to certain posts, that much I know).

Sorry I can't be more of help.

---

### Post by pt123 on 2007-03-05
Can you tell me how to do the decoding manually. I don't want to waste the bandwidth I wasted on these files.

---

### Post by Corvo78 on 2007-03-05
Ok, first the Linux way. Apparently there's a util in Feisty Fawn that should decode Yenc: _[packages.ubuntulinux.org/feisty/utils/yydecode](http://packages.ubuntulinux.org/feisty/utils/yydecode)_
Otherwise have a look at this page for other Linux utils: _[www.yenc.org/linux.htm](http://www.yenc.org/linux.htm)_
I haven't used any of those, so...

...and during my time in Windows I believe I used this: _[www.yenc32.com](http://www.yenc32.com/)_
Otherwise have a look at this page for other Win32 utils: _[www.yenc.org/windows.htm](http://www.yenc.org/windows.htm)_

Good luck

---

### Post by pt123 on 2007-03-16
Now it is working it doesn't seem to work when you use it first time after you install, same problem on another machine.

its all good now.

---

### Post by kunchi on 2007-04-24
this is great I have WINE and I have grabit... YES I AM A GRABIT FAN...

NOw how do I get PAR2 and WINRAR? to work in linux?

Also is there a perferred method for where the download cach is and download directory or do they have
to exist in the .wine drive?  

Can they be changed to home/username/download and cache?

I am new to ubuntu but am loving Fiesty Fawn already.!!!!

---

### Post by Corvo78 on 2007-04-25
> **kunchi said:**
> this is great I have WINE and I have grabit... YES I AM A GRABIT FAN...Hehe, so was I :)

> **kunchi said:**
> NOw how do I get PAR2 and WINRAR? to work in linux?WinRar isn't needed. Ubuntu's Archive manager (a.k.a. File Roller) should be able to open the files and extract its' contents.
I'm not sure if the is a Par2 application that has a GUI (graphical user interface), though I know for sure that there is a command-line Par2 in the repositories.
Just have a look in Synaptic and search for Par or Par2.

> **kunchi said:**
> Also is there a perferred method for where the download cach is and download directory or do they have
to exist in the .wine drive? I know that if you use 'winecfg' you can map a Windows-directory to a Linux-directory. So yes, in a way: you can. You can also choose to let it reside in the .wine drive

> **kunchi said:**
> Can they be changed to home/username/download and cache?Just create the appropriate directories in linux. Press ALT-F2, type 'winecfg' and search for a tab where 'my documents' and such are mentioned. It is in this tab you should be able to map a Wine/windows location to a Linux location.
For instance, you could 'my documents' point to '/home/kunchi'. So, in GrabIt you can point to 'My Documents\download'... which would result into files being downloaded to '/home/kunchi/download'.

> **kunchi said:**
> I am new to ubuntu but am loving Fiesty Fawn already.!!!!
I'm glad this how-to (and many others, for sure) make your Ubuntu experience such a great one :KS 



Currently I am no longer using GrabIt in Linux anymore. I've switched to HellaNZB which does everything for me.
Have a look at this how-to: _[HOWTO: NZB, PAR and UNRAR all-in-one](http://ubuntuforums.org/showthread.php?t=169749)_


Basically, if HellaNZB is started. All you have to do is place a NZB file in a specified directory, and the rest is done by HellaNZB!
Which is: Downloading the RAR files (not PAR), trying to extract RAR (if not succeeded, PAR will be downloaded and used afterall), place extracted contents in a specified directory.
I just love it :D

Only thing I really miss from GrabIt is that Hella doesn't shut my computer down (allthough I believe the Devs want to implement this eventually).

---

