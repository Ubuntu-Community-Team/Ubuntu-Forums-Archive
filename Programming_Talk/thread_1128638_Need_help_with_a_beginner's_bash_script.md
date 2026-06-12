---
title: "Need help with a beginner's bash script"
date: 2009-04-17
forum: Programming Talk
---

### Post by The Funkbomb on 2009-04-17
1.  I have read the FAQ (I hope this does warm your heart)
2.  I am not a programmer.  I basically just run a few commands in a bash script but nothing complex.
3.  I'm not even sure this is the right forum.  If it isn't, or my questions too stupid, let me know and I'll shut up.

Okay, now that we have the niceties out of the way, it's brass tacks time.

Here is the situation.  I have two wireless cards.  One is built into my machine but it is a broadcom.  The card doesn't support much so I went out and bought a ralink rt73 chipset card.  I compiled the enhanced drivers by myself (I'm new at this :/, a little credit).

Unfortunately, it's a royal pain in the butt to disable the stock card (wlan0), bring up the USB card (rausb0), put it into monitor mode and all that stuff.  I wrote a very simple bash script. Please don't laugh.

```
#!/bin/bash

sudo ifconfig wlan0 down
sudo ifconfig rausb0 down
sudo iwconfig rausb0 mode monitor rate 1M
sudo ifconfig rausb0 up
sudo iwpriv rausb0 forceprism 1
sudo iwpriv rausb0 rfmontx
```

It's a start, right?  Now I can just run that in terminal and it does all the work for me after I put in my root password.  That's good.

Now, the second part is basically undoing all of that.  It's an even simpler script that I need help with.

This one looks like this:

```
#!/bin/bash

sudo ifconfig rausb0 down
sudo ifconfig wlan0 up

```

Here is what I need help with.  On the second script, I would like my wlan0 to automatically connect to my preferred router but I don't know any commands for that in terminal.  I'm a GNOME network manager applet wienie.

What I would eventually like to do is for my computer to automatically run the first script as soon as I plug the USB device in.  That's way over my head at this point, obviously.

Thank you for your time and I look forward to learning.

---

### Post by Cybie257 on 2009-04-17
Until something else shows up, you might want to check out this thread. It talks about creating an action upon a USB device connection.

[http://ubuntuforums.org/showthread.php?t=1124324](http://ubuntuforums.org/showthread.php?t=1124324)

-Cybie

---

### Post by The Funkbomb on 2009-04-17
Thanks for your help!

---

