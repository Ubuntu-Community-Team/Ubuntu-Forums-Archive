---
title: "How To: Use Transcode to rip DVD audio tracks directly to mp3 under Karmic Koala"
date: 2009-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2009-12-16
This short guide aims to demonstrate how to directly rip audio tracks from DVD movies and with the same commandline transcode to mp3 using Transcode v1.1.4 from the Karmic Koala Repository. It also aims to 'test the waters' to see if a more comprehensive Transcode guide will be warranted on these Forums! 

----------------------
**Preparation...**
----------------------

First install Transcode from the Karmic Koala Repository:

```
sudo apt-get install transcode
```

and then ensure you have a copy of libdvdcss2 available for encrypted DVD support by adding the Medibuntu repository and installing the required library:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update && sudo apt-get install libdvdcss2

```

The good news is that under Karmic Koala the standard installation of Transcode allows import from DVDs and export to mp3 with no further setup! 

-------------------------
**Transcode to mp3...**
-------------------------

I will explain the commandline step by step so those not familiar with Transcode can see how it all fits together, and finally give the complete commandline. First you must give Transcode an indication of what import module is required and also what export module to use:

```

transcode -x null,dvd -y null,tcaud

```

The first option is *-x null,dvd* which tells Transcode that we will not import video but we require the dvd import module for audio. The *--y null,tcaud* option sets the export modules where again video will not be exported but the transcode audio module will be used for the audio. Next the commandline tells Transcode where the input file is and which title, chapter, angle and audio track to use:

```

-i /dev/dvd -T 1,3,1 -a 0

```

The first option is *-i /dev/dvd* and this pretty self-explanatory since we are ripping from a DVD after all. The next option *-T 1,3,1 -a 0* tells Transcode to use the first title, third chapter, first angle and audio track 0 of the DVD, remember that this will change according to the DVD you are working with. If you are not sure that you have selected the appropriate section and track of the DVD you can interrogate the DVD with:

```

tcprobe -i /dev/dvd

```

to see the actual makeup of tracks on the DVD and then test your choice with tccat and MPlayer as follows:

```

tccat -i /dev/dvd -T 1,3,1 -a 0 | mplayer -cache 1024 -

```

Finally to add in some sound and lame options and give the output file location:

```

-E 44100,16,2 --lame_preset standard -m $HOME/Desktop/output.mp3

```

Transcode understands the lame presets so this is what I have used here as well as a few basic options for the sound: *-E 44100,16,2* which dictates the audio output samplerate, bits per sample and number of channels. Of course the final option *-m $HOME/Desktop/output.mp3* simply gives the location and name of the final file. And thus the final commandline is:

```

transcode -x null,dvd -y null,tcaud -i /dev/dvd -T 1,3,1 -a 0  \
-E 44100,16,2 --lame_preset standard -m $HOME/Desktop/output.mp3

```

How cool is that! I hope when the commandline is dissected as I have done above it is all a little more understandable and I wish you all the best with your further exploration of this great program....

Andrew

---

### Post by mjitkop on 2010-06-12
Excellent thread, andrew.46!

Tonight I was looking for an easy and quick way to extract audio from a concert DVD that I bought yesterday and I found this thread.

Thanks to your instructions that I adapted for my needs, I was able to get all the tracks as MP3.

If this helps anybody else, you can create a plain text file that contains the extraction commands for every chapters. For example:

```
transcode -x null,dvd -y null,tcaud -i ~/Videos/BONJOVI_MSG -T 1,1,1 -a 0  -E 44100,16,2 -s 3 --lame_preset standard -m ~/Music/"Bon Jovi"/"Live at MSG 2009"/"01 - Lost Highway.mp3" &&
.
.
.
transcode -x null,dvd -y null,tcaud -i ~/Videos/BONJOVI_MSG -T 1,7,1 -a 0 -E 44100,16,2 -s 3 --lame_preset standard -m ~/Music/"Bon Jovi"/"Live at MSG 2009"/"07 - Living In Sin - Chapel Of Love.mp3" &&
transcode -x null,dvd -y null,tcaud -i ~/Videos/BONJOVI_MSG -T 1,8,1 -a 0 -E 44100,16,2 -s 3 --lame_preset standard -m ~/Music/"Bon Jovi"/"Live at MSG 2009"/"08 - Always.mp3" &&
transcode -x null,dvd -y null,tcaud -i ~/Videos/BONJOVI_MSG -T 1,9,1 -a 0 -E 44100,16,2 -s 3 --lame_preset standard -m ~/Music/"Bon Jovi"/"Live at MSG 2009"/"09 - Whole Lot Of Leavin'.mp3" &&
transcode -x null,dvd -y null,tcaud -i ~/Videos/BONJOVI_MSG -T 1,10,1 -a 0 -E 44100,16,2 -s 3 --lame_preset standard -m ~/Music/"Bon Jovi"/"Live at MSG 2009"/"10 - In These Arms.mp3" &&
.
.
.
transcode -x null,dvd -y null,tcaud -i ~/Videos/BONJOVI_MSG -T 1,20,1 -a 0 -E 44100,16,2 -s 3 --lame_preset standard -m ~/Music/"Bon Jovi"/"Live at MSG 2009"/"20 - Livin' On A Prayer.mp3"
```Make the file executable with the command typed from the directory where the file is saved:

```
chmod +x file_name
```and then run the file from the directory where it is saved as follows:

```
./file_name
```Great job! :guitar:

---

### Post by jcreneau on 2011-02-25
This is utterly fantastic - thanks for the tutorial on transcode.

---

### Post by jcreneau on 2011-02-26
Just a quick follow up - I have a talk on DVD that I want to rip to one mp3 file.  The problem is that the audio is broken into chapters.  Is there a way to rip the audio into one file rather than ripping it from each chapter individually?

---

### Post by mjitkop on 2011-02-27
I'm not sure but I would try the following command:

```
transcode -x null,dvd -y null,tcaud -i <VIDEO_SOURCE> -T <TITLE_NUMBER> -a 0 -E 44100,16,2 -s 3 --lame_preset standard -m <OUTPUT_MP3_FILE>
```

Basically, you just specify the title number without individual chapter numbers. I'm hoping it will take the whole title and convert it to MP3, including all chapters in the whole MP3 file.

Make sure to replace <VIDEO_SOURCE>, <TITLE_NUMBER> and <OUTPUT_MP3_FILE> to fit your needs.

I hope this works for you.

---

### Post by sorgud on 2011-04-18
Excellent! thank you so much...I have been looking for this simple solution.

---

### Post by andrew.46 on 2011-04-19
> **sorgud said:**
> Excellent! thank you so much...I have been looking for this simple solution.

Great news :). I will admit that I had assumed this little guide was dead and buried, good to see it still has some use!

---

### Post by andrew.46 on 2011-04-19
> **jcreneau said:**
> Just a quick follow up - I have a talk on DVD that I want to rip to one mp3 file.  The problem is that the audio is broken into chapters.  Is there a way to rip the audio into one file rather than ripping it from each chapter individually?

I must apologise, I have missed this query as I have not been monitoring this guide :(. In the Transcode man page there is a hint that this can be done, I have outlined the relevant section:

```

       -T  t[,c[,a]]
           select DVD title[,chapter[,angle]] [1,1,1]. Only a single chapter
           is transcoded. [B][COLOR="Red"]Use -T 1,-1 to trancode all chapters in a row. You
           can even specify chapter ranges.[/COLOR][/B]

```

I have not personally experimented with this but it seems the way to go...

---

### Post by sorgud on 2011-04-26
BTW I am using Lucid and it works.
Just one question. I used lsdvd to find out which chapter/audio to extract. Among several titles (16) there are two (seems the same) 
Title: 04, Length: 01:00:25.110 Chapters: 16, Cells: 16, Audio streams: 03, Subpictures: 03

Title: 05, Length: 01:00:25.110 Chapters: 16, Cells: 16, Audio streams: 03, Subpictures: 03
Where can I find information about what means every thing there... 
more precisely I want to know what "Cells" are, and what are those 3 audio streams. 
I have used your command line with -a 0 and -a 1 with "apparently" the same result 
thank you again

---

### Post by andrew.46 on 2011-04-26
Unfortunately I am not familiar with lsdvd and thus uncertain as to how one should interpret its output. My own method of determining which title, chapter and stream to extract is decidedly uncool, I navigate the dvd with SMPlayer and select the various streams until I find the one I want :).

---

### Post by mjitkop on 2011-04-26
> **sorgud said:**
> BTW I am using Lucid and it works.
Just one question. I used lsdvd to find out which chapter/audio to extract. Among several titles (16) there are two (seems the same) 
Title: 04, Length: 01:00:25.110 Chapters: 16, Cells: 16, Audio streams: 03, Subpictures: 03

Title: 05, Length: 01:00:25.110 Chapters: 16, Cells: 16, Audio streams: 03, Subpictures: 03
Where can I find information about what means every thing there... 
more precisely I want to know what "Cells" are, and what are those 3 audio streams. 
I have used your command line with -a 0 and -a 1 with "apparently" the same result 
thank you again

Hi there. My suggestion for DVD technical details is this site: [http://www.dvd-replica.com/DVD/index.php](http://www.dvd-replica.com/DVD/index.php)

I hope this helps.

---

### Post by chaltein on 2011-10-19
Incredible! Thanks a lot!

---

### Post by andrew.46 on 2011-10-19
> **chaltein said:**
> Incredible! Thanks a lot!

My pleasure, good to see this old guide still has some use :).

---

