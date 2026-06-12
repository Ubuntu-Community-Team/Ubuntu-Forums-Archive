---
title: "music_convert: Convert flac ogg and mp3 files with shell script"
date: 2006-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by diebels on 2006-02-04
Hi.
I usually backup my cd's in flac with sound-juicer. But not many portable players or standalone dvd-players play flac, so the files must be converted to ogg or mp3.

Just doing 'flac -d *.flac; oggenc *.wav' in a directory isn't nice since you loose tags. Also lame don't like globbing, and bash don't like spaces in filenames. So I have searched a bit for a program that can do this while keeping tags. Didn't find any, so made a little script. No gui yet, but it's quite easy to use.

Just run it without parameters to see usage.
```
#! /bin/sh
# music_convert, converts a couple music formats keeping tags
# Needs vorbis-tools, lame and flac installed
E_BADARGS=63
E_MISSING_PROGRAM=64
if [ ! -e /usr/bin/flac ] || [ ! -e /usr/bin/oggenc ] || [ ! -e /usr/bin/lame ]
then
        if [ $LANG == nb_NO.UTF-8 ]
        then
                echo "Du trenger vorbis-tools, lame og flac installert"
        else
                echo "You need vorbis-tools, lame and flac installed"
        fi
        exit $E_MISSING_PROGRAM
fi
print_usage() {
if [ $LANG == nb_NO.UTF-8 ]
then
        echo -e "$(basename $0) konverterer flac ogg og mp3 filer, beholder \
taggger\n"
        echo "Bruk: $(basename $0) fra til kvalitet"
        echo "der 'fra' kan være flac og ogg"
        echo "'til' kan være ogg og mp3"
        echo "'kvalitet' er standard, extreme eller insane for mp3 utputt"
        echo -e "og mellom -1 og 10 for ogg-vorbis\n"
        echo "eks: $(basename $0) flac ogg 7, $(basename $0) ogg mp3 extreme"
else
        echo -e "$(basename $0) converts flac ogg and mp3 files, keeping tags\n"
        echo "Usage: $(basename $0) from to quality"
        echo "where 'from' can be flac and ogg"
        echo "'to' can be ogg and mp3"
        echo "'quality' is standard, extreme or insane for mp3 output"
        echo -e "and between -1 and 10 for ogg-vorbis output\n"
        echo "ex: $(basename $0) flac ogg 7, $(basename $0) ogg mp3 extreme"
fi
}
if [ -z $3 ]
        then
        print_usage
        exit $E_BADARGS
fi
f=$1
t=$2
q=$3
get_tag() {
        if [ $f == flac ]
        then
                metaflac --show-tag=$1 "$i" | sed "s/$1=//"
        elif [ $f == ogg  ]
        then
                ogginfo "$i" | sed -n "s/^.*$1=//p"
        fi
}
wav_file() {
        echo "$i" | sed "s/\.$f/\.wav/"
}
for i in *.$f
do
if [ $f == flac ]
        then
        flac -d "$i"
elif [ $f == ogg ]
        then
        oggdec "$i"
else
        print_usage
        exit $E_BADARGS
fi
if [ $t == ogg ]
        then
        oggenc -q $q -t "$(get_tag TITLE)" -a "$(get_tag ARTIST)" \
        -l "$(get_tag ALBUM)" -d "$(get_tag DATE)" -N \
        "$(get_tag TRACKNUMBER)" -G "$(get_tag GENRE)" "$(wav_file)"
        rm "$(wav_file)"
elif [ $t == mp3 ]
        then
        lame --preset $q --tt "$(get_tag TITLE)" --ta "$(get_tag ARTIST)" \
        --tl "$(get_tag ALBUM)" --ty "$(get_tag DATE)" --tn \
        "$(get_tag TRACKNUMBER)" --tg "$(get_tag GENRE)" "$(wav_file)" \
        "$(echo "$i" | sed "s/\.$f/\.mp3/")"
        rm "$(wav_file)"
else
        print_usage
        exit $E_BADARGS
fi
done
exit 0

```

---

### Post by Parkotron on 2006-02-07
Nice script. I've actually been considering writing a KDE/C++ program to do this very task. In my case I'm moving flac files from a desktop with a big hard drive and nice stereo speakers to a laptop with limited storage and tinny speakers or headphones.

I've tested it out and it seems to perform as expected. You might however want to clarify that it works on all files of a given type in a particular **directory**. At first I was trying to pass it individual filenames. If you're looking to expand it further, you might want to consider adding the ability to pass the input and output directories via the command line. The option to search the input directory recursively could also be useful.

---

### Post by kozimodo on 2006-02-07
I believe soundconverter does what you want.  It is gui and appears to have preserved the tags.  It's in the universe repository.

---

### Post by beerorkid on 2006-02-09
that soundconverter worked great.  thanks for the tip

---

### Post by Ergo on 2007-06-27
I don't find that soundconverter preserves the tag information when converting from ogg to mp3 format or am I missing something important.

---

### Post by Piraja on 2008-12-04
Thanks! I tried this, but there seems to be a problem:

```
piraja@ubuntu-desktop:~$ music_convert /home/piraja/Music/elliottsharp05-7-25flac16/*.flac mp3 standard
[: 85: ==: unexpected operator
[: 85: ==: unexpected operator
[: 85: ==: unexpected operator
-e music_convert converts flac ogg and mp3 files, keeping tags

Usage: music_convert from to quality
where 'from' can be flac and ogg
'to' can be ogg and mp3
'quality' is standard, extreme or insane for mp3 output
-e and between -1 and 10 for ogg-vorbis output

ex: music_convert flac ogg 7, music_convert ogg mp3 extreme
piraja@ubuntu-desktop:~$ 

```

Why am I getting this "unexpected operator"?

---

### Post by Deebster on 2009-03-19
I get that error too.  Seems to not be working in the ```
for i in *.$f
``` loop.  I'm not sure how it's meant to work, but it's failing on the first check for me (finding the from type).  I don't know enough Bash to debug this though :)

---

### Post by thomas_tallis on 2010-02-03
flac2ogg.py is simple to use and executes quickly... preserves all the meta data as well.

It's available at [http://channelping.com/audio/](http://channelping.com/audio/)

---

### Post by dorpm on 2010-02-26
In line 1 replace "#! /bin/sh" with "#! /bin/bash".

Greets,
Florian

---

