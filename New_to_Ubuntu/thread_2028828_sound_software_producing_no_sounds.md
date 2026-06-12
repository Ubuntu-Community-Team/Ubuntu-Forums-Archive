---
title: "sound software producing no sounds"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by bgrumbin on 2012-07-18
None of Virtual Midi nor Audacious nor any of the other new installations that I completed using sudo tasksel are producing any outputs through my computer speakers.  SOUND, however, verifies that my Ubuntu installation *is* connected to my hardware.  What's happening and how do I fix it so that I can actually use these installed softwares?

---

### Post by jmfal on 2012-07-18
Welcome to Ubuntu

try unmuting the s/pdif controls is alsamixer.

---

### Post by bgrumbin on 2012-07-19
As you suspected, jmfal, the S/PDIF was [off] when I went into terminal / alsamixer v1.0.25.  Master showed 100, PCM 70, all of Line, CDMic, MicBoos, Video, Phone were at 0 along with S/PDIF.  The question now becomes 'HOW do I unmute the S/PDIF?".  I could find no means of changing any of the settings while I was in the terminal.

---

### Post by NikTh on 2012-07-19
> **bgrumbin said:**
>  The question now becomes 'HOW do I unmute the S/PDIF?".  I could find no means of changing any of the settings while I was in the terminal.

Hi , 
when you are in terminal (in alsamixer) you can navigate with arrow keys and mute - unmute with "m" key. Volume up or Volume down with up- down arrow keys.
Thanks

---

### Post by jmfal on 2012-07-19
I was hoping you would click on the alsamixer link below so I wouldn't have to explain.

---

### Post by bgrumbin on 2012-07-19
There are two of the prospects that have no sound bars above them: MicBoos and S/PDIF. So when I press "m" the MM disappears and instead I get a "00" which refuses to adjust with the arrow keys that I used to eliminate the red line portion of Master. With the <F6> I have tried adjusting it with all three of the available choices including my identified Ensoniq Audio PCI. Chip Cirrus Logic CS4297A rev3. No matter what I choose, I continue to get the "00" for S/PDIF devoid of sound bar and devoid of response to the arrow keys. With that "00" S/PDIF setting refusing to change, even though it is no longer [OFF], the Virtual Midi Keyboard continues to produce no sound.

---

### Post by jmfal on 2012-07-19
I don't mess with that stuff, but somebody the other day had the same problem with drumstick, and it was suggested that they install the timidity package and set output to 1 or 0

There was no reply after that so I'm not sure if it worked.

Maybe there is some kind of setting like that in the app you're using.

Try going to sound settings and change the card there to the digital card.

---

### Post by james12 on 2012-07-19
Initially i was using Windows and Mac Operating System and now in my System all systems has been migrated from Mac to Ubuntu, so do not have any idea about it, the sound driver has installed on my system, it is showing the Speaker icon on the task bar, and can connect speakers also to it but without speakers i cannot hear the sound, is there any setting to be done or anything missing in it?

---

### Post by jmfal on 2012-07-19
To james12,  Welcome to Ubuntu
Click on the alsamixer link below.
Is your problem no sound, or is it related to the thread?

---

### Post by bgrumbin on 2012-07-19
Responding to recent suggestions: TIMIDITY made the problems WORSE so that now the RhythmBox is incapable of normal sound volumes, even with all available volume settings boosted to maximum. Made no change to the inability of alsamixer to provide a means of adjusting S/PDIF nor to the functionality of the Midi Keyboard. I'm going to need to uninstall that nonsense and preparing at least to try on the Ubuntu Software site momentarily.
 
As for changing the card to digital in SOUND, there is one only possible choice offered which is to "Play Sound thru Analog output ES1371 [Audio PCI-97]". There is no digital choice offered.
 
Still no progress on the original question which is how to run the installed music software which has proven incapable of producing so much as a peep despite the SOUND tester proving connection to the physical hardware required.

---

### Post by jmfal on 2012-07-19
Was your sound working before you installed these apps??

If you have sound then you just need to make connection from app to sound.
Don't worry about s/pdif  for now.

---

### Post by bgrumbin on 2012-07-19
> **jmfal said:**
> Was your sound working before you installed these apps??
If you have sound then you just need to make connection from app to sound.
Don't worry about s/pdif for now.
 
Yes and No. Rhythmbox has been flakey all along, even before I installed the entire set of music apps using sudo tasksel. It regularly stops playing any sounds in the midst of known good MP3s, for example, takes the expected amount of time to end of record in silence and then starts up on the next song in the list. SOUND tells me I have consistently good connectivity between Ubuntu and my pair of speakers, even if Rhythmbox quits using it in mid MP3 with all too much regularity. The tests in SOUND always succeed. So it isn't only the newly installed apps which have never connected but also the originally installed Rhythmbox which flakes out as described.
 
Bottom line remains how to "make connection from app to sound" when none of them has any offered controls for making (or improving to becoming consistent) the connection between the apps and the verified functional by SOUND speakers.

---

### Post by jmfal on 2012-07-19
Have you installed ubuntu-restricted-extras
It should solve the mp3 problem

```
  sudo apt-get install ubuntu-restricted-extras
```

Restart pc/laptop
unmute sound
try some music

---

### Post by bgrumbin on 2012-07-20
Sudo couldn't find it but Ubuntu Software Center did on "multiverse" where I got ubuntu-restricted-extras installed. There were also four other updates from Ubuntu which I had installed during the same online session. Then did a cold reboot of my VMware Ubuntu. Reset SOUND to normal amplification. Have four MP3 files on my Ubuntu for testing purposes. Rhythmbox played thru the 2:17 and 1:43 files but shorted out at 2:00/4:11 and 1:03/3:24, pretty much what it was doing before these installations (although I hadn't previously annotated *where* the shorting out was occurring). Problem remains exactly the same with Rhythmbox. Out of curiosity, I also tried the Virtual MIDI Keyboard yet again; it too still refuses to make a peep.

---

### Post by jmfal on 2012-07-20
So are you running ubuntu in a vm?

---

### Post by bgrumbin on 2012-07-20
Absolutely for sure, "trying" to run Ubuntu as a virtual machine, complete with sandbox to protect my normal business systems from attack. Wasn't aware, when I started exploring Ubuntu, of its particular insistences for massive exposure to being "online" which outnumber even the absurd set of "updates" that Micey Sorft demands for its slopperating system (but doesn't necessarily get since they were identified as the exclusive suspect for "Melissa" style expungement of politically sensitive photos and some entire directories of such photos and subsequent sabotage of the entire Win7 desktop). But it wouldn't have made any difference if I had known since I am loath to allow, especially persistent, demands for access to my computers regardless of the reasons, without at least a sandbox to provide "some" protection and an "unknown to me" security risk such as Ubuntu would certainly have required a sandbox treatment regardless.
 
Yes, I am aware of some things which VMware does in the way of interference with normal functioning of "some" programs. For example, my decades successful DOS programming platform, which has helped me write the entirety of my business entourage of programs, has one key function (search and replace in source files) which VMware uses to shut down or lock up the operation of the platform. Isn't allowed to run at all under Win7, so that's scant complaint about VMware which *is* allowing me to carry on with the rest of my decades successful business programs since at least I "can" work around the absence of search and replace functions (but not the total absence of ability to patch and improve my proggies). 
 
Dunno whether that is impacting the operation of Rhythmbox or any of the others. Fact is, I haven't been able to get VMTools installed into Ubuntu yet because the "help" VMware provides suggests it is a more complicated process than I'm capable of dealing with yet in an unknown to me operating system. Known, however, to the extent that when I noticed (via making a movie of them and extracting the frames involved) the repeated flashed references, on the way in and out of the Ubuntu virtual machine, to /etc/default/speech-dispatcher, and attempted to change its "no" to a "yes" as the file itself suggests, I was blocked from storing the changed config file and in a Terminal couldn't even get access to that little tidbit of inherently suggested change. So I've been following the suggestions given in this forum (within the mandatory context of the VMware sandbox) in an effort to get some use out of Ubuntu.

---

### Post by jmfal on 2012-07-20
Running a vm causes some problem with sound in ubuntu
I did some googling
1 set client tools (virtual audio) to AC97
2 install guest additions
3 try logging into ubuntu as a single user ( you will be root, so all commands requiring sudo  >> don't need to use sudo)

---

### Post by bgrumbin on 2012-07-20
I'll be trying your suggestions a bit later this afternoon. But I did misspeak myself when I said I didn't have VMTools installed in Ubuntu (that's my attempt at setting up a sandbox for freeBSD that has *that* problem). Of course I have VMTools installed, that's how I got those four music files copied over into the "Music" directory in Ubuntu. I began this attempt to install Ubuntu at the suggestion of a friend who has made several excellent suggestions in the past (including Thunderbird v10 as an email client) and who uses Ubuntu as his primary operating system. With two serious winners to his credit, I'd rather this suggestion prove useful too. Thanks for the continued flow of "things to try that might work".

---

### Post by 2burke on 2012-07-21
[LEFT]Hi,
[/LEFT]
Have been having the same prob.
Have looked everywhere here on the forum and in the end tried this.
It had the default card in F6  so I changed it to the next one down.
Am loathe to play with these things so took a risk and now it works.
Many thanks to everybodys help:razz:


/home/greg/Pictures/Screenshot from 2012-07-21 16:19:21.png
Will go and do some more reading and find out how to put in pics.

---

### Post by 2burke on 2012-07-21
Again the people on Ubuntu are really good with their info.Found out how to upload pic. and here it is for the last post.

---

### Post by 2burke on 2012-07-21
Again the people on Ubuntu are really good with their info.Found out how to upload pic. and here it is for the last post.
Still not able to get the front speakers up,down arrows to work,but the sound works.

---

### Post by bgrumbin on 2012-07-21
> **jmfal said:**
> Running a vm causes some problem with sound in ubuntu
I did some googling
1 set client tools (virtual audio) to AC97
2 install guest additions
3 try logging into ubuntu as a single user ( you will be root, so all commands requiring sudo >> don't need to use sudo)
 
Found no way to do any of those things. But the concept of setting Ubuntu up as a single user system was something that I "thought I saw" when I did the OFFline first attempt at installing Ubuntu. Went ONLINE however, for the entire installation process and never saw any way of getting the system established as a single user system. Added tasksel and did the sudo tasksel procedure for the sound related proggies and to change from Ubuntu Desktop over to Basic Server (Ubuntu Studio). Spent my life between 3am and 7am this morning going through that, frequently at <60 Kb/s download speeds.
 
Bottom line, however, is that none of the sound related software ever did anything correctly. I had already dismissed Firefox as a dysfunctional idea. I already have video software in Win7 which I used the other day successfully to process some 5 year old video that I recorded. The "photo album" software was an absolute beginner style atrocity of filing photos "by date" which is totally absurd for a guy such as myself who already has more than 30,000 photos and an insistent need to keep them organized by *subject*. So absent the sound studio software actually working (and its refusals even to correctly play known good MP3s is pretty indicative that it doesn't and ain't never gonna), there was no reason for me to continue futzing with sorft WAR none of which connects properly to any of its own other parts, none of which allows me even to modify the system config files taking up space on *MY* computer, none of which is willing to allow me to see the "Ubuntu-docs" which were supposedly placed on my computer, and none of which is willing to do any actual work for me.
 
So the pair of Ubuntu installations (and the original source ISO that I tediously downloaded from Ubuntu in the first place) are en route to being deleted. Not that I don't have "space" for them on my voluminous new hard drive and its backup systems. But with an endless stream of inexcusable failures, I just don't have the time to futz with Ubuntu further. Too many considerably more interesting and useful things to do in the world. 
 
This may not have been "solved" in the manner I was hoping when I began the inquiry, but it has in fact been SOLVED in the real world by the expunging those time wasting Ubuntu vms and documents.

---

