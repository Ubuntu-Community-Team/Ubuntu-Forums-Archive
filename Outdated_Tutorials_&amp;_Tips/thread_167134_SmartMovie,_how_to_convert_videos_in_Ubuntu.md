---
title: "SmartMovie, how to convert videos in Ubuntu"
date: 2006-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ResetReboot on 2006-04-27
Hello everyone!

I've just made this howto for those using a Symbian smartphone (like N-Gage, Nokia 6600...) and use that nifty program called SmartMovie.

The original program has two parts: The player (in the mobile device) and the converter (in your Windoze PC). The part we substitute is the Windoze PC one.

[SIZE="5"]Getting Ready[/SIZE]

First of all we must install the **Xvid Codec** and **Mencoder**:

```
# sudo apt-get install libxvidcore4 mencoder-586
```

[SIZE="5"]Converting the video[/SIZE]

Now we must convert the original video to the avi format that SmartMovie will understand:

```
# mencoder original_video.avi -srate 16000 -vop scale=208:176 -o mobile_video.avi -oac mp3lame -lameopts vbr=0:br=32:mode=3 -ovc xvid -xvidencopts bitrate=112 -ofps 12 -sws 2
```

This will convert the video to XviD with MP3 audio @ 12 fps, 112 kbps for the video and 32 kbps for the audio. Everything adjusted to the size of the screen of a Symbian device.

If you don't want to write down that every time you want to get a movie into your phone, you can fire up your favourite $EDITOR and paste this:

```
#!/bin/bash

mencoder $1 -srate 16000 -vop scale=208:176 -o $2 -oac mp3lame -lameopts vbr=0:br=32:mode=3 -ovc xvid -xvidencopts bitrate=112 -ofps 12 -sws 2
```

Save it as converter.sh, make it executable (chmod +x converter.sh) and then do:

```
# converter movie.avi movie_mobile.avi
```

And just beam it over irDa, Bluetooth or copy to the phone's memory card.

Enjoy!!

---

### Post by mundano on 2006-05-06
I will try that tomorow... One more thing I can do on Linux :D

---

### Post by maduranga on 2006-05-11
i did as u told.. the last command didn't gave any result for me. Even no errors or messages.. should i convert the movie into avi before i convert it to my Nokia 6600 phone?

maduranga....

---

### Post by NiceGuy on 2006-06-30
I just wanted to say a great big THANKYOU =D> =D> =D> =D> 

BTW I've got a Nokia 6680 and the videos are a bit squished, is there anything I can do about that? Oh and is there any way to do a sort of 'onestep rip and encode' for dvd's? My guess is not (nothing is ever that easy!) but I thought I'd ask!

pps. Is there a way of converting mpeg files in a simmilar way?

---

### Post by xalen on 2007-01-31
Just wanted to say thank you!!! There is now a DIVX player available for symbian that's free! So you can now convert and watch your movies completely for free... legally! (At least I think divx is free) No Windoze needed!

One thing though, the audio always lags behind by half a second to a second. Anyone know how to sort this out? DivX doesn't have an audio pre-roll setting!!

---

### Post by xalen on 2007-02-01
Ok I answered my own question.  You just have to use the -delay option and set the delay in seconds.

I also made my own slightly modified version of bash code to automatically make an output filename so you just do: converter video.ext and it outputs it as videoenc.avi

```

#!/bin/bash

mencoder $1 -srate 16000 -vop scale=352:240 -o ${1:0:${#1}-4}enc.avi -oac mp3lame -lameopts vbr=0:br=32:mode=3 -ovc xvid -xvidencopts bitrate=112 -ofps 24 -sws 2 -delay 0.60

```

Also if you add this script to your /bin folder but omit the .sh extension then the command will be available wherever you are.

---

### Post by TrendyDark on 2007-02-01
Great guide! I found out the power of the Mencoder command line tool the other day when making a screencast with Istanbul, very useful software!

---

### Post by rkakkar on 2007-02-05
my sony ericsson phone supports only AMR as the audio codec and 3GP as the video codec. can someone please guide me where i could get these codecs from and what changes do i need to make to the mencoder command to convert the video into 3gp using amr (instead of mp3) as audio?

---

### Post by lotvx on 2010-04-10
> **ResetReboot said:**
> Hello everyone!

I've just made this howto for those using a Symbian smartphone (like N-Gage, Nokia 6600...) and use that nifty program called SmartMovie.

The original program has two parts: The player (in the mobile device) and the converter (in your Windoze PC). The part we substitute is the Windoze PC one.

[SIZE="5"]Getting Ready[/SIZE]

First of all we must install the **Xvid Codec** and **Mencoder**:

```
# sudo apt-get install libxvidcore4 mencoder-586
```

[SIZE="5"]Converting the video[/SIZE]

Now we must convert the original video to the avi format that SmartMovie will understand:

```
# mencoder original_video.avi -srate 16000 -vop scale=208:176 -o mobile_video.avi -oac mp3lame -lameopts vbr=0:br=32:mode=3 -ovc xvid -xvidencopts bitrate=112 -ofps 12 -sws 2
```

This will convert the video to XviD with MP3 audio @ 12 fps, 112 kbps for the video and 32 kbps for the audio. Everything adjusted to the size of the screen of a Symbian device.

If you don't want to write down that every time you want to get a movie into your phone, you can fire up your favourite $EDITOR and paste this:

```
#!/bin/bash

mencoder $1 -srate 16000 -vop scale=208:176 -o $2 -oac mp3lame -lameopts vbr=0:br=32:mode=3 -ovc xvid -xvidencopts bitrate=112 -ofps 12 -sws 2
```

Save it as converter.sh, make it executable (chmod +x converter.sh) and then do:

```
# converter movie.avi movie_mobile.avi
```

And just beam it over irDa, Bluetooth or copy to the phone's memory card.

Enjoy!!

thanks, but now comes the question : how to embed the subtitles?

---

### Post by fast_rizwaan on 2010-04-25
somewhat improved, handles spaces in filenames. this script is for n97, 5800 xm phones s60v5 smartmovie 4.15:
```

#!/bin/bash

mencoder "$1" -srate 48000 -vf scale=320:180 -o "${1:0:${#1}-4}enc.avi" -oac mp3lame -lameopts vbr=0:br=128:mode=3 -ovc xvid -xvidencopts bitrate=224 -ofps 24 -sws 2


```

if we really need small file for nokia n97/5800/5233:

encode with:
```

#!/bin/bash

mencoder "$1" -srate 16000 -vf scale=320:180 -o "${1:0:${#1}-4}enc.avi" -oac mp3lame -lameopts vbr=0:br=32:mode=3 -ovc xvid -xvidencopts bitrate=224 -ofps 24 -sws 2

```

---

