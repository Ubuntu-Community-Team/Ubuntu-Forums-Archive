---
title: "Downloading FLV Files (Youtube etc)"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Daveg4otu on 2008-04-26
Is there any way of doing this successfully....?

I have tried using the Miro Internet TV - doesn't recognise the files for download altho it will play already d/led(In WinXP)  files

Tried installing the Moyea FLV downloader  under WINE - shows error messages - refuses to D/l

Any advice very welcome.

---

### Post by hackle577 on 2008-04-26
If you use Firefox then [this extension]("https://addons.mozilla.org/en-US/firefox/addon/3006") is what you want.

---

### Post by unclejac on 2008-04-26
I was meaning to ask this a while ago. :) cheers hackle577

---

### Post by unutbu on 2008-04-26
For youtube you do not need any new software. After you watch the video, look in /tmp for a large file called Flash*****. If it's there, its probably the flv file. It it isn't there, look in 

~/.mozilla/firefox/fazmc0f6.default/Cache

I'm not sure if "fazmc0f6" is the same for everyone -- yours might be different. Look for a large file with an appropriate time stamp. 

Note that this does not work with all sites.
It does not work with Jay Leno's episodes ([http://www.nbc.com/The_Tonight_Show_with_Jay_Leno/video/episodes.shtml](http://www.nbc.com/The_Tonight_Show_with_Jay_Leno/video/episodes.shtml)) for example.

If you search ubuntuforums I think there is a thread (possibly many) where people recommended plugins for Firefox that can also download the videos.

There is also, [http://keepvid.com/](http://keepvid.com/), where I think all you do is paste in the url and click 'download'. 
It gives you the option to save .flv (low quality) or .mp4 (high quality).

---

### Post by nina_aoki on 2008-04-26
You need to add the **Download Helper** extention in Firefox.  

Very easy peasey!  ;)

- nina

---

### Post by DMK62 on 2008-04-26
There is also a command line program you can use called youtube-dl

sudo apt-get install youtube-dl or install from synaptic.

Dale

---

### Post by Anduu on 2008-04-26
The DownloadHelper plugin for Firefox is the only way to go IMHO.It works on virtually any site with video content.

---

### Post by mowque on 2008-04-27
I personally think they did a good job with youtube-dl....just throw that plus the url into terminal and you have a vid! loads pretty quick too....

---

### Post by Daveg4otu on 2008-04-27
Thanks  to all - The Firefox extension works  just fine.

---

