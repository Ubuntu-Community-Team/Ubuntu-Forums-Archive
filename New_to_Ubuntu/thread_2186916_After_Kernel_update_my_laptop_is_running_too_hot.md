---
title: "After Kernel update my laptop is running too hot"
date: 2013-11-09
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-11-09
Hi Guys,

The other day I ran the update manager and Kernel 3.5.0-43 was installed on my Dell inspiron 1520 which is running Ubuntu 12.04
Since the update my fan doesn't stop and the temperature indicator reads between 71 and 77 degrees C.
The only time I got that high prior to the update was if I was rendering video.

How can I go back to an older version of the Kernel?
I don't see GRUB when I login so I'm not sure how to select an older version.

I really appreciate the help!

---

### Post by GrouchyGaijin on 2013-11-10
[U][COLOR=#ff0000][B]UPDATE

[/B][/COLOR][/U]I found that I can force the GRUB menu to appear if I hold hold down the shift key at boot.
I did and the tempature of my system (and CPU activity dropped significantly).

Does anyone know what I should do to make Ubuntu boot into Kernel 3.5.0-42-generic by default, so that I don't need to hold the shift key each time I start the machine?

Or another way to put it is, how can I uninstall 3.5.0-43-generic and not be nagged to update to from 42?

---

### Post by monkeybrain20122 on 2013-11-10
Just boot into 3.5.0-42 and uninstall 3.5.0-43. The easiest way to do that would be through synaptic. Locate all the 3.5.0-43 packages (there are 4 of them I think, two header files and two images --linux image and linux-image-extra) and remove them.

---

### Post by GrouchyGaijin on 2013-11-10
Thanks Brain!

---

### Post by GrouchyGaijin on 2013-11-11
[COLOR=#b22222][B]UPDATE 2


[/B][/COLOR]Well, it didn't seem to be the Kernel after all.
Even after ensuring that I was booting into an older Kernel I noticed my temperature climbing to abnormally high levels. (over 70C)
The only other thing I did about the same time as update the Kernel was install Play on Linux so I could run Microsoft Word.
I removed that and my temperature is back to normal.
The thing I don't understand is why the temperature would climb even if Word was not open.  I mean simply having Play on Linux installed shouldn't do anything if it isn't being used right?
Could there be a background process that is triggered at boot by Play on Linux?

---

