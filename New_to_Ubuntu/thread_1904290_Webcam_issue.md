---
title: "Webcam issue"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Jary316 on 2012-01-04
Hi,

I have an Asus N61J running Ubuntu 11.10.

My webcam used to work perfectly with Cheese and Skype but today it stopped working. (I did not install drivers manually for it). My webcam is internal to the laptop.

Cheese is just a black screen (not allowing me to click on almost anything in the menu) and Skype video devices option has USB 2.0 UVC 2M WebCam (/dev/video0) as the only option. Clicking the "Test" button does nothing in Skype.

Running lsusb:

rudys@rudys-N61Jq:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 001 Device 006: ID 13d3:5122 IMC Networks 
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 

I am not sure how to test and solve this problem, searches on the forum or Google gave responses that did not correspond to my problem (it seemed).

Could anyone please give me a bit of help? I would really appreciate.

My webcam used to work perfectly in Cheese and Skype. I am not sure why it's not working anymore, I don't recall any major recent install, except software updates for Ubuntu itself.

Thank you very much.

---

### Post by audiomick on 2012-01-04
I hope that someone can help you, but bear in mind that the camera might simply be broken, as in mechanical defect. The easiest option might end up being an external one.

---

### Post by Jary316 on 2012-01-04
> **audiomick said:**
> I hope that someone can help you, but bear in mind that the camera might simply be broken, as in mechanical defect. The easiest option might end up being an external one.

Thank you for your quick answer. I believe the answer is going to be no to what I would like to ask but, is there any easy way to detect hardware defects for a webcam at all please?

---

### Post by Jary316 on 2012-01-04
> **audiomick said:**
> I hope that someone can help you, but bear in mind that the camera might simply be broken, as in mechanical defect. The easiest option might end up being an external one.

I've just plugged an external webcam. It works fine in Skype's test but I still have a black screen with Cheese.

---

### Post by audiomick on 2012-01-04
> **Jary316 said:**
> .., is there any easy way to detect hardware defects for a webcam at all please?
I don't know how to mechanically test them. All I could suggest would be lsusb, which you have already done. If there is a switch for the camera, you should lsusb, switch then lsusb again just to make sure it is not turned off. 

It is also possible that the connectiong cable is damaged. If you fell up to it, you could try opening up the machine to have a look. Dismantling laptops is a bit of a pain, but if you google a bit you might find instructions on the net some where. If you are willing to go that far, you may also be able to find replacement parts on the net somewhere. 

Oh, how old is it? Any chance of a gaurantee?

Any rate, what you describe with your external indicates that the internal may indeed be simply broken. However, don't just believe me. I'm not a computer mechanic ;) I hope somone else will offer an opinion.

---

### Post by Jary316 on 2012-01-04
> **audiomick said:**
> I don't know how to mechanically test them. All I could suggest would be lsusb, which you have already done. If there is a switch for the camera, you should lsusb, switch then lsusb again just to make sure it is not turned off. 

It is also possible that the connectiong cable is damaged. If you fell up to it, you could try opening up the machine to have a look. Dismantling laptops is a bit of a pain, but if you google a bit you might find instructions on the net some where. If you are willing to go that far, you may also be able to find replacement parts on the net somewhere. 

Oh, how old is it? Any chance of a gaurantee?

Any rate, what you describe with your external indicates that the internal may indeed be simply broken. However, don't just believe me. I'm not a computer mechanic ;) I hope somone else will offer an opinion.

I think you've been definitely correct!

I have a dual partition with Windows 7 installed on my other partition. I decided to test the webcam there as well. It doesn't work with Skype or with Asus Lifeframe 3 program. It seems that the webcam is indeed damaged.

I did not expect that as it seems to be well protected in the lid of the screen, but I guessed wrong.

I am not sure how long the guarantee is supposed to last for (bought it online through Amazon). I bought a year and a half ago. I'll see if I can find the guarantee, otherwise I have an external camera so that should do the trick.

Thanks a lot for your help!

---

### Post by Jary316 on 2012-01-04
Actually, the laptop's sticker mentions a 24 months warranty. It may be worth it to get it fixed then.

---

### Post by audiomick on 2012-01-04
> **Jary316 said:**
> I think you've been definitely correct!

I have a dual partition with Windows 7 installed on my other partition. I decided to test the webcam there as well. It doesn't work with Skype or with Asus Lifeframe 3 program. It seems that the webcam is indeed damaged.

Yep, that sounds pretty definite. Bad luck. Check out the gaurantee, and if it is still supposed to be current, don't let them give you any crap about a Linux install voiding it.

If it is run out, you can still think about opening the thing up to have a look, if you want. I have to admit, I have an apparently broken camera in my laptop since a year or so, and I haven't looked at that yet, even though I have had the thing open to fix a fan in the past. ;)

---

### Post by Jary316 on 2012-01-04
> **audiomick said:**
> Yep, that sounds pretty definite. Bad luck. Check out the gaurantee, and if it is still supposed to be current, don't let them give you any crap about a Linux install voiding it.

If it is run out, you can still think about opening the thing up to have a look, if you want. I have to admit, I have an apparently broken camera in my laptop since a year or so, and I haven't looked at that yet, even though I have had the thing open to fix a fan in the past. ;)

The warranty should still work. The laptop shipped on August 15th 2010. Amazon says the following about the warranty:> The notebook comes with the ASUS 360 service program that includes a 2 year global warranty, one month zero bright dot guaranty, free two-way standard shipping, twenty-four hour tech support seven days a week, and a one year accidental damage warranty, protecting the notebook from drops, fire, spills and surge. 

I just hope the camera is part of the 2 year global warranty and not the one year accidental damage warranty, but it should.

Do you know how I can prove to them that it is not software but hardware? Should I just tell them I tried 2 softwares on both Ubuntu and Windows 7 and the webcam did not respond please?

Thank you!

---

### Post by audiomick on 2012-01-04
I've never dealt with them, but I would get in touch with them and just tell them that the camera suddenly stopped working for no apparent reason. Don't hide the fact that you have ubuntu on there, but start by telling them that the camera doesn't work in the Asus program and in skype in windows. They will almost certainly want you to send it in, and it might be away for a long time. Certainly backup anything that is important that is on there before you send it anywhere.

---

### Post by Jary316 on 2012-01-04
> **audiomick said:**
> I've never dealt with them, but I would get in touch with them and just tell them that the camera suddenly stopped working for no apparent reason. Don't hide the fact that you have ubuntu on there, but start by telling them that the camera doesn't work in the Asus program and in skype in windows. They will almost certainly want you to send it in, and it might be away for a long time. Certainly backup anything that is important that is on there before you send it anywhere.

Okay, I will try that. Thanks a lot for your help, you've been extremely helpful!

Thank you.

---

