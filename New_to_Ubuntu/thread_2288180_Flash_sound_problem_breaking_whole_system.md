---
title: "Flash sound problem breaking whole system"
date: 2015-07-24
forum: New to Ubuntu
---

### Post by jack152 on 2015-07-24
So I have a strange problem, when I first reboot my computer and start up internet, install flash, sound works fine for a few minutes, then suddenly stops. When this happens, it also shuts down whole system sounds. If I shut down firefox, computer speakers will function again, reopen, also still working, until I go to youtube or another flash site and press play, then all sounds stop working again.

---

### Post by Vladlenin5000 on 2015-07-25
It is indeed a problem. Flash itself is a huge problem.
The good news is you don't need it and shouldn't be using it for Youtube (or any other major streaming services without DRM). You should always use HTML5 and nothing else. You don't even have to have Flash installed for Youtube, Vimeo, Dailymotion, etc. so why have it in the first place?

Now, assuming you really need it, here's the story: Adobe no longer updates Flash for Linux and sooner than later _nothing will work with that old version_. Google Chrome has updated Flash due to special agreement between those giants so, give yourself a break, and just use what works. (Note: DRM will be an issue regardless of Flash version or browser used)

---

### Post by jack152 on 2015-07-25
You mean, it should work if I go over to chrome? What do I use for all the websites that say "a plugin is needed" if not flash?

---

### Post by Vladlenin5000 on 2015-07-25
It should work no matter the browser provided it supports HTML5 (all major ones do) and you have set your Youtube or other websites accordingly. Most default to HTML5 in a fresh installation but that can be reversed as soon as your profile syncs - automatically in Chrome/Chromium if you use a Gmail account; by user request in FF - so you have to make sure it is configured as it should be in 2015.

For everything else that really need Flash yes, use Chrome. Again, if the given (commercial) website enforces DRM then not even with Google Chrome, I'm afarid. If/when that happens I suggest you google the website's name + Ubuntu and pick only _current_ sites, blogs, discussions, forums, etc. Anything from 2013 and before is, mostly, old news (some things used to work but no longer do - websites keep changing/evolving - and you need to focus in the new things only).

---

### Post by jack152 on 2015-07-25
Well this is interesting. I downloaded chrome and tried it out. Sure enough, sound, no problem. Two minutes later, it stopped.

---

### Post by jack152 on 2015-07-25
Another oddity, the little speaker icon in the top right of my monitor has now vanished as well. I have to type "sound" into the search tool to access it. I just tried this: restarted google, tried playing youtube, no sound. Leaving it running, in the sound control, I press the test sound button. Nothing. I pause the youtube video, and press the test sound button again. Now,I get the "front left, front right" no problem.

---

### Post by Vladlenin5000 on 2015-07-25
Although the symptom seems to point out to audio, it probably has something to do with graphics and respective drivers.
What is your graphics card/chip and what driver are you using?

---

### Post by Julind on 2015-07-25
It seems as if Flash is keeping the audio driver just for itself and not letting anything else use it. I know this thing has to do with the Audio driver and not graphics. I noticed when you said that no system sound was present when you played YouTube but it came back when you paused the video. Im sure its a audio driver problem. Does this only happen with flash? Tried playing .mp3's? Does it happen again?

(I know this, because I can easily recreate it in Windows but not with flash, something called ASIO, where you have do **disable** the system sound **in order for it to work** - and it does work because it makes sound, even though system audio is turned off. Maybe it also happens in Ubuntu, who knows)

---

### Post by jack152 on 2015-07-25
Ok well, I have just rebooted again, because I had tried several command line fixes taken from various threads trying to properly install flash and other sound things, and I thought perhaps that was gumming things up. This is a live boot system, so rebooting is a complete wipe and startover. So as far as the system is concerned at this point, Flash has never been installed and is not installed now. I started up Spotify: No sound. System sound test: no sound. I opened a movie in VLC player: sound. System sound test #2: sound . At the moment, youtube.com is returning "server not found" for me, not sure if the fact that this extends to Spotify helps. Here is the card info: 

ubuntu@ubuntu:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: GK104M [GeForce GTX 775M Mac Edition]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:49 memory:b0000000-b0ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:1000(size=128) memory:b1000000-b107ffff
ubuntu@ubuntu:~$

---

### Post by Vladlenin5000 on 2015-07-25
> **Julind said:**
> It seems as if Flash is keeping the audio driver just for itself and not letting anything else use it. I know this thing has to do with the Audio driver and not graphics.

If only it were so simple...
You do realize that if you're using let's say HDMI or DisplayPort with audio that's actually your graphics card and respective driver doing the (audio) work, not the traditional audio driver your integrated audio chip uses, don't you?

What you can or cannot 'recreate' in Windows is kinda irrelevant... And I'm yet to see the described issue occurring _only_ in streaming video in and otherwise fine system. A problem with an audio drivers is usually system wide.


Anyway, specs is what we need to start *thinking* about it, not wild speculations.

---

### Post by jack152 on 2015-07-25
Then I go into the "additional drivers" tab. It has two. 1. NVIDIA Corporation: Unknown. "Using X.OrgX server- Nouveau display driver from xserver-xorg-video-nouveau (open source)" is checked. 

2. Broadcom Corporation: Unknown This device is not working. "Do not use the device" is checked. 

No proprietary drivers are in use.

---

### Post by jack152 on 2015-07-25
I'm not sure if the information i've supplied is what you wanted, and if not, I don't know how to get it. So instructions will be appreciated.

---

### Post by Vladlenin5000 on 2015-07-25
```
product: GK104M [[COLOR=#ff0000]GeForce GTX 775M Mac Edition[/COLOR]]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=[COLOR=#ff0000]nouveau[/COLOR] latency=0
       resources: irq:49 memory:b0000000-b0ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:1000(size=128) memory:b1000000-b107ffff
```

As expected... A 'beast' of a card being run by the open source driver *nouveau* which has almost no support for newer chips like yours. 
You need a proprietary nvidia driver for that card or you're doomed to have problems just like that. And probably other tweaks... You conveniently "forgot" to tell us it's a MAC!! :rolleyes:
(yes, it can have specific problems I'm not aware of at this moment).

Please check System Settings > Software & Updates, the rightmost tab, Additional Drivers. There should be a list of the available proprietary drivers. Usually the recommended (tested) one is preferable but depending on the Ubuntu release you're running you may need to add a third party PPA (software repository/source) in order to be able to easily install a newer, more adequate, nvidia driver version for your specific hardware.

---

### Post by Vladlenin5000 on 2015-07-25
You need the third party PPA...

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
```

Then you'll find a few more offers in "Additional Drivers".
Select and activate 352.xx (it should also work with at least 346.xx).
Reboot.
Test.

---

### Post by Julind on 2015-07-25
> **Vladlenin5000 said:**
> If only it were so simple...
You do realize that if you're **using let's say HDMI or DisplayPort with audio** that's actually your graphics card and respective driver doing the (audio) work, not the traditional audio driver your integrated audio chip uses, don't you?

What you can or cannot 'recreate' in Windows is kinda irrelevant... And I'm yet to see the described issue occurring **_only_ in streaming video** in and otherwise fine system. A problem with an audio drivers is usually system wide.


Anyway, specs is what we need to start ***thinking*** about it, not wild speculations.

1. Then we need to ask if he is using HDMI or Displayport and not VGA or DVI. He could be using a headphone jack. What about that?
2. Thats why i asked if he tried to play something not using flash.
3. What was I doing then?

---

### Post by jack152 on 2015-07-25
Ok, I got them all downloaded and installed, but to no avail. Exactly the same problem. Also, I can no longer access facebook or youtube, but according to the web the sites are up. Probably a coincidence.

---

### Post by jack152 on 2015-07-25
Incidentally, as this is a Live boot, I cannot do anything that requires a reboot, as changes are simply lost. And no, a persistent install is not an option in this case. I'm just trying to get a live boot that functions normally!

---

### Post by Julind on 2015-07-25
A live boot is sort of ment for demo purposes or maybe for partitioning the drive before instaling ubuntu, or sort of a rescue disk, but never for actual, regular use. Unless you install ubuntu in an USB (I don't know how it will detect hardware), you will never be able to make what you are trying to achieve on a DVD/CD.

---

### Post by jack152 on 2015-07-25
is it s a Live USB. But the thing is, it's worked perfectly for months now, so surely it must be fixable?

---

### Post by Vladlenin5000 on 2015-07-25
You could have said so already...
No, there's no easy way to make it work, not with that hardware. An installed system can be "tweaked" whereas a live session can't. Even with persistence there are many other factors at play that prevents that to be used as a daily driver. Without it it's impossible because you _must_ reboot so the changes take effect

In a complementary note, I'm starting to suspect you have a problem with your internet connection and that's the main culprit. You mentioned earlier that you saw a Broadcom driver not in use in the Additional Drivers. didn't you? Well, almost always it's related with an internal Broadcom WiFi card and those are quite [problematic]("http://ubuntuforums.org/showthread.php?t=2214110"), to say the least. Whether you would be installing the one offered or one of the better alternatives recommend by Dr. Chili in the previous link, again, reboot is a must.

Bottom line: Simple live sessions can work acceptably in simple Intel based systems, with Intel Graphics, and with the rest of the hardware being also completely supported. In any other scenario, namely with a newer Nvidia card and a WiFi device desperately in need of some 'love' you'll surely have (unsolvable) problems. The media is good for installing though. Then, the installed system can be configured properly.

---

### Post by jack152 on 2015-07-26
I did mention that it was live once before. But it seems strange, that I have been using this for so long without this problem, then suddenly it happens at every reboot. I can't even get any sound through the headphones. Maybe i'll try creating a new USB.

---

