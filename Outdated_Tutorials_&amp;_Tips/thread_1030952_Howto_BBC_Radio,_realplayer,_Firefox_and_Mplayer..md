---
title: "Howto: BBC Radio, realplayer, Firefox and Mplayer."
date: 2009-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by SilverWave on 2009-01-04
This is a howto to help anyone who has had problems trying to listen to various BBC Radio programs that are streamed in realplayer format.
______________________________

Linux x86_64
Ubuntu/8.10 (intrepid)
Firefox/3.0.5
______________________________


The default Firefox plugin "Totem Web Browser Plugin" is no good for this so I install mozilla-mplayer.

Install the following packages:
> 
mplayer
mozilla-mplayer
mplayer-fonts
mplayer-skin-blue
mplayer-skins

Restart Firefox and you should be good to go.

Here is a good place to test that its working:
[http://www.bbc.co.uk/radio4/history/inourtime/rams/inourtime_20060629.ram](http://www.bbc.co.uk/radio4/history/inourtime/rams/inourtime_20060629.ram)

If all goes well the mplayer plugin should, **after a pause**, start playing the episode regarding GALAXIES.

If not try typing...
```
 about:plugins
```
...in the address bar and check that it has been installed.


**BBC URL's**
[http://www.bbc.co.uk/radio4/history/inourtime/inourtime_archive_home.shtml](http://www.bbc.co.uk/radio4/history/inourtime/inourtime_archive_home.shtml)
[http://www.bbc.co.uk/radio4/](http://www.bbc.co.uk/radio4/)
**Useful URL's**
[http://computerperson.wordpress.com/2008/04/06/linux-sol-2-mplayer-af_inet6-error/](http://computerperson.wordpress.com/2008/04/06/linux-sol-2-mplayer-af_inet6-error/)
[https://answers.launchpad.net/ubuntu/+source/soundconverter/+question/49509](https://answers.launchpad.net/ubuntu/+source/soundconverter/+question/49509)

______________________________

**Tips:**
______________________________

**1. If you stop or pause a stream it will probably start again from the begining :(**
[B][U]
Workaround[/U][/B]
You can right click and "Copy URL" then paste this in mplayer direct to allow you to go to a particular time, its a bit of a pain but it does work... here is how:

The initial url is:

> [http://www.bbc.co.uk/radio4/history/inourtime/rams/inourtime_20060629.ram](http://www.bbc.co.uk/radio4/history/inourtime/rams/inourtime_20060629.ram)


This actual relates to:

> rtsp://rmv8.bbc.net.uk/radio4/history/inourtime/inourtime_20060629.ra?BBC-UID=7blah5608d0***1b74ec06c2718aa3f41f5blaha9040b1eaa4bbfa05e28115e4&SSO2-UID=

Remove all after .ra? like so:

> 
rtsp://rmv8.bbc.net.uk/radio4/history/inourtime/inourtime_20060629.ra?

Add your start time to the end of the url:

> 
rtsp://rmv8.bbc.net.uk/radio4/history/inourtime/inourtime_20060629.ra?start="20:39"

Now open mplayer up and right click "Open" > "play url" paste your link in and wait a couple of minutes.

If you get mplayer error: "Couldn't resolve name for AF_INET6" add... 

```
prefer-ipv4 = yes
```

...to the configuration file /etc/mplayer/mplayer.conf.

______________________________

**2. RA/RAM to MP3 conversion**
Based on Bhavani Shankar's post here:
[https://answers.launchpad.net/ubuntu/+source/soundconverter/+question/49509](https://answers.launchpad.net/ubuntu/+source/soundconverter/+question/49509)

> you can also use:

mplayer -dumpstream <stream>

to record streaming audio and video. The song will then be inside "stream.dump" (same format as the stream)

then use:
mplayer stream.dump -ao pcm:file=ripped_audio.wav

to convert to wav.

Then you can use Audacity (or similar) to convert to mp3 (/ogg).

Hope that helped & Good Luck!

---

### Post by SilverWave on 2009-01-09
**Here is a worked example of saving a realplayer stream to disk, then converting it to MP3 via the command line.**

**Prerequisites:**
1. You will need to install mplayer and lame.

2. You will need a temp folder to save the files to - the one used in this example is 
> /home/tmp/stream1

**Worked Example:**
Open a terminal up and enter the following:

> cd /home/tmp/stream1

> mplayer -dumpstream 'rtsp://rmv8.bbc.net.uk/radio4/science/sci9_thu_20040318.ra?start="0:32"&title="Cosmic_Ocean"&BBC-UID=4439968289dedb6879300a7b70f0971a4d7f75c670f021b4342f966f22250800&SSO2-UID='

> mplayer stream.dump -ao pcm:file=ripped_audio.wav

> lame --vbr-new ripped_audio.wav output_low.mp3

> 
lame -h -b 160 --vbr-new ripped_audio.wav output_high.mp3

**Note:**
To load mp3 on to my iPod I use...
> gtkpod

... which allows you to manage songs and playlists on your Apple iPod.

---

