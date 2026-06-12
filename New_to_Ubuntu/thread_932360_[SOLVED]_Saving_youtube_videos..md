---
title: "[SOLVED] Saving youtube videos."
date: 2008-09-28
forum: New to Ubuntu
---

### Post by ellalan on 2008-09-28
Hi
Could someone tell me how can I save youtube videos in my hard disc please.
My OS is Hardy Heron 8.04. TIA.

---

### Post by conphara on 2008-09-28
That's so easy to do. I have two apps for that. The best one is called PyTube Multimedia Converter, I got it from getdeb.net, maybe it's in Synaptic I don't know.
[http://www.getdeb.net/app/PyTube]("http://www.getdeb.net/app/PyTube"). Just choose Download videos in the start menu and add the youtube video address. The app is being placed in Sound and Video.
The other is Qttube, not as good, but still good enough.

---

### Post by Biggy on 2008-09-28
Install [QtTube]("https://wiki.ubuntu.com/QtTube") from synaptic.

System > Administration >Synaptic package manager and search QtTube and mark for installation

---

### Post by mike1234 on 2008-09-28
> **ellalan said:**
> Hi
Could someone tell me how can I save youtube videos in my hard disc please.
My OS is Hardy Heron 8.04. TIA.


 If you have FF 3 install this and install ffmpeg in synaptic. You can setup this app to save as .avi or .mov, etc. Whatever you want. It's a great applicattion. 

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

M.

---

### Post by wesley_of_course on 2008-09-28
Download Helper works also . It'll even convert them to .avi ' s and save them to wherever U want . Works with Firefox . 
                    [http://www.downloadhelper.net/index.php](http://www.downloadhelper.net/index.php)

        Enjoy .

---

### Post by jamesrfla on 2008-09-28
I install the download helper add-on for Firefox then download the you tube video or any other web video. Then use the default video player in Ubuntu to play them. You will need to download some code to play the .flv files but the player will direct you to what you need to do. Good Luck!!

---

### Post by steveneddy on 2008-09-28
> **mike1234 said:**
> If you have FF 3 install this and install ffmpeg in synaptic. You can setup this app to save as .avi or .mov, etc. Whatever you want. It's a great applicattion. 

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

M.

Thank you for this.

I was looking for this just last night.

This helps me very much.

---

### Post by spiderbatdad on 2008-09-28
youtubedl works great, but another very simple way is to launch gksu nautilus then view a video with your browser. With the file browser go to /tmp copy/paste or drag/drop the file to your desktop.

---

### Post by Sealbhach on 2008-09-28
> **wesley_of_course said:**
> Download Helper works also . It'll even convert them to .avi ' s and save them to wherever U want . Works with Firefox . 
                    [http://www.downloadhelper.net/index.php](http://www.downloadhelper.net/index.php)

        Enjoy .

+1 to that. If you see something you like you can just grab it.

Very easy and hassle free.

.

---

### Post by HittingSmoke on 2008-09-28
> **ellalan said:**
> Hi
Could someone tell me how can I save youtube videos in my hard disc please.
My OS is Hardy Heron 8.04. TIA.

I've got a better solution that any in this thread.

Provided you're using Firefox and have the [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") add-on installed (which you should) just install this script into Greasemonkey. [http://userscripts.org/scripts/show/13333](http://userscripts.org/scripts/show/13333)

It not only allows you to download, but lets you select different formats, resize video, choose higher quality if its available and really cleans up the video viewing page to make it more enjoyable.

All of this, right from your Youtube page, no encumbering download managers to install. Every Youtube user should be running this script.

---

### Post by Sealbhach on 2008-09-28
> **HittingSmoke said:**
> I've got a better solution that any in this thread.

Provided you're using Firefox and have the [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") add-on installed (which you should) just install this script into Greasemonkey. [http://userscripts.org/scripts/show/13333](http://userscripts.org/scripts/show/13333)

It not only allows you to download, but lets you select different formats, resize video, choose higher quality if its available and really cleans up the video viewing page to make it more enjoyable.

All of this, right from your Youtube page, no encumbering download managers to install. Every Youtube user should be running this script.

Thanks. I've tried it, but it won't play videos or sound - just silent white area where the video should be. The download links appear, and all the other script features. I've got Flash 9 from the repos.


.

---

### Post by ellalan on 2008-09-28
Hi
I have downloaded and installed this but I do not know how to convert the .flv files to .avi using this [http://www.downloadhelper.net/index.php](http://www.downloadhelper.net/index.php).
How do I enable my movie player to play .flv files. I do appreciate your help.

---

### Post by SuperSonic4 on 2008-09-28
VLC plays them as flv files.

Does Avidemux or FFMpeg convert them for you? Normally I just do an audio rip using pacpl converter

---

### Post by Sycron on 2008-09-28
You don't need any softwares to save movies from websites. They are saved on your /tmp directory.

---

### Post by ellalan on 2008-09-28
Hi SuperSonic4,
I can see it playing in VLC but without any sound, is my VLC broken or do I need to change any settings, Thanks for the Help.

---

### Post by SuperSonic4 on 2008-09-28
flv files play perfectly in my VLC. I assume the streaming sound is ok on the video. Do you have any other audio troubles? Sometimes it's as simple as forgetting to put something in headphones out (happened to me)

I believe you can change the transcode options in tools -> addons -> Downloadhelper in firefox

---

### Post by Sycron on 2008-09-28
I can see them too.

---

### Post by ellalan on 2008-09-28
Hi
In fact, I have no sound in VLC,gXine,movie player,Exaile and Rhythmbox but I can play Youtube videos without any problem. I have installed Greasemonkey and Downloadhelper installed. I have installed FFMpeg in Synaptics as well. Any ideas please.

---

### Post by SuperSonic4 on 2008-09-28
Hmm, so flash works but audio doesn't?

Have you tried installing the audio codecs?


```
sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs
```

Source: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by ellalan on 2008-09-28
Everything got fixed, Thank you all for helping me out. Its Brilliant.

---

### Post by Sycron on 2008-09-29
We'll we're glad that can help people.

---

