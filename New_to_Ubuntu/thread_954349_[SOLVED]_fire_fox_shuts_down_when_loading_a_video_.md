---
title: "[SOLVED] fire fox shuts down when loading a video preview"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by fr.theo on 2008-10-21
Hello,

I have successfully installed Adobe Flash Player 10 for Ubuntu 64 bit, they finally have one for this architecture, however every time I enter my service providers services, such as movies in which i can view a trailer fire fox shuts down. I am not sure of what to make of it any one knows how to fix this problem.


Thank you for your help.

---

### Post by fr.theo on 2008-10-21
found the answer thanks to steveneddy post I am just placing it here for future reference or if anyone has the same problem hope it helps. 

it is a bit slow to start up so be patient it will start the video, oh and I installed Adobe Flash player 10, this site instructed how to install the flash player: [http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html) 

```
 Re: Flash crashes!!
Maybe an answer here:

I first made sure that I using the flashplugin-nonfree that is available in Synaptic and then followed advice from here that addressed the sound issue in Firefox causing the crash and not actually Flash.

It tell you how to install alsa-oss and how to get Firefox to use it correctly.

I had sound already but did it anyway. This along with another hint did it for me.

The third hint is from this post that deals with adding a line to the /usr/bin/firefox file.

Here is a copy of that post:

HTML Code:

1. Open the firefox file...

    Ubuntu users: sudo gedit /usr/bin/firefox

    Kubuntu users: sudo kate /usr/bin/firefox

2. Add the following line as last but one line of the file:

    export XLIB_SKIP_ARGB_VISUALS=1

3. Restart Mozilla Firefox

Adding the line in the firefox bin file and changing the Firefox default sound app to alsa-oss helped me.

I was crashing ALL THE TIME - usually after 3-4 videos. I just did that and went to YouTube and watched almost 30 minutes of video with no crash. I started them in the middle, closed the tab while playing and started a new video in the moddle of one that was already playing. I opened three tabs and played video in all three tabs with no crash.

I did also open firefox in terminal to see what the error code was when it crashed, but like I said, no crashes.

1. Use the correct driver
2. Download alsa-oss and tell Firefox to use it.
3.Add the line in /usr/bin/firefox


Hope this helps.
```

Thanks again to all Ubuntu Forum members and all those who helped.

Cheers!.

---

### Post by marshall.robert on 2008-10-21
I also have this problem with 32 bit flash. The only time it doesnt crash if a session is restored with flash on the page.

It's highly irritating.


EDIT: ill try that when i get home!

---

### Post by fr.theo on 2008-10-21
by the way I have Ubuntu hardy LTS 64 bit, so if you have the 32 follow the instruction to install Adobe flash for the 32 bit architecture.

---

