---
title: "Alternative like mplayer to play FLASH ADOBE?"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-18
Hello,

I would like to watch Polsat without installing Adobe flash adobe. I have mplayer installed and I can ask a bit to the admin. No flash is installed since it is a limited x11 machine.

Here is the link
[http://www.megawypas.pl/readarticle.php?article_id=176](http://www.megawypas.pl/readarticle.php?article_id=176)

What could be the alternative? 

Thank you !

---

### Post by el_koraco on 2011-09-18
Install the package gecko-mediaplayer, and the Firefox addons FlashVideoReplacer and FlashBlock.

---

### Post by gandaran on 2011-09-18
> **el_koraco said:**
> Install the package gecko-mediaplayer, and the Firefox addons FlashVideoReplacer and FlashBlock.

+1
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

---

### Post by honeybear on 2011-09-18
> **el_koraco said:**
> Install the package gecko-mediaplayer, and the Firefox addons FlashVideoReplacer and FlashBlock.

I am sorry but firefox is not installed :( Can it run from the bash under X11 without iceweasel/firefox? There is elinks for internet.

---

### Post by dniMretsaM on 2011-09-18
You could try [Gnash](http://www.gnu.org/s/gnash/).

---

### Post by honeybear on 2011-09-18
> **dniMretsaM said:**
> You could try [Gnash](http://www.gnu.org/s/gnash/).

thank you. However the concerned webpage is not working through gnash :( 
 ( [http://www.megawypas.pl/readarticle.php?article_id=176](http://www.megawypas.pl/readarticle.php?article_id=176) ) How to bring the flash video url into gnash or other any program to make it work?

forget gnash :( 
> 
Alessandro Pignotti (a-pignotti)  wrote on 2011-04-23:  	  #8

Currently only YouTube is supported officially (although it's does not work anymore with 0.4.6.1 and we will release an update shortly). We are working to improve coverage of the supported sites but we have limited manpower so I cannot guarantee support for any specific site in the short term. I'm closing the bug as it's a mix of issues but I confirm the problem.


---

### Post by jtarin on 2011-09-18
[Gnash documentation can be found here.]("http://www.gnu.org/software/gnash/manual/gnashuser.html")

---

### Post by honeybear on 2011-09-18
> **jtarin said:**
> [Gnash documentation can be found here.]("http://www.gnu.org/software/gnash/manual/gnashuser.html")

it seems that we would need a RTMPE reader for LINUX. there are a bunch for the windows microsoft

[http://stream-recorder.com/forum/record-rtmp-flash-video-flv-stream-embedded-t2324.html](http://stream-recorder.com/forum/record-rtmp-flash-video-flv-stream-embedded-t2324.html)

(I read man of gnash, but gnash rtmp:(( I have no idea how to convert it since right click is not working into firefox to copy the URL link of the rtmp flash streaming server to internet)



here the links for webtv: [http://wiki.gnashdev.org/Web_TV](http://wiki.gnashdev.org/Web_TV)

---

### Post by honeybear on 2011-09-18
> **dniMretsaM said:**
> You could try [Gnash](http://www.gnu.org/s/gnash/).

nice buddy icon ;) Look penguin power ;) :) 
mplayer [http://www.montereybayaquarium.org/media/strm/mba_peng.asx](http://www.montereybayaquarium.org/media/strm/mba_peng.asx)

---

### Post by jtarin on 2011-09-19
Open Synaptic Package Manager and search for "rtmpdump".

is a console application that allows you to download RTMP and RTMPE streams to your hard drive. rtmpdump supports SWF verification. It can resume recording ( --resume option)

Example of usage:
rtmpdump -r "rtmp://host/dir/file.flv" -o filename.flv

---

### Post by honeybear on 2011-09-19
> **jtarin said:**
> Open Synaptic Package Manager and search for "rtmpdump".

is a console application that allows you to download RTMP and RTMPE streams to your hard drive. rtmpdump supports SWF verification. It can resume recording ( --resume option)

Example of usage:
rtmpdump -r "rtmp://host/dir/file.flv" -o filename.flv

thank you very much. A small question to get the url for rtmpdump, the thing is that the url of the flash stream is kind of hidden... that becomes tricky and not easy ... :(

---

### Post by Monsuco on 2011-09-19
I'm not familiar with Polsat but I've had issues with a netbook of mine and flash videos inside a web page. It seems flash is a little too resource hungry for this netbook.

My solution  has been to use the [Video Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/") extension to rip videos and then I just watch the flv files in VLC or MPlayer. You said you don't use Firefox. I could find [Chrome extensions]("http://www.chromeplugins.org/extensions/video-downloader-extension-with-multiple-sites-support/") that sound like they work the same way but I haven't personally tested them.

VLC and MPlayer clearly are less resource hungry when playing videos than embedded flash. I hope this helps a bit.

---

### Post by jtarin on 2011-09-19
> **honeybear said:**
> thank you very much. A small question to get the url for rtmpdump, the thing is that the url of the flash stream is kind of hidden... that becomes tricky and not easy ... :(
[Something here might help.]("http://all-streaming-media.com/faq/recording-media-stream/faq-get-media-stream-URL.htm")
Might I ask why you are reluctant to use Firefox with the Flashgot plugin. I use the combination to download all flash movies. It has rarely failed me.I also use jDownloader in conjunction with Flashgot to be able to resume all downloads.

Edit: [Just found this]("http://ceicer.org/streamcapture/index_eng.php")....look to the bottom for Ubuntu version.

[And this.]("http://code.google.com/p/get-flash-videos/")

---

