---
title: "Ripping DVD takes over TWO DAYS!"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by fotoflex on 2013-03-18
Hi,
I started using Ubuntu 12.04 this week and tried to rip a dvd I made. (Red Nose Day)
It's a 4.7 GB disc, the program lasts 4 hours.
**51 hours** to rip in OGMRip, that's crazy!
I'm used to work in windows, Xilisoft ripper would take an hour or so.
I've searched the forum, but most info seems to be from 2010.
People there suggest Handbrake and K9, but how to install these, I don't understand.
I understand a bit of English, but not any technical terms, my toshiba P100-276 laptop speaks Dutch. :)

---

### Post by varunendra on 2013-03-18
> **fotoflex said:**
> **51 hours** to rip in OGMRip, that's crazy!
I'm used to work in windows, Xilisoft ripper would take an hour or so.

It may be a faulty track or some other error. I recently ripped a 4.7 GB DVD containing some non-standard tracks as well as standard ones, and it took less time than TVC on windows (besides, TVC's h264 encoding was crappy and out-of-sync as well).

What is the hardware configuration and which profile are you using to rip the DVD in OGMRip?
What is the codec that Xilisoft ripper used?

If it is using "High Quality PC (Quantizer 2, X264 + AAC)", then be aware that X264 is a much complex codec than others and as such, it will need much more time than traditional ones.

Typically, the x264 encoding needs about 3-4 times more time than a typical xvid encoding. But the difference you are reporting is simply too much to be called normal.

---

### Post by andrew.46 on 2013-03-18
If you mean ripping *and* transcoding a decent cpu can get the job done in less than an hour. I do it all manually in this time period:

[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

using an amd 8 core 8350 chip...

---

### Post by varunendra on 2013-03-18
> **andrew.46 said:**
> using an amd 8 core 8350 chip...

Umm.. that's a bit more than 'decent' IMHO :P

---

### Post by andrew.46 on 2013-03-18
> **varunendra said:**
> Umm.. that's a bit more than 'decent' IMHO :P

I guess so :). Mind you the chip itself does not cost all that much, in Australia about $200 and it works beautifully with FFmpeg / x264.

---

### Post by mastablasta on 2013-03-18
> **fotoflex said:**
> People there suggest Handbrake and K9, but how to install these, I don't understand.



open software center and search for handbrake. when you found it click install to install it. then you use it.
if it's not in software center then you can install it via PPA: [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)
PPA can be added via command line or you simply add them as software source in software center and then when you update the packages it will appear in software center.

as mentioned it is probably something to do with bad disk, bad reader or bad data.

---

### Post by fotoflex on 2013-03-18
Thanks all,

maybe I should have mentioned that I ripped a different disc before that.
[http://wikisend.com/download/536944/Schermafdruk](http://wikisend.com/download/536944/Schermafdruk) van 2013-03-18 18:24:12.png
A one hour program, took over 9 hours.
Had to do that twice, the first codec-setting had no sound.
The result is good, the same as I'm used to, and when you just let it run during the night, it's there the next day.
I don't mind that. :)
But over 2 days?
The external disc-player is fine.
So I'll try and install Handbrake via the software center, maybe that works.

---

### Post by papibe on 2013-03-18
I've done this to speed up the process: create an ISO image of the DVD on disk, and rip, using handbrake, from the ISO instead of the DVD itself.

Just a thought.
Regards.

---

### Post by fotoflex on 2013-03-18
Nice dog!

What should I use to create an ISO image?

---

### Post by Merrattic on 2013-03-18
How to create Image (ISO) files from CD/DVD

    e.g. Assumed that /dev/cdrom is the location of CD/DVD-ROM 

sudo umount /dev/cdrom

dd if=/dev/cdrom of=file.iso bs=1024

---

### Post by fotoflex on 2013-03-18
Thanks, but...

WHAT???

I have not worked with Ubuntu before,
I read somewhere that Android is based on Ubuntu, and I can work with that.
So I thought it would be a bit alike. 

Really, apart from the first line, that has no meaning for me. :(

---

### Post by MartyBuntu on 2013-03-18
So, what hardware do you have?

---

### Post by varunendra on 2013-03-18
> **fotoflex said:**
> Thanks, but...

WHAT???

I have not worked with Ubuntu before,
I read somewhere that Android is based on Ubuntu, and I can work with that.
So I thought it would be a bit alike. 

Really, apart from the first line, that has no meaning for me. :(

:P

Try "xfburn" from the program menu. I believe it has the option to create iso images of DVDs.

**PS:**
You may also take a look at "bombono". Can create new DVD (with new chapters) or its ISO using an existing one, or its folder structure.
Good for re-authoring, but involves some unnecessary steps in what you want to do.

---

### Post by fotoflex on 2013-03-18
I have a Toshiba P100-276, Xubuntu, 320GB HDD, 2GB Ram.

I record DVD's from a DVDRecorder, and copy the programs I want to keep.
Before, I used XilisoftDVDRip, set the begin- and end time, how big I wanted the file to be and some other settings like .MKV.
That would take about an Hour for a whole 4.7GB Disk.

As far as I can see, XFBurn does just burn.
Bombono is now running.

Thanks.

---

### Post by VeeDubb on 2013-03-18
Ignore all talk about your CPU.  Even if you ignore the fact that you're running a laptop and therefore can't upgrade your CPU short of buying a new computer, you do NOT need an 8 core CPU to rip and/or transcode.

If anything about that process is taking 57 hours, something is TERRIBLY wrong.

I strongly suspect that the issue is that you are selecting unreasonable or unrealistic settings because you're used to just telling it how big to make the file, and the program you're using now doesn't support that feature.

I would second the recommendation of HandBreak.  It's a very easy to use piece of software.  To start out, I'd select "High Profile" which you'll see when you have handbreak open, change the file type to .mkv, and just let it go at the default settings.  Once you see how your videos turn out and how large they turn out, you can tweak the settings from there to dial in what you want.

---

### Post by varunendra on 2013-03-19
> **VeeDubb said:**
> you're used to just telling it how big to make the file, and the program you're using now doesn't support that feature.
For the record, the OP was using OGMRip, and it does support that feature (defined size). :)

In fact it supports all three forms of transcoding - fixed size, fixes bit rate and fixed quantizer. There are existing profiles to do so in it, and new, custom profiles can be created or existing ones can be edited using custom parameters for codecs/formats. It has its own way of doing things, and can't be compared as better or worse than other applications.

As far as I have seen, it does beautifully what it is supposed to do. *(and I am frequently using OGMRip, OpenShot, AVIDemux and MKVtoolnix, besides Bombono, KDEnlive, GOPchop, WinFF and audacity, which I use only occasionally, as the need may be)*

Just clearing doubts. :)

---

### Post by fotoflex on 2013-03-19
Thanks VeeDubb,

I followed the link to Handbrake, but the explanation how to install I don't understand.
It seems similar to the commamd line in Windows, which has never worked for me.
Too many options to do something wrong, I suppose.

I won't blame my laptop, but things have always gone ' different' on it,
sometimes to baffle even the experts.
Now that I use Xubuntu, this does seem to continue.
F.I., when I reboot, my desktop background is gone.
When I then right-click on the desktop and then ' change background', it re-appears.
Typing this, I look up and see the second half of my sentence in another window, called; 'systeem-vereisten'. ( I don't know the translation for that.)
That kind of thing.

So, as I said, I hope I can somehow install XP.
Then the troubles I have are the troubles I'm used to. :)
 Sort of.

---

### Post by fotoflex on 2013-03-19
Thanks Varunendra.

I used the same settings as I was used to in Xilisoft, and the result was very much the same.
Even the file size of the end result was the same as comparable files ( epiosodes of Horizon) I made earlier.
Only, it took so long to extract them that I posted the question here.

---

### Post by varunendra on 2013-03-19
I wouldn't try to force any solution on you (that never works anyway ;)), but how much time it takes to just simple copy-paste the **VIDEO_TS** folder from the DVD to the hard disk ?

You may try to work on the folder instead with any application of your choice then.

For example, I recently got a problematic DVD (was very badly created) which no program could directly work on.
I extracted tracks with Bombono > saved individual tracks/chapters with it as separate DVD structures > loaded the structures on Open Shot and transcoded them to MP4 (x264, aac). Crude, but only a little bit longer and the end result was fantastic!

But of course it is a logically good choice to switch to windows if it fits your needs better. Besides, dual boot is always an option.

---

### Post by fotoflex on 2013-03-19
Thanks Varunendra.

Copy-paste straight from the DVD?
Just like a file?
I didn't know that worked, I thought you had to rip.
On the other hand, I did find out that simply changing the extention from .flv to .avi or so, sometimes works.
And that is a lot quicker, also.:)
In the meantime I've used Bombono to rip, that went very fast.
Oggconverter is now converting the file, will take four hours.
That's how long the dvd runs, so I guess they are watching while converting.
I'm found of .mkv, does Open Shot support that?

Multiboot, good idea!
My computer was too weak to really support *one* OS, let alone two,
but since my upgrade it has twice the ram and twice the disc space, so it should now be able do that.

---

### Post by varunendra on 2013-03-19
> **fotoflex said:**
> Copy-paste straight from the DVD?
Just like a file?
I didn't know that worked, I thought you had to rip.
Unless some big revelation is awaiting me, all I know is that DVD is a digital video standard, means a simple file that contains digital streams and so can be copied like any other normal file.

Ripping is necessary only when the source media contains analog stream, and that kind of ripping is a lossy process, since the digital data has to be 'converted' to some digital format in order to save it as a file.

> I'm found of .mkv, does Open Shot support that?
Unfortunately not.
But mkv is just a container, not a format itself. The audio/video stream in it can be of a wide variety of formats. The best quality HD rips that you can find on the net are nearly all **h264 + ac3/aac **videos, contained in either mkv or mp4 containers, and Openshot does support direct export to mp4 with your preferred combination of supported formats and custom settings with them if you want.

You can just export to mp4, then re-mux the file with MKVToolnix *(if you like mkv, you should take a close look on MKVToolnix anyway)*. It takes as much time as copying the file from one folder to another.

Alternatively, you can try OGMRip again on the copied dvd structure to see if it works any better. It does support direct export to mkv, saving the trouble of remuxing.

Yet another very rich alternative is AVIDemux, which does almost everything you want, but *sometimes* I have experienced AV sync issue with the exported files *(in fact it is a known issue with avidemux, not sure if it is fixed or not yet)*. Although it only happens when the source streams have some kind of problems (missing frames, variable bit rates, etc,). But Openshot handles the sync issue perfectly, so I prefer it over avidemux for transcoding.

> My computer was too weak to really support *one* OS, let alone two
Apart from disk space, nothing else is affected by keeping multiple OSes. As long as they are not booted into, they are just files lying around :)

**Bottomline,** if you are really into video transcoding, dedicate some time (in face a lot of time) with all available popular options in Linux. Post whatever questions that may arise in the process, and they'll surely get answered. In the end, you may actually like the Linux alternatives.

And I say that with my first 6-7 years of enthusiastic experience with Windows :) *(about 8 years being total experience with computers ;))*


**PS:**
Almost forgot, you can install and use **mediainfo gui** to get format/codec details of any audio/video file. You can compare the difference yourself or post here for others to analyse the difference to offer better suggestions.

---

### Post by fotoflex on 2013-03-21
ThanksVarun.

At the moment somebody is trying to re- install vidta to my laptop, so I can't try anything. If that succeeds, it would take the pressure off hving thimgs to work, and work straightaway.
This is written from a tablet, every browser and every website react differently to each other, so there is allways something that does not work right.

---

