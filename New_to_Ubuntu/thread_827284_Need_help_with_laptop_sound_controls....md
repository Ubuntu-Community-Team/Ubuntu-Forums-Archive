---
title: "Need help with laptop sound controls..."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Grimhound on 2008-06-12
I've had Gutsy installed on my laptop for a while now, and I'm just now getting into asking about this problem I've been having with the sound controls as well as the routes through which sound is transmitted.

My problem is that the sound control shortcuts on the keyboard (Function +...) don't actively lower or raise the volume. The GUI shows the volume bar and has it showing it raise or lower or mute, but it doesn't actually do anything past the visual side. To raise or lower volume, I've had to manually click down and drag the volume slider on the taskbar itself.

Also, I'm having an issue where when I plug in headphones or speakers through the audio jack, it continues to transmit sound through both the speakers and the jack itself rather than automatically switching between when the presence of headphones or not is detected.

If anyone could assist me in getting things to work correctly, I'd be vastly grateful.

---

### Post by Raistlin82 on 2008-06-12
Hi there, go to system>preferences>sound from the panel and try selecting the correct device from the list at the bottom. On my laptop its PCM. Hope this helps

EDIT - for the sound coming out through jack and speakers, I have the same problem, but if i turn down "front speakers" after double clicking on the volume icon it will turn off the laptop speakers, seems to be a common problem that the jack isn't always auto sensed

---

### Post by Grimhound on 2008-06-12
> **Raistlin82 said:**
> Hi there, go to system>preferences>sound from the panel and try selecting the correct device from the list at the bottom. On my laptop its PCM. Hope this helps

EDIT - for the sound coming out through jack and speakers, I have the same problem, but if i turn down "front speakers" after double clicking on the volume icon it will turn off the laptop speakers, seems to be a common problem that the jack isn't always auto sensed
Thanks! :)
Alright, the PCM thing worked for the volume controls, but I'd really like to figure out how to make it detect the headphones. Going to be using this laptop when I head back to college, and mistakenly forgetting to lower volume after I plug in the headphones could cause some rather... iffy circumstances.

---

### Post by Raistlin82 on 2008-06-12
LOL  Let me know if you have any joy with this, I've been looking for a while, its a bummer when you think your the only one listening to your music only to look up and realise that others at work here it too :)

EDIT - just trying a possible solution for the jack sense that i found at [http://ubuntuforums.org/showthread.php?t=765867&highlight=jack+sense](http://ubuntuforums.org/showthread.php?t=765867&highlight=jack+sense), i'll let you know how it goes!

---

### Post by Raistlin82 on 2008-06-12
That seems to have worked for me!
[I]
sudo passwd root[/I]

enter your chosen password, then re-enter it to confirm, then to login root type the command:

*su*

it will as you for your password  then type:

[I]apt-get install module-assistant

module-assistant a-i alsa-source[/I]

when this completes you will need to reboot, then hopefully it will have worked!  Touch wood it has for me, at least for now :)

---

### Post by Grimhound on 2008-06-12
Doesn't seem like it did anything. Still doesn't alternate when I plug in headphones.

---

### Post by Raistlin82 on 2008-06-12
have you checked out alsamixer in the terminal, if not have a look and see what your settings there are, not sure if that will help though to be honest.  I did, about a week ago, think that i had this problem solved only to be proved wrong, it seemed then like a certain set of headphones was auto-sensed but when i put my own in it wasnt, good luck finding a solution!

---

