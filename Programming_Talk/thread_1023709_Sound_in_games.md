---
title: "Sound in games"
date: 2008-12-28
forum: Programming Talk
---

### Post by Emill on 2008-12-28
Hello. I want sound and music in my games. I've tried sdl_mixer but I get too much latency on the sound effects, and if I change the buffer size, the quality on the music gets too bad. I use midi music and wav sound effects. What to do?

---

### Post by slavik on 2008-12-28
I think there is a separate sound library for SDL ... SDL_sound I think.

I believe that for wav, you have to preload the sound and then tell it to play, or some such.

---

### Post by Emill on 2008-12-28
I can't find any examples for SDL_sound how to play sounds. I don't see any "PlaySound" function in the API documentation.

---

### Post by cb951303 on 2008-12-28
> **Emill said:**
> I can't find any examples for SDL_sound how to play sounds. I don't see any "PlaySound" function in the API documentation.

you can try OpenAL?
Devmaster has a series of openal articles: [http://www.devmaster.net/articles.php](http://www.devmaster.net/articles.php) (at the bottom)

---

### Post by Emill on 2008-12-28
OpenAL seems to have too much latency too when I test this: [http://www.devmaster.net/articles/openal-tutorials/lesson1.php](http://www.devmaster.net/articles/openal-tutorials/lesson1.php)

I compare with an old DirectX 5 game I run in wine, and that has almost no latency.

---

### Post by cb951303 on 2008-12-28
I tried both couple of months ago and never had latency problem. are you sure it's not something with your system rather than the libraries?

---

### Post by Emill on 2008-12-28
How many ms is your latency? Mine is about 200 ms for OpenAL. How can I see if I have done something to my system? I use PulseAudio.

---

### Post by cb951303 on 2008-12-28
> **Emill said:**
> How many ms is your latency? Mine is about 200 ms for OpenAL. How can I see if I have done something to my system? I use PulseAudio.

I don't know now it was a couple of months ago and I don't have the codes now but latency was not noticeable. 200ms is noticeable though. 
are you using 8.10. PulseAudio was very buggy in early versions and it got really really better in 8.10 (Still it needs works though)

---

### Post by Emill on 2008-12-28
I changed the settings in SDL_mixer to
Mix_OpenAudio(44100, MIX_DEFAULT_FORMAT, 2, 1024)
and now it's OK. It could have been better but this works :)

---

