---
title: "Convert FLAC to MP3 easily"
date: 2008-08-17
forum: Outdated Tutorials &amp; Tips
---

### Post by mellowd on 2008-08-17
Hi all

I haven't been on the forum as well, but I thought I'd post this quick as it can save quite a bit of time.

Let's say you've created or downloaded some FLAC audio files. Now your MP3 player doesn't support FLAC so you need to convert them all to MP3.

I've created a script that will do this quickly and easily. Once the script is installed you'll only need to excecute one command to do it all.

First, you'll need lame 3.98 and flac install. You can get FLAC from the repositories:

```
sudo aptitude install flac
```

lame 3.97 is only on the repository so you'll need to compile 3.98 yourself (I can adjust the script later if a lot of people are still using 3.97)

cd to bin:

```
cd /bin
```

Create a new file called encode (Use whatever text editor you like, I use vim):

```
vim encode
```

Paste the following in the file:

```
# Encode
# v0.1 17.08.08 - First created
# Darren O'Connor <mellow.drifter@gmail.com>

# This script, when run in a folder full of FLAC files, will create high quality VBR mp3's for use in mp3 players.
# This version uses lame 3.98. If you use version 3.97 and below you'll need to change a few options

#!/bin/bash
mkdir wav/
flac -d *.flac
mv *.wav wav/
cd wav/
for f in *.wav; do mv "$f" "${f%.wav}";done
mkdir ../mp3/
find -maxdepth 1 -type f -name '*' -exec lame -V0 -q0 '{}' -o '../mp3/{}' \;
cd ../mp3/
for FILE in *; do mv "$FILE" "$FILE.mp3"; done
cd ../
rm -r wav/
```

Save the file. You'll now need to make it excecutable: 

```
sudo chmod +x encode
```

Now cd to any directory with your FLAC files in and simply type encode. Once it's complete you'll be left with a new mp3 folder with all your new mp3's.


If you have a look at the script you'll see it uses the -V0 option so the resulting files will be very high quality VBR mp3's. Also it doesn't have the --vbr-new switch which lame 3.97 will need. I might add an option for lame 3.97 in later, I might also change the script so it asks which quality you would like before encoding them for you. 

Let me know if you have any questions.

---

### Post by Ushi on 2008-12-29
Thanks for a very useful script, just one small thing.

The #!/bin/bash line needs to be at the top, before any comments, or else this won't work.

---

### Post by NTolerance on 2008-12-29
Is *--vbr-new* all that's necessary to get this to work with lame 3.97?  

I'd like to see an option to delete the source files after encoding.  Thanks for your script!

---

### Post by NTolerance on 2009-02-02
Just tested this script out with lame 3.97 and it works great with the slight syntax modification here:

```
# Encode
# v0.1 17.08.08 - First created
# Darren O'Connor <mellow.drifter@gmail.com>

# This script, when run in a folder full of FLAC files, will create high quality VBR mp3's for use in mp3 players.
# This version uses lame 3.98. If you use version 3.97 and below you'll need to change a few options

#!/bin/bash
mkdir wav/
flac -d *.flac
mv *.wav wav/
cd wav/
for f in *.wav; do mv "$f" "${f%.wav}";done
mkdir ../mp3/
find -maxdepth 1 -type f -name '*' -exec lame --vbr-new -V0 -q0 '{}' -o '../mp3/{}' \;
cd ../mp3/
for FILE in *; do mv "$FILE" "$FILE.mp3"; done
cd ../
rm -r wav/
```

I like that the mp3s are dumped in a subdirectory, keeps thing tidy.  Thanks for this script!

---

### Post by jalirious on 2009-02-03
Nice work lad.

---

### Post by AnAmusedFrog on 2009-02-04
That's extremely useful.  Thanks a lot.

---

### Post by mattlach on 2009-07-30
Thank you.

Great script.

Works like a charm.


Only one question, why -v0 -q0 for lame settings.

AS I understand most people in double blind settings can not distinguish between -v0 and -v2 even in a hifi quiet listening setting

And as far as -q0 goes, the output is bit for bit identical to -q2, but -q2 is faster to encode...

I'd appreciate your thoughts on this, and the rationale you used for your settings :)

---

### Post by bionnaki on 2009-07-31
this is the script I use. it transfers id3 tags and does V0 (not sure if yours does or not -- if it doesnt, incorporate the tag stuff into your script). 

> 
for a in *.flac

do
OUTF=`echo "$a" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$OUTF"
id3 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"

done


---

### Post by bacchusmarsh on 2009-09-17
if this does not work for you then try here:
[http://ubuntuforums.org/showthread.php?t=790587&highlight=convert+flac+to+mp3]("http://ubuntuforums.org/showthread.php?t=790587&highlight=convert+flac+to+mp3")

---

### Post by redcharlie on 2009-12-19
Thanx bionnaki!  Tags are the rub.  I rip my CD's as flacs with soundjuicer, which does a decent job with the flac tags.  oggenc will then convert the flacs to oggs along with the tags.  But for mp3 neither lame nor sound converter converts the tags for me.  So, I would have to go behind to edit them manually, (or re-rip the CD as mp3).  

I was just about to break down and try to work out a script, but you saved me the legwork!

The only thing I changed was id3 to id3v2 and then I wrapped lame in an if to avoid re-ripping the flacs if you just want to set the tags.

> **bionnaki said:**
> 
**if [ ! -e "$OUTF" ]; then**
    flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$OUTF"
**fi**
id3**v2** -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"

:)

---

### Post by haruki on 2010-11-07
Thank you mellowd, bionnaki and redcharlie. 

I have a question: how would I modify bionnaki's script so that it created and moved the mp3s into a folder of their own? mellowd's script does this but the two scripts are different enough to this newbie's eyes that I'm unsure how to implement it.

---

### Post by dom_lochet on 2010-11-09
Here's a script I just wrote, based on bionnaki's (thanks, btw). It takes two parameters: the directory where your *.flac files are, and the directory where you want your mp3 to be copied. The script creates a subdirectory in the destination directory, with the same name as the source directory and put the mp3 files there. Hope it helps...

```

#!/bin/bash

E_WRONG_ARGS=85
NBRPARAMS=2
if [ $# ne "$NBRPARAMS" ]
then
  echo "Usage: `basename "$0"` source-dir dest-dir"
  exit $E_WRONG_ARGS
fi

OLD_CURRENT_DIR="$PWD"

SRC_BASENAME="`basename "$1"`"
cd "$2"
DEST_FULLNAME="$PWD"
mkdir "$SRC_BASENAME"
echo "Directory $DEST_FULLNAME/$SRC_BASENAME created."
cd "$OLD_CURRENT_DIR"
cd "$1"

for a in *.flac
do
  OUTF=`echo "$a" | sed s/\.flac$/.mp3/g`

  ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
  TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
  ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
  GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
  TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
  DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`
  
  echo "Encoding $OUTF..."

  flac -c -d "$a" | lame -q5 -V4 - "$DEST_FULLNAME/$SRC_BASENAME/$OUTF"
  id3v2 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$DEST_FULLNAME/$SRC_BASENAME/$OUTF"
done 

cd "$OLD_CURRENT_DIR"
exit

```

---

### Post by zang3tsu on 2010-11-24
Thanks for the script. Missing dash btw.

```
if [ $# [SIZE="4"]**-**[/SIZE]ne "$NBRPARAMS" ]
```

---

### Post by haruki on 2011-01-14
thank you dom_lochet, and zang3tsu. 

how would i change the script to put the mp3s in a folder named the same as the source but ending in 'V0'?

i realize it does make sense to have the folders sorted '/flac/' '/mp3/' but currently i don't have that setup.

---

### Post by m1 grant on 2011-02-24
Just wanted to say excellent script,and thank you. Minus one modification (move the #!bin/bash line to the top) it works great and its definately my preferred way of converting my flacs made from cd ripping to mp3's.

---

### Post by linuxbasiccommand on 2011-02-24
> **NTolerance said:**
> Just tested this script out with lame 3.97 and it works great with the slight syntax modification here:

```
# Encode
# v0.1 17.08.08 - First created
# Darren O'Connor <mellow.drifter@gmail.com>

# This script, when run in a folder full of FLAC files, will create high quality VBR mp3's for use in mp3 players.
# This version uses lame 3.98. If you use version 3.97 and below you'll need to change a few options

#!/bin/bash
mkdir wav/
flac -d *.flac
mv *.wav wav/
cd wav/
for f in *.wav; do mv "$f" "${f%.wav}";done
mkdir ../mp3/
find -maxdepth 1 -type f -name '*' -exec lame --vbr-new -V0 -q0 '{}' -o '../mp3/{}' \;
cd ../mp3/
for FILE in *; do mv "$FILE" "$FILE.mp3"; done
cd ../
rm -r wav/
```I like that the mp3s are dumped in a subdirectory, keeps thing tidy.  Thanks for this script!
Thanks! I'm looking...

---

