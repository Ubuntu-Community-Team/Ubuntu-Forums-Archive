---
title: "dvdslideshow problem"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by gerben1 on 2008-05-09
Hi, 
I am trying to make a simple picture DVD slide show, without any music. I am getting an error when dvdslideshow tries make a silent audio file as you can see below:

Error in console output:
```

...
[dvd-slideshow] No audio files passed.  Using 0:1:0.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:1:0.000
sox soxio: Failed reading `/dev/zero': unknown file type `raw'
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:1:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
cat: /home/gerben/dvd-slideshow_temp_13985/audio1_????.raw: No such file or directory
sox soxio: Failed reading `-': unknown file type `raw'
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see [dvd-slideshow] No audio files passed.  Using 0:1:0.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:1:0.000
sox soxio: Failed reading `/dev/zero': unknown file type `raw'
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:1:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
cat: /home/gerben/dvd-slideshow_temp_13985/audio1_????.raw: No such file or directory
sox soxio: Failed reading `-': unknown file type `raw'
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/gerben/dvd-slideshow.log for details
[dvd-slideshow] cleanup...
 for details
[dvd-slideshow] cleanup...

```

error in /home/gerben/dvd-slideshow.log:

```

[dvd-slideshow] No audio files passed.  Using 0:1:0.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:1:0.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:1:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
[dvd-slideshow] Creating ac3 audio...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
/home/gerben/dvd-slideshow_temp_13985/audio1.wav: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/gerben/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

```

Does anybody know how I can get this working?

---

### Post by timcredible on 2008-05-09
i use digikam to make slide shows, but it looks like dvdslideshow may require an audio track.  maybe you could find a .wav or .mp3 that has no sound in it for what you're looking to do.

---

### Post by halitech on 2008-05-09
try ManDVD ([http://getdeb.net](http://getdeb.net)) works fine for me

---

### Post by gerben1 on 2008-05-09
It is trying to make a silent audiotrack, but it somehow doesn't succeed. I have tried some GUI programs to make a slide show, but not much luck. I'd rather just use these commandline programs for now, as I believe there is no GUI program for Ubuntu that works nicely (and is  english and maintained etc.). 

I already found out that it can be done very easily just like this:
```

dir2slideshow -n 'MySlides' -t 10 directory_where_pictures_are/

dvd-slideshow -n MyslideShowTitle -f MySlides.txt

```

but unfortunately dvd-slideshow produces that error

---

### Post by gerben1 on 2008-05-09
@Halitech:
I tried manDVD, but is just a frontend that also uses dvd-slideshow, so it gives me the same error message. Also the program is French, and if you choose English a bunch of things are not translated at all (like the title bar) and other parts have very basic spelling errors, so I can't say I would have much confidence in using that program.

---

### Post by gerben1 on 2008-05-09
by the way this is the command that is not succeeding:

(from /usr/bin/dvdslideshow)
```

sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir"/audio1_$i_padded.raw trim "0" "$song_end_hms"

```

---

### Post by gerben1 on 2008-05-09
I found out how to solve this, I did this to get it working:

- installed all libsox packages I could find in Synaptics
- edited /usr/bin/dvd-slideshow, replace all "ab 192" with "ab 192k"


It is strange that ManDVD is working for you Halitech, as the option "ab 192" is passed to ffmpeg and ffmpeg doesn't take 192 anymore, the new ffmpeg requires a 'k' after 192. This is just wrong in dvd-slideshow. I guess you had already changed that? or you have an older version of ffmpeg? (or perhaps I have a strange ffmpeg version)

---

### Post by halitech on 2008-05-09
I've been using it for over a year with making slide shows and putting tv shows on dvd and only had 1 mess up (my own fault though, forgot to change it to NTSC instead of PAL) but I'm also still using Gutsy so maybe that is why it is working for me. Far as the language, the title bar is the only thing I've noticed (but then again I'm not a stickler for proper grammer as long as the program works for me)

---

### Post by glug101 on 2008-05-14
Thanks a bunch for this.  I was pulling my hair out figuring this one out.  There should be a simple way to fix this though, with steps to follow.  

For instance:
command to install all libsox files
```
sudo apt-get install libsox-fmt-all
```

There also must be some single line command for awk that would allow you to find and replace the ab 192's.  I discovered that dvd-menu (another program that is installed with dvd-slideshow) was having similar problems.  

Anyhow, worked like a charm, thanks! :-D

---

### Post by gerben1 on 2008-05-15
> **glug101 said:**
> Thanks a bunch for this.  I was pulling my hair out figuring this one out.  There should be a simple way to fix this though, with steps to follow.  

For instance:
command to install all libsox files
```
sudo apt-get install libsox-fmt-all
```

There also must be some single line command for awk that would allow you to find and replace the ab 192's. 


You can find and replace the text from the command line like this:
```

sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow

```
this will search for all occurrences of "-ab 192" in the file /usr/bin/dvd-slideshow and replace them with "-ab 192k"

To summarise, you just need to issue these two commands in the console:
```

sudo apt-get install libsox-fmt-all
sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow

```
The first command will install all sox libraries, it is only about 1 Mb in total, and the second command does the necessary text replacement in the dvd-slideshow script.

> **glug101 said:**
>  I discovered that dvd-menu (another program that is installed with dvd-slideshow) was having similar problems. :-D

Yes, I have also tried dvd-menu for a while but I did not get it working properly, so I decided to just use Qdvdauthor to make my menus.

---

### Post by heiNey on 2008-08-02
typing sudo apt-get install libsox-fmt-all doesnt work for me...it says coudlnt find package information...do i need to add in any repositories?

---

### Post by gerben1 on 2008-08-02
It is in multiverse, take a look at "System->Administration->Software sources" and make sure that "Software restricted by copyright or legal issues (multiverse)" is checked.

---

### Post by heiNey on 2008-08-02
yea its checked, but still nothing...how odd.  i guess ill just load each deb individually

---

### Post by heiNey on 2008-08-02
ok, got it working...one other off topic question though...is there a way to have the soundtrack on a continuous loop when creating a slideshow?

i put in a soundtrack but the slideshow is 10 minutes long adn the song is 4 minutes long, so the remaining 6 minutes is just silence.

---

### Post by gerben1 on 2008-08-03
There doesn't seem to be a loop option for the sound, but you can give multiple audiofiles which will then be played back to back in order, so I guess you can just give the same file a couple of times so that the combined length is longer that the slideshow.

something like this:
```
dvdslideshow -f SlideShowInput.txt -n My10minSlideShowWithMusic -a My4minMusicfile.mp3 -a My4minMusicfile.mp3 -a My4minMusicfile.mp3 
```

---

### Post by heiNey on 2008-08-04
hmm...i guess if i did this using commandline...but i was using mandvd...i guess you cant do it in that program

---

### Post by gerben1 on 2008-08-04
I don't know about ManDVD, but I would expect it would offer the possibility to add more than one sound file to a slideshow.

Did you try adding the sound file twice? If you can't add the same sound file twice, just make a copy of the original sound file and add both, original and copy.

---

### Post by halitech on 2008-08-04
I think you will need to use something like audacity to put them all together and use the modified song

---

### Post by heiNey on 2008-12-29
im having another problem.  i had this all working a few months ago, but then i had to format in order to install hardy.  now, when i try to make a slideshow with -a <audiofile.mp3>, i get a sox error that says: 

```

sox soxio: Can't open input file `/home/heiney/slideshow/done/dvd-slideshow_temp_11966/audio1_0000.wav': No such file or directory

```

i did a -nocleanup option to see what files are created, and there's an audio1.wav file in the temp directory, but its just silence.  have no idea what's wrong here.

EDIT: solved it. in case anyone needs to know what went wrong, you need to install the lame package first.

```


sudo apt-get install lame


```

---

### Post by mpoole on 2009-01-24
I was having the same problem and am now able to create the vob file without error messages.  I am following the instructions presented on this web page: [http://dvd-slideshow.sourceforge.net/wiki/Complete_Example]("http://dvd-slideshow.sourceforge.net/wiki/Complete_Example")

Now I am on the the step where I create the dvd-menu and I am getting a similar error.  Here is what the dvd-menu.log looks like:
[dvd-menu] Sat Jan 24 13:50:07 CST 2009
[dvd-menu] dvd-menu version 0.7.5
[dvd-menu] Linux martin-desktop 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux
[dvd-menu] Output directory=/home/martin
[dvd-menu] Final dvd filesystem is in /home/martin/dvd_fs
[dvd-menu] Video: NTSC  Audio: AC3
[dvd-menu] Debug=0  
[dvd-menu] Found mjpegtools version 1.8.0
[dvd-menu] mjpegtools is >= 1.6.3-rc1
[dvd-menu] ###################################
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, wav, from '/home/martin/dvd-menu_temp_11647/audio.wav':
  Duration: 00:00:01.0, start: 0.000000, bitrate: 1536 kb/s
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Output #0, ac3, to '/home/martin/dvd-menu_temp_11647/audio.ac3':
  Stream #0.0: Audio: ac3, 48000 Hz, 5:1, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
[dvd-menu] mplexing the files.............
[dvd-menu] ###############################################
[dvd-menu] spumuxing the files.............
[dvd-menu] ERROR during spumux execution!
[dvd-menu] see /home/martin/dvd-menu.log for details

Can anybody help solve this issue?

---

### Post by gogink on 2012-08-02
these two comands that install libsox-fmt-all, and
sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow
did NOT solve my issue (same problem with ac3 sond and crash after that).
but thi did, 
[http://mohaksblog.blogspot.com/2008/12/how-to-create-slideshow.html](http://mohaksblog.blogspot.com/2008/12/how-to-create-slideshow.html)
i.e. just let be mp2 defoult spund, not ac3.
For the ones that has deeper understanding of dvd-slideshow, look at this
[http://www.linuxquestions.org/questions/linux-software-2/dvd-slideshow-gives-problem-with-ffmpeg-encoder-655699/](http://www.linuxquestions.org/questions/linux-software-2/dvd-slideshow-gives-problem-with-ffmpeg-encoder-655699/)

---

