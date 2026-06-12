---
title: "After using skype, webcam doesn't work"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by swisscow on 2008-08-30
Hi

I have a new webcam, a logitech quickcam e3500 plus which I researched before I bought  it - I wanted one that works!! and indeed it does, cheese works, camorama doesn't (? - says can't find /dev/video0), ekiga does and skype with a bit of fiddling works with both the video and mic

The problem is though after using skype, I get no picture in cheese until I reboot. And if I try to use cheese or ekiga, then the webcam in skype stops working (video and mic). It's like the application grabs the camera and then doesn't let go...if you know what I mean

I'm using the current skype beta on ubuntu 64 bit

Anyone else seeing this?

Anyone got any ideas?

---

### Post by Crafty Kisses on 2008-09-02
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by swisscow on 2008-09-02
Thanks for replying.

Yes, no problems out of the box with Ekiga, only when I use skype. If I use skype first, Ekiga doesn't work after (nor cheese). Only a reboot gives me Ekiga back.

---

### Post by Crafty Kisses on 2008-09-05
I've done some research and as it turns out, the webcam will not work if you have a 64-bit machine and have Skype, I too am in that situation. :(

---

### Post by swisscow on 2008-09-05
> **Codename said:**
> I've done some research and as it turns out, the webcam will not work if you have a 64-bit machine and have Skype, I too am in that situation. :(

Now that is a bit of a bummer..........hmmm. I've had partial success but too erratic to be usable.

Actually tried to load th 32 bit version Ubuntu but it wouldn't play nicely............though kubuntu and mandriva have no problems - go figure??!!!

Will have to try to persuade people to use ekiga then,.

Thanks

---

### Post by Crafty Kisses on 2008-09-05
No problem man, anytime. :)

---

