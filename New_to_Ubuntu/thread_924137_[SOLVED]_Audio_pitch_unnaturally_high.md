---
title: "[SOLVED] Audio pitch unnaturally high?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by debiant on 2008-09-19
Hi there,
I'm fairly new here-
All my audio-whether from WAVS on the hard-drive or burnt off a CD and even streaming in Firefox has this unnaturally high pitch to it.

I'm running 8.04 with an AMD 64 processor. My soundcard is a Creative EMU 0404 PCI, with the latest open Asio driver.

I've tried very hard to solve this myself, there are similar issues but not one I could identify as the same. If I've missed an existing thread, my apologies, please let me know.

If anyone can help me, I'm keen to learn and can understand a few things in BASH!

Thank you!

---

### Post by debiant on 2008-09-21
Oh well, I guess I might as well have a conversation with myself about this.
It isn't the pitch, it is definitely the speed of playback-play something fast and it's pitch will appear to increase. When you watch a longer video on something like YouTube you can see the pictures keep going after the audio has finished!

The problem is, I think, something to do with pulse-audio. This is a "sound server" in Ubuntu. Or something like that, I'm supposed to be a newbie, remember-but thats what i seem to be getting from my research.
The alsa-mixer which connects it to applications isn't reading it because I'm using a 64 bit AMD version of Ubuntu and it is a 32 bit application.

By using gstreamer instead of xine I've now got mplayer and banshee installed and working so I can now listen to music ok, which is nice!:)

However-flashplayer didn't work until I found this-

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Ah, but-now I get this loud farting sound every time I click on a video on the BBC web-site. After that-the sound seems ok. A bit tinny, but it is at least running at the right speed. The farting sound is however, very loud, so you need to turn speakers/head-phones down etc and then up once the video is running.

But hey, we're making progress! If anyone out there who actually knows anything about Linux feels like joining in that would be really nice. I'd like to be able to recommend Ubuntu to my friends but I'm not sure they share my endless patience and tenacity.

BBBRRRRRRPPPPP, oh excuse me I just clicked on a video on BBC news, honest.

I don't think we are quite ready to post "solved" on this one yet...
:confused:


Tried to watch a program on the BBC-still sounds like a 1940s newsreel. Short news items run at the right speed but with the noise I described above as each one loads.
Beginning to feel very skeptical about the "wonderful world of linux" and Ubuntu's "amazing community". After several weeks of time and effort, including working through a huge book on BASH and how to do this and that, I really have not experienced either.
There really isn't an alternative to Windows, lunch is definitely not free. I have spent more time and effort on this than I have on anything in 10 years of using computers and it just doesn't work. There is no manual to read, no-one to ask and no support to e-mail.
I'd love to give someone £30 to let me have this working, so maybe I'm just not clever enough to do this.

---

### Post by markbuntu on 2008-09-21
If you have another few hours to spend, you can look through the links in my overly extensive sound troubleshooting guide:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The best thing for you to do is determine your specific sound card/chip and then look for threads that discuss it. There are links to doing that in my guide.

---

### Post by Tatty on 2008-09-21
I cant help much more im afraid, other than to suggest you look for settings related to "sample rate".

From your description it sounds as though somehow your system is trying to play audio at a sample rate which is higher than the sample rate of the actual audio - this would cause it to sound high pitched.

---

### Post by Tatty on 2008-09-21
Also, here is the page on the ALSA wesbite related to your card:
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)

I know it gives a different model number in the title but the [details link]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") for your card directed me there.


Something which seems to still be largely ignored in linux is semi-pro and pro soundcard support.  Although as with everything linux, this is improving all the time, keep your eyes out in the community for development.

---

### Post by debiant on 2008-09-21
Markbuntu and Tatty,
Thank you so much for replying, I had a bit of a morale crash there.

It's a brilliant suggestion about the sampling rate-I have looked into that and you're absolutely. I would never have guessed that someone clever enough to write that software could then have been so unbelievably stupid. 

I've been in the music business since 1979 and I haven't a clue what anyone running a pc would do in 48K. Apparently the controls are in the Alsamixer, but mine doesn't have anything except one volume control so I can't scroll across to change it to normal. I can't find any code to do it either.

My attempts to re-install alsa or find a mixer have left me with 4 directories in the wastebasket i don't have permission to delete and none of the fixes for that work.

I thought it was supposed to be Windows that said you didn't have permission to do things.

Getting a pc to run Ubuntu is really tough and I appreciate you offering to help. It's nearly 4 am and this is my last sleepless night on this. Given that this is the easiest distro to get into Linux, I really don't think I have the programming skills to do this.

I appreciate your help but I think we should close this thread because I've had enough. I still need Windows to run the home studio anyway, and as thats a stand-alone system i can run another disk with my XP registration.

Thanks for offering to help-it's nice that there is a community here, I thought i knew about computers but you guys must be incredible to run this stuff.

I've finally solved this-

Tatty's right. The sampling rate is set wrong-I say wrong because I have never seen sample rates other than 44.1k outside a professional studio. You master to 44.1 which is what they use on planet Earth- CDs, WAVs, MP3s, the internet-if the public listen to it's 44.1. 

My card is a faily cheap one but, yes it is the low end of pro-even so, but for one very irrational default setting I could have had working sound a month ago. The Alsamixer was useless for changing the settings-it didn't have the controls.
I've also fixed the trash can, by the way-you have to BASH you're way to it and change ownership of the files. Good grief, but it is listed as a bug and should be fixed next version. I'll find somewhere else to post that! 
I only came back to retrieve my e-mails from Thunderbird, gave it one last go and seem to have got lucky!
I love the idea of Ubuntu, but we badly need to sort out some really silly bugs before I can go recommending this as an operating system for anyone who isn't an obsessive geek like me. I was right on the giving up point this morning and I've been working on this for 6 weeks!
Extremely grateful to Markbuntu-that is an epic post, obviously a lot of work and Tatty, well done. There is nothing anywhere on google that would have made me think of that-thank you!
:guitar:

---

### Post by Tatty on 2008-09-22
Excellent, Im glad you have sorted it,  may i inquire as to what exactly you did to get it working?  Its always good to end threads with a conclusion to help out anyone who may google in... Also im rather curious :)

As i said before, the linux support of semi-pro / pro soundcards is still quite poor (and the documentation is even worse).  I still have a windows machine to run cubase, tracks etc. And it is just about the only thing I still need windows for (well that and my gf cant get photos to upload to myspace in linux)

But having witnessed the increadible speed of development in linux over the last couple of years I remain ever-optimistic that one day soon I shall manage to get a machine running ardour without stuttering - and maybe even recognising my friend's firewire echo soundcard :)

---

### Post by debiant on 2008-09-22
Of course Tatty-


Right click on the volume icon (speaker, usually top-right of screen)-
click on "open volume control", the alsa-mixer control panel opens.
Then edit, preferences, and in the list;
scroll down to "clock internal rate" and check it (make it visible).
Close the preferences and return to the alsa-mixer control panel,
Click the options tab, the box "internal clock rate" needs setting to 44100 and that's it!!!

Tatty I remember Cubase from ages ago! :) I went with Cakewalk Sonar, I've had it since Pro-Audio 9. I also use FLStudio which is a fantastic midi program and you can use it as a plug-in in Sonar! I still run XP for it but that drive has no network, IE is as uninstalled as it can be and there's no firewall or anything else for that matter. Goes really well-haven't tried WINE or vmware yet to dip them in Ubuntu yet?
For a pc I run everything else here on Ubuntu, well since I got some advice on running audio from you last night that is! :biggrin:

---

### Post by markbuntu on 2008-09-22
Wow, that was lucky. I don't even have a clock internal rate box for my sound card. Well, now that you have that working, you should check out Ubuntu-Studio if you are using Cakewalk Sonar and stuff like that. I suggest a Hydrogen-Rosegarden-Ardour setup for starters. Hydrogen is a midi drum machine and Rosegarden does the rest of the midi and they sync together with the ardour mixer using jack. You can read about some of that here:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)


[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

### Post by debiant on 2008-09-22
Thank you Mark, you guessed right-I am definitely interested in finding out about that and thanks for the tip about where to start!

The soundcard thing is something we have gotta work on. It is now 18 hours since I used wiped my old XP drive (I used it to clone my music one!) so I am just finishing my first day windows-free! The music drive doesn't count really-it has no internet etc.
So I've been burning CDs putting things in my iPod, sending e-mails etc. I now consider myself enough of an expert to start offering advice to the newbies about installation problems.
Possibly because installation is about the only thing I've actually done with Ubuntu! :wink:
We should get a separate area for soundcards and try and pull the various threads together-you know, The Alsa stuff advice about pulse audio, settings, sample rates etc. If more musicians get involved here can you imagine what we could achieve? The sound quality I've got here-its really sweet-I've had banshee playing away all night!
Feeling very happy to be part of the Ubuntu community-thanks again, Mark!

:guitar:

---

### Post by markbuntu on 2008-09-23
A lot of sound and video issues are addressed in the Multimedia and Video Forum. I suggest you look at the stickys at the top of the forum. You can also look though my overly extensive and long winded troubleshooting guide to sound here. It explains a lot about how sound works in Ubuntu and has tons of links. There is a jack section near the bottom:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by JosephWheatley on 2010-02-11
Is there any clear and simple solution on this?

I am disappointed to be using Karmic Koala 9.10 as a Newbie to find hiccups like this.

Did I cause it by installing Medibuntu?

---

### Post by debiant on 2010-02-11
The high pitch effect is your sample rate being set to 46000!:-?


Right click on the volume icon (speaker, usually top-right of screen)-
click on "open volume control", the alsa-mixer control panel opens.
Then edit, preferences, and in the list;
scroll down to "clock internal rate" and check it (make it visible).
Close the preferences and return to the alsa-mixer control panel,
Click the options tab, the box "internal clock rate" needs setting to 44100 

If this doesn't match what you find in the menus or whatever-put a reply here with what you do see and when the e-mail ping's up here I'll come back and try again
:P

I'm in London UK so I'm here tonight Friday evening)!

I meant Thursday evening...I work shifts!

:roll:

---

### Post by JosephWheatley on 2010-02-13
Thanks for your reponse.
Right-clicking the sound symbol in my Karmic give options of "Mute" or "Sound Preferences"
I open "Sound Preferences" to see only the option of five tabs "Sound Effects", "Hardware ", "Input", Output" and "Applications"
None lead me to an option to change "Clock Internal Rate"
Alternatively I have installed "GNOME Alsa Mixer" from "Software Centre" - again I can't find "Clock Internal Rate" option just lots of sliders to push up and down. There are boxes to tick but not sure of their significance.

I came across some advice from this webpage [http://jg234.co.uk/2010/01/getting-the-e-mu-0404-pci-to-work-in-ubuntu/ ]("http://jg234.co.uk/2010/01/getting-the-e-mu-0404-pci-to-work-in-ubuntu/")(I don't have that particular sound card)
It suggested typing ***alsamixer*** into the terminal but yet again I couldn't find a reference to "Clock Internal Rate" or my sound card in the information that I went through by click the right arrow.

Also tried 
# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload
from [http://ubuntuforums.org/showthread.php?t=1280009](http://ubuntuforums.org/showthread.php?t=1280009)

**no success yet!**

---

### Post by underquark on 2010-02-13
I'm in Jaunty as per the post and can't find "clock internal rate" by following those instructions.

---

### Post by debiant on 2010-02-15
I gotta do some research on this!  I know we're on the right lines about the sample rate so its all about finding how to change it.
I'll post again as soon as I figure it out!  

:-s

---

### Post by pr92 on 2010-05-28
Any luck yet?

---

