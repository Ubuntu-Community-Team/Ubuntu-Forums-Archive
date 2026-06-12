---
title: "How to pass on my software to the Linux-community?"
date: 2012-12-04
forum: Programming Talk
---

### Post by moma on 2012-12-04
Hello,
I have an audio-recorder software that I would like to pass on to the Linux-community, so more hands can involve in its development. 

I cannot maintain the software further because I have started other projects. I want to give it to the Linux-community.

How can I setup an incubator for the code?

The software is here:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

It is a rather simple audio-recorder that uses Gstreamer for the tough part. I can see from the statistics of PPA that is has at least 5000 downloads already, maybe even more. So I can't just throw it away without notice.

Please tell me if you are interested to maintain the code further. I have already ported it to Gstreamer 1.0 so the changes for Ubuntu 13.04 and 13.10 will be very subtle, near zero. The quality of code is not any prime-art, but it has served well so far, and more hands can easily improve the code.

Some screenshots:
[http://ubuntuforums.org/showthread.php?p=12306562](http://ubuntuforums.org/showthread.php?p=12306562)

[B]The code must keep its copyright statements, must be fully GPL3, and have zero price forever. And to be maintained on the Launchpad.net. ;-)
[/B]
Suggestions are welcomed. Please help if you can!

EDIT: I just created a team "audio-recorder" on the Launchpad. I invite you to join this group. It will have its own mailing list. I hope to transfer my project to this team.
The team page: [https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)
[COLOR="Red"]Please join![/COLOR]

---

### Post by moma on 2012-12-05
Bump.

---

### Post by moma on 2012-12-06
[SIZE="4"][COLOR="Red"]Bump.[/COLOR][/SIZE]

---

### Post by mastablasta on 2012-12-06
there is not many developers here i guess. how about using one of their mailing lists?

---

### Post by QDR06VV9 on 2012-12-06
> **moma said:**
> Hello,
I have an audio-recorder software that I would like to pass on to the Linux-community, so more hands can involve in its development. 

I cannot maintain the software further because I have started other projects. I want to give it to the Linux-community.

How can I setup an incubator for the code?

The software is here:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

It is a rather simple audio-recorder that uses Gstreamer for the tough part. I can see from the statistics of PPA that is has at least 5000 downloads already, maybe even more. So I can't just throw it away without notice.

Please tell me if you are interested to maintain the code further. I have already ported it to Gstreamer 1.0 so the changes for Ubuntu 13.04 and 13.10 will be very subtle, near zero. The quality of code is not any prime-art, but it has served well so far, and more hands can easily improve the code.

Some screenshots:
[http://ubuntuforums.org/showthread.php?p=12306562](http://ubuntuforums.org/showthread.php?p=12306562)

[B]The code must keep its copyright statements, must be fully GPL3, and have zero price forever. And to be maintained on the Launchpad.net. ;-)
[/B]
Suggestions are welcomed. Please help if you can!

EDIT: I just created a team "audio-recorder" on the Launchpad. I invite you to join this group. It will have its own mailing list. I hope to transfer my project to this team.
The team page: [https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)
[COLOR="Red"]Please join![/COLOR]

___________________________________________________________


Cant use it. it pulls in pulseaudio!! A No Go! for alll three of my machines.

---

### Post by mörgæs on 2012-12-06
Yes, the fora are mainly for support, and we rarely see developers here. 

If you want, I can move the thread to [http://ubuntuforums.org/forumdisplay.php?f=307](http://ubuntuforums.org/forumdisplay.php?f=307) giving it a chance (though small) that a developer will notice.

Thanks for the donation!

---

### Post by cariboo on 2012-12-06
The [ubuntu-devel]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") mailing list may be the best to get the info you need.

---

### Post by moma on 2012-12-06
Yes please.
Move this thread to [http://ubuntuforums.org/forumdisplay.php?f=307](http://ubuntuforums.org/forumdisplay.php?f=307)

Thank you.
I hope this recorder would at least function as a model for other similar products, just in case the code is too spaghetti to be maintained further. (humble me)

---

### Post by cariboo on 2012-12-06
Moved by request.

---

### Post by moma on 2012-12-06
@runrickus:
>Cant use it. it pulls in pulseaudio!! A No Go! for alll three of my machines.

The program has a dependency to libpulse library. It is only used to get device names and IDs for audio devices, these are then shown in the listbox. GStreamer can now provide the same information, so the -lpulse dependency can be removed.

A question to runrickus:

You are using ALSA.
Can you compose a Gstreamer-pipeline and make a test-recording.

Please see:   
[https://bugs.launchpad.net/audio-recorder/+bug/1009930/comments/1](https://bugs.launchpad.net/audio-recorder/+bug/1009930/comments/1)

List devices:
$ pactl list | grep -A2 'Source #'

Test recording (records to filesink test.oga):
$ gst-launch-0.10 pulsesrc device="alsa_output.xxxxxxxx-.monitor" ! queue ! audioconvert ! vorbisenc ! oggmux ! filesink location=test.oga

Set the device="xxxxx" to a correct value. See your pactl listing. Please read the guide.

**Notice:** You can use either Gstreamer 0.10 or 1.0. These pipelines are relatively simple so they do the same job.

Does this work in your computers? If yes, then we can also fix the recorder.

---

### Post by moma on 2012-12-09
-deleted-

---

### Post by moma on 2012-12-18
Hello,
**PulseAudio 3.0 **was just released.
It has ability to connect to other devices via bluetooth. Eg. it can copy audio from your phone or tablet.

This might give new ideas to Audio-Recorder too. 
It could have a new selection to "Record from bluetooth or wifi device..." and it would then ask parameters to pair the devices. Nice ;-)

Please read:
[http://www.h-online.com/open/news/item/PulseAudio-3-0-now-better-with-mobile-and-wireless-1771599.html](http://www.h-online.com/open/news/item/PulseAudio-3-0-now-better-with-mobile-and-wireless-1771599.html)

---

### Post by Lucamaxx on 2013-02-09
Hello moma,
Thank you so much for your software !
I use it a lot to record audio output from web audio streams.

Unfortunately I'm not anymore a developper, my only "serious" experience was on Labview and Visual Basic 5 , but 20 years ago ...

I recently install on Mint 14 64bit Audio recorder but there is no more the possibility to record in mp3 format.
I do not remember how I got it previously.

I have try to add to Gstreamer the plugin gstreamer010-fluendo.mp3 but still no mp3 format recording.

How should I proceed to get mp3 format recordings ?

Thanks 
Luca

---

### Post by moma on 2013-02-09
Hello Lucamaxx,
Sorry for delayed reply.

Fluendo's gstreamer010-fluendo.mp3 has ability playback MP3-files, but it cannot record (encode) MP3.

Please install necessary plugins for MP3 and other audio formats. The instructions are here.
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

ps. please join to the audio-recorder team now!
[https://launchpad.net/~audio-recorder](https://launchpad.net/~audio-recorder)

---

### Post by moma on 2013-05-13
Audio-recorder for Ubuntu 13.04 is now ready for download.
Just fixed couple of bugs. You are very welcome to use it.
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

---

### Post by elianto on 2013-06-11
> **moma said:**
> Audio-recorder for Ubuntu 13.04 is now ready for download.
Just fixed couple of bugs. You are very welcome to use it.
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

Hi, I was successfully using this great audio-recorder but with the new 13.04 it doesn't record any audio from any source and the progress meter doesn't show any audio activity.
Can I debug the problem somehow? It would be great to have it working again. I've purge and installed the new version but maybe it still reads some old config or there are other problems.
any hint appreciated
Eli

ps. I've also tried manually using  gst-launch-1.0 and gst-launch-0.1 same result a file with no audio

---

