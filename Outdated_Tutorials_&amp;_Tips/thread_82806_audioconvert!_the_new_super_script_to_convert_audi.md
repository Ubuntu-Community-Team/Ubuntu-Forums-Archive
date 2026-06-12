---
title: "audioconvert! the new super script to convert audio files!"
date: 2005-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by thetroublemaker on 2005-10-27
hi gals, hi dudes!

audio convert is a script that converts audio files from wav, ogg, mp3, mpc, flac, ape, aac or wma into wav, ogg, mp3, mpc, flac, ape or aac! all with a right click of the mouse! that is, if you're usin' nautilus or rox. it was designed for nautilus, but it also works on rox, and of course as a standalone bash script. it uses zenity to show progress bars and ask questions :)

this is the freshmeat link: [http://freshmeat.net/projects/audio-convert/](http://freshmeat.net/projects/audio-convert/) there you will find the latest version, the cvs version and the link to the homepage! :)

many of you on this forum have already tested it, used it successfully, and reported bugs and suggestions to me. please keep doin' so! your feedback so far has been **awesome**! :)

and for those of you who were expectin' it: version **0.3.0** is out and... **aac support** is now ready! :)

ciao! :)

edo

---

### Post by Koybe on 2005-10-27
Hi, I just had a look at your script and previous post on Hoary. And i have a problem going to MP3. 

Look [here ](http://www.ubuntuforums.org/showthread.php?t=82704)and [here](http://www.ubuntuforums.org/showthread.php?t=48007&page=5). Thank you.

---

### Post by sailor420 on 2005-10-27
Looks very nice. I'll have to give it a try...

---

### Post by sailor420 on 2005-10-27
I've only got the option to convert to ogg or wav. Is there any setup I have to do with codecs, etc?

---

### Post by thetroublemaker on 2005-10-27
koybe. i guess you pointed out a little, very little bug in the program. i read that you don't have mppdec. then you can't convert from mpc. the program is supposed to tell you that and stop you, but it don't. the problem is that audioconvert looks for mppenc, assumin' that if you have that then you've got mppdec, too. but that don't seem to be the case with you :)

so two things. one, get mppdec, somehow, and everythin' will probably work out fine. if not, contact me and i'll help you out. two, i will change the check form mppenc to mppdec in the next version! :)

hope this works! thankyou! :)

ciao! :)

edo

---

### Post by Koybe on 2005-10-27
Thanks for your answer, so I'll have a look at home. But can you tell me which package I need to install to get on it?
For my point of view I installed everything. What about a listing of all PACKAGES (not only enumerate progs like on freshmeat) dependencies?
I think it could help Sailor420 too, and many other people to get such a list ;-)

Thank you very much indeed.

Edit : Downloaded mppdec from musepack website and put it in the /usr/bin directory with +x permission... Nothing change.

---

### Post by thetroublemaker on 2005-10-27
sailor420, koybe. i'm startin' to think i'll have to put this in the README, and probably will in the next version. but for now, if you edit or even just show the script with your favourite file editor, vim for instance, or gedit, you will see that there is a list of dependencies in the first lines. check those out and see if your problems are still there! :)

koybe. a list of packages is not possible, as different programs are placed on different packages dependin' on the distribution you use. and this is a multi-distribution script :) in the meantime, to help you out, could you describe exactly what happens now that you've got mppdec installed? :)

ciao! :)

edo

---

### Post by Koybe on 2005-10-27
What happend is exactly the same as before, even updated to 0.3.0.
I put the audio-convert script in my ~/.gnome2/nautilus-scripts, then i right click a mpc file and i clic convert -> I got 3 possibilities : flac, ogg and wav. Unfortunately I need MP3.

[Look at it](http://img439.imageshack.us/my.php?image=screenshotaudioconvert0308da.png)

FYI, i just tried it on my FC4 and got the same problem :(

---

### Post by fut21 on 2005-10-27
I need "lame" to get the scribt going. I dont have it in apt, where can i get it.

---

### Post by Koybe on 2005-10-27
fut21, yes you can have it by apt, maybe you need [to enable universe/multiverse repo](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) and retry to get it.

thetroublemaker, I can use mppdec for decoding MPC and then use lame to encode MP3 on the command line and it works.... So i guess everything is installed. But the quality of the mp3 is really bad.

---

### Post by jamesford on 2005-10-27
i cant get this to work. where are the new files supposed to go ? is it supposed to overwrite the existing ones?

edit: doh it works in nautils but not for files on desktop

---

### Post by fut21 on 2005-10-27
I can only convert between ogg and wav:(

---

### Post by bionnaki on 2005-10-28
wow - works wonderfully! thanks!
been looking for a way to easily
convert my flac to ogg - q6

---

### Post by i3dmaster on 2005-10-28
great stuff! Thanks!

---

### Post by thetroublemaker on 2005-10-28
fut21. i think you need to get lame. try and follow koybe's hint. let me know :)

koybe. what you need to do is this. edit the script with your favourite text editor, such as vim, or gedit, and add a line on a **newline** just before version="0.3.0". add this line:

set -x

after that, run the script from console on an audio file, catch the output, and send it to me via email :) you can do somethin' like this:

./audio-convert filename.mpc &> logname

run the program as you usually would. when it's done, send me logname via email :) my email address is on the freshmeat page. your issue seems to be a little cryptic, so that output will help me out in solvin' it :) if it's too hard, please ask questions and i'll try to answer them :)

and for all of those the script worked for, thankyou **very much** for reportin' it! :) great feedback like yours keeps me goin'. along with wantin' to make one of the best audio scripts out there :)

ciao! :)

edo

---

### Post by frodon on 2005-10-29
Hi thetroublemaker

I have some problems converting .wma to .mp3, it seems that it's not working. I have mplayer installed, i joined the terminal output.
Hope the problem could be solved, i already used the script to convert FLAC to mp3 or ogg with success.

Thank you for your effort, great script !

---

### Post by cvmostert on 2005-10-29
Hi there,

There seems to be alot of work that needs to go into your porgram... But of what I read, it works fine when it does work. Will surely have a look.

Thanks

---

### Post by SilvioTO on 2005-11-03
I installed audio convert 3.0 on breezy, with all dep raccomended, and the script don't convert wav to mp3. When I select the file to convert, script ask me if I like to compile mp3 tag; I answer not and in one second windows disappeare, and another window advise me that the conversion is ok, but I don't have mp3 file converted. Another problem is convert ape files to another; script advise me that I don't have codec called "mac"; where I download it? Thanks, Hi!

Silvio.

---

### Post by SilvioTO on 2005-11-03
solved mac problem, but don't convert in mp3... can you help me please?

---

### Post by frodon on 2005-11-03
thetroublemaker, i make some tests and have a look to the script. The problem i have with your script with flac to mp3 and also other conversion is due to the fact that the windows which allow to specify the quality does not appear and then the parameter $quality is not set and the lame command failed because of the lack of this parameter : ```
lame -m auto --preset '/mnt/zik/new_zik/Ernest Ranglin/In Search Of The Lost Riddim/01 - D'\''accord Dakar.wav' '/mnt/zik/new_zik/Ernest Ranglin/In Search Of The Lost Riddim/01 - D'\''accord Dakar.mp3'
LAME version 3.96.1 (http://lame.sourceforge.net/)

Error: You did not enter a valid profile and/or options with --preset
```So i think the main bug come from the "choose quality" step which sometimes not occurs.

In my case i solved all my problems fixing the mp3 quality to 224 (line 264) because i always want this quality : ```
if [ "$1" == "mp3" ]
then
	quality=224
fi
```

---

### Post by thetroublemaker on 2005-11-04
silvioto. with this much information i cannot help you that much :) follow the steps i suggested koybe take on post fifteen, then send me the output as an email attachment, and i'll try to help you! :)

frodon. i dunno, it looks a little weird to me. it works fine here. could you send me the set -x output too of the **original** script?

you guys, send me some output or else i won't be able to help you much! and keep tryin' to troubleshoot my script out, and i'll keep tryin' to help you! :)

ciao! :)

edo

---

### Post by SilvioTO on 2005-11-04
Thanks edo, I'll send you a log... but I think the problem is in Breezy and not in script, because avidemux have problem (don't find lame but only toolame in audio codec section) too. I discovered this today.

Ciao!

Silvio.

---

### Post by SilvioTO on 2005-11-04
this is attachment of my audio-convert script.[ATTACH]3365[/ATTACH]

---

### Post by frodon on 2005-11-04
Ok problem solved.
The problem is with french language only i think.

Line 86 : ask_quality="Choisir la qualit&#233; voulue:"
This line is the problem, i don't know why but the character "&#233;" is wrong understood by zenity, this is a sample of the output at this step : ```
++ zenity '--title=WOM audioconverter 0.3.0' --list --radiolist --column= '--column=Choisir la qualit\uffff voulue:' FALSE medium FALSE standard TRUE extreme FALSE insane
Cette option n'est pas disponible. Veuillez consulter --help pour toutes les utilisations possibles.
+ quality=
```So replacing the character "&#233;" by the charater "e" solve the problem.

---

### Post by thetroublemaker on 2005-11-05
frodon. does it give problems in the 'ask_track' section? when it prints 'Numéro de la piste:', does it print the charachter correctly? tell me and i'll see if i have to correct that, too :)

silvioto. workin' on your issue, hope to have it fixed soon! :)

thankyou **very much** for all the reports! new version out in about a week! :)

ciao! :)

edo

---

### Post by frodon on 2005-11-05
Yes, the troublemaker, i didn't test it before but same problem with "&#233;" character in the "ask_track" section.
I discovered a small and weird problem in wma_decode function : ```
wma_decode ()
{
	temp_file=`echo "$1" | sed 's/\.\w*$/'.wav'/'`
	mplayer -ao pcm:file="$temp_file" "$1" 2>&1 | awk -vRS='\r' '(NR>1){gsub(/%/," ");print 100-$5; fflush();}' | zenity --progress --title="$title" --text="$2 $1" --auto-close
```The progress bar fail and it close de wma decode too early but if i remove the last pipe (the zenity progress bar) it works really nice.
I joined the terminal output of this step.

I want to say that despites severals minor issues the script works really well and would like to say thank you for that.
I use this script really often and enjoy using it :)

---

### Post by SilvioTO on 2005-11-06
Thanks edo for your interest :) 
your is a grate software!

Silvio.

---

### Post by thetroublemaker on 2005-11-06
silvioto. are you usin' an old version of zenity? could you type here which one you're usin'? i think it's a zenity issue. if you've got 2.12.0 then it's probably that. if you're usin' 2.12.1 then i dunno what it is, but from a rough look at your log it seems that zenity ain't recognizin' an option, possibly because of the accent in 'qualità'. so try and replace 'qualità' with 'qualita' in the script and tell me what happens! i can't do that myself cause it works fine over here :)

and for everyone, i just added a really nice feature to the new version of the script, which will be out in three or four days! :)

ciao! :)

edo

---

### Post by SilvioTO on 2005-11-08
I have installed zenity 2.12.1-0ubuntu1

---

### Post by Koybe on 2005-11-09
Hello thetroublemaker.

As you asked me I sent you a mail with the report of my error. Log and a little analysis. I've done it on the 29 of october and still got no answer from you... Did you get it?

---

### Post by thetroublemaker on 2005-11-09
koybe. yup, i got your email. all i can answer is that **you** can switch the file detection method for the mpc files. since the problem is in your files, which have an incorrect metatag, i can't change the detection method for everyone. so here's what you can do: go to the is_mpc function and substitute the line with this one:

echo $1 | grep -i '\.mpc$' || file -b "$1" | grep 'Musepack'

it will probably work out fine from then. also, the new version is out soon, so you would have to do that with thattun, too. hope it works for you! :)

ciao! :)

edo

---

### Post by Koybe on 2005-11-09
Thank you it's nice.

---

### Post by thetroublemaker on 2005-11-09
hi everyone! :)

version **0.3.1** is out! you can download it from here: [http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert). new features include: rewrote the question askin' process. instead of a series of questions we now have a checklist with options! changed checks for two codecs. rewrote a function for efficiency. created an installer. updated the readme. updated english, italian and dutch translations. bugfixes.

as usual, new features suggestions, pointin' bugs out, new translations, new translated readme's, and updates to existin' translations are **more than welcome**! :) we really need someone to update the spanish readme, for instance. but all the other things i listed are **very much needed**! :)

i would like to thankyou for all of your **awesome** feedback! keep it up, and i'll keep my work up too! :)

ciao! :)

edo

---

### Post by bionnaki on 2005-11-10
sweet! 
however, mp3 is not listed...although I do have lame installed.
any ideas?

---

### Post by SilvioTO on 2005-11-10
I'm upgraded script, but have the same problem :???: . I persist to tell that lame in ubuntu 5.10 don't recognized correctly; in fact, avidemux also don't recognize the lame library but I have lame installed.

---

### Post by bionnaki on 2005-11-12
how do you convert monkey's audio files? where do I download "mac" from?

---

### Post by Lizzy on 2005-11-12
Hi  everyone, i'm a desperate newbie who is in desperate need for a wma-->mp3 converter, since  was so stupid and downloaded wma files and paid for'em a time ago, before Linux got into the picture. So far i can't even play them on Mplayer (w32codecs is installed....so is lame) 

I tried it with a script...can't even figure out what to do and what those commands are good for aso..aso...aso.. TOOOOOO DIFFICULT
This one looks nice on the website, and since i'm still very much of a GUI freak a nd a total noob. But i don't even know what to download, how to install it :confused:  :confused: .... Any tips there guys??

Help would be realy appriciated

---

### Post by Lizzy on 2005-11-12
And now i also know why they can't be played.....grrrrr... the files are DRM protected..... what now :confused: :confused: :confused:  I paid for those files and can't play them anywhere :mad:

---

### Post by thetroublemaker on 2005-11-12
you guys! a **deb package for ubuntu** is now available! please download it and test it at [http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert). after you install it, you need to erase your old version of audio-convert, if you have it, and run audio-convert-install **as user**. if many things go well, the package will probably be available in dapper in the future. so test it and let me know!

silvioto. did you change the accented letter like i typed?

bionnaki. i think you need to go to [http://sourceforge.net/projects/mac-port](http://sourceforge.net/projects/mac-port).

lizzy. well, now there's a deb package. follow the instructions i gave you. basically. install the deb package, then run audio-convert-install from console as user. after you do that, you can right-click on the audio file, or group of files, you need to convert, choose scripts, then audio-convert, and a very easy-to-use graphical interface will pop up! :) but yeah, if the wma's are drm'ed then i doubt it'll be of much use in that sense. but you can still use it for every other audio conversion! :)

you guys, let me know! :)

ciao! :)

edo

---

### Post by SilvioTO on 2005-11-13
I'm correct qualità with qualita, and now the script work fine!! ok, thanks edo.

Ciao! :p

---

### Post by Lizzy on 2005-11-13
Hi, *caugh*.... I must be doing something wrong, or i am simply tooooo stupid.. I can't install it :confused: ... after i downloaded it i tried to install it... But i'm told there is no file or directory.... what am i doing wrong? Pretty sure i did something wrong.... i managed to install Limewire, w32codecs before amongst other things...

Would appreciate a step by step howto... sorry to bother everyone :oops: 

Cheers

---

### Post by WetWilly on 2005-11-13
A nice feature would be the possibility to "cut" the files.

For example I only want the data between time 0:30 to 1:25!

:KS

---

### Post by Stormy Eyes on 2005-11-14
Nice work so far, but I've noticed one little problem. When converting Ogg to MP3, I've noticed that the Artist/Album/Title/Tracknumber tags aren't being copied from the ogg file into the mp3 file even if I choose the "pass the metatags on to the new files" option. Would it be possible to bring over the tag info as well to avoid having to bother with EasyTag?

---

### Post by bigiii on 2005-11-16
I have the same problem as above except I am using flac to mp3

---

### Post by iguanaphobic on 2005-11-19
[QUOTE=Lizzy]Hi, *caugh*.... I must be doing something wrong, or i am simply tooooo stupid.. I can't install it :confused: ... after i downloaded it i tried to install it... But i'm told there is no file or directory.... what am i doing wrong? Pretty sure i did something wrong.... i managed to install Limewire, w32codecs before amongst other things...

Would appreciate a step by step howto... sorry to bother everyone :oops: 

Cheers[/QUOTE]

Open a terminal window.

Odds are you downloaded the audio-convert_0.3.1.1-0ubuntu1_all.deb file to your desktop, so let's start by changing to the Desktop folder.

```
~$cd Desktop
```

Then look for the audio-convert_0.3.1.1-0ubuntu1_all.deb file.

```
~$ls *.deb
audio-convert_0.3.1.1-0ubuntu1_all.deb
```

Highlight the name of the .deb with the left mouse button and then right-click on this selection. Select copy.

```
~$sudo dpkg -i (CTRL-Shift-V)
```

This will paste in the name of the .deb and install it.

---

### Post by jrincon87 on 2005-11-19
Hey, thetroublemaker. Is there a way that I can get audio-convert to erase automatically all the original files after being transcoded?
And here goes some suggestions for further versions (also, what asked you for below goes here too):
1. Prevent the progress window from splashing on-top every time it starts converting another song. I mean, if you're doing another thing and you have audio-convert minimized, when it starts converting another song, it jumps up and you have to minimize it again.
2. Put a "converting done" message that pops up. (Useful for keeping it minimized).
3. Keep a "profile" of the quality you use (obviously being able to change it).
Anyways, great program!
Thanks.

---

### Post by aznboi on 2005-11-30
Works for me when i convert one by one... but when i do more than one file, it only converts part of the song and then stops... any way to fix this? thnx troublemaker

---

### Post by cwhitmore75 on 2005-12-15
Ok... I must be completely dense or something.  I downloaded the .deb package, installed it.  Get this:

```
christian@mainbox:~/Desktop$ sudo dpkg -i audio-convert_0.3.1.1-0ubuntu1_all.deb
Selecting previously deselected package audio-convert.
(Reading database ... 84956 files and directories currently installed.)
Unpacking audio-convert (from audio-convert_0.3.1.1-0ubuntu1_all.deb) ...
Setting up audio-convert (0.3.1.1-0ubuntu1) ...
```

Everything should be great, right?  Not so much... nothing is showing up in my scripts menu when I right click and I can't find a trace of it installed anywhere.  Am I missing something? :confused: 

Thanks in advance.

---

### Post by PolarBear64 on 2006-01-03
I also have the same problem when I run the *.deb package nothing in scripts folder and cant use anyone got a line on how to fix this problem or a walk through on using the tar or some other install method this would be great to get working I have about a 1000 songs that need to go from flac to ogg.

thanks

---

### Post by Chrissss on 2006-01-03
After you installed the deb package, just execute

# audio-convert-install

one time as user. This will copy the script into your nautilus scripts directory.

CU
 Christoph

---

### Post by linkunderscore on 2006-01-03
EDIT:

I just ran audio-convert-install again and now everything works perfectly.

---

### Post by Aphorism on 2006-01-03
Nice script effort...

Maybe you can work on making this GUI a little better too...


soundconverter

sudo apt-get install soundconverter

It is a great newbie GUI driven converter.

---

### Post by guilag on 2006-02-03
Hi !

I'm running ubuntu dapper and i've installed nautilus-script-audio-convert package version: 0.3.1.1-0ubunt1.

The files have well been copied in the folder /usr/share/nautilus-scripts/ but when i do a right click on a music file in nautilus, no actions is shown to me.

I have read in this forum to execute the audio-converter-install file but I don't find it.

What can I do ?

Thanks for your help.

---

### Post by pakux on 2006-02-05
Hi Edo, 

I was trying to use your script (sudo-installed from .deb ubuntu package with dpkg -i and audio-convert-install as user)

it apparently works (asked for output type, etc etc) but in spite of confirmation message ("... goobye") I'm not able to find any output file. Tried both mp3 and ogg with identical results.

I found a similar question some posts ago in this same thread but no answer to it.

I have checked and all flac, lame and vorbis-tools are installed (last version).

the only weird thing I can see is when wav is selected; options dialog shown is empty.

any ideas?

grazie.


EDIT: As a last chance, I made a brand new flac from one of my cd's and tried to apply the script.... bingo! it works flawlessly. Then I decided to test the flac program to decode the original troubling file and surprinsingly it gave me an error message:

[FONT="Courier New"]ERROR while decoding data state = FLAC__STREAM_DECODER_READ_FRAME[/FONT]

googling around it seems to be a bug with some flac encoders in windows environment (i didn't read so much, actually). The point is that, at the end of the day, your script works fine but the flac files I was trying to convert appear to be partially corrupted (but can be still reproduced).

grazie ancora.

---

### Post by Mguel on 2006-03-04
Hi, thanks a lot for your script! is very useful and safe a lot of work.

I'm using Kubuntu and wanted to add the script to the action menu in konqueror and I managed to do so, so I wanted to post it here in case anyone else finds it useful. I have to say though that I'm new to linux, so correct me please if I have something wrong, and forgive me if this is too basic ;) (at least it can be useful for another kubuntu newbie).

The steps are the following:
- download a compressed version of audioconverter
- extract it to a temporal folder
- copy "audio-convert" file to "/usr/bin/"
- and create the following file (i.e. "audioconvert.desktop") under: "~/.kde/share/apps/konqueror/servicemenus/"
> [Desktop Entry]
Encoding=UTF-8
ServiceTypes=audio/wav,audio/x-wav,audio/x-mp3,audio/mp3,application/ogg,audio/vorbis
Actions=audioconvert


[Desktop Action audioconvert]
Name=Audio Convert
Icon=kcmsound
Exec=audio-convert %u- save the file,

And now you should have an extra entry under actions of the filetypes on "ServiceTypes".

You can add to the "ServiceTypes" the other supported audio formats, and change the Icon to another one or simply delete that line.

I have tested it with wav/mp3/ogg conversions and is working fine.

I hope this helps someone.

Cheers,
Mguel

---

### Post by mszl_1 on 2006-03-08
im having trouble just getting the music to a folder in a short period of time! it seems to take forever to load the music to the library. im using fedora 4 at the minute. also is it possible to listen to the music as you add to the library? thanx:???:

---

### Post by twowheeler on 2006-03-08
Just wanted to say thanks, it works great and saved me a lot of work.

---

### Post by maqi on 2006-03-13
I can convert from/to wav, flac, ogg & mp3. For some reason conversion to aac is not working. I have faac-1.24clean-0ubuntu3. I do not have the dev package installed.

Anyone have any ideas as to why this is so?

---

### Post by fizgig on 2006-03-25
Just a quick note - I can't use the script by right-clicking a file on my desktop - it says it converts it (instantly) but it doesn't.  In order to convert a file that is on my desktop, I have to open nautilus and browse to it and right-click it in nautilus.  Just FYI.

---

### Post by majikstreet on 2006-03-26
this project was mentioned briefly in the CPU magazine for March 2006 in a K3B music burning article..

way to go!

---

### Post by adamkane on 2006-04-07
audio-convert doesn't seem to work on Ubuntu, since Ubuntu needs aac ape, flac, mpc and wma support.

First you may need to install extra repositories:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

Next install the version of mplayer that matches your system.

Intel Pentium:

```

sudo apt-get install mplayer-686

``` 
AMD K Series (Duron, Athlon or Sempron):

```

sudo apt-get install mplayer-k7

``` 
Older legacy system:

```

sudo apt-get install mplayer-386

``` 
Download and install the remaining audio conversion packages:

```

sudo apt-get install lame vorbis-tools flac faac faad nasm
cd ~/Desktop
mkdir install
cd install
wget http://morgoth.free.fr/ubuntu/pool/main/m/monkeys-audio/monkeys-audio_3.99-u4-b3-0.1~5.10mlk1_i386.deb
wget http://morgoth.free.fr/ubuntu/pool/main/m/monkeys-audio/libmac2_3.99-u4-b3-0.1~5.10mlk1_i386.deb
wget http://download.savannah.nongnu.org/releases/audio-convert/audio-convert_0.3.1.1-0ubuntu1_all.deb
sudo dpkg -i *.deb

``` 
Option 1.
After you install the audio-convert debian packages, open a terminal:

```

audio-convert-install

``` 

This places a shortcut in your nautilus-scripts directory.

Option 2.
If you prefer to have the audio-convert script, not a shortcut, placed in your nautilus-scripts directory:

```

sudo mv /usr/bin/audio-convert ~/.gnome2/nautilus-scripts

``` 
Nautilus-script Mini-Howto:
[http://g-scripts.sourceforge.net/]("http://g-scripts.sourceforge.net/")

---

### Post by VCSkier on 2006-04-08
any chance we could get support for converting wavpack images with embedded cuesheets to individual track files?  I have all my cd's backed up in this format, from my windows days (a couple months ago), and so far, foobar2000 through wine is the only way i can find to convert them.

---

### Post by bored2k on 2006-04-09
I kinda hate how intrusive it is. Other than that, it's great.

---

### Post by beagle on 2006-04-10
Hi TroubleMaker,
I read most of the posts in this thread.  Still, I can't get AudioConvert to work.
I down loaded latest AudioConvert.deb package from sourceForge.  Installed with dpkg command; moved the script to Gnome2.
When I open Nautilus and right click on a '.wma' file, I only see menu options such as,
Open with - Totem Movie player, MPlayer, VLC player, Other application,
Scripts (gedit-root, root-nautilus-here, search-here and open script folder),
Send to,
Create Archive,
Properties...

There is no option for AudioConvert.

Any help in getting it to work for me is welcome.  Thanks,

---

### Post by wheelspin on 2006-04-16
This is a little script I wrote based on audio-convert (great program by the way) to shrink my mp3 files to my portable player, generally I rip them pretty with high quality for playback on the pc but the files sizes prohibit getting very may onto my 512MB player. I don't want to re-rip them all just for my player so that's where the script comes in. To install copy shrink-mp3-to-usb into your script folder. ${HOME}/.gnome2/nautilus-scripts/
It needs to be executable so: chmod u+x 
more complete instructions are inside the script itself if needed.
I should have noted earlier that it requires:
lame
id3v2
zenity
maybe some others

---

### Post by adamkane on 2006-04-21
For those who wonder why audio-convert doesn't work, please see Post 61.

The original poster didn't bother to detail the steps to get audio-convert working on Ubuntu.

Again, please see Post 61, if you can't get audio-convert to work.

---

### Post by El_Virdi on 2006-05-01
[QUOTE=beagle]Hi TroubleMaker,
I read most of the posts in this thread.  Still, I can't get AudioConvert to work.
I down loaded latest AudioConvert.deb package from sourceForge.  Installed with dpkg command; moved the script to Gnome2.
When I open Nautilus and right click on a '.wma' file, I only see menu options such as,
Open with - Totem Movie player, MPlayer, VLC player, Other application,
Scripts (gedit-root, root-nautilus-here, search-here and open script folder),
Send to,
Create Archive,
Properties...

There is no option for AudioConvert.

Any help in getting it to work for me is welcome.  Thanks,[/QUOTE]


I had the same problem, the trouble seems to be that the script is not autoenabled in nautilus, i solved it writing in the console:

```
nautilus-script-manager enable ConvertAudioFile
```

cant remember if i had to restart nautilus or gnome. Anyway it worked like a dream after that, its a very handy script.

The only thing i miss is CBR options for encoding mp3 with lame, i dont know if this option can be enabled editing any of the script files ¿any clue?

---

### Post by danielph on 2006-05-21
Hi,

Firstly just to say this is an awesome bit of work. It is a great tool.

However, I cannot get it to work correctly. It installed flawlessly. All my codecs are installed and up to date and it integrates well with nautilus. 2 problems:

1. No mp3 (lame) support - there is no option displayed for this. I only get ape, aac, ogg and wav. I would love to just use ogg, but I need mp3 for an old ipod.
2. tried to convert to ogg which looked good, but the results were white noise. On further investigation it was the flac to wav conversion that had the problem. Checked flac by running flac --decode and it worked ok.

I have gone through this thread but cannot find any answers, but I may have missed something I guess.

thanks in advance for your input

Regards

Dan

---

### Post by adamkane on 2006-05-21
audio-convert works well, but it doesn't do everything it advertises. Some conversions do not work. Some conversions to OGG don't work, and some conversions to MP3 don't work. Overall it works very well though, if you are flexible.

When you try to make an all-on-one Nautilus-script that works with any linux distribution, this type of thing always happens.

audio-convert will never function completely for every conversion, until someone writes an application, rather than a Nautilus-script.

---

### Post by seditiousmonkey on 2006-06-17
hi,

im trying to convert .m4a to .ogg but when i execute the script i get an error that reads "you don't have the right codec to decode the selected file.  missin' codec faad"

converting from .mp3 to .ogg works fine so the script seems to be working i just don't know what dependancies or whatever i may be missing

i also have libfaad2-0 and libmp4v2-0 installed which are the only packages that come up on a search for faad in synaptic

---

### Post by adamkane on 2006-07-24
audio-convert was written to work on any linux platform. It will convert anything as long as you have the codec. Unfortunately not every codec is available for dapper yet.

---

### Post by Hikaru79 on 2006-07-25
> **Mguel said:**
> Hi, thanks a lot for your script! is very useful and safe a lot of work.

I'm using Kubuntu and wanted to add the script to the action menu in konqueror and I managed to do so, so I wanted to post it here in case anyone else finds it useful. I have to say though that I'm new to linux, so correct me please if I have something wrong, and forgive me if this is too basic ;) (at least it can be useful for another kubuntu newbie).

Firstly, thank you very much for your script, Mguel =) However, I'm having trouble getting it to work. I've followed the instructions, and the "Convert Audio" entry correctly appears when I go to "Actions" of a valid filetype. However, nothing happens after that. It just hangs. Any idea why this might be happening? =/

---

### Post by Mguel on 2006-07-26
> **Hikaru79 said:**
> Firstly, thank you very much for your script, Mguel =) However, I'm having trouble getting it to work. I've followed the instructions, and the "Convert Audio" entry correctly appears when I go to "Actions" of a valid filetype. However, nothing happens after that. It just hangs. Any idea why this might be happening? =/

I made it work in Kubuntu 5.10, now I'm using Dapper and tested it and can't make it work neither.

Maybe it's the lack of codecs as mentioned by adamkane.

You can try:
[**audiokonverter**]("http://www.kde-look.org/content/show.php?content=12608") from kde-look

Although:
> It needs oggenc, oggdec, faac, faad, flac, mplayer and lame to work. id3lib is optional for full functionality.

Cheers, and sorry for being of no more help.

---

### Post by rpalyvoda on 2006-08-06
Just wanted to thank you for such a great script. One of the best things I've found for multimedia (because it's simple and ti works!!!)

---

### Post by lomomo on 2006-08-08
Thanks for the script, nice work. Anyway, does somebody know if there is something similar to this script but for converting image file formats?

It will be very coolo i we could convert image formats and resize them just with a few clicks.

---

### Post by slimb on 2006-08-28
seems to convert fine for me in relatively short order if i choose "standard".  gonna give the files a listen for a while and determine the actual quality :)

otherwise it works wonderfully, thanks!!

---

### Post by trypokaridos on 2006-09-12
Thank's for the SUPER script but i have a small problem.

I'm converting mpc to mp3 everything is working fine from shell.

When i try to convert files from Nautilus Scripts progress window open and close very quckly and the script creates (*.mp3) files to parent folder with size 625 bytes.

Thank's for yours time

---

### Post by VCSkier on 2006-09-12
again, any chance of wavpack, or cuesheet support planned?

---

### Post by MrChonks on 2006-09-15
> **trypokaridos said:**
> Thank's for the SUPER script but i have a small problem.

I'm converting mpc to mp3 everything is working fine from shell.

When i try to convert files from Nautilus Scripts progress window open and close very quckly and the script creates (*.mp3) files to parent folder with size 625 bytes.

Thank's for yours time

Hey, where did you find the mpc codec to use for this?  I am trying to do the same thing.

EDIT: Nevermind.  I went to musepack.net and downloaded mppdec-linux-libc6-1.95z2.zip to /usr/bin, unzipped it and then chmodded it to 755.  Works like a charm now.

---

### Post by em3raldxiii on 2006-10-15
I second the desire for WavPack support.

---

### Post by h2gofast on 2006-10-25
Excellent script, much respect.
I am having trouble with m4a to mp3 conversion.  The conversion is working but it isn't putting the metatag info in the mp3 file.  
I know the meta info is in the m4a I checked with banshee, but after the conversion the mp3 plays but contains no metadata.


I took a look at your script and it looks like it calls id3tag to set metatag info.  
I didn't see id3tag anywhere in repositories. 
I might have time over the next few weeks to experiment with corrections.  There are command line tag editors that might work.

I got soundconverter working, this one is handy because you can run it from a nautilus right click, but soundconverter gets the metatags right.  
I would have to recommend soundconverter.
cheers 
h2.

---

### Post by haaskaa on 2006-11-14
Great script! One question though: Is it possible to make it recursively convert all *.wma files in many folders as suppose to manually doing each folder?

---

### Post by adamkane on 2006-11-19
audio-convert uses id3lib to create id3 tags, but id3lib isn't in the Universe Repository.

To get tags working, replace id3info with id3ed -i.

```

if (is_mp3 "$1")
    then
        artist_name=`id3ed -i "$1" | awk '/artist/ { print substr($0, match($0, /:/) + 2 ) }'`
        album_name=`id3ed -i "$1" | awk '/album/ { print substr($0, match($0, /:/) + 2 ) }'`
        song_name=`id3ed -i "$1" | awk '/songname/ { print substr($0, match($0, /:/) + 2 ) }'`
        track_number=`id3ed -i "$1" | awk '/tracknum/ { print substr($0, match($0, /:/) + 2 ) }'`
    fi

```

Thanks to wheelspin.

---

### Post by BLTicklemonster on 2006-11-19
Excellent, now I can burn some cds for my car! (prolly could already anyway with k3b or something but anyway.....)

---

### Post by HugoPalma on 2007-01-10
This seems to work fine for all formats except ape. When i try to run the script on a .ape file i get "Format not supported".

I installed all the packages as described, including monkey-audio.
Any ideas ?

---

### Post by Bossieman on 2007-01-11
> **fizgig said:**
> Just a quick note - I can't use the script by right-clicking a file on my desktop - it says it converts it (instantly) but it doesn't.  In order to convert a file that is on my desktop, I have to open nautilus and browse to it and right-click it in nautilus.  Just FYI.

Same for me, I thought the script was broken

---

### Post by Bossieman on 2007-01-11
I cant pass on the id3tags. What program do i need for the script to work?
Fixed it! Thanks for this script!

---

### Post by kiddvenom on 2007-04-08
How do I enable this script in Thunar?

---

### Post by ap9er on 2007-05-09
> **kiddvenom said:**
> How do I enable this script in Thunar?

1) Right click on the song you want to convert
2)' Open with' --> 'Other Application'
3) Uncheck 'Use as default for this kind of file'
4) Drop down the 'Use a custom command' box
5) Enter in ' audio-convert '

Should now open with audio-convert script. For all subsequent converisons there will be a pre-set option in 'Other Application' to open audio-convert.
You can also highlight more than one file at a time instead of having to continually right click, but will need to manually enter in the format and audio quality for each song.

---

### Post by nrune on 2007-06-30
Okay this script works great, except for mp3,  I can not get it to convert to mp3.  Flacc, Wav, and ogg work fine.  MP3 leaves me with a 0byte size file.  No clue as to why.  Lame is installed and mp3 is a choice. Help?

---

### Post by nrune on 2007-06-30
um nevermind turns out was one file that would not convert for some reason.  thanks

---

### Post by Sadsailor on 2008-01-08
Hello,
I tried installing audio convert  - few questions...apologies for the very long and tedious post but I'm a confused newbie and figured it better to list exactly what I've done...
(I'm running Ubuntu studio)

1. on the freshmeat page [http://freshmeat.net/projects/audio-convert/](http://freshmeat.net/projects/audio-convert/) there are a list of versions of audio convert. I chanced the debian package as I'm running ubuntu - (is this right??)  but I don't understand what all the various versions are for or how to make an informed choice of which one to install... any tips?

2. Also there is a list of dependencies further down the page; should I install each of these manually or are they included in the main package?

3. Having downloaded 'audio-convert_0.3.1.1-0ubuntu1_all.deb' to my desktop, I double clicked on it and it launched the package installer which seems to have done the job of installing it,  however, I can't see where to launch the actual application from... it's not listed in my applications menu. Neither when I right-click on a .mp3 file does it give me the option to open it with 'audio-convert'.
Where is the application? How do I get at it via GNOME?

4.I ran it from the terminal window and it tells me I'm missing the lame codec (see printout of terminal window below). I tried getting this using apt-get lame but this didn't work... so I downloaded lame from [http://sourceforge.net/project/showfiles.php?group_id=290&package_id=309](http://sourceforge.net/project/showfiles.php?group_id=290&package_id=309) instead.  (Again, I wasn't sure which version to download but I went with lame-3.97.tar.gz which is listed as the latest version.)
What should I do with lame-3.97.tar.gz once I have it on my machine? Where should I extract it to? Currently it's extracted onto the desktop but when I tried running audio-convert from the terminal window again it still tells me I'm missing the lame codec so I guess it needs to be in a specific location??

5. Presumably the same thing will happen with the rest of the dependencies required to run audio-convert; how do I get it all up and running? 

laura@laura-laptop:~/Desktop$ audio-convert

+ version=0.3.1

+ title='audio convert 0.3.1'

+ pleasesel='please select at least one file.'

+ noselec='audio convert 0.3.1 converts audio files. please select at least one file.'

+ choix='extension of output file:'

+ warning=warning

+ proceed='already exists. overwrite?'

+ recur='audio convert 0.3.1 can'\''t convert a directory. please select at least one file.'

+ conversion='converting file:'

+ ask_artist='enter the artist name:'

+ ask_album='enter the album name:'

+ ask_song='enter the song name:'

+ ask_track='enter the track number:'

+ ask_quality='select the desired quality:'

+ ask_compression='select the desired compression level:'

+ confirmation='do you want to convert'

+ decoding='decoding file:'

+ ask_fields='manually enter file metatags'

+ ask_confirmation_question='get prompted a confirmation question before convertin'\'' each file'

+ no_codec='you don'\''t have the right codec to decode the selected file. missin'\'' codec:'

+ not_supported='format not supported'

+ completed='conversion completed. goodbye!'

+ ask_to_pass='pass the metatags on to the new files'

+ options='choose from the followin'\'' options:'

+ options_conflict='options one and two conflict. please unselect one of them'

+ case $LANG in

+ '[' 0 -eq 0 ']'

+ zenity --error --title=warning '--text=audio convert 0.3.1 converts audio files. please select at least one file.'

+ exit 1

laura@laura-laptop:~/Desktop$ audio-convert voxcycle1.mp3

+ version=0.3.1

+ title='audio convert 0.3.1'

+ pleasesel='please select at least one file.'

+ noselec='audio convert 0.3.1 converts audio files. please select at least one file.'

+ choix='extension of output file:'

+ warning=warning

+ proceed='already exists. overwrite?'

+ recur='audio convert 0.3.1 can'\''t convert a directory. please select at least one file.'

+ conversion='converting file:'

+ ask_artist='enter the artist name:'

+ ask_album='enter the album name:'

+ ask_song='enter the song name:'

+ ask_track='enter the track number:'

+ ask_quality='select the desired quality:'

+ ask_compression='select the desired compression level:'

+ confirmation='do you want to convert'

+ decoding='decoding file:'

+ ask_fields='manually enter file metatags'

+ ask_confirmation_question='get prompted a confirmation question before convertin'\'' each file'

+ no_codec='you don'\''t have the right codec to decode the selected file. missin'\'' codec:'

+ not_supported='format not supported'

+ completed='conversion completed. goodbye!'

+ ask_to_pass='pass the metatags on to the new files'

+ options='choose from the followin'\'' options:'

+ options_conflict='options one and two conflict. please unselect one of them'

+ case $LANG in

+ '[' 1 -eq 0 ']'

+ is_mp3 voxcycle1.mp3

+ file -b voxcycle1.mp3

+ grep MP3

+ echo voxcycle1.mp3

+ grep -i '\.mp3$'

voxcycle1.mp3

+ depformat=

+ which lame

+ is_mp3 voxcycle1.mp3

+ file -b voxcycle1.mp3

+ grep MP3

+ echo voxcycle1.mp3

+ grep -i '\.mp3$'

voxcycle1.mp3

+ zenity --error --title=warning '--text=you don'\''t have the right codec to decode the selected file. missin'\'' codec: lame'

+ exit 1

---

### Post by Sadsailor on 2008-01-08
Ok, Please ignore the bit about lame in the last post - I tried installing it using apt-get install and it worked. Re-ran audio-convert voxcycle.mp3 and it seems to have worked according to the terminal window but I can't find the converted file... where should it be?
While audio-convert was running a dialog box appeared asking me to “select items from the list” but there are no items in the list... what should show up here and why is nothing showing up? Despite the fact that I can't select anything, when I hit 'okay' it appears to continue with the conversion process, ending with another dialog box which says conversion complete! Goodbye' ...but no sign of my .wav..
What am I doing wrong?
Thanks

laura@laura-laptop:~/Desktop$ audio-convert voxcycle1.mp3
+ version=0.3.1
+ title='audio convert 0.3.1'
+ pleasesel='please select at least one file.'
+ noselec='audio convert 0.3.1 converts audio files. please select at least one file.'
+ choix='extension of output file:'
+ warning=warning
+ proceed='already exists. overwrite?'
+ recur='audio convert 0.3.1 can'\''t convert a directory. please select at least one file.'
+ conversion='converting file:'
+ ask_artist='enter the artist name:'
+ ask_album='enter the album name:'
+ ask_song='enter the song name:'
+ ask_track='enter the track number:'
+ ask_quality='select the desired quality:'
+ ask_compression='select the desired compression level:'
+ confirmation='do you want to convert'
+ decoding='decoding file:'
+ ask_fields='manually enter file metatags'
+ ask_confirmation_question='get prompted a confirmation question before convertin'\'' each file'
+ no_codec='you don'\''t have the right codec to decode the selected file. missin'\'' codec:'
+ not_supported='format not supported'
+ completed='conversion completed. goodbye!'
+ ask_to_pass='pass the metatags on to the new files'
+ options='choose from the followin'\'' options:'
+ options_conflict='options one and two conflict. please unselect one of them'
+ case $LANG in
+ '[' 1 -eq 0 ']'
+ is_mp3 voxcycle1.mp3
+ file -b voxcycle1.mp3
+ grep MP3
+ echo voxcycle1.mp3
+ grep -i '\.mp3$'
voxcycle1.mp3
+ depformat=
+ which lame
/usr/bin/lame
+ is_mp3 voxcycle1.mp3
+ grep MP3
+ file -b voxcycle1.mp3
+ echo voxcycle1.mp3
+ grep -i '\.mp3$'
voxcycle1.mp3
+ which oggenc
/usr/bin/oggenc
+ is_ogg voxcycle1.mp3
+ file -b voxcycle1.mp3
+ grep Vorbis
+ echo voxcycle1.mp3
+ grep -i '\.ogg$'
+ depformat=' ogg'
+ which mppenc
+ which mppdec
+ is_mpc voxcycle1.mp3
+ grep Musepack
+ file -b voxcycle1.mp3
+ grep -i '\.mpc$'
+ echo voxcycle1.mp3
+ which flac
+ is_flac voxcycle1.mp3
+ grep FLAC
+ file -b voxcycle1.mp3
+ echo voxcycle1.mp3
+ grep -i '\.flac$'
+ which mac
+ is_mac voxcycle1.mp3
+ file -b voxcycle1.mp3
+ grep data
+ which faac
+ which faad
+ is_aac voxcycle1.mp3
+ file -b voxcycle1.mp3
+ grep AAC
+ echo voxcycle1.mp3
+ grep -i '\.aac$'
+ which mplayer
+ is_wma voxcycle1.mp3
+ grep Microsoft
+ file -b voxcycle1.mp3
+ echo voxcycle1.mp3
+ grep -i '\.wma$'
+ is_wav voxcycle1.mp3
+ file -b voxcycle1.mp3
+ grep WAVE
+ grep -i '\.wav$'
+ echo voxcycle1.mp3
+ depformat=' ogg wav'
+ '[' '!' '' ']'
++ zenity --title 'audio convert 0.3.1' --list --column=Format ogg wav --text 'extension of output file:'
+ formatout=wav
+ '[' 0 '!=' 0 ']'
+ '[' 0 -ne 0 ']'
+ '[' '!' wav ']'
+ question_list voxcycle1.mp3 1
+ '[' wav == mp3 ']'
+ '[' wav == ogg ']'
+ '[' wav == flac ']'
+ '[' wav == aac ']'
+ '[' 1 -gt 1 ']'
+ ask_questions
+ repeat=1
+ '[' 1 -eq 1 ']'
++ zenity --list --checklist --column '' --column 'choose from the followin'\'' options:'
+ answers=
+ echo ''
+ grep -i 'pass the metatags on to the new files'
+ repeat=0
+ '[' 0 -eq 1 ']'
+ parse_questions
+ echo ''
+ grep -i 'pass the metatags on to the new files'
+ pass_metatags=1
+ echo ''
+ grep -i 'manually enter file metatags'
+ fields=1
+ echo ''
+ grep -i 'get prompted a confirmation question before convertin'\'' each file'
+ confirmation_question=1
+ '[' wav '!=' wav ']'
+ file_number=1
+ '[' 1 -gt 0 ']'
+ for i in '$formatout'
+ in_file=voxcycle1.mp3
++ echo voxcycle1.mp3
++ sed 's/\.\w*$/.wav/'
+ out_file=voxcycle1.wav
++ echo wav
++ sed 's/"//g'
+ i=wav
++ true
+ ls voxcycle1.wav
+ grep -v '^ls'
ls: voxcycle1.wav: No such file or directory
+ '[' 1 -gt 1 ']'
+ caf voxcycle1.mp3 voxcycle1.wav wav
+ is_mp3 voxcycle1.mp3
+ grep MP3
+ file -b voxcycle1.mp3
+ echo voxcycle1.mp3
+ grep -i '\.mp3$'
voxcycle1.mp3
+ '[' wav = ogg ']'
+ '[' wav = mpc ']'
+ '[' wav = flac ']'
+ '[' wav = ape ']'
+ '[' wav = aac ']'
+ '[' wav = wav ']'
+ mp3_decode voxcycle1.mp3 'converting file:'
++ sed 's/\.\w*$/.wav/'
++ echo voxcycle1.mp3
+ temp_file=voxcycle1.wav
+ lame --decode voxcycle1.mp3 voxcycle1.wav
+ awk '-vRS=\r' '-F[ /]+' '(NR>2){if((100*$2/$3)<=100)print 100*$2/$3; fflush();}'
+ zenity --progress '--title=audio convert 0.3.1' '--text=converting file: voxcycle1.mp3' --auto-close
+ break
+ shift
+ '[' 0 -gt 0 ']'
+ completed_message
+ zenity --info --title 'audio convert 0.3.1' '--text=conversion completed. goodbye!'

---

### Post by casperlingus on 2008-02-24
To use this in nautilus you need to open up a terminal and type

```
nautilus-script-manager enable ConvertAudioFile
```

When you restart nautilus, you should have a "Scripts" menu when you right click on a file.  The rest should be self-explanatory

---

### Post by king mob on 2008-02-28
Dear troublemaker and the rest.
Is this stuff for people who know what they're doing?
'Cause I tried installing (that worked) but after that I'm in the dark.
When I right-click an audio file there's no converting options in the menu.
I tried reading the other posts here, but that is beyond my comprehension of computer science. So could you tell me if this is something I could get the hang of, or are there easier alternatives for converting audio files in ubuntu?

Thank you
Sincerely

km

---

### Post by king mob on 2008-02-28
HurraH!
It's not beyond my comprehension anymore!
It all works, thank you for a great addition to my virtual life.
And sorry for disturbing.

km

---

### Post by king mob on 2008-02-28
Hi again.
I'm back with a new query now that I have enjoyed the script for a few hours.
It's mpc. I installed mppdec, but I'm not allowed to convert mpc's in nautilus.
"you don't have the right codec to decode the selected file. missin' codec: musepack-tools"
so I checked this forum [http://forum.musepack.net/showthread.php?t=362](http://forum.musepack.net/showthread.php?t=362) but that did't help much so now I'm back here.

km

---

### Post by burneverything on 2008-03-12
> **casperlingus said:**
> To use this in nautilus you need to open up a terminal and type

```
nautilus-script-manager enable ConvertAudioFile
```

When you restart nautilus, you should have a "Scripts" menu when you right click on a file.  The rest should be self-explanatory

that code returns:
Error: No script with that name available

after checking the nautilus script folder there was nothing there :(
tried reinstalling the script with the installer but that didn't work.

I found the script in /usr/bin as well as the audio-convert-install script
I ran the install script which put a link in the nautilus scipt folder > still no dice
I copied the audio-convert script to the nautils scipt folder > still no dice 

am I missing something or am I just plain stoopeed?
[edit]
D'oh
I must be stoopeed
or my install is
:)
after about Nth restart of nautilus the script is now here
shame I did all my converting in audacity in the meantime.
[/edit]

---

### Post by burneverything on 2008-03-19
Well

script is there.
it asks me all the questions.
then pretends to have done the conversion in about 5 seconds, but there is nothing to be found anywhere.
I'm trying to convert WAV files into ogg-vorbis, oggenc is installed and works fine when used from the terminal.

any ideas or step I should take to give you the info you need to help me?

---

### Post by Ludek on 2008-07-04
Hello Everyone,

New user here and very impressed with the script so far. Fast, easy, just like me!

One thing though, I have backed up my music to CD in FLAC format and I want now to convert the files to AAC to have them available for my computer use and also for my portable player. 

So I open the CD, right click on the files, select the AAC option but I don't have an choice to where to save my newly converted files to.

Am I missing something or does the script not have this feature yet?

Many thanks,

Ludek :)

---

### Post by hbb on 2008-08-12
Perhaps I'm missing something, but it doesn't seem like audio-convert is actually doing anything on my computer...

I've installed audio-convert as a Nautilus script (on 7.10, in case that's relevant), and can run the script on .wma files just fine. All the available conversion formats show up, quality selection menu, etc. and audio-convert ends with a polite little message telling me everything went off without a hitch...

...BUT, this new .mp3 (or .aac, or .flac, etc.) file which has supposedly been created for me is nowhere to be found - not in the folder of the original .wma, not in my home folder, not on the Desktop...

I've noticed that several other users seem to have had this same problem, and  I have yet to actually see anyone give them help, so perhaps this is just another futile post falling on dead ears, but what gives? Have any of those users had success in finding these damn files? Is this program just making a good show of things, or is it really creating these files (and where the heck are they, in that case)?

---

### Post by tomski on 2008-08-12
did you try:

sudo updatedb

sudo locate nameoffile.mp3/aac/etc

---

### Post by hbb on 2008-08-12
Yes. Nothing shows up. I can only assume an error is occuring somewhere, but nothing in the output of the program would suggest that.

---

### Post by lad3391 on 2008-12-27
feeling like a noob cuz you can't get this to work? i know i did lol. heres some stuff i found, hopefully you can use ;)
1) the .gnome2 folder (which has the nautilus scripts folder in it) is HIDDEN, go to your home folder, and hit ctrl+h to show the hidden folders
2) if youre not getting the script to show up even after installation try this
     2a) go here: [http://packages.ubuntu.com/gutsy/nautilus-script-audio-convert](http://packages.ubuntu.com/gutsy/nautilus-script-audio-convert)  
     2b) this link is the package details, download the deb package manually from the bottom, find where it downloaded (usually either home folder, or desktop) right click and hit extract here, then open the folder it extracted, and use the extract here command once more on the folder labeled data. open that, then open usr, then share, then nautilus scripts
     2c) take the convertaudioscript file and place it in your nautilus scripts folder that is located in the .gnome2 folder
     2d) run this in terminal: chmod 740 ~/.gnome2/nautilus-scripts/ConvertAudioFile

hope that helps somebody ;)

also if youre interested, heres a similar script for video. i havent tested it extensively, but it should work


[http://ubuntuforums.org/showthread.php?t=193754](http://ubuntuforums.org/showthread.php?t=193754)

---

### Post by rogue_ronin on 2009-07-03
id3tag works, as of Xubuntu 8.10.

But to get the metadata from ogg, you must change
```

314 artist_name=`ogginfo "$1" | grep artist | cut -d \= -f 2`
315 album_name=`ogginfo "$1" | grep album | cut -d \= -f 2`
316 song_name=`ogginfo "$1" | grep title | cut -d \= -f 2`
317 track_number=`ogginfo "$1" | grep tracknumber | cut -d \= -f 2`
```

to

```
314 artist_name=`ogginfo "$1" | grep ARTIST | cut -d \= -f 2`
315 album_name=`ogginfo "$1" | grep " ALBUM" | cut -d \= -f 2`
316 song_name=`ogginfo "$1" | grep TITLE | cut -d \= -f 2`
317 track_number=`ogginfo "$1" | grep TRACKNUMBER | cut -d \= -f 2`
```

where line 315 must have a tab preceding ALBUM. (Otherwise it grabs a bunch of replaygain data, too.)

m a r

---

### Post by adamsmith111 on 2011-07-26
hi by using the technology you cant get accuracy in the document that you were converted. the [transcription service]("http://www.qualitytranscript.com/transcription-services.html") companies providing the convert file facilities with 98% accuracy in this format.
 The [Audio to text transcription]("http://www.qualitytranscript.com/mp3-to-text-transcription.html") service is another popular arm in the transcription service industry. It has become a part and parcel of day to day life. Its impact is that much great one cannot imagine without its presence.

---

### Post by adamsmith111 on 2011-07-26
Audio files conversations not up to the standard in the software tool. so i m now using the transcription service facility to keep my record properly with accuracy...

---

