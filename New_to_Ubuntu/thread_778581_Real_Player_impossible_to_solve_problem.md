---
title: "Real Player impossible to solve problem"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Benbow on 2008-05-02
I used to be able to get BBC radio on Ubunto perfectly but now all I get is what appears to be scrambled rubbish. I have reinstalled realplayer which didn't help. I can ge all kinds of other radio, Shoutcast etc, but not BBC.
Help please.

---

### Post by zhouxing on 2008-05-02
Are you using Real Player 11 Gold or the old 10 Gold?

---

### Post by DJ_Peng on 2008-05-02
There's actually a thread about [RealPlayer 11 Gold on Hardy 8.04]("http://ubuntuforums.org/showthread.php?t=758024") that includes people stating that it fixed the BBC Radio issue. You don't say which version of Ubuntu you're running but it may help resolve your issue.

---

### Post by Benbow on 2008-05-02
Sorry for the delay, I had to trim an overgrown hedge!! I tried the deb supplied by jen 1963 but the sound from the BBC still came through apparently scrambled. I wonder if this is a BBC problem, as I said I can receive other radio stations, Does anyone else have this annoying bug with the BBC?

---

### Post by jimv on 2008-05-02
Yes, Real Player is an impossible to solve problem and BBC radio mostly broadcasts scrambled rubbish.

---

### Post by FreewheelinFrank on 2008-05-02
The MPlayer plug-in plays streaming BBC radio on Hardy without the RealPlayer malarkey.

---

### Post by rogerp1 on 2008-05-02
I have the same problem. It worked before the upgrade to Hardy.

If I save the link and open it with realplayer it works OK

I'll install the MPlayer Plugin and try that

Edit...no that didnt work its still garbled

---

### Post by Benbow on 2008-05-02
Doesn't work for me. I really like some of the bbc programmes and find it disappointing that it won't let me!

---

### Post by Fenris_rising on 2008-05-02
hi there
fiesty fawn runs the iplayer ok for me. but hardy heron wont. so i click the option in iplayer to use stand alone realplayer. not ideal but it works until  they sort out whatever it is thats causing the problem.

regards

fenris

---

### Post by FreewheelinFrank on 2008-05-03
BBC steaming radio working for me with MPlayer plug-in and Hardy Heron 8.04.

Maybe having RealPlayer and the MPlayer plug-in causes problems?

---

### Post by TransplantedCanuck on 2008-05-03
> **FreewheelinFrank said:**
> BBC steaming radio working for me with MPlayer plug-in and Hardy Heron 8.04.

Maybe having RealPlayer and the MPlayer plug-in causes problems?

Don't think so, I've got the m-player plugin installed (at least its in the plugins list...) and have been trying to figure out how to install real player...

same problem, 

sounnds like the chipmunks on reverse or something.

---

### Post by Petergeek on 2008-05-03
FIXED IT! :popcorn:

I had the same problem yesterday. I have just followed the instructions here and it now works.
[http://www.zyxware.com/articles/2008/04/27/setting-up-raaga-com-to-work-on-ubuntu-8-04-hardy-heron](http://www.zyxware.com/articles/2008/04/27/setting-up-raaga-com-to-work-on-ubuntu-8-04-hardy-heron)

Seems to be a Firefox 3/Realplayer incompatibility.

---

### Post by WitchCraft on 2008-05-03
> **Benbow said:**
> 
I used to be able to get BBC radio on Ubunto perfectly but now all I get is what appears to be scrambled rubbish. I have reinstalled realplayer which didn't help. I can ge all kinds of other radio, Shoutcast etc, but not BBC.
Help please.


Hi!

I don't know about BBC, but I had similar problems with the Swiss Radio station. But I did not hear scrambled sound, I heard no sound.

You can do the following.

Go to:
[https://player.helixcommunity.org/Index.html](https://player.helixcommunity.org/Index.html)

And either download realplayer or helixplayer.
If RealPlayer doesn't work try HelixPlayer.

Then, the thing to notice is that none of them works with firefox.
So:
If you use HelixPlayer: this one works with Epiphany Webbrowser on 7.10
If you use RealPlayer:  this one works with Seamonkey Webbrowser on 8.04

Everything else did not work.

In other words: install all browsers you can, and then try each one - if you're as lucky as I, you will find one that works...

---

### Post by Fenris_rising on 2008-05-03
hi there well done that man, well found. sorted here to iplayer fully functional with the firefox shipped with HH8.04.

regards

Fenris

---

### Post by anrom on 2008-05-03
> **Petergeek said:**
> FIXED IT! :popcorn:

I had the same problem yesterday. I have just followed the instructions here and it now works.
[http://www.zyxware.com/articles/2008/04/27/setting-up-raaga-com-to-work-on-ubuntu-8-04-hardy-heron](http://www.zyxware.com/articles/2008/04/27/setting-up-raaga-com-to-work-on-ubuntu-8-04-hardy-heron)

Seems to be a Firefox 3/Realplayer incompatibility.

This fix at zyxware.com did work for me in terms of getting BBC radio via their iPlayer, which I could not do before 8.04, not even in Dapper.  I prefer to listen in RealPlayer as a stand-alone though.

The iPlayer is not displaying the "choose standalone player" thingy.  I find it easier to just open the RealPlayer & choose a saved weekly show, instead of going to the site & opening the iPlayer.  

And with the iPlayer - you can't go backwards at all, and control of the forwarding function is limited.

Most posters here have said they have the "choose stand-alone player" function in iPlayer, but mine is missing it.  Any ideas how to get it?

---

### Post by anrom on 2008-05-05
As for BBC iPlayer Radio, I hadn't realized that the "open in stand-alone player" function is not allowed for music shows.  Curiously, I can still play the few URLs I saved in real player before upgrading to 8.04, including music shows.

I'm trying to figure out how to put the dozen or so shows I like back into Favourites.  I can get some info by right-clicking in BBC iPlayer Radio in the left area where the show is selected and This Frame/View Frame Info/Media, using the 'embed' URL.

Here's an example of 2 music shows' URLs I have in Favourites that work:

Paul Barnes: rtsp://rmv8.bbc.net.uk/england/radionorfolk/aod/paul_barnes_sat.ra?BBC-UID=84c7dae34c225d6c2ecf404f81f863e8675f19c9a0f001f95bab121d741f717e&SSO2-UID=

Celtic Heartbeat: rtsp://rmv8.bbc.net.uk/wales/radiowales/celticheartbeat.ra?BBC-UID=84c7dae34c225d6c2ecf404f81f863e8675f19c9a0f001f95bab121d741f717e&SSO2-UID=

In my attempt to get Travelling Folk back in Favourites, I tried this: rtsp://rmv8.bbc.net.uk/radio/aod/shows/rpms/scotland/travelfolk.ra

and this: rtsp://rmv8.bbc.net.uk/scotland/radioscotland/travelfolk.ra
 
but neither work.  I get this message: The url rtsp://rmv8.bbc.net.uk/radio/aod/shows/rpms/scotland/travelfolk.ra was not able to play back.
The link you followed may be outdated or inaccurate. (rtsp://rmv8.bbc.net.uk/radio/aod/shows/rpms/scotland/travelfolk.ra)

I don't know if the long string after ".ra?" is necessary to know beforehand.  Any ideas?

---

### Post by anrom on 2008-05-08
After much googling, I discovered [http://beebotron.timeforabrew.com/]("http://beebotron.timeforabrew.com[URL="http://beebotron.timeforabrew.com/")

"This site provides rtsp RealAudio .ra and .rm streaming links for BBC Listen Again programs that the Beeb hides."  The Beebotron was created primarily for mobile devices, but works on a PC.  

Just choose a station, then a show.  A launch application opens.  I'm using RealPlayer.  After that you can save that show in RP Favourites.  

It doesn't have every single BBC radio show, but there's quite a large selection & they will take requests despite having busy lives.  Many thanks to Kronalias!

This is not a method of ripping BBC radio programs.  In actual fact, I've bought a lot of music that I would never have discovered if not for Beeb radio.  And I find The Beebotron (a name even Roy Cropper might love) much easier to use than iPlayer.  :)

---

### Post by gn2 on 2008-05-08
BBC iPlayer Radio works perfectly in Ubuntu 8.04 with Firefox 2 using Real Player 11 downloaded from Real Player's website and manually installed.

---

