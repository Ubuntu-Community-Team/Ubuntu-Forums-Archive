---
title: "[SOLVED] help with saving a radio interview"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Jay Car on 2008-07-08
This morning a friend called to say she is being interviewed
on a radio show this afternoon, she wanted to know if I could
record her interview (it will run about 30 minutes).

I told her I would try. She's a Windows user, and this sounded 
like a fun opportunity to show my Ubuntu system off a bit. 

But over the last two hours I've not been able to figure 
out how to do a simple recording of an audio stream.

Here's the station URL [http://www.healthylife.net/](http://www.healthylife.net/)

I did get the station to show in Streamtuner, and have
Streamripper installed from the repository.  After pointing
to the URL and hitting "Record", it LOOKS like it's recording:

A terminal window opens with this text:

prefs_fn = /home/jcar/.config/streamripper/streamripper.ini
Connecting...
stream: Streamripper_rips
server name: Microsoft-IIS/6.0
bitrate: 0
meta interval: -1

So, something is working somewhere (Maybe?).  But...

**a)** what does the "meta interval" mean?  Is it only recording in small chunks, rather than one long stream, if so, can it be changed? 

**b)** where is the audio file being recorded to? How do I find it to replay it later?

**c)** what format is it recording to? is there a way to specify saving it as an ogg file (I can't seem to find a "save as" option)?  

**d)** The "Record" button is easy to see...but where's the "Stop" button?

I feel like I'm making progress (ever the optimist, ain't I?) :)
but I only have about two more hours to figure this out (gulp).
It isn't a tragic thing if I don't get the recording, but it 
would sure be fun to be able to save the interview for her.  

Am I on the right track?

---

### Post by dca on 2008-07-08
bitrate: 0
 
is not a good indicator...
 
Did you use this how-to?
 
[http://lifehacker.com/software/linux-tip/record-streaming-radio-with-streamripper-and-streamtuner-263493.php](http://lifehacker.com/software/linux-tip/record-streaming-radio-with-streamripper-and-streamtuner-263493.php)

---

### Post by Jay Car on 2008-07-08
Uh oh...

It just occured to me that my questions about recording streaming audio might not be appropriate for the Ubuntu 
support forum, since it's really not an Ubuntu problem. 

I'm afraid I'm just so used to running here for help that
I wasn't thinking. Sorry for that.

So, if help is offered, I will be very appreciative, but if 
this post needs to be sent elsewhere, I understand. 

Jay Car

---

### Post by Jay Car on 2008-07-08
Wow, dca!  That was fast!

Yes, I did follow that how-to...that's how I got as far as I did.  It all sounded so easy, but I'm struggling to get it to work.  I also read through the Streamripper forums and got a little discouraged. 

I'm curious, there's a little "Sound Recorder" in my program list. It looks dead-simple. I assumed it would record whatever was playing through my sound card, but so far it hasn't worked either.  

Then I tried VLC, but just got more confused trying to figure out the settings.  I followed a "How-To" for that one too. 

Is there a simpler way to just grab 30 minutes of streaming audio?

---

### Post by dca on 2008-07-08
The only other app  that may help is Audacity...  There have been threads in the past where certain radio streams were not able to be recorded because of RIAA piracy...
 
Audactity used to be the way to record what was playing through your speakers, haven't used it in yeaaarrrsss...  Made a great laptop-based four track recorder if you're into playing music with a band...

---

### Post by kostkon on 2008-07-08
> **Jay Car said:**
> Wow, dca!  That was fast!

Yes, I did follow that how-to...that's how I got as far as I did.  It all sounded so easy, but I'm struggling to get it to work.  I also read through the Streamripper forums and got a little discouraged. 

I'm curious, there's a little "Sound Recorder" in my program list. It looks dead-simple. I assumed it would record whatever was playing through my sound card, but so far it hasn't worked either.  

Then I tried VLC, but just got more confused trying to figure out the settings.  I followed a "How-To" for that one too. 

Is there a simpler way to just grab 30 minutes of streaming audio?
You could try *Mplayer*. 

I assume it is a *Windows Media* audio stream and thus *Streamripper* cannot save it (I think it supports only MP3 and maybe OGG streams).

---

### Post by Nopposan on 2008-07-08
Well, unfortunately  I'm not at my Ubuntu desktop right now; XP in a conference room at work.  But, just open your package manager, probably Synaptic, and search for software to install using a text string like "mp3 stream recorder".  You'll find something; I did, but I'm not sure what it was called.  I think it's called icecream.  Ooh, yeah, that's it.  Quickly, I'll Google up a link for you . . . Here it is:
[http://icecream.sourceforge.net/](http://icecream.sourceforge.net/)

It's command-line software, but it's very easy to use; just read the help page by typing "icecream --help" at the command prompt.

BTW, you might want to check your basic audio set up too.

Cheers.

---

### Post by neilg4rqn on 2008-07-08
Hi, to do what you want and produce a file you can play back. Here is what I do.
Check that you have the MPlayer plugin in Firefox (this was my cure to recording a local radio station).
Use Sound Recorder to record the audio.
It may not work out as simple as that and some fiddling with the audio setup you have may be required, but try that for starters.
I could never get Audacity to record but I use it as the recorded sound is a little quiet and Audacity is good for boosting the volume of the recorded sound file.
I have just tried that on the station you mention and it worked just fine.
Stay cool.
Neil

---

### Post by kostkon on 2008-07-08
> **Jay Car said:**
> Wow, dca!  That was fast!

Yes, I did follow that how-to...that's how I got as far as I did.  It all sounded so easy, but I'm struggling to get it to work.  I also read through the Streamripper forums and got a little discouraged. 

I'm curious, there's a little "Sound Recorder" in my program list. It looks dead-simple. I assumed it would record whatever was playing through my sound card, but so far it hasn't worked either.  

Then I tried VLC, but just got more confused trying to figure out the settings.  I followed a "How-To" for that one too. 

Is there a simpler way to just grab 30 minutes of streaming audio?
Yes, indeed you could also try record it using a sound recorder application, if you are using *PulseAudio*. Check at the end of [this how-to page]("https://wiki.ubuntu.com/PulseAudio") for a way to record it using *Audacity*.

---

### Post by Jay Car on 2008-07-08
> There have been threads in the past where certain radio streams were not able to be recorded because of RIAA piracy...

I don't think the radio station has a policy against recording. They even advertise a software for sale that makes recording streaming audio easy, but It's Windows only. 

I'll go take a look at MPlayer. 
Thanks to both of you for responding so fast!

:)

---

### Post by Jay Car on 2008-07-08
neilg4rqn, I have the mplayer plugin for firefox, opening the "Sound Recorder" where it says "Record from input" there are several choices:  Digital, Capture, IEC958, and Mic Boost...

I've tried all but the Mic boost.  It even makes an ogg file, but when I play it back it's just silent.

I have an hour left.  I'm going to try the icecream. Just got it from the repository...

Even if I don't get the interview recorded I will have sure learned a lot this morning.

---

### Post by Jay Car on 2008-07-08
Okay, here are the examples for recording streaming audio (from the icecream manual)

streaming to mpg123
    icecream --stdout [http://radio.com/playlist.pls](http://radio.com/playlist.pls) | mpg123 - 

split stream into different tracks
    icecream -t [http://metal.org/radio.pls](http://metal.org/radio.pls) 

split stream into tracks and play with vlc at the same time
    icecream -t --stdout [http://streaming.com/playlist.pls](http://streaming.com/playlist.pls) | vlc file:/dev/stdin 

prepare a 74 minute cd
    icecream -t --stop 74min [http://trace.net/playlist.m3u](http://trace.net/playlist.m3u) 

use a filename with today's date as output
    icecream -q --name 'radio_%y_%m_%d' --stop 60min [http://radio.com/playlist.pls](http://radio.com/playlist.pls) 

The last one looks like it would record for 60 minutes (though I could change that to 30 minutes, yes?)

So, would this a proper way to phrase it for the broadcast I want to record?

icecream -q --name 'radio_%y_%m_%d' --stop 60min [http://www.ecstreams.com/HealthyLife/HealthyLifeLive.asx](http://www.ecstreams.com/HealthyLife/HealthyLifeLive.asx)

Sorry, I'm really showing my lack of experience here...

---

### Post by Jay Car on 2008-07-08
Oops, I forgot to add the date before...

icecream -q --name 'radio_%08%07%08' --stop 60min [http://www.ecstreams.com/HealthyLife...hyLifeLive.asx](http://www.ecstreams.com/HealthyLife...hyLifeLive.asx)

I just tried this line in the terminal and got this error:
error: failed to retreive playlist

Tried this instead:
icecream -q --name 'radio_%08%07%08' --stop 60min [http://www.healthylife.net/](http://www.healthylife.net/)

Got an "invalid playlist file" message.

So, it needs adjusting.

---

### Post by kostkon on 2008-07-08
> **Jay Car said:**
> Oops, I forgot to add the date before...

icecream -q --name 'radio_%08%07%08' --stop 60min [http://www.ecstreams.com/HealthyLife...hyLifeLive.asx](http://www.ecstreams.com/HealthyLife...hyLifeLive.asx)

I just tried this line in the terminal and got this error:
error: failed to retreive playlist

Tried this instead:
icecream -q --name 'radio_%08%07%08' --stop 60min [http://www.healthylife.net/](http://www.healthylife.net/)

Got an "invalid playlist file" message.

So, it needs adjusting.
Sorry, but I think you'll not be able to do anything with icecream. It can only parse *M3U* and *PLS* playlists (mostly used with MP3s) and not *Windows Media* based playlists/metafiles, like ASX.

Nevertheless, here is the actual url of the stream you are looking for:
```
http://healthylife.ecstreams.com/HealthyLifeLive?MSWMExt=.asf
```
or
```
http://64.22.99.202:80/HealthyLifeLive?MSWMExt=.asf
```
Try to use this with *icecream*. But again, it is not a sure thing that it will work.

This radio streams *Windows Media* audio and I am not sure if *icecream* can handle such format.

That's why I recommended you *Mplayer*, it can handle such formats (after installing the *w32codecs* package from the [*Medibuntu* repositor]("http://medibuntu.org/")y, though)

---

### Post by Jay Car on 2008-07-08
kostkon, you're great for helping with this.  

I did try the lines that you gave, and you're right, icecream doesn't seem to work with it.  

I just spoke with my friend and explained that I probably wouldn't be able to record her interview (she'll be talking to 
Wendy Nan Rees, of Wendy's Animal Talk, about wolves) I only have about 5 minutes left, so I won't be able to get it recorded, but I have lots of information now to prepare for the next one. (I could always dig out my old Radio Shack cassette recorder!) :)

The Ubuntu forums are absolutely amazing, and have the nicest people in the world.  Even if I can't always solve a problem, I still always learn something new here.  Thanks again, JC

---

### Post by roquefilipe on 2008-07-08
I used this command and was able to record it and play it after

give it a try.

```
mplayer -playlist http://www.ecstreams.com/HealthyLife/HealthyLifeLive.asx -dumpstream -dumpfile teste

```

---

### Post by Jay Car on 2008-07-08
Wow!  It worked!!! 

How cool is that!?

I wasn't able to record the program in time today, but next time I'll be ready. 

Thank you!!

---

