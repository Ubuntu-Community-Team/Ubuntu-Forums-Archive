---
title: "Rhythmbox/Music Question"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by dswhite85 on 2008-07-13
I'm using Rhythmbox 0.11.5 for Ubuntu 8.04.1 and when I play a certain artist, and then try to play a different one, I notice that the audio level is not the same. I know for iTunes, when it imports music, it can automatically adjust the volume playback so all songs play at the same volume, and I'm looking for a Ubuntu equivalent or work around for that. My music collection is small right now, only 223 songs, the rest 4,000+ songs are still on my iPod, so would I need to convert my music files to ogg or another certain format to get that same volume level? As always any help is greatly appreciated, thanks.

---

### Post by chrisod on 2008-07-13
I believe Banshee and Amarok both have the volume leveling option when importing songs.

---

### Post by nowshining on 2008-07-13
well it depends on the kbps - the higher = the higher the volume and better, the lower= the lower the volume by default..

---

### Post by dswhite85 on 2008-07-17
Banshee 0.13.2 doesn't have any importing option that allows the volume for files to be the same. Any other help?

---

### Post by cariboo on 2008-07-17
You could try mp3gain to set the volume levels. It is available in the repositories, you can use Add/Remove Programs or Synaptic Package Manager o install it. It is a command line application, but it is fairly easy to use. In a terminal type:

```
mp3gain --help
```

or

```
man mp3gain
```

to get you going.

Jim

---

