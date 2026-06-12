---
title: "ubuntu 10.04 a lick of paint over a mess?"
date: 2010-04-29
forum: Recurring Discussions
---

### Post by phaedr_os on 2010-04-29
ubuntu 10.04 a lick of paint over a mess
What a pity if effort has gone into cosmetic nonsense mauveing windows buttons to the left etc instead of addressing ubuntu's oft reported problems
Poor default sound mixer
no realplayer provision
no shotcast stream provision

And after installing the 'recommended' nvidia driver, the whole thing became unusable.

For stability, best stick to debian. This mess does it no favours.

---

### Post by ttshivers on 2010-04-29
Thanks for the advice.  I'll have to try out Debian now.

---

### Post by antenna on 2010-04-29
wait.. realplayer?

---

### Post by Geoff918 on 2010-04-29
You can easily move the buttons to the left:

1) Alt-F2 gconf-editor
2) Apps
3) Metacity
4) General
5) change button-layout to read as follows:

:minimize,maximize,close

There, you're back to the "old, familiar style"

I've never directly used Debian--might be preferable for a server. Otherwise, the apps get way too old, IMO. Why should I run Firefox 3.0.8? Or worse?

::Correction:: Debian uses Firefox 3.0.6

---

### Post by phaedr_os on 2010-04-29
>wait.. realplayer?

Well for a complete internet experience one wants to be able to play rm streams when they occur and shoucast 1.fm etc radio pls streams

Realplayer can be set up to do this very nicely so
for complete internet experience ubuntu should cater for this either via realplayer or alternative

---

### Post by NMFTM on 2010-04-29
> **phaedr_os said:**
> Poor default sound mixer
I've never had any problems with Pulse Audio.

---

### Post by ibuclaw on 2010-04-29
> **phaedr_os said:**
> >wait.. realplayer?

Well for a complete internet experience one wants to be able to play rm streams when they occur and shoucast 1.fm etc radio pls streams

Realplayer can be set up to do this very nicely so
for complete internet experience ubuntu should cater for this either via realplayer or alternative

rm still exist? And if they do, why?

---

### Post by Giant Speck on 2010-04-29
> **ibuclaw said:**
> rm still exist? And if they do, why?
For the same reason AOL still exists: people still use it.

---

### Post by Chrysantine on 2010-04-30
> **NMFTM said:**
> I've never had any problems with Pulse Audio.
The moon is also cheese.

Seriously, the current Linux Audio landscape is.. horrible. In fact, horrible does not quite convey my distaste for the whole mess.

---

### Post by Foster Grant on 2010-04-30
I also have never had a problem with PulseAudio.

@phaedr: Totem plays RealPlayer streams and so does VLC. Rhythmbox, Banshee, Amarok and Exaile can all play Shoutcast streams. Any of those have the extreme advantage of not being RealPlayer.

---

### Post by Crunchy the Headcrab on 2010-04-30
> **Foster Grant said:**
> Any of those have the extreme advantage of not being RealPlayer.
This! Real Player is privacy stealing garbage software.

---

### Post by zipperback on 2010-04-30
> **phaedr_os said:**
> 
no realplayer provision
no shotcast stream provision


Real player is available for installation from one of the repositories.

rhythmbox will allow you to listen to audio streams, as does audacious and numerous other audio players.

> **phaedr_os said:**
> 
And after installing the 'recommended' nvidia driver, the whole thing became unusable.


Was there a specific feature which was unavailable for you using the default video driver which caused you to install a different one?

> **phaedr_os said:**
> 
For stability, best stick to debian. This mess does it no favours.

As with the introduction of any new release of just about any Linux distribution, there are always going to be things which fail to meet some peoples expectations and there are generally going to always be problems. However Ubuntu 10.04 is an LTS release and given time I suspect that it will be extremely stable and highly recommended by many people.

As for "This mess does it no favours.", You didn't really give any specifics as to errors or problems other than a general issue with your video driver.

If you could post some specifics and errors that you are dealing with, I'm sure that many of use would be happy to try and help you resolve them if possible.

- zipperback
:popcorn:

---

### Post by 3rdalbum on 2010-04-30
Realplayer is utter garbage. It wasn't too bad on the Macintosh, but Windows users hated (and still hate) it. On Linux it's even worse, it doesn't even play all of its own files! The w32codecs play all Realplayer files.

I don't have problems with Pulseaudio either. Most people either complain about PA because they don't understand that you need to set up an input device for Skype within the Pulseaudio volume control itself (NOT through Skype, as previously was the case); or because they try to remove PA and end off with things not working.

---

### Post by Linuxforall on 2010-04-30
RM plays fine on Mplayer, running nvidia current installed via jockey, its smoother than Karmic which was no slouch, about Debian, well lets put it this way, it won't endear itself to newcomers or average desktop users, specially those who are switching from Windows.

---

### Post by cb951303 on 2010-04-30
no realplayer? seriously?

i'm with you on the "looks" argument. i too think that there are more important things to improve but realplayer support is definitely not one of them.

if you really need this obsolete and proprietary streaming technology you can always install it yourself: [http://www.real.com/realplayer/linux](http://www.real.com/realplayer/linux)

---

### Post by bowens44 on 2010-04-30
> **Chrysantine said:**
> The moon is also cheese.

Seriously, the current Linux Audio landscape is.. horrible. In fact, horrible does not quite convey my distaste for the whole mess.

I have never had better audio in Linux (or other operating system) then I do now in Lucid and did before in Karmic. 

I don't think the pulseaudio is the problem

---

### Post by dasbooter on 2010-04-30
> **bowens44 said:**
> I have never had better audio in Linux (or other operating system) then I do now in Lucid and did before in Karmic. 

I don't think the pulseaudio is the problem

Pulse audio is still a problem for many. There is no denying that but u can still make statements to the contrary if u like, I dont care. It would be nice if these 3 things worked out of the box on any distro( I have tried a few and many versions of each) Display/Graphics preferably 3d accelerated(proprietary, sigh dont get me started), Audio (I dont mean default install of the codecs but the sound output system/server itself. Burning CD/DVD/ at least up to DVD dual layer. It is a rare occurence that all of these things worked for me out of the box.

Right now pulse audio still skips and stutters horribly, but I will hope for a fix :-\" have a nice day

---

### Post by juancarlospaco on 2010-05-01
Yeah, 
i remember that Windows and OSX's out-of-the-box fresh installed realplayer and shotcast are better...

---

### Post by phaedr_os on 2010-05-01
Realplayer bashing is imho an unhelpful distraction
 If one is really going to use linux then it is quite possible one wants to listen to a bit of online radio or some other stream while working on spreadsheets etc and using the internet as a source of data
 

 A list of apps which supposedly deal with streaming media is not much use when in practise they don't fully work
 

 Realplayer does not give any sound with unbuntu LL unless u hack it. I can document what is to be done. If anyone can properly document how to get any of the other suggestions fully working (video and sound) please do so
 

 Gnome mplayer is the app I use to play [www.1.fm]("http://www.1.fm/") streams (but no sound with rm files in Ubuntu LL)

 

 That all supposes using firefox as browser when accessing these online streams and playing bbc iplayer streams whilst trying to copy data from other sites while using ff seems to cause other problems.
 

 Chrome, on early impressions, may be better at playing flash media whilst still allowing the browser to select and copy(and paste int oo calc) information from other sites but that brings in other requirements for built in streaming media plugins.
 

 For a decent experience, playing media, working on files, essentially OOTB there is work to be done. So less emphasis on which side or the window the minimise button is on and what shade of puce is used for the background and more on getting multimedia apps to work well and in harmony with browser would be appreciated.

---

### Post by cb951303 on 2010-05-02
yeah but why the hell do you complain in ubuntu forums?
there is a realplayer for linux and if that doesn't work in ubuntu blame the realplayer company.

---

### Post by Dark Aspect on 2010-05-02
> **NMFTM said:**
> I've never had any problems with Pulse Audio.

> **Foster Grant said:**
> I also have never had a problem with PulseAudio.

Same here, however I don't see what the big deal is ALSA is still being developed. One can easily delete PulseAudio and replace it with ALSA - PulseAudio is not the only sound choice for Linux.

---

### Post by NMFTM on 2010-05-03
> **Dark Aspect said:**
> Same here, however I don't see what the big deal is ALSA is still being developed. One can easily delete PulseAudio and replace it with ALSA - PulseAudio is not the only sound choice for Linux.
Does ALSA have an easy to use sound mixer like PulseAudio does? Because I've only played around with pure ALSA (standalone ALSA, not through PulseAudio) a little bit while using Debian before switching to Ubuntu but none of the ALSA mixers in the repos actually allowed me to adjust the rate of individual applications. They just adjusted the settings of all ALSA sounds in general.

---

### Post by Chrysantine on 2010-05-03
> **Dark Aspect said:**
> Same here, however I don't see what the big deal is ALSA is still being developed. One can easily delete PulseAudio and replace it with ALSA - PulseAudio is not the only sound choice for Linux.
PulseAudio without ALSA is *nothing* - PulseAudio does not provide any sound drivers or interact with the hardware, everything you hear if you're using PA goes through ALSA. 

All PA does is mix audio in software and it's yet another unnecessary layer on top of the current mess that Linux audio landscape is. What the system needs is proper standardization and not hackish crap like PA. It doesn't help that the PA developers are some of the most arrogant people I have ever had the displeasure of talking to, ever.

---

### Post by vipin.balakrishnan on 2010-05-03
Hi 

 Can you make sourround40 to work in alsa without the help of pulseaudio???

---

### Post by rajeev1204 on 2010-05-03
Whats RealPlayer ? :D

---

### Post by rajeev1204 on 2010-05-03
> **vipin.balakrishnan said:**
> Hi 

 Can you make sourround40 to work in alsa without the help of pulseaudio???


Hi,

You should open a new support thread for this question . I had a 4.1 setup and it worked nicely with alsa.

In the new volume control, go to hardware > device > profile and set sound output.




rajeev

---

### Post by NMFTM on 2010-05-03
> **Chrysantine said:**
> All PA does is mix audio in software and it's yet another unnecessary layer on top of the current mess that Linux audio landscape is. What the system needs is proper standardization and not hackish crap like PA. It doesn't help that the PA developers are some of the most arrogant people I have ever had the displeasure of talking to, ever.
What exactly do you mean? From an end user standpoint I don't see any problems with audio and don't know what you mean by "lack of standardization". Linux has OSS and ALSA, OSS is pretty much depreciated and as far as I know all newer Linux applications use ALSA. The only major Linux app I'm aware of that still uses OSS is Wolfenstein: Enemy Territory, and that's just because it's legacy. How much more standardized could it be?

I could open up a playlist in Rhythmbox, talk to someone on Skype, and play Nexuiz all at the same time. Provided I adjusted the sound levels appropriately in PulseAudio.

---

### Post by jacobw7 on 2010-05-03
MOST simple thing IMO is that this is ANOTHER ubuntu release where there are no templates installed by default, windows does this, mac does this, everything sensible does this, why doesn't Ubuntu?

---

### Post by JosephMarc on 2010-05-04
> What exactly do you mean? From an end user standpoint I don't see any  problems with audio and don't know what you mean by "lack of  standardization".

I can tell you that, here is my Alsa/PA parcours since i first started using ubuntu :

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1471304](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1471304)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1410711](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1410711)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1309160](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1309160)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1145920](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1145920)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1149653](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1149653)

A sound thread for each and every new release I've tried(latest 10.04 included oc), each time I was hoping for the issue to get fixed instead of hacking around with config files, all I've got is the removal of the hack in a PA update in Karmic and up ( I now have to configure my sound system each time I restart my computer). Point is PA/Alsa might work well for the standard 2.0 speakers that most people have, but it still remains an ugly mess that just doesn't do things "right".

---

### Post by NMFTM on 2010-05-05
> **JosephMarc said:**
> Point is PA/Alsa might work well for the standard 2.0 speakers that most people have, but it still remains an ugly mess that just doesn't do things "right".
I haven't had any trouble with my analog 5.1 channel sound on either 9.10 or 10.04. Are you using analog or digital surround sound speakers?

---

### Post by JosephMarc on 2010-05-06
> I haven't had any trouble with my analog 5.1 channel sound on either  9.10 or 10.04. Are you using analog or digital surround sound speakers?

[http://en.wikipedia.org/wiki/Digital_speakers#Speakers_marked_as_digital](http://en.wikipedia.org/wiki/Digital_speakers#Speakers_marked_as_digital)
There are no "digital" speakers, this is just a marketing blunder by some audio firms out there. BTW how did you get it to work? Did you just insert the jacks and got all 5 channels working out of the box?

---

