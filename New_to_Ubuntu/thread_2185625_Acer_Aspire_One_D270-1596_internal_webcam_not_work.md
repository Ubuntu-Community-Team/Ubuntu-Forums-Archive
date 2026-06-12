---
title: "Acer Aspire One D270-1596 internal webcam not working"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by megan-n on 2013-11-03
Hi; 
I have an Acer Aspire One D270-1596 laptop (Intel Atom N2600 1.6 GHz processor) with an internal camera that is listed in the terminal. The camera shows as;
usb 1-3: Webcam
usb 1-3: Manufacturer:SuYin
usb 1-3: SerialNumber:HF0319-M08C-OV01-VR01.00.00
followed by (and I don't know if this applies to the camera or is simply the next on the list - sorry);
ata1:SATA link up 3.0 Gbps 
When I was setting up the operating system on the laptop I was asked to take a picture (of myself) with the camera and it appeared to be working. That was unfortunately the last time I used the camera. I don't see the picture taken anywhere either even though there did seem to be one taken. Has anyone had this issue before? Or any suggestions on the solution. I did look on the net, but no joy. Thank you!

meg

---

### Post by gordintoronto on 2013-11-03
What makes you believe the webcam is not working?

What version of Ubuntu? Have you installed Cheese and tried it? Could you run this command and paste the result into your response: lsusb

---

### Post by coldraven on 2013-11-04
Look in your home folder for the hidden file .face (Dot face) it could be the picture of yourself.
To see hidden files in the Nautilus file browser press Ctrl+H.

In addition to installing cheese you could also try installing uvcview. In uvcview you might need to uncheck "Auto Levels" and adjust the brightness.

---

