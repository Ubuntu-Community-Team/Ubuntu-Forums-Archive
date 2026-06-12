---
title: "Using Logitech Web Cam But Mic Not Working"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by demarshall on 2012-08-01
I believe I should be posting this in another area of the forum but couldn't figure out how to do that. It seems that I can only post here...

Anyhow...  I have a Logitech web cam connected to my computer through USB and the video works fine but the mic will not work. I was in some app and it showed through a gauge that it was hearing me but that's the best that I've been able to do. I am, hopefully, temporarily using a microphone plugged into the mic jack which works fine too. Can somebody tell me how to find out why Xubuntu isn't allowing me to use the mic in the Logitech web cam and how to get it working.

Thank you very much.

David Marshall

---

### Post by levlaz on 2012-08-01
Open a terminal and type; 

alsamixer

Make sure that the mic levels are not turned down.

Which app are you trying to use this with. Sometimes you need to adjust the settings in that particular app as well.

---

### Post by demarshall on 2012-08-02
> **levlaz said:**
> Open a terminal and type; 

alsamixer

Make sure that the mic levels are not turned down.

Which app are you trying to use this with. Sometimes you need to adjust the settings in that particular app as well.

Thanks levlaz. It shows microphone and it was turned down. i believe that it is the one plugged into the microphone jack since when I unplugged it I did not hear anything come back when I did a sound check on Skype. That's where I'm trying to use the mic. It would be real nice to be able to use the one built into the web cam so that I don't have to wear a headset.

I have an HP webcam that I could use on this computer too but it had the same problems. It appears to me to be the microphones built into webcams aren't supported currently and I say currently because I remember that they were. 

Thanks again. Do you have any other ideas of can anyone else help me with this?

---

