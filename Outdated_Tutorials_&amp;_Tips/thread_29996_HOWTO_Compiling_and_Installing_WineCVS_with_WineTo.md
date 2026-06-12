---
title: "HOWTO: Compiling and Installing WineCVS with WineTools"
date: 2005-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Vaego on 2005-04-26
Alright, well, i've tried the latest Wine CVS and winetools and I have to say i'm impressed, wine is not too far behind Cedega and I think in the next year Wine might take the step ahead of them. Granted, they deserve to be ahead, they are the creators and Transgaming kind of stole their project and are hogging it for themselves.

So I present to you all, a howto on how to install the latest Wine CVS, installing wine tools and getting everything you'll need for the road.

**1) Getting The Development Libraries to compile wine:**

We also need a few development libs to compliment this:

xlibs-dev will allow you to compile wine with x support, the reason behind why most compilations of wine fail under Ubuntu.

```
sudo apt-get install xlibs-dev
```


If you want OpenGL support, don't forget to get these libs here:

```
sudo apt-get install xlibmesa-glu-dev
```

Heres two other packages that will make it so wine compiles, and are required during the wine compilation, these are the bison and flex packages.

```
sudo apt-get install bison flex
```

This package here is for winetools, i'll explain this later on.

```
sudo apt-get install libgtk-1.2 libgtk-1.2-common
```

And lastly, we need to get the cvs package to even be able to grab the cvs streight from winehq.

```
sudo apt-get install cvs
```

--

---

### Post by Vaego on 2005-04-26
--
**2) Getting the Wine CVS**

Now we need to pop up a terminal, and lets make a cvs directory. You can do this wherever, but I strongly recommend having one for organization purposes.

```
mkdir cvs
```

Lets go to it now.

```
cd cvs
```

Now, that we are in our cvs directory, and have the right packages, lets connect to the wine cvs now.

There are two servers, a US server, and a Europe server, if you are in the U.S. follow the U.S. howto under here on how to connect to the cvs, if you are in Europe, then do the same for the Europe connection.

To be able to connect, you must type these on your command line ;) and when you connect, it will not say anything, do not be worried

How to Connect to the Wine U.S. CVS Server:

```
export CVSROOT=:pserver:cvs@cvs.winehq.org:/home/wine
```

How to Connect to the Wine Europe Server:

```
export CVSROOT=:pserver:cvs@rhlx01.fht-esslingen.de:/home/wine
```

Now that we have connected to it, now its time to login

```
cvs login
```

the password has and always will be cvs for their cvs login.

Now that you are logged in, its time to download the wine cvs.

```
cvs -z 0 checkout wine
```

Now it will start downloading a bunch of stuff, depending on your connection will depend on how long it will take, this is about 40 megabytes.

--

---

### Post by Vaego on 2005-04-26
--
**3) Compiling and installing Wine**

Now that we have our wine cvs here now, we need to compile it, lets go to your new wine directory inside your cvs directory.

```
cd wine
```

Now, we need to compile this baby, this is the longest part but the easiest hehe..

```
./tools/wineinstall
```

Now it will start the configure script and will ask you a question at the end of the script about logging into root to install wine, just say yes, and let it rock. It will take quite a while, i'm running a AMD 64 3200+ overclocked at 2.3 ghz and it took me about 20 minutes. On my 900 mhz AMD Athlon it took me approx. 50 minutes. So be patient, watch some tv or something.

Ahh, we have the latest version of wine cvs now compiled, but to install it, ahh wait, it says here to login to root, lets say yes ;)

Now it will install the stuff, does not take long a minute or two, and then it will ask you a question about adding in the default wine config at .wine/config

Lets say no. We are going to do something more interesting today kids.

--

---

### Post by Vaego on 2005-04-26
--
**4) Installing Winetools**

Now, for the fun stuff, finally! right? hehe ;), lets go download winetools, here is the url:

But Before I give you the url, we should just get all linuxy and use wget, screw the browsers ;), in your home directory just make a temp directory since this directory won't be here very long....

```
mkdir temp
```

Lets go to it now.

```
cd ./temp
```

And finally, lets download the winetools.

```
wget http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz
```

This you may notice is off my personal webstorage, why did I do this? Because my links will never die ;), anyways lets start on installing this beast.

Lets extract the new tar.gz file now.

```
tar -xzf winetools-211jo.tar.gz
```

It should had created a new directory called winetools, lets go to it now

```
cd winetools
```

To install it, its simple.

```
sudo sh install.sh
```

Now its in, thank god right? hehe, lets get out of this temp directory, if you followed my step, just do this.

```
cd ..
```

One more time.

```
cd ..
```

And now, its time to remove the temp directory to cleanup our mess.

```
rm -rf temp
```

Cleaned, just like that, hehe, well anyway lets rock n roll with winetools.

On your command line, just type wt2 and it should come right up saying something about you using a different version of wine that is not recommended, just click ok, don't worry about that

The GPL License for the software, and the creator, email him if you want and tell him how awesome his winetools are ;)

Just click ok after the intro and now you should see the menu with base setup and all the good stuff we want. Lets start with base setup.

Since we did not create a wine config through the wine install script, which I told you to do this for a reason ;), and if you didn't follow my instructions, no big deal, we can remove it here, just pop up a terminal and type:

```
rm -rf .wine
```

Done, but if you did follow my instructions, lets continue.

Create a fake windows drive is the first one

It should create everything for you, and don't worry if you see any errors through your time in winetools don't worry about it.

Next up is DCOM98 and you're probably asking me, why not install the fonts? Reason why, is because the links are dead to the fonts from winetools, it will just hang, try it if you do not believe me hehe, anyways, install DCOM98.

After DCOM98 is installed, it'll go through its regular routine of shutting down wine after its installed and doing a simulated windows reboot. Next up is Internet Explorer 6.0 SP1, just download it for the language you want. And it will install.

After its done, go back to the main menu.

Now lets install windows system software, install it in this order:

Windows Installer
Microsoft Foundation Classes 4.0
Visual Basic 5 Runtime
Visual Basic 6 Runtime
Visual C++ run-time English -- or german if you are german.
MDAC 2.8 English -- or german if you once again german ;)
Jet 4.0 SP8 English -- Or german if you have german blood!
Windows Script 5.6 English -- Or German if you can drink 50 gallons of beer and still not pass out.

HTML Help Update Package
Common Controls 5.0

Now that you have them all installed, lets go back to the main menu.

Lets exit...

Now what!? What about our great fonts? Yeah yeah... Lets move onto fonts...

--

---

### Post by Vaego on 2005-04-26
--
**5) Installing Windows Fonts**

Now that we have our wine pretty much setup now, we need fonts. I have all the windows fonts you will need uploaded to my storage. I recommend doing this from the command line.

Lets make another temp directory first.

```
mkdir temp
```

Now go there.

```
cd temp
```

Download the fonts.

```
wget http://home.comcast.net/~themachinez/wine/fonts/winfonts.tar.gz
```

Now extract the fonts

```
tar -xzf winfonts.tar.gz
```

time to install them all one by one. I also want to remind everyone, do not install the andale32.exe it fails on wine for some reason, but you can try it if you want.

To install them you will need to do this:

```
wine arial32.exe
```

That will come up with a menu, just click ok then it will install it then it will say the font has been successfully installed. Do this with the rest of them.

wine then the name of the font executable.

When you are done, I am proud to say, you have a full blown wine install with the latest cvs, was it that hard? No, just time consuming and it looks longer than it really is because I talked too much on the HOWTO :)

---

### Post by Seth on 2005-04-26
Very nice! I was able to follow it through with no trouble, except IE6 took a few run-throughs to download completely.

---

### Post by Brain Juice on 2005-04-26
best tutorial evar!  thanks for doing this.

---

### Post by zPacKRat on 2005-04-26
Great tutorial, however I have a question regarding the "sudo apt-get install xlibmesa-glu-dev" this would seem to be a dev package for the Mesa drivers. What if you have installed the ATI drivers? does this still apply?

TIA, a new Ubuntu user
zPacKRat

---

### Post by Silvio Moioli on 2005-04-27
[QUOTE=Vaego]--
**5) Installing Windows Fonts**

Now that we have our wine pretty much setup now, we need fonts. I have all the windows fonts you will need uploaded to my storage. I recommend doing this from the command line.

Lets make another temp directory first.

```
mkdir temp
```

Now go there.

```
cd temp
```

Download the fonts.

```
wget http://home.comcast.net/~vaego/wine/fonts/winfonts.tar.gz
```

Now extract the fonts

```
tar -xzf winfonts.tar.gz
```

time to install them all one by one. I also want to remind everyone, do not install the andale32.exe it fails on wine for some reason, but you can try it if you want.

To install them you will need to do this:

```
wine arial32.exe
```

That will come up with a menu, just click ok then it will install it then it will say the font has been successfully installed. Do this with the rest of them.

wine then the name of the font executable.

When you are done, I am proud to say, you have a full blown wine install with the latest cvs, was it that hard? No, just time consuming and it looks longer than it really is because I talked too much on the HOWTO :)[/QUOTE]
 Why do you recommend the fonts from the command line? Works fine from WineTools here..

---

### Post by jonny on 2005-04-27
Great How-to.  I'm working my way through it with interest.  Some minor points that could trip up unwary noobs, though - I suggest you edit the original post.

1. Two packages are incorrectly named above - it's libgtk1.2 and libgtk1.2-common
2. On a fresh ubuntu installation, you also need the  buildessential package
3. The run as root bit presupposes that you have a root password - which you don't by default in Hoary.  I had to copy the failed command that was reported to me and paste it with sudo.
4. Before running wineinstall, I had to change the permissions on one file, thus: sudo chmod a+w /etc/ld.so.conf, and return it to its former state afterwards
5. Before running wineinstall, I had to backup one file: sudo mv /usr/X11R6/lib/libGL.a /usr/X11R6/lib/libGL.a.old

---

### Post by Vaego on 2005-04-28
Sorry if the links didn't work for a bit, had a user name change and forgot to update the thread's links, enjoy ;)

[QUOTE=zPacKRat]Great tutorial, however I have a question regarding the "sudo apt-get install xlibmesa-glu-dev" this would seem to be a dev package for the Mesa drivers. What if you have installed the ATI drivers? does this still apply?

TIA, a new Ubuntu user
zPacKRat[/QUOTE]

Opengl mesa is already installed, on the system, I believe it uses symbolic links to your real gl (nvidia or ATI), but I may be wrong. Opengl runs without a issue for me with my nvidia card, so it doesn't hurt to install them, if you do run into issues let me know, they are just development packages, my wine would not compile opengl support until I had that package in, but opengl runs flawlessly in wine with that so it shouldn't be a problem, post back though if you get any issues ;)

---

### Post by Thomvis on 2005-04-28
thank you very much for this clear, easy and perfectly usefull HOWTO! I even managed to get my latin-dutch dictionary (wich uses ActiveX) to work thanks to this!

I have one question: in the folder where i created the cvs dir there isn't a cvs dir anymore. But instead of that it contains a wine dir wich is approx 600mb in size! Is this the wine installation or just the compile files, in other words: is it safe to remove? And on the same location i have a winetools dir, and i have the same question for that one.

Thanks in Advance,
thomas

---

### Post by Narg on 2005-04-28
I got up to the point of the fonts fine, and then when I try to

wine arial32.exe

It goves:

wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or director

When I try to do ANYTHING with wine it gives that. What happened? :p

---

### Post by Narg on 2005-04-28
[QUOTE=Narg]I got up to the point of the fonts fine, and then when I try to

wine arial32.exe

It goves:

wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or director

When I try to do ANYTHING with wine it gives that. What happened? :p[/QUOTE]
 Heh, thanks to some help from your friendly #winehq, I fixed it. Nevermind :)

---

### Post by mrbass on 2005-04-29
I installed wine on ubuntu from apt-get....I know not the greatest.  But before I follow this compile wine guide could someone please try to get dvdshrink 3.2 working on their ubuntu.  While installing dvdshrink I'll get a reference error and it'll bomb.
[http://forum.doom9.org/showthread.php?&threadid=91078](http://forum.doom9.org/showthread.php?&threadid=91078)

---

### Post by xodeus on 2005-04-30
[QUOTE=mrbass]I installed wine on ubuntu from apt-get....I know not the greatest.  But before I follow this compile wine guide could someone please try to get dvdshrink 3.2 working on their ubuntu.  While installing dvdshrink I'll get a reference error and it'll bomb.
[http://forum.doom9.org/showthread.php?&threadid=91078](http://forum.doom9.org/showthread.php?&threadid=91078)[/QUOTE]
 I get this messages in console when trying to use wine.
```
wine client error:9: version mismatch 172/159.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```
What can I do to correct it?

---

### Post by jtsai256 on 2005-04-30
This guide worked great! I have one question though... now that it's installed, how do I access the windows desktop? I remember this could be done somehow but I can no longer remember... Thanks.

---

### Post by Vaego on 2005-05-01
[QUOTE=xodeus]I get this messages in console when trying to use wine.
```
wine client error:9: version mismatch 172/159.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```
What can I do to correct it?[/QUOTE]

It almost seems like you got the wine package from the hoary respitory from apt and then tried to do the compiled version of wine, i'd try this if you did maybe

sudo apt-get remove wine wine-libs

I believe its called wine libs, I haven't looked, but if that does not work or you did not have the wine package installed from apt, then I do not know what you could do :(

Also if the remove works and it actually removes the stuff, go back to your directory where the wine cvs source is, and do a make uninstall and run the ./tools/wineinstall script again to completely clean it and have it go back in

Hope that helps ;)

---

### Post by renderedbrian on 2005-05-03
Having trouble with this guide.

I'm running Ubuntu 5.04 AMD64, and I am trying to install wine.

However:

./tools/wineinstall
WINE Installer v0.74

Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.


What gives?

-- 
Brian

---

### Post by foxy123 on 2005-05-03
[QUOTE=Vaego]```
./tools/wineinstall
```--[/QUOTE]

after 30 min I've got the folloing:

```
"./sql.y", line 71: unknown character `.' in declaration section
``` 

over and over again for another half an hour. Is it ok or something's wrong?

---

### Post by foxy123 on 2005-05-04
The full section is the following:
```
bison -p SQL_ -d ./sql.y -o sql.tab.c
"./sql.y", line 71: junk after `%%' in definition section
"./sql.y", line 71: no input grammar
"./sql.y", line 71: unknown character `.' in declaration section
``` 
and the last line is repeating over and over

---

### Post by foxy123 on 2005-05-05
the line it is complaining about is:

```
%pure-parser
```

---

### Post by BAshworth on 2005-05-05
I'm having a problem with this myself.

I get no error messages during the installation of either wine or winetools.  It finishes with no problems, and entering the command wt2 at the command line brings up all the disclaimer screens that are mentioned.  This leaves me at the WineTools 2.1.1 window.  I can select base setup, but the window just flickers, and then comes right back to the same thing.  Apparently, no matter what I select it does this exact same thing.

Any ideas?

---

### Post by Rehevkor on 2005-05-06
I followed the guide exactly and I get this in the terminal repeatedly when I try to run the base setup from winetools:
```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libindustrial.so",
```

The base setup won't open. It just keeps going back to the main menu. It appears that I have the same problem as Bashworth.

What gives? ](*,)

---

### Post by BAshworth on 2005-05-06
Hey!  Got it to work.  I had entered in only half of the command necessary to run as sudo after the root password bit times out.

(of course, I did not think to write down what the rest of the command string was.)

I hit enter twice to have it error out on the root password bit, and then it listed the full command string that it was attempting to run.

Working good now.

---

### Post by Saitun on 2005-05-07
I have just tried this guide, and had the ATI drivers installed and working beforehand. After following this guide, I had Mesa drivers installed instead, and my framerate had dropped by about 75%. I'm fairly confident that I didn't mess up anything during the install. I had simply reinstalled Ubuntu, it was a near-fresh installation anyways. Just trying to give a word of warning for those as eager as me.

---

### Post by simianMiscreant on 2005-05-07
i get this when i hit "base setup" under winetools...

```
Base setup
Choice is
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
```

and winetools flashes once but nothing happens.

---

### Post by willis on 2005-05-08
Good guide but just wondering if you knew about: [http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)

---

### Post by simianMiscreant on 2005-05-08
[QUOTE=BAshworth]Hey!  Got it to work.  I had entered in only half of the command necessary to run as sudo after the root password bit times out.

(of course, I did not think to write down what the rest of the command string was.)

I hit enter twice to have it error out on the root password bit, and then it listed the full command string that it was attempting to run.

Working good now.[/QUOTE]

i'm having the same problem you were - so wait...what did you do to fix it? i don't understand. thanks!

---

### Post by BAshworth on 2005-05-08
Yeah, would have made more sense if I had written down the entire command string that it was trying to run.

When I was prompted for the root password, I hit enter twice to let it error out, and return me to a standard command prompt.   The little message that it gives at this time contains the command string to enter in. 

It broke the first time because I had just entered in 'make/install'. However, the actual command to run is 'make/install;/*insert correct command here*'.  It gives you this after it errors out from you not being able to give it a root password.

Again, sorry for not making notation of what the entire command was.

---

### Post by The Producer on 2005-05-09
Wow, nice tutorial!  

Up until now i've never been able to bring up IE6 under WINE...amazing!

However, I have one problem:

```

err:module:import_dll Library OPENGL32.dll (which is needed by L"H:\\Applications\\anim8or\\anim8or.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\Applications\\anim8or\\anim8or.exe" failed, status c0000135

```

This happens when I try to run a Anim8or, a Windows 3D modeling program.
It's not a big program, only a few MBs.  And I had it running VERY well under Wine when I was using SuSE 9.2

OpenGL works fine however, according to glxinfo and glxgears.

Any ideas why this is happening?

---

### Post by notos on 2005-05-09
[QUOTE=Rehevkor]I followed the guide exactly and I get this in the terminal repeatedly when I try to run the base setup from winetools:
```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libindustrial.so",
```

The base setup won't open. It just keeps going back to the main menu. It appears that I have the same problem as Bashworth.

What gives? ](*,)[/QUOTE]

i ve found the problem is  bug with GTK module_path you have to change  you theme to "human" because GTK cant find libsomething in module path (altrought you have installed it look at synaptic)

mine was libsmooth :(

but i have it in

/usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so
/usr/lib/gtk-2.0/2.4.0/engines/libsmooth.la

---

### Post by quick_snack on 2005-05-09
When I use:
> This package here is for winetools, i'll explain this later on.

Code:

sudo apt-get install libgtk-1.2 libgtk-1.2-common

I get an error message that libgtk-1.2 is not found:
> familie@kajadamachine:~$ sudo apt-get install libgtk-1.2
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
E: Kon pakket libgtk-1.2 niet vinden


---

### Post by simianMiscreant on 2005-05-09
[QUOTE=notos]i ve found the problem is  bug with GTK module_path you have to change  you theme to "human" because GTK cant find libsomething in module path (altrought you have installed it look at synaptic)

mine was libsmooth :(

but i have it in

/usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so
/usr/lib/gtk-2.0/2.4.0/engines/libsmooth.la[/QUOTE]

so is there a way to install wine without switching theme to human?

---

### Post by Goober on 2005-05-10
Wow!  Great Tutorial!

I have done everything up until it comes to compiling the thing, with this line: 

```
./tools/wineinstall
```

When I put that in (Yes, I am in the correct folder), I get the following:

```
WINE Installer v0.74

Running configure...

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Configure failed, aborting install.

```

Any suggestions?  I am on Hoary 5.04, just upgraded from a newly installed Warty 4.10.

Awesome job though, I truly appreciate all the work you have done!

---

### Post by notos on 2005-05-10
just type  (in terminal)

apt-get install build-essential

> so is there a way to install wine without switching theme to human?

yep create a file in ~/ called .gtkrc and add the following lines 

```

include "/home/$USER/.gtkrc.mine"
module_path "/usr/lib/gtk-2.0/2.4.0/engines/"

```

also create .gtkrc.mine (empty) just to be sure all files are there :)

---

### Post by Goober on 2005-05-10
*sigh*

Ok, I ran into another problem.  I did this just fine:

```
./tools/wineinstall
```

However, at the end, it asks for my Root Password to complete Installation.  I enter my password.  But it says that it is invalid, so I cannot complete installation.  So my question is is the Root password different then the Password that I use to log in and stuff, and, if not, then what is going wrong?

---

### Post by notos on 2005-05-10
run the 

```
sudo make install 
```

OR activate the root user password

```
sudo passwd root
```
and re run the

./tool/wineintsall

---

### Post by qrazi on 2005-05-10
as i understand, Wine doesnt support directx, but wineX does support directX. and you can install WineX CVS for free. is it possible to install WineX CVS, if i already installed Wine CVS with WineTools?

---

### Post by AndreAPL on 2005-05-10
> configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.


still can't get it work  in amd64... got from sources..

---

### Post by Goober on 2005-05-10
Ok, I got Wine working, and, well, I'm loving it, not to sound cliche, lol.  

I do have one question.  How do I configure things to make Wine install things directly from the CDRom?  I know that to get things to install with Wine, you just type "wine whatever.exe" into the terminal, provided you are in the right folder.  Well, how do I get the Terminal to access the CDRom to install things with Wine?

I am currently trying to copy/paste all the contents into a Temperory Folder, but that just seems like a very cumbersome way to do things.

Thanks in advance for the answer :D

---

### Post by thegreatleslie on 2005-05-11
[QUOTE=Goober]Ok, I got Wine working, and, well, I'm loving it, not to sound cliche, lol.  

I do have one question.  How do I configure things to make Wine install things directly from the CDRom?  I know that to get things to install with Wine, you just type "wine whatever.exe" into the terminal, provided you are in the right folder.  Well, how do I get the Terminal to access the CDRom to install things with Wine?

I am currently trying to copy/paste all the contents into a Temperory Folder, but that just seems like a very cumbersome way to do things.

Thanks in advance for the answer :D[/QUOTE]

Why not just go to the directory on the CDROM to install it?  For instance, when I have a disk in my CDROM and it is mounted, I just do /media/cdrom0.  From there I can do wine autexec.exe, or whatever needs to be run.

If you don't know what your CDROM path is, open it up in nautilus or something and take note of it in the location bar.

---

### Post by Goober on 2005-05-11
Ok, so I put the CD in the Drive, it comes up on the screen, and you can see the files in it (I assume that is "Mounting" the CD).  I right-click on "SETUP.EXE", which installs whats on the CD, and click on "Open with 'Wine Windows Emulator'", and then it comes up with a Windows-looking Box that says "DemoShield Player" at the top, and it shows all my folders, just like when you are Browsing in Windows.  So I assume that I need to find a file to open to be able to use Wine to Install what is on the CD.  So where do I find the CD?

I can take a screenshot if needed.  Can I upload on this Site?

Oh, and what is "Nautilus"?

Thanks :)

---

### Post by foxy123 on 2005-05-11
[QUOTE=Goober]So I assume that I need to find a file to open to be able to use Wine to Install what is on the CD.  So where do I find the CD?

I can take a screenshot if needed.  Can I upload on this Site?

Oh, and what is "Nautilus"?

Thanks :)[/QUOTE]
I guess it should be mounted to your fake windows file system, somewhere in /home/user/.wine/, as I remember I found it there.

nautilus is a file manager in Gnome.

---

### Post by McQuaid on 2005-05-11
Hello, I was going to install wine via synaptic, what does this latest cvs bring to the table over the one in apt?

Also I wonder how often the one in apt will be updated?  I believe they just use the latest deb sid when it was made but not sure.

---

### Post by iogiuseppe on 2005-05-11
<rant>
I haven't tried any of the steps in this tutorial. "I'm not a patch or build it myself kind of guy." (to quote someone else here on the forums. 

I have, however, followed the directions posted on WineHQ perfectly and run into a problem getting the latest using SPM. If it's so easy for you all to build this via CVS, why can't I take what you've built via SPM and install it on my machine? 
</rant>

---

### Post by Goober on 2005-05-12
Ok, I have a picture of where I am having trouble figuring out what to do next, how to use Wine.  Here is the .exe that I want to run, and that Wine thingie is what comes up[ with I right-click the .exe, and clock "Open with 'Wine Windows Emulator'"

[img]http://img149.echo.cx/img149/3425/winepic5nn.gif[/img]

My question is what do i do next?  How do i use this to run .exe files?

---

### Post by simianMiscreant on 2005-05-12
[QUOTE=notos]just type  (in terminal)

apt-get install build-essential



yep create a file in ~/ called .gtkrc and add the following lines 

```

include "/home/$USER/.gtkrc.mine"
module_path "/usr/lib/gtk-2.0/2.4.0/engines/"

```

also create .gtkrc.mine (empty) just to be sure all files are there :)[/QUOTE]

didn't work for me.

---

### Post by notos on 2005-05-12
[QUOTE=simianMiscreant]didn't work for me.[/QUOTE]

may be you dont have lib"somthing".so in your modulle path
whats its the error are you geting

Gnome** bla bla bla libsomething.so

you can install then via synaptic just open it search for name of the lib or the like ;)
then install it

be sure to do save it in

/home/$user/.gtkrc

;)

jus what error do you get?

put it here and maybe we can help :)

---

### Post by simianMiscreant on 2005-05-12
it's missing libsmooth.so

libsmooth.so isn't a package in synaptic.

---

### Post by notos on 2005-05-13
```
sudo apt-get install gtk2-engines-smooth 
```

---

### Post by simianMiscreant on 2005-05-13
have it already

---

### Post by bored2k on 2005-05-13
I am a Cedega 4.3 user. I can't wait to test this WineCVS on my Steam account :D. I'll start using this howto.. after I'm done playing counterstrike LOL.

---

### Post by notos on 2005-05-13
[QUOTE=simianMiscreant]have it already[/QUOTE]

WTF?

are you using hoary?

contact me via Gaim maybe i can help you 
MSN,ICQ and Y! are in mi profile :)

---

### Post by Goober on 2005-05-13
Ok, I have good news!  I figured out how to use this.  Apparently you just type in "wine /media/cdrom0/Whatever.exe" to install things from a CD using Wine from a Terminal.  

Now, I get things to Install in my "C" Drive in the Wine Windows Emulator, and it puts the Icon  on my "Desktop" and "Program Files".   However, I cannot find the Icon for the Deskrtopn, and I am not sure how to run the program I installed.  Can anybody help?  I assume it is in my Windows Emulator, I am just not sure where to find it.

Thanks in advance, Goober.

---

### Post by foxy123 on 2005-05-14
great howto! I reinsatlled Ubuntu on my primary drive (eventually replaced my beloved SuSE) and the install worked great. I am even able to run OfficeXP, albeit with several problems. For example I cannot open files from apps. If I click File-Open in Excel, it gets frozen. The workaround is to type in console 

```
wine /PATH/excel.exe /PATH/file.xls
``` 

any way to make Open work in wine or it works only with crossover office?

---

### Post by brad.arth on 2005-05-14
[QUOTE=renderedbrian]Having trouble with this guide.

I'm running Ubuntu 5.04 AMD64, and I am trying to install wine.

However:

./tools/wineinstall
WINE Installer v0.74

Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.


What gives?

-- 
Brian[/QUOTE]

I too have this same error, running AMD64. Has anyone figured out a fix?

---

### Post by notos on 2005-05-15
[QUOTE=foxy123]great howto! I reinsatlled Ubuntu on my primary drive (eventually replaced my beloved SuSE) and the install worked great. I am even able to run OfficeXP, albeit with several problems. For example I cannot open files from apps. If I click File-Open in Excel, it gets frozen. The workaround is to type in console 

```
wine /PATH/excel.exe /PATH/file.xls
``` 

any way to make Open work in wine or it works only with crossover office?[/QUOTE]

well why use officeXP if you have openoffice ? if you want some thing paid use staroffice well there are a lot of options you can see also the corel wordperfect also paid or install something from repos 

but with openoffice you get all you may/can need ;)

Also CrossOver is the EZ way to go :) and you support Wine Project ;)

---

### Post by foxy123 on 2005-05-15
[QUOTE=notos]well why use officeXP if you have openoffice ? if you want some thing paid use staroffice well there are a lot of options you can see also the corel wordperfect also paid or install something from repos 

but with openoffice you get all you may/can need ;)

Also CrossOver is the EZ way to go :) and you support Wine Project ;)[/QUOTE]

OpenOffice suffices almost all my personal needs. The problem sometimes is compatibility. Some features from XP I need do not work in Ooo. So occasionally I need M$ Office.

I tried crossover office and it works fine. However since I do not need OfficeXP very often, I can live with dual boot for now. 

BTW, is it ok to have wine, crossover and cedega install together?

---

### Post by notos on 2005-05-15
yes i think there is no problem ;)

---

### Post by Oblivious Hazard on 2005-05-15
WINE Installer v0.74

Running configure...

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Configure failed, aborting install.



how do I fix this?

---

### Post by Sam on 2005-05-15
You need the compile tools !

```
$ sudo apt-get install build-essential
```

---

### Post by Oblivious Hazard on 2005-05-15
[QUOTE=Sam]You need the compile tools !

```
$ sudo apt-get install build-essential
```[/QUOTE]
 your awsome!

---

### Post by Oblivious Hazard on 2005-05-15
when I type wt2.... it says i dont have wine installed... even tho alll the setps befor worked fine and i had no errors....

---

### Post by Vin_L on 2005-05-25
Looks like a good procedure. Before I try it I would like to know if it will work with KDE running?

Thanks

---

### Post by questionasker on 2005-05-25
[QUOTE=Vin_L]Looks like a good procedure. Before I try it I would like to know if it will work with KDE running?

Thanks[/QUOTE]
 yeah, it is for me anyways...

im running kubuntu with KDE 3.4, and so far, it works as good as can be expected for something that isnt suposed to work... ;)
AIM beta works like a charm, so does IE 6 SP1...  (not that i use IE anymore...)

somehow though, ive got to figure out how to install MSN messenger... that would be the ultimate humiliation for /\/\$... :evil:

---

### Post by hardwarder on 2005-05-26
Whenever I run wt2, I get this on the terminal
```
Gdk-WARNING **: locale not supported by Xlib, locale set to C
```
When I click Base Setup, the menu disappears and appears again. It does that when I select an option from the menu.

Edit: Solved the problem by adding my locale to the /usr/X11R6/lib/X11/locale/locale.dir file.

---

### Post by seezar on 2005-05-28
Everything works fine for me up until I try to install DCOM98 then it errors out.

I get the following:

Parameters are
Choice is DCOM98 with checked=F
dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
grep: /home/greg/.wine/installed.reg: No such file or directory
grep: /home/greg/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/greg/.wine/installed.reg': No such file or directory
software installation verified by /home/greg/.wine/winetools.log
1229056
WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 127
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
Failed: 127




Any ideas?

---

### Post by ::DoGG:: on 2005-05-31
[QUOTE=AndreAPL]still can't get it work  in amd64... got from sources..[/QUOTE]

Figured that one out!!
1. Get the latest updates for binutils package from repo.
2. In shel type:
```
sudo export CC=gcc
```

That Worked.

---

### Post by Jesus Franco on 2005-05-31
WOW. How did this get past my dirty fingers!  :roll: 

Awesome man. No problems what-so-ever. CVS builds are alot faster than crossover office.  :razz:  :D And you can play games in wine. Just install direct x. You *might* need a patch that can be found [HERE](http://sourceforge.net/project/showfiles.php?group_id=134206&package_id=151214&release_id=324093) 
Make sure you apply it before compiling. Takes a bit of work but its worth it.  :)

---

### Post by quick_snack on 2005-05-31
[QUOTE=quick_snack]When I use:

apt-get install libgtk-1.2

I get an error message that libgtk-1.2 is not found:[/QUOTE]

BUMP. No one has an anwser?

---

### Post by boredinwichita on 2005-05-31
Okay, things were going great til I was trying to download from posters original site, then I get 
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net[204.127.198.24]:80... connected.
HTTP request sent, awaiting response... 404 Not found
14:08:48 ERROR 404: Not found.

any ideas?

---

### Post by AndyAWS on 2005-05-31
[QUOTE=quick_snack]BUMP. No one has an anwser?[/QUOTE]

Are you running apt-get as ```
sudo apt-get install libgtk-1.2

```?

Also try updating repositories first ```
sudo apt-get update
```
       
Or just search for libgtk in Synaptic and install through there.

---

### Post by quick_snack on 2005-05-31
I just found out that by using hoary libgtk1.2 was already installed. But apt-get **did** say libgtk1.2 was not found. Strange.
OK, I can go on now.

---

### Post by wellery on 2005-06-01
I get this error when I try to compile wine. It's really weird. It looks like a compiler error. It's a real worry when you crash the compiler.

mixer.c: In function `mixer_test_deviceW':
mixer.c:965: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[3]: *** [mixer.o] Error 1
make[3]: Leaving directory `/home/home/cvs/wine/dlls/winmm/tests'
make[2]: *** [tests] Error 2
make[2]: Leaving directory `/home/home/cvs/wine/dlls/winmm'
make[1]: *** [winmm] Error 2
make[1]: Leaving directory `/home/home/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

---

### Post by Orunitia on 2005-06-01
Your links will never go down? Riiiiiiiiiiiiiiight...


Sorry but this guide completely failed. Your links were down when I installed, and IE fails to install.

---

### Post by ::DoGG:: on 2005-06-02
Hey, guys, i got the error like this when try to compile that stuff :

```
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -D__i386__ -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:283: Error: `12(%esp)' is not a valid 64 bit base/index expression
{standard input}:284: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:285: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:286: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:294: Error: `12(%esp)' is not a valid 64 bit base/index expression
{standard input}:295: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:296: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:297: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:305: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:306: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:307: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:315: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:316: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:317: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:325: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:326: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:327: Error: `(%edx)' is not a valid 64 bit base/index expression
make[2]: *** [interlocked.o] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/mizer/cvs/wine/libs/port'
make[1]: *** [port] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/mizer/cvs/wine/libs'
make: *** [libs] B&#322;&#261;d 2
```

I`m using amd64 release and everything else compiled ok.. any clues ???

---

### Post by hammett111 on 2005-06-11
[QUOTE=renderedbrian]Having trouble with this guide.

I'm running Ubuntu 5.04 AMD64, and I am trying to install wine.

However:

./tools/wineinstall
WINE Installer v0.74

Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.


What gives?

-- 
Brian[/QUOTE]

Before typing ./tools/wineinstall type CC=gcc then ./tools/wineinstall, it tells the compiler what your c-compiler is

---

### Post by hammett111 on 2005-06-11
[QUOTE=quick_snack]BUMP. No one has an anwser?[/QUOTE]

Go back to the beginning of this thread, the libs are spelt wrong.

---

### Post by hammett111 on 2005-06-11
[QUOTE=AndreAPL]still can't get it work  in amd64... got from sources..[/QUOTE]
Dude type CC=gcc before typing ./configure

---

### Post by skierbri10 on 2005-06-11
Crud I get a file not found from your host.   [-X

---

### Post by Sav on 2005-06-11
[http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz)


This link works.

Please I need help with libsmooth.so.
I have all the gtk packages installed.
I haven't this dir:

/home/$user/.gtkrc

should I create it?

---

### Post by Sav on 2005-06-11
[QUOTE=Sav][http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz)


This link works.

Please I need help with libsmooth.so.
I have all the gtk packages installed.
I haven't this dir:

/home/$user/.gtkrc

should I create it?[/QUOTE]

Solved.
I just reinstalled all the gtk packages.

Now there is only one missing thing: the winfont package.

---

### Post by dikdik on 2005-06-16
can u help me?when i will compile i have this massage:

WINE Installer v0.74

You are running wineinstall as root, this is not advisable. Please rerun as a user.
Aborting.

 ](*,)

---

### Post by Vaego on 2005-06-17
Links are fixed, I had a user name change on my account so I had to fixy fixy and forgot to update the post ;)

---

### Post by Karl S. on 2005-06-17
Okay, total computer no-nothing, but I've followed your instructions, and they work, until I get to Winetools. I've tried to install IE SP1 many, many times, and it always fails. Any ideas why?

---

### Post by WetWilly on 2005-06-18
yeah, wtf, I also manage to start and everything, but when it comes to install internet explorer english for the first time it just goes into neverending loop. usually around 47%. pretty weird. and as I have seen 2 other people with the same problem there must be something strange...

For those of you that managed to install internet explorer, how much time did it take?

Update, heard someone in #winehq say that winetools doesnt work with the latest ver of wine...

---

### Post by TheRealEdwin on 2005-06-18
[QUOTE=Karl S.]Okay, total computer no-nothing, but I've followed your instructions, and they work, until I get to Winetools. I've tried to install IE SP1 many, many times, and it always fails. Any ideas why?[/QUOTE]
 I too can not get IE to install via wine tools. Freezes up at 44%. If WetWilly is correct what do we do?

---

### Post by dezgot on 2005-06-19
Same here, IE6 won't install, I even tried the French one but its sources must be the same.  If i cannot follow the tutorial I definitely won't figure this one (installing and configuring wine) out on my own.  Anyone get past this?  Are there other install tutorials that are not affected?  

I think microsoft is behind this... :-x

---

### Post by audie on 2005-06-19
Having the same issue with IE6. Has anyone figured this out ? So close.  ](*,) 
BTW - Awesome tutorial, and forum...

---

### Post by Wandering Wombat on 2005-06-19
All great until IE6 Install, same as above (previous posts) other than this prob, all has gone well!  ](*,) 

Please help.

---

### Post by xalphas on 2005-06-19
[QUOTE=seezar]Everything works fine for me up until I try to install DCOM98 then it errors out.

I get the following:

Parameters are
Choice is DCOM98 with checked=F
dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
grep: /home/greg/.wine/installed.reg: No such file or directory
grep: /home/greg/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/greg/.wine/installed.reg': No such file or directory
software installation verified by /home/greg/.wine/winetools.log
1229056
WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 127
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
Failed: 127

Any ideas?[/QUOTE]

Yep the same problem occured. I solved it by looking at the logs of make install. Here it says.
> *************************************************
The installed Wine libraries will not be found!
You can either:
   Add the line '/usr/local/lib' to /etc/ld.so.conf and run /sbin/ldconfig
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
*************************************************
************************************************* 

So i gedit /etc/ld.so.conf and add /usr/local/lib at the end of the file. Then sudo /sbin/ldconfig solves the problem. 

This howto is working very good. Just follow all the things and install wine but after for winetools use the new version. 

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz
```

Everything is working fine here. 

thx.

---

### Post by Karl S. on 2005-06-19
Well, for everyone who's having trouble with Explorer, my problem doesn't seem to be the same as yours. Mine doesn't hang. It just doesn't install. I get a 'Your installation seems to have failed' message. And, yes, I tried to French one too, and I would have tried German or Port. if I read those.

My problem is described [http://bugs.winehq.org/show_bug.cgi?id=2308](http://bugs.winehq.org/show_bug.cgi?id=2308).

This is what the final bit before it fails looks like:
--
err:setupapi:SetupDefaultQueueCallbackA delete error 2 "C:\\Windows\\inf\\ie5dom.inf" 
err:thunk:_loadthunk (commctrl.dll, Cctl1632_ThunkData16, comctl32.dll): Unable to load 
'commctrl.dll', error 2 
err:module:LdrInitializeThunk Main exe initialization for 
L"C:\\Windows\\msdownld.tmp\\AS003DF8.tmp\\acmsetup.exe" failed, status c0000142 
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH 
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO 
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH 
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO 
--
So, Wine is aware of this problem, and it seems to have hit with an earlier version of the product, too.

---

### Post by WetWilly on 2005-06-19
tried with the latest winetools.. but still freeze when installing IE6

```
downloading [http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe) to ie6setup.exe with 491768 bytes...
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
err:shell:SHGetFolderPathW Failed to create directory 'L"Z:\\home\\ivanox\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"Z:\\home\\ivanox\\Desktop"'.
err:ver:GetFileVersionInfoW Cannot access NE resource in L"C:\\windows\\msdownld.tmp\\AS050226.tmp\\w95inf16.dll"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\msdownld.tmp\\AS050226.tmp\\w95inf16.dll" -> "c:\\windows\\system\\w95inf16.dll"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "C:\\windows\\msdownld.tmp\\AS050226.tmp\\w95inf32.dll" -> "c:\\windows\\system\\w95inf32.dll"
err:vxd:VMM_VxDCall Using the native Win95 advapi32.dll is no longer supported.
err:vxd:VMM_VxDCall Please configure advapi32 to builtin.

```

Failed to create directory, I think that is the error... no idea how to fix it though  ](*,)

---

### Post by DooMRunneR on 2005-06-19
Looks like the WineCVS wont work on Ubuntu amd64.
```
{standard input}: Assembler messages:
{standard input}:283: Error: `12(%esp)' is not a valid 64 bit base/index express ion
{standard input}:284: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:285: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:286: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:294: Error: `12(%esp)' is not a valid 64 bit base/index express ion
{standard input}:295: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:296: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:297: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:305: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:306: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:307: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:315: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:316: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:317: Error: `(%edx)' is not a valid 64 bit base/index expressio n
{standard input}:325: Error: `8(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:326: Error: `4(%esp)' is not a valid 64 bit base/index expressi on
{standard input}:327: Error: `(%edx)' is not a valid 64 bit base/index expressio 
``` 

anyone have a clue?

---

### Post by Octane on 2005-06-19
I'm getting the same exact error as above -- looks like its a CVS problem..

---

### Post by Octane on 2005-06-19
[QUOTE=Octane]I'm getting the same exact error as above -- looks like its a CVS problem..[/QUOTE]
I just tried making the latest wine release, wine-20050524, and got the same exact errors.

---

### Post by cookiecaper on 2005-06-20
I'm getting the same error as well. Any help on this would be deeply appreciated, it is rather urgent.

---

### Post by dezgot on 2005-06-20
anyone found anything at all about getting IE6 installed?  extremely stuck.  
even tried 386 mode and downloading the IE6 temp files in windows then copying to ie6setup's folder in Ubuntu.  no luck

---

### Post by DopeyDan on 2005-06-23
Everything works great until I try INSTALLING IE6.0 SP1

Then I get a stream of these messages too fast (maybe dozens per second)

fixme:thunk:__regs_CommonUnimpStub generic stub: ?
fixme:thunk:__regs_CommonUnimpStub generic stub: ?
fixme:thunk:__regs_CommonUnimpStub generic stub: ?

... etc, you get the point ...

Then it stays at 47%.  I tried quitting and letting Setup try to recover, but it didn't make a difference.

Dan.

---

### Post by dezgot on 2005-06-24
Something must have been forgotten from the tutorial.  (where is the dude that wrote it?)

I'm pretty much gonna give up on this one.

---

### Post by sexycatsinhats on 2005-06-27
For all of you having trouble with installing internet explorer.. you can compile and use the 20050111 build. It works perfectly for me. Get it [here](ftp://ftp.ibiblio.org/pub/Linux/ALPHA/wine/development/Wine-20050111.tar.gz) .

---

### Post by homerglemkin on 2005-06-28
That worked for me.  
Thanks

---

### Post by xalphas on 2005-06-28
For all of you who could not success with internet explorer with latest cvs build wine 20050524 ;

Try this (It is the best for IE6) : [http://www.tatanka.com.br/ies4linux/index.html](http://www.tatanka.com.br/ies4linux/index.html)

That's just for internet explorer and doesn't create .wine or config for wine. It only creates it's own config and .ies4linux folder. That's it. Have ie with this. 

Then use winetools for other windows stuff. That would be better cause seperate configs and folders. 

regards

---

### Post by moment on 2005-06-29
[QUOTE=sexycatsinhats]For all of you having trouble with installing internet explorer.. you can compile and use the 20050111 build. It works perfectly for me. Get it [here](ftp://ftp.ibiblio.org/pub/Linux/ALPHA/wine/development/Wine-20050111.tar.gz) .[/QUOTE]

That worked for me! thanks very much!

---

### Post by Skel on 2005-07-02
I was unable to get cvs login got Conenction about check CVSROOT i dont know.... but when i ghet this install can i install my printer driver under wine  :)

---

### Post by Zaare on 2005-07-02
Trying to follow this howto, I've run into a problem. When I run wineinstall I get the following error:
> /sbin/ldconfig: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
I don't have root password, so during the wineinstall when I was asked for root password, I did as someone had suggested in this thread: I hit enter twice to cancel and  ran the command it was trying to run with sudo:
```

sudo make install;echo /usr/local/lib>>/etc/ld.so.conf;/sbin/ldconfig

```
And that's when I get the "permission denied"-message.
Does anyone know why I'm getting this error, and what can I do about it?

---

### Post by Octane on 2005-07-02
Still can't figure it out with AMD64 -- is it even possible?

I have tried:
setting CC="gcc-3.4 -m32" 
setting CC="gcc -m32"
setting CC="gcc"
and setting CC="gcc3.4"

none of these work. I either get an error during configue:
```
checking for gcc... gcc-3.4 -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
```
or 
during an error during make:
```
gcc-3.4 -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -D__i386__ -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:223: Error: `12(%esp)' is not a valid 64 bit base/index expression
{standard input}:224: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:225: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:226: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:234: Error: `12(%esp)' is not a valid 64 bit base/index expression
{standard input}:235: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:236: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:237: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:245: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:246: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:247: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:255: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:256: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:257: Error: `(%edx)' is not a valid 64 bit base/index expression
{standard input}:265: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:266: Error: `4(%esp)' is not a valid 64 bit base/index expression
{standard input}:267: Error: `(%edx)' is not a valid 64 bit base/index expression
make[2]: *** [interlocked.o] Error 1
make[2]: Leaving directory `/home/dan/cvs/wine/libs/port'
make[1]: *** [port] Error 2
make[1]: Leaving directory `/home/dan/cvs/wine/libs'
make: *** [libs] Error 2
```
Any help would be appreciated.

---

### Post by thingy on 2005-07-02
Hi,

From this link: [http://www.winehq.com/hypermail/wine-devel/2004/08/0470.html](http://www.winehq.com/hypermail/wine-devel/2004/08/0470.html)

and this one:

[http://lists.debian.org/debian-amd64/2004/08/msg00087.html](http://lists.debian.org/debian-amd64/2004/08/msg00087.html)

I tried this: (after installing the package ia32-libs-dev as well as gcc-3.4)

```

LD="ld -m elf_i386" CC="gcc-3.4 -m32" AS="gcc-3.4 -c -m32" ./WineCVS.sh

``` 

and I do get pretty far in the build (the configure/make depend all work), but it all falls apart when the linker tries to link Wine against libX11 and other X libs.

It's a bug that the ia32-libs pkg has 32bit X11 libs, but the ia32-libs-dev package doesn't have the 32bit X11 development files. I mean, it has the dev files for all the other libs in ia32-libs except the x11 ones.

This is why I'm stuck! :-(

I've given up on this now...Unless you compile Wine in a chroot environment it's not going to work.

One last thing I came across was this:

In the /usr/share/doc/ia32-libs/README.Debian file, it says:

> If more libraries are needed, file wishlist severity bugs against
amd64-libs in the Debian bug tracking system at bugs.debian.org and
we'll try to oblige.  For a quick fix, you can download the amd64-libs
source package, add the debs in the "update-packages" file and rebuild
and install the package locally with:

        apt-get install devscripts fakeroot build-essential
        apt-get build-dep amd64-libs
        debuild -us -uc
        dpkg -i ../amd64-libs*deb

The above offers the chance for oneself to build the missing libs, which are ofcourse the dependancies of xlibs-dev package.

I'm not brave enough to do this...I've put too much effort into this box to risk hosing it. I'll try and file a bug tomorrow regarding the ia32-libs-dev package, but I doubt it will get fixed in time for breezy.

---

### Post by DonVla on 2005-07-02
great howto!!!

but a question:

how can i uninstall wine ?
is there a special way or can i can only remove the /usr/local/bin entries and the /usr/local/lib/wine directory?

thank you

---

### Post by geearf on 2005-07-05
try make uninstall in the wine rep, where you made make install.

---

### Post by Sav on 2005-07-05
I tried the winehq repositories.
All was perfect, plus winetools downloaded the fonts without any hang.

It's not the last version, but is simple and fast.

---

### Post by DW5 on 2005-07-07
> **xalphas]For all of you who could not success with internet explorer with latest cvs build wine 20050524  said:**
> http://www.tatanka.com.br/ies4linux/index.html[/url]

That's just for internet explorer and doesn't create .wine or config for wine. It only creates it's own config and .ies4linux folder. That's it. Have ie with this. 

Then use winetools for other windows stuff. That would be better cause seperate configs and folders. 

regards

I downloaded IES4Linux and it starts an edition of ie6, and it works fine but it won't browse to the one set of webpages I need it to. 

I'm a university prof working at a small school that has an online advising program that works only with IE6 (built on Foxpro I think).  Anyway, I only need that prog out of windows and want an easy solution.

Can anyone using ies4linux get something to come up for my.snu.edu?

Thanks.

---

### Post by jstrubberg on 2005-07-16
Running into trouble getting DCOM98 installed.  Can't go any farther until this wall comes down.



dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
grep: /home/jstrubberg/.wine/installed.reg: No such file or directory
grep: /home/jstrubberg/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/jstrubberg/.wine/installed.reg': No such file or directory
software installation verified by /home/jstrubberg/.wine/winetools.log
1229056
WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 127
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
Failed: 127



Any ideas?

---

### Post by DonVla on 2005-07-20
[QUOTE=Sav]I tried the winehq repositories.
All was perfect, plus winetools downloaded the fonts without any hang.

It's not the last version, but is simple and fast.[/QUOTE]

here are the winehq debian/ubuntu repos:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

i did it like they told there, and everything worked fine. wine/dvdshrink works without any problems.

---

### Post by tanix on 2005-07-20
hey i am at the point where you base install winetools....ok i try to install ie6 english but when it gets to the part where it starts to download it it doesnt connect to server...it says connect to internet or try again later...i have tryed over the course of a few days and i cannot get past this point, i need help

---

### Post by geearf on 2005-07-20
do you need a proxy, or anything like that to connect to the net ?

---

### Post by tanix on 2005-07-20
yeah... if you mean i am going through a router, then ya

here is some code from the terminal on whats happening

```

software installation verified by /home/takayuki/.wine/winetools.log
496888
downloading http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe to ie6setup.exe with 491768 bytes...
WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.WIN" "Options.WIN" "InstallDir" 0x10253f8 260 0x7b98f830 (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stubsoftware installation verified by /home/takayuki/.wine/winetools.log
496888
downloading http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe to ie6setup.exe with 491768 bytes...
WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.WIN" "Options.WIN" "InstallDir" 0x10253f8 260 0x7b98f830 (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "IE4Setup.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:ExecuteCab ((nil) 0x7b98f9e8 (nil)): stub

fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "IE4Setup.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:ExecuteCab ((nil) 0x7b98f9e8 (nil)): stub

```

---

### Post by DonVla on 2005-07-20
as i remember i also got problems with ie 6, but i think (it's three weeks ago) i didn't install it at all (no it's not installed).
you don't really need everything what's in the base install (you need the fake drive and the fonts). wine says that you cannot install system software without ie6, but that's not true. the windows installer worked.
i only use wine for dvdshrink and it works. 
what do you need wine for?

vlad

---

### Post by tanix on 2005-07-20
I am mainly using it for ps7...

---

### Post by DonVla on 2005-07-20
[QUOTE=tanix]I am mainly using it for ps7...[/QUOTE]


than i try to apt-get install it from here:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

and install only the mandatory things: the fake drive, dcom, the fonts and the windows installer.
then try to run ps. wine uses the your default system browser (eg firefox). 
i haven't tried ps, but perhaps it works this way.

---

### Post by tanix on 2005-07-20
I am relativly new to linux, can you tell me how to uninstall all this stuff i have installed so far? heres what i did...on the desktop to remove dir...went to places, then went to computers, then went you home, then del cvs dir and wine tools dir...will that uninstall everything?

---

### Post by DonVla on 2005-07-20
[QUOTE=tanix]I am relativly new to linux, can you tell me how to uninstall all this stuff i have installed so far? heres what i did...on the desktop to remove dir...went to places, then went to computers, then went you home, then del cvs dir and wine tools dir...will that uninstall everything?[/QUOTE]

i don't really understand what you did, but here's what i'll do:

go to the winetools and wine cvs directory and then "make uninstall" in both . then you can delete the directories. it's not a big problem, if you already deleted the directories. untar the wine and winetools tar.gz again, change to the untared directories, then "./configure" and "make" again, and then "make uninstall" (not "make install").

then edit your sources.list like it's described on the winehq site etc ...

---

### Post by tanix on 2005-07-20
well, i have decided to try symantic...here is what i have done

installed wine, wine tools, libwine (with symantic)

after they were installed i went to terminal and typed in "winetools"

winetool gui comes up okay

i go to base tools

i installe fake windows then i install dcom98, then i try to install ie 6, it brings up "intialize setup" screen and then it closes with an error box 

error box title="windows update: internet exploerer and internet tools" 

content="setup was unable to download req. components, please make sure you are connected to the internet (i am), or try to run set up again later"

options="okay; help" i click okay

then another box comes up


box title="wine status"

content="it seems that installation has failed (well no ----)"

options="okay" i click okay and it brings me back to winetools base set-up screen


i think i need ie6 cuz i tryed to install windows system software but it wouldnt let me because it depends on ie6

does this happen to anyone else, or am i just retarted? lol

please feel free to help me :)

---

### Post by DonVla on 2005-07-20
ok, try now to install the windows-programs you want (ps7) without the windows system tools. forget about ie6... look if it works.
and don't forget the fonts...

---

### Post by tanix on 2005-07-20
I try what you say don and nothing will install it says it's dependent on microsoft internet explorer...maybe i am screwed

---

### Post by DonVla on 2005-07-20
[QUOTE=tanix]I try what you say don and nothing will install it says it's dependent on microsoft internet explorer...maybe i am screwed[/QUOTE]


what have you tried to install, photoshop?

---

### Post by tanix on 2005-07-20
i am gonna try something really fast...i am gonna disconnect my router and make a direct connection.

---

### Post by DonVla on 2005-07-20
[QUOTE=tanix]i am gonna try something really fast...i am gonna disconnect my router and make a direct connection.[/QUOTE]

i guess wine is now installed (maybe without ie6).
put your photoshop cd in your cdrom drive.
then you mount your cdrom drive.
then you cd /media/cdrom
and type> wine setup.exe 

from here on the windows installing wizard starts and you can install the program where you want on your fake c_drive. 
to start photoshop type : wine  ~/.wine/c_drive/[whereinstalled]/ps(or_how_its_called).exe

---

### Post by tanix on 2005-07-20
i think it should work...thank you for supporting...if i have any other problems i guess i will bump this topic with it :)

---

### Post by DonVla on 2005-07-20
your internet connection works. you installed dcom...

---

### Post by tanix on 2005-07-20
my internet connection is awesome, whats weird is wheni try to install some fonts with wine tools...the download will sit at 0%, may ps7 will run w/o these fonts, it should be okay i think

---

### Post by DonVla on 2005-07-20
try to install photoshop only with the settings you have now and post here what happened. i described above what to do.

and you can get the fonts from here

> wget [http://home.comcast.net/~themachinez/wine/fonts/winfonts.tar.gz](http://home.comcast.net/~themachinez/wine/fonts/winfonts.tar.gz) 

look at the beginning of  this thread how to do this (  5) Installing Windows Fonts).

vlad

---

### Post by mcescher on 2005-07-21
Ok...here goes. I have followed the guide and performed all of the steps with no hang-ups....except one.  ](*,) 

After the installation of wine and wine-tools I run the command "wt2" and wine-tools gui comes up. I agree to all the promps and end up at the menu with all of the options to select "Base Set-up", "Install Windows Software"...etc

My problem occurs when I try to select one of these options. The gui disappears for a second then re-appears in the same state. It doesn't open anything or give me any options. It does the same thing for every single selection whether I double-click or scroll and hit enter.

Any ideas?

Also, what would be a good program to try and install that is known to work with wine.  I have tried iTunes.exe and it returns errors saying it can only be installed on Winblows machines.

```
nick@Home:~/Desktop$ wine iTunesSetup.exe
fixme:msi:MsiGetProductInfoW L"{47808F78-F178-49DC-B708-15FE538B16FF}" L"PackageCode" 0x7bc7dd80 0x7b99d87c
fixme:msi:MsiInstallProductW L"C:\\windows\\temp\\_is854\\ISScript8.Msi" L"REBOOT=ReallySuppress ADDLOCAL=All"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"SelfUnregModules"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"RemoveFiles"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"MoveFiles"
fixme:msi:ACTION_InstallFiles Write DiskPrompt
err:msi:ITERATE_DuplicateFiles Failed to copy file L"c:\\Program Files\\Common F iles\\InstallShield\\Driver\\8\\Intel 32\\IDriver.exe" -> L"c:\\Program Files\\Common Files\\InstallShield\\Driver\\8\\Intel 32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"RemoveFolders"
```

---

### Post by hyrican on 2005-07-22
When I follow the How-To guide, the process runs smoothly until I try to install the "Windows Installer" from Winetools. The error is "The installer has insufficient privaledges to modify the file: C:\Config.Msi\bea.rbf."

Any pointers?

---

### Post by benplaut on 2005-07-22
hmm... Internet Explorer keeps failing...

i tried the "ies4lin" (or whatever it's called), and it worked, but wine/winetools doesn't acknowledge that it's there.

will a direct connection (no router) help?

<<edit>>

maybe i should read the thread first  :roll: 


20050111 works just fine!  :grin:

---

### Post by NightwishFreak on 2005-07-23
[QUOTE=jonny]
5. Before running wineinstall, I had to backup one file: sudo mv /usr/X11R6/lib/libGL.a /usr/X11R6/lib/libGL.a.old[/QUOTE]

i had the same problem when i ran wine install. any idea what moving that file does to the system?

---

### Post by NightwishFreak on 2005-07-23
```
Compiling WINE. Grab a lunch or two, rent a video, or whatever,
in the meantime...

make[1]: Entering directory `/home/robert/cvs/wine/libs'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/robert/cvs/wine/libs'
make: *** [libs] Error 2
make[1]: Entering directory `/home/robert/cvs/wine/libs'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/robert/cvs/wine/libs'
make: *** [libs] Error 2

Compilation failed, aborting install.
```

the makefile is there and i have full ownership over everything. why doesnt it find it? any help would be appreciated.

---

### Post by lyricmuse on 2005-07-25
I just wanted to say thank you to the writer of this How To. Excellent!!! I wanted to install Photoshop 7 only because I'm used to it. I'll figure Gimp out eventually. I'm installing Photoshop 7 as I write this.

Thank you\\:D/

---

### Post by zarathustra on 2005-07-25
[QUOTE=][/QUOTE]
 I managed to get Winetools to install IE6 by forcing Synaptic to install the version from the backports. I had similar problems mentioned by using the one from Wine's repositories.

---

### Post by zarathustra on 2005-07-25
[QUOTE=][/QUOTE]
 Although now I can't install the Windows installer because "installer has insufficient priveledges" :?

---

### Post by Statik on 2005-07-25
Just followed through these instructions tonight. Here's the errors I got at the install phase:
> gcc -c -I. -I. -I../../../include -I../../../include    -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o edit.o edit.c
edit.c: In function `test_edit_control_1':
edit.c:432: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[3]: *** [edit.o] Error 1
make[3]: Leaving directory `/home/statik/cvs/wine/dlls/user/tests'
make[2]: *** [tests] Error 2
make[2]: Leaving directory `/home/statik/cvs/wine/dlls/user'
make[1]: *** [user] Error 2
make[1]: Leaving directory `/home/statik/cvs/wine/dlls'
make: *** [dlls] Error 2 

Any ideas? Help appreciated

Statik

---

### Post by Baci on 2005-07-27
When trying to download IE it says you are unable to download IE at the time, please try setup again later. I have dcom installed already, the exact error:

"Setup was unable to download the required components. Please make sure you are connected to the Internet, or try to run Setup again later.

I know my internet is working, even on that machine, i just installed dcom, I assume the server that it is pointing to no longer has the files, and being my newbish self, need a complete walkthrough on how to get them.

---

### Post by Baci on 2005-07-27
I have tried going to the microsoft site, downloading ie6setup.exe by hand, and then going into terminal and typing: wine /home/baci/Desktop/ie6setup.exe and it still has the same error. Perhaphs it is with the microsoft website where the problem is?


<-------Linux Newber, 2 days & counting =p

---

### Post by vkkim on 2005-07-28
[QUOTE=Baci]When trying to download IE it says you are unable to download IE at the time, please try setup again later. I have dcom installed already, the exact error:

"Setup was unable to download the required components. Please make sure you are connected to the Internet, or try to run Setup again later.

I know my internet is working, even on that machine, i just installed dcom, I assume the server that it is pointing to no longer has the files, and being my newbish self, need a complete walkthrough on how to get them.[/QUOTE]

The same thing happens to me, and I know my network connecting is working here too.

---

### Post by Baci on 2005-07-28
sigh... I really need someone that has msn/aim to help me, I have alot of questions in sevral forums that never seem to get awnsered

---

### Post by Statik on 2005-07-29
Tried doing the WineXCVS install, and I'm getting this error now:
> desktop.c: In function `GetDisplayModeCount':
desktop.c:179: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:179: error: (Each undeclared identifier is reported only once
desktop.c:179: error: for each function it appears in.)
desktop.c:186: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c: In function `GetRealMode':
desktop.c:196: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:199: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c: In function `X11DRV_EnumDisplayModes':
desktop.c:217: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:239: warning: implicit declaration of function `X11DRV_XF86VM_GetCurrentMode'
desktop.c:256: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c: In function `X11DRV_ChangeDisplayMode':
desktop.c:285: error: `xf86vm_allow_mode_changes' undeclared (first use in this function)
desktop.c:317: error: `xf86vm_mode_count' undeclared (first use in this function)
desktop.c:319: error: `xf86vm_modes' undeclared (first use in this function)
desktop.c:356: warning: implicit declaration of function `X11DRV_XF86VM_SetCurrentMode'
make[2]: *** [desktop.o] Error 1
make[2]: Leaving directory `/root/temp/winex-stable/winex/dlls/x11drv'
make[1]: *** [x11drv/libx11drv.so] Error 2
make[1]: Leaving directory `/root/temp/winex-stable/winex/dlls'
make: *** [dlls] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: GetWineX.sh) 

The only other main error I seem to get tells me that GCC is out of date, but I seem to have the most recent GCC?

Statik

---

### Post by Skel on 2005-07-29
root@ubuntu:/home/skel/temp/winetools # sudo sh install.sh
Installing WineTools to /usr/local/winetools...
Installing translations...
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt2.mo
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt2.mo
Start WineTools as *normal* user with "wt2". Don't use as root!


I get this error but when i do it as normal user i get U need to be root "wtf" ](*,)

---

### Post by Jaivaz on 2005-07-30
I'm having a problem. I get to the part of installing things through winetools. I get the following while using winetools:

> horace@Ubuntu:~/cvs/wine $ wt2
found gettext in /usr/bin
Browser is /usr/bin/firefox.
detecting Wine version... done.
Drive C: is /home/horace/.wine/drive_c
Wine Warning: could not find DOS drive for current working directory '/home/horace/cvs/wine', starting in the Windows directory.
20050725
wine is executed as wine
Parameters are --noexit
/usr/local/bin/wt2: line 2568: [: too many arguments
/usr/local/bin/wt2: line 2568: [: too many arguments
Version of Wine is OK.
Calls to wine are executed as wine.
Config is /home/horace/.wine/winetools.log.
CDROM is /cdrom.
Choice is Base setup
Choice is Create a fake Windows drive with checked=F
waiting for wineservers to exit...
 
The "wineservers" then never exit.

---

### Post by gn0me on 2005-08-01
Very helpful! Thank you very much!

---

### Post by arunsub on 2005-08-01
In file included from compare.c:38:
winldap_private.h:125: warning: `struct berval' declared inside parameter list
winldap_private.h:125: warning: its scope is only this definition or declaration, which is probably not what you want
winldap_private.h:126: warning: `struct berval' declared inside parameter list
winldap_private.h:127: warning: `struct berval' declared inside parameter list
winldap_private.h:128: warning: `struct berval' declared inside parameter list
compare.c:119: warning: `struct berval' declared inside parameter list
compare.c:120: error: conflicting types for `ldap_compare_extA'
winldap_private.h:125: error: previous declaration of `ldap_compare_extA'
compare.c:170: warning: `struct berval' declared inside parameter list
compare.c:171: error: conflicting types for `ldap_compare_extW'
winldap_private.h:126: error: previous declaration of `ldap_compare_extW'
compare.c:227: warning: `struct berval' declared inside parameter list
compare.c:228: error: conflicting types for `ldap_compare_ext_sA'
winldap_private.h:127: error: previous declaration of `ldap_compare_ext_sA'
compare.c:277: warning: `struct berval' declared inside parameter list
compare.c:278: error: conflicting types for `ldap_compare_ext_sW'
winldap_private.h:128: error: previous declaration of `ldap_compare_ext_sW'
make[2]: *** [compare.o] Error 1
make[2]: Leaving directory `/home/prabha/cvs/wine/dlls/wldap32'
make[1]: *** [wldap32] Error 2
make[1]: Leaving directory `/home/prabha/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

Help please!!!  ](*,)

---

### Post by High Roller on 2005-08-01
I just got the same error so I guess something is being updated on the CVS?

*shrugs*

Oh well...  will try again later I suppose :)

---

### Post by cullan on 2005-08-04
I get this error message when trying to compile wine.  It looks like maybe I am missing an xml library or something but I am not really sure.

```
make[2]: Entering directory `/home/cullan/cvs/wine/dlls/msxml3'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o element.o element.c
element.c:45: error: syntax error before "xmlDocPtr"
element.c:45: warning: no semicolon at end of struct or union
element.c:46: warning: type defaults to `int' in declaration of `domelem'
element.c:46: warning: data definition has no type or storage class
element.c:48: error: syntax error before '*' token
element.c:49: warning: return type defaults to `int'
element.c: In function `impl_from_IXMLDOMElement':
element.c:50: error: syntax error before ')' token
element.c:50: error: syntax error before ')' token
element.c: In function `domelem_AddRef':
element.c:78: error: `This' undeclared (first use in this function)
element.c:78: error: (Each undeclared identifier is reported only once
element.c:78: error: for each function it appears in.)
element.c: In function `domelem_Release':
element.c:85: error: `This' undeclared (first use in this function)
element.c: At top level:
element.c:553: error: syntax error before "xmlDocPtr"
element.c: In function `DOMElement_create':
element.c:555: error: `elem' undeclared (first use in this function)
element.c:562: error: `xmldoc' undeclared (first use in this function)
element.c:565: error: `DOMElement' undeclared (first use in this function)
make[2]: *** [element.o] Error 1
make[2]: Leaving directory `/home/cullan/cvs/wine/dlls/msxml3'
make[1]: *** [msxml3] Error 2
make[1]: Leaving directory `/home/cullan/cvs/wine/dlls'
make: *** [dlls] Error 2
```

---

### Post by alvari on 2005-08-04
[QUOTE=cullan]I get this error message when trying to compile wine.  It looks like maybe I am missing an xml library or something but I am not really sure.

```
make[2]: Entering directory `/home/cullan/cvs/wine/dlls/msxml3'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o element.o element.c
element.c:45: error: syntax error before "xmlDocPtr"
element.c:45: warning: no semicolon at end of struct or union
element.c:46: warning: type defaults to `int' in declaration of `domelem'
element.c:46: warning: data definition has no type or storage class
element.c:48: error: syntax error before '*' token
element.c:49: warning: return type defaults to `int'
element.c: In function `impl_from_IXMLDOMElement':
element.c:50: error: syntax error before ')' token
element.c:50: error: syntax error before ')' token
element.c: In function `domelem_AddRef':
element.c:78: error: `This' undeclared (first use in this function)
element.c:78: error: (Each undeclared identifier is reported only once
element.c:78: error: for each function it appears in.)
element.c: In function `domelem_Release':
element.c:85: error: `This' undeclared (first use in this function)
element.c: At top level:
element.c:553: error: syntax error before "xmlDocPtr"
element.c: In function `DOMElement_create':
element.c:555: error: `elem' undeclared (first use in this function)
element.c:562: error: `xmldoc' undeclared (first use in this function)
element.c:565: error: `DOMElement' undeclared (first use in this function)
make[2]: *** [element.o] Error 1
make[2]: Leaving directory `/home/cullan/cvs/wine/dlls/msxml3'
make[1]: *** [msxml3] Error 2
make[1]: Leaving directory `/home/cullan/cvs/wine/dlls'
make: *** [dlls] Error 2
```[/QUOTE]


I'm having this problemo too.. All help appreciated!

---

### Post by domesticatewhat on 2005-08-04
[QUOTE=Baci]When trying to download IE it says you are unable to download IE at the time, please try setup again later. I have dcom installed already, the exact error:

"Setup was unable to download the required components. Please make sure you are connected to the Internet, or try to run Setup again later.

I know my internet is working, even on that machine, i just installed dcom, I assume the server that it is pointing to no longer has the files, and being my newbish self, need a complete walkthrough on how to get them.[/QUOTE]

Use this [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)  program instead of winetools for the latest CVS version of wine. It installed IE fine.

---

### Post by kiwi_bloke on 2005-08-06
Similar problem installing wine. I'm using Kubuntu 5.04, kernel 2.6.10.5-k7. The installation aborts with:

make[2]: Leaving directory `/home/don/cvs/wine/dlls/mswsock'
make[2]: Entering directory `/home/don/cvs/wine/dlls/msxml3'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o element.o element.c
element.c:45: error: syntax error before "xmlDocPtr"
element.c:45: warning: no semicolon at end of struct or union
element.c:46: warning: type defaults to `int' in declaration of `domelem'
element.c:46: warning: data definition has no type or storage class
element.c:48: error: syntax error before '*' token
element.c:49: warning: return type defaults to `int'
element.c: In function `impl_from_IXMLDOMElement':
element.c:50: error: syntax error before ')' token
element.c:50: error: syntax error before ')' token
element.c: In function `domelem_AddRef':
element.c:78: error: `This' undeclared (first use in this function)
element.c:78: error: (Each undeclared identifier is reported only once
element.c:78: error: for each function it appears in.)
element.c: In function `domelem_Release':
element.c:85: error: `This' undeclared (first use in this function)
element.c: At top level:
element.c:553: error: syntax error before "xmlDocPtr"
element.c: In function `DOMElement_create':
element.c:555: error: `elem' undeclared (first use in this function)
element.c:562: error: `xmldoc' undeclared (first use in this function)
element.c:565: error: `DOMElement' undeclared (first use in this function)
make[2]: *** [element.o] Error 1
make[2]: Leaving directory `/home/don/cvs/wine/dlls/msxml3'
make[1]: *** [msxml3] Error 2
make[1]: Leaving directory `/home/don/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

I'm lost here, having 'upgraded' from Windows 98SE just a couple of weeks ago. Hoping for help, ideas . . .
:)

---

### Post by eprivett on 2005-08-06
I was having the same difficulty as everyone else with compiling the current version of Wine.  What I ended up doing to get things rolling was load the latest BINARY version from Synaptic (20050419) which saved me from having to compile the beast.  Once that was done, everything seemed to be working until I tried to install ie6 with Wine Tools 2.1.1.  It would hang on install and would not download.  I reinstalled all the fonts as in this HOWTO first, and then reinstalled the windows installer via wt2 and ie6 downloaded and installed just fine.  I don't know if this is the cure for the ie6 download problem, but it did work for me.

---

### Post by Octane on 2005-08-07
[QUOTE=kiwi_bloke]Similar problem installing wine. I'm using Kubuntu 5.04, kernel 2.6.10.5-k7. The installation aborts with:

make[2]: Leaving directory `/home/don/cvs/wine/dlls/mswsock'
make[2]: Entering directory `/home/don/cvs/wine/dlls/msxml3'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -o element.o element.c
element.c:45: error: syntax error before "xmlDocPtr"
element.c:45: warning: no semicolon at end of struct or union
element.c:46: warning: type defaults to `int' in declaration of `domelem'
element.c:46: warning: data definition has no type or storage class
element.c:48: error: syntax error before '*' token
element.c:49: warning: return type defaults to `int'
element.c: In function `impl_from_IXMLDOMElement':
element.c:50: error: syntax error before ')' token
element.c:50: error: syntax error before ')' token
element.c: In function `domelem_AddRef':
element.c:78: error: `This' undeclared (first use in this function)
element.c:78: error: (Each undeclared identifier is reported only once
element.c:78: error: for each function it appears in.)
element.c: In function `domelem_Release':
element.c:85: error: `This' undeclared (first use in this function)
element.c: At top level:
element.c:553: error: syntax error before "xmlDocPtr"
element.c: In function `DOMElement_create':
element.c:555: error: `elem' undeclared (first use in this function)
element.c:562: error: `xmldoc' undeclared (first use in this function)
element.c:565: error: `DOMElement' undeclared (first use in this function)
make[2]: *** [element.o] Error 1
make[2]: Leaving directory `/home/don/cvs/wine/dlls/msxml3'
make[1]: *** [msxml3] Error 2
make[1]: Leaving directory `/home/don/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

I'm lost here, having 'upgraded' from Windows 98SE just a couple of weeks ago. Hoping for help, ideas . . .
:)[/QUOTE]
Hi, just add deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ and apt-get install wine (after an update)

---

### Post by kiwi_bloke on 2005-08-07
[QUOTE=Octane]Hi, just add deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ and apt-get install wine (after an update)[/QUOTE]
 Hey, thanks for the advice:
------------------------------------
Hi, just add deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ and apt-get install wine (after an update)
-----------------------------------

Some (not too dumb, I hope) questions before I do that:
1) Should I uninstall what I've done first? With 'sudo make uninstall wine' in /cvs?
2) Do I uninstall all the other pre-requisite stuff I installed according to the Howto earlier in this thread?
3) Will this install 'Winetools" or is that a separate installation?

---

### Post by Octane on 2005-08-07
[QUOTE=kiwi_bloke]Some (not too dumb, I hope) questions before I do that:
1) Should I uninstall what I've done first? With 'sudo make uninstall wine' in /cvs?
2) Do I uninstall all the other pre-requisite stuff I installed according to the Howto earlier in this thread?
3) Will this install 'Winetools" or is that a separate installation?[/QUOTE]
Here is exactly wha tI Did (still not working cuz IE6 gives me errors though)

0) uninstall all wine-related stuff
1) Add deb "http://wine.sourceforge.net/apt/ binary/" to sources.list
2) update apt
3) install wine
4) comment it out
5) Add "deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted" and "deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted" to sources.list
6) update apt
7) install winetools
8) comment out step 5 repos once file time & uncomment step 1 repo
9) apt update
10) install libwine and upgrade apt-get

---

### Post by kiwi_bloke on 2005-08-07
[QUOTE=Octane]Here is exactly wha tI Did (still not working cuz IE6 gives me errors though)

0) uninstall all wine-related stuff
1) Add deb "http://wine.sourceforge.net/apt/ binary/" to sources.list
2) update apt
3) install wine
4) comment it out
5) Add "deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted" and "deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted" to sources.list
6) update apt
7) install winetools
8) comment out step 5 repos once file time & uncomment step 1 repo
9) apt update
10) install libwine and upgrade apt-get[/QUOTE]

Hey, Octane
Thanks for the support. I uninstalled/undid what I had and had already completed your steps 1 - 4 independently. Didn't know anything about the reference in step 5. Instead I went to Winetools home page [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/) , downloaded and installed the tar.gz - a first time experience!

I too am getting IE6 non-installation problems. I note the Winetools homepage recommends "The actual version wt212jo work with Wine versions 20040914, 20041019, 20041201 and 20050111. I definitely recommend using 20041019." So when I get time, I might uninstall my current version of wine and install version 20041019 from [http://prdownloads.sourceforge.net/wine](http://prdownloads.sourceforge.net/wine) . Not looking forward to it tho, I too inexperienced at linux/Ubuntu.

But I'll be back.

---

### Post by Cameroon Loser on 2005-08-08
```
sudo apt-get install libgtk-1.2 libgtk-1.2-common
```

Couldn't find libgtk-1.2. Anybody else having trouble with this?

---

### Post by kiwi_bloke on 2005-08-09
[QUOTE=Cameroon Loser]```
sudo apt-get install libgtk-1.2 libgtk-1.2-common
```

Couldn't find libgtk-1.2. Anybody else having trouble with this?[/QUOTE]


As I remember the names are incorrectly spelt, I think you should omit the hyphen.

---

### Post by DonVla on 2005-08-11
a thread/ howto i found about ie6:
[http://forums.gentoo.org/viewtopic-t-148168-highlight-media.html](http://forums.gentoo.org/viewtopic-t-148168-highlight-media.html)

perhaps it works. i haven't tried it yet.

vlad

---

### Post by xodeus on 2005-08-14
I'm getting some strange problems running winetools.
Something about missing stuff. can't do anything in wt2, it just jumps back to the main screen.
```
Gtk-WARNING **: Kunne ikke finde modul i module_path: "libindustrial.so",
```

---

### Post by pbobby on 2005-08-14
I cannot install IE6.

These are the final console msgs when performing IE6 install.

> Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/pbobby/.wine/installed.reg: No such file or directory
grep: /home/pbobby/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/pbobby/.wine/installed.reg': No such file or directory
software installation verified by /home/pbobby/.wine/winetools.log
491768
WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.WIN" "Options.WIN" "InstallDir" 0x10253f8 260 0x7b98f830 (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub



BTW I also tried the sidenet installer script also - and get the same error. "Setup was unable to download the required components.... etc etc "

Geez this is frustrating as all heck!

---

### Post by leifson37 on 2005-08-15
make[2]: Går til katalog '/home/frank/wine/wine/dlls/wldap32'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2  -o misc.o misc.c
misc.c: In function `WLDAP32_ldap_result':
misc.c:58: error: `LDAP_NOT_SUPPORTED' undeclared (first use in this function)
misc.c:58: error: (Each undeclared identifier is reported only once
misc.c:58: error: for each function it appears in.)
make[2]: *** [misc.o] Fejl 1
make[2]: Forlader katalog '/home/frank/wine/wine/dlls/wldap32'
make[1]: *** [wldap32] Fejl 2
make[1]: Forlader katalog '/home/frank/wine/wine/dlls'
make: *** [dlls] Fejl 2

Compilation failed, aborting install.
frank@ubuntu:~/wine/wine$

I get this error when compiling, what shall i do, plz someone help me with this

---

### Post by absinthe on 2005-08-19
I got ie6 to install following this method here:

[http://www.frankscorner.org/index.php?p=ie6](http://www.frankscorner.org/index.php?p=ie6)

---

### Post by carajean on 2005-08-20
Ok i have followed the instuctions to a T but i still cant get IE6 to install i have tried other installation methods also actually all the ones i found on goodle.  i keep getting this error 
   regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/carajean/.wine/installed.reg: No such file or directory
grep: /home/carajean/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/carajean/.wine/installed.reg': No such file or directory
software installation verified by /home/carajean/.wine/winetools.log
Failed: 1



can some one help on that  also i have one more question does anyone know another tutorial that i can read that will help me to figure out how to run this tool and install games?

---

### Post by kennny2004 on 2005-08-20
ummm here is the thing i get plz help me
[B]alexander@house:~/temp/winetools$ sudo sh install.sh
Installing WineTools to /usr/local/winetools...
Installing translations...
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt2.mo
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt2.mo
Start WineTools as *normal* user with "wt2". Don't use as root![/B]
and
[B]alexander@house:~/temp/winetools$ sh install.sh
Installing WineTools to /usr/local/winetools...
Installing translations...
Installed translations for de_DE@euro to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt2.mo
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt2.mo
Start WineTools as *normal* user with "wt2". Don't use as root![/B]
 and what is going on

---

### Post by humanity_to_others on 2005-08-21
[QUOTE=absinthe]I got ie6 to install following this method here:

[http://www.frankscorner.org/index.php?p=ie6](http://www.frankscorner.org/index.php?p=ie6)[/QUOTE]
I got it from this way, too

---

### Post by carajean on 2005-08-21
OK i reinstalled ubuntu once again to see if i could get this to run and now im getting a error early when i first try to install wintools 

configure: error: /usr/X11R6/lib/libGL.a is present on your system.
This prevents linking to OpenGL. Delete the file and restart configure.

Configure failed, aborting install.

thats the error i get.

Now i have another question since this is the cvs version it all free right?

ALso I hope someone can answer my question becuase i gotta play world of warcraft :)

---

### Post by carajean on 2005-08-21
p.s im a newb to linux so i dont know how to delete the file. ](*,)

---

### Post by Weav on 2005-08-22
[QUOTE=carajean]OK i reinstalled ubuntu once again to see if i could get this to run and now im getting a error early when i first try to install wintools 

configure: error: /usr/X11R6/lib/libGL.a is present on your system.
This prevents linking to OpenGL. Delete the file and restart configure.

Configure failed, aborting install.

thats the error i get.

Now i have another question since this is the cvs version it all free right?

ALso I hope someone can answer my question becuase i gotta play world of warcraft :)[/QUOTE]
Well to delete the file just open up a terminal and type:
```

cd /usr/X11R6/lib/
sudo rm libGL.a

```
and that should be all you need to do to get rid of that file

---

### Post by Weav on 2005-08-22
I am having a problem installing cvs and wine. First off the ./tools/wineinstall halts after it asks me for the root password even though i am 100% sure i'm typing it in correct. As i did sudo make install and it worked.

So i get to wine tools setup and i have an error installing DCOM98, it simulates windows reboots and says installation failed.

Any ideas on how to get DCOM98 to work?

EDIT: Ok i got DCOM98 to install by apt-get install winelib

However now when i try to install IE6 i get installation failed.

---

### Post by thelung on 2005-08-22
Tried this and ran into the same problem as the other AMD_64 users.

> ...
{standard input}:294: Error: `12(%esp)' is not a valid 64 bit base/index expression
{standard input}:327: Error: `(%edx)' is not a valid 64 bit base/index expression
make[2]: *** [interlocked.o] Error 1
make[2]: Leaving directory `/home/thelung/cvs/wine/libs/port'
make[1]: *** [port] Error 2
make[1]: Leaving directory `/home/thelung/cvs/wine/libs'
make: *** [libs] Error 2

Compilation failed, aborting install.
 

I wish I had read the whole thread and seen that people are getting stuck here before I tried it for myself. Oh well.

---

### Post by stunro on 2005-09-07
[QUOTE=hardwarder]Whenever I run wt2, I get this on the terminal
```
Gdk-WARNING **: locale not supported by Xlib, locale set to C
```
When I click Base Setup, the menu disappears and appears again. It does that when I select an option from the menu.

Edit: Solved the problem by adding my locale to the /usr/X11R6/lib/X11/locale/locale.dir file.[/QUOTE]


hi im using hoary i have the same problem like you but how do you solve your problem? 

thanks

---

### Post by Sunil on 2005-09-07
[QUOTE=Weav]Well to delete the file just open up a terminal and type:
```

cd /usr/X11R6/lib/
sudo rm libGL.a

```
and that should be all you need to do to get rid of that file[/QUOTE]


rather than delete it all together (which might cause problems altogether) just

sudo mv LibGL.a LibGL.a_backup

Sunil

---

### Post by kirisato on 2005-09-08
[QUOTE=stunro]hi im using hoary i have the same problem like you but how do you solve your problem? 

thanks[/QUOTE]

Your locale isn't supported by Xlib. So you need to change your locale
 to one that is, or change your Xlib to one that supports your locale.
 "echo $LANG"

and like he said just edit and add your local on /usr/X11R6/lib/X11/locale/locale.dir

---

### Post by Knyven on 2005-09-10
[QUOTE=kirisato]Your locale isn't supported by Xlib. So you need to change your locale
 to one that is, or change your Xlib to one that supports your locale.
 "echo $LANG"

and like he said just edit and add your local on /usr/X11R6/lib/X11/locale/locale.dir[/QUOTE]
 Me too have the same problem, I manage to find the file locale.dir. what do i do with it? i have run text editor, what is "local"? what is "echo$LANG?
*please give specific directions*

BTW:
Do i need to install all of these before proceeding to Fonts?

DCOM98
Windows Installer
Microsoft Foundation Classes 4.0
Visual Basic 5 Runtime
Visual Basic 6 Runtime
Visual C++ run-time English -- or german if you are german.
MDAC 2.8 English -- or german if you once again german
Jet 4.0 SP8 English -- Or german if you have german blood!
Windows Script 5.6 English -- Or German if you can drink 50 gallons of beer and still not pass out.

HTML Help Update Package
Common Controls 5.0

---

### Post by Pheylan on 2005-09-11
I tried installing it this way but when I get to the part to load up Winetools I get this error message.

Error messeage deleted.

I tried apt-getting the Libgtk-1.2 but it is supposed to be included in Ubuntu is it not.  Anyone have any ideas on this?  I would really like to install this so I can play some of my windows games on linux  --  NVM went into synaptic and found it there.   :smile: 

However following these instrcutions once i get to the point to download IE6 with SP 1 it gives me therror message:

Setup was unable to download the required components.  Please make sure you are connected to the internet, or try to run the setup again.   

It then goes on to say that the install failed.

---

### Post by Knyven on 2005-09-12
Its Libgtk1.2 remove the dash (-)

---

### Post by Knyven on 2005-09-13
[QUOTE=Knyven]Me too have the same problem, I manage to find the file locale.dir. what do i do with it? i have run text editor, what is "local"? what is "echo$LANG?
*please give specific directions*[/QUOTE]

I reinstalled Ubuntu and chose English/United States to fix the problem since no one bothers to reply.

Now it works but there is problem with downloading the Internet Explorer 6 SP1 English. Can anyone suggest an alternative?

---

### Post by rainestorm on 2005-09-13
i can follow through your tutorial even if iam a noob in Ubuntu

but i encounter an error during the compilation in ./tools/wineinstall
it says

gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o xrender.o xrender.c
xrender.c:1659: error: conflicting types for ‘X11DRV_XRender_ExtTextOut’
x11drv.h:274: error: previous declaration of ‘X11DRV_XRender_ExtTextOut’ was here
make[2]: *** [xrender.o] Error 1
make[2]: Leaving directory `/home/pcx15/wine/dlls/x11drv'
make[1]: *** [x11drv] Error 2
make[1]: Leaving directory `/home/pcx15/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.


Please help me

---

### Post by rj686 on 2005-09-17
[QUOTE=rainestorm]i can follow through your tutorial even if iam a noob in Ubuntu

but i encounter an error during the compilation in ./tools/wineinstall
it says

gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o xrender.o xrender.c
xrender.c:1659: error: conflicting types for ‘X11DRV_XRender_ExtTextOut’
x11drv.h:274: error: previous declaration of ‘X11DRV_XRender_ExtTextOut’ was here
make[2]: *** [xrender.o] Error 1
make[2]: Leaving directory `/home/pcx15/wine/dlls/x11drv'
make[1]: *** [x11drv] Error 2
make[1]: Leaving directory `/home/pcx15/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.


Please help me[/QUOTE]
 i had exactly the same problem

---

### Post by pinoyskull on 2005-09-17
after reading the guide, installing different wine version (which almost all of them failed to install ie6), my wine is now running smooth, ie6 working, all components no problem with installation

im using ubuntu 5.04 on Intel x86, wine (20050111), winetools (212) :)

---

### Post by jeffreyvergara.NET on 2005-09-17
hello, im stuck at step 3) Compling and installing Wine

> 
etc... more checking here...  

checking for X11/Xlib.h... yes
checking for X11/XKBlib.h... yes
checking for X11/Xutil.h... yes
checking for X11/extensions/shape.h... yes
checking for X11/extensions/XInput.h... yes
checking for X11/extensions/XShm.h... yes
checking for X11/extensions/Xrandr.h... yes
checking for X11/extensions/Xrender.h... yes
checking for X11/extensions/xf86dga.h... no
checking for X11/extensions/xf86vmode.h... no
checking for XkbQueryExtension in -lX11... yes
checking for XShmQueryExtension in -lXext... yes
checking for XShapeQueryExtension in -lXext... yes
checking for XRenderSetPictureTransform in -lXrender... yes
checking for GL/gl.h... yes
checking for GL/glx.h... yes
checking for GL/glext.h... yes
checking for up-to-date OpenGL version... yes
checking for glXCreateContext in -lGL... no
configure: error: /usr/X11R6/lib/libGL.a is present on your system.
This prevents linking to OpenGL. Delete the file and restart configure.

Configure failed, aborting install.


---

### Post by jeffreyvergara.NET on 2005-09-17
[QUOTE=jeffreyvergara.NET]hello, im stuck at step 3) Compling and installing Wine[/QUOTE]
 never mind... Im just stupid.... i figured it out

---

### Post by jeffreyvergara.NET on 2005-09-18
but now I have this problem:

> 
Wine build complete.

Performing 'make install' as root to install binaries, enter root password
Password:
su: Authentication failure
Sorry.
Password:
su: Authentication failure
Sorry.

Either you entered an incorrect password or we failed to
run 'make install;echo /usr/local/lib>>/etc/ld.so.conf;/sbin/ldconfig' correctly.
If you didn't enter an incorrect password then please
report this error and any steps to possibly reproduce it to
[http://bugs.winehq.org/](http://bugs.winehq.org/)

Installation failed, aborting.



my password is correct

---

### Post by chroot on 2005-09-22
[QUOTE=BAshworth]I'm having a problem with this myself.

I get no error messages during the installation of either wine or winetools.  It finishes with no problems, and entering the command wt2 at the command line brings up all the disclaimer screens that are mentioned.  This leaves me at the WineTools 2.1.1 window.  I can select base setup, but the window just flickers, and then comes right back to the same thing.  Apparently, no matter what I select it does this exact same thing.

Any ideas?[/QUOTE]

Is this issue resolved? Im also having this problem  :|

---

### Post by Qwacko on 2005-09-27
Hi

I have tried this procedure, but when it comes to the install ie6 part, the installer stops at the very start where it says, initializing  setup. The error message is "Setup was unable to download the required component. Please make sure you are connected to the internet, or try to run setup again later" This message comes up when i install wine using this guide, and also when i installed wine through synaptic, anyone know what i could do to fix this?

---

### Post by Statik on 2005-09-29
So I'm trying the older wine install now, and I've created a rootpwd to ease the installation. Is there a way to undo this when the install is complete?

Statik

---

### Post by rvricaforte on 2005-09-30
Hope you guys can help me.  I've gotten to the point of compiling and issued the following command:

./tools/wineinstall

Message that follows are the following:

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Configure failed, aborting install.
rvricaforte@PC01:~/cvs3/wine$

Sure would appreciate some wise advise.

Thanks in advance.

---

### Post by Gorlist on 2005-10-01
Hi, brilliant how to guide, though run into a spot of trouble.

When I go to run Winetools it comes up with: 

```

LD_PRELOAD=
found gettext in /usr/bin
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 20050930
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "20050930".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/james/.wine/winetools.log.
CDROM is .
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

I followed it through, had no problems accept when it wanted me to log in as root to 'make install', so I used the sudo command instead. When installing winetools I also used the newer version which I found on this thread.

Anyideas, regards. :)

---

### Post by j37h3r on 2005-10-02
Im having issues downloading IE 6. Any ideas how I can work around this? Thanks!

---

### Post by MBro on 2005-10-02
[QUOTE=j37h3r]Im having issues downloading IE 6. Any ideas how I can work around this? Thanks![/QUOTE]
I'm having the exact same problem

---

### Post by zaytsevi on 2005-10-03
x@s37:~/cvs/wine$ **sudo apt-get install libgtk-1.2 libgtk1.2-common**
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk-1.2
that doesnt work....
and this doesnt work...
x@s37:~/cvs/wine$ **./tools/wineinstall**
WINE Installer v0.75
Running configure...
configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
Configure failed, aborting install.

---

### Post by j37h3r on 2005-10-03
[QUOTE=MBro]I'm having the exact same problem[/QUOTE]


[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

^^ Worked for me! :eek:

---

### Post by KrisDwyer on 2005-10-07
at least u have the "bison" package :S

---

### Post by Jasconius on 2005-10-08
This is my first time using Linux, I have Ubuntu 5.04 on the AMD64 platform and I'm trying to install wine.

I get up to this part

./tools/wineinstall

And this is what I get in the Terminal

WINE Installer v0.75

Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I have installed build-essential time and time again, and I still get this error, any help?

---

### Post by OttoDestruct on 2005-10-15
Anyone know why I get this when I try to install any of the winetools stuff, or use wine to install the fonts?

```

wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
```

---

### Post by OttoDestruct on 2005-10-16
It seems no matter what I use (this guide, or using repositories to install wine and use the sidenet config tools) I can't install IE6. Does anyone know why it always says 'cant download' or 'cant install'?

---

### Post by Lod on 2005-10-26
[QUOTE=OttoDestruct]It seems no matter what I use (this guide, or using repositories to install wine and use the sidenet config tools) I can't install IE6. Does anyone know why it always says 'cant download' or 'cant install'?[/QUOTE]
I've got the same problem. Using the sidenet solution seems to mess up the wt2 setup. :( It installs IE, but then when I go back to this howto it wants to start all over again.
If anyone has a solution please let me (us) know :)

---

### Post by drdnl on 2005-10-27
PARTIAL SOLUTION FOUND, INTERNET EXPLORER WORKS FINE

I found a way to get IE6 to install using sidenet without screwing up winetools, personally I have other issues to sort out, but this should help some of you.

Download and install Sidenet [http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.8.6.tgz](http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.8.6.tgz) , yes I know that link takes up a lot of space, but somehow I crashed Firefox trying to make a link...

Please dont fill this thread with "how do I untar" questions, go here for those [www.ubuntuguide.org](www.ubuntuguide.org)

Download Sidenet, put in a temp folder, unpack and follow the readme (hint: run setup.sh from nautilus, but in a terminal. Or open a terminal and run setup, sudo not necessary)

Easiest install is 1, silent install. But 3 (read the readme) will make your life easier regarding com98. Seems to work fine for me....

You'll end up with a .wine with a fully functional internet explorer, but winetools will b*tch and ask you to install its 'filesystem'. So, rename .wine to .wine_whatever_is_easiest
I picked .wine_sidenet

make sure the old .wine is gone... download and run winetools as mentioned on the first page of this large how-to, but get it from [http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-212jo.tar.gz)

Its the latest version and works better with Wine

After winetools is running let it run its config and create a fake c drive (its under base setup, top option)

Now you have a perfectly working but rather empty and useless .wine

open the folders .wine and .wine_sidenet side by side, notice similarities?

copy the c: from sidenet into winetools' c:, look around a bit, it should be all there

you'll notice that .wine has 4 or 5 files in its main folder, config, system, user, userdef and winetools (I think),

copy system, user, userdef and winetools into .wine from .wine_sidenet but dont copy the config (remember winetools asking to change it?)

Now you should have a fully functioning Internet explorer and a happy Winetools, try it out :)

Now for my problem: all the installs 'cept fonts and the winetools IE6 will work, so vb5,6 c++ windows installer etc.

But when you try to install the database files (mdac and jet) it gives this error:

Choice is MDAC 2.8 and Jet 4.0 SP8 English
MDAC_TYP.EXE
software installation verified by /home/daniel/.wine/winetools.log
5556616
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="" wine ./MDAC_TYP.EXE
waiting for wineservers to exit...
err:setupapi:SetupDefaultQueueCallbackA copy error 32 "C:\\windows\\temp\\IXP006.TMP\\msvcrt.dll" -> "c:\\windows\\system32\\msvcrt.dll"
all wineservers endet after 15 seconds...
Failed: 194
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Wine is finalizing your software installation. This may take a few minutes,
though it never actually does.
Failed: 194
MDAC_TYP.EXE
software installation verified by /home/daniel/.wine/winetools.log
dependency MDAC_TYP.EXE *not* fulfilled

Can anyone help me out with it?

---

### Post by geoguy on 2005-10-28
What is MDAC used for on a windows system? does it need to be installed to use a lot of programs?

---

### Post by drdnl on 2005-10-28
I need it to run the rather excellent mediamonkey. A very, very good music management program. I use it to put music on my iAudio M3

---

### Post by pkslot on 2005-11-20
[QUOTE=Vaego]Alright, well, i've tried the latest Wine CVS and winetools and I have to say i'm impressed, wine is not too far behind Cedega and I think in the next year Wine might take the step ahead of them. Granted, they deserve to be ahead, they are the creators and Transgaming kind of stole their project and are hogging it for themselves.

So I present to you all, a howto on how to install the latest Wine CVS, installing wine tools and getting everything you'll need for the road.

**1) Getting The Development Libraries to compile wine:**

We also need a few development libs to compliment this:

xlibs-dev will allow you to compile wine with x support, the reason behind why most compilations of wine fail under Ubuntu.

```
sudo apt-get install xlibs-dev
```


If you want OpenGL support, don't forget to get these libs here:

```
sudo apt-get install xlibmesa-glu-dev
```

Heres two other packages that will make it so wine compiles, and are required during the wine compilation, these are the bison and flex packages.

```
sudo apt-get install bison flex
```

This package here is for winetools, i'll explain this later on.

```
sudo apt-get install libgtk-1.2 libgtk-1.2-common
```

And lastly, we need to get the cvs package to even be able to grab the cvs streight from winehq.

```
sudo apt-get install cvs
```

--[/QUOTE]


Hey there, thanks for taking the time to write all this down.

Now the fun stops halfway through for me, i can't seem to find the libgtk-1.2 & libgtk-1.2-common files.

What can i do to change this :oops: 

I've used Ubuntu - my first linux os - for about two days now, so i'm not superskilled using the terminal yet, be gentle :)

---

### Post by 11hjpphty76lkjj on 2005-11-21
All,

Thanks for the looking at my question.

When I am at the step for:

./tools/wineinstall  

I am getting the following error:

make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wintrust'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/wldap32'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o value.o value.c
value.c: In function ‘bv2str’:
value.c:123: error: dereferencing pointer to incomplete type
value.c:128: error: dereferencing pointer to incomplete type
make[2]: *** [value.o] Error 1
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wldap32'
make[1]: *** [wldap32] Error 2
make[1]: Leaving directory `/home/aaron/cvs/wine/dlls'
make: *** [dlls] Error 2

I've followed the instructions prior to running this step.  I have build-essential, gcc-3.4 installed.

I've done a: ./tools/make clean and then ./tools/wineinstall with the same result.

make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/winmm/wineoss'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/wininet'
make[3]: Entering directory `/home/aaron/cvs/wine/dlls/wininet/tests'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/aaron/cvs/wine/dlls/wininet/tests'
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wininet'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/winspool'
make[3]: Entering directory `/home/aaron/cvs/wine/dlls/winspool/tests'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/aaron/cvs/wine/dlls/winspool/tests'
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/winspool'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/wintrust'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wintrust'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/wldap32'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o value.o value.c
value.c: In function ‘bv2str’:
value.c:123: error: dereferencing pointer to incomplete type
value.c:128: error: dereferencing pointer to incomplete type
make[2]: *** [value.o] Error 1
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wldap32'
make[1]: *** [wldap32] Error 2
make[1]: Leaving directory `/home/aaron/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

I've tried to search to what could be causing this but I didn't find anything.  Any help is appreciated.

Help!!

Aaron

---

### Post by 11hjpphty76lkjj on 2005-11-21
hmm well I added the deb dir from:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

and did a 

sudo apt-get install wine winetools libwine

and it 'seems' to be working now.

Although someone may be interested in the errors I was seeing.   I did not follow the rest of this how to, I just did the apt-get than ran winetools to install, etc.

Aaron

---

### Post by No-Brain on 2005-11-27
Followed the instrucions for compiling from cvs.  

Everything went well, but when I try to run Winecfg I get the following error:

*_/usr/local/bin/wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory_*

I have verified that the file(s) exist in /usr/local/lib

Any suggestions?

TIA
Roger

---

### Post by sylverpyro on 2005-11-28
> **jeffreyvergara.NET]but now I have this problem:
 Wine build complete.

Performing 'make install' as root to install binaries, enter root password
Password:
su: Authentication failure
Sorry.
Password:
su: Authentication failure
Sorry.

Either you entered an incorrect password or we failed to
run 'make install said:**
> http://bugs.winehq.org/[/url]

Installation failed, aborting.


my password is correct

I am not sure if this has been answered already or not, but I got around it by making a temp root account.  

user@computer:~$ sudo passwd root
 - enter your sudo password then create a different password for the "root" account

After that is done, you can test it by typing

user@computer:~$ su
 - You will be prompted for a password.  Type in the temp one you created for the "root" account.  If you see this:
root@computer:/dirs#
it worked.
Re-run wineinstall and use your "root" password when it asks for it. 

IMPORTANT
Once this is done, you need to run the following command
user@computer:~$ sudo passwd -l root
This will lock the root account again so that your GUI admin tools like Synaptic and Add Programs will work again.  Ubuntu is built around the sudo "account" and does not the root account being active.

Hope this helps

---

### Post by sylverpyro on 2005-11-28
[QUOTE=No-Brain]Followed the instrucions for compiling from cvs.  

Everything went well, but when I try to run Winecfg I get the following error:

*_/usr/local/bin/wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory_*

I have verified that the file(s) exist in /usr/local/lib

Any suggestions?

TIA
Roger[/QUOTE]

I ran into a similar problem with the libwine.so.1 file.  The error message that I got looked like this:
*/usr/local/bin/wine-pthread: relocation error: /usr/local/bin/wine-pthread: symbol wine_pthread_set_functions, version WINE_1.0 not defined in file libwine.so.1 with link time reference*

The workaround that I found for this is in the link: [http://www.spinics.net/lists/wine/msg22052.html](http://www.spinics.net/lists/wine/msg22052.html)

In short, this is what I did:
user@computer:~$ locate ld.so.conf
 - If no file is returned after this command this is what you have to do:

user@computer:~$ sudo vim /etc/ld.so.conf
 - Paste this line into the text file that was created:
/usr/local/lib/

Save the file and exit vim (For those who do not use vim normally hit Esc then type in :wq )

Then run the following command
user@computer:~$ sudo /sbin/ldconfig

---

### Post by psychosushi on 2005-11-30
Hey, great guide, but I'm having a problem following the instructions. When I type in ./tools/wineinstall, and the actual installation starts, I get the message:

../../include/winnls.h:758: warning: ‘__stdcall__’ attribute ignored
make[2]: *** [casemap.o] Error 1
make[2]: Leaving directory `/home/psychosushi/installed/cvs/wine/libs/unicode'
make[1]: *** [unicode] Error 2
make[1]: Leaving directory `/home/psychosushi/installed/cvs/wine/libs'
make: *** [libs] Error 2

Compilation failed, aborting install.

Anybody know what that means?

---

### Post by Josef K. on 2005-11-30
I'm afraid that means
if you want to use wine you should downgrade to ubuntu 32bit and use a packaged version of wine :-k

---

### Post by Eyeball Kid on 2005-12-02
Hi!

After doing

      ./tools/wineinstall

the compiler errs out with the following message:

make[2]: Entering directory `/home/james/cvs/wine/dlls/wininet'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_WINX32_ -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o netconnection.o netconnection.c
netconnection.c:246: error: syntax error before ‘*’ token
make[2]: *** [netconnection.o] Error 1
make[2]: Leaving directory `/home/james/cvs/wine/dlls/wininet'
make[1]: *** [wininet] Error 2
make[1]: Leaving directory `/home/james/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

Why would I get a syntax error? I sure would like to be able to install SMAC!

---

### Post by psychosushi on 2005-12-04
I have ubuntu linux x86_64 and am trying to compile wine on it. When I type ./tools/wineinstall everything proceeds smoothly until:

../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./ddraw.spec    clipper.o ddraw_hal.o ddraw_main.o ddraw_thunks.o ddraw_user.o ddraw_utils.o main.o palette_hal.o palette_main.o regsvr.o surface_dib.o surface_fakezbuffer.o surface_gamma.o surface_hal.o surface_main.o surface_thunks.o surface_user.o surface_wndproc.o  version.res   -o ddraw.dll.so -L../../dlls -L../../dlls/ole32 -L../../dlls/user32 -L../../dlls/gdi32 -L../../dlls/advapi32 -L../../dlls/kernel32 -lole32 -luser32 -lgdi32 -ladvapi32 -lkernel32  -L../../libs/wine -lwine -ldxguid -luuid  -L/usr/X11R6/lib  -lXext -lX11   -L../../libs/port -lwine_port
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.2/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/psychosushi/installed/cvs/wine/dlls/ddraw'
make[1]: *** [ddraw] Error 2
make[1]: Leaving directory `/home/psychosushi/installed/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

Does anybody know how to fix this, and is it in fact possible to compile wine in 64-bit?

---

### Post by pepolez on 2005-12-11
any ideas howto add extra filesystems?

---

### Post by Il_Tuo_Nome on 2005-12-19
When installing for OpenGL Support, I received the following error:

rosso@Gianuntu:~$ sudo apt-get install xlibmesa-glu-dev
Reading package lists... Done
Building dependency tree... Done
Package xlibmesa-glu-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibmesa-glu-dev has no installation candidate

and when I tried installing libgtk-1.2 libgtk-1.2-common, I received the following:

rosso@Gianuntu:~$ sudo apt-get install libgtk-1.2 libgtk-1.2-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk-1.2
rosso@Gianuntu:~$

I would appreciate any insight, thank you

---

### Post by polt on 2005-12-20
I am getting the exact same error as expressed by this user.  Does anyone know what the problem is?  it doesn't have to do with permissions does it?

[QUOTE=kalosaurusrex]
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/winmm/wineoss'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/wininet'
make[3]: Entering directory `/home/aaron/cvs/wine/dlls/wininet/tests'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/aaron/cvs/wine/dlls/wininet/tests'
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wininet'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/winspool'
make[3]: Entering directory `/home/aaron/cvs/wine/dlls/winspool/tests'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/aaron/cvs/wine/dlls/winspool/tests'
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/winspool'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/wintrust'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wintrust'
make[2]: Entering directory `/home/aaron/cvs/wine/dlls/wldap32'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__   -D_REENTRANT -fPIC -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o value.o value.c
value.c: In function ‘bv2str’:
value.c:123: error: dereferencing pointer to incomplete type
value.c:128: error: dereferencing pointer to incomplete type
make[2]: *** [value.o] Error 1
make[2]: Leaving directory `/home/aaron/cvs/wine/dlls/wldap32'
make[1]: *** [wldap32] Error 2
make[1]: Leaving directory `/home/aaron/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

[/QUOTE]

---

### Post by polt on 2005-12-20
[QUOTE=zaytsevi]
x@s37:~/cvs/wine$ **sudo apt-get install libgtk-1.2 libgtk1.2-common**
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk-1.2
that doesnt work....
[/QUOTE]

the package was misnamed in the howto.  try:
$sudo apt-get install libgtk1.2 libgtk1.2-common

you can also find those packages in synaptic package manager.  they are probably already installed anyway.

[QUOTE=zaytsevi]
and this doesnt work...
x@s37:~/cvs/wine$ **./tools/wineinstall**
WINE Installer v0.75
Running configure...
configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
Configure failed, aborting install.[/QUOTE]

you need a c compiler.  gcc should work.  you can get it by doing:
$sudo apt-get install gcc

that should work for you.

---

### Post by polt on 2005-12-20
[QUOTE=Il_Tuo_Nome]

and when I tried installing libgtk-1.2 libgtk-1.2-common, I received the following:

rosso@Gianuntu:~$ sudo apt-get install libgtk-1.2 libgtk-1.2-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk-1.2
rosso@Gianuntu:~$

I would appreciate any insight, thank you
[/QUOTE]

the libgtk package was misnamed in the howto.  you can look in synaptic package manager for it or just type:

$sudo apt-get install libgtk1.2 libgtk1.2-common

---

### Post by starscalling on 2005-12-22
in order to work i had to reference this page:
[http://appdb.winehq.org/appview.php?versionId=469](http://appdb.winehq.org/appview.php?versionId=469)
notably this post:
Manual installation:
0) recommanded but optional: install latest Wine release and start with a clean wine installation (this will remove all your installed windows applications):
rm -rf ~/.wine
1) download and import ie6_overrides.reg in your registry*:
wine regedit ie6_overrides.reg
2) find dcom98 and install it using:
wine dcom98.exe

3) delete regsvr32.exe:
rm -f ~/.wine/drive_c/windows/system32/regsvr32.exe
4) install IE6SP1 (select minimal installation and uncheck Connection wizard. You can install Media Player with codecs if you want):
wine ie6setup.exe

just had to overwrite the registry bit then back to the installer ..... not so impressed so far tbh

---

### Post by fatalerror on 2006-02-12
hi everyone,

first of all,I'm new user for ubuntu..I'm trying to install wine and winetools for a long time.

```
./tools/wineinstall
```
I wrote this code but it says this
```
WINE Installer v0.75

The source directory is not writable. You probably extracted the sources as root.
You should remove the source tree and extract it again as a normal user.

```

what should i do?i'm really new in this.thanks....

---

### Post by eran- on 2006-06-05
Okay... I've done everything, and I think I'm not the first one to ask this, but seems like winetools can't find libraries mentioned:
```
$ wt2
LD_PRELOAD=
found gettext in path
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.12
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.12".
/usr/local/bin/wt2: line 2946: [: 0.9.12: integer expression expected
/usr/local/bin/wt2: line 2946: [: 0.9.12: integer expression expected
Version of Wine is OK.
Calls to wine are executed as  "wine".
Config is /home/user/.wine/winetools.log.
CDROM is .
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Dpkg -S libgtk-1.2* says:
```
$ dpkg -S libgtk-1.2*
libgtk1.2: /usr/lib/libgtk-1.2.so.0
libgtk1.2-dbg: /usr/lib/debug/libgtk-1.2.so.0.9.1
libgtk1.2-dbg: /usr/lib/debug/libgtk-1.2.so.0
libgtk1.2: /usr/lib/libgtk-1.2.so.0.9.1

```

So, those libraries have been installed, but winetools can't find them. Is there a solution for this..?

---

### Post by papaver on 2006-06-05
yeah i get the same error to : 

~$ wt2
found gettext in path
Browser is /usr/bin/firefox.
detecting Wine version... done.
Drive C: is /home/papaver/.wine/drive_c
Wine 0.9.14
wine is executed as wine
Parameters are --noexit
/usr/local/bin/wt2: line 2568: [: 0.9.14: integer expression expected
/usr/local/bin/wt2: line 2568: [: 0.9.14: integer expression expected
Version of Wine is OK.
Calls to wine are executed as wine.
Config is /home/papaver/.wine/winetools.log.
CDROM is /media/cdrom0.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

~% dpkg -S libgtk-1.2*
libgtk1.2: /usr/lib/libgtk-1.2.so.0
libgtk1.2: /usr/lib/libgtk-1.2.so.0.9.1

I have installed using the 

HowTo - Install 32 bit wine to 64 bit Dapper without chroot
[http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557)

don't know if that makes a difference or not.

---

### Post by fizz on 2006-06-23
when compiling wine, I get the following error:


make[1]: Entering directory `/home/kelly/Desktop/wine/wine/include'
../tools/widl/widl -I. -I. -I../include -I../include    -h -H exdisp.h exdisp.idl
Could not open exdisp.h for output
make[1]: *** [exdisp.h] Error 1
make[1]: Leaving directory `/home/kelly/Desktop/wine/wine/include'
make: *** [include] Error 2

---

### Post by ahh_dee on 2006-06-25
awesome thanks

---

### Post by Linux_Noobie03 on 2006-07-18
Hey i just strolled across this tutorial and thought id give it a go, but im having a few problems, when i run ./tools.wineinstall it runs through alot of the procedure, i get past entering my root password but then it ends on a error:


err:module:export_dll Library wined3d.dll (which is needed by L"c://windows//system32//ddraw.dll") not found 

What have i done wrong??? please any advice would be great ive been sitting on this for two days now.](*,) 

Youll Never Walk Alone

---

### Post by Linux_Noobie03 on 2006-07-18
As far as i can tell im missing the wined3d.dll.so file has it not compiled when i ran wineinstall?

---

### Post by robotangel on 2006-07-22
Same problem here. No errors when I run configure. I attached my config.log and the output of "make ./dlls/wined3d/Makefile". Please help, it seems that this problem doesn't happen very often, google doesn't find anything suitable...:confused: 
Doesnt anyone has solved this problem?!](*,)

edit: I found something on the winehq-wiki but it's not something specific. Maybe someone can use it and tell us why it doesn't work...
[quote="John Rimell, http://appdb.winehq.org/commentview.php?iAppId=2249&iVersionId=5068&iThreadId=12975"]I came across this too. There was some setting that was disabling the building of D3D. I think it might have been that the configure script had noticed something was missing (something that was required to build D3D) so it was deciding to not build it. Check the config.log also, when you run ./configure and make, pipe (>) all the output to a log file, so you can go back and look at its decisions.

I don't remember anything more, however I might try this all again and report back. I've just moved to Fedora Core 5 and haven't tried it since.[/quote]

---

### Post by wdcrls on 2006-09-23
got as far as the i.e. setup
but that is a dead link.
it downloads the link but not the i.e itself
:((:confused:

---

### Post by Shiryou on 2006-10-14
```
wget http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz
```

This you may notice is off my personal webstorage, why did I do this? Because my links will never die ;), anyways lets start on installing this beast.




I'm getting this error

"=> `winetools-211jo.tar.gz'
Resolving home.comcast.net... 204.127.198.24
Connecting to home.comcast.net|204.127.198.24|:80... connected.
HTTP request sent, awaiting response... 404 Not found
09:00:14 ERROR 404: Not found."

Is there an alternative way to get that file?

---

### Post by Shiryou on 2006-10-14
Nevermind, i got that it to work through some other site.

But i bigger problem now... I did the Basesetup and the fake windows drive and the DCOM98, but now it wont let me install Explorer 6.0 SP1 English. Kinda stuck now..

any ideas?

Thanks in advance

---

### Post by Xera on 2006-12-12
> ```
wget http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz
```
This you may notice is off my personal webstorage, why did I do this? Because my links will never die , anyways lets start on installing this beast.
Well, your link is dead. so is the one on the winetools website and i can't find any other links ](*,)


Xera

---

### Post by nkayesmith on 2006-12-19
I've put a slightly modified version (enabling support for the latest versions of wine) at [http://download.formationos.net/](http://download.formationos.net/)

---

### Post by Azeroth on 2006-12-29
Hi!

I'm trying to compile wine cvs with openGL support, but after running configure, I get this:
```

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

Configure finished.  Do 'make depend && make' to compile Wine.
```

and in the part that cheks for opengl produce this:
```

checking for X11/Xutil.h... yes
checking for X11/extensions/shape.h... yes
checking for X11/extensions/XInput.h... yes
checking for X11/extensions/XShm.h... yes
checking for X11/extensions/Xinerama.h... no
checking for X11/extensions/Xrandr.h... yes
checking for X11/extensions/Xrender.h... no
checking for X11/extensions/xf86vmode.h... yes
checking for XkbQueryExtension in -lX11... yes
checking for XShmQueryExtension in -lXext... yes
checking for XShapeQueryExtension in -lXext... yes
checking for XF86VidModeQueryExtension in -lXxf86vm... yes
checking for GL/gl.h... yes
checking for GL/glx.h... yes
checking for GL/glext.h... yes
checking for GL/glu.h... yes
checking for up-to-date OpenGL version... yes
checking for glXCreateContext in -lGL... no
checking for gluLookAt in -lGLU... yes

```
I have installed all packages mentioned in this page: [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

and in this howto, but nothing happens.
I own a kubuntu dapper install with dri activated for my card (I can play ppracer)
Bye!!

---

### Post by tjtoml on 2007-01-11
> **jonny said:**
> Great How-to.  I'm working my way through it with interest.  Some minor points that could trip up unwary noobs, though - I suggest you edit the original post.

1. Two packages are incorrectly named above - it's libgtk1.2 and libgtk1.2-common
**2. On a fresh ubuntu installation, you also need the  buildessential package**
3. The run as root bit presupposes that you have a root password - which you don't by default in Hoary.  I had to copy the failed command that was reported to me and paste it with sudo.
4. Before running wineinstall, I had to change the permissions on one file, thus: sudo chmod a+w /etc/ld.so.conf, and return it to its former state afterwards
5. Before running wineinstall, I had to backup one file: sudo mv /usr/X11R6/lib/libGL.a /usr/X11R6/lib/libGL.a.old
As jonny said, you need the buildessential package. If you are getting the
```
./tools/wineinstall: line 225: make: command not found
./tools/wineinstall: line 227: make: command not found
Compilation failed, aborting install.
```
you need this package.
To install it: 
```
sudo apt-get install build-essential
```
and GREAT HOWTO, thanks a million. I wish there was a +rep button :).

---

### Post by penndragonn on 2007-02-19
I am totally new to Linux...just got it installed after 3 days!  Whew!! I downloaded all the updates. This, by far,  was easy to understand somewhat. I didn't even know how to get into that Terminal window at first...found it   by just browsing around. It would be great if someone actually told us   ultra newbies what do do and how to do it from the start....I had no idea I had  to Copy and Paste those command lines into the terminal window...It was purely by chance, knowing a little something about DOS, that I was able to fugure it out. 
             So, everything was  going fine until I hit that one area   where the link was dead, and I got that error 404 message after trying to go to:

wget [http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz](http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz).

Now, I'm at a standstill, have absolutely no idea what to do, where to go, or how to do it.. Or even how to get back to the last entry I made in Terminal window that worked until I got that error above.  Most of what I see  here I don't even understand what the heck your all saying....the terminology is unclear to me. Perhaps I'm far to new at this to be trying to install WINE??? Any help and guidance would be great...Baby steps...please!!!!  Thank you all in advance.:confused:

---

### Post by penndragonn on 2007-02-19
Also,:mrgreen: 

I    used the link above to download WINE. It    downloaded fine, It's Some sort of zipped file, for lack of a better word. Ark program opened it, asked where I wanted it extracted. I gave it a folder name, and it gave me an error message...Now what...Boy is     this stuff confusing. I know learning a completely new OS will take time, so It's not bothering me too much, other then me feeling like a total idiot! :lolflag: 

Thanks again:mrgreen:

---

### Post by berteh on 2007-03-02
just to mention: an official Ubuntu package of a recent wine snapshot is readily available from 
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)  

Not cvs though, but it is updated quite regularly... just in case you need recent wine but not "to the edge".

I guess most of you already knew, but hope this helps the other ones with avoiding a manual compilation.

---

### Post by peetue on 2007-05-30
There's so many replies, aniwai: thanks for this guide, awsome.

---

### Post by peetue on 2007-05-30
I love this part, im waiting for it to install.
You never see this kinda "textflood" in windows, one of the biggest reasons why I love linux more.

---

### Post by Hendrick on 2007-06-04
Hello.

For some reason, I have never been able to access download.microsoft.com.  Not sure why, just have always been the case.  So it makes a bit of an issue for the DCOM98.  I downloaded it using an online proxy, but it didn't install with WineTools.  So, does anyone know which directory I would put it in to install it?

Thanks.

---

### Post by kezef on 2007-07-05
gg is all i can say.  you nailed the HOWTO genre.  ty for all the help. F cedega

---

### Post by Tarmael on 2007-09-08
> **Vaego said:**
> --
**4) Installing Winetools**

And finally, lets download the winetools.

```
wget http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz
```

This you may notice is off my personal webstorage, why did I do this? Because my links will never die ;), anyways lets start on installing this beast.
--

Links dead :(

---

### Post by KushMaster on 2007-09-09
I followed your steps loged in as root, now when i do ./tools/wineinstall it says, "The source directory is not writable. You probably extracted the sources as root. You should remove the source tree and extract it again as a normal user." How do i resolve this problem ?

---

### Post by KushMaster on 2007-09-10
Well i resolved my problem, but now your supposedley link that will never die is dead " wget [http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz](http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz) " Can you please redirect me to a working code or link for this file ? Thank You

---

### Post by Tarmael on 2007-09-10
Found the link.

here it is

[http://www.arte.unipi.it/Public/UNIX/winetools-211jo.tar.gz](http://www.arte.unipi.it/Public/UNIX/winetools-211jo.tar.gz)

---

### Post by Tarmael on 2007-09-10
Problem:

{standard input}: Assembler messages:
{standard input}:38: Error: suffix or operands invalid for `push'
{standard input}:39: Error: suffix or operands invalid for `push'
{standard input}:46: Error: suffix or operands invalid for `pop'
{standard input}:47: Error: suffix or operands invalid for `pop'
make[2]: *** [interlocked.o] Error 1
make[2]: Leaving directory `/home/tarmael/cvs/wine/libs/port'
make[1]: *** [port] Error 2
make[1]: Leaving directory `/home/tarmael/cvs/wine/libs'
make: *** [libs] Error 2

Compilation failed, aborting install.



This is from
./tools/wineinstall

after typing in yes etc.

---

### Post by Serax on 2007-09-18
does this not work with fiesty? i got some errors with winetools not working with any fiesty wine versions...

---

### Post by khristian on 2007-09-19
I got the same error here:

```
$ sudo make install
make[1]: Entrando no diretório `/home/kas/downloads/prog/wine_src/wine/tools'
make[1]: `makedep' está atualizado.
make[1]: Saindo do diretório `/home/kas/downloads/prog/wine_src/wine/tools'
make[1]: Entrando no diretório `/home/kas/downloads/prog/wine_src/wine/libs'
make[2]: Entrando no diretório `/home/kas/downloads/prog/wine_src/wine/libs/port'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2 -D__i386__  -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:38: Error: suffix or operands invalid for `push'
{standard input}:39: Error: suffix or operands invalid for `push'
{standard input}:46: Error: suffix or operands invalid for `pop'
{standard input}:47: Error: suffix or operands invalid for `pop'
make[2]: ** [interlocked.o] Erro 1
make[2]: Saindo do diretório `/home/kas/downloads/prog/wine_src/wine/libs/port'
make[1]: ** [port] Erro 2
make[1]: Saindo do diretório `/home/kas/downloads/prog/wine_src/wine/libs'
make: ** [libs] Erro 2
```


got wine from git and running Gutsy tribe 5. Any ideas?

---

### Post by Dark_X on 2007-09-23
Different error...
```
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o clipping.o codepage.o dce.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o text.o window.o winpos.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res    -o winex11.drv.so  -luser32 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/joe/cvs/wine/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/joe/cvs/wine/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

```

---

### Post by MMalen on 2007-10-03
```
                                      ./tools/wineinstall
WINE Installer v0.75

Warning !! wine binary (still) found, which may indicate
a (conflicting) previous installation.
You might want to abort and uninstall Wine first.
(If you previously tried to install from source manually, 
run 'make uninstall' from the wine root directory)
Running configure...

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.
```

Should I need to uninstal Wine first?

Also, this link is dead: [http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz](http://home.comcast.net/~themachinez/wine/winetools/winetools-211jo.tar.gz)

---

### Post by cbovet on 2007-11-08
Hmmmmm.. I need Direct3D and OpenGL support, but when I tried installing, something didn't work right.  I did enter the command in the tutorial that's supposed to give you Direct3D and OpenGL, but that didn't work either.  Sorry I don't have the log for the first problem, but here's the log it gave me after I did the part that's supposed to install wine (just before you do the extra WineTools setup).

I'm a very inexperienced Ubuntu user, and I'm trying to install Soldat (a 2d sidescroller game) but it doesn't seem to be working.  Any help would be greatly appreciated!  Do I really need to buy Cedega or subscribe to transgaming?  How do I get the time trial version?  The link in the "Ubuntu Hacks" book doesn't seem to work unless you subscribe to transgaming....

Here's part of the log (what I assume is the error part)  

configure: WARNING: No OpenGL library found on this system.
Wine will be build without OpenGL or Direct3D support.

configure: WARNING: FontForge is missing.
Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished.  Do 'make depend && make' to compile Wine.


We need to install wine as root user, do you want us to build wine,
'su root' and install Wine?  Enter 'no' to continue without installing
(yes/no)    


Again, I'm sorry if this is in the wrong section/already answered, etc.  Thanks!
Colin

---

### Post by tzes on 2007-11-10
well guys anyone got a link for the wine tools??Because the first link is dead and every other link i tried is taking too long to respond..

---

### Post by tzes on 2007-11-10
Ok i found the link for the winetools in the previous page but now i cannot find a link for the winfonts.tar.gz anyone having an alternative??
Or maybe the topic author can update his links plz!

---

### Post by Sil3n7 on 2008-03-08
i get the same error as Dark

```
make[2]: Entering directory `/home/drew/cvs/wine/dlls/winex11.drv'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o clipping.o codepage.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o text.o window.o winpos.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res  -o winex11.drv.so  -luser32 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/drew/cvs/wine/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/drew/cvs/wine/dlls'
make: *** [dlls] Error 2
```

not sure what to do here...hmmm

---

### Post by Spxza on 2008-04-05
If you're getting this:

```
make[2]: Entering directory `/home/drew/cvs/wine/dlls/winex11.drv'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./winex11.drv.spec    bitblt.o bitmap.o brush.o clipboard.o clipping.o codepage.o desktop.o dib.o dib_convert.o dib_dst_swap.o dib_src_swap.o event.o graphics.o init.o keyboard.o mouse.o opengl.o palette.o pen.o scroll.o settings.o text.o window.o winpos.o wintab.o x11ddraw.o x11drv_main.o xdnd.o xfont.o xim.o xinerama.o xrandr.o xrender.o xvidmode.o     version.res  -o winex11.drv.so  -luser32 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -lXext -lX11  ../../libs/port/libwine_port.a  
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/drew/cvs/wine/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/drew/cvs/wine/dlls'
make: *** [dlls] Error 2
```

This worked for me, while compiling wine 32 on a 64 bit system:: sudo ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so

You may also want: sudo ln -s /usr/lib32/libX11.so.6 /usr/lib32/libX11.so

Most other errors seem to be missing packages. Search for the packages in Synaptic and install the -dev versions.Or, you could try:
sudo apt-get build-dep wine

For everyone having this error:
```

make[2]: Entering directory `/.../wine/libs/port'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2 -D__i386__  -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:38: Error: suffix or operands invalid for `push'
{standard input}:39: Error: suffix or operands invalid for `push'
{standard input}:46: Error: suffix or operands invalid for `pop'
{standard input}:47: Error: suffix or operands invalid for `pop'
make[2]: *** [interlocked.o] Error 1
make[2]: Leaving directory `/.../wine/libs/port'
make[1]: *** [port] Error 2
make[1]: Leaving directory `/.../wine/libs'
make: *** [libs] Error 2

```
goto [http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit") 

You may need to create some more symlinks based on what ./configure complains about (and, if you want the extra functionality)

---

### Post by Patb on 2008-04-06
> **Spxza said:**
> If you're getting this:

```
...
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed...
```

This worked for me, while compiling wine 32 on a 64 bit system:: sudo ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so

You may also want: sudo ln -s /usr/lib32/libX11.so.6 /usr/lib32/libX11.so
Thanks Spxza.  

I am compiling on a 32 bit system.  I do not have the directory /usr/lib32/ but only /usr/lib/ so I had to edit the command accordingly.  
```
sudo ln -s /usr/lib/libXext.so.6 /usr/lib/libXext.so
```
Then it worked fine.  

Cheers, Pat.

---

### Post by j3susxxx on 2009-03-08
when i type ./tools/wineinstall
i get this error 

checking for -lfreetype... not found
configure: error: FreeType development files not found. Fonts will not be built.
Use the --without-freetype option if you really want this.

Configure failed, aborting install.

how can i fix that

---

