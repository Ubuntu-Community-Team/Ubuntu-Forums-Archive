---
title: "dvd"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by amina fatim on 2012-04-03
hello everyone,
please tell me how can i play my dvd in my ubuntu 10.10???

---

### Post by Grenage on 2012-04-03
Assuming that you have the restricted extras installed, you should be able to use the default media player.  If you don't:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by arochester on 2012-04-03
Commercial DVD? 

Add the Medibuntu repository - [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

Get the package: libdvdcss2 --from there

---

### Post by morhin on 2012-04-03
This worked for me. It's from the book "Ubunut for Non Geeks" by Rickford Grant with Phil Bull... It's about how to play encrypted dvds.

From the Ubuntu Software Center get and install:

gst-plugins-base

gstreamer0.10-plugins-good

gstreamer0.10-plugins-ugly

gstreamer0.10-plugins-bad

gst-ffmpeg

libdvdread4



Okay, you're not done yet. This next step is essential.

Go to Applications / Accessories / Terminal

Once the Terminal is open type this

sudo apt-get install libdvdread4

Once this is done you have another step to do while in Terminal

sudo /usr/share/doc/libdvdread4/install-css.sh

Now when this is completed you can close the Terminal.

Okay, now try to play the dvd. If if plays great (mine did not). In that case make sure the Ubuntu Software mentioned in the first list has been installed. If it has then repeat the steps for the Terminal. 
You can try it but mine still didn't work. So I shut down, restarted and then it worked. 

I'll subscribe to this thread to see how you do.

Morhin

:p

---

### Post by morhin on 2012-04-03
Did I really type UBUNUT for Non Geeks.

That's not bad but the book is entitled UBUNTU for Non-Geeks.

Oh yeah. The book is about 10.04 which is what I'm running.

Morhin

---

