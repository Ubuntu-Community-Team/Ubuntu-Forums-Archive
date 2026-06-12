---
title: "getting audio input via usb"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by shultzbaby on 2011-12-15
hey all, im trying to get ardour up and running, but having some problems as im used to the simplicity of windows. im using a lightsnake usb cable as the audio input for my guitar. i have it plugged into the usb port, how do i know if my computer is recognizing it? how can i get that audio into ardour? i started messing with qjackctl but im in way over my head. anyone wanna hold a newbs hand on this one?

---

### Post by Ms. Daisy on 2011-12-15
Have you seen this?
[http://en.flossmanuals.net/ardour/](http://en.flossmanuals.net/ardour/)

---

### Post by sandyd on 2011-12-15
> **shultzbaby said:**
> hey all, im trying to get ardour up and running, but having some problems as im used to the simplicity of windows. im using a lightsnake usb cable as the audio input for my guitar. i have it plugged into the usb port, how do i know if my computer is recognizing it? how can i get that audio into ardour? i started messing with qjackctl but im in way over my head. anyone wanna hold a newbs hand on this one?
Firstly, what Ubuntu version are you using? 
If you intend to use JACK, using Ubuntu Studio would be a good idea as JACK is already set up, and you will be using the RT kernel.

Anyways, QJackCTL will show MIDI devices while JACK is running, and the device is connected. I connected the studio keyboard to my laptop (as we use different software/hardware here at work) to show you.

1. First, make sure JACK is started. This can be a PITA if pulseaudio is installed and conflicts with JACK. Thats for you to figure out, since I use a different OS on here. You might want to raise and lower the latency by going to Setup, and playing with the Frames, Sample Rate, and Buffer. Test it yourself to make sure you don't get any XRuns. (its on the QjackCTL main window).
Make sure you flip the MIDI driver to RAW on the setup screen, and restart jack.

2. Once JACK is started, open qjackctl, and click the "connect" button. Click on "MIDI", and your devices should be there.
[[IMG]http://img249.imageshack.us/img249/2369/snapshot24t.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/249/snapshot24t.jpg/")

---

### Post by shultzbaby on 2011-12-16
Thanks for the input guys, Im gonna see what I can do with it tonight. Btw I am running 11.10

---

### Post by shultzbaby on 2011-12-16
ok, when i go to sound settings i see the device listed, and it responds to input (the volume bar responds when i strum the guitar) but i have no idea how to configure this! now my speakers wont work at all! i dont know what i did. i am trying out all different combinations of settings but getting nowhere.
this is what i get from "aplay -l"

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x19400xac01 [USB Device 0x1940:0xac01], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

and i have two crappyish speakers hooked up to the output on the back of my computer. anyone have any ideas for me? ive unmuted everything, and i know the audio works somehow, i was watching youtube videos yesterday. so its not bad speakers or a bad output or anything like that. its my configuration, which is where i get lost...
 PS "card 1" is the usb input i have for my guitar.

---

### Post by shultzbaby on 2011-12-16
cant figure out how to post a screenshot to show you all my jack connections tho

---

### Post by shultzbaby on 2011-12-16
all right, got my speakers working, and the computer is reading mic input from my usb cable. now i just have to figure out how to use ardour!

---

### Post by shultzbaby on 2011-12-21
well i cannot figure this out no matter how much i research so it looks like ill just have to get a 1/4 to 1/8 adapter and go straight to the sound card. sad face.

---

