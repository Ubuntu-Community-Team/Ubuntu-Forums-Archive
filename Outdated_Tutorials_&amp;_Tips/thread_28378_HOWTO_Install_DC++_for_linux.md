---
title: "HOWTO: Install DC++ for linux"
date: 2005-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by wbeck85 on 2005-04-19
Hey Y'all! I just successfully installed DC++ for linux, that means, no confusing dcgui or dcgui-qt. It looks and behaves just like DC++ for Windows, but it looks better, even. No longer do I have to go through wine, and that makes me happy. Here's a helpful howto to get you running DC++ natively in linux.

[[IMG]http://img26.echo.cx/img26/9961/dcpp15gc.th.jpg[/IMG]](http://img26.echo.cx/my.php?image=dcpp15gc.jpg)

Here goes:
First, you must download the sources from the linuxdcpp website via cvs. They do not have any binaries available.
so:
```
$ sudo cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
   (leave password blank and hit enter)

$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
```

(This put a linuxdcpp folder in my home directory. I left it there, you may move it somewhere else if you would like to. Just keep in mind that the commands that follow assume the folder is in your home directory)

Ok, so you have the sources now, but you need to compile them and ubuntu does not come packaged with all the requirements. you need:

libgtk2.0-dev
libgtkmm-2.4-dev
libglademm-2.4-dev
zlib1g-dev
libbz2-dev
g++-3.4
libgtk2.0-bin
libgtk2.0-0
libgtk2.0-common
libgtkmm-2.4-1
libglademm-2.4-1

To make sure this is all installed apt-get the following. The packages you have installed already will be ignored, or upgraded (I think)
```
sudo apt-get install libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1 libglademm-2.4-1 scons
```

Also apt-get install your kernel headers.

This next part is apparently unnecessary. (Thanks to Chousuke for pointing that out) But I don't really feel like removing it because it took me a while.... So ignore the immediately following quote insert, unless you get a missing libglade error when running scons later on.
> Most of the stuff can be found in the repositories. However, I could not find libglade 2.4 so the next part of this howto is how to get and install libglade 2.4.

Go to [http://www.zentek-international.com/mirrors/gnome/sources/libglade/2.4/](http://www.zentek-international.com/mirrors/gnome/sources/libglade/2.4/) and download the most recent sources.
Extract them to a directory, I use ~/src (i made that directory for myself for sources i download)
To compile this, you will need to apt-get:
```
sudo apt-get install libglib2.0-dev libxml1 libxml2-dev
```

and apt-get whatever else you get yelled at for when trying to ./configure
so:
```
$ cd ~/src/libglade-2.4*
$ sudo ./configure
$ sudo make
$sudo make install
```

(So, hopefully, libglade-2.4 has successfully installed.

Next is to install the actual dcpp program so switch to the linuxdcpp directory that you downloaded)
```
$ cd ~/linuxdcpp  (mine was my home folder)

	(then run scons, which compiles the program for you)

$ sudo scons
```

And there you have it. It should work. The executable is in the ~/linuxdcpp directory. You should just be able to double click on it to run the program. To get it to show up in the the Gnome menu however, you will need to get the program Menu Editor. You can find that [here](http://dev.realistanew.com/menu-editor/menueditor_0.4.3ubuntu1_all.deb). To install this program, download it, then switch to the directory to which you downloaded the .deb file and:
```
$ sudo dpkg -i menueditor*
```
Then open the program, which can be found in Applications>System Tools>Menu Editor. On the right, Enter the name you would like to show up in the menu, any comments you would like to enter about dcpp, and the command which will be: ```
/directory/in/which/the/executable/subsides/dcpp
```, select an icon if that pleases you, and a category. Click save, exit menueditor and see if your program works (I hope it does!)

Well, good luck with this. I do not know how many people use DC++, but hopefully this howto works for those who want to use it.

This is my first howto, and I'm sure it needs work. Please, give me your feedback and I will edit the howto as needed.

(Edited 5/20/05 @ 1:30 pm to clean stuff up, added Chousuke's info in here, so thanks to him for that.)

---

### Post by bolamix on 2005-04-20
Heya!
Thanks for this howto, I've managed to install Valknut (dcgui-qt) but i'm not very satisfied with it... so installing dc++ on my linux box would be great :) The whole procedure went nice and smooth up until the **$ sudo scons** command. Here's the output:```
scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for C header file asm/atomic.h... yes
Checking for PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP in pthread.h... ok
scons: done reading SConscript files.
scons: Building targets ...
g++-3.4 -DXTHREADS -Wl,--export-dynamic -pthread -pthread -DHAVE_ASM_ATOMIC_H -D_GNU_SOURCE -DHAVE_DECL_PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP -I. -DENABLE_BINRELOC -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c -o build/client/ADLSearch.o client/ADLSearch.cpp client/FinishedManager.cpp client/Socket.cpp client/AdcCommand.cpp client/HashManager.cpp client/StringDefs.cpp client/AdcHub.cpp client/HttpConnection.cpp client/StringTokenizer.cpp client/BZUtils.cpp client/HubManager.cpp client/Text.cpp client/BufferedSocket.cpp client/LogManager.cpp client/Thread.cpp client/Client.cpp client/NmdcHub.cpp client/TigerHash.cpp client/ClientManager.cpp client/QueueManager.cpp client/TimerManager.cpp client/ConnectionManager.cpp client/ResourceManager.cpp client/UploadManager.cpp client/CryptoManager.cpp client/SFVReader.cpp client/User.cpp client/DCPlusPlus.cpp client/SearchManager.cpp client/UserConnection.cpp client/DirectoryListing.cpp client/ServerSocket.cpp client/Util.cpp client/DownloadManager.cpp client/SettingsManager.cpp client/ZUtils.cpp client/Encoder.cpp client/ShareManager.cpp client/stdinc.cpp client/Exception.cpp client/SimpleXML.cpp
g++-3.4: --export-dynamic: linker input file unused because linking not done
cc1plus: error: unrecognized command line option "--export-dynamic"
scons: *** [build/client/ADLSearch.o] Error 1
scons: building terminated because of errors.
```

I don't know what I can do to avoid this error, if anything. I'm running Warty, not Hoary, cuz Valknut wouldn't compile on Hoary; could that be the reason? Thanks for any ideas!

---

### Post by Chousuke on 2005-04-20
The OP's how-to is now correct, but I'll leave this here nonetheless. :)

(I'll use code tags to prevent smilies)
Do this:
```

(no need for sudo yet. Do this in ~/ somewhere.)
$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login 
(No password)
$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp

You need the following development packages: 
libgtk2.0-dev
libgtkmm-2.4-dev # I believe this is required since DC++ is a C++ app.
libglademm-2.4-dev
zlib1g-dev
libbz2-dev

downloading kaffe-pthread isn't required, since pthreads is a kernel feature

you need the following programs/libraries also:
(some may be already installed)
scons
g++-3.4
libgtk2.0
libgtkmm-2.4-1
libglademm-2.4-1

after this, just run scons to build. (sudo/root is still unneeded ;))

```

Follow OP's advice for menu entries etc.

---

### Post by bolamix on 2005-04-20
[QUOTE=Chousuke]The original poster's how-to is slightly flawed. It does work, but there's no need to download libglade2.4 source and compile them: Here's an easier and cleaner method:

(I'll use code tags to prevent smilies)
Do this:
```

(no need for sudo yet. Do this in ~/ somewhere.)
$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login 
(No password)
$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp

You need the following development packages: 
libgtk2.0-dev
libgtkmm-2.4-dev # I believe this is required since DC++ is a C++ app.
libglademm-2.4-dev
zlib1g-dev
libbz2-dev

downloading kaffe-pthread isn't required, since pthreads is a kernel feature

you need the following programs/libraries also:
(some may be already installed)
scans
g++-3.4
libgtk2.0
libgtkmm-2.4-1
libglademm-2.4-1

after this, just run scons to build. (sudo/root is still unneeded ;))

```

Follow OP's advice for menu entries etc.[/QUOTE]
 Thx Chousuke, but I still get the same error... Can anyone help please? Tia ;)

---

### Post by destino on 2005-04-20
Try this:

[http://www.ubuntuforums.org/showthread.php?t=17514&page=2&pp=10&highlight=scons](http://www.ubuntuforums.org/showthread.php?t=17514&page=2&pp=10&highlight=scons)

---

### Post by bolamix on 2005-04-20
[QUOTE=destino]Try this:

[http://www.ubuntuforums.org/showthread.php?t=17514&page=2&pp=10&highlight=scons](http://www.ubuntuforums.org/showthread.php?t=17514&page=2&pp=10&highlight=scons)[/QUOTE]
 Thx :) I got the same advice on the #linuxdcpp irc channel, and it worked like a dream :D So, to all those who wanna try out dc++ on linux, [update your scons first](http://www.scons.org/download.php) ;)

---

### Post by zwaardmeester on 2005-04-20
Excellent how-to, I got it working in about 3 minutes! There is only tiny little thing though, I needed a few more packages because I got the 

>> Did not find the header time.h

error. Then I installed the "build-essentials" package and everything worked fine. It was just a couple of standard-C library's missing. (ps. I just re-installed Ubuntu 1 hour ago, that's because I didn't have them)

cheers  \\:D/ ,

Leo

---

### Post by Bassism on 2005-04-20
[QUOTE=zwaardmeester]Excellent how-to, I got it working in about 3 minutes! There is only tiny little thing though, I needed a few more packages because I got the 

>> Did not find the header time.h

error. Then I installed the "build-essentials" package and everything worked fine. It was just a couple of standard-C library's missing. (ps. I just re-installed Ubuntu 1 hour ago, that's because I didn't have them)

cheers  \\:D/ ,

Leo[/QUOTE]
 Very cool.
Thanka!

---

### Post by ow50 on 2005-04-20
I downloaded and installed this a while ago and it didn't really require other than getting from cvs and sconcssing.

Does the search work in your latest cvs versions?

---

### Post by martinez9049 on 2005-04-21
first off thanks for this tutorial cuz wine sucks and so does dcgui...but, when i run cvs i get bash: cvs: command not found. what's up with that?

thanks,
ismael m

---

### Post by bolamix on 2005-04-21
I was chatting yesterday with a couple people on #linuxdc++ about the few controls that aren't yet included in this program, like the ability to add a hub to Favorites with the /fav command. And lo and behold, a patch is available for this command. I don't know how long it will remain available, but for now, thanks to s4kk3, it is.
I had the prog already compiled so i did the following:
```
$ cd your_linuxdcpp_folder
$ wget http://s4kk3.servebeer.com/patches/user-commands-0.02.diff
$ patch -p1 < user-commands-0.02.diff
$ scons
```I don't remember having to install extra libs, but it probably depends on your system.

Also, bear in mind that this prog is "under development", so a few features are missing: only the "Nick" and "Sharesize" columns are visible in the userlist, some nicks don't seem to show (Ptokax bots , for example), and chat-logging seems not to work (upload- and download-logging work fine though). But since Valknut seems not to be working with Hoary (I couldn't compile the latest version, same goes with a couple friends), this makes a fine replacement for all those DC-addicted people out there :grin:

---

### Post by warlock on 2005-04-22
im having trouble with the SEARCH function.. , he keep saying "searching" without results. did he works to u guys?

---

### Post by kb00heda on 2005-04-22
At first it didn't work for me either --- but now it does: 

I switched to active mode, set the UDP/TCP traffic to go through port 9176, and opened that one up in Firestarter (my firewall). Also I had to forward the same port to my "DC++ computer" in the configuration of my router. Ever since it has worked nicely. 

Otherwise you could try passive mode? The downside is that one can't connect to other users in passive mode, i.e., the number of hits may decrease. On the other hand some is better than none!   :)

---

### Post by XDevHald on 2005-04-22
Hmm, never had a problem connecting to a cvs site, it goes to the password thing for it, then I press enter, and it just takes me back to my normal root ****@Ubuntu:/home/user #

But after that, it doesn't do anything ](*,)

---

### Post by jerome bettis on 2005-04-23
[QUOTE=Doc]Hmm, never had a problem connecting to a cvs site, it goes to the password thing for it, then I press enter, and it just takes me back to my normal root ****@Ubuntu:/home/user #

But after that, it doesn't do anything ](*,)[/QUOTE]
 ^ yeah i had the same thing happen.  there's two cvs commands you need to run.  see the original post.

dc++ rules ... i have to get active mode up and running through my router and find a good hub that doesn't have a huge share .. i only have like 1 gig of stuff on my hard drive, i keep everything on an external drive.

---

### Post by jerome bettis on 2005-04-23
Segmentation fault

oh noes!!!1

---

### Post by XDevHald on 2005-04-23
Ok, I found the bottom command for the cvs, I did see it last night but it didn't register to my head to copy/paste it ](*,)


But it does work now, just need to get it all setup :) 

Cheers **kb00heda!**

---

### Post by jerome bettis on 2005-04-24
does anybody else find this program to be incredibly unstable??

---

### Post by ow50 on 2005-04-24
[QUOTE=jerome bettis]does anybody else find this program to be incredibly unstable??[/QUOTE]

Unstable, yes. Incredibly unstable, no considering it's development software with no releases made yet. I reckon software people would call this alpha.

It might be a good alternative to people wanting a gtk dc-client. And Valknut doesn't always work that well either.

---

### Post by jerome bettis on 2005-04-25
ok i just tried the other dc clients and they're much worse.

i'm looking forward to the official release ... it's been running ok now.  but earlier this afternoon it would just keep crashing in different ways.

---

### Post by NeoChaosX on 2005-04-25
There's a lot of features missing vs. regular DC++ (or BCDC++ when I use Windows), but it's certainly a step up from Valknut (which can't even sync to the GNOME theme).

---

### Post by docomo on 2005-04-25
Some people are running dc++ successfully under wine. I haven't tried it myself but here's a guide if you want to try it:

[http://funkfunk.orcon.net.nz/dcwine.html]("http://funkfunk.orcon.net.nz/dcwine.html")

---

### Post by cajunaggie on 2005-04-29
For some reason the second cvs command won't run in the shell. Whenever I run this:```
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
``` I get this:```
bash: cvs: command not found
```
Any suggestions?

---

### Post by bolamix on 2005-04-29
[QUOTE=cajunaggie]For some reason the second cvs command won't run in the shell. Whenever I run this:```
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
``` I get this:```
bash: cvs: command not found
```
Any suggestions?[/QUOTE]
I got this error too, as I hadn't installed cvs. I opened Synaptic, searched for it there and installed it, but i guess "sudo apt-get install cvs" should do the trick too ;)

---

### Post by cajunaggie on 2005-04-29
Alright I did that and now I tried running ```
sudo scons
``` and I got this ```
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... no
Did not find the header time.h
Can't live without it, sorry

```

Suggestions?

---

### Post by wbeck85 on 2005-04-29
[QUOTE=cajunaggie]Alright I did that and now I tried running ```
sudo scons
``` and I got this ```
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... no
Did not find the header time.h
Can't live without it, sorry

```

Suggestions?[/QUOTE]
 Have you installed your kernel headers? I dont know if that will solve the problem but if you already have installed the packages specified in the first post, I can't think of any other problems.

---

### Post by mird on 2005-04-29
[QUOTE=cajunaggie]```
bash: cvs: command not found
```
Any suggestions?[/QUOTE]
You'll need to install the cvs and build-essentials packages... 
```
sudo apt-get install cvs build-essentials
```
... also make sure you also have ALL the packages listed in the first post of this thread.

---

### Post by sanjeevdas on 2005-04-30
I get the following compilation errors:


sanjeev@ubuntu:~/linuxdcpp $ scons
scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for C header file asm/atomic.h... yes
Checking for PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP in pthread.h... ok
scons: done reading SConscript files.
scons: Building targets ...
g++ -DXTHREADS -pthread -pthread -DHAVE_ASM_ATOMIC_H -D_GNU_SOURCE -DHAVE_DECL_PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP -I. -DENABLE_BINRELOC -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c -o build/client/ADLSearch.o client/ADLSearch.cpp
In file included from client/DirectoryListing.h:26,
                 from client/ADLSearch.h:237,
                 from client/ADLSearch.cpp:27:
client/Util.h: In instantiation of `IsOfClassType<std::string>':
client/Util.h:52:   instantiated from `TypeTraits<std::string>'
client/User.h:123:   instantiated from here
client/Util.h:47: error: invalid use of undefined type `class
   IsOfClassType<std::string>'
client/Util.h:42: error: declaration of `class IsOfClassType<std::string>'
client/Util.h:47: error: enumerator value for `Result' not integer constant
client/Util.h: In instantiation of `IsOfClassType<CID>':
client/Util.h:52:   instantiated from `TypeTraits<CID>'
client/User.h:131:   instantiated from here
client/Util.h:47: error: invalid use of undefined type `class
   IsOfClassType<CID>'


Help?

---

### Post by sanjeevdas on 2005-04-30
sorry, my bad. I apt got gcc 3.4 that didn't get g++ 3.4. Got g++ 3.4 and it is compiling now.

---

### Post by BoHu on 2005-04-30
I get an error message right from the start -

bash: cvs: command not found

---

### Post by NeoChaosX on 2005-04-30
[QUOTE=BoHu]I get an error message right from the start -

bash: cvs: command not found[/QUOTE]
sudo apt-get install cvs

I had this problem at first, too.

---

### Post by Dandy on 2005-04-30
[QUOTE=bolamix] But since Valknut seems not to be working with Hoary (I couldn't compile the latest version, same goes with a couple friends), this makes a fine replacement for all those DC-addicted people out there :grin:[/QUOTE]

I'm using Hoary and Valknut 0.3.7. from this site (.deb package)

[http://peppesbodega.nu/turban/tumbo/Debian%20Packages/Apps/Valknut/](http://peppesbodega.nu/turban/tumbo/Debian%20Packages/Apps/Valknut/)

and it's working good.

---

### Post by BoHu on 2005-05-01
[QUOTE=NeoChaosX]sudo apt-get install cvs

I had this problem at first, too.[/QUOTE]


thanks :-)

---

### Post by CocaCola on 2005-05-07
i tried to install dcpp but i had the following error


cocacola@coke:~/linuxdcpp$ sudo scons
scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... no
Did not find the pthread library, exiting!
Note: You might have the lib but not the headers

Im new with using linux... so witch libary should i install?

---

### Post by bolamix on 2005-05-08
[QUOTE=Dandy]I'm using Hoary and Valknut 0.3.7. from this site (.deb package)

[http://peppesbodega.nu/turban/tumbo/Debian%20Packages/Apps/Valknut/](http://peppesbodega.nu/turban/tumbo/Debian%20Packages/Apps/Valknut/)

and it's working good.[/QUOTE]
Hey thanx for the tip, I'll try it out ;)

---

### Post by yage on 2005-05-17
Just a note. If gnome-menu-editor does'nt work you can add this by hand:

sudo gedit /usr/share/applications/dc++.desktop

And filling in:

[Desktop Entry]
Name=DC++
Comment=Direct Connect
Exec=/whre/you/put/cvs/linuxdcpp/dcpp
Icon=dc++.svg
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;Application;

The Icon, i found here: [http://www.gnome-look.org/content/show.php?content=23306](http://www.gnome-look.org/content/show.php?content=23306)
Download it and type;
sudo tar xzvf 23306-dc++.svg.tar.gz -C /usr/share/pixmaps

---

### Post by stepper on 2005-05-17
A very fine HOWTO! keep it up man. went flawlessly.

---

### Post by cymkhat on 2005-05-25
i have a fedora core 2 in my system. this is a wrong place to post a fedora core 2 problem but i thought people have some good experience installing dc++ on linux. that is why i am posting it here.

i got linuxdcpp from the cvs
then cd ~/linuxdcpp

when i do 
[root@Dr-Goud linuxdcpp]# scons

Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... failed
libglade >= 2.4 not found.

so i downloaded the latest libglade-2.4.0.tar.bz

then i installed libglade-2.4.0 in my system.
still i get the same error. i dont know why.
kindly help me.

cymkhat

---

### Post by meastp on 2005-05-27
[QUOTE=CocaCola]i tried to install dcpp but i had the following error


cocacola@coke:~/linuxdcpp$ sudo scons
scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... no
Did not find the pthread library, exiting!
Note: You might have the lib but not the headers

Im new with using linux... so witch libary should i install?[/QUOTE]

I'm having exactly the same problem... Anyone?

---

### Post by DrMoxie on 2005-05-27
Just wanted to say thanks for the great How-To; had DC++ up and running in under 30 minutes.  \\:D/

---

### Post by Orunitia on 2005-05-28
Thanks, works perfectly. Nice that I don't have to run DC++ through wine anymore.

---

### Post by hamil on 2005-05-28
Hello!

When trying to install Dc++, i do get some errors...
scons runs for 20 sec, and then I get this error.
Anyone have any inputs that can help me further on???

Thanx in advance
Brgds
Lasse

```

client/Speaker.h:99:   instantiated from `void Speaker<Listener>::addListener(Listener*) [with Listener = BufferedSocketListener]'
client/UserConnection.h:354:   instantiated from here
/usr/include/c++/3.4/bits/stl_uninitialized.h:112: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-3.4/README.Bugs>.
scons: *** [build/client/QueueManager.o] Error 1
scons: building terminated because of errors.

```

---

### Post by greendots on 2005-05-29
Check this!  :) 

[http://www.broadbandreports.com/faq/6514](http://www.broadbandreports.com/faq/6514)


I haven't tried any of these client yet..

---

### Post by xristos on 2005-06-03
I have a very good internet connection and i never had a problem connecting to any site . 
I am using a vpn connection . When I try to connect through cvs i get timed out .
```
xristos@ubuntu:/$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Logging in to :pserver:anonymous@cvs.linuxdcpp.berlios.de:2401/cvsroot/linuxdcppCVS password:
cvs [login aborted]: connect to cvs.linuxdcpp.berlios.de(195.37.77.137):2401 failed: Connection timed out
``` 

Any ideas ?

---

### Post by JeffBlouin on 2005-06-07
[QUOTE=wbeck85]Have you installed your kernel headers? I dont know if that will solve the problem but if you already have installed the packages specified in the first post, I can't think of any other problems.[/QUOTE]


Hi Im new with linux and i get the same error as the person you answered when i try to compile DC++ for linux

scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... no
Did not find the header time.h
Can't live without it, sorry

Im not familiar with headers and i dont know the ones i need to install and how to chose them. I Run ubuntu 5.04 on a amd athlon 700 with the i386 

I have installed all the other packages 
Thanks

---

### Post by weazle on 2005-06-08
[QUOTE=wbeck85]Hey Y'all! I just successfully installed DC++ for linux, that means, no confusing dcgui or dcgui-qt. It looks and behaves just like DC++ for Windows, but it looks better, even. No longer do I have to go through wine, and that makes me happy. Here's a helpful howto to get you running DC++ natively in linux.

[[IMG]http://img26.echo.cx/img26/9961/dcpp15gc.th.jpg[/IMG]](http://img26.echo.cx/my.php?image=dcpp15gc.jpg)

Here goes:
First, you must download the sources from the linuxdcpp website via cvs. They do not have any binaries available.
so:
```
$ sudo cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
   (leave password blank and hit enter)

$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
```

(This put a linuxdcpp folder in my home directory. I left it there, you may move it somewhere else if you would like to. Just keep in mind that the commands that follow assume the folder is in your home directory)

Ok, so you have the sources now, but you need to compile them and ubuntu does not come packaged with all the requirements. you need:

libgtk2.0-dev
libgtkmm-2.4-dev
libglademm-2.4-dev
zlib1g-dev
libbz2-dev
g++-3.4
libgtk2.0-bin
libgtk2.0-0
libgtk2.0-common
libgtkmm-2.4-1
libglademm-2.4-1

To make sure this is all installed apt-get the following. The packages you have installed already will be ignored, or upgraded (I think)
```
sudo apt-get install libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1 libglademm-2.4-1 scons
```

Also apt-get install your kernel headers.

This next part is apparently unnecessary. (Thanks to Chousuke for pointing that out) But I don't really feel like removing it because it took me a while.... So ignore the immediately following quote insert, unless you get a missing libglade error when running scons later on.


Next is to install the actual dcpp program so switch to the linuxdcpp directory that you downloaded)
```
$ cd ~/linuxdcpp  (mine was my home folder)

	(then run scons, which compiles the program for you)

$ sudo scons
```

And there you have it. It should work. The executable is in the ~/linuxdcpp directory. You should just be able to double click on it to run the program. To get it to show up in the the Gnome menu however, you will need to get the program Menu Editor. You can find that [here](http://dev.realistanew.com/menu-editor/menueditor_0.4.3ubuntu1_all.deb). To install this program, download it, then switch to the directory to which you downloaded the .deb file and:
```
$ sudo dpkg -i menueditor*
```
Then open the program, which can be found in Applications>System Tools>Menu Editor. On the right, Enter the name you would like to show up in the menu, any comments you would like to enter about dcpp, and the command which will be: ```
/directory/in/which/the/executable/subsides/dcpp
```, select an icon if that pleases you, and a category. Click save, exit menueditor and see if your program works (I hope it does!)

Well, good luck with this. I do not know how many people use DC++, but hopefully this howto works for those who want to use it.

This is my first howto, and I'm sure it needs work. Please, give me your feedback and I will edit the howto as needed.

(Edited 5/20/05 @ 1:30 pm to clean stuff up, added Chousuke's info in here, so thanks to him for that.)[/QUOTE]
 Cool HOWTO worked like a charm for me :-) Thanks :-)

---

### Post by Wingdings on 2005-06-10
Everything's worked nicely so far, except for one thing. Hashing my files (files on mounted NTFS partitions) is really really slow, only 3-4 MB/s. In Windows XP, the hashing has the speed of ~30 MB/s. What's up with that?

---

### Post by danip on 2005-06-12
Good howto works well for me.  The only issue i have with the program is there is no option to have right clickers.  I operate a hub and not having those is kind of a pain :(

---

### Post by wbeck85 on 2005-06-12
[QUOTE=Wingdings]Everything's worked nicely so far, except for one thing. Hashing my files (files on mounted NTFS partitions) is really really slow, only 3-4 MB/s. In Windows XP, the hashing has the speed of ~30 MB/s. What's up with that?[/QUOTE]
 could that have something to do with hdparm or dma settings on the drive itself? possibly not related to dc++?

I really could'nt tell you, but i figured that that may have something to do with it?

---

### Post by Scio on 2005-06-18
My apt-get doesn't find scons: E: Couldn't find package scons

Where to get it?

Edit: I fixed it by uncommenting lines
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) hoary universe
in /etc/apt/sources.list

---

### Post by lovemaker on 2005-06-24
hy all. i`m a linux beginner. I work on a Fedora core 4 system and i tryed to install dc++ for linux .. but i have some serious problem and i don't know how to resolv them. I'm beginner so please be patient with me ...
when i type   "sudo scons" in console ... i get this error message ...

[...]
client/Thread.h:103: error: 'atomic_inc' was not declared in this scope
client/Thread.h: In static member function 'static long int Thread::safeDec(volatile long int&)':
client/Thread.h:113: error: 'atomic_dec' was not declared in this scope
scons: *** [build/client/ADLSearch.o] Error 1
scons: building terminated because of errors.

please help pe to fix this problem .,... thanks

---

### Post by DiESELMuSA on 2005-06-26
On my second day with Ubuntu i compiled DC++ sucessfully \\:D/ 
Thanks for this excellent guide!

---

### Post by pelago on 2005-06-27
[QUOTE=Wingdings]Everything's worked nicely so far, except for one thing. Hashing my files (files on mounted NTFS partitions) is really really slow, only 3-4 MB/s. In Windows XP, the hashing has the speed of ~30 MB/s. What's up with that?[/QUOTE]
I believe the Linux NTFS drivers are simply slower than native NTFS. So this isn't a DC++ problem.

---

### Post by Keeper on 2005-07-07
g++ 3.4scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for C header file asm/atomic.h... yes
Checking for PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP in pthread.h... ok
scons: done reading SConscript files.
scons: Building targets ...
g++ -DXTHREADS -D_REENTRANT -DXUSE_MTSAFE_API -pthread -pthread -DHAVE_ASM_ATOMIC_H -D_GNU_SOURCE -DHAVE_DECL_PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP -I. -DENABLE_BINRELOC -D_FILE_OFFSET_BITS=64 -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib64/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/freetype2/config -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -c -o build/client/ADLSearch.o client/ADLSearch.cpp
In file included from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/algorithm:65,
                 from client/stdinc.h:52,
                 from client/ADLSearch.cpp:24:
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/stl_algobase.h:64:28: error: bits/c++config.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/stl_algobase.h:69,
                 from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/algorithm:65,
                 from client/stdinc.h:52,
                 from client/ADLSearch.cpp:24:
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/iosfwd:45:29: error: bits/c++locale.h: No such file or directory
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/iosfwd:46:25: error: bits/c++io.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/memory:54,
                 from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/stl_tempbuf.h:64,
                 from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/stl_algo.h:65,
                 from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/algorithm:68,
                 from client/stdinc.h:52,
                 from client/ADLSearch.cpp:24:
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/allocator.h:52:31: error: bits/c++allocator.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/basic_string.h:45,
                 from /usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/string:52,
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/stringfwd.h:49: error: declaration of 'struct std::allocator<char>'
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/basic_string.h: In member function 'bool std::basic_string<_CharT, _Traits, _Alloc>::_Rep::_M_is_shared() const [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]':
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/basic_string.h:851:   instantiated from 'void std::basic_string<_CharT, _Traits, _Alloc>::push_back(_CharT) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]'
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/basic_string.h:771:   instantiated from 'std::basic_string<_CharT, _Traits, _Alloc>& s td::basic_string<_CharT, _Traits, _Alloc>::operator+=(_CharT) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]'
client/Util.h:312:   instantiated from here
/usr/lib/gcc/x86_64-redhat-linux/4.0.0/../../../../include/c++/4.0.0/bits/basic_string.h:186: error: 'const struct std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep' has no member named '_M_refcount'
scons: *** [build/client/ADLSearch.o] Error 1
scons: building terminated because of errors.

---

### Post by mird on 2005-07-07
If you're having trouble compiling and can't figure it out yourself then just install it the [easy way](http://www.ubuntuforums.org/showthread.php?t=42084).

---

### Post by Keeper on 2005-07-08
Im running Fedora core 4

---

### Post by Embalmedlenin on 2005-07-25
Awsome guide
followed everything to the number and it worked perfectly.
Now i got my Dc++ on my linux box
thanks!!

---

### Post by dasunst3r on 2005-08-29
Thanks a lot... it works! :)

---

### Post by daageep on 2005-08-31
Works --so far-- perfectly on Debian linux 2.6.8 kernel. I was *thissss* close in installing XP on my old, old IBM laptop just to connect to my university's private hub. That is until I found this thread in google. Thank you so much.

---

### Post by tpls on 2005-09-23
I'm using Ubuntu 5.04 and when I run scons the following will happen:
```

#:~/linuxdcpp$ sudo scons
Password:
scons: Reading SConscript files ...
Checking for g++ >= 3.4...failed
Found g++-3.4
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP in pthread.h... ok
scons: done reading SConscript files.
scons: Building targets ...
g++-3.4 -DXTHREADS -pthread -pthread -DTARGET_I386 -DHAVE_ASM_ATOMIC_H -D_GNU_SOURCE -DHAVE_DECL_PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP -I. -DENABLE_BINRELOC -D_FILE_OFFSET_BITS=64 -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c -o build/client/QueueManager.o client/QueueManager.cpp
/usr/include/c++/3.4/ext/mt_allocator.h: In instantiation of `void __gnu_cxx::__mt_alloc<_Tp>::deallocate(_Tp*, size_t) [with _Tp = UserConnectionListener*]':
/usr/include/c++/3.4/bits/stl_vector.h:117:   instantiated from `void std::_Vector_base<_Tp, _Alloc>::_M_deallocate(_Tp*, size_t) [with _Tp = UserConnectionListener*, _Alloc = std::allocator<UserConnectionListener*>]'
/usr/include/c++/3.4/bits/vector.tcc:139:   instantiated from `std::vector<_Tp, _Alloc>& std::vector<_Tp, _Alloc>::operator=(const std::vector<_Tp, _Alloc>&) [with _Tp = UserConnectionListener*, _Alloc = std::allocator<UserConnectionListener*>]'
client/Speaker.h:58:   instantiated from `void Speaker<Listener>::fire(T0, const T1&, const T2&) [with T0 = AdcCommand::Type<5264723u>, T1 = UserConnection*, T2 = AdcCommand, Listener = UserConnectionListener]'
client/UserConnection.h:303:   instantiated from here
/usr/include/c++/3.4/ext/mt_allocator.h:482: internal compiler error: Muistialueen ylitys
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-3.4/README.Bugs>.
scons: *** [build/client/QueueManager.o] Error 1
scons: building terminated because of errors.
#:~/linuxdcpp$

```

Please, can somebody help me to fix this problem? What should I do next?

---

### Post by tpls on 2005-09-24
Ok, problem solved. I just installed the dc++ via the easy way.

---

### Post by burk on 2005-10-06
I get this message when i try to install the required packages:
```
The following packages have unmet dependencies:
  g++: Depends: g++-3.3 (>= 1:3.3.5-1) but it is not going to be installed
  g++-3.4: Depends: libstdc++6-dev (>= 3.4.3-9ubuntu4) but it is not going to be installed
  libbz2-dev: Depends: libc6-dev but it is not going to be installed
  libgtk2.0-dev: Depends: libglib2.0-dev (>= 2.4.1-2) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.5.1) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libx11-dev but it is not going to be installed or
                          xlibs-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed or
                          xlibs-dev but it is not going to be installed
  libgtkmm-2.4-dev: Depends: libglibmm-2.4-dev (>= 2.6.0) but it is not going to be installed
  zlib1g-dev: Depends: libc6-dev but it is not going to be installed or
                       libc-dev
E: Broken packages

```
Im not so good at packages and all that so can someone please point me in the right directions??

---

### Post by burk on 2005-10-07
Anyone??

---

### Post by johannes on 2005-10-08
Have you enabled the [extra repositories]("http://ubuntuguide.org/#extrarepositories")? Try installing the package build-essential.

---

### Post by Owdy on 2005-10-26
How can i use active mode? I have opened one port via NAT, but it isnt working.

---

### Post by unf on 2005-10-26
[QUOTE=Owdy]How can i use active mode? I have opened one port via NAT, but it isnt working.[/QUOTE]
Avaa portit tcp 412 ja udp1412 siihen ip:seen jossa sun konees on ja sitten tunget sun ulkosen ip:n sinne.. ja active mode pitäs toimia.  Mikäs ADSL purkki sulla on?

Open Ports tcp 412 and upd 1412 to dhcp ip that you have in your ubuntu dcpp machine, then just put your external.. its should fine then.  What is your ADSL modem?

---

### Post by Owdy on 2005-10-26
Zyxel 660H-61. I dont have firewall on, so how do i open these ports? Shouldnt they be open if theres no firewall?

---

### Post by meastp on 2005-10-26
I'm having trouble with this also. I have set the port to 4000 in DCPP, and I have opened port 4000 UDP and TCP in my NAT-router.

---

### Post by alekz on 2005-10-27
Hey dude you are the one :P before ubuntu i had fedora and i tried months to install dcpp and i never could but tonight took me just 10 minutes thanks :)

alekz *at* alekz *dot* com *dot* mx

---

### Post by unf on 2005-10-27
[QUOTE=Owdy]Zyxel 660H-61. I dont have firewall on, so how do i open these ports? Shouldnt they be open if theres no firewall?[/QUOTE]

Just add those two lines in here([Picture]("http://www.portforward.com/zyxel/650R-33-EditSua-Nat.jpg"))
example:
412 > 412 > 192.168.1.2
1412 > 1412 > 192.168.1.2

Someone was whining about Zyxels way to handle upd ports with NAT I read that from palsta.saunalahti.fi .

edit: the 69 post in this topic :)

---

### Post by Owdy on 2005-10-27
Bingo! Thanks! I only had that other port open :D

---

### Post by teaker1s on 2005-10-28
ignore

---

### Post by Binnikemasken on 2005-11-01
Thanks a lot! This worked fine \o/
I really appreciate this tutorial :)

---

### Post by jordz on 2005-11-01
thx, install did work fine :)

---

### Post by c4pp4 on 2005-11-05
thanks for great howto :)

---

### Post by Sonobana on 2005-11-09
Hi all!

How i make a deb from cvs-version.

---

### Post by WetWilly on 2005-11-13
[SIZE="1"]I just wanted to give people the option to use the latest version of this client cause the binary that people use [here]("http://www.ubuntuforums.org/showthread.php?t=76643")  is now way outdated and numerous patches to this great client have been released.
Most of the info is copied from a thread by [wbeck85]("http://www.ubuntuforums.org/showthread.php?t=28378") and cred goes to him. I just updated packages to go with Breezy and Dapper.
[/SIZE]

First you need the necessary packages to download and build it correctly, so fire up a terminal and type

If you use Breezy:
```
sudo apt-get install cvs libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-1.0 libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1c2 libglademm-2.4-1c2 scons
```

If you use Dapper:
```
sudo apt-get install cvs libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-1.0 libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1c2a libglademm-2.4-1c2a scons
```

When that is done you should install the headers for your kernel:

```
sudo apt-get install linux-headers-`uname -r`
```

OK! So far so good. Now you need to download the files from the CVS and compile it.

Its easiest to download and install it in your home directory so:

```

cd ~
sudo cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
```
Now it asks you for a password but just hit Enter without typing anything then 

```
cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
```

Now the download starts and a folder called linuxdcpp gets created in your home dir. Once it finishes enter in that folder and start building with

```
cd linuxdcpp
sudo scons
```
It will start compiling and that may take some time depending on your hardware but once it finishes you can run(or make a starter for)

```
~/linuxdcpp/dcpp
```

Here is a nice icon to use for your starter, [http://www.tucoo.com/icon/Exogen/s/DC++.png](http://www.tucoo.com/icon/Exogen/s/DC++.png) or maybe u prefer this one: [http://image.versiontracker.com/client_icons/win/45502/anyversion-icon-32x32-32bit.png](http://image.versiontracker.com/client_icons/win/45502/anyversion-icon-32x32-32bit.png)

---

### Post by nepenthean on 2005-11-22
I do not know if this guide is pertinent to Kubuntu, but I got to the very end, sudo scons, and got this...

scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/__init__.py", line 870, in _main

??

---

### Post by nepenthean on 2005-11-22
I get to the end, sudo scons, and and met with,

Checking for main() in C library bz2... no
Did not find the bz2 library (bz2 compression)
Can't live without it, exiting
Note: You might have the lib but not the headers


I am using Kubuntu 5.10


Thanks in advance ya'll.

---

### Post by dabear on 2005-11-23
install libbz2-dev

---

### Post by WetWilly on 2005-11-23
[QUOTE=dabear]install libbz2-dev[/QUOTE]


try that or

libbz2-1.0

---

### Post by nepenthean on 2005-11-23
That worked! Thanks guys!!!

---

### Post by Rangeli on 2005-11-28
Hi! This is my first message on this forum. I am using Slackware, but i hope we can help each other anyway. 

I downloaded linuxdcpp with cvs, but there is no file named 'scons' in the directory. There are other files, but no scons. Does anyone have an idea what may be wrong?

---

### Post by royg1234 on 2005-12-16
how do I make a menu shortcut for this once I install it?

---

### Post by hewhocutsdown on 2005-12-16
I have libglib/gtk1.2, needing 2.0, but when I try to install it I get 

libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.6-0ubuntu2) but 2.8.6-0ubuntu2.1 is to be installed

This is preventing me from installing 3 or 4 of the necessary files for DC++. How can I work around this? Thank you

                            Gideon

---

### Post by Skytreker on 2005-12-17
Works like magic!!!
I'm telling all my friends :grin:

---

### Post by s_spiff on 2006-01-10
I did as the howto says, but i get the following error 
>  Reading SConscript files ...
Checking for g++ >= 3.4...ok
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... failed
gtk+ >= 2.4 not found.


What to do ?
Also tried installing libglade, it gave me the following output :
> 
ME@Krishnautix:~/src/libglade-2.4.2$ sudo make
make: *** No targets specified and no makefile found.  Stop.
ME@Krishnautix:~/src/libglade-2.4.2$ sudo make install
make: *** No rule to make target `install'.  Stop.

someone help fast!

---

### Post by *zeus* on 2006-01-15
I get:

> scons: Reading SConscript files ...
Checking for g++ >= 3.4...ok
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... no
Did not find the header signal.h
Can't live without it, sorry


libsigc++-2.0 installed

what I must install?

---

### Post by kaktusztea on 2006-01-26
nepenthean: type: 'cd linuxdcpp' before 'scons'

---

### Post by louis_nichols on 2006-01-27
just worked. nice. 

Valknut wasn't that bad, though. And dcgui, despite all the criticism, is surprising. I mean, the GUI might be a little "crowded", but the degree of customization is great. Anyway, the power of habit... And the fact that dcgui wasn't displaying texts (that was weird, seeing that it worked in my previous install of Breezy)... made me try DC++. Now... let's see how it behaves.


Oh! I made a deb with libglade 2.4 You can find it here:

[http://louis-nichols.uv.ro/libglade-2.4.2_2.4.2-1_i386.deb](http://louis-nichols.uv.ro/libglade-2.4.2_2.4.2-1_i386.deb)

hope it's useful

---

### Post by Luoja on 2006-02-07
I get this error message when i run scons:

> 
scons: Reading SConscript files ...
Checking for None >= 3.4...ValueError: invalid literal for int(): s:
  File "SConstruct", line 77:
    if not conf.CheckCXXVersion(cxx, 3, 4):
  File "/usr/lib/scons/SCons/SConf.py", line 354:
    ret = apply(self.test, (context,) +  args, kw)
  File "SConstruct", line 58:
    if ((string.atoi(ret[0]) == major and string.atoi(ret[2]) >= minor)
  File "/usr/lib/python2.4/string.py", line 403:
    return _int(s, base)


Any advice?

---

### Post by KillerBOB on 2006-02-08
First I'd like to thank you for this great How-To! It is now very easy to update every time the devs fix/add something to linuxdcpp.

Now I have found out that (since when i don't know) the binary is no longer named dcpp, but instead ldcpp.
i.e
```
~/linuxdcpp/ldcpp
```

I just thought that I should mention this, since if you just re-do the How-To in the same directory you used the first time without changing your shortcuts to the app, you would still be running the old binary.

---

### Post by henkeboy on 2006-02-09
Hi! I have big troubles whit linux dc++. It's just shuts down all the time and sometimes it's works a couple of days at the same time and then shuts down time after time some days. My question is: Is that a known problem that many users have problem with? (Sorry for my bad english). A god working dc-client is what forces me to use windows :(

---

### Post by HarlemHenke on 2006-02-10
I have two mounted NTFS disk's (left from my windows time) on my computer, but every time I start DC++ the program starts to hash files that alredy are hashed and no changes is made on the harddrives... Why does DC++ do this?

---

### Post by yorick on 2006-02-14
@Henkeboy: It used to happen to me also.

Now it doesn't work at all... I follow the changelog and everytime there is a change I upgrade. So I reinstalled on Feb 9th and it doesn't work anymore. It crashes everytime right after starting. I'm not at home now so I don't know exactly what the message is but I think it is related to some unsupported option in the configuation file. 

Is anybody else having the same problem? When I get home I'll post the exact error message.

---

### Post by loftx on 2006-02-14
[QUOTE=yorick]@Henkeboy: It used to happen to me also.

Now it doesn't work at all... I follow the changelog and everytime there is a change I upgrade. So I reinstalled on Feb 9th and it doesn't work anymore. It crashes everytime right after starting. I'm not at home now so I don't know exactly what the message is but I think it is related to some unsupported option in the configuation file. 

Is anybody else having the same problem? When I get home I'll post the exact error message.[/QUOTE]
The latest CVS is broken. There is a patch, but I don't think it's been commited yet. Either wait for the next CVS commit (within a week most likely) or downgrade back to a previous version

---

### Post by loftx on 2006-02-15
The CVS has now been updated and should compile fine. Any compiling problems ask here. If you notice any bugs (that haven't already been submitted) please post them to the bugtraq at [http://developer.berlios.de/bugs/?group_id=2230](http://developer.berlios.de/bugs/?group_id=2230)

---

### Post by yorick on 2006-02-16
Yes, thank you, I have compiled it yesterday and it works great.

---

### Post by ubuntublue on 2006-02-25
im having a problem installing linux dc++ i followed ur guide
THANKS
but  when i try to run scons i get this error dunno what it means
scons: Reading SConscript files ...
Checking for None >= 3.4...ValueError: invalid literal for int(): s:
  File "SConstruct", line 77:
    if not conf.CheckCXXVersion(cxx, 3, 4):
  File "/usr/lib/scons/SCons/SConf.py", line 354:
    ret = apply(self.test, (context,) +  args, kw)
  File "SConstruct", line 58:
    if ((string.atoi(ret[0]) == major and string.atoi(ret[2]) >= minor)
  File "/usr/lib/python2.4/string.py", line 403:
    return _int(s, base)

any help greatly appreciated thanks in advance
i installed all the packages etc....

---

### Post by loftx on 2006-02-26
[QUOTE=ubuntublue]
but  when i try to run scons i get this error dunno what it means
scons: Reading SConscript files ...
Checking for None >= 3.4...ValueError: invalid literal for int(): s:
[/QUOTE]

I could be wrong, but I seem to recall this error can occur if you haven't got the latest version of scons or are missing the g++

try installing them separately and check there are no errors using:

```
sudo apt-get install scons
```

and

```
sudo apt-get install g++
```

---

### Post by FaZZy on 2006-02-27
when i aptget libgtkmm-2.4-dev   it says that it is N/A  ?

---

### Post by loftx on 2006-02-27
[QUOTE=FaZZy]when i aptget libgtkmm-2.4-dev   it says that it is N/A  ?[/QUOTE]
Are you running dapper? I seem to recall some of the packages have slightly different names in dapper, so if any are missing search for them or use synaptic.

---

### Post by ubuntublue on 2006-02-27
thanks loftx for your help

i actually used the .deb package u created from the other thread install dc++ for linux (easy way)

worked great  ...thanks

---

### Post by loftx on 2006-02-27
Glad it worked, but the Deb package is way out of date - I made it a couple of months ago and there have been plenty of changes since then.

If it's fine for you then stick with the Deb, but you're missing out on a few new features and some stability improvements and bugfixes.

I'll try and get a new deb made sometime soon though.

---

### Post by FaZZy on 2006-02-27
nopp do it matters ?  i cant finde any how to:s to hoary

---

### Post by loftx on 2006-02-27
[QUOTE=FaZZy]nopp do it matters ?  i cant finde any how to:s to hoary[/QUOTE]
Everything here should work for for hoary - can you post the exact command you use and the output you get here.

---

### Post by FaZZy on 2006-02-27
i got this and the same for libgtkmm-2.4-dev and scons

```
 sudo apt-get install libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1 libglademm-2.4-1 scons
Password:
Reading package lists... Done
Building dependency tree... Done
Package libgtk2.0-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgtk2.0-bin
E: Package libgtk2.0-dev has no installation candidate

```

---

### Post by loftx on 2006-02-27
[QUOTE=FaZZy]i got this and the same for libgtkmm-2.4-dev and scons

```
 sudo apt-get install libgtk2.0-dev libgtkmm-2.4-dev libglademm-2.4-dev zlib1g-dev libbz2-dev g++-3.4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common g++ libgtkmm-2.4-1 libglademm-2.4-1 scons
Password:
Reading package lists... Done
Building dependency tree... Done
Package libgtk2.0-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgtk2.0-bin
E: Package libgtk2.0-dev has no installation candidate

```[/QUOTE]

I haven't got a clue why you can't install libgtk2.0-dev - it should just be in the standard repos :-? 

Try doing "sudo apt-get install libgtk2.0-bin" as it seems to suggest that's the right package - no idea why though. If the same error comes up for libgtkmm-2.4-dev do the same thing and install whatever package it suggests. 

For scons the problem could be you haven't enabled universe - [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

If that doesn't help I don't know I'm afraid as it seems to be a package problem rather than a ldcpp provlem :(

---

### Post by FaZZy on 2006-02-27
could it be some outher solution on this problem........wrong aproatch  may be

---

### Post by loftx on 2006-02-27
If none of the stuff in my post above works, try using the package install at [http://www.ubuntuforums.org/showthread.php?t=42084](http://www.ubuntuforums.org/showthread.php?t=42084) it's a bit of an older version though.

---

### Post by FaZZy on 2006-02-27
the file that i should change akordingly the link you add before this dossent exist

---

### Post by loftx on 2006-02-27
[QUOTE=FaZZy]the file that i should change akordingly the link you add before this dossent exist[/QUOTE]
Ah sorry, I forgot - you can find the actual link around page 6 - but I've copied it here. Use:

```
http://www.studentdiscussion.co.uk/linux/dcpp_0.0.20050809cvs-1~mird_i386.deb
```

---

### Post by FaZZy on 2006-02-27
that workt tnx........but it is a old version......:(

---

### Post by FaZZy on 2006-02-27
you have posted this one:
[http://www.studentdiscussion.co.uk/linux/dcpp_0.0.20060102cvs-1~loftx_i386.deb](http://www.studentdiscussion.co.uk/linux/dcpp_0.0.20060102cvs-1~loftx_i386.deb)

---

### Post by FaZZy on 2006-02-27
you cant add share directorys is some of the problem

```
  wget http://ftp.se.debian.org/debian/pool/main/l/linuxdcpp/linuxdcpp_0.0.1.cvs20060217-1_i386.deb
--00:42:47--  http://ftp.se.debian.org/debian/pool/main/l/linuxdcpp/linuxdcpp_0.0.1.cvs20060217-1_i386.deb
           => `linuxdcpp_0.0.1.cvs20060217-1_i386.deb'
Resolving ftp.se.debian.org... 130.239.18.137, 130.239.18.142, 130.239.18.165, ...
Connecting to ftp.se.debian.org|130.239.18.137|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 757,342 (740K) [application/x-debian-package]

100%[===================================================================>] 757,342        1.13M/s

00:42:48 (1.12 MB/s) - `linuxdcpp_0.0.1.cvs20060217-1_i386.deb' saved [757342/757342]

fuzzy@Gateway:~$ sudo dpkg -i linuxdcpp_0.0.1.cvs20060217-1_i386.deb (Reading database ... 57582 files and directories currently installed.)
Unpacking linuxdcpp (from linuxdcpp_0.0.1.cvs20060217-1_i386.deb) ...
dpkg: error processing linuxdcpp_0.0.1.cvs20060217-1_i386.deb (--install):
 trying to overwrite `/usr/bin/dcpp', which is also in package dcpp
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 linuxdcpp_0.0.1.cvs20060217-1_i386.deb

```

i tryed to install the new version

---

### Post by loftx on 2006-02-27
You should be able to add directories - though there could be a problem if they have unicode (none english characters generally) in the filenames. If you can be more specific about the error I might be able to help

To get the debian package working try uninstalling the other package first.

---

### Post by FaZZy on 2006-02-27
I got it working now. i did that whit the repositories and after that i folowed you how to and it workt :)   and the problem whit the share solved 

tnx again

---

### Post by Biffy on 2006-02-28
This is a long thread.

Is there a .deb binary? I installed my dcpp from one, but that was some time ago so maybe there is a new version?

Mine is from 2005-08-09

---

### Post by Biffy on 2006-02-28
[http://ftp.se.debian.org/debian/pool/main/l/linuxdcpp/linuxdcpp_0.0.1.cvs20060217-1_i386.deb](http://ftp.se.debian.org/debian/pool/main/l/linuxdcpp/linuxdcpp_0.0.1.cvs20060217-1_i386.deb)

That's a fresh one! But can i use it on my Ubuntu system? I know it's for Debian but i just wanna be sure.

---

### Post by loftx on 2006-02-28
I haven't tested the .deb binary, but it should be fine - just make sure you select the right one for your architecture (This should be i386 for most people, as the link above is), you can see/download them all at [http://packages.debian.org/testing/net/linuxdcpp](http://packages.debian.org/testing/net/linuxdcpp).

I haven't tried the deb packages yet (using windows currently :() but someone mentioned conflicts with the old packages (the mird and loftx ones) so you might want to uninstall that first.

Edit: I forgot - if you're brave you can also try downloading the source and installing it yourself - it shouldn't be too hard see [http://ubuntuforums.org/showthread.php?t=28378](http://ubuntuforums.org/showthread.php?t=28378) for details.

---

### Post by Biffy on 2006-02-28
loftx: Hi! There was some problems with the Debian one. Too old packages in breezy.

Well, i compiled the CVS-version. It was fairly simple simple and worked.

---

### Post by lleberg on 2006-03-06
```
lleberg@margit:~/linuxdcpp$ sudo scons
scons: Reading SConscript files ...
Checking for g++ >= 3.4...ok
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.6... failed
gtk+ >= 2.6 not found.

```

Seems to be a problem :/

Edit: damn, i hate this, searching without noticing what forum i end up in!

---

### Post by loftx on 2006-03-06
The latest version uses has some shiny progressbars which require gtk2.6  - I'm guessing this is the problem as earlier versions only needed 2 or 2.4 I think. I don't have ubuntu to hand so can't do any testing, but I rekon if you do the apt get line again but replace the 2.4's with 2.6's it will all work fine.

---

### Post by toots on 2006-03-09
Hi all!

In order to install linuxdcpp from the debian package, all you have to do it recompile it using your packages.
The way to do it is really easy if you look on Google.

I think it might be added to ubuntu after dapper release.

Romain

---

### Post by zacman on 2006-03-12
I tweaked the linuxdcpp package from debian unstable so that the dependencies work with Ubuntu.  It's a pretty recent CVS snapshot (02/17/2006) and works great.  [Get it here.]("http://bassfreq.home.comcast.net/linuxdcpp_cvs20060217.deb")

---

### Post by xmastree on 2006-03-12
[QUOTE=zacman]I tweaked the linuxdcpp package from debian unstable so that the dependencies work with Ubuntu.  It's a pretty recent CVS snapshot (02/17/2006) and works great.  [Get it here.]("http://bassfreq.home.comcast.net/linuxdcpp_cvs20060217.deb")[/QUOTE]Yay, that works right out of the box on my new Breezy installation. Thanks.
02/17/06, eh? That's my birthday. :-)

---

### Post by LadyDoor on 2006-03-21
Hi!

I followed your tutorial and had nothing but success (yay!)! But for future reference, how do I update it? Do I just go to the directory and put in CVS update? Or do I need to do something with all the CVS pserver stuff, but adding update? Also:  after doing whatever update step is necessary, is that the end, or do I have to actually do all the installation steps again (w/scons and whatnot)?

I'm just new to CVS stuff and would like to know...and this seems an appropriate place since it's an app you get from there and that I use...

Thanks,
Door

---

### Post by stevensheehy on 2006-03-22
LadyDoor: To update, you just run the following commands in the linuxdcpp directory:

```
$cvs update -d
$scons
```

If you installed it to somewhere on your system, you have to run scons install with the PREFIX set to wherever you installed it.

See the official linuxdcpp guide at [Ldcpp Manual]("http://openfacts.berlios.de/index-en.phtml?title=Ldcpp_Manual")

I tried to make the guide as distribution agnostic as possible, but it should be pretty simple to follow regardless. Also, as you can see on the guide, ther are official Debian packages maintained by Romain at [http://packages.debian.org/unstable/net/linuxdcpp]("http://packages.debian.org/unstable/net/linuxdcpp") that he keeps quite up-to-date. Keep in mind these are not official linuxdcpp packages, just Debian ones. We are waiting until the program is stable enough before making any binaries.

---

### Post by stevensheehy on 2006-03-22
About the hash data problem mentioned earlier, this is a problem with the DC++ core that is fixed in more recent versions. Naga is in the process of porting the newest DC++ core to LinuxDC++. You can see the progress on his site: [http://ldcpp.dx.homelinux.org/ldcpp/wiki]("http://ldcpp.dx.homelinux.org/ldcpp/wiki")

Feel free to test his patch (patch -p2 < filename_of_patch.patch) and let him know about any undiscovered bugs. But beware, changes to DC++ queue saving causes queue sources to be deleted so back up your profile first.

Also, we increased the required GTK+ version since the progress bars I added require it. This shouldn't be a problem since Breezy Badger comes with GTK+ 2.8 and everyone else just needs to apt-get update.

---

### Post by LadyDoor on 2006-03-25
Hi all!

This is probably a weird-sounding question, but does anybody know of a text-based (like curses or something, not command-line--that'd be a challenge, to say the least) or other type of keyboard-driven dc++ program that I could install? The one described in this thread works great, but the touchpad on my laptop is kind of messed up and there is pretty much no way to navigate this program with the keyboard (also, is there some kind of Feature Requests thing for the program? I definitely would not be looking for a replacement if it worked via keyboard at all)...does anyone have any suggestions (I tried google and found the appropriate words but they were never describing the same program, which is a difficulty)?

Thanks, and sorry to co-opt the thread but I didn't really know where else to post this because it's kind of Gnome/KDE/etc. agnostic (or atheist, if text-based...)
Door

---

### Post by stevensheehy on 2006-03-26
There's a guy in the #linuxdc++ channel who said he was working on an ncurses based dc++ port, but I don't know how far along he is. I believe his nick is xcow.

There's a feature request for linuxdc++ at:
[http://developer.berlios.de/feature/?group_id=2230]("http://developer.berlios.de/feature/?group_id=2230")

Someone else has already opened a similar request already, though:
[http://developer.berlios.de/bugs/?func=detailbug&bug_id=6179&group_id=2230]("http://developer.berlios.de/bugs/?func=detailbug&bug_id=6179&group_id=2230")

I'm actually planning on adding keyboard events to the program sometime soon, I've just been waiting for naga to finish up his branch so I don't make a lot more code that he has to integrate.

---

### Post by LadyDoor on 2006-03-26
Yay! Thanks, stevensheehy!

--Door

---

### Post by int on 2006-03-27
```
int@int:~$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Logging in to :pserver:anonymous@cvs.linuxdcpp.berlios.de:2401/cvsroot/linuxdcppCVS password:
cvs [login aborted]: connect to cvs.linuxdcpp.berlios.de(195.37.77.137):2401 failed: Connection refused
int@int:~$
```

---

### Post by stevensheehy on 2006-03-27
[QUOTE=int]```
int@int:~$ cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Logging in to :pserver:anonymous@cvs.linuxdcpp.berlios.de:2401/cvsroot/linuxdcppCVS password:
cvs [login aborted]: connect to cvs.linuxdcpp.berlios.de(195.37.77.137):2401 failed: Connection refused
int@int:~$
```[/QUOTE]

Berlios has connection problems sometimes. Try it again and it'll probably work.

---

### Post by stevensheehy on 2006-03-29
ldcpp has been updated. Lots of nice [updates]("http://cvs.berlios.de/cgi-bin/viewcvs.cgi/*checkout*/linuxdcpp/linuxdcpp/Changelog.txt?rev=HEAD&content-type=text/plain") in it (though this may be a bit biased considering I wrote them :D).

---

### Post by fizz on 2006-03-30
sweet, compiling now... nothing better to waste time than with a bit of a state of trance 242 (which kicked *** btw)

---

### Post by fizz on 2006-03-30
Any reason CPU usage on this program is through the roof?  Its actually better than the last feb build i was running though :)

Feature Request: Small, dont worry..  Diffrent colored status bars for upload/download. One green and one blue.. makes just eye'in things easier :)

---

### Post by stevensheehy on 2006-03-30
[QUOTE=fizz]Any reason CPU usage on this program is through the roof? Its actually better than the last feb build i was running though[/QUOTE]

CPU usage is fine here, except maybe on very large hubs.

[QUOTE=fizz]Feature Request: Small, dont worry.. Diffrent colored status bars for upload/download. One green and one blue.. makes just eye'in things easier[/QUOTE]

I prefer it how it is. The colors for the progress bars are set by the window manager's theme this way. If I were to hardcode it, it wouldn't necessarily match the color of the theme and may look strange. As it is, you can easily tell which are downloads and which are uploads by the color of the icon and by how they are sorted (downloads->uploads->others). Though perhaps we could add an linux-specific setting to switch between the two....

---

### Post by dp_wiz on 2006-04-07
How can i start dc++ client with init.d as daemon (w/o GUI)?
Is there a solution without too much PITA? ](*,)

btw, now using valknut and succesfully sconspiled ldcpp (which is pretty slow at hashing).

---

### Post by Costas on 2006-04-23
tried to install dc++ but i get this error message when i type the scons command: 

scons: Reading SConscript files ...
Checking for g++ >= 3.4...ok
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.6... failed
gtk+ >= 2.6 not found.

any help guys? 

thanx a lot...much appreciated

c

---

### Post by LadyDoor on 2006-04-23
Costas--I may not be a guy but I may have an idea! Have you checked to make sure you have libgtk2-dev installed? The version should be greater than 2.6, and I think that a lot of times what's missing in compiling stuff (apparently, so I've heard/it seems) is development files.

Good luck!
--Door

---

### Post by Costas on 2006-04-23
LadyDoor you are the best! I managed to istall the libgkt2-dev and everything worked out fine! Thanx again...and sorry for mentioning only "guys" earlier....won't happen again!

costas

---

### Post by LadyDoor on 2006-04-23
Glad to help...just passing on stuff I've seen around the forum (and from answers I've gotten to my many many questions that never end). And re-reading my post, I didn't mean to make an example of you or anything on the "guy" thing, I was just being silly since "guy" is kind of gender-neutral anyway. But yeah, las mujeres do use linux too ;-p . Anyway, I'm glad that that worked out for you!

--Door

---

### Post by nemtudod on 2006-04-25
Hi 

The problem, not found libgtk but is installed ](*,) ](*,) 
Checking for libgtk+2.0-0 >= 2.6... failed

---

### Post by stevensheehy on 2006-04-25
[QUOTE=nemtudod]Hi 

The problem, not found libgtk but is installed ](*,) ](*,) 
Checking for libgtk+2.0-0 >= 2.6... failed[/QUOTE]
Dude, you've got to be kidding me. The person a couple posts before you posted the exact same problem and LadyDoor helped him fix it. You can try reading at least a little bit...

---

### Post by Costas on 2006-04-25
Check the last post on page 14!

---

### Post by nemtudod on 2006-04-25
ok the libgtk2.0-dev is installed too but not working.
I deleted the linuxdcpp and download cvs again.
and scons work fine.;)

---

### Post by nicxz on 2006-04-28
I had the 'Checking for gtk+-2.0 >= 2.6... failed' message too, after downloading updates and running scons. My problem however, is that I switched to Dapper Drake in the meantime.

Just posting how I solved this problem, as it may help others. If this should be in the Dapper Drake subforum, apologies.

I ran a 
```

pkg-config gtk+-2.0 --print-errors

```
to get an idea what the problem was. 
This returned a 

```

Package glitz was not found in the pkg-config search path.
Perhaps you should add the directory containing `glitz.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glitz', required by 'cairo', not found

```

I then proceded to install libglitz-glx1-dev and libglitz1-dev (don't know if both are necessary, libglitz-glx1 and libglitz1 were already installed). This solved the problem, and scons ran without further complaints.

---

### Post by Apollinaire on 2006-04-30
Hello.

I'm new to any form of linux so please bare with me. Here is what happened to me, maybe someone can explain why:
$ sudo cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
Password: (I left it blank)

$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
bash: cvs: command not found <--- what in the #$%$$ is that?

---

### Post by loftx on 2006-04-30
Ignore this

---

### Post by Apollinaire on 2006-04-30
[QUOTE=loftx]Ignore this[/QUOTE]
Cannot ignore it, as the linuxdcpp folderdoes not appear in my home dir. As it doesnt, I presume something went wrong...

Damn, this is frustrating... :(

---

### Post by stevensheehy on 2006-05-01
"bash: cvs: command not found" happens when you don't have cvs installed, but I assume you do have it installed since you were able to login to the cvs in the first step, right?

Why do you run one command as sudo and the other not? Just make a folder in your home dir, cd into it, then run those two commands without sudo.

---

### Post by Jeff250 on 2006-05-16
Works great.  Why isn't this in the universe repository?

---

### Post by Degenetron on 2006-06-03
worked pretty well. thanks. looked a little intimidating (i litterally started using linux for the first time yesterday :/) but i followed the original posts instructions and had very few bumps. they were easily fixed as the terminal gave me instructions on the few lib's that were outdated or not necessary.

---

### Post by stevensheehy on 2006-06-11
This guide is not accurate. Use this new guide I wrote for Dapper:

[HOWTO: LinuxDC++]("http://www.ubuntuforums.org/showthread.php?t=193984")

---

### Post by senzapadroni on 2006-06-11
[QUOTE=stevensheehy]This guide is not accurate. Use this new guide I wrote for Dapper:

[HOWTO: LinuxDC++]("http://www.ubuntuforums.org/showthread.php?t=193984")[/QUOTE]

I've followed that HowTo and ldcpp runs well, but it's not able to download public hubs list. 
Is there a way to import manually that file since I'm able to get it from [http://www.hublist.org?](http://www.hublist.org?)

---

### Post by stevensheehy on 2006-06-11
[QUOTE=senzapadroni]I've followed that HowTo and ldcpp runs well, but it's not able to download public hubs list. 
Is there a way to import manually that file since I'm able to get it from [http://www.hublist.org?](http://www.hublist.org?)[/QUOTE]

You can add any url that you want to use as a filelist on the public hubs tab. If you're able to connect to hubs and download just fine, then this is your solution. However, if you can't connect to anything, then try switching to passive and restarting. You can also use active mode, but that's too complex for me to explain here (see dcpp.net/faq instead).

---

### Post by senzapadroni on 2006-06-12
[QUOTE=stevensheehy]You can add any url that you want to use as a filelist on the public hubs tab. If you're able to connect to hubs and download just fine, then this is your solution. However, if you can't connect to anything, then try switching to passive and restarting. You can also use active mode, but that's too complex for me to explain here (see dcpp.net/faq instead).[/QUOTE]

Problem solved: ldcpp has been able to download the list after some hours; I think it was a hublist.org problem.
Cheers

---

### Post by ak47 on 2006-06-30
hi this topic was very helpfull for me!
10x very much because i've been trying to find and install dc client,similar to the win os one(since i'm a newbie with ubuntu and linux at all) and i'm very thankfull ! :D
(i hope one day i could post such topics to help the community:))))

---

### Post by Washington Irving on 2006-07-15
When I do the CVS part I get:```
$ sudo cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/l inuxdcpp login
Password:
$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/li nuxdcpp co linuxdcpp
bash: cvs: command not found

```

I am probably doing something stupid and obvious wrong but I don't know what.

---

### Post by stevensheehy on 2006-07-15
> **Washington Irving said:**
> I am probably doing something stupid and obvious wrong but I don't know what.

You need to install cvs. :)

```
sudo apt-get install cvs
```

Regardless, you shouldn't really be using this howto, anyway. It says you need gtkmm but even at the time this guide was written LinuxDC++ didn't require gtkmm. Use the [howto](http://ubuntuforums.org/showthread.php?p=1123003#post1123003) I wrote for Dapper.

---

### Post by Washington Irving on 2006-07-17
Brilliant! i ran into a few problems about missing libraries but quickly installed them and then everything worked fine. Thanks for the nice HOWTO and by the way do you know of any way that I can "migrate" my settings and downloads from my windows DC++ (fav hubs with their properties and unfinished downloads)?

---

### Post by kill_u on 2006-07-21
Hi 
I use ldcpp from three mounts and have not problems. But yesterday I try to load the application and I have a strange drain of RAM. After using a system monitor I understand that the ldcpp use a 458 MB of RAM (system RAM is 512). And system crash immediately!
Reinstalling the ldcpp has not effect, the same strange RAM leaking. And now I cannot use the LDCPP. 
Any idea? 
](*,) :evil:

[SIZE="2"]*Sorry about my English* [/SIZE]

---

### Post by kill_u on 2006-07-23
Hey forgot about it. Now i use Valknut....

---

### Post by stevensheehy on 2006-07-23
> **kill_u said:**
> use ldcpp from three mounts and have not problems. But yesterday I try to load the application and I have a strange drain of RAM. After using a system monitor I understand that the ldcpp use a 458 MB of RAM (system RAM is 512). And system crash immediately!
Reinstalling the ldcpp has not effect, the same strange RAM leaking. And now I cannot use the LDCPP.

Yes, this is a known bug. It's caused by the program writing junk data to HashIndex.xml, which it then tries to load into memory on startup. Temporary fix is to delete HashIndex.xml.

---

### Post by kill_u on 2006-07-25
Where I can find that HashIndex.xml?

---

### Post by stevensheehy on 2006-07-26
> **kill_u said:**
> Where I can find that HashIndex.xml?

~/.dc++/HashIndex.xml

---

### Post by kill_u on 2006-07-27
Hi
I remove the HashIndex.xml, without effect. Then I use a CVS installation witch is explain on this  [thread, ]("http://www.ubuntuforums.org/showthread.php?t=193984")and now I have a great working DC++ with no bugs. Before, when I try to connect to our server in always fall, but now I catch him without any problems.

---

### Post by mordox on 2006-08-25
my system was also not able to find time.h although I had g++ 4.0 but after the build-essentials my dc++ compiled smoothly

---

### Post by coldsoul on 2006-09-11
Hi! I have Dapper on AMD64 and i tryed to install the client. Although it worked.. when i wanted to install the packages that you described i got an error:
```
Unpacking libglitz1-dev (from .../libglitz1-dev_0.5.6-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz1-dev_0.5.6-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz.la', which is also in package glitz-cvs
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz1-dev_0.5.6-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
now my whole system is messed up. Can someone help me solve this? nothing works: apt-get update, apt-get -f install ... even synopsis can't solve this. the funny thing is.. dc++ works with no problems... thanks!

---

### Post by jadfw007 on 2006-10-19
> **coldsoul said:**
> Hi! I have Dapper on AMD64 and i tryed to install the client. Although it worked.. when i wanted to install the packages that you described i got an error:
```
Unpacking libglitz1-dev (from .../libglitz1-dev_0.5.6-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz1-dev_0.5.6-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz.la', which is also in package glitz-cvs
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz1-dev_0.5.6-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
now my whole system is messed up. Can someone help me solve this? nothing works: apt-get update, apt-get -f install ... even synopsis can't solve this. the funny thing is.. dc++ works with no problems... thanks!


I had the same problem, this worked for me:

```

sudo dpkg --force-overwrite -i /var/cache/apt/archives/libglitz1-dev_0.5.6-0ubuntu1_amd64.deb
sudo apt-get -f install
```

HTH

---

### Post by celalo on 2006-12-13
Hi,

I get the message:

```
root@su6667:/home/celalo/linuxdcpp# scons
scons: Reading SConscript files ...
Checking for g++ >= 3.4...(cached) yes
Checking for pkg-config... yes
Checking for gtk+-2.0 >= 2.6... yes
Checking for gthread-2.0 >= 2.4... yes
Checking for libglade-2.0 >= 2.4... yes
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for main() in C library ssl... no
        OpenSSL library (libssl) not found
        Note: You might have the lib but not the headers
```

I did everything explained in the documation. And I think I have the libssl library, I could not find out how to solve the issue about headers.

Thanks

---

### Post by stevensheehy on 2006-12-13
> **celalo said:**
> Hi,

I get the message:

```
root@su6667:/home/celalo/linuxdcpp# scons
scons: Reading SConscript files ...
Checking for g++ >= 3.4...(cached) yes
Checking for pkg-config... yes
Checking for gtk+-2.0 >= 2.6... yes
Checking for gthread-2.0 >= 2.4... yes
Checking for libglade-2.0 >= 2.4... yes
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for main() in C library ssl... no
        OpenSSL library (libssl) not found
        Note: You might have the lib but not the headers
```

I did everything explained in the documation. And I think I have the libssl library, I could not find out how to solve the issue about headers.

Thanks

Use the proper [guide]("http://www.ubuntuforums.org/showthread.php?t=193984").

---

### Post by Dcode^ on 2007-01-02
Excellent guide, worked great here thank you.

Having the "build-essential" package was needed to successfully install the package.

Edit: I also needed libbz2-dev & libssl-dev to compile with scons.

---

### Post by hardyn on 2007-03-11
Can the hash file be migrated from windows to linux? i have about a zillion gigs of hashed stuff that i would rather not hash again... does this work?

thanks.

---

### Post by deathspell on 2007-07-07
Hello, I get the following error when I type sudo scons
```

scons: Reading SConscript files ...
Checking for g++ >= 3.4...(cached) yes
Checking for pkg-config... yes
Checking for gtk+-2.0 >= 2.6... no
        gtk+ >= 2.6 not found.
        Note: You might have the lib but not the headers
```

I downloaded gtk+-2.8.0.tar.bz2 and tried to install it and it said it needed glib-2.12.9.tar.bz2 and pango-1.16.4.tar.bz2 (I chose the latest versions in the list...)


while installing glib, it said I needed gettext.. so I installed that too... 

What do I do now? I have gtk+-2.8.0.tar.bz2 .. after I extract it and go into the folder to type "make" after configure.. it says ```
make: *** No targets specified and no makefile found.  Stop.
```

So I'm stuck here.. Please help me! I'm completely clueless

---

### Post by mdv69 on 2007-08-10
Thanks for a great howto! Even though it has been a while since it was posted and some have said that it is outdated, it worked like a charm for me earlier today.

However, I have a small problem and I saw something similar earlier in the thread, but not quite like it. 
I selected some directories to share in LinuxDC++ but when I had done two directories and added a third, dc told me that it was already shared. It continued like that with all directories I was trying to add and then I noticed that it hashed all of my files on my non-linux partitions (six in total; 3 NTFS and 3 FAT32). Since I recently switched from Windows (still have it on dual-boot though), that is quite a lot and the partitions contain many files that I do not wish to share e.g. personal photos, documents, work-related stuff etc.

Also, I can not get the GUI now when I start since dc is hashing all of my files and apparently won't start the GUI while doing so. Does anyone else have this problem and is there a way around it?

---

### Post by danip on 2007-09-03
ok i got it installed without any problems so the how to was great for that.  now id like to add a launcher for it this is what the command looks like for me.

/home/steve/linuxdcpp/linuxdcpp

which doesnt do anything.  if im in terminal and i cd to its directory and type ./linuxdcpp it works great but i dont want to have to open up terminal every time.  what can i do to get this launcher to work?

---

### Post by inflamous on 2007-09-28
> **danip said:**
> ok i got it installed without any problems so the how to was great for that.  now id like to add a launcher for it this is what the command looks like for me.

/home/steve/linuxdcpp/linuxdcpp

which doesnt do anything.  if im in terminal and i cd to its directory and type ./linuxdcpp it works great but i dont want to have to open up terminal every time.  what can i do to get this launcher to work?

I'm on KDE, so:
open up your menu, right click on one of the submenus you want dc++ to be in, and click "edit menu".  Fill in the name and description with whatever you like and under "command: ", put:
```
cd <wherever you put the folder>/linuxdcpp/ ; ./linuxdcpp
```
Then you can copy this onto your desktop

On the desktop, you can create a shortcut, and under the "Application" tab, put:
```
cd <wherever you put the folder>/linuxdcpp/ ; ./linuxdcpp
```
where the" Command: " is.

The command should work in GNOME as well (if you're using that), but I'm not exactly sure how the menu editors are like.

---

### Post by aparigraha on 2007-09-29
LinuxDC++ 1.0.0 has been released
get it [HERE]("http://www.getdeb.net/app.php?name=Linux+DC%2B%2B")

---

### Post by the_nomad on 2008-01-05
```
$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
cvs checkout: warning: failed to open /home/username/.cvspass for reading: Permission denied

```

why is it trying to read cvspass?

---

### Post by Trindol on 2008-01-09
> **pelago said:**
> I believe the Linux NTFS drivers are simply slower than native NTFS. So this isn't a DC++ problem.

I know this was from awhile back but it seems a lot of people still complain about hashing being slow.

Hashing on from my USB 2.0 HDD formatted as vfat was 1 MiB/s, aka, dead slow. I didn't try NTFS but it looks like it is also slow.

So I formatted a thumb drive as ext3 and the hashing sped up 30x.

Both are USB so that's not it. So it is definitely a formatting issue. FAT and NTFS are just slow.

I'm using Linux DC++ 1.0.1 on gutsy.

---

### Post by amitsabne on 2008-03-24
HI..I am getting some strange error.. th library is actually installed..

Checking for g++ >= 3.4...(cached) yes
Checking for pkg-config... yes
Checking for gtk+-2.0 >= 2.6... yes
Checking for gthread-2.0 >= 2.4... yes
Checking for libglade-2.0 >= 2.4... yes
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C library pthread... yes
Checking for C library z... yes
Checking for C library bz2... yes
Checking for C library crypto... no
        crypto library not found
amit@amit-laptop:~/linuxdcpp-1.0.1$ 
amit@amit-laptop:~/linuxdcpp-1.0.1$ file:///home/amit/Desktop/lpc2k_pgm_1.05.tar.gz

---

### Post by Lukul on 2008-04-02
@amitsabne:

Try 
sudo apt-get install libssl-dev

Lukul

---

### Post by zaza1851983 on 2008-05-25
> **Lukul said:**
> @amitsabne:

Try 
sudo apt-get install libssl-dev

Lukul

Many thnx, thatw as very helpful :)

---

### Post by scullkrusher on 2008-10-17
Ok so I don't get it. I installed DC++ through the add/remove and set it up and made the download directory. I can connect to other hubs and people but whenever I go to search of a file I never get any results and nothing happens. There's no error going on it's just coming back with blank results. All I want to do is just download files like with limewire or any other p2p client and this is driving me nuts.

---

### Post by whatshisname on 2008-11-15
> **scullkrusher said:**
> Ok so I don't get it. I installed DC++ through the add/remove and set it up and made the download directory. I can connect to other hubs and people but whenever I go to search of a file I never get any results and nothing happens. There's no error going on it's just coming back with blank results. All I want to do is just download files like with limewire or any other p2p client and this is driving me nuts.

When this happens, it means you aren't really connected to the hub members.  It took me a while to figure out that just because you can see the members of a hub in the list, it doesn't mean you are connected and can download from any of those members.

Make judicious use of "canyouseeme.org".  If it doesn't say it can see your service, you will not be able to download anything.  Make sure DC++ is running when you check your connection at "canyouseeme.org".

Here are the things I have in my notes about DC++ that I use when things go south.  As I recall, restarting my firewall seems to fix things most of the time.

1) I start LinuxDC++ with this command: 

cd /usr/local/bin/linuxdcpp-1.0.1;scons;linuxdcpp &

The "scons" bit seems to be important.  Don't ask me why.

2) As I mentioned above, restarting my firewall, guarddog, seems to help a lot.

3) Try closing down DC++ and starting it back up.

4) I usually run in active mode.  It took a lot of dickering around to get that going but I finally did.  Sometimes when I notice I'm not downloading anything, I switch back to passive mode for a while.  After an hour or 2, I switch back to active and it's working again.  Who knows why?!

Hope this helps.  I'm just getting back to using DC++.  I'll bookmark this thread and report back the next time I experience these problems and tell you what worked.

---

### Post by VinZz972 on 2009-01-04
Is that possible to run it onto a server without graphical interface ?

---

### Post by peace.gangsta on 2010-03-05
> **Trindol said:**
> I know this was from awhile back but it seems a lot of people still complain about hashing being slow.

Hashing on from my USB 2.0 HDD formatted as vfat was 1 MiB/s, aka, dead slow. I didn't try NTFS but it looks like it is also slow.

So I formatted a thumb drive as ext3 and the hashing sped up 30x.

Both are USB so that's not it. So it is definitely a formatting issue. FAT and NTFS are just slow.

I'm using Linux DC++ 1.0.1 on gutsy.
I dont get it. I have a NTFS partition and the hashing takes at some 30mb/s.

---

### Post by emarkay on 2010-07-10
Someone confirm this thread is outdated for Lucid - it appears so - see: 
[http://ubuntuforums.org/showthread.php?t=193984&highlight=linuxdc](http://ubuntuforums.org/showthread.php?t=193984&highlight=linuxdc)

---

### Post by stevensheehy on 2010-08-23
> **emarkay said:**
> Someone confirm this thread is outdated for Lucid - it appears so - see: 
[http://ubuntuforums.org/showthread.php?t=193984&highlight=linuxdc](http://ubuntuforums.org/showthread.php?t=193984&highlight=linuxdc)

It's not outdated. Those directions will still allow you to compile LinuxDC++ from source in Lucid. However, I recommend you install from PPA as  mentioned in Update #2.

---

