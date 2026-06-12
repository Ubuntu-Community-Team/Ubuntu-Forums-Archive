---
title: "Realtek ALC268 Simple Please"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by borisagrees on 2008-05-14
Please help i ahve been looking all over the net and can really find anything i am brand new to ubuntu and dont want to ahve to script. I have installed the drivers from the Realtech webiste but nothing happened. the sound card will not give me sound and when i open sound properties none of the mixes including ALSA work. Please help me and keep it simple as i am a n00b to ubuntu:)

---

### Post by bjm1904 on 2008-05-14
I had the same issue. Here's how to solve it:

Open a terminal session:

sudo su
<type in passord>
sudo gedit /etc/modprobe.d/alsa-base

Then, at the end of the file that pops up (as in right at the bottom) add:

options snd-hda-intel model=lenovo

This worked for my laptop with integrated sound (I'm pretty sure it's an ALC286). I've yet to get the headphones or microphone to work, but if you find that things are a bit quiet, open up your volume control (hit 'edit > preferences...' and allow yourself to view plenty of options), and head to system > administration > services and allow the volume control/alsa-mixer service.

Let me know how you get on!

---

### Post by borisagrees on 2008-05-14
i have done what you sid but in sound when i test ALSA it said

audiotestsrc wave=sine freq=512 | audioconvert| audioresample| gconfaudiosink profile=chat: Could not open resource for writing.

Please help but keep it simple

---

### Post by bjm1904 on 2008-05-19
and you definitely added that line to the BOTTOM of the file?

I'm sorry I was unable to help you - especially as I had uncovered a way of getting the headphones working. You could always try '3stack' or 'auto' instead of 'lenovo' also.

Let me know how you get on! :(

---

### Post by blackduck on 2008-05-24
[FONT="Arial"][SIZE="4"]The Realtek ALC268 in my Acer Travelmate 6492 (Centrino pro, 2gb Ram) is not responding as anticipated. The Notebook dual boots to winxp pro or Ubunto 8.04.
I first installed 8.04 on my desktop, AMD-64 Athlon, & all went swimmingly. The peripherals, Canon ptr, Logitech webcam, Acer scanner, etc were all recognized. The AMD installation indicates the snd sys is Realtek ALC850 which works well using snd recorder & even a connect to Ekiga.
So I followed the same road to installing 8.04 (using i86 image) on the notebook. All but the snd performed - a clicking static noise is the constant fruit of my efforts in snd recorder, even after numerous combo changes in system/pref as well as the right click route on vol ctrl, mic boost, capture, etc choices. I am left with clicking static thru' out the boot sequence, so much so that the start up wav file music is barely recognizable.
My limited Linux experience leads me to conclude that drivers for ALC268 have not been installed, indeed, may not yet be available which leads to my 2nd problem.
The notice icon for updates available lights up every time I boot. The first time there were 8 but Update mgr did not download. The updates grew to 10 and now are at 18 and still update mgr freezes when commanded to download & install. Mayhap the snd problem will be solved if I could get update mgr to perform. I confess that at age 77 my thinking is not as acute as days of yore so a boost for grampa would be welcomed.[FONT="Arial"][/FONT][/SIZE][/FONT]

---

### Post by bjm1904 on 2008-05-27
I'll try to answer those one at a time!!!

You could try things through the terminalc if update manager isn't helping. Open a terminal (Applications > Accessories > Terminal) and type

sudo su
sudo apt-get updates
sudo apt-get upgrade

Sometimes working through the terminal can produce better results. Also, make sure that your System > Administration > Software Sources is set up correctly.

Another attempt to try to solve your sound problem would be for you to try typing the following into another terminal:

alsamixer

This will bring up an interesting looking screen. Use the arrow keys to move around and adjust volumes, and press 'm' on every entry that says 'MM'. Press 'Esc' to save and exit. This will allow more channels in your volume control. Unmuting various channels in your volume control will create different results. I can't give a definitive guide to this as it's different with each system, but a bit of experimentation might just lead to your sound working!

---

### Post by Raistlin82 on 2008-05-29
Hi there, just wondered what you did to get the headphones working.  On my laptop the sound comes out both speakers and earphones, it just doesnt seem to sense the jack.  I've looked under preferences etc and looked at the switches tab but have no headphone detected :-(

---

### Post by bjm1904 on 2008-05-30
Head to Volume Control > Preferences.

Enable the 'switches' channel, and then check the 'headphones' option.

I'm pretty sure that this is probably all you have to do - let me know how you get on!

---

### Post by Raistlin82 on 2008-06-03
Hi there, after adding the line 

options snd-hda-intel model=auto


to alsa base i got the headphone option added to the swithces.  However it now only auto senses the headphones about half the time, the rest of the time i have to mute "front" speakers, still its now workable! cheers for the reply!

---

### Post by bjm1904 on 2008-06-03
I'm glad to help - If I find a solution I'll let you know!

Enjoy your music!

---

### Post by alexander1 on 2008-09-04
Hi, 
I have bought a Dell Vostro 1510 and I didn't got my Mic (intern and extern) working with alsa.
But with oss I could get my extern mic working.

Here is a little tutorial how it worked for me:

- In the alsa-base: options snd-hda-intel model=dell
- set the record devide (in System->Settings->Audio) to oss.

Then you have to change the input device in Audacity to oss.

Then the Mixer: 
Unter the Kategory "Output":
- Turn everything on except the Boost's

Unter the Kategory "Record":
- Turn everything on except the Record1 Mic Symbol

Unter the Kategory "Options":
- Turn everything to Mic


I hope, I could help you a little bit.

Greetings Alexander

---

