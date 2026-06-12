---
title: "Heron has Flash issues and crashes"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by The Populist on 2008-06-11
First off, I like Heron. I hesitated to upgrade, but after doing so I'm impressed with the new OS. However, there are some teething problems that we need to figure out.

Flash player has always been flaky in Ubuntu, and I'm ok with that. In Gutsty, I had do download libflash and disable some other programs to get Flash working on web pages. At least after doing all that and surfing the forums, I was able to get good performance.

Not so with Heron. I have surfed the forums, tried disabling VLC, tried various other solutions offered on this forum, and I've gone to Medibuntu and done everything they said. And Heron still cant play Flash reliably.

Some websites simply appear as blank spaces where the flash video should appear. Other times flash will play for awhile, then all my Firefox screens go grey, *and stay grey*. And some times my computer simply restarts while running a flash video. I even had one website with a bunch of changing adds in the margins that crashed my computer. 

Is this a bug? Or is there a solution to this problem that I havent found?

...

---

### Post by jbrown96 on 2008-06-11
You could always go with a free alternative. Gnash or swfdc. I know that swfdc doesn't play all flash content. They both should work reasonably well and are worth a try. Remember to uninstall adobe's flash player first.

---

### Post by stchman on 2008-06-11
> **The Populist said:**
> First off, I like Heron. I hesitated to upgrade, but after doing so I'm impressed with the new OS. However, there are some teething problems that we need to figure out.

Flash player has always been flaky in Ubuntu, and I'm ok with that. In Gutsty, I had do download libflash and disable some other programs to get Flash working on web pages. At least after doing all that and surfing the forums, I was able to get good performance.

Not so with Heron. I have surfed the forums, tried disabling VLC, tried various other solutions offered on this forum, and I've gone to Medibuntu and done everything they said. And Heron still cant play Flash reliably.

Some websites simply appear as blank spaces where the flash video should appear. Other times flash will play for awhile, then all my Firefox screens go grey, *and stay grey*. And some times my computer simply restarts while running a flash video. I even had one website with a bunch of changing adds in the margins that crashed my computer. 

Is this a bug? Or is there a solution to this problem that I havent found?

...

Flash works fine in Hardy using Firefox.

I used this package:

```
sudo apt-get install flashplugin-nonfree
```

Works like a charm.  The only thing is that drop down menus are behind Flash videos, but Adobe won't fix that.

---

### Post by The Populist on 2008-06-11
Ok, I have the latest non-free flash plugin. Basically Flash is working on most sites. But I do have stability issues with some sites. I still get the grey screen with some sites, and I have had crashes where my computer restarts.

...

---

### Post by alienexplorers on 2008-06-11
I downloaded flash from the Adobe site and loaded it on my system and have not had any flash related errors or crashes.

---

### Post by TenPlus1 on 2008-06-11
I had problems with flash in Hardy also, but found the pulseaudio system to be screwing around and crashing the flash plugin...  So I removed what pulse audio libraries I could in Synaptic and my flash hasn't crashed once...  Alsa sound system still works great for me...

---

### Post by robglenh on 2008-06-11
> **stchman said:**
> Flash works fine in Hardy using Firefox.

I used this package:

```
sudo apt-get install flashplugin-nonfree
```

Works like a charm.  The only thing is that drop down menus are behind Flash videos, but Adobe won't fix that.

I just sstarted using Ubuntu.  I used the code to get the flash plugin.  How can I get it to work?  DIY Network videos keep telling me I need what I downloaded. Tanks in advance for any help

---

### Post by MmmmJoel on 2008-06-12
> **The Populist said:**
> Is this a bug? Or is there a solution to this problem that I havent found?

You can try the [Flash 10 beta]("http://labs.adobe.com/downloads/flashplayer10.html"). Uninstall Flash 9 and then move the libflashplayer.so in archive to ~/.mozilla/plugins and restart Firefox.

---

### Post by cariboo on 2008-06-12
I agree with MmmmJoel Flash10 is way better. Use the attached script to install it.

---

### Post by The Populist on 2008-06-15
Just an update, I have posted this to another thread but I'll add it here in case anyone with a problem searches and finds this thread.

I uninstalled Firefox 3 and installed Firefox 2, now EVERYTHING works. I've had my computer running for three days, playing LastFm, and various flash videos. I havent had any blank screens where flash images should be, and my computer has not rebooted, (crashed).

I am very happy with Hardy Heron with Firefox 2. There is no monkey business getting Flash to work, (like nspluginwrapper), and everything is running smoothly. I highly recommend anyone having trouble with Flash player in hardy heron uninstall Firefox 3 and install FF 2.

...

---

