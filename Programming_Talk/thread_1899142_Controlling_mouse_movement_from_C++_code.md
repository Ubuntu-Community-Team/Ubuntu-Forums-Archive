---
title: "Controlling mouse movement from C++ code"
date: 2011-12-22
forum: Programming Talk
---

### Post by mohitdaksh on 2011-12-22
Hello everyone,

I am planning to do an image processing project for my college.

I basically want to track the hand movements and gestures using a webcam to move and click the mouse cursor. 
The image processing part can be done with OpenCV. 
The part I am more concerned with is how to control the mouse from a C++ code. I have searched on various places and there seem to be a few ways of doing it(ioctl, uinput) but I am not very sure.

In fact from what it seems the whole project can be done easily(or maybe I just think so) with [processing]("http://processing.org") without involving C++.

But, I want to learn about the linux system programming and how the hardware devices are controlled, etc. So I want to do this in C++. I just need some pointer  about how to start it and some references about things that are good to read and will be helpful.

Any reference that can first clear my understanding of how things really work down there even if unrelated to my current topic are very much welcome.

I hope my requests are not sounding too confused :)

---

### Post by hakermania on 2011-12-23
Em, I don't know if this will really help you, but I have used OpenCV along with Qt and it worked pretty good (not many things, just to show video being captured from webcam).

So, Qt provides a very easy way to control the mouse, you could start from here: [http://tinyurl.com/85r7r7n](http://tinyurl.com/85r7r7n)

---

### Post by mohitdaksh on 2011-12-23
It is certainly helpful as its the starting stage of this small project and I basically want to learn something useful thats why I am doing it. I am also interesting in learning QT so I might just give it a try as well. Thanks a lot :)

---

### Post by mohitdaksh on 2011-12-23
[This]("http://www.cprogrammingreference.com/Tutorials/Advance_Tutorials/mouseprogramming.php") seems like a good tutorial but the only problem is that it is for windows. I am sharing this for anybody who would like to access the mouse functions from windows. 

> First thing you must know how to tell a mouse to do anything. In actual  we do not communicate with mouse directly but through the driver  provide. We use interrupts to get access to this driver. Each device  provide by computer has its own port and more or less we access these  ports.....Mouse has port attached to it 0X33............We also make use of address registers. These are basically Union of type REGS defined in dos.h.> We can access various mouse functions using different  values of AX input Register and passing those values to mouse port  using a interrupt
       The Functions are listed below - Here AX, BX, CX and DX are members of Union REGS and more or less integers. 

AX = 0                     Get Mouse Status               .      Output AX Value = FFFFh  if mouse support is available.                                                        Output AX Value = 0  if mouse support is not available.
AX = 1                   Show Mouse Pointer             
AX = 2                  Hide Mouse Pointer             

etc.


One question for anyone who has done such programming. Do these things apply to Linux as well? Or the Contents of the registers can be different? And is there any equivalent of dos.h in linux?

---

### Post by Liiiim on 2011-12-23
That link looks very old and outdated.

Try the suggestions [here](http://stackoverflow.com/questions/1946181/how-can-i-control-the-keyboard-and-mouse-with-python) or [here](http://stackoverflow.com/questions/1470171/controlling-mouse-in-linux) instead.

---

### Post by mohitdaksh on 2011-12-24
Thanks a lot Liiiim!! Lot of useful information there :)

---

