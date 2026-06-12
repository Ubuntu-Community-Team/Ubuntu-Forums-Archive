---
title: "sound recorder that records audio from computer"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by ontherooftop on 2008-06-10
I want a sound recorder from synaptic package manager that 
would record sounds not from me , but music from youtube that I 
can record and make it like a mp3 or .wav any help , thanks, Im
learning more everyday.

---

### Post by spiderbatdad on 2008-06-10
ffmpeg will do this. And youtube-dl.

Also someone pointed out once...go to /tmp with gksu nautilus and grab the file once it finishes loading.

---

### Post by logos34 on 2008-06-10
audacity 

or

gnome-sound-recorder

sudo apt-get install gnome-media

set input to mix, I believe, and format as mp3, wav, whatever

---

### Post by bluepowder7 on 2008-06-10
i think ffmpeg can extract the audio.  it's a manual program, so you'd need to run it from the terminal, but it's fairly easy.


first, install ffmpeg using synaptic

then open the terminal and type "man ffmpeg"

when done reading, press the Q key to exit the manual and get back to the prompt

if you need to repeat a previous command in the terminal, use the UP arrow key to view past commands - it stores a bunch of history for quick recall

---

### Post by logos34 on 2008-06-10
> **spiderbatdad said:**
> ffmpeg will do this. And youtube-dl.

you mean it grabs the stream like mplayer -dumpfile as mp3 (no converting needed)?

---

