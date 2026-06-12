---
title: "Importing photos takes 30 min.  Is this normal?"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by clambucket on 2011-09-22
I'm using 10.04.  A blank import window appears upon turning the camera on.  Left alone the photos will eventually be recognized.  This process can take 30 minutes or more.  This seems excessive.  Is there a better way?

---

### Post by technosysind on 2011-09-22
This is not normal. Can you check your log files? I'm sure it will show some errors.

---

### Post by wolfen69 on 2011-09-23
Please give the make and model of the camera.

---

### Post by clambucket on 2011-09-23
TIL I have log files.  I went into the log viewer and clicked the top one Xorg.0.log.  I did not see any errors, but the last line in the log was:

(II) No input driver/identifier specified (ignoring)

---

### Post by clambucket on 2011-09-23
The camera is a Canon rebel XT.

---

### Post by mcduck on 2011-09-23
The better way is to use a card reader to get your images directly from the memory card instead of relying on the camera's transfer.

 Pretty much all cameras have a terribly slow transfer rate compared to reading the card directly, and of course you don't need to have the camera plugged in this way so you'll be able to use it at the same time (if you have at least two memory cards for it) and you don't need to waste your camera's battery for transfers (only makes a difference if the camera doesn't charge through USB of course).

---

### Post by ofnuts on 2011-09-23
> **clambucket said:**
> The camera is a Canon rebel XT.Canon cameras do not support USB "Mass storage", and connect as "Picture Transfer" devices. 

You will also find that they are very picky about USB cable quality (use the provided cable, avoid cables of unknown specs that may be good only for USB 1.x speeds). Your camera may connect in USB 1.X mode (12Mb/s) instead of USB2 (480Mb/s).

I second the recommendation for the card reader, much faster and efficient (this is what I use for my own XT).

---

### Post by papibe on 2011-09-23
> **mcduck said:**
> The better way is to use a card reader to get your images directly from the memory card instead of relying on the camera's transfer.
+1

I had a couple of terrible experiences transferring photos using the provided USB cable. I bought a very [inexpensive]("http://www.microcenter.com/single_product_results.phtml?product_id=0319528") USB card reader and all problem solved!

Regards.

---

### Post by ofnuts on 2011-09-23
> **papibe said:**
> +1

I had a couple of terrible experiences transferring photos using the provided USB cable. I bought a very [inexpensive]("http://www.microcenter.com/single_product_results.phtml?product_id=0319528") USB card reader and all problem solved!

Regards.And most recent computers have a SD card reader built-in.

---

### Post by mike555 on 2011-09-23
You might try plugging into the usb in the back of your computer, often computers have only USB 1.1 plugs in front ,but have USB 2. in back.

---

### Post by clambucket on 2011-09-23
Thanks for all the replies everyone.  I am going to try the card reader and see how that goes.

---

