---
title: "Lubuntu running on old hardware. What are reasonable expectations?"
date: 2018-02-24
forum: New to Ubuntu
---

### Post by ja1124 on 2018-02-24
I am trying Lubuntu 17.10 on old hardware - Pentium 4 1.6 ghz, 2 Gb DDR400, Asus P4S333-VM, and GeForce MX440 128MB AGP video card.

After installing, I opened Firefox and tried watching a youtube video. The audio was clear, but video often froze and was choppy.

Is it asking too much of the hardware to get smooth video playback, or should I tweak the installation? If the latter, please provide some pointers.

Many thanks.

---

### Post by deadflowr on 2018-02-24
Most likely the browser sucking up valuable resources.
You might try seeing how well streaming through a video/media player like vlc works.
I would open a YouTube video, then copy the address, then close the browser, then open vlc and copy the link into it and see how well it runs.

I had to run (or tried to run) from an old pentium 4 about a week ago and what you describe is exactly what I experienced.
But running videos through a media player instead of a browser ran smooth ( or at least noticeably smoother than through a browser.)

Browsers are just getting too fat these days.

---

### Post by DuckHook on 2018-02-24
> **deadflowr said:**
> …Browsers are just getting too fat these days.
&#8593; Agreed.

Just curious, but have you ever tried a lighter-weight browser? Epiphany perhaps? I can't try this anymore because I recycled my Pentium 4 last year.

---

### Post by ja1124 on 2018-02-25
I had read that SMPlayer and the SMTube plug-in had given good results for another user, so I tried that first, but SMTube was unable to locate the URL of the youtube video. Next I installed VLC, and it yeilded better results than the web browser, but still was unacceptable as a viable viewing experience. The Gnome MPV gave the best results. The video dropped some frames. With a clip lasting 4:45, the audio finished about 35 seconds ahead of the video.

---

### Post by kerry_s on 2018-02-25
try elementary os, based on ubuntu 16.04. 

it ran pretty good on a netbook i had with your kinda specs.

---

### Post by ja1124 on 2018-02-26
Thank you for the suggestion. I should further elaborate the purpose of this experiment as it might yield more viable suggestions.

I work with a local man who, in the course of running an electronics repair shop, has hoarded about fifty obsolete Windows XP desktop PC's. The specs of the one I am using is representative of the least powerful. So if I can get acceptable performance out of the one I am experimenting with, I should get acceptable performance from the rest of them.

I am investigating the viability of installing linux distros on all of them and shipping them to Liberia for use in a rural school. This is a charitable endeavor. (I have already worked out solutions to the other logistic issues, i.e. electrical power, satellite internet, etc.)

The goal is to teach the students how to use open source office suite software, and also introduce them to open source operating systems. I would like to be able to utilize videos as teaching aids.

---

### Post by sudodus on 2018-02-26
See this 'mega-tread' about old hardware,

[Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by DuckHook on 2018-02-26
> **ja1124 said:**
> …I should further elaborate the purpose of this experiment as it might yield more viable suggestions.
This is good background. Glad you added it.
> …about fifty obsolete Windows XP desktop PC's. The specs of the one I am using is representative of the least powerful. So if I can get acceptable performance out of the one I am experimenting with, I should get acceptable performance from the rest of them.
You may be shortchanging yourself basing your strategy on the least capable machine. With the sheer quantity of machines you have, I would suggest a different strategy:

The most graphically challenged machines might be better off without any GUI whatsoever. Use them as servers for the others. In the kind of setup that you appear to be putting together, there will always be a need for file servers, backup servers, print servers, etc. Older HW that is underpowered for a desktop installation may be fine for server use. To be sure, the CLI environment has a learning curve, but once set up, it isn't that hard to learn the limited set of commands that are needed to keep simple servers maintained. Most of the maintenance tasks can be automated with scripts.

Incidentally, it is far easier, safer and more efficient to administer a server remotely with the command line (using ssh) than using some graphical tool.
> I am investigating the viability of installing linux distros on all of them and shipping them to Liberia for use in a rural school. This is a charitable endeavor. (I have already worked out solutions to the other logistic issues, i.e. electrical power, satellite internet, etc.)
This seems to cry out for server use. Satellite internet is expensive. You may wish to consider running one of those servers as a private Ubuntu mirror. That way, the other machines in your network can get their updates from this local server rather than each machine pulling their updates over the internet. Just another example of the usefulness of CLI-based servers.
> The goal is to teach the students how to use open source office suite software, and also introduce them to open source operating systems. I would like to be able to utilize videos as teaching aids.
A laudable goal. As their skills increase, you may very well want to run a web server, a database server, etc. There is no end to the uses of machines that run the Ubuntu Server install.

To summarize—you may wish to split those machines into two groupings:

[list=1]
[*]Those capable of running a Lubuntu desktop with decent audio/video throughput. These machines would be for end users.
[*]Those not powerful enough for desktop use would run Ubuntu Server and be used for backoffice duties like repo mirroring, backups, fileserver, print server and eventually, even mail server, web server, database server and whatever else you care to throw at them.
[/list]

---

### Post by monkeybrain20122 on 2018-02-27
Both flash and html5 are resource demanding, so if you have a weak system it would be hard on your resources. You will get much smoother videos on youtube streaming through either vlc or smtube (youtube only) or Smplayer with mpv backend which you can access many more video sites

You get Smplayer and smtube from [https://launchpad.net/%7Ervm/+archive/ubuntu/smplayer/+index?batch=75&memo=75&start=75](https://launchpad.net/%7Ervm/+archive/ubuntu/smplayer/+index?batch=75&memo=75&start=75)
You would also need up to date mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests) (read the detail instructions)

---

### Post by monkeybrain20122 on 2018-02-27
> **ja1124 said:**
> I had read that SMPlayer and the SMTube plug-in had given good results for another user, so I tried that first, but SMTube was unable to locate the URL of the youtube video. Next I installed VLC, and it yeilded better results than the web browser, but still was unacceptable as a viable viewing experience. The Gnome MPV gave the best results. The video dropped some frames. With a clip lasting 4:45, the audio finished about 35 seconds ahead of the video.

You sure your smtube is up to date? The one from repo is GUARANTEED broken.

---

### Post by mastablasta on 2018-02-27
it could be that the GPU is the one struggling. i would also check if it is using it or the CPU.

also it depends a lot on resolution. lower resoluton video will still look ok on "VGA" monitor and will work ok, while the higher one might not.

funny how RaspberryPi can do many things these old PC can't :-)

it's been a while since i touched the very old laptop PC but i do remember it played videos well on Crashbang linux (now forked to BunsenLabs Linux[FONT=arial]). it only had 1.2 Ghz Athlo and only 256 MB ram. so at least on your machine i would expect them to be normally playable. 

you could also explore AntiX.

Debian was always a bit lighter and ran faster on old hardware. you might find osme thing missing, but it is not necessary you will need them at all. if Bunsenlabs is anything like the old crash bang it will ask you what you want installed.[/FONT]

---

