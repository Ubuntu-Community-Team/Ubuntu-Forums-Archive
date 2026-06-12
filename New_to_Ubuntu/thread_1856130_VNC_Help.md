---
title: "VNC Help"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by Guffmeister on 2011-10-07
Hey all!

I'm trying to connect to my uni computer from home with graphics. I don't want to use SSH, as I've found it to be fairly slow, so I'm trying to connect with VNC, but I'm having a little trouble. I'm pretty sure I've not set something up properly, but I've found the online tutorials aren't particularly helpful.

I'm using x11vnc on my uni computer, which I set up via SSH from here. I'm then tried Remmina and Vinagre to connect, but no luck. It comes up with an error that the connection is closed.

I am using Ubuntu 10.10 on my uni computer, and I have 11.04 on this computer (and also 10.10 on another computer I'm using here). I don't know if there will be a problem with the university having some security blocking something, but I can SSH in fine, so I don't think that's a problem.

I'll be grateful of any help.

---

### Post by CharlesA on 2011-10-07
I would rather use something such as FreeNX over VNC as VNC is quite insecure - it sends everything unencrypted, so anyone listening can read what it being sent.

---

### Post by Guffmeister on 2011-10-07
OK, great thanks! I've set everything up with freeNX, but surprise surprise...I'm having trouble now with that too!

I can connect fine this time, but once I do, the screen which comes up is completely black, and shows nothing.

---

### Post by CharlesA on 2011-10-07
Do you have desktop effects enabled?

---

### Post by collisionystm on 2011-10-07
Did you enable remote desktop on the machine you are connecting to?

---

### Post by Guffmeister on 2011-10-07
@CharlesA: I didn't see anything about that. I'll go back through the configuration.

@collisionystm: I don't know. I haven't specifically done that to my knowledge...

I tried logging in again, and I wasn't accurate in my description of what happens...firstly, the NX logo pops up, then a loading type screen pops up with some other logos, then the screen goes blank. The fact that something loads up before it goes blank suggests that graphics are coming through...maybe...

---

### Post by CharlesA on 2011-10-07
Are you connecting locally or via the internet?

---

### Post by Guffmeister on 2011-10-07
Via the internet. 

BTW, I didn't see anything in the configuration files about desktop effects...

---

### Post by CharlesA on 2011-10-07
Hmm, I would try it locally to make sure it's not the connection (which it shouldn't be).

It works ok if you forward X over SSH, right?

---

### Post by Guffmeister on 2011-10-07
Ahh...I've fixed it! I had it set as UNIX KDE, and once I changed it to GNOME it worked fine.

Thanks very much for all your help!

---

### Post by CharlesA on 2011-10-07
> **Guffmeister said:**
> Ahh...I've fixed it! I had it set as UNIX KDE, and once I changed it to GNOME it worked fine.

Thanks very much for all your help!
Done that before.

Glad you got it working. :)

---

