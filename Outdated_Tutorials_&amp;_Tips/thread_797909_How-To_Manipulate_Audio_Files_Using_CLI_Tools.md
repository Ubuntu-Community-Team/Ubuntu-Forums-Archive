---
title: "How-To: Manipulate Audio Files Using CLI Tools"
date: 2008-05-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Christmas on 2008-05-17
I initially posted this tutorial 
[here]("http://lintut.50webs.org/tut_audio.html"). The tutorial explains how to use tools like oggenc, vorbiscomment or flac to manipulate audio files. It works in both Ubuntu and Debian, and probably any other Debian-based distribution.


**Manipulate Audio Files Using CLI Tools in Debian**
Updated: May 08, 2008 - v0.2b

This is a tutorial about using CLI (Command Line Interface) tools in Ubuntu and Debian to manipulate, encode and decode various audio formats, like FLAC or OGG Vorbis. It describes the packages needed to install, and some basic commands for converting audio files and working with CUE and FLAC files.The commands in this tutorial were tested in Kubuntu 7.10 Gutsy Gibbon and Debian Lenny, with all the updates to date.

Command line tools such as oggenc or flac can be used for example to convert FLAC (Free Lossless Audio Codec) files or WAV (WaveForm Audio Format) in OGG Vorbis files. Vorbis is a free audio codec offering lossy compression, and is known to have a smaller size and better quality (at least for lower bitrates) than the widely used MP3.

All the tools used in this tutorial are available through four packages, and to install them issue the following command as root (Ubuntu users must precede it with 'sudo', since the root account is disabled by default in Ubuntu):
```

apt-get install flac vorbis-tools cuetools shntool

```
These packages contain several programs and utilities for manipulating audio files. To convert a FLAC file into WAV do a:
```

flac -d file.flac

```
If there are several FLAC files in the same directory, use the command:
```

flac -d *.flac

```
And all the files with the .flac extension will be converted. Of course, one can include many more options, like the name of the output file. Do a 'man flac' or a 'flac --help' command to see detailed help and a list of options. To convert either WAV or FLAC files into OGG, execute one of the following commands:
```

oggenc -b 192 *.wav
oggenc -b 192 *.flac

```
The '-b' option refers to the bitrate of the resulting OGG file, in this case the average bitrate being 192 kbps. Or you can choose to use the quality option:
```

oggenc -q 6 *.flac

```
The quality is represented on a scale from 1 to 10, 10 being the highest. More details on the official website. Some albums may come as a single FLAC file and a CUE file which stores the information needed to split the former. In this case the programs 'cuebreakpoints' and 'shnsplit' come in handy:
```

cuebreakpoints album_name.cue | shnsplit album_name.flac

```
And the same goes with the WAV:
```

cuebreakpoints album_name.cue | shnsplit album_name.wav

```
It will result in several .flac or .wav files, splitted according to the lengths specified in the CUE file. You can also edit the CUE file with a text editor and change the split lengths, for concatenating two melodies or more in a single one.

Once you obtained the desired OGG Vorbis files, you may want to edit or remove their tags. To clear all the tags in an OGG Vorbis file, use the 'vorbiscomment' tool. For example:
```

touch file
vorbiscomment -w song.ogg -c file

```
The first command will create an empty file (if it doesn't already exist). The second one will edit the tags in song.ogg with the info found in file, which is none. Here is a script to remove all the tags from all vorbis files with OGG extensions in a directory:
```

#!/bin/bash

echo "OGG Tag Remover"
echo "Creating empty file..."
touch file

echo "Removing all tags in OGG files..."
for i in *.ogg; do
        echo "Executing command 'vorbiscomment -w \"$i\" -c file'..."
        nice -n 15 vorbiscomment -w "$i" -c file
done

echo "Removing empty file..."
rm file

echo "Done! All tags removed."

```
Copy this into a file of your choice, say 'vorbis_rm.bash', make it executable and then and run it:
```

chmod 755 vorbis_rm.bash
./vorbis_rm.bash

```
All the tags in OGG files will be removed. This is useful when you have large albums and you want to clear some wrong edited tags in one command and start clear.


Some audio players like Amarok offer an easy tag editing system. However, to make your work even faster, you can use various Bash scripts which edit as much as is needed to just leave only fields like 'TITLE' unfilled. Next is an example of a script which automatically fills the 'TRACKNUMBER' field for each OGG file in a directory:
```

#!/bin/bash

echo "OGG TRACKNUMBER Edit"

n=1
for i in *.ogg; do
        echo "Executing command 'vorbiscomment -a \"$i\" -t \"TRACKNUMBER=$n\"'"...
        nice -n 15 vorbiscomment -a "$i" -t "TRACKNUMBER=$n"
        n=$((n + 1))
done

echo "Done. TRACKNUMBER tags completed."

```
After running this script in a directory with OGG files, all of them will have the 'TRACKNUMBER' field completed.


I'm open to suggestions, corrections or additions, so please feel free to give feedback on this.

---

### Post by smcguinness on 2008-08-05
Hi There

Is this something that can be used and applied using a web app? I am looking to create a web app that combines multiple audio files (probably mp3 format) into one long mp3 file. Thanks.

Seth

---

### Post by swanee on 2010-12-23
I use wget to "record" ogg files from a public radio station's stream. Embedded in the stream are numerous title=tags. From the current song title, to a weather update. Playing them in, say, xmms works fine. But if I try to load one onto my Sansa Fuze player, the multiple title tags scramble its little brain. Is there a way to remove *all* such tags from an ogg file? I have tried vorbiscomment -w -c /dev/null file.ogg, but this only removes the *first* tag.

Thanks for any help!

---

