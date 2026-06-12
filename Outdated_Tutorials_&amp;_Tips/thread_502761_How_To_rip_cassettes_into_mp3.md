---
title: "How To: rip cassettes into mp3"
date: 2007-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by irwand on 2007-07-17
I tested this using my Ubuntu machine while ripping about 100 or so cassette tapes. It was a long project, so I was using Ubuntu 6.4 up to 7.4. This tutorial should work on other distribution too, except for the package installation/uninstallation parts.

Hardware you need:
[LIST]
[*]cassette player with line out. Hopefully one that can play both sides and stop automatically to make it easier.
[*]sound card with line in
[*]huge hard drive is preferrable. Wav files are generally huge.
[/LIST]

Software packages you need:
[LIST]
[*]audacity - great sound editor
[*]gramofile - detect song tracks and separate them
[*]lame - encode wav files into mp3
[*]mp3info - mp3 tag editor and viewer
[/LIST]

To install those, you just need to issue the command:

```
sudo aptitude install audacity gramofile lame mp3info
```

your repository might not include lame, but there are other postings in this forum that talks about how to install lame on your ubuntu machine, so just search around.

Once everything is installed, you need to generally go through the following steps:
[LIST=1]
[*]record the cassette to a big wav file
[*]separate the song tracks into separate wav files
[*]encode each wav files to mp3
[/LIST]

Let's talk about it one by one.

1. Record the cassette into a big wav file.

Preferrably, you should use line out from the cassette player to line in to your sound card to preserve the original sound as much as possible. Then launch audacity. Make sure that you're playing side A first, just so you get the orientation correct in your recording to make it easier later. Play the cassette, make sure that audacity can see the audio wave just fine. Play with the recording level to your satisfaction.

Once this is done, rewind the cassette back, start anew in audacity. Then play the cassette and let audacity record for a while. If you have a huge hard drive, you can let it be for a while. Don't worry about stopping the recording right after the cassette stop playing. With audacity, you can erase long silent portion of the sound wave. Do exactly that, trim the silent portion of the beginning and the trailing end. Also, trim the silent portion in the middle where your cassette player switches side.. BUT don't trim this part too much, because it helps to know where exactly the switch happens so that you know which part of the wave is which song later easier. Maybe leave about 10 second-ish there.

Once that's done, save the file as regular audacity file. You may want to rip all your cassettes into audacity files first and get this part over with. When you're ready to execute the next step, use audacity, open the audio file, then do the menu File->Export As WAV, to save the file into a big huge wav file into a new EMPTY directory. This directory will be renamed later automatically.

2. Separate the song tracks into separate wav files

This is where gramofile comes in handy. Use Linux console (konsole or gnome-terminal), go to the directory where the big wav file resides. Launch gramofile, then select "Locate Tracks" and select your big wav file. It'll then present you with default settings, but IMHO, for cassettes, it works well if you change "global silence factor" to 15, and "Minimal length of inter-track silence" to about 10. For cassettes where the songs are very close together, tweak inter-track silence down, to 3 or 5. The settings should look like the following:

```
[X] Save/load signal power (RMS) data to/from .rms file

[ ] Generate graph files

Length of blocks of signal power data (samples)   : 4410

Global silence factor (0.1 %)                     : 15 
Local silence factor (%)                          : 5

Minimal length of inter-track silence (blocks)    : 5 
Minimal length of tracks (blocks)                 : 50

Number of extra blocks at track start             : 3
Number of extra blocks at track end               : 6
```

Well, let it then do its thing. Once it's done, it'll save the tracks it found in the name of your big wav file followed by ".tracks". Now comes the really time-consuming part. You must now edit that file (using your favorite text editor), and make sure that the track start and end timestamps of each song is correct. Do this by comparing those timestamps with the audio wave in audacity (you didn't close audacity yet, did you?). You may need to listen to specific sections of the sound wave in audacity to match up the track number with the song number in your cassette.

Once you're done with that, you can launch gramofile again, but this time select "Process the audio signal", then select your big wav file, and just use all the default settings, including the output file name (should be processed.wav or something like that). Gramofile will be nice to you and split all the tracks into individual wav file for each song. Now comes the last part.

3. Encode each wav files to mp3

If you followed all those instructions exactly, you'd be able to use this helper script. This script detects all your processed*.wav files in the current directory, and generate yet another script, that you have to edit to put the correct song title, artists, and album info. This final script is the one that encodes all processed*.wav files into mp3, put mp3 id tag appropriately, rename the files into nice readable file name, rename the current directory name, and optionally clean up the current directory from all other non-mp3 file.

So here's the script that generates that other script:

```
#!/bin/bash

if [[ "$2" == "" ]]; then
   echo "Usage: $0 <artist> <album>"
   echo "       if it's a various artists, use the following:"
   echo "       $0 various <album>"
   exit 1
fi

encoderScriptOutput=encodeAndRename.sh
inputFileName=processed*.wav
mp3Encoder="lame --preset fast medium"
mp3InfoCommand="mp3info -t \"TITLE\" -a \"ARTIST\" -l \"ALBUM\" -y YEAR -n TRACK"

if [[ "$1" == "various" ]]; then
   fileName="%l - %02n - %a - %t"
   dirName="Various - $2"
else
   fileName="%a - %l - %02n - %t"
   dirName="$1 - $2"
fi

echo "#!/bin/sh" > $encoderScriptOutput
chmod u+x $encoderScriptOutput

echo "# Encoding commands..." >> $encoderScriptOutput
for i in `ls $inputFileName`; do
   echo "$mp3Encoder $i ${i/.wav/.mp3}" >> $encoderScriptOutput
done

echo "# Setting mp3info..." >> $encoderScriptOutput
for i in `ls $inputFileName`; do
   track=`echo $i | sed 's/[^0-9]*\([0-9]\+\).*/\1/'`
   if [[ "$1" == "various" ]]; then
      echo "$mp3InfoCommand ${i/.wav/.mp3}" | sed "s/TRACK/$track/" | sed "s/ALBUM/$2/" >> $encoderScriptOutput
   else
      echo "$mp3InfoCommand ${i/.wav/.mp3}" | sed "s/TRACK/$track/" | sed "s/ALBUM/$2/" | sed "s/ARTIST/$1/" >> $encoderScriptOutput
   fi
done

echo "# Rename mp3 files..." >> $encoderScriptOutput
for i in `ls $inputFileName`; do
   echo "mv ${i/.wav/.mp3} \"\`mp3info -p \"$fileName\" ${i/.wav/.mp3}\`.mp3\"" >> $encoderScriptOutput
done

echo "# Rename current directory..." >> $encoderScriptOutput
currentDir=`pwd`
echo "mv \"$currentDir\" \"${currentDir%/*}/$dirName\"" >> $encoderScriptOutput

echo "" >> $encoderScriptOutput
echo "#UNCOMMENT THIS BELOW TO REMOVE ALL OTHER FILES BESIDES MP3" >> $encoderScriptOutput
echo "#ls -1 --hide=*.mp3 --quoting-style=literal | xargs rm -rf" >> $encoderScriptOutput
```

TIP: If you don't like the file name format that I use, you can change it yourself. Change the fileName and dirName to the name format of your liking.

Run the script in the directory where your big wav file resides as follows: "<scriptName> <artist> <album>", or, for various artists cassettes, "<scriptName> various <album>". After running that script, it'll generate another script into the current directory, called encodeAndRename.sh. Now you have to edit encodeAndRename.sh, and change TITLE, ARTIST, and YEAR appropriately for each songs. If you want the script to also delete all non-mp3 files in the current directory, uncomment the last line as well. Once you're done, save the file, and run "./encodeAndRename.sh", and that script will then encode each song into mp3, rename stuff, and optionally cleanup the directory, so you'll end up with a clean nice directory. By the way, you can't see the new directory name while you're still in that directory, but if you "cd ..", you'll see the new directory name.

That's it.. It'll take a lot of work, and it took me quite a lot of time to do, but I'm a happy camper now that this project is done. Good luck with this.

To revert your machine, just uninstall those software packages I mentioned in the beginning.

Keywords: convert cassettes mp3 Linux

---

### Post by reclusivemonkey on 2007-07-17
You might like this =]

[http://www.thinkgeek.com/computing/drives/7a8d/](http://www.thinkgeek.com/computing/drives/7a8d/)

---

### Post by irwand on 2007-07-17
That is wack! :-) I never knew there's such product.. It can convert songs into mp3 directly? I wonder how well it works. Oh well, now that all my cassettes are ripped, I'd have no use for it.. :-)

---

### Post by reclusivemonkey on 2007-07-17
> **irwand said:**
> That is wack! :-) I never knew there's such product.. It can convert songs into mp3 directly? I wonder how well it works. Oh well, now that all my cassettes are ripped, I'd have no use for it.. :-)

Thought you would like it =]

It seems you link it to your soundcard via leads. There is quite a comprehensive review here;

[http://www.devhardware.com/c/a/Peripherals/Plusdeck-Review/](http://www.devhardware.com/c/a/Peripherals/Plusdeck-Review/)

Its quite expensive for what it is, but anyone with a large amounts of tapes, some spare cash and a nostalgic bent could really enjoy that!

---

### Post by tinker123 on 2008-04-20
irwand ( the original poster):  thanks for the great how to!

---

### Post by Dynamo_Joe on 2008-04-21
Hi Inwand, 

Also one of my "to do" projects but I would convert to flac rather than mp3. 

Suppose your script can be modified to do it? 

Cheers!

---

### Post by 3rdalbum on 2008-04-21
Dynamo_Joe: I believe flac, unlike lame, can batch process files in a directory by this:

```
flac *
```

But I'm not in front of a Linux computer so I can't be absolutely sure, sorry. Try man flac.

Also, if you're doing tapes, you should use the Noise Removal filter in Audacity. Usually just setting it to its minimum works wonders.

---

### Post by Dynamo_Joe on 2008-04-22
Thanks for the tips, 3rdalbum! 

I'm doing my CD collection to flac at the moment but will be moving onto cassettes and LPs next (some of which will never be re-issued as CDs). 

CDs are simple ... just insert and "Sound Juicer" automatically do the rest. 

Once again, many thanks for the head's up.

---

