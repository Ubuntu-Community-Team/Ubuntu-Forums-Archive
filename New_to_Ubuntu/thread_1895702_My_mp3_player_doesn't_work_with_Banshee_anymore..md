---
title: "My mp3 player doesn't work with Banshee anymore."
date: 2011-12-15
forum: New to Ubuntu
---

### Post by smiley07 on 2011-12-15
I don't know what happened, but my mp3 player (Zen) no longer works with Banshee. Whenever I connect it, and choose to use it with Banshee, my computer gets really slow, Banshee freezes and then eventually shuts down.

Ubuntu clearly recognizes my mp3 player because whenever I connect it to my computer, a mp3 player icon is immediately added to the launcher.

I've tried manually dragging my songs into the music folder of my mp3 player, but none of the songs show up on it when I disconnect it to try and play them.

How do I fix this? I want to go back to using Banshee to add songs to my mp3 player.

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-15
It would benefit anyone trying to help you to have more info.
Such as what OS are you running (Ex. Xubuntu 10.04 kernel  2.6.32-36-generic)
What version of banshee? (eg. 1.6.1)
When did this happen? (e.g. during the most recent update of banshee/Ubuntu)
Someone who knows more about this should be able to offer you some insight with this info included

---

### Post by smiley07 on 2011-12-15
> **TREESofRIGHTEOUSNESS said:**
> 
Such as what OS are you running (Ex. Xubuntu 10.04 kernel 2.6.32-36-generic)

 
Ubuntu 11.10 (I don't know how to find out the kernel information.)
 
> **TREESofRIGHTEOUSNESS said:**
> 
What version of banshee? (eg. 1.6.1)

 
Banshee 2.2.1
 
> **TREESofRIGHTEOUSNESS said:**
> 
When did this happen? (e.g. during the most recent update of banshee/Ubuntu)

 
I honestly couldn't tell you when it happened, but it's been a while. I know Banshee was working when I had Ubuntu 11.04, and the reason I didn't try to fix it sooner is because I thought if I waited for a few updates, the problem would naturally be resolved.

---

### Post by blackbird34 on 2011-12-15
You can get kernel info in the System Monitor. 
Did you update Banshee between installing Oneiric and having the problem? Has your player ever worked with Banshee on Oneiric?

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-15
> **blackbird34 said:**
> 
Did you update Banshee between installing Oneiric and having the problem? Has your player ever worked with Banshee on Oneiric?


Very good point.

Also have you ever used another program to upload to your Mp3 player, like Rhythmbox, or Guaydeque, etc?

i found a bug on launchpad relating to banshee and zen
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/535268](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/535268)
not sure if this will help, but you might take a look

---

### Post by smiley07 on 2011-12-15
> **blackbird34 said:**
> You can get kernel info in the System Monitor. 


Kernel Linux 3.0.0-14-generic
GNOME 3.2.1

> **blackbird34 said:**
>  
Did you update Banshee between installing Oneiric and having the  problem?

I don't know. The only updates I do are the ones that pop up in the update manager, so if software can be added to the update manager I might have update it.

> **blackbird34 said:**
>  
 Has your player ever worked with Banshee on Oneiric?

Not to my knowledge. I tried it once, and what happened was the mp3 player icon briefly showed up in Banshee's tray, then Banshee froze, and it hasn't worked since.

---

### Post by smiley07 on 2011-12-15
> **TREESofRIGHTEOUSNESS said:**
> Very good point.

Also have you ever used another program to upload to your Mp3 player, like Rhythmbox, or Guaydeque, etc?


No, I haven't. I'll try Rhythmbox in a couple minutes.

> **TREESofRIGHTEOUSNESS said:**
> 
i found a bug on launchpad relating to banshee and zen
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/535268](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/535268)
not sure if this will help, but you might take a look

Thanks for the info. I couldn't really understand it, but as far as I can tell the problem hasn't been solved yet, right?

---

### Post by smiley07 on 2011-12-15
Rhythmbox works!

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-16
Good!!!  that means it is probably just a banshee problem.
You might try to reintsall it.
If you have synaptic, open it find banshee and mark it for re-installation.
if it still doesn't work you should run 
ubuntu-bug banshee
to add a bug report.

At least you have rhythmbox!!  I keep both around for that same reason (if 1 doesn't work the other does)

---

### Post by Christofferh on 2011-12-18
I'm having the same problem with my Creative Zen V Plus. Banshee goes dark and then shuts down as soon as I connect my mp3 player. This didn't happened yesterday before I reorganized banshee music library.

I'm using Ubuntu 11.10 aswell.

Rhythmbox worked well after a few re-connects.

---

