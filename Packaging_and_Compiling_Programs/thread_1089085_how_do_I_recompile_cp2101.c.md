---
title: "how do I recompile cp2101.c"
date: 2009-03-06
forum: Packaging and Compiling Programs
---

### Post by philipMac on 2009-03-06
Hey, this might be a kind of silly question, but I have an issue which I believe might go away if I patch and recompile Linux/drivers/usb/serial/cp2101.c.

[http://ubuntuforums.org/showthread.php?p=6851047#post6851047](http://ubuntuforums.org/showthread.php?p=6851047#post6851047)

At the moment I do not have this file on my machine, I am just looking at it online.  

I was thinking maybe I need to recompile my kernel (shudder) but according to this : [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) I don't need to?

Basically I just want to add a line to cp2101.c and recompile. 

I have build-essential linux-headers-$myKernelVer and so on. 


I got the source for ubuntu 2.6.27, [https://launchpad.net/ubuntu/intrepid/+source/linux/2.6.27-11.27](https://launchpad.net/ubuntu/intrepid/+source/linux/2.6.27-11.27)

and I can see linux-2.6.27/drivers/usb/serial/cp2101.c and I have added one line to the source, 
	{ USB_DEVICE(0x08fd, 0x000a) }, /* Digianswer A/S by philip */

And not sure what to do now.  How do I compile this?

What do I have to link it against.  I am not really much of a C coder.  Ahem. 
Yeah, any help would be amazing guys. 

Thanks!!!

edit and any help I get here, I will link back to my ori thread (above), I just figured you guys would be the ones to ask this question.


EDIT I fixed this issue; see 
[http://ubuntuforums.org/showthread.php?p=6851047#post6851047](http://ubuntuforums.org/showthread.php?p=6851047#post6851047)

---

