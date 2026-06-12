---
title: "HOWTO: Install gift/Apollon filesharing (kazaa, gnutella, openft)"
date: 2005-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by sk545 on 2005-08-25
This was somewhat of a pain to get running, so i am gonna post here how i did it.

So, you wanna share/download files from the kazaa, gnutella, or openft network? Follow these steps:

1) Install the required pacakges (will require you to have the [universe](http://ubuntuguide.org/#extrarepositories) section in sources.list):
```
 $ sudo apt-get install gift giftd apollon
```
Note: apollon is a client, you could use any client.  Another one is giftoxic, so you could use that instead if you don't like QT/KDE libs in a Gnome environment.

That should install all of these:
```
gift                                            
giftd                                                                        
libgift0                                        
libgiftproto0                                 
libgnutella-gift                               
libopenft-gift
apollon

```
However, you need the fastrack (kazaa) plugin too.  That is not in the repository, so download it here:

[ftp://ftp.berlios.de/pub/gift-fasttrack/dists/unstable/main/binary-i386/](ftp://ftp.berlios.de/pub/gift-fasttrack/dists/unstable/main/binary-i386/)

Its called libfasttrack-gift_0.8.9-1_i386.deb, and to install it, do this:
```
$ sudo dpkg -i libfasttrack-gift_0.8.9-1_i386.deb
```
You should now have all the required packages installed, and believe it or not, that was the easy part.  Get ready for the next step.

2)  Configuring gift to work.

Run this command as user, NOT root or sudo:
```
$ gift-setup
```
That will launch the gift setup script.  It is quite long and takes a bit of patience, but most choices should be self-explanatory.  If you hit 'Enter' it will use the default choice, which is what i did in most instances.  However, make sure to set the first question to 1, otherwise gift won't even start.  Another question is that it will ask you to give it what plugins to use.  In that question, put in the answer exactly like so (yes its case sensitive):
```
OpenFT:Gnutella:FastTrack
```
Other things to set will be your incoming and outgoing folder, and also your upload/download limits.  This depends on your particular connection.

After all of the questions are answered, the script will end and drop you back to the command prompt.

Ofcourse, we aren't done yet.

3)  Configuring the plugins

One problem that i noticed is that even after going through the 'gift-setup' script, it does not make the required folders in your home folder for the plugins.  You are supposed to have a FastTrack, Gnutella, and a OpenFT folder in your ~/.giFT folder.  Check to see if they are there already, and if not you're going to have to make them manually.  Here is how to make them manually:
```
 cd ~/.giFT
$ mkdir FastTrack
$ mkdir Gnutella 
$ mkdir OpenFT

```
So, we done? Nope.  Read on cowboy.

Ok, so now you have the required folders, but they are empty.  You need to copy over the config files from /usr/share/giFT<plugin directory> into the directories you just made above.  In other words, you need to do it like so:
```

$ sudo cp /usr/share/giFT/OpenFT/OpenFT.conf.template  ~/.giFT/OpenFT/  OpenFT.conf

$ sudo cp /usr/share/giFT/OpenFT/nodes  ~/.giFT/OpenFT/

$ sudo cp /usr/share/giFT/FastTrack/FastTrack.conf.template ~/.giFT/FastTrack/FastTrack.conf

$ sudo cp /usr/share/giFT/Gnutella/Gnutella.conf.template ~/.giFT/Gnutella/Gnutella.conf

$ sudo cp /usr/share/giFT/Gnutella/gwebcaches ~/.giFT/Gnutella/

```
After doing all that, make sure your owner/group permisssions are correct in the plugin folder.  So, for example, if you go to ~/.giFT/Gnutella and do 'ls -l Gnutella.conf', it should say that its owner is you and the group is you:
```
-rw-r--r--  1 you you 1537 2005-08-25 10:47 Gnutella.conf
```
If it shows up as 'root' and not 'you' then change the ownership and group like so:
```
$ sudo chown you Gnutella.conf
$ sudo chgrp you Gnutella.conf

```
Ofcourse, substitude 'you' with your username.  Make sure to do this to all the files you copied over from /usr/share/giFT/<plugin directories>.

Out of all of the above, OpenFT conf file needs to be edited only.  Open up the OpenFT config file like so:
```
$ gedit ~/.giFT/OpenFT/OpenFT.conf
```
After opening it, just comment the port sections and save the file:

#port = 1215
#http_port = 1216

This will make OpenFT use the default behavior, which is using random ports (at least that is what worked for me).

Almost done...start up apollon (or giftoxic) and it will try to connect and use gift.

If there are problems, try running gift from the command line like so:
```
$ giftd -v
```
That will spit out any errors/problems that gift is encountering.  The log is also saved in the ~/.giFT folder as giftd.log.

Good luck!

Thanks to the following thread on Gentoo forums:

[http://forums.gentoo.org/viewtopic.php?t=130787](http://forums.gentoo.org/viewtopic.php?t=130787)

I am also attaching my ~/.giFT/giftd.conf file, which i have working behing a NAT router/firewall.

---

### Post by Mishura on 2005-08-26
Apollon is great.  It has replaced Limewire as my favorite p2p app.

---

### Post by picpak on 2005-08-26
First off: Great work :) 

Secondly: How do you add extra plugins? (Ares, OpenNap, etc)? I installed them, I ran the setup, I edited giftd.conf, I checked the permissions, and it still won't load. Any ideas?

---

### Post by sk545 on 2005-08-29
So, did the instructions work for you for the other plugins?  Let me know if i missed any steps and or something....

As for Ares/Opennap....well, OpenNap-plugin is sorta dead:

[http://gift-opennap.berlios.de/](http://gift-opennap.berlios.de/)

You can try to get it to work...

Ares you should be able to get working...i haven't tried it, will let you know soon if i get it working.

---

### Post by picpak on 2005-08-29
Ok, thanks. I wasn't too concerned about OpenNap...I just saw a giFT screenshot with OpenNap on it and wanted to try it out.

---

### Post by sk545 on 2005-08-29
Well, this is how i installed Ares (even though it didn't work, but maybe it will work on your machine):

```
$ sudo apt-get install libgiftproto-dev libgift-dev
```

Then i downloaded the Ares plugin:

[http://developer.berlios.de/project/showfiles.php?group_id=2648](http://developer.berlios.de/project/showfiles.php?group_id=2648)

Untared gift-ares-0.2.2.tar.bz2, and just did 'configure',  'make' then 'sudo make-install'.  Also, i added the word Ares in giftd.conf like so:

plugins = OpenFT:Gnutella:FastTrack:Ares

Then i ran 'giftd -v' which i think made the ~/.giFT/Ares directory automatically (unlike the other plugins).  However, when i run apollon, it just says 'connecting' forever under the Ares icon.  I did open the port 59049 in my NAT firwall, but still no luck.

The only things relevant to Ares in ~/.giFT/giftd.log file are these:

[14:37:59] Plugin Ares (0.2.2) successfully loaded and initialized
[14:37:59] Ares: asp_plugin.c:230(asp_giftcb_start): Starting up.
[14:37:59] Ares: as_ares.c:87(as_init): Initializing Ares library...
[14:37:59] Ares: as_node_man.c:481(as_nodeman_load): Loaded 353 nodes from node file
[14:37:59] Ares: as_session_man.c:78(as_sessman_connect): Requested: 4, connected: 0, connecting: 0

**Ares* GIFT-ERROR: Ares: Handshake with 24.226.36.38:8797 failed. Got something else than ACK.

---

### Post by oliwally on 2005-09-08
Your instructions here have been brillian! I have struggled to get amule going on my particular modem (D-link dsl-302g) but without success.

This (Apollon) works beautifully. Thanks so much

---

### Post by sk545 on 2005-09-08
> Your instructions here have been brillian! I have struggled to get amule going on my particular modem (D-link dsl-302g) but without success. 
welcome.  The trick to amule is to have to correct ports open on the router's firewall.  Try looking here:

[http://www.portforward.com/english/routers/port_forwarding/Dlink/DSL-302Gv2/eMule.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DSL-302Gv2/eMule.htm)

---

### Post by Harry_Sack on 2006-02-12
"However, you need the fastrack (kazaa) plugin too. That is not in the repository, so download it here:

[ftp://ftp.berlios.de/pub/gift-fasttr...n/binary-i386/](ftp://ftp.berlios.de/pub/gift-fasttr...n/binary-i386/)

Its called libfasttrack-gift_0.8.9-1_i386.deb, and to install it, do this"


          This didn't work for me, the page would never load, so here's another solution : [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/)
Add those to sources.list to apt-get fasttrack-plugin  (and Ares if you want)  :mrgreen:

Does anyone know if there are bittorrent or ed2k plugins available too?
would be nice to do all filesharing through a single program.

And thanks for the guide!

---

### Post by realdog on 2006-04-01
I try to install apollon and give me this result

hugo@ubuntu:~$ sudo cp /usr/share/giFT/OpenFT/OpenFT.conf.template  ~/.giFT/OpenFT/  OpenFT.conf
Password:
cp: `OpenFT.conf': specified destination directory does not exist
Try `cp --help' for more information.
 
 What can i do

---

### Post by akiro.yamamoto on 2006-04-04
You can also use the Ares plugin.
Just convert the SUSE guru 3.0.1 ares .rom to .deb with alien and re-run the gift-setup (choose Y to keep your original conf file) to enable it, then you can select it in apollon and access the Ares network.

Hope this info helps ;)

---

### Post by easyease on 2006-04-22
thanks for doing all the hard work. very much appreciated. it works great for me!

---

### Post by clayhd on 2006-11-12
> **realdog said:**
> I try to install apollon and give me this result

hugo@ubuntu:~$ sudo cp /usr/share/giFT/OpenFT/OpenFT.conf.template  ~/.giFT/OpenFT/  OpenFT.conf
Password:
cp: `OpenFT.conf': specified destination directory does not exist
Try `cp --help' for more information.
 
 What can i do

You have a space before the OpenFT.conf that shouldn't be there. That that away and you will be fine

---

### Post by jasex on 2006-11-14
Woot. Thanks.

---

### Post by carlo_v2.0 on 2006-11-22
Hi have just followed the instructions and have successfully installed gift with apollon with FastTrack, Open FT and Gnutella plugins, however when I start apollon it onl connects to Gnutella, and isn't connecting to the other two I am new t ubuntu so I dare say I've done somethin wrong somewhere any help would be greatly appreciated, thanks

---

### Post by Extrapolation on 2007-02-01
Oddly, mine connects to everything *except* Gnutella.  And with Ares I get only 2 users and 2 files.  Is there a setting in the conf files that I oughtta be playing around with?

---

### Post by gollybegully on 2007-02-19
I am only able to connect to Open FT which only has like 400 users right now

when running in verbose mode I get: 

Gnutella: No hosts to try. Looking in gwebcaches...
 Gnutella: gt_web_cache.c:780(access_gwebcaches): Access already in progress
 Gnutella: Retrying to connect to nodes...

and for fasttrack I get something like:

FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 217.121.228.142:3316
[13:31:18] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.168.174.194:3384, load: 50%
[13:31:18] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[13:31:18] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.57.223.163:3691 
ending with
FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others

---

### Post by myname on 2007-02-20
I have OpenFT, Fasttrack, Gnutella, and Ares installed, and forwarded the correct ports (in my router) found in the .conf files, and only OpenFT is connected, the rest say connecting.

Any ideas?

--Kevin

---

