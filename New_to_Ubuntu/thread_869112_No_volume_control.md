---
title: "No volume control"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by RGreaves on 2008-07-24
I have a problem that the sound card works, however I can not control the volume level. I have went through all the devices I can in volume control and none affect the sound volume.

Below is the output from the cat /proc/asound/cards

 cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [SB0310] at 0xdf00 irq 21
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 18

While this is not a show stopper any help on this would be appreciated.

-Rick

---

### Post by kansasnoob on 2008-07-24
Perhaps install > gnome-alsamixer from synaptic. It'll then show up in Sound & Video. Nice gui with lots of toggles and if it doesn't work you can go back to synaptic and remove it.

[ATTACH]78806[/ATTACH]

[ATTACH]78807[/ATTACH]

So many toggles my old CRT monitor requires two screenshots:(

---

### Post by RGreaves on 2008-07-24
That is a sweet tools, thank you :)

Using it i found which audio channel controlled the output and now it works fine. Just need to change the channel which the keyboard controls and the world will be a better place!

Thanks again man.

-Rick

---

### Post by mgmiller on 2008-07-24
> Just need to change the channel which the keyboard controls and the world will be a better place!

If you mean the keyboard volume controls are making the wrong channel go up and down, you usually want it to control the MAIN channel.

Click on System > Preferences > Sound

At the bottom of the devices tab is an area called "Default Mixer Tracks"
below that is a list of the different channels controlled by your keyboard.

In the device drop down, select your sound card (or just try Alsa Mixer)

In the list below that, highlight Master, and you should be all set.

---

### Post by kansasnoob on 2008-07-24
> **RGreaves said:**
> That is a sweet tools, thank you :)

Using it i found which audio channel controlled the output and now it works fine. Just need to change the channel which the keyboard controls and the world will be a better place!

Thanks again man.

-Rick

Sorry I can't help with keyboard controls. I just buy super cheap generic keyboards. I haven't had a custom keyboard since about 2001.

I spill, it dies, I grab another!

---

