---
title: "Webcam (iBall) support"
date: 2020-06-18
forum: New to Ubuntu
---

### Post by sahoo-aurokumar on 2020-06-18
I want to buy this webcam below

I found their support to Linux is limited.

[https://www.iball.co.in/Product/Desktop-Accessories/Web-Cameras-/CHD20-0/640](https://www.iball.co.in/Product/Desktop-Accessories/Web-Cameras-/CHD20-0/640)

[https://www.iball.co.in/Product/Desktop-Accessories/Web-Cameras-/Robo-K20/833](https://www.iball.co.in/Product/Desktop-Accessories/Web-Cameras-/Robo-K20/833)

I want wheather it's supported on ubuntu/ kubuntu. So I mailed and I got this answer below.

we would like to inform you that we don’t provide webcam driver for Ubuntu as Ubuntu have inbuilt driver for connecting the webcam of any company if you are connecting  the webcam in Ubuntu then please contact Ubuntu team they will help you accordingly.

So if anyone using this can help me in this regard.

Thanks

---

### Post by Holger_Gehrke on 2020-06-18
Since this is a product marketed mostly -- if not exclusively -- in India (even it's page on Amazon gives the price in Indian currency), I'm not sure whether asking on an international forum in which Ubuntu users -- not Ubuntu developers -- help each others is the right place for this question.

Beyond this I can tell you that the Linux kernel has drivers for [UVC]("https://en.wikipedia.org/wiki/USB_video_device_class") devices. So if this camera conforms to the specification, it will work (plug and play, no driver installation necessary), although it might have abilities that go beyond the spec which will not be accessible or that are part of the specification but are not yet supported by the driver, like for example compressed video streams .

Holger

---

