---
title: "Can't get Skype to work at same time as Flash (youtube) -- sound conflict issues."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by nicholasperry on 2008-07-08
I just installed Linux Mint and I've been having what I think are essentially sound conflict troubles.

I got Skype installed pretty quickly no problem with a .deb file, and I was also able to get flash installed so I could watch videos on Youtube.

Whichever one I choose first will work, but will make it impossible to use the other.

For example, I'll sign on Firefox and watch a youtube video. Then when I try to make a call on Skype, I get an error message that says "Problem with Audio Playback", and I'm not able to make the call. It is also impossible for other people to call me. They get some sort of error message explaining that I can't be contacted.

However, as soon as I close the Firefox tab where I have Youtube running, I am suddenly able to make calls on Skype again.

Now Skype will work but Youtube won't work. If I play something on Youtube, the video aspect of it will work and the red bar will load, but there will be no sound, and after exactly two seconds the video will just freeze. I am able to scroll around in the video, and even press play (the video will play for another 2 seconds without sound, and then freeze again), but I can't get any sound.

If I shut down Skype and then try playing another Youtube video, the video will work just fine.

So I think there must be a sound conflict issue. Skype and Flash must be trying to use the same Sound Out sound device, or something, but I don't know how to fix these things.

I've tried fiddling around with like, going into my Skype options, selecting "Sound Devices", and selecting the various weird options they have for "Sound Out" (stuff like "ATI IXP (hw:IXP,0)" or ATI IXP (plughw:IXP,0)" and a bunch of others like that), and that doesn't seem to work.

I thought of trying to change things within Flash but I can't figure out how to access the plugin and change sound settings and stuff.

So basically I suspect both Skype and Flash are fighting over the same sound stuff and I need to figure out a way to mediate the dispute.

~~~

By the way, I just noticed that Skype seems to like to fight with other stuff for control of the sound. I just tried playing an mp3 off of the included Rhythmbox Music Player software while talking on Skype, and it wouldn't play. I stopped talking on Skype and Rhythmbox played the mp3 just fine. Tried to make a call while listening to an mp3 on Rhythmbox and Skype said the usual "Problem With Audio Playback".

Hey! Just noticed same thing with Pidgin. Normally it makes little beep sounds when I send or receive messages, but that won't happen while I'm making a Skype call.

And it's gotta be Skype that's messing everything up, because when I play an mp3 off of Rhythmbox Music Player, I still hear those Pidgin message sounds. I can even have a Youtube video playing successfully at the same time I'm listening to stuff off of Rhythmbox.

What is Skype doing to my sound, and how do I set it straight?!

Thank you!!!

---

### Post by rockerphil on 2008-07-08
i have the same issue with my XMMS media player, when i play a YouTube vid i can't run my XMMS, i get an error about configuring my sound device and making sure it's not blocked, and as you said i've tried fiddling with it, but unfortunately it seems like i can only run one app that requires the sound card at one time and can't run anything else requiring the sound card without first closing out the other app, so unfortunately it's somthing you just have to accept, at least it seems that way for me. sorry

---

### Post by bryncoles on 2008-07-08
have you installed libflashsupport from synaptic? if not, do so! it should help...

i had trouble running two programs which use sound, until in realised i had to install flash support separately!

---

### Post by inxs44 on 2008-07-31
The problem isn't Adobe Flash it's PulseAudio Sound Server. Both Sabayon Linux 3.5 and gOS Spaces 2.9 (Which is based on Ubuntu 7.10) are able to run Skype and a YouTube videos at the same time. What both these distros have in common is that they do not use PulseAudio Sound Server. Perhaps someone more experienced could tell us how to uninstall PulseAudio Server and replace it with Enlighten Sound Daemon which is used by both Sabayon 3.5 & gOS Spaces 2.9

---

