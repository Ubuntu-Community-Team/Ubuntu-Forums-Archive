---
title: "Trouble Installing Webcam"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rockfan0005 on 2008-06-03
So, I'm an old Windows User and I just converted one of my laptops to Ubuntu...so I haven't really fooled around with it that much and already I've  encountered a problem. I want to install my Webcam. My first step was popping in the CD it came with and I clicked on the SETUP.EXE file... to be given this error: "No application suitable for automatic installation is available for handling this kind of file."

So...I did a quick google search and found out that you use Synaptic Package Manager to Install things. This is where I was more or less lost...do I search for the setup file on the CD rom? Or else how do I install it? 

Thanks in advanced,
Nick

---

### Post by spiderbatdad on 2008-06-03
many webcams work via the existing opensource driver. Do you have any apps running to use the webcam that are failing?

What kind of webcam?

Try installing camorama or cheese to open your webcam.

---

### Post by mix. on 2008-06-03
> **rockfan0005 said:**
> first step was popping in the CD it came with and I clicked on the SETUP.EXE file... to be given this error: "No application suitable for automatic installation is available for handling this kind of file."


Unfortunately, .exe files aren't runnable programs when under Linux, so the old Windows way of installing things will not work.

+1 on the suggestion for camorama, that instantly recognized my webcam.

Type this in the terminal to try:
```
sudo apt-get install camorama
```

---

### Post by loell on 2008-06-03
if you would like to find out what your webcam is or the chipset as they call it.

plug your webcam then launch the **terminal**
then type ```
lsusb
```  

you might wanna copy/paste the output here.

---

