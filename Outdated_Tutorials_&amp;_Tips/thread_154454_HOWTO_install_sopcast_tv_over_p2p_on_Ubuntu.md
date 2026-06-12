---
title: "HOWTO install sopcast tv over p2p on Ubuntu"
date: 2006-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by jude999 on 2006-04-03
[B][COLOR="Red"]**** Do not try the following, it does not work anymore ****
**** I will update when I have tried the new program ****[/COLOR][/B]

Hi all,
I will explain here how to install sopcast on your ubuntu box
This thread also has a purpose of improving the installation process... and maybe the program.

**Background**

I started this whole thing coz i'm French, I live in China, and I needed a way to watch French football games live on my laptop at home.
If you have winxp, no problem, there are 4 or 5 p2p programs that do that, but I only run Breezy at home, so had to find a solution... 
I came here first, nothing. I googled a little and found out some chinese websites (most tv over p2p progs are chinese). after a while, I found out that a linux version of sopcast had been developped, but still in it's early stages. I found 2 different howto that helped me, both in french, both not really suiting my needs... This will be a mix of both.

I am still kinda noob to linux, swiched just over a year ago, please correct me if I write stupid things, this is my 1st howto.

**Websites**

The official program website: 
[http://www.sopcast.org]("http://www.sopcast.org")

the 2 websites I used as reference (in French):
[http://pascal.vmfacility.fr/wiki/HomePage/linux/sopcast]("http://pascal.vmfacility.fr/wiki/HomePage/linux/sopcast")
[http://rimarchives.free.fr/sopcast2.htm]("http://rimarchives.free.fr/sopcast2.htm")

**Requirements**

mplayer
alien
fakeroot

**Installation**

1/ Install fakeroot and alien:

Fakeroot and alien will be needed during the installation to turn a rpm into a deb. Hopefully we will soon be able to skip this process.

```
$ sudo apt-get install fakeroot alien
```

2/ Create a sopcast folder

I put this in /home/yourname/sopcast

3/ Download the sopcast rpm in the newly created sopcast folder

Download the rpm [here]("http://www.magiclinux.org/people/sejishikong/sopcast-0.2-9mgc.src.rpm") and save it to /home/yourname/sopcast

4/ Change the rpm package to a deb package

```
$ cd /home/yourname/sopcast
$ fakeroot alien -d sopcast-0.2-9mgc.src.rpm
sopcast_0.2-10_i386.deb generated 
```

*If somebody has a place to host the deb package so we can skip the last step, please say so and give me a link to the file so I can update the howto.*

5/ Extract the deb package **(do not install!)**

```
$ dpkg -x sopcast_0.2-10_i386.deb .
```

6/ Play a channel

go to the channel page on sopcast: [http://www.sopcast.org/channel/]("http://www.sopcast.org/channel/")

copy the link of the channel you want to watch, for example, espn:
sop://broker.sopcast.org:3919/official/espn

in a terminal, type:
```
/home/yourname/sopcast/sp-sc sop:sop://broker.sopcast.org:3919/official/espn 8900 8800
```

Wait for around 15 seconds, open mplayer, go to play location and play: [http://localhost:8800](http://localhost:8800)

That should make it.


There is a gui somewhere, but I figured I didn't need it as this works ok, so I hav not tried it.
I usualy experience some lag on the image, but I have a lousy connection. Please give feedback with a better than 1Mb connection.
I will try to update this when new things come up, I will follow closely new developments.
Help and advice on how to make it work better would be appreciated.

---

### Post by meth on 2006-06-13
I have made all steps, but when i type:
```

 ./sp-sc sop://broker.sopcast.org:3919/official/cctv5 8900 8800

```
I get an error:
```

(null):(null):sop://broker.sopcast.org:3919/official/cctv5
url=sop://broker.sopcast.org:3919/official/cctv5
resourceID=ab34
localaddr:      a0a5717:8900
sio_broker closed
sio_broker closed
sply->SEDNDDDDDDDDDDDDDDDDDDD 0:0
RECV len=95
sio_broker closed
sio_broker closed
        spsc_cleanup

```

And i cant see anything

---

### Post by jude999 on 2006-06-14
The Sopcast people have changed everything since the version I explained higher. I was unable to use it (or any other program) for the past 2-3 months, but just found a way that I have to try.
Check it here: [http://phpbbstar.com/freesoccer-about822.html]("http://phpbbstar.com/freesoccer-about822.html")
I'll give more details when I have tried it in a few days.

---

### Post by declaration on 2006-09-09
any chance of an update to this howto?

much appreciated if there is.

---

### Post by leexiangwen on 2006-11-11
finally manage to figure out how to do this trick ...

open a terminal, print

```
sp-sc sop://211.152.34.35:3912/6002 8908 8909
```

where 6002 is the channel number you found in the official channel list
[http://www.sopcast.com/channel/](http://www.sopcast.com/channel/)
8908 is the connection port with the server, 8909 is the port for the player.

after this you should see lots of text message in the terminal.

open another terminal, or open your media player( mplayer for instance)

```
mplayer [http://localhost:8909](http://localhost:8909)
```

now wait half a minute and enjoy!

---

### Post by oyvindaa on 2007-01-24
So, how's the support for SopCast on Dapper these days?

---

### Post by tombott on 2007-03-13
A new version of Sopcast has been released.

A updated DEB can be found [here]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb")

Save it, right click and 'Open with GDebi Package Installer'

Works a treat on Edgy. Will put icon in Sound & Video Menu

Regards,

Tom

---

### Post by TURNER on 2007-03-16
Hi, 

I downloaded and installed the sopcast deb [[COLOR=Navy]here[/COLOR]]("http://http://dengpeng.name/blog/2006/12/07/gsopcast/") 

I first attempted running sopcast from the terminal using ```
 gsopcast 
``` this obviously lauched the gui, immediatly listing channels, having clicked on a channel it immediatly buffered, and seemed to be working.

Next step, media player, having googled I located this thread, and took the recommendation to download and install mplayer, from synaptic, I then attempted to have mplayer play from a url and entered [http://localhost:8800](http://localhost:8800) into the relevant field, and nothing!

Next I attempted ```
sp-sc sop://211.152.34.35:3912/6002 8908 8909
``` which sent my terminal in a flurry, and also kicked up the following error:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=27577&stc=1&d=1174079583[/IMG]

My Terminal is still going mad printing code, heres an example

```
speer_msg_exchange_block_info blockStart=3034431, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034431, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034431, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034431, nblockAvailable=100
I START = 0
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=98
hook_sc_accept:MSG_CONNECT


speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=98
I START = 0
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=99
I START = 0
PUT_BLOCK_DATAAAAAAA
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=100
GLOBAL uploadRate=8745  upSum=18341786
I START = 0
PUT_BLOCK_DATAAAAAAA
I START = 0
Re--------------------29/2053
I START = 0
speer_msg_exchange_block_info blockStart=3034433, nblockAvailable=100
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=98
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=98
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=98
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=98
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=98
I START = 72
GLOBAL downloadRate=59926       dnSum=47096645
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=3034435, nblockAvailable=99
speer_msg_exchange_block_info blockStart=30
```

Hardware: ATI Raedon 7500
Anyone able to help an exiled Englishman get to watch Rugby tomorrow??

---

### Post by TURNER on 2007-03-17
ok problem somehow solved...

After tinkering around last night, installing plugins so that mplayer could play in firefox I fired up my pc this morning and bang, working sopcast with a full colour picture, behaviour doesnt seem logical but I am not going to complain :) 

only downside; Ive just wasted an entire day watching football :KS

---

### Post by Headspin on 2007-03-19
Wow.. the new Sopcast is excellent!!   

I had the old one working but it was kinda all over the place. This installs great!

:)

---

### Post by pt123 on 2007-03-24
Does gsopcast take in path parameters like the windows version.
Because I am trying to get it to open the channels from a webpage through firefox.

But it just opens gsopcast, than opening the channel.

---

### Post by tombott on 2007-05-17
I've updated the link to Sopcast in my original post as the URL had moved.

It can be found [here]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb")

---

### Post by tombott on 2007-05-17
> **pt123 said:**
> Does gsopcast take in path parameters like the windows version.
Because I am trying to get it to open the channels from a webpage through firefox.

But it just opens gsopcast, than opening the channel.

I tend to copy the link from FireFox, then open SopCast and paste into the box at the bottom then click Launch.

[IMG]http://www.worldcup-tv.co.uk/images/SopCast1.png[/IMG]

I'll post again if I can work out how to get Firefox to do this for you.

Tom.

---

### Post by Seandq on 2007-07-08
> **tombott said:**
> I tend to copy the link from FireFox, then open SopCast and paste into the box at the bottom then click Launch.

[IMG]http://www.worldcup-tv.co.uk/images/SopCast1.png[/IMG]

I'll post again if I can work out how to get Firefox to do this for you.

Tom.

Not to raise the dead, but I can't do this in any version of Gsopcast. I downgraded to 2.10 and it didn't work and i downgraded further to 2.8 and it didn't work.

I'd like to know this so I won't have to go to some streams from Wine.

---

### Post by lazyron on 2007-08-26
I was using 0.2.8 and after having not used it a while I wanted to watch some MLS. Sopcast loaded fine and seemed to be pulling down the stream, but mplayer would not launch.

Some Google searches later, I ran across this:

[http://dengpeng.name/blog/2007/06/25/how-to-compile-lastest-gsopcast-via-subversion/](http://dengpeng.name/blog/2007/06/25/how-to-compile-lastest-gsopcast-via-subversion/)

I tried to install via SVN, but it was a PITA and ended up with some compile errors. If I had read down a bit further, I would have found the .deb just waiting for me.

[http://dengpeng.name/upload/gsopcast_0.3.1svn20070625-1_i386.deb](http://dengpeng.name/upload/gsopcast_0.3.1svn20070625-1_i386.deb)

So there you have it folks, new version available... and the Colorado Rapids just scored on LA Galaxy.

Bend it like who?

---

### Post by pt123 on 2007-09-15
Thanks for posting this

---

### Post by Morbett on 2007-09-19
> **lazyron said:**
> I was using 0.2.8 and after having not used it a while I wanted to watch some MLS. Sopcast loaded fine and seemed to be pulling down the stream, but mplayer would not launch.

Some Google searches later, I ran across this:

[http://dengpeng.name/blog/2007/06/25/how-to-compile-lastest-gsopcast-via-subversion/](http://dengpeng.name/blog/2007/06/25/how-to-compile-lastest-gsopcast-via-subversion/)

I tried to install via SVN, but it was a PITA and ended up with some compile errors. If I had read down a bit further, I would have found the .deb just waiting for me.

[http://dengpeng.name/upload/gsopcast_0.3.1svn20070625-1_i386.deb](http://dengpeng.name/upload/gsopcast_0.3.1svn20070625-1_i386.deb)

So there you have it folks, new version available... and the Colorado Rapids just scored on LA Galaxy.

Bend it like who?

Just downloaded that deb and installed it in Feisty.  When I open gsopcast, it stays open for about 20 seconds or so then closes the program every time.  Do I need to have some other package installed or something?

---

### Post by tombott on 2007-09-20
> **Morbett said:**
> Just downloaded that deb and installed it in Feisty.  When I open gsopcast, it stays open for about 20 seconds or so then closes the program every time.  Do I need to have some other package installed or something?

I get exactly the same problem.
I already had Sopcast installed.
I am removed this version and am going to re-install the previous version.

---

### Post by tombott on 2007-09-20
Ok I have got mine working by doing the following:

Navigate to usr\local\bin 
Delete Sopcast

Download Sopcast 2.8.1 from [here]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb")

Select Reinstall package

Sopcast now loads again and works without any problems.

---

### Post by Morbett on 2007-09-21
> **tombott said:**
> Ok I have got mine working by doing the following:

Navigate to usr\local\bin 
Delete Sopcast

Download Sopcast 2.8.1 from [here]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb")

Select Reinstall package

Sopcast now loads again and works without any problems.

Thanks so much, this worked perfectly.

Do you have a preference for which program you use for viewing?  The default in config reads: "mplayer -ontop -geometry 100%:100%". 

 I also have VLC and movie player installed.  What do you use?  What do recommend I put in the config section for the player?  (Mostly watching sports)

When I use the default mplayer and maximize the window, the image quality is choppy.

---

### Post by Morbett on 2007-09-22
Help!

Sopcast no longer crashed upon opening, but when I paste a sop address next to the launch button and then press launch, it closes right away.  I can watch normal channels that pop up in the list, but not ones I paste in there.

Any ideas? Thanks!

---

### Post by ingo on 2007-09-23
Yep, same thing happens to me :confused:

I've tried some command line options but that is only a case of copy and paste since I don't know what I am doing.

HELP:lolflag:

---

### Post by blueorder on 2007-09-23
Yup, I seg fault also with 0.2.8 and 0.3.1

---

### Post by Morbett on 2007-09-24
Has any progress been made with this problem?  :confused:

---

### Post by pt123 on 2007-09-29
I started to get seg fault error on .281, so I upgraded to .31 and still got it. 

Then I completely removed the sopcast using synaptic and reinstalled .281 and everything is fine now.

---

### Post by Morbett on 2007-10-02
Where can I download the .deb for version .31 ?

Still trying to fix this glitch where it crashes after pasting and launching an adress.....

---

### Post by matteospqr on 2007-10-02
Hello!
I was trying to install sopcast but I have an amd64 and all of the links above are for i386!!

What could I do?

---

### Post by begemot1 on 2007-10-08
> **tombott said:**
> I tend to copy the link from FireFox, then open SopCast and paste into the box at the bottom then click Launch.

[IMG]http://www.worldcup-tv.co.uk/images/SopCast1.png[/IMG]

I'll post again if I can work out how to get Firefox to do this for you.

Tom.

I'm afraid I can't quite figure this one out: Gsopcast (I have 2.8 ) doesn't _let_ me paste in the box at the bottom.  I can only paste in the search box up top which, when I click, apparently does nothing.

Any suggestions for a n00b?

---

### Post by tombott on 2007-10-08
You cannot type into that box.

You cannot click into the box and do Ctrl-V to paste.

You have to right click on box, you will then get the option to paste

[IMG]http://freetowatchtv.co.uk/images/ubuntu/gsopcast1.png[/IMG]

Once you have pasted click on Launch.

[IMG]http://freetowatchtv.co.uk/images/ubuntu/gsopcast2.png[/IMG]

---

### Post by begemot1 on 2007-10-08
> **tombott said:**
> You cannot type into that box.

You cannot click into the box and do Ctrl-V to paste.

You have to right click on box, you will then get the option to paste

Once you have pasted click on Launch.



Thanks for the quick reply, and sorry to have asked the same question in two different threads (hopefully I get n00bie forgiveness on this).

As I mentioned on the other thread, with your help I figured out how to do the pasting, but I now get a "segmentation fault" when I do this, which I'm not sure how to correct ...

---

### Post by tombott on 2007-10-08
See this [thread]("http://ubuntuforums.org/showthread.php?p=3497059#post3497059")

---

### Post by zhanglini on 2007-10-08
I downloaded and installed Sopcast 2.8.1.  But when I ran it all it does is the buffer going up to 100% and nothing else happened.
I have Window Media Player 6.4 installed under wine.  Do I miss anything?
Thanks

---

### Post by tombott on 2007-10-09
Why not install the Ubuntu version ?

[http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb)

Plenty of info in this thread to show you how it all works.

---

### Post by zhanglini on 2007-10-09
> **tombott said:**
> Why not install the Ubuntu version ?

[http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb)

Plenty of info in this thread to show you how it all works.

I will try that.
But first how do I uninstall the old one?  I couldn't find it on Synaptic or Ins/Uninstall....
Thanks

---

### Post by jpgv on 2007-10-15
> **tombott said:**
> Why not install the Ubuntu version ?

[http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb)

Plenty of info in this thread to show you how it all works.

Great!!  I had the same problem with the 0.2.10 version.  Uninstalled that, installed this package and started working just fine.

Thanks a lot!

---

### Post by sleep furious idea on 2007-10-28
(Warning: New user)

Well, I just reinstalled SOPCAST 2.8-1 and it seems to be working, ALMOST working that is!

It is buffering and I can get a stream of 95+ percent on some channels but the launch button won't launch MPLAYER.

Any tips?

I can record the stream and open MPLAYER and watch the recordings but I can't see the live streams.

Also, I tried Kaffine and got the same results.

Thanks in advance,
Sleep furious, idea.

---

### Post by pt123 on 2007-10-28
^ try running that command you have in gsopcast in a terminal with a file. See if mplayer opens, what you will usually find is that the video & audio out have not been set.

---

### Post by ingo on 2007-10-29
I installed 0.2.8.1 but I still get the segmentation fault whenever I click on "launch" - anybody else experiencing the same prob still?

Mind, I'm on Debian Etch...

---

### Post by sleep furious idea on 2007-10-30
Sorry, can't help with that.
I'm still having troubles "launching" kaffeine.
I can stream, record, watch recordings but I can't figure out how to watch the live stream.

It would be great if somebody give a (really) basic step by step of how to get either Kaffeine or Totem Movie Player to launch from Sopcast.

Or I guess anyway to view Sopcast.

Thanks,

the sleep furious idea

---

### Post by Tom B on 2007-10-30
> **ingo said:**
> I installed 0.2.8.1 but I still get the segmentation fault whenever I click on "launch" - anybody else experiencing the same prob still?

Mind, I'm on Debian Etch...

I had that problem too, then I installed [qsopcast]("http://ubuntuforums.org/showpost.php?p=2648111&postcount=53") and it is working perfectly. (Except now I'm having trouble with sound in VLC, but that's another issue.)

---

### Post by ingo on 2007-10-31
> **Tom B said:**
> I had that problem too, then I installed [qsopcast]("http://ubuntuforums.org/showpost.php?p=2648111&postcount=53") and it is working perfectly. (Except now I'm having trouble with sound in VLC, but that's another issue.)
wow - it is working!!! I can now paste sop://broker... addresses into the bottom bit without getting segmentation faults (most of the time). 

When I first did it, nothing happened. After some 10 minutes or so I decided to click on "player" after I noticed that "record" was selected - doh! mplayer came up a treat :) This might also be the solution to one of the problems mentioned earlier (somebody who could do everything but watch - click on "player").

Soooo happy to be able to watch footy at last:guitar:
Thanks to all!

---

### Post by yoburtu on 2007-11-12
Hello,

is there a ubuntu 64 bits version of gsopcast package?.

Best regards.

---

### Post by h0me5k1n on 2007-11-24
EDITED THREAD BY h0me5k1n
FOLLOW TOMBOTTS INSTRUCTIONS IN POST 48 OF THIS THREAD

These instructions will install the GUI and then update the Sopcast executable to the latest version

# Get the sopcast GUI deb file
wget [http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb)
# Install the deb 
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb
# get the newest version of sopcast
wget [http://sopcast.referencias.tv/download/sp-auth.tgz](http://sopcast.referencias.tv/download/sp-auth.tgz)
# extract it
tar xzf sp-auth.tgz
# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc
# root should own the sp-sc executable - probably not required
chown root:root /usr/bin/sp-sc

To run it either type gsopcast at the commandline or select "applications" - "sound & video" then "Sopcast TV Player".  You need to wait a few seconds for the channel list to fill.  If you have any problems run gsopcast from a terminal and you can see any errors in the terminal output.

:popcorn:

---

### Post by h2z on 2007-11-24
```

Segmentation fault (core dumped)

```

This is what I get when trying to play a channel (not showing in the channel list as I changed that URL and lost the original so no list now) and when trying to play it with the command line option (sp-sc) :confused:

---

### Post by h2z on 2007-12-01
OK so I got it to work without segmentation faults :) What ports do I need to forward on my router (and firewall) to enable it incomming connections on it?

The official FAQ has this:

```

For SopClient, recommends open 3900-13900 ports for inbound connections.

```

But thats just silly I don't want to open so many ports! Isn't there a way to restrict it to maybe just a few ports? opening 10k ports doesn't sound very secure :(

---

### Post by vector on 2007-12-18
whats the latest on this package?

I tired the wget howto above and it dont work

wget [http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb)
--18:33:58--  [http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb)
           => `gtk-so...2.8-1_i386.deb'
Resolving linuxtoy.org... 208.113.198.67
Connecting to linuxtoy.org|208.113.198.67|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:34:09 ERROR 404: Not Found.

---

### Post by tombott on 2007-12-18
> **vector said:**
> whats the latest on this package?

I tired the wget howto above and it dont work

wget [http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb)
--18:33:58--  [http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-so...2.8-1_i386.deb)
           => `gtk-so...2.8-1_i386.deb'
Resolving linuxtoy.org... 208.113.198.67
Connecting to linuxtoy.org|208.113.198.67|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:34:09 ERROR 404: Not Found.

Try
wget [http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb)

*Note that the link is different from the displayed text*

Or just browse to via Firefox, download and install - [URL="http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb"]http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb
[/URL]

---

### Post by tombott on 2007-12-18
> **h0me5k1n said:**
> These instructions will install the GUI and then update the Sopcast executable to the latest version

# Get the sopcast GUI deb file
wget [http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb](http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb)
# Install the deb 
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb
# get the newest version of sopcast
wget [http://sopcast.referencias.tv/download/sp-auth.tgz](http://sopcast.referencias.tv/download/sp-auth.tgz)
# extract it
tar xzf sp-auth.tgz
# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc
# root should own the sp-sc executable - probably not required
chown root:root /usr/bin/sp-sc

To run it either type gsopcast at the commandline or select "applications" - "sound & video" then "Sopcast TV Player".  You need to wait a few seconds for the channel list to fill.  If you have any problems run gsopcast from a terminal and you can see any errors in the terminal output.

:popcorn:

Seems to be a problem with the second link, I have downloaded the latest release from Sopcast's site and upped to my server. This will be a quicker download for all  Europeans.
I have also added instructions for installing the QSopcast GUI.
QSopcast handles manually adding Sopcast channels much better than GSopcast, in my opinion.

This will install the latest version of Sopcast,  GSopcast GUI and the QSopcast Gui and set-up Firefox to open Sopcast Channels with Sopcast

# Get the GSopcast GUI deb file
wget [http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb](http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb)
# Install the deb
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb
# get the newest version of sopcast
wget [http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz](http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz)
# extract it
tar xzf sp-auth.tgz
# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc
# root should own the sp-sc executable - probably not required
sudo chown root:root /usr/bin/sp-sc

#Download the QSopcast GUI and Extract
wget [http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz](http://freetowatchtv.co.uk/images/ubuntu/qsopcast.tar.gz)
tar xzf qsopcast.tar.gz
#Copy to /usr/bin and change ownership
sudo cp qsopcast /usr/bin/
sudo chown root:root /usr/bin/qsopcast
#Create shortcut to qsopcast
sudo gedit /usr/share/applications/qsopcast.desktop

Enter the following into the blank text document, then save and close

[Desktop Entry]
Name=QSopcast
Comment=Sopcast TV Player
Exec=/usr/bin/qsopcast
Icon=/usr/share/pixmaps/gsopcast.xpm
Terminal=false
Type=Application
Categories=Application;AudioVideo;

You should now have QSopcast and Sopcast TV Player icons under Sound & Video in your menu.

I find that QScopast is much better if you want to manually add in sopcast channels.

To get Firefox to open Sopcast links with QSopcast do the following:

Go into firefox and enter URL: "about:config".
 Right click, select new and string. 

Set string name to:
*network.protocol-handler.app.sop*

Set value to:
*qsopcast*

Now when clicking on a Sopcast url (from [http://www.myp2p.eu/]("http://www.myp2p.eu/") for example) Qsopcast should launch

If you prefer to use GSopcast follow the above steps but substitute *qscopast* with *gsopcast*

Some people will also need to install the following (If you don't already have and KDE applications installed)

sudo apt-get install qt3-apps-dev vlc build-essential

sudo apt-get install libqt3-mt

Thanks to h0me5k1n

Tom.

---

### Post by wataboutbob on 2008-01-05
@tombott

thanks for the instruction. and yes, QSopcast does seem better than gsopcast.

---

### Post by maxxum on 2008-01-16
tombott, your instructions worked like a charm! many thanks!

---

### Post by h0me5k1n on 2008-01-18
NIce one Tombott - I've edited my post directing people to your instructions.

I'm not using the sopcast desktop GUIs anymore - I'm controlling it on a headless server using a http web interface which I created.

---

### Post by yeev on 2008-01-22
i need help guys:(
[http://ubuntuforums.org/showthread.php?t=608175&highlight=sopcast](http://ubuntuforums.org/showthread.php?t=608175&highlight=sopcast)

---

### Post by ryukent on 2008-02-23
Please see:

[http://ubuntuforums.org/showthread.php?t=703409](http://ubuntuforums.org/showthread.php?t=703409)

For a guide to install sopcast, the gui and setup firefox sop:// links

---

### Post by pt123 on 2008-02-23
Thanks the channel list on sopcast is down quite often, this would help by pass it.

---

### Post by tombott on 2008-03-29
I have now added more instructions to setup Firefox URL links etc.
Thanks to ryukent for his guide on this.

---

### Post by pt123 on 2008-03-29
gtk-sopcast_0.2.8-1_i386 is working fine on Hardy

---

### Post by Tmorr034 on 2008-09-30
Hey guys, 
Has anyone managed to get Sopcast working on Hardy64?  I am a recently converted Ubuntu user and haven't been able to manage to get it to function.  I have tried the corce Architecture trick posted elsewhere.  Is there a how-to guide which is current?

---

### Post by flyguy97 on 2009-01-06
Hello all,

I created a new SopCast front-end and would love it if people would help test it out a bit. It features a built-in player and a channel guide with the ability to bookmark favorite channels. Currently the only available language is English, but I'm working with a few people to try and bring support for Japanese and Chinese as well. Let me know what needs improvement, and please, be honest.

[http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player")

btw. Be sure to read the Installation notes on the website before you install, due to the GPL I am unable to include the SopCast client program in the package.

flyguy97

---

### Post by tombott on 2009-01-07
flyguy97  just downloading and installing now.
Will let you know how I get on.
Looking at the screenshots on the website it looks very good, well done and thank you.

Tom.

---

### Post by tombott on 2009-01-07
Ok installed without any problems, and works brilliantly.
My only issue is that you can't resize the window.
I'm testing on my Asus Eee PC so am restricted to 1024x600.

Tom.

---

### Post by pt123 on 2009-01-07
you might want to try this new Sopcast application
[http://ubuntuforums.org/showthread.php?t=1032901](http://ubuntuforums.org/showthread.php?t=1032901)

---

### Post by tombott on 2009-01-07
> **pt123 said:**
> you might want to try this new Sopcast application
[http://ubuntuforums.org/showthread.php?t=1032901](http://ubuntuforums.org/showthread.php?t=1032901)

Thats the one I'm talking about.
Look up a few posts, the author posted in here too.

Tom

---

### Post by pt123 on 2009-01-07
^ sorry missed his post

---

### Post by flyguy97 on 2009-01-10
Good news, my mate is taking holiday with his girlfriend and he is letting me borrow his eee pc. I won't be able to play with it until Monday, but as soon as I do I will be posting a binary specifically designed for the eee pc (or hopefully creating one binary for all Ubuntu distros). I want to make sure anyone using Linux is able to use SopCast Player.

btw-For those Redhat users out there, I will be posting an RPM just as soon as I can figure how to package a Python program in RPM. Any help on this would be much appreciated.

> **tombott said:**
> Ok installed without any problems, and works brilliantly.
My only issue is that you can't resize the window.
I'm testing on my Asus Eee PC so am restricted to 1024x600.

Tom.

---

### Post by flyguy97 on 2009-01-12
All,

An updated version (0.1.1) has been posted to my [project page]("http://code.google.com/p/sopcast-player") which address resolution issues. Instead of using a straight 600 * 800 pixel area of the screen, the player takes up 40% of the height of the open window and resizes the width to maintain a proper aspect ratio. Please let me know if there are any issues using it on the Eee PC, thank you.

> **flyguy97 said:**
> Good news, my mate is taking holiday with his girlfriend and he is letting me borrow his eee pc. I won't be able to play with it until Monday, but as soon as I do I will be posting a binary specifically designed for the eee pc (or hopefully creating one binary for all Ubuntu distros). I want to make sure anyone using Linux is able to use SopCast Player.

btw-For those Redhat users out there, I will be posting an RPM just as soon as I can figure how to package a Python program in RPM. Any help on this would be much appreciated.

---

