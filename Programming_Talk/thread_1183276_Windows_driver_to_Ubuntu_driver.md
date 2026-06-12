---
title: "Windows driver to Ubuntu driver ???"
date: 2009-06-09
forum: Programming Talk
---

### Post by shg234 on 2009-06-09
**Hi all,**
 
**I'm doing a hobby project with some embedded touch panels. For running a simple demo for my project I have a windows driver and a piece of small demonstration software. It runs quite well in my Windows XP, now as an Ubuntu fan I want to run the same demo software in Ubuntu. But the driver I have is only supported by windows.**
 
**Now, can anyone help me to convert my windows driver to Ubuntu driver?? Please enlight something on this topic. I've never experienced linux driver before. **
 
**Note: If needed, I can provide the C/C++ source code of my windows driver. **

---

### Post by dileepm on 2009-06-10
What kind of driver program is it?

---

### Post by shg234 on 2009-06-10
> **dileepm said:**
> What kind of driver program is it?
Can you please ask more specifically???

---

### Post by PmDematagoda on 2009-06-10
> **shg234 said:**
> Can you please ask more specifically???

He's asking what kind of driver it is that you created, whether it is an input device driver, graphics card driver, sound card driver or whatever. From what I see in your first post, I'm guessing it's a driver for an input device like a mouse or keyboard?

---

### Post by johnl on 2009-06-10
If your device connects to the PC through a serial port it should be a fairly easy task.  You won't need to write an actual 'driver', just setup the linux serial port in the expected mode and write some code to talk to your device.

If your device connects via USB it might be more difficult.

---

### Post by shg234 on 2009-06-10
> **PmDematagoda said:**
> He's asking what kind of driver it is that you created, whether it is an input device driver, graphics card driver, sound card driver or whatever. From what I see in your first post, I'm guessing it's a driver for an input device like a mouse or keyboard?
 
Yes, you are right, it's an input device. 
To be more specific, its an embedded 3inch X 7inch touch panel to take input by touching that panel.
 
Its encouraging to get reply from such experienced people like you...

---

### Post by shg234 on 2009-06-10
> **johnl said:**
> If your device connects to the PC through a serial port it should be a fairly easy task. You won't need to write an actual 'driver', just setup the linux serial port in the expected mode and write some code to talk to your device.
 
How to setup the ubuntu serial port in an expected mode?? where to write those codes? Even though my device has no serial port, I would like to learn the process. 
 
[quote=johnl] 
If your device connects via USB it might be more difficult.[/quote]
 
Its difficult!! Oh ...no... I'm afraid my device is a USB input device. Now, how to start??

---

### Post by leblancmeneses on 2009-06-10
sweet so you used wdk sdk?

something i've been meaning to do.. [http://osrfx2.sourceforge.net/](http://osrfx2.sourceforge.net/)
he has it working in ubuntu

actually i have the hardware but haven't had time to run it....

maybe its time...

---

### Post by shg234 on 2009-06-12
> **leblancmeneses said:**
>  
something i've been meaning to do.. [http://osrfx2.sourceforge.net/](http://osrfx2.sourceforge.net/)
he has it working in ubuntu
 
actually i have the hardware but haven't had time to run it....
 
From where I can have this board? if you have no time to run it, send it to me :) ...

---

### Post by shg234 on 2009-06-22
Can anyone tell me about some open source linux driver for USB input device??? please...:popcorn:

---

