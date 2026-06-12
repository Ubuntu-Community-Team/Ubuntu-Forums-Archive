---
title: "Hello Not sure where to post."
date: 2011-12-24
forum: New to Ubuntu
---

### Post by budder8818 on 2011-12-24
I just installed Ubuntu on an old 2003 dell desktop XPS. It seems like a very nice OS and I like the UI desktop. I have a question about to the possibility of something.

My experience:

First, I'm an electrical engineer just graduated and I have experience programming Java, C and C++ and alittle verilog. Most of my C programming experience comes for programming on smaller machines like micro-controllers and FPGAs and DSP. I'm very good at programming java but my expereince is mostly limited to the fundamental programming concepts of OOP as I have never actually written an application outside of the command prompt (Eclipse). However, I have written a lot in Java and am more than beginner.  

I've built,tested and designed a lot of circuitry before and understand how wireless communication systems work. 

So my question:

I want to be able to talk to my desktop using a UART chip. I wanted to know how I can write applications on Ubuntu OS that can act as standalone GUI interfaces and interface via I/O ports on my desktop like the USB, Speakers ect. Is there some IDE (For Ubuntu) I need to download that contains the libraries to interface with these I/O ports like USB? So lets say I want to write a program on my Ubuntu desktop that contains just a text box and a graphical button. The function of the program is:

1. Enter a number in the text box. 
2. Press the button --> Transmit number over USB to UART. 
3. Then the number say 5 ->101 would turn on say some LEDs. Say LED 1,2,3. 1 ->ON, 2->OFF, 3->ON corresponding to the high bits for the number "5". 

Thank you

I really just want to learn how to program on a powerful desktop machine and communicate data over USB. 

John Budd

---

### Post by 73ckn797 on 2011-12-24
You probably would want to post in Programming Talk. Be a little more descriptive with the post title. I do not program so I cannot answer your other concerns.   				[Ubuntu Forums]("http://ubuntuforums.org/index.php")  	> [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Other Community Discussions]("http://ubuntuforums.org/forumdisplay.php?f=125")   	> [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")

---

### Post by anewguy on 2011-12-24
You need the libusb development library and documentation.  It contains such things as low-level calls to USB device endpoints, etc..  I believe it is still called libusb-dev, but I haven't checked in a while.

Dave ;)

---

### Post by btindie on 2011-12-24
Run synaptic and type in libusb in the search box, it'll list a number of packages. There may be something more suited to what you want to do already available?

The packages that contain the C header files end in *-dev.

You may want to look at another language such as Python which is interpreted so it doesn't need to be compiled etc.. It should be quite easy for you to pick up if you're familiar with C and Java.

There's also VHDL / Xilinx software if that's what you're working on... Just type it into the search box in Synaptic.

---

### Post by Paqman on 2011-12-24
You can also get good help at askubuntu.com for this type of thing. It's excellent if you've got specific questions about progamming or very techy subjects.

---

### Post by budder8818 on 2011-12-24
Thanks guys

---

### Post by anewguy on 2011-12-25
All of the things in the libusb development lib are not difficult to use, especially for someone with the programming background and the engineering background you have.  You already understand endpoints and how to use them.

It's been about 2 years since I last fiddled with them.  I may have a sample yet somewhere and if I do I'll PM it to you.

Dave ;)

---

