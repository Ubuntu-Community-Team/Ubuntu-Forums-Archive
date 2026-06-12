---
title: "Help with sound and and video issues in toshiba nb255-n250"
date: 2016-01-02
forum: New to Ubuntu
---

### Post by Amae on 2016-01-02
I have a Toshiba NB255-N250 as described in this thread, it came with Windows Starter but it was terribly slow, it was impossible to do anything so I decided to install Ubuntu. 

I can do almost anything now, although I have some issues when it comes to playing music and videos. 

For example, I have these mkv files, and when I try to reproduce them I get an error about hecv something. I have tried several ways to solve it, I have followed the steps here for instance: [http://askubuntu.com/questions/362745/how-to-install-h-265-hevc-codec-on-ubuntu-linux](http://askubuntu.com/questions/362745/how-to-install-h-265-hevc-codec-on-ubuntu-linux) 

But I've had not success, I also installed SMPlayer, and I can listen to the videos, but I can't see any image. 

My other issue is that the sound is very, very low. Even if it's at 100%. I have no clue how to fix this. 

I also have a question and if its possible to convert these, or any other video file to .avi format? Its just my dvd player aprrently won't read any other format :( 

Thanks so much in advance guys!

---

### Post by Bucky Ball on 2016-01-02
First off, do you have ubuntu-restricted-extras installed? If not, install it and reboot. Go through your tests again and let us know what works and doesn't.

You can use the Software Centre or in a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

As for low sound, have you got Pulseaudio Volume Control installed? If not, you can install and have a tweak in there. Get an audio stream running (play music or a video with audio), check the 'Output' tab and look for the stream from the app you are using (if you were using VLC, for instance, that stream will appear in 'outputs' and, hopefully, 'playback' tabs).

Have a look at what device the audio is being streamed to. Experiment and see if you can make any improvements.

---

