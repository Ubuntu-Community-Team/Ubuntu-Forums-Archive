---
title: "Guitar Pro (5) on Ubuntu Dapper Drake 6.06/Wine"
date: 2006-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by sebastfr on 2006-08-31
For people willing to use Guitar Pro (GP5) on their Ubuntu (this was the last program that kept me using Windows, yeepee), here's a summary on how to proceed (I gathered a few tutorials together, sorry no references as I don't have them handy).

1- Install wine:

sudo apt-get install wine

2- Get some font files from a Windows box (windows/fonts/*.ttf) and copy them to ~/.wine/drive_c/windows/fonts (assuming you kept the default wine setttings). I guess you can get the fonts files from somewhere else, but this is the way I did it.

3- Install Guitar Pro:

winelauncher [path to your guitar pro install file (the exe)]

I didn't select the RMS sound banks but feel free to give it a go.

Guitar Pro should install smoothly (leave the default options).

4- Run Guitar Pro for a try:

winelaucher ~/.wine/drive_c/Program\ Files/Guitar\ Pro\ 5/GP5.exe

That should work fine, make sure the notes/menus display normally (otherwise you may still miss some fonts files).

Don't expect any sound at this stage, unless you have setup MIDI already.

5- Install timidity (which can also convert midi to wave on the fly which is what we need here)

sudo apt-get install timidity timidity-interfaces-extra

6- Install some better sound patches for timidity (if you want)

wget -c -O /tmp/timidity-patches-eaw \
[http://www.fbriere.net/debian/dists/etch/misc/deb/](http://www.fbriere.net/debian/dists/etch/misc/deb/) \
timidity-patches-eaw_12-0fbriere.1_all.deb

sudo dpkg -i /tmp/timidity-patches-eaw.deb

sudo gedit /etc/timidity/timidity.cfg

Change:

"source /etc/timidity/freepats.cfg"

to:

"source /usr/share/doc/timidity-patches-eaw/examples/timidity.cfg"

And remove the temp file:

rm /tmp/timidity-patches-eaw

Check Timidity works:

timidity [whatever MIDI file]


7- Start Timidity as ALSA sequencer:

First check the snd_seq module is loaded:

lsmod | grep snd_seq

if not:

sudo modprobe snd_seq

Then:

timidity -iA -B2,8 -Os &

You should see a few lines looking like:

opening port 128:1 128:2 [etc..]

From then you should have the sound working on guitar pro.

8- Last test

Start guitar pro, load a gp file. 

Check the MIDI configuration is OK on guitar pro:

Click on Options/MIDI Setup and check ports 1-4 maps to timidity (if not select 'timidity in the drop-down list, assigning a different timidity port to each port). Make sure you don't select 'Midi Through' (this is for midi input).

Play the file, enjoy! And now, write a few scripts which automate the process!


Seb

---

### Post by CaptainBommel on 2006-09-15
Hi! Thank you for this, it workED fine.

Ok, no problems anymore. It's running fine. Some performance problems but nothing that's too hard too use the prog...thanks again:cool:

---

### Post by vinnytrix on 2006-09-21
Worked like a charm, than you :)

---

### Post by Xecuter on 2006-09-23
Ah thanks man! I've been having trouble with playback. I will try this when I get home! ;)

---

### Post by jd_ on 2006-09-23
If Guitar Pro 5 displays messy fonts, you can copy **[msttcorefonts]("http://packages.ubuntu.com/dapper/x11/msttcorefonts")** fonts from [FONT="Courier New"]/usr/share/fonts/truetype/msttcorefonts/[/FONT] in [FONT="Courier New"]~/.wine/drive_c/windows/fonts/[/FONT].

You must have [FONT="Courier New"]Guitar Pro 5.ttf[/FONT] in this folder, too.

---

### Post by aeto on 2006-09-23
hey man thanks, especially on the midi part. i'v been running gp5 for a while on wine but i had somehow set a sequencer to run on boot..it was kinda messy & sometimes other apps cant play midi files or vice-versa. now the midi issues r solved..no problems yet.

---

### Post by smithveg on 2006-10-27
Hi,

seems i'm the one who can not install guitar pro successfully. Someone helps me.

I'm using Guitar Pro 4 Demo.
I run the installation, lisk what in this thread said, as below.
winelauncher [path to your guitar pro install file (the exe)]
Then, i run, i notice that the font missing.

Then i donwload the msstcorefont in /user/share/... and copy all the font .ttf file into /.wine/drive_c/windows/fonts/ directory.

Then i run again, why the same problems occur? The errors as below,
==
veg@veg-desktop:~$ winelauncher ~./wine/drive_c/Program\Files/Guitar\Pro\4\Demo/GP4Demo.exe
Invoking /usr/bin/wine ~./wine/drive_c/ProgramFiles/GuitarPro4Demo/GP4Demo.exe ...
wine: cannot find '~./wine/drive_c/ProgramFiles/GuitarPro4Demo/GP4Demo.exe'
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Wine failed with return code 2
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
veg@veg-desktop:~$
==

Someone can helps me...

---

### Post by metalsam on 2006-10-28
This guide looks great!

when I install GP4, i installed msttcorefonts, but the installer give me loads of jibberish characters and music symbols arther than letters. Anyone know how to fix this ?

---

### Post by sebastfr on 2006-10-31
RE the problem with GP4:

I haven't tried to install GP4 (only GP5)... But you're just missing some font files, it's just the matter of knowing which one(s) :)

Could you...

1/ Check that you have a 'Guitar Pro x.ttf' file under :~/.wine/drive_c/windows/fonts ? (Mine is 'Guitar Pro 5.ttf')

2/ Try to install GP4 on a Windows machine and see what font files get installed?

Good luck,

Seb

---

### Post by metalsam on 2006-11-02
I have a GPro.ttf file under my wine fonts.

Anyone know what hte fonts file is on windows ?

---

### Post by AstarothCY on 2007-01-28
Has anyone worked out a way to improve the performance? MIDI works but it's impossible to play anything, it stutters all over the place.

---

### Post by AstarothCY on 2007-01-31
bump

---

### Post by AstarothCY on 2007-02-02
anyone?

---

### Post by AstarothCY on 2007-02-06
bump?

---

### Post by Ixnay on 2007-02-10
I installed Guitar Pro 5 and it works fine, except for the sound...when I installed timidity, all I could select as a midi output device was "Midi Through Port-0". So why can't I select timidity as an output device? I installed it just as you told, except the patches...it told me I already have the newest version. So what did I do wrong???

Thanks,
Chris

---

### Post by AstarothCY on 2007-02-10
Have you done this step:

```
timidity -iA -B2,8 -Os &
```

?

I need to do it for every reboot or else the Timidity ports don't appear.

---

### Post by Ixnay on 2007-02-10
yea and this is what comes out:

```

chris@chris-desktop:~$ timidity -iA -B2,8 -Os &
[1] 7774
chris@chris-desktop:~$ ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'default'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')


```

I have no idea if any of this is good or bad

---

### Post by AstarothCY on 2007-02-10
You need to configure your ALSA drivers properly, your problem is not in Timidity or GP. Look for the ALSA Tutorials.

---

### Post by Ixnay on 2007-02-10
ehm thanks, but I couldn't find anything seeing as I have no clue what I'm supposed to look for...so naturally I used my instincts and installed everthing that started with "alsa" via the synaptic package manager and now I can't even select an input device in GP5 :D

---

### Post by adam0509 on 2007-02-10
French version @ [http://doc.ubuntu-fr.org/tutoriel/wine_et_midi?s=wine%20midi](http://doc.ubuntu-fr.org/tutoriel/wine_et_midi?s=wine%20midi)

(It works for all Win32-MIDI apps BTW !)


There's a cool free program to replace Guitar-Pro, it's called **"TuxGuitar"**, and is very very very very very very very very nice ^^


Check the website : [www.tuxguitar.com.ar](www.tuxguitar.com.ar)

:guitar:

---

### Post by Ixnay on 2007-02-10
I can't remember much of the french I learned...but from what I saw...do they uninstall timidity and install some weird piano thingy? :D...if that will get my guitarpro 5 to work then Ill do it!

---

### Post by AstarothCY on 2007-02-10
I suggest you search for keywords related to your audio hardware, find a Tutorial on how to install drivers for it, reinstall them completely, and try again. If it still doesnt work, try redoing all of the guitar pro tutorial.

---

### Post by Ixnay on 2007-02-10
I clicked on the little sound thingy at the top to see which device was enabled, and it says I have two: [0] HDA NVidia (Alsa mixer) and [1] Realtek ALC883 (OSS Mixer)

the Nvidia one is currently enabled...or should I use the other one?

here is what I found: [http://www.alsa-project.org/](http://www.alsa-project.org/) ...the newest driver?

---

### Post by AstarothCY on 2007-02-10
I cannot really help you with this since I am a bit of a beginner myself, but try reading through this tutorial:

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by Ixnay on 2007-02-10
thanks Ill try it out

---

### Post by Ixnay on 2007-02-10
nah it's hopeless...everytime I try to run alsamixer when it should work, it doesn't...oh well...

---

### Post by 417xray on 2007-03-04
Great posts here thank all for the information.  I finally got the sound working in GP5 but how do I pass the timidity parameters to GP5 for the MIDI output options?  When ever I reboot I run the script for launching the snd_seq and timidity but have to manually enter the MIDI output options in GP5 proper.  Is there any work around for this or is this a WINE limitation?

Thanks again,
John

---

### Post by sympeltun on 2007-03-04
nice! it works, but it's a note or two behind the actual line.. still it works im happy for that

---

### Post by PaulW89 on 2007-04-01
Hi there,

I installed GP5 + timidity and it runs fine under wine.
But everytime I start Guitar Pro 5, i have to register it again. All my settings are gone.

Is there a way to avoid that?

I'm using xubuntu 7.04.

Hope you can help me ;)

Best,
Paul

---

### Post by Typhon on 2007-05-08
I created mimetype icons to use with TuxGuitar, KGuitar, and Guitar Pro files. [Check them out](http://www.kde-look.org/content/show.php?content=57892). :)

---

### Post by DrumScum on 2007-08-11
Hi,

You can also use QSynth/Jack to get sound from GP5. Has very good performance on my system.

---

### Post by acl123 on 2007-09-29
I've just got Guitar Pro 5 working under wine and Ubuntu 7.04.
Everything seems ok except...

I can't see text comments and notations such as tapping, slapping etc. that are made above the tab lines.

Also, some gp5 files I can't open. It says that I need to upgrade guitar pro.

Anyone managed to solve these issues?

---

### Post by AstarothCY on 2007-09-29
As far as some gp5 files not opening, that's because files edited in Guitar Pro 5.1 are not compatible with Guitar Pro 5 (very stupid oversight by the developers, that's all).

---

### Post by trias100 on 2007-10-22
Guys thanks it worked for me. Very good instructions. I am a newbie on Linux but the more i learn the less i appreciate microsoft... :) ty for all guys. You :guitar: :)

---

### Post by necromancer13 on 2007-10-25
Thanks a ton....works 4 me...:guitar:

---

### Post by AstarothCY on 2007-10-26
so you guys don't have any slowdown? it's REALLY slow for me, i can't really play anything back because it stutters so much. maybe i should completely reinstall wine and try again...

---

### Post by AstarothCY on 2007-11-12
bump, i did a complete reinstall (of ubuntu and everything else) and the problem is the same.. basically the program runs very slowly and when you play something back it stutters because its so slow.

---

### Post by acl123 on 2007-11-30
Waaa
Guitar Pro was working great for a few months but now its just died.
I was trying to install my webcam and something I did killed it.

Firstly, when I started it up, it would give me some error messages (see below). Then it would work fine except that I got no sound.

I reinstalled it and now it won't even play any songs. It crashes with a French error message.

I can't select the Audio Preferences without it crashing.

Waaa... what can I do :(


> 
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 0
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 1
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:1
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
ALSA lib conf.c:3949: (snd_config_expand) Unknown parameters 2
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL default:2
fixme:mixer:ALSA_MixerInit No master control found on UA-25, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on Camera , disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x34f820,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x30060,0x00000000,200,2): stub!


---

### Post by AvionicAvionic on 2008-02-08
**hello everybody**, I am new on Ubuntu, (my third day) I once tried SuSe and RedHat server edition but was different, now returned with ubuntu. here is the problem, (maybe you already solved it on past posts but I tried to see how does feel to post:) )
[COLOR="Red"]does the given wine method for 6.06 works for 7.04?[/COLOR]
I use 7.04 and need something like guitarpro 5, My Xp is still on the c partition. but I dont want to use it anymore, [COLOR="red"]How can I use guitarpro 5 on ubuntu 7.04 and is there any equivalent of guitarpro 5 for linux[/COLOR]?



*ohh I speak too muchhh*

---

### Post by Krokkan on 2008-02-11
Works great on ubuntu 7.10!
However, installing this sound patch was quite tricky, but eventually I made it work))

---

### Post by AstarothCY on 2008-02-11
so does it run at a good speed or is it really slow when you're playing the music?

---

### Post by Krokkan on 2008-02-12
It works quite smoothly. 
However, there is some slow down when I try to open or move windows of other application or do something in GPro (scroll up or downwards:)). With or without RSE - doesn't matter at all)))

---

### Post by diwas on 2008-03-22
I have configuration 512MB RAM and integrated Audio Card. Guitar pro's install was succesfull but it is really very slow. Very slow means really very slow. I dont know wats the problem.
On top of that...the app wont properly maximise.
Any suggestions?

---

### Post by AstarothCY on 2008-03-22
FINALLY another person with the same problem. I don't know why it's slow but I've been trying this on ever release since Edgy and it has always behaved exactly the same.

---

### Post by diwas on 2008-03-24
Actually, I have given up. I have dual boot XP and Ubuntu 7.10. I wanted myself completely isolated from the M$ area but Iam helpless with 2 softwares: Guitar Pro 5.2 and Windows Media Player 11. These two softwares always makes me long towards XP.

BTW do you also have the maximise problem??

---

### Post by babyfoxx on 2008-03-28
Thank you for the "how to". I got mine running smoothly, but when I go to play the song part it fades in. Anyone know how to change that? Other than that, it rocks. :guitar:

---

### Post by gladstone on 2008-04-02
> **diwas said:**
> I have configuration 512MB RAM and integrated Audio Card. Guitar pro's install was succesfull but it is really very slow. Very slow means really very slow. I dont know wats the problem.
On top of that...the app wont properly maximise.
Any suggestions?
"Very very slow" here also :( Unusable for me unfortunately, so I'm on the look out for some alternatives

---

### Post by elchico04 on 2008-04-05
It isn't extremely slow for me, It is definately a little choppy unless the file is only 1 track. I exported files as midi and played them back outside of guitar pro and they work fine so it must be some problem with guitar pro running with wine.

I didn't use the guide here to change my midi sounds but the guide here was really easy and worked for me
[http://josefhuber.com/index.php?option=com_content&view=article&id=12&Itemid=1](http://josefhuber.com/index.php?option=com_content&view=article&id=12&Itemid=1)

also the guide asks you to download a soundfont file, you can download it a lot faster from this torrent
[http://thepiratebay.org/tor/3726467/Soundfont_Package](http://thepiratebay.org/tor/3726467/Soundfont_Package)

(you only need the Musica Theoria file so don't waste your time downloading the others)

---

### Post by diwas on 2008-04-06
May be bcoz its a "Windows" program...but the memory management of Linux is good compared to windows isnt it? So y isnt it runnin smoothly?

---

### Post by NemX162 on 2009-03-01
Hello all, I have gotten GP5 working on my Ubuntu 8.10, except for the notes, both tab and standard notation, are displayed out-of-line.  It makes it very hard to read because you can't tel what string it's on... I've tried installing the font over and over.

Does it have to be in the fonts folder in the GP5 folder, or in thew windows fonts folder?  I've tried it each way, both at the same time, and I even deleted the font and it does the same thing.  

What's going on?

---

### Post by Rasheeke on 2009-03-10
I'm having the same problem as someone mentioned before and nobody else seems to talk about it, upon startup the splash is fine but then it crash with some French error message.  

How do I fix this?

---

### Post by diwas on 2009-03-10
Can you please post a screenshot?

---

### Post by czsergey on 2009-05-29
> **diwas said:**
> Can you please post a screenshot?

Have the same problem (tested in 96 & 120 dpi fonts).
The problem started after upgrade to Kubuntu Jaunty (with KDE 4.2.2).
In Kubuntu Intrepid (with KDE 3.5.10) works fine.
Screenshots attached.

Additional info:
WINE 1.1.22
GP 5.2 (01/18/2007)

---

### Post by theguitarfreak on 2009-07-02
when i run thesudo dpkg -i /tmp/timidity-patches-eaw.deb command i get the following error. i have followed the previous steps of the guide correctly and there also seems to be a timidity-patches-eaw file in my tmp folder.

dpkg: error processing /tmp/timidity-patches-eaw.deb (--install):
 cannot access archive: No such file or directory

---

### Post by nandagopal on 2009-08-04
i installed guitar pro as per your instructions.
.when i open guitar pro i even get the opening sound and all the menus and all are perfect but it gives an error.
i have to force quit.it's not possible to close this message

 

/////////////////////////////////////////////
Violation d'acces a l'addresse 39840950 dans le module gdiplus.dll'.Lecture de l'adresse 00000048 
/////////////////////////////////////////////
is this error to be expected if timidity is not installed or is it some other problem?
please help.
this program is one of the last reasons i am sticking on to windows.

---

### Post by Feareilo on 2009-08-22
Thanks a lot!
Works great on a Pentium IV 1.8GHz, 512Mb RAM with Jaunty Jackalope.

EDIT:
I hadn't tested an actual GP file, just the GP jingle. The sound sucks. As someone mentioned earlier, it stutters and is really slow. Thanks for the tutorial though. It helped some.

---

### Post by Shugs81 on 2009-08-23
> **nandagopal said:**
> i installed guitar pro as per your instructions.
.when i open guitar pro i even get the opening sound and all the menus and all are perfect but it gives an error.
i have to force quit.it's not possible to close this message

 

/////////////////////////////////////////////
Violation d'acces a l'addresse 39840950 dans le module gdiplus.dll'.Lecture de l'adresse 00000048 
/////////////////////////////////////////////
is this error to be expected if timidity is not installed or is it some other problem?
please help.
this program is one of the last reasons i am sticking on to windows.

I get this same message.... anyone managed to get past it?

I already seem to have sound as it plays the little jingle thing on the splash screen... but as i get that error message can't do anything else... could it be the RSE being installed....

I'll apologize as I'm doing this in a spare minute... haven't had chance to scour the thread yet...

oh... and I'm using 9.04 too....

---

### Post by theboycalcoen on 2009-09-29
I solved the French error by deleting the gdiplus.dll file.

---

### Post by uffargh on 2009-10-04
Great walktrough.

I seem to be suffering crashes while employing RSE. I've tried a few things, among others is to copy .dll files from the GPfolder to the system32 folder - too bloody bad it's not working?

Has anyone gotten RSE going?

---

### Post by Thrasherrich on 2009-11-02
I moved to Ubuntu 9.10 from XP because i thought Tuxguitar would be the same, but when i open guitar pro files in it they dont play :( i'm trying to write a song for my college work aswell so its pretty annoying considering i don't know any drummers, bassists or more Guitarists lol

And this is too complicated for me :o i might try later but i know i'll go wrong.

---

### Post by AstroPhysik on 2009-11-03
> **Thrasherrich said:**
> I moved to Ubuntu 9.10 from XP because i thought Tuxguitar would be the same, but when i open guitar pro files in it they dont play :( i'm trying to write a song for my college work aswell so its pretty annoying considering i don't know any drummers, bassists or more Guitarists lol

And this is too complicated for me :o i might try later but i know i'll go wrong.

I have ubuntu 9.04,   32 + AMD64 Bit operating systems. And Tuxquitar works well with guitar pro files.
u can send me your faulty file, if its working at my setup, you have another issue :)
There were some sound erros, with some intel HDA Sound Chips, but they should be resolved...
BTW: Which Hardware do u have?

greetz AP

---

### Post by vlada92 on 2009-12-12
Ohh THX UU!! This worked FINEEEEEEEEE ;DD

---

### Post by AverellTorrent on 2010-04-24
Is it possible to get RSE and Midi playback working at the same time?  It seems that I can get one or the other to work by screwing with the settings a little, but I have a song with a piano (so no RSE) and a bass guitar that sounds awful unless it's RSE.

---

