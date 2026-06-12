---
title: "Linux Equalizer"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Shippou on 2008-10-07
Is there a GENERAL Linux equalizer out there? 

What I mean by general is that the equalizer is not application-specific.

And also, what I mean by equalizer is something like the level of Realtek... something like that.

---

### Post by talsemgeest on 2008-10-07
If there is, I havn't found it. I really want one too...

---

### Post by whitethorn on 2008-10-07
Hi, 
I've found a thread out there which is kinda what you are looking for.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Shippou on 2008-10-07
Thank you very much! :)

It IS a long post.. maybe I'll check it again later. But thank you very much for the link!

---

### Post by chamk on 2009-03-13
Hi, if you dont want to use PulseAudio you can use caps wich is a small ladspa plugin. Select alsa in your sound preference as a playback device for sound and movies.
install caps
create the alsa config file if you dont have one in your home dir ( .asoundrc) and put the values of your preference. see the example below

> 

   pcm.!default {
          type plug
          slave.pcm "equalized";
   }

   pcm.equalized {
          type ladspa
          slave.pcm "plug:dmix";
          path "/usr/lib/ladspa";
          plugins [
                {   # Eq
                       id 2594
                       input {
                           controls [ 5 6 3 -7 -6 -3 -2 3 7 5 ]
                      }
                }
                {   # ToneStackLT
                       id 2590
                           controls [ 4 -3 -4 4 ]
                }
   ]
   }
Check out the caps site for more options. By the way im using Hardy

---

### Post by WebDawg on 2010-01-12
Anyone still needing something like this.  Take a look at this thread.  The EQ *PLUGIN* for pulse is great:

[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

---

### Post by Shippou on 2010-01-13
> **WebDawg said:**
> Anyone still needing something like this.  Take a look at this thread.  The EQ *PLUGIN* for pulse is great:

[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

Thanks for getting my attention to this thread. I really appreciate it.

---

### Post by joel007 on 2010-04-11
Well, first, does pulseaudio-equalizer work ok for u? When I use it changing the volume really jerks. 

Second, it uses too much of the processor and when I start the internet browser f.e., the sound playback stops for several seconds. However, my EeePC is really weak, that's why I'd like to know if u all are facing the same problem or not.

Like this, the eq is unusable for me...

---

### Post by tom.swartz07 on 2010-04-11
Try this.

Open a terminal (Applications>Accessories>Terminal) and type
```
alsamixer
```

See if that fits your needs. Im not quite sure of the functionality youre looking for.

---

