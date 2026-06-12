---
title: "[SOLVED] Can't see whole window because of low resolution"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by richardgundersen on 2008-10-12
Hi

Trying to install the propriatary ATI driver. It's got a GUI, but because I'm locked into 640x480, I can't see the buttons at the bottom of the installation wizard. 

I know there is a 'continue' button there, but since I can't see it, I can't click on it, and no keyboard commands I've tried seem to work either. 

Is there a way I can zoom out or somehow see the bottom part of the window? (PS it wont resize either...)

Thanks

---

### Post by Elfy on 2008-10-12
Try to use alt + left (I think) mouse button - there is definitely a combination that works to move the screen up so you can see the buttons.

---

### Post by richardgundersen on 2008-10-12
Thanks forestpixie, that did the job perfectly - simple but effective :)

If it helps anyone, I have been installing the latest ATI prop drivers, and this is how I did it on Hardy

Run the ati-driver-installer-8-9-x86.x86_64.run installer

sudo ./ati....run

That opens the gui, but it doesn't work because ubuntu-specific package isnt there, so you have to build it. To do that, quit and then run...

./ati...run --listpkg

This will give a list of packages to build. At the end of the output of that command is an example, so replace the package name in the example with 'Ubuntu/hardy'

This will then generate a load of .deb files in the current directory. 
Install all of these .deb packages
Then run the original ATI installer again (now that the dependencies are installed)

Reboot, and you will have a nice hi-res screen - at last!!!

BTW this is on an ATI 4870 HD

---

### Post by Elfy on 2008-10-12
Good, wasn't sure if it would work :)

Can you mark the thread please.

---

