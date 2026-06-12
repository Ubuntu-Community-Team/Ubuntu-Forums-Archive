---
title: "HOWTO: Get Sound Juicer to rip MP3's"
date: 2004-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by emperor on 2004-10-16
"gststreamer0.8-mad" seems to only allow Rhythmbox to play MP3, does not
enable Sound Juicer to rip MP3's

To rip MP3's with Sound Juicer, you you will need to install the following:
1. liblame0                         (in another world)
2. gstreamer0.8-lame    (this one is in a galaxy, outside our universe!)

The other world is: (add to Synaptic's repositories list if not already there!)
ftp:ftp.nerim.net.debian-marillat/         unstable      main

This particular galaxy is located at:
[http://henrik.synth.no/deb/](http://henrik.synth.no/deb/)

First install liblame0 using apt or synaptic.
Then download and install gstreamer's lame as follows:

dpkg -i gstreamer0.8-lame_0.8.2-2_i386.deb


FYI, here is the Info from the thread on the web detailing how the gstreamer0.8-lame deb was build:

1. fetch a gstreamer-lame RPM. I got mine from
   [http://rpm.pbone.net/index.php3?stat=3&amp;search=gstreamer-lame](http://rpm.pbone.net/index.php3?stat=3&amp;search=gstreamer-lame)
   (Choose gstreamer-lame v0.6 for sound-juicer v0.5.10, or v0.8 for
   sound-juicer v0.5.12+. I used a PLD package.)
2. alien gstreamer-lame*.rpm
3. dpkg -i gstreamer-lame*.deb

---

### Post by TimL on 2004-10-27
Thanks for the howto.

Unfortunately, when I first ran sound-juicer (without the lame and gstreamer-lame packages installed) it greyed-out the MP3 radio button after I tried to select it, because no encoder was available. Now that I've followed your howto, that button is *still* greyed out and I can't select it!

Do you know how to re-enable that option? I've searched for a config file, but haven't come across anything that looks like it'll fix it yet.

---

### Post by emperor on 2004-10-28
It is possible that lame & mp3 support has not been registered. Try running "gstreamer-register"  in a terminal for your login account (not using sudo).

---

### Post by TimL on 2004-10-28
[QUOTE=emperor]It is possible that lame & mp3 support has not been registered. Try running "gstreamer-register"  in a terminal for your login account (not using sudo).[/QUOTE]
 I got there eventually!

After posting here. I then stumbled across the gst-register-0.8 command.
I ran that, but STILL couldn't get MP3 playback.

In the end, I thought it was a bug and submitted it to the sound-juicer bugzilla.
The maintainer of sound-juicer then explained that it wasn't a bug and I was using the wrong version of gstreamer-lame (I was using 0.6 rather than 0.8 )

I didn't spot that in your howto. I could have saved myself hours of messing about if I had!

---

### Post by Allen S on 2004-11-21
The packages liblame0 & gstreamer-lame0.8 don't seem to be available from the listed sources for an AMD64 install. Any ideas where to find these files for the AMD64?

Thanks
Allen

---

### Post by hkctr on 2004-11-22
Both of the required debs can be found here in one convenient repository:
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

---

### Post by Lennart on 2004-12-18
Tried to follow the above instructions, but something must be wrong. When entering the ftp address into synaptic, it won't recognize the address/folder.
I tried to find the liblame package "in the wild" but didn't know which one to choose (distro).
Any help would be much appreciated.

---

### Post by emperor on 2004-12-21
Repository that has liblame0
 
 URI: ftp:ftp.nerim.net/debian-marillat/
 Distribution: unstable
 Section: main

---

### Post by unperson on 2005-01-04
You can also follow this guide to build gstreamer0.8-lame from source in the ubuntu universe repository:

[http://www.columbia.edu/~jr2075/gstreamer-lame-how-to.html](http://www.columbia.edu/~jr2075/gstreamer-lame-how-to.html)

It does require that you've grabbed lame and liblame-dev, for example from the marillat repository.  The advantage to this is not having to grab a binary package from some less well known repository.

Nick

---

### Post by steffen on 2005-01-05
Sound Juicer doesn't give you any options for encoding oggs or mp3s in a specific bitrate, does it? At least, mine doesn't...

Anyone know how to change the bitrate?

---

### Post by unperson on 2005-01-05
[QUOTE=steffen]Sound Juicer doesn't give you any options for encoding oggs or mp3s in a specific bitrate, does it? At least, mine doesn't...

Anyone know how to change the bitrate?[/QUOTE]

I noticed this immediately myself.  I have no idea if there's any way to change it in Sounds Juicer.  The next thing I did was download grip, which seems to offer a bit more control.  I still haven't actually used it yet, though.  It's also not clear if it's using constant bitrate, average bitrate, or variable bit rate encoding.  (not sure if the last two are different in generally, but they seem to refer to different things in lame)

---

### Post by emperor on 2005-01-06
[QUOTE=steffen]Sound Juicer doesn't give you any options for encoding oggs or mp3s in a specific bitrate, does it? At least, mine doesn't...
 
 Anyone know how to change the bitrate?[/QUOTE]
 
 The bitrates for flac, ogg, and wav files "may ?" be adjustable using the GConf editor. (system - gstreamer - 0.8 - audio - profiles - (cdlossless, cdlossy, voice). I did not have a profile that appears to be used for mp3 files. I also have not fiddled with the settings.

---

### Post by kanem on 2005-01-07
Goobox is another Gnome ripper that seems to be just like Sound-juicer except that it allows you to pick the bitrate (for ogg, not for mp3) and it's also a cd player

To get it to rip mp3s I had to do all the stuff listed above in this thread to get Sound-juicer to.

Edit: had a link here to it's site at GnomeFiles ([http://www.gnomefiles.org/](http://www.gnomefiles.org/)) but it's no longer there.
Edit: and now it's back: [http://www.gnomefiles.org/app.php?soft_id=531](http://www.gnomefiles.org/app.php?soft_id=531)

---

### Post by steffen on 2005-01-07
Unfortunately my Creative Zen Micro Jukebox (PMP) doesn't allow me to play other files than .mp3, .wma and .wav. It doesn't accept my .oggs. So I have to rip in .mp3, and be able to set the bitrate.

I used a ripper in Fedora, which ripped in wav and converted to mp3s or oggs, where I was able to set the bitrate. But I don't remember the name of it... :(

---

### Post by emperor on 2005-01-08
[QUOTE=steffen]I used a ripper in Fedora, which ripped in wav and converted to mp3s or oggs, where I was able to set the bitrate. But I don't remember the name of it... :([/QUOTE]
 
 I am also a Fedora user; in fedora I used ***Grip*** to rip to mp3 format.
 I have both sound-juicer and Grip installed and working in Ubuntu.

---

### Post by Humboldt on 2005-01-10
Go to: Applications -> System Tools -> Configuration Editor.
In the configuration editor click 

-> system -> gstreamer ->-profiles -> cdlossy

Then go to the line "pipeline". In the end of that line set the quality. I think this should work. Tell me if it does.

---

### Post by miss tina on 2005-01-11
hi, maybe ya should try[COLOR=YellowGreen] cripple[/COLOR]
its a commandline cdriptool, download the source compile and install.
i've been searching and testing a lot of rippers, grip did the job a time ago, but that was on my gentoo-box, in Ubuntu things where quite frustrating when ripping, i only could rip at speed 2 :evil: That's when i tested cripple... fast, i could even rip 3cd's at once!, 
The problem is that with this kernel(a recent 2.6) cdparanoia doesn't work well, cdda2wav wil work faster, So use the command like this:

[COLOR=YellowGreen] cripple -S 12 -R cdda2wav -d /dev/sr0[/COLOR]

this will rip the cd in devive sr0 (a firewire dvd-burner) with the cdda2wav codec, it will provide high quality variable bitrate mp3 streams.
use  cripple --help for options...
greertz tina

---

### Post by steffen on 2005-01-12
[QUOTE=Humboldt]Go to: Applications -> System Tools -> Configuration Editor.
In the configuration editor click 

-> system -> gstreamer ->-profiles -> cdlossy

Then go to the line "pipeline". In the end of that line set the quality. I think this should work. Tell me if it does.[/QUOTE]

Just did it. Doesn't work.

I set the quality to 0.2 instead of the default 0.5. Sound Juicer still rips in 256 Kbps, 44KHz stereo, and files are just as big.

---

### Post by steffen on 2005-01-13
There are three options in the system configuration for gstreamer
- cdlossless
- cdlossy
- voice

cdlossy is the only one having a quality= string in the pipeline. I thought that the problem might be that soundjuicer is by default using the cdlossless encoding profile. So I went in to the pipeline of cdlossless, and added 'quality=0.5'.

However, it didn't change anything  :sad: Still ripping huge files!

There really should be someone out there who knows what to do about this. I refuse to believe that everyone in the Linux world are content with ripping mp3s at 256 kbps for their poor mp3-sticks.

---

### Post by Humboldt on 2005-01-13
[QUOTE=steffen]There are three options in the system configuration for gstreamer
- cdlossless
- cdlossy
- voice

cdlossy is the only one having a quality= string in the pipeline. I thought that the problem might be that soundjuicer is by default using the cdlossless encoding profile. So I went in to the pipeline of cdlossless, and added 'quality=0.5'.

However, it didn't change anything  :sad: Still ripping huge files!

There really should be someone out there who knows what to do about this. I refuse to believe that everyone in the Linux world are content with ripping mp3s at 256 kbps for their poor mp3-sticks.[/QUOTE]

Well, Steffen. One solution could be to download goobox, wich is another ripping tool for gnome. In goobox you can set the quality parameter when you rip. Goobox is also a cdplayer. I haven't found any debian packages for the latest version however, and the version I got - 6.0 can't write m3u playlist files however. (The new version sould be able to do that) For playlists I use a music player for gnome called muine.  I like muine better than rhythmbox actually.

I'm still trying to find out how to set the encoding quality for soundjuicer in gconf-editor. I did an experiment and found out that it doesnt matter if you erease the quality value competly (leaving it blanq). It encodes the same bitrate anyway. I can't figure out why however. If anyone can explain this it would be nice.

Regards

---

### Post by Humboldt on 2005-01-20
I have found a very nice tool called "abcde". It is a tool for cd ripping and encoding. It's not a graphical tool, but a command line tool - a script actually - but it is not difficult to use - it's very easy. It does averyting for you. Just put the cd in the tray, launc a console window, write abcde, ansver a couple of simple questions, and then it do everything for you. Very effective and simple. I don't know if it's in Ubuntus resopitories. I picked mine from Debians testing.

Good luck

---

### Post by chele on 2005-01-27
[QUOTE=unperson]You can also follow this guide to build gstreamer0.8-lame from source in the ubuntu universe repository:

[http://www.columbia.edu/~jr2075/gstreamer-lame-how-to.html](http://www.columbia.edu/~jr2075/gstreamer-lame-how-to.html)

It does require that you've grabbed lame and liblame-dev, for example from the marillat repository.  The advantage to this is not having to grab a binary package from some less well known repository.

Nick[/QUOTE]Does this work for PPC? I have found repositories with liblame, but nothing with gstreamer0.8-lame. Nor does the liblame-dev package appear to be available for PPC.

---

### Post by chele on 2005-01-27
[QUOTE=chele]Does this work for PPC? I have found repositories with liblame, but nothing with gstreamer0.8-lame. Nor does the liblame-dev package appear to be available for PPC.[/QUOTE]Yes.

The repository to use is:

deb [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/) unstable/

~$ sudo apt-get update
~$ sudo apt-get install liblame-dev
~$ sudo apt-get source gstreamer0.8-misc
~$ cd gst-plugins0.8-0.8.7/
~$ ./configure --prefix=/usr
~$ cd ext/lame
~$ make
~$ sudo make install
~$ sudo gst-register-0.8

I now choose MP3 as an option in Sound Juicer. And 1/2 an hour later, I have ripped an audio CD to MP3. Why it takes so long, I am no sure. Something to do with Apple hardware I hear.

---

### Post by RunningWild on 2005-01-27
it works! nice tip :D

---

### Post by reedlaw on 2005-02-17
I've got liblame0 and gstreamer-lame installed but I get no option in Sound Juicer for MP3.  In fact, it is not even greyed out on my version 2.9.91 of Sound Juicer (on Hoary).  I only have the options for cdlossless, cdlossy, or raw.  I can edit the cdlossy format in configuration editor but I don't know what I need to change to get MP3 encoding.  My current cdlossy configuration is:
/system/gstreamer/audio/profiles/cdlossy/pipeline
audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5

---

### Post by Marquis_de_Carabas on 2005-02-17
One of the first things I did after installation was "sudo apt-get remove sound-juicer; sudo apt-get install grip" Maybe it's just because it's what I'm used to, but I much prefer [Grip](http://nostatic.org/grip/), and it's ridiculously easy to change the bitrate, and any other option you care to mention.

---

### Post by will_rat on 2005-03-04
[QUOTE=reedlaw]I've got liblame0 and gstreamer-lame installed but I get no option in Sound Juicer for MP3.  In fact, it is not even greyed out on my version 2.9.91 of Sound Juicer (on Hoary).  I only have the options for cdlossless, cdlossy, or raw.  I can edit the cdlossy format in configuration editor but I don't know what I need to change to get MP3 encoding.  My current cdlossy configuration is:
/system/gstreamer/audio/profiles/cdlossy/pipeline
audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5[/QUOTE]

once you have the gstreamer-lame encoder installed you can rip mp3s using any setting that lame enables. I alter the GConf key...

/system/gstreamer/audio/profiles/cdlossy/

to

extension mp3
pipeline audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1002

* changed vorbisenc to lame
* changed extension from ogg to mp3
* changed quality=0.5 to preset=1002

I got the preset=1002 from the plugin settings -- to find out what options you can use 

* install the gstreamer pipline editor
* run it from the programming menu
* From the Utility Palette window select Codec->Encoder->Audio->lame
* From the Properties window (you may need to enable it from the View menu item if it is now visible)
* Look at all the properties you can select!
* Enter any options you want into the pipeline key (as above with the preset option)

Now open sound-juicer and select cdlossy.

Much nicer than grip

Will

---

### Post by pedrorolo on 2005-03-29
[QUOTE=will_rat]once you have the gstreamer-lame encoder installed you can rip mp3s using any setting that lame enables. I alter the GConf key...

/system/gstreamer/audio/profiles/cdlossy/

to

extension mp3
pipeline audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1002

* changed vorbisenc to lame
* changed extension from ogg to mp3
* changed quality=0.5 to preset=1002

I got the preset=1002 from the plugin settings -- to find out what options you can use 

* install the gstreamer pipline editor
* run it from the programming menu
* From the Utility Palette window select Codec->Encoder->Audio->lame
* From the Properties window (you may need to enable it from the View menu item if it is now visible)
* Look at all the properties you can select!
* Enter any options you want into the pipeline key (as above with the preset option)

Now open sound-juicer and select cdlossy.

Much nicer than grip

Will[/QUOTE]

nicer my ass... the options are all in strange codes and there are 3 diferent lames: lame0, lame1, lame2... and by the way... where is ABR???

---

### Post by Muchacho_Gasolino on 2005-04-01
heres what i get when i try to apt-get update(or the synaptic equivalent) with marillat's repository

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

my repository is set in synaptic as
type binary
url [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
distribution unstable
section main

---

### Post by Marquis_de_Carabas on 2005-04-02
[QUOTE=Muchacho_Gasolino]heres what i get when i try to apt-get update(or the synaptic equivalent) with marillat's repository

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

my repository is set in synaptic as
type binary
url [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
distribution unstable
section main[/QUOTE]

That shouldn't affect the installation of those packages, but you should be able to solve the problem by importing the relevant public key, as described on [Christian Marillat's site](ftp://ftp.nerim.net/debian-marillat/index.html).

---

### Post by Muchacho_Gasolino on 2005-04-02
hmm ill try that but when i apt-get install liblame0, it returns couldn't find package liblame0
i am running AMD64, could that be the problem?

edit: shoot, it was, should have read the site better

anyway, i got liblame in  :D

for any amd64 users having this problem, just change the repository address to

[http://cyberspace.ucla.edu/marillat/](http://cyberspace.ucla.edu/marillat/)
still unstable and main

---

### Post by graigsmith on 2005-04-25
OK i found out how to change the settings in sound juicer!  its in the help file.

just run this 
gnome-audio-profiles-properties

and change the encoder, to mp3, change the encoding quality of the ogg files or whatever :)

---

### Post by jbjornson on 2005-04-26
Check out the MP3 encoding section here:

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

---

### Post by Galdor on 2006-09-26
had the same probs, solution like follows:

In the Soundjuicer's helpfile under Preferences ist explained how to rip directly to mp3.
Install the PlugIns - gstreamer -lame encoder
create new Profile e.g. "MP3"
the pipeline settins are
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux
restart SoundJuicer please!
 
if you like, read here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg25t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg25t2.htm)

btw, does anybody now how to tell LAME custom settings?
:) 
greetz

---

### Post by Jacob Bezemer on 2006-12-02
Ubuntu: Ripping in mp3 with id3 tags
By default, ubuntu does not come with this enabled. To add functionality to rip mp3's in ubuntu with sound juicer with id3 tags, lets do the following.

1. Install the necessary gstreamer packages:
# apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
2. Load sound juicer, go to Edit->Preferences
3. Under Format, choose Edit Profiles, and click New.
4. For Profile name, pick mp3 and hit Create.
5. Then click on the mp3 profile and click Edit.
6. Change the gstreamer pipeline to the following:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux
7. Then set the File Extension to "mp3".
8. Click on the checkmark box "Active?" then click Ok.
9. Hit Close on the Edit profiles screen.
10. You will need to exit the sound juicer application and restart it.
11. After reloading sound juicer, go back to Edit->Preferences and under the Output format section, you will now be able to set the newly created mp3 profile you created.

This will create mp3 files with a bitrate of 128 kb/s. Now stick in your cd's and you should be ready to go! If you are using another cd extracting program which uses gstreamer, this functionality should work fine as you just added a new gstreamer profile to the system, not specifically to sound juicer.
Tested under dapper.

---

### Post by SuperMike on 2007-01-07
Jacob Bezemer:

Your technique worked for me on Breezy. I noticed that it operates much faster than Grip and has a less confusing interface. There was one catch. There's one path you can take in the UI in doing the process you suggest that causes the UI to crash. It's temporary problem, however, because when you open the UI again for Sound Juicer it works.

That path was to add a new profile and then click Edit. When I did, Sound Juicer bombed out and I had to restart it. However, the new mp3 profile was there. On another PC, the fix was to create the new profile, but don't click Edit. Instead, close the program down and come back in again. Then, I edited the 'mp3' profile as you stated above and it worked.

---

### Post by H.P. Hovercraft on 2007-01-25
Utter noob here, running Dapper, trying to get gstreamer-lame running properly on Sound-juicer. All plugins are happily installed, profiles created as per the SJ help file. The mp3 profile's edited to use the following string...

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux

...as its pipeline. When I go to encode a track from the CD, I'm told gstreamer cannot connect to the specified pipeline. What am I missing?

I do have Grip installed, but it seems to run about as quickly as continental drift. I'd rather have SJ working...

---

### Post by tombott on 2007-01-29
Many thanks Jacob, that worked under Edgy.

Cheers,

Tom

---

### Post by Odin_one_eye on 2007-05-16
Struggled with this for a bit with Feisty Fawn. Jacob Bezemer's post showed me what I was missing:

the gstreamer0.10-plugins-ugly-multiverse package. In my experience, all I needed to do from a basic Feisty Fawn install was 

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

Sound Juicer (in my case at least) came with an entry for MP3 that became available once the -ugly-multiverse package was installed.

You can then either make a new one if you want a different bitrate or to change the tags.

---

### Post by tom17 on 2007-08-05
This is not working for me. I have gstreamer0.10-plugins-ugly-multiverse inbstalled and the mp3 profile just never shows up in SJ.

Edgy 64 bit and 32 bit as well... Any ideas?

---

### Post by xkendrax on 2007-08-07
same problem as tom, thers no mp3 option listed in the profile

---

### Post by r-mo on 2007-08-12
Just wondering, how do you adjust the bitrate?  at the moment I'm getting 128Kbps CBR out of sound juicer.  How can I make it give me 192 or 224 ABR encodes?

---

### Post by tom17 on 2007-08-12
I actually fixed the problem. It was user error. I was trying to get this working on two different machines. A package was missing from one and there was a typo on the other.

But I am still having problems. I have been looking and looking and have found no solid answers to the problems of incorrectly displayed track lengths in certain players when using vbr encoding.

I have included xingmux in the gstreamer pipeline which helped initially, but the track lengths are still sometimes incorrectly displayed.

I have a track that is 5:28 on the CD. I rip it using SJ & Lame and Amarok reports it as being 8:43 with a bitrate of 128. Most other progs report it correctly with an average bitrate of 203.

I get the same incorrect track times in 64 and 32 bit versions of Edgy.

As per the [CDRipping page]("https://help.ubuntu.com/community/CDRipping"), here is my gstreamer pipeline.

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=standard ! xingmux ! id3v2mux

I have the necessary packages installed.
Package: gstreamer0.8-lame
Version: 0.8.12-2ubuntu1

Package: gstreamer0.8-mad
Version: 0.8.12-6ubuntu3

Package: gstreamer0.10-plugins-ugly-multiverse
Version: 0.10.5-2

According to checkmp3, the file has some problems with missing frames... If I encode with grip (using lame preset standard for VBR), checkmp3 does not show any problems and the time displays correctly in Amarok.
Possible ID3v2 frame found, skipping

An expected frame was not found. Expected it at offset 0x7f4 (BYTE 2036), now at offset 0x7f5 (BYTE 2037).
FILE_NAME           Heart/Dreamboat Annie/01 - Magic Man.mp3
GOOD_FRAMES         12572
BAD_FRAMES          1
LAST_BYTE_CHECKED   8370377
VBR_HIGH            320
VBR_LOW             32
VBR_AVERAGE         204
SONG_LENGTH         05:28.43

USER_TIME           0.06s
SYS_TIME            0.01s

So it seems Amarok cannot handle this incorrectly constructed file. Maybe this is a fault of Amarok, maybe not, but there is a problem with the gstreamer pipeline, I assume not adding the xing header correctly.

It seems this has been a problem for some people for a while now with no acnowledgement of the problem. Should a bug report be created for this?

---

### Post by tom17 on 2007-08-13
After looking round all day, reading up on the gstreamer developer docs and digging through the code on the xingmux plugin, I came across this gstreamer plugins bug that looks like it could be the issue.

[http://bugzilla.gnome.org/show_bug.cgi?id=397759]("http://bugzilla.gnome.org/show_bug.cgi?id=397759")

Gonna try recompiling the plugin with the correct xing frame size and see how it goes...

I cannot believe there are not more people out there with this problem.

---

### Post by tom17 on 2007-08-13
Well recompiling xingmux fixes the problem reported by checkmp3, but the time is still displayed incorrectly in Amarok. I still think xingmux is incorrectly making the header. I guess I should take this over to the gstreamer forums/bugtracker.

Tom...

---

### Post by tom17 on 2007-08-15
Now I think it is a bug in Azureus :)

My reasoning for this is...
I have examined the resulting file from xingmux with a hex editor. After trawling the mp3 and xing header specs I have discovered that Amarok is not correctly reading the xing flags.

For those unfamiliar with them they are as follows...

0x0001 - Frames field is present
0x0002 - Bytes field is present
0x0004 - TOC field is present
0x0008 - Quality indicator field is present

Now Amarok is only looking at the frames field (the one needed to calculate track length) if the Bytes field and the TOC field are set. This is incorrect behaviour. If I set these two fields (and even if I unset the frames field too) then Amarok correctly looks at the frames field and calculates the track length correctly.

I will file this as a bug report somewhere on the Amarok site.

So in summary for those people using xingmux in their gstreamer pipeline for ripping CDs and playing back on Amarok there are two problems.

1. xingmux is creating an xing header that is 1 byte too large. A fix has been proposed on the bug tracker so it may be in a newer version. It would be nice to have a sooner fix for this so that people ripping cds have decent resulting mp3s

2. Amarok is not reading the xing headers correctly resulting in incorrectly displayed track times if the bytes and TOC fields are not set.

Tom...

---

### Post by tom17 on 2007-08-15
Me again.

The Amarok problem is a bug in taglib.

[http://bugs.kde.org/show_bug.cgi?id=70649]("http://bugs.kde.org/show_bug.cgi?id=70649")

I have made the changes in the taglib code, recompiled and it all works ok now. 

Hopefully this bugfix will trickle down to the distributions soon although it was changed in the SVN for taglib over a year ago so I am not overly hopeful about that.

Tom...

---

### Post by zutronius on 2007-08-15
I've tried everything here and I'm still unable to rip mp3s. I give up. :(

---

### Post by tom17 on 2007-08-16
What's the problem zutronius?

---

### Post by JohnnyVW on 2007-08-18
> **Jacob Bezemer said:**
> Ubuntu: Ripping in mp3 with id3 tags
By default, ubuntu does not come with this enabled. To add functionality to rip mp3's in ubuntu with sound juicer with id3 tags, lets do the following.

1. Install the necessary gstreamer packages:
# apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
2. Load sound juicer, go to Edit->Preferences
3. Under Format, choose Edit Profiles, and click New.
4. For Profile name, pick mp3 and hit Create.
5. Then click on the mp3 profile and click Edit.
6. Change the gstreamer pipeline to the following:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux
7. Then set the File Extension to "mp3".
8. Click on the checkmark box "Active?" then click Ok.
9. Hit Close on the Edit profiles screen.
10. You will need to exit the sound juicer application and restart it.
11. After reloading sound juicer, go back to Edit->Preferences and under the Output format section, you will now be able to set the newly created mp3 profile you created.

This will create mp3 files with a bitrate of 128 kb/s. Now stick in your cd's and you should be ready to go! If you are using another cd extracting program which uses gstreamer, this functionality should work fine as you just added a new gstreamer profile to the system, not specifically to sound juicer.
Tested under dapper.

This worked well for me!  The key, I think, was getting gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse installed.

I was able to create mp3's, but, they were garbage and unplayable.  Now, I'm ripping mp3's with Sound Juicer!!!  Thanks!

---

### Post by immrlizard on 2008-02-12
The only thing that I had to do was to install the ubuntu restricted extras and it will now allow me to rip away.   I spent the rest of the day filling my mp3 player.

I hope that this helps someone

---

### Post by GermWarfare on 2008-05-11
> **Jacob Bezemer said:**
> Ubuntu: Ripping in mp3 with id3 tags
By default, ubuntu does not come with this enabled. To add functionality to rip mp3's in ubuntu with sound juicer with id3 tags, lets do the following.

1. Install the necessary gstreamer packages:
# apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
2. Load sound juicer, go to Edit->Preferences
3. Under Format, choose Edit Profiles, and click New.
4. For Profile name, pick mp3 and hit Create.
5. Then click on the mp3 profile and click Edit.
6. Change the gstreamer pipeline to the following:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux
7. Then set the File Extension to "mp3".
8. Click on the checkmark box "Active?" then click Ok.
9. Hit Close on the Edit profiles screen.
10. You will need to exit the sound juicer application and restart it.
11. After reloading sound juicer, go back to Edit->Preferences and under the Output format section, you will now be able to set the newly created mp3 profile you created.

This will create mp3 files with a bitrate of 128 kb/s. Now stick in your cd's and you should be ready to go! If you are using another cd extracting program which uses gstreamer, this functionality should work fine as you just added a new gstreamer profile to the system, not specifically to sound juicer.
Tested under dapper.

Thankyou

Also works on LinuxMint (Ubuntu 7.10 (Gutsy))

---

### Post by Kenno on 2009-01-03
The actual answer to "How To get Sound Juicer to rip MP3's" should actualy be a firm "don't"! As indicated in previous posts, juicer interfaces with LAME through gstreamer, and [the gstreamer LAME plugin is thoroughly broken.]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22") Instead of Juicer, please [use rubyripper for ripping CDs.]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Installation_on_Ubuntu_8.04") Happy ripping!

---

### Post by LT1Caprice57L on 2009-02-07
Bumping this.

> **Jacob Bezemer said:**
> Ubuntu: Ripping in mp3 with id3 tags
By default, ubuntu does not come with this enabled. To add functionality to rip mp3's in ubuntu with sound juicer with id3 tags, lets do the following.

1. Install the necessary gstreamer packages:
# apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
2. Load sound juicer, go to Edit->Preferences
3. Under Format, choose Edit Profiles, and click New.
4. For Profile name, pick mp3 and hit Create.
5. Then click on the mp3 profile and click Edit.
6. Change the gstreamer pipeline to the following:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux
7. Then set the File Extension to "mp3".
8. Click on the checkmark box "Active?" then click Ok.
9. Hit Close on the Edit profiles screen.
10. You will need to exit the sound juicer application and restart it.
11. After reloading sound juicer, go back to Edit->Preferences and under the Output format section, you will now be able to set the newly created mp3 profile you created.

This will create mp3 files with a bitrate of 128 kb/s. Now stick in your cd's and you should be ready to go! If you are using another cd extracting program which uses gstreamer, this functionality should work fine as you just added a new gstreamer profile to the system, not specifically to sound juicer.
Tested under dapper.

How to get 256kb/s?  128 doesn't come anywhere near cutting it for me.

---

### Post by tigerdog on 2009-02-21
As I understand it, Sound-juicer uses gstreamer to invoke LAME for mp3s.  Unfortunately, it invokes LAME with some pretty low-quality settings by default as has been beaten about on many posts.  I finally began to get true VBR mp3 files with high quality and high bit rates by changing the mp3 profile:
[LIST]
[*]Edit/preferences
[*]click "Edit Profiles" at the bottom
[*]highlight "CD Quality, MP3"
[*]click edit
[*]eplace the default Gstreamer pipeline with
[/LIST]```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 quality=0 vbr-min-bitrate=32 vbr-max-bitrate=320  lowpass-freq=25000 ath-lower=0 ! id3v2mux
```
[LIST]
[*]close the edit
[*]close soundjuicer and restart
[*]edit/preferences and select "CD Quality, MP3"
[*]close preferences and (hopefully) get halfway-decent mp3s.
[/LIST]

Here's a guide to the pipeline command and its LAME equivalent
mode=0           -m stereo  (change to mode=1 for joint stereo)
vbr=4            --vbr-new  (use new vbr algorithm)
vbr-quality=0    -V 0       (use highest vbr quality , 9 is lowest)
quality=0        -q 0       (use highest quality encoding algorithm)

hopefully the rest are self-explanatory.  I hope this helps someone.

Note: after posting this, I used VLC to display the stream statistics and make further comparisons between files encoded with sound-juicer and directly with LAME.  Juicer files were still smaller; further examination showed the need to override gstreamer's default "ath-lower" of -3 to 0.  The command line above has been edited to reflect this.  The resulting files are quite large by mp3 standards but still much smaller than either wav or flac.

---

### Post by Kenno on 2009-03-25
> **tigerdog said:**
> ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 quality=0 vbr-min-bitrate=32 vbr-max-bitrate=320  lowpass-freq=25000 ath-lower=0 ! id3v2mux
```


Not bad, but Nyquist's theorem dictates that the lowpass frequency needs to be significantly lower than half of the sample rate (44100) to avoid aliasing artefacts (which can be quite severe). I believe Lame internally sets the lowpass to 21000 when asked for CBR 320 (the highest quality available), to 19500 when given -V 0 (the highest VBR quality), and even lower for lower qualities. Anything higher than 21000 is considered unsafe with regard to aliasing.

The bottom line is, knowing just how many switches LAME has and how unskillfully the defaults are set in the gstreamer plugin, it is very unlikely to find a gstreamer command line that works as intended and will pass rigorous listening tests. This lowpass issue perfectly illustrates my point. The only way to fix the problem is at code level, and posting command lines will just distract from this.

@LT1Caprice57L and possibly other people who overlooked my previous post:
[B][I][SIZE="4"][COLOR="Red"]Please do not use juicer or gstreamer to create MP3s.
It's broken and will produce substandard quality files.[/COLOR]
[Here's why]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22"), and [here's an alternative.]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Installation_on_Ubuntu_8.04")[/SIZE][/I][/B]

---

### Post by TheGuyWhoGotOn on 2009-05-18
Rubyripper seems pretty great I totally recommend it :). It's so easy to use I was shocked, he's my high quality LAME MP3 settings: "-V 0 -b 32 -B 320"

The crazy thing is...It actually works! And it's fast...

P.S. Sorry for the bump I just got a little excited (You can check it off to get it to rip in Ogg, FLAC, and MP3!!)

Oh and as for a good Sound Juicer pipeline...Here's mine for Rhythmbox (Which is the same thing really because they both use GStreamer): "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 quality=0 vbr-min-bitrate=32 vbr-max-bitrate=320 lowpass-freq=21000 ath-lower=0 ! xingmux ! id3v2mux"

It shouldn't produce faulty times and it should produce a pretty good sound. However as mentioned above it's recommended that "lowpass-freq=21000" isn't overrided however I believe GStreamer does this on it's own accord so I set it to 21000 because I think that's relatively safe.

Edit: "xingmux" allows it to produce tags that support newer players (I think it helped me anyways with song length and bitrate reporting).

---

### Post by logos34 on 2009-05-18
> **Kenno said:**
> Not bad, but Nyquist's theorem dictates that the lowpass frequency needs to be significantly lower than half of the sample rate (44100) to avoid aliasing artefacts (which can be quite severe). I believe Lame internally sets the lowpass to 21000 when asked for CBR 320 (the highest quality available), to 19500 when given -V 0 (the highest VBR quality), and even lower for lower qualities. Anything higher than 21000 is considered unsafe with regard to aliasing.

The bottom line is, knowing just how many switches LAME has and how unskillfully the defaults are set in the gstreamer plugin, it is very unlikely to find a gstreamer command line that works as intended and will pass rigorous listening tests. This lowpass issue perfectly illustrates my point. The only way to fix the problem is at code level, and posting command lines will just distract from this.

@LT1Caprice57L and possibly other people who overlooked my previous post:
[B][I][SIZE="4"][COLOR="Red"]Please do not use juicer or gstreamer to create MP3s.
It's broken and will produce substandard quality files.[/COLOR]
[Here's why]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22"), and [here's an alternative.]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Installation_on_Ubuntu_8.04")[/SIZE][/I][/B]

Very interesting...Just checked out your launchpad bug report...was astonished to read the part about the source code comments

I thought I was able to isolate the problem of lame vbr output to the  gstreamer0.10-plugins-ugly-multiverse (the lame plugin), and fix it by rolling back from the current 0.10.7-1 to the old feisty 0.10.5-2.  

It appears to output correctly now (at the correct target bitrate), or does it? Are you saying it it's totally unreliable?  I don't use Sound Juicer or gstreamer myself, but I wish someone would get to the bottom of this, as a large portion of ubuntu users are using Sound Juicer and gstreamer to rip their cds to mp3

---

### Post by kevinshields on 2010-08-10
Instead of sound user, I made a small script that uses lame (lame is plain great), read the top readme stuff in order to use it, run it with the install flag like 

# ripcd.sh install

should binaries be missing the first time you have a go.

[http://nollettnoll.net/ripcd.sh](http://nollettnoll.net/ripcd.sh)

Works great for me.

---

### Post by boarderpatrol on 2010-08-20
**Wow,  I like your script kevinshields.**

  Just a little configure for my system and I am up an ripping mp3.  
Thank you for your contribution.  :)

---

