---
title: "HOWTO: Sopcast with GUI and sop:// URLs"
date: 2008-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by ryukent on 2008-02-21
Sopcast

**EDIT**: There is a new and more up to date howto using Chromium and the sopcast-player here: [http://ubuntuforums.org/showthread.php?t=1609505]("http://ubuntuforums.org/showthread.php?t=1609505")

This guide will help you install sopcast on Ubuntu 7.10 Gutsy. It will also help you get a special modified version of the GUI running and setup firefox to send sop:// links to the program.

**Installing packages**

Make sure you have all universe and multiverse repositories switched on. Then, in terminal:

[FONT="Courier New"]sudo apt-get install qt3-apps-dev vlc build-essential[/FONT]

**Downloading the latest SopCast binary**

Link: _[COLOR="Blue"][Sopcast ix86 binary]("http://download.sopcast.cn/download/sp-auth.tgz")[/COLOR]_

Unzip it and cd into that directory using terminal. Then run:

[FONT="Courier New"]sudo cp sp-sc-auth /usr/bin/sp-sc[/FONT]
[B]
Downloading and building the latest GUI
[/B]
Download this specially modified source package. I have added URL handling.

Link: _[COLOR="Blue"][RKMOD version of QSopCast]("http://www.linux.ryukent.co.uk/show.php?id=36")[/COLOR]_

Aga*in, unzip it and cd into that (src) directory using terminal. Then run

[FONT="Courier New"]sudo qmake
sudo make
sudo make install[/FONT]


This should compile the source and install the binary into the correct location.

**Creating a menu shortcut**

Go to System / Preferences / Main Menu... then 'Internet' and 'Add New Item'. Give it the name "QSopCast" and command "qsopcast". You should now be able to launch from the main menu.

**Setting up the GUI**

Once the gui is open, goto config then config again. Make sure that the player settings are all set to "vlc" and that the channel URL is set to "http://www.sopcast.com/gchlxml"

You should now be able to watch sop casts by selecting a channel, launching it and then hitting player when the stream is at 100%

**Firefox sop:// URLS**

Go into firefox and enter URL: "about:config". Right click, select new and string. The string name is "network.protocol-handler.app.sop" and the value is "qsopcast". It should now send sops to the modified version of QSopCast ready to be launched.

---

### Post by FokkerCharlie on 2008-02-24
Awesome.

Thanks very much.

Charlie

---

### Post by cadaverousmob on 2008-03-11
> **ryukent said:**
> Sopcast

This guide will help you install sopcast on Ubuntu 7.10 Gutsy. It will also help you get a special modified version of the GUI running and setup firefox to send sop:// links to the program.

**Installing packages**

Make sure you have all universe and multiverse repositories switched on. Then, in terminal:

[FONT="Courier New"]sudo apt-get install qt3-apps-dev vlc build-essential[/FONT]

**Downloading the latest SopCast binary**

Link: _[COLOR="Blue"][Sopcast ix86 binary]("http://download.sopcast.cn/download/sp-auth.tgz")[/COLOR]_

Unzip it and cd into that directory using terminal. Then run:

[FONT="Courier New"]sudo cp sp-sc-auth /usr/bin/sp-sc[/FONT]
[B]
Downloading and building the latest GUI
[/B]
Download this specially modified source package. I have added URL handling.

Link: _[COLOR="Blue"][RKMOD version of QSopCast]("http://www.linux.ryukent.co.uk/show.php?id=36")[/COLOR]_

Aga*in, unzip it and cd into that (src) directory using terminal. Then run

[FONT="Courier New"]sudo qmake
sudo make
sudo make install[/FONT]


This should compile the source and install the binary into the correct location.

**Creating a menu shortcut**

Go to System / Preferences / Main Menu... then 'Internet' and 'Add New Item'. Give it the name "QSopCast" and command "qsopcast". You should now be able to launch from the main menu.

**Setting up the GUI**

Once the gui is open, goto config then config again. Make sure that the player settings are all set to "vlc" and that the channel URL is set to "http://www.sopcast.com/gchlxml"

You should now be able to watch sop casts by selecting a channel, launching it and then hitting player when the stream is at 100%

**Firefox sop:// URLS**

Go into firefox and enter URL: "about:config". Right click, select new and string. The string name is "network.protocol-handler.app.sop" and the value is "qsopcast". It should now send sops to the modified version of QSopCast ready to be launched.

Your instructions are impeccable; Thanks! :D

---

### Post by udh on 2008-03-12
> **ryukent said:**
> Sopcast

This guide will help you install sopcast on Ubuntu 7.10 Gutsy. It will also help you get a special modified version of the GUI running and setup firefox to send sop:// links to the program.

**Installing packages**

Make sure you have all universe and multiverse repositories switched on. Then, in terminal:

[FONT="Courier New"]sudo apt-get install qt3-apps-dev vlc build-essential[/FONT]

**Downloading the latest SopCast binary**

Link: _[COLOR="Blue"][Sopcast ix86 binary]("http://download.sopcast.cn/download/sp-auth.tgz")[/COLOR]_

Unzip it and cd into that directory using terminal. Then run:

[FONT="Courier New"]sudo cp sp-sc-auth /usr/bin/sp-sc[/FONT]
[B]
Downloading and building the latest GUI
[/B]
Download this specially modified source package. I have added URL handling.

Link: _[COLOR="Blue"][RKMOD version of QSopCast]("http://www.linux.ryukent.co.uk/show.php?id=36")[/COLOR]_

Aga*in, unzip it and cd into that (src) directory using terminal. Then run

[FONT="Courier New"]sudo qmake
sudo make
sudo make install[/FONT]


This should compile the source and install the binary into the correct location.

**Creating a menu shortcut**

Go to System / Preferences / Main Menu... then 'Internet' and 'Add New Item'. Give it the name "QSopCast" and command "qsopcast". You should now be able to launch from the main menu.

**Setting up the GUI**

Once the gui is open, goto config then config again. Make sure that the player settings are all set to "vlc" and that the channel URL is set to "http://www.sopcast.com/gchlxml"

You should now be able to watch sop casts by selecting a channel, launching it and then hitting player when the stream is at 100%

**Firefox sop:// URLS**

Go into firefox and enter URL: "about:config". Right click, select new and string. The string name is "network.protocol-handler.app.sop" and the value is "qsopcast". It should now send sops to the modified version of QSopCast ready to be launched.

I followed above instructions(plus and now I have Sopcast, QSopcast,GSopcast etc. 
I can see channels list, after I click 'launch' it connects, buffers to 100%, but clicking 'player' doesn't open media player window (I modified 'config' settings, but neither vlc nor mplayer opens).
Do I need '.wmv' codecs for these media players?


**EDIT:**Oh, I think the problem was in codec, it is working fine now, thanks a lot.

---

### Post by ryukent on 2008-03-12
I think it depends on the codec that the channel is being sent as. But tbh, VLC should launch anyway. Can I confirm, channel is at 100% and player button is pushed down (and stays down). Player setting reads "vlc" and "Enable Autorestarting Player" is ticked in config??

---

### Post by vector on 2008-03-12
Many thanks I follwed the instructions and the sports  test channels come up and start buffering.


sop from firefox url click

However when entering live footy [http://livefooty.doctor-serv.com/index.html](http://livefooty.doctor-serv.com/index.html) and clicking on an stream, it pops up sopcast is not installed. I ignored that and just hit the play live stream same result.
Yes i did all the instruction including adding gsopcast to firefox config and restarting firefox.

Some examples on how to get something working would be nice as I am new at sopcast.

---

### Post by ryukent on 2008-03-12
Ahh.... you're using livefooty... It doesn't point to sop:// links. Instead they've got a special plugin that launches sopcast only on windows systems. Use [http://www.myp2p.eu/](http://www.myp2p.eu/) instead.

---

### Post by Andeh on 2008-03-12
i use myp2p to watch ice hockey live, only the pop up links don't seem to work,

the links point to brokers similar to:

sop://broker.sopcast.com:3912/33952

and qsopcast loads up fine, it's just i don't get the stream at all. i can click on the channels in the channel list and they work fine any idea?

thanks in advance

Edit: i juyst needed to click launch sorry mate!!

---

### Post by ryukent on 2008-03-13
Yeah, the channel will be inactive by default and you have to click on the launch button to initiate the stream. Also, it sometimes does take some time to fully load. It's probably worth pointing out that not all channels work all of the time and particularly the channel list server seems to go down regularly.

If you are having trouble connecting to a channel, first check if you can get through to one of the major ones on the list. If you can then it's likely that your system is set up correctly. Maybe the particular channel you want to connect to is down. Perhaps the link you are following is old.

If you cannot get the channel list to work, it's probably a temporary thing because the load can get massive. Try using a link from a website instead. If you're waiting for an important show at a time when the system is likely to be very busy, it might be worth saving the link elsewhere. Even if the channel list server goes down, you can connect to an individual channel if you know its exact link.

---

### Post by MaindotC on 2008-03-16
> **Andeh said:**
> i use myp2p to watch ice hockey live, only the pop up links don't seem to work,

What, you haven't been banned by the power hungry admins like PKCable yet??  How odd.

Op I gave you thanks.

---

### Post by BLTicklemonster on 2008-03-21
bill@bill-desktop:~/qsopcast-0.3.5$ sudo qmake
Usage: qmake [mode] [options] [files]

   QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
        -project       Put qmake into project file generation mode
                       In this mode qmake interprets files as files to
                       be built,
                       defaults to *.c; *.ui; *.y; *.l; *.ts; *.h; *.hpp; *.hh; *.H; *.hxx; *.cpp; *.cc; *.cxx; *.C
        -makefile      Put qmake into makefile generation mode (default)
                       In this mode qmake interprets files as project files to
                       be processed, if skipped qmake will try to find a project
                       file in your current working directory

Warnings Options:
        -Wnone         Turn off all warnings
        -Wall          Turn on all warnings
        -Wparser       Turn on parser warnings
        -Wlogic        Turn on logic warnings

Options:
         * You can place any variable assignment in options and it will be     *
         * processed as if it was in [files]. These assignments will be parsed *
         * before [files].                                                     *
        -o file        Write output to file
        -unix          Run in unix mode
        -win32         Run in win32 mode
        -macx          Run in Mac OS X mode
        -d             Increase debug level
        -t templ       Overrides TEMPLATE as templ
        -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
        -help          This help
        -v             Version information
        -after         All variable assignments after this will be
                       parsed after [files]
        -cache file    Use file as cache           [makefile mode only]
        -spec spec     Use spec as QMAKESPEC       [makefile mode only]
        -nocache       Don't use a cache file      [makefile mode only]
        -nodepend      Don't generate dependencies [makefile mode only]
        -nomoc         Don't generate moc targets  [makefile mode only]
        -nopwd         Don't look for files in pwd [ project mode only]
        -norecursive   Don't do a recursive search [ project mode only]
bill@bill-desktop:~/qsopcast-0.3.5$ 




figures... I'm the only one with a problem. :)

*EDIT:

Okay, I tried sudo qmake -makefile and got to make install, and now get

bill@bill-desktop:~/qsopcast-0.3.5$ sudo make install
make: Nothing to be done for `install'.
bill@bill-desktop:~/qsopcast-0.3.5$

*EDIT:
on a lark, I executed the binary, and sopcast came up. I set it to use vlc, and set the url, but I don't see anything. Is it supposed to come up with some choice of podcasts I can choose from, or do I have to manually insert the urls, or is the make install part keeping me from seeing podcasts to choose from?

---

### Post by ryukent on 2008-03-21
Looks like you might be in the wrong directory. You need to be in the src dir before you can run the qmake commands etc.... After the install option has been run, it will put the binary in the correct bin dir on your system. After that, you can launch the gui by just typing "qsopcast". Make sure you've already installed the back end though!

Once the gui loads, it should download a list of channels. If it doesn't, make sure you've set the channel list URL correctly in the options. If it still doesn't work, chances are the server is down. It happens all the time. You can still run sopcasts from sop:// links on webpages (if you've set that up - see original post). When the address is entered in qsopcast, click launch and it will connect to the stream. Note these are not podcasts, this is live streaming video.

If you want to find a list of sop:// links, do a google search.

---

### Post by BLTicklemonster on 2008-03-21
Bingo, thanks. I think actually putting the 

cd /home/yourname/blahblahblah/src

line in how tos is imperative for folks like me who are a bit ... detail challenged (read ADD).

---

### Post by jayznbiggiesmalls on 2008-03-24
When i get to the $make stage i get this error:

> 
user@user-desktop:~/Desktop/qsopcast-0.3.5/src$ sudo make install
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -I.moc/ -o .obj/channel.o channel.cpp
make: g++: Command not found
make: *** [.obj/channel.o] Error 127


could someone give me some help on this. I'm pretty new to ubuntu.

Thanks in advance

---

### Post by ryukent on 2008-03-24
Did you run the

sudo apt-get install qt3-apps-dev vlc build-essential

command? It looks like you don't have g++ installed. The above line will install everything you need to build the application.

---

### Post by MaindotC on 2008-03-25
Thanks for the tutorial!  It installed perfectly, but at the bottom it keeps saying its connecting and it never really connects.  I tried several channels just to make sure it wasn't just the NHL channels.  Can you think of why this would happen?  Thanks.

Problem resolved - put sp-sc in /usr/local/bin [http://ubuntuforums.org/showthread.php?t=728683](http://ubuntuforums.org/showthread.php?t=728683)

---

### Post by sholter on 2008-03-26
> **strAlan said:**
> What, you haven't been banned by the power hungry admins like PKCable yet??  How odd.

Op I gave you thanks.

That's funny since I'm one of those power hungry admins on there ;)

---

### Post by SLA_leandrin on 2008-03-26
Thanks!!

Very simple and useful guide...

---

### Post by splittter on 2008-03-31
Thanks a lot for this, had a few previous goes to get some gui version of sopcast working with launching from a browser but failed ... with this guide it took me 10 mins :)

---

### Post by jjgomera on 2008-04-01
thank you very much ryukent, work fine =D>

I've packaged this to easy install, a click and run :D

[[COLOR="Blue"]qsopcast_0.3.5.rkmod-1_i386.deb[/COLOR]]("http://www.adrive.com/public/15bbecc20fcc2e7dc76e13a7b1d796bc5d38a8cbfeb106467b202f9644f2d321.html")

Also the last-version comand-line sopcast, recently downloable versión 3.0.1: [[COLOR="Blue"]sopcast_3.0.1_1.i386.deb[/COLOR]]("http://www.adrive.com/public/8e330a22b169f878f4e7a4df4f3f5529980a2dd92344364388269e47bd935a80.html")

---

### Post by Walc on 2008-04-08
ok guys
i followed the steps given in 1st post and heres the thing:

when adding the menu shortcut and tryin to run it i have: 
```
couldnt launch menu item, failed to execute child process 'qsopcast' no such file or directory 
```

any1?

---

### Post by ryukent on 2008-04-14
Looks like it can't find the qsopcast binary. Did "sudo make install" execute correctly?? It should have put the binary into the our bin dir, which should also have a path set to it. If you still have the source directory, go in there and check that there is a binary file. If running that works, it's simply a matter of copying it into a directory that is included in the environment path.

---

### Post by steffega on 2008-04-26
I know this setup was meant for Gutsy, but I'll try anyway..

The launching from Mozilla doesn't work anymore after I upgraded to Hardy.
As i click on a sop-link, it doesn't respond in any way.

The qsopcast command still works from the terminal, and the string in "about:config" is still there. Maybe it has something to do with the browser upgrade? (As of now I have firefox 3 beta 5) 

Any ideas?

---

### Post by bribri124 on 2008-04-26
I have been doing a little bit of research and apparently Windows users are experiencing the same issue with FF3 Beta 3.  I've been using qsopcast for quite a while now without problem, so it must be a browser issue.

---

### Post by bribri124 on 2008-04-26
I did discover no significant changes have been made to Opera, other than going to version 9.27.  I have tested and can confirm sop links do work with this browser.  To set that up, go to Tools > Preferences > Advanced > Programs, click Add, enter 'sop' for Protocol, 'qsopcast' for Open with other application, and click OK.

I know this isn't Firefox, but I also use Opera, and I do not want to keep typing the sop address until Firefox resolves this issue.

---

### Post by ubunter1 on 2008-04-28
does anyone know if it will work in hardy yet? or can it be done?.

---

### Post by mcgooie on 2008-04-30
when i follow this and leave the channel to buffer to 100% and click player nothing happens, anyone got an idea?

thanks

---

### Post by mcgooie on 2008-04-30
> **mcgooie said:**
> when i follow this and leave the channel to buffer to 100% and click player nothing happens, anyone got an idea?

thanks

just solved it, i was just changing where it had mplayer instead of removing the entire lines and replacing with vlc and now it works

---

### Post by frecon on 2008-04-30
> **ubunter1 said:**
> does anyone know if it will work in hardy yet? or can it be done?.
Yes, but I couldn't get it to work with this guide.

I found another guide that worked for me and was also really easy to install.
[http://ubuntuforums.org/showthread.php?t=728683](http://ubuntuforums.org/showthread.php?t=728683)

---

### Post by guildofghostwriters on 2008-05-01
I followed this and sopcast is working in Hardy but there's one more step required before it will launch a sop link from MyP2P in Firefox3 - even after adding the string in about:config, when you click on a sop link it pops up a dialog box asking the  application to launch with sop streams, along with its location. It took me a while to find it in /usr/local/bin/ (being a total ubuntu noob) but now it works fine and it seems to be quicker than it was under Windows. Thanks for the guide!

---

### Post by cttytony on 2008-05-21
[http://ubuntuforums.org/showthread.php?t=728683](http://ubuntuforums.org/showthread.php?t=728683)

I tried to install gsopcast as described in the above link and it works like a charm! The installation is easy as somebody wrote an automated installation deb for the program. Plus the tutorial above on how to make Firefox call in gsopcast (do remember to enter the string value as "gsopcast" instead of "qsopcast") to handle sop://, now everything works as in Windows! Even faster loading!

---

### Post by tarntow on 2008-05-28
This is just wonderful stuff you've posted here...thank you so much for your well written and easy to follow instructions...good on you mate...respect:KS:KS:KS...you're a STAR and a half!!!

---

### Post by gripped on 2008-06-20
I have found how to get sopcast to open from a link in firefox 3 with hardy.

follow the tutorial but when in the about:config bit add the string 

/usr/local/bin/qsopcast instead of just qsopcast.
It should work now but doesn't

Now on the about:config page right click and make a new boolean value

network.protocol-handler.warn-external.sop
and make sure its set to TRUE

Now click a sop link and a dialog will open. 
You will see qsopcast as a choice but if you select it you can't click ok.

You need to browse to /usr/local/bin/qsopcast in this dialog and then you can click ok on the second qsopcast in the dialog box.

sop links now work. 

Isn't it nice when things 'just work' !

---

### Post by df9517 on 2008-08-13
I have installed and run sopcast many times previously without any trouble.

Now I installed qsopcast and after clicked on a channel it just stays connecting... nopthing more happen. 

Now I live in China. Can it be that the great fire wall of China is blocking or even the ISP (ChinaNET)? Do I need to open some ports?

Any idea welcome.

---

### Post by coolbrook on 2008-08-20
Same here. For some reason my most recent install of QSopCast is ending up with the same result. Connecting...

---

### Post by mirhciulica on 2008-09-03
The instalation work on hardy too:P
But I can't start QSopcast :confused:. I have this error: 

```
sound.cpp:44: Sound::Sound(QObject*, const char*): Assertion `elem' failed.
Aborted

```

The only reason I found about this error is because of the presence of two sound adapters, but not a resolve! :(
I have 2 sound cards, one onboard(Intel) and the other is Creative Sound Blaster Audigy SE.
I want to resolve it! Help please!

---

### Post by c-m on 2008-09-10
wrong thread

---

### Post by TnTMike on 2008-09-27
Many thanks gripped, I had similar problems opening QSOPCAST from FF3 and Hardy but your fix June 20th worked a treat.

---

### Post by chrismacp on 2008-10-25
Nice tutorial. Been using Sopcast et al on windows for a while. Really glad to get it on my Ubuntu now!! Works great. Didn't realise MPlayer was not installed at first (bit new to Linux) but all sorted now.

---

### Post by hydralv on 2008-11-07
Thanks alot for Howto. I tried it all on 8.10 Interpid and works great just on doing "sudo make" it throws error. I googled and found this:
[http://www.linuxquestions.org/questions/linux-software-2/qsopcast-compile-problem-on-ubuntu-8.10-680563/](http://www.linuxquestions.org/questions/linux-software-2/qsopcast-compile-problem-on-ubuntu-8.10-680563/)
One more thing i did is instead of doing "sudo make install" i did "sudo checkinstall" to make deb package.

---

### Post by satellite360 on 2008-11-30
> **df9517 said:**
> I have installed and run sopcast many times previously without any trouble.

Now I installed qsopcast and after clicked on a channel it just stays connecting... nopthing more happen. 

Now I live in China. Can it be that the great fire wall of China is blocking or even the ISP (ChinaNET)? Do I need to open some ports?

Any idea welcome.
Try this - [http://www.sopcast.cn/gchlxml](http://www.sopcast.cn/gchlxml)
Works in Beijing

---

### Post by flyguy97 on 2009-01-06
Hello all,

I created a new SopCast front-end and would love it if people would help test it out a bit. It features a built-in player and a channel guide with the ability to bookmark favorite channels. Currently the only available language is English, but I'm working with a few people to try and bring support for Japanese and Chinese as well. Let me know what needs improvement, and please, be honest.

[http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player")

btw. Be sure to read the Installation notes on the website before you install, due to the GPL I am unable to include the SopCast client program in the package.

flyguy97

---

### Post by petersk on 2009-01-27
I don't think I have two sound card and I'm having the same problem on Hardy.  Did you find a solution?
Kurt


> **mirhciulica said:**
> The instalation work on hardy too:P
But I can't start QSopcast :confused:. I have this error: 

```
sound.cpp:44: Sound::Sound(QObject*, const char*): Assertion `elem' failed.
Aborted

```

The only reason I found about this error is because of the presence of two sound adapters, but not a resolve! :(
I have 2 sound cards, one onboard(Intel) and the other is Creative Sound Blaster Audigy SE.
I want to resolve it! Help please!

---

### Post by c-m on 2009-04-12
This doesn't work for me. 

```

carl@carl-laptop:~/qsopcast-0.3.5/src$ sudo qmake
sudo: qmake: command not found
carl@carl-laptop:~/qsopcast-0.3.5/src$ ls
channel.cpp  icons         mainwindow.cpp  mylabel.cpp      mystatusbar.h  playfork.h    sopfork.h      timing.cpp
channel.h    language      mainwindow.h    mylabel.h        mytabbar.h     qsopcast.pro  sound.cpp      timing.h
config.cpp   loadsave.cpp  menubar.cpp     mylistitem.h     pageplay.cpp   record.cpp    sound.h        utils.cpp
config.h     loadsave.h    menubar.h       mypopupmenu.h    pageplay.h     record.h      tabwidget.cpp  utils.h
header.h     main.cpp      myhbox.h        mystatusbar.cpp  playfork.cpp   sopfork.cpp   tabwidget.h
carl@carl-laptop:~/qsopcast-0.3.5/src$


```

---

### Post by c-m on 2009-04-29
different computer. I get the following:

```
 carl@carl-desktop:~/qsopcast-0.3.5/src$ sudo make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/channel.o channel.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/config.o config.cpp
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/playfork.o playfork.cpp
playfork.cpp: In member function &#8216;void PlayFork::onPlayerExit()&#8217;:
playfork.cpp:117: warning: suggest explicit braces to avoid ambiguous &#8216;else&#8217;
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/loadsave.o loadsave.cpp
loadsave.cpp: In member function &#8216;void LoadSave::saveopenstate()&#8217;:
loadsave.cpp:130: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I.moc/ -o .obj/main.o main.cpp
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:49: error: &#8216;srand&#8217; was not declared in this scope
make: *** [.obj/main.o] Error 1
carl@carl-desktop:~/qsopcast-0.3.5/src$ 
  
```

---

### Post by luddgopelle on 2009-05-08
I had the same error. By adding 
```
#include <stdlib.h>
```
to header.h it compiled.

---

### Post by din on 2009-05-11
> **luddgopelle said:**
> I had the same error. By adding 
```
#include <stdlib.h>
```
to header.h it compiled.


Thanks. It solved my problem.

---

### Post by hyz on 2009-07-06
I have the same problem as c-m.Any solution?
by "#include <stdlib.h>" doesn't seem to work 

Edit: Found a fix.It seems that if I use #include <cstdlib>, it complies

---

### Post by pantera10 on 2009-09-16
ok i followed flyguys awesome guide and installed sopcast...it works...but everytime i click on Reload Sopcast Server channel guide..it says server down : ( ...i just wanna watch football in peace

---

### Post by jjgomera on 2009-09-16
that isn't a qsopcast problem, simply this server is down, or time out: [http://www.sopcast.com/chlist.xml](http://www.sopcast.com/chlist.xml), check it yourself

---

### Post by chaitanya408 on 2010-01-06
Hi Guys,

Try this URL for channel guide in sopcast player...looks like it is working now
[http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)

//Chaitanya

---

### Post by capagira on 2010-10-16
the instructions sop protocol association did not work (for gsopcast)
I had to follow the instructions found in the mozilla knowledge base:
[http://kb.mozillazine.org/Register_protocol](http://kb.mozillazine.org/Register_protocol)
and now it's ok
(using maverick)

hope it will help other ppl

---

