---
title: "audioconvert! the new super script to convet audio files!"
date: 2005-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by thetroublemaker on 2005-07-10
hi gals, hi dudes! :)

this is my first post to this forum! :) i hope it's the right section! :)

i just made a script that converts audio files from wav, ogg, mp3, mpc, flac, ape or wma into wav, ogg, mp3, mpc, flac or ape! all with a right click of the mouse! that is, if you're usin' nautilus or rox. it was designed for nautilus, but it also works on rox, and of course as a standalone bash script. it uses zenity to show progress bars and ask questions :)

this is the freshmeat link: [http://freshmeat.net/projects/audio-convert/](http://freshmeat.net/projects/audio-convert/) there you will find the latest version, the cvs version, and the link to the homepage!

please test it and give me feedback on the homepage on how it works, point me out bugs, make suggestions on how to improve it, and please test it on fluxbox and such, to see if it can be installed as a file manager script there, too!

there is a documentation file in the cvs version :)

aac support comin' soon!

ciao! :)

edo

---

### Post by sapo on 2005-07-10
nice script... worked perfectly.. can i convert a whole folder with it?

---

### Post by dickohead on 2005-07-10
That is someting I have been after for a long time!!! So many MP3's to convert to OGG!!!!

But just a suggestion... maybe a .deb package for Ubuntu?

---

### Post by thetroublemaker on 2005-07-10
[QUOTE=sapo]nice script... worked perfectly.. can i convert a whole folder with it?[/QUOTE]

well, not quite. i mean, you can go into the folder, select all of the files, and then click on the script. it'll convert'em one by one. would that work out? :)

ciao! :)

edo

---

### Post by thetroublemaker on 2005-07-10
[QUOTE=dickohead]That is someting I have been after for a long time!!! So many MP3's to convert to OGG!!!!

But just a suggestion... maybe a .deb package for Ubuntu?[/QUOTE]

i don't know how to make deb packages. i'm pretty sure it's not hard though. it's just that i'm a gentoo user. i made a thread about the script in here cause obivously the script is intended to work on any distribution, and i hope you ubuntu guys will enjoy it!

check the freshmeat page every once and a while, somethin' new might pop up in the next few days! :)

ciao! :)

edo

---

### Post by MetalMusicAddict on 2005-07-10
This is really cool. Cant wait to try it. :)

[QUOTE=dickohead]That is someting I have been after for a long time!!! So many MP3's to convert to OGG!!!!

But just a suggestion... maybe a .deb package for Ubuntu?[/QUOTE]
Honestly you shouldnt go from 1 lossy format to another.

---

### Post by sapo on 2005-07-10
[QUOTE=MetalMusicAddict]This is really cool. Cant wait to try it. :)


Honestly you shouldnt go from 1 lossy format to another.[/QUOTE]

maybe you could hack my car mp3 player to play ogg files?  :-P 

[QUOTE=troublemaker]well, not quite. i mean, you can go into the folder, select all of the files, and then click on the script. it'll convert'em one by one. would that work out? 
[/QUOTE]

but it asks too many questions  ](*,)

---

### Post by notos on 2005-07-11
using ogg instead of mp3 is gooood because ogg is free (as in speech :) - libre) and mp3 is a "closed" format  [-X

---

### Post by Pulsie on 2005-07-11
[QUOTE=MetalMusicAddict]
Honestly you shouldnt go from 1 lossy format to another.[/QUOTE]

Agreed - I'm all for Ogg Vorbis and use it to rip my own CDs, but transcoding existing mp3s to create poorer sounding Vorbis files really isn't helping the cause.   

If you don't believe me, here it is, straight from the horse's mouth:
**[http://www.vorbis.com/faq.psp#transcode](http://www.vorbis.com/faq.psp#transcode)**


Thanks for the script though; it's great for converting my FLAC files to Vorbis files :)

---

### Post by sapo on 2005-07-11
my little help ;)

Brazilian portuguese translation  :grin: 

```

	###### Brazilian Portuguese ######
	pt-br* )
		title="audio convert "$version""
        	pleasesel="por favor, selecione pelo menos um arquivo."
	        noselec=""$title" converter arquivos de audio. "$pleasesel""
	        choix="extensão do arquivo de saída:"
	        warning="atenção"
	        proceed="já existe! sobrescrever?"
	        recur=""$title" não é possível converter pasta. "$pleasesel""
	        conversion="convertendo arquivo:"
	        ask_artist="digite o nome do artista:"
	        ask_album="digite o nome do album:"
	        ask_song="digite o nome da música:"
	        ask_track="digite o número da faixa:"
	        ask_quality="selecione a qualidade desejada:"
		confirmation="você quer converter"
		decoding="decodificando arquivo:"

```

hope it helps ;)

---

### Post by vassie on 2005-07-11
Fantastic script, however I have a couple of comments / question.

1. Can it read ID3 (v1&v2) tags from MP3, I have a folder full of MP3's but the script keeps asking me for Artists / Album / Title / Track Number for each file

2. Can it remember bitrate settings? It keeps asking what format and bitrate, and each time I select ogg and level 6

3. Can it ask me if I want to delete the original file after conversion?

Thanks
Ben

---

### Post by thetroublemaker on 2005-07-12
thankyou very much gals and dudes for all of your great feedback! keep watchin' out the freshmeat page, as in less than a week i'll probably update it.

also sapo, if you wanna send me your email adress in private, and preferrably your name, i said preferrably, it's not mandatory, i'll put you in the changelog for the brazilian translation! :)

ciao! :)

edo

---

### Post by thetroublemaker on 2005-07-12
uh, by the way. if someone wants to help me out with more translation, you're more than welcome to do so! you can either post'em here or in the savannah homepage as a patch! or send'em to me by email! by the way, don't forget to tell me your email address and possibly your name, or at least your nickname, so i'll put you in the changelog! :)

ciao! :)

edo

---

### Post by thetroublemaker on 2005-07-12
[QUOTE=vassie]Fantastic script, however I have a couple of comments / question.

1. Can it read ID3 (v1&v2) tags from MP3, I have a folder full of MP3's but the script keeps asking me for Artists / Album / Title / Track Number for each file

2. Can it remember bitrate settings? It keeps asking what format and bitrate, and each time I select ogg and level 6

3. Can it ask me if I want to delete the original file after conversion?

Thanks
Ben[/QUOTE]

question one: i'm workin' on it, but of course it would only work from ogg to mp3, or from mp3 to ogg.

question two: not yet, as it don't have a config file yet. i'm not sure if i'll ever implement this, but if i will, it'll remember the value, but still ask for confirmation :)

question three: i might implement that. i think it's already askin' too many questions though, so if i can reduce some of'em, maybe i'll add this one! :)

thankyou very much for your feedback, and stay tuned for more news! :)

ciao! :)

edo

---

### Post by Yotam2 on 2005-07-14
Hello!

I'm on Hoary 686, and I'm trying to convert and APE file using this scripts. I'm being asked all the questions, and then nothing happens - no conversion takes place. When I run it from shell, I get the error message:

audio-convert: line 375: id3tag: command not found

I have libID3tag0 version 0.15.1b-3 installed. Should I install more packages?

---

### Post by thetroublemaker on 2005-07-16
version 0.2 has come out! :) visit [http://freshmeat.net/projects/audio-convert/](http://freshmeat.net/projects/audio-convert/) to download it!

many new features, includin': it's now **a lot** easier to convert large groups of files. for instance, at the very beginnin' a question asks if we want to edit the metatags for each file or not, so we can say no and let the files convert. right after that, quality of compression is only asked once, before compressions take place, and it's used for all the group of files.

there still is a question askin' for each file if we want to convert it or not, but i think i'll make it optional in 0.2.1, so convertin' large groups of files will then become a snap of fingers! :)

dutch, french, to be completed, and brazilian portuguese translations added. german translation comin' soon! :)

for yotam2. try now and see if the bug is corrected! :)

please give me **a lot** of feedback! :)

ciao! :)

edo

---

### Post by Yotam2 on 2005-07-18
Alas, it still doesn't work.
When I try to convert an .ape to .mp3, I choose not to change the tags, and then I get several rectangular pop-ups that disappear really fast, and the cryptic error message is:

ls: /path/to/file/Track01.mp3: No such file or directory

Iget similar messages when trying to convert to and from other types of files.
What could be the problem? Can I help debugging it?

---

### Post by thetroublemaker on 2005-07-18
it might be, might be, that ya don't have enough disk space on that partition. because, in your case of ape to mp3, the way the program works is that it converts the ape into wav, and then the wav into mp3, and then deletes the wav. so maybe there's not enough space for the wav. so check that out.

in case that's not the issue, add the line 'set -x' at the very beginnin' on the file, but **after** the first line. then, from a shell, give this command: 'path/to/audio-convert path/to/filename.ape 2>&1 audio-convert.log'. and then post the log into somethin' like [http://pastebin.com/](http://pastebin.com/), and then paste the link here. we'll check it out! :)

thankyou! :)

ciao! :)

edo

---

### Post by Yotam2 on 2005-07-18
This is getting weirder by the minute.

I have no disk space problems (free gigs). when I did as you said (added a set -x after #!/bin/bash and issued the command from shell followed by 2>&1 audio-convert.log), the following happened:

1. I got output in the shell for every line.
2. I skipped ID3 tags. I was asked for mp3 data, and then was asked if I wanted to convert my .ape file to .mp3. I said yes.
3. The I was asked if I wanted to convert audio-convert.log (that's right!) to audio-convert.mp3. Eerie. I said no, of course.
4. When the process was done, I couldn't find audio-convert.log nowhere. No .mp3 was created.

I copied-pasted the data from the shell, since the log file was self-destructed or something. Here it is:

[http://pastebin.com/315657](http://pastebin.com/315657)

Thank you very much for the attention!

Yotam

---

### Post by frodon on 2005-07-18
really good script !!!

however I have some problem converting .ape files, the window close itself without converting the file. Do you already have this problem with .ape files ?

---

### Post by thetroublemaker on 2005-08-01
hello everyone! :)

audioconvert version 0.2.1 is out! visit [http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert) to download it! :) a new feature has been added so that now it's possible to convert large groups of files with three or four clicks! support for flac metatags has been added! and now the script is available in german, too, thanks to lukaz! :)

keep in mind that new translations, or updates to translations, since there are a few new variables to translate, are more than welcome! :) as of now we have: italian, dutch, english, french, german, brazilian portuguese! submit more if you feel like, and don't forget to give me your email address, so i can quote you in the changelog! :)

thank you **very much** for your feedback, but please give me **a lot** more on how it works, and what features you would like included! :)

for yotam2 and frodon. are your issues still there in this new version? please let me know! :)

ciao! :)

edo

---

### Post by frodon on 2005-08-02
I put audio-convert (latest version  ;-) )in /home/frodon/.gnome2/nautilus-scripts/, then I go in the directory where the .ape is and right click on it and run audio convert, then I choose mp3 without metatags and with default compression and a windows appear and disappear 3 times and nothing more ...
When I run audio-convert on the same file in a console it say that : ```
/usr/bin/lame
/usr/bin/oggenc
/usr/bin/flac
ls: CDImage.mp3: Aucun fichier ou répertoire de ce type
```The last line means : no file or directory of this type
It sounds like a small problem, maybe your script can't create the CDImage.mp3 file due to wrong permissions (the directory where the file is have 777 rights).

---

### Post by Remix_88 on 2005-08-02
Great script! This is just what I needed and much easier and beeter to use that SoundConverter :smile: 

I rip my CD's to FLAC so I don't lose any quality, then I convert the FLAC files to Ogg for my iAudio portable music player and also to MP3 so I can make compilation CD's to play in my DVD player. My DVD player doesn't play Ogg, snif :-(

My only suggestions would be that :

1. The default quality/compression settings should be...

Lame : Standard
Ogg : 6
FLAC : 6 

...becuase these are sane but decent quality/compression defaults. Defaulting to optimum settings is a bit odd. I don't use Monkeys Audio so don't know what the sane defaults are for that,

2. When encoding to FLAC have it say "Compression" not "Quality". 

These a minor points I know, your script is excellent and I will be keeping an eye on how it develops.

---

### Post by A-star on 2005-08-02
Is it possible to make a deb file or something, which checks for the needed dependancies and installs them?

---

### Post by thetroublemaker on 2005-08-02
for frodon. from the console output i see you don't have the mac codec installed. therefore you cannot read ape files. therefore, you cannot convert them :) get the mac-port for linux at [http://sourceforge.net/projects/mac-port](http://sourceforge.net/projects/mac-port), install it, and everythin' will work fine! :)

for remix_88. i dunno about the quality levels, they look fine to me :) but i will look into changin' 'quality' to 'compression level' for flac and ape. it seems more appropriate :)

for a-star. i have no idea how to make a deb package. but if someone wants to make one, you're more than welcome to do so! :) the dependencies are listed at the beginnin' of the script. also, if in the future this script will become part of ubuntu, i will be even happier! :)

keep givin' me **a lot** of feedback, and wait for the next version, 0.3, which will be out in about a week! :)

ciao! :)

edo

---

### Post by frodon on 2005-08-03
[QUOTE=thetroublemaker]for frodon. from the console output i see you don't have the mac codec installed. therefore you cannot read ape files. therefore, you cannot convert them :) get the mac-port for linux at [http://sourceforge.net/projects/mac-port](http://sourceforge.net/projects/mac-port), install it, and everythin' will work fine! :)[/QUOTE]
thanks thetroublemaker for your support and your nice script and ... sorry to not have found myself that i haven't mac codec installed .... maybe you could add a line in the homepage in dependency section.

---

### Post by cutOff on 2005-08-03
[QUOTE=thetroublemaker]for frodon. from the console output i see you don't have the mac codec installed. therefore you cannot read ape files. therefore, you cannot convert them :) get the mac-port for linux at [http://sourceforge.net/projects/mac-port](http://sourceforge.net/projects/mac-port), install it, and everythin' will work fine![/QUOTE]
Hi thetroublemaker,

when I try to compile 'mac-3.99-u4-b3' got this errors

```
make[3]: *** [Assembly.lo] Error 1
make[3]: Leaving directory `/home/cutoff/downloads/mac-3.99-u4-b3/src/MACLib/Ass embly'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/cutoff/downloads/mac-3.99-u4-b3/src/MACLib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cutoff/downloads/mac-3.99-u4-b3/src'
make: *** [all-recursive] Error 1
``` 
Do you know how to solve this?

thanks

---

### Post by GrammatonCleric on 2005-08-03
It looks like you need to install "nasm"

Check out the HOWTO for getting BEEP to play .ape files.  It describes the dependences need to build the MAC lib.

[http://ubuntuforums.org/showthread.php?t=52785&highlight=.ape](http://ubuntuforums.org/showthread.php?t=52785&highlight=.ape)

GC

---

### Post by cutOff on 2005-08-03
[QUOTE=GrammatonCleric]It looks like you need to install "nasm"

Check out the HOWTO for getting BEEP to play .ape files.  It describes the dependences need to build the MAC lib.

[http://ubuntuforums.org/showthread.php?t=52785&highlight=.ape](http://ubuntuforums.org/showthread.php?t=52785&highlight=.ape)

GC[/QUOTE]
Yeah! it works fine. Many thanks.

---

### Post by IdoMcFly on 2005-08-12
where can I find mppdec needed by the script to decode MPC ?

---

### Post by thetroublemaker on 2005-08-12
idomcfly, you can find the needed codec on this page: [http://www.musepack.net](http://www.musepack.net)

give me some feedback on how it worked out! :)

version 0.2.2 comin' soon! :)

ciao! :)

edo

---

### Post by chaumurky on 2005-08-15
I can't see it mentioned but is **aac** supported yet? I want to convert some wav's to rintone format for my phone! :grin:

---

### Post by true nemesis on 2005-08-15
Can anyone give me a step by step installation process of audio convert? I am a complete linux newb. Please help. 

I would like the Right Click menu option enabled also.

---

### Post by SilvioTO on 2005-08-23
symply put the audio-convert script in /home/youname/.gnome2/nautilus-scripts folder (enable visualization of hidden files with Ctrl+H)

right click on audio file to convert -> scripts -> audio-convert and follow the instruction.

Hi  :)

---

### Post by thetroublemaker on 2005-08-29
hello everyone! :)

version 0.2.2 is out! visit [http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert) to download it! many new features are in, includin': artist and album metatag fields are now remembered through multiple files. added two checks to make sure the input files are supported and the user has the right codecs to decode them. now a message informs the user the conversion has been completed. updated french translation. spanish translation added.

i want to remember you that more translations and updates to existin' translations are more than welcome! as of now we have: english, italian, french, brazilian portuguese, dutch, german and spanish! :)

i hope you guys enjoy the new features, point me out to bugs, and keep givin' me the **great** feedback you gave me so far! :)

for everyone who's had issues so far: are the issues still present in this new release? :)

ciao! :)

edo

---

### Post by REBELinBLUE on 2005-08-29
[QUOTE=thetroublemaker]hello everyone! :)

version 0.2.2 is out! visit [http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert) to download it! many new features are in, includin': artist and album metatag fields are now remembered through multiple files. added two checks to make sure the input files are supported and the user has the right codecs to decode them. now a message informs the user the conversion has been completed. updated french translation. spanish translation added.

i want to remember you that more translations and updates to existin' translations are more than welcome! as of now we have: english, italian, french, brazilian portuguese, dutch, german and spanish! :)

i hope you guys enjoy the new features, point me out to bugs, and keep givin' me the **great** feedback you gave me so far! :)

for everyone who's had issues so far: are the issues still present in this new release? :)

ciao! :)

edo[/QUOTE]
 This is cool, once you get AAC working I will definately install this

---

### Post by majikstreet on 2005-08-29
deleted-------------impossible!

---

### Post by BLueSS on 2005-09-07
How about DRM wma's? Do they work?   :)  I have the licenses if needed.

---

### Post by thetroublemaker on 2005-09-18
hi everyone! :)

version 0.2.3 is out! check out [http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert) to download it! new features include: a message warns about which codec is missin'. it's now possible to pass metatags on from one file to another. void metatags are now recognized and treated. updated german and spanish translations!

as usual i remind y'all that translations and updates to translations are always **very** welcome, as i want this script to be as widespread as possible! :)

thankyou **very much** for your feedback, keep it up and i'll keep answerin' your concerns! :)

ciao! :)

edo

---

### Post by moose6589 on 2005-09-19
Hello, 

Great job on the script! However, I have been having a problem with it. I am trying to convert a lot of ogg files, but only some work! They are all ogg files, but only some CD's seem to convert, whereas other ogg files don't convert; an error pops up saying the format is unsupported! What possible reason could there be for such an error? Other ogg files work just fine. Also, it's not just one or two files but almost half of all of them! They play well, so I don't know what the problem is.

---

### Post by urbandryad on 2005-09-27
do you need lame or any other program for this, or is it standalone? Cause LAME confuses me, and I gave up on trying to figure it out with a headache. :3 This seems simpler.

I'd stick with OGG, but I need a format that goes onto iPod shuffle. therefore, MP3. ^^ Thanks for this script, I hope it works for me!

---

### Post by thetroublemaker on 2005-10-09
hi everyone! :)

version **0.2.4** is out! go to [http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert) to download it! the new features include: files with dots in their name are now recognized, thus supported. completely rewrote filetype checks for efficency. this means, the program now runs faster! polish translation added. bug fixes! :)

as usual i remind you that any new translation or updates to existin' translations are more than welcome! i want this program to be as international as possible! :) also any suggestion to improvements, pointin' bugs out and all kind of feedback are always welcome! :)

moose6589. i think there's a good chance your files weren't supported because there was one or more dots in their name. try the new version out and let me know!

urbandryad. you do need lame **installed**, but you do **not** use lame directly. the program uses it for you, based on the graphical choices you make. it's as simple as a few clicks away! try it and let me know!

that's it for now. keep givin' me the **awesome** feedback you've been givin' me so far, and i'll keep answerin'! :)

ciao! :)

edo

---

### Post by sinbad782 on 2005-10-17
Hi, 
   I have had a small problem: When selecting multiple WMA files in order to convert to MP3, the output files seem to come out too small, and play at the wrong speed (too fast). When you select just one file, the transcoded MP3 file comes out perfectly and so there may be a problem in one of your for loops that are invoked when multiple files are being handled - either decoding of WMA and writing to WAV or the subsequent re-encoding into MP3 - I don't know which!

-----
This script is a really great idea and would help me out immensely due to my VERY messy music collection. SoundConverter for GNOME doesn't seem to be working for me (doesn't produce any output files), and SoundKonverter for KDE wouldn't compile properly either. 

Keep up the good work, PJS

---

### Post by Koybe on 2005-10-23
Hello,

it looks great. Anyway, i tried to convert from MPC to MP3 and when the menu appears, i can only select FLAC, ogg or wav. 
What do i need to install? Lame, flac, vorbis-tools, libid3, zenity already installed.

Thank you

---

### Post by steil on 2005-11-09
When converting to mp3, nothing happens. It asks me for the ID3 information, then says it's complete. Also when working with an mp3 file, there is no option to convert to mp3 (to change the bitrates and such).

---

### Post by maqi on 2005-12-06
just tried the script out in ROX. Have installed the 0.3.1 deb package. Works well - thanks very much for this :)

I do have a couple of suggestions - it would be great to have the option to choose the output directory. Currently this defaults to the same dir as the file to be converted. 

Problem with this is - I have a bunch of files on an NTFS volume (mounted read-only) which I want to convert. I tried converting a file. The script did its thing and exited without converting (obviously couldn't write the new file). No problem there except that there was no error message to let me know why. Not so hard to work out why it failed, but for less experienced users it might seem as though the script is broken.

The workaround is to copy the files to a writable volume and then convert. And then delete the original files. However, if there was an option to choose the output directory these extra steps could be avoided. Might also avoid the need for an error message?

Anyway, other than that I think this is an excellent script. It's so nice to just right click and convert. Thanks heaps :D

---

### Post by pompeyjohn on 2005-12-12
Great script - I love it :)

Thank you thank you thank you!!

---

### Post by jwsalaz on 2010-04-16
This script no longer works/is broken in Karmic.

Ape files come across as unsupported.  Please update the script.

---

### Post by Sandiep on 2010-04-30
[COLOR=Magenta]**are "If" loops set up a decision structure ?**[/COLOR]

---

