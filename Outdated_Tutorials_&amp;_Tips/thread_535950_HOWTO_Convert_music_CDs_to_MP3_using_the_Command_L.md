---
title: "HOWTO: Convert music CDs to MP3 using the Command Line."
date: 2007-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2007-08-27
I have tried a variety of programs to rip my personal collection of music from CD to mp3 format on my computer. I consistently found significant shortcomings with many of the GUI programs and throughout I was a little nonplussed at the complexities of whole process. Fortunately I came across the program abcde which eliminates the needless froth of the GUI as well as seamlessly takes care of much of the complexity of the process. abcde is available in the repositories and can be downloaded as follows:

```
sudo apt-get install abcde cd-discid lame cdparanoia id3 id3v2
```The program abcde is actually a long script that manipulates a handful of programs, which I have conveniently added into the Terminal command above. It can actually do a great deal more than simply produce reasonable mp3 files but I will leave you to explore its many other possibilities. The programs that will be used to produce mp3s in this example are:[LIST]
[*]**abcde**
    "A Better CD Encoder" = abcde! Ordinarily, the process of grabbing the data off a CD and encoding it, then tagging or commenting it, is very involved. The abcde script is designed to automate this.
[*]**cd-discid**
    In order to do CDDB (Compact Disc Database) queries over the Internet, you must know the DiscID of the CD you are querying. cd-discid provides you with that information. It outputs the discid, the number of tracks, the frame offset of all of the tracks, and the total length of the CD in seconds, on one line in a space-delimited format.
[*]**cdparanoia**
    cdparanoia retrieves audio tracks from CDROM drives. The data can be saved to a file or directed to standard output in WAV, AIFF, AIFF-C or raw format. For the purposes of conversion to mp3 abcde directs cdparanoia to produce WAV files.
[*]**lame**
    LAME is a program which can be used to create MPEG Audio Layer III (MP3) files.
[*]**id3**
    id3 is an ID3 v1.1 tag editor. ID3 tags are traditionally put at the end of compressed streamed audio files to denote information about the audio contents.
[*]**id3v2**
    id3v2 is an ID3 v2 tag editor. ID3 tags are traditionally put at the end of compressed streamed audio files to denote information about the audio contents. Using this command line software you can add/modifiy/delete id3v2 tags and optionally convert id3v1 tags to id3v2.[/LIST]abcde looks for two files on startup: /etc/abcde.conf and ~/.abcde.conf. The file abcde.conf is a fully commented configuration file that is well worth looking at, if only to copy to your home directory as ~/.abcde.conf (as is most usually done). Or if you are only interested in creating mp3s my gift to you, Gentle Reader, is my own ~/.abcde.conf file:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       MP3 format using abcde version 2.3.99.6
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for MP3. In this case
# the alternatives are gogo, bladeenc, l3enc, xingmp3enc, mp3enc.
MP3ENCODERSYNTAX=lame 

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/lame
LAME=lame

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
LAMEOPTS='--preset extreme' 

# Output type for MP3.
OUTPUTTYPE="mp3"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"               

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

With this simple setup complete all that is required is to place the music CD of your choice in your drive and run the command abcde from a Terminal and make a cup of tea while your mp3s are being created. The script can of course do so much more than this. You can create ogg or flac files, you can normalise the volume of your mp3s or you can be much more adventurous with your lame settings. Enjoy your exploration of these great CLI programs!

Andrew
April 9th, 2009

---

### Post by GrammatonCleric on 2007-10-31
Thanks! I've been looking for some like this.

-GC

---

### Post by andrew.46 on 2007-10-31
Hi,

 Thanks:

> **GrammatonCleric said:**
> Thanks! I've been looking for some like this.

 The fuller version of the page also shows ogg and flac conversion as well as the syntax to convert a cd to all 3 formats with one command:

_[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)_

 Great script that one, but not all that well known unfortunately,

                   Andrew

---

### Post by rockstar on 2007-11-08
Alright, I understand the idea, but you lost me at copying the file to your home drive and using a script.  How do I get ABCDE to use one of your scripts (/etc/.abcde.conf) instead of the /ect/abcde.conf?

---

### Post by andrew.46 on 2007-11-08
Hi,

 Just a small misunderstanding:

> **rockstar said:**
> Alright, I understand the idea, but you lost me at copying the file to your home drive and using a script.  How do I get ABCDE to use one of your scripts (/etc/.abcde.conf) instead of the /ect/abcde.conf?

 You have to create a file in your home directory called .abcde.conf and then if you like copy my suggested settings into it. You can then place a cd in your drive, run the command abcde and the cd will be converted to mp3.

 Let me know if this is little clearer?

          Andrew

---

### Post by rockstar on 2007-11-08
So, I did what you said and copied the file:

cp /etc/abcde.conf ~/.abcde.conf

Then I opened the file and pasted your script

gedit ~/.abcde.conf

But then when I run ABCDE it still uses the original config file because it gets stuck on CDDB choices

Thanks so much!

---

### Post by rockstar on 2007-11-08
Here is what I get when I run;

Sudo abcde

Multiple exact matches:
#1: ---- folk 4c092806 Led Zeppelin / Physical Graffiti (Disc 1) ----
1: Custard Pie
2: The Rover
3: In My Time of Dying
4: Houses of the Holy
5: Trampled Under Foot
6: Kashmir

#2: ---- misc 4c092806 Led Zeppelin / Physical Graffiti (Disc 1) ----
1: Custard Pie
2: The Rover
3: In My Time of Dying
4: Houses of the Holy
5: Trampled Under Foot
6: Kashmir

#3: ---- rock 4c092806 Led Zeppelin / Physical Graffiti (Disc One) ----
1: Custard Pie
2: The Rover
3: In My Time Of Dying
4: Houses Of The Holy
5: Trampled Under Foot
6: Kashmir

/home/paul/abcde.4c092806/cddbchoices (END)

---

### Post by andrew.46 on 2007-11-08
Hi,

 Now I see:

> **rockstar said:**
> Here is what I get when I run;
Sudo abcde

Multiple exact matches:
#1: ---- folk 4c092806 Led Zeppelin / Physical Graffiti (Disc 1) ----
[...]

#2: ---- misc 4c092806 Led Zeppelin / Physical Graffiti (Disc 1) ----
[...]

#3: ---- rock 4c092806 Led Zeppelin / Physical Graffiti (Disc One) ----
[...]
(END)

A couple of small points:

[LIST=1]
[*]You should not have to use sudo for this
[*]Although you appear to have things working I have been a little less than clear, for which my apologies. You *either* copy the /etc/abcde.conf to home and edit it as .abcde.conf *or*  you create a blank ~/.abcde.conf file and then copy my configuration into it. But I think in your case this has made no difference.
[/LIST]

 The problem you have encountered here is a cddb database problem: 3 different people have entered the details of this album :-), in this case in 3 different categories.  All that happens then is abcde waits for you to select 1, 2 or 3 and then the script continues.

  All the best; perservere as you are almost there!

             Andrew

---

### Post by rockstar on 2007-11-09
Alright I went through and removed abcde and re-installed in just in case I broke something.

So I tried a different cd. I'm pretty sure it got passed the CDDB and I hope It's using your FLAC script

[http://people.aapt.net.au/~adjlstrong/abcde.html#flac](http://people.aapt.net.au/~adjlstrong/abcde.html#flac)

But I must have done something else wrong as well.


210 rock 4d0a6c07 CD database entry follows (until terminating `.')
# xmcd
#
# Track frame offsets:
#       182
#       47090
#       75907
#       89350
#       117595
#       136480
#       157792
# Disc length: 2670 seconds
# Revision: 35
# Processed by: cddbd v1.5.2PL0 Copyright (c) Steve Scherf et al.
#
# Submitted via: libkcddb 0.10
#
DISCID=470a6507,490a6407,4d0a6c07
DTITLE=Led Zeppelin / Presence
DYEAR=1976
DGENRE=Classic Rock
TTITLE0=Achilles Last Stand
TTITLE1=For Your Life
TTITLE2=Royal Orleans
TTITLE3=Nobody's Fault But Mine
TTITLE4=Candy Store Rock
TTITLE5=Hots On For Nowhere
TTITLE6=Tea For One
EXTD=
EXTT0=
EXTT1=
EXTT2=
                 [ Read 38 lines (Converted from DOS format) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


I really appreciate the help!

---

### Post by andrew.46 on 2007-11-09
Hi,

 I hope you are still having fun? You have bumped into another simple problem:


> **rockstar said:**
> But I must have done something else wrong as well. [..]

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
!

 The program that is open there is nano, which must be your default console editor. What you have done is selected' y' at the following question:

> Edit selected CDDB data? [y/n] (n):

 which then opens the cddb info in nano for further editing. Unless you wish to edit the information select 'n' instead and the process will continue. Hope this helps you on the way!

            Andrew

---

### Post by kpkeerthi on 2007-11-09
abcde is simple and just works. I've been using this nice tool for a long time. There is already a post in tutorials section [http://ubuntuforums.org/showthread.php?t=109429](http://ubuntuforums.org/showthread.php?t=109429) about abcde that I followed.

---

### Post by rockstar on 2007-11-12
Thanks for all the Help

I've gotten cds to work and rip! However, I still can't figure out how to tell ABCDE how to choose the first Database entry in CDDB like that example I gave you before.

Thanks again,

---

### Post by smartboyathome on 2007-11-12
This is an awesome tool! One question: is there a way to lower how fast it spins the CD? It makes a whole bunch of noise.

---

### Post by magiver on 2007-11-12
> **rockstar said:**
> Thanks for all the Help

I've gotten cds to work and rip! However, I still can't figure out how to tell ABCDE how to choose the first Database entry in CDDB like that example I gave you before.

Thanks again,

just press q and it'll ask you which database entry you want to select.

---

### Post by magiver on 2007-11-12
abcde is great, but i have a problem using it.
just as sound juicer, it shows a wrong duration on all the mp3s i throw at it. is this a lame problem (the wav files have the right duration) or is this a noob-user problem (i'm doing something wrong)?

edit: the wrong duration only appears when i check it in the properties dialog (right click -> properties). In rythmbox it appears to be right

---

### Post by thecrwth on 2008-01-25
I have a question about this.  Everything works great except for one thing.  The only change I made to .conf file was

OUTPUTDIR="$HOME/music/" 

My mp3s end up there, but they are locked with administrative priviledges.  They are read only and executable to users.  I run abcde from my usr>bin file, which I know is an admin rights file, but I am not sure why they are outputing with admin rights to my home directory.

Any thoughts?

---

### Post by andrew.46 on 2008-01-25
Hi,

I suspect I can see the problem:

> **thecrwth said:**
> I have a question about this.  Everything works great except for one thing.  The only change I made to .conf file was

OUTPUTDIR="$HOME/music/" 

My mp3s end up there, but they are locked with administrative priviledges.  They are read only and executable to users.  I run abcde from my usr>bin file, which I know is an admin rights file, but I am not sure why they are outputing with admin rights to my home directory.

Any thoughts?

Have you actually modified the file /etc/abcde.conf? Try copying the file to your $HOME directory and running it from there instead. That is:

```
$ cp -v /etc/abcde.conf $HOME/.abcde.conf
```

and I suspect that this *might *solve the issue.

      Andrew

---

### Post by Piraja on 2008-10-24
Thanks for this thread! Just installed the packages and tried out abcde and it's splendid. I would have used the "Thank Andrew.46 for this useful post" button but I don't see any in this thread...

---

### Post by andrew.46 on 2008-10-24
Hi Piraja:

> **Piraja said:**
> Thanks for this thread! Just installed the packages and tried out abcde and it's splendid. I would have used the "Thank Andrew.46 for this useful post" button but I don't see any in this thread...

Glad it all worked out :-). I had more or less abandoned this guide as there seem to be a couple of abcde guides already on this forum and I have already written a more advanced one on my own website. The 'thanks' thing I suspect is because this represents an older posting perhaps?

Another suggestion though to make your life easier is the program easytag which will fine-tune your tags after abcde has done its magic. It is in the repositories:

```
sudo apt-get install easytag
```

and is a great assistance for those who like their tags perfect :-).

  Andrew

---

### Post by inso_741 on 2010-05-23
that is just great....thanx for this how-to :P

---

