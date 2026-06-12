---
title: "How to download an external program and install it!"
date: 2015-09-12
forum: New to Ubuntu
---

### Post by David_Navratil on 2015-09-12
I found a program I might want to try in U14.04 LTS!  It's called YaRock.  I went to their homesite and downloaded it using U14.04 Firefox.   I have U14.04 on an external drive on my laptop with W10 on my C drive so I can use both OS's and try to learn Ubuntu.  I found where I downloaded the program but instead of it downloading to my external drive where Ubuntu is It ended up on my internal drive!!  I opened the folder and I don't see any Exe files.  Does Ubuntu use Exe files? - I'm completely new to Linux as you can tell!! Tks for any help - David

---

### Post by brian-mccumber on 2015-09-12
If that program is for Linux/Ubuntu there won't be any exe's in it. If the program doesn't have a deb file, ppa, or isn't in the Ubuntu Software Center then you will probably have to build the program or run the install or makefile script in it's folder for it to run on Ubuntu.

---

### Post by David_Navratil on 2015-09-12
Yikes, it looks like this is all over my head!!!

---

### Post by coffeecat on 2015-09-12
No, you rarely if ever need to compile anything. But one thing you need to bear in mind is that Linux is not Windows. Searching the internet for downloadable application installers should be last but one in a very long list. Compiling last - unless you are a developer or enjoy misery! :) Wherever possible, install stuff from the repositories using the Software Centre or another package manager. If the application you want isn't in the official Ubuntu repositories, more often than not someone has set up a PPA - personal package archive. The advantage of using a PPA is that you get automatic updates. The disadvantage is that the quality of some PPAs leaves something to be desired.

For Yarock, you could look at this:

[http://www.webupd8.org/2015/08/qt-music-player-yarock-113-released.html](http://www.webupd8.org/2015/08/qt-music-player-yarock-113-released.html)

I can't vouch for the quality of that PPA though.

---

### Post by brian-mccumber on 2015-09-12
It's a little more complicated than double clicking an exe for sure. Just so you know Ubuntu has a music player but if you want to install YaRock I found the ppa for it for you. 

In order to install it, run these three lines one at a time in the terminal. In order to paste them into the terminal you must press Control+Shift+v.

```

sudo add-apt-repository ppa:samrog131/ppa
sudo apt-get update
sudo apt-get install yarock

```

Basically what this does is it adds Yarock ppa(personal package archive) to your list of software sources, updates your software source's list, and then installs Yarock. You can paste them all in at once, but for simplicity's sake I suggested one line at a time.

Here is the link where I found the ppa at - [http://www.webupd8.org/2014/11/qt4-music-player-yarock-100-released.html](http://www.webupd8.org/2014/11/qt4-music-player-yarock-100-released.html)

---

### Post by pfeiffep on 2015-09-12
> **David_Navratil said:**
> Yikes, it looks like this is all over my head!!!
I would rethink your statement about being over your head and reword it to something like "I'm at the beginning of my learning curve"
Please remember that Linux accomplishes most tasks differently than Windows. 
I did a quick [search]("http://gamblisfx.com/how-to-install-yarock-1-0-on-ubuntu-14-04/") YaRock on Ubuntu 14.04 ... take a gander and see if you're willing to do some work in the terminal.
If you're not ready for the chapter on terminal operations quite yet, then I respectfully suggest that you consider the VLC music player which is available for install from the Software Center.

---

### Post by monkeybrain20122 on 2015-09-12
Is this the music player? You can install it with webupd8's ppa. It will add the application to your software sources and update it through the normal update channel.

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install yarock
```

[http://www.webupd8.org/2015/08/qt-music-player-yarock-113-released.html](http://www.webupd8.org/2015/08/qt-music-player-yarock-113-released.html)

> **brian-mccumber said:**
> 
Here is the link where I found the ppa at - [http://www.webupd8.org/2014/11/qt4-music-player-yarock-100-released.html](http://www.webupd8.org/2014/11/qt4-music-player-yarock-100-released.html)

samrog's ppa has been removed from launchpad. Now yarock is in webupd8's ppa.

> **coffeecat said:**
>  

For Yarock, you could look at this

[http://www.webupd8.org/2015/08/qt-music-player-yarock-113-released.html](http://www.webupd8.org/2015/08/qt-music-player-yarock-113-released.html)

I can't vouch for the quality of that PPA though.

 

I can vouch for the quality (I mean the ppa, not the software, never use it) Webupd8 is very popular and reliable.

---

### Post by Geoffrey_Arndt on 2015-09-12
Hmm, , , what does yarock have in features that are not already provided by proven linux media players such as Banshee or even VLC?    Those take maybe 40 seconds to complete the install and add the icon to the Unity Launcher (using Ubuntu Software Center).


That's not even over my granny's head.  :guitar:

---

### Post by monkeybrain20122 on 2015-09-12
> **Geoffrey_Arndt said:**
> Hmm, , , what does yarock have in features that are not already provided by proven linux media players such as Banshee or even VLC?    Those take maybe 40 seconds to complete the install and add the icon to the Unity Launcher (using Ubuntu Software Center).


That's not even over my granny's head.  :guitar:

I use guayadeque, it is the best music organiser, player for me, but unfortunately it is abandoned (dev has other fish cooking and promises a new player, just released a demo video recently but don't know when it is coming) It is broken in 15.04 and had to install an older version. I don't expect it to work after 15.04. I have been looking for a replacement. Never like Rhythmbox, Banshee is bloated and buggy, Clementine cannot recognise some of my files and it seems development is also stalled. 

It is good that I come across this thread. This does look interesting.

---

### Post by mystics on 2015-09-12
For future reference EXE files are Windows-specific. You'll need Wine in order to run them on Linux: [https://www.winehq.org/](https://www.winehq.org/)

However, compatibility with Wine is not guaranteed, and even if you can get the program running, there may be issues with performance. Best thing to do is to first look for a Linux version of the program or an alternative on Linux.

And as for finding software on Ubuntu, a few things to do (in order of the best method):
1. Look up the program in the Ubuntu Software Center and/or Synaptic Package Manager. The former comes pre-installed on Ubuntu, and I believe you need to install the latter. Both of those provided convenient ways to search for specific software or just browse categories for something that looks good. The Ubuntu Software Center is easier to use and provides helpful things like reviews. Synaptic, however, tends to be better overall from my experience.

2. Follow command-line instructions. These will often be given for you one the products web page.

3. Locate a DEB file online. This is equivalent to the EXE installer on Linux. While not ideal, this is a method used by some programs, particularly those geared towards Windows.

4. Quit trying with that program and look for another. 

5. Compile it yourself from source code. Make sure you have a few years to spare for this method. :)

Hope that helps for future reference. I know it seems a little like an information dump at first, but give it a little time and it'll eventually become comfortable.

(Note: Despite my jokes about compiling from source code, it is a valid method that does not take years to complete. I just personally tend to look for alternatives once I realize that that is the only available method. There almost always are alternatives that you can get up and running with the other methods in half the time, if even that.)

---

### Post by Geoffrey_Arndt on 2015-09-13
Exaile seems well supported, actively developed, and a ton of plugins.   Most stable player I've personally used.

---

