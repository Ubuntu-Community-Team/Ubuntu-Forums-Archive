---
title: "HOW-TO: Gaim-Rhythmbox 1.5.0.1 plug-in installation."
date: 2006-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by borisattva on 2006-01-16
This nifty little plug in wil conveniently display your currently played Rhythmbox track  in your AIM Profile or Away message, through use of %rb (like %n - name, %t - time, etc)

Necessary Dependencies:
gain-dev, libgtk2.0-dev, libbonobo-dev
(possibly others, so please report if you have any errors)

If you havent already, get the tarball of the plug-in here:
[http://gaim-rhythmbox.sourceforge.net/](http://gaim-rhythmbox.sourceforge.net/)

you can Download it to anywhere but for simplicty of instructions,
it is necessary that you drop it on your Desktop (you can delete it afterwards)

Right-click on the file name gaim-rhythmbox-1.5.0.1.tar.gz and selecte 'Extract Here'

a Folder 'gaim-rhythmbox-1.5.0.1' will be created.

Open up your Terminal and type:```
cd ~/Desktop
cd gaim-r*
```

verify that you are in:
username@machine:**~/Desktop/gaim-rhythmbox-1.5.0.1$**

type: ```
./configure
```

If you see any errors, the process will stop. This means that there are still some dependencies that you need to install prior to this step

If you see something like:
** configure: error: Package requirements (*packagename* >=**

go to Synaptic and search for it with 'packagename**-dev**', install it and its dependencies.

Or come here with your error and we'll help you idnetify it.

If you do not see any errors, type: ```
**sudo** make
```

Provide your linux password if necessary.

Once completed type: ```
**sudo** make install
```

Record errors if any.

If you dont see any errors, open up Gaim and do CTRL+P on your keyboard.
In the preferences window click on Plugins and put a checkmark next to Gaim-Rhythmbox, and click Close.

Either in your AIM profile or your away message put ```
%rb
```

Open up Rhythmbox and play a track. Check your away/profile.
If you see the song information there, youre set.
Feel free to customize the message by adding text anywhere around %rb

---

### Post by BitTorrentBuddha on 2006-03-19
what do I do if it says that the gaim package is not found? (I am using gaim 1.5.0) and this happens for every plugin I try to compile
```
checking for gaim >= 0.79... Package gaim was not found in the pkg-config search path. Perhaps you should add the directory containing `gaim.pc' to the PKG_CONFIG_PATH environment variable No package 'gaim' found
configure: error: Library requirements (gaim >= 0.79) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```
would all i have to do to fix this be to add a line reading `gaim.pc' to /usr/bin/pkg-config (this specific plugin is gaim-xmms)

---

### Post by borisattva on 2006-03-19
search the synaptic for gaim-dev, you need to install it if you dont alreday have it. i noticed that in debian based systems (which is ubuntu) you need to have the -dev pacakage installed when the package itself is claimed to to not be present.

---

### Post by mikemn84 on 2006-05-03
I followed the instructions here and I thought I had installed it all correctly (I got all the neccesary dependencies, untarred etc.), but there is no option for gaim-rhythmbox in my gaim preferences window.  If I try to remake and install it again, it shows nothing to be done for 'install-exec-am' and similar nothing to be done messages.  I have gaim 1.5.0 and am running ubuntu breezy.

---

### Post by borisattva on 2006-05-03
i'm actually no longer runnign linux :(
so my advise is kind of blind, but for what its worth,

before youre checking preferencs tab, are you sure you activated the plug in in the plugins tab?

hope it helps.

---

### Post by mikemn84 on 2006-05-03
[QUOTE=borisattva]
before youre checking preferencs tab, are you sure you activated the plug in in the plugins tab?
[/QUOTE]

Yeah, I looked in the plugin section and there is nothing there to activate.  I don't know what the deal is.  I'll try to completely uninstall it and start over I s'pose :-k.

---

### Post by dpsleep on 2006-05-04
hey, what if your useing the 2.0 beta 3 version. is there a way i can still install this?

---

### Post by baytuni on 2006-11-04
```
checking for dbus... configure: error: Package requirements (dbus-1 >= 0.50) were not met:

No package 'dbus-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables dbus_CFLAGS
and dbus_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
:D

---

### Post by Turbo Audi on 2006-12-13
Worked great!  Had to download lots from Synaptic.  Every error I got in the command line I ran a search for that file and downloaded it.  works great!

---

### Post by rudyj on 2007-01-11
In trying to get this plugin I've run in to a small problem.  Here's the error I get when runnint ./configure :

checking for rhythmbox... configure: error: Package requirements (rhythmbox >= 0.6) were not met.

I've gotten a bunch of errors like this during this installation and I could usually find the proper downloads in synaptic.  I can't seem to find any that'll fix this error though.  I'm running Ubuntu 6.10, Rhythmbox is 0.9.6 and gaim is 2.0 beta3.1

---

### Post by xsidekick409 on 2007-02-05
Has anyone found a fix for the above problem?

I have the same exact problem and I cannot find a rhythmbox-dev or anything similar.  I even updated rhythmbox to 0.9.7 and that didn't work.

---

### Post by spacemoth on 2007-02-08
I had to install the following packages to get this working: gaim-dev, libgtk2.0-dev, libbonobo-dev, libdbus-1-2, and libdbus-glib-1-2.

---

### Post by blackdalek on 2007-03-01
I installed this plug-in and it is ticked in the gaim plug-in preferences. But I do not know how or where to enter the %rb thing. I use an msn account through gaim. Does this plug-in not work for msn accounts?

---

### Post by bedake on 2007-03-06
> **blackdalek said:**
> I installed this plug-in and it is ticked in the gaim plug-in preferences. But I do not know how or where to enter the %rb thing. I use an msn account through gaim. Does this plug-in not work for msn accounts?


I believe it only works for aim, but im not 100%

Ah I got it working fine after downloading all the packages needed via synaptic

---

### Post by blackdalek on 2007-03-10
Is this thing supposed to work in IRC with Gaim too? I can't make that work neither.
Maybe I am using wrong versions? My Rhythmbox is version 0.9.6 and my gaim is version 2.0.0beta6, rhythmbox-gaim plugin is version 2.0beta5

---

### Post by ravindran.k on 2007-04-01
hey frnds

Pls also install some more:

sudo apt-get install libdbus-1-2-dev  libdbus-glib-1-dev

that works.. :)

---

### Post by ravindran.k on 2007-04-01
Greeting to all..

Finally i figured it out...

install the plugin.,enable it in GAIM. close and restart GAIM and Rhythmbox if they are running

Then go to GAIM status messages area and create a new status title Music (this can be anything) and the text area shld contain %rb.. start rhythmbox and play some song and the status will change :)


njoy!!!!!
Ravi

---

### Post by honeydew on 2007-05-31
this howto worked for me w/ pidgin-rhythmbox pluggin and fiesty

---

### Post by spock84 on 2007-06-01
I can't get this to work for my MSN account. Does it only work with AIM?

---

### Post by mpgarate on 2007-10-14
managed to get it all set up... except it just shows '%rb' and does not get replaced.. is there anything I must do from the rhythmbox end?

edit: nevermind, just had to restart the song :P thanks!

---

### Post by panand178 on 2008-06-22
I installed this however the %rb remains in my status and change to show my current track. I tried restarting both pidgin and rhythmbox but no luck!

---

### Post by ravindran.k on 2008-06-22
just make sure you have enabled the plugin in pidgin.. shld work

---

### Post by panand178 on 2008-06-22
> **ravindran.k said:**
> just make sure you have enabled the plugin in pidgin.. shld work

I have enabled the plugin. Still it doesnt work. I use three different accounts in pidgin: yahoo, MSN and gtalk. I hope this plugin works with these.

---

### Post by ravindran.k on 2008-06-23
Hmmm.. it has nothing to do with accounts.. basically if the plugin is enabled... when the song changes the %rb is replaced by the string defined in the plugin configuration. Thats wht I had done.. [http://ravindrank.blogspot.com/2007/04/for-ubuntu-fans-gaim-rhythmbox-plug-in.html](http://ravindrank.blogspot.com/2007/04/for-ubuntu-fans-gaim-rhythmbox-plug-in.html)

---

### Post by panand178 on 2008-06-23
> **ravindran.k said:**
> Hmmm.. it has nothing to do with accounts.. basically if the plugin is enabled... when the song changes the %rb is replaced by the string defined in the plugin configuration. Thats wht I had done.. [http://ravindrank.blogspot.com/2007/04/for-ubuntu-fans-gaim-rhythmbox-plug-in.html](http://ravindrank.blogspot.com/2007/04/for-ubuntu-fans-gaim-rhythmbox-plug-in.html)

The plugin did not throw any error while installing. I enabled the plugin in pidgin. But still all I can see is the %rb (Shown in image below). 

[ATTACH]75077[/ATTACH]

---

### Post by panand178 on 2008-06-26
Hey Guys!

Does anybody have an answer to this yet?

I am still not able to view the current track in my Pidgin?

stupid Question: Is it only my friends who get to see the %rb resolved to show the current track whereas i always get to see only the %rb as shown in the screenshot in my previous post? :confused:

---

### Post by ravindran.k on 2008-06-26
Excellent Question.. To know that you your own ID as a frnd in ur messenger list..then u can see ur status

---

### Post by panand178 on 2008-06-26
> **ravindran.k said:**
> Excellent Question.. To know that you your own ID as a frnd in ur messenger list..then u can see ur status

I tried adding my own id as a friend on yahoo and MSN. I cannot even see the %rb for these two accounts. Meaning there is not status. It's only my name that appears. :(

---

### Post by ravindran.k on 2008-06-26
Hope some song is playing in Rhythm box and the plugin in pidgin is as shown in attachment...

---

### Post by panand178 on 2008-06-29
> **ravindran.k said:**
> Hope some song is playing in Rhythm box and the plugin in pidgin is as shown in attachment...

Yes the plugin in pidgin is as shown in your attachment and there is a song playing in Rhythm Box. Still no luck! :(

---

### Post by telepathetic on 2008-06-30
ditto-- same issue for me as well on heron

what i did:
make sure rhythmbox and pidgin are closed
got pidgin-rhythmbox-2.0
./configure
make
make install
checked plugin in pidgin
changed status message to %rb

and nothing-- just %rb in AIM

---

### Post by panand178 on 2008-10-11
I had long since ditched my effort to get the %rb thingy working i.e. until recently I happened to notice something. 

I also happen to have the KDE desktop installed and logged into the KDE environment a couple of days back. Surprisingly the %rb got resolved while I was on KDE. But the moment I switch back to GNOME it stopped working again. 

Any clues anyone?

---

