---
title: "HowTo: Install and Use Beagle Easily"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2005-10-19
Beagle baffled me the first time I tried to use it. [This Ubuntu Forums thread](http://ubuntuforums.org/showthread.php?t=31518) recommended [the Beagle wiki](http://beaglewiki.org/index.php/UbuntuInstall) for tips on how to get it working. I found the wiki complicated and misleading (I followed their instructions exactly and just got some weird error, and I couldn't get my Beagle daemon running). Apparently [I'm not the only one](http://www.ubuntuforums.org/printthread.php?t=46622).

Installing, setting up, and using Beagle is a lot easier than the Beagle wiki would have you believe. First, [make sure you have the Universe repositories enabled](http://www.psychocats.net/sources.html). Then ```
sudo apt-get install beagle
```.

(This is what the wiki has wrong), instead of doing this at the command prompt, type this in the Run dialogue (the keyboard shortcut for the Run dialogue is generally *alt-F2*): ```
beagled
```

Then, open a new Run dialogue and type in ```
beagle-settings
```. A GUI will pop up with the settings. Set it how you want (which directories you want it to index).

Finally, open a terminal and type ```
beagle-info --status
``` to see that it's indexing things correctly.

When you want to use Beagle, click on Applications > Accessories > Beagle Search. Otherwise, if you want to *alt-F2* the command, it's ```
best --no-tray
```

When I run that command, I get a search box. [Here's me using the search box to find the word *grammar*](http://i22.photobucket.com/albums/b337/psychocats/37a73a7f.png)

That's Beagle.

---

### Post by ubuntu_demon on 2005-10-19
indexing your data goes faster when you type this before starting beagled (without the $) :

```

$ export BEAGLE_EXERCISE_THE_DOG=1

```

from :
[http://www.beaglewiki.org/Indexing_Data](http://www.beaglewiki.org/Indexing_Data)

Also make sure extended attributes are enabled in your /etc/fstab
see : [http://www.beaglewiki.org/Enabling_Extended_Attributes](http://www.beaglewiki.org/Enabling_Extended_Attributes)

---

### Post by HanZo on 2005-10-19
unfortunately enabling extended attibutes created big troubles... system would not start and I had to use system rescue disk to restore old fstab again... can it be that the beagle wiki is somehow misleading on this part. I use a ext3 fs, and Breezy, I have one big partition with everything in it (system and home) what exactly do I have to write in the fstab?
note: beagle seems to work fine for evolution, tomboy but It does not find any file on my hd... looks like I need those extended attributes...

---

### Post by ubuntu_demon on 2005-10-19
[QUOTE=HanZo]unfortunately enabling extended attibutes created big troubles... system would not start and I had to use system rescue disk to restore old fstab again... can it be that the beagle wiki is somehow misleading on this part. I use a ext3 fs, and Breezy, I have one big partition with everything in it (system and home) what exactly do I have to write in the fstab?
note: beagle seems to work fine for evolution, tomboy but It does not find any file on my hd... looks like I need those extended attributes...[/QUOTE]
I don't know about that problem. But it is recommended to have a seperate /home partition and to enable the extended attributes for that partition. Also without extended attributes beagle is crippled.

---

### Post by nehalem on 2005-10-19
I was so excited for breezy+beagle but I must say that the 100mb+ RAM consumption is way too steep.  I wonder if this will be getting better in future versions...

---

### Post by arunsub on 2005-10-19
I think beagle is well integrated in breezy. I could make beagle search my Windows partition also. What i did was, i went to Application - accessories - files or folder and index option (not sure of the name since i'm not near Ubuntu system) and added my windows partition to folders to be indexed. I then added beagled to my session startup. It works like a charm. Now I can search both my home folder and windows partition.

---

### Post by Saiboogu on 2005-10-19
[QUOTE=HanZo]unfortunately enabling extended attibutes created big troubles... system would not start and I had to use system rescue disk to restore old fstab again... can it be that the beagle wiki is somehow misleading on this part. I use a ext3 fs, and Breezy, I have one big partition with everything in it (system and home) what exactly do I have to write in the fstab?
note: beagle seems to work fine for evolution, tomboy but It does not find any file on my hd... looks like I need those extended attributes...[/QUOTE]

No problems with extended attributes here. Here's my fstab line - Breezy default, except for adding the attributes option from Beagle wiki:

```
/dev/hdb1       /               ext3    defaults,user_xattr,errors=remount-ro 0       1
```

---

### Post by mtron on 2005-10-20
[QUOTE=arunsub]I could make beagle search my Windows partition also.... and added my windows partition to folders to be indexed.[/QUOTE]

I assume you use vfat for your windows partition. Did you enable any extended attributes like on a ext3 partition in your fstab? or is it working also without it?

cheers

---

### Post by jon_gunnar on 2005-10-20
[QUOTE=aysiu]Beagle baffled me the first time I tried to use it. [This Ubuntu Forums thread](http://ubuntuforums.org/showthread.php?t=31518) recommended [url=http://beaglewiki.org/index.php/UbuntuInstall]the [/QUOTE]

Thank's a lot for this. Then I finally got beagle running without problems too. :p

---

### Post by arunsub on 2005-10-20
[QUOTE=mtron]I assume you use vfat for your windows partition. Did you enable any extended attributes like on a ext3 partition in your fstab? or is it working also without it?

cheers[/QUOTE]
I have 2 windows partition, one for programs and windows and another one for my documents. Both are vfat. I enabled extended attribute only to Linux home folder. I didn't do anything to windows partition. I just added that partition to file and indexing. I'll post my fstab if you want once i go home.

---

### Post by kashms on 2005-10-20
Every time I try to start beagled, it exits with an error:
```

Unhandled Exception: GLib.GException: Unknown error
in <0x00187> Evolution.Cal:GetChanges (string,Evolution.CalComponent[]&,Evolution.CalComponent[]&,string[]&)
in <0x00121> Beagle.Daemon.EvolutionDataServerQueryable.CalContainer:IndexChanges ()
in <0x001c8> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:IndexSourceGroup (Evolution.SourceGroup,bool)
in <0x001c6> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:.ctor (string,System.Type,Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable,string)
in <0x000fc> Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable:Start ()
in <0x00016> Beagle.Daemon.Queryable:Start ()
in <0x000e9> Beagle.Daemon.QueryDriver:Start ()
in <0x0012e> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f4b74f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0057b> Beagle.Daemon.BeagleDaemon:Main (string[])


** (beagled:7916): WARNING **: FIXME: wait for completion unimplemented
```

It worked the very first time I started it, but refuses to after that. I'm not sure what is going on?

---

### Post by kvidell on 2005-10-20
Works fine for me. I'm quite impressed.

And it's only using 98 megs of ram for me, which isn't an issue because this laptop has 2 gigs of it ;P
- K

---

### Post by mtron on 2005-10-21
Thanks. It also works on my vfat partition. Indexes even ID3 tags of mp3s.

Really impressive tool, and the search speed is absolutly amazing! 

Only problem left it that this version doesn't index thunderbird mailboxes. That's the really big missing feauture now. I hope sb is working on it. 

But the rest, respect! Very good work. I remember seeing the google desktop search on a co - workers computer... arg. slows down the system horribly and has only a browser search interface. 

beagle is much faster in bringing results and does NOT slow down the system at all. Even on my quite old P4 1.8 GHZ with only 256 MB ram.

Try it!

---

### Post by ameerirshad on 2005-10-23
> ** (/usr/lib/beagle/Info.exe:520): WARNING **: _wapi_connect: Need to translate 2 [No such file or directory] into winsock error
Could not connect to the daemon.

Is what I get when I type *beagle-info --status* after following all aother steps of your tutorial! I would really like this Beagle to get to work someday....... but untill now it seems it refuses

---

### Post by teevee on 2005-10-23
How can beagled be stopped and restarted easily? If using beagle-shutdown and then restarting beagled, I get...

```
Unhandled Exception: System.Net.Sockets.SocketException: Address already in use
in <0x000cb> System.Net.Sockets.Socket:Bind (System.Net.EndPoint)
in <0x00022> System.Net.Sockets.TcpListener:Start ()
in <0x00056> System.Runtime.Remoting.Channels.Tcp.TcpServerChannel:StartListening (object)
in <0x0001c> System.Runtime.Remoting.Channels.Tcp.TcpChannel:StartListening (object)
in <0x002bc> System.Runtime.Remoting.Channels.ChannelServices:RegisterChannel (System.Runtime.Remoting.Channels.IChannel)
in <0x00053> Beagle.WebService.WebBackEnd:init ()
in <0x0025b> Beagle.WebService.WebServiceBackEnd:Start ()
in <0x0018a> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7ec874f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0057b> Beagle.Daemon.BeagleDaemon:Main (string[])
```
...there's still a mono-beagled process after running beagle-shutdown. This can't be killed with killall for some reason(?), but with kill -15 `pidof mono-beagled`. Kind of lame though. Any better way? I have to stop it when playing games, otherwise beagled slows it down horribly.

---

### Post by justaguynpc on 2005-10-23
I liked what I saw of this package when installed.  However, I thought it's RAM usage was way too steep for me, having 512M for memory.  After heavy surfing, it caused all sorts of problems with X!! Locked my system up hard: lost workable cursor, firefox failed to load pages, ctl:alt:backspace was unusable altogether due to its burden on available memory.  Finally had to hard reboot ... not happy 'bout that!

Repeated "mono" issues seem to be the culprit here.

Hoping once it comes out of beta, issues will be resolved.

justaguy

---

### Post by Nonno Bassotto on 2005-10-23
I would love to use beagle, but i have to install even evolution! Why is this?
is there any workaround? Sometimes I don't understand the dependencies (e.g. Mplayer needs Xmms). Why some desktop-related tools need evolution? I think that this not a great design if one wants to replace the mail reader or do without.
Andrea

---

### Post by teevee on 2005-10-24
[QUOTE=justaguynpc]I liked what I saw of this package when installed.  However, I thought it's RAM usage was way too steep for me, having 512M for memory.  After heavy surfing, it caused all sorts of problems with X!! Locked my system up hard: lost workable cursor, firefox failed to load pages, ctl:alt:backspace was unusable altogether due to its burden on available memory.  Finally had to hard reboot ... not happy 'bout that![/QUOTE]
Wow, deja vu!

[http://www.ubuntuforums.org/showthread.php?t=81307](http://www.ubuntuforums.org/showthread.php?t=81307)

---

### Post by crypto178 on 2005-10-24
[QUOTE=Nonno Bassotto]I would love to use beagle, but i have to install even evolution! Why is this?
is there any workaround? Sometimes I don't understand the dependencies (e.g. Mplayer needs Xmms). Why some desktop-related tools need evolution? I think that this not a great design if one wants to replace the mail reader or do without.
Andrea[/QUOTE]
The point of beagle is to go beyond simple file searching (the 'locate' command does that much faster) by indexing data from other desktop applications. A good example is the ability to search tomboy notes or firefox history (need an extension for that though). In the case of evolution, I think beagle has a (more subtle) way to index emails that doesn't rely on the raw mbox files stored on your hard drive. Therefore it needs some evolution libraries to get the data.
If you want a lighter version of beagle, you could try to compile it yourself, there must be some flags specifying whether or not including a specific feature.

---

### Post by guter_gecko on 2005-10-25
uuuh this is really way nicer, than the beaglewiki ( which actually worked for me...but was a lot of trouble)

BIIIIIG THANKS

---

### Post by kroiz on 2005-10-25
I use breezy.
after I have done what is described in the first post, should I continue and follow the beagle wiki?
should I use the user_xattr? (I have only one partition.)

I feel like there are not much posts regading beagle, in this forums, does that mean that it is not for newbies?

---

### Post by jmb365 on 2005-11-19
I am trying to run beagled version 0.1.1 on Ubuntu 5.1 (Breezy) stock install with latest updates, and don't seem to get anything indexed.  Can anybody provide a clue?  This is my second unsuccessful attempt on a different PC with a fresh Ubuntu "Breezy" installed.

Beagle was installed (using apt-get) following the directions of the Wiki at "http://beaglewiki.org/index.php/UbuntuInstall"  I have configured beagle to search my (local) home directory & one NFS mounted directory "/home/Engr".  "beagle-index-info" shows zero files have been indexed!  I do not use Kmail, Evolution, calendars or addressbooks on this test machine.  I have even tried by rebooting the PC as well.  Here are some of the WARNINGS & ERRORS I get with debug turned on:

export BEAGLE_EXERCISE_THE_DOG=1
beagled --fg --debug

INFO: Starting Beagle Daemon (version 0.1.1)
DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe --fg --debug
DEBUG: Starting main loop
DEBUG: Starting messaging server
DEBUG: Starting QueryDriver
DEBUG: Found index helper at /usr/lib/beagle/beagled-index-helper
DEBUG: Found 1 types in EvolutionDataServer, Version=0.0.0.0, Culture=neutral
INFO: KMail folders not found. Will keep trying
DEBUG: Starting Inotify Backend
DEBUG: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
DEBUG: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
DEBUG: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
DEBUG: Loading Beagle.Util.Conf+NetworkingConfig from networking.xml
DEBUG: Loading Beagle.Util.Conf+WebServicesConfig from webservices.xml
DEBUG: Found 12 types in BeagleDaemonLib, Version=1.4.3.3, Culture=neutral
DEBUG: Found 0 user-configured static queryables
INFO: Scanning addressbooks and calendars
INFO: Scanned addressbooks and calendars in 1.79s
INFO: Starting Evolution mail backend
WARN: Evolution mail store not found, watching for it.
DEBUG: Adding root: /home/ks
INFO: Starting KMail backend
DEBUG: KMail directories (local mail) /home/ks/.kde/share/apps/kmail/dimap not found, will repoll.
DEBUG: Loaded 0 records from /home/ks/.beagle/Indexes/FileSystemIndex/FileAttributesStore.db in 0.246s
DEBUG: Adding root: /home/Engr
DEBUG: Done starting FileSystemQueryable
DEBUG: Starting Scheduler thread
DEBUG: Starting Inotify threads
INFO: This Computer Hostname: localhost.localdomain
DEBUG: Starting WebBackEnd
INFO: Starting WebServiceBackEnd
DEBUG: Global WebServicesAccess Enabled
DEBUG: Starting Internal Web Server
BeagleXsp
Listening on port: 8888
Listening on address: 0.0.0.0
Root directory: /usr/share/beagle/xsp
** (beagled:13595): WARNING **: _wapi_connect: Need to translate 2 [No such file or directory] into winsock error
DEBUG: Caught ResponseMessageException: System call failed
DEBUG: Launching helper process
WARN: Caught exception in DoTaskReal
WARN:         Tag: Final Flush for FileSystemIndex
WARN:     Creator:
WARN: Description:
WARN:    Priority: Maintenance (100)
WARN: System.Exception: Couldn't launch helper process
in <0x00144> Beagle.Daemon.RemoteIndexer:LaunchHelper ()
in <0x002b4> Beagle.Daemon.RemoteIndexer:SendRequest (Beagle.Daemon.RemoteIndexerRequest request)
in <0x001bd> Beagle.Daemon.RemoteIndexer:Flush (Beagle.Daemon.IndexerRequest request)
in <0x00158> Beagle.Daemon.LuceneQueryable:Flush ()
in <0x00010> Beagle.Daemon.LuceneQueryable+FinalFlushTask:DoTaskReal ()
in <0x000dc> Beagle.Util.Scheduler+Task:DoTask ()
DEBUG: Starting messaging server
DEBUG: Helper Size: VmRSS=9.3 MB, size=1.00, 0.0%
DEBUG: Helper Size: VmRSS=9.5 MB, size=1.02, 0.5%
DEBUG: Helper Size: VmRSS=9.5 MB, size=1.02, 0.5%
DEBUG: Helper Size: VmRSS=9.5 MB, size=1.02, 0.6%
DEBUG: Helper Size: VmRSS=9.5 MB, size=1.02, 0.6%
DEBUG: Helper Size: VmRSS=9.5 MB, size=1.02, 0.6%
DEBUG: BeagleXSP Applications list: /:/usr/share/beagle/xsp,/beagle:/usr/share/beagle/xsp,/beagle/local:/usr,/beagle/gnome:/usr,/beagle/img:/home/ks/.beagle/img
DEBUG: Daemon initialization finished after 85.07s
DEBUG: Helper Size: VmRSS=9.5 MB, size=1.02, 0.6%
DEBUG: Helper Size: VmRSS=9.5 MB, size=1.02, 0.6%
... several similar lines deleted...
DEBUG: Helper Size: VmRSS=9.8 MB, size=1.06, 1.5%
DEBUG: Helper Size: VmRSS=11.7 MB, size=1.26, 6.6%
DEBUG: Helper Size: VmRSS=15.6 MB, size=1.69, 17.2%
DEBUG: Helper Size: VmRSS=17.2 MB, size=1.86, 21.5%
DEBUG: Helper Size: VmRSS=19.2 MB, size=2.07, 26.8%
DEBUG: Optimizing EvolutionDataServerIndex
DEBUG: Helper Size: VmRSS=21.0 MB, size=2.27, 31.7%
DEBUG: Optimizing MailIndex
DEBUG: Optimizing KMailIndex
DEBUG: Optimizing FileSystemIndex
DEBUG: Optimizing GaimLogIndex
DEBUG: Optimizing IndexingServiceIndex
DEBUG: Optimizing TomboyIndex
DEBUG: Optimizing BlamIndex
DEBUG: Optimizing LifereaIndex
DEBUG: Optimizing AkregatorIndex
DEBUG: Optimizing KopeteIndex
DEBUG: Helper Size: VmRSS=21.6 MB, size=2.34, 33.4%
DEBUG: Helper Size: VmRSS=21.6 MB, size=2.34, 33.4%
... several similar lines deleted...
DEBUG: Helper Size: VmRSS=21.8 MB, size=2.35, 33.8%
DEBUG: Helper Size: VmRSS=21.8 MB, size=2.35, 33.8%
DEBUG: No activity for 30.0 minutes, shutting down
DEBUG: (1) Waiting for 1 worker...
DEBUG: waiting for server '/home/ks/.beagle/socket-helper'
INFO: Exiting
DEBUG: Server '/home/ks/.beagle/socket-helper' shut down

Thanks
JMB

---

### Post by bugi on 2005-11-28
Beagle makes port number 8888 open. Is it secure?

---

### Post by JazzCrazed on 2005-11-29
Nice! Thanks for this howto - worked really well!

One minor quip, though... Any way to change the font size it's using? For some reason for me, it's using a really small font.

---

### Post by Telep on 2005-12-01
[QUOTE=crypto178]The point of beagle is to go beyond simple file searching (the 'locate' command does that much faster) by indexing data from other desktop applications. A good example is the ability to search tomboy notes or firefox history (need an extension for that though). In the case of evolution, I think beagle has a (more subtle) way to index emails that doesn't rely on the raw mbox files stored on your hard drive. Therefore it needs some evolution libraries to get the data.
If you want a lighter version of beagle, you could try to compile it yourself, there must be some flags specifying whether or not including a specific feature.[/QUOTE]

I guess it's still pretty stupid to actually *require* installing software simply because Beagle supports it. I guess that's what being Beta means though. :)

---

### Post by Cl1mh4224rd on 2005-12-03
Hmm... Beagle seems to only index MP3s by the ID3v2 tag (or the file name itself, of course), ignoring ID3v1 tags. :?

---

### Post by gmc on 2005-12-03
Hi Folks,

     I've successfully got Beagle running, but I wondered if anyone knows how to add the "user_xattr" to a usb mounted external hard drive?

G.

Update: I found the answer to this question [here]("http://www.ubuntuforums.org/showthread.php?t=59919&highlight=user_xattr")

---

### Post by benplaut on 2005-12-03
it's a big ugly memory hog, and the one in the repos won't index .doc files :|

---

### Post by Rob2687 on 2005-12-03
Seems to index docs just fine for me.

---

### Post by besada on 2005-12-09
For the people with evolution calendar exceptions when reloading beagle, with a mesage similar to:

Unhandled Exception: GLib.GException: Unknown error
in <0x00187> Evolution.Cal:GetChanges (string,Evolution.CalComponent[]&,Evolution.CalComponent[]&,string[]&)
in <0x00121> Beagle.Daemon.EvolutionDataServerQueryable.CalContainer:IndexChanges ()
in <0x001c8> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:IndexSourceGroup (Evolution.SourceGroup,bool)
in <0x001c6> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:.ctor (string,System.Type,Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable,string)
in <0x000fc> Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable:Start ()
in <0x00016> Beagle.Daemon.Queryable:Start ()
in <0x000e9> Beagle.Daemon.QueryDriver:Start ()
in <0x0012e> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f4b74f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0057b> Beagle.Daemon.BeagleDaemon:Main (string[])


** (beagled:7916): WARNING **: FIXME: wait for completion unimplemented

To solve this, use

beagled --deny-backend EvolutionDataServer

This will not index calendar and contacts information in evolution, but will continue indexing mails. No problems after this.

---

### Post by BanskuZ on 2006-04-01
```

kayttaja@mahtava:~$ beagle-info --status
Could not connect to the daemon.

```

---

### Post by jahtooth on 2006-04-22
[QUOTE=benplaut]it's a big ugly memory hog, and the one in the repos won't index .doc files :|[/QUOTE]
try and install the "wv" package (word viewer) and you'll see your .doc files index too. (Found the tip on: [http://www.antezeta.com/beagle-fedora.html](http://www.antezeta.com/beagle-fedora.html))

---

### Post by fmpuk on 2006-04-22
When I try and install beagle from apt I get this error:

The following packages have unmet dependencies:
  beagle: Depends: firefox (>= 1.4.99) but 1.0.8-0ubuntu5.10 is to be installed
E: Broken packages

But I have Firefox 1.5 installed so I am really confused as to why it is doing this.  
Thanks!

---

### Post by magnusbb on 2006-04-23
I have the same problem here.

---

### Post by invalid on 2006-12-09
As of version 2.0
```
best --no-tray
```
should be
```
beagle-search --no-tray
```

---

### Post by sipickles on 2007-12-13
Is it possible to add a samba shared network location to the search path for beagle?

Thanks!

Si

---

### Post by go_beep_yourself on 2007-12-21
Is it possible to get a native  Beagle for Windows?

---

### Post by dbera on 2007-12-21
> **go_beep_yourself said:**
> Is it possible to get a native  Beagle for Windows?

No. Its linux only.

---

