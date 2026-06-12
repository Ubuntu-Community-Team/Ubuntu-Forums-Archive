---
title: "problems in ibex with my kinstone webcam..."
date: 2008-11-14
forum: New to Ubuntu
---

### Post by kristiansuhl on 2008-11-14
Hello!

I've been using ubuntu on my hp pavilion dv1263ea for a couple years. I upgraded from hardy heron to intrepid ibex and now my USB-webcam stopped working.

When I had the hardy heron the webcam worked just fine without any installation needed. Now - with intrepid ibex - I cannot get it to work! The system does not seem to "find" my webcam in the new ubuntu version... :-( 

Is this a bug or have some kind of library or driver been taken out of the distribution? 


I have:
hp pavilion dv1263ea
intrepid ibex
USB kinstone pc camera KS-188P
(it's not "kingston")

I was thinking that maybe one of you guys could help me with this, I have no idea how to solve this little problem.

Thanks alot in advance!

Kristian

---

### Post by Vadi on 2008-11-14
If you're using Cheese for the webcam, try going to preferences and lowering the resolution.

I had the same issue - it was working fine before but stopped now. Turns out the driver was 'lying' about which resolutions the camera was supporting (2 highest simply didn't work), and programs were of course trying to use the best resolution possible.

---

### Post by kristiansuhl on 2008-11-14
> **Vadi said:**
> If you're using Cheese for the webcam, try going to preferences and lowering the resolution.

I had the same issue - it was working fine before but stopped now. Turns out the driver was 'lying' about which resolutions the camera was supporting (2 highest simply didn't work), and programs were of course trying to use the best resolution possible.
I have a standard version of the intrepid ibex I think, when I checked for cheese I saw that it was not installed now, so I installed it to see what would happen. When I go to settings it says "no camera found". I get "no device found" from skype and ekiga as well. :-( 

I tried the command "dmesg" in a terminal and when I connect the camera I get this:
> 
[170968.088152] usb 1-2: new full speed USB device using uhci_hcd and address 6
[170968.296967] usb 1-2: configuration #1 chosen from 1 choice
[170968.301428] usb 1-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x0AC8:0x303B)
[170968.391050] usb 1-2: No supported image sensor detected


and when I disconnect the camera I get this: 
> 
[171012.043751] usb 1-2: USB disconnect, address 6


I don't know much about computers/ubuntu linux but I guess it seems as if the system detects something...
when I had the hardy heron the camera worked fine in different programs - now it says "no device found" everywhere.

Could there be some crucial driver/codec or so that have been excluded in the ibex? What should I do?

---

### Post by Vadi on 2008-11-14
Possibly could have been, as ibex sports a new kernel and thus possibly different drivers. But from what I heard the webcam situation was supposed to improve, not degrade.

I'm afraid I can't be of much assistance here, don't know much stuff either. Try filing a bug report on [https://bugs.launchpad.net/linux](https://bugs.launchpad.net/linux) with as much information as you can provide, hopefully someone experienced will look into this.

---

### Post by kristiansuhl on 2008-11-14
> **Vadi said:**
> Possibly could have been, as ibex sports a new kernel and thus possibly different drivers. But from what I heard the webcam situation was supposed to improve, not degrade.

I'm afraid I can't be of much assistance here, don't know much stuff either. Try filing a bug report on [https://bugs.launchpad.net/linux](https://bugs.launchpad.net/linux) with as much information as you can provide, hopefully someone experienced will look into this.
ah ok, I guess I'll have to downgrade to hardy heron again then... :-(

Thanks alot for the answers though, now I know that there might be some kind of bug anyway, this way I don't have to think about it anymore! :-)

Unless someone else has another solution for it of course! :-)

---

