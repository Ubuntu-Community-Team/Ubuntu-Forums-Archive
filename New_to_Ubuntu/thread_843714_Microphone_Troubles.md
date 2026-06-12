---
title: "Microphone Troubles"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by napalm brain on 2008-06-28
I will make this short and sweet:

I tried to use Sound Recorder and I got absolutely no playback aside from nasty static. I checked my Alsa Mixer and Volume Control to see if something was muted but no. In fact, in the Volume Control, there is absolutely no tab for the microphone.

Anyone have any ideas?

---

### Post by markbuntu on 2008-06-28
What model of computer are you using?
Is the microphone a USB mic?

---

### Post by aktiwers on 2008-06-28
Is it pluged in "in front" of the computer?

If you double-click the sound icon in your panel and pick settings=>properties

You can add "mic select" and then pick Mic2. That always works when I plugin mics in front..

But then again, this is when you it in front.

Also make sure that SoundRecorder is set to the correct input!

---

### Post by napalm brain on 2008-06-29
No, it is not an USB mic. It is built into my laptop. And my laptop is a *VAIO VGN-FZ190*.

---

### Post by aktiwers on 2008-06-29
Sometimes that is seen as "in front" as well. Have you tried what I said before? :)

---

### Post by napalm brain on 2008-06-29
lol, I am sorry. I'm usually not this thick. I attached what I see to this post.

---

### Post by aktiwers on 2008-06-29
Yes click on "Edit" in that window and add "microphone select" or "mic select" or whatever it is called :)

Then a new tab should show up, and you can pick "mic2"...  I have fixed a problem like yours doing this.

---

### Post by napalm brain on 2008-06-29
Not there. 

I figured there was some package or driver that needed to be installed. I'm just unclear on *what* to get or install.

---

### Post by chyneymon on 2008-06-29
Hey I had this problem too when speaking on Skype - For some reason, the Alsa Mixer settings got changed. The following worked for me though: 

Open the Alsa Mixer control panel. Go to Edit --> Preferences and make sure the appropriate boxes are checked. I noticed that in my case, the front mic was not checked. I checked it. then close. 

then, go into the options tab, and make sure that the input source is the right one. Again, I had to select front mic.

See if that works for ya.


Whoops sorry, 
I just looked more closely at the above post. You probably already tried this.

---

