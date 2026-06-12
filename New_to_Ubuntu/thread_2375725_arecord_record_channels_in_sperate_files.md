---
title: "arecord: record channels in sperate files"
date: 2017-10-27
forum: New to Ubuntu
---

### Post by mohammadraffi on 2017-10-27
Hi,
I am using the arecord in my application
But i am not able to record left and right channels  inputs in separate files.
Help me out.

---

### Post by ajgreeny on 2017-10-27
In terminal **man arecord** shows this, but not knowing anything about recording sound or mapping channels I have no idea if it helps you do what you want.
>  -m, --chmap=ch1,ch2,...
              Give the channel map to override or follow.  Pass channel position strings like FL, FR, etc.

              If a device supports the override of the channel map, aplay tries to pass the given channel map.  If it
              doesn't support the channel map override but still it provides the channel map information, aplay tries
              to rearrange the channel order in the buffer to match with the returned channel map from the device.

See **man arecord** in terminal for all the rest of the manual.

I wonder if you could record both channels normally then separate them with audacity or similar? Never tried that so I am not even sure if it's possible.

---

