---
title: "Video Streaming in Apache"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by aneez004 on 2013-05-07
Hi,

I am trying to stream videos from a local server (localhost), but all videos are getting downloaded. I need to stream videos (all video formats) with seeking option from a web browser.


I am using Ubuntu 12.04, apache 2.2. It would be very much helpful if anyone can provide a detailed solution for this?


Regards,
Anees

---

### Post by Lars Noodén on 2013-05-07
These three should do streaming of video for you, but none of them are actually Apache.  They do however support a wide variety of formats/codecs.

Icecast

[http://www.icecast.org/faq.php](http://www.icecast.org/faq.php)

[http://www.icecast.org/ezstream.php](http://www.icecast.org/ezstream.php)


FFMPEG

[http://ffmpeg.org/](http://ffmpeg.org/)

VLC

[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

---

### Post by FakeOutdoorsman on 2013-05-07
You didn't give us much information to work with. What have you tried? What formats are you attempting to play? Note that "all video formats" are not able to be played via a web browser. Do you want streaming (as in a live broadcast where the encoder is working in real time) or progressive download (like most video sites where the video has been previously encoded and the viewer watches-as-it-downloads)?

---

### Post by aneez004 on 2013-05-08
Thanks for replying. Let me look into those.

---

### Post by aneez004 on 2013-05-08
> **FakeOutdoorsman said:**
> You didn't give us much information to work with. What have you tried? What formats are you attempting to play? Note that "all video formats" are not able to be played via a web browser. Do you want streaming (as in a live broadcast where the encoder is working in real time) or progressive download (like most video sites where the video has been previously encoded and the viewer watches-as-it-downloads)?

I put the videos in different formats (flv, avi, mp4, wmv etc..) in the Document root of the server. Then I tried to access them from browser as localhost. When I click on the video, it's getting downloaded. I want to make them stream with the option to "seek" as in Youtube. Downloading them and playing them is space & time consuming and is not what is required. 

I could play mp3 files, view documents etc.. all via browser without getting downloaded. I need to make videos also like that. Actually it is for setting up ad digital resource center for providing tutorial videos for students, from a local server (within an institution). It need not be accessed worldwide.

Please suggest apt solutions for this.

Regards,
Anees

---

### Post by HermanAB on 2013-05-08
ffserver

---

### Post by aneez004 on 2013-05-08
> **HermanAB said:**
> ffserver


Thanks for the reply.

Could you please elaborate its working. From this link [http://www.ffmpeg.org/ffserver.html](http://www.ffmpeg.org/ffserver.html), I think it will only help for real time video streaming. ([http://www.ffmpeg.org/ffserver.html#toc-What-can-this-do_003f](http://www.ffmpeg.org/ffserver.html#toc-What-can-this-do_003f)). 

I think it wont serve my purpose. Any other suggestions?


Regards,
Anees

---

### Post by SeijiSensei on 2013-05-08
From the [ffserver page]("http://www.ffmpeg.org/ffserver.html#What-can-this-do_003f"):

"It can also stream from files, though that is currently broken. Very often, a web server can be used to serve up the files just as well."

I don't think that will solve the OP's problem.  

I'm curious about this, too.  I'd like to watch videos on my server with my Android phone, but simply retrieving them from Apache results in the file being downloaded rather than streamed.  I installed VLC on my server, but so far have been unable to figure out the right set of command-line parameters to get it to stream an existing file.  Most of the comments on the web concern streaming from things like cameras or TV cards.

---

### Post by Cheesemill on 2013-05-08
You can pick from any number of the embedded video players available, or just code your own page using a few lines of HTML5.


[http://jarisflvplayer.org/](http://jarisflvplayer.org/)
[http://www.longtailvideo.com/jw-player/download/](http://www.longtailvideo.com/jw-player/download/)
[http://flowplayer.org/](http://flowplayer.org/)
[http://www.w3schools.com/html/html_videos.asp](http://www.w3schools.com/html/html_videos.asp)
[http://www.instantshift.com/2010/05/14/21-free-video-players-for-your-website-and-blogs/](http://www.instantshift.com/2010/05/14/21-free-video-players-for-your-website-and-blogs/)

---

### Post by aneez004 on 2013-05-13
Thanks everyone for your replies. It's now working almost for me with the help of htaccess. I added following contents to .htaccess file in Document Root : 

# MIME types for Video
AddType video/mp4 .mp4 .m4v .f4v .f4p
AddType video/ogg .ogv
AddType video/webm .webm
AddType video/flv .flv


Now the videos are not getting downloaded. I am able to stream videos within a LAN

---

### Post by Lars Noodén on 2013-05-13
Glad it works.  Isn't that just regular downloading that you have going now and not streaming?

---

