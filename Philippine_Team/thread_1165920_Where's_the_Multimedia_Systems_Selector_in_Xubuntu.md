---
title: "Where's the Multimedia Systems Selector in Xubuntu?"
date: 2009-05-21
forum: Philippine Team
---

### Post by SHENGTON on 2009-05-21
Hello guys, good day.

I'm having problems here with my Xubuntu 9. 04 when playing videos and audios. When I tried to play videos and audios, the Movie Player will open for awhile and then it will just close. VLC Media Player could play audios but when I tried it with videos same with Movie Player. Both Movie Player and VLC Media Player will automatically close when playing videos and audios.

My kernel version is 2. 6. 28-11-generic.

In Ubuntu, I solved my problem by going to System => Preferences => Multimedia System Selector and changed the video output to something other than auto detect. But there's no Multimedia System Selector in Xubuntu.

How I will gonna solve this problem?

Hope someone will help me with this.

Take care and God bless.

---

### Post by loell on 2009-05-21
the system _multimedia_ selector is just,

**gstreamer-properties**

you could execute it through command line or any launcher.

---

### Post by SHENGTON on 2009-05-21
Thanks loell, that's helps a lot.

Take care and God bless. :)

---

