---
title: "HOWTO: Set up SHOUTcast-server at home and Internet DJ Console"
date: 2007-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Eazy© on 2007-06-30
[COLOR="Red"]**For Kubuntu Feisty.**[/COLOR] Might work on Ubuntu as well.

I always wanted to set up a shout cast to be able to share my music, and have the possibility to change the song I broadcast whenever I want. As I understand, most of the applications available only let you share a play-list. I googled some, and found [Internet DJ Console]("http://www.onlymeok.nildram.co.uk/") that would let you stream music to a simple SHOUTcast. It also let you change songs whenever I wanted. I was surprised how easy it was to set up, both the SHOUTcast-server and Internet DJ Console. Thought I share how I did it even if it's easy to figure out by yourself. I don't think I will be able to help much if this don't work for you as I am a noob even after 2 years of using linux (guess I'm slow;)).

[COLOR="Red"]**SHOUTcast-server:**[/COLOR]
Download it [here]("http://www.shoutcast.com/downloads/sc1-9-8/sc_serv_1.9.8_Linux.tar.gz") decompress it to a location of your choice and move to that location. You might want to make a folder to decompress them to. Now we need to change some settings in the sc_serv.conf. Every settings here is well explained, but the settings I changed is these:
```
; ***************************
; Required stuff
; ***************************
Password: *****   	I don't tell you mine ;)

MaxUser=20  		Set as high as your connection can handle

PortBase=8000	[COLOR="Red"]I did not changed this, but you need to open this port in your [/COLOR]router/firewall.

; ***************************
; Network configuration
; ***************************

SrcIP=127.0.0.1

```
This is all I changed. Save and close. Now lets test if it works. Open a console an cd to the directory where you decompressed the server files and run ./sc_serv Hopefully it will start nicely. You might want to make a short cut to the server to make it more easy to start it.

[COLOR="Red"]**Internet DJ Console:**[/COLOR]
This you will find in the repository. Open a console and do (or install it from Synaptic):
```
sudo apt-get install idjc libxine-extracodecs
```
After it is installed, in a console do:
```
echo "/usr/bin/jackd -d alsa -r 44100" >~/.jackdrc
```
it will start jackd when Internet DJ console starts. Start it (you will probably find it in KDE/Gnome menu) and Click on Server (Radio Server).

Under "Connection" set this:
In "Type:" select Shoutcast
In "Host:" localhost
In "Port:" 8000
in "pass" the password you picked in sc_serv.conf

Under Encoding:
in "Format" I have mp3 (ogg will work too I guess)
in "Bitrate" I have 192 (the higher you set this, the delay to the clients will be less, but also hog more bandwidth.)
I ticked the box Stereo.

Under "Stream Info" it is your choice. I only have "DJ Name: Eazy" Rest I have blank.

Connect to your SHOUTcast-server by clicking on the "Server Connect"-button, then close "Radio Server"-window. Only thing left is to add some music to the play lists, start a song, and lastly click on "Stream"-button.

The address ppl will need to be able to connect to your SHOUTcast is: [http://your.external.IP:8000/listen.pls](http://your.external.IP:8000/listen.pls)


**[COLOR="Blue"][SIZE="3"]Alternative to Internet DJ Console[/SIZE][/COLOR]**

The few ppl that have tested my howto reports they have problems with the sound (probably jack that is acting up), so I tried to find a different solution and I found LiveIce. It is a plugin to Xmms which I have tried before, but I could never make it work until now. Here is what I did:
```
sudo apt-get install xmms-liveice
```
Start xmms and press Ctrl + P.
Click on the second tab from the left.  Select "LiveIce 1.0.0" and click on configure.
The settings I have there:

[COLOR="Green"]**In the tab Audio Format**[/COLOR]
[COLOR="DarkOrange"]
Audio Format:[/COLOR]
Sample Rate (Hz): 44100
Number Of Channels: Stereo
Stream Bitrate (bps): 64000

[COLOR="DarkOrange"]Encoder:[/COLOR]
Encoder Type: Lame (3.21 and above)
Executable name: /usr/bin/lame

[COLOR="Green"]**Description tab:**[/COLOR] 
Its your choice I guess.

[COLOR="Green"]**In the tab Server**[/COLOR]

[COLOR="DarkOrange"]Server Location:[/COLOR]
Server Address: localhost
Server Port: 8001 (yes needs to be 8001 even though your server is set to 8000, its a bug.)
Encoder Password: pass to the shoutcast server

[COLOR="DarkOrange"]Extra Icecast Only Features:[/COLOR]
Unselect  Use X-Audiocast Headers
Unselect Enable Icecast Title Data
Stream Mountpoint: listen.pls (don't know if this is needed to be this, but there probably has to be something here)
Remote Dumpfile I have unselected.

Now click ok (twice) and close Xmms. Start your shoutcast-server and then start Xmms. Now you should be ready to shout.
The address ppl need to connect is [http://IP:8000](http://IP:8000)

Happy Shouting!!

If you got suggestions to this howto, please tell them so I can improve it.

---

### Post by drytear on 2007-07-14
what libs does it need to stream and play mp3? cause mine isn't working, it connects to the server but when i click on stream the idjc stop workin, i tried it without streaming ... and it doesn't even play the mp3.

---

### Post by Eazy© on 2007-07-14
try in console: 
```
sudo apt-get install libmad0 lame
```

Please respond to this if it works so I can add it to my howto. Guess I had mp3-support working before I installed idjc.

Edit:
Here are a dependency list: [http://www.onlymeok.nildram.co.uk/download.html](http://www.onlymeok.nildram.co.uk/download.html) both optional and required. Also, here are a howto to get multimedia support: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

---

### Post by drytear on 2007-07-14
still dunno what's wrong with it, i already had lame and libmad installed the first time, i installed now the gstreamer-lame .. but still not working. when i press play it jumps from one song to another until it finishes the playlist but doesn't play any of them. any other ideas? :)

---

### Post by Eazy© on 2007-07-14
Are you running Ubuntu or Kubuntu? If you run Kubuntu you can try with:
```
sudo apt-get install libxine-extracodecs
```

---

### Post by drytear on 2007-07-14
ubuntu 7.04 :)

---

### Post by Eazy© on 2007-07-14
Can you even play mp3's in xmms or some other player? 

I edited post #3...forgot to put the link to the dependency list. You might want to try to install some of the recommended/optional. 

As I said in the howto, I'm not very good at linux, so If you don't get this working I'm hoping some other might have a solution for you.

---

### Post by drytear on 2007-07-14
yeah mp3 works in xmms, but xmms uses the alsa plugin for output, idjc uses jackd, maybe that's the problem. Anyway thanks for the suggestions. :)

---

### Post by Eazy© on 2007-07-14
I have libjack0.100.0-0 and libjack0.100.0-dev installed. Try to install them if you don't got them.

```
sudo apt-get install libjack0.100.0-0 libjack0.100.0-dev
```

---

### Post by drytear on 2007-07-15
it works now, i mean i can hear sound but the sound isn't smooth like normal playback , it interrupts very often. what could it be now ?

The problem before were the xine extracodecs, idjc uses xine as the encoder. So , include that in the how-to.

---

### Post by Eazy© on 2007-07-15
I think the problem with interrupts is jack. Check here:[http://www.onlymeok.nildram.co.uk/realtime.html](http://www.onlymeok.nildram.co.uk/realtime.html)

Before you recompile your kernel ;) try this in a console:
```
echo "/usr/bin/jackd -d alsa -r 44100 -p 2048" >~/.jackdrc
```

I really don't know if it will help.

---

### Post by drytear on 2007-07-16
did you have to recompile the kernel on your system? or did it work fine the first time?

---

### Post by Eazy© on 2007-07-16
I always compile my own kernel, but I did not compile it for idjc in mind. I don't know if those required options to make idjc work was already applied in xconfig when I compiled my kernel. If you want to compile your own kernel, here is a good howto for it (Its easy :)) : [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

The kernel I compiled was 2.6.20.3, so it was some time ago. I did not see any improvement in 2.6.22.1 (the newest kernel available) when I tested it, so I went back to my 2.6.20.3-kernel (for other reasons).

If compiling a kernel is required to make idjc to work, I will request to have this howto removed. Its to much hassle for a small thing like idjc, and is not what I had in mind when I wrote this howto.

---

### Post by drytear on 2007-07-16
isn't there a way to make it use alsa instead so we get rid of the priority problem with jack ?

---

### Post by flugheim on 2007-07-19
I have the same problem as drytear, is there another tool to use as a "song-manager"?

---

### Post by Eazy© on 2007-07-20
I have sent a email to the creator of idjc, and hopfully he resond here about the problem you have. I'm sorry that I cant help you further, so I'm hoping he will respond :)

Btw. what soundcard do you have? I have a Sondblaster Live 5.1 Digital wich have HW-mixing

---

### Post by flugheim on 2007-07-20
Im not good with hardware, but i think this is the name of the card: Intel 82801DB-IHC4, i dont know anything about the specs ;)

---

### Post by Eazy© on 2007-07-22
Added the howto (Xmms-plugin) I wrote in this post to the howto.

---

### Post by eskuge on 2007-08-09
The liveice plugins works fine. Thx Eazy.

Btw anyone gotten the internetDJConsole to work? It just connects and disconnects again on my Ubuntu Feisty.

---

### Post by freshspinach on 2007-08-15
"Open a console an cd to the directory where you decompressed the server files and run ./sc_serv Hopefully it will start nicely. You might want to make a short cut to the server to make it more easy to start it."

I'm very new to Linux. How do I make a shortcut to the server and place it on my desktop? I'm using Ubuntu Feisty.

Thanks for the HowTo. It's been a big help. Being able to set up my web radio station is one of the only things keeping me from switching completely over to the Linux side.

---

### Post by Eazy© on 2007-08-15
Are you using Ubuntu (Gnome) or Kubuntu (KDE)?

---

### Post by freshspinach on 2007-08-15
I'm using Ubuntu Feisty (Gnome).

---

### Post by Eazy© on 2007-08-15
I googled som and found this:
[http://www.unix-tutorials.com/go.php?id=921](http://www.unix-tutorials.com/go.php?id=921)

I Use Kubuntu with KDE so I only know how to do it in KDE. Hope this helps.

---

### Post by freshspinach on 2007-08-25
I'm having trouble getting IDJC to connect to my SHOUTcast server. IDJC is playing with the stream button down and I have all the proper server info filled out. However, when I press 'Server Connect' I get an error saying 'The connection to the radio server failed'. 

Checking the SHOUTcast logs shows that: 

<08/25/07@00:43:01> [source] connected from 127.0.0.1      
<08/25/07@00:43:01> [source] icy-name:freshSPINACHradio
<08/25/07@00:43:01> [source] icy-pub:0 ; icy-br:48 ; icy-url:[http://www.freshspinach.com:8000/listen.pls](http://www.freshspinach.com:8000/listen.pls)
<08/25/07@00:43:01> [source] icy-irc: ; icy-icq: ; icy-aim:
<08/25/07@00:43:01> [source] source dropped connection. disconnecting.
<08/25/07@00:43:20> [sleeping] 0 listeners (0 unique) 

I have also forwarded the correct port on my router.

---

### Post by halitech on 2007-10-20
I'm having the same problem with IDJC, I can connect but then get a connection dropped window after about 30 seconds. I have the stream button pressed but nothing comes through. I know my shoutcast server is working as I can connect from a windows box using Winamp and the plugin.

Any ideas?

---

### Post by YaroMan86 on 2008-03-06
I am having trouble. I got everything set up... except when set to shoutcast mode, it disables my connect to server button. What do I do?

---

### Post by PinkFloyd102489 on 2008-03-06
I keep getting an invalid password error when trying to stream from LiveIce on my desktop over to Shoutcast on my server.

I know for a fact that the passwords are the same, in the conf and in LiveIce. Any idea?

---

### Post by PinkFloyd102489 on 2008-03-07
Ok I got it to connect but I cant figure out for the life of me how to get songs to add in to the the playlist. I dont know if this is a GNOME problem that it's not displaying or what. I click the Add File button at the top and select the mp3 file but it does nothing after I hit Ok

Anyone have tips?

---

### Post by Eazy© on 2008-03-07
It seems that it is a bit buggy to add song in idjc. Best way to add songs is to make a play list with some other media-player and save it as a .m3u (I use Amarok). Then right-click in idcj's play list window and then add the .m3u-play list. That works for me.

---

### Post by 888mafia on 2008-03-07
> **Eazy© said:**
> [COLOR="Red"]**For Kubuntu Feisty.**[/COLOR] Might work on Ubuntu as well.

I always wanted to set up a shout cast to be able to share my music, and have the possibility to change the song I broadcast whenever I want.

This is exactly what i have been posting about all over theses forums i cant seem to get it done . Again i am a true beginner.  
 
I own a poker forum that is hosted by a company and wont allow steraming audio because of bandwith .

All i want to do is broadcast the games.  
To my under standing it  would be best for a radio station to have its own server to stream
 I have downloaded (Gutsy Gibson ) 7.1 server is this the right choice? If not what do you think i should use?

The server im trying to set up will be for this only 

I am willing to pay you to help me get this set up and running but i guess if your interested you should pm me  i really need the help

---

### Post by Eazy© on 2008-03-07
Just install the normal Kubuntu/Ubuntu. There is no need for a special edition.  I'm not sure what you want to do, but I guess that you want to talk in a microphone, live, and have pause music played with mp3. I think you can manage that with [Idjc]("http://www.onlymeok.nildram.co.uk/") You need to read on that homepage! You will need the shout cast-server as I explained in my howto. If you just follow it, I think it will work. I have never tested to broadcast with a microphone, so I'm not sure how/If it works (remember, I am a noob as well :))

---

### Post by dimas869 on 2008-04-12
i get this...maybe something else is running but i dont know how to terminate it.

** SHOUTcast Distributed Network Audio Server
** Copyright (C) 1998-2004 Nullsoft, Inc.  All Rights Reserved.
** Use "sc_serv filename.ini" to specify an ini file.
*******************************************************************************

Event log:
<04/12/08@12:24:09> [SHOUTcast] DNAS/Linux v1.9.8 (Feb 28 2007) starting up...
<04/12/08@12:24:09> [main] pid: 6068
<04/12/08@12:24:09> [main] loaded config from sc_serv.conf
<04/12/08@12:24:09> [main] initializing (usermax:32 portbase:8000)...
<04/12/08@12:24:09> [main] No ban file found (sc_serv.ban)
<04/12/08@12:24:09> [main] No rip file found (sc_serv.rip)
<04/12/08@12:24:09> [main] opening source socket
<04/12/08@12:24:09> [main] source thread starting
<04/12/08@12:24:09> [main] opening client socket
<04/12/08@12:24:09> [main] error opening client socket! FATAL ERROR! Some other process is using this port!

---

### Post by chadwick359 on 2008-04-13
Make sure that the sc_serv process isn't already running, try pulling up the gnome system monitor and killing the process manually, sounds to me like you still have it running from a previous attempt.

---

### Post by dimas869 on 2008-04-19
ok...i have it up a running properly...but i am experiencing two issues, i can't get to terminate the server...i try TERM or contrl c and the server keep on and the other issues is that the buffering is very slow and people tent to get disconnected very quick...any suggestion?

---

### Post by dimas869 on 2008-05-16
hey, i did upgrade ubuntu and reinstall IDJ Console but when i choice shoutcast the "connect" botton to the server go Grey...whats wrong?...any idea?

---

### Post by PinkFloyd102489 on 2008-05-17
It's because the settings are incorrect. Maximize IDJC's window and scroll through the settings. It's probably set on the OGG tab, which needs to be switched to mp3. If the mp3 tab doesnt exist, install the attached deb file. I built it from the latest source which has everything fixed.

---

### Post by dimas869 on 2008-05-21
working just perfect!

---

### Post by Krasauskas on 2008-06-01
I can't start my idjc after I installed the attachment. That is what I got in alsa session shell:

unknown destination port in attempted connection [idjc-sc:lt_in]
unknown destination port in attempted connection [idjc-sc:rt_in]


**** alsa_pcm: xrun of at least 134.857 msecs

unknown destination port in attempted connection [idjc-sc:lt_in]
unknown destination port in attempted connection [idjc-sc:rt_in]
unknown destination port in attempted connection [idjc-sc:lt_in]
unknown destination port in attempted connection [idjc-sc:rt_in]
unknown destination port in attempted connection [idjc-sc:lt_in]
unknown destination port in attempted connection [idjc-sc:rt_in]

Also, when launching it through terminal, I get this:

/usr/local/libexec/idjcsourceclient: error while loading shared libraries: libmp3lame.so.0: cannot open shared object file: No such file or directory
unexpected reply from idjcsourceclient
idjc: the server module appears to have crashed -- possible segfault
hyphen@hyphen-desktop:~$ Mixer module has closed

Any ideas?

---

### Post by PinkFloyd102489 on 2008-06-01
Those are JACK errors. Version 0.7.6 has everything fixed plus a few performance upgrades. It still skips on mine a bit but only when I switch windows and stuff like that, the skipping doesnt send to the server though. Im running IDJC on a 450Mhz Pentium 3 with 512MB RAM so that's probably why.

I havent tested Skype with it but that'll probably be my next venture.

---

### Post by PlayEdUdE on 2008-11-21
when i goto server settings i get this error [IMG]http://static3.filefront.com/images/personal/e/EdUdEToD/26414/pofxufvwyt.jpg[/IMG]

can somebody tell me why mp3 streaming is unavailable?

---

### Post by kopilo on 2008-11-22
I'm not sure exactly why it is unavailable, however I would recommend attempting to compile from source before playing with anything else.. I just compiled on the latest Xubuntu and everything worked fine.

Instructions on how to compile from source here: [http://ubuntuforums.org/showthread.php?p=5200135&highlight=idjc#post5200135](http://ubuntuforums.org/showthread.php?p=5200135&highlight=idjc#post5200135)

---

### Post by da_velos_code on 2009-04-11
Hi all,

I have installed **[COLOR="Blue"]IDJC[/COLOR]** however in Server->Connection->Type the Shoutcast choice is not available to check. The only choice is Icecast 2.
I have installed *[COLOR="Blue"]sc_serv_1.9.8_Linux.tar.gz[/COLOR]* and it's running normally.
Any ideas about how to overcome this?

Thanks in advance
dvc

---

### Post by Kenchappagoudra on 2009-12-14
Hello Folks,

  I have successfully installed latest version of IDJC and it is working great. Also, Jack is also working great. But, I have problems running IDJC continuously. I have static IP address and fixed the internal IP address. When I start IDJC, it runs fine and I could successfully broadcast my songs. After couple of hours, IDJC disconnects because shoutcast server can't find the destination server. I don't know why it happens. When I checked system Log. I see a kernal error message as follows. 

  [COMPUTER NAME] Kernel : idjcsourceclien[n]: segfault eip [HEXNUMBER] esp [HEXNUMBER] error [n]


Usually, IDJC is ok if I have atleast 1 listner, otherwise shoutcast server goes to sleep causing IDJC to crash. But, even if I have one listener all the time, shoutcast server diconnects after streaming couple of hours.

Anybody knows what is causing this error? 

Thank you

-Kenc

---

### Post by fatleader on 2010-02-02
Hello, 
I have set everything up following the tutorial, but it seems like people have problem connecting to the stream. I give them the link 

[http://189.149.124.96:8000/listen.pls](http://189.149.124.96:8000/listen.pls)[B]

but they are still not able to connect. 

sorry haha, I am a complete noob. 
any suggestions of what happened?
[/B]

---

### Post by silameth on 2011-05-05
I have a question I hope I can get answered here.
My IDJC and Jack run fine as well as my SC_serv. But I want to use mic port and my bluetooth headset mic so 2 people can kind of do a talkshow kind of thing, but when I push either mic button they both use the mic port. What would I need to do to say use mic2 with the bluetooth?

---

