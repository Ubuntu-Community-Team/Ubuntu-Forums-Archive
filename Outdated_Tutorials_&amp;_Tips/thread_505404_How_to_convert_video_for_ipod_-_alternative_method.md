---
title: "How to convert video for ipod - alternative method with VLC"
date: 2007-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by mpgarate on 2007-07-20
I had some difficulties with the other ipod video method, so I tried with VLC. Here goes:

> sudo apt-get update
sudo apt-get upgrade
sudo apt-get install vlc

   1. Run VLC
   2. Click file > Open File...
   3. Where it says "Browse" on the upper right, pick the file you want to convert
   4. Under "Advanced Options" at the bottom check "Stream / Save"
   5. Click settings
   6. Under outputs, check "File" and choose the filename
   7. Change the encapsulation method to "MP4"
   8. Under transcoding options, check the video, and make sure its set at "MP4v" with 1024 bitrate and 1 scale
   9. Check the audio, and make sure it is "mpa" with 128 bit rate and 2 channels
  10. Click okay at the bottom, and then click okay in the "Open..." window
  11. Your video should begin encoding!
  12. The resulting file can easily be transferred with latest gtkpod, or installed with automatix

---

### Post by fearpi on 2008-04-17
I had the same thought, but my output has no sound, regardless of which audio codec I select. Any thoughts?

---

### Post by schnauzer93 on 2008-04-25
I also have this problem.

---

### Post by jefflange on 2008-11-23
I also had this problem. I followed the directions, that didn't work the first time.
So, I changed the audio options, tried to do that, again, didn't work.

Finally, I tried the directions one last time, and then it magically worked. I don't know what I did to make it work, but I got it to save the video and audio properly. Does this help?

---

### Post by binbash on 2008-11-23
Nice tutorial ,thanks

---

