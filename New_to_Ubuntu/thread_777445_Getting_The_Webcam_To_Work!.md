---
title: "Getting The Webcam To Work?!"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by iwallet on 2008-05-01
i have an hp laptop... with integrated webcam, it works fine with the "cheese" software, but amsn, or the facebook 'record from webcam' dont find it... why?! does anyone know how i can fix this?! thanks!!!!i will link screenshots!


[http://co1tjg.blu.livefilestore.com/y1psA9X1sjk5M_7M-O_sG7-F7Be4JKtbGxqsFKOWRvQfDE9VcdsKnPm5eVcjh22VI5PsckmotsngEyjo8Thy0cJqQ/notworking.png](http://co1tjg.blu.livefilestore.com/y1psA9X1sjk5M_7M-O_sG7-F7Be4JKtbGxqsFKOWRvQfDE9VcdsKnPm5eVcjh22VI5PsckmotsngEyjo8Thy0cJqQ/notworking.png)

[http://co1tjg.blu.livefilestore.com/y1psA9X1sjk5M_JkyWyZKAKKLNaEm-Ymsh2TpmQ6bZH83Y9aYDRGRZw0h_SM7OSqkBn8AOjbwqbt2R3S4Ji10f3Rg/options.png](http://co1tjg.blu.livefilestore.com/y1psA9X1sjk5M_JkyWyZKAKKLNaEm-Ymsh2TpmQ6bZH83Y9aYDRGRZw0h_SM7OSqkBn8AOjbwqbt2R3S4Ji10f3Rg/options.png)

[http://cid-d26273cb40479c95.skydrive.live.com/self.aspx/Public/webcam%20working.png](http://cid-d26273cb40479c95.skydrive.live.com/self.aspx/Public/webcam%20working.png)

---

### Post by artir on 2008-05-01
Type in console gstreamer-properties Then go to Video tab and click Test or a button like that. Tell me what happens.

---

### Post by iwallet on 2008-05-01
$ gstreamer-properties
/home/alexandre/.themes/Simple green/gtk-2.0/gtkrc:40: error: unexpected keyword `class', expected character `{'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
Segmentation fault

well i did the test three times, and once the webcam worked... so but i tried it one more time and it didnt :S

---

