---
title: "HOWTO: MIDI in Hoary"
date: 2005-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Deusiah on 2005-05-01
[SIZE=3]_Introduction_[/SIZE]
This HOWTO is work in progress. Ideally I'd like a set of commands that work universally for everyone with a soundcard that has a **hardware synthesizer** and works with **ALSA** or **OSS**. So far I have only been able to try this on two machines but have had success with both. I would like to hear if anyone else has any success or problems with these commands but please ensure you know your card works with **ALSA** or **OSS** and has a **hardware synthesizer** if your card does not have both please seek help elsewhere on the forums.

[SIZE=3]_Setting up the Midi_[/SIZE]
Open up a Terminal (alt+f2 then gnome-terminal) and enter the following commands:
```
sudo modprobe snd_seq_midi
sudo modprobe snd_emux_synth
sudo modprobe snd_emu10k1_synth
sudo apt-get install awesfx;asfxload
"asfxload soundfont.sf2" for ALSA or "sfxload soundfont.sf2" for OSS
```**NOTE:** Where soundfont.sf2 is the soundfont file you wish to use, many sound fonts can be found at [http://www.hammersound.net](http://www.hammersound.net). I use [Fluid - Release 3 [68.5MB]](http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=699;SoundFont_Location_Selected=Download%20It;SoundFont_Filename_Selected=Download) but this is down to preferance, you may like the sound of other sound founts better. One thing to look out for when choosing is to ensure your sound font is organized according to the GM (General Midi) standard for instruments. Sound fonts will normally mention GM in their description or title if they are. 

[SIZE=3]_Adding the modules to statup automatically_[/SIZE]
If this works for you, you will want to have these modules load at startup. Add the following to the bottom of /etc/modules (NOTE: This file will need root permissions so use sudo nano /etc/modules or sudo gedit /etc/modules):
```
snd_seq_midi
snd_emux_synth
snd_emu10k1_synth
```
[SIZE=3]_**Currently Tested With**_[/SIZE]
If you have tried the above commands and they worked for you please give feedback and post the make and model of your card so that when others come to search for their card and enabling midi they should come across this post, Thanks.
[list][*]Sound Blaster Audigy 2 ZX
[*]Sound Blaster Audigy 2 Platinum
[*]Sound Blaster Live!
[/list] 
[SIZE=3]_**Extra Help**_[/SIZE]

[SIZE=3]_If you have downloaded an sfArk SoundFont_[/SIZE]
If your soundfont is in sfArk format (which is a compressed losless format for soundfont files), you will need to decompress (extract) it before use. This can be done with a simple utility found which can be found at: [http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm). This program is very simple to use and instructions on it's use can be found within the programs download. If your file extracts as anything other than a soundfont (*.sf2) i.e. *.exe you will not be able to  use it so simply try another soundfont file.

[SIZE=3]_Playing Midi with pMidi_[/SIZE]
This next step is optional, if you already have a player capable of playing Midi files use that instead, since I had no player capable of playing midi to test the Midi support I downloaded a simple command line midi player for ALSA, pmidi.

```
sudo apt-get install pmidi
pmidi -l
pmidi -p x : x midifile.mid
```**NOTE:** pmidi -l gives you a list of possible out put ports, I used the port "Emu10k1 Port 0" but you may need to use another. You then use these ports with the -p option. e.g. pmidi -p 65:0 midifile.mid where midifile.mid is the name of your midifile.

---

### Post by alphazero on 2005-05-02
I tried the modprobe commands and everything worked great. However, as soon as I reboot the modules seem to be gone and midi won't work until I input them. Is there any file I can write to?

---

### Post by Adamal on 2005-05-02
try adding the modules you need to load on start up to the /etc/modules

---

### Post by maliStfn on 2005-05-03
hey, I'm very happy about finding this threat, I tried it - but it does not work. I want to use the midiport on my terratec aureon fun for comunication to my keyboard. I tried the above except the sudo apt-getinstall... and asfxload...
A > cat /dev/sndstat still gives me back a

Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux Ljudstvo1 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0xb800, irq 10

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: CMedia PCI

Do you know what I did wrong (working on hoary)?
greetings, stefan

---

### Post by Deusiah on 2005-05-03
[QUOTE=alphazero]I tried the modprobe commands and everything worked great. However, as soon as I reboot the modules seem to be gone and midi won't work until I input them. Is there any file I can write to?[/QUOTE]

Good point :razz:, I have updated the HOWTO thanks. Great to hear it works for you BTW.

maliStfn you will need the apt-get line otherwise you will not hear anything from a midi file. Also please note this howto is only for hardware sequencers.

---

### Post by jonny on 2005-05-03
Thanks for this.  I can't wait to try it on my home PC.

I've sweated blood trying to get midi to work.  Everything else that I've found on the net is either so complex that I'm lost within a paragraph or two, or is so distribution specific that it's useless.  I'll let you know how I get on.

---

### Post by jonny on 2005-05-04
Fabulous.  Works perfectly - thanks.

The only step that tripped me up was that the sound font is in a compressed format, even after you've untarred it.  You need [this package](http://www.melodymachine.com/files/sfarkxtc_lx86.tar.gz) to turn it into an SF2 file.

---

### Post by Deusiah on 2005-05-05
Great to hear it works for you Jonny!

Sorry about the sfArk problem, I forgot to add this to the HOWTO. Sometimes it's easy to forget that certain steps you take are not known to all.

Anyway, I have added it to the HOWTO and also reformatted the post to make it a bit more presentable.

---

### Post by Merc248 on 2005-05-05
Nice. :D  Thanks for the HOWTO guide... works absolutely great over here with a Sound Blaster Audigy 2 Platinum. ;p

---

### Post by Deusiah on 2005-05-05
More good news :)

I also have an Audigy 2 to. Your post has given me an idea thanks :P Could everyone who has tried this and got this working please post the sound card and whether you use it with ASLA or OSS. Please be descriptive about your card, include the exact model if you know it, please don't just write SoundBlaster lol.

I'll be adding a list of cards that work to the HOWTO :)

---

### Post by vidyu on 2005-05-24
I have a problem with midi and i think it is the sequencer. Whena i typed sudo apt-get install awesfx;asfxload i saw this message : 
No Emux synth hwdep device is found.
When I type cat /dev/sndstat i see this:
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux vidyu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Ensoniq AudioPCI ENS1371 at 0xd800, irq 5

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371

Timers:
7: system timer

Mixers:
0: Cirrus Logic CS4297A rev 3

I will de happy if anyone can help me.
Sorry for my bad english speeking.

---

### Post by alainhenry on 2005-05-24
For the sake of full information , you could point to this wiki page for the software synthesis: 
[http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo](http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo)

Alain

---

### Post by Deusiah on 2005-05-24
[QUOTE=Deusiah]please ensure you know your card works with **ALSA** or **OSS** and has a **hardware synthesizer** if your card does not have both please seek help elsewhere on the forums.[/QUOTE]

Need I say more?

---

### Post by alainhenry on 2005-05-24
This was just to expand on the 'elsewhere' part of the sentence, for the sake of completeness.  I did not want to interfere in any other way.
Alain

---

### Post by vidyu on 2005-05-24
I followed the steps from [http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo](http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo) , but when I type timidity -iA -B2,8 -Os1l -s 44100 it shows me that is opening 128:0 (I`m not sure for the number of the port) and other ports and does nothing else until i "ctrl-c" it. And then when I type pmidi -p 128:0 music.mid i did not hear any sound. I`m not sure that my card have hardware  synthesizer. How can I find that? Thank you for the answers and again all my apologies for my bad english.

---

### Post by Deusiah on 2005-05-25
Sorry Alain, that post was not meant for you. I don't wish to include such links because it encourages people with software Midi problems to post here, as you can see by the fact that Vidyu has ignored what I said and just posted here anyway. There are many many topics about software synthesis on these forums, why should this hardware synthesis topic be turned into another?

For Vidyu, as I said before and will continue to repeat until you take note:
[QUOTE=Deusiah]_please seek help elsewhere on the forums._[/QUOTE]
There are better places for you to ask that question, this is not one of them. Please ask in another thread or start your own thread. Thank You.

---

### Post by foxy123 on 2005-05-25
[QUOTE=Deusiah]Sorry Alain, that post was not meant for you. I don't wish to include such links because it encourages people with software Midi problems to post here, as you can see by the fact that Vidyu has ignored what I said and just posted here anyway. There are many many topics about software synthesis on these forums, why should this hardware synthesis topic be turned into another?

For Vidyu, as I said before and will continue to repeat until you take note:

There are better places for you to ask that question, this is not one of them. Please ask in another thread or start your own thread. Thank You.[/QUOTE]
I guess you should rename the topic then, because it is a bit misleading... What about HOWTO: MIDI in Hoary with hardware synthesizer or something like that. 

I do not hardware synth myself, but the first topic I bumped in was that one. I would disregard it if the title were different.

Having said that I do not see a problem to have software and hardware synth in one thread, but it's up to Deusiah of course.

---

### Post by Merc248 on 2005-05-25
Anyone happen to know if there's a program out there that is not QT based that can play MIDI files through the hardware synthesizer?

I was considering the xmms-midi plugin, but I noticed that it uses Timidity. :x

---

### Post by Deusiah on 2005-05-25
That's a good idea foxy123 and I did just try to change it but to no avail. I really do hate the mega bloated vBulletin when it comes to forums.

Anyway the reason why I would prefer it to be kept to hardware is because there are already good software midi Howto's in this forum yet I never found one for using your hardware. True I could write more about setting up timidi but I feel I would just be repeating what others have already gone to a lot of trouble to explain.

As for GTK 2 based midi players, I don't know to any sorry. There are some sequencers available which should do the job. Take a look at [http://gnomefile.org](http://gnomefile.org) for some.

---

### Post by jonny on 2005-05-25
In response to the request for hardware details, this works perfectly for me with a Soundblaster Live! Value, circa 2000 vintage.  Thanks to Deusiah, I finally have Rosegarden working properly - and it wastes an indecent amount of my time, too.

I can't get midi to work with Wine, though, and I can't find any threads that might help.  Anyone else had any luck?

---

### Post by Deusiah on 2005-05-26
Thanks for the feedback Jonny :) I have added a section in the HOWTO about cards it is known to work on.

As for Midi in Wine I know nothing about this sorry, from Google'ing it I see it is possible as there is a [guide to getting it to work with TiMidity++](http://www.google.co.uk/url?sa=U&start=1&q=http://frankscorner.org/index.php%3Fp%3Dmid&e=10313). This is a solution but obviously it's not what you want. Perhaps you could post to some wine or linux audio forum/mailing list? Good Luck!

---

### Post by [censored] on 2005-06-04
Ok, did all the above, and pmidi and midi appears to be working at last! First time I've ever got midi working on linux. Thanx.

I've also written the modules into /etc/modules, as per above, so I won't have to reload them after boot up.

Just one question: will I have to reload the sound font after boot up? If so, is there somewhere I can put an instruction to load the sound font automatically for me?

---

### Post by Spug on 2005-07-14
[quote=terminal]$ sudo apt-get install awesfx;asfxload
Reading package lists... Done
Building dependency tree... Done
awesfx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
No Emux synth hwdep device is found
$ asfxload /home/iddi/Ultimate/Ultimate.SF2
No Emux synth hwdep device is found[/quote]What does "No Emux synth hwdep device is found" mean, and can I fix it?

(What I'm trying to do is running a Windows game in Cedega, but it complains about being "Unable to locate MIDI device. Final Fantasy VII requires a Windows 95-compliant MIDI device". I'm not expecting Cedega help here, though, of course.)

---

### Post by Deusiah on 2005-07-14
It means no hardware synthesizer can be found. Are you sure you have one?

---

### Post by fractalvibes on 2005-07-18
> **Deusiah][SIZE=3]_Introduction_[/SIZE]
This HOWTO is work in progress. Ideally I'd like a set of commands that work universally for everyone with a soundcard that has a **hardware synthesizer** and works with **ALSA** or **OSS**. So far I have only been able to try this on two machines but have had success with both. I would like to hear if anyone else has any success or problems with these commands but please ensure you know your card works with **ALSA** or **OSS** and has a **hardware synthesizer** if your card does not have both please seek help elsewhere on the forums.

[SIZE=3]_Setting up the Midi_[/SIZE]
Open up a Terminal (alt+f2 then gnome-terminal) and enter the following commands:
```
sudo modprobe snd_seq_midi
sudo modprobe snd_emux_synth
sudo modprobe snd_emu10k1_synth
sudo apt-get install awesfx said:**
> http://www.hammersound.net[/url]. I use [Fluid - Release 3 [68.5MB]](http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=699;SoundFont_Location_Selected=Download%20It;SoundFont_Filename_Selected=Download) but this is down to preferance, you may like the sound of other sound founts better. One thing to look out for when choosing is to ensure your sound font is organized according to the GM (General Midi) standard for instruments. Sound fonts will normally mention GM in their description or title if they are. 

[SIZE=3]_Adding the modules to statup automatically_[/SIZE]
If this works for you, you will want to have these modules load at startup. Add the following to the bottom of /etc/modules (NOTE: This file will need root permissions so use sudo nano /etc/modules or sudo gedit /etc/modules):
```
snd_seq_midi
snd_emux_synth
snd_emu10k1_synth
```
[SIZE=3]_**Currently Tested With**_[/SIZE]
If you have tried the above commands and they worked for you please give feedback and post the make and model of your card so that when others come to search for their card and enabling midi they should come across this post, Thanks.
[list][*]Sound Blaster Audigy 2 ZX
[*]Sound Blaster Audigy 2 Platinum
[*]Sound Blaster Live!
[/list] 
[SIZE=3]_**Extra Help**_[/SIZE]

[SIZE=3]_If you have downloaded an sfArk SoundFont_[/SIZE]
If your soundfont is in sfArk format (which is a compressed losless format for soundfont files), you will need to decompress (extract) it before use. This can be done with a simple utility found which can be found at: [http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm). This program is very simple to use and instructions on it's use can be found within the programs download. If your file extracts as anything other than a soundfont (*.sf2) i.e. *.exe you will not be able to  use it so simply try another soundfont file.

[SIZE=3]_Playing Midi with pMidi_[/SIZE]
This next step is optional, if you already have a player capable of playing Midi files use that instead, since I had no player capable of playing midi to test the Midi support I downloaded a simple command line midi player for ALSA, pmidi.

```
sudo apt-get install pmidi
pmidi -l
pmidi -p x : x midifile.mid
```**NOTE:** pmidi -l gives you a list of possible out put ports, I used the port "Emu10k1 Port 0" but you may need to use another. You then use these ports with the -p option. e.g. pmidi -p 65:0 midifile.mid where midifile.mid is the name of your midifile.
 What commands would I need to issue for a system having a Turtle Beach Santa Cruz soundcard  (and a Roland Sound Canvas hooked up to that via joystick port)?  Audio works fine but MIDI works not.  Someone suggested trying Timidity with a soundfont - horrible sound quality I got and I need to listen as I create...

thanks,

fv

---

### Post by Deusiah on 2005-07-19
Why ohh why have you quoted my entire guide?

Does your sound card have a hardware synthesizer? Google if you don't know. If it does have a hardware synthesizer follow this guide. If not post somewhere else as this is the wrong forum.

---

### Post by fractalvibes on 2005-07-19
thanks....

---

### Post by maruchan on 2005-07-20
Works great with my Audigy Plat series 1.

Thanks for the howto, now Rosegarden actually works! :D

---

### Post by teathief on 2005-07-28
I've completed all the steps in your howto successfully except
I'm still having trouble getting the midi to work right
I've edited my /etc/modules file to get the appropriate modules
loaded on boot and the modules are up and running
and KInfoCenter says the midi device of my soundcard is enabled in config
but I'm still not getting any midi sound and everything seems to be configured
correctly too for my creative sound blaster live 5.1 ls

Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux orion 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Sound Blaster Live! (rev.10) at 0xd400, irq 18

Audio devices:
0: EMU10K1 (DUPLEX)

Synth devices:
0: Emu10k1

Midi devices:
0: EMU10K1 MPU-401 (UART)

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9758/59

I haven't been using linux for long and I may have missed something
I would appreciate some advice on what I can do about this

---

### Post by Deusiah on 2005-07-28
If you were able to load the soundfont correctly your midi should be working, this may sound obvious but check your volume controls. The best way of doing this is by running alsamixer from a terminal. I can't remember if alsamixer is installed by default or if I got it from the repositories. In anycase just type sudo apt-get install alsamixer if it tells you the command is not found.

Good Luck.

---

### Post by teathief on 2005-07-28
nah there isn't any midi output devices visible in the mixer and what devices I do have are all on and the volume is up on them
and everything else went smoothly though the loading the drivers
downloading the soundfont and installation of it
I'm going to post a message in the hardware help section
I've wanted to get midi support for awhile now (about two years 0_o now)
I have yet to have it on any soundcard
thx for the help and the howto

---

### Post by Deusiah on 2005-07-29
You were using Alsamixer right? Sorry I had to ask but it's very important and you didn't mention it. Since there are often a few volume levels and some are not to obvious as to what they are just make sure they are all up, and check the mute isn't on. There may also be toggle options which you should play about with

Sorry I can't help any more.

---

### Post by szr4321 on 2005-08-11
@Deusiah: Thank you very much for this HowTo, it helped me a lot.
[QUOTE='[censored]']
Just one question: will I have to reload the sound font after boot up? If so, is there somewhere I can put an instruction to load the sound font automatically for me?[/QUOTE]There might be a more elegant way using the /etc/modprobe.d files, but the following worked for me. Insert something like ```
/usr/bin/asfxload /usr/share/sounds/sf2/default.sf2
``` into */etc/init.d/alsa* in the *start()* procedure, that's about line 273 on my system.

Edit: One might as well try to put that into **/etc/init.d/bootmisc.sh**.

---

### Post by [censored] on 2005-09-06
Midi works, but it's clogging up my system.

Every time I asfxload FluidR3GM.SF2, my system slows down heaps.

It's a 1.1Ghz Celeron, with 256 meg of RAM.

Is there a cure for this? Other than upgrading to something post 2001?

---

### Post by Deusiah on 2005-09-07
I didn't do any testing on older hardware sorry, I assumed that since it's making use of your soundcards hardware this wouldn't be too important.

The only thing I can suggest is try using a small soundfont, other than that nothing springs to mind sorry.

---

### Post by [censored] on 2005-09-07
[QUOTE=Deusiah]I didn't do any testing on older hardware sorry, I assumed that since it's making use of your soundcards hardware this wouldn't be too important.

The only thing I can suggest is try using a small soundfont, other than that nothing springs to mind sorry.[/QUOTE]
 Can u suggest such a soundfont? I tried a few, but none seemed to work.

---

### Post by zero0w on 2005-09-08
[QUOTE='[censored]']Can u suggest such a soundfont? I tried a few, but none seemed to work.[/QUOTE]
 If you have the SB Live! Liveware CD you should be able to find the smaller soundfont at this location once you put the CD in drive:

/cdrom/AUDIO/COMMON/SFBANK/

For more information you can take a look at the ALSA wiki snd_emu10k1 section:
[http://alsa.opensrc.org/emu10k1](http://alsa.opensrc.org/emu10k1)

---

### Post by [censored] on 2005-09-08
zero0w cheers! May the source be with you always.

---

### Post by elegant_dice on 2005-09-10
That doesn't seem to help me... 

[www.birthdaycards.com](www.birthdaycards.com) has MIDI things on the webpage.  How do you get it to work on Firefox (with ESD)?

I can't even tell how to set up a helper app in ubuntu firefox?

Thanks
Paul

ps And, how do you get flashplayer to work via ESD ??  Thats pretty frustrating.

---

### Post by Deusiah on 2005-09-10
You might be able to use Mozplugger to get midi working inside Firefox, as for using ESD that should be just a case of selecting ESD System -> Preferances -> Multimedia Systems Selector

---

### Post by zero0w on 2005-09-16
[QUOTE=Deusiah][SIZE=3]_Adding the modules to statup automatically_[/SIZE]
If this works for you, you will want to have these modules load at startup. Add the following to the bottom of /etc/modules (NOTE: This file will need root permissions so use sudo nano /etc/modules or sudo gedit /etc/modules):
```
snd_seq_midi
snd_emux_synth
snd_emu10k1_synth
```[/QUOTE]

In my experience, only **snd_emu10k1_synth** is required to add to the file /etc/modules
The other two modules will be loaded automatically as a dependency to **snd_emu10k1_synth**. 

You can tell it by running *lsmod | grep snd_emu10k1_synth*.

---

### Post by AgenT on 2005-11-11
[http://melodymachine.com/]("http://melodymachine.com/") is dead, which is a major problem because that is where the extraction utility should be. Does anyone know where a utility to extract sfark files can be located?

**EDIT**: There seems to be some strange routing problems! Using a proxy that website works. This is strange because every other website (including ubuntu forums) works fine.

---

### Post by TechSonic on 2006-01-31
This is kind of annoying, it would be better if you could just double click the darn file and have Totem play it.

---

### Post by mlind on 2006-03-01
Thanks for the guide, works great with SB Audigy! :)
I tried with ALSA driver.

---

### Post by Nicram on 2006-04-08
Very helpfull! Thanks!
My SB Aydigy 2 (value) plays perfectly with Fluid_R3_GM

---

### Post by papaschlumpf on 2006-06-26
Went to buy the sound blaster live (24bit, the only sound blaster live that was on sale) today in the hope to finally get a sound card with linux-compatible midi. Followed all steps of your guide, but when I installed the awesfx, it said something about not being able to configure it and:

[FONT="Courier New"]No Emux synth hwdep device is found[/FONT]

the loading of the modules before went smoothly. Trying to load a soundfont leads to the same error.
[FONT="Courier New"]
doing cat /dev/sndstat[/FONT]  gave me:

[FONT="Courier New"]Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux schlumpfhausen 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Live! 7.1 24bit [SB0410] at 0xe400 irq 5

Audio devices:
0: CA0106 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: CA0106 MPU-401 (UART)

Timers:
7: system timer

Mixers:
0: mixer00[/FONT]


I have an onboard sound chip (AC97), which I enabled in the BIOS before installing the SB Live. The SB Live works ok for normal audioplayback, only MIDI is not working. I am on (K)Ubuntu 6.06.

What could possibly be the reason for my problems?

---

### Post by papaschlumpf on 2006-06-28
ok, apparently MIDI for the SB Live 24 bit is not supported yet.
Also I figured out that it does not work with the snd-emu10k1 driver, but uses snd-ca0106.
 I looked around on the ALSA page and zillions of other pages, but couldn't find anything Linux-MIDI-related about the SB Live 24 bit, so I am giving up and bringing the darn thing back tomorrow. Guess I'll have to try to get one of those older SB Live somewhere to get MIDI working :-(

---

### Post by jem7v on 2006-10-21
Hi! Just writing in to say that this method ALSO WORKS IN DAPPER, as of 5 days before Edgy is being released. :P

I am running an old Audigy MP3+, which is basically just an Audigy 1. It works fine with the ALSA [drivers?] but I had to change the MIDI device in my MIDI-playin' programs from the default to one of the "Emu10K Wavetable... etc" ones for it to work. Other than that, it's fine.

I'd also like to say that it took me several hours of frustrated fighting with my computer, trying to get MIDI playback to work, before I found this thread by accident and solved the problem in a matter of minutes. This little guide is excellent... I just wish it had been more visible to start with, because I went through a Lot of threads that said nothing except "I can't get it to work!", "It's too hard to do... just use Timidity instead..." and "After hours of grewling searching and experimenting trying to get it to work, it works! but instead of telling everybody how I did it, I'm going to post more questions that nobody will be able to answer..."

---

### Post by PatrickMay16 on 2006-10-27
FACKIN' OUT like a master at 100,0000 kilometers per hour.

I recently found an old soundcard with an OPL3 chip on it... 
[http://en.wikipedia.org/wiki/OPL3](http://en.wikipedia.org/wiki/OPL3) - a little info here.
I think several different soundcards from several different manufacturers had this chip. Anyway, it gives the ability of hardware MIDI synthesis. It doesn't sound very good, but it works.

If you have an Avance Logic ALS4000 or another card with the OPL3 chip, this is how to get it working.

Install package "pmidi"

Load these modules

snd-seq
snd-seq-midi
snd-seq-midi-event
snd-seq-device
snd-seq-oss
snd-opl3-synth (or perhaps it is called "opl3", I can't quite remember)

Now, do this command:

aplaymidi -l

And in the list that it outputs, you should see something in it which looks like "65:0 OPL3 FM synth". Here's a screenshot of how it looked in my case:
[http://img317.imageshack.us/img317/6297/amazementmn9.jpg](http://img317.imageshack.us/img317/6297/amazementmn9.jpg)

Then, you must install the package "alsa-tools". It was not in the breezy repositories, but it is in the dapper repositories.

That package should include "sbiload", and two files: std.o3 and drums.o3

Now you have installed that package, locate the two files "std.o3" and "drums.o3", so you know where they are in the system. (I assume that they come with the "alsa-tools" package, but I can't remember. I do not have that computer system available to me now.)

Now do this command:

sbiload -p65:0 --opl3 std.o3 drums.o3

And then test to see if it worked.

aplaymidi -p 65:0 testfile.mid

You should be hearing some wonderful synthesized music noises. 
Here's a little sound clip I made in case you'd like to know what it would sound like.
[http://dusthillguy.netfirms.com/opl3.mp3](http://dusthillguy.netfirms.com/opl3.mp3) - OPL3 FM synth playing "segarally.mid"
[http://dusthillguy.netfirms.com/segarally.mid](http://dusthillguy.netfirms.com/segarally.mid) - source midi file
Like I said, it doesn't sound so good. But maybe someone would like to use it with linux, so I thought I'd post this.

Let me know if you found this helpful or interesting.

---

### Post by jem7v on 2006-10-29
For the record, I've tried it out and Deusiah's method works in Edgy too.

---

### Post by Jeece on 2007-10-04
Hello from france.

Thanks a lot.

All of this tips works fine with my Sound Blaster Audigy 4 PRO under Feisty.

I see someone complaining about his PC to slowdown after loading the Fluid set. Well you have to know that sound bank is effectively loaded in main memory. So such a big bank with only 256M ram is not recommended.

Have a nice day

lspci for info about my sound card :

[FONT="Courier New"]02:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Unknown device 2007
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at 9c00 [size=64]
        Capabilities: [dc] Power Management version 2[/FONT]

---

### Post by mnmus on 2008-07-11
Works beautifully in Hardy (8.04). Funny thing... I had searched many times through the Ubuntu forums using variations of "set up midi" but only (finally!) found this via a search of the forums at [http://www.techspot.com](http://www.techspot.com)!

Also, for those using a SBLive! (as I am doing), a decent soundfont is essential. Here's a freebie based on the Roland GS samples in the venerable SCC1 (still my fav midi card, though in this day of no ISA slots, now retired):

[http://soundfonts.homemusician.net/collections_soundfonts/roland_sound_canvas_tuned.html](http://soundfonts.homemusician.net/collections_soundfonts/roland_sound_canvas_tuned.html)

There are others based on the Roland samples at the same site.

Simply following the directions in this HOWTO, I've freed up my SD-35 external synth for other uses. Nice.

Thanks!

Note: Ubuntu 8.04 64-bit running on AMD 64 X 2 5200+ with 4GiB memory; lil old SBLive! 16-bit card using a soundfont based on the Roland Sound Canvas samples.

---

