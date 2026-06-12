---
title: "C++, Youtube downloader."
date: 2011-05-25
forum: Programming Talk
---

### Post by cgroza on 2011-05-25
Hello, I am working on a Youtube downloader together with another user on this forum.
We have the GUI part done.
The program is doing playlist, video and user searching.
Now we want to release version 0.1 but we need to implement the video download.

According to the documentation I have read, I need the video ID (which I already have it by parsing the xhtml returned by youtube) and a video token, with which I make an URL:

"http://www.*youtube*.com/*get_video*.php?video_id&t % id, token.

Now, I do not know how to get that token.
I have looked at php scripts but I do not seem to get them. 

I use curl to interact with the Youtube API.

Is there a request I should do to the Youtube API to get that token?

Thank you.

---

### Post by nvteighen on 2011-05-25
I highly doubt you're using the YouTube *API* ([http://code.google.com/apis/youtube/getting_started.html](http://code.google.com/apis/youtube/getting_started.html)). If you're using curl, what you're doing is to use curl to interface with YouTube via regular HTTP.

Considering that YouTube doesn't allow people to download their videos, I'm pretty sure curl won't work. And I'm also pretty sure the YouTube API won't work either.

As far as I know, YouTube downloaders work by repathing the video stream of the Adobe Flash Player to a new output place, usually converting it to MPEG-4 or some other format.

---

### Post by cgroza on 2011-05-25
> **nvteighen said:**
> I highly doubt you're using the YouTube *API* ([http://code.google.com/apis/youtube/getting_started.html](http://code.google.com/apis/youtube/getting_started.html)). If you're using curl, what you're doing is to use curl to interface with YouTube via regular HTTP.

Considering that YouTube doesn't allow people to download their videos, I'm pretty sure curl won't work. And I'm also pretty sure the YouTube API won't work either.

As far as I know, YouTube downloaders work by repathing the video stream of the Adobe Flash Player to a new output place, usually converting it to MPEG-4 or some other format.
I saw examples using get_video. I remember pasting a UR like that into my browser and it started a download. Maybe they disabled this thing. 

Anyway, I will research more.

You said they repath the stream from adobe flash.

Could someone describe me the general process of doing it?

---

### Post by Blackbug on 2011-05-26
well, i tried myself with curl/wget but download didnt succeed.
in case someone comes up with some fruitful output, it would be great to hear

---

### Post by cgroza on 2011-06-19
Just wanted to let you know that today, me and my teammate successfully  downloaded a youtube video using curl and C++.

No need to intercept any kind of video player stream. 

Github with source code at:
[EMAIL="git@github.com:cgroza/wx-Youtube.git"]git@github.com:cgroza/wx-Youtube.git[/EMAIL]

---

### Post by JupiterV2 on 2011-06-20
I am fairly confident that you violate the [Terms of Service]("http://www.youtube.com/t/terms") by downloading videos from Youtube and that the practice is illegal due to [copyrigh]("http://www.youtube.com/t/copyright_center")t concerns. There is a reason why they go to so much trouble to prevent people from downloading from Youtube, whether we agree agree with it or not. Just want to make sure you guys protect yourselves and practice safe coding (like safe sex but with more rubber).

---

### Post by cgroza on 2011-06-20
> **JupiterV2 said:**
> I am fairly confident that you violate the [Terms of Service]("http://www.youtube.com/t/terms") by downloading videos from Youtube and that the practice is illegal due to [copyrigh]("http://www.youtube.com/t/copyright_center")t concerns. There is a reason why they go to so much trouble to prevent people from downloading from Youtube, whether we agree agree with it or not. Just want to make sure you guys protect yourselves and practice safe coding (like safe sex but with more rubber).
Hmm, I will read more on that, thanks for the heads up...

---

