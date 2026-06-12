---
title: "Tweak My Code! - Vol. 1"
date: 2009-09-12
forum: Programming Talk
---

### Post by tgeer43 on 2009-09-12
You guys let me know if you think this is a fun or interesting idea. If so, there will be more to come. If not, well... there won't.

I'm just beginning to learn shell scripting. I'm a big proponent of concise, efficient code, having cut my teeth in assembler on machines with 32K of RAM or less. Tight code was an absolute must back then and this basic tenet has stuck with me through the years. The way I see it this exercise benefits everyone. You get to exercise your grey matter and I get to learn better programming techniques. Here's how it will work:

I will post code snippets that you will modify or completely rewrite to make them more concise and/or efficient. These code blocks are not 'made up' for this exercise. They are actual pieces of scripts that I have written (with help from the forum) for personal use. There are only a few rules to observe:


[LIST=1]
[*] All commands must be fully supported by bash or sh - no other shells allowed.
[*] Each block of code must be able to be entered as a single continuous line in the console. I'll be expanding my examples for readability only. You should do the same.
[*] No calls to other programming languages (perl, awk, ruby, python, etc.) Yeah, I know that sucks but I'm trying to learn basic shell scripting for now, remember? The others will come later.
[*] No commands from packages that are not installed by default in Ubuntu unless they are very commonly installed packages or there is no other way to accomplish the task.
[*]No extraneous output to the console. Eliminate/avoid it altogether or send it to /dev/null.
[*] Test your code before posting. I won't always have time to test all of it and we don't want any errors sneaking through, now do we? :wink:
[/LIST]
 
That's it. I don't want to hamper creativity any more than is necessary but at the same time I want to keep things as universal and 'native' as possible.

So without further ado here are the first two code snippets. Have fun!

_**EXERCISE #1**_
The goal of the first exercise is to rename all MP3s in the current directory so that the first letter of each word in the filename is capitalized and the file extension is not capitalized. In addition, all underscores ("_") need to be converted to spaces (" "). For example: "As_long_as_I_can_see_the_light.MP3" becomes: "As Long As I Can See The Light.mp3".
Here is my code:
```
#!/bin/bash
rename 'tr/_/ /' *.mp3
rename 's/MP3/mp3/' *.MP3
for a in *.mp3
do
  c=""
  for i in $a
  do
    b=`echo "${i:0:1}" | tr a-z A-Z `${i:1}
    c=$c" "$b
    if echo $c | grep mp3 > /dev/null
    then
      c=${c:1}
      mv "$a" "$c"
    fi
  done
done
```Although this code executes without error and gives the desired result, there is a minor flaw in it. Bonus points to the first person that finds it. Hint: there is one case where the output will not meet the requirements.

_**EXERCISE #2**_
The goal of the second exercise is to convert all WMAs in the current directory to MP3 (128kbps CBR stereo) and replace all underscores ("_") in the filename to spaces (" "). I used Mplayer and Lame for the conversions because that's all I know but as long as you adhere to the above rules, you are free to do it any way you wish. Don't forget to delete the WMAs and any temporary files created:
```
#!/bin/bash
rename 'tr/_/ /' *.mp3
rename 's/WMA/wma/' *.WMA
for i in *.wma
do
  mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$i"
  lame -m j -b 128 -h --cbr audiodump.wav -o "$i""_";
  rm audiodump.wav
done
rename 's/wma_/mp3/' *.wma_
rm *.wma
```That's a lot of audio processing for such a small bit of code. See if you can do better.

Once I mark the thread [SOLVED], no further submissions will be considered. I will do my best to declare a "winner" for each code block. The winner will receive 10 points plus possible bonus points for ingenuity and originality. Non-winners may also receive these bonus points but don't lose sight of the original goals - conciseness and efficiency. I will keep a running total of all points holders and post them at the end of the thread so we can see who is most likely to be crowned "Script King/Queen" of the Ubuntu forums!

Good luck and let the games begin!

tgeer

---

