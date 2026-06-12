---
title: "Recursively searching and converting WMA files to MP3"
date: 2015-12-12
forum: Programming Talk
---

### Post by Spency on 2015-12-12
Hi all, 
I'm a bit of a programming noob and would greatly appreciate anyones input. I'm trying to help a buddy out who has a pretty vast collection of WMA music files, organized into different sub directories of the Music directory. What we want is a script or program that can recursively go through sub folders and convert WMA files to MP3, and then delete the WMA files.

We started off with [soundconverter]("http://soundconverter.org/") - it froze everytime we tried, and we tried it on 3 different machines 1 14.0.4 and 2 different 15.10 systems. Besides, even if it did work it wouldn't do what we wanted.

Next we hit this [page]("http://askubuntu.com/questions/55352/convert-library-of-wma-tracks-to-mp3s/55469#55469") and found some code that seemed very promising. 

```
[COLOR=#111111][FONT=Consolas]#!/bin/bash[/FONT][/COLOR]
current_directory=$( pwd )

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names 
[COLOR=#111111][FONT=Consolas]for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; done[/FONT][/COLOR]
```

The thing is, this doesn't recursively search through sub directories for WMAs to convert, otherwise it does exactly what we want. At a distance, it seems like it would be an easy line of code to get this script to recursively search multiple subdirectories directories. Is anyone willing to help us out?

---

### Post by Vaphell on 2015-12-12
```
#!/bin/bash

shopt -s globstar

for f in **/*.[Ww][Mm][Aa]
do
    path=${f%/*}
    filename=${f##*/}
    new=${filename// /_}  # space -> underscore
    new=${new,,}             # lowercase
    mv -v -- "$f" "$path/$new"
done

for f in **/*.wma
do
    mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader "$f" && lame -m s audiodump.wav -o "$f"
    mv -v -- "$f" "${f/%.wma/.mp3}" 
done
```

i typed the code here directly so test it well first on some sample files

---

### Post by Spency on 2015-12-12
It works brilliantly! Thank you SOOOOOO MUCH!

---

### Post by Spency on 2015-12-16
I spoke too soon... everything seemed to work, until we started trying to play some of the files on systems that did not accept wma. Shame on me for not checking the codecs of the newly created files. It seems all the script did was rename all the files with mp3.

---

### Post by Spency on 2015-12-16
Turns out that piece of code I gave you was responsible for that. 

This actually works though:
```
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$i" && lame -m j -h --vbr-new -b 320 audiodump.wav -o "`basename "$i" .wma`.mp3"; done; rm -f audiodump.wav
```

Only works on my 14.04 desktop, not on my 15.10 desktop, and doesn't delete the wma files. No idea where I found this.

---

### Post by Spency on 2015-12-16
I tried to insert the code into you're script, and it's working but there's one issue....
```

#!/bin/bash


shopt -s globstar


for f in **/*.[Ww][Mm][Aa]
do
    path=${f%/*}
    filename=${f##*/}
    new=${filename// /_}  # space -> underscore
    new=${new,,}             # lowercase
    mv -v -- "$f" "$path/$new"
done


for f in **/*.wma
do
    mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$f" && lame -m j -h --vbr-new -b 320 audiodump.wav -o "`basename "$f" .wma`.mp3"
    rm -f audiodump.wav
    rm -f "$f" "${f/%.wma}"
done

```

... the issue now is the mp3 files are being created in the main directory and not in the respective directory it's being converted from.

---

### Post by Spency on 2015-12-17
Script seems to be now working:

```

#!/bin/bash


shopt -s globstar


for f in **/*.[Ww][Mm][Aa]
do 
    path=${f%/*}
    filename=${f##*/}
    new=${filename// /_}  # space -> underscore
    new=${new,,}             # lowercase
    mv -v -- "$f" "$path/$new"
done


for f in **/*.wma
do  
    mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$f"  && lame -m j -h --vbr-new -b 320 audiodump.wav -o "${f%.wma}.mp3"
    rm -f audiodump.wav
    rm -f "$f" "${f/%.wma}"
done

```

Thanks to: 
Vaphell (this post)|
Muru (from [AskUbuntu]("http://askubuntu.com/questions/710378/script-recursively-convert-wma-files-to-mp3-then-remove-wma-files"))
Rory Aslop (from [AskUbuntu]("http://askubuntu.com/questions/55352/convert-library-of-wma-tracks-to-mp3s"))
Unknown (see post details)

---

