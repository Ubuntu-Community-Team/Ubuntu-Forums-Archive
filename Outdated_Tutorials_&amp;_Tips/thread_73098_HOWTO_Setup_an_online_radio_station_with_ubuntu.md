---
title: "HOWTO: Setup an online radio station with ubuntu"
date: 2005-10-08
forum: Outdated Tutorials &amp; Tips
---

### Post by JimmyJazz on 2005-10-08
This HOWTO will explain how to set up an online radio station for an example to tune into mine: [http://jimmyjazz.homeip.net:808/listenwavy/](http://jimmyjazz.homeip.net:808/listenwavy/)

*NOTE: you can play whatever you want on your station but, for the record I reccomend complying with the copyright laws as they may be set out in your region*

There are alot of way to set up an online radio station but for the sake of simplicity I will explain how I do it personally.
All online station are made up of two parts the server and the source.

THE SERVER...
for my station I use the standard shoutcast server,  Icecast is a better open source server but for my need I use shoutcast.

download shoutcast:

	wget [http://www.shoutcast.com/downloads/sc1-9-5/shoutcast-1-9-5-linux-glibc6.tar.gz](http://www.shoutcast.com/downloads/sc1-9-5/shoutcast-1-9-5-linux-glibc6.tar.gz)

untar it:

	tar -zxvf shoutcast-1-9-5-linux-glibc6.tar.gz

move to a usable location (i.e. /usr/local/bin)

	cd shoutcast-1-9-5-linux-glibc6/

	sudo cp sc_serv /usr/local/bin

	sudo cp sc_serv.conf /usr/local/etc

	sudo chmod 755 /usr/local/bin/sc_serv

edit the config:

	sudo nano /usr/local/etc/sc_serv.conf

at this point the only thing you should need to change in this file is the password. save it. next step...

Launch the server:

	sudo sc_serv /usr/local/etc/sc_serv.conf

test it in a browser:

	localhost:8000

Works? good...
now its time to feed some music to your new server.  For this I use ices 0.4 (which handles mp3s if you wanna use OGG you can use ices 2.0)

THE SOURCE...

get ices:

	wget [http://downloads.us.xiph.org/releases/ices/ices-0.4.tar.gz](http://downloads.us.xiph.org/releases/ices/ices-0.4.tar.gz) 

(at this point there doesn't seem to be a package in repos for ices 0.4 so we are going to build from source however, there is one for ices 2.0 so you can just 'apt-get install ices2' if you wanna
go that route but if you do that you're on your own from here.)

untar it:

	tar -zxvf ices-0.4.tar.gz

okay time to build it:

you will need Lame (sudo apt-get install lame liblame-dev)
you may need some other dependencies but you should be able to figure out what from simpley reading any error messages that come up.
we are compiling with lame I don't reccomend compiling without it although you can.  Okay enough talk...

	./configure --with-lame
 
no errors? then...

	sudo make 

	sudo make install

if everything worked without error then you now have ices compiled and ready for fun...
now lets do some configing, first off you are going to want to put all the mp3s you want to play on your station in a directory together (it can contain sub directories as well)
now we make a handy playlist for ices to read...

	find /path/to/your/mp3s -type f -name "*.mp3" > /path/to/your/mp3s/play.lst

now you have a nice big playlist containing all the mp3s in the directory you indicated and better yet its formatted in a way ices can read, now we config ices...

	sudo nano /usr/local/etc/ices.conf.dist

	okay this config is real self explainatory but the main thing you wanna change is the playlist handler so enter the path to that playlist we just made.
now get down were you see the server config section, this is where you will specify howto feed the music to the server we set up earlier.  Hostname will be the address to your server, localhost will usally work but you may need something more specific (if you are not sure just type localhost:8000 in a browser and see if anything happens).  Keep the port at 8000 for now.  Enter the password from your server config file in the password section.  Now this the protocol should be set to 'icy' (without quotes) that important since we are feeding to a shoutcast server.  The rest of the config file is up to you to figure out, you'll see parts there where you name your stream and what not.  Remeber an average broadband connection can't handle very many people at 128k stereo so don't be to greedy (unless you have a sweet connection).
Go ahead and save you file when you are done...I'll wait...

okay lets launch this baby...

	ices -c /usr/local/etc/ices.conf.dist

you're done! now if everything went well you can goto 'localhost:8000' in your browser and start enjoying some tunes.

If you have any questions feel free to ask me. and umm listen to my station here: [http://jimmyjazz.homeip.net:808/listenwavy](http://jimmyjazz.homeip.net:808/listenwavy)

*NOTE: you may have noticed there arn't many good GUI interfaces for sourcing to a shoutcast server on Linux if anyone would like to start some sort of easy plugin for say BEEP_MEDIA_PLAYER I would be really interested in hearing about it*

---

### Post by kscurloc on 2005-10-24
Having problems getting LAME.  Any suggestions.  The apt-get procedure you've outlined gives this result:

#sudo apt-get install lame liblame-dev
Reading package lists... Done
Building dependency tree... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate

---

### Post by andlinux21 on 2005-10-30
I didnt go through all that not sure about security issues though.  I set up my own shoutcast server by downloading the 2 components off the shoutcast website (one for server and one for dj). I extracted each into their own directories.  Then i did sudo gedit <config filename>.conf  i put the necessary info in and then saved. I then started the server and then the dj and wham shoutcast was up and running :p

---

### Post by Funktown on 2005-11-01
The steps you outline have the user overwrite /usr/local/etc with the configuration file (or that was my case, anyways). Oh well, nothing seems to be broken yet =P Should be: 

**sudo cp sc_serv.conf /usr/local/etc/sc_serv.conf**
**sudo cp sc_serv /usr/local/bin/sc_serv**

---

### Post by JimmyJazz on 2005-11-20
[QUOTE=andlinux21]I didnt go through all that not sure about security issues though.  I set up my own shoutcast server by downloading the 2 components off the shoutcast website (one for server and one for dj). I extracted each into their own directories.  Then i did sudo gedit <config filename>.conf  i put the necessary info in and then saved. I then started the server and then the dj and wham shoutcast was up and running :p[/QUOTE]

yeah thats anotehr method but ices is really much better with more features than the sourcing client you get from the nullsoft webpage.  Ices includes python support and ID3 reading.

---

### Post by andlinux21 on 2005-11-27
Ok I'll have to try it out do you have a server running so I can check out your station??

---

### Post by DaMasta on 2005-12-29
Yes, this is somewhat old but I wanted to comment....why doesn't scrobbler pick up the id3 tags? My last.fm profile is not getting updated. JimmyJazz, I listened to your station and last.fm was not updated then either. Any ideas? Scrobbler plugin says bad id3 tag but I know they're good. :confused:

---

### Post by galgoz on 2006-01-14
you say 

move to a usable location (i.e. /usr/local/bin)

do you mean move the entire folder that is created when you untar the file?

at this step

sudo nano /usr/local/etc/sc_serv.conf

I get a blank file?

---

### Post by JimmyJazz on 2006-01-14
[QUOTE=galgoz]you say 

move to a usable location (i.e. /usr/local/bin)

do you mean move the entire folder that is created when you untar the file?

at this step

sudo nano /usr/local/etc/sc_serv.conf

I get a blank file?[/QUOTE]

just run the following commands (sorry the formatting of the how-to is a little confusing)

cd shoutcast-1-9-5-linux-glibc6/

sudo cp ./sc_serv /usr/local/bin

sudo cp ./sc_serv.conf /usr/local/etc

sudo chmod 755 /usr/local/bin/sc_serv

sudo gedit /usr/local/etc/sc_serv.conf

---

### Post by galgoz on 2006-01-14
Ok, moved beyond that using the corrected post from FunkTown but now when I run

 sudo sc_serv /usr/local/etc/sc_serv.conf

I get the following:

<01/14/06@00:24:02> [SHOUTcast] DNAS/Linux v1.9.5 (Dec 27 2004) starting up...
<01/14/06@00:24:02> [main] pid: 7266
<01/14/06@00:24:02> [main] loaded config from /usr/local/etc/sc_serv.conf
<01/14/06@00:24:02> [main] initializing (usermax:32 portbase:8000)...
<01/14/06@00:24:02> [main] No ban file found (sc_serv.ban)
<01/14/06@00:24:02> [main] No rip file found (sc_serv.rip)
<01/14/06@00:24:02> [main] opening source socket
<01/14/06@00:24:02> [main] error opening source socket! FATAL ERROR! Some other process is using this port!


Any ideas?

---

### Post by JimmyJazz on 2006-01-14
[QUOTE=galgoz]Ok, moved beyond that using the corrected post from FunkTown but now when I run

 sudo sc_serv /usr/local/etc/sc_serv.conf

I get the following:

<01/14/06@00:24:02> [SHOUTcast] DNAS/Linux v1.9.5 (Dec 27 2004) starting up...
<01/14/06@00:24:02> [main] pid: 7266
<01/14/06@00:24:02> [main] loaded config from /usr/local/etc/sc_serv.conf
<01/14/06@00:24:02> [main] initializing (usermax:32 portbase:8000)...
<01/14/06@00:24:02> [main] No ban file found (sc_serv.ban)
<01/14/06@00:24:02> [main] No rip file found (sc_serv.rip)
<01/14/06@00:24:02> [main] opening source socket
<01/14/06@00:24:02> [main] error opening source socket! FATAL ERROR! Some other process is using this port!


Any ideas?[/QUOTE]

yeah looks like some other proccess is using port 8000 try 8002 - 8003

---

### Post by JimmyJazz on 2006-01-14
I really need to **rewrite** this and post it to the breezy section soon.

---

### Post by galgoz on 2006-01-18
during the make I get this error.

```

checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
configure: /usr/bin/pkg-config couldn't find libshout. Try adjusting PKG_CONFIG_PATH.
checking for shout-config... no
configure: error: Could not find a usable libshout

```

---

### Post by Jenga201 on 2007-10-29
I'm getting an error when trying to start ices.

Cannot use config file (no XML support).
Ices Exiting...

I'm not sure what i'm missing for this.  I believe i did all the config files correctly.

Thanks for your help.

---

### Post by Vitamin-Carrot on 2007-10-30
Can we have an updated how to for this topic?
Its very interesting but i want to make sure.

---

### Post by Scimu on 2007-11-01
Thanks for this... There is also a script written in PHP called CastControl... This will let you change all the settings and add more Shoutcast Servers with that in the web browser. You would need apache, PHP and MySQL installed though.

---

### Post by Jenga201 on 2007-11-02
i found my problem about the no xml support error.

sudo apt-get install libxml2

recompile ices, and make sure XML [YES] is at the end of the configure

---

### Post by Siph0n on 2007-11-20
Hey! I was having some problems and questions about setting an icecast server up. I googled and found [http://www.gnuware.com/icecast/unofficial/index.html](http://www.gnuware.com/icecast/unofficial/index.html) . It looks pretty detailed! It might help some other people out! Good luck...

---

### Post by myharshdesigner on 2007-11-21
cool thanks :)

---

### Post by ppihus on 2007-12-13
Hi!

Everything worked very well :) But I don't like the fact that it takes songs from a playlist, is there a way that I could stream my audio card's input or output?

---

### Post by icindr13 on 2010-03-22
Resolving [www.shoutcast.com](www.shoutcast.com)... 207.200.100.5
Connecting to [www.shoutcast.com|207.200.100.5|:80](www.shoutcast.com|207.200.100.5|:80)... connected.
HTTP request sent, awaiting response... 404 /shoutcast/downloads/sc1-9-5/shoutcast-1-9-5-linux-glibc6.tar.gz
2010-03-22 14:18:52 ERROR 404: /shoutcast/downloads/sc1-9-5/shoutcast-1-9-5-linux-glibc6.tar.gz.

---

