---
title: "Where's the microphone?"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Applesauce on 2012-06-12
I have a Compaq Presario CQ60 laptop running 12.04.
I downloaded Audacity to do a bit of audio work. My laptop has an auxiliary 3.5mm mic input. 

I can't get Audacity to pick up anything worthwhile from this port.
Any ideas where to start, or what to do?

---

### Post by jtarin on 2012-06-12
[Maybe here]("http://audacity.sourceforge.net/manual-1.2/tutorial_basics_4.html")?

Also check your alsamixer settings by opening a terminal and typing ```
alsamixer
```

---

### Post by Autodave on 2012-06-12
> **Applesauce said:**
> I have a Compaq Presario CQ60 laptop running 12.04.
I downloaded Audacity to do a bit of audio work. My laptop has an auxiliary 3.5mm mic input. 

I can't get Audacity to pick up anything worthwhile from this port.
Any ideas where to start, or what to do?

You need to go into the PREFERENCES menu, then to RECORDING.  There, you can pick different inputs.  You may have to try a few before you find the specific one that Audactiy will use.  Under PREFERENCES (Ibelieve it is the first choice when that menu opens) you might want to click the PLAY THROUGH box.  Just be careful: if the volume is up to far, you will get instant feedback when you choose the correct input. :-)

While in the INPUT area, you will probably see that the volume level for that is set to minimum or may be even muted.  Make sure you unmute it and start by putting the volume about 1/2 up to 100%.

If you have headphones, this is a little better way of doing it.  Plug your phones in and make sure they work: play something that you know has sound.  Then, leave the headphones on while you try different inputs: you'll be able to hear yourself in the phones and have less chance of feedback.

---

### Post by Applesauce on 2012-06-12
Ok. Here's what came up when I typed in alsamixer. 

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.25 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia * * * * * * * * * * * * * * * * * * F1: *Help * * * * * * * &#9474;
&#9474; Chip: Nvidia MCP77/78 HDMI * * * * * * * * * * * * * F2: *System information &#9474;
&#9474; View: F3:[Playback] F4: Capture *F5: All * * * * * * F6: *Select sound card *&#9474;
&#9474; Item: Master [dB gain: -18.00] * * * * * * * * * * * Esc: Exit * * * * * * * &#9474;
&#9474; * * &#9484;&#9472;&#9472;&#9488; * * &#9484;&#9472;&#9472;&#9488; * * &#9484;&#9472;&#9472;&#9488; * * &#9484;&#9472;&#9472;&#9488; * * &#9484;&#9472;&#9472;&#9488; * * * * * * *&#9484;&#9472;&#9472;&#9488; * * * * * * * &#9474;
&#9474; * * &#9474; *&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474; *&#9474; * * * * * * * &#9474;
&#9474; * * &#9474; *&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474; *&#9474; * * * * * * * &#9474;
&#9474; * * &#9474; *&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474; *&#9474; * * * * * * * >
&#9474; * * &#9474; *&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474;&#9618;&#9618;&#9474; * * * * * * * >
&#9474; * * &#9474; *&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474;&#9618;&#9618;&#9474; * * * * * * * >
&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474;&#9618;&#9618;&#9474; * * * * * * * >
&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474;&#9618;&#9618;&#9474; * * * * * * * >
&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474;&#9618;&#9618;&#9474; * * * * * * * >
&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474;&#9618;&#9618;&#9474; * * * * * * * &#9474;
&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474;&#9618;&#9618;&#9474; * * &#9474; *&#9474; * * * * * * *&#9474;&#9618;&#9618;&#9474; * * * * * * * &#9474;
&#9474; * * &#9500;&#9472;&#9472;&#9508; * * &#9500;&#9472;&#9472;&#9508; * * &#9500;&#9472;&#9472;&#9508; * * &#9492;&#9472;&#9472;&#9496; * * &#9492;&#9472;&#9472;&#9496; * * &#9484;&#9472;&#9472;&#9488; * * &#9500;&#9472;&#9472;&#9508; * Enabled * * &#9474;
&#9474; * * &#9474;OO&#9474; * * &#9474;OO&#9474; * * &#9474;OO&#9474; * * * * * * * * * * * &#9474;OO&#9474; * * &#9474;OO&#9474; * * * * * * * &#9474;
&#9474; * * &#9492;&#9472;&#9472;&#9496; * * &#9492;&#9472;&#9472;&#9496; * * &#9492;&#9472;&#9472;&#9496; * * * * * * * * * * * &#9492;&#9472;&#9472;&#9496; * * &#9492;&#9472;&#9472;&#9496; * * * * * * * &#9474;
&#9474; * * *47 * *100<>100 100<>100 100<>100 * 0<>0 * * * * * * * 67 * * * * * * * *&#9474;
&#9474; *< Master >Headphon Speaker * *PCM * *Mic Boos *S/PDIF * *Beep * Auto-Mut * *&#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by Applesauce on 2012-06-12
@ Autodave= I tried fooling with the different inputs earlier and didn't seem to get any help there.

The options it gives me are= default, pulse, sysdefault, and HDA NVidia CONEXANT analog (hw:0,0). 

I hope that stuff means more to you than to me.

---

### Post by Curtis6767 on 2012-06-12
You might look this over: [http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html](http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html)

Pulse Audio Volume Control is in the Software Center.

---

### Post by Applesauce on 2012-06-12
Okay, I'm not sure what did it exactly, but it is working like a charm now.
I followed some of the instructions on the site you mentioned Curtis6767 but I wasn't aware that I downloaded anything new. I did open Pavucontrol and poked around a little bit and the next thing I knew it was working perfectly. Thanks for the help:)

---

### Post by thunderheights on 2012-07-07
I have tried, Googled, and forumed :confused:and I have not been able to get my mic working with this or the previous distro. I know it works because I had it working on Fedora. I'm not an expert but not an absolute beginner either. Someone give the simpleton some ideas? :)

Compaq Presario CQ50-107NR

---

