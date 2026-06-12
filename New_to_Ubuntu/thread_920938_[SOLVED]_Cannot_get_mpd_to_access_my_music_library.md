---
title: "[SOLVED] Cannot get mpd to access my music library"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Eureka? on 2008-09-15
I am a complete newbie trying to make MPD work. 
I´ve done every step recommended to configure MPD, installed, compiled, client gets connected but cannot access my music nor browse. I have checked the config file several times and everything seems to be alright.. Can anyone help me to diagnose the problem please?

---

### Post by Eureka? on 2008-09-16
The problem was that mpd was lacking FLAC and MP3 libraries (by using the mpd --version command the supported formats are displayed) . I installed them, recompiled and got it working.

---

