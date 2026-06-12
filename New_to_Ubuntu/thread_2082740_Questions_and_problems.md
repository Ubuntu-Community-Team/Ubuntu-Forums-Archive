---
title: "Questions and problems"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by csergiu on 2012-11-10
Hello, I have just started using Lubuntu and I think I am in love with it xD, it's very fast and simple... just the way I like it. I have to mention that I am a complete beginner when it comes to Linux but that I have basic knowledge of PCs (former Windows user).

Here are my questions:
1. Do I need to update the Linux Kernel version? (current on my system: 3.5.0.18, and the current stable release on kernel.org is 3.6.6)

2.I've installed the application System Monitor from Lubuntu Software Center and it is showing me gnome 3.6.0 in the System tab although Lubuntu uses LXDE, so which DE do I have, gnome or LXDE?

Now here come the problems that I've encountered:

1. Cheese only shows a blank screen (I had Linux Mint Mate installed and there it would show me a green screen and crash and freeze the whole system entirely).

2. guvcview works but it shows the image upside down.

3. If I close the laptop lid and it goes into suspend it can't resume only if I shut it down from the button and I turn it back on, it shows me something like:
> [drm]nouveau: failed to idle channel 2
and some random greyish colors like it's trying to resume.

4. I don't know if I should post this here or on winehq but I'm trying to get GTA: San Andreas Multiplayer to work, I followed [this]("http://forum.ls-rp.com/viewtopic.php?f=63&t=239950") guide but I'm stuck on step 13, right after the logos the screen remains blank (this happens while on the nvidia drivers instead of the nouveau expermiental ones, but on those instead of the logos it would show me only a blank screen). I guess it's more complicated than this but what I'm trying to figure out is why both cheese and GTA San Andreas on Wine act the same and only show me a blank screen (on Linux Mint they would freeze the whole system).

I'm really sorry for the eventual mistakes but my mother tongue isn't english. Also, I hope you understand what I'm trying to explain in this post, I tried to explain it the best I could.

I hope the support of this community is as good as I hear it is :P
Thanks in advance!

P.S. I attached a lshw just in case.

---

### Post by ibjsb4 on 2012-11-10
Hi csergiu, welcome to the forums  :)

1. Do I need to update the Linux Kernel version?

Stick with what the lubuntu updater has to offer until you feel more comfortable with linux.  Even with a new stable kernel from kernel.org, there is still a chance of breakage.

 2.  so which DE do I have, gnome or LXDE?

You have both.  LXDE is your DE, but LXDE is built on the gnome environment.  This is true with all the spins (unity, xubuntu, and other distros).

A tip.  When you have many questions, its better to start separate threads in the proper subforum.  When others jump in to answer the conversation can get confusing.

---

### Post by csergiu on 2012-11-10
Thank you for your answer. I will post my problems in the correct sections.
I only wanted to update the kernel because I thought that was the cause of my problems, I'll stick with what the updater has to offer for now.

---

### Post by csergiu on 2012-11-10
Nice to see such a big and friendly community here.
I am running Lubuntu 12.10 and I'm having a couple of issues with the webcam.

I installed Cheese from Lubuntu Software Manager and when I open it all it does is show a blank black screen instead of live webcam image. This isn't a really big problem as I have guvcview installed by default that works (but the image is upside down) only that I'm just curious why it wouldn't work.

The real problem that I have and don't know how to solve is with guvcview: the image is upside down, how can I make it right without playing with the filters every time I launch it?

P.S. I want to mention that before Lubuntu I had Mint 13 Mate installed and when I ran Cheese instead of a blank black screen it gave me a green screen, a couple of flashes and after that a complete system freeze.

Thanks in advance!

---

### Post by grahammechanical on 2012-11-10
I do not use Lubuntu so I cannot give you Lubuntu specific advice. I do not see how any of your issues will be resolved by changing the kernel. Trying to do that might break the system if you get it wrong.

To help work out why GTA does not load you should open a terminal and try loading the program from there. You will then see error messages which might indicate what is causing the program to fail.

```
wine PROGRAM
```.

How did you install Cheese and guvcview? If you install applications from the Software Centre that comes with Lubuntu you will get applications that are compatible with Lubuntu.

I notice that Cheese is a Gnome application.

[http://projects.gnome.org/cheese/]("http://projects.gnome.org/cheese/")

May be Lubuntu does not have the requirements needed to run Cheese. Again you can try loading the program through the terminal. It might show error messages.

Regards.

---

### Post by Rex Bouwense on 2012-11-10
Guvcview is installed by default in Lubuntu.  It should be fine.  Not sure why the picture is upside down but you should see any errors if you start it via the terminal.

---

### Post by csergiu on 2012-11-11
Thank you for your answers!
Like I said, I ran Cheese in Linux Mint too and there it would crash the system entirely so my guess is that it has something to do with my laptop, probably missing drivers or something. Also, like ibjsb4 said above, LXDE is based on gnome so it can run any gnome application :D

Well, I ran guvcview from Terminal and I don't understand a thing about what those error messages mean, I'll post them here... also, when I invert the image from the Filters tab it is chopped in half and it moves randomly and somethimes it duplicates.

> guvcview 1.5.3
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
Init. USB2.0 1.3M UVC WebCam  (location: usb-0000:00:1a.7-2)
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
	Time interval between frame: 2/15, 1/5, 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
	Time interval between frame: 2/15, 1/5, 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
	Time interval between frame: 2/15, 1/5, 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 2/15, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 960 }
	Time interval between frame: 2/15, 1/5, 
{ discrete: width = 1280, height = 1024 }
	Time interval between frame: 2/15, 1/5, 
vid:04f2 
pid:b012 
driver:uvcvideo
checking format: 859981650
fps is set to 1/30
drawing controls

fps is set to 1/30
no codec detected for H264
no codec detected for MP3 - (lavc)
Checking video mode 352x288@32bpp : OK 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
 Could not grab image (select timeout): Resource temporarily unavailable
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
VIDIOC_QBUF - Unable to queue buffer: Invalid argument
Error grabbing image 
VIDIOC_QBUF - Unable to queue buffer: Invalid argument
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
VIDIOC_QBUF - Unable to queue buffer: Invalid argument
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
VIDIOC_QBUF - Unable to queue buffer: Invalid argument
Error grabbing image 
VIDIOC_QBUF - Unable to queue buffer: Invalid argument
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
 Could not grab image (select timeout): Resource temporarily unavailable
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
ioctl (-1069263343) retried 4 times - giving up: Resource temporarily unavailable)
VIDIOC_DQBUF - Unable to dequeue buffer : Resource temporarily unavailable
Error grabbing image 
write /home/csergiu/.guvcviewrc OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK


Thanks again for your answers!

---

### Post by mörgæs on 2012-11-11
Threads merged.
Please don't double-post.

---

### Post by csergiu on 2012-11-14
bump... doesn't anyone know how I can solve my problems, please?:(

Thanks.

---

