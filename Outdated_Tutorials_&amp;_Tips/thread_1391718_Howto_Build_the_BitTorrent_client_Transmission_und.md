---
title: "Howto: Build the BitTorrent client Transmission under Karmic Koala"
date: 2010-01-27
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2010-01-27
In February 2010 a great new version of Transmission was released. This mini-guide demonstrates how to build this version from source under Karmic Koala. First we need to remove the repository version, which has been split into a few different components (we will be building instead a *single* package that has the gtk frontend, the cli client, the remote utility and the daemon):

```

sudo apt-get remove transmission transmission-daemon \
transmission-common transmission-gtk transmission-cli transmission-qt

```

Don't worry if you don't actually have all of the above packages installed. Next download some compiling tools and dependencies:

```

sudo apt-get install build-essential automake autoconf checkinstall \
libtool pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev \
libnotify-dev libglib2.0-dev libgconf2-dev libcanberra-gtk-dev

```

Next download the source code, open the tarball and compile and install it:

```

$ cd $HOME
$ wget http://mirrors.m0k.org/transmission/files/transmission-1.92.tar.bz2
$ tar xjvf transmission-1.92.tar.bz2
$ cd transmission-1.92
$ ./configure
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
  --deldesc=yes --delspec=yes --default --pkgversion "1.92"
$ make distclean


```

And that is it! This gives you the newest version of a great BitTorrent program, perfect for downloading and sharing the latest versions of Ubuntu. Remember: Have Fun!!

**Recent Updates to this Guide:**

[LIST]
[*]Mar 24th 2010: Updated to Transmission 1.92
[*]Feb 27th 2010: Updated to Transmission 1.91
[*]Feb 20th 2010: Updated to Transmission 1.90
[*]Jan 30th 2010: Updated to Transmission 1.83
[/LIST]

---

### Post by smeerbartje on 2010-01-29
Will this also work on the server version without GUI? And if so, what is different?

---

### Post by andrew.46 on 2010-01-29
Hi smeerbartje,

> **smeerbartje said:**
> Will this also work on the server version without GUI? And if so, what is different?

The command to start the cli version is *transmissioncli* and its options are well documented in its own man page or by running the following:

```
andrew@skamandros:~$ **[COLOR="Red"]transmissioncli --help[/COLOR]**
Transmission 1.83 (10040) - http://www.transmissionbt.com/
A fast and easy BitTorrent client

Usage: transmission-cli [options] <file|url|magnet>

Options:
  -h  --help                            Display this help page and exit
  -a  --announce             <url>      Set the new torrent's announce URL
  -b  --blocklist                       Enable peer blocklists
  -B  --no-blocklist                    Disable peer blocklists
  -c  --comment              <comment>  Set the new torrent's comment
  -d  --downlimit            <speed>    Set max download speed in KB/s
  -D  --no-downlimit                    Don't limit the download speed
  -er --encryption-required             Encrypt all peer connections
  -ep --encryption-preferred            Prefer encrypted peer connections
  -et --encryption-tolerated            Prefer unencrypted peer connections
  -f  --finish               <script>   Run a script when the torrent finishes
  -g  --config-dir           <path>     Where to find configuration files
  -i  --info                            Show torrent details and exit
  -m  --portmap                         Enable portmapping via NAT-PMP or UPnP
  -M  --no-portmap                      Disable portmapping
  -n  --new                  <source>   Create a new torrent
  -p  --port                 <port>     Port for incoming peers (Default: 51413)
  -r  --private                         Set the new torrent's 'private' flag
  -s  --scrape                          Scrape the torrent and exit
  -t  --tos                  <tos>      Peer socket TOS (0 to 255, default=0)
  -u  --uplimit              <speed>    Set max upload speed in KB/s
  -U  --no-uplimit                      Don't limit the upload speed
  -v  --verify                          Verify the specified torrent
  -w  --download-dir         <path>     Where to save downloaded data
```

Bear in mind the *transmission-cli* is not the command, the correct command is *transmissioncli*. I have submitted [a patch]("http://trac.transmissionbt.com/attachment/ticket/2836/cli.diff") to correct this.

If you actually mean what is different *in this version* this can be seen [in the changelogs]("http://trac.transmissionbt.com/wiki/Changes").

All the best,

Andrew

---

### Post by andrew.46 on 2010-01-29
Updated the guide to Transmission 1.83 which compiles cleanly. Changes in this version noted [here]("http://trac.transmissionbt.com/wiki/Changes#version-1.83").

Andrew

---

### Post by Yingy on 2010-01-29
Followed your instructions and it worked like a charm.  Thanks for posting clear instructions for a beginner like me.

---

### Post by andrew.46 on 2010-01-29
Hi Yingy,

> **Yingy said:**
> Followed your instructions and it worked like a charm.  Thanks for posting clear instructions for a beginner like me.

Excellent news :).

Andrew

---

### Post by smeerbartje on 2010-01-30
Well, I'm almost there. I have compiled the latest version and modified the settings.json file. Now I start transmission as a daemon by typing: 'transmission-daemon' on the console. However, How do I stop the daemon? Not by typing /etc/init.d/transmission-daemon stop... (that's not available)

EDIT 1
An additional question: when I make some changes to the config-file, it get's overwritten the next time I restart the server, why is that?

EDIT 2
Problem solved. It seems that Transmission always saves the logfile on exit. Therefore I had to change the logfile before running Transmission. Cool, I'm happy now!

---

### Post by Alvaro_SG on 2010-01-30
Thanks! Works perfectly! ^_^

---

### Post by andrew.46 on 2010-01-30
Hi smeerbartje,

> **smeerbartje said:**
>  Now I start transmission as a daemon by typing: 'transmission-daemon' on the console. However, How do I stop the daemon? Not by typing /etc/init.d/transmission-daemon stop... (that's not available

I have little experience with running the transmission daemon but I believe the information you are after is on this page:

Scripts/init.d - Transmission
[http://trac.transmissionbt.com/wiki/Scripts/initd](http://trac.transmissionbt.com/wiki/Scripts/initd)

Hopefully this will help?

Andrew

---

### Post by smeerbartje on 2010-01-31
> **andrew.46 said:**
> Hi smeerbartje,



I have little experience with running the transmission daemon but I believe the information you are after is on this page:

Scripts/init.d - Transmission
[http://trac.transmissionbt.com/wiki/Scripts/initd](http://trac.transmissionbt.com/wiki/Scripts/initd)

Hopefully this will help?

Andrew

Thanks, exactly what I was looking for!

---

### Post by Longinus00 on 2010-02-01
For checkinstall, you probably want to do something like this.
```

sudo checkinstall -D --fstrans=yes \
--pkgname=transmission --backup=no --deldoc=yes --deldesc=yes --delspec=yes  --default \
--provides=transmission-cli,transmission-daemon,transmission-common,transmission-gtk \
--pkgversion='`grep "LONG_VERSION_STRING" libtransmission/version.h | cut -d"\"" -f2 | cut -d" " -f1`'

```

---

### Post by smeerbartje on 2010-02-02
> **Longinus00 said:**
> For checkinstall, you probably want to do something like this.
```

sudo checkinstall -D --fstrans=yes \
--pkgname=transmission --backup=no --deldoc=yes --deldesc=yes --delspec=yes  --default \
--provides=transmission-cli,transmission-daemon,transmission-common,transmission-gtk \
--pkgversion='`grep "LONG_VERSION_STRING" libtransmission/version.h | cut -d"\"" -f2 | cut -d" " -f1`'

```

What is the difference? Andrew.46's solution works fine for me :).

---

### Post by andrew.46 on 2010-02-02
Hi Longinus00,

Thanks for your suggestions. Two small points though:

```
checkinstall -D
```

This is given as a default in Ubuntu, have a look in /etc/checkinstallrc, so does not normally need to be given. The other point:

```
--fstrans=yes
```

I believe in Karmic Koala this option is still broken and by default, again in /etc/checkinstallrc, this is turned *off*. The newest version of checkinstall has apparently solved this old problem but I will admit I have not tested this yet.

Thanks for your trouble,

Andrew

---

### Post by leonardo_neo on 2010-02-14
Thanks a lot for this great tutorial.

---

### Post by andrew.46 on 2010-02-15
Hi leonardo,

> **leonardo_neo said:**
> Thanks a lot for this great tutorial.

No problems, glad it has been useful :).

Andrew

---

### Post by prem1er on 2010-02-19
Another successful install this time on 9.04 headless box with Transmission 1.90. One small suggestion being a novice *nix user I had to look up some of the commands I was using before I actually used them on my system (not that I didn't trust it, but just for my knowledge). If you have time you may want to add a brief description before each command. If not no big deal. Thanks again!!

---

### Post by andrew.46 on 2010-02-19
Hi prem1er,

> **prem1er said:**
> Another successful install this time on 9.04 headless box with Transmission 1.90. One small suggestion being a novice *nix user I had to look up some of the commands I was using before I actually used them on my system (not that I didn't trust it, but just for my knowledge). If you have time you may want to add a brief description before each command. If not no big deal. Thanks again!!

Glad the guide has proved helpful to you :). I shall update to 1.90 this weekend, I had not realised that a new version had arrived! When I do this I shall do as you have suggested and add a few explanatory notes...

All the best,

Andrew

---

### Post by prem1er on 2010-02-19
Thanks for getting back to me. I'm playing around with a lot of the new features on here and getting more comfortable with the application. Since 1.8.0 was released, lots of things have changed with the way the application is configured and run. If anyone is interested I would be willing to put together some knowledge base on getting Transmission 1.8.0+ configured on a headless ubuntu server (or for anyone who wants to take advantage of the web interface).  If anyone here has yet to upgrade their version of Transmission, I highly suggest using version 1.90 (which works perfectly with andrew.46's tutorial) , as it has a ton of new features and has also fixed bugs that were causing bans on the 1.80 software from many private torrent sites.

---

### Post by andrew.46 on 2010-02-19
Hi prem1er,

> **prem1er said:**
> If anyone is interested I would be willing to put together some knowledge base on getting Transmission 1.8.0+ configured on a headless ubuntu server (or for anyone who wants to take advantage of the web interface).

I for one would be keen to see such information. I am building a headless server shortly and certainly using transmission in this way would be very new to me. BTW you may have noticed a new notification system is now possible for Transmission with support for libappindicator. I have not added this in but looks like the required libraries for Karmic can be [found here]("https://edge.launchpad.net/~indicator-applet-developers/+archive/indicator-core-ppa"). I suspect I will wait for Lucid before experimenting myself and I see that the [Lucid repository version]("http://changelogs.ubuntu.com/changelogs/pool/main/t/transmission/transmission_1.90-0ubuntu1/changelog") will have this support built in.

Andrew

---

### Post by Charybdisz on 2010-02-21
Thank you andrew.46! I followed your guide on Ubuntu 9.10, and it worked perfectly! Now I have the latest version, much appreciated.

---

### Post by andrew.46 on 2010-02-22
Hi Charybdisz,

> **Charybdisz said:**
> Thank you andrew.46! I followed your guide on Ubuntu 9.10, and it worked perfectly! Now I have the latest version, much appreciated.

Excellent news, I will have to admit that I am a little surprised at how popular this little guide has become :). Perhaps I will write a Lucid version if Transmission development outstrips the repository version too quickly...


All the best,

Andrew

---

### Post by andrew.46 on 2010-02-27
Those Transmission guys never stop, I have updated the guide to cover the release of Transmission 1.9.1 :).

Andrew

---

### Post by Jive Turkey on 2010-03-08
> **smeerbartje said:**
> Well, I'm almost there. I have compiled the latest version and modified the settings.json file. Now I start transmission as a daemon by typing: 'transmission-daemon' on the console. However, How do I stop the daemon? Not by typing /etc/init.d/transmission-daemon stop... (that's not available)

EDIT 1
An additional question: when I make some changes to the config-file, it get's overwritten the next time I restart the server, why is that?

EDIT 2
Problem solved. It seems that Transmission always saves the logfile on exit. Therefore I had to change the logfile before running Transmission. Cool, I'm happy now!

I'm having the same issue but I can't seem to find the log file you are talking about.  What change did you need to make, and where is this logfile?

[rant]For that matter why would they tell us how to configure it using settings.json and then have the app overwrite those settings on every start (without some undocumented hack in some random logfile that isn't in any standard logfile type location)? how does that make any sense?[/rant]

---

### Post by smeerbartje on 2010-03-09
It's simple: just edit the settings file BEFORE starting transmission-daemon. I'm not sure why the settings are being saved once transmission-daemon is shut down.

By the way, can someone please tell me HOW I stop transmission-daemon?

---

### Post by andrew.46 on 2010-03-23
OK so I have updated the guide for Transmission 1.92 and I suspect that will do for my work with this guide as Lucid Lynx is almost upon us. It has been great fun and I hope to see you all using Transmission with Ubuntu Lucid Lynx :).

Andrew

---

### Post by smeerbartje on 2010-03-24
> **andrew.46 said:**
> OK so I have updated the guide for Transmission 1.92 and I suspect that will do for my work with this guide as Lucid Lynx is almost upon us. It has been great fun and I hope to see you all using Transmission with Ubuntu Lucid Lynx :).

Andrew

Hi Andrew, really appreciate your work here!

---

### Post by andrew.46 on 2010-03-24
Hi smeebartje,

> **smeerbartje said:**
> Hi Andrew, really appreciate your work here!

Thanks for those kind words :). Mind you I have just installed Lucid beta 1 and I notice that Transmission is already a little dated there: 1.91. I attach a screenshot and then I must download the Gimp, which is what I usually use for screenshots... I forgot that the default install no longer contains it!

Andrew

---

### Post by Charles Kerr on 2010-03-24
Thanks for the great work, Andrew!

---

### Post by andrew.46 on 2010-03-24
Hi Charles,

> **Charles Kerr said:**
> Thanks for the great work, Andrew!

And again thanks for those kind words :).

All the best,

Andrew

---

### Post by Sonsum on 2010-04-01
This guide is great. Does anybody know of a up-to-date transmission ppa so we can automate the updates?

---

### Post by andrew.46 on 2010-04-02
Hi Sonsum,

Perhaps this:

[https://launchpad.net/~transmissionbt/+archive/ppa](https://launchpad.net/~transmissionbt/+archive/ppa)

but I will admit I have not tried this PPA...

All the best,

Andrew

---

### Post by Sonsum on 2010-04-05
> **andrew.46 said:**
> Hi Sonsum,

Perhaps this:

[https://launchpad.net/~transmissionbt/+archive/ppa](https://launchpad.net/~transmissionbt/+archive/ppa)

but I will admit I have not tried this PPA...

All the best,

Andrew

Wow. I have no idea how I missed that. Thanks!

---

### Post by andrew.46 on 2010-04-05
Hi Sonsum,

> **Sonsum said:**
> Wow. I have no idea how I missed that. Thanks!

My pleasure :). Perhaps you could report back if the PPA has a good quality build?

All the best,

Andrew

---

### Post by Sonsum on 2010-04-07
The PPA seems legit, won't know for sure until a newer version is released though... lol

---

### Post by Jive Turkey on 2010-04-24
I decided to go for the svn approach as detailed at the the projects website. but instead of "make install" I used checkinstall -D and manually filled in the details.

I had to change one line in /etc/init.d/transmission-daemon to reflect the different binary location (change highlighted in red):```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          transmission-daemon
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start or stop the transmission-daemon.
### END INIT INFO

NAME=transmission-daemon
DAEMON=[COLOR="Red"]/usr/local/bin/$NAME[/COLOR]
USER=debian-transmission
# FIXME: no pidfile support; forks, so --make-pidfile doesn't work either
#PIDFILE=/var/run/$NAME.pid
STOP_TIMEOUT=3

export PATH="${PATH:+$PATH:}/sbin"

[ -x $DAEMON ] || exit 0

[ -e /etc/default/$NAME ] && . /etc/default/$NAME

. /lib/lsb/init-functions

start_daemon () {
    if [ $ENABLE_DAEMON != 1 ]; then
        log_progress_msg "(disabled, see /etc/default/${NAME})"
    else    
        start-stop-daemon --start \
        --chuid $USER \
        --exec $DAEMON -- $OPTIONS
    fi
}

case "$1" in
    start)
        log_daemon_msg "Starting bittorrent daemon" "$NAME"
        start_daemon
        log_end_msg 0
        ;;
    stop)
        log_daemon_msg "Stopping bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo
        log_end_msg 0
        ;;
    reload)
        log_daemon_msg "Reloading bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON \
            --oknodo --signal 1
        log_end_msg 0
        ;;
    restart|force-reload)
        log_daemon_msg "Restarting bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo
        start_daemon
        log_end_msg 0
        ;;
    *)
        echo "Usage: /etc/init.d/$NAME {start|stop|reload|force-reload|restart}"
        exit 2
        ;;
esac

exit 0
```
Then I had to make the debian-transmission user with:```
adduser --system --group --no-create-home --quiet debian-transmission
``` and all appears to be working so I updated rc-d to make sure it runs at boot time (I have yet to test this) with ```
sudo update-rc.d transmission-daemon defaults
```
Lastly, it remains unclear to me whether my daemon is gettin its config from which of these directories```
~/.config/transmission-daemon/
/etc/transmission-daemon/
/var/lib/transmission-daemon/info/
```
So I copied the one I edited to suit me to all three locations like so:```
sudo service transmission-daemon stop && sudo cp ~/.config/transmission-daemon/settings.json /etc/transmission-daemon/settings.json && sudo cp ~/.config/transmission-daemon/settings.json /var/lib/transmission-daemon/info/settings.json
``` It starts ok on reboot but fails to actually read from the watch directory or write any files even though it can connect to peers, the download directory is owned and writable by debian-transmission, grrrr... my syslog gets these before transmission-daemon gives up and pauses the torrents:```
Watching "/moo/torrent/src/" for new .torrent files (daemon.c:456)
Using inotify to watch directory "/moo/torrent/src/" (watch.c:84)
Unable to watch "/moo/torrent/src/": Permission denied (watch.c:90)
--snip--
Couldn't create "/moo/torrent": Permission denied (utils.c:605)
Couldn't create "/moo/torrent/incomplete/The Ghost Of Grand Rapids": Permission denied (fdlimit.c:362)
The Ghost Of Grand Rapids tr_fdFileCheckout failed for "/moo/torrent/incomplete/The Ghost Of Grand Rapids/GhostOfGrandRapids.avi.part": Permission denied (inout.c:134)
Couldn't create "/moo/torrent": Permission denied (utils.c:605)
Couldn't create "/moo/torrent/incomplete/The Ghost Of Grand Rapids": Permission denied (fdlimit.c:362)
The Ghost Of Grand Rapids tr_fdFileCheckout failed for "/moo/torrent/incomplete/The Ghost Of Grand Rapids/GhostOfGrandRapids.avi.part": Permission denied (inout.c:134)
``` 

Any ideas guys?

---

### Post by yug23 on 2010-04-28
Thanks for the guide Andrew, very useful, looking forward to installing this on Luicd as well.

I found this guide because the version of Transmission in the Karmic repos was causing my whole samba network to go slow- I have a laptop dualbooting Karmic and WinXP, a headless server running Karmic and a modded xbox running XBMC. 

Once I removed the gui from the server and installed cli versions of several programs, the whole network ground almost to a halt. This was of course the opposite of the intention, but I tracked down the culprit: transmission-daemon. So I am trying this new version from the guide to see whether it's any better- unfortunately as I'm writing this it seems to be on a go-slow again - the music I'm streaming is stuttering... any ideas why this might be happening?

Anyway I wanted to respond to the post from Jive Turkey - I can confirm that the daemon gets its settings from ```
~/.config/transmission-daemon/
```

I am having a problem though in that the transmission remote gui and web interface refuse to connect to the daemon if it's running as a service (the web interface says 'incorrect username or password' and the remote gui program says that I have not enabled the whitelist when I have).
I have to do 'sudo /etc/init.d/transmission-daemon stop' when the server boots, then start it manually with 'transmission-daemon', then I can connect to the daemon remotely. Again, any clues?

Also I tried to make the download folder for transmission writeable by the debian-transmission user but it says 'Operation not permitted', even when I use sudo.

I know I should probably create a separate thread for each of these issues but I thought as people who have posted here have set this up and might have a similar situation to me, they might be able to provide the answers directly.

Thanks for any help in advance.

---

### Post by snapy on 2010-04-30
thank you very much for this thread!

---

### Post by doccc on 2010-05-15
Great work man!

> **andrew.46 said:**
> Next download the source code, open the tarball and compile and install it:

```

$ cd $HOME
$ wget http://mirrors.m0k.org/transmission/files/transmission-1.92.tar.bz2
$ tar xjvf transmission-1.92.tar.bz2
$ cd transmission-1.92
$ ./configure
$ make
$ sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
  --deldesc=yes --delspec=yes --default --pkgversion "1.92"
$ make distclean


```And that is it! This gives you the newest version of a great BitTorrent program, perfect for downloading and sharing the latest versions of Ubuntu. Remember: Have Fun!!

I've done everything else up until here,I'm confused about this part can I have detailed instructions of how to please

Thanks,

Doccc

---

### Post by mchlor on 2010-06-15
excellent guide.

---

### Post by s3v3nsins on 2010-11-01
Sorry to dig up such an old thread, but I would like to know this

1. Does andrew.46's guide make an installation of transmission whereby the GTK frontend connects to the daemon at the default rpc port of 9091 ?

2. Does this installation ensure that even if the GTK front end is closed (not minimized to tray) the daemon will continue to run at the background and download files ?

---

### Post by s3v3nsins on 2010-11-12
Hi andrew.46 can you please respond back to the above query ?

---

### Post by andrew.46 on 2010-11-18
Hi s3v3nsins,

> **s3v3nsins said:**
> Hi andrew.46 can you please respond back to the above query ?

My apologies, I have not really looked at this guide for a while :(. Unfortunately I am not sure of this answer as I no longer run Karmic Koala or Transmission for that matter.

Apologies,

Andrew

---

### Post by nothingspecial on 2012-04-07
Closed and moved to Outdated Tutorials at the authors request.

---

