---
title: "can't play Mp3"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by MordL on 2008-08-02
Hello,
i just can't play mp3 i tried everything i saw a forums but it seems it won't work when im going 2 play an mp3 with all the ubuntu programs it just says Error (null) . But when i try to play them at itunes they work... the prob is that when i use itunes my whole pc freeze so i don't think it's a solution, Any help? i tried reinstalling gstreamer or istalling bonus packages or that libflashsupport but nothing seem to worked.

--I use Ubuntu 8.04

---

### Post by northern lights on 2008-08-02
First, check whether the package 'ubuntu-restricted-extras' is installed. Simply run ```
sudo apt-get install ubuntu-restricted-extras
```if it already was installed apt will not alter a thing

---

### Post by MordL on 2008-08-02
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

it seems i have :)

---

### Post by sayakb on 2008-08-02
Which application are you playing your mp3s in? Does it play on vlc? Invoke the application from a terminal and post any error messages while trying to play an mp3

---

### Post by MordL on 2008-08-02
how can i run an application thought the terminal?  im new to linux =)

---

### Post by sayakb on 2008-08-02
Suppose you are using rhythmbox, just open a terminal (System->Accessories->Terminal) and type in 
```
rhythmbox
```
Which application are you using btw?

---

### Post by northern lights on 2008-08-02
> **MordL said:**
> how can i run an application thought the terminal? :D im new to linux =)

Drop any mp3 file into your home folder. Navigate to "Applications > Accessories > Terminal". In the newly opened window type ```
totem FILENAME.mp3
```where filename needs to be replaced by the actual filename.

Alternatively to putting the file into home, you could also run ```
totem /path/to/file/FILENAME.mp3
```or```
cd /path/to/file
totem FILENAME.mp3
```

Of course, instead of totem you can also execute your player of choice.

---

### Post by ApOgEEs on 2008-08-02
Hi MordL,

Forget the terminal for a while. 

If you want to play mp3 on your Ubuntu, you have to install the decoder for mp3. Here's how to install it.

> 1. Click on **System > Administration > Synaptic Package Manager**
2. Enter your password.
3. Click on search and type "gstreamer mp3" (without quote marks)
4. then right click on **gstreamer0.10-fluendo-mp3** or any newer version of this decoder and Click on "Mark for Installation"
5. Click on Apply

when you're done, you may now play mp3. Feel free to ask more if this didn't work for you. :)

---

### Post by MordL on 2008-08-02
ah... alt+f2 did the work that's the error that came out i used it in amaroc rymth vlc already
on vlc:
VLC media player 0.8.6e Janus
[00000309] main decoder error: no suitable decoder module for fourcc `wmal'.
VLC probably does not support this sound or video format.
[00000284] main playlist: nothing to play



on totem:
 Message: don't know how to handle audio/x-asf-unknown, codec_id=(int)355
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2284): prepare_output (): /play

** Message: Missing plugin: gstreamer|0.10|totem|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (audio/x-asf-unknown decoder)
no application found
** Message: No installation candidate for missing plugins found.
** Message: don't know how to handle audio/x-asf-unknown, codec_id=(int)355
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2284): prepare_output (): /play

** Message: Missing plugin: gstreamer|0.10|totem|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
** Message: All missing plugins are blacklisted, doing nothing

---

### Post by sayakb on 2008-08-02
See this: [http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)
And add medibuntu to your repository and install w32codecs package.
Now try playing them again.

---

### Post by MordL on 2008-08-02
ApOgEEs, i have that already installed :)

---

### Post by ApOgEEs on 2008-08-02
Odd, Have you tried to play mp3 using Rhythmbox?

**Applications > Sound & Video > Rhythmbox Music Player**

---

### Post by MordL on 2008-08-02
ApOgEEs,ofc :D Sooo LinuxIsInnovation i tried what u said with medibuntu
my connection is slow so i just finished dling the w32codecs still no sound :S

---

### Post by MordL on 2008-08-02
any ideas? :P

---

### Post by bigbrovar on 2008-08-02
ok try this it always works for me and am sure it would for you

open terminal (Applications/Accessories/Terminal) copy and paste this command and hit enter ..

```
 sudo apt-get install ubuntu-restricted-extras vlc libdvdcss2 ubuntu-restricted-extras w32codecs libxine1-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

when u are done try playing an mp3 file and its see what happens

---

### Post by MordL on 2008-08-02
> **bigbrovar said:**
> ok try this it always works for me and am sure it would for you

open terminal (Applications/Accessories/Terminal) copy and paste this command and hit enter ..

```
 sudo apt-get install ubuntu-restricted-extras vlc libdvdcss2 ubuntu-restricted-extras w32codecs libxine1-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

when u are done try playing an mp3 file and its see what happens
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.

S:

---

### Post by bigbrovar on 2008-08-02
hmmm could be that not all of ur repositories are enabled .. or u didnt run a full update of the system cus ordinarily it shouldnt give that error .. so ( yeah i know u said ur internet sucks) run a ```
sudo apt-get update
``` again and make sure that it runs till ur prompt is returned .. u can do this via synaptic .. just click the reload buttom .

---

### Post by MordL on 2008-08-02
nah... still nothing

---

### Post by bigbrovar on 2008-08-02
hey i just found out that ur problem could be a rhythmbox specific issue .. u could try installing amarok or banshee or exaile all better than rythmbox 

```
sudo apt-get install amarok banshee exaile 
```
or open synatics and search amarok , banshee , exaile 

right click , mark for install, apply. apply 
lets know it went

---

### Post by MordL on 2008-08-02
Nop it's not working aswell :S i had amarok already but it seems it didn't worked again :S

---

### Post by bigbrovar on 2008-08-02
ok we will beat this .. but i need u to work with me .. dont give up :)

open terminal and run amarok  from there .. then attempt to use it to play an mp3 file and post the output ...

---

### Post by bigbrovar on 2008-08-02
> and post the output ...  i meant the output that terminal displays when the sound is being played .. btw .. do u get any sound on login this could be a general sound problem with ur system .. just a thought

---

### Post by MordL on 2008-08-02
i can't open amarok from terminal it just close on boot screen i tried opening it with the mp3 it still does the same :S i posted errors previusly from Rhyth and VLC tho

---

### Post by MordL on 2008-08-02
Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x440001c
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x440001c


"dunno if that helps"

---

### Post by bigbrovar on 2008-08-02
ok this is getting really interesting .. but that is how u learn :)
i think they must have been a problem with the amarok config files we can fix this by deleting the amarok folder which is hidden somewhere in ur home dir 

so run this  
```
rm -rf ~/.kde/share/apps/amarok
``` 
which would delete the amarok folder hidden in ur home dir ... this would reset amarok to default setting .. now start amarok again from terminal and let me see the output

---

### Post by MordL on 2008-08-02
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d7f8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809d7f8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

that's the new

---

### Post by bigbrovar on 2008-08-02
so does it start amarok .. if yes .. try playing an mp3 file and lets see what happens

---

### Post by MordL on 2008-08-02
that's what happen when i try play an MP3 :D owh the same error as b4 aswell :S 

dimos@dimos-desktop:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x42000dc
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x42000dc
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
ICE default IO error handler doing an exit(), pid = 30748, errno = 11

---

### Post by bigbrovar on 2008-08-02
i had a similar problem when i  started  ubuntu some years ago.. i solved it by removing all the codecs i installed all the gstreamers then installing them from fresh .. so try ```
sudo apt-get remove --purge ubuntu-restricted-extras vlc libdvdcss2 ubuntu-restricted-extras w32codecs libxine1-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll amarok totem-gstreamer totem-common totem-plugins totem-plugins-extra totem-xine

```
  that should completely remove all the codecs on the system .. when this is done 
 restart the system then install them back with ```
sudo apt-get install ubuntu-restricted-extras vlc libdvdcss2 ubuntu-restricted-extras w32codecs libxine1-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll amarok totem-gstreamer totem-common totem-plugins totem-plugins-extra totem-xine
```

---

### Post by robertchahine on 2008-08-02
supposing you have mplayer installed.
Go to the terminal and use the "cd" command to enter the directory where you have the music file then
```

mplayer themusicfile

```.
Don't forget that the terminal is case sensitive that means there's difference between "This" and "this"(capital letters.).
If you don't have mplayer installed
then ```
sudo apt-get install mplayer
```

---

### Post by AndyCooll on 2008-08-02
> **robertchahine said:**
> supposing you have mplayer installed.
Go to the terminal and use the "cd" command to enter the directory where you have the music file then
```

mplayer themusicfile

```.
Don't forget that the terminal is case sensitive that means there's difference between "This" and "this"(capital letters.).
If you don't have mplayer installed
then ```
sudo apt-get install mplayer
```
Let's not confuse the guy, he's already been asked to install Amarok, vlc, Exaile and Banshee!

The issue is with codecs and not audio players. Ideally he should be able to play an mp3 using either of the default installed players (Rhythmbox or Totem).

By default, when you open up either Rhythmbox or Totem, then navigate to an mp3 and try playing that file it should bring up a message saying that it can't play the file and you need to install a codec. It should offer to install that file. Did it do that originally?

And while we're at it, if you click System > Administration > Software Sources on the "Ubuntu Software" tab do you have all the sources underneath 'Downloadable from the Internet' ticked? 

:cool:

---

### Post by MordL on 2008-08-02
eh wt... ok i tried the solution u told me... Not working :S both of them :( any help? :<

---

### Post by MordL on 2008-08-02
i guess im the only that much ****** up?

---

### Post by AndyCooll on 2008-08-02
> **MordL said:**
> eh wt... ok i tried the solution u told me... Not working :S both of them :( any help? :<
And EXACTLY what did you try (step-by-step)? EXACTLY What error messages did you get? And EXACTLY what software sources do you have ticked? 

:cool:

---

### Post by MordL on 2008-08-02
> **AndyCooll said:**
> Let's not confuse the guy, he's already been asked to install Amarok, vlc, Exaile and Banshee!

The issue is with codecs and not audio players. Ideally he should be able to play an mp3 using either of the default installed players (Rhythmbox or Totem).

By default, when you open up either Rhythmbox or Totem, then navigate to an mp3 and try playing that file it should bring up a message saying that it can't play the file and you need to install a codec. It should offer to install that file. Did it do that originally?

And while we're at it, if you click System > Administration > Software Sources on the "Ubuntu Software" tab do you have all the sources underneath 'Downloadable from the Internet' ticked? 

:cool:

ehh.. Can't explain this more :D i just had all tickets up now... i purged and reinstalled everything from the terminal including apt-get autoclean
so that's the 2 thing that was told :S still no sound or anything should a ubuntu reinstall solve this thing?

---

### Post by northern lights on 2008-08-02
> **MordL said:**
> should a ubuntu reinstall solve this thing?Yes. But it also should not be necessary.

It might be helpful to answer a direct question such as one of Andy's with a suitable answer.

E.g: Question "Software sources checked?" - Answer "Yes / No / which"

Are you trying to play the same file or are you varying files?

---

### Post by MordL on 2008-08-02
Yea!! and i tried over 20 different files :S

---

### Post by MordL on 2008-08-04
Reinstalling Linux Solved the problem. :D ty for every1 that helped

---

### Post by linuxisevolution on 2008-09-18
> **MordL said:**
> Reinstalling Linux Solved the problem. :D ty for every1 that helped

I have the same problem, but don't want to reinstall. I tried to:



winrid@winrid-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for winrid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: ubuntu-sounds but it is not going to be installed
E: Broken packages


so i tried:

sudo apt-get install ubuntu-sounds


and that went well, but didn't fix my problem!


I try to play it in Totem and i get:

An error occurred

The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed.


I tried everything on this forum, PLEASE HELP

---

### Post by northern lights on 2008-09-18
Archeology!

Creating a new thread might be the better option.

---

### Post by wblack on 2008-11-06
I'm having a similar problme. I have Banshee and Rythmbox and Totem. They used to work fine. Then a few weeks ago something happened and now they don't play mp3's or any other files. ITs loads the file (it shows the length of the file anyways) and then nothing happens. I tried rinstalling Rythmbox, didn't help. And i tried some of the fixes in here too but that didn't help. I'm at a loss at this point.

---

