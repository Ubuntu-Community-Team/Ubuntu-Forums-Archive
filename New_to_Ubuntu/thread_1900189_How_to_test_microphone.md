---
title: "How to test microphone"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by mkornig on 2011-12-25
Hi there!

My external microphone doesn't seem to work. My computer may have an internal microphone. But I'm not sure.

Questions:


[LIST=1]
[*]What's the simplest way to test an external mic?
[*]Is there a configuration somewhere (mute, microphone on/off) which I need to check?
[*]Would Ubuntu detect a mic (external or internal) automatically?
[*]How would I know whether or not there is an internal mic?
[/LIST]

---

### Post by matt_symes on 2011-12-25
Hi

Check your alsa mixer settings. Open a terminal and type

```
alsamixer
```

Check your microphone is not muted.

Kind regards

---

### Post by jerome1232 on 2011-12-25
There is also a gui frontend, If you click the speaker icon in the top right, and click sound settings, you have various tabs you can go through with their related settings. For microphone click the input tab, you should have a list of the various peices of hardware which allow sound input, and you can select their various inputs from a drop down menu.

To test that a mic is working you should be able to talk into it and see the input meter bouncing up and down, you can also open up "sound recorder" (search for it using the unity menu) and test it out.

---

### Post by mkornig on 2011-12-26
Thanks, jerome. That's a simple way of testing the mic.

I don't understand the information alsamixer displays.

For a strange reason that I ignore, my microphone is working now although I didn't touch the settings. I tested it also with a Skype test call.

Best regards, Martin

---

