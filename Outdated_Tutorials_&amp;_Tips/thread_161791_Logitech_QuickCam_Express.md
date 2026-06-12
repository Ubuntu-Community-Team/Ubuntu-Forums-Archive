---
title: "Logitech QuickCam Express"
date: 2006-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Garyu on 2006-04-17
I have been sweating over my webcam trying to get it to work. I tried downloading qc-usb from the repositories but that didn't work. So I found the easycam script at [https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam) but that didn't work either. Then I discovered the HOWTO on webcams ([http://www.ubuntuforums.org/showthread.php?t=75284](http://www.ubuntuforums.org/showthread.php?t=75284)) written by Arnieboy, but that didn't work either. So I went to [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/) and downloaded the qc-usb driver fresh and compiled it with their instructions, but it still didn't work. But then I tried running easycam again, and would you believe it, it actually worked fine. FINALLY! Just thought I would share what I did since it might be of help to someone else who is trying to solve this problem. :cool:

My first error was that /dev/video0 didn't exist. That was fixed by Arnieboys HOWTO.

My second error was that camorama wouldn't start because of something with video0, but aMSN would find QC Express with channel TV8532, but it would give an error message similar to "this device uses a palette that isn't supported yet". This error was fixed by running easycam, but as I said, the first time I tried running easycam it wouldn't work, so I had to have done something else in between that made it work.

Well, actually, it only works in aMSN so far of what I have tried. Camorama says "Unable to capture image", but I don't care, as long as video conferencing works. 

Anyhow, now I am happy, and I hope this works for you too. :)

---

