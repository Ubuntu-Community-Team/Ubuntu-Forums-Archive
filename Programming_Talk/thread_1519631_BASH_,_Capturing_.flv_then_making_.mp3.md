---
title: "BASH ?, Capturing .flv then making .mp3"
date: 2010-06-28
forum: Programming Talk
---

### Post by wannabegeek on 2010-06-28
good day everyone,

I'm working on a personal project, a script to make MP3's of youtube videos.

I have found various articles and technics, the one that makes the most sense to me
is to use cclive and ffmpeg. 

I am stuck with two things.
1) getting output file from ffmpeg to lame for final mp3 and rm .wav and .flv files
2) some youtube pages don't get 'fetched' even though I know that they are good pages.

here's my code, mostly just copied from the cclive man pages.
```

echo "paste url of youtube video"
read URL
cclive -F %t --exec="ffmpeg -i %i -ab 12800 -ar 4100  %i.wav;" -e "$URL"
#lame  
#rm infile.wav  .flv

```I though perhaps the reason why cclive couldn't get certain flash videos, was because
the page was loading slow. I tried the option '--connect-timeout'  and that didn't seem to help.

thank you for your help,  :guitar:

wbg

PS I think I could use curl and scan the descriptions of the videos and then use an mp3 script, to collect all songs on youtube
with key words like "Jazz" or an artist name.

---

### Post by lkjoel on 2010-06-28
Type this in a Terminal (Applications->Accessories->Terminal) window
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ffmpeg
```
Then point your browser to [http://www.ffmpeg.org/documentation.html](http://www.ffmpeg.org/documentation.html)

---

### Post by detrate on 2010-06-28
No need to reinvent the wheel

```
sudo apt-get install youtube-dl
```

```
#!/bin/sh
#
# Youtube mp3 extractor
#
# requirements: sudo apt-get install youtube-dl mplayer
#
# format videos.txt as follows:
#
# [http://www.youtube.com/watch?v=zllH3ZMzSwU](http://www.youtube.com/watch?v=zllH3ZMzSwU) "Armin van Buuren - Unforgivable"
# [http://www.youtube.com/watch?v=5fftTZSEPu0](http://www.youtube.com/watch?v=5fftTZSEPu0) "ATB - Desperate Religon (Expander Mix)"
#

while read line; do
  url="$(echo $line | awk -F '\"' '{ print $1 }')"
  nicename="$(echo $line | awk -F '\"' '{ print $2 }')"
  uglyname="$(echo $url | awk -F '=' '{ print $2 }')"
  youtube-dl -b $url
  mplayer -dumpaudio $uglyname.flv -dumpfile "$nicename.mp3"
done < videos.txt

```

---

### Post by wannabegeek on 2010-06-28
thanks detrate...

your code is more advanced than the direction I am heading ...received some help from a forum
member and want to work with my original script for minute, however your ideas have a lot to offer.

thanks again, will be looking at that code again more carefully...
wbg

---

### Post by lkjoel on 2010-07-03
Try winff.
It is a GUI to ffmpeg.
There are also audio rippers for videos.
If it goes to the wrong format, you can always use soundconverter.

---

### Post by soltanis on 2010-07-03
The ffmpeg invocation would be something along these lines:

```

ffmpeg -i "$FLV" -ar 48000 -ab 128k -ac 2 -acodec libmp3lame "$OUTPUT.mp3"

```

ffmpeg automagically detects sound and video encoded in containers so generally you just need to give it the correct output formatting and off it goes.

---

### Post by lkjoel on 2010-07-05
Based on soltanis's code:
```
#!/bin/bash
echo -n "URL of downloaded FLV (with extention): "
read url
echo -n "Name of mp3 file (with extention): "
read mpthree
ffmpeg -i "$url" -ar 48000 -ab 128k -ac 2 -acodec libmp3lame "$mpthree"
```

---

### Post by wannabegeek on 2010-07-06
here's what I have now with some help from geirha
cclive will name the .flv based on the input file name which is generally the track title in this case.

At the moment I cannot get the loop download and convert each url in the the file I call urlvar .

```

# Script to grab flash videos and extract mp3's from youtube

read -p "Enter search string with + bw words,example:lightnin+hopkins: " keyword

tmpdir=$(mktemp -d)
cd "$tmpdir" || exit
curl -s 'http://www.youtube.com/results?search_query='$keyword'&aq=f' | grep -e '<a href="/watch?v=' | cut -c 20-30  > "$tmpdir"/urlvar

for name in '(cat urlvar)'
  do
   read LINE
   name=$LINE
   cclive -F %t  --exec "ffmpeg -i %i -ab 128000 -ar 44100 %i.wav;" -e "http://www.youtube.com/watch?v=$name"
  for file in ./*.wav; do
    mp3file=${file%.wav}.mp3
    lame "$file" "$mp3file" && mv "$mp3file" ~/grabphase2test/
  done
 done < urlvar
done
cd || exit
trap 'rm -rf "$tmpdir"' EXIT

```

---

### Post by geirha on 2010-07-07
Instead of parsing the html yourself, I'd use a text browser to parse it. E.g.
```
lynx -dump -listonly -nonumbers "http://www.youtube.com/results?search_query=$keyword&aq=f" | awk '/youtube.com\/watch\?v=/ && !seen[$1]++' > urllist
```

Then loop over that with a while loop.
```

while read -r url; do
   cclive -F %t  --exec "ffmpeg -i %i -ab 128000 -ar 44100 %i.wav;" -e "$url"
done < urllist

```
And finally, convert all wave files to mp3 and move them to the destination
```

for file in ./*.wav; do
  mp3file=${file%.wav}.mp3
  lame "$file" "$mp3file" && mv "$mp3file" ~/grabphase2test/
done

```

And lastly, it's pointless to have an exit-trap at the end. Set the trap right after you've created the tmpdir.
```
tmpdir=$(mktemp -d)
trap 'rm -rf "$tmpdir"' EXIT
trap 'exit 2' 1 2 3 15
# rest of code below

```

The first trap above will remove the tempdir if the script exits, and the second trap will make the script exit if you give it certain signals (see trap -l). E.g. if you hit Ctrl+C, that will send signal 2 (SIGINT), which triggers the second trap. The second trap runs «exit 2» which in turn triggers the first trap, the temporary directory is removed and the script exits.

---

### Post by FakeOutdoorsman on 2010-07-07
> **wannabegeek said:**
> ```

   cclive -F %t  --exec "ffmpeg -i %i -ab 128000 -ar 44100 %i.wav;" -e "http://www.youtube.com/watch?v=$name"
  for file in ./*.wav; do
    mp3file=${file%.wav}.mp3
    lame "$file" "$mp3file" && mv "$mp3file" ~/grabphase2test/

```

You don't need to declare *-ab* when outputting to wav.  Why not combine the ffmpeg and lame commands?
```
ffmpeg -i input.foo -f wav - | lame - output.mp3
```

---

### Post by geirha on 2010-07-07
> **FakeOutdoorsman said:**
> Why not combine the ffmpeg and lame commands?
```
ffmpeg -i input.foo -f wav - | lame - output.mp3
```

That's a good idea, but that depends on whether the cclive command treats the | the same way as the shell does. If it parses and runs the command-line itself, then it probably doesn't. If it passes the command to a shell, then that should work.

---

### Post by wannabegeek on 2010-07-08
thanks again for all the input, need a free day to sift though this.

special thanks to geirha for patience and detailed (good) advice....will report back what works
for me and what I 'understand'

thanks again,
wbg

---

### Post by FakeOutdoorsman on 2010-07-08
> **geirha said:**
> That's a good idea, but that depends on whether the cclive command treats the | the same way as the shell does. If it parses and runs the command-line itself, then it probably doesn't. If it passes the command to a shell, then that should work.

If that doesn't work, then another option to avoid creating a temporary wav file is to just use *libmp3lame* via FFmpeg:
```
ffmpeg -i input.foo -acodec libmp3lame -aq 4 output.mp3
```

---

### Post by geirha on 2010-07-08
> **FakeOutdoorsman said:**
> If that doesn't work, then another option to avoid creating a temporary wav file is to just use *libmp3lame* via FFmpeg:
```
ffmpeg -i input.foo -acodec libmp3lame -aq 4 output.mp3
```

Oh! That'll shorten it quite a bit! Something like
```

#!/bin/bash

read -p "Keyword: " keyword

lynx -dump -listonly -nonumbers "http://www.youtube.com/results?search_query=$keyword&aq=f" | 
awk '/youtube.com\/watch\?v=/ && !seen[$1]++' |
while read -r url; do
    cclive -F %t  --exec "ffmpeg -i %i -acodec libmp3lame -aq 4 %i.mp3;" -e "$url"
done

```

---

### Post by detrate on 2010-07-08
> **wannabegeek said:**
> thanks detrate...

your code is more advanced than the direction I am heading ...received some help from a forum
member and want to work with my original script for minute, however your ideas have a lot to offer.

thanks again, will be looking at that code again more carefully...
wbg

As my programming teacher used to say, "it's only hard because it's easy".

There is no need to reinvent the wheel.  The core of my script relies on 2 programs.  youtube-dl and mplayer

youtube-dl accepts a video url and other parameters and will download the flv (man youtube-dl).

mplayer *dumps* the audio from the video.

Everything else is just a for loop with variables being rearranged to give you cleaner output (though my syntax could be improved :-P).

You can technically achieve this is less commands, relying again on a simple text file with a url per line.

videos.txt (example)
```
http://www.youtube.com/watch?v=zllH3ZMzSwU
http://www.youtube.com/watch?v=5fftTZSEPu0
http://www.youtube.com/watch?v=2VmpJBiHMaI

```

```
youtube-dl -b -t -a videos.txt
```
that command will download the best quality available of every video url you have and rename it to a more sensible title.

You could then use mplayer to dump the audio
```
mplayer -dumpaudio myvideo.flv -dumpfile myaudio.mp3
```

but that's computer work, we shouldn't be manually doing that process.

Easiest way to batch edit them would be with a for loop.  The first action of the following code happens in the subshell $() -- a file list gets generated and then the for loop kicks off:

```
for file in $(ls *.flv);
    do mplayer -dumpaudio $file -dumpfile ${file/%flv/mp3}
done
```

This of course, assumes they will all be flvs which is untrue if you're using the -b parameter with youtube-dl.  This ${//} variable is a bash substitution operator (find and replace).  The % signifies that we are looking for a suffix (end of string).  So ${variable/find/replace}. Making ours ${file/%flv/mp3}, this generates an output file with the same name as the video.

Before I explain how to automatically support multiple input types, lets tighten up that for loop.  You can replace linebreaks with semicolons and change "file" to "f".

```
for f in $(ls *.flv); do mplayer -dumpaudio $f -dumpfile ${file/%flv/mp3}; done
```

Using single line for loop are very handy, they become second nature if you spend enough time doing file operations.

Now that we crossed that bridge, lets move forward to support multiple file types.  I chose to use egrep for its short and simple syntax but you can create any command inside the subshell to create a list. The $ inside inside the quotes is a regular expression meaning "end of line".  The | means "or".

```
for f in $(ls | egrep "flv$|mp4$"); do mplayer -dumpaudio $f -dumpfile ${f/%${f##*.}; done
```

This probably looks confusing as heck but bare with me and you'll be able to use this abstractly in the future without having to think twice about how to solve the problem.

I used some shorthand bash with a variable using the substitution I reviewed above, nested inside another substitution.  The inner substitution uses hashs (#) instead of a backlash (/) for readability, but a backslash can be used.  The inner substitution is grabbing the file extension, compensating for a difference in *.flv, *.mp4 or what ever else we allow into our for loop via the egrep.

try the following code to see how the inner substitution works
```
f=myfile.txt; echo ${f##*.}
```

To expand on that, here is a quick test case
```
mkdir test
cd test
touch test1.flv test2.flv test3.mp4 test4.jpg
for f in $(ls | egrep "*.flv|*.mp4"); do echo ${f/%${f##*.}/mp3}; done
```
outputs:
```
test1.mp3
test2.mp3
test3.mp3
```

Sorry, I might have gone a little more in depth then what you were looking for and became a little longer than I expected.

---

### Post by geirha on 2010-07-09
> **detrate said:**
> 
```
for file in $(ls *.flv);
    do mplayer -dumpaudio $file -dumpfile ${file/%flv/mp3}
done
```

Oh, please, don't do that; never use ls in a script. See [bash pitfall 1](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.60ls_.2A.mp3.60).
And quote parameter expansions unless you actually want them to be subjected to word splitting and globbing (which you almost never want). 
```
mplayer -dumpaudio "$file" -dumpfile "${file/%flv/mp3}"
# or using POSIX parameter expansion:
mplayer -dumpaudio "$file" -dumpfile "${file%.flv}.mp3"

```

> **detrate said:**
> 
```
for f in $(ls | egrep "flv$|mp4$"); do mplayer -dumpaudio $f -dumpfile ${f/%${f##*.}; done
```

I recommend using a loop like this instead:
```
for f in *.flv *.mp4; do mplayer -dumpaudio "$f" -dumpfile "${f%.*}"; done
```
See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by detrate on 2010-07-09
> **geirha said:**
> 
I recommend using a loop like this instead:
```
for f in *.flv *.mp4; do mplayer -dumpaudio "$f" -dumpfile "${f%.*}.mp3"; done
```
See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

I wasn't aware I could do a multiple wildcard patter like that.  I don't think I'll ever stop using $(ls) with parameters for some situations, most of my files don't contain spaces :-P -- but when I can I will certainly use this technique you just shared with me as it's shorter and more efficient :)

I did find this loop still runs in no files are found though.

---

### Post by d3v1150m471c on 2010-07-09
```

ffmpeg -i video.flv -sameq sound.mp3

```or you could go the extra mile...
```

cd /input/path
read -p "prompt for url: " link
wget $link
for i in * ; do ffmpeg -i "$i" -sameq ~/path/to/destination/"`basename "$i" | awk -F "." {print $1} `".mp3
done
exit 0

```that'll chop off the .flv extension and land you the same title with a new .mp3 extension.

---

### Post by geirha on 2010-07-09
> **detrate said:**
> I did find this loop still runs in no files are found though.

Yes, that's the standard behavior. If the glob doesn't match a file, the shell will just pass it as is, and not replace it.

```
$ echo *.foo
*.foo
$ echo *.txt
file1.txt file2.txt

```

There are two typical ways to skip those in a for-loop. You check if it exists (-e) or if it exists and is the type of file you want (e.g. -f, -L, -d etc)
```

# Bash
for f in *.flv *.mp4; do
  [[ -f $f ]] || continue   # $f is a regular file, or skip it.
  do_stuff_with "$f"
done

# POSIX sh
for f in *.flv *.mp4; do
  [ -f "$f" ] || continue   # Note that you need quotes around $f with test/[
  do_stuff_with "$f"
done

```
Second, enable the shell option nullglob (bash only). The glob will then expand to nothing if there's no match.
```
$ echo *.txt *.foo
file1.txt file2.txt *.foo
$ shopt -s nullglob
$ echo *.txt *.foo
file1.txt file2.txt
$ 

```

---

### Post by geirha on 2010-07-09
> **d3v1150m471c said:**
> 
```

cd /input/path
read -p "prompt for url: " link
wget $link
for i in * ; do ffmpeg -i "$i" -sameq ~/path/to/destination/"`basename "$i" | awk -F "." {print $1} `".mp3
done
exit 0

```that'll chop off the .flv extension and land you the same title with a new .mp3 extension.

basename and awk to do something that the shell can do better itself? (Your code will chop off too much if the file contains more dots. e.g.  foo.bar.flv becomes foo.mp3 instead of foo.bar.mp3)

See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073) and [http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)

---

