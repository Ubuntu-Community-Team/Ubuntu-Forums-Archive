---
title: "how to install a webcam in 7.10"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by hazman on 2008-08-16
how do you install a webcam in ubuntu 7.10

---

### Post by one_iota on 2008-08-17
What make/model is the web cam?

---

### Post by Crafty Kisses on 2008-08-25
Some webcams are detected out of the box.

Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If that doesn't work post the results of > lsusb

---

### Post by hazman on 2008-09-01
still unable to use cam wat i get from lsusb is

Bus 001 Device 005: ID 05a9:a518 OmniVision Technologies, Inc. 
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by hazman on 2008-09-02
do i need the windows driver its a zoom webcam

---

### Post by one_iota on 2008-09-02
Not sure if [this]("https://answers.launchpad.net/ubuntu/+question/17420") link will help? It's about someone who needed a driver for a Logitech zoom webcam (assuming that's the same as yours) and managed to get it working.

---

### Post by cszikszoy on 2008-09-02
Try to install a program called Cheese, and see if it shows your webcam.

```
sudo apt-get install cheese
```

Cheese usually does a pretty good job with webcams.

---

### Post by hazman on 2008-09-02
tried it but no joy. i dont think it a logitech zoom it just says"ZOOM" on it. cheese just says sorry couldn't find webcam

---

### Post by hazman on 2008-09-02
can anyone help.it doing my nut in trying to get webcam to work

---

### Post by doug1212 on 2008-09-02
Is this link any use:

[HTML]http://alpha.dyndns.org/ov511/[/HTML]

Doug.

---

### Post by hazman on 2008-09-02
tried that and everything seems to be there it just wont work it lights up and everything used camoramo but that couldn't find cam

---

### Post by hazman on 2008-09-09
still no joy with this webcam it says its there light is on but camorama canrn't find it

---

### Post by aomlives on 2008-09-09
There are a few more things you could try [here]("https://help.ubuntu.com/community/Webcam").

Hope this helps.

---

