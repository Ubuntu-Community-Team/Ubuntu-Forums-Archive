---
title: "HowTo: Download YouTube videos (the easy way)"
date: 2007-09-10
forum: Outdated Tutorials &amp; Tips
---

### Post by FRuMMaGe on 2007-09-10
Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

---

### Post by sad_iq on 2007-09-13
Here is a simple way also: Find the video you want to download...let's say this one here:[http://youtube.com/watch?v=2BCoZiSbGtY](http://youtube.com/watch?v=2BCoZiSbGtY)
You don't need to watch it or anything...then in the address bar on top of **ANY** browser put **kiss** in front of the youtube...so the address will be [http://**kiss**youtube.com/watch?v=2BCoZiSbGtY](http://**kiss**youtube.com/watch?v=2BCoZiSbGtY)
 That will take you to a page that will give you the preview of the video(like youtube) and a lot of links ...and one of them is Download Now (guess what it does :) )

---

### Post by Belinrahs on 2007-09-13
There are also a few services I've seen floating around, web-based, that grab the YouTube FLA file, and convert it to MPEG-4.

Google it..:popcorn:

---

### Post by bashologist on 2007-09-13
Cool, that's really neat, didn't know that.

Check out this nice bash script.
```
#!/bin/bash
flash=$(ls -t /tmp/Flash* | head -n 1)
destination=$(find ~/.mozilla -name sessionstore.js -exec sed 's/.*title:"\([^"]*\).*selected.*/\1/' {} \;)
echo "waiting for download to finish ..."
size=$(du $flash)
while sleep 5s; do
	if [ "$size" != "$(du $flash)" ]; then
		size=$(du $flash)
		continue
	else
		break
	fi
done
cp "$flash" "$HOME/${destination////%2f}.swf"

```
Load a YouTube web page, wait a few seconds, run it, then look in your home directory. n_n

---

### Post by capink on 2007-09-13
Another approach is to install firefox extension [unplug]("https://addons.mozilla.org/en-US/firefox/addon/2254"). This extension will give you download link to the youtube videos.

---

### Post by FRuMMaGe on 2007-09-13
> **Belinrahs said:**
> There are also a few services I've seen floating around, web-based, that grab the YouTube FLA file, and convert it to MPEG-4.

Google it..:popcorn:

These usuall take ages though.

I'm assuming people can convert the videos themselves if they see it necessary.

Personally, I use WinFF to convert all my videos.  You can also use to it convert to iPod format :P

---

### Post by qpieus on 2007-09-14
> **bashologist said:**
> Cool, that's really neat, didn't know that.

Check out this nice bash script.
```
#!/bin/bash
flash=$(ls -t /tmp/Flash* | head -n 1)
destination=$(find ~/.mozilla -name sessionstore.js -exec sed 's/.*title:"\([^"]*\).*selected.*/\1/' {} \;)
echo "waiting for download to finish ..."
size=$(du $flash)
while sleep 5s; do
	if [ "$size" != "$(du $flash)" ]; then
		size=$(du $flash)
		continue
	else
		break
	fi
done
cp "$flash" "$HOME/${destination////%2f}.swf"

```
Load a YouTube web page, wait a few seconds, run it, then look in your home directory. n_n

That's brilliant, thanks. I've been wanting to save a few youtube videos and this worked perfectly.

---

### Post by Kopfgeldjaeger on 2007-09-14
Have a look at [http://code.google.com/p/vdown/](http://code.google.com/p/vdown/) , too, it has a little GTK-GUI and downloads from many video portals (all supported by videograb.de), it saves the files with the original name of the video. You can also download video lists with it.

greetings

---

### Post by metroplex on 2007-09-15
I'd suggest installing the package "youtube-dl" available from the unverse repo. From a terminal:

[FONT="Courier New"]sudo apt-get install youtube-dl[/FONT]

Using the download-script is easy. Start a terminal, and type:

[FONT="Courier New"]youtube-dl <link to youtube video> [/FONT]

---

### Post by Steve1961 on 2007-09-15
There's also a firefox extension called download helper:

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by wersdaluv on 2007-09-15
That is AMAZING!

It even works for pages that youtube video downloaders can't download from like [http://youtube.com/watch?v=FhAdjEvyWEk](http://youtube.com/watch?v=FhAdjEvyWEk)

---

### Post by genbuntu on 2007-10-17
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

Wow man; this is really simple and simply great :)
does not require any software (as long as one is watching it on computer , no conversion needed)

---

### Post by fululian on 2007-11-18
thanks a bunch. i really don't d'like to know how many things like *these* i still am not aware of. *shudder

---

### Post by Kadrus on 2007-11-18
haha..pretty sweet stuff indeed :)..
There is also keepvid.com or something like this
You copy the link of the video into keepvid.com(there is an input to copy the link to)and you press download..and that's it:)

---

### Post by fululian on 2007-11-18
i let the vid complete downloading, switch to /temp, and get the flash-video copied onto the desktop. however, when i go back to firefox, the browser crashes if i cut-and-pasted the file. it seems you may only copy, not cut.

---

### Post by FRuMMaGe on 2007-11-18
> **fululian said:**
> i let the vid complete downloading, switch to /temp, and get the flash-video copied onto the desktop. however, when i go back to firefox, the browser crashes if i cut-and-pasted the file. it seems you may only copy, not cut.

I just drag it. Maybe firefox is looking for the file that no longer exists.

---

### Post by Co.Sinecure on 2007-11-19
FYI, youtube-dl has been updated (since youtube itself was updated and broke the old version!) 
Feisty repos have the ***old*** version. Don't know about gutsy.

Link is here [here]("http://ubuntuforums.org/showthread.php?t=540871") (provided by forum-user hyperair)

---

### Post by genbuntu on 2007-11-20
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

I wonder which temp directory to look for in 'Internet explorer' :confused:. Couldn't find it in 'temporary files'.

---

### Post by helpee on 2007-11-26
Oh, dear god. Thank you. THANK YOU.

---

### Post by Kopfgeldjaeger on 2007-11-27
I have written a little PyGTK video downloader (also commandline) for that; [http://code.google.com/p/vdown/](http://code.google.com/p/vdown/)
*promote*

I hope that's OK here :-)

Looks like that (also German):
[IMG]http://www.r4g.de/downloads/gvdown.png[/IMG]

---

### Post by murt on 2007-11-28
Tried your program, and it downloaded the flash video-file well, but when i used it (your command for ffmpeg) the output was an empty .avi-file.

---

### Post by linuxlizard on 2007-11-28
The EASIEST way-
just get the media pirate extension for firefox. Go to firefox-tools-extensions-add extension and get it.

---

### Post by Keith Hedger on 2007-11-28
I wrote the attached script to do it usage is ./dlv.sh LINK ie: ./dlv.sh [http://uk.youtube.com/watch?v=DsxJwqezf_w](http://uk.youtube.com/watch?v=DsxJwqezf_w) will download  hawkwind s chronical of the black sword to the current directory. I find its easier to keep a script updated than a full program for something this simple.

---

### Post by smacattack on 2007-11-28
personally i would suggest just doing:

sudo apt-get install youtube-dl

and then type:      youtube-dl <linkofvideo> in the terminal! easy enough.

---

### Post by Keith Hedger on 2007-11-28
Tried youtube-dl it dont work nor does the version i tried downloading from their site hence the script

---

### Post by maudy on 2007-11-29
Hi!
I used QtTube

[http://ubuntudicas.blogspot.com/2007/11/baixe-vdeos-do-youtube-com-o-qttube.html](http://ubuntudicas.blogspot.com/2007/11/baixe-vdeos-do-youtube-com-o-qttube.html)
(In portuguese) or:

[http://www.getdeb.net/app.php?name=QTTube](http://www.getdeb.net/app.php?name=QTTube)

Voilà!
Cya!!

---

### Post by computerfreak on 2008-01-20
> **metroplex said:**
> I'd suggest installing the package "youtube-dl" available from the unverse repo. From a terminal:

[FONT="Courier New"]sudo apt-get install youtube-dl[/FONT]

Using the download-script is easy. Start a terminal, and type:

[FONT="Courier New"]youtube-dl <link to youtube video> [/FONT]
Ok so I ran the termanal and downloaded the youtube.dl and i ran the thing to get the video, now where do i find it?:confused:

---

### Post by Anduu on 2008-01-20
> **Steve1961 said:**
> There's also a firefox extension called download helper:

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

This is the one I'm using forever...I haven't found a site yet it can't download from.

---

### Post by xinilux on 2008-01-25
Post removed by xinilux.

---

### Post by aonegodman on 2008-01-25
> **metroplex said:**
> I'd suggest installing the package "youtube-dl" available from the unverse repo. From a terminal:

[FONT="Courier New"]sudo apt-get install youtube-dl[/FONT]

Using the download-script is easy. Start a terminal, and type:

[FONT="Courier New"]youtube-dl <link to youtube video> [/FONT]

As you may already know youtube-dl is no longer working.  :(

Looking for fix or replacement now.

---

### Post by razorfish on 2008-02-01
[www.TubeLeecher.com](www.TubeLeecher.com). There is no easier way

---

### Post by becausetimtoldme on 2008-04-08
Are the .flv files "jumpy" for anyone else?  After I download the youtube video mplayer will not play it and when I play it in Kaffeine the video is jumpy and will not play smoothly.  The audio is perfect.

If anyone can suggest an alternative way that avoids this for a beginner I would appreciate this!

cheers

---

### Post by kiisu on 2008-04-22
Can anyone suggest a simple method for extracting just the audio from a downloaded youtube video?

I found a couple of programs suggested online, but they are windows only.

---

### Post by aonegodman on 2008-04-23
> **kiisu said:**
> Can anyone suggest a simple method for extracting just the audio from a downloaded youtube video?

I found a couple of programs suggested online, but they are windows only.

):P  ffmpeg

Check out the following link and you're good to go:

[http://justanothertechblog.blogspot.com/2007/02/easily-extract-audio-from-any-youtube.html](http://justanothertechblog.blogspot.com/2007/02/easily-extract-audio-from-any-youtube.html)


:KS

---

### Post by kiisu on 2008-04-24
I'm not sure I understand...

when I use this code in the terminal:
ffmpeg -i input.flv -f mp3 -vn -acodec copy output.mp3

how do I specify which/where the file is that I am using to get the audio?

I also tried the second method mentioned there (using mplayer) but got an error message about unknown syntax

alas!!

---

### Post by thewOndErEr57 on 2008-05-16
To let all you folks know, I have written a little software tool which uses youtube-dl with a GUI for those who don't like the command line.

It includes the opportunity to select which format you wish to download as and also stores the directory preference for your videos.

Find it at 

[http://yourtubedownloader.awardspace.com/]("http://yourtubedownloader.awardspace.com/")

Feedback most appreciated!

Thanks

---

### Post by ChameleonDave on 2008-05-26
I've just tried "sudo apt-get install clive".

Then you just have to type "clive" before a YouTube URL, and there you go!

Unfortunately, it can't download videos that have been marked as not suitable for minors by annoying morons.

---

### Post by puttux on 2008-05-26
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

this works great...theoretically this must work for all sites streaming video, not just youtube...thanks a lot...
 i used to go to the profile cache directory of firefox and cp the file that was last downloaded (ls -t)...

---

### Post by youtubemaniac on 2008-06-29
I use the new NetVideoHunter add-on to download videos and music not only from Youtube, but from any site:
[Download NetVideoHunter here]("http://netvideohunter.com")

---

### Post by robertchahine on 2008-06-29
you can add downloadhelper extension to your firefox, so when you watch a video you will use this extension to download the video.
And there's another way, or paste the link of the youtube video in this webpage
[www.tubeleecher.com](www.tubeleecher.com)

---

### Post by mickinator on 2008-06-30
That clive is a good program!!

---

### Post by dipayan on 2008-07-24
Hello everyone,
Found another easy way... use "www.savetube.com" or any other such website which provides you a download url for Youtube videos... 
1. Open the video you want to download in Youtube.

2. Open [www.savetube.com](www.savetube.com) in another browser window or tab.

3. Copy the url in the address bar.

4. Paste it in the space provided in savetube(type "&fmt=6" at the end of the url in the space for high quality .flv) and press go.

5. The savetube page will re-open showing a "Download" button. Press it and save the video where ever u want to.

6. As far as converting the file is concerned, just type ".mpg" at the end of the filename before or after downloading it. Example - "get_video.mpg".
       The .flv files don't seem to play with any of the players(Vlc, Totem...), but, the .mpg files play brilliantly well.

P.S- This method works great in Ubuntu 8.04LTS(Hardy Heron) and Opera 9.25.
Try it out and let me know...

---

### Post by ashleycurtis on 2008-07-24
Thanks for all the tips. Now I know how to download youtube videos in easy way. :)

---

### Post by thewOndErEr57 on 2008-07-25
I've actually written a GUI tool based on youtube-dl for those people who prefer GUI interfaces. It also allows you to download in a variety of formats, including the one required for IPOD video players.

Find it here:
[http://yourtubedownloader.awardspace.com/]("http://yourtubedownloader.awardspace.com/")

Let me know what you think by email if you wish !

---

### Post by MongooseCage on 2008-08-05
I prefer the first way... I was checking if anyone else found it... feel sorry for windows users... they rely on websites to do what we do by just opening the /tmp and taking out the video.

---

### Post by extremizt on 2009-03-12
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!
The method you have mentioned here was working fine for me, for years. But now, when i try playing the copied files, i am getting the error "cannot recoganise undf file format". Any ideas? What is this undf file format afterall?:-(
Thanks in advance

---

### Post by breese on 2009-03-24
Works perfectly: very easy method.  Thanks!

> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

---

### Post by blackrosezy on 2009-03-26
I also found easy way.I'm using Morz Video Downloader.Good and easy to use. you can download at [morzsoftware.com/morz-video-downloader]("http://morzsoftware.com/morz-video-downloader")

---

### Post by darksideforge on 2009-03-29
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

This worked PERFECTLY for me! Thanks!!

---

### Post by Clueless163 on 2009-03-31
I noticed that my audio/video is off when I am playing a copied video from youtube using the temp files method...any idea's?

---

### Post by timjumpshigh on 2009-04-16
is it legal to download them like the first writer?

---

### Post by aL3xandar on 2009-05-05
Well, I've managed to write a lil' script that uses youtube-dl to catch videos from youtube. Hope you'll enjoy it!

---

### Post by SPARTAN-118 on 2009-06-29
> **sad_iq said:**
> Here is a simple way also: Find the video you want to download...let's say this one here:[http://youtube.com/watch?v=2BCoZiSbGtY](http://youtube.com/watch?v=2BCoZiSbGtY)
You don't need to watch it or anything...then in the address bar on top of **ANY** browser put **kiss** in front of the youtube...so the address will be [http://**kiss**youtube.com/watch?v=2BCoZiSbGtY]("http://%3Cb%3Ekiss%3C/b%3Eyoutube.com/watch?v=2BCoZiSbGtY")
 That will take you to a page that will give you the preview of the video(like youtube) and a lot of links ...and one of them is Download Now (guess what it does :) )

Yeah, but some videos are too large to download this way (for example, Weird Al Yankovic's "Trapped in the Drive-Thru" is about 11 minutes long and you get THIS error:

The requested URL /get_video... is too large to process.  

This has happened to me on a number of occasions, from Halo 3 Montages to Sonic X episode parts (the good Japanese subbed ones, not the crappy North American english ones).

Also, the same error message kinda ruins the magic, since it shows that Kissyoutube uses Google Video to download the file.

---

### Post by SPARTAN-118 on 2009-06-30
Sorry for the double post, but here's a good [online] service that allows you to download Youtube videos:
[http://www.youtubecatcher.com/](http://www.youtubecatcher.com/)

Whatever you do, [SIZE=5]***DON'T DOWNLOAD THE TOOLBAR!!!!!***[/SIZE]
Even if you have WINE, since it totally screwed up my computer (I couldn't get into any Internet-related programs, and had to back up my files to Windows and re-install Ubuntu - again!)

SPARTAN-118

---

### Post by John Private on 2009-06-30
For me the easiest of all ways was [http://file2hd.com/](http://file2hd.com/) put in the Video Link of your choice and then mark movies and click "Get Files" then right click the one that says (Youtube Video Name).mp4 and right click and click Save Link As Download it and it is fast and downloads as mp4.

---

### Post by SVEN1 on 2009-07-01
> **John Private said:**
> For me the easiest of all ways was [http://file2hd.com/](http://file2hd.com/) put in the Video Link of your choice and then mark movies and click "Get Files" then right click the one that says (Youtube Video Name).mp4 and right click and click Save Link As Download it and it is fast and downloads as mp4.

Wow!! Works great with Ubuntu 8.10
Been trying to use many of those downloadable programs off the web when running windows, nothing really worked well.

It's been about 5 months now running Ubuntu, love it, no need for Windows any longer.

---

### Post by Suranjit on 2009-07-01
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

>> Thanks Dude...

---

### Post by ontadimanamana on 2009-07-01
i always use _keepvid.com_
or opera browser

---

### Post by SPARTAN-118 on 2009-07-02
> **ontadimanamana said:**
> i always use _keepvid.com_
or opera browser

KeepVid didn't work AT ALL for me...

In windows, I used altervista's Youtube Downloader (worked really well, but didn't always get the HQ video).

Now, I either use Youtube Grabber, or, if that doesn't work, some other online service.

I wonder why Ubuntu hasn't gone mainstream yet?
Oh yeah, plenty of reasons:

1. It's free.
2. If more people knew about Ubuntu, then they'd probably make viruses for it.
3. It requires at least some knowledge of using the command line interface (I was just starting to learn how to use applications like Terminal; I still am).

---

### Post by bgiannes on 2009-07-02
I've been using clive for sometime, you can setup login to download any video from youtube.

Q:
just found a program called addy it's a gui for clive

[http://code.google.com/p/abby/](http://code.google.com/p/abby/)

can this be install/port it into ubuntu, can someone have a look at it, please. 

thanx

---

### Post by SPARTAN-118 on 2009-07-02
Alright, I'll tell everyone the easiest way to download Youtube videos.

Just use FRuMMaGE's technique: 


[LIST=1]
[*]Load a video (doesn't even have to be a Youtube video - it can be from any website that uses flash; in fact, I use it to get around paying for a service that lets you download animes.)
[*]Minimize the browser.
[*]Go to your temporary directory (located - for most people - in your Filesystem(/) it's the folder "tmp"
[*]Locate the flash file (It'll start with "Flash" and be an alphanumeric string after that. BE WARNED: sometimes flash ads end up in this directory, so be sure it's the right file).
[*]Rename it to what you like (this can also be step 6).
[*]Drag it to your desktop or another folder (this can also be step 5).
[/LIST]

[LIST]
[*] Note: If you drag the file to a folder in another OS installed on your computer (ex. Windows), you may want to delete the flash file, if you plan on using it only in Windows (for example, if you just want the file to edit in Windows Movie Maker). Remember, Ubuntu can see files on Windows, but not the other way around! ;)
[/LIST]

---

### Post by cz8 on 2009-07-25
I followed your steps, but there is no flash file in my tmp folder.

---

### Post by ssdt on 2009-07-25
Really nice trick but by default there is Firefox and with the help of some addons, you could do the same.

---

### Post by SPARTAN-118 on 2009-07-25
> **cz8 said:**
> I followed your steps, but there is no flash file in my tmp folder.

Are you using Firefox?

Do you *minimize* the browser? (closing it deletes tmp.)

Do you wait for the video to *fully* load? (It helps you let the video play, then just pause it.)

Do you wait for the file to fully finish transferring into your tmp folder? (You'll know it's done when you can see a media preview as the icon.)

Also, when you browse the tmp folder, are there any files without an extension? Whose size keeps increasing?
Those are the files you're looking for.

I'll attach a screenie of what a Flash file looks like.

SPARTAN-118

---

### Post by SPARTAN-118 on 2009-07-25
> **ssdt said:**
> Really nice trick but by default there is Firefox and with the help of some addons, you could do the same.

Yeah, but I prefer to keep my addons to a minimum; 
download toolbar and autopager are good enough for me! (most of the time, anyways....)

---

### Post by yvan232002 on 2009-07-28
Thank you so much for the tip & best wishes

---

### Post by Tclarkie on 2009-07-29
install the addon "Easy Youtube Downloader" from the firefox addon pages

---

### Post by Anxious Nut on 2009-07-29
> **Steve1961 said:**
> There's also a firefox extension called download helper:

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)
+1 It can download any video stream

BTW if you watched any video you'll find it as .flv in your tmp folder, you can copy it to keep it. to go to tmp, here's the path: /tmp/

---

### Post by pixy84 on 2009-08-25
[Here]("http://www.idesktop.tv/") is a link to a wonderful website where you can download YouTube videos in a variety of formats for FREE!

[http://www.idesktop.tv/](http://www.idesktop.tv/)

---

### Post by nesh87 on 2009-08-27
If you guys are still looking/interested to try something new:

[http://ubuntuforums.org/showpost.php?p=7545745&postcount=1](http://ubuntuforums.org/showpost.php?p=7545745&postcount=1)

[http://ubuntube.tk/](http://ubuntube.tk/)

---

### Post by kyle2595 on 2009-08-29
There is also a Firefox extension called "Media Converter". It downloads videos and converts them to whatever file type that you would like. [http://www.mediaconverter.org/](http://www.mediaconverter.org/)

---

### Post by phar0z on 2009-09-14
I've written a script that downloads music from youtube and converts it automatically to mp3.

```
#!/bin/bash
#By: phar0z
# checking whether you have youtube-dl
if [ ! -x `which youtube-dl`  ];then
echo “Error! youtube-dl isn’t installed.”
exit 0
fi

#checking whether you have vbrfix
if [ ! -x `which vbrfix`  ];then
echo “Error! vbrfix isn’t installed.”
exit 0
fi

#download video(s)
for URL in $*; do
youtube-dl -t “$1&fmt=18&#8243;
done

#process
for VIDEO in `ls *.flv`; do
OUTPUT=${VIDEO:0:${#VIDEO}-4}”.mp3&#8243;
ffmpeg -i $VIDEO -acodec copy $OUTPUT
#move video
mv $OUTPUT /home/$USER/music
vbrfix /home/$USER/music/$OUTPUT /home/$USER/music/$OUTPUT
rm -rf vbrfix.log vbrfix.tmp
#clean-up
rm -rf $VIDEO
done
echo “Done.”
```

[Here you can read my explanation]("http://phar0z.wordpress.com/2009/09/03/11/").

---

### Post by rs.smith on 2009-09-23
Go to [http://www.youtubevdl.110mb.com](http://www.youtubevdl.110mb.com). 
 
it offers live preview of the video you are going to download. offers multiple formats of videos like, .flv,.3gp,.mp4(HD) ,etc. to download.

---

### Post by blaselinux on 2009-09-24
Here is my script. If you need only the sound in mp3 this will help you:

If you would like to use this script you need:
[LIST]
[*]youtube-dl
[*]mencoder
[/LIST]

```
sudo apt-get install youtube-dl mencoder
```

```
#!/bin/bash

# Set the download variable to the working directory
download=$HOME/youtube

# Check the working directory; exist or not, if not the script make it
if [ ! -e $download ]
    then
	mkdir $download
	echo "The $download directory is created" 
fi

if [ ! -e $download/flv ]
    then
	mkdir $download/flv
	echo "The $download/flv directory is created" 
fi

# Go to the working directory
cd $download


if [ $# == 1 ]
    then
	wget $1
	nev=`cat watch* | grep "<title>" | awk -F">" '{print $2}' | awk -F"<" '{print $1}'`
	nev=`echo $nev | sed 's/ /_/g'`
	rm watch*
    elif [ $# -ne 2 ]
	then
	    echo -e "\n You need to use the following parameters \n"
	    echo -e " youtube.sh [url] [the video name]"
	    echo -e " You can leave the [video name], this time you get the original youtube video name. \n"
	    exit
	else
		nev=$2
fi

echo "Start the download"

# Download the video
youtube-dl $1

echo "The video is downloaded" 

# Set the video variable
video=`echo $1 | awk -F= '{print $2 }'`

# Set the zene variable
zene=`echo $nev | awk -F. '{print $1}'`.mp3

echo "Start the convert"

# Convert the flv file to mp3
mencoder $video.flv -of rawaudio -oac copy -ovc copy -o $zene

echo "The mp3 is ready"

video=`echo $zene | awk -F. '{print $1}'`.flv

# Rename the flv file
mv *.flv $video

# Move the flv file to the flv directory
mv $video $download/flv/

echo "The script ran succesfully"
```

You can download the script from [here]("http://linuxegyszeruen.homelinux.org/request.php?41"), but in the downloaded script, the echoes are in hungarian language, the comments are in english.

After you type in (or download) the script, don't forget about the permission:
```
chmod +x youtube.sh
```

Enjoy! ;)

---

### Post by rahulkundu4u on 2009-10-08
It is very easy way to download YouTube video with Downloadhelper add-ons.
When a page with youtube video is opened Downloaderhelper in Navigation 
toolbar rotetes and from this video can be downloaded.

---

### Post by kiridude on 2009-10-08
Nice one FRuMMaGe !

simple and effective!

---

### Post by kevinguillorytraining on 2009-10-09
A great working tip. can we download videos from other sites too with this trick?

---

### Post by Onforty on 2009-10-09
You can also embed it in a HTML file :biggrin:

---

### Post by Jugantor on 2009-10-24
simple, easy and best! Thumbs up:guitar:

> **metroplex said:**
> I'd suggest installing the package "youtube-dl" available from the unverse repo. From a terminal:

[FONT=Courier New]sudo apt-get install youtube-dl[/FONT]

Using the download-script is easy. Start a terminal, and type:

[FONT=Courier New]youtube-dl <link to youtube video> [/FONT]

---

### Post by smileyguy on 2009-10-28
That's fantastic Frummage. Works a treat!

Too easy:)

---

### Post by sandwicheguy on 2009-10-30
>Here is the easy way.
>Enjoy!

You Rock! So simple, so quick, so obvious... So Elegant!
THANK YOU for a good start on the weekend.

---

### Post by Marrkk on 2009-10-31
Video download helper is tidiest IMO
first, install ffmpeg or ffmpeg

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

- an  new browser icon rotates when a flash stream is downloadable,
so click it, select flv or HQ  or MP3
finished.


even better though, u can set it in preferences to dload, save and convert in one press.

it will auto convert as wmv mpg mp4 avi or even mp3.
They save in /home/dwhelper .a true must have.  really try it. disable the twitter and mp3tunes and stuff. soooo easy.

---

### Post by alienclone on 2009-10-31
dont know if it was mentioned already (too tired to read all 9 pages) but in FF you can go to Tools>Page Info>Media  and see all images and videos on the current page and download them.

---

### Post by vratnica on 2009-11-02
> it will auto convert as wmv mpg mp4 avi or even mp3

I never get it converted this way, it doesn't work

---

### Post by Dan Again on 2009-11-10
The original method described by the topic works great for me...awesome! Thanks!

---

### Post by SashaShveik on 2009-11-20
[JDownloader]("http://jdownloader.org/")
Support download from RapidShare.com, RapidShare.de, Depositfiles.com, Filefactory.com, Uploaded.to, Megaupload.com, Megashares.com, Vip-file.com, upshare.net, Youtube.com, Myvideo.de, Imagefap.com and many other...

---

### Post by MIJ-VI on 2009-11-23
> **Steve1961 said:**
> There's also a firefox extension called download helper:

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)


Houston, we have a problem:

**Reviews**

                                           ** **

                     Nice addon, very useful.
Great work.

No problem with Firefox 3.5.5 and windows 7.
                                     Rated 5 out of 5 stars                     by [Prezio67]("https://addons.mozilla.org/en-US/firefox/user/3591296") on November 22, 2009          
         
                                      ** **

                     Best addon available. This should absolutely be standard for every web browser. Never get frustrated by glitchy streaming video again - just download it all and watch at your leisure! If I wasn't a student living well below the poverty line I would donate some cash to these guys - well done gents and a heartfelt thank you!
                                     Rated 5 out of 5 stars                     by [snaqpak]("https://addons.mozilla.org/en-US/firefox/user/5031594") on November 22, 2009          
         
                                      ** **

                     Pro's: Easy to use, fast, stable and free video downloaded.

Con's: _**Installs Trojan.Goldun**_, which isn't particularly harmful Trojan and a small price to pay for this great product.
                                     Rated 4 out of 5 stars                     by [Lobomoon]("https://addons.mozilla.org/en-US/firefox/user/5031478") on November 22, 2009 



--------


**Trojan.Goldun**

 **Discovered: **January 7, 2005
  **Updated: **February 13, 2007 12:31:36 PM
  **Also Known As: **Trojan-Dropper.Win32.Agent.dz 
  **Type: **Trojan Horse
  **Systems Affected: **Windows 2000, Windows 95, Windows 98, Windows Me, Windows NT, Windows Server 2003, Windows XP. EDIT: :P

 
Trojan.Goldun is a Trojan horse program that steals user's authentication for e-gold.

[http://support.brightmail.com/security_response/writeup.jsp?docid=2005-010715-5330-99](http://support.brightmail.com/security_response/writeup.jsp?docid=2005-010715-5330-99)

---

### Post by MIJ-VI on 2009-11-23
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!

+1

And if I may add, bookmark the tmp folder (in Nautilus, not Firefox) so that it's easy to access.

---

### Post by J V on 2009-11-23
Thats nice, but is there any way to save videos forced to open in totem? (Stupid divx)

Totem doesn't save them to the /tmp directory, so you're stuck with watching streamed version (And because totem is crap with streaming theres no DL-indicator, seeker, or even pause available...)

Does totem have its own /tmp?

---

### Post by Guitar John on 2009-11-23
Thank you.  

This worked great.  And yes, it was the easy way.

---

### Post by Nagulan on 2009-11-25
hi i  am nagulan i am kubuntu new user. i need to installed the softwares.

i can't install the youtube down loader. but i download the youtube down loader software. onece i down load the file but i can't install. once i click it's opening open with format

---

### Post by AlexanderDGreat on 2010-01-20
Download YouTube the Easy Way -- works! Tried it on Karmic and FF 3.5

Make everything simple, but not simpler. -Albert Einstein.

---

### Post by jamorod on 2010-01-21
Both the /tmp file method and the DownloadHelper addon worked fine for me. Thank you!

---

### Post by karthick87 on 2010-01-21
This script works  for me,thanks a lot..And similarly is there any bash script to get flash files from a website???

---

### Post by Scythium on 2010-01-22
Is it possible to get streams from grooveshark.com?

---

### Post by ilia on 2010-02-04
The best *command line* tool to download videos is **cclive** (note the double c! It's not the same as clive!). Packages are only available for Lucid at [http://packages.ubuntu.com/lucid/cclive](http://packages.ubuntu.com/lucid/cclive) but can be easily installed in Karmic. I personally use prevu tool to rebuild it for karmic:
```
prevu cclive/lucid
```
There is also PPA somewhere and, of course, sources at [http://code.google.com/p/cclive/](http://code.google.com/p/cclive/)
For best experience put the following into **~/.ccliverc**
```
filename-format = "%t.%s"
format = "best"
stream-exec = "mplayer -really-quiet %i"

```
Download video:
```
cclive VIDEO_PAGE_LINK
```
Start downloading video and call mplayer to watch it when download reaches 20%
```
cclive --stream=20 VIDEO_PAGE_LINK
```

The following sites are supported by cclive: youtube.com, video.google., break.com, evisor.tv, sevenload.com, liveleak.com, dailymotion., vimeo.com, golem.de, clipfish.de, funnyhub.com, myubo.com, cctv.com, ehrensenf.de, spiegel.de, redtube.com, youjizz.com, xvideos.com, tube8.com

For more info read **man cclive**. There is also a GUI for cclive called abby but I don't use it.

---

### Post by Norwal on 2010-02-08
WoW that was easy.

Thanks:popcorn:

---

### Post by ikt on 2010-02-08
I've got a bit of a guide for download high definition videos from youtube: [http://ikt.id.au/?p=45](http://ikt.id.au/?p=45)

---

### Post by arunbio on 2010-02-14
Step 1:Download-Google Chrome Web Browser and install,Follow link
[http://www.google.com/chrome](http://www.google.com/chrome)
Step 2:Download Youtube Files using Google Chrome,below links will help You
[http://www.chromefans.org/chrome-plugins/download-youtube-videos-movies-in-google-chrome](http://www.chromefans.org/chrome-plugins/download-youtube-videos-movies-in-google-chrome)
Step 3:You can enjoy flv file using vlc Player of ubuntu

Best of Luck

Arun K S,Koothali:popcorn:

---

### Post by sndppm on 2010-02-15
> **arunbio said:**
> Step 1:Download-Google Chrome Web Browser and install
Step 2:Download Youtube Files using Google Chrome,below links will help You
[http://www.chromefans.org/chrome-plugins/download-youtube-videos-movies-in-google-chrome](http://www.chromefans.org/chrome-plugins/download-youtube-videos-movies-in-google-chrome)
Step 3:You can enjoy flv file using vlc Player of ubuntu

Best of Luck

Arun K S,Koothali:popcorn:
:p Thanku arun. Its working............
                                                    Sandeep

---

### Post by LintonHanes on 2010-02-18
keepvid.com was great until I learnt this and (in firefox) about:cache
I rename the shockwave files there to 'name.flv' and drag then to /Videos

See the point of this howto is that it'll work on 'any' site you'd find at videosurf.com, not just youtube right?

---

### Post by Arkapravo on 2010-02-19
> **FRuMMaGe said:**
> Many people have been asking how to download youtube videos, and kept being pointed to useless software which will do it for them.

Here is the easy way:

Step 1: Find the video you want to download and wait for it to completely finish loading.

Step 2: Minimize your browser (do NOT close it, some browsers delete the temp directory upon closing), and navigate to the directory /tmp

Step 3: Drag the flash file onto your desktop. Voila!

This definitely works with firefox, and probably most other browsers aswell. Enjoy!
Yep ! ...... that works as a dream !

---

### Post by littlepeon on 2010-02-20
hey
firefox has a handfull of youtube download extensions...the one i've used the most and it works correctly is netvideo hunter

[HTML]https://addons.mozilla.org/en-US/firefox/addon/7447[/HTML]it seems to work with most sites....and is stable...

have fun
-Peon

---

### Post by henrodon on 2010-02-21
Works in Chrome too. Thanks for the tip.

---

### Post by penguinv on 2010-04-02
> **Arkapravo said:**
> Yep ! ...... that works as a dream 


---- oops I meant to QUOTE "the method of looking in the /tmp directory and picking out the file". sounded so easy.!

Your dream not mine. My /tmp has a number of FOLDERS for instance;
hersperfdata_myname 1kyg|L orbit-gdm orbit-myname 
and the list goes on and on.

I am using Ubuntu 9.10

Please help me download this video.

The kiss method gave me a page but no "Download Now" link. There are two maybe download links, One is an uparrow and the other is an HQ
and it informs me that it will download in some ?? format called FLV for which I can also download a video player and a video converter (your guess what-to-what.
Gets messier and messier.

In addition, there is a firefox add-on called unplug that looks suspiciously like it (only?) works on Windows.
This is now 2010 and Ubuntu 9.10 so please someone who knows, tell us the status today.

I appreciate all your work and others, as well as I, will appreciate an up to date plan.


And while you are waiting.....   :popcorn:

---

### Post by maghoxfr on 2010-04-04
FLV is Flash video, get VLC player and you can play it without problem. If you want to encode the video to a different format handbrake will suffice.
For the easy questions such as video formats and so on you can look them up on google or wikipedia.

---

### Post by isbiyanto on 2010-04-15
> **sad_iq said:**
> Here is a simple way also: Find the video you want to download...let's say this one here:[http://youtube.com/watch?v=2BCoZiSbGtY](http://youtube.com/watch?v=2BCoZiSbGtY)
You don't need to watch it or anything...then in the address bar on top of **ANY** browser put **kiss** in front of the youtube...so the address will be [http://**kiss**youtube.com/watch?v=2BCoZiSbGtY]("http://%3Cb%3Ekiss%3C/b%3Eyoutube.com/watch?v=2BCoZiSbGtY")
 That will take you to a page that will give you the preview of the video(like youtube) and a lot of links ...and one of them is Download Now (guess what it does :) )

It's work for me.
thanks for all, nice info. :)
sample: [http://www.kissyoutube.com/watch?v=CKMOMQo035M](http://www.kissyoutube.com/watch?v=CKMOMQo035M)

---

### Post by isbiyanto on 2010-04-15
can i save file in *.mp3 or *.mp4?

---

### Post by maddg3241 on 2010-04-15
[https://addons.mozilla.org/en-US/firefox/addon/13990]("https://addons.mozilla.org/en-US/firefox/addon/13990") i use this it does a great job or sometimes i use this but it does not always work [http://www.youtubedroid.com]("http://www.youtubedroid.com")

---

### Post by jetta on 2010-04-17
> **metroplex said:**
> I'd suggest installing the package "youtube-dl" available from the unverse repo. From a terminal:

[FONT="Courier New"]sudo apt-get install youtube-dl[/FONT]

Using the download-script is easy. Start a terminal, and type:

[FONT="Courier New"]youtube-dl <link to youtube video> [/FONT]

hey thanks, this method works for me (for now).

---

### Post by ardneb on 2010-04-17
thanks metroplex

---

### Post by hxcobd on 2010-04-17
I'm sure someone has mentioned this at some point in this thread, but DownloadHelper supports every flash video site I've ever visited, and has quite literally never failed me.

[http://www.downloadhelper.net/](http://www.downloadhelper.net/)

Much more straightforward than the /tmp file technique.

---

### Post by d3v1150m471c on 2010-04-17
the easiest way to download youtube videos is with the firefox addon "unplug". you can score a lot of free pr0n with it, too.

---

### Post by warrior_juggalo on 2010-04-18
It makes you think, These people who make software for this sort of thing, Why did they not think of this?

And i mean, I'd rather this than a download link, That way you can stream it too and it does not take any more of your bandwidth.

---

### Post by lisati on 2010-04-18
Thread closed: see [here]("http://ubuntuforums.org/showthread.php?t=1429211")

---

