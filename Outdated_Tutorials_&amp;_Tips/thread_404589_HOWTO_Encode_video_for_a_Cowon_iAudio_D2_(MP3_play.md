---
title: "HOWTO: Encode video for a Cowon iAudio D2 (MP3 player)"
date: 2007-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by dcs3jah on 2007-04-08
I recently bought a Cowon iAudio D2. It's excellent player.  It fits the bill very well for Ubuntu users as it's fully linux-compatible and has OGG support.

Anyway, the only issue is that the software that comes with the player (JetAudio) for converting videos to a format that's playable on the D2 is Windows-only.

Having spent a long time time experimenting with various settings, I've written a short script that should allow most users to simple right click on a file to transcode it into the right format.

Before you start, you'll need transcode,ffmpeg and mencoder installed. If you don't already have them, the easiest way to install them is to use [Automatix]("http://www.getautomatix.com/").

To use the script,[ download it from here]("http://www.mozmarks.com/james/---files/d2-convert").  Now drag the file into your ~/.gnome2/nautilus-scripts directory (you might need to show hidden files with Ctrl-H).  Then right click on the file, go to Properties. In "Permissions" tab, make sure "Allow Executing File as Program" is ticked.

You should now be able to right-click a file, go to Scripts and select "d2-convert" (this may take a minute or so to appear - it's not immediate after installation).  This will convert the file for you and save it as D2-<oldfilename>.avi

You can also select multiple files, and they will be queued.  It's worth noting that I upgraded my firmware to 2.41 recently - so if you find it doesn't work for you, I'd try that.

This script is a bit rough, so feel free to suggest improvements!  I'm hoping to create a DEB installer to simplify the process - if I find the time!

Enjoy.

James.

---

### Post by bruenig on 2007-04-08
Those of you who don't want to add automatix and all the baggage that comes with that for such a simple task of adding three packages
```
sudo sed -e 's/# deb/deb/g' -e 's/universe$/universe multiverse/g' -i.backup /etc/apt/sources.list
sudo apt-get update
sudo apt-get install transcode mencoder ffmpeg
```

And a simplification of getting the script into the right directory with the right permissions.
```
wget http://www.mozmarks.com/james/---files/d2-convert -P ~/.gnome2/nautilus-scripts
chmod +x ~/.gnome2/nautilus-scripts/d2-convert
```

---

### Post by edemark on 2007-04-08
Hi
I was happy to find this howto as I have a stormblue av-700 mp3 player that has the same disadvantage as your, the program for transforming videos is   w in   only. The retail box of the player states that is linux compatible and it actually plays ogg and works well with linux except videoo. So I was just thinkiing how to make yur script working for my player also. For this reason i would like to ask what is the output format oyur script produces and if you have any idea how to make with your script .mpx format.
thanks for your time

---

### Post by dcs3jah on 2007-04-09
The "d2-convert" script save video as a DivX AVI file, rescaled to fit into a 320x240 box but keep aspect ratio.  Audio is MP3.

Sorry, I've never heard of the MPX format for video.  I've had a quick look around on google and it seems other people are having the [same problem trying to find a linux converter]("http://www.moviecodec.com/topics/16678p1.html").  I suspect MPX is quite an obscure format.

You could check to see if mencoder supports MPX - but having had a quick look at the list supported format in "libavcodec" it [doesn't seem likely]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html").

Sorry I can't be more helpful. Good luck though!

---

### Post by edemark on 2007-04-09
thank you anyway i will keep trying

---

### Post by tlwolf on 2007-05-06
Having just got my d2 I was expecting to have to figure out how to convert video and make a script. Thanks so much.  My only problem is I use kde. I figured out how to add it to konquerors right click menu. How ever the script acts differently. Instead of opening just one file at a time it trys to do them all at once. When that happens with more then around five files some files get dropped. You can still run run it in konsole but the file path can't have any spaces in it or else it says it can't find the file.
 
I was wondering if anyone had a quick fix. If not I'll get in the script and figure out what needs to be changed to make it work in kde.


Spencer

---

### Post by Ender Black on 2007-05-27
It works just flawlessly!  Thanks a million.. I was about to climb a wall I was getting so frustrated.   Woot!

---

### Post by yotama9 on 2007-06-19
I have a little bit of a problem there.

When I right click the file and choose the script nothing happen. If I run the script from terminal I get the timet, I'm running it now on a big file so later I'll be able to tell you if it worked.

I'm using Ubuntu Feisty and I'm tying yo convert an AVI file.

---

### Post by Daveth on 2007-07-06
this works a bit for me- I'm using the 2.5 beta firmware on my brand new D2. Script runs ok and coverts avi to playable avi, but is not too successful with other common file formats. Anybody say what file formats they have had success with?
An excellent player other wise.

---

### Post by akalias on 2007-07-12
I can confirm that the following works for VOB files on my D2

transcode --export_par 1,1 -H 10 -a 0 -q 1 -i IN.VOB -w 800,50 -F mpeg4 -b 128,0,2 -s 1.311 --a52_drc_off -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -Z 320x240 -y ffmpeg -o OUT.AVI

Did not need mplayer for conversion. Worked on Xvid files as well.

---

### Post by sickenmcsluggets on 2007-07-27
Anybody know what I could use to get video on my Cowon iAudio7? The D2 nautilus script won't work for it.

---

### Post by argotnaut on 2007-08-23
[bump] I have an iAudio 7 and would like to know, too -- although I haven't actually tried the D2 script yet, so I don't know what's wrong with it...

---

### Post by Paul133 on 2007-08-24
The following was taken from [http://www.cowonamerica.com/products/cowon/d2/tech_specs.html](http://www.cowonamerica.com/products/cowon/d2/tech_specs.html)
and
[http://www.cowonamerica.com/products/iaudio/7/](http://www.cowonamerica.com/products/iaudio/7/)
respectively:

Here's the video the Cowon D2 takes:

AVI : MPEG4 ~ 2Mbps, 320x240, 30fps, MP3 audio
WMV : WMV9 ~ 768kbps, 320x240, 30fps, WMA audio

Here's the video the Cowon iAudio7 takes:

AVI: XviD, MPEG4, 256 ~ 384 kbps CBR, up to 160x128, 15 fps * 

 *Need to transcode using jetAudio

Hopefully, someone can edit the script, giving it these new parameters for all you iAudio7 users. Personally, I'm still deciding between the Cowon D2 and the iRiver Clix 2.

---

### Post by doorn12 on 2007-08-31
Just install Iriverter, wich is in the ubuntu package.
copy one of the preset files to D2 and edit it with the D@ variables.
Works better than the program in windows that came with the device.

---

### Post by Paul133 on 2007-09-07
Your script worked great on my 2 hour movie. It took a 320x240 Xvid DVD rip/encoding with a huge A/V sync problem (video was twice as fast as audio) and made it into a 320x240 DivX that had perfect (or nearly perfect) A/V sync. The output file was 100 MB bigger than the input, but that's a small price to pay for A/V sync.

---

### Post by rdwtux on 2007-09-08
Thanks for the iRiverter tip.. I downloaded it.  

here's a profile for the D2.  Just add it to your /usr/share/iriverter/profiles/ directory

BTW - I didn't create the file.  I grabbed it from the iAudiophile forums.  Seems to work well.

---

### Post by earlycj5 on 2007-09-21
Thanks for the thread.

I was beating my head against the proverbial wall myself.

Paul133's post had the info I needed.  Being that I'm using OpenSuSE right now I downloaded and installed KVideoEncoder and used that to convert my files using the paremeters above.

---

### Post by andrew.46 on 2007-10-31
Hi,

 You all seem much more at home with encoding for such devices than me! Could I get a suitably skilled person to look over some work I have done on an iRiver X20 player:

[http://people.aapt.net.au/~adjlstrong/iRiverX20.html](http://people.aapt.net.au/~adjlstrong/iRiverX20.html)

 I have been wrestling with this for some time and have achieved reasonable results but I would love a little input from outside!

             Andrew

---

### Post by nathank on 2007-12-21
Another simple command line converter which only needs ffmpeg


FFMPEG -i INPUT.VOB -s 320x240 -vcodec mpeg4 -vtag XVID -b 500kb -mbd rd -flags +4mv+trell+aic -cmp 2 -subcmp 2 -g 300 -r 29.97 -acodec mp3 -ab 128 -ac 2 -async 1 OUTPUT.avi

---

### Post by feisty_hot_lover on 2007-12-28
Thank you very much for this script dcs3jah-James.  I hope you are continuing work on this script.  I find it very useful for converting my downloaded TV shows.  Again thanks very much.

---

### Post by dcs3jah on 2007-12-30
Glad someone else found it useful. I've not taken a look at the script for a long time, so I've not updated it I'm afraid (I don't watch much video on my D2 anymore).

But, in case it's useful, I found a video tutorial - I reckon this is a much simpler approach in the long run:
[URL="http://unix-tutorial.blogspot.com/2007/07/cowon-d2-avidemux-howto.html"]
http://unix-tutorial.blogspot.com/2007/07/cowon-d2-avidemux-howto.html[/URL]

It has worked for me - I've just tried converting an MPEG. I think for some videos, the sound may need re-encoding to MP3 - it should work for most without re-encoding the audio though.

---

### Post by feisty_hot_lover on 2008-01-01
> **dcs3jah said:**
> Glad someone else found it useful. I've not taken a look at the script for a long time, so I've not updated it I'm afraid (I don't watch much video on my D2 anymore).

But, in case it's useful, I found a video tutorial - I reckon this is a much simpler approach in the long run:
[URL="http://unix-tutorial.blogspot.com/2007/07/cowon-d2-avidemux-howto.html"]
http://unix-tutorial.blogspot.com/2007/07/cowon-d2-avidemux-howto.html[/URL]

It has worked for me - I've just tried converting an MPEG. I think for some videos, the sound may need re-encoding to MP3 - it should work for most without re-encoding the audio though.Thanks for the  link to Avidemux.  Great little program.

---

### Post by Sonja on 2008-01-16
Awesome!!

---

### Post by Sonja on 2008-01-16
I have tried both, and the Iriverter method works better. The Nautilus script unfortunately squashed one of my videos too much, so the people looked very thin instead of normal width. Iriverter it is.

---

### Post by kiev on 2008-02-18
thank you

---

### Post by jabeez on 2008-03-19
Man this is driving me nuts....I just got a D2 for the wife's B-Day, and so far trying to get video on it has been fruitless. I've tried iriverter with the D2 profile, but no matter what I try to change the audio is always WAY loud/overmodulated. I tried Avidemux, following the exact steps in that video tutorial, and the video won't even really play, it just stutters REALLY slowly. I tried adding this script to Koqueror's service menu, but haven't quite figured it out yet (to previous poster, how did you do this?). Any other options and how/why is it this complicated?

---

### Post by jman0591 on 2008-05-06
Let me start by saying thanks for creating this script.  It saved me from having to boot back into windows.  The only problem is that it doesn't work (just a small problem I know).  

When run outside of the terminal nothing happens, but when run inside the terminal it runs ok until it gets to the line  with the 'let' command.  At this point I get this error message "d2-convert: 194: let: not found".  Since this has worked for other people I assume it is my computer that is the issue.

Can anyone help me out with this?  I would like to switch over from iRiverter to this script, but can't really do so for obvious reasons.  Thanks in advance!

---

### Post by Sonja on 2008-05-20
Iriverter is crashing now, though. :(

[http://ubuntuforums.org/showthread.php?p=5004933](http://ubuntuforums.org/showthread.php?p=5004933)

---

### Post by Sonja on 2008-05-21
How would I edit the Nautilus script to make it move the completed file to /media/D2/VIDEO ?

In other words, the script would create a D2-compatible file and put it directly on my D2, rather than putting it where the source file was. (I don't need 2 copies of the file on my computer.)

---

### Post by GrouchoMarx on 2008-05-23
I haven't tested it myself (I've settled on the Avidemux method), but try adding a move command to the while loop at the end of the script:

```
while [ $# -gt 0 ]; do
	total_frames=0
	movie=$1
	echo "# Processing $video_in_type Video $movie \n Total: $Video_Count"
	get_frames
	get_input_res
	get_input_ar
	calc_output_res
	mpeg4_encode
	**mv "D2-$movie" /media/D2/VIDEO/$movie**
	let Video_Count=Video_Count+1
	shift
done


```

---

### Post by AlmoG on 2008-08-01
when trying to run the script in nautilus, nothing happens,
and when trying to run it in the terminal i get this output:
> 
almog@Almogs:~$ ./.gnome2/nautilus-scripts/d2-convert trt5.flv 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
# Processing  Video trt5.flv \n Total: 1
Can't get aspect ratio or input resolution - using 320x240
tmp_x is 7
tmp_y is 7
out_movie1 is trt5.avi
out_movie2 is D2-trt5.avi
rm: cannot remove `frameno.avi': No such file or directory
rm: cannot remove `divx2pass.log': No such file or directory
rm: cannot remove `stream.yuv': No such file or directory
rm: cannot remove `D2-trt5.avi': No such file or directory
# Converting trt5.flv to MPEG4
Total frames: 
Total movies: 1
res_x= - res_y=
ar_x= - ar_y=
Output res: 320x240
Can't estimate progress



can anyone please help?

---

### Post by greenplastic on 2009-09-19
sweet! thanks

---

### Post by macias on 2010-01-18
Could someone please attach the original converter (the one dcs3jah linked 2 years ago) because now the link (and the whole home page) is dead.

Thank you very much in advance.

Cheers,

---

### Post by eddier on 2010-01-18
REf. MPX, Is it possible that this is referring to MP3,MP4,MPEg etc.

eddie

---

### Post by nothing1212 on 2011-03-07
I use the more recent ffmpeg:

ffmpeg -i input_video.avi -vcodec libxvid -acodec libmp3lame -s 320x240 output_video.avi

Has been working flawlessly. Info from: [CowonD2VideoConversion/]("http://www.david-web.appspot.com/cnt/CowonD2VideoConversion/") (http://www.david-web.appspot.com/cnt/CowonD2VideoConversion/)

---

