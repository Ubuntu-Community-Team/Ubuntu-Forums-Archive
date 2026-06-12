---
title: "please teach me to install"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by humansreplaceable on 2008-06-29
I just installed xubuntu on an old computer to teach myself linux. It has no internet connection wich seem to be the only way to install stuff on the computer. 
Ive been reading all the forum questions and guides on how install but it seems impossible. 

can someone please help me with what I need to know to understand these things? rtfm is good I like that philosphy so can someone please shot me a good guide for installing stuff in xubuntu or maybe even a book.

ive spent this entire day trying to install a nes emulator. 

and another thing. in the install.txt file or whatever it was it says. press ./configure then make and make install. ive read other instructions like this. it didnt work at all.
usually it will not just work but with this, nestux or something, it did say tat it didnt know the host. i read something on how to tell the shell or whats it called what the host was. then another problem comes up.


so i need some kind of instruction guide that clearly explain how to install downloaded apps in xubuntu.

thank you for reading this far and sorry for making it so long.
^^

---

### Post by sayakb on 2008-06-29
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
In this: Synaptic, CLI methods etc. are also applicable for Xubuntu

---

### Post by Troll_the_Great on 2008-06-29
You were trying to install a source code.It is difficult for a beginner to do this.If you want to install a package, find a debian package (has a .deb extension : package.deb) and just double click it (like in windows).This link may be helpful: 
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
Also try these:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://www.getdeb.net/](http://www.getdeb.net/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)

---

### Post by humansreplaceable on 2008-06-29
> **LinuxIsInnovation said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
In this: Synaptic, CLI methods etc. are also applicable for Xubuntu
-------------------------

okay i dont understand the linux terminology yet so i didnt understand that but il check the påage thank you

---

### Post by sayakb on 2008-06-29
Well, I meant that all instances in the page referring to "Synaptic Package Manager" or "apt-get" or "dpkg" should work fine with Xubuntu (which has XFCE window manager). Sorry for not being clear :)

---

### Post by Troll_the_Great on 2008-06-29
CLI=command line interface (in the terminal).The terminal can be found under Applications-Accessories-Terminal.
Synaptic is a graphical interface for installing programs.You can find it under System-Administration-Synaptic Package Manager (I use gnome desktop, but I think is the same in X-face).
Hope this helps.
Cheers!

---

### Post by humansreplaceable on 2008-06-29
hmmm. this still seem to be a online guide.

each time i try to install a program ive downloaded it says something like i need to install another thing to install that program.

with any ubuntu or linux is it possible to install any application i download? .tar.gz or .deb or .rpm???

you advice is to mostly look for .deb?

---

### Post by sayakb on 2008-06-29
Yes. Debian (.deb) packages are easy to install. While trying yo install something, open Synaptic Package Manager and search for the application there. If you find it, click it and select **Mark for installation** and then press **Apply.** If you know the package name (for example, if you want VLC media player for which the package name is simply **vlc**) open a terminal and type:
```
sudo apt-get install vlc
```
And it'll download and install it for you. :)

---

### Post by Troll_the_Great on 2008-06-29
Yes, debian packages are for linux how is .exe for windows (in a way).Tar.gz, tar.bz2 and so on are source packages, and they usually require "dependencies" (other programs) in order to work.It's not for a beginner to try to install them.Rpm packages are for other major linux branch, The red-hat linux.You can install them on Ubuntu, but you have to translate them, and it's not worth it because is a very high probability to find a debian package instead.
Hope this helps.

---

### Post by humansreplaceable on 2008-06-29
so the sudo apt-get only works with deb?

is that the reason why each time i try to isntall a downloaded and extracted file it says "e: couldnt find vlc" as an example?

---

### Post by humansreplaceable on 2008-06-29
okay. now i tried a .deb nes emulator. it seems as if i still need alot of other stuff programmed too. does everyone simply install these one by one or can i download somekind of bigger file containing the most important stuff?

is this off topic?

---

### Post by nowshining on 2008-06-29
u need the roms for the emulator - as for RPMs, u can install alien and fakeroot to change a RPM to deb, etc.. by going into the terminal 

fakeroot alien -d pathtofile/file - once it creates a deb file u can double-click on it to start the install.

---

### Post by humansreplaceable on 2008-06-30
> **nowshining said:**
> u need the roms for the emulator - as for RPMs, u can install alien and fakeroot to change a RPM to deb, etc.. by going into the terminal 

fakeroot alien -d pathtofile/file - once it creates a deb file u can double-click on it to start the install.

but how do I get alien. that whole synaptic installer thing is useless. the computer will always be off line so i need advices that works on an offline computer or perhaps link that teaches the basics of using xubuntu. cant i install anything with it?

i try look for the alien thanks

---

### Post by humansreplaceable on 2008-06-30
> **humansreplaceable said:**
> but how do I get alien. that whole synaptic installer thing is useless. the computer will always be off line so i need advices that works on an offline computer or perhaps link that teaches the basics of using xubuntu. cant i install anything with it?

i try look for the alien thanks

---------------------

and of course i tried to install alien but I couldnt it said error and something else. always the errors.

the description of the program says that it converts so i can use dkpgk or something to install. what is dkpgk?? does it works in xubuntu?

arigato

---

### Post by Midgetprawn on 2008-06-30
I had a lot of similar problems as my PC was a standalone and did not connect to the net. I spent lots of time downloading debs and tarballs to my pendrive and copying them. Then I would find that I needed to download another package to support xy and z. It was very frustrating. Even when you are connedcted to the net it can still be a nightmare.

Has anyone produced a Cd with packages for distribution? This could help offline Ubuntu users?!?

---

### Post by nowshining on 2008-06-30
u can order a copy of the repos on DVD, etc.. from the canonical store :) or download it urself if you have a fast connection.

and as for dpkg -i nameofpackage/pahtotofilepackage

it's a terminal command:

and yes 

when the installer errors out - it prob. needs another package installed first.

packages.ubuntu.com

---

### Post by sayakb on 2008-06-30
Goto System->Administration->Software Sources
Check first four sources under the **Ubuntu Software** tab.
Check all available 3rd party sources you.
Check **Important **and **Recommended** update sources.

Then open a terminal and do:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install vlc
```

PS: Use of alien is NOT advised because:
1. You are most likely to find a debian alternative of the rpm package being worked upon
2. The resultant deb may break your system packages

You may download individual deb files from [here]("http://packages.ubuntu.com"). Make sure you select the correct OS version and architecture.

---

### Post by humansreplaceable on 2008-06-30
> **Midgetprawn said:**
> I had a lot of similar problems as my PC was a standalone and did not connect to the net. I spent lots of time downloading debs and tarballs to my pendrive and copying them. Then I would find that I needed to download another package to support xy and z. It was very frustrating. Even when you are connedcted to the net it can still be a nightmare.

Has anyone produced a Cd with packages for distribution? This could help offline Ubuntu users?!?

did it get better?

yes the ubuntu community really need to distribute some kinds of usb dvd or cds with alot of stuff that could be needed.

---

### Post by sayakb on 2008-06-30
There are Ubuntu DVDs that contain quite many packages as compared to the CD.
[http://nginyang.uvt.nl/](http://nginyang.uvt.nl/)

---

### Post by durand on 2008-06-30
Try NoNetDebs: [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819) for installing programs if you don't have an internet connection.

---

### Post by cariboo on 2008-06-30
With all the hassle's you are having won't it just be easier to temporarily connect to the internet and install what you want.

Jim

---

