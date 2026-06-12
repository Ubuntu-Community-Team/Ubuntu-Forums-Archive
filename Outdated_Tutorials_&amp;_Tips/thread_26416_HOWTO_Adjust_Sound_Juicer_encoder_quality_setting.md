---
title: "HOWTO: Adjust Sound Juicer encoder quality setting"
date: 2005-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Curufir on 2005-04-12
Sound Juicer in Hoary uses the 0.5 quality setting for ripping songs to Ogg format. If you have plenty of disk space, but don't want the extravagance of FLAC, you can adjust this setting to get better results.

Open: Applications->System Tools->Configuration Editor

Navigate to: /system/gstreamer/audio/profiles/cdlossy

Alter: Pipeline audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5

Quality is a value between 0 (Low quality) and 1.0 (High quality). At a quality setting of 1.0 the resultant Ogg will be approximately 1/3 the size of the same song encoded as FLAC.

***

First post, hope I put it in the right place.

---

### Post by Nis on 2005-04-12
You can also press '<Alt>+F2' and type in 'gnome-audio-profiles-properties' and edit the profile from there.  Just change 'Gstreamer pipeline' to what Curufir wrote above.

And yes, this is exactly the right place. :)  Thanks for the HOWTO.

---

### Post by riffic on 2005-04-13
how about encoding in mp3 with lame's --alt-preset standard config, how would you go about setting that up?

---

### Post by Curufir on 2005-04-13
[QUOTE=riffic]how about encoding in mp3 with lame's --alt-preset standard config, how would you go about setting that up?[/QUOTE]

That's a little more involved.

Add the marillat repositories to your sources.lst ([http://ubuntuguide.org/](http://ubuntuguide.org/) shows how to do this).

Get gstreamer0.8-lame and liblame0 using Synaptic.
(Or enter command: sudo apt-get install gstreamer0.8-lame liblame0)

Press '<Alt>+F2' and type in 'gnome-audio-profiles-properties'.

You will be presented with a dialogue titled 'Edit GMAudio Profiles'.

Hit 'New'.

Set 'Profile name' to 'CD Quality, MP3'.

'CD Quality, MP3' will now appear in the list of 'Profiles'.

Select 'CD Quality, MP3' and hit 'Edit'.

Fill in the 'Editing profile "CD Quality, MP3"' form with these values:

'Profile name:' = 'CD Quality, MP3'
'Profile Description:' = 'Used for converting to CD-quality audio, but with a lossy compression codec. Use this for CD extraction and radio recordings.'
'GStreamer Pipeline:' = 'audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=standard'
'File Extension:' = 'mp3'

Mark the profile as 'Active'

Hit 'Ok'
Hit 'Close'
 
Open up a terminal (Applications->System Tools->Terminal).

Enter command: gst-register-0.8

You can now select 'CD Quality, MP3 (MP3 audio)' in the Sound Juicer preferences.

The value 'preset' in 'GStreamer Pipeline:' can be one of the following:

None (Lowest Quality/Size)
Medium
Standard
Extreme
Insane (Highest Quality/Size)

***

Thanks for pointing out the shortcut Nis.

---

### Post by kuleali on 2005-04-13
NIce!

---

### Post by Deusiah on 2005-04-16
This may be a stupid question but I'm assuming 0.5 is the same as Q5? and so Q10 is 1?

---

### Post by Bob D. on 2005-04-16
You are correct.

Bob

---

### Post by graigsmith on 2005-04-25
so how do i get bitrate management mode?  i need to make ogg files that don't drop below 96kbps, because if they do my player crashes.

---

### Post by Curufir on 2005-04-25
Use this as your GStreamer Pipeline:

audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc max-bitrate=96000

---

### Post by graigsmith on 2005-04-25
[QUOTE=Curufir]Use this as your GStreamer Pipeline:

audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc max-bitrate=96000[/QUOTE]
 hmm does that set the max bitrate at 96kbps?  or does it set the Minimum bps to 96?

also can i set that i want 128 average kbps, with 96 as a minimum?

---

### Post by Curufir on 2005-04-25
[QUOTE=graigsmith]hmm does that set the max bitrate at 96kbps?  or does it set the Minimum bps to 96?
[/QUOTE]

That gives you variable bitrate, no set minimum, maximum set to 96kbps. I misread your post, thought you needed to keep them below 96kbps, apologies. min-bitrate is used to set a minimum.

> also can i set that i want 128 average kbps, with 96 as a minimum?

These are some pretty non-standard settings you're asking for.

audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc managed=true min-bitrate=96000 bitrate=128000

You should be able to figure out anything else with a combination of 'gst-inspect-0.8 vorbisenc' and 'man oggenc'.

---

### Post by graigsmith on 2005-04-25
[QUOTE=Curufir]That gives you variable bitrate, no set minimum, maximum set to 96kbps. I misread your post, thought you needed to keep them below 96kbps, apologies. min-bitrate is used to set a minimum.



These are some pretty non-standard settings you're asking for.

audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc managed=true min-bitrate=96000 bitrate=128000

You should be able to figure out anything else with a combination of 'gst-inspect-0.8 vorbisenc' and 'man oggenc'.[/QUOTE]
 thanks :)

---

### Post by Sniffer on 2005-04-26
There is anyway to change the encoder??

Let's say to use lame 3.93 (recommended codec by audiophonics) and use Gain as well?

I just want to have a quality solution in my linux box and avoid using EAC for it.

---

### Post by dirk362 on 2005-04-30
Excellent HOWTO.

Slightly off topic but . . .

I'm a recent convert from M$ to Ubuntu, but want to get the best out of the system that I can. In the M$ world I used EAC with very specific settings and LAME to get Uber Standard.

I'm trying to get to the same sort of quality with Linux, but just can't get there. For example, I want to use a specific release of LAME (not the latest as that has accoustic issues with certain audio types). Is there an easy way to get say LAME 3.90.3 the default?

Alternatively does anyone have any experience of getting EAC to work in Ubuntu?

---

### Post by robn824 on 2005-05-06
How to resolve this?

root@ubuntu:/home/rob # apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-lame: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

TIA,
Rob

Also, I had to write this in gedit and paste in the reply.  Why can't I type in the reply box?

---

### Post by ruben_b on 2005-05-08
hello,

can someone tell me how i could adjust sound juicer to rip my files as mp3's with a variable bitrate? i used grip for a while but now that i'm using ubuntu i'd like to try sound juicer.
the lame package is allready installed and the mp3 profiles i created. now i need to know to set it up so it rips my files with the following settings:
min bitrate 160bps
max bitrate 320bps

thanks!

---

### Post by ruben_b on 2005-05-10
does no one know how to do that? :(

---

### Post by davidjany on 2005-05-13
Take a look at
[http://ubuntuforums.org/archive/index.php/t-957.html]("http://ubuntuforums.org/archive/index.php/t-957.html")
what will_rat has written (03-04-2005, 04:41 AM).

> Haven't tested it yet, but sounds success-promising.
:arrow: I just tried it and it seems to work. Although I can't find any application that could read the correct characteristics from vbr-files.

:idea: Here an example of an vbr-profile created with gnome-audio-profiles-properties:
Profilename: MP3 VBR
Description: ...
GStreamer-Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=5
Fileext: mp3

:-$ Don't forget to run gst-register-0.8 before starting Sound Juicer!

---

### Post by homerhomer on 2005-05-17
I messed with this and then thought "forget it"

and install ripperx and now I"m a happy camper again

---

### Post by ruben_b on 2005-05-17
@davidjany
thanks for the hints. i haven´t been able to try it yet, but i´m going to try it this evening.

---

### Post by mohsin on 2005-08-13
thnx for telling this man .. great tip

---

### Post by xyz on 2005-10-03
Curufir!
that was clear,understandable and even I was able to do it!:-\\\ musical thanks!

---

### Post by corefile on 2005-10-22
This may sound dumb, but why would you want to use a variable rate when encoding mp3's?

---

### Post by shadow07 on 2005-12-04
@corefile:

That was explained on the second page of this thread by davidjany.

---

