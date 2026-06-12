---
title: "HOWTO: Peerguardian Installation and automatic updates"
date: 2005-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Kokanee on 2005-11-27
**PeerGuardian** is a free and open source IP address blocking software programs capable of blocking incoming and outgoing addresses. The application uses a [blocklist]("http://en.wikipedia.org/wiki/Blacklist#Computing") of IP addresses to filter the computers of several organisations, including the [RIAA]("http://en.wikipedia.org/wiki/RIAA") and [MPAA]("http://en.wikipedia.org/wiki/MPAA") while using filesharing networks such as [FastTrack]("http://en.wikipedia.org/wiki/FastTrack") and [BitTorrent]("http://en.wikipedia.org/wiki/BitTorrent"). The system is also capable of blocking [advertising]("http://en.wikipedia.org/wiki/Advertising"), [spyware]("http://en.wikipedia.org/wiki/Spyware"), [government]("http://en.wikipedia.org/wiki/Government") and [educational]("http://en.wikipedia.org/wiki/Educational") ranges, depending upon user preferences.

[More at WikiPedia]("http://en.wikipedia.org/wiki/PeerGuardian").

**PeerGuardian is not a firewall. ** It filters your incoming/outgoing connections. It is usefull when on P2P networks because it blocks the RIAA, MPAA and other evile empires from seeing you. This helps because they can not collect evidence against you and will help in filtering the bogus seeded files they litter the P2P networks with.

Okey, lets get started. Download and install PeerGuardian. There is a .DEB package and source code posted on their SoureForge site. This HOWTO will use the DEB. 

[http://sourceforge.net/project/showfiles.php?group_id=131687&package_id=148849]("http://sourceforge.net/project/showfiles.php?group_id=131687&package_id=148849")

```
sudo dpkg -i peerguardnf-1.5beta.i386.deb
``` 
Now that it's installed blocklists need to be setup.

```
sudo mkdir /etc/peerguardian
``` 
Create a blank text file and save it as **peerguardian.sh**.

```
sudo cp peerguardian.sh /usr/local/bin
``` 
```
sudo chmod -c 755 /usr/local/bin/peerguardian.sh
``` 
Now open peerguardian.sh wth gedit....

```
sudo gedit /usr/local/bin/peerguardian.sh
``` 
Now paste the following into it then save and close:

```
# version for bluetack.co.uk lists!
#!/bin/sh
# Update new blocklists and start/stop/restart PeerGuardian
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
# testdescription
#
#CONFIGURATION
# Make sure PG_ETC points to the directory where
# you want to put your downloaded blocklists.
PG_ETC=/etc/peerguardian/
# Remove the lists you don't want to download and
# use from BLOCKLISTS.
BLOCKLISTS="level1"
PG_CONF=/etc/PG.conf
PG_LOG=/var/log/PG.log
PG_LIST=/etc/p2p.p2b.p2p
#The URL where the blocklists reside
URL=http://www.bluetack.co.uk/config
#The format of the lists to download
SUFFIX=gz
#The format after unpacking
SUFFIX2=txt

endscript () {
date +"------------ "%F" "%X" "%Z" End PeerGuardian Script"
exit $1
}
date +"------------ "%F" "%X" "%Z" Begin PeerGuardian $1"


case "$1" in
'start')
    cd "$PG_ETC"
    # check if blockfiles were updated:
    UPDATED=""
    for i in $BLOCKLISTS ; do
    TIMESTAMP=0
    if [ -e $i.$SUFFIX ] ; then
    TIMESTAMP=`stat --format=%y $i.$SUFFIX`
    echo "File $i.$SUFFIX last updated $TIMESTAMP"
    TIMESTAMP=`stat --format=%Y $i.$SUFFIX`
    fi
    wget -N $URL/$i.$SUFFIX
    if [ `stat --format=%Y $i.$SUFFIX` -gt $TIMESTAMP ] ; then
    UPDATED=$i
    fi
    done
    
    # if none of the blockfiles were updated:
    if [ -z $UPDATED ] ; then
    echo "No blocklists needed updating."
    echo "Starting PeerGuardian"
    mv $PG_LOG $PG_LOG.backup
    peerguardnf -h -m -d -c "$PG_CONF" -l "$PG_LOG"
    endscript 0
    fi
    
    # if any blockfiles were updated:
    for i in $BLOCKLISTS ; do
    gunzip -c $i.$SUFFIX > $i.$SUFFIX2
    BLOCKLISTSCAT="$BLOCKLISTSCAT $i.$SUFFIX2"
    done
    cat $BLOCKLISTSCAT | peerguardnf -f merged.p2b.p2p
    for i in $BLOCKLISTS ; do
    rm $i.$SUFFIX2
    done
    # uncomment below to unblock Yahoo! Mail and whatever
    # else needs unblocking here. Do this also in the
    # restart section.
    grep -v -i "yahoo\!" merged.p2b.p2p | grep -v -i "Microsoft" | grep -v "Google" > merged.p2b.p2p.tmp
    mv merged.p2b.p2p.tmp merged.p2b.p2p
    mv $PG_LIST $PG_LIST.backup
    mv merged.p2b.p2p $PG_LIST
    mv $PG_LOG $PG_LOG.backup
    echo "Starting PeerGuardian"
    peerguardnf -h -m -d -c "$PG_CONF" -l "$PG_LOG"
    endscript 0
    ;;

'stop')
    echo "Stopping PeerGuardian"
    killall peerguardnf > /dev/null 2>&1
    endscript 0
    ;;

'restart')
    cd "$PG_ETC"
    # check if blockfiles were updated:
    UPDATED=""
    for i in $BLOCKLISTS ; do
    TIMESTAMP=0
    if [ -e $i.$SUFFIX ] ; then
    TIMESTAMP=`stat --format=%y $i.$SUFFIX`
    echo "File $i.$SUFFIX last updated $TIMESTAMP"
    TIMESTAMP=`stat --format=%Y $i.$SUFFIX`
    fi
    wget -N $URL/$i.$SUFFIX
    if [ `stat --format=%Y $i.$SUFFIX` -gt $TIMESTAMP ] ; then
    UPDATED=$i
    fi
    done
    
    # if none of the blockfiles were updated:
    if [ -z $UPDATED ] ; then
    echo "No blocklists needed updating."
    echo "Stopping PeerGuardian"
    killall peerguardnf > /dev/null 2>&1
    mv $PG_LOG $PG_LOG.backup
    sleep 4
    echo "Starting PeerGuardian"
    peerguardnf -h -m -d -c "$PG_CONF" -l "$PG_LOG"
    endscript 0
    fi
    
    # if any blockfiles were updated:
    for i in $BLOCKLISTS ; do
    gunzip -c $i.$SUFFIX > $i.$SUFFIX2
    BLOCKLISTSCAT="$BLOCKLISTSCAT $i.$SUFFIX2"
    done
    cat $BLOCKLISTSCAT | peerguardnf -f merged.p2b.p2p
    for i in $BLOCKLISTS ; do
    rm $i.$SUFFIX2
    done
    # uncomment below to unblock Yahoo! Mail and whatever
    # else needs unblocking here. Do this also in the
    # restart section.
    grep -v -i "yahoo\!" merged.p2b.p2p | grep -v -i "Microsoft" | grep -v "Google" > merged.p2b.p2p.tmp
    mv merged.p2b.p2p.tmp merged.p2b.p2p
    echo "Stopping PeerGuardian"
    killall peerguardnf > /dev/null 2>&1
    mv $PG_LIST $PG_LIST.backup
    mv merged.p2b.p2p $PG_LIST
    mv $PG_LOG $PG_LOG.backup
    sleep 4
    echo "Starting PeerGuardian"
    peerguardnf -h -m -d -c "$PG_CONF" -l "$PG_LOG"
    endscript 0
    ;;

*)
    echo "Usage: $0 { start | stop | restart }"
    ;;
esac
exit 0
``` 
You can now handle PeerGuardian by just typing in a console one of the following commands:

```
sudo peerguardian.sh start
``` 
IF there are updates for the blocklists available they are updated, the old blocklist and the log-file are backuped and PeerGuardian is started.

```
sudo peerguardian.sh restart
``` 
If there are updates for the blocklists available they are updated, the old blocklist and the log-file are backuped, old PeerGuardian processes are killed and after 4 seconds PeerGuardian is started again.

```
sudo peerguardian.sh stop
``` 
PeerGuardian is stopped.

**This following section is optional.**  If you want Peerguardian to run at startup and update the blocklists daily.

```
ln -s /usr/local/bin/peerguardian.sh /etc/init.d/peerguardian.sh
ln -s /etc/init.d/peerguardian.sh /etc/rc0.d/K20peerguardian.sh
ln -s /etc/init.d/peerguardian.sh /etc/rc2.d/S95peerguardian.sh
ln -s /etc/init.d/peerguardian.sh /etc/rc3.d/S95peerguardian.sh
ln -s /etc/init.d/peerguardian.sh /etc/rc4.d/S95peerguardian.sh
ln -s /etc/init.d/peerguardian.sh /etc/rc5.d/S95peerguardian.sh
ln -s /etc/init.d/peerguardian.sh /etc/rc6.d/K20peerguardian.sh
``` 
Now we need to create a CRON entry to update and restart Peerguardian daily. Create a blank text file called **pg**.  

```
sudo gedit pg
``` 
Paste the following into it:

```
#!/bin/sh

/usr/local/bin/peerguardian.sh restart
``` 
Save and close then we need to copy it and set permissions.

```
sudo cp pg /etc/cron.daily
``` 
```
sudo chmod -c 755 /etc/cron.daily/pg
``` 
Now we're done. You will notice in the script that connections to Yahoo, Microsoft and Google are allowed. I was having issues with connecting to MSN and Gtalk in Gaim along with connectiong to various Google sites. If you don't use these service you can leave that out.

Everything will be logged in /var/log/PG.log

This is the [original source]("http://forums.phoenixlabs.org/showthread.php?t=7270&page=3&pp=10") for this info.  I just changed it a bit.

---

### Post by ounas on 2005-11-28
Thanks, I shall try this out.

_ounas :o

---

### Post by Arktis on 2005-11-28
Oh crap...  I just completed a howto on this covering installation from source.  In my defense, I didn't see this, and I did search.. but I realize now that when searching, I spelled guardian as "gaurdian" by mistake and thus only came up with 3 results.  Ah well.  Sorry.  Maybe it won't be approved by the mods.

---

### Post by ephman on 2005-11-29
Never mind below, all is well, i had to start the script again and it worked fine.


hi,

thanks for the howto, i've been looking for something like this.  here's an error i get when i start peerguardian, at least i think it's an error, any help would be appreciated.  

root@wintermute:/home/ephman/Desktop# sudo peerguardian.sh start
------------ 2005-11-29 05:54:48 AM EST Begin PeerGuardian start
--05:54:49--  [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)
           => `level1.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... failed: Name or service not known.
stat: cannot stat `level1.gz': No such file or directory
/usr/local/bin/peerguardian.sh: line 57: [: -gt: unary operator expected
No blocklists needed updating.
Starting PeerGuardian
mv: cannot stat `/var/log/PG.log': No such file or directory
------------ 2005-11-29 05:54:59 AM EST End PeerGuardian Script
root@wintermute:/home/ephman/Desktop#


thanks for the bandwidth,
ephman

---

### Post by ubuntu27 on 2005-11-30
In this how to for "PeerGuardian 2" or "PeerGuardian Lite" or neither?

---

### Post by Grimlock on 2005-12-01
I've installed it but I can still get on the riaa website?????

---

### Post by ephman on 2005-12-01
same here.

---

### Post by Kokanee on 2005-12-02
[quote=ubuntu27]In this how to for "PeerGuardian 2" or "PeerGuardian Lite" or neither?[/quote]

PeerGuardian for Linux is actually the Lite version.  PeerGuardian 2 is an awful Windows app with a useless gui.

---

### Post by Kokanee on 2005-12-02
[quote=Grimlock]I've installed it but I can still get on the riaa website?????[/quote]

Visiting a website is harmless.  Open up a torrent or connect to aMule or something then check your /var/log/PG.log file.  It should show lots of dropped connections.

---

### Post by ace2005 on 2005-12-04
Um... guys

Do a scan:

[http://scan.sygatetech.com/stealthscan.html](http://scan.sygatetech.com/stealthscan.html)

Who here thinks there is a problem ;)

---

### Post by Kokanee on 2005-12-04
All mine report blocked.  That is because I am running the iptables firewall.  You must have missed the part in the first post in big bold letters that says Peerguardian is not a firewall.

---

### Post by ace2005 on 2005-12-04
I also get this in my log:

Reading blocklist
detected ASCII blocklist
Entering daemon mode
Blocking 87916 ranges (658873113 IP addresses)
error: $

:(

Edit: SOLVED

------------------------======--------------------

When i'm running PG its always saying closed and not blocked, how did you get it to say blocked?

---

### Post by ace2005 on 2005-12-04
Start PG, do a scan and they're all closed

Stop PG do a scan and they are all blocked

Restart PG, do a scan and they're all closed

What the hell is going on?

> All mine report blocked. That is because I am running the iptables firewall. You must have missed the part in the first post in big bold letters that says Peerguardian is not a firewall.

Doesn't PG use Iptables?, and wouldn't this suggest that its causing the problem?

And i found this:

[http://forums.phoenixlabs.org/t9901-pg-linux-disables-your-firewall.html](http://forums.phoenixlabs.org/t9901-pg-linux-disables-your-firewall.html)

Did you set it up so that IPtables will block stuff while PG is running just like when it is not? if so how did you do it?

I'm a noob and i need help

---

### Post by Kokanee on 2005-12-04
I have used [Firestarter]("http://www.fs-security.com/") to activate the iptables firewall.  The firewall works good and Peerguardian works as well.  When I connect to eMule or Gnutella the log show lots of dropped connections.  The script that Firestater makes seems to play nice with Peerguardian.  I have read that post before which concerned me but everything seems to work with firestarter. :confused:

If you don't know what Firestarter is... it's a front end for iptables and  a monitoring program.

Try it out.

```
sudo apt-get install firestarter
```

---

### Post by ace2005 on 2005-12-04
I think you're wrong on this one, i disabled the allow all on http, then tried to go to the IRAA's site, didn't work, so everythings fine with the blocking, did a sygate scan and everything is closed so i started firestarter, "sudo firestarter" and firestarter was running and did a scan from sygate, everything looked fine, all blocked, went to the IRAA's site again and it LOADED!!! :eek: 

Closed firestarter, quit from it, restarted PG and all the ports were closed again and the IRAAs site was blocked again.

Argh!!!!!! This is annoying!!!!!!!

How did you get them to work together?

I need HELP and what about the rest of the people in the thread? how's it working for you?

---

### Post by Nutterpc on 2005-12-07
I've currently got Peerguardian running perfectly with my own iptables firewall (which I have on my webspace), and I've had no probs with them running together.

If anyone wants a hand setting up the two to work. gimme a pm and I'll do what I can to help :)

---

### Post by Aussie on 2005-12-08
Nice HOWTO, worked a charm...I think.  How do I know if it's working?

---

### Post by Bloot on 2005-12-08
[QUOTE=Aussie]Nice HOWTO, worked a charm...I think.  How do I know if it's working?[/QUOTE]
Type *pgtext* in a terminal and then go to *Monitor PG*.

---

### Post by Aussie on 2005-12-08
This is what I got:

>                  PEERGUARDIAN v1.5beta


          Packets Blocked               Packets Checked
              0                             377858


                              Blocked
Reading blocklist
detected ASCII blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 42555 ranges (636415032 IP addresses)
error: $

So how will i know if it blocks something?  Will that also show up in the log?

---

### Post by Bloot on 2005-12-08
Something's wrong with your peerguardian... it alerts you with an error

Mine shows that in the present moment

```

                         PEERGUARDIAN v1.5beta    ****** ******


          Packets Blocked               Packets Checked
              1237                          6164983


                              Blocked
dropped src: 204.188.166.137 dst: 192.168.2.2 (Savvis)
dropped src: 192.168.2.2 dst: 198.150.196.50 (WiscNet)
dropped src: 192.168.2.2 dst: 128.12.22.158 (Stanford University)
dropped src: 192.168.2.2 dst: 80.102.165.9 (Uni2 IP Data Network)
dropped src: 192.168.2.2 dst: 147.230.153.45 (Network of Technical University at Liberec)
dropped src: 192.168.2.2 dst: 129.108.212.177 (University of Texas at El Paso)
dropped src: 192.168.2.2 dst: 198.150.196.50 (WiscNet)
dropped src: 192.168.2.2 dst: 128.12.22.158 (Stanford University)



```

---

### Post by Aussie on 2005-12-08
> Something's wrong with your peerguardian

So should mine be reading like yours?  Or will it look like that when someone trys to connect with my system?

Thanks.

---

### Post by Bloot on 2005-12-08
Well, if you open a p2p program it's for sure peerguardian should show blocked packets. Try it.

---

### Post by Aussie on 2005-12-08
I just opened limewire and did a search, and nothing has changed.  The log still reads:


Reading blocklist
detected ASCII blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 42555 ranges (636415032 IP addresses)
error: $

I followed the instructions, did I miss something?

---

### Post by Bloot on 2005-12-08
Maybe restarting the script it will work

```
sudo peerguardian.sh restart
```

---

### Post by Aussie on 2005-12-08
Just restarted it and this is what I get:

P.S I also reinstalled the .deb but I still don't think its working.  Does it have anything to do with the router that my computer is hooked up to?


@Ubuntu:~$ sudo peerguardian.sh restart
------------ 2005-12-08 23:15:24 EST Begin PeerGuardian restart
File level1.gz last updated 2005-12-08 16:27:22.000000000 +1100
--23:15:24--  [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)
           => `level1.gz'
Resolving [www.bluetack.co.uk](www.bluetack.co.uk)... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/level1.gz](http://dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/level1.gz) [following]
--23:15:25--  [http://dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/level1.gz](http://dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/level1.gz)
           => `level1.gz'
Resolving dialspace.dial.pipex.com... 195.129.111.61, 195.129.111.62, 195.129.111.86, ...
Connecting to dialspace.dial.pipex.com|195.129.111.61|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,490,467 (1.4M) [text/plain]
Server file no newer than local file `level1.gz' -- not retrieving.

No blocklists needed updating.
Stopping PeerGuardian
Starting PeerGuardian
------------ 2005-12-08 23:15:31 EST End PeerGuardian Script

---

### Post by Aussie on 2005-12-08
Thanks,

Just got it to work, must have been either reinstalling the deb or restarting it that fixed it.

Thanks again.

---

### Post by househead on 2005-12-08
Peerguardian stops me from being able to use SSL websites for some reason. 

[OT]Firestarter is excellent, apart from the fact it makes no distinction whatsoever between UDP/TCP, which IMO is a showstopper. Why should I open two ports, when I only need one?!

---

### Post by Locutus on 2005-12-08
I followed the instructions from the howto and I cannot SSH into my box anymore. Any ideas?

---

### Post by ace2005 on 2005-12-08
Oh now i see why everyione thinks its working, you lot are just using the command line, oh man

[http://www.lynucs.org/index.php?screen_type=1&screen_id=17659520764394beddc176d&m=screen](http://www.lynucs.org/index.php?screen_type=1&screen_id=17659520764394beddc176d&m=screen)


This is how i know its working or not (yea yea i know vista like)

I start the entire thing with "sudo alltray /usr/bin/peerguardnf2/peerguardnf2" Alltray puts the GUI in the system tray and when i click he close button on the window border it goes back to the system try (the system tray is not in view, it autohides in the bottom right hand corder, its vertical)

It clearly shows if the daemon is active, Then in the "Root configuration" remove all the allowed ports (80 is default) then go to the IRAA site, and you can't, do a sygate scan and it shows everything is closed" not blocked,

Then stop it and the ports are back to blocked again :mad: 

See what i mean, i turned it **on** in the middle of a scan

[http://img356.imageshack.us/my.php?image=screenshiotpgblockingwellnotso.jpg](http://img356.imageshack.us/my.php?image=screenshiotpgblockingwellnotso.jpg)

---

### Post by ace2005 on 2005-12-08
[QUOTE=househead]Peerguardian stops me from being able to use SSL websites for some reason.[/QUOTE]


Did you try allowing port 443?

[QUOTE=Locutus]I followed the instructions from the howto and I cannot SSH into my box anymore. Any ideas?[/QUOTE]

Same thing but i have no idea what SSH or what port it works on

---

### Post by ace2005 on 2005-12-08
[QUOTE=Bloot]Type *pgtext* in a terminal and then go to *Monitor PG*.[/QUOTE]

Is this in realtime or does it just read it and just display what is there at that moment?

---

### Post by Josef K. on 2005-12-08
[QUOTE=Arktis]Oh crap...  I just completed a howto on this covering installation from source.  In my defense, I didn't see this, and I did search.. but I realize now that when searching, I spelled guardian as "gaurdian" by mistake and thus only came up with 3 results.  Ah well.  Sorry.  Maybe it won't be approved by the mods.[/QUOTE]

don't underestimate source compiling ;) 
since I use breezy64, I can't use kokanee guide, but maybe I can try yours :D 
where is it?

---

### Post by Bloot on 2005-12-08
[QUOTE=ace2005]Is this in realtime or does it just read it and just display what is there at that moment?[/QUOTE]

I do think it reads the PG.log file in /var/log, but not in real-time because I've noticed it sometimes shows the blocked packets a bit late.

---

### Post by ace2005 on 2005-12-09
So how come no ones using the GUI?

[http://forums.phoenixlabs.org/t7270-peerguardin-daemongui-installations-amp-update-script.html](http://forums.phoenixlabs.org/t7270-peerguardin-daemongui-installations-amp-update-script.html)

---

### Post by househead on 2005-12-09
[QUOTE=ace2005]Did you try allowing port 443?
[/QUOTE]

I thought it wasn't a firewall!?

---

### Post by ace2005 on 2005-12-09
Well the filtering system could be messing with the SSL stuff on port 443 so i just guessed that if you allowed all connections regardless of source on that port only then it might work.

So what does a sygate scan on you're system show?

---

### Post by Kokanee on 2005-12-10
[quote=ace2005]So how come no ones using the GUI?

[http://forums.phoenixlabs.org/t7270-peerguardin-daemongui-installations-amp-update-script.html]("http://forums.phoenixlabs.org/t7270-peerguardin-daemongui-installations-amp-update-script.html")[/quote]

It looks all right but it is a KDE app.  I am a Gnome user and don't have any KDE or QT packages installed.  ANother reason is that I don't care what it's doing.  I just want it to work and not bother me.  :p

---

### Post by ephman on 2005-12-10
how could i add other lists to download and include?  such as 

[http://www.bluetack.co.uk/config/level2.gz](http://www.bluetack.co.uk/config/level2.gz)

thanks for the bandwidth,
ephman

---

### Post by Kokanee on 2005-12-10
[quote=ephman]how could i add other lists to download and include?  such as 

[http://www.bluetack.co.uk/config/level2.gz]("http://www.bluetack.co.uk/config/level2.gz")[/quote] 
Open your /usr/local/bin/peerguardian.sh and look for the line that starts with BLOCKLISTS=".......

The following can be put in that option:

ads-trackers-and-bad-pr0n
edu
level1
level2 
Microsoft
spider
spyware

So for example to use both level1 and level2 put:

```
BLOCKLISTS="level1 level2"
```

---

### Post by Nutterpc on 2005-12-11
well I found a few issues with the script you had up on the first page

for instance, after getting peerguardian to work, and looking at the logfile, it was listing that it was running successfully, and blocking 0 IP Ranges?????

That got me.....I was thinking WTF....how the heck is it doing that?

So I've spent the past 2 weeks working away at it........

And needless to say, without revealing too much:

Reading blocklist
detected ASCII blocklist
Entering daemon mode
Blocking 168504 ranges (980490802 IP addresses)

;) Hows that sound

UPDATE: Successful integration of my own iptables firewall & peerguardian has happened!!!!! :D:D:D:D:D I've checked to see my firewall is still running, which it is, and checked the logs of peerguardian, and its doing what its supposed to (Not bad for an aussie eh;) )

Here's a bit of proof its dropping packets:

dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)

:)

---

### Post by fede on 2005-12-14
Hello,

   I get this error, running breezy... Am I missing something? 

   When it says

```

peerguardnf: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

   Is it because I should install libstdc++5? (checked and got version 6 installed)

    Thanks a lot for your help!

```

fede@ubuntu:/usr/local/bin$ peerguardian.sh restart
------------ 2005-12-14 09:12:09 PM ART Begin PeerGuardian restart
File level1.gz last updated 2005-12-13 22:10:42.000000000 -0300
--21:12:09--  http://www.bluetack.co.uk/config/level1.gz
           => `level1.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/level1.gz [following]
--21:12:10--  http://dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/level1.gz
           => `level1.gz'
Resolving dialspace.dial.pipex.com... 195.129.111.62, 195.129.111.86, 195.129.111.87, ...
Connecting to dialspace.dial.pipex.com|195.129.111.62|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,493,877 (1.4M) [text/plain]
Server file no newer than local file `level1.gz' -- not retrieving.

No blocklists needed updating.
Stopping PeerGuardian
mv: cannot stat `/var/log/PG.log': No such file or directory
Starting PeerGuardian
peerguardnf: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
------------ 2005-12-14 09:12:15 PM ART End PeerGuardian Script

```

---

### Post by Kokanee on 2005-12-14
[quote=fede]Hello,

   I get this error, running breezy... Am I missing something? 

   When it says

```

peerguardnf: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

``` 
   Is it because I should install libstdc++5? (checked and got version 6 installed)

    Thanks a lot for your help![/quote]

I have both 5 and 6 installed.  So, yes, install version 5 as well and it should work.

---

### Post by fede on 2005-12-14
GREAT! It is working now. Thanks a lot for the info and your help!

---

### Post by foxy123 on 2005-12-15
it looks like peerguardian blocks Virgin Radio stream...
```
dropped src: 10.0.0.3 dst: 69.28.159.90 (Limelight Networks, LLC)
dropped src: 69.28.159.90 dst: 10.0.0.3 (Limelight Networks, LLC)
dropped src: 10.0.0.3 dst: 69.28.159.90 (Limelight Networks, LLC)

```
I guess it is because this Limelight thing appears only when I try to play the stream and the stream plays ok when I stop pg.

I wonder how I can unblock it?

---

### Post by ace2005 on 2005-12-16
Find the blocklist you're using and open it in in kwrite or gedit, do a search for Limelight Networks and delete the one that contain the ranges 10.0.0.3 and 69.28.159.90 or change them into two parts like:

E.g if you wanted to unblock 0.0.0.129 from this: 0.0.0.1-0.0.0.225

You would use these two:
0.0.0.1 - 0.0.0.128 this is the first part
0.0.0.130 - 0.0.0.225

---

### Post by ace2005 on 2005-12-16
[QUOTE=Nutterpc]well I found a few issues with the script you had up on the first page

for instance, after getting peerguardian to work, and looking at the logfile, it was listing that it was running successfully, and blocking 0 IP Ranges?????

That got me.....I was thinking WTF....how the heck is it doing that?

So I've spent the past 2 weeks working away at it........

And needless to say, without revealing too much:

Reading blocklist
detected ASCII blocklist
Entering daemon mode
Blocking 168504 ranges (980490802 IP addresses)

;) Hows that sound

UPDATE: Successful integration of my own iptables firewall & peerguardian has happened!!!!! :D:D:D:D:D I've checked to see my firewall is still running, which it is, and checked the logs of peerguardian, and its doing what its supposed to (Not bad for an aussie eh;) )

Here's a bit of proof its dropping packets:

dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)
dropped src: 192.168.1.100 dst: 205.156.51.200 (The National Oceanic and Atmospheric Administration)

:)[/QUOTE]

How did you get the ports to be blocked, any chance of a how to?

---

### Post by Nutterpc on 2005-12-16
I'm actually in the middle of a rewrite of my previous version iptables firewall, and one of the things which is being integrated with it is Peerguardian

a few people have pm'd me about it, if you like I can let you know once my friend and I finish the new firewall

---

### Post by ace2005 on 2005-12-18
Thanks, that's be great :)

---

### Post by Nutterpc on 2005-12-18
just that over the christmas break, I'm gunna be rather drunk.........not much use trying to do firewall stuff while under the influence :)

---

### Post by spockrock on 2005-12-18
thanks I have peerguardian working..........

---

### Post by gpeck157 on 2006-01-12
Hi Kokanee,

I followed your instructions for installing peerguardian, and I'm able to start it up from my terminal with no problem. I went further, and followed the instructions for starting it up automatically, but it's not starting up automatically. I know this because when I go to my terminal and tell it to start peerguardian, it does, and it shouldn't if it is already running, correct?

I'm using Ubuntu 5.10 Breezy. I rechecked to make sure I followed your instructions, and I'm certain I followed them to the letter. Any help would be appreciated.

Thanks...

---

### Post by Nutterpc on 2006-01-14
gpeck, if u want, talk to me on msn, I can give you a hand getting it going if you like :)

my email for msn is pretty self explanatory

---

### Post by kosmic on 2006-01-14
Hum I don't understand why you do this :
 
Code:
[LEFT]ln -s /usr/local/bin/peerguardian.sh /etc/init.d/peerguardian.shln -s /etc/init.d/peerguardian.sh /etc/rc0.d/K20peerguardian.shln -s /etc/init.d/peerguardian.sh /etc/rc2.d/S95peerguardian.shln -s /etc/init.d/peerguardian.sh /etc/rc3.d/S95peerguardian.shln -s /etc/init.d/peerguardian.sh /etc/rc4.d/S95peerguardian.shln -s /etc/init.d/peerguardian.sh /etc/rc5.d/S95peerguardian.shln -s /etc/init.d/peerguardian.sh /etc/rc6.d/K20peerguardian.sh[/LEFT]
 
Why do you put peerguardian in all the runlevels ? if you put peerguardian runlevel 3 (Multiuser) it should start always, You should only put peerguardian in /etc/init.d and for example in /etc/init.d/rc3.d/.
 
 
More info about runlevels where : [http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-init-boot-shutdown-init.html]("http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-init-boot-shutdown-init.html")

---

### Post by joflow on 2006-03-22
So it seems that firestarter and peer guardian can not work together since firestarter doesn't play well with iptables (or something of that nature).  What is a solution for someone who wants peer guardian but still needs a firewall (CLI since this is going to be on a server)?  Shouldn't Firehol play well with peer guardian?

---

### Post by jipke on 2006-03-23
Two questions:

At the moment I've got PeerGuardian running automaticly after login (I've followed the instructions above). I've changed my mind and wish to start PeerGuardian by hand. How do I remove those symlinks?

And if I want to completly remove PeerGuardian from my system, how do I do that? (sorry for the noob question).

---

### Post by Jabbadahut on 2006-03-27
Hello, I am having trouble installing this program.

I downloaded the program, then ran the following command as described above.

```


jay@jabbadahut:~$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
dpkg: error processing peerguardnf-1.5beta.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb


```

Then I remembered I downloaded it to the Desktop folder, and made the appropriate changes -

```


jay@jabbadahut:~$ cd Desktop
jay@jabbadahut:~/Desktop$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
(Reading database ... 80004 files and directories currently installed.)
Preparing to replace peerguardnf 1.5 (using peerguardnf-1.5beta.i386.deb) ...
Unpacking replacement peerguardnf ...
Setting up peerguardnf (1.5) ...


```

Then, I created the folder as shown above - "mkdir /etc/peerguardian", no problem there.

However, I am having trouble creating the peerguardian.sh file.

```


jay@jabbadahut:~$ sudo cp peerguardian.sh /usr/local/bin
cp: cannot stat `peerguardian.sh': No such file or directory


```

I'm relatively new to Linux, but I copied & pasted the commands correctly.  However,  as you can see above, I am having trouble creating the 'peerguardian.sh' file.  What did I do wrong?

---

### Post by Jabbadahut on 2006-03-28
I would love to know how to solve this problem. :)

---

### Post by Drain on 2006-04-10
> However, I am having trouble creating the peerguardian.sh file.

```


jay@jabbadahut:~$ sudo cp peerguardian.sh /usr/local/bin
cp: cannot stat `peerguardian.sh': No such file or directory


```

I'm relatively new to Linux, but I copied & pasted the commands correctly.  However,  as you can see above, I am having trouble creating the 'peerguardian.sh' file.  What did I do wrong?

I just installed that, and noticed the same thing - then I realized I didn't create a file called "peerguardian.sh"  

So open a text editor, save a blank file named "peerguardian.sh" to your home directory, and try it again.  :-)

EDIT: Not that I'm having that much more success - when I attempt to monitor the blocks with pgtext, I get a message (repeating over and over) ERROR OPENING PIPE .

---

### Post by Nutterpc on 2006-04-26
Well for anyone who wants a bit of a hand getting these to work together, add me on msn and I'll be only too happy to set you up :)

Getting the two to work together, being a firewall & peerguardian is a little bit of work

---

### Post by unnes on 2006-04-26
I can get PG to work, but when I try to to add it to my startup I run into errors. I thought I might be able to use chmod to gain permissions (I don't really know what I'm doing), but no luck:

> unnes@ubuntu:~$ ln -s /usr/local/bin/peerguardian.sh /etc/init.d/peerguardian.sh
ln: creating symbolic link `/etc/init.d/peerguardian.sh' to `/usr/local/bin/peerguardian.sh': Permission denied
unnes@ubuntu:~$ sudo chmod -c 755 /usr/local/bin/peerguardian.sh
unnes@ubuntu:~$ ln -s /usr/local/bin/peerguardian.sh /etc/init.d/peerguardian.sh
ln: creating symbolic link `/etc/init.d/peerguardian.sh' to `/usr/local/bin/peerguardian.sh': Permission denied
unnes@ubuntu:~$ sudo chmod -c 755 /etc/init.d/peerguardian.sh
chmod: cannot access `/etc/init.d/peerguardian.sh': No such file or directory


---

### Post by botbotdingzip on 2006-04-28
[QUOTE=Jabbadahut]Hello, I am having trouble installing this program.

I downloaded the program, then ran the following command as described above.


```


jay@jabbadahut:~$ sudo cp peerguardian.sh /usr/local/bin
cp: cannot stat `peerguardian.sh': No such file or directory


```

I'm relatively new to Linux, but I copied & pasted the commands correctly.  However,  as you can see above, I am having trouble creating the 'peerguardian.sh' file.  What did I do wrong?[/QUOTE]

hi Jabba dude, I had the same problem with breezy following the instruction "sudo cp peerguardian.sh /usr/local/bin
cp: cannot stat `peerguardian.sh': No such file or directory" 
This worked fine for me, "kdesu kate" in a terminal, and just use it to create whatever file with whatever extension in whatever location.

---

### Post by botbotdingzip on 2006-04-28
Um, I need some help please.
My PG.log says this:

Reading blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 0 ranges (0 IP addresses)
caught signal, cleaning up and terminating

Effectively means its doing nothing.
I followed the instructions and the daemon is registered as working, any clue?

---

### Post by dpfurniss on 2006-05-13
Please help i am very new to linux (mepis). I have installed peerguardian. Where do i go from here. I know u have put the code here but were do i type it ect sorry to be a pain in the arse but i would love to run linux on my download pc but will not with out peerguardian or some thing off the same.Agian am very new i have tried suse mandriva ferdra core 5 and ubuntu and couldnt even get it to install until i tried mepis.I use peerguardian and azureus with xp but want to run linux as it works well with my old p3. Cheers

---

### Post by ludzter on 2006-05-14
Got it to work in dapper, atleast so it starts, but it dont block anything. the list&#347; are updated. 
PG.log:
```
Reading blocklist
detected ASCII blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 172487 ranges (977439745 IP addresses)
```
pgtext
```

                         PEERGUARDIAN v1.5beta    ******


          Packets Blocked               Packets Checked
              0                             54231


                              Blocked
Reading blocklist
detected ASCII blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 172487 ranges (977439745 IP addresses)


```
My blocklist in peerguardian.sh
```
BLOCKLISTS="level1 level2 spyware ads-trackers-and-bad-pr0n edu spider"
```

Cant understand why it dosnt block someting atleast, when i have peerguardian runing in win its block stuff all the time.

---

### Post by Nutterpc on 2006-05-25
Peerguardian is actually reasonably easy to get running with iptables

If anyone wants a hand, gimme a msg on msn and I'll see what I can do :)

---

### Post by inovermyheadd on 2006-05-30
hey I installed this but how do I know if it works?

---

### Post by inovermyheadd on 2006-05-31
ok I get this:

[PHP]------------ 2006-05-31 05:19:14 PM CDT Begin PeerGuardian start
File level1.gz last updated 2006-05-30 22:38:42.000000000 -0500
--17:19:14--  http://www.bluetack.co.uk/config/level1.gz
           => `level1.gz'
Resolving www.bluetack.co.uk... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.saunalahti.fi/zolord/bluetack/level1.gz [following]
--17:19:14--  http://www.saunalahti.fi/zolord/bluetack/level1.gz
           => `level1.gz'
Resolving www.saunalahti.fi... 62.142.11.7
Connecting to www.saunalahti.fi|62.142.11.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,796,069 (1.7M) [text/plain]
Server file no newer than local file `level1.gz' -- not retrieving.

No blocklists needed updating.
Starting PeerGuardian
------------ 2006-05-31 05:19:16 PM CDT End PeerGuardian Script
[/PHP]

Does that mean it is working?

---

### Post by bionnaki on 2006-05-31
is it safe to delete peerguardian.sh from the home directory?

---

### Post by inovermyheadd on 2006-06-03
I would say yes if you used his code...since you copy the file to another directory

---

### Post by SqRt7744 on 2006-06-12
I have a couple of subtle improvements to this otherwise excellent howto... first of all, it would be nicer to replace the line

```
sudo cp peerguardian.sh /usr/local/bin
``` 
with
 ```
sudo touch /usr/local/bin/peerguardian.sh 
``` 
... this will create the empty file peerguardian.sh in /usr/local/bin and allow that step to be a simple copy and paste rather than leaving it to the person following the instructions to invent their own method of creating the empty peerguardian.sh file, and then also having a redundant copy kicking around on their computer that they later have to remove.

Now, more significantly:
The dowload URL in the script is obsolete. It is luckily still being forwarded to the correct link, but who knows how long that will be the case.  Please replace
```
URL=http://www.bluetack.co.uk/config
``` 
with
```
URL=http://www.saunalahti.fi/zolord/bluetack/
``` 

Finally, if you want Peerguardian to run at startup there is a much easier way than that used by Kokanee, although the result is identical.  Rather than creating all the links one-by-one, the desired results can be achieved with two simple commands:
```

sudo cp /usr/local/bin/peerguardian.sh /etc/init.d/
sudo update-rc.d peerguardian.sh defaults

```

That's my 2cents.  Best of luck, and thanks for the how-to.  Nice script.

---

### Post by smartalecks on 2006-06-13
How do I uninstall PG?

---

### Post by smoove on 2006-08-09
Right please forgive my n00byness, but i've installed .deb package. 
Now I've come to the first command and I get this:

> smoove@smoove-laptop:~$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
dpkg: error processing peerguardnf-1.5beta.i386.deb (-smoove@smoove-laptop:~$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
dpkg: error processing peerguardnf-1.5beta.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb
 -install):
 cannot access archive: No such file or directorysmoovsmoove@smoove-laptop:~$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
dpkg: error processing peerguardnf-1.5beta.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb
e@smoove-laptop:~$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
dpkg: error processing peerguardnf-1.5beta.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb

Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb


Also, where am i supposed to save the peerguardian.sh file? If someone would be kind enough to jump on MSN to help me through it, i would appreciate it. Getting peerguardian to work on Ubuntu is my last thing, before I'm windows free. [email]martincollins01@hotmail.com[/email] Thanks.

---

### Post by bjorkiii on 2006-09-05
As soon as i start peerguardian i lose internet connection e.g i cant browse the web ?

---

### Post by andw on 2006-09-22
> **ace2005 said:**
> I also get this in my log:

Reading blocklist
detected ASCII blocklist
Entering daemon mode
Blocking 87916 ranges (658873113 IP addresses)
error: $

:(

Edit: SOLVED

... 
I'm getting this exact error message (error: $)
It only occurs when I have PG set to autorun at startup.
If I do a restart of PG, it is fine.
It seems to block the IPs regardless of the error message, but the PG.log doesn't update.
If I restart PG manually, it fixes it all and reports ok.

I notice that a couple of people have reported this and then mentioned that they had solved it.
Can anyone tell me what needs to be done to solve it, or are you just manually starting it?

---

### Post by Zone17 on 2006-10-14
I am a newbie and I am trying to get this to work but I can not seem to find the log file to see if it is working, I searched the entire file system for pg.log and nothing. Any suggestions?

zone@zone-laptop:~$ cd Apps
zone@zone-laptop:~/Apps$ sudo dpkg -i peerguardnf-1.5beta.i386.deb
Selecting previously deselected package peerguardnf.
(Reading database ... 97483 files and directories currently installed.)
Unpacking peerguardnf (from peerguardnf-1.5beta.i386.deb) ...
Setting up peerguardnf (1.5) ...
zone@zone-laptop:~/Apps$ sudo mkdir /etc/peerguardian
zone@zone-laptop:~/Apps$ sudo cp peerguardian.sh /usr/local/bin
zone@zone-laptop:~/Apps$ sudo cp peerguardian.sh /usr/local/bin
zone@zone-laptop:~/Apps$ sudo chmod -c 755 /usr/local/bin/peerguardian.sh
mode of `/usr/local/bin/peerguardian.sh' changed to 0755 (rwxr-xr-x)
zone@zone-laptop:~/Apps$ sudo gedit peerguardian.sh
zone@zone-laptop:~/Apps$ sudo peerguardian.sh start

---

### Post by mighty_falcon on 2006-11-08
is there any way to exclude a range of ips?? any sort of white list?

tnx

---

### Post by TattooedFish on 2006-12-01
I've been looking for PeerGuardian or something like that for Linux, and I found this guide, and it's all working fine. No error messages at all.
SO many thanks goes to everyone who contributed to this topic.

Only thing, as I'm not downloading stuff all the time, I didn't set it up to start on start-up; there's no need for that unless you're on piracy 24/7...

---

### Post by russryder on 2006-12-24
Thanks for the howto, I just got a message from my ISP with a complaint from Columbia Pictures about sharing a file.  Hopefully this will thwart their efforts towards any more evidence gathering.

Russ

Zone17,

The log file is here - /var/log/PG.log

You can watch the file in real time by using the following command
#sudo tail -f /var/log/PG.log

---

### Post by moore.bryan on 2006-12-27
*quick question... i've used peerguardian for a while now and never had this problem: port 995 is forced closed every startup, even though i have an iptables rule to allow it... but, i can reset the rule by deleting and re-adding it at startup.  any ideas?*

---

### Post by Jazkal on 2007-01-03
Can anyone point me in the right direction?

My home system is in a blocked range (in level1). And my remote box running pg won't allow me to access the system.

I would like to be able to use the peerguardian.sh script to parse out my blocked range and modify the level1.txt list for the adjusted (read: minus my IP range) block lists.

---

### Post by ntetreau on 2007-01-16
For some reason, I could download the level1.gz list from bluetack anymore, keep getting a 403 error.  Replacing the [www.bluetack.co.uk/config/](www.bluetack.co.uk/config/) URL in the peerguardian.sh script by dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/ seems to fix the problem.

Nic

---

### Post by sloter on 2007-02-25
Hi,

I've just installed the package _peerguardnf-1.5-cvs20060228-14.deb_ from the repository [http://moblock-deb.sourceforge.net/debian unstable main](http://moblock-deb.sourceforge.net/debian unstable main).
# sudo apt-get install peerguardnf

Thus i got a script in /etc/init.d/peerguardnf
4 configuration files in /etc/peerguardn/PG.conf, blocklists.list, p2p.p2b.p2p and .bak
and 2 log files in /var/log/peerguardnf/ deamon and script

Problem when i do a manual stop or restart i got the followin message
# sudo peerguardnf stop
password:
Reading blocklist
Failed to read blocklist
# sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
PEERGUARD_IN  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
PEERGUARD_FW  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
PEERGUARD_OUT  all  --  anywhere             anywhere            

Chain PEERGUARD_FW (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
QUEUE      all  --  anywhere             anywhere            state NEW 

Chain PEERGUARD_IN (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
QUEUE      all  --  anywhere             anywhere            state NEW 

Chain PEERGUARD_OUT (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
QUEUE      all  --  anywhere             anywhere            state NEW 


How can i properly shutdown or restart the pg deamon ?

The machine is running the edjy eft with kernel 2.6.17-11-386.

Thanks

---

### Post by sloter on 2007-02-27
_o/ Hello forum,

I am still investigating, I looked at the source of the peerguardnf-1.5cvs deb package but without any good conclusion.

May be my stop/restart problem is directly linked with the Deleting iptables [fail] issue.

look at the log file
foo@bar $ tail -f /var/log/peerguardnf/peerguardnf.script.log
 * peerguardnf was already running, not inserting iptables rules
2007-02-27 08:23:24 PST End: /etc/init.d/peerguardnf update
2007-02-27 09:09:23 PST Begin: /etc/rc0.d/K20peerguardnf stop
 * -n Stopping PeerGuardian...                                           [ ok ] 
 * Deleting iptables...                                                  [fail] 
2007-02-27 09:09:23 PST End: /etc/rc0.d/K20peerguardnf stop
2007-02-27 18:13:11 PST Begin: /etc/rc2.d/S20peerguardnf start
 * Starting PeerGuardian...                                              [ ok ] 
 * Inserting iptables...                                                 [ ok ] 
2007-02-27 18:13:12 PST End: /etc/rc2.d/S20peerguardnf start

any one has any ideas would be great!

---

### Post by jre on 2007-03-04
> **ntetreau said:**
> For some reason, I could download the level1.gz list from bluetack anymore, keep getting a 403 error.  Replacing the [www.bluetack.co.uk/config/](www.bluetack.co.uk/config/) URL in the peerguardian.sh script by dialspace.dial.pipex.com/town/pipexdsl/s/ashu56/bluetack/ seems to fix the problem.

Nic

Because of bandwidth problems of bluetack the level1-list is provided over the CORAL Cache system: [http://www.bluetack.co.uk/forums/index.php?showtopic=16352&st=0](http://www.bluetack.co.uk/forums/index.php?showtopic=16352&st=0)
If you get a 403, also there the bandwidth has reached its daily (?) quota or you are temporarilly blacklisted because you tried to download lists to often. Just try it once a day!
Please only use the [www.bluetack.co.uk/config/](www.bluetack.co.uk/config/) links, so that bluetack has more control over their bandwidth.
Greets
jre

---

### Post by dbqp on 2007-03-14
> As soon as i start peerguardian i lose internet connection e.g i cant browse the web ?


This was mentioned earlier in the thread...page 8, but no one ever responded to it. I am now having this problem with losing internet connection in general as well as my web hosting providers IP address (for their mail server) is listed in the block file (p2p.p2p.p2p). Now Thunderbird will not connect and I cannot access my mail through a client. I am abe to log into the webmail interface via FireFox.

First can someone explain how my internet connection is being killed and any suggested fixes? And how do I edit the block list to allow me to access my mail through Thunderbird. The IP being blocked is within a range of IP's listed on one line. I know I can just edit this line, but I don't know which file to edit as when I try to sudo gedit p2p.p2p.p2p, it just hangs at the terminal screen - so I don't think this file is the one I am after...

I have tried searching in a lot of places, but can't seem to locate the exact details on how to do this...hmmm.

Any Help!!???!!!

Thank you.

---

### Post by dbqp on 2007-03-14
> **dbqp said:**
> This was mentioned earlier in the thread...page 8, but no one ever responded to it. I am now having this problem with losing internet connection in general as well as my web hosting providers IP address (for their mail server) is listed in the block file (p2p.p2p.p2p). Now Thunderbird will not connect and I cannot access my mail through a client. I am abe to log into the webmail interface via FireFox.

First can someone explain how my internet connection is being killed and any suggested fixes? And how do I edit the block list to allow me to access my mail through Thunderbird. The IP being blocked is within a range of IP's listed on one line. I know I can just edit this line, but I don't know which file to edit as when I try to sudo gedit p2p.p2p.p2p, it just hangs at the terminal screen - so I don't think this file is the one I am after...

I have tried searching in a lot of places, but can't seem to locate the exact details on how to do this...hmmm.

Any Help!!???!!!

Thank you.

I found additional instructions on the pheonixlabs forum stating that I would whitelist by editing /etc/default/peerguardnf  - Is this correct? Currently at work and not at my PC, but wanted to throw this out there so I can run home and try it if this is correct. And if so, will this file give the complete list as shown in the p2p.p2p.p2p file?

---

### Post by dbqp on 2007-03-14
As no responses are coming in, I have been looking around further and want to see if anyone can confirm that this is not being maintained anymore and I should switch to moblock?

Please, anyone?

---

### Post by jre on 2007-03-14
> **sloter said:**
> Hi,

I've just installed the package _peerguardnf-1.5-cvs20060228-14.deb_ from the repository [http://moblock-deb.sourceforge.net/debian unstable main](http://moblock-deb.sourceforge.net/debian unstable main).
# sudo apt-get install peerguardnf

Thus i got a script in /etc/init.d/peerguardnf
4 configuration files in /etc/peerguardn/PG.conf, blocklists.list, p2p.p2b.p2p and .bak
and 2 log files in /var/log/peerguardnf/ deamon and script

Problem when i do a manual stop or restart i got the followin message
# sudo peerguardnf stop
password:
Reading blocklist
Failed to read blocklist
[...]
How can i properly shutdown or restart the pg deamon ?
sudo /etc/init.d/peerguardnf stop

This calls the init-script which itself tells the peerguardnf-daemon what to do. What you typed was going directly to the daemon (who didn´t understand what you typed)

---

### Post by sloter on 2007-03-14
Hello dbqp,


May be take a look at your PG.conf file normaly it is well commented and easily understandable.
standard SMTP port is 25
standard POP3 port is 110
standard HTTP port is 80

Thank you,

#
# PGD.conf -- This is a basic PGD configuration file.
# To really apply changes reload proftpd after modifications.
#  

# Modify the block file below to match the block file you use
BLOCKFILE=/etc/p2p.p2b.p2p

# Please edit below if you wish not to block certain ports with 
# were in the format 80,25,x,x; or leave it blank if you don't wish
# to use this feature. 
PORTS_NOT_TO_BLOCK=80;

ADMIN_NAME=admin
ADMIN_PASSWORD=d033e22ae348aeb5660fc2140aec35850c4da997

---

### Post by jre on 2007-03-14
> **dbqp said:**
> As no responses are coming in, I have been looking around further and want to see if anyone can confirm that this is not being maintained anymore and I should switch to moblock?

Please, anyone?

The peerguardnf code is not developed anymore since 2005. I wrote the init-script in the first post of this thread and developed it further resulting in the version which is included in the moblock-deb.sourceforge.net peerguardnf...deb. I stopped this last december since I switched to moblock.

The moblock code has an active developer. The script included in the moblock-deb.sourceforge.net moblock...deb is based on an early version of the script I wrote. I had no time yet to improve this script and will not do this for the next future.

The maintainer of moblock-deb.sourceforge.net is not active at the moment.

I can give you some support here from time to time but I prefer forums.phoenixlabs.org. Note that I don´t use Ubuntu but Debian Etch.

jre

---

### Post by jre on 2007-03-14
> **dbqp said:**
> I found additional instructions on the pheonixlabs forum stating that I would whitelist by editing /etc/default/peerguardnf  - Is this correct? Currently at work and not at my PC, but wanted to throw this out there so I can run home and try it if this is correct. And if so, will this file give the complete list as shown in the p2p.p2p.p2p file?


As sloter just wrote you can use PG.conf to whitelist the needed ports.
Alternatively you can have a look at /etc/default/peerguardnf for whitelisting ports and/or IPs and for removing lines from the blocklist p2p.p2p.p2p. (Yes, peerguardnf reads the blocklist from  p2p.p2b.p2p, in the past this list was in /etc/p2p.p2b.p2p but I changed this to /etc/peerguardnf/p2p.p2b.p2p at some time).

---

### Post by dbqp on 2007-03-14
Thank you both jre and sloter. Much appreciated.

Considering that neither is currently maintained, how would I go about completely removing peerguardnf? I try stopping it and it still won't allow me to connect to the particular IP or access the internet. I would rather just remove it completely.

With that being said, is there another privacy protectin program available for Linux?

Thanks again!

---

### Post by jre on 2007-03-15
> **dbqp said:**
> Considering that neither is currently maintained, how would I go about completely removing peerguardnf? I try stopping it and it still won't allow me to connect to the particular IP or access the internet. I would rather just remove it completely.
1. Do you use any additional firewalls or iptable rules? They might cause problems.
2. If you use a SMP-kernel you will have problems with peerguardnf. Move to moblock in this case.
3. With all iptables rules removed peerguardnf has no influence (so neither causing problems nor filtering IPs.) On the other hand if peerguardnf is stopped but the iptables-rules are not removed completely then you will have trouble.

If you want me to help you then tell me which version you installed (and where from you got it) and post the ´iptables -L´ output after starting and after stopping peerguardnf.
If your problems are ubuntu-related I won´t be able to help you.

> With that being said, is there another privacy protectin program available for Linux?
Moblock is not not maintained, just not very actively ;-)
I don´t know about other similar problems (except linblock which is AFAIK not a real alternative for the desktop).

greets
jre

---

### Post by dbqp on 2007-03-15
Jre, your replies cannot be appreciated enough.  As I go through these different forum regarding peerguardnf, I see your name everywhere when assistance is requested on this program.

Late last night I was able to remove pg through the package manager and I am now able to connect to my mail server and the internet again.

I didn't do what I always tell others: "Don't 'test' programs on your production or main system" I have another desktop that I usually do these things on and it just underlined why I usually take this approach. So, I will test moblock using my test machine and see how it goes! If I have trouble, I'll post over at pheonixlabs as per your request, but moblock has some great step by step tutorials to get me going.

Thank you again and I wish you nothing but great rewards for all your help in the open source community.

keep rockin'
:guitar:

---

### Post by sloter on 2007-03-16
Jre,

i understood my mistake, thanks!
the daemon is stopping [ok]...but...
```
foo@bar $ sudo /etc/init.d/peerguardnf start
 * Starting PeerGuardian, but not updating the blocklists peerguardnf    [ ok ] 
foo@bar $ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

I assume the PEERGUARD rules should be present here, don't they?

Thank you,

---

### Post by jre on 2007-03-16
> **sloter said:**
> 
I assume the PEERGUARD rules should be present here, don't they?


Yes, they should.

Check your TABLES settings in /etc/default/peerguardnf, as default TABLES="6" should be correct. ```
. /etc/default/peerguardnf
echo $TABLES
```--> Output should be "6". (Note the dot followed by a space in the first line!)

If possible reboot your system because iptables-rules are only inserted if peerguardnf wasn´t running before. After reboot check your iptables settings (everything should have been done automatically) before you do any manual starting/stopping. (If you can´t reboot then make sure that there is no /var/run/peerguardnf.pid and no running peerguardnf process.)

If this works but you experience problems later, something with restarting peerguardnf after the daily blocklist-update might cause problems.

Do you use any additional firewalls? E.g. firehol purges all other iptables-rules.

Please post your results.

@dbqp: Thanks for the warming words :-) Next to nice users my thanks go to the developers and all people doing work without being present on the forums.

greets
jre

---

### Post by sloter on 2007-03-16
ok,

i do not use ant additional firewall on the machine, just run the ubuntu edjy eft.
i've booted the system and checked the TABLES variable...it is good. the peerguardnf deamon is running [ok] since it is set up in the /etc/init.d/ folder.

what did i do when {dot and space and script /etc/default/peerguardnf}? 

```
foo@bar $ . /etc/default/peerguardnf
foo@bar $ echo "$TABLES"
6
foo@bar $ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
PEERGUARD_IN  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
PEERGUARD_FW  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
PEERGUARD_OUT  all  --  anywhere             anywhere            

Chain PEERGUARD_FW (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
QUEUE      all  --  anywhere             anywhere            state NEW 

Chain PEERGUARD_IN (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
QUEUE      all  --  anywhere             anywhere            state NEW 

Chain PEERGUARD_OUT (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
QUEUE      all  --  anywhere             anywhere            state NEW 

```

> If possible reboot your system because iptables-rules are only inserted if peerguardnf wasn´t running before. 

I need to be able to stop and start/restart the peerguardnf deamon without rebooting the system. why could it be a problem?

> If this works but you experience problems later, something with restarting peerguardnf after the daily blocklist-update might cause problems.

Can you detail your idea?

I plan to add my own iptable rules to use it like firewall. I've read you said in this post that using other iptables rules may lead to a problem with peerguardnf. I plan to filter the traffic both for in, out and forward before queing it in the PEERGUARD chains. Where is the problem you were talking about?

---

### Post by jre on 2007-03-17
> **sloter said:**
> what did i do when {dot and space and script /etc/default/peerguardnf}?
You loaded the variables that are set in /etc/default/peerguardnf to your current bash-session. That was just a way to control if the variable TABLES is set correctly.
Normally this variable is loaded by the init-script to determine what variant of iptables-insertion shall be done.

> foo@bar $ sudo iptables -L
[...]
So now everything is working!?

> I need to be able to stop and start/restart the peerguardnf deamon without rebooting the system. why could it be a problem?
To start peerguardian two things have to be done: starting the daemon peerguardnf and insertion of the iptables-rules (peerguardnf filters all traffic that is directed to QUEUE).
But `/etc/init.d/peerguardnf start´ does start the daemon only if it wasn´t already running to avoid several daemons running at the same time. Furthermore the iptables-rules are only inserted if the daemon wasn´t already running to avoid having the same iptables rules several times. (I would prefer a direct test for the existence of the iptables rules but I don´t know a way to do this, so I chose this workaround).
I told you to reboot to make sure that everything starts from a clear system (no running peerguardnf-process, no PID-file and no iptables-rules inserted). One bad scenario might be the peerguardnf-process is already running but the iptables-rules are not present (either because something didn´t work as I want, e.g. your Ubuntu system doesn´t behave as I know it from my Debian system; or because you started the peerguardnf-process directly but not over the script; or ...)
You get my point? "running peerguardnf-process" and/or "PID-file present" --> "no iptables-rules insertion"
If everything is working as it is supposed to be there is of course no need to reboot or not to start/stop/restart peerguardian.

lol, I just saw that I already wrote something about this topic in the man-page (man peerguardnf) under the section BUGS - highly recommended to read this!

You can always check if the process/daemon is running:
```
ps aux | grep peerguardnf
```
if the PID-file is there:
```
ls -l /var/run/peerguardnf.pid
```
if the iptables-rules are present:
```
sudo iptables -L
```
if blocking is working:
```
tail -f /var/log/peerguardnf/peerguardnf.daemon.log
```

> Can you detail your idea?
E.g. process killed, iptables-rules removed, PID-file not removed --> problems
If you experience problems then remove all " > /dev/null 2>&1" in /etc/init.d/peerguardnf. This will give you a more detailed peerguardnf.script.log.

> I plan to add my own iptable rules to use it like firewall. I've read you said in this post that using other iptables rules may lead to a problem with peerguardnf. I plan to filter the traffic both for in, out and forward before queing it in the PEERGUARD chains. Where is the problem you were talking about?
Just set TABLES="5" (don´t forget to comment out #TABLES="6") in /etc/default/peerguardnf and insert your iptables-rules as you want. But remember: when you stop the process you also have to change QUEUE to ACCEPT, otherwise your traffic will be stuck in QUEUE.
Iptables-rules are processed from top to bottom. Packets which are accepted by peerguardian might (There exist problems but I´m no pro in this topic) leave this process and just be accepted although there might be later another rule which would block this packet. So as long as QUEUE is the last rule there will be no problems. Also the isolation of the QUEUE in it´s extra chain already seems to have solved most problems which occured in the past.
So just try it and check if everything is working as you want it to.

Puh, long post, I hope you understood what I wanted to say ;-)
greets
jre

---

### Post by Xvani on 2007-03-18
How do I unistall it? I want no trace of this program on my computer :)

---

### Post by sloter on 2007-03-19
Hello,

Jre thanks for your long rich post I need time to take it into account but after the first read I understood all what you said. ;)

Xvani, I assume u r running under debian or ubuntu and you installed the .deb package.
Use apt-get remove --purge <package>.deb to remove the application and its dependencies and delete the configuration files.
As a backup solution use dpkg --purge <package>.deb but prefer the first solution.

Replace <package> by the name of your peerguardian package.

Have a look to the man page of apt-get or/and dpkg, or maybe search on the internet.


Thank you!

---

### Post by jre on 2007-04-05
[ATM bluetack´s level1.gz list is distributed via the Coblitz system.]("http://www.bluetack.co.uk/forums/index.php?showtopic=16352&view=findpost&p=80423") (At least here) the IPs of the Coblitz server is in the level2 list. Therefore automatic updates for the level1.gz don´t work here. (This is the same problem as with the Coral system being blocked on the edu-list).
Don´t worry, the other lists update just fine and PeerGuardian continues to use the old level1-list (as long as it has been downloaded and saved to /var/spool/peerguardnf/ in the past).
Everybody feel free to donate money to bluetack.co.uk so that they can afford to distribute their level1 list with their own server again ;-)

---

### Post by chinaski on 2007-04-08
I have a problem

it's several days Peerguardian is not updating P2P block list anymore

that's what I get

> acp@central:~$ sudo peerguardian.sh start
------------ 2007-04-09 02:27:09 AM CEST Begin PeerGuardian start
File level1.gz last updated 2007-03-30 13:39:52.000000000 +0200
--02:27:09--  [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)
           => `level1.gz'
Resolving [www.bluetack.co.uk]("http://www.bluetack.co.uk")... 67.18.178.4
Connecting to www.bluetack.co.uk|67.18.178.4|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.btack.info/level1.gz](http://www.btack.info/level1.gz) [following]
--02:27:09--  [http://www.btack.info/level1.gz](http://www.btack.info/level1.gz)
           => `level1.gz'
Resolving [www.btack.info]("http://www.btack.info")... 82.165.138.54
Connecting to www.btack.info|82.165.138.54|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://coblitz.codeen.org:3125/min.midco.net/jinx/bluetack/level1.gz](http://coblitz.codeen.org:3125/min.midco.net/jinx/bluetack/level1.gz) [following]
--02:27:10--  [http://coblitz.codeen.org:3125/min.midco.net/jinx/bluetack/level1.gz](http://coblitz.codeen.org:3125/min.midco.net/jinx/bluetack/level1.gz)
           => `level1.gz'
Resolving coblitz.codeen.org... 131.175.17.9, 131.175.17.10
Connecting to coblitz.codeen.org|131.175.17.9|:3125... connected.
HTTP request sent, awaiting response... 400 Bad Request
02:27:10 ERROR 400: Bad Request.

No blocklists needed updating.
Starting PeerGuardian
------------ 2007-04-09 02:27:11 AM CEST End PeerGuardian Script
acp@central:~$ 


---

### Post by Scruffynerf on 2007-04-10
Just installed this following the scripts/howto on the first page.

Just popped in to say that Firestarter and Peerguardian seem to be working well together, and that everythign seems good.

Many thanks for the howto and providing the bandwidth to maintain packages.

cheers

Rob

---

### Post by Scruffynerf on 2007-04-10
As an aside, Azureus now has an optional plugin called SafePeer, which uses the p2p list from Peerguardian.

It also installed without a hitch for me.

(Azureus -> Plugins -> Installation Wizard -> Safepeer)

cheers

Scruffy

---

### Post by jre on 2007-04-11
@chinaski. I also get the Error 400. I think it´s related to Coblitz but I haven´t found anything yet why this could happen. But when I manually do a ```
wget http://www.bluetack.co.uk/config/level1.gz
``` it works.
So just copy that file to /var/spool/peerguardnf

---

### Post by chinaski on 2007-04-14
thanks a lot jre ;)

just one thing: I do not have peerguardnf directory in /var/spool so I created one and copied level1.gz into it

is it correct?

cheers

EDIT: nevermind, as I've just [installed Moblock]("http://ubuntuforums.org/showthread.php?t=192559&highlight=peerguardian")

---

### Post by jre on 2007-04-16
> **chinaski said:**
> just one thing: I do not have peerguardnf directory in /var/spool so I created one and copied level1.gz into it
Just for future reference (I know you´re using moblock now): I thought you had installed the debian package from moblock-deb.sourceforge.net. If you haven´t done this creating the directory will have no use.

---

### Post by chinaski on 2007-04-16
> **jre said:**
> Just for future reference (I know you´re using moblock now): I thought you had installed the debian package from moblock-deb.sourceforge.net. If you haven´t done this creating the directory will have no use.
I followed [this]("http://ubuntuforums.org/showthread.php?t=95793&highlight=peerguardian") tutorial but only the first part (no automatic start of PG and no automatic updates, as I use rarely P2P) but today I removed Moblock - which is surely great but too complicated for me to whitelist things - and put PG back with autostart and autoupdates and the directory /var/spool/peerguardnf was there (I previously removed the one I've created before) so I just wget the updates and copy them in there as you suggested and it is working (I know because the IP range blocked is increased from before) ;)

thanks again jre

---

### Post by Yaffle on 2007-05-09
Can peer guardian be installed on amd 64 systems?

---

### Post by jre on 2007-05-10
> **Yaffle said:**
> Can peer guardian be installed on amd 64 systems?

If you want to use the precompiled debian packages from [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/): I doubt that it will work, but you would have to try.
But on the same site there´s something for moblock (the nearly official PeerGuardian Linux) from [jamesford]("http://ubuntuforums.org/member.php?u=27791"). However this only works under Edgy, not Feisty. If you are under Feisty have a look at [this post]("http://ubuntuforums.org/showthread.php?p=2531418#post2531418").

Since there have been problems with peerguardnf and SMP-Kernels I´d suggest to try moblock anyway. (These matters are not really related but moblock is newer and actively developed.)

Just do a forum/google search.
Greets
jre

---

### Post by narehart on 2007-07-11
thanx a mil. my ISP was watching me...

---

### Post by dangling participle on 2007-07-23
Hey everyone,

thanks for the info, I am getting the following error when attempting to start peerguardian for the first time:

```
peerguardnf: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
```

I have verified that the file does exist on my machine by running the following:

```
#locate libncurses.so.5
/lib/libncurses.so.5.5
/lib/libncurses.so.5

```

and by going into synaptic package manager and verifying that libncurses is installed.

any idea why peerguardian isn't able to see this file?  how do i check the library path in ubuntu?

thanks!

---

### Post by clessing on 2007-07-25
I just wanted to announce that for me it feels very unlikely to be able to maintain the moblock debian package in the upcoming future. I've promised cross-compiling for other platforms and script improvements for quite some time now but due to lack of time I'm often even unable to integrate patches that users have sent in.

If you feel like beeing able to handle subversion and the debian packaging tools, please feel free to contact me via the email on [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/) .

I will hand over the sourceforge account for the project and will assist with initial problems.

I'm sorry for this, but at the moment that's reality - other things in life have higher priority.

clessing

---

### Post by rubikfreak on 2007-09-16
I found myself following this procedure often on new installs and wrote a quick bash script to install it.
The peerguardian package is included, so this is the only download you need to make.
It took a couple of minutes to write the script, but most of the work is the doing of Kokanee that started the thread. Thank you!
[MediaFire Download]("http://www.mediafire.com/?2mrqjyten99")
[RapidShare Download]("http://rapidshare.com/files/57116864/peerguardian.tar.gz.html")

---

### Post by jre on 2007-09-26
Hi all
I'm the new maintainer of moblock-deb.sourceforge.net. As you may have noted the peerguardnf packages aren't there any more (clessing already removed them). peerguardnf is no more developed (since 2 years). The scripts (in the debian package but also the one in this thread) aren't maintained any more since nearly one year (most parts were from me, but I have to credit many other people).

Of course everybody is free to use peerguardnf. But be warned that there exists a bug with SMP kernels and possibly another one that i can't remember.

rubikfreak, nice done. But I suggest to use moblock instead (maintained, less bugs, more features, easier to configure & install). See [moblock-deb.sourceforge.net]("http://moblock-deb.sourceforge.net") (there are special versions for Feisty and Gutsy), the [forums at phoenixlabs]("http://forums.phoenixlabs.org/forumdisplay.php?f=15") (home of peerguardian) and the [moblock thread here at the ubuntu forum]("http://ubuntuforums.org/showthread.php?t=192559")

greets
jre

---

### Post by sefs on 2007-09-27
Can you tell me if moblok workes well with firestarte/iptables.  I need something to work with frostwire as it does not support an ipfilter importer like deluge which is retarded to say the least.

---

### Post by jre on 2007-09-28
> **sefs said:**
> Can you tell me if moblok workes well with firestarte/iptables.  I need something to work with frostwire as it does not support an ipfilter importer like deluge which is retarded to say the least.

Current moblock (0.8) [EDIT: stupid smiley theme; this is a "zero point eight" - not a smiley] only works with firehol. All other firewalls are reported not to work in combination with moblock.

The next moblock version (have a look at the CVS repository at [http://moblock.berlios.de](http://moblock.berlios.de)) will have this feature. [note: I'm NOT the moblock developer. I don't know any release date.)

iplist can do this already: [http://iplist.sourceforge.net/](http://iplist.sourceforge.net/)

I don't know frostwire or deluge.

greets
jre

---

### Post by Fungal Fractoids on 2007-12-10
This might be a really dumb question... But I downloaded the deb to my desktop (that's just where firefox sent it by default) but when I enter that dpkg -i  command into terminal it tells me that no such directory exists. As far as I can tell the command doesn't specify where to look for the dpkg, so does it even matter where it is?

```
error processing peerguardnf-1.5beta.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb

```

---

### Post by jre on 2007-12-11
> **Fungal Fractoids said:**
> This might be a really dumb question... But I downloaded the deb to my desktop (that's just where firefox sent it by default) but when I enter that dpkg -i  command into terminal it tells me that no such directory exists. As far as I can tell the command doesn't specify where to look for the dpkg, so does it even matter where it is?

```
error processing peerguardnf-1.5beta.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 peerguardnf-1.5beta.i386.deb

```

Did you read the last comments in this thread? Do you really want to use a program that is dead since 2 years and has some flaws?
I suggest you have a look at moblock ([http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559))

To your question: try **as root** ```
dpkg - i /home/USERNAME/Desktop/peerguardnf-1.5beta.i386.deb
```

---

### Post by Krusader3z on 2007-12-15
I get this error. Anyone know what I haven't done correctly?

Reading blocklist
detected ASCII blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 188776 ranges (744699856 IP addresses)
**ipq_set_mode failed; is the ip_queue kernel module loaded?**

---

### Post by jre on 2007-12-15
> **Krusader3z said:**
> I get this error. Anyone know what I haven't done correctly?

Reading blocklist
detected ASCII blocklist
Entering daemon mode
Allowing all traffic on port 80
Blocking 188776 ranges (744699856 IP addresses)
**ipq_set_mode failed; is the ip_queue kernel module loaded?**

Using a kernel without ip_queue?
Use moblock (nfq) instead

---

### Post by wieszczus on 2008-03-21
Thank You. Next step away from windows.

---

### Post by StormGuy on 2008-03-29
I apologize in advance.  I'm terribly new to this sort of thing. 

I installed Peerguardian using the walkthrough on the first page, and the installation went fine, but anytime I try to run Peerguardian, it shuts off my internet access completely.  I can't visit websites or use Gaim.  I assume it's blocking something that it shouldn't be blocking, but I'm not sure what that is or how to change it.

I've tried some of the recommended solutions.  I edited my PG file, but it already had port 80 listed as something it shouldn't be blocking.

---

### Post by spikeez on 2008-04-26
That worked great. Thanks!

---

### Post by jre on 2008-05-06
Once again: peerguardnf is dead. No support, no development, no developers.
Use MoBlock or IPList instead. Both have many threads in this forum, moblock has also a wiki page. And they both have Debian packages.

---

### Post by souljahh2050 on 2008-08-20
> **ace2005 said:**
> Well the filtering system could be messing with the SSL stuff on port 443 so i just guessed that if you allowed all connections regardless of source on that port only then it might work.

So what does a sygate scan on you're system show?

How do I go about opening port 443?

---

### Post by jre on 2008-08-21
> **souljahh2050 said:**
> How do I go about opening port 443?

Read the post before yours: you are using absolutely dead software.

Go to moblock-deb.spourceforge.net and install MoBlock or go to iplist.sourceforge.net and install IPBlock. They both do the same as peerguardnf.

EDIT: I have just requested to remove this obsolete HOWTO, see here: [http://ubuntuforums.org/showthread.php?t=896667](http://ubuntuforums.org/showthread.php?t=896667)

---

### Post by souljahh2050 on 2008-08-21
> **jre said:**
> Read the post before yours: you are using absolutely dead software.

I understand that you are saying that it is dead, but I still want to enable port 443 on this program because of my ssl problem. Is there anyone out there who knows how to do this? I am still fairly new to linux.

Thx,

---

### Post by souljahh2050 on 2008-08-21
> **souljahh2050 said:**
> How do I go about opening port 443?

I just figured it out, you have to edit /etc/PG.conf.

---

### Post by jre on 2008-08-22
Good that you figured it out on your own.
Still I'd suggest that you **change to other software with the exact same functionality such as MoBlock or IPBlock**.
The peerguradnf program that you are using has at least a bug with SMP kernels, that is why I suggest to stop using that program.

EDIT:
If you have installed peerguardnf (in spite off all warnings not to use this outdated software) and decide later to install other software such as MoBlock or IPList, then make sure to remove peerguardnf completely first.
Otherwise other software that uses the iptables target NFQUEUE (and all software with this purpose does so) will not be able to bind to the QUEUE.
Short version: **Uninstall peerguardnf completely before installing MoBlock or IPList.**

This command will scan your entire harddisk (so it will take a while) for remaining PeerGuardian files:```
sudo find / -name "*[Pp]eer[Gg]uard*"
```

The error message for MoBlock in /var/log/moblock.log that you would encounter otherwise is:
```
Error during nfq_bind_pf()
```

---

### Post by TESFox on 2009-03-16
Thanks for the guide!  Got everything working flawlessly, however for some reason /etc/p2p.p2b.p2p was blank, so I had to copy p2p.p2b.p2p.backup over it to make PG work properly.  I'll keep an eye on it and see what happens when an update comes around.

---

### Post by jre on 2009-03-16
Come on, please read my last several posts. This is an outdated tutorial (see the section), for outdated software.

[SIZE="6"]**Someone please close this thread!**[/SIZE]

---

### Post by Kd40 on 2009-08-21
ok tried
```
sudo cp peerguardian.sh /usr/local/bin
```

and i come up with the message ```
kd40@tango-laptop:~$ sudo cp peerguardian.sh /usr/local/bin
[sudo] password for kd40: 
cp: cannot stat `peerguardian.sh': No such file or directory

```doesnt seem to work? what should i do?

---

### Post by Arch Parsons on 2009-09-13
I followed the guide for installing peerguardian but when it starts I get this line:  Server file no newer than local file `level1.gz' -- not retrieving. Does this mean PG is not working?  I cannot see any evidence (tray icon, etc.) of a program running.

---

