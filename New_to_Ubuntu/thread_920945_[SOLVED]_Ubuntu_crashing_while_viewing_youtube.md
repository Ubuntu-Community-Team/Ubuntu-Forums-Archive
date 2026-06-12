---
title: "[SOLVED] Ubuntu crashing while viewing youtube"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Chelives1928 on 2008-09-15
Everytime I have a webpage on firefox opened and I want to view some youtube videos ubuntu locks up and i can't do anything which forces me to restart the computer.  any ideas?

---

### Post by milky2313 on 2008-09-15
Do you have compiz desktop effects enabled? If you do, that sometimes interferes with flash videos playing(at least it does on my computer)

Try viewing the video after turning off desktop effects with this command: 
```
metacity --replace
```

After you are finished you can reenable the desktop effectes using this command:

```
compiz --replace
```

I put buttons for each of these commands on my Gnome panel. It makes it much easier if you need to switch back and forth quickly. Hope this helps...

---

### Post by Grimhound on 2008-09-15
Speaking as a novice who attempted something to stop that same sort of issue, you may want to install libflashsupport off of Synaptic. Try it again and let me know if it helps at all. At first it just made it so Firefox crashed instead of all of Ubuntu going down, but things seem stabler now.

---

### Post by Chelives1928 on 2008-09-15
Wow what respond time....okay i'll try both options and let you know how it goes.  Thanks everyone.

---

### Post by Chelives1928 on 2008-09-15
one more quick questions.  I've had the same problem when I'm using VLC should switching desktop effects on and off effect work with that as well.

---

### Post by Grimhound on 2008-09-15
> **Chelives1928 said:**
> one more quick questions.  I've had the same problem when I'm using VLC should switching desktop effects on and off effect work with that as well.

I've had a lot of the same problems, so I'm really not sure how to help you with a lot of it. When I was experiencing my most recent Linux nightmare moment it seemed like a tandem issue between Flash and VLC, so hopefully an answer will come through to fully resolve the issues here.

---

### Post by nitramf82 on 2008-09-15
I had a similar problem with VLC that was solved by shutting off compiz. If you want to leave it on, in VLC go to Settings - Preferences, collapse Video and click on "output modules". Turn on advanced options and change the output module to X11.

---

