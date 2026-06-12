---
title: "No Sound while playing any media."
date: 2011-11-27
forum: New to Ubuntu
---

### Post by ask_ on 2011-11-27
Hello, I am running Lubuntu on a HP pc with intel processor.

Upto half an hour ago, my speakers were running properly. But now they don't seem to work. I replaced speakers by headphones, and those are also not giving any output. 

I wish to know how to check if sound card is not working.

I did an lspci and aplay -l and the sound card was listed in the output,is it possible that the sound card is damaged, even if it is detected?

I am not at all sure whether problem is at software level or at soundcard level.

Please help.

---

### Post by Rex Bouwense on 2011-11-27
So, half an hour ago (plus or minus) your speakers were working and then suddenly they stopped working.  Can you get sound out of any program?

---

### Post by ask_ on 2011-11-28
No , I am unable to get sound out of any program.

As you know (from another post where you helped me), I installed a new program system monitor, before I installed it they were working , after I installed it they have stopped working.

It may be a complete co-incidence, but I want to make sure whether this is not a software issue.

Since it happened in the recent past I think it may be because of a software/driver issue. I may be completely wrong and I may have to replace my sound card, but when I tried out aplay -l I got following output :-

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also I read some of the following thread,

> **LordRaiden said:**
> 
A very common cause for a user to not have sound is not having his/her username in the /etc/group.

Thanks to **rustybutt** for this simple check.

```
grep 'audio' /etc/group
```

You should see a line similar to ```
audio:x:29:
``` followed by a username i.e. if the username is "ubuntu" then you should see ```
audio:x:29:ubuntu
```. If you see something else i.e. ```
audio:x:29:root
``` you should add your username to the file by doing ```
 sudo nano /etc/group
```. Now find the line that looks like ```
audio:x:29:root
``` and change it to ```
audio:x:29:root:moocow
``` only replacing moocow with your real username.

Hit CTRL + 0 to save, then CTRL + X to exit. That's the end of that :-D 

[/SIZE]



In my group file audio: x:29 was followed by 'pulse', I changed it to my username, but didn't get any positive results. I checked the first few steps of that guide but what they suggest is working fine on my system, i.e aplay -l is able to detect soundcard, Alsamixer shows all the volumes as unmuted.

---

### Post by ask_ on 2011-11-28
update:

A funny thing is happening.

I checked the alsamixer settings. They were ok. Then I checked vlc media player settings, in it I changed the default output module to ALSA output module. Then I inserted a pair of headphones , lo and behold, I got sound in my headphones.

But, whenever I play youtube videos ,I am not getting any output. 

This means at least soundcard is working. But why aren't youtube videos being played?

---

### Post by Rex Bouwense on 2011-11-28
Have you installed Ubuntu restricted extras?

---

### Post by deadcatt on 2011-11-28
whoop whoop finally i find a tread with the exact same problem i just rebooted my laptop and boom the sound was not working, it works with skype because i changed the audio device but like you ask_ i dont get any audio from youtube or any other application that does not have audio setting.
lspci and aplay -l shows my audio device just like yours.

im farly new to linux and dont have a clue what to do next! hope we get some answares 


whats with the ubuntu restricted extras ?

---

### Post by ask_ on 2011-11-28
> **Rex Bouwense said:**
> Have you installed Ubuntu restricted extras?

Thanks for replying. Your help on some of my other threads was very useful. :D


One thing , I would like to point out, as I mentioned in first post,the sound was working fine till morning. All kinds of sound were well supported till then, be it flash/youtube or vlc media.

Then as I mentioned, sound went off , then I did that ALSA thing on vlc, and it is working well.

Do I still have to install Ubuntu restriced extras ? I mean is there a way to see if it is already installed ? For I was able to hear youtube earlier.

I have a hunch something is simply wrong with the flash settings,I maybe wrong here.I am not averse to trying out Ubuntu restricted extras, and will do so,it's just that I am afraid I may mess up with some codecs while installing. :)

---

### Post by Rex Bouwense on 2011-11-28
I have always had to install restricted extras for video and audio on U-Tube.  It has always worked for me after I installed.  Where are you located?  The codecs are restricted in some countries.

There is a thread that you might be interested in reading since you are using Lubuntu:

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

---

### Post by ask_ on 2011-11-28
> **Rex Bouwense said:**
> I have always had to install restricted extras for video and audio on U-Tube.  It has always worked for me after I installed.  Where are you located?  The codecs are restricted in some countries.

I am located in India.

But I was able to play all videos and sound successfully, till yesterday, so restriction must not be an issue in my country.

---

### Post by ask_ on 2011-11-30
I tried to study a lot of stuff on ALSA and Pulse Audio, but the configuration settings , I wasn't able to understand, as there were many webpages dedicated to it. I simply didn't know what my problem required.

Then I came across the solution proposed in the following quote:-


> **Lisiano said:**
> I have a feeling either pulseaudio or chromium is remembering that you tried using HDMI audio and is staying on it. I would suggest downloading [pavucontrol]("apt://pavucontrol") by either just clicking the name or typing this in a terminal
```
sudo apt-get install pavucontrol
```
After it installed, just run it using either Alt+F2 or a terminal and just type ```
pavucontrol
```
Now open up chromium and find wherever you can't hear sound and tell chromium using pavucontrol to use your speakers or whatever you use.


I did exactly as I was told to do there, and now flash is playing sound effortlessly.

I guess, since I am a beginner, what I needed was a simple GUI based tool, and that is what the solution in the quote provided.

---

### Post by Rex Bouwense on 2011-11-30
Great!!  Did you install the Ubuntu restricted extras or merely do what you said in your post?

---

### Post by Lisiano on 2011-11-30
> **ask_ said:**
> No , I am unable to get sound out of any program.

As you know (from another post where you helped me), I installed a new program system monitor, before I installed it they were working , after I installed it they have stopped working.

It may be a complete co-incidence, but I want to make sure whether this is not a software issue.

Since it happened in the recent past I think it may be because of a software/driver issue. I may be completely wrong and I may have to replace my sound card, but when I tried out aplay -l I got following output :-

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also I read some of the following thread,



In my group file audio: x:29 was followed by 'pulse', I changed it to my username, but didn't get any positive results. I checked the first few steps of that guide but what they suggest is working fine on my system, i.e aplay -l is able to detect soundcard, Alsamixer shows all the volumes as unmuted.

I should point out that unless Lubuntu does it's Pulseaudio settings differently, you should undo your change to the audio group and make sure "pulse" is the only member of the audio group. Also glad that my tip worked.

---

### Post by ask_ on 2011-12-01
> **Lisiano said:**
> I should point out that unless Lubuntu does it's Pulseaudio settings differently, you should undo your change to the audio group and make sure "pulse" is the only member of the audio group. Also glad that my tip worked.

Yes , I had made changes to audio group , but since that didn't work , I reverted back to pulse. I had also made changes to VLC media player settings.Now I have reset preferences in VLC too , just to be safe. I was quite worried that something may be wrong with my soundcard, so it is a relief. :)

> **Rex Bouwense said:**
> Great!!  Did you install the Ubuntu restricted extras or merely do what you said in your post?

I merely did what I said in the post. I was thinking of installing restricted extras , but when I read the community page for it I got the feeling it would install some codecs. 
But then , my system was able to play sound on flash a few days back , so I thought that it was unlikely that it was a case of missing codec. Probably,something was wrong with the settings. 
The tip about pavucontrol worked ,thankfully. :)


Thanks everyone on this thread, for taking the time to investigate my problem.:guitar:

---

