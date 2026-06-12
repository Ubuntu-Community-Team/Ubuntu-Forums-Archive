---
title: "Streaming Monitor of Audio Out using VLC Media Player"
date: 2011-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by shiman6 on 2011-08-13
Tutorial Time! This one is fairly short, and I cannot find it anywhere else on google.

If you wish to do the Stereo Mix thing like they do in Windows, this is for you.

**First off:**
On a standard Ubuntu install, make sure you have vlc installed, and to install pulse audio volume control with 

```

sudo apt-get install pavucontrol

```

**Step two:**

Open up pulse audio volume control (under sound and video menu), go to "Input devices" tab, then the "Show:" Drop down menu in the bottom right hand corner. Choose "Monitors" from the menu, and look for "Monitor of Internal Analog Audio Stereo." Click the green check mark. It should now show up under the option "All Input Devices".

[B]Step three:

[/B]Open up vlc. Media: Open Capture Device. Now, since i cannot find out how to use this without a video input device, leave the video device name section blank, and put in "pulse" for audio input device.

[B]Step four:

[/B]Go back to the pulse audio volume control, go to the recording tab. You should see the vlc traffic cone as a recording program. Make sure that the button in that section says "Monitor of Internal Audio Analog Stereo". If it does not, go back to the input devices tab and repeat step two. 

This should work! I will update when i figure out how to do this without having to have a webcam plugged in. 

Questions, comments, and suggestions are welcome!

---

