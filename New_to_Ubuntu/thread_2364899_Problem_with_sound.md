---
title: "Problem with sound"
date: 2017-06-29
forum: New to Ubuntu
---

### Post by mac187 on 2017-06-29
Hi, i just installed Ubuntu 16.04 LTS on my machine, but i have problem when i use Skype, on windows its works great, but in Ubuntu, when i speak with my family living in Dubai, they can hear me, but i cant hear them, sound is lagging , anyone know how to solve it ?

Is it better to install realtek? i have seen that Puleadio make issues with ALSA, maybe i need to remove Pulseadio and alsa and install realtek drivers for linux ? or ? does anyone know how to make my audio card in laptop work perfectely ?

Thanx

---

### Post by Autodave on 2017-06-29
I personally have had no problems with *pavucontrol *(pulse audio) on any machine. Have you gone into Pulseaudio to confirm that the proper input is selected? You need to make sure that *Input devices *is properly looking at the correct device, that *playback *also has correct device, and that* configuration *is also correct.

Please post some specs on you machine: that may also help some one here figure out your problem.

Do you have another computer that you can run Skype on and play with the configuration on your machine?

---

### Post by Autodave on 2017-06-29
Thought of something else: where did you get the install file for Skype: from the repositories or from the Skype site?

---

### Post by mac187 on 2017-06-29
Where can i check that [I]Input devices is properly looking at the correct device, that [I]playback also has correct device, and that[I]configuration is also correct. ?

Where can i find my computer specs?


[/I][/I][/I]

---

### Post by mac187 on 2017-06-29
I installed from Canonical Partners

just typed

sudo apt-get install skype

---

### Post by mac187 on 2017-06-29
i typed alsamixer in terminal , pressed F6 to choose my audio card, it was set on default then i changed it to PC HDA Intel PCH, but the voice reciving from other side still lagging

---

### Post by Autodave on 2017-06-29
How about make and model of computer: I can try looking it up. Did you install *pavucontrol? *If so, click on your speaker icon and then *Sound Settings* or go into *Settings->* *Pulse Audio Preferences.*

---

