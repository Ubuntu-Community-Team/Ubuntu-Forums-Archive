---
title: "how do I tag my videos like I have done to my music"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-04-30
I used Easytag for getting the tags right on my music and it works great. But it doesn't show my videos when I open them. So is there a program like Easytag to do the same with my videos. I have .mp4 .avi .vob .mkv

---

### Post by slickymaster on 2014-04-30
See this: [Tag and manage video files]("http://askubuntu.com/questions/29513/tag-and-manage-video-files")

---

### Post by EZZ9 on 2014-04-30
Ok, I looked at it and went to the page [http://wwidd.com](http://wwidd.com)
Did what it said, well tried to on step 2 "[B]ffmpeg" is not there to download
And in step 3 it says to [/B]Enter the Wwidd folder and run the file [I]start
[/I]The sadness of being a newbie is I don't know what the meaning of "run the file" is.
Can someone tell me?
 Mama always said no running in the house, but that was 50 years ago lol.

---

### Post by slickymaster on 2014-04-30
> **EZZ9 said:**
> Ok, I looked at it and went to the page [http://wwidd.com](http://wwidd.com)
Did what it said, well tried to on step 2 "[B]ffmpeg" is not there to download
And in step 3 it says to [/B]Enter the Wwidd folder and run the file [I]start
[/I]The sadness of being a newbie is I don't know what the meaning of "run the file" is.
Can someone tell me?
 Mama always said no running in the house, but that was 50 years ago lol.

From that website> Unzip the downloaded file. It will unpack a folder named Wwidd. Before starting, you're free to move this folder someplace else.
on Ubuntu Check and install the following packages in the Ubuntu Software Center: nodejs, ffmpeg, sqlite3, and vlc

Did you installed the mentioned packages?

---

### Post by squakie on 2014-05-01
If it is dependant on ffmpeg, you will have to find a way to install it outside of the Ubuntu repositories.  There was a disagreement in the ffmpeg community a couple of years ago that resulted in Debian/Ubuntu going with a fork of ffmpeg called libav.  ffmpeg is no longer available in Ubuntu.

---

### Post by EZZ9 on 2014-05-01
Oh bummer, so without ffmpeg,  [URL="http://wwidd.com"]wwidd.com 

[/URL] We can say "it's dead Jim", for Ubuntu users?

---

### Post by squakie on 2014-05-02
If it's only needed at runtime, that is when the start is executed after unpacking the zip file does NOT try to build the program from source, I'd at least try it - it probably won't work but it's worth a shot (might be run-time compatible with libav).  If it needs to build the source - give it a try - the worst that can happen is the build fails.

---

### Post by squakie on 2014-05-02
I just downloaded this. I already had vlc, so I downloaded the other packages except ffmpeg.  I extracted the files and looked at the start.sh file.  It doesn't build anyting, so I tried executing it.  I get an error message about "node" not found.  I don't know if that's an ffmpeg thing that isn't in libav or if it's something else.  I ended up just removing it as the website does say the Ubuntu file for download is for version 10, and that is way, way outdated and not supported.  I suspect this has never been made to work with 14.04, or for that matter any release after 10.

So, it doesn't need the ffmeg libs to build, maybe at run time, and that may be the difference.  Either way, it doesn't run for me.

---

### Post by EZZ9 on 2014-05-02
Yeah, it did now work for me either 
IT's DEAD, JIM!
Going to keep this one open, because there is no solve for this to todays date and someone may know another way or there may be a way in the near future.

---

### Post by EZZ9 on 2014-05-02
[http://www.bittorrent.com/sync/downloads](http://www.bittorrent.com/sync/downloads)
Want to set this up so I can share files with my computers and my mother's computer. But 
1. How do I find out want version I need to download there are 7 under Linux? Ahh!
 2. I have download the first one on the list "to try" and I have extracted it, now I have the file in my "download file" So what do I do with it? Where do I need to place it, so it will work?

---

### Post by squakie on 2014-05-02
That's sharing/sync program - it has nothing to do with the title of your thread.  If this is a new question please open a new thread with a relevant title - it will get the attention it deserves and be there for others looking for such a thing instead of imbedded inside a thread whose title has nothing to do with it.

---

### Post by squakie on 2014-05-03
If you are looking for something to organize you movies I found this mentioned in another thread:

[http://linux.softpedia.com/get/Multimedia/Video/MeD-s-Movie-Manager-6486.shtml](http://linux.softpedia.com/get/Multimedia/Video/MeD-s-Movie-Manager-6486.shtml)

---

