---
title: "AVI to DVD"
date: 2005-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by ptesone on 2005-08-30
here's 6 basic steps to convert a .AVI to DVD so you can watch your movies on your home player, not just your computer. . .But first we need to figure out if it's a fullscreen movie or letterbox movie. . .Movies normally come in two sizes: 4:3 (fullscreen) or 16:9 (letterbox) which they call aspect ratio. . .They also come in two formats PAL (Non-US) and NTSC (US). . .The following examples are for NTSC Only!

what you need first:
transcode
mplayer
Mjpegtools
ffmpeg
dvd+rw-tools
Dvdauthor
some hardrive space

in this example I will be using a 16:9 movie.avi for our conversion. . .

1.) Split the .avi file into 2 seperate files, one for video and one for audio:

```
transcode -i movie.avi -y ffmpeg --export_prof dvd-ntsc --export_asr 3 -o movie -D0 -s2 -m movie.ac3 -J modfps=clonetype=3 --export_fps 29.97
```

this will make:
movie.m2v (video)
movie.ac3 (audio)

note: if you're doing a fullscreen (4:3) movie then simply change --export_asr 3 to --export_asr 2

2.) (optional) Extract 5.1 Audio:

```
tcextract -d2 -i movie.avi -a0 -x ac3 | tcextract -d2 -x ac3 -t raw > movie.ac3
``` 

This is an extra step if you know your .avi file actually has 5.1 surround sound. (Step one only produces a stereo .ac3 file !)
How can you tell? Do this first:

```
mplayer -vo dummy -identify movie.avi 2> /dev/null | grep "5.1 ("
``` 

if you get this output then you have 5.1:

```
AC3: 5.1 (3f+2r+lfe) 48000 Hz 384.0 kbit/s
``` 
if you don't, just ignore this step!

3.) Put the video & audio file back together:

```
mplex -f 8 -o dvd_movie.mpg movie.m2v movie.ac3
``` 

this will make dvd_movie.mpg ready for DVD authoring. . .

4.) open your favorite text editor and paste the following:

```
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>
``` 

save the file as: dvdauthor.xml 
in the same directory as your movie files
(you can also change the chapters to fit the times of your movie)

5.) Create a DVD directory where your movie files are and do this:

```
dvdauthor -x dvdauthor.xml
``` 

this will create two AUDIO_TS and VIDEO_TS directories in your DVD directory. . .

6.) Test it & Burn it:

to test it:
```
xine dvd:/full/path/to/DVD/VIDEO_TS/
``` 

to burn it:
```
growisofs -Z /dev/dvd -dvd-video DVD/
``` 

note: I like to use DVD-RW discs for a test before I use a real disc. . .
If all goes well, the above will produce movie with no menus, just the movie that should play when you put in your disc. . .and if there's more than one .avi then simply do this in your dvdauthor.xml file:

```
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie_part1.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
         <vob file="dvd_movie_part2.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
     </titles>
   </titleset>
 </dvdauthor>
``` 


GOOD LUCK!

---

### Post by endy on 2005-08-30
Nice guide, I've done a similar thing but using ffmpeg for the transcoding:

[http://www.ubuntuforums.org/showthread.php?t=50063](http://www.ubuntuforums.org/showthread.php?t=50063)

---

### Post by WirelessMike on 2005-08-30
Yet another interesting method...

[http://www.videohelp.com/forum/viewtopic.php?t=242455](http://www.videohelp.com/forum/viewtopic.php?t=242455)

---

### Post by ptesone on 2005-08-31
here's how you add subtitles to your video stream:

1.) download the correct subtitle from [http://eXTratitles.to](http://eXTratitles.to)

2.) use a program from dvdauthor called Spumux to add the subtitle text into the DVD video. Just make sure you have a .spumux dir in your home dir and put your fav .tff font in it. I used Vera.tff but any True Type font will do. Open your fav text editor and paste this:

```
<subpictures> <stream> <textsub filename="movie.srt" characterset="ISO8859-1" fontsize="18.0" font="Vera.ttf" horizontal-alignment="center" vertical-alignment="bottom" left-margin="60" right-margin="60" top-margin="20" bottom-margin="30" subtitle-fps="29.97" movie-fps="29.97" movie-width="720" movie-height="478"/> </stream> </subpictures>
``` 

save as 'subtitle.xml'

3.) Merge the subtitles into the DVD video:

```
spumux -s0 subtitle.xml < dvd_movie.mpg > dvd_movie.mpg.temp mv dvd_movie.mpg.temp dvd_movie.mpg
``` 

when complete you should now have subtitles in your dvd_movie.mpg

I goto [http://cdcovers.cc](http://cdcovers.cc) for all my printing and menu needs. . .

---

### Post by mstlyevil on 2005-08-31
Nice guide

   However this thread probally should be moved to the how to's.

---

### Post by ptesone on 2005-08-31
ok
where's that at?

---

### Post by poofyhairguy on 2005-08-31
[QUOTE=ptesone]ok
where's that at?[/QUOTE]

Don't worry, thats my job.

---

### Post by wood1950 on 2006-02-13
Really isn't necessary to convert, just get a Phillips 642  player, that model plays everything from AVI to MPG's, to DVIX.

---

