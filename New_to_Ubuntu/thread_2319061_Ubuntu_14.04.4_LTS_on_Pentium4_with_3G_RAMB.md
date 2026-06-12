---
title: "Ubuntu 14.04.4 LTS on Pentium4 with 3G RAMB"
date: 2016-03-31
forum: New to Ubuntu
---

### Post by Adrian_Vlaheli on 2016-03-31
Hi,

Needles to say I'm new to Ubuntu and have a question.
I've installed recently Ubuntu 14.04 LTS and I'm quite ok with how it works except for one thing.

Every time I'm starting a Mozilla session or start to stream a movie (not HD) from the plex media server (plex.tv) installed the CPU is 100% directly.
The PC is still working but I would not except a single task to drive my CPU to 100%!!

The PC HW I'm using is a bit old but well above the reqs specified to run Ubuntu.
Is there anything I should do to improve this?

Below is some more detils on my system
GNOME: 3.8.4
Kernel: 3.19.0-56-generic
CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz
RAM total: 3009 MiB
Motherboard: GA-8I915P from Gigabyte (a bit old to be honest)
Graphic card: NVIDIA GEForce 210, manufacturer is Asus 

BR Adrian

---

### Post by papibe on 2016-03-31
Hi Adrian_Vlaheli. Welcome to the forum ):P

A few thoughts...

A P4 by itself is not able to reproduce 1080p video. However, it should do much, much better if you offload the decoding to the GPU. In order to do that you should use the Nvidia proprietary driver.

I would start testing local media first. Use either totem, vlc or mpv. If my recollection is correct, you should fairly smooth playback, and a CPU load of about 60-80%. Note that you may get some stuttering on high bit rate parts (like fast action scenes).

Once you are satisfied with that, you need to setup Firefox to use hardware acceleration. There are two alternatives here depending on how you are reproducing the stream: Are you using **flash**, or an **HTML** player to reproduce the video?

Regards.

---

### Post by grahammechanical on 2016-03-31
I have an Nvidie GT 210. It has 1GB of its own memory and is capable of doing hardware accelerated 3D rendering. So, what is the CPU doing to be working so hard? Run top or install htop and see what is going on.

Regards.

---

### Post by Adrian_Vlaheli on 2016-04-03
Hi,

Thanks both for the answer!

I'm now using [COLOR=#000000]Nvidia proprietary driver, se below pics for details.
However I think my problem is not really about rendering locally on the P4 Ubuntu PC a movie or similar because what I'm using in 98% of the cases is to stream from the Ubuntu PC to another (windows) PC or to a TV.
Please see below the CPU rate for process "PLEX New Transcoder" that is my issue.

But on the hand please let me know how to configure Firefox to use [/COLOR][COLOR=#000000]hardware acceleration both for flash and HTML players.

[/COLOR][COLOR=#000000]Best regards,
Adrian

[/COLOR][ATTACH=CONFIG]268141[/ATTACH][ATTACH=CONFIG]268142[/ATTACH][COLOR=#000000]

[/COLOR]

---

### Post by grahammechanical on 2016-04-03
Something else came to my mind. I do not know if it is applicable to this situation. In the old days single CPUs did run full speed. I have no idea if Pentium 4s had any kind of technology for running 2 speed or any kind of variable speed.

If you open the Nvidia X Server Settings utility that came with the Nvidia driver and go to PowerMizer you should see that the video adapter will run at different clock speeds according to the load.

Regards.

---

### Post by papibe on 2016-04-03
I am a little confused. Could you explain your whole set up?

Plex is running on another machine? What is the hardware on that?
Is the Plex server streaming the content?
What is the machine receiving the stream? What are the hardware specs on this one?

BTW, I've tried a transcoding plex server on a P4, and it was not good. Even with a good graphic card. You can decode a movie fairly well. However, the GPU doesn't have acceleration for (re)encoding. Thus, transcoding while streaming is not fast enough for smooth playing regardless of the receiving device's power.

If you are in a situation like that, say Plex server running on a P4 streaming to a chromecast, or a tablet, I'd recommend reencoding your videos so thare's no transcoding at all while streaming.

Regards.

---

### Post by Adrian_Vlaheli on 2016-04-04
Hi,

My PLEX server is run on P4 CPU with Ubuntu as OS. So the situation is the one you describe.
I've done some quick research myself and found also that PLEX server relies completly on CPU to transcode, GPU is not involved at all.

So I guess I need to reemcode my videos or buy a more powerfull CPU.

Best reagrds

---

### Post by Adrian_Vlaheli on 2016-04-04
Hi again,

Actually after some research I've found out that PLEX server needs a bit more powerful CPU than P¤ to be able to transcode and stream at the same time.
One final question, any suggestion for another multimedia server that can run on P4 similar to plex server (I'm thinking mostly on user interface and easy of use)

Best regards.

---

### Post by papibe on 2016-04-04
What are the devices that will receive the stream? Are they tablets, chromecasts, raspberry PIs, other PCs?

If you could narrow the devices' formats, you may not need to cover all angles.

On the other hand, I've heard from people who what's to be able to transcode to any possible device's format, prefer Core i5.

Regards.

---

### Post by Adrian_Vlaheli on 2016-04-04
All of them you mentioned except raspberry PI but at least one TV set (Sony Bravia [COLOR=#2F353D][FONT=SST W01 Roman]W805A)
Another info I've found is that plex server forums recommend a CPU with passmark score of at least 1500 to be able to transcode (and stream) 720p content/4Mbps

My P4 has a passmark score of 400 so not even near!

Best regards[/FONT][/COLOR]

---

