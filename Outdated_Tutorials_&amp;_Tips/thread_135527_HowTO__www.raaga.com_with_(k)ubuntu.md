---
title: "HowTO : www.raaga.com with (k)ubuntu"
date: 2006-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by abhaysahai on 2006-02-24
Hi,
After months of windowing just to listen to songs from raaga.com, I finally got a Linux alternative. Though it is not a native Linux one, but works never the less. 
OK It is not an orignal idea by me, but a borrowed/stolen one. But being a nice thief ( Robinhood), I belive in sharing that idea with all. 
Here it goes ::

Some sites like [www.raaga.com](www.raaga.com) do not work in spite of having the latest real player and the corresponding firefox plugins, even mplayer plugins do not work. I've tried my best, but there seems to be no way of getting them to work, so I had to use a workaround. Do this only if there are some sites which do not work, otherwise you should be all set.

    * Download and install wine. I am using the latest wine using 
          deb  [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

    * Run #wine. It will create default directories, etc.
    * Copy this file as your wine [config]("http://www.cs.cornell.edu/~scs49/config.txt") file, i.e. save it as ~/.wine/config
    * Download the [windows installer of firefox]("http://www.mozilla.org/products/firefox/all") and install it by opening it with wine. Start it using wine (You may have to give a command like # wine /home/abhaysahai/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe , and install realplayer (windows version) from [www.real.com](www.real.com) through it. (At the end of installation, real player hangs, but after restarting ( or kill the process associated with real player-- dont know kill, restart) , everything works ok for me).
    * Now this installation of firefox should be able to play all sorts of internet radios, etc. (At least, it plays raaga.com and smashits.com for me!)
    * If you find a better solution, [EMAIL="abhaysahai@gmail.com"]Please do let me know![/EMAIL]

Want the orignal link -- yes it has more, actually much more info

[http://www.cs.cornell.edu/~scs49/install_linux.html#destHeader164](http://www.cs.cornell.edu/~scs49/install_linux.html#destHeader164)

And yes even the sites like hsbc.co.in works with this trick. 
How was my version ( did u say coppied or lifted version ?? :mad: )

Abhay
\\:D/

---

### Post by daredevil on 2006-03-01
Raaga.com !!! cool site. must give this info a try

---

### Post by infinitee on 2006-03-20
Hi, 
nice work around. But doesnt it hog memory? and it involves installing FF twice. I used to get it done before, but now I keep getting this "Error: Methods not found" error for raaga and musicindiaonline.com, for both Opera and FF inspite of having mplayer, Realplayer and respectve plugins.

thanks,
Pavan

---

### Post by graphic23 on 2006-03-27
Hey - This Works. Thanks for the idea.

---

### Post by neoflight on 2006-03-28
[QUOTE=abhaysahai]Hi,
After months of windowing just to listen to songs from raaga.com, I finally got a Linux alternative. Though it is not a native Linux one, but works never the less. 
OK It is not an orignal idea by me, but a borrowed/stolen one. But being a nice thief ( Robinhood), I belive in sharing that idea with all. 
Here it goes ::

Some sites like [www.raaga.com](www.raaga.com) do not work in spite of having the latest real player and the corresponding firefox plugins, even mplayer plugins do not work. I've tried my best, but there seems to be no way of getting them to work, so I had to use a workaround. Do this only if there are some sites which do not work, otherwise you should be all set.

    * Download and install wine. I am using the latest wine using 
          deb  [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

    * Run #wine. It will create default directories, etc.
    * Copy this file as your wine [config]("http://www.cs.cornell.edu/~scs49/config.txt") file, i.e. save it as ~/.wine/config
    * Download the [windows installer of firefox]("http://www.mozilla.org/products/firefox/all") and install it by opening it with wine. Start it using wine (You may have to give a command like # wine /home/abhaysahai/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe , and install realplayer (windows version) from [www.real.com](www.real.com) through it. (At the end of installation, real player hangs, but after restarting ( or kill the process associated with real player-- dont know kill, restart) , everything works ok for me).
    * Now this installation of firefox should be able to play all sorts of internet radios, etc. (At least, it plays raaga.com and smashits.com for me!)
    * If you find a better solution, [EMAIL="abhaysahai@gmail.com"]Please do let me know![/EMAIL]

Want the orignal link -- yes it has more, actually much more info

[http://www.cs.cornell.edu/~scs49/install_linux.html#destHeader164](http://www.cs.cornell.edu/~scs49/install_linux.html#destHeader164)

And yes even the sites like hsbc.co.in works with this trick. 
How was my version ( did u say coppied or lifted version ?? :mad: )

Abhay
\\:D/[/QUOTE]


nice....but have you figured out how to play media files .rm, kinda stuff in dapper? i cant play music from real....or napster.....any clues?

---

### Post by jamba on 2006-08-25
The issue here is with firefox. 
I had success with raaga and other websites.

I have downgrade firefox to 1.0.5 and realplayer to 10.0.1.450.

Now every thing is working fine.
Did this work for you.

---

### Post by deepesh on 2006-11-19
Hi,
My first post, and may be off topic.
After months of search, found [http://www.hindisongs.net](http://www.hindisongs.net)
Song plays well in embedded player on my Kubuntu box without any problem.
I have realplayer 10 installed, which I think is required.
Deepesh

---

### Post by Saswat on 2007-01-21
Hi,

Finally, I can listen to raaga.com using Firefox 1.5 on a Dapper Drake box **WITHOUT** using Wine. Thanks to the same webpage mentioned earlier in the thread, [http://www.cs.cornell.edu/~scs49/install_linux.html](http://www.cs.cornell.edu/~scs49/install_linux.html)
Although the instructions in that webpage is for Redhat, it works fine on Ubunto too.

This is what I did:
1- Downloaded the realplayer rpm mentioned in the above webpage. That realplayer package is built with gcc 3.4, which apparently makes the difference. 
2- Installed "rpm" package (using Synaptic), 
3- Issued the following commands:

   tar -jxvf RealPlayer-10.0.3-rc1-rhel4.src.rpm.tar.bz2
   rpm -ivh RealPlayer-10.0.3-rc1-rhel4.src.rpm
   mkdir realplayer
   cd realplayer
   tar -jxvf /usr/src/rpm/SOURCES/install.bz2
 
  (I tried using alien, but it did not work).

4- Made a symlink: "ln -s realplayer/realplay /usr/bin/realplay" so that realplay is in the system path.
 
5- Copied the new plugin files nphelix.so and nphelix.xpt (which are now in realplayer folder) to ~/.mozilla/plugins.

5- Restart the firefox.

Hope this helps!

---

### Post by vguhesan on 2007-06-16
Hello:

For folks who are in need of detailed directions on installing the latest Real Player and getting Raaga.com to work... 

I have documented the steps here:
[http://tinyurl.com/2rg7hd](http://tinyurl.com/2rg7hd)

Good Luck

Venkatt Guhesan
Linux = A Revolution
w/ Ubuntu Linux - The Revolution Is Here!!!

---

### Post by visionary on 2007-08-11
[COLOR="Blue"]
**OK FOLKS I MANAGED TO GET IT WORKING WITHOUT WINE OR DUPLICATES OR ADDITIONAL RESOURCES/FILE SPACES TAKEN UP...HERE IS HOW!!!!**[/COLOR]

1) Please uninstall any exisiting RealPlayer you have installed in your system
2)Print out this article as we need to close/exit your firefox while we install and configure.....

**So lets start....**

**1)          Uninstalled real player?  Yes?  Proceed to next step......**

**2)         Closed Firefox? yes? Proceed to next step......**

We need to ensure we have the basic codecs,,,
So open up your terminal/console and type....

**3)          sudo apt-get install alsa-oss            **

No Problem?? Good Proceed To Step 4.....

[B]4)      Go to *[http://www.real.com/linux ]("http://www.real.com/linux")* and download the installer to your Desktop. It shoud be a .bin file (eg RealPlayer10GOLD.bin)
[/B]

Open the terminal and navigate to the file "RealPlayer10GOLD.bin". Type 

**5)                  $ cd ~/Desktop**

Verify that the file is executable. If it isn't, type 

** 6)                $ chmod a+x RealPlayer10GOLD.bin**

Run the installer by typing 

** 7)                $ sudo ./RealPlayer10GOLD.bin**

Follow the prompts provided to finish installation.

** Note while Installing RealPlayer ...Take Note of your installation directory. I Installed into my home directory and maybe you could try installing to your home directory rather than to its default desktop.

8) Finally, go to your installed directory. For example, if you installed to /home/XXX/RealPlayer , (Where XXX is the name of your directory) then from your terminal type

**              sudo gedit /home/XXX/RealPlayer/realplay**

[B]and changed line 73 from

                     $REALPLAYBIN &#8220;$@&#8221;
 
                                   to

                 aoss $REALPLAYBIN &#8220;$@&#8221;
[/B]

Save and exit....

Now launch Firefox, go to Raaga.Com and Enjoy your top 10!!

Cheers All!!!:guitar::popcorn:

Visionary,Singapore

---

### Post by bharani on 2007-08-24
Hey Visionary,
                                  The solution you have provided is not working man...Shall I have to tweak the plugins...or install a Firefox Add on called "mediaplayerConnectivity" to check it through...please help...

:popcorn:

---

### Post by visionary on 2007-08-24
> **bharani said:**
> Hey Visionary,
                                  The solution you have provided is not working man...Shall I have to tweak the plugins...or install a Firefox Add on called "mediaplayerConnectivity" to check it through...please help...

:popcorn:

What was the error message? or was there no error message at all? Or just that you were never been able to play at all???....


Did you follow my earlier post without fail? any errors u encountered? and did you close firefox browser when you were executing the commands in my previous post?


If you have successfully completed my above mentioned steps without error and yet you are not able to play from raaga.com, then proceed with the following steps.....

1)Close the browser, open a Terminal and create a symbolic link in your system path that points at the "realplay" script. An example of an appropriate location for your symbolic link would be

$ ln -s /usr/local/RealPlayer/realplay /usr/local/bin/realplay

To Test your work:
   $ which realplay
   $ /usr/local/bin/realplay

The plugin provided by RealPlayer should now handle embedded real media. 

2)    *  Enter about:config into the Firefox address bar. You will see a large list of configurable options for the Firefox browser. In the search bar, enter "plugin". Look for an entry named plugin.expose_full_path and set its value to true. (This will allow you to see the full path to the plugins in the next step.)
    
* Enter about: plugins  into the browser address bar. You should now see a list of installed plugins along with some additional information and their locations in the file system. You see a list of plugins for Realplayer?.so is given, the plugin is installed correctly.If you do not see the installed plugins then i am afraight you need to follow my previous post closely again.

Or i suspect you default plugin for real media could be Totem player which could also stirr up little problems in some systems....to over come that, execute the following commands as well....

3)Just go to the firefox plugins directory located on:

/usr/lib/mozilla-firefox/plugins

and remove

libtotem-complex-plugin.so

libtotem-complex-plugin.xpt

type:

sudo rm libtotem-complex-plugin.*

That sould remove the colliding plugins ....


You can also try linking via mediaplayer connectivity, to do that ....

You need to make sure that there's a link to your RealPlayer 10 program's libraries in your Firefox installation's plugin directories.

By default, the directory where Firefox is installed is called /usr/lib/firefox/plugins. So, close Firefox, and run this command:

Code:

$ ln -s /opt/RealPlayer/libnullplugin.so /usr/lib/firefox/plugins/libnullplugin.so



Re-start your firefox and try again...

Good luck pal...cheers!

---

### Post by bharani on 2007-08-24
Okay Vision,
                          I banged my head for past few hours but couldn't get the stuff right...I have done all you have said in the two posts...Finally I tried with media player connectivity but I couldn't find the libnullplugin.so in my realplayer installation directory. so was there any problem with installation..I did exactly like u said b4..please look at my screen shots...

:confused:

---

### Post by visionary on 2007-08-24
> **bharani said:**
> Okay Vision,
                          I banged my head for past few hours but couldn't get the stuff right...I have done all you have said in the two posts...Finally I tried with media player connectivity but I couldn't find the libnullplugin.so in my realplayer installation directory. so was there any problem with installation..I did exactly like u said b4..please look at my screen shots...

:confused:

What linux distribution are you using?? The normal directory for firefox is /usr/lib/firefox, but you can verify this by invoking:

Quote:
whereis firefox

in a terminal. Next you need to find where real play is installed so do
Quote:
whereis realplay

 Now you need to copy nphelix.so into the mozilla plugins directory so login in as root (su - or sudo depending on your distro) and do:

Quote:
cp /path/to/nphelix /usr/lib/firefox/plugins/

Where the /path/to is the path to the realplayer plugin nphelix. Do similar for the nphelix.xpt file, except copy it into /usr/lib/firefox/components/. The symbolic link to Realplayer should be in in your path. If you can start it with realplay in a terminal then it is....restart your firefox and try again

---

### Post by bharani on 2007-08-25
Okay Got the stuff working right...I used the realplayer nightly build from helix community...the problem is firefox is compiled with gcc>=3.2 and realpplayer gold is <3.2...so we need to find a version which compiled with >= 3.2..that's it ...no more wine and no more changing the code....find this file "realplay-10.0.3.748-linux-2.2-libc6-gcc32-i586"  in helixcommunity page...

thanks Bro...
:lolflag:

---

### Post by visionary on 2007-08-25
> **bharani said:**
> Okay Got the stuff working right...I used the realplayer nightly build from helix community...the problem is firefox is compiled with gcc>=3.2 and realpplayer gold is <3.2...so we need to find a version which compiled with >= 3.2..that's it ...no more wine and no more changing the code....find this file "realplay-10.0.3.748-linux-2.2-libc6-gcc32-i586"  in helixcommunity page...

thanks Bro...
:lolflag:


Hey bro....

Nice to hear your's is working now....Enjoy the music!!

Cheers!

---

### Post by cowbuntu on 2007-09-05
The latest version of RealPlayer 10.0.9 has fixes to allow playback on Indian music websites (raaga.com, smashits.com, musicindiaonline.com). You can download the binary from [www.real.com/linux](www.real.com/linux) or get the deb from the Canonical repos.

---

### Post by sumithar on 2007-09-23
Duplicate post- deleted

---

### Post by sumithar on 2007-09-23
Can you use the navigation buttons- next song, previous song etc?

Also another weird problem- the PCM volume level gets reset with each song, so I have to go back to volume control and keep increasing it!

---

### Post by skanchi on 2007-11-11
grab the latest real player nightly builds and update. copy the mozilla plugins, if not copied while upgarde, to the ~/.mozilla/plugins directory

restart firefox! To check, in the address bar, type about:plugins. You should see the realplayer plugin information

You should now be able to listen raaga.com

---

### Post by Shrikaant on 2008-08-09
[http://abhinay.wordpress.com/2008/05/27/raagacom-in-linux/#comment-4404](http://abhinay.wordpress.com/2008/05/27/raagacom-in-linux/#comment-4404)

---

### Post by kagashe on 2008-09-28
I recently tried this site on Firefox 3 Ubuntu Hardy installation. I installed the latest Real Player 11 from bin file downloaded from real.com/linux.

The main problem is you need to copy the following from /opt/real/RealPlayer/mozilla directory to /mozilla/plugins directory **if necessary**:
nphelix.so nphelix.xpt

The default plugin directory is /usr/lib/mozilla/plugins

and delete the following Totem plugins which may conflict:
libtotem-complex-plugin.so libtotem-complex-plugin.xpt libtotem-gmp-plugin.so libtotem-gmp-plugin.xpt

Some songs on musicindiaonline need dnet codec which is not present in Real Player 11 due to licensing restrictions. You can search for follwing files on Google:
ddnt.so.6.0 dnet.so.6.0

Copy these files in /opt/real/RealPlayer/codecs and create the following symlink:
ln -s dnet.so.6.0 dnet.so

kagashe

---

### Post by pintoosingh on 2009-02-14
> **visionary said:**
> [COLOR="Blue"]
**OK FOLKS I MANAGED TO GET IT WORKING WITHOUT WINE OR DUPLICATES OR ADDITIONAL RESOURCES/FILE SPACES TAKEN UP...HERE IS HOW!!!!**[/COLOR]

1) Please uninstall any exisiting RealPlayer you have installed in your system
2)Print out this article as we need to close/exit your firefox while we install and configure.....

**So lets start....**

**1)          Uninstalled real player?  Yes?  Proceed to next step......**

**2)         Closed Firefox? yes? Proceed to next step......**

We need to ensure we have the basic codecs,,,
So open up your terminal/console and type....

**3)          sudo apt-get install alsa-oss            **

No Problem?? Good Proceed To Step 4.....

[B]4)      Go to *[http://www.real.com/linux ]("http://www.real.com/linux")* and download the installer to your Desktop. It shoud be a .bin file (eg RealPlayer10GOLD.bin)
[/B]

Open the terminal and navigate to the file "RealPlayer10GOLD.bin". Type 

**5)                  $ cd ~/Desktop**

Verify that the file is executable. If it isn't, type 

** 6)                $ chmod a+x RealPlayer10GOLD.bin**

Run the installer by typing 

** 7)                $ sudo ./RealPlayer10GOLD.bin**

Follow the prompts provided to finish installation.

** Note while Installing RealPlayer ...Take Note of your installation directory. I Installed into my home directory and maybe you could try installing to your home directory rather than to its default desktop.

8) Finally, go to your installed directory. For example, if you installed to /home/XXX/RealPlayer , (Where XXX is the name of your directory) then from your terminal type

**              sudo gedit /home/XXX/RealPlayer/realplay**

[B]and changed line 73 from

                     $REALPLAYBIN “$@”
 
                                   to

                 aoss $REALPLAYBIN “$@”
[/B]

Save and exit....

Now launch Firefox, go to Raaga.Com and Enjoy your top 10!!

Cheers All!!!:guitar::popcorn:

Visionary,Singapore


Thank you, that helped... though i didnt need to change line 73 [:)]

---

