---
title: "HOWTO: install amaroK 1.3-beta2"
date: 2005-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by moment on 2005-07-03
**[COLOR=Red]Update2:[/COLOR]** To install the 1.3 final version refer to [this post](http://ubuntuforums.org/showpost.php?p=304006&postcount=54) of this thread.

**[COLOR=Red]Update:[/COLOR]** To install the beta3 refer to [this post](http://ubuntuforums.org/showpost.php?p=297377&postcount=28) of this thread.
--

When I switched from SuSE and KDE to Ubuntu and GNOME the only application that I was missing a lot was amaroK. It's such a good music player. The latest version on hoary is 1.2.3. But the latest beta version has very nice features such as Wikipedia artist lookup, improved sidebar and playlist etc. (changes in [beta1](http://amarok.kde.org/content/view/55/66/) and [beta2](http://amarok.kde.org/content/view/56/66/)). So I decided to compile it myself. Since I'm not a KDE fan anymore I had to download more than 30 devel packages and uninstall them later on which was a pain in the neck. I thought I might save some of you guys who are interesed in amaroK from this hassle. But firstly you need to install all the dependencies yourself (install the amaroK form hoary to have all the dependencies installed and then uninstall the main package and install the beta package instead). After installing the dependencies open a terminal and type:

```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta2-1_i386.deb
sudo dpkg -i amarok_1.3-beta2-1_i386.deb

```

---

### Post by Caboto on 2005-07-03
I agree. Amarok is an absolut great program. Probably one of the best progs, i've installed lately (and that are really many).

The latest package in the backports repos is 1.2.4. Nevertheless, how stable is this Beta release? I would be interested in the new features, but the player should stay as stable as possible, of course.

---

### Post by moment on 2005-07-03
Well as far as I've tested it's working ok and moreover it's the second beta release so a lot of bugs are fixed. The new features worth some rare random crashes  :). Give it a try!

---

### Post by Caboto on 2005-07-03
Okay. I will try it. But it has to wait till tomorrow evening. I'll let you know how good/bad it worked. ;)

---

### Post by hunteramor on 2005-07-06
i enjoy amarok, but my concern for gnome fans that want to use it would be the memory drawbacks of having to install all of those extra libraries.

can anyone quantify how much extra ram is being used to support those libraries, etc., all for just one program?

---

### Post by henriquemaia on 2005-07-06
I really love amarok. Thanks a lot for this package!
The wikipedia feature is amazing. Thanks again.

---

### Post by MikePB on 2005-07-16
I love amaroK, just installed the beta.

I'd drop XMMS for amaroK in a heartbeat if I didn't have to manually advance on m4a files.. :???:

---

### Post by pt123 on 2005-07-16
How do you get the Feature to fill in missing tags of MusicBrainz to work, when I click all it does is to take me to the site's search for the track.

When I click on "Fill In Tags using MusicBrainz"

It says track was not found in MusicBrainz database.

Does anyone know what module is used to perform that, I think I have to install it in Ubuntu.

---

### Post by Mishura on 2005-07-22
I installed that package, but Synaptic keeps complaining that "amarok-arts" and "amarok-gstreamer" is broken.  I can't install anything with Synaptic without uninstalling the gstreamer engine (No engine = no play!).  Is there some replacement packages for the engines somewhere that is 1.3 compatible, or is there a way to LIE to Apt/Synaptic?

---

### Post by johnmc on 2005-07-22
nice one, thank you very much! :)
apt just asked for libtag1 installed - now it works like a charm!

Thanks!

---

### Post by Loungefly on 2005-07-22
I had the same issues that Mishura had . How can I use this  if there are no compatible engines for it? If I try to reinstall the engines in Synaptic it tries to make me install amarok 1.2.4 again  :?

---

### Post by moment on 2005-07-23
[QUOTE=Loungefly]I had the same issues that Mishura had . How can I use this  if there are no compatible engines for it? If I try to reinstall the engines in Synaptic it tries to make me install amarok 1.2.4 again  :?[/QUOTE]
gstreamer is included in the package. Please uninstall previous amarok engines and set the engine to gstreamer in amaroK.

---

### Post by Mishura on 2005-07-24
[QUOTE="moment"]gstreamer is included in the package. Please uninstall previous amarok engines and set the engine to gstreamer in amaroK.[/QUOTE]

OK this worked.  Thanks!  :smile:

---

### Post by manicka on 2005-07-24
Thanks for this. Let us know if you build the next one as well :D

---

### Post by Sephiriz on 2005-08-01
Now that amaroK 1.3-beta3 has been released, after having used your debian package, can we just compile the source to get a new release to work?  Because the way I understood what you supplied, it was simply a way of having all the external libraries needed easily gathered.

---

### Post by manicka on 2005-08-01
I'm just in the middle of trying to compile beta 3 from source and had to share this error message I recieved

ROTFL

```
 = No suitable multimedia framework was detected. You need to install at least
 = one of the supported frameworks as detailed in the amaroK README.
 = If you are thinking, 'I have aRts you stupid configure!', then you probably
 = need to install kdemultimedia-devel.
```

---

### Post by billputer on 2005-08-02
Is anybody working on a package for beta 3?  I'd rather not have to compile it myself.

---

### Post by manicka on 2005-08-02
Beta 3 compiles failry easily and gives clear messages about which packages are needed if you don't have them. The major hassle I had was that it uses taglib 1.4 and hoary/breezy are only using libtag 1.3 . Major problem here was that I didn't know how to create the libtag libraries from source so I compiled a taglib 1.4 package and it seems to be coexisting quite happily with libtag 1.3.

For this reason I wouldn't be that keen on sharing the debs I've made in case it causes trouble for people. If anyone really wants them then I guess I could make them available, but with the usual caveats.

First impresions of beta 3. It seems a bit resource intensive when the main window is open, but okay when minimised to the systray. I also have access to arts and gstreamer as engines with this compile, but have stayed with gstreamer as it has more options and seems more reliable. I also had to rebuild my collection which wasn't that much of a biggy.

Apart from that everything seems pretty much the same as beta 2

---

### Post by Lord Illidan on 2005-08-02
When I type apt-get remove amarok, it tells me..

```
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  amarok amarok-arts amarok-gstreamer amarok-xine kubuntu-desktop
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 12.2MB disk space will be freed.
Do you want to continue [Y/n]?

```

What do I do? I don't want to remove kubuntu-desktop, but I want to install new amarok beta!

---

### Post by Mishura on 2005-08-02
"Kubuntu-desktop" is a meta package, that resolves dependencies and such when you install KDE fresh.  The package itself, doesn't have anything really; and as far as I know its safe to remove.

Try this:  Instead of removing amaroK, remove all the engines, and just upgrade amaroK via .deb package posted here.  *Should* work, but I'm unsure.. its late right now.  *zzZZzz*

---

### Post by thechitowncubs on 2005-08-08
how about beta3

---

### Post by MikePB on 2005-08-09
So, did the devs dump xine? Or did you just not include that? Because I found that xine will auto advance .m4a files while gstreamer won't....

---

### Post by moment on 2005-08-10
[QUOTE=MikePB]So, did the devs dump xine? Or did you just not include that? Because I found that xine will auto advance .m4a files while gstreamer won't....[/QUOTE]
No I didn't include it myself.

---

### Post by xodeus on 2005-08-10
For all of those that really have problems understanding:

Install amarok from hoary's repo.

```
sudo apt-get install amarok
``` 

Then remove amarok and amarok-arts

```
sudo apt-get remove amarok
``` 

Now get the file:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta2-1_i386.deb
``` 

And install:
```
sudo dpkg -i amarok_1.3-beta2-1_i386.deb
```


Attatchment:
amaroK up and running.

---

### Post by Lizzy on 2005-08-10
Hi everyone  :)  ! I'm new here, plus i'm a complete newbie when it comes to Linux . I just wanted to thank you so much for the install-help xodeus. It is the first time i got amarok to work. I tried to install it before and it never worked (no sound). But now i'm happy  \\:D/ .

Thanks again

---

### Post by xodeus on 2005-08-10
[QUOTE=Lizzy]Hi everyone  :)  ! I'm new here, plus i'm a complete newbie when it comes to Linux . I just wanted to thank you so much for the install-help xodeus. It is the first time i got amarok to work. I tried to install it before and it never worked (no sound). But now i'm happy  \\:D/ .

Thanks again[/QUOTE]
 Hi Lizzy. 
All credits to moment, who started this. But you're welcome. Just wanted to make it simple.

---

### Post by MikePB on 2005-08-10
Thanks all of ya for putting this together. I sure as heck wouldn't be getting as proficient with Linux as I am if not for you and people like you.

But I think I'll wait on the latest version until I can get it with xine.. It won't let me have 1.3b2 and install amarok-xine. Keeps "upgrading" back to 1.2

Don't get me wrong, but I can't get gstreamer to advance automatically after playing an m4a file... The length reads something like 6 digits or something. Strangeness.

Bah :P 1.2 works fine for me ^_^

---

### Post by moment on 2005-08-11
[QUOTE=thechitowncubs]how about beta3[/QUOTE]
Although the beta3 is not that much different from beta2 (The most obvious changes are the equaliser presets and podcasting support) I built the deb packages for the beta3 as well (amarok and libtag). But you need to firstly upgrade the libtag1 library to version 1.4:

get them:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/libtag1_1.4-1_i386.deb
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta3-1_i386.deb
```
and install them:
```
sudo dpkg -i amarok_1.3-beta3-1_i386.deb libtag1_1.4-1_i386.deb
```

---

### Post by thechitowncubs on 2005-08-11
[QUOTE=moment]Although the beta3 is not that much different from beta2 (The most obvious changes are the equaliser presets and podcasting support) I built the deb packages for the beta3 as well (amarok and libtag). But you need to firstly upgrade the libtag1 library to version 1.4:

get them:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/libtag1_1.4-1_i386.deb
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta3-1_i386.deb
```
and install them:
```
sudo dpkg -i amarok_1.3-beta3-1_i386.deb libtag1_1.4-1_i386.deb
```[/QUOTE]

yipee, thanks a lot moment  :)  :)  :)

---

### Post by Lizzy on 2005-08-12
Hi again!! Something weird happend after an upgrade... all over sudden, amaroK doesn't work any more. I had to remove amaroK, and tried to install it again the same way as xodeus described.. but when it gets to unpacking the program, i'm told that an error acured regarding dependencies????? I'm a total newbie, and in addition to all this i'm not good with data-stuff (*just a girlie trying to use and understand Linux).. What am i doing wrong? Was it wrong to make an update/upgrade of Ubuntu? I'm having problems figuring out what sound engines to use, how to use them??? 

Sorry for my stupid questions  :confused: 
It's just that i liked the amaroK so much *sniff  ](*,)

---

### Post by Lizzy on 2005-08-12
Hi again... Help
This is the message i receive when i try to install beta2 or in this case beta3????


Selecting previously deselected package amarok.
(Reading database ... 71236 files and directories currently installed.)
Unpacking amarok (from amarok_1.3-beta3-1_i386.deb) ...
Preparing to replace libtag1 1.3.1-1 (using libtag1_1.4-1_i386.deb) ...
Unpacking replacement libtag1 ...
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing amarok (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtag1:
 libtag1 depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing libtag1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amarok
 libtag1

What does that mean??? Got no clue... Do i have to install something???

thx

---

### Post by xodeus on 2005-08-12
[QUOTE=Lizzy]Hi again... Help
This is the message i receive when i try to install beta2 or in this case beta3????


Selecting previously deselected package amarok.
(Reading database ... 71236 files and directories currently installed.)
Unpacking amarok (from amarok_1.3-beta3-1_i386.deb) ...
Preparing to replace libtag1 1.3.1-1 (using libtag1_1.4-1_i386.deb) ...
Unpacking replacement libtag1 ...
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing amarok (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtag1:
 libtag1 depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing libtag1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amarok
 libtag1

What does that mean??? Got no clue... Do i have to install something???

thx[/QUOTE]
 Did you follow all the steps I wrote in one of my previous steps?? [http://ubuntuforums.org/showpost.php?p=294635&postcount=24](http://ubuntuforums.org/showpost.php?p=294635&postcount=24)
Then you can easily update with the commands below.

---

### Post by moment on 2005-08-12
[QUOTE=Lizzy]Hi again... Help
This is the message i receive when i try to install beta2 or in this case beta3????


Selecting previously deselected package amarok.
(Reading database ... 71236 files and directories currently installed.)
Unpacking amarok (from amarok_1.3-beta3-1_i386.deb) ...
Preparing to replace libtag1 1.3.1-1 (using libtag1_1.4-1_i386.deb) ...
Unpacking replacement libtag1 ...
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing amarok (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtag1:
 libtag1 depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing libtag1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amarok
 libtag1

What does that mean??? Got no clue... Do i have to install something???

thx[/QUOTE]

please upgrade your libgcc1 package by downloading it from here:
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb)

and then go to the directory you have downloaded it and install it:
```
sudo dpkg -i libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb
```

and then reinstall libtag and amaroK again. It should be fine.  :-)

---

### Post by Lizzy on 2005-08-12
](*,)  ](*,)  ](*,)  I give up....... this is almost too much for me....
i downloaded the file.... it got downloaded into Home.... like all the other amaroK files... and then what? i extracted them... how do i install them??? 
(I'm realy almost crying, cause i believe i'm too stupid for this=Linux, just startet with it 1 month ago. )

1. i downloaded the file... the file ended up in Home (like all the other amaroK-files)
2. extracted the file.. in the same folder
3. now what?


Guess i need a crash-course in Linux  :roll: 
sorry to bother  :???:

---

### Post by moment on 2005-08-12
Don't get disappointed :D It was my fault that I didn't explain it very well. OK again. You don't need to extract it. After downloading it open a terminal then install it by entering this command in the terminal:

```
sudo dpkg -i libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb
```

---

### Post by Lizzy on 2005-08-12
*crying even more and lowder.....  ](*,) 

I downloaded the file
opened a shell.... and then entered the code...
and then:---->>>> this message came up

 dpkg: error processing libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb

there is something wrong, eighter with my brain or my system *lol

---

### Post by moment on 2005-08-12
It's because your file is not in the home directory. it's probably  on your Desktop. You need to change to the directory that you have downloaded the file:
```

cd ~/Desktop
```

and then issue that command. If that didn't work either do this:```

wget http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb
sudo dpkg -i libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb
```

---

### Post by Lizzy on 2005-08-12
Ok.... thank u ever so much moment, for your tips and for being so nice  :smile: :
So here's what happend.... i managed to download and install the libcc1...successfully... i managed to download and install amaroK beta2...successfully....but... amaroK crashes  :???:  :???:  #-o 

eek.... Now i realy give up.... it worked like a bell yesterday, until i made that horrible mistake and said yes to an update/upgrade for god knows what it was!! *lol

I'm not cring anymore., i'm now laughing about my own stupidity  \\:D/

---

### Post by moment on 2005-08-12
I'm sorry that I couldn't be of any help but did you try the beta3 as well? Follow this post:

[http://ubuntuforums.org/showpost.php?p=297377&postcount=28](http://ubuntuforums.org/showpost.php?p=297377&postcount=28)

PS. do you get any broken packages warning when you open the Synaptic Package Manager (in System -> Administration)? Did you upgrade your Ubuntu usind the red icon that appears in the notification area? In that case you might be able to undo it by looking at the history of synaptic. Hope it helps.

---

### Post by Lizzy on 2005-08-12
thank u ever so much, moment... well, u are a great help!!  :smile: 
i checked there, and i didn't get any message there, but i got it when i first tried to install amaroK.. i probably did something stupid there as well when i clicked on fix broken package *LOL
That is what happens when a girl without data experience tries to go for Linux...
 i asked for it... but i won't go back to MS  [-X 
i'd rather learn something new (the hard way  :grin:  )

thx  ;-)

---

### Post by noelferg on 2005-08-13
I re-installed amarok using xodeus's code.

All seemed to go OK (no error messages).

But when I try to play music, I get this error:

[GStreamer Error] OSS Device "/dev/dsp" is already in use by another program.  :???: 

In the amaroK configure engine page, nothing shows up under device  :???: 

Any help appreciated  !!??

---

### Post by Soulfly on 2005-08-13
[QUOTE=noelferg]I re-installed amarok using xodeus's code.

All seemed to go OK (no error messages).

But when I try to play music, I get this error:

[GStreamer Error] OSS Device "/dev/dsp" is already in use by another program.  :???: 

In the amaroK configure engine page, nothing shows up under device  :???: 

Any help appreciated  !!??[/QUOTE]

Try to find out which program is claiming /dev/dsp  with:

$ fuser -v /dev/dsp

Here you can either kill that program manual or through a terminal ( "fuser -k /dev/dsp" or "kill <pid>" ). I recommend you switch to the gstreamer alsasink in amarok though.

---

### Post by noelferg on 2005-08-13
[QUOTE=Soulfly]Try to find out which program is claiming /dev/dsp  with:

$ fuser -v /dev/dsp

Here you can either kill that program manual or through a terminal ( "fuser -k /dev/dsp" or "kill <pid>" ). I recommend you switch to the gstreamer alsasink in amarok though.[/QUOTE]

PID = 9451 
How do I identify that?

Would I have to kill it manually every time?

How do I switch to gstreamer alsasink? Why?

---

### Post by moment on 2005-08-13
[QUOTE=noelferg]PID = 9451 
How do I identify that?

Would I have to kill it manually every time?
[/QUOTE]

change to alsa instead of esd and get rid of these problems forever. here is a great how to:
[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound+esd](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound+esd)

> 
How do I switch to gstreamer alsasink? Why?
Settings -> Configure amaroK -> Engine -> Output Plugin

---

### Post by noelferg on 2005-08-13
[QUOTE=moment]change to alsa instead of esd and get rid of these problems forever. here is a great how to:
[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound+esd]("http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound+esd")


Settings -> Configure amaroK -> Engine -> Output Plugin[/QUOTE]


 (All sound stopped when I used the quoted link info. Maybe I stuffed up !?)

 Got it working now :D

Using this:

[http://ubuntuguide.org/#configuresoundproperly]("http://ubuntuguide.org/#configuresoundproperly")

---

### Post by yhotg on 2005-08-13
hi
i have a problem with the engine, amarok 1.3 says
that the gstreme can play mp3
i used xine with amarok 1.2
and i read before in the post that you don't.
So, how i get amarok to play mp3 with gstreme?
thanks
yhotg

edit:
the strange thing is that i can play .ogg
so why mp3 is not playing?
maybe i forgot to install some gstreamer file ?

---

### Post by manicka on 2005-08-13
Looks like you have not installed the necessary plugin to play mp3's with gstreamer.

Install the metapackage 

gstreamer0.8-plugins

that way you'll get every plugin available for gstreamer

---

### Post by Rob2687 on 2005-08-13
I installed this then I tried to go back to the one available in apt-get but now no version of Amarok will run :(

---

### Post by manicka on 2005-08-14
[QUOTE=Rob2687]I installed this then I tried to go back to the one available in apt-get but now no version of Amarok will run :([/QUOTE]
 Have you uninstalled the 1.3beta package, as both versions will sit on your system causing conflicts.

---

### Post by yhotg on 2005-08-15
[QUOTE=manicka]Looks like you have not installed the necessary plugin to play mp3's with gstreamer.

Install the metapackage 

gstreamer0.8-plugins

that way you'll get every plugin available for gstreamer[/QUOTE]


just kind of imagined that was what i needed to do. yesterday i started installing all the gstreamer packages until amarok started playing mp3.

thank u very much. 
yhotg

update:
i forgot to say that i used this post 

[http://ubuntuforums.org/showthread.php?t=32770&highlight=gstreamer+mp3](http://ubuntuforums.org/showthread.php?t=32770&highlight=gstreamer+mp3)  [COLOR=Teal](post #2)[/COLOR]

that took me to this post where i found the answer lol

[https://wiki.ubuntu.com//RestrictedFormats#head-d67b20adc8d30f9d239222912aeb42f2e456b36b](https://wiki.ubuntu.com//RestrictedFormats#head-d67b20adc8d30f9d239222912aeb42f2e456b36b)

---

### Post by 8FootSativa on 2005-08-15
1.3 final is out now. :-)

---

### Post by PeP on 2005-08-15
the .deb

[http://pep.homelinux.net/~tonio/](http://pep.homelinux.net/~tonio/)

the install procedure didn't change

please mirror it the site won't be up for so long ...

---

### Post by linzer on 2005-08-16
[QUOTE=PeP]the .deb

[http://pep.homelinux.net/~tonio/](http://pep.homelinux.net/~tonio/)

the install procedure didn't change

please mirror it the site won't be up for so long ...[/QUOTE]

Does this mean libtag needs to be 1.4 or higher?

When I go to install (with libtag1.3.1-1) I get the followiing:


matt@win2k:~/dl$ sudo dpkg -i amarok-1.3_1.3-1_i386.deb
(Reading database ... 81873 files and directories currently installed.)
Unpacking amarok-1.3 (from amarok-1.3_1.3-1_i386.deb) ...
dpkg: error processing amarok-1.3_1.3-1_i386.deb (--install):
 trying to overwrite `/usr/bin/amarok', which is also in package amarok
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 amarok-1.3_1.3-1_i386.deb

Should I remove all of amarok and try again?

tia

---

### Post by PeP on 2005-08-16
>  
 Does this mean libtag needs to be 1.4 or higher?


certainly, follow the above get libtag as posted previously in this thread:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/libtag1_1.4-1_i386.deb

```

then get amarok1.3 final  from me:
```
wget http://pep.homelinux.net/~tonio/amarok-1.3_1.3-1_i386.deb
```
and install both of them:
```
sudo dpkg -i amarok-1.3_1.3-1_i386.deb libtag1_1.4-1_i386.deb
```

Edit: I have kde_3.4.2, and I compiled an x86 version.
Edit 2: corrected the dkpg -i line to fix the first filename.

---

### Post by shanghaipi on 2005-08-16
You messed up your amarok install code...(missing _i386 and you need to replace an underscore with a hyphen).\


Edit:  By the way, thank you for hosting and creating the .deb package.  Amarok kicks so much punani.

---

### Post by XQC on 2005-08-16
Is there any way how to install other amarok-engines, xine-engine in my case?

---

### Post by negatory on 2005-08-16
I've compiled the same thing for amd64...enjoy!
[taglib1.4](http://pwp.netcabo.pt/0245939201/linux/taglib_1.4-1_amd64.deb) 
[amarok1.3](http://pwp.netcabo.pt/0245939201/linux/amarok_1.3-1_amd64.deb)
Pedro Carrico

---

### Post by TheK on 2005-08-16
[QUOTE=PeP]certainly, follow the above get libtag as posted previously in this thread:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/libtag1_1.4-1_i386.deb

```

then get amarok1.3 final  from me:
```
wget http://pep.homelinux.net/~tonio/amarok-1.3_1.3-1_i386.deb
```
and install both of them:
```
sudo dpkg -i amarok_1.3_1.3-1.deb libtag1_1.4-1_i386.deb
```

Edit: I have kde_3.4.2, and I compiled an x86 version.[/QUOTE]

this does not really work that easy, if you come from amarok 1.2, so (this also cleans broken installations). And your libtag1 also does NOT work on hoary! So:

[list]
[*]sudo apt-get remove --purge amarok-*
[*]sudo apt-get install libtag1/hoary
[*]sudo dpkg -i amarok-1.3_1.3-1_i386.deb
[/list]

---

### Post by shanghaipi on 2005-08-16
Libtag works fine on my Hoary.

---

### Post by Alienist on 2005-08-17
[QUOTE=TheK]this does not really work that easy, if you come from amarok 1.2, so (this also cleans broken installations). And your libtag1 also does NOT work on hoary! So:

[list]
[*]sudo apt-get remove --purge amarok-*
[*]sudo apt-get install libtag1/hoary
[*]sudo dpkg -i amarok-1.3_1.3-1_i386.deb
[/list][/QUOTE]

Thanks! Those previous instructions just kind of broke things for me. Yours worked.

---

### Post by manicka on 2005-08-17
[QUOTE=shanghaipi]Libtag works fine on my Hoary.[/QUOTE]
 works fine for me as well

---

### Post by manicka on 2005-08-17
[QUOTE=XQC]Is there any way how to install other amarok-engines, xine-engine in my case?[/QUOTE]

I've compiled a build with checkinstall, that has aRts and xine engines as well. You're welcome to give it a try if you like.

[http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb](http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb)

don't forget the libtag 1.4 package

---

### Post by Ninnghizidha on 2005-08-17
May someone tell me, how i can compile the mysql-support into the source? What packages do i need for this feature?

Ninnghizidha.

---

### Post by Cagnulein on 2005-08-17
[QUOTE=linzer]Does this mean libtag needs to be 1.4 or higher?

When I go to install (with libtag1.3.1-1) I get the followiing:


matt@win2k:~/dl$ sudo dpkg -i amarok-1.3_1.3-1_i386.deb
(Reading database ... 81873 files and directories currently installed.)
Unpacking amarok-1.3 (from amarok-1.3_1.3-1_i386.deb) ...
dpkg: error processing amarok-1.3_1.3-1_i386.deb (--install):
 trying to overwrite `/usr/bin/amarok', which is also in package amarok
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 amarok-1.3_1.3-1_i386.deb

Should I remove all of amarok and try again?

tia[/QUOTE]

same here...

i've tried to `sudo apt-get remove --purge amarok-*` but without success :(
any hints?

---

### Post by manicka on 2005-08-17
[QUOTE=Cagnulein]same here...

i've tried to `sudo apt-get remove --purge amarok-*` but without success :(
any hints?[/QUOTE]
 Try using a search in synaptic and remove all the amarok packages that way

---

### Post by manicka on 2005-08-17
> May someone tell me, how i can compile the mysql-support into the source? What packages do i need for this feature?

Ninnghizidha.

My suggestion would be to install any relevant client, server and dev files. amarok should then pick them up during ./configure

---

### Post by thomax on 2005-08-17
[QUOTE=PeP]certainly, follow the above get libtag as posted previously in this thread:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/libtag1_1.4-1_i386.deb

```

then get amarok1.3 final  from me:
```
wget http://pep.homelinux.net/~tonio/amarok-1.3_1.3-1_i386.deb
```
and install both of them:
```
sudo dpkg -i amarok_1.3_1.3-1.deb libtag1_1.4-1_i386.deb
```

Edit: I have kde_3.4.2, and I compiled an x86 version.[/QUOTE]

Thanx this worked perfectly for me :)

---

### Post by Alienist on 2005-08-17
I should add that **not**  installing the 1.4 lib crashed Amarok every time I started it. So I had to go back to PeP's instructions and just fix the pathways to Amarok, as the snippet he gave was wrong. Right idea but wrong execution. Anyway - working like a charm now. Liking the wiki lookup.

---

### Post by riffic on 2005-08-18
[QUOTE=PeP]certainly, follow the above get libtag as posted previously in this thread:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/libtag1_1.4-1_i386.deb

```

then get amarok1.3 final  from me:
```
wget http://pep.homelinux.net/~tonio/amarok-1.3_1.3-1_i386.deb
```
and install both of them:
```
sudo dpkg -i amarok_1.3_1.3-1.deb libtag1_1.4-1_i386.deb
```

Edit: I have kde_3.4.2, and I compiled an x86 version.[/QUOTE]
was this compiled with mysql support? thanks for compiling.

---

### Post by XQC on 2005-08-18
[QUOTE=manicka]I've compiled a build with checkinstall, that has aRts and xine engines as well. You're welcome to give it a try if you like.

[http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb](http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb)

don't forget the libtag 1.4 package[/QUOTE]
 Works like a charm,
Thanks :)

---

### Post by Mgcross on 2005-08-19
[QUOTE=manicka]I've compiled a build with checkinstall, that has aRts and xine engines as well. You're welcome to give it a try if you like.

[http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb](http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb)

don't forget the libtag 1.4 package[/QUOTE]


I didn't install the libtag 1.4 pakage and it seems to work just fine...except that it wont sent Audioscroble data. Would not installing the libtag pakage cause this? I would really like for this feature to work!

Audoiscrobbler plugin works just fine with Beep Player, but I really don't much like it.

Also, how can I install visualizations without installing XMMS, and is it too late now that I've installed the deb?

Questions questions, lol!


When I try to install the .deb it gives me this error:

dpkg: dependency problems prevent configuration of libtag1:
 libtag1 depends on libgcc1 (>= 1:4.0.0-7); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
dpkg: error processing libtag1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libtag1


has the pakage been updated since this post was made?

---

### Post by marcopse on 2005-08-19
[QUOTE=manicka]I've compiled a build with checkinstall, that has aRts and xine engines as well. You're welcome to give it a try if you like.

[http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb](http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb)

don't forget the libtag 1.4 package[/QUOTE]
It works great, thanx!

---

### Post by GreyDuck on 2005-08-23
[QUOTE=manicka]I've compiled a build with checkinstall, that has aRts and xine engines as well. You're welcome to give it a try if you like.

[http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb](http://members.iinet.net.au/~gracey88/amarok-1.3-1_i386.deb)

don't forget the libtag 1.4 package[/QUOTE]
Manicka's package (and the previously-posted libtag 1.4) for the win! *wry grin*

Working like a charm, here. Whew! I was going nuts trying to hand-compile the damned thing...

---

### Post by arnieboy on 2005-08-23
[QUOTE=GreyDuck]Manicka's package (and the previously-posted libtag 1.4) for the win! *wry grin*

Working like a charm, here. Whew! I was going nuts trying to hand-compile the damned thing...[/QUOTE]
doesnt work for me. installs fine. but when i start amarok, an error message comes up saying that itcant find any sound engines which is understandable cuz when i removed amarok 1.2, amarok-xine, amarok-engines etc all gotremoved. and now i cant get them back with the latest version of amarok.
any suggestions?

---

### Post by thechitowncubs on 2005-08-23
[QUOTE=arnieboy]doesnt work for me. installs fine. but when i start amarok, an error message comes up saying that itcant find any sound engines which is understandable cuz when i removed amarok 1.2, amarok-xine, amarok-engines etc all gotremoved. and now i cant get them back with the latest version of amarok.
any suggestions?[/QUOTE]
 its compiled with a sound engine, so there is no need for an extra package

search libtag and remove that, install the new one, remove old amarok, install the new one

easy as pie.

---

### Post by arnieboy on 2005-08-24
[QUOTE=thechitowncubs]its compiled with a sound engine, so there is no need for an extra package

search libtag and remove that, install the new one, remove old amarok, install the new one

easy as pie.[/QUOTE]
i posted the message after I did all that.. still says it cant find the sound engine...

---

### Post by arnieboy on 2005-08-24
[QUOTE=arnieboy]i posted the message after I did all that.. still says it cant find the sound engine...[/QUOTE]
ok I figured out the solution:
I needed to install the following packages:
kdemultimedia
kdemultimedia-dev
gstreamer0.8-plugins

These 3 packages help set up the aRTs and gstreamer sound engines for amarok

---

### Post by foxy123 on 2005-08-25
well, I have finally noticed that I have to uninstall previous versions of libtag and amarok. Now it works! Thanks a lot.

BTW, has anyone know if it is possible to get rid of konqueror in the amarok. I mean if you click on musicbranz icon and do not have konqueror installed, you've got the following message:
```
Could not launch the browser
Could not find service 'kfmclient'
``` 

kfmclient is a part of konqueror and I doubt if it is possible to install it without it. I just do not install konqueror for that because it tails a huge amount of libraries I do not need.

---

### Post by Caboto on 2005-09-05
[QUOTE=PeP]the .deb

[http://pep.homelinux.net/~tonio/](http://pep.homelinux.net/~tonio/)

the install procedure didn't change

please mirror it the site won't be up for so long ...[/QUOTE]
And nobody did mirror it? :(
It's down now and i didn't get the chance to download it...

Edit: I've tried to compile it for myself and i was astonished that it worked completly fine. But somehow it compiled without the gstreamer engine.. :/ Will have a look at that later.

---

### Post by Dirhael on 2005-09-05
[QUOTE=Caboto]And nobody did mirror it? :(
It's down now and i didn't get the chance to download it...

Edit: I've tried to compile it for myself and i was astonished that it worked completly fine. But somehow it compiled without the gstreamer engine.. :/ Will have a look at that later.[/QUOTE]

For the time being, I'm hosting a copy on one of my servers :)

Get it here:

[http://205.234.98.146/deb/amarok-1.3_1.3-1_i386.deb](http://205.234.98.146/deb/amarok-1.3_1.3-1_i386.deb)

---

### Post by foxy123 on 2005-09-06
has anyone compiled 1.3.1 already?

---

### Post by jobezone on 2005-09-06
Hi, maybe this is late in the thread, but when installing individual .DEB packages, there are only 2 steps to do to have all the depencies installed automatically using apt-get (if they are available from the configured repositories, of course).
Firs step:
```
sudo dpkg -i package.deb
```

This will give some errors that there are unmet dependencies. Then, just tell apt-get to **f**ix everything for you, using:

```
sudo apt-get -f install
```

This will download the dependencies, if they are available in the repositories, and finish installing the previous package.deb.

---

### Post by Magadass on 2005-09-06
[QUOTE=hunteramor]i enjoy amarok, but my concern for gnome fans that want to use it would be the memory drawbacks of having to install all of those extra libraries.

can anyone quantify how much extra ram is being used to support those libraries, etc., all for just one program?[/QUOTE]

Seriously though this should not be an issue to anyone these days should it?  RAM is very very cheap, and in my opinion everyone should have at least 1 gb...

I stopped paying attention to RAM usage along time ago, these days I could really careless how much ram an application uses, but I guess some people are really anal about how much system resources are being used un-necessarily...But in reality if you put it all into perspective and put your retentiveness aside I dont think its a big deal!!

Just had to throw my 2 cents in their, cause I constantly see these comments and I just cant justify why people are still so cautious about memory usage....

---

### Post by foxy123 on 2005-09-09
So what about 1.3.1 with some bugfixes? I would have compiled it myself, but I do not have KDE installed, which many libraries are needed to compile and I would not like to install all of them just to make one package...

---

### Post by w0073r on 2005-09-09
[QUOTE=foxy123]has anyone compiled 1.3.1 already?[/QUOTE]
 I compiled 1.3.1 without a problem (after realizing the gstreamer dev package was under libgstreamer...oops), but am not familiar with how to make packages and such, so I can't give you one. :P

---

### Post by xbaez on 2005-09-09
I am compiling 
**amarok_1.3-beta3-1_i386.deb**

This one includes:
 ==========================
 ===  amaroK - PLUGINS  ========================================================
 ==========================
 =
 = The following extra functionality will be included:
 =   + aRts-engine
 =   + GStreamer-engine
 =   + MAS-engine
 =   + Helix-engine
 =   + MySql support
 =   + Konqueror Sidebar
 =
 ===============================================================================

I can upload it to my website
[http://downloads.gamingaccess.com](http://downloads.gamingaccess.com)
but I will first like to see if people will be willing to go to my website and download it

I don't know and I don't have much time in order to make my site a repository for amarok, and the file I made is called:
amarok_1.3-beta3-1_i386.deb , it's version is **1.3-beta3**
In order to make it "Ubuntu comptabile" it's version should be **2:1.3-beta3**, the file should be called:
amarok_2%3a1.3-beta3-0ubuntu1~5.04ubp2_i386.deb

Anyway, installation is easy and I've used it for over a month now, and it works GREAT

All you have to do is
1) download the libtag and amarok .deb files (I can upload them today)
2) upgrade libtag with a .deb file I've already made
3) remove all the amarok deb files
4) install this one

The main feature that I like of amarok is that
1) You'll have lots of engines to chose and features:
 =  + MySQL Support apart from SQLite
 =   + aRts-engine
 =   + GStreamer-engine
 =   + MAS-engine
 =   + Helix-engine
 =   + MySql support
 =   + Konqueror Sidebar
2) One .deb file includes all these features, you can select the engine that works best (for me it's gstreamer with autoconf)
3) compatible with Ubuntu Hoary (and possible Breezy)
4) You can install plugins such as lyrics and have fetched lyrics for your songs, and you have a nice WIKI Information

I will open a new thread asking people if they will be willing to go to my site and download these, I haven't seen many .deb for amarok.

I will also like to learn how to make a .deb file with it's version 2:1.3-beta3

Regards

---

### Post by foxy123 on 2005-09-09
[QUOTE=xbaez]I am compiling 
**amarok_1.3-beta3-1_i386.deb**

This one includes:
 ==========================
 ===  amaroK - PLUGINS  ========================================================
 ==========================
 =
 = The following extra functionality will be included:
 =   + aRts-engine
 =   + GStreamer-engine
 =   + MAS-engine
 =   + Helix-engine
 =   + MySql support
 =   + Konqueror Sidebar
 =
 ===============================================================================

I can upload it to my website
[http://downloads.gamingaccess.com](http://downloads.gamingaccess.com)
but I will first like to see if people will be willing to go to my website and download it

I don't know and I don't have much time in order to make my site a repository for amarok, and the file I made is called:
amarok_1.3-beta3-1_i386.deb , it's version is **1.3-beta3**
In order to make it "Ubuntu comptabile" it's version should be **2:1.3-beta3**, the file should be called:
amarok_2%3a1.3-beta3-0ubuntu1~5.04ubp2_i386.deb

Anyway, installation is easy and I've used it for over a month now, and it works GREAT

All you have to do is
1) download the libtag and amarok .deb files (I can upload them today)
2) upgrade libtag with a .deb file I've already made
3) remove all the amarok deb files
4) install this one

The main feature that I like of amarok is that
1) You'll have lots of engines to chose and features:
 =  + MySQL Support apart from SQLite
 =   + aRts-engine
 =   + GStreamer-engine
 =   + MAS-engine
 =   + Helix-engine
 =   + MySql support
 =   + Konqueror Sidebar
2) One .deb file includes all these features, you can select the engine that works best (for me it's gstreamer with autoconf)
3) compatible with Ubuntu Hoary (and possible Breezy)
4) You can install plugins such as lyrics and have fetched lyrics for your songs, and you have a nice WIKI Information

I will open a new thread asking people if they will be willing to go to my site and download these, I haven't seen many .deb for amarok.

I will also like to learn how to make a .deb file with it's version 2:1.3-beta3

Regards[/QUOTE]

I wonder why you are compiling 1.3beta3, while 1.3.1 is already available?

---

### Post by xbaez on 2005-09-10
Didn't noticed that, I can make a package for that one, but that wouldn't be neccesary if that version will come with Breezy

---

### Post by xbaez on 2005-09-10
I've checked Breezy and noticed that version 1.3 is not there, so maybe there's a point in compiling this .deb file of amarok, anyone interested?

Brezzy seems to include version 1.2.4

---

### Post by yhotg on 2005-09-10
[QUOTE=foxy123]So what about 1.3.1 with some bugfixes? I would have compiled it myself, but I do not have KDE installed, which many libraries are needed to compile and I would not like to install all of them just to make one package...[/QUOTE]

hi, 
sorry but i don't get your meaning.
i found 2 .deb of 1.3.1 here in this same thread (or i am wrong?)

in the first post u have an update2 pointing u to  
[http://ubuntuforums.org/showpost.php?p=304006&postcount=54](http://ubuntuforums.org/showpost.php?p=304006&postcount=54)
that's a post in this same thread with one .deb (i think it comes with gstreamer)

and the second one is
[http://ubuntuforums.org/showpost.php?p=305253&postcount=62](http://ubuntuforums.org/showpost.php?p=305253&postcount=62)
with xine

or you r talking about a newer version than those?

 :wink:  yhotg

---

### Post by zer on 2005-09-10
> or you r talking about a newer version than those?
Yes, as you can see on the [amarok page](http://amarok.kde.org/component/option,com_frontpage/Itemid,66/), the newest version is 1.3.1, not 1.3-1 :)
I want it!!!! ....but i don't know how i could get a deb-file.

---

### Post by foxy123 on 2005-09-10
[QUOTE=yhotg]hi, 
sorry but i don't get your meaning.
i found 2 .deb of 1.3.1 here in this same thread (or i am wrong?)

in the first post u have an update2 pointing u to  
[http://ubuntuforums.org/showpost.php?p=304006&postcount=54](http://ubuntuforums.org/showpost.php?p=304006&postcount=54)
that's a post in this same thread with one .deb (i think it comes with gstreamer)

and the second one is
[http://ubuntuforums.org/showpost.php?p=305253&postcount=62](http://ubuntuforums.org/showpost.php?p=305253&postcount=62)
with xine

or you r talking about a newer version than those?

 :wink:  yhotg[/QUOTE]
both are 1.3... 1.3.1 was out only a few days ago...

---

### Post by yhotg on 2005-09-10
[QUOTE=zer]Yes, as you can see on the [amarok page](http://amarok.kde.org/component/option,com_frontpage/Itemid,66/), the newest version is 1.3.1, not 1.3-1 :)
I want it!!!! ....but i don't know how i could get a deb-file.[/QUOTE]

LOL!!!!
i thought the 1.3.-1 was a typo when they made the .debs 
haha

oks then forget what i said.

I Want The 1.3.1 too lol
but i can wait too 'cos the 1.3.-1 is working well enough lol

---

### Post by foxy123 on 2005-09-11
I have built an Ubuntu 1.3.1 package. The problem it does not have alsasink in gstreamer engine... I will try to figure out what is wrong and rebuild it... I have not got a webspace to upload it though :(

---

### Post by shizow on 2005-09-11
[QUOTE=PeP]
then get amarok1.3 final  from me:
```
wget http://pep.homelinux.net/~tonio/amarok-1.3_1.3-1_i386.deb
```[/QUOTE]

cant connect to this server

wget [http://pep.homelinux.net/~tonio/amarok-1.3_1.3-1_i386.deb](http://pep.homelinux.net/~tonio/amarok-1.3_1.3-1_i386.deb)
--12:26:14--  [http://pep.homelinux.net/%7Etonio/amarok-1.3_1.3-1_i386.deb](http://pep.homelinux.net/%7Etonio/amarok-1.3_1.3-1_i386.deb)
           => `amarok-1.3_1.3-1_i386.deb'
Resolving pep.homelinux.net... 82.228.125.118
Connecting to pep.homelinux.net[82.228.125.118]:80...  

but then nothing happens

---

### Post by xbaez on 2005-09-12
If you want you can send it to [email]downloads@socceraccess.com[/email] and I'll upload it tomorrow
in around 5 minutes I expect to provide the URL with the link to the following files:
amarok_1.3.1-1_i386.deb (allthough it was made with a AMD XP Processor, so it is k7 compatible as well)
libtag (version 1.4.1)

this one includes:
MySQL
Helix
NAS
and more

---

### Post by xbaez on 2005-09-12
Ok I've uploaded both files to my server, here is the link for you to download:
Here is the link
[http://downloads.gamingaccess.com/index.php?cat_id=317](http://downloads.gamingaccess.com/index.php?cat_id=317)

Amarok built by Xavier Baez, totally compatible with Ubuntu/Kubuntu Hoary Hedgegod 5.04 and possibly compatible with Breezy. The latest version of Amarok includes cool features such as WIKI, Lyrics (you can install plugins such as lyrics in order to have fetched lyrics as well)
<br>
This special build includes:
Gstreamer (alsa, oss, gaudioconfig...),Helix, MySQL, MAS... support, ALL the engines that you can get from the ./configure script have been included
<br>
<b>INSTRUCTIONS</b>
1) check that you have all the dependencies:
<i>artsbuilder (>= 4:3.4.0), kdelibs4 (>= 4:3.4.0), konqueror (>= 4:3.4.0), libart-2.0-2 (>= 2.3.16), libarts1 (>= 1.3.2), libasound2 (>> 1.0.8), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.2.ds1-4), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libflac6, libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0.0-7), libglib1.2 (>= 1.2.0), libglib2.0-0 (>= 2.6.0), libgstreamer0.8-0 (>= 0.8.9-1), libgtk1.2 (>= 1.2.10-4), libice6 | xlibs (>> 4.1.0), libidn11 (>= 0.5.2), libjpeg62, libmusicbrainz4 (>= 2.1.1), libmysqlclient14 (>= 4.1.10a), libogg0 (>= 1.1.2), libpcre3 (>= 4.5), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libqt3c102-mt (>= 3:3.3.3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libtag1 (>= 1.4-0), libtunepimp2 (>= 0.3.0), libvorbis0a (>= 1.0.1), libvorbisenc2 (>= 1.0.1), libvorbisfile3 (>= 1.0.1), libx11-6 | xlibs (>> 4.1.0), libxcursor1 (>> 1.1.2), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxi6 | xlibs (>> 4.1.0), libxinerama1, libxml2 (>= 2.6.17), libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxt6 | xlibs (>> 4.1.0), xmms, zlib1g (>= 1:1.2.1)</i>
2) install libtag version 1.4 #dpkg --install libtag1_1.4-0_i386.deb
2) remove amarok (all engines, I recommend using synaptic and removing everything that starts with amarok)
3) install this new version of amarok #dpkg --install amarok_1.3.1-1_i386.deb
4) you can go to synaptic, search for amarok, and lock the version so that you won't be bugged about updating amarok.

---

### Post by xbaez on 2005-09-12
I recommend you to use **Gstreamer Engine** and use the output plugin Gconfaudiosink

I've tried with all the engines:
Helix
Gstreamer
aRTS
MAS

And that one seems to use a reasonable ammount of memory (using aRTS for example makes Arts and amarok use much more VMemory Size)

I really hope some downloads, my first work in Linux :)

---

### Post by shanghaipi on 2005-09-12
where do i get all those packages that are dependent upon amarok..they aren't in the repositories...

localbob@ubuntu:~$ sudo dpkg -i amarok_1.3.1-1_i386.deb
Password:
(Reading database ... 76012 files and directories currently installed.)
Preparing to replace amarok 1.3.1-1 (using amarok_1.3.1-1_i386.deb) ...
Unpacking replacement amarok ...
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on artsbuilder (>= 4:3.4.0); however:
  Package artsbuilder is not installed.
 amarok depends on kdelibs4 (>= 4:3.4.0); however:
  Package kdelibs4 is not installed.
 amarok depends on konqueror (>= 4:3.4.0); however:
  Package konqueror is not installed.
 amarok depends on libarts1 (>= 1.3.2); however:
  Package libarts1 is not installed.
 amarok depends on libmusicbrainz4 (>= 2.1.1); however:
  Package libmusicbrainz4 is not installed.
 amarok depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
 amarok depends on libtunepimp2 (>= 0.3.0); however:
  Package libtunepimp2 is not installed.
dpkg: error processing amarok (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amarok

---

### Post by foxy123 on 2005-09-12
[QUOTE=xbaez]Ok I've uploaded both files to my server, here is the link for you to download:
Here is the link
[http://downloads.gamingaccess.com/index.php?cat_id=317](http://downloads.gamingaccess.com/index.php?cat_id=317)
[/QUOTE]

How did you enable ALSA support in gstreamer? I tried to build amarok twice and in both time I did not have alsasink...

your version is very much for Kubuntu unfortunately.... needs Konqueror to be installed... it is what I have been trying to avoid...

---

### Post by xbaez on 2005-09-12
Shangapi:
#apt-get remove amarok
#apt-get install artsbuilder kdelibs4 konqueror libarts1 libmusicbrainz4 libqt3c102-mt libtunepimp2
#dpkg --install amarok_1.3.1-1_i386.deb

Please tell me if it worked OK
I'm enjoying amarok 1.3 for over a month and this .deb really works great with Ubuntu, dependencies and everything

Look what I see when I try to install that software:
#apt-get install artsbuilder kdelibs4 konqueror libarts1 libmusicbrainz4 libqt3c102-mt libtunepimp2

Reading package lists... Done
Building dependency tree... Done
artsbuilder is already the newest version.
kdelibs4 is already the newest version.
konqueror is already the newest version.
libarts1 is already the newest version.
libmusicbrainz4 is already the newest version.
libqt3c102-mt is already the newest version.
libtunepimp2 is already the newest version.

**0 upgraded, 0 newly installed, 0 to remove and 82 not upgraded**

---

### Post by shanghaipi on 2005-09-12
This is what I get

localbob@ubuntu:~$ sudo apt-get remove amarok
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  amarok
0 upgraded, 0 newly installed, 1 to remove and 98 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 76010 files and directories currently installed.)
Removing amarok ...
localbob@ubuntu:~$ sudo apt-get install artsbuilder kdelibs4 konqueror libarts1 libmusicbrainz4 libqt3c102-mt libtunepimp2
Reading package lists... Done
Building dependency tree... Done
Package kdelibs4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs4c2 kdelibs4-dev
E: Package kdelibs4 has no installation candidate

then again, I forgot that I'm running breezy.....oops

---

### Post by vassalle on 2005-09-14
Im using Kubuntu Breezy Preview. Tried installing libtag and this is what i get :
```
 vassalle@st0c:~/downloads$ sudo dpkg --install libtag1_1.4-0_i386.deb
Selecting previously deselected package libtag1.
dpkg: regarding libtag1_1.4-0_i386.deb containing libtag1:
 libtag1c2 conflicts with libtag1
  libtag1 (version 1.4-0) is to be installed.
dpkg: error processing libtag1_1.4-0_i386.deb (--install):
 conflicting packages - not installing libtag1
Errors were encountered while processing:
 libtag1_1.4-0_i386.deb

```
should i remove libtaglc2 ?

---

### Post by foxy123 on 2005-09-14
[QUOTE=vassalle]Im using Kubuntu Breezy Preview. Tried installing libtag and this is what i get :
```
 vassalle@st0c:~/downloads$ sudo dpkg --install libtag1_1.4-0_i386.deb
Selecting previously deselected package libtag1.
dpkg: regarding libtag1_1.4-0_i386.deb containing libtag1:
 libtag1c2 conflicts with libtag1
  libtag1 (version 1.4-0) is to be installed.
dpkg: error processing libtag1_1.4-0_i386.deb (--install):
 conflicting packages - not installing libtag1
Errors were encountered while processing:
 libtag1_1.4-0_i386.deb

```
should i remove libtaglc2 ?[/QUOTE]
you'd better to ask in Breezy forum, since the libtag and amarok here are compiled in Hoary. There is a thread in Breezy about compiling amarok as I remember...

---

### Post by yhotg on 2005-09-14
hi again.
how's working the 1.3.1.-1?
r already all the engines included and working ?

or better to wait a little more? lol

---

### Post by shanghaipi on 2005-09-14
Yes, remove the libtag that is in the repositories if you are running Breezy.  If you notice, that version is still 1.3 and not libtag 1.4.  Unfortunately, running the Amarok 1.3.1 is not possible in Breezy right now, unless you want to hunt down all those needed .deb files on the internet.  Just stay with 1.3 right now, backports are coming for Breezy in just a month.

---

### Post by yhotg on 2005-09-14
[QUOTE=shanghaipi]Yes, remove the libtag that is in the repositories if you are running Breezy.  If you notice, that version is still 1.3 and not libtag 1.4.  Unfortunately, running the Amarok 1.3.1 is not possible in Breezy right now, unless you want to hunt down all those needed .deb files on the internet.  Just stay with 1.3 right now, backports are coming for Breezy in just a month.[/QUOTE]

i was talking about hoary.

---

### Post by xbaez on 2005-09-18
I have compiled amarok 1.3 (all engines) + libtag, compatible with Ubuntu Hoary 5.04
[http://downloads.gamingaccess.com/index.php?cat_id=317](http://downloads.gamingaccess.com/index.php?cat_id=317)

---

### Post by xbaez on 2005-09-18
shanghaipi are you running Breezy already?

I made amarok 1.3 and libtag 1.4 for the Hoary users, what error do you have?

The good thing about my build is that you ONLY need to
1) uninstall amarok and all the amarok* packages
2) install libtag
3) install amarok

so basically the ONLY package that changes is libtag1.4, the rest of your Hoary is the same as it was before.

Besides I've read that version 1.2 will be included in Breezy

---

### Post by GameManK on 2005-09-18
i'm trying to compile amarok 1.3.1 on kubuntu with a k7 kernel

i get this error when trying to ./configure or ./configure --prefix=`kde-config --prefix` (which is what the readme says to do):

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

what do i do?

EDIT: problem solved by installing kdemultimedia-dev

---

### Post by yhotg on 2005-09-21
hi again:

i saw this on the amarok site today:

amaroK Airborne 1.3.2
Tuesday, 20 September 2005

so, where r we now? is there somebody trying to do the .deb?

---

### Post by xbaez on 2005-09-23
I've made the .deb for amarok 1.3.1
[http://downloads.gamingaccess.com](http://downloads.gamingaccess.com), search for 'amarok'

---

### Post by foxy123 on 2005-09-23
[QUOTE=xbaez]I've made the .deb for amarok 1.3.1
[http://downloads.gamingaccess.com](http://downloads.gamingaccess.com), search for 'amarok'[/QUOTE]
1.3.2 got alsasink fix... could you build it as well? I may try on weekend on the another pc (this one has a dependency hell for some reasons)...

---

### Post by yhotg on 2005-09-24
[QUOTE=xbaez]I've made the .deb for amarok 1.3.1
[http://downloads.gamingaccess.com](http://downloads.gamingaccess.com), search for 'amarok'[/QUOTE]

well  i finally got over my pop up-add dislike and went to your site and got amarok 1.3.1
it sounds Great!

and it has the splash screen of my in use theme! nice!

i, now, have a technical question:

why gstreamer and no xine?

i don't know the difference between both engines, but as xine was the first one i got actually working in my first week of linux i since then had a soft spot for it.

(i am being subjective or amarok 1.3.1 sounds better?))

---

### Post by yhotg on 2005-10-06
hi again, some weeks have passed
there's nobody with the amarok 1.3.2 .deb package?

pls pls pls??changed to 

;-)


Or have u all upgraded to breezy already?

---

### Post by wirjo on 2005-10-10
I tried to install amarok 1.3, but I get this:

 amarok depends on libgcc1 (>= 1:4.0.0-7); however:
 Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.

Does anyone know how I can fix this?

---

