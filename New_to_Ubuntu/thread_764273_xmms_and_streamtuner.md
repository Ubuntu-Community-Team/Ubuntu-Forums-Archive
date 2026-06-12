---
title: "xmms and streamtuner"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by phoenixrising888 on 2008-04-23
got everything going with xmms and streamtuner but when i go to listen to a live stream i cant do it.when i click on a stream and click tune in another box pops up and says couldnt open audio.not sure what to do from here.

---

### Post by spiderbatdad on 2008-04-23
do you use totem? I have changed the settings in streamtuner preferences to totem and it works fine...also use streamripper to save streams.

---

### Post by phoenixrising888 on 2008-04-23
do i just install totem?will it show up in my streamtuner preferences?how do i change the settings?

---

### Post by nicedude on 2008-04-23
I am not sure about your intended use but I am listening to an internet streaming radio station while I type this and I only have XMMS not streamtuner. But if your wanting to do something different than me I am not sure what it takes. I just listen to a station where you click on a "listen live" link in a web page & open it with XMMS and it works fine. Thought I might just tell you encase you just click a link to listen as well.

---

### Post by spiderbatdad on 2008-04-23
Totem is the default movieplayer in your Sound&Video menu. To change in streamtuner, click edit>>preferences. Double click the lines where you have xmms %q and change to totem %q . You will also need to add the last line you see in my screeshot To Record a stream if you want to use streamripper.
Restart the player for settings to take effect.

---

### Post by phoenixrising888 on 2008-04-23
well when i changed the xmma% to totem and i clicked to tune in it open a video player

---

### Post by spiderbatdad on 2008-04-23
totem also plays audio files and includes a nice virtualization. Are you saying you have no sound?

---

### Post by phoenixrising888 on 2008-04-23
nope no sound.when i open streamtuner click on the station i want to listen to and xmms pops up but it couldnt open audio.

---

### Post by spiderbatdad on 2008-04-23
try ```
sudo apt-get install ubuntu-restricted-extras
```I believe that contains audio codecs you may be missing.

---

### Post by phoenixrising888 on 2008-04-23
i tried that code but it still doesnt have audio

---

### Post by spiderbatdad on 2008-04-23
Sorry I can't help with xmms, as I don't use it. I do use streamtuner with totem. I know the first time I changed the preferences to totem from xmms, it didn't stick. I had to go back and change them again...in both places where xmms is listed. Since then, no problems. Good luck.

---

### Post by rustutzman on 2008-04-23
Have you checked to see output you're set to? In xmms if you go in to "Options"/"Preferences" than look at the "Output Plugin" you can set this to whatever configuration you're running.

Russ

---

### Post by mrreality13 on 2008-05-11
just wanted to say thanx this worked great for me i havent played with  ubuntu for over a year:) 
I do have a question how do i use streamripper with totem?

---

### Post by spiderbatdad on 2008-05-11
> **mrreality13 said:**
> just wanted to say thanx this worked great for me i havent played with  ubuntu for over a year:) 
I do have a question how do i use streamripper with totem?

It just works. Set Edit>>Preferences up in streamtuner like the screenshot below. Stream will be saved to a file in your home directory.

---

### Post by spiderbatdad on 2008-05-11
> **mrreality13 said:**
> just wanted to say thanx this worked great for me i havent played with  ubuntu for over a year:) 
I do have a question how do i use streamripper with totem?

It just works. Set Edit>>Preferences up in streamtuner like the screenshot below. Stream will be saved to a file in your home directory.

see also the "record a stream" line at the bottom of the list.

EDIT: opps double post.

---

### Post by mrreality13 on 2008-05-12
thanx!!:popcorn:

---

