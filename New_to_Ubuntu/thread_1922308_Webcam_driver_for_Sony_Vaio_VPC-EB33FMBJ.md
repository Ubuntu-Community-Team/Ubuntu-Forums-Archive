---
title: "Webcam driver for Sony Vaio VPC-EB33FM/BJ"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by Adam Jensen on 2012-02-08
Hello everyone,

   Where/how can I get the driver for my Sony Vaio's webcam? The model number is VPC-EB33FM/BJ. Thanks in advance.

-Adam Jensen

---

### Post by samigina on 2012-02-08
Please open a terminal and type "lsusb" and copy/paste the output here, so we can know the chip of your webcam.

---

### Post by Adam Jensen on 2012-02-08
> **samigina said:**
> Please open a terminal and type "lsusb" and copy/paste the output here, so we can know the chip of your webcam.

Here is the output:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:6409 Microdia Webcam
Bus 001 Device 004: ID 8086:0186 Intel Corp. WiMAX Connection 2400m
Bus 002 Device 003: ID 0461:4d64 Primax Electronics, Ltd 

```

---

### Post by samigina on 2012-02-08
Hi, are you sure your camera isnt working? Have you installed cheese from the Software Center?

From what I can see the driver is already on the linux kernel, so your camera should work out of the box.

Please verify if it is really working installing Cheese an using it to test your camera.

---

### Post by Adam Jensen on 2012-02-08
I installed cheese and it works fine. The only thing that is not working now is the microphone.

---

### Post by samigina on 2012-02-09
How are you testing your microphone?

---

### Post by Adam Jensen on 2012-02-09
I tried using the feature in Google chrome where you can enter a search query by speaking into the microphone. It works fine on my Windows OS but does not work on Ubuntu.

---

### Post by samigina on 2012-02-09
Im at the office, here Im using windows, so when I came home I will test my system to find if it works.

Meanwhile have you looked at your sound setting, input tab?

---

### Post by Adam Jensen on 2012-02-10
I went to the input tab in the sound settings. Turns out the input was on mute (im guessing by default?). I un-muted it and the microphone works fine now. Thanks for the help.

---

