---
title: "Help with wget script"
date: 2008-11-22
forum: Programming Talk
---

### Post by WitchCraft on 2008-11-22
Hi, I need a little help with a bash script.
It downloads videos from youtube.

invoke with:
chmod +x getvideo.sh
./getvideo.sh [http://www.youtube.com/watch?v=dxkeJALHrVM](http://www.youtube.com/watch?v=dxkeJALHrVM)
```

#!/bin/bash
#
# getvideo.sh
# Released under the GPL 3.O
#
# Download youtube videos with bash and wget ;-)
#
# run: chmod +x getvideo.sh
# run:  ./getvideo.sh YOUTUBE_URL 
# e.g.  ./getvideo.sh http://www.youtube.com/watch?v=00KYPsQSG10
#
# Last modified: Jul 09, 2008


#youtubeURL="http://www.youtube.com/watch?v=43sUEFcD4Ro" # only has flv
#youtubeURL="http://www.youtube.com/watch?v=00KYPsQSG10" # has mp4 & flv
youtubeURL=$1; # get command line argument 1
youtubeURL=$(echo "$youtubeURL") # argh, damn bash! Remove invisible double quote

reset

echo "Downloading video: $youtubeURL"
echo ""
youtubeHTML=$(wget -O - "$youtubeURL" 2> /dev/null)
#youtubeHTML=$(cat "$(echo ~)/Desktop/teletubbie.htm") # cat it from an existing file

#echo "HTML Page:"
#echo "$youtubeHTML"
#echo "$youtubeHTML" >> youtube.htm # For review, if the keyword changes


#flvURL=$(echo "$youtubeHTML" | grep -o -E 'player2\.swf?[^\"]+' | head -n 1 | sed 's/^player2\.swf?//g')
flvURL=$(echo "$youtubeHTML" | grep 'fullscreenUrl' | sed -re 's/^.+video_id=//;s/&hl=.+//') # sed -re enables regex search syntax extensions
echo "Encrypted URL = $flvURL"
echo ""

VideoTitle=$(echo "$youtubeHTML" | grep "<title>" | sed 's/<title>//;s/<\/title>//;s/YouTube - //;s/^\s*//g')
FLVfile=$(echo "$youtubeHTML" | grep "<title>" | sed 's/<title>//;s/<\/title>/.flv/;s/YouTube - //;s/^\s*//g')
MP4file=$(echo "$youtubeHTML" | grep "<title>" | sed 's/<title>//;s/<\/title>/.mp4/;s/YouTube - //;s/^\s*//g')
#sed 's/^\s*//g' # finally, trim trailing whitespaces
echo "Video title: $VideoTitle"
echo ""

echo "Starting wget: "
FLVdownloadURL="http://www.youtube.com/get_video.php?hl=en&video_id=$flvURL"
MP4downloadURL="http://www.youtube.com/get_video.php?hl=en&video_id=$flvURL&fmt=18"
# append &fmt=6   <--> FLV
# append &fmt=18  <--> MP4
echo "FLV download URL: $FLVdownloadURL"
echo "MP4 download URL: $MP4downloadURL"
echo ""

wget -O "$FLVfile" "$FLVdownloadURL"
wget -O "$MP4file" "$MP4downloadURL"
reset
echo ""

echo "Voilà, download of \"$VideoTitle\" completed."

```

the above script works excellently.

Now I wanted to get wget to download via a proxy server, because some youtube videos are censored by ip from country to country...

I only added a:
export http_proxy="201.216.211.81:80"
export ftp_proxy="201.216.211.81:80"
and the "--proxy=on" directive to every wget command.

Why is it not working?

This is the list of proxy servers i used:
[http://www.samair.ru/proxy/](http://www.samair.ru/proxy/)
[http://www.proxy4free.com/page1.html](http://www.proxy4free.com/page1.html)

```

#!/bin/bash
#
# getvideo.sh
# Released under the GPL 3.O
#
# Download youtube videos with bash and wget ;-)
#
# run: chmod +x getvideo.sh
# run:  ./getvideo.sh YOUTUBE_URL 
# e.g.  ./getvideo.sh http://www.youtube.com/watch?v=00KYPsQSG10
#
# Last modified: Jul 09, 2008


#youtubeURL="http://www.youtube.com/watch?v=43sUEFcD4Ro" # only has flv
#youtubeURL="http://www.youtube.com/watch?v=00KYPsQSG10" # has mp4 & flv
youtubeURL=$1; # get command line argument 1
youtubeURL=$(echo "$youtubeURL") # argh, damn bash! Remove invisible double quote

reset
#export http_proxy="http://proxy.example.com:8080"
export http_proxy="201.216.211.81:80"
export ftp_proxy="201.216.211.81:80"
#export ftp_proxy="http://proxy.example.com:8080"

echo "Downloading video: $youtubeURL"
echo ""
youtubeHTML=$(wget -O - --proxy=on "$youtubeURL" 2> /dev/null)
#youtubeHTML=$(cat "$(echo ~)/Desktop/teletubbie.htm") # cat it from an existing file

#echo "HTML Page:"
#echo "$youtubeHTML"
#echo "$youtubeHTML" >> youtube.htm # For review, if the keyword changes


#flvURL=$(echo "$youtubeHTML" | grep -o -E 'player2\.swf?[^\"]+' | head -n 1 | sed 's/^player2\.swf?//g')
flvURL=$(echo "$youtubeHTML" | grep 'fullscreenUrl' | sed -re 's/^.+video_id=//;s/&hl=.+//') # sed -re enables regex search syntax extensions
echo "Encrypted URL = $flvURL"
echo ""

VideoTitle=$(echo "$youtubeHTML" | grep "<title>" | sed 's/<title>//;s/<\/title>//;s/YouTube - //;s/^\s*//g')
FLVfile=$(echo "$youtubeHTML" | grep "<title>" | sed 's/<title>//;s/<\/title>/.flv/;s/YouTube - //;s/^\s*//g')
MP4file=$(echo "$youtubeHTML" | grep "<title>" | sed 's/<title>//;s/<\/title>/.mp4/;s/YouTube - //;s/^\s*//g')
#sed 's/^\s*//g' # finally, trim trailing whitespaces
echo "Video title: $VideoTitle"
echo ""

echo "Starting wget: "
FLVdownloadURL="http://www.youtube.com/get_video.php?hl=en&video_id=$flvURL"
MP4downloadURL="http://www.youtube.com/get_video.php?hl=en&video_id=$flvURL&fmt=18"
# append &fmt=6   <--> FLV
# append &fmt=18  <--> MP4
echo "FLV download URL: $FLVdownloadURL"
echo "MP4 download URL: $MP4downloadURL"
echo ""

wget --proxy=on -O "$FLVfile" "$FLVdownloadURL"
wget --proxy=on -O "$MP4file" "$MP4downloadURL"
reset
echo ""

echo "Voilà, download of \"$VideoTitle\" completed."

```

---

### Post by drubin on 2008-11-22
Not sure if this is relevant but have you tried ```
youtube-dl
``` application?

---

### Post by WitchCraft on 2008-12-09
bump.
just wanna proxy and bash, not python.

---

### Post by drubin on 2008-12-09
> **WitchCraft said:**
> bump.
just wanna proxy and bash, not python.

What does this mean?

Do you only want to use bash, and not python?

---

### Post by WitchCraft on 2008-12-09
> **drubin said:**
> What does this mean?

Do you only want to use bash, and not python?

exactly. that's what my script does, just that wget does't work / i got the parameters for the proxy wrong / chose wrong proxy.

---

