---
title: "Audio programming with Mono/C# (For a novice)"
date: 2007-07-20
forum: Programming Talk
---

### Post by happysinger on 2007-07-20
Hello!

I'm teaching myself desktop GUI programming for the first time (after a couple of years with PHP). I plumped for C# and Mono. It's also my first time writing object-oriented code, so I'm having a big adventure and loving every second.

So far, I've managed to solve every problem I've met by searching and reading as much as I can. Now I've got a tricky stumbling block. The program I'm writing will involve basic audio editing, and here's the big problem. Any time I try to Google for audio-programming advice, the word 'Mono' obviously scuppers it! I so wish they'd used a made-up name sometimes! :)

I have managed to decipher the WAV file format, and can play back to a certain extent by sending bytes directly to /dev/dsp via a FileStream but I'm sure I'm approaching this the wrong way. I'd be grateful for pointers in the following directions:

1. What is the best general way to capture/play back sound using my soundcard from a Mono/C#/Gtk#/Linux app? E.g. Should I be using ALSA, Jack or something else?

2. Do I need more packages or just a reference to make this functionality available to my app? Am I right in thinking the process is similar to including Gtk in my program? In short: what do I do?! :)

3. I might want to port the app to Windows later: how big a consideration is this (from an audio point of view)?

4. Does anyone know any good online resources for the sort of stuff I'm talking about? Again, my biggest problem is trying to get good results from Google with search terms like 'Mono audio programming'...

Thank you for being wonderful. Sorry for being vague. I love Ubuntu and Ubuntu people.

Dave

---

### Post by kknd on 2007-07-20
You can use gstreamer. [http://www.mono-project.com/Gstreamer](http://www.mono-project.com/Gstreamer)

---

