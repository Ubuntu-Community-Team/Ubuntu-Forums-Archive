---
title: "sed cannot delete forward slash in while loop?"
date: 2014-08-14
forum: Programming Talk
---

### Post by shamsat on 2014-08-14
I am downloading online videos with a bash script this is the code of script test.sh:
```

#!/bin/bash

while read line
 do

"/usr/bin/wget" $line
sed -i "/$line/d" urls

done  <urls

``` 
The while loop read the videos url from the urls file and parse them to the wget for dwonlaod, i write the wget  for easy of exmple in this code otherwise i use another script to downlaod the embed videos , the code ```
sed -i "/$line/d" urls 
``` delete the url of videos from the urls file when it is download is complete.
The problem is http address contain the foreward slashes "/" and sed cannot delete them and get error, this is the urls file:
```

http://download.wavetlan.com/SVV/Media/HTTP/MP4/ConvertedFiles/Media-Convert/Unsupported/test7.mp4
http://download.wavetlan.com/SVV/Media/HTTP/H264/Talkinghead_Media/H264_test3_Talkingheadclipped_mp4_480x360.mp4
http://download.wavetlan.com/SVV/Media/HTTP/H264/Talkinghead_Media/H264_test4_Talkingheadclipped_mp4_480x320.mp4
http://download.wavetlan.com/SVV/Media/HTTP/H264/Other_Media/H264_test8_voiceclip_mp4_480x320.mp4

```
This is  output of test.sh script:
```

# ./test.sh
http://download.wavetlan.com/SVV/Media/HTTP/MP4/ConvertedFiles/Media-Convert/Unsupported/test7.mp4
sed: -e expression #1, char 8: unknown command: `/'
http://download.wavetlan.com/SVV/Media/HTTP/H264/Talkinghead_Media/H264_test3_Talkingheadclipped_mp4_480x360.mp4
sed: -e expression #1, char 8: unknown command: `/'
http://download.wavetlan.com/SVV/Media/HTTP/H264/Talkinghead_Media/H264_test4_Talkingheadclipped_mp4_480x320.mp4
sed: -e expression #1, char 8: unknown command: `/'
http://download.wavetlan.com/SVV/Media/HTTP/H264/Other_Media/H264_test8_voiceclip_mp4_480x320.mp4
sed: -e expression #1, char 8: unknown command: `/'

```

---

### Post by ofnuts on 2014-08-14
The forward slash is by default taken as a delimiter in sed instructions. But you can use any other character as a delimiter, you just need to use one that is not allowed  in a URL (anything outside of "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789-._~:/?#[]@!$&'()*+,;=", like the pipe, for instance).

---

### Post by shamsat on 2014-08-14
sorry i didn't know how to do that, please can you please post the corrent code.

---

### Post by steeldriver on 2014-08-14
For the special case of the sed 's' (substitute) command, you can just replace the / delimiters by another character of your choice e.g.

```

s/pattern/replacement/flags

```
becomes
```

s#pattern#replacement#flags

```

For other commands (such as the d command that you are trying to use) the first instance needs to be backslash-escaped i.e. choosing '#' as the delimiter
```

\#pattern#d

```

so in your case that would be something like

```

sed -i "\#$line#d" urls

```

**However **I'm really not sure it's a good idea to be deleting lines from the file at the same time as you are reading it - you may get unexpected results depending on how the file streams get buffered. Why do you need to do that anyway?

---

### Post by shamsat on 2014-08-14
Thanks so much it is working now.=d>

---

