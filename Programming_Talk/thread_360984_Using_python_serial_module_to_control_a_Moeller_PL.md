---
title: "Using python serial module to control a Moeller PLC device"
date: 2007-02-13
forum: Programming Talk
---

### Post by kthakore on 2007-02-13
I have a Moeller PLC device that connects to computer with Rs232 serial cable, and I was trying to make a python-qt gui that will control the inputs and receive timer data. I have created the gui,  and I have got the Python serial module install. I also have a documentation that tells me how the driver for it works on windows. How do I go about creating a device control in python

The attached files are the python files

also the pdf that tell me about the driver's data is [here]("http://www.mynah.com/pdf/ascii-PLC-IO(1).pdf")

---

### Post by jblebrun on 2007-02-14
> **kthakore said:**
> I have a Moeller PLC device that connects to computer with Rs232 serial cable, and I was trying to make a python-qt gui that will control the inputs and receive timer data. I have created the gui,  and I have got the Python serial module install. I also have a documentation that tells me how the driver for it works on windows. How do I go about creating a device control in python

The attached files are the python files

also the pdf that tell me about the driver's data is [here]("http://www.mynah.com/pdf/ascii-PLC-IO(1).pdf")

It looks like you have all of the information you need in the PDF and the Python code. What exactly is it that you need to know? What do you mean by "creating a device control"?

---

### Post by kthakore on 2007-02-14
I just wanted to know how I can send those commands in the PDF using python serial. By device control, I want to make a module that has functions for all the commands.

---

### Post by jblebrun on 2007-02-14
> **kthakore said:**
> I just wanted to know how I can send those commands in the PDF using python serial. By device control, I want to make a module that has functions for all the commands.

Have you looked at the documentation for the python-serial module? It's very straightforward. You open the serial port using the appropriate baud rate and settings. Then you simply use serial write commands and serial read commands, as if you were working with a file.

---

